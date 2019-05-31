---
title: Vizualizációk jelentésen belüli működése
description: A Power BI végfelhasználóinak szóló dokumentáció, amely bemutatja, hogyan működnek a vizualizációk egy jelentésoldalon.
author: mihart
manager: kvivek
ms.custom: seodec18
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 05/29/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 7148a52d7c7475fbe685f83b1e1cc325521460db
ms.sourcegitcommit: d88cc6a87d4ba82ad2c4d496a3634f927e4ac529
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/30/2019
ms.locfileid: "66413170"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Vizualizációk közötti keresztszűrés Power BI-jelentésben
A Power BI egyik legnagyszerűbb funkciója, hogy a jelentésoldalon szereplő vizualizációk mind kapcsolódnak egymáshoz. Ha kiválasztja a vizualizáció egyik adatpontját, az oldalon szereplő összes többi, az adott adatot tartalmazó vizualizáció módosul a kijelölés alapján. 

![videó a vizualizációk interakciójáról](media/end-user-interactions/interactions.gif)

Alapértelmezett, válassza az oldal egy Vizualizáció egy adatpontra fog keresztszűrés, egymás közötti keresztkiemelések és lefúrással megjelenítheti a lapon lévő többi vizualizációt. 

Ez hasznos lehet az adatok hogyan teljesít egyetlen érték azonosításához járul hozzá a másikra. Például minden oszlopához az összes egység hónap diagram szerint az adott szegmens a hozzájárulását a moderálás szegmensben válassza a perecdiagram emeli ki, és azt szűrte a vonaldiagramot a jobb oldalon.

![Vizualizációk interakció képe](media/end-user-interactions/power-bi-interactions.png)

Lásd: [Szűrés és kiemelés](../power-bi-reports-filters-and-highlighting.md). 

A jelentés *tervezője* állítja be, hogy pontosan milyen módon lépnek interakcióba egymással az oldalon szereplő vizualizációk. A tervezők ki- és bekapcsolhatják a vizualizációk interakcióit, és módosíthatják az alapértelmezett keresztszűrés, a keresztkiemelés és a részletezés működését. 
  
> [!NOTE]
> A *keresztszűrés* és *keresztkijelölés* kifejezésekkel az itt ismertetett viselkedéseket a **Szűrők** ablaktábla szűrés és kiemelés funkciójától különböztetjük meg.  

## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás
- Ha a jelentés rendelkezik egy vizualizációt, amely támogatja a [részletes elemzések kibontásáról](../power-bi-visualization-drill-down.md), alapértelmezés szerint egy Vizualizáció részletező elemzés nem befolyásolja a jelentésoldalon lévő többi vizualizációt.     
- VisualA visualB interakcióba használatakor a rendszer visualA a Vizualizáció-szintű szűrőkről visualB alkalmazza.

## <a name="next-steps"></a>Következő lépések
[A jelentésszűrők használata](../power-bi-how-to-report-filter.md)
