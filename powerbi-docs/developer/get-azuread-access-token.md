---
title: Felhasználók hitelesítése és Azure AD hozzáférési token beszerzése az alkalmazáshoz
description: Megismerheti, hogyan regisztrálhat egy alkalmazást az Azure Active Directoryban Power BI-tartalmak beágyazásához.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/05/2019
ms.openlocfilehash: 7b2249964f2fff26bc68fea19fd0010d8990110b
ms.sourcegitcommit: 0abcbc7898463adfa6e50b348747256c4b94e360
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/06/2019
ms.locfileid: "55762536"
---
# <a name="get-an-azure-ad-access-token-for-your-power-bi-application"></a>Azure AD hozzáférési jogkivonat beszerzése a Power BI-alkalmazáshoz

Megtudhatja, hogyan hitelesíthet felhasználókat a Power BI-alkalmazásban, és hogyan kérhet le hozzáférési jogkivonatot a REST API-val való használathoz.

A Power BI REST API hívásához egy Azure Active Directory (Azure AD) **hitelesítési hozzáférési tokenre** (hozzáférési tokenre) van szüksége. A **hozzáférési jogkivonattal** engedélyezhető, hogy az alkalmazás hozzáférjen a **Power BI**-irányítópultokhoz, -csempékhez és -jelentésekhez. Az Azure Active Directory **hozzáférési token** folyamatával kapcsolatos további információkért lásd az [Azure AD hozzáférési kód engedélyezési folyamatával](https://msdn.microsoft.com/library/azure/dn645542.aspx) kapcsolatos cikket.

A tartalom beágyazási módjától függően eltérő módon kérhető le a hozzáférési jogkivonat. Ebben a cikkben két különböző megközelítést használunk.

## <a name="access-token-for-power-bi-users-user-owns-data"></a>Hozzáférési token Power BI-felhasználók számára (a felhasználó az adatok tulajdonosa)

Ez a példa arra vonatkozik, amikor a felhasználók manuálisan jelentkeznek be az Azure AD-be a szervezeti bejelentkezési adataikkal. Ez a feladat a tartalmak olyan Power BI-felhasználók számára történő beágyazásához használható, akik rendelkeznek hozzáférési jogosultsággal a tartalomhoz és a Power BI szolgáltatáshoz.

### <a name="get-an-authorization-code-from-azure-ad"></a>Hozzáférési kód beszerzése az Azure AD-ből

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
    {"redirect_uri", "http://localhost:13526/Redirect"}
};
```

A lekérdezési sztring összeállítása után átirányítja azt az **Azure AD-be** **hozzáférési kód** lekéréséhez.  Az alábbiakban egy teljes C# metódus látható **hozzáférési kód** lekérdezési sztringjének elkészítésére és az **Azure AD-ba** való átirányítására. Ha megvan a hozzáférési kód, a **hozzáférési kóddal** lekér egy **hozzáférési jogkivonatot**.

A redirect.aspx.cs fájlban az [AuthenticationContext.AcquireTokenByAuthorizationCode](https://msdn.microsoft.com/library/azure/dn479531.aspx) hívás létrehozza a tokent.

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
        {"redirect_uri", "http://localhost:13526/Redirect"}
    };

    //Create sign-in query string
    var queryString = HttpUtility.ParseQueryString(string.Empty);
    queryString.Add(@params);

    //Redirect authority
    //Authority Uri is an Azure resource that takes a client id to get an Access token
    // AADAuthorityUri = https://login.microsoftonline.net/common/
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;
    var authUri = String.Format("{0}?{1}", authorityUri, queryString);
    Response.Redirect(authUri);
}
```

### <a name="get-an-access-token-from-authorization-code"></a>Hozzáférési token lekérése hozzáférési kódból

Most már rendelkeznie kell egy hozzáférési kóddal az Azure AD-ből. Amikor az **Azure AD** átirányít a webalkalmazásra egy **hozzáférési kóddal**, a **hozzáférési kóddal** lekér egy hozzáférési tokent. Az alábbiakban látható C# minta az átirányítási oldalon és a default.aspx oldal Page_Load eseményében használható.

A **Microsoft.IdentityModel.Clients.ActiveDirectory** névtér az [Active Directory hitelesítési tár](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet-csomagjából kérhető le.

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

Ezt a megközelítést általában ISV típusú alkalmazásokhoz használják, ahol az alkalmazás az adatok hozzáférésének tulajdonosa. A felhasználók nem feltétlenül Power BI-felhasználók, és az alkalmazás vezérli a hitelesítést és a végfelhasználók hozzáférését.

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

## <a name="next-steps"></a>Következő lépések

Most, hogy rendelkezik a hozzáférési tokennel, meghívhatja a Power BI REST API-t tartalmak beágyazásához. A tartalmak beágyazásával kapcsolatos információkért lásd: [Power BI-tartalom beágyazása](embed-sample-for-customers.md#embed-content-within-your-application).

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)