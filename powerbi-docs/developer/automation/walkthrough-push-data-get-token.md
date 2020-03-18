---
title: Hitelesítési hozzáférési jogkivonat beszerzése
description: Útmutatás az adatok leküldéséhez – Hitelesítéshez szükséges hozzáférési jogkivonat beszerzése
author: KesemSharabi
ms.author: kesharab
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.date: 05/29/2019
ms.openlocfilehash: 4b1c890a69863f3e05dee052efe9529b174f0874
ms.sourcegitcommit: 87b7cb4a2e626711b98387edaa5ff72dc26262bb
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/10/2020
ms.locfileid: "79079117"
---
# <a name="step-2-get-an-authentication-access-token"></a>2\. lépés: Hitelesítési hozzáférési jogkivonat beszerzése

Ez a cikk az [Adatok elküldése Power BI-adatkészletbe](walkthrough-push-data.md) című sorozat második lépése.

Az 1. lépésben [regisztrált egy ügyfélalkalmazást az Azure AD-ben](../register-app.md). Ebben a lépésben hitelesítéshez szükséges hozzáférési jogkivonatot fogja beszerezni. A Power BI-alkalmazások integrálva vannak az Azure Active Directoryval, hogy biztonságos bejelentkezést és hitelesítést biztosítsanak az alkalmazáshoz. Az Azure AD-hitelesítéshez és a Power BI-erőforrásokhoz való hozzáféréshez az alkalmazás jogkivonatokat használ.

## <a name="get-an-authentication-access-token"></a>Hitelesítési hozzáférési jogkivonat beszerzése

A kezdés előtt győződjön meg róla, hogy elvégezte az [Adatok leküldése Power BI-adatkészletekbe](walkthrough-push-data.md) sorozat [előző lépését](../register-app.md). 

Ehhez az eljáráshoz a Visual Studio 2015 vagy újabb verziója szükséges.

1. A Visual Studióban hozzon létre egy új C# **Konzolalkalmazás** projektet.

2. Telepítse az [Azure AD Authentication Library for .NET NuGet csomagot](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727). A .NET-alkalmazásnak szüksége van erre a csomagra a hitelesítéshez szükséges biztonsági jogkivonat beszerzéséhez. 

     a. Válassza az **Eszközök** > **NuGet-csomagkezelő** > **Package Csomagkezelő konzol** elemet.

     b. Írja be az **Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612** kifejezést

     c. Adja hozzá a Program.cs-hez az alábbi kifejezést: `using Microsoft.IdentityModel.Clients.ActiveDirectory;`.

3. Adja hozzá a lépések után található mintakódot a Program.cs fájlhoz.

4. Cserélje le a „{ClientID}” kifejezést az [előző cikkben](../register-app.md) az alkalmazás regisztrálásakor kapott **ügyfél-azonosítóra**.

5. Futtassa a Konzolalkalmazást, és jelentkezzen be a Power BI-fiókjába. 

   A konzolablakban látnia kell egy jogkivonatsztringet.

**Hitelesítéshez szükséges biztonsági jogkivonat beszerzésére szolgáló mintakód**

Adja ezt a kódot a Program {...} elemhez.

* Műveletek hívására szolgáló jogkivonat-változó: 
  
  ```csharp
  private static string token = string.Empty;
  
  static void Main(string[] args)
  {
  }
  ```
* Static void Main(string[] args):
  
  ```csharp
  static void Main(string[] args)
  {
    //Get an authentication access token
    token = GetToken();
  }
  ```
* GetToken() metódus hozzáadása:

```csharp
       #region Get an authentication access token
       private static string GetToken()
       {
           // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
           // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

           //The client id that Azure AD created when you registered your client app.
           string clientID = "{Client_ID}";

           //RedirectUri you used when you register your app.
           //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
           // You can use this redirect uri for your client app
           string redirectUri = "https://login.live.com/oauth20_desktop.srf";

           //Resource Uri for Power BI API
           string resourceUri = "https://analysis.windows.net/powerbi/api";

           //OAuth2 authority Uri
           string authorityUri = "https://login.microsoftonline.net/common/";

           //Get access token:
           // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
           // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
           // To install the Active Directory Authentication Library NuGet package in Visual Studio,
           //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

           // AcquireToken will acquire an Azure access token
           // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
           AuthenticationContext authContext = new AuthenticationContext(authorityUri);
           string token = authContext.AcquireToken(resourceUri, clientID, new Uri(redirectUri)).AccessToken;

           Console.WriteLine(token);
           Console.ReadLine();

           return token;
       }

       #endregion
```

A hitelesítési jogkivonat beszerzése után bármilyen Power BI-műveletet hívhat.

A sorozat következő cikke bemutatja, hogyan [hozhat létre adatkészletet a Power BI-ban](walkthrough-push-data-create-dataset.md).


## <a name="complete-code-listing"></a>Teljes kódlista

```csharp
using System;
using Microsoft.IdentityModel.Clients.ActiveDirectory;

namespace walkthrough_push_data
{
    class Program
    {
        private static string token = string.Empty;

        static void Main(string[] args)
        {

            //Get an authentication access token
            token = GetToken();

        }

        #region Get an authentication access token
        private static string GetToken()
        {
            // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
            // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

            //The client id that Azure AD created when you registered your client app.
            string clientID = "{Client_ID}";

            //RedirectUri you used when you register your app.
            //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
            // You can use this redirect uri for your client app
            string redirectUri = "https://login.live.com/oauth20_desktop.srf";

            //Resource Uri for Power BI API
            string resourceUri = "https://analysis.windows.net/powerbi/api";

            //OAuth2 authority Uri
            string authorityUri = "https://login.microsoftonline.com/common/";

            //Get access token:
            // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
            // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
            // To install the Active Directory Authentication Library NuGet package in Visual Studio,
            //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

            // AcquireToken will acquire an Azure access token
            // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
            AuthenticationContext authContext = new AuthenticationContext(authorityUri);
            string token = authContext.AcquireToken(resourceUri, clientID, new Uri(redirectUri)).AccessToken;

            Console.WriteLine(token);
            Console.ReadLine();

            return token;
        }

        #endregion

    }
}
```



## <a name="next-steps"></a>Következő lépések

* A sorozat következő cikke [az adathalmazok Power BI-ban való létrehozását ismerteti](walkthrough-push-data-create-dataset.md)
* [A Power BI REST API áttekintése](overview-of-power-bi-rest-api.md)  
* [Power BI REST API-k](https://docs.microsoft.com/rest/api/power-bi/)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)