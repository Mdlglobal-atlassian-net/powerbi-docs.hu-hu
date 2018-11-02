---
title: Vizualizációk jelentésen belüli működésének bemutatása (a jelentések felhasználói számára)
description: A Power BI végfelhasználóinak szóló dokumentáció, amely bemutatja, hogyan működnek a vizualizációk egy jelentésoldalon.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 08/28/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: c87f99b768f52fe7f6b565c47ed7e434b167a046
ms.sourcegitcommit: dc8b8a2cf2dcc96ccb46159802ebd9342a7fa840
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/11/2018
ms.locfileid: "49112061"
---
# <a name="visualization-interactions-in-a-power-bi-report"></a>Vizualizációk interakciói a Power BI-jelentésekben
A Power BI egyik legnagyszerűbb funkciója, hogy a jelentésoldalon szereplő vizualizációk mind kapcsolódnak egymáshoz. Ha kiválasztja a vizualizáció egyik adatpontját, az oldalon szereplő összes többi, az adott adatot tartalmazó vizualizáció módosul a kijelölés alapján. 

![videó a vizualizációk interakciójáról](media/end-user-interactions/interactions.gif)

Alapértelmezés szerint a jelentésoldalakon található vizualizációk az adott oldalon található többi vizualizáció keresztszűrésére, keresztkiemelésére és részletezésére használhatók. Ha egy térkép vizualizáción kiválaszt egy államot, azzal úgy emelheti ki az oszlopdiagramot és szűrheti a vonaldiagramot, hogy a rendszer csak az adott államra vonatkozó adatokat jelenítse meg.

Lásd: [Szűrés és kiemelés](../power-bi-reports-filters-and-highlighting.md). Ha pedig olyan vizualizációkkal is rendelkezik, amelyek támogatják a [részletes vizsgálatot](../power-bi-visualization-drill-down.md), akkor alapbeállítás szerint egy adott vizualizáció részletező elemzése nem lesz hatással a jelentésoldal többi vizualizációjára. 

A jelentés *tervezője* állítja be, hogy pontosan milyen módon lépnek interakcióba egymással az oldalon szereplő vizualizációk. A tervezők ki- és bekapcsolhatják a vizualizációk interakcióit, és módosíthatják az alapértelmezett keresztszűrés, a keresztkiemelés és a részletezés működését.
  
> [!NOTE]
> A *keresztszűrés* és *keresztkijelölés* kifejezésekkel az itt ismertetett viselkedéseket a **Szűrők** ablaktábla szűrés és kiemelés funkciójától különböztetjük meg.  

### <a name="next-steps"></a>Következő lépések
[A jelentésszűrők használata](../power-bi-how-to-report-filter.md)
