---
title: Jelentések teljesítményének figyelése a Power BI-ban
description: Útmutató a jelentések teljesítményének Power BI-beli figyeléséhez.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: 9245dd6c25917b2c8c861ea5b83710cd8b52bb22
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83279020"
---
# <a name="monitor-report-performance-in-power-bi"></a>Jelentések teljesítményének figyelése a Power BI-ban

Figyelheti a jelentések Power BI Desktopbeli teljesítményét a [Power BI Premium Metrics alkalmazással](../admin/service-premium-metrics-app.md), kiderítheti, hogy hol vannak a szűk keresztmetszetek, és megtudhatja, hogy miként javítható a jelentések teljesítménye.

Ezekben az esetekben fontos figyelni a teljesítményt:

- Lassú az importálási adatmodell frissítése.
- Lassúak a DirectQuery- vagy az élő kapcsolatot használó jelentések.
- Lassúak a modellszámítások.

A folytatólagos optimalizálás során kiemelt figyelmet igényelnek a lassú lekérdezések (vagy a jelentésekben szereplő vizualizációk).

## <a name="use-query-diagnostics"></a>Lekérdezési diagnosztika használata

A Power BI Desktop [Lekérdezési diagnosztika](/power-query/QueryDiagnostics) funkciójával megállapíthatja, hogy milyen műveleteket végez a Power Query a lekérdezések alkalmazásakor vagy az előzetes eredményeik megjelenítésekor. A _Diagnosztikai lépés_ funkcióval emellett rögzítheti az egyes lekérdezési lépések részletes kiértékelési adatait. Az eredmények megjelennek a Power Queryben, és átalakítások alkalmazásával jobban megértheti a lekérdezések végrehajtását.

> [!NOTE]
> A Lekérdezési diagnosztika egyelőre előzetes funkcióként működik, ezért engedélyeznie kell a _Lehetőségek és beállítások_ lapon. Miután engedélyezte, megjelennek a hozzá tartozó parancsok a Power Query-szerkesztő ablak menüszalagjának **Eszközök** lapján.

![Ezen a képen a Power Query-szerkesztő menüszalagjának Eszközök lapja látható, rajta a Diagnosztikai lépés, a Diagnosztika indítása és a Diagnosztika leállítása gombbal.](media/monitor-report-performance/power-query-diagnotics.png)

## <a name="use-performance-analyzer"></a>A Teljesítményelemző használata

A Power BI Desktop [Teljesítményelemző](../create-reports/desktop-performance-analyzer.md) funkciójával kiderítheti, hogy milyen teljesítményt nyújtanak az egyes jelentéselemek, köztük a vizualizációk és a DAX-képletek. Különösen hasznos annak megállapításához, hogy a lekérdezés vagy a vizualizáció renderelése okoz-e teljesítményproblémákat.

## <a name="use-sql-server-profiler"></a>Az SQL Server Profiler használata

A lassú lekérdezéseket az [SQL Server Profiler](/sql/tools/sql-server-profiler/sql-server-profiler) használatával is azonosíthatja.

> [!NOTE]
> Az SQL Server Profiler az [SQL Server Management Studio](/sql/ssms/download-sql-server-management-studio-ssms) része.

Akkor célszerű az SQL Server Profilert használni, ha az adatforrás az alábbiak valamelyike:

- SQL Server
- SQL Server Analysis Services
- Azure Analysis Services

> [!CAUTION]
> A Power BI Desktop támogatja a diagnosztikai portokhoz való csatlakozást. A diagnosztikai port lehetővé teszi, hogy más eszközök csatlakozzanak, és diagnosztikai célú nyomkövetést végezzenek. A Power BI Desktop-adatmodellt semmiképpen sem szabad módosítani, mert a módosítása adatsérülést és adatvesztést okozhat.

SQL Server Profiler-nyomkövetés létrehozásához végezze el ezeket a lépéseket:

1. Nyissa meg a Power BI Desktop-jelentést, hogy könnyen megtalálhassa a portot a következő lépésben. Zárja be az összes többi megnyitott jelentést.
1. A Power BI Desktop által használt port meghatározásához írja be az alábbi parancsot a PowerShellben (rendszergazdai jogosultságokkal) vagy a parancssorban:
    ```powershell
    netstat -b -n
    ```
    A parancs kimenete az alkalmazások és a nyitott portjaik listája lesz. Keresse meg az **msmdsrv.exe** fájl által használt portot, és jegyezze fel későbbi használat céljából. Ez a Power BI Desktop-példány.
1. Kapcsolja össze az SQL Server Profilert a Power BI Desktop-jelentéssel:
    1. Nyissa meg az SQL Server Profilert.
    1. Válassza az SQL Server Profiler _File_ (Fájl) menüjének _New Trace_ (Új nyomkövetés) elemét.
    1. Válassza a **Server Type** (Kiszolgáló típusa) > _Analysis Services_ lehetőséget.
    1. Írja be a **Server Name** (Kiszolgálónév) mezőbe a _localhost:[az előzőekben feljegyzett portszám]_ parancsot.
    1. Kattintson a _Run_ (Futtatás) elemre. Ezzel élővé teszi az SQL Server Profiler-nyomkövetést, és az megkezdi a Power BI Desktop-lekérdezések profiljainak elkészítését.
1. A Power BI Desktop-lekérdezések végrehajtása közben látni fogja, hogy mennyi ideig tartanak, és hogy mennyi processzoridőt használnak. Az adatforrás típusától függően előfordulhat, hogy a lekérdezés végrehajtásának módját jelző egyéb események is megjelennek. Ezen információk alapján meghatározhatja, hogy mely lekérdezések jelentik a szűk keresztmetszetet.

Az SQL Server Profiler használatának egyik előnye, hogy menteni lehet az SQL Server (relációs) adatbázisainak nyomkövetéseit. A nyomkövetéseket felhasználhatja a [Database Engine Tuning Advisor](/sql/relational-databases/performance/start-and-use-the-database-engine-tuning-advisor) bemeneteként, így javaslatokat kaphat az adatforrás finomhangolásával kapcsolatban.

## <a name="monitor-premium-metrics"></a>Premium-metrikák figyelése

Power BI Premium-kapacitások esetén a **Power BI Premium Metrics alkalmazással** figyelheti Power BI Premium-előfizetése állapotát és kapacitását. További információt [A Power BI Premium Metrics alkalmazás](../admin/service-premium-metrics-app.md) című témakör tartalmaz.

## <a name="next-steps"></a>Következő lépések

Erről a cikkről a következő forrásanyagokban talál további információt:

- [Lekérdezési diagnosztika](/power-query/QueryDiagnostics)
- [Teljesítményelemző](../create-reports/desktop-performance-analyzer.md)
- [Jelentésteljesítménnyel kapcsolatos problémák elhárítása a Power BI-ban](report-performance-troubleshoot.md)
- [Power BI Premium Metrics alkalmazás](../admin/service-premium-metrics-app.md)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
- Javaslatai vannak? [A Power BI javítására vonatkozó ötletek beküldése](https://ideas.powerbi.com/)
