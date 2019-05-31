---
title: A Power BI Premium kapacitásainak figyelése a felügyeleti portállal
description: A Power BI felügyeleti portáljával figyelheti a prémium szintű kapacitások.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
LocalizationGroup: Premium
ms.openlocfilehash: 36b03a67e7c02702a70b6486880cc8eabf93e823
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65564891"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>Kapacitások monitorozása a felügyeleti portálon

A **egészségügyi** lapján a **kapacitásbeállítások** terület a felügyeleti portál mérőszámait egy összefoglaló információk a kapacitás és engedélyezve van a számítási feladatokat.  

![A kapacitás állapot lapon a portálon](media/service-admin-premium-monitor-portal/admin-portal-health.png)

Ha átfogóbb metrikák van szüksége, használja a [Power BI Premium kapacitás-metrikák](service-admin-premium-monitor-capacity.md) alkalmazást. Az alkalmazás biztosít részletes elemzés és szűrési, és a legrészletesebb metrikák majdnem minden szempontból kapacitás teljesítményét. További tudnivalókért lásd: [figyelő prémium szintű kapacitások az alkalmazással](service-admin-premium-monitor-capacity.md).

## <a name="system-metrics"></a>Rendszer-metrikák

Az a **egészségügyi** lapon, a legfelső szinten CPU-kihasználtság és a memóriahasználat a legfontosabb metrikákat, a kapacitás gyors áttekintést nyújt. Ezek a metrikák halmozott, többek között a kapacitás a számítási feladatok engedélyezve.

| **Metrika** | **Leírás** |
| --- | --- |
| CPU-KIHASZNÁLTSÁG | Átlagos CPU-kihasználtság, a teljes rendelkezésre álló Processzorkapacitást százalékában. |
| MEMÓRIAHASZNÁLAT | Átlagos memóriahasználat (gigabájtban).|

## <a name="workload-metrics"></a>Munkaterhelési mérőszámokat

Minden számítási kapacitásért engedélyezve van. CPU-kihasználtság és a memóriahasználat jelennek meg.

| **Metrika** | **Leírás** |
| --- | --- |
| CPU-KIHASZNÁLTSÁG | Átlagos CPU-kihasználtság, a teljes rendelkezésre álló Processzorkapacitást százalékában. |
| MEMÓRIAHASZNÁLAT | Átlagos memóriahasználat (gigabájtban).|

### <a name="detailed-workload-metrics"></a>Részletes munkaterhelési mérőszámokat

Minden számítási feladathoz tartozik a további metrikákat. A feltüntetett metrikákat típusa attól függ, hogy a számítási feladatok. Számítási feladatok részletes metrikáinak megtekintéséhez kattintson a Kibontás (le).

![Bontsa ki a számítási feladat állapota](media/service-admin-premium-monitor-portal/admin-portal-health-expand.png)

#### <a name="dataflows"></a>Adatfolyamok

##### <a name="dataflow-operations"></a>Adatfolyam-műveletek

| **Metrika** | **Leírás** |
| --- | --- |
| Teljes darabszám | Az egyes adatfolyamok frissítéseinek teljes száma. |
| Sikeres műveletek száma | Minden egyes adatfolyamot teljes sikeres frissítését.|
| Átlagos időtartama (perc) | Az adatfolyam frissítéseinek átlagos időtartama, percekben kifejezve |
| Max. időtartam (perc) | Az adatfolyam leghosszabb ideig futó frissítésének időtartama, percekben kifejezve. |
| Átlagos várakozási idő (perc) | Az ütemezett időpont és az adatfolyam frissítésének kezdete közötti átlagos késés, percekben kifejezve. |
| Maximális várakozási idő (perc) | Az adatfolyamhoz tartozó leghosszabb várakozási idő, percekben kifejezve.  |

#### <a name="datasets"></a>Adathalmazok

##### <a name="refresh"></a>Frissítés

| **Metrika** | **Leírás** |
| --- | --- |
| Teljes darabszám | Az egyes adathalmazok frissítéseinek teljes száma. |
| Sikeres műveletek száma | Összes sikeres frissül az egyes adatkészletek. |
| Hibásak száma | Összes sikertelen frissül az egyes adatkészletek. |
| Sikerességi arány  | Mérhető összesített frissítések osztva a sikeres frissítések száma. Megbízhatóságát. |
| Átlagos időtartama (perc) | Az adathalmaz frissítéseinek átlagos időtartama, percekben kifejezve.  |
| Max. időtartam (perc) | Az adathalmaz leghosszabb ideig futó frissítésének időtartama, percekben kifejezve. |
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

##### <a name="eviction"></a>Kiürítés

| **Metrika** | **Leírás** |
| --- | --- |
| Modell száma | A kapacitásnak az adatkészlet adatbázislap teljes száma. Ha egy kapacitásban magas memóriaterhelés lép fel, a csomópont egy vagy több adathalmazt kizár a memóriából. Először az inaktív adathalmazok (nincs végrehajtás alatt álló lekérdezési/frissítési művelet) lesznek kizárva. Ezután a „legrégebben használt” (LRU) paraméter értéke határozza meg a kizárási sorrendet. |

#### <a name="paginated-reports"></a>Lapszámozott jelentések

##### <a name="report-execution"></a>Jelentés-végrehajtás

| **Metrika** | **Leírás** |
| --- | --- |
| Végrehajtások száma  | A jelentés már végre lett hajtva. hányszor és felhasználók tekinthetők meg.|

##### <a name="report-usage"></a>Használati jelentés

| **Metrika** | **Leírás** |
| --- | --- |
| Sikeres műveletek száma | A szám, ahányszor a felhasználó megtekinti a jelentést. |
| Hibásak száma |A szám, ahányszor a felhasználó megtekinti a jelentést.|
| Sorok száma |A jelentésben szereplő adatsorok száma. |
| Adatok lekérése időtartama (ms) |Az adatok jelentéshez való lekérésének átlagos időtartama, ezredmásodpercben megadva. A hosszú időtartamok lassú lekérdezésekre vagy az adatforrással kapcsolatos más problémára utalhatnak.  |
| Feldolgozási időtartam (ms) |Az adatok jelentéshez való feldolgozásának átlagos időtartama, ezredmásodpercben megadva. |
| Renderelési időtartama (ms) |A jelentés böngészőben való renderelésének átlagos időtartama, ezredmásodpercben megadva. |

> [!NOTE]
> Részletes metrikáinak a **AI** számítási feladatok még nem érhető el.

## <a name="next-steps"></a>Következő lépések

Most, hogy megismerkedett a Power BI Premium kapacitásainak monitorozásával, tudjon meg többet a kapacitás optimalizálásáról is.

> [!div class="nextstepaction"]
> [A Power BI Premium-kapacitásait optimalizálása](service-premium-capacity-optimize.md)
