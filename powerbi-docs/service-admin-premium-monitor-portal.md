---
title: A Power BI Premium kapacitásainak figyelése a felügyeleti portállal
description: A Power BI felügyeleti portáljával figyelheti a prémium szintű kapacitások.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/06/2020
LocalizationGroup: Premium
ms.openlocfilehash: 18ae8828ce5811b4f06038b18ff6b423562c335b
ms.sourcegitcommit: d43761104f7daf4b2f297648855bb573b53e6d8c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/18/2020
ms.locfileid: "81637690"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>Kapacitások monitorozása a felügyeleti portálon

A felügyeleti portál **Kapacitásbeállítások** területén található **Állapot** lapon a kapacitással és az engedélyezett számítási feladatokkal kapcsolatos mérőszámok összegzését találja.  

![A Kapacitásállapot lap a portálon](media/service-admin-premium-monitor-portal/admin-portal-health.png)

Ha átfogóbb metrikákra van szüksége, használja a [Power BI Premium Capacity Metrics](service-admin-premium-monitor-capacity.md) alkalmazást. Az alkalmazás részletekbe menő elemzést, szűrést, és a kapacitásteljesítményre hatást gyakorló szinte minden tényezőhöz részletes mérőszámokat biztosít. További tudnivalókért lásd: [Prémium szintű kapacitások monitorozása az alkalmazással](service-admin-premium-monitor-capacity.md).





## <a name="system-metrics"></a>Rendszermetrikák

Az **Állapot** lapon a processzorhasználat és a memóriahasználat gyors és általános áttekintést nyújt a kapacitás legfontosabb mérőszámairól. Ezek a metrikák kumulatívak, beleértve a kapacitáshoz engedélyezett összes számítási feladatot.

| **Metrika** | **Leírás** |
| --- | --- |
| CPU-KIHASZNÁLTSÁG | Az átlagos processzorkihasználtság a teljes elérhető CPU százalékában. |
| MEMÓRIAHASZNÁLAT | Átlagos memóriahasználat, gigabájtban (GB) kifejezve.|

## <a name="workload-metrics"></a>Számítási feladatok metrikái

A kapacitáshoz engedélyezett összes számítási feladatra vonatkozóan. A rendszer megjeleníti a processzor- és memóriahasználatot.

| **Metrika** | **Leírás** |
| --- | --- |
| CPU-KIHASZNÁLTSÁG | Az átlagos processzorkihasználtság a teljes elérhető CPU százalékában. |
| MEMÓRIAHASZNÁLAT | Átlagos memóriahasználat, gigabájtban (GB) kifejezve.|

### <a name="detailed-workload-metrics"></a>Számítási feladatok részletes metrikái

Minden számítási feladathoz további metrikák is tartoznak. A megjelenő metrikák típusa az érintett számítási feladattól függ. A számítási feladat részletes metrikáinak megtekintéséhez kattintson a kibontási (lefelé mutató) nyílra.

![Számítási feladat állapotának kibontása](media/service-admin-premium-monitor-portal/admin-portal-health-expand.png)

#### <a name="dataflows"></a>Adatfolyamok

##### <a name="dataflow-operations"></a>Adatfolyam-műveletek

| **Metrika** | **Leírás** |
| --- | --- |
| Teljes darabszám | Az egyes adatfolyamok frissítéseinek teljes száma. |
| Sikeres műveletek száma | Az egyes adatfolyamok sikeres frissítéseinek teljes száma.|
| Átlagos időtartam (perc) | Az adatfolyam frissítéseinek átlagos időtartama, percekben kifejezve |
| Maximális időtartam (perc) | Az adatfolyam leghosszabb ideig futó frissítésének időtartama, percekben kifejezve. |
| Átlagos várakozási idő (perc) | Az ütemezett időpont és az adatfolyam frissítésének kezdete közötti átlagos késés, percekben kifejezve. |
| Maximális várakozási idő (perc) | Az adatfolyamhoz tartozó leghosszabb várakozási idő, percekben kifejezve.  |

#### <a name="datasets"></a>Adathalmazok

##### <a name="refresh"></a>Frissítés

| **Metrika** | **Leírás** |
| --- | --- |
| Teljes darabszám | Az egyes adathalmazok frissítéseinek teljes száma. |
| Sikeres műveletek száma | Az egyes adathalmazok sikeres frissítéseinek teljes száma. |
| Hibásak száma | Az egyes adathalmazok sikertelen frissítéseinek teljes száma. |
| Sikerességi arány  | A sikeres frissítések száma elosztva és a mérni kívánt frissítések teljes számával. megbízhatóság. |
| Átlagos időtartam (perc) | Az adathalmaz frissítéseinek átlagos időtartama, percekben kifejezve.  |
| Maximális időtartam (perc) | Az adathalmaz leghosszabb ideig futó frissítésének időtartama, percekben kifejezve. |
| Átlagos várakozási idő (perc) | Az ütemezett időpont és az adathalmaz frissítésének kezdete közötti átlagos késés, percekben kifejezve. |
| Maximális várakozási idő (perc) | Az adathalmazhoz tartozó leghosszabb várakozási idő, percekben kifejezve. |

##### <a name="query"></a>Lekérdezés

| **Metrika** | **Leírás** |
| --- | --- |
| Teljes darabszám | Az adathalmazon futtatott lekérdezések teljes száma. |
| Átlagos időtartam (ms) |Az adathalmaz lekérdezéseinek átlagos időtartama, ezredmásodpercben megadva|
| Maximális időtartam (ms) |Az adathalmaz leghosszabb ideig futó lekérdezésének időtartama, ezredmásodpercben megadva. |
| Átlagos várakozási idő (ms) |Az adathalmaz lekérdezéseinek átlagos várakozási időtartama, ezredmásodpercben megadva. |
| Maximális várakozási idő (ms) |Az adathalmaz leghosszabb ideig várakozó lekérdezésének időtartama, ezredmásodpercben megadva. |

##### <a name="eviction"></a>Kizárás

| **Metrika** | **Leírás** |
| --- | --- |
| Modellek száma | A kapacitás adathalmaz-kizárásainak teljes száma. Ha egy kapacitásban magas memóriaterhelés lép fel, a csomópont egy vagy több adathalmazt kizár a memóriából. Először az inaktív adathalmazok (nincs végrehajtás alatt álló lekérdezési/frissítési művelet) lesznek kizárva. Ezután a „legrégebben használt” (LRU) paraméter értéke határozza meg a kizárási sorrendet. |

#### <a name="paginated-reports"></a>Lapszámozott jelentések

##### <a name="report-execution"></a>Jelentés végrehajtása

| **Metrika** | **Leírás** |
| --- | --- |
| Végrehajtások száma  | Azon alkalmak száma, amikor a jelentés végre lett hajtva, és egy felhasználó megtekintette.|

##### <a name="report-usage"></a>Jelentés használata

| **Metrika** | **Leírás** |
| --- | --- |
| Sikeres műveletek száma | Azon alkalmak száma, amikor egy felhasználó megtekintette a jelentést. |
| Hibásak száma |Azon alkalmak száma, amikor egy felhasználó megtekintette a jelentést.|
| Sorok száma |A jelentésben szereplő adatsorok száma. |
| Adatlekérési időtartam (ms) |Az adatok jelentéshez való lekérésének átlagos időtartama, ezredmásodpercben megadva. A hosszú időtartamok lassú lekérdezésekre vagy az adatforrással kapcsolatos más problémára utalhatnak.  |
| Feldolgozási időtartam (ms) |Az adatok jelentéshez való feldolgozásának átlagos időtartama, ezredmásodpercben megadva. |
| Renderelési időtartam (ms) |A jelentés böngészőben való renderelésének átlagos időtartama, ezredmásodpercben megadva. |

> [!NOTE]
> Az **AI** számítási feladathoz még nem érhetők el részletes metrikák.

## <a name="next-steps"></a>Következő lépések

Most, hogy megismerkedett a Power BI Premium kapacitásainak monitorozásával, tudjon meg többet a kapacitás optimalizálásáról is.

> [!div class="nextstepaction"]
> [Power BI Premium-kapacitások optimalizálása](service-premium-capacity-optimize.md)
