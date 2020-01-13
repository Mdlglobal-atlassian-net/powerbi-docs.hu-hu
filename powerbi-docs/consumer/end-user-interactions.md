---
title: Vizualizációk jelentésen belüli működése
description: A Power BI végfelhasználóinak szóló dokumentáció, amely bemutatja, hogyan működnek a vizualizációk egy jelentésoldalon.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 12/18/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: dc8dad0417ac2ed6498fb7612900ebdbb0ce2a18
ms.sourcegitcommit: 4359baa43ca01b179d28ec59f4e61ba8c07ee288
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/20/2019
ms.locfileid: "75303884"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Vizualizációk közötti keresztszűrés Power BI-jelentésben
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
- Ha a jelentés olyan vizualizációkkal is rendelkezik, amelyek támogatják a [részletes vizsgálatot](end-user-drill.md), akkor alapbeállítás szerint egy adott vizualizáció részletező elemzése nem lesz hatással a jelentésoldal többi vizualizációjára.     
- A vizualizációszintű szűrők megmaradnak a jelentésoldalon más vizualizációk szűrése és kiemelése során. Ha az „A” vizualizáció vizualizációszintű szűrőkkel rendelkezik, melyeket a tervező agy Ön állított be, és az „A” vizualizációt használja a „B” vizualizációval való interakcióra, az „A” vizualizáció vizualizációs szintű szűrőit a rendszer a „B” vizualizációra alkalmazza.

    ![A jelentésoldal a perecdiagram Moderálás szegmensének kiválasztása után](media/end-user-interactions/power-bi-visual-filters.png)

## <a name="next-steps"></a>Következő lépések
[A jelentésszűrők használata](../power-bi-how-to-report-filter.md)    


[A szűrés és a kiemelés](end-user-report-filter.md). 
