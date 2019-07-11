---
title: A jelentés Szűrők paneljének bemutatása
description: Szűrő hozzáadása jelentéshez az ügyfeleknek készült Power BI szolgáltatásban
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: ef7e4f556832f1323043a80cf219678a16511c9e
ms.sourcegitcommit: e67bacbfc5638ee97e3d2e0e7f5bd2d9aac78f9c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67532976"
---
# <a name="take-a-tour-of-the-report-filters-pane"></a>Ismerkedés a jelentések Szűrők panelével

Ez a cikk a jelentések **Szűrők** paneljét mutatja be a Power BI szolgáltatásban. A szűrőkkel új megállapításokat nyerhet ki az adatokból.

Az adatok szűrésének számos módja érhető el a Power BI-ban. A szűrőkkel kapcsolatos további információkért tekintse meg a [Power BI- jelentések szűrőivel és kiemeléseivel](../power-bi-reports-filters-and-highlighting.md) foglalkozó részt.

![Képernyőkép egy jelentésről a böngészőben, amelyen a nyíl a Szűrők beállításra mutat.](media/end-user-report-filter/power-bi-browser-new2.png)

## <a name="working-with-the-report-filters-pane"></a>A jelentések Szűrők panelének használata

Amikor a munkatársa megoszt Önnel egy jelentést, mindenképp keresse meg a **Szűrők** panelt. Előfordulhat, hogy össze van csukva a jelentés jobb szélén. Kattintson rá a kibontáshoz.

![Képernyőkép a jelentésről, amelyen a Szűrők panel ki van bontva.](media/end-user-report-filter/power-bi-filter-pane.png)

A **Szűrők** panel olyan szűrőket tartalmaz, amelyekkel a jelentés *tervezője* látta el a jelentést. A *felhasználók* kezelhetik a meglévő szűrőket és menthetik a módosításokat, azonban nem adhatnak hozzá új szűrőket a jelentéshez. A fenti képernyőképen például a tervező két oldalszintű szűrőt adott hozzá: a **Segment** és a **Year** szűrőt. Kezelheti és módosíthatja ezeket a szűrőket, de nem adhat hozzá egy harmadik lapszintű szűrőt.

A Power BI szolgáltatásban a jelentések megőrzik a **Szűrők** panelen végzett módosításokat. A szolgáltatás emellett a jelentés mobilos verziójára is alkalmazza őket.

A **Szűrő** panelnek a tervező alapértelmezett értékeire való visszaállításához válassza a ![Képernyőkép a Visszaállítás alapértelmezettre beállításról](media/end-user-report-filter/power-bi-reset.png) elemet a felső menüsávon.

## <a name="view-all-the-filters-for-a-report-page"></a>Jelentésoldal összes szűrőjének megtekintése

A **Szűrők** panel a tervező által a jelentéshez adott összes szűrőt megjeleníti. A **Szűrők** panel egyben az a terület is, ahol a szűrőkkel kapcsolatos információk megtekinthetőek és kezelhetőek. Mentheti az elvégzett módosításokat vagy a **Visszaállítás alapértelmezettre** beállítással visszaállíthatja az eredeti szűrőbeállításokat.

Ha menteni szeretné a módosításokat, létrehozhat egy személyes könyvjelzőt is.  További információért tekintse meg [a könyvjelzőket](end-user-bookmarks.md) bemutató cikket.

A **Szűrők** panel különböző típusú jelentésszűrőket kezel és jelenít meg. Ezek alkalmazhatók egy vizualizációra, jelentésoldalra vagy a teljes jelentésre is.

Ebben a példában egy olyan vizualizációt választottunk, amelyhez két szűrő tartozik. A jelentésoldalon szintén találhatók szűrők, ezek **Az ezen a lapon megtalálható szűrők** fejléc alatt vannak felsorolva. Emellett a teljes jelentés rendelkezik a **Date** szűrővel.

![Képernyőkép egy jelentésről a vizualizáció és a kapcsolódó szűrők megjelenítésével.](media/end-user-report-filter/power-bi-all-filters2.png)

Némelyik szűrő mellett az **(Összes)** szó szerepel. Az **(Összes)** azt jelenti, hogy a szűrő az összes értékre kiterjed. A fenti képernyőképen a **Segment (Összes)** azt jelzi, hogy a jelentésoldal az összes termékszegmens adatait tartalmazza. A **Region is West** lapszintű szűrő kiválasztása esetén a jelentésoldal csak a nyugati régióra vonatkozó adatokat tartalmazza.

Bárki, aki megtekinti a jelentést, kezelheti ezeket a szűrőket.

### <a name="view-only-those-filters-applied-to-a-visual"></a>Csak a vizualizációra alkalmazott szűrők megtekintése

Egy adott vizualizációra alkalmazott szűrők alaposabb vizsgálatához vigye az egérmutatót a vizualizáció fölé a ![Szűrőikon képernyőképe](media/end-user-report-filter/power-bi-filter-icon.png) szűrőikon megjelenítéséhez. Válassza ki ezt a szűrőikont a vizualizációra ható összes szűrőt, szeletelőt stb. tartalmazó előugró ablak megjelenítéséhez. Az előugró ablakon található szűrők ugyanazok, amelyek a **Szűrők** panelen is megjelennek.

![Képernyőfelvétel a szűrők listájáról, amelyen nyilak mutatják, hogy ezek a szűrők hol találhatók a Szűrők panelen.](media/end-user-report-filter/power-bi-hover-visual-filter.png)

Ebben a nézetben a következő szűrőtípusok jelenhetnek meg:

