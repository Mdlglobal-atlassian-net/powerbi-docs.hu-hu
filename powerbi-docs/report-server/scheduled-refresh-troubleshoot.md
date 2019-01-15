---
title: Ütemezett frissítések hibaelhárítása a Power BI jelentéskészítő kiszolgálón
description: Ez a cikk a Power BI jelentéskészítő kiszolgáló ütemezett frissítéseivel kapcsolatos hibák elhárításához rendelkezésre álló forrásokat ismerteti.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/01/2017
ms.author: maghan
ms.openlocfilehash: 3aa4047f5a4b0146c534a5734d8d13a42c46fe58
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54287807"
---
# <a name="troubleshoot-scheduled-refresh-in-power-bi-report-server"></a>Ütemezett frissítések hibaelhárítása a Power BI jelentéskészítő kiszolgálón
Ez a cikk a Power BI jelentéskészítő kiszolgáló ütemezett frissítéseivel kapcsolatos hibák elhárításához rendelkezésre álló forrásokat ismerteti.

Újabb problémák megjelenésekor ez a cikk további segítséget nyújtó információkkal fog bővülni.

## <a name="common-issues"></a>Gyakori problémák
Az alábbiak a jelentések frissítésének ütemezésekor fellépő leggyakoribb hibák. 

### <a name="driver-related-problems"></a>Illesztőprogrammal kapcsolatos problémák
A különböző adatforrásokhoz való kapcsolódáshoz szükség lehet külső gyártótól származó illesztőprogramokra, melyeket a sikeres kapcsolódáshoz telepíteni kell. Ezeket nem csak arra a gépre kell telepíteni, amelyen a Power BI Desktopot használja. Arról is gondoskodnia kell, hogy az illesztőprogram telepítve legyen a jelentéskészítő kiszolgálón.

Az illesztőprogramnak 32 bites és 64 bites verziója is lehet. Mindenképpen a 64 bites illesztőprogramot telepítse, hiszen a Power BI jelentéskészítő kiszolgáló 64 bites.

A külső gyártótól származó illesztőprogramok telepítésével és konfigurálásával kapcsolatban tájékozódjon a gyártónál.

### <a name="memory-pressure"></a>Memóriaterhelés
Memóriaprobléma fordulhat elő, ha a jelentések feldolgozása és megjelenítése több memóriát igényel. A jelentések ütemezett frissítése jelentős memóriaterhelést ró a gépre. Ez fokozottan így van a nagyobb jelentések esetén. A memóriaterhelés a jelentéskészítés sikertelenségét és akár a jelentéskészítő kiszolgáló összeomlását is okozhatja.

Ha rendszeresen tapasztal memóriaterhelés miatti hibát, akkor érdemes lehet megfontolni a jelentéskészítő kiszolgáló bővítő telepítését az erőforrás-terhelések elosztása érdekében. Az rsreportserver.config fájlban található `IsDataModelRefreshService` beállítással az is megadható, hogy egy adott jelentéskészítő kiszolgáló részt vesz-e az adatfrissítésben. Ezzel a beállítással megadhat egy vagy több előtér-kiszolgálót, amelyek a jelentések igény szerinti kezelését végzik, míg más kiszolgálókat csak az ütemezett frissítésekhez használ.

