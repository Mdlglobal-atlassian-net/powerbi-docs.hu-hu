---
title: Vizualizációk jelentésen belüli működése
description: A Power BI végfelhasználóinak szóló dokumentáció, amely bemutatja, hogyan működnek a vizualizációk egy jelentésoldalon.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 45f3aa4ccf92237085db0c7517c291fe8d0f0428
ms.sourcegitcommit: a72567f26c1653c25f7730fab6210cd011343707
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564883"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Vizualizációk közötti keresztszűrés Power BI-jelentésben

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

A Power BI egyik legnagyszerűbb funkciója, hogy a jelentésoldalon szereplő vizualizációk mind kapcsolódnak egymáshoz. Ha kiválasztja a vizualizáció egyik adatpontját, az oldalon szereplő összes többi, az adott adatot tartalmazó vizualizáció módosul a kijelölés alapján. 

![videó a vizualizációk interakciójáról](media/end-user-interactions/interactions.gif)

## <a name="how-visuals-interact-with-each-other"></a>Hogyan működnek együtt a vizualizációk

Alapértelmezés szerint a jelentésoldalakon található egyik vizualizáció adatpontjának kiválasztásával lehet az oldal többi vizualizációjára keresztszűrést és keresztkiemelést végezni. A jelentés *tervezője* állítja be, hogy pontosan milyen módon lépnek interakcióba egymással az oldalon szereplő vizualizációk. A *tervezők* ki- és bekapcsolhatják a vizualizációk interakcióit, és módosíthatják az alapértelmezett keresztszűrés, a keresztkiemelés és a [részletezés](end-user-drill.md) működését. 

Ha még nem találkozott a hierarchiákkal és a részletezéssel, megismerkedhet velük a [Részletezés a Power BI-ban](end-user-drill.md) című cikkben. 

### <a name="cross-filtering-and-cross-highlighting"></a>Keresztszűrés és keresztkiemelés

A keresztszűrés és a keresztkiemelés hasznos lehet annak azonosítására, hogy az adatértékek hogyan járulnak hozzá egy másikhoz. A *keresztszűrés* és *keresztkijelölés* kifejezésekkel az itt ismertetett viselkedéseket a **Szűrők** ablaktábla szűrés és kiemelés funkciójától különböztetjük meg.  

Definiáljuk ezeket a kifejezéseket, miközben megtekintjük az alábbi jelentésoldalakat. A „Mennyiség az összes kategóriában” perecdiagram két értékkel rendelkezik: „Moderálás” és „Kényelmi”. 

![Jelentésoldal](media/end-user-interactions/power-bi-interactions-before.png)

1. Lássuk, mi történik, ha kiválasztjuk a **Moderálást**.

    ![A jelentésoldal a perecdiagram Moderálás szegmensének kiválasztása után](media/end-user-interactions/power-bi-interactions-after.png)

2. A **keresztszűrés** eltávolítja a nem alkalmazható adatokat. Ha a perecdiagramban a **Moderálás** lehetőséget választja, azzal keresztszűrést végez a vonaldiagramon. A vonaldiagramon most csak azok az adatpontok jelennek meg, amelyek a Moderálás szegmensre vonatkoznak. 

3. A **keresztkiemelés** az összes eredeti adatpontot megtartja, de elhalványítja azokat, amelyek nem vonatkoznak a kijelölésre. Ha a perecdiagramban a **Moderálás** lehetőséget választja, azzal keresztkijelölést végez a vonaldiagramon. Az összes olyan adat elhalványul az oszlopdiagramon, amely a Kényelmi szegmensre vonatkozik, és az összes olyan adat ki lesz emelve, amely a Moderálás szegmensre vonatkozik. 


## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás
- Ha a jelentés olyan vizualizációkkal is rendelkezik, amelyek támogatják a [részletes vizsgálatot](end-user-drill.md), akkor alapbeállítás szerint egy adott vizualizáció részletező elemzése nem lesz hatással a jelentésoldal többi vizualizációjára. A jelentés *tervezője* azonban megváltoztathatja ezt a viselkedést, ezért ellenőrizze a részletezhető vizualizációknál, hogy engedélyezte-e a jelentés *tervezője* a **részletező szűrők más vizualizációit**.
    
- A vizualizációszintű szűrők megmaradnak a jelentésoldalon más vizualizációk szűrése és kiemelése során. Ha az „A” vizualizáció vizualizációszintű szűrőkkel rendelkezik, melyeket a tervező agy Ön állított be, és az „A” vizualizációt használja a „B” vizualizációval való interakcióra, az „A” vizualizáció vizualizációs szintű szűrőit a rendszer a „B” vizualizációra alkalmazza.

    ![A jelentésoldal a perecdiagram Moderálás szegmensének kiválasztása után](media/end-user-interactions/power-bi-visual-filters.png)

## <a name="next-steps"></a>Következő lépések
[A jelentésszűrők használata](../consumer/end-user-report-filter.md)


[A szűrés és a kiemelés](end-user-report-filter.md).
