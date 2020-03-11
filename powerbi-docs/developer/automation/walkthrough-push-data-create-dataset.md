---
title: Adathalmaz létrehozása
description: Útmutató – Adatok elküldése adatkészletbe – Adatkészlet létrehozása a Power BI-ban
author: KesemSharabi
ms.author: kesharab
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.date: 02/05/2019
ms.openlocfilehash: a013053e3a7948f340b8c27e154cc7578cdea672
ms.sourcegitcommit: 87b7cb4a2e626711b98387edaa5ff72dc26262bb
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/10/2020
ms.locfileid: "79079140"
---
# <a name="step-3-create-a-dataset-in-power-bi"></a>3\. lépés: Adatkészlet létrehozása a Power BI-ban
Ez a cikk az [adatok az adatkészletekbe való küldését](walkthrough-push-data.md) ismertető részletes útmutató része.

Az Adatok elküldése az adatkészletbe **2. lépésében** ([Hitelesítéshez szükséges hozzáférési jogkivonat beszerzése](walkthrough-push-data-get-token.md)) egy tokent kapott, amellyel hitelesítheti magát az **Azure AD**-ben. Ebben a lépésben a token használatával meghívja a [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets) műveletet.

REST-erőforrás meghívásához használja az erőforrás helyét megadó URL-címet, és küldjön az adatkészletet leíró JavaScript Object Notation- (JSON-) sztringet a Power BI szolgáltatás erőforrásának. A REST-erőforrás azonosítja a Power BI szolgáltatás azon részét, amellyel dolgozni szeretne. Adatok adatkészletbe történő küldéséhez a célerőforrás egy **Adatkészlet**. Az adatkészletet azonosító URL-cím https://api.PowerBI.com/v1.0/myorg/datasets. Ha egy csoporton belül küld adatokat, akkor az URL-cím https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets.

Egy Power BI REST-művelet hitelesítéséhez adja hozzá a [hitelesítéshez szükséges hozzáférési jogkivonat beszerzését](walkthrough-push-data-get-token.md) ismertető szakaszban kapott jogkivonatot egy kérés fejlécéhez:

Amikor a [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets) műveletet meghívja, egy új adatkészlet jön létre. 

![](media/walkthrough-push-data-create-dataset/powerbi-developer-create-dataset.png)

A következőképpen hozhat létre adatkészletet a Power BI-ban.

## <a name="create-a-dataset-in-power-bi"></a>Adatkészlet létrehozása a Power BI-ban
> [!NOTE]
> Mielőtt elkezdené, győződjön meg arról, hogy követte az [adatok leküldése az adatkészletbe](walkthrough-push-data.md) bemutatóban található korábbi lépéseket.
> 
> 

1. A [2. lépés – Hitelesítéshez szükséges hozzáférési jogkivonat beszerzése](walkthrough-push-data-get-token.md) részben létrehozott Konzolalkalmazás-projektben adja hozzá a **using System.Net;** és a **using System.IO** parancsot a Program.cs-hez.
2. Adja hozzá a Program.cs-hez az alábbi kódot.
3. Futtassa a Konzolalkalmazást, és jelentkezzen be a Power BI-fiókjába. A konzolablakban látnia kell az **Adatkészlet létrehozva** üzenetet. Az új adatkészlet megtekintéséhez bejelentkezhet a Power BI-ba is.

**Minta: Adatok küldése adatkészletekbe**

Adja hozzá ezt a kódot a Program.cs fájlhoz.

* Static void Main(string[] args):
  
    ```csharp
    static void Main(string[] args)
    {
        //Get an authentication access token
        token = GetToken();
  
        //Create a dataset in Power BI
        CreateDataset();
    }
    ```