Az Analysis Services-példányok figyeléséről az [Analysis Services-példány figyelése](https://docs.microsoft.com/sql/analysis-services/instances/monitor-an-analysis-services-instance) című cikk nyújt tájékoztatást.

Az Analysis Servicesen belüli memóriabeállításokról a [Memóriatulajdonságok](https://docs.microsoft.com/sql/analysis-services/server-properties/memory-properties) című cikkben olvashat.

### <a name="kerberos-configuration"></a>Kerberos-konfiguráció
Ha egy adatforráshoz Windows hitelesítő adatokkal kíván kapcsolódni, akkor a sikeres kapcsolódáshoz korlátozott Kerberos-delegálás konfigurálására lehet szükség. A korlátozott Kerberos-delegálás konfigurálásáról az [A Kerberos konfigurálása Power BI-jelentések használatára](configure-kerberos-powerbi-reports.md) című cikk nyújt bővebb tájékoztatást.

## <a name="known-issues"></a>Ismert problémák
Itt lesznek felsorolva az ismert problémákkal kapcsolatos információk, ha elérhetővé válnak.

## <a name="configuration-settings"></a>Konfigurációs beállítások
Az ütemezett frissítéseket érintő beállítások a következők. Az SQL Server Management Studión (SSMS) belüli beállítások egy bővítő telepítés valamennyi jelentéskészítő kiszolgálójára vonatkoznak. Az rsreportserver.config fájlban konfigurált beállítások csak az adott kiszolgálóra érvényesek.

**Beállítások az SSMS-ban:**

| Beállítás | Leírás |
| --- | --- |
| MaxFileSizeMb |Feltöltött jelentések maximális fájlmérete. Alapértelmezett értéke 1000 MB (1 GB). Maximális értéke 2000 MB (2 GB). |
| ModelCleanupCycleMinutes |A modell memóriából való kizárásának ellenőrzési gyakoriságát adja meg. Alapértelmezett értéke 15 perc. |
| ModelExpirationMinutes |Megadja, hogy mennyi idő után jár le és záródik ki a modell az utolsó használat időpontja után. Alapértelmezett értéke 60 perc. |
| ScheduleRefreshTimeoutMinutes |Megadja, hogy mennyi ideig tarthat egy modell adatfrissítése. Alapértelmezett értéke 120 perc. Felső korlátja nincs. |

**Beállítások az rsreportserver.config fájlban:**

```
<Configuration>
    <Service>
        <PollingInterval>10</PollingInterval>
        <IsDataModelRefreshService>false</IsDataModelRefreshService>
        <MaxQueueThreads>0</MaxQueueThreads>
    </Service>
</Configuration>
```

## <a name="tools-for-troubleshooting"></a>Hibaelhárítási eszközök
### <a name="logs-relevant-for-scheduled-refresh-of-power-bi-reports"></a>Power BI-jelentések ütemezett frissítéseire vonatkozó naplók
Az ütemezett frissítéssel kapcsolatban az RSPowerBI_ naplófájlok tartalmaznak információt. A jelentéskészítő kiszolgáló telepítési helyének LogFiles mappájában találhatók. 

```
C:\Program Files\Microsoft Power BI Report Server\PBIRS\LogFiles\RSPowerBI_*.log
```

**Hibaállapot**

```
2017-10-20 02:00:09.5188|ERROR|744|Error Processing Data Model Refresh: SessionId: e960c25e-ddd4-4763-aa78-0e5dceb53472, Status: Error Model can not be refreshed because not all the data sources are embedded, Exception Microsoft.PowerBI.ReportServer.AsServer.InvalidDataSourceException: Model can not be refreshed because not all the data sources are embedde
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.CanModelRefresh(IEnumerable`1 dataSources)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
```

***Sikeres frissítés***

```
2017-10-25 15:23:41.9370|INFO|6|Handling event with data: TimeEntered: 10/25/2017 8:23:41 PM, Type: Event, SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, EventType: DataModelRefresh
2017-10-25 15:23:41.9370|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Data Refresh.
2017-10-25 15:23:41.9370|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Retrieving PBIX AsDatabaseInfo.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Verifying all the data sources are embedded.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Verifying connection strings are valid.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Streaming model to Analysis Server.
2017-10-25 15:23:42.7603|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Refreshing the model.
2017-10-25 15:23:51.5258|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Removing credentials from the model.
2017-10-25 15:23:51.6508|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Saving model to the catalog.
```

**Helytelen hitelesítő adatok**

```
2017-10-20 08:22:01.5595|INFO|302|Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Starting Refreshing the model.
2017-10-20 08:22:02.3758|ERROR|302|Error Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Error Failed to refresh the model, Exception Microsoft.AnalysisServices.OperationException: Failed to save modifications to the server. Error returned: 'The credentials provided for the SQL source are invalid. (Source at rosecatalog;reportserver.). The exception was raised by the IDbCommand interface.
'.
   at Microsoft.AnalysisServices.Tabular.Model.SaveChanges(SaveOptions saveOptions)
   at Microsoft.PowerBI.ReportServer.AsServer.TOMWrapper.RefreshModel(Database database)
   at Microsoft.PowerBI.ReportServer.AsServer.AnalysisServicesServer.RefreshDatabase(String databaseName, IEnumerable`1 dataSources)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.RefreshDatabase(AsDatabaseInfo asDatabaseInfo)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
2017-10-20 08:22:02.4588|ERROR|302|Error Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Error Failed Data Refresh, Exception Microsoft.AnalysisServices.OperationException: Failed to save modifications to the server. Error returned: 'The credentials provided for the SQL source are invalid. (Source at rosecatalog;reportserver.). The exception was raised by the IDbCommand interface.
'.
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.ExecuteActionWithLogging(Action methodToExecute, String description, String localizedDescription, String messageInFailure, RefreshInfo refreshInfo, DataAccessors dataAccessors, ReportEventType operation, Int64 size, Boolean isDataRetrieval, Boolean showInExecutionLog)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.RefreshData(RefreshInfo refreshInfo)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
```

#### <a name="enabling-verbose-logging"></a>Részletes naplózás engedélyezése
A részletes naplózás ugyanúgy engedélyezhető a Power BI jelentéskészítő kiszolgálón, ahogyan az SQL Server Reporting Servicesben.

1. Nyissa meg a következő fájlt: `<install directory>\PBIRS\ReportServer\bin\ReportingServicesService.exe.config`.
2. A `<system.diagnostics>` alatt állítsa át a **DefaultTraceSwitch** értékét **4**-re.
3. A `<RStrace>` alatt állítsa át a **Components** értékét **all:4**-ra. 

### <a name="executionlog"></a>ExecutionLog (Végrehajtási napló)
Power BI-jelentés készítésekor vagy ütemezett frissítési terv végrehajtásakor új bejegyzések kerülnek az adatbázis végrehajtási naplójába. Ezek a bejegyzések a jelentéskészítési kiszolgáló katalógus-adatbázisában érhetők el az **ExecutionLog3** nézetben.

A Power BI-jelentések végrehajtásinapló-bejegyzései eltérnek más jelentéstípusokéitól.

* A TimeRendering oszlopok tartalma mindig 0. A Power BI-jelentések összeállítása nem a kiszolgálón, hanem a böngészőben történik.
* Két kérelemtípus létezik, a hozzájuk tartozó elemműveletekkel:
  * **Interactive**: egy jelentés megtekintésekor.
    * **ASModelStream**: az adatmodell adatfolyamként történő továbbításakor a katalógusból az Analysis Services felé.
    * **ConceptualSchema**: amikor egy felhasználó a jelentés megtekintésére kattint.
    * **QueryData**: adatoknak az ügyféltől való lekérésekor.
  * **Refresh Cache**: ütemezett frissítési terv végrehajtásakor.
    * **ASModelStream**: az adatmodell adatfolyamként történő továbbításakor a katalógusból az Analysis Services felé.
    * **DataRefresh**: adatoknak egy vagy több adatforrásból történő frissítésekor.
    * **SaveToCatalog**: adatmodellnek a katalógusba történő visszamentésekor.

## <a name="analysis-services"></a>Analysis Services
Előfordulhat, hogy diagnosztikai céllal vagy a memóriakorlátok átállítása miatt módosítani szeretné az Analysis Servicest.

> [!IMPORTANT]
> Ezek a beállítások a jelentéskészítő kiszolgáló minden frissítésekor alaphelyzetbe állnak. Gondoskodjon a módosítások egy másolatának megőrzéséről, hogy szükség esetén megismételhesse őket.
> 
> 

### <a name="install-location"></a>Telepítési hely
A Power BI jelentéskészítő kiszolgáló és az Analysis Services alapértelmezett helye a következő.

`C:\Program Files\Microsoft Power BI Report Server\PBIRS\ASEngine`

### <a name="configuring-analysis-services-settings-msmdsrvini"></a>Az Analysis Services beállításainak konfigurálása (msmdsrv.ini)
A `<install directory>\PBIRS\ASEngine` mappában találja a *msmdsrv.ini* fájlt, amellyel az Analysis Services különböző beállításait tudja kezelni. Ezt a fájlt megnyitva azonnal látni fogja, hogy nincs meg benne minden beállítás, amelyeket az msmdsrv.ini fájlban várna. 

Ennek az az oka, hogy a Power BI jelentéskészítő kiszolgáló által futtatott tényleges Analysis Services-folyamat a `<install directory>\PBIRS\ASEngine\workspaces` helyről indul. Ebben a mappában a teljes *msmdsrv.ini* fájlt találja, amelyet megszokott. Fontos, hogy a munkaterület mappájában lévő fájlt ne módosítsa, mert az az Analysis Services-folyamat indulásakor mindig újraíródik. Ha módosítani kíván egy beállítást, akkor ezt a `<install directory>\PBIRS\ASEngine` mappában lévő msmdsrv.ini módosításával tegye.

Az Analysis Services-folyamat indulásakor a következő beállítások mindig alaphelyzetbe állnak. Az ezeken végzett módosítások hatástalanok.

* ConfigurationSettings\PrivateProcess
* ConfigurationSettings\DataDir
* ConfigurationSettings\LogDir
* ConfigurationSettings\TempDir
* ConfigurationSettings\BackupDir
* ConfigurationSettings\AllowedBrowsingFolders
* ConfigurationSettings\CrashReportsFolder
* ConfigurationSettings\ExtensionDir
* ConfigurationSettings\Port
* ConfigurationSettings\DeploymentMode
* ConfigurationSettings\ServerLocation
* ConfigurationSettings\TMCompatabilitySKU
* ConfigurationSettings\FlightRecorder\TraceDefinitionFile

### <a name="profiling-the-local-analysis-services-process"></a>Profilkészítés a helyi Analysis Services-folyamatról
Diagnosztikai céllal SQL Profiler nyomkövetést indíthat a helyi Analysis Services-folyamatra. A helyi Analysis Services-példányhoz való kapcsolódás menete a következő.

[SQL Server Management Studio (SSMS) letöltéséhez](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) az SQL Server Profiler Trace is hozzátartozik.

1. Indítsa el az **SQL Server Profilert** rendszergazdaként.
2. Válassza az **Új nyomkövetés** gombot.
3. A **Kapcsolódás kiszolgálóhoz** párbeszédablakban válassza az **Analysis Services** elemet majd a kiszolgáló neveként adja meg a következőt: **localhost:5132**.
4. A **Nyomkövetés tulajdonságai** párbeszédablakban jelölje ki rögzíteni kívánt eseményeket, majd válassza a **Futtatás** lehetőséget.

## <a name="lock-pages-in-memory-windows-privilege"></a>Memórialapok zárolása Windows-jogosultság
Ha azt tapasztalja, hogy nem tud Power BI jelentéseket készíteni, akkor segíthet a **Memórialapok zárolása** jogosultság megadása a Power BI jelentéskészítő kiszolgáló szolgáltatásfiókjának. A **Memórialapok zárolása** konfigurálásáról további információt talál az [Analysis Services-szolgáltatásfióknak adott Windows-jogosultságok](https://docs.microsoft.com/sql/analysis-services/instances/configure-service-accounts-analysis-services#bkmk_winpriv) témakörben.

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

