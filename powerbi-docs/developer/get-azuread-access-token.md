---
title: Felhasználók hitelesítése és Azure AD hozzáférési token beszerzése az alkalmazáshoz
description: Megismerheti, hogyan kell regisztrálni egy alkalmazást az Azure Active Directoryban Power BI-tartalom beágyazásához.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 08/11/2017
ms.author: maghan
ms.openlocfilehash: f97376477ff3938280bf00b14f4aa511b977d8c7
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54286973"
---
# <a name="authenticate-users-and-get-an-azure-ad-access-token-for-your-power-bi-app"></a>Felhasználók hitelesítése és Azure AD hozzáférési token beszerzése a Power BI-alkalmazáshoz
Megtudhatja, hogyan hitelesíthet felhasználókat a Power BI-alkalmazásban, és hogyan kérhet le hozzáférési tokent a REST API-val való használathoz.

A Power BI REST API hívásához egy Azure Active Directory (Azure AD) **hitelesítési hozzáférési tokenre** (hozzáférési tokenre) van szüksége. A **hozzáférési tokennel** engedélyezhető, hogy az alkalmazás hozzáférjen a **Power BI**-irányítópultokhoz, -csempékhez és -jelentésekhez. Az Azure Active Directory **hozzáférési token** folyamatával kapcsolatos további információkért lásd az [Azure AD hozzáférési kód engedélyezési folyamatával](https://msdn.microsoft.com/library/azure/dn645542.aspx) kapcsolatos cikket.

A tartalom beágyazási módjától függően eltérő módon kérhető le a hozzáférési token. Ebben a cikkben két különböző megközelítést használunk.

## <a name="access-token-for-power-bi-users-user-owns-data"></a>Hozzáférési token Power BI-felhasználók számára (a felhasználó az adatok tulajdonosa)
Ez a példa arra vonatkozik, amikor a felhasználók manuálisan jelentkeznek be az Azure AD-be a szervezeti bejelentkezési adataikkal. Tartalmak olyan Power BI-felhasználók számára történő beágyazásához használható, akik az általuk a Power BI szolgáltatásban elérhető tartalmakat fogják elérni.

### <a name="get-an-authorization-code-from-azure-ad"></a>Hozzáférési kód beszerzése az Azure AD-ből
A **hozzáférési token** lekérésének első lépése egy hozzáférési kód lekérése az **Azure AD-ből**. Ehhez egy lekérdezési sztringet kell összeállítani a következő tulajdonságokkal és átirányítani azt az **Azure AD-be**.

**Hozzáférési kód lekérdezési sztringje**

```
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

A lekérdezési sztring összeállítása után átirányítja azt az **Azure AD-be****hozzáférési kód** lekéréséhez.  Az alábbiakban egy teljes C# metódus látható **hozzáférési kód** lekérdezési sztringjének elkészítésére és az **Azure AD-ba** való átirányítására. Ha megvan a hozzáférési kód, a **hozzáférési kóddal** lekér egy **hozzáférési jogkivonatot**.

Ezután a rendszer a redirect.aspx.cs fájlban meghívja az [AuthenticationContext.AcquireTokenByAuthorizationCode](https://msdn.microsoft.com/library/azure/dn479531.aspx) elemet a token létrehozásához.

**Hozzáférési kód lekérése**

```
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
    // AADAuthorityUri = https://login.windows.net/common/oauth2/authorize/
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;
    var authUri = String.Format("{0}?{1}", authorityUri, queryString);
    Response.Redirect(authUri);
}
```

### <a name="get-an-access-token-from-authorization-code"></a>Hozzáférési token lekérése hozzáférési kódból
Most már rendelkeznie kell egy hozzáférési kóddal az Azure AD-ből. Amikor az **Azure AD** átirányít a webalkalmazásra egy **hozzáférési kóddal**, a **hozzáférési kóddal** lekér egy hozzáférési tokent. Az alábbiakban látható C# minta az átirányítási oldalon és a default.aspx oldal Page_Load eseményében használható.

A **Microsoft.IdentityModel.Clients.ActiveDirectory** névtér az [Active Directory hitelesítési tár](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet-csomagjából kérhető le.

```
Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
```

**Redirect.aspx.cs**

```
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

**Default.aspx**

```
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

Ehhez a megközelítéshez egyetlen *fő* fiókot használunk, amely egy Power BI Pro-felhasználó. A fiók hitelesítő adatai az alkalmazással együtt vannak tárolva. Az alkalmazás ezeket a tárolt hitelesítő adatokat használja az Azure AD-val való hitelesítéshez. Az alábbiakban látható példa kód az [alkalmazás tulajdonában lévő adatmintából](https://github.com/guyinacube/PowerBI-Developer-Samples/tree/master/App%20Owns%20Data) származik.

**HomeController.cs**

```
using Microsoft.IdentityModel.Clients.ActiveDirectory;

// Create a user password cradentials.
var credential = new UserPasswordCredential(Username, Password);

// Authenticate using created credentials
var authenticationContext = new AuthenticationContext(AuthorityUrl);
var authenticationResult = await authenticationContext.AcquireTokenAsync(ResourceUrl, ClientId, credential);

if (authenticationResult == null)
{
    return View(new EmbedConfig()
    {
        ErrorMessage = "Authentication Failed."
    });
}

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");
```

Az **await** használatával kapcsolatos információért lásd: [await (C# referencia)](https://docs.microsoft.com/dotnet/csharp/language-reference/keywords/await)

## <a name="next-steps"></a>További lépések
Most, hogy rendelkezik a hozzáférési tokennel, meghívhatja a Power BI REST API-t tartalmak beágyazásához. A tartalmak beágyazásával kapcsolatos információkért lásd: [Power BI-irányítópultok, -jelentések és -csempék beágyazása](embed-sample-for-customers.md#embed-your-content-within-your-application).

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)