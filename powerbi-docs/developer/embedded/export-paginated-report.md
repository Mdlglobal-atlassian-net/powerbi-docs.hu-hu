---
title: API Power BI-jelentések exportálásához
description: Útmutató beágyazott többoldalas Power BI-jelentések exportálásához
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 04/05/2020
ms.openlocfilehash: acb13a70ea4693f447b70aa59da07cd91639de25
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "81268765"
---
# <a name="export-paginated-report-to-file-preview"></a>Többoldalas jelentés fájlba exportálása (előzetes verzió)

Az `exportToFile` API lehetővé teszi többoldalas Power BI-jelentések REST-hívással végzett exportálását. A támogatott fájlformátumok a következők:
* **.pptx** (PowerPoint)
* **.pdf**
* **.xlsx** (Excel)
* **.dox** (Word)
* **.csv**
* **.xml**
* **.mhtml**
* **Kép**
    * Képként exportáláskor a képformátum az `OutputFormat` formátumbeállítással adható meg
    * Az OutputFormat támogatott értékei: .bmp, .emf, .gif, .jpeg, .png vagy .tiff (alapértelmezés)

## <a name="usage-examples"></a>Használati példák

Az exportálási funkció többféleképpen is felhasználható. Bemutatunk néhány példát:

* **Küldés nyomtatóra gomb** – Létrehozhat egy gombot az alkalmazásban, amely kattintásra elindít egy exportálási feladatot. A feladat .pdf vagy .pptx formátumban exportálhatja a megtekintett jelentést, és amikor az elkészül, a felhasználó letöltheti a fájlt. Jelentésparaméterek és formátumbeállítások használatával a jelentés egy meghatározott állapotban exportálhatja, beleértve az adatok szűrését, az egyéni oldalméreteket és más formátumbeállításokat is. Mivel az API aszinkron, a fájlok esetleg csak valamivel később lesznek elérhetők.

* **E-mail-melléklet** – Automatikusan e-mailt küldhet a beállított időközökkel, egy ahhoz mellékelt .pdf-jelentéssel. Ez a megoldás hasznos például akkor, ha automatizálni szeretné a vezetőknek küldött heti jelentést.

## <a name="using-the-api"></a>Az API használata

Az API aszinkron. Az [exportToFile](https://docs.microsoft.com/rest/api/power-bi/reports/exporttofile) API a meghívásakor egy exportálási feladatot indít el. Az exportálási feladat elindítása után [ciklikus lekérdezéssel](https://docs.microsoft.com/rest/api/power-bi/reports/getexporttofilestatus) követi nyomon a feladatot annak befejezéséig.

Amikor az exportálás befejeződik, a ciklikus lekérdezést végző API egy [Power BI URL-címet](https://docs.microsoft.com/rest/api/power-bi/reports/getfileofexporttofile) ad vissza a fájl eléréséhez. Az URL-cím 24 órán át érhető el.

## <a name="supported-features"></a>Támogatott funkciók

### <a name="format-settings"></a>Formátumbeállítások

Minden fájlformátumhoz többféle formátumbeállítás adható meg. A támogatott tulajdonságok és értékek a többoldalas jelentés URL-paramétereihez használt [Eszközadat-paraméterek](../../paginated-reports/report-builder-url-parameters.md#report-commands-rdl) megfelelői.

A következő két példa egyike egy jelentés első négy oldalát a jelentés oldalméretét felhasználva .pptx-fájlba exportálja, a másik egy jelentés harmadik oldalát exportálja .jpeg-fájlba.

**Az első négy oldal exportálása .pptx-fájlba**

```json
{
      "format": "PPTX",
      "paginatedReportConfiguration":{
            "formatSettings":{
                  "UseReportPageSize": "true",
                  "StartPage": "1",
                  "EndPage": "4"
            }
      }
}
```

**A harmadik oldal exportálása .jpeg-fájlba**

```json
{
      "format": "IMAGE",
      "paginatedReportConfiguration":{
            "formatSettings":{
                  "OutputFormat": "JPEG",
                  "StartPage": "3",
                  "EndPage": "3"
            }
      }
}
```

### <a name="report-parameters"></a>Jelentésparaméterek

Az `exportToFile` API használatával programozottan exportálhat jelentést a jelentésparaméterek egy halmazával. Ez a [jelentésparaméter](../../paginated-reports/paginated-reports-parameters.md) képességekkel valósítható meg.

Az alábbi példa a jelentésparaméter-értékek beállítását mutatja be.

```json
{
      "format": "PDF",
      "paginatedReportConfiguration":{
            "parameterValues":[
                  {"name": "State", "value": "WA"},
                  {"name": "City", "value": "Seattle"},
                  {"name": "City", "value": "Bellevue"},
                  {"name": "City", "value": "Redmond"}
            ]
      }
}
```

### <a name="authentication"></a>Authentication

A hitelesítést felhasználó (vagy fő felhasználó) vagy egy [egyszerű szolgáltatásnév](embed-service-principal.md) használatával is elvégezheti.

### <a name="row-level-security-rls"></a>Sorszintű biztonság (RLS)

Ha az adatforrás olyan Power BI-adathalmaz, amelyre sorszintű biztonság (RLS) van definiálva, olyan jelentést exportálhat, amelyben csak a bizonyos felhasználók által látható adatok jelennek meg. Ha például regionális szerepkörökkel definiált jelentést exportál, programozottan szűrheti a jelentést úgy, hogy csak egy adott régiót jelenítsen meg.

Az RLS használatával végzett exportáláshoz a jelentés által adatforrásként használt Power BI-adathalmazra vonatkozó olvasási engedéllyel kell rendelkeznie.

Az alábbi példa egy hatályos felhasználónév RLS-hez való megadását mutatja be.

```json
{
      "format": "PDF",
      "paginatedReportConfiguration":{
            "identities": [
                  {"username": "john@contoso.com"}            
            ]
      }
}
```

## <a name="code-examples"></a>Kódpéldák

A példákban használt Power BI API SDK [itt](https://www.nuget.org/packages/Microsoft.PowerBI.Api) tölthető le.

Exportálási feladat létrehozásakor három lépést kell végrehajtania:

1. Exportálási kérés küldése.
2. Ciklikus lekérdezés.
3. A fájl lekérése.

Ez a szakasz erre a három lépésre mutat be példát.

### <a name="step-1---sending-an-export-request"></a>1\. lépés – exportálási kérés küldése

Az első lépés egy exportálási kérés elküldése. Ez a példa egy adott oldaltartományra, méretre és jelentésparaméterekre vonatkozó exportálási kérés elküldését mutatja be.

```csharp
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId)
{
    // For documentation purposes the export configuration is created in this method
    // Ordinarily, it would be created outside and passed in
    var paginatedReportExportConfiguration = new PaginatedReportExportConfiguration()
    {
        FormatSettings = new Dictionary<string, string>()
        {
            {"PageHeight", "14in"},
            {"PageWidth", "8.5in" },
            {"StartPage", "1"},
            {"EndPage", "4"}
        },
        ParameterValues = new List<ParameterValue>()
        {
            { new ParameterValue() {Name = "State", Value = "WA"} },
            { new ParameterValue() {Name = "City", Value = "Redmond"} }
        }
    };

    var exportRequest = new ExportReportRequest
    {
        Format = FileFormat.PDF,
        PaginatedReportExportConfiguration = paginatedReportExportConfiguration,
    };

    var export = await Client.Reports.ExportToFileInGroupAsync(groupId, reportId, exportRequest);

    // Save the export ID, you'll need it for polling and getting the exported file
    return export.Id;
}
```

### <a name="step-2---polling"></a>2\. lépés – ciklikus lekérdezés

Egy exportálási kérés elküldése után ciklikus lekérdezéssel állapíthatja meg, hogy elkészült-e a várt exportált fájl.

```csharp
private async Task<Export> PollExportRequest(
    Guid reportId,
    Guid groupId,
    string exportId /* Get from the ExportToAsync response */,
    int timeOutInMinutes,
    CancellationToken token)
{
    Export exportStatus = null;
    DateTime startTime = DateTime.UtcNow;
    const int secToMillisec = 1000;
    do
    {
        if (DateTime.UtcNow.Subtract(startTime).TotalMinutes > timeOutInMinutes || token.IsCancellationRequested)
        {
            // Error handling for timeout and cancellations
            return null;
        }

        var httpMessage = 
            await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
            
        exportStatus = httpMessage.Body;
        if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
        {
            // The recommended waiting time between polling requests can be found in the RetryAfter header
            // Note that this header is only populated when the status is either Running or NotStarted
            var retryAfter = httpMessage.Response.Headers.RetryAfter;
            var retryAfterInSec = retryAfter.Delta.Value.Seconds;

            await Task.Delay(retryAfterInSec * secToMillisec);
        }
    }
    // While not in a terminal state, keep polling
    while (exportStatus.Status != ExportState.Succeeded && exportStatus.Status != ExportState.Failed);

    return exportStatus;
}
```

### <a name="step-3---getting-the-file"></a>3\. lépés – a fájl lekérése

Ha a ciklikus lekérdezés egy URL-címet ad vissza, a kapott fájlt az alábbi példa alapján kérheti le.

```csharp
private async Task<ExportedFile> GetExportedFile(
    Guid reportId,
    Guid groupId,
    Export export /* Get from the GetExportStatusAsync response */)
{
    if (export.Status == ExportState.Succeeded)
    {
        var httpMessage = 
            await Client.Reports.GetFileOfExportToFileInGroupWithHttpMessagesAsync(groupId, reportId, export.Id);

        return new ExportedFile
        {
            FileStream = httpMessage.Body,
            ReportName = export.ReportName,
            FileExtension = export.ResourceFileExtension,
        };
    }

    return null;
}

public class ExportedFile
{
    public Stream FileStream;
    public string ReportName;
    public string FileExtension;
}
```

### <a name="end-to-end-example"></a>Teljes példa

Ez a példa egy jelentés exportálásának teljes folyamatát mutatja be. A példa tartalmazza a következő szakaszokat:
1. [Az exportálási kérés elküldése](#step-1---sending-an-export-request).
2. [Ciklikus lekérdezés](#step-2---polling).
3. [A fájl lekérése](#step-3---getting-the-file).

```csharp
private async Task<ExportedFile> ExportPaginatedReport(
    Guid reportId,
    Guid groupId,
    int pollingtimeOutInMinutes,
    CancellationToken token)
{
    try
    {
        var exportId = await PostExportRequest(reportId, groupId);

        var export = await PollExportRequest(reportId, groupId, exportId, pollingtimeOutInMinutes, token);
        if (export == null || export.Status != ExportState.Succeeded)
        {
           // Error, failure in exporting the report
            return null;
        }

        return await GetExportedFile(reportId, groupId, export);
    }
    catch
    {
        // Error handling
        throw;
    }
}
```

## <a name="next-steps"></a>További lépések

Tekintse át, hogyan ágyazhat be tartalmat ügyfelei és vállalata számára:

> [!div class="nextstepaction"]
>[Jelentés exportálása fájlba](export-to.md)

> [!div class="nextstepaction"]
>[Beágyazás az ügyfelek számára](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Beágyazás a cég számára](embed-sample-for-your-organization.md)