---
title: Diagnosztikai naplózás a Power BI Embedded szolgáltatáshoz az Azure-ban | Microsoft Docs
description: A cikk azt ismerteti, hogyan állítható be a diagnosztikai naplózás a Power BI Embedded szolgáltatáshoz az Azure-ban.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: power-bi-embedded
ms.topic: conceptual
ms.date: 08/13/2018
ms.openlocfilehash: 362c765fb5e739563b8d21eaed53304eddce8acc
ms.sourcegitcommit: c395fe83d63641e0fbd7c98e51bbab224805bbcc
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74265708"
---
# <a name="diagnostic-logging-for-power-bi-embedded-in-azure"></a>Diagnosztikai naplózás a Power BI Embedded szolgáltatáshoz az Azure-ban

Az [Azure-erőforrások diagnosztikai naplóinak](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-of-diagnostic-logs) használatával a kapacitást érintő számos esemény naplózható, és ha ezeket egy elemző eszközbe tölti be, információt kaphat az erőforrás viselkedéséről.

A diagnosztika több különféle helyzetben is használható, például:

* Hosszan futó vagy hibás lekérdezések felismerése.
* [Kapacitásmetrikák](https://powerbi.microsoft.com/blog/power-bi-developer-community-april-update/) származtatása.
* Meghatározott adatkészletek használatának nyomon követése.

## <a name="set-up-diagnostics-logging"></a>Diagnosztikai naplózás beállítása

### <a name="azure-portal"></a>Azure Portal

1. Az [Azure Portal](https://portal.azure.com) > Power BI Embedded erőforrásának területén válassza a **Diagnosztikai naplók** lehetőséget a navigációs menüben, majd válassza a **Diagnosztika bekapcsolása** elemet.

    ![Diagnosztikai naplózás bekapcsolása a Power BI Embedded szolgáltatáshoz az Azure Portalon](media/azure-pbie-diag-logs/azure-pbie-diag-logs-01.png)

2. A **diagnosztikai beállítások** területen adja meg a következő beállításokat:

    * **Név** – adjon meg egy nevet a létrehozandó diagnosztikai beállításhoz.

    * **Archiválás tárfiókba** – ennek a beállításnak a használatához csatlakoznia kell egy meglévő tárfiókhoz. Tárfiók létrehozásához kövesse a [Tárfiók létrehozása](https://docs.microsoft.com/azure/storage/common/storage-create-storage-account) című témakörben található lépéseket. Ezt követően térjen vissza erre az oldalra a Portalon, és válassza ki a tárfiókot. Néhány percet igénybe vehet, hogy az újonnan létrehozott tárfiók megjelenjen a legördülő menüben. A naplófájl JSON-formátumban van tárolva.
    * **Streamelés eseményközpontba** – Ennek a lehetőségnek a használatához csatlakoznia kell egy meglévő Event Hubs-névtérhez és egy eseményközponthoz. További információt az [Event Hubs-névtér és eseményközpont létrehozása az Azure Portal használatával](https://docs.microsoft.com/azure/event-hubs/event-hubs-create) című témakörben talál.
    * **Küldés a Log Analyticsnek** – ennek a beállításnak a használatához vagy egy meglévő munkaterületet kell használnia, vagy létre kell hoznia egy új Log Analytics-munkaterületet a Portalon az [új munkaterületet létrehozását](https://docs.microsoft.com/azure/log-analytics/log-analytics-quick-collect-azurevm#create-a-workspace) ismertető útmutatót követve. Ez az [Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) szolgáltatást használja, amely beépítetten tartalmaz elemzési és értesítési képességeket, valamint irányítópultot. A Log Analytics használatával más erőforrásokból származó további adatokhoz is csatlakozhat, és egyetlen helyen tekintheti át az alkalmazás összes erőforrására vonatkozó adatokat teljes egészében. Ezen kívül [egyetlen kattintással csatlakoztatható a Power BI-hoz](https://docs.microsoft.com/azure/log-analytics/log-analytics-powerbi) is.
    A [Naplók megtekintése a Log Analyticsben](https://docs.microsoft.com/azure/log-analytics/log-analytics-activity) című témakörben további információt talál a naplók megtekintéséről.
    * **Motor** – ezzel a beállítással naplózhatja a motor [alább felsorolt eseményeit](#whats-logged).
    * **AllMetrics** – ezzel a beállítással részletes adatokat tárolhat a [Metrikákban](https://docs.microsoft.com/azure/analysis-services/analysis-services-monitor#server-metrics). Ha tárfiókba archivál, kiválaszthatja a diagnosztikai naplók megőrzési időtartamát. A megőrzési időszak lejárta után a naplókat automatikusan törli a rendszer.

3. Kattintson a **Mentés** gombra.

    A diagnosztikai naplók mentési módját ezen az oldalon változtathatja meg a beállításokban.

    ![Diagnosztikai beállítások](media/azure-pbie-diag-logs/diag-settings.png)

### <a name="using-powershell-to-enable-diagnostics"></a>Diagnosztika engedélyezése a PowerShell használatával

PowerShell használatával a diagnosztikát és a metrikákat az alábbi parancsok segítségével engedélyezheti:

* Az alábbi paranccsal engedélyezheti a diagnosztikai naplók tárfiókban való tárolását:

    ```powershell
    Set-AzureRmDiagnosticSetting -ResourceId [your resource id] -StorageAccountId [your storage account id] -Enabled $true
    ```
    A Storage-fiók azonosítója (storage account ID) annak a tárfióknak az erőforrás-azonosítója, amelybe a naplókat szeretné küldeni.

* Az alábbi parancs használatával engedélyezheti a diagnosztikai naplók streamelését egy eseményközpontba:

    ```powershell
    Set-AzureRmDiagnosticSetting -ResourceId [your resource id] -ServiceBusRuleId [your service bus rule id] -Enabled $true
    ```
* Az Azure Service Bus szabályazonosítója (rule ID) egy sztring az alábbi formátumban:

    ```powershell
    {service bus resource ID}/authorizationrules/{key name}
    ```

* Az alábbi paranccsal engedélyezheti a diagnosztikai naplók Log Analytics-munkaterületre való küldését:

    ```powershell
        Set-AzureRmDiagnosticSetting -ResourceId [your resource id] -WorkspaceId [resource id of the log analytics workspace] -Enabled $true
    ```

* A Log Analytics-munkaterület erőforrás-azonosítóját (ResourceId) az alábbi paranccsal kérheti le:

    ```powershell
    (Get-AzureRmOperationalInsightsWorkspace).ResourceId
    ```

Ezeket a paramétereket kombinálhatja is, ha több kimeneti eredményt szeretne kapni.

### <a name="rest-api"></a>REST API

Ismerje meg, [hogyan módosíthatja a diagnosztikai beállításokat az Azure Monitor REST API használatával](https://docs.microsoft.com/rest/api/monitor/). 

### <a name="resource-manager-template"></a>Resource Manager-sablon

Ismerje meg, [hogyan engedélyezheti a diagnosztikai beállításokat az erőforrás létrehozásánál a Resource Manager-sablon használatával](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-enable-diagnostic-logs-using-template).

## <a name="whats-logged"></a>Mi kerül naplózásra?

Választhatja a **motor** és/vagy az **AllMetrics** (minden metrika) kategóriát.

### <a name="engine"></a>Motor

A Motor kategória választása esetén az erőforrás az alábbi eseményeket naplózza, és mindegyik eseményhez tulajdonságok tartoznak:

|     Esemény neve     |     Esemény leírása     |
|----------------------------|----------------------------------------------------------------------------------|
|    Naplózás bejelentkezése    |    A nyomkövetés kezdetétől a motorhoz való összes új csatlakozási eseményt naplózza.    |
|    A munkamenet inicializálása    |    A nyomkövetés kezdetétől az összes munkamenet-inicializálási eseményt naplózza.    |
|    Vertipaq-lekérdezés kezdete    |    A nyomkövetés kezdetétől minden VertiPaq SE-lekérdezés kezdete eseményt rögzít.    |
|    Lekérdezés kezdete    |    A nyomkövetés kezdetétől minden lekérdezés kezdete eseményt rögzít.    |
|    Lekérdezés vége    |    A nyomkövetés kezdetétől minden lekérdezés vége eseményt rögzít.    |
|    Vertipaq-lekérdezés vége    |    A nyomkövetés kezdetétől minden VertiPaq SE-lekérdezés vége eseményt rögzít.    |
|    Naplózás kijelentkezés    |    A nyomkövetés kezdetétől minden motorkapcsolat bontása eseményt naplóz.    |
|    Hiba    |    A nyomkövetés kezdetétől minden motorhiba eseményt naplóz.    |

<br>
<br>

| Tulajdonság neve | Vertipaq-lekérdezés vége példa | Tulajdonságleírás |
|-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|
| EventClass | XM_SEQUERY_END | Az Eseményosztály (EventClass) az események kategóriákba sorolására szolgál. |
| EventSubclass | 0 | Az eseményalosztály további információt biztosít az egyes eseményosztályokról. (például 0: VertiPaq Scan) |
| RootActivityId | ff217fd2-611d-43c0-9c12-19e202a94f70 | Legfelsőbb szintű tevékenység azonosítója. |
| CurrentTime | 2018-04-06T18:30:11.9137358Z | Az esemény kezdetének ideje, ha elérhető. |
| StartTime | 2018-04-06T18:30:11.9137358Z | Az esemény kezdetének ideje, ha elérhető. |
| JobID | 0 | A folyamat feladatazonosítója. |
| ObjectID | 464 | Objektumazonosító |
| ObjectType | 802012 | ObjectType |
| EndTime | 2018-04-06T18:30:11.9137358Z | Az esemény befejezésének ideje. |
| Időtartam | 0 | Az esemény időtartama (ezredmásodpercben). |
| SessionType | Felhasználó | Munkamenet típusa (milyen entitás indította a műveletet). |
| ProgressTotal | 0 | Teljes előrehaladás. |
| IntegerData | 0 | Egész típusú adatok. |
| Severity | 0 | Egy kivétel súlyossági szintje. |
| Siker | 1 | 1 = sikeres. 0 = sikertelen (például engedélyek ellenőrzésekor az 1 azt jelenti, hogy a művelet sikeres volt, a 0 pedig azt, hogy sikertelen). |
| Hiba | 0 | Az adott esemény hibaszáma. |
| ConnectionID | 3 | Egyedi kapcsolatazonosító. |
| DatasetID | 5eaa550e-06ac-4adf-aba9-dbf0e8fd1527 | Annak az adatkészletnek az azonosítója, amelyben a felhasználó utasítása fut. |
| SessionID | 3D063F66-A111-48EE-B960-141DEBDA8951 | A munkamenet GUID-azonosítója. |
| SPID | 180 | A kiszolgálói folyamat azonosítója. Ez egyedileg azonosít egy felhasználói munkamenetet. Ez közvetlenül megfelel az XML/A által használt munkamenet GUID-azonosítónak. |
| ClientProcessID | null | Az ügyfélalkalmazás folyamatazonosítója. |
| ApplicationName | null | Annak az ügyfélalkalmazásnak a neve, amely a kiszolgálóhoz való csatlakozást létrehozta. |
| CapacityName | pbi641fb41260f84aa2b778a85891ae2d97 | A Power BI Embedded-kapacitás erőforrásának neve. |


### <a name="allmetrics"></a>AllMetrics

Az **AllMetrics** lehetőség választásával minden olyan metrikának az adatait naplózza a rendszer, amely a Power BI Embedded-erőforrással használható.

   ![Metrikák megjelenítése](media/azure-pbie-diag-logs/azure-pbie-diag-logs-02.png)

## <a name="manage-your-logs"></a>Naplók kezelése

A naplók általában a naplózás beállítását követő néhány órán belül elérhetőek. A naplókat a tárfiókban kezelheti:

* A standard Azure-beli hozzáférés-vezérlési módszerekkel szabályozhatja, hogy kik férhetnek hozzá a naplókhoz.
* Ha már nincs szüksége a tárfiókban tárolt naplókra, törölje azokat.
* Fontos, hogy megőrzési időtartamot is beállítson, így a régi naplókat törli a rendszer a tárfiókból.

## <a name="view-logs-in-log-analytics"></a>Naplók megtekintése a Log Analyticsben

A Log Analyticsben a metrikák és a kiszolgálóesemények integrálva vannak az xEvent típusú eseményekkel az egymás melletti elemzés érdekében. A Log Analytics úgy is konfigurálható, hogy más Azure-szolgáltatásokból is fogadjon eseményeket, így átfogó képet kaphat a diagnosztikai naplózás révén a teljes architektúráról.

A diagnosztikai adatok megtekintéséhez a Log Analyticsben nyissa meg a **Naplók** oldalt a bal oldali menüben vagy a felügyeleti területen, ahogy az alábbi képen látható.

![Log Analytics-oldal](media/azure-pbie-diag-logs/azure-pbie-diag-logs-analytics.png)

Miután engedélyezte az adatgyűjtést, a **Naplók** területen válassza **Az összes gyűjtött adat** lehetőséget.

![Az összes gyűjtött adat](media/azure-pbie-diag-logs/azure-pbie-diag-logs-analytics-all-collected-data.png)

A **Típus** alatt válassza az **AzureDiagnostics**, majd az **Alkalmaz** lehetőséget. Az AzureDiagnostics motoreseményeket tartalmaz. Figyelje meg, hogy a Log Analytics-lekérdezés működés közben jön létre.

![Azure Diagnostics](media/azure-pbie-diag-logs/azure-pbie-diag-logs-analytics-azure-diagnostics.png)

Válassza az **EventClass\_s** lehetőséget vagy az egyik eseménynevet, a Log Analytics pedig folytatja a lekérdezés létrehozását. A lekérdezéseket ajánlatos menteni későbbi használatra.

Javasoljuk a [Log Analytics](https://docs.microsoft.com/azure/log-analytics/) felkeresését, amely bővített lekérdezést, irányítópultot és az összegyűjtött adatokhoz kapcsolódó riasztási funkciókat kínáló webhelyet tartalmaz.

### <a name="queries"></a>Lekérdezések

Több száz lekérdezést használhat. Az alábbiakban bemutatunk néhányat az első lépésekhez. A [Naplókeresések a Log Analyticsben](https://docs.microsoft.com/azure/log-analytics/log-analytics-log-search) című témakörben további információt talál a Naplókeresési lekérdezőnyelvről.

* Kevesebb mint 5 percig (300.000 ezredmásodpercig) futó lekérdezés visszatérése.

    ```
    search *
    | where Type == "AzureDiagnostics"
    | where ( OperationName == "QueryEnd" )
    | where toint(Duration_s) < 300000
    ```

    ![Időtartam-lekérdezés eredményei](media/azure-pbie-diag-logs/azure-pbie-diag-logs-analytics-duration-query.png)

* Kapacitásnevek azonosítása.

    ```
    search *
    | where ( Type == "AzureDiagnostics" )
    | summarize count() by CapacityName_s 
    ```

    ![Kapacitásnév-lekérdezés eredményei](media/azure-pbie-diag-logs/azure-pbie-diag-logs-analytics-capacity-name-query.png)

## <a name="next-steps"></a>Következő lépések

További információ az Azure-erőforrások diagnosztikai naplózásáról.

> [!div class="nextstepaction"]
> [Azure-erőforrások diagnosztikai naplózása](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-of-diagnostic-logs)

> [!div class="nextstepaction"]
> [Set-AzureRmDiagnosticSetting](https://docs.microsoft.com/powershell/module/azurerm.insights/Set-AzureRmDiagnosticSetting)
