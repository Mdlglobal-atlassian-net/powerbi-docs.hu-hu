---
title: Vizualizációk jelentésen belüli működése
description: A Power BI végfelhasználóinak szóló dokumentáció, amely bemutatja, hogyan működnek a vizualizációk egy jelentésoldalon.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 09/24/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: b95df5c32d9058e4480d7af5e226a971ba581144
ms.sourcegitcommit: 02042995df12cc4e4b97eb8a369e62364eb5af36
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/25/2019
ms.locfileid: "71256295"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Vizualizációk közötti keresztszűrés Power BI-jelentésben
A Power BI egyik legnagyszerűbb funkciója, hogy a jelentésoldalon szereplő vizualizációk mind kapcsolódnak egymáshoz. Ha kiválasztja a vizualizáció egyik adatpontját, az oldalon szereplő összes többi, az adott adatot tartalmazó vizualizáció módosul a kijelölés alapján. 

![videó a vizualizációk interakciójáról](media/end-user-interactions/interactions.gif)

Alapértelmezés szerint a jelentésoldalakon található egyik vizualizáció adatpontjának kiválasztásával lehet a többi vizualizációra keresztszűrést, keresztkiemelést és részletezést végezni. 

Ez hasznos lehet annak azonosítására, hogy az adatértékek hogyan járulnak hozzá egy másikhoz. Ha például ha a perecdiagramon kijelöli a Moderálási szegmenst, akkor a rendszer kiemeli az adott szegmens hozzájárulását az Egységek teljes száma hónap szerint diagram minden egyes oszlopához, és a jobb oldalon található vonaldiagram is szűrve lesz.

![kép vizualizációk interakciójáról](media/end-user-interactions/power-bi-interactions.png)

Lásd: [Szűrés és kiemelés](../power-bi-reports-filters-and-highlighting.md). 

A jelentés *tervezője* állítja be, hogy pontosan milyen módon lépnek interakcióba egymással az oldalon szereplő vizualizációk. A tervezők ki- és bekapcsolhatják a vizualizációk interakcióit, és módosíthatják az alapértelmezett keresztszűrés, a keresztkiemelés és a részletezés működését. 
  
> [!NOTE]
> A *keresztszűrés* és *keresztkijelölés* kifejezésekkel az itt ismertetett viselkedéseket a **Szűrők** ablaktábla szűrés és kiemelés funkciójától különböztetjük meg.  

## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás
- Ha a jelentés olyan vizualizációkkal is rendelkezik, amelyek támogatják a [részletes vizsgálatot](../power-bi-visualization-drill-down.md), akkor alapbeállítás szerint egy adott vizualizáció részletező elemzése nem lesz hatással a jelentésoldal többi vizualizációjára.     
- Ha az „A” vizualizációt használja a „B” vizualizációval való interakcióra, az „A” vizualizáció vizualizációs szintű szűrőit a rendszer a „B” vizualizációra alkalmazza.

## <a name="next-steps"></a>Következő lépések
[A jelentésszűrők használata](../power-bi-how-to-report-filter.md)