- Alapszintű szűrők

- Szeletelők

- Keresztkijelölés

- Keresztszűrés

- Speciális szűrők

- Felső N szűrők

- Relatív dátum szerinti szűrők

- Szinkronszűrők

- Belefoglalási/kizárási szűrők

- URL-címen keresztül átadott szűrők

A következő példában:

1. Látható, hogy az oszlopdiagram esetében keresztszűrés történt.

1. Az **Included** azt jelzi, hogy a keresztszűrő a **Segment** értékre vonatkozik, és három ilyen van.

1. A **Negyedévre** egy szeletelő lett alkalmazva.

1. A **Region** szűrő lett alkalmazva erre a jelentésoldalra.

1. Az **isVanArsdel** és a **Year** szűrő lett alkalmazva erre a vizualizációra.

![Képernyőkép egy jelentésről és annak szűrőiről, amelyen a szűrők listájának számozása megfelel a fenti számozott listának.](media/end-user-report-filter/power-bi-visual-pop-up.png)

### <a name="search-in-a-filter"></a>Keresés szűrőben

Egy szűrő olykor hosszú értéklistával rendelkezhet. A keresőmezővel keresse meg, és válassza ki a kívánt értéket.

![Képernyőkép a szűrőben történő keresés bemutatására.](media/end-user-report-filter/power-bi-fiter-search.png)

### <a name="display-filter-details"></a>Szűrő részleteinek megjelenítése

A szűrők megértéséhez vessen egy pillantást az elérhető értékekre és számokra.  Ha az egérmutatót a szűrő neve melletti nyílra viszi, majd kiválasztja a nyilat, megtekintheti a szűrő részleteit.
  
![Képernyőkép egy szűrőről, amelyen a nyugati régió van kiválasztva.](media/end-user-report-filter/power-bi-expand-filter.png)

### <a name="change-filter-selections"></a>Szűrők beállításának módosítása

Az adatokkal kapcsolatos megállapítások kinyerésének egyik módja a szűrők használata. A szűrők kiválasztott beállításait a mező neve melletti legördülő nyílra kattintva lehet módosítani.  A szűrőtől és a Power BI által szűrt adattípusoktól függően számos lehetőség érhető el az egyszerű listából való kiválasztástól a dátum- vagy számtartományok megadásáig. Az alábbi speciális szűrő esetében módosítottuk a **Total Units YTD** szűrőt a fatérképen, hogy az érték 2000 és 3000 között legyen. Látható, hogy ennek hatására eltűnik a Prirum a fatérképről.
  
![Képernyőkép egy jelentésről és a szűrőiről, amelyen a Fashion Direct van kiválasztva.](media/end-user-report-filter/power-bi-filter-treemap.png)

> [!TIP]
> Egyszerre több szűrőérték kiválasztásához tartsa lenyomva a CTRL billentyűt. A legtöbb szűrő támogatja a több elem kiválasztását.

### <a name="reset-filter-to-default"></a>Szűrő alaphelyzetbe állítása

Ha szeretné visszaállítani a szűrőkön végzett összes módosítást, válassza a felső menüsávon a **Visszaállítás alapértelmezettre** lehetőséget.  Ez visszaállítja a szűrők eredeti állapotát, amelyet a jelentés tervezője állított be.

![Képernyőkép a Visszaállítás alapértelmezettre lehetőségről.](media/end-user-report-filter/power-bi-reset.png)

### <a name="clear-a-filter"></a>Szűrők törlése

Ha csak egy szűrő esetében szeretné megadni az **(Összes)** beállítást, a szűrő neve melletti radír ikonnal ![Képernyőkép a radír ikonról](media/end-user-report-filter/power-bi-eraser-icon.png) kikapcsolhatja a szűrőt.
  
<!--  too much detail for consumers

## Types of filters: text field filters
### List mode
Ticking a checkbox either selects or deselects the value. The **All** checkbox can be used to toggle the state of all checkboxes on or off. The checkboxes represent all the available values for that field.  As you adjust the filter, the restatement updates to reflect your choices. 

![list mode filter](media/end-user-report-filter/power-bi-restatement-new.png)

Note how the restatement now says "is Mar, Apr or May".

### Advanced mode
Select **Advanced Filtering** to switch to advanced mode. Use the dropdown controls and text boxes to identify which fields to include. By choosing between **And** and **Or**, you can build complex filter expressions. Select the **Apply Filter** button when you've set the values you want.  

![advanced mode](media/end-user-report-filter/power-bi-advanced.png)

## Types of filters: numeric field filters
### List mode
If the values are finite, selecting the field name displays a list.  See **Text field filters** &gt; **List mode** above for help using checkboxes.   

### Advanced mode
If the values are infinite or represent a range, selecting the field name opens the advanced filter mode. Use the dropdown and text boxes to specify a range of values that you want to see. 

![advanced filter](media/end-user-report-filter/power-bi-dropdown-and-text.png)

By choosing between **And** and **Or**, you can build complex filter expressions. Select the **Apply Filter** button when you've set the values you want.

## Types of filters: date and time
### List mode
If the values are finite, selecting the field name displays a list.  See **Text field filters** &gt; **List mode** above for help using checkboxes.   

### Advanced mode
If the field values represent date or time, you can specify a start/end time when using Date/Time filters.  

![datetime filter](media/end-user-report-filter/pbi_date-time-filters.png)

-->

## <a name="next-steps"></a>Következő lépések

Tudnivalók arról, hogyan és miért történik [keresztszűrés és keresztkiemelés a vizualizációknál a jelentésoldalakon](end-user-interactions.md)