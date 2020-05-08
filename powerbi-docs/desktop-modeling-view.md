---
title: A Modellező nézet használata a Power BI Desktopban
description: A Modellező nézet használata összetett adathalmazok vizuális megjelenítéséhez a Power BI Desktopban
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: b9df4398c410f52e3d5cdd51a99a40de107f5867
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "75760882"
---
# <a name="work-with-modeling-view-in-power-bi-desktop"></a>A Modellező nézet használata a Power BI Desktopban

A **Power BI Desktopban** a **Modellező nézettel** sok táblát tartalmazó, összetett adathalmazokat tekinthet meg és használhat.


## <a name="using-modeling-view"></a>A Modellező nézet használata

A Modellező nézet a **Power BI Desktop** bal oldalán található Modellező nézet ikont választva érhető el, ahogyan az alábbi ábrán látható.

![A Modellező nézet ikonja a Power BI Desktopban](media/desktop-modeling-view/modeling-view_02.png)

## <a name="creating-separate-diagrams"></a>Külön diagramok létrehozása

Modellező nézetben olyan diagramokat készíthet a modelljéről, amelyek csak a modell tábláinak egy-egy részhalmazát tartalmazzák. Ezáltal átláthatóbbak lesznek azok a táblák, amelyekkel dolgozni kíván, és az összetett adathalmazokkal végzett munka egyszerűbbé válik. A tábláknak csak egy részhalmazát tartalmazó új diagram létrehozásához kattintson az **Összes tábla** lapfül melletti **+** jelre a Power BI Desktop ablakának alján.

![Hozzon létre új diagramot a lapfülek melletti + jelre kattintva](media/desktop-modeling-view/modeling-view_03.png)

Ezt követően áthúzhat egy táblát a **Mezők** listából a diagram felületére. Kattintson a jobb gombbal a táblára, majd válassza a **Kapcsolódó táblák hozzáadása** lehetőséget a felugró menüből.

![Kattintson a jobb gombbal egy táblára, és válassza a Kapcsolódó táblák hozzáadása lehetőséget](media/desktop-modeling-view/modeling-view_04.png)

Ennek hatására az eredeti táblához kapcsolódó táblák is megjelennek az új diagramon. Az alábbi kép azt mutatja be, hogy hogyan jelennek meg a kapcsolódó táblák a **Kapcsolódó táblák hozzáadása** menüelem kiválasztása után.

![Kapcsolódó táblák megjelenítése](media/desktop-modeling-view/modeling-view_05.png)

## <a name="setting-common-properties"></a>Közös tulajdonságok beállítása

Modellező nézetben egyszerre több objektumot is kijelölhet, ha a **CTRL** billentyűt lenyomva tartva több táblára is rákattint. Ha több táblát is kijelöl, azok ki lesznek emelve a modellező nézetben. Amíg több tábla is ki van jelölve, a **Tulajdonságok** panelen végrehajtott módosítások az összes kijelölt táblára vonatkoznak.

Módosíthatja például a diagramon szereplő több tábla [tárolási módját](desktop-storage-mode.md), ha a **CTRL** billentyűt lenyomva tartva kijelöli a táblákat, majd a **Tulajdonságok** panelen megváltoztatja a tárolási mód beállítását.

![Jelöljön ki több táblát a CTRL billentyűt lenyomva tartva, és állítsa be a kijelölt táblák közös tulajdonságait](media/desktop-modeling-view/modeling-view_06.png)


## <a name="next-steps"></a>Következő lépések

Az alábbi cikkek bővebben ismertetik az adatmodelleket, és a DirectQuery részletes leírását is tartalmazzák.

* [Aggregációk a Power BI Desktopban (előzetes verzió)](desktop-aggregations.md)
* [Összetett modellek a Power BI Desktopban](desktop-composite-models.md)
* [Tárolási mód a Power BI Desktopban (előzetes verzió)](desktop-storage-mode.md)
* [Több a többhöz kapcsolatok a Power BI Desktopban](desktop-many-to-many-relationships.md)


A DirectQuery-vel kapcsolatos cikkek:

* [DirectQuery használata a Power BI-ban](desktop-directquery-about.md)
* [A DirectQuery által támogatott adatforrások a Power BI-ban](desktop-directquery-data-sources.md)
