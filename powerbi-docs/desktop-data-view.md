---
title: Adatnézet a Power BI Desktopban
description: Adatnézet a Power BI Desktopban
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/05/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 1fee95bbfb790a1c61d82131579c8fb43980ca05
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/06/2020
ms.locfileid: "82866725"
---
# <a name="work-with-data-view-in-power-bi-desktop"></a>Az Adatok nézet használata a Power BI Desktopban

Az *Adat nézet* segítségével megvizsgálhatja, felderítheti és megismerheti *Power BI Desktop*-modellben lévő adatokat. Így másképp tekintheti meg a táblákat, oszlopokat és adatokat, mint a *Power Query-szerkesztőben*. Az Adat nézettel a modellbe való betöltésük *után* tekintheti meg az adatokat.

> [!NOTE]
> Mivel az adatnézet a modellbe való betöltés utáni állapotban mutatja az adatokat, az Adatnézet ikon nem látható, ha minden adatforrás DirectQuery-alapú. 

Az adatok modellezésekor előfordulhat, hogy csak meg szeretné tekinteni egy tábla vagy oszlop aktuális tartalmát anélkül, hogy ehhez egy vizualizációt vagy jelentésvásznat kellene létrehoznia. Akár sorszintű betekintésre is szüksége lehet. Ez a képesség akkor igazán hasznos, amikor mértékeket vagy számított oszlopokat hoz létre, vagy amikor azonosítani szeretné az adatok típusát vagy kategóriáját.

Tekintsük meg részletesebben az Adat nézet néhány elemét.

![Adatnézet a Power BI Desktopban](media/desktop-data-view/dataview_fullscreen.png)

1. **Adatnézet ikonja**. Az ikon kiválasztásával Adatnézetbe léphet.

2. **Adatrács**. Ez a terület a kijelölt táblát és a benne lévő összes oszlopot és sort jeleníti meg. A *Jelentés* nézet elől elrejtett oszlopok itt szürkén jelennek meg. Jobb gombbal az egyes oszlopokra kattintva elérheti a beállításokat.

3. **Modellezési menüszalag**. Lehetővé teszi a kapcsolatok kezelését, a számítások létrehozását és az oszlopok adattípusának, formátumának és adatkategóriájának szerkesztését.

4. **Képletsáv**. Itt adhatja meg a mértékek és a számított oszlopok Data Analysis Expression- (DAX-) képleteit.

5. **Keresés**. Táblákat vagy oszlopokat kereshet meg a modellben.

6. **Mezőlista**. Az adatrácsban megjelenítendő táblák vagy oszlopok kiválasztására szolgál.

## <a name="filtering-in-data-view"></a>Szűrés Adatnézetben

Az Adatnézet lehetővé teszi az adatok szűrését és rendezését is. Mindegyik oszlopnál feltüntetésre kerül a rendezés irányát szemléltető ikon, ha az oszlopra van rendezés alkalmazva.

![Rendezés és szűrés a Power BI Desktop Adatnézetében](media/desktop-data-view/dataview_sort-and-filter.png)

Szűrést alkalmazhat egyes értékekre, vagy az oszlopban található adatokat alapul véve használhatja a speciális szűrés funkciót is.

> [!NOTE]
> Amikor egy, a felhasználói felülettől eltérő kulturális környezetben hoz létre egy Power BI-modellt, a keresőmező kizárólag szövegmezők esetén jelenik meg az Adatnézet felhasználói felületén. Ez történne például egy amerikai angol nyelven létrehozott, spanyol területi beállítással megtekintett modell esetében.


## <a name="next-steps"></a>Következő lépések

A Power BI Desktop műveletek és lehetőségek széles tárházát tartalmazza. A program képességeivel kapcsolatos további információkért lásd az alábbi forrásanyagokat:

* [Mi az a Power BI Desktop?](desktop-what-is-desktop.md)
* [Lekérdezések áttekintése a Power BI Desktopban](desktop-query-overview.md)
* [Adattípusok a Power BI Desktopban](desktop-data-types.md)
* [Adatok formázása és kombinálása a Power BI Desktoppal](desktop-shape-and-combine-data.md)
* [Gyakori lekérdezési feladatok a Power BI Desktopban](desktop-common-query-tasks.md)