* Adjon hozzá egy CreateDataset() metódust:
  
    ```csharp
    #region Create a dataset in Power BI
    private static void CreateDataset()
    {
        //TODO: Add using System.Net and using System.IO
  
        string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
        //POST web request to create a dataset.
        //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
        HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
        request.KeepAlive = true;
        request.Method = "POST";
        request.ContentLength = 0;
        request.ContentType = "application/json";
  
        //Add token to the request header
        request.Headers.Add("Authorization", String.Format("Bearer {0}", token));
  
        //Create dataset JSON for POST request
        string datasetJson = "{\"name\": \"SalesMarketing\", \"tables\": " +
            "[{\"name\": \"Product\", \"columns\": " +
            "[{ \"name\": \"ProductID\", \"dataType\": \"Int64\"}, " +
            "{ \"name\": \"Name\", \"dataType\": \"string\"}, " +
            "{ \"name\": \"Category\", \"dataType\": \"string\"}," +
            "{ \"name\": \"IsCompete\", \"dataType\": \"bool\"}," +
            "{ \"name\": \"ManufacturedOn\", \"dataType\": \"DateTime\"}" +
            "]}]}";
  
        //POST web request
        byte[] byteArray = System.Text.Encoding.UTF8.GetBytes(datasetJson);
        request.ContentLength = byteArray.Length;
  
        //Write JSON byte[] into a Stream
        using (Stream writer = request.GetRequestStream())
        {
            writer.Write(byteArray, 0, byteArray.Length);
  
            var response = (HttpWebResponse)request.GetResponse();
  
            Console.WriteLine(string.Format("Dataset {0}", response.StatusCode.ToString()));
  
            Console.ReadLine();
        }
    }
    #endregion
    ```

A következő lépés bemutatja, [hogyan kérhet le egy adatkészletet sorok Power BI-táblához való hozzáadásához](walkthrough-push-data-get-datasets.md).

Az alábbiakban megtalálja a [teljes kódlistát](#code).

<a name="code"/>

## <a name="complete-code-listing"></a>Teljes kódlista

```csharp
using System;
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using System.Net;
using System.IO;

namespace walkthrough_push_data
{
    class Program
    {
        private static string token = string.Empty;

        static void Main(string[] args)
        {

            //Get an authentication access token
            token = GetToken();

            //Create a dataset in Power BI
            CreateDataset();

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


        #region Create a dataset in Power BI
        private static void CreateDataset()
        {
            //TODO: Add using System.Net and using System.IO

            string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
            //POST web request to create a dataset.
            //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
            HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
            request.KeepAlive = true;
            request.Method = "POST";
            request.ContentLength = 0;
            request.ContentType = "application/json";

            //Add token to the request header
            request.Headers.Add("Authorization", String.Format("Bearer {0}", token));

            //Create dataset JSON for POST request
            string datasetJson = "{\"name\": \"SalesMarketing\", \"tables\": " +
                "[{\"name\": \"Product\", \"columns\": " +
                "[{ \"name\": \"ProductID\", \"dataType\": \"Int64\"}, " +
                "{ \"name\": \"Name\", \"dataType\": \"string\"}, " +
                "{ \"name\": \"Category\", \"dataType\": \"string\"}," +
                "{ \"name\": \"IsCompete\", \"dataType\": \"bool\"}," +
                "{ \"name\": \"ManufacturedOn\", \"dataType\": \"DateTime\"}" +
                "]}]}";

            //POST web request
            byte[] byteArray = System.Text.Encoding.UTF8.GetBytes(datasetJson);
            request.ContentLength = byteArray.Length;

            //Write JSON byte[] into a Stream
            using (Stream writer = request.GetRequestStream())
            {
                writer.Write(byteArray, 0, byteArray.Length);

                var response = (HttpWebResponse)request.GetResponse();

                Console.WriteLine(string.Format("Dataset {0}", response.StatusCode.ToString()));

                Console.ReadLine();
            }
        }
        #endregion
    }
}
```

[Következő lépés >](walkthrough-push-data-get-datasets.md)

## <a name="next-steps"></a>Következő lépések
* [Adatkészlet lekérése, és sorok hozzáadása egy Power BI-táblához](walkthrough-push-data-get-datasets.md)  
* [Hitelesítési hozzáférési token beszerzése](walkthrough-push-data-get-token.md)  
* [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdataset)  
[PostDatasetInGroup](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdatasetingroup)  
* [Adatok elküldése egy Power BI-irányítópultba](walkthrough-push-data.md)  
* [A Power BI REST API áttekintése](overview-of-power-bi-rest-api.md)  
* [A Power BI REST API-jainak leírása](https://docs.microsoft.com/rest/api/power-bi/)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

