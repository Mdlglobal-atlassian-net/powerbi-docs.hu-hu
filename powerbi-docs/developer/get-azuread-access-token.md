---
title: Felhasználók hitelesítése és Azure AD hozzáférési token beszerzése az alkalmazáshoz
description: Megismerheti, hogyan regisztrálhat egy alkalmazást az Azure Active Directoryban Power BI-tartalmak beágyazásához.
author: rkarlin
ms.author: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/04/2019
ms.openlocfilehash: 1655843d9e3175b9c428434fd533a601cc42d847
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875741"
---
# <a name="get-an-azure-ad-access-token-for-your-power-bi-application"></a>Azure AD hozzáférési jogkivonat beszerzése a Power BI-alkalmazáshoz

Ez a cikk bemutatja, hogyan hitelesíthet felhasználókat a Power BI-alkalmazásban, és hogyan kérhet le hozzáférési jogkivonatot a [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/)-val való használathoz.

Ahhoz, hogy az alkalmazás meghívja a REST API-t, egy Azure Active Directory (Azure AD) **hitelesítési hozzáférési jogkivonatra** van szüksége. Az alkalmazás hozzáférési jogkivonat használatával fér hozzá a Power BI-irányítópultokhoz, -csempékhez és -jelentésekhez. További információ: [Hozzáférés hitelezése Azure Active Directory-webalkalmazásokhoz az OAuth 2.0 kódengedélyezési folyamatával](https://docs.microsoft.com/azure/active-directory/develop/v1-protocols-oauth-code).

A tartalom beágyazási módjától függően eltérő módon kérhető le a hozzáférési jogkivonat. Ez a cikk két különböző megközelítést mutat be.

## <a name="access-token-for-power-bi-users-user-owns-data"></a>Hozzáférési token Power BI-felhasználók számára (a felhasználó az adatok tulajdonosa)

Ez a példa arra vonatkozik, amikor a felhasználók manuálisan jelentkeznek be az Azure AD-be a szervezeti bejelentkezési adataikkal. Ez a feladat akkor használatos, amikor a Power BI szolgáltatáshoz való hozzáféréssel rendelkező felhasználók számára ágyaz be tartalmat.

### <a name="get-an-azure-ad-authorization-code"></a>Azure AD-beli hitelesítési kód beszerzése

A **hozzáférési token** lekérésének első lépése egy hozzáférési kód lekérése az **Azure AD-ből**. Állítson össze egy lekérdezési sztringet a következő tulajdonságokkal és irányítsa át azt az **Azure AD-be**.

#### <a name="authorization-code-query-string"></a>Hozzáférési kód lekérdezési sztringje

```csharp
var @params = new NameValueCollection
{
    //Azure AD will return an authorization code. 
    //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
    {"response_type", "code"},

    //Client ID is used by the application to identify themselves to the users that they are requesting permissions from.
    //You get the client id when you register your Azure app.
    {"client_id", Properties.Settings.Default.ClientID},

    //Resource uri to the Power BI resource to be authorized
    // https://analysis.windows.net/powerbi/api
    {"resource", Properties.Settings.Default.PowerBiAPI},

    //After user authenticates, Azure AD will redirect back to the web app
    {"redirect_uri", "https://localhost:13526/Redirect"}
};
```

A lekérdezési sztring összeállítása után átirányítja azt az **Azure AD-be** **hozzáférési kód** lekéréséhez.  Az alábbiakban egy teljes C# metódus látható **hozzáférési kód** lekérdezési sztringjének elkészítésére és az **Azure AD-ba** való átirányítására. Ez után a **hitelesítési kód** használatával szerezhet be **hozzáférési jogkivonatot**.

A redirect.aspx.cs fájlban az [AuthenticationContext.AcquireTokenByAuthorizationCode](https://docs.microsoft.com/dotnet/api/microsoft.identitymodel.clients.activedirectory.authenticationcontext.acquiretokenbyauthorizationcodeasync?view=azure-dotnet#Microsoft_IdentityModel_Clients_ActiveDirectory_AuthenticationContext_AcquireTokenByAuthorizationCodeAsync_System_String_System_Uri_Microsoft_IdentityModel_Clients_ActiveDirectory_ClientCredential_System_String_) hívás létrehozza a tokent.

#### <a name="get-authorization-code"></a>Hozzáférési kód lekérése

```csharp
protected void signInButton_Click(object sender, EventArgs e)
{
    //Create a query string
    //Create a sign-in NameValueCollection for query string
    var @params = new NameValueCollection
    {
        //Azure AD will return an authorization code. 
        //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
        {"response_type", "code"},

        //Client ID is used by the application to identify themselves to the users that they are requesting permissions from. 
        //You get the client id when you register your Azure app.
        {"client_id", Properties.Settings.Default.ClientID},

        //Resource uri to the Power BI resource to be authorized
        // https://analysis.windows.net/powerbi/api
        {"resource", Properties.Settings.Default.PowerBiAPI},

        //After user authenticates, Azure AD will redirect back to the web app
        {"redirect_uri", "https://localhost:13526/Redirect"}
    };

    //Create sign-in query string
    var queryString = HttpUtility.ParseQueryString(string.Empty);
    queryString.Add(@params);

    //Redirect authority
    //Authority Uri is an Azure resource that takes a client id to get an Access token
    // AADAuthorityUri = https://login.microsoftonline.com/common/
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;
    var authUri = String.Format("{0}?{1}", authorityUri, queryString);
    Response.Redirect(authUri);
}
```

### <a name="get-an-access-token-from-authorization-code"></a>Hozzáférési token lekérése hozzáférési kódból

Amikor az **Azure AD** átirányít a webalkalmazásra egy **hozzáférési kóddal**, azt használva lekérhet egy hozzáférési jogkivonatot. Az alábbi C#-mintát felhasználhatja az átirányítási oldalon, és a default.aspx `Page_Load` eseményében.

A **Microsoft.IdentityModel.Clients.ActiveDirectory** névteret az [Active Directory hitelesítési kódtár](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet-csomagból kérheti le.

```powershell
Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
```

#### <a name="redirectaspxcs"></a>Redirect.aspx.cs

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{
    //Redirect uri must match the redirect_uri used when requesting Authorization code.
    string redirectUri = String.Format("{0}Redirect", Properties.Settings.Default.RedirectUrl);
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;

    // Get the auth code
    string code = Request.Params.GetValues(0)[0];

    // Get auth token from auth code
    TokenCache TC = new TokenCache();

    AuthenticationContext AC = new AuthenticationContext(authorityUri, TC);
    ClientCredential cc = new ClientCredential
        (Properties.Settings.Default.ClientID,
        Properties.Settings.Default.ClientSecret);

    AuthenticationResult AR = AC.AcquireTokenByAuthorizationCode(code, new Uri(redirectUri), cc);

    //Set Session "authResult" index string to the AuthenticationResult
    Session[_Default.authResultString] = AR;

    //Redirect back to Default.aspx
    Response.Redirect("/Default.aspx");
}
```

#### <a name="defaultaspx"></a>Default.aspx

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{

    //Test for AuthenticationResult
    if (Session[authResultString] != null)
    {
        //Get the authentication result from the session
        authResult = (AuthenticationResult)Session[authResultString];

        //Show Power BI Panel
        signInStatus.Visible = true;
        signInButton.Visible = false;

        //Set user and token from authentication result
        userLabel.Text = authResult.UserInfo.DisplayableId;
        accessTokenTextbox.Text = authResult.AccessToken;
    }
}
```

## <a name="access-token-for-non-power-bi-users-app-owns-data"></a>Hozzáférési token nem Power BI felhasználókhoz (alkalmazás tulajdonában lévő adatok)

Ezt a megközelítést általában független szoftverszállítói (ISV) típusú alkalmazásokhoz használják, ahol az alkalmazás hozzáféréssel rendelkezik az adatokhoz. A felhasználók nem feltétlenül Power BI-felhasználók, és az alkalmazás vezérli a felhasználók hitelesítését és hozzáférését.

### <a name="access-token-with-a-master-account"></a>Hozzáférési jogkivonat fő fiókkal

Ehhez a megközelítéshez egyetlen *fő* fiókot használunk, amely egy Power BI Pro-felhasználó. A fiók hitelesítő adatai az alkalmazással együtt vannak tárolva. Az alkalmazás ezeket a tárolt hitelesítő adatokat használja az Azure AD-val való hitelesítéshez. Az alábbiakban látható példa kód az [alkalmazás tulajdonában lévő adatmintából](https://github.com/guyinacube/PowerBI-Developer-Samples) származik.

### <a name="access-token-with-service-principal"></a>Hozzáférési jogkivonat szolgáltatásnévvel

Ehhez a módszerhez használhat egy olyan [szolgáltatásnevet](embed-service-principal.md), amely **csak az alkalmazásra vonatkozó** jogkivonat. Az alkalmazás a szolgáltatásnevet használja az Azure AD-val való hitelesítéshez. Az alábbiakban látható példa kód az [alkalmazás tulajdonában lévő adatmintából](https://github.com/guyinacube/PowerBI-Developer-Samples) származik.

#### <a name="embedservicecs"></a>EmbedService.cs

```csharp
var authenticationContext = new AuthenticationContext(AuthorityUrl);
       AuthenticationResult authenticationResult = null;
       if (AuthenticationType.Equals("MasterUser"))
       {
              // Authentication using master user credentials
              var credential = new UserPasswordCredential(Username, Password);
              authenticationResult = authenticationContext.AcquireTokenAsync(ResourceUrl, ApplicationId, credential).Result;
       }
       else
       {
             // Authentication using app credentials
             var credential = new ClientCredential(ApplicationId, ApplicationSecret);
             authenticationResult = await authenticationContext.AcquireTokenAsync(ResourceUrl, credential);
       }


m_tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");
```

## <a name="troubleshoot"></a>Hibaelhárítás

Hibaüzenet: „Az 'AuthenticationContext' nem tartalmaz 'AcquireToken' definíciót, és nem található az 'AuthenticationContext' típusú első argumentumot elfogadó hozzáférhető 'AcquireToken' (hiányzik egy using utasítás vagy szerelvényhivatkozás?)”.

   Ha ezt a hibát tapasztalja, próbálkozzon a [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727) letöltésével.

## <a name="next-steps"></a>Következő lépések

Most, hogy rendelkezik a hozzáférési tokennel, meghívhatja a Power BI REST API-t tartalmak beágyazásához. További információ: [Power BI-tartalom beágyazása](embed-sample-for-customers.md#embed-content-within-your-application).

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
