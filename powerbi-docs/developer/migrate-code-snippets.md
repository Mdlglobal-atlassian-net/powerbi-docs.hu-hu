---
title: Kódrészletek a tartalmak Power BI Embeddedből való migrálásához
description: Íme a tartalmak migrálásához szükséges alapvető műveletek néhány kódrészlete
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 03/06/2018
ms.author: maghan
ms.openlocfilehash: ea323419e38aab7360bb817a56ae4c7c662998ed
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34689849"
---
# <a name="code-snippets-for-migrating-content-from-power-bi-workspace-collection"></a>Kódrészletek a tartalmak Power BI-munaterületcsoportból való migrálásához
Íme a tartalmak migrálásához szükséges alapvető műveletek néhány kódrészlete. Egyes jelentéstípusok kapcsolódó folyamatai: [Power BI-munkaterület-csoport tartalmainak migrálása a Power BI Embeddedbe](migrate-from-powerbi-embedded.md#content-migration).

A Power BI Embedded (PaaS) tartalmainak a Power BI szolgáltatásba (SaaS) való másolásában egy **migrálási eszközt** használhat segítségül. Ez különösen akkor hasznos, ha sok tartalommal rendelkezik. További információ: [Power BI Embedded migrálási eszköz](migrate-tool.md).

Az alábbi példakódok a C# és a [Power BI .NET SDK](https://www.nuget.org/profiles/powerbi) használatával készültek.

A következő névtereket használja az alábbi kódrészletek végrehajtásához.

```
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.PowerBI.Api.V1;
using Microsoft.PowerBI.Api.V1.Models;
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;
using Microsoft.Rest;
using Microsoft.Rest.Serialization;
using Newtonsoft.Json;
using Newtonsoft.Json.Linq;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Net;
using System.Net.Http;
using System.Net.Http.Headers;
using System.Text;
using System.Threading.Tasks;
```


## <a name="export-report-from-paas-workspace"></a>Jelentés exportálása PaaS-munkaterületről
```
    // Create a token credentials with "AppKey" type
    var credentials = new TokenCredentials(<myAppKey==>, "AppKey");

    // Instantiate your Power BI client passing in the required credentials
    var client = new PowerBIClient(credentials);

    client.BaseUri = new Uri("https://api.powerbi.com");

    var response = client.Reports.ExportReportWithHttpMessagesAsync(<myWorkspaceCollectionName>, <myWorkspaceId>, <myReportId>);

    if (response.Result.Response.StatusCode == HttpStatusCode.OK)
    {
        var stream = response.Result.Response.Content.ReadAsStreamAsync();

        using (FileStream fileStream = File.Create(@"C:\Migration\myfile.pbix"))
        {
            stream.Result.CopyTo(fileStream);
            fileStream.Close();
        }
    }
```

## <a name="import-report-to-saas-workspace"></a>Jelentés importálása SaaS-munkaterületre
```
    AuthenticationContext authContext = new AuthenticationContext("https://login.windows.net/common/oauth2/authorize");
    var PBISaaSAuthResult = authContext.AcquireToken("https://analysis.windows.net/powerbi/api", <myClientId>, new Uri("urn:ietf:wg:oauth:2.0:oob"), PromptBehavior.Always);
    var credentials = new TokenCredentials(PBISaaSAuthResult.AccessToken);
    var client = new PowerBIClient(new Uri($"{"https://api.powerbi.com"}"), credentials);
    using (var file = File.Open(@"C:\Migration\myfile.pbix", FileMode.Open))
    {
        client.Imports.PostImportWithFileInGroup(<mySaaSWorkspaceId>, file, "importedreport", "Abort");
        while (true) ;
    }
```

## <a name="extract-directquery-connection-string-from-paas-report"></a>DirectQuery kapcsolati karakterlánc kinyerése a PaaS-jelentésből
Ez a PBIX frissítéséhez szükséges az SaaS-be való migrálás után.

```
    // Extract connection string from PaaS - DirectQuery report
    // Create a token credentials with "AppKey" type
    var credentials = new TokenCredentials(<myAppKey==>, "AppKey");

    // Instantiate your Power BI client passing in the required credentials
    var client = new PowerBIClient(credentials);

    client.BaseUri = new Uri("https://api.powerbi.com");

    var reports = client.Reports.GetReports(<myWorkspaceCollectionName>, <myWorkspaceId>);

    Report report = reports.Value.FirstOrDefault(r => string.Equals(r.Id, <myReportId, StringComparison.OrdinalIgnoreCase));

    var datasource = client.Datasets.GetDatasources(<myWorkspaceCollectionName>, <myWorkspaceId>, report.DatasetId);
```

## <a name="update-directquery-connection-string-is-saas-workspace"></a>DirectQuery kapcsolati karakterlánc frissítése az SaaS-munkaterületen
```
    public class ConnectionString
    {
        [JsonProperty(PropertyName = "connectionString")]
        public string connection { get; set; }
    }

    AuthenticationContext authContext = new AuthenticationContext("https://login.windows.net/common/oauth2/authorize");
    var PBISaaSAuthResult = authContext.AcquireToken("https://analysis.windows.net/powerbi/api",<myclient_id>, new Uri("urn:ietf:wg:oauth:2.0:oob"), PromptBehavior.Always);
    var credentials = new TokenCredentials(PBISaaSAuthResult.AccessToken);
    var client = new PowerBIClient(new Uri($"{"https://api.powerbi.com"}"), credentials);

    ConnectionString connection = new ConnectionString() { connection = "data source = <server_name>; initial catalog = <db_name>; persist security info = True; encrypt = True; trustservercertificate = False" };

    client.Datasets.SetAllConnectionsInGroup(<myWorkspaceId>, <dataset_id>, connection);
```

## <a name="set-directquery-credentials-in-saas-workspace"></a>DirectQuery hitelesítő adatok beállítása az SaaS-munkaterületen
Ebben a kódrészletben az egyszerűség kedvéért nem titkosított hitelesítő adatokat használunk, de a titkosított adatok használata is támogatott.

```
    public class ConnectionString
    {
        [JsonProperty(PropertyName = "connectionString")]
        public string connection { get; set; }
    }

    public class BasicCreds
    {
        [JsonProperty(PropertyName = "username")]
        public string user { get; set; }

        [JsonProperty(PropertyName = "password")]
        public string pwd { get; set; }
    }

    var basicCreds = new BasicCreds() { user = <sqldb_username>, pwd = <sqldb_password> };
    var body = new SetCredsRequestBody() { credentialType = "Basic", basicCredentials = basicCreds };

    var url = string.Format("https://api.powerbi.com/v1.0/myorg/gateways/{0}/datasources/{1}", <gateway_id>, <datasource_id>);
    var request = new HttpRequestMessage(new HttpMethod("PATCH"), url);
    // Set authorization header from you acquired Azure AD token
    AuthenticationContext authContext = new AuthenticationContext("https://login.windows.net/common/oauth2/authorize");
    var PBISaaSAuthResult = authContext.AcquireToken("https://analysis.windows.net/powerbi/api", <myclient_id>, new Uri("urn:ietf:wg:oauth:2.0:oob"), PromptBehavior.Always);

    request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", PBISaaSAuthResult.AccessToken);

    request.Content = new StringContent(JsonConvert.SerializeObject(body), Encoding.UTF8, "application/json");

    HttpClient simpleClient = new HttpClient();
    var response = await simpleClient.SendAsync(request);
```

## <a name="push-dataset--report"></a>Adatkészlet leküldése és jelentés
Újra össze kell állítania a jelentést a létrehozott adatkészlethez.

Ebben a kódrészletben feltételezzük, hogy a leküldhető adatkészlet már az SaaS-környezet egyik alkalmazás-munkaterületén van. További információ a leküldési API-ról: [Adatok leküldése Power BI-adatkészletekbe](walkthrough-push-data.md).

```
    var credentials = new TokenCredentials(<Your WSC access key>, "AppKey");

    // Instantiate your Power BI client passing in the required credentials
    var client = new Microsoft.PowerBI.Api.V1.PowerBIClient(credentials);
    client.BaseUri = new Uri("https://api.powerbi.com");

    // step 1 -> create dummy dataset at PaaS worksapce
    var fileStream = File.OpenRead(<Path to your dummy dataset>);
    var import = client.Imports.PostImportWithFileAsync(<Your WSC NAME>, <Your workspace ID>, fileStream, "dummyDataset");
    while (import.Result.ImportState != "Succeeded" && import.Result.ImportState != "Failed")
    {
        import = client.Imports.GetImportByIdAsync(<Your WSC NAME>, <Your workspace ID>, import.Result.Id);
        Thread.Sleep(1000);
    }
    var dummyDatasetID = import.Result.Datasets[0].Id;

    // step 2 -> clone the pushable dataset and rebind to dummy dataset
    var cloneInfo = new Microsoft.PowerBI.Api.V1.Models.CloneReportRequest("pushableReportClone",null, dummyDatasetID);
    var clone = client.Reports.CloneReportAsync(<Your WSC NAME>, <Your workspace ID>, <Your pushable report ID>, cloneInfo);
    var pushableReportCloneID = clone.Result.Id;


    // step 3 -> Download the push API clone report with the dummy dataset
    var response = client.Reports.ExportReportWithHttpMessagesAsync(<Your WSC NAME>, <Your workspace ID>, pushableReportCloneID);
    if (response.Result.Response.StatusCode == HttpStatusCode.OK)
    {
        var stream = response.Result.Response.Content.ReadAsStreamAsync();
        using (fileStream = File.Create(@"C:\Migration\PushAPIReport.pbix"))
        {
            stream.Result.CopyTo(fileStream);
            fileStream.Close();
        }
    }

    // step 4 -> Upload dummy PBIX to SaaS workspace
    AuthenticationContext authContext = new AuthenticationContext("https://login.windows.net/common/oauth2/authorize");
    var PBISaaSAuthResult = authContext.AcquireToken("https://analysis.windows.net/powerbi/api", <Your client ID>, new Uri("urn:ietf:wg:oauth:2.0:oob"), PromptBehavior.Always);
    var credentialsSaaS = new TokenCredentials(PBISaaSAuthResult.AccessToken);
    var clientSaaS = new Microsoft.PowerBI.Api.V2.PowerBIClient(new Uri($"{"https://api.powerbi.com"}"), credentialsSaaS);
    using (var file = File.Open(@"C:\Migration\PushAPIReport.pbix", FileMode.Open))
    {

        var importSaaS = clientSaaS.Imports.PostImportWithFileAsyncInGroup(<Your GroupID>, file, "importedreport1", "Abort");
        while (importSaaS.Result.ImportState != "Succeeded" && importSaaS.Result.ImportState != "Failed")
        {
            importSaaS = clientSaaS.Imports.GetImportByIdAsync(importSaaS.Result.Id);
            Thread.Sleep(1000);
        }
        var importedreport1ID = importSaaS.Result.Reports[0].Id;


        // step 5 -> Rebind report to "real" push api dataset
        var rebindInfoSaaS = new Microsoft.PowerBI.Api.V2.Models.RebindReportRequest(<Your pushable dataset  ID at power bi>);
        var rebindSaaS = clientSaaS.Reports.RebindReportInGroupWithHttpMessagesAsync(<Your GroupID>, importedreport1ID, rebindInfoSaaS);

    }
```

## <a name="next-steps"></a>További lépések
[Power BI Embedded migrálási eszköz](migrate-tool.md)  
[Beágyazás a Power BI-jal](embedding.md)  
[Power BI Embedded munkaterület-csoport tartalmainak migrálása a Power BI-ba](migrate-from-powerbi-embedded.md)  
[Power BI-irányítópultok, -jelentések és -csempék beágyazása](embedding-content.md)  
[Power BI Premium – pontosan mi is ez?](../service-premium.md)  
[JavaScript API Git-adattár](https://github.com/Microsoft/PowerBI-JavaScript)  
[Power BI C# Git-adattár](https://github.com/Microsoft/PowerBI-CSharp)  
[JavaScript beágyazási minta](https://microsoft.github.io/PowerBI-JavaScript/demo/)  
[Power BI Premium-tanulmány](https://aka.ms/pbipremiumwhitepaper)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

