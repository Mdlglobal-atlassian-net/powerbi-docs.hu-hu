---
title: A jelentés Szűrők paneljének bemutatása
description: Szűrő hozzáadása jelentéshez az ügyfeleknek készült Power BI szolgáltatásban
author: mihart
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: cb3947ec7aaf6d67a22eb1d7543a57e66e87f5f3
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "79114444"
---
# <a name="take-a-tour-of-the-report-filters-pane"></a>Ismerkedés a jelentések Szűrők panelével

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Ez a cikk a jelentések **Szűrők** paneljét mutatja be a Power BI szolgáltatásban. A szűrőkkel új megállapításokat nyerhet ki az adatokból.

Az adatok szűrésének számos módja érhető el a Power BI-ban. A szűrőkkel kapcsolatos további információkért tekintse meg a [Power BI- jelentések szűrőivel és kiemeléseivel](../power-bi-reports-filters-and-highlighting.md) foglalkozó részt.

![Képernyőkép egy jelentésről a böngészőben, amelyen a nyíl a Szűrők beállításra mutat.](media/end-user-report-filter/power-bi-report.png)

## <a name="working-with-the-report-filters-pane"></a>A jelentések Szűrők panelének használata

Amikor a munkatársa megoszt Önnel egy jelentést, mindenképp keresse meg a **Szűrők** panelt. Előfordulhat, hogy össze van csukva a jelentés jobb szélén. Kattintson rá a kibontáshoz.

![Képernyőkép a jelentésről, amelyen a Szűrők panel ki van bontva.](media/end-user-report-filter/power-bi-expand-filter-pane.png)

A **Szűrők** panel olyan szűrőket tartalmaz, amelyekkel a jelentés *tervezője* látta el a jelentést. A *felhasználók* kezelhetik a meglévő szűrőket és menthetik a módosításokat, azonban nem adhatnak hozzá új szűrőket a jelentéshez. A fenti képernyőképen a tervező például három oldalszintű szűrőt vett fel: **Szegmens = mind**, **Év = 2014** és **Régió = Középső**. Kezelheti és módosíthatja ezeket a szűrőket, de nem adhat hozzá egy negyedik oldalszintű szűrőt.

A Power BI szolgáltatásban a jelentések megőrzik a **Szűrők** panelen végzett módosításokat. A szolgáltatás emellett a jelentés mobilos verziójára is alkalmazza őket. 

A **Szűrők** panelnek a tervező alapértelmezett értékeire való visszaállításához válassza ki a felső menüsáv **Visszaállítás alapértelmezettre** lehetőségét.

![A Visszaállítás alapértelmezettre ikon képernyőképe.](media/end-user-report-filter/power-bi-reset-icon.png) 

> [!NOTE]
> Ha nem jelenik meg **Visszaállítás alapértelmezettre** lehetőség, akkor lehetséges, hogy a jelentés *készítője* letiltotta azt. A *jelentéskészítő* egyes szűrőket is zárolhat, hogy Ön ne módosíthassa azokat.

## <a name="view-all-the-filters-for-a-report-page"></a>Jelentésoldal összes szűrőjének megtekintése

A **Szűrők** panel a tervező által a jelentéshez adott összes szűrőt megjeleníti. A **Szűrők** panel egyben az a terület is, ahol a szűrőkkel kapcsolatos információk megtekinthetőek és kezelhetőek. Mentse az elvégzett módosításokat vagy a **Visszaállítás alapértelmezettre** beállítással állítsa vissza az eredeti szűrőbeállításokat.

Ha menteni szeretné a módosításokat, létrehozhat egy személyes könyvjelzőt is. További információért tekintse meg [a könyvjelzőket](end-user-bookmarks.md) bemutató cikket.

A **Szűrők** panel különböző típusú jelentésszűrőket kezel és jelenít meg: jelentés, jelentésoldal és vizualizáció.

Ebben a példában egy olyan vizualizációt választottunk, amelyhez három szűrő tartozik. A jelentésoldalon szintén találhatók szűrők, ezek **Az ezen a lapon megtalálható szűrők** fejléc alatt vannak felsorolva. Emellett a teljes jelentés rendelkezik a **Date** szűrővel.

![Képernyőkép egy jelentésről a vizualizáció és a kapcsolódó szűrők megjelenítésével.](media/end-user-report-filter/power-bi-filters-pane.png)

Némelyik szűrő mellett az **(Összes)** szó szerepel. Az **(Összes)** azt jelenti, hogy a szűrő az összes értékre kiterjed. A fenti képernyőképen a **Segment (Összes)** azt jelzi, hogy a jelentésoldal az összes termékszegmens adatait tartalmazza. 

Bárki, aki megtekinti a jelentést, kezelheti ezeket a szűrőket.

### <a name="view-only-those-filters-applied-to-a-visual"></a>Csak a vizualizációra alkalmazott szűrők megtekintése

Egy adott vizualizációra alkalmazott szűrők alaposabb vizsgálatához vigye az egérmutatót a vizualizáció fölé a ![Szűrőikon képernyőképe](media/end-user-report-filter/power-bi-filter-icon.png) szűrőikon megjelenítéséhez. Válassza ki ezt a szűrőikont a vizualizációra ható összes szűrőt, szeletelőt stb. tartalmazó előugró ablak megjelenítéséhez. A felugró ablakban látható szűrők között szerepelnek azok, amelyek a **Szűrők** panelen jelentek meg, valamint a kijelölt vizualizációt érintő további szűrők.

![Képernyőfelvétel a szűrők listájáról, amelyen nyilak mutatják, hogy ezek a szűrők hol találhatók a Szűrők panelen.](media/end-user-report-filter/power-bi-hover-filters.png)

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

Ebben a példában:
1. A **Belefoglalva** szakaszból tudjuk, hogy a vizualizáción keresztszűrés van érvényben. Ez azt jelenti, hogy Utah, Colorado és Texas állam ki van jelölve ennek a jelentésoldalnak egy másik vizualizációján. Ebben az esetben ez a térkép. A három állam kijelölése megakadályozza, hogy bármely más állam adatai megjelenjenek a kiválasztott sávdiagramon.  

1. A **Dátum** a jelentés összes oldalára alkalmazott szűrő.

1. A **Régió = Középső** és az **Év = 2014** szűrők erre a jelentésoldalra vannak alkalmazva.

4. A **Gyártó = VanArsdel, Natura, Aliqui vagy Pirum** szűrő erre a vizualizációra érvényes.


### <a name="search-in-a-filter"></a>Keresés szűrőben

Egy szűrő olykor hosszú értéklistával rendelkezhet. A keresőmezővel keresse meg, és válassza ki a kívánt értéket.

![Képernyőkép a szűrőben történő keresés bemutatására.](media/end-user-report-filter/power-bi-search.png)

### <a name="display-filter-details"></a>Szűrő részleteinek megjelenítése

A szűrők megértéséhez vessen egy pillantást az elérhető értékekre és számokra.  Ha az egérmutatót a szűrő neve melletti nyílra viszi, majd kiválasztja a nyilat, megtekintheti a szűrő részleteit.
  
![Képernyőkép egy szűrőről, amelyen a nyugati régió van kiválasztva.](media/end-user-report-filter/power-bi-filter-expand.png)

### <a name="change-filter-selections"></a>Szűrők beállításának módosítása

Az adatokkal kapcsolatos megállapítások kinyerésének egyik módja a szűrők használata. A szűrők kiválasztott beállításait a mező neve melletti legördülő nyílra kattintva lehet módosítani.  A szűrőtől és a Power BI által szűrt adattípusoktól függően számos lehetőség érhető el az egyszerű listából való kiválasztástól a dátum- vagy számtartományok megadásáig. Az alábbi speciális szűrő esetében módosítottuk a **Total Units YTD** szűrőt a fatérképen, hogy az érték 2000 és 3000 között legyen. Látható, hogy ennek hatására eltűnik a Pirum a fatérképről.
  
![Képernyőkép egy jelentésről és a szűrőiről, amelyen a fatérkép vizualizáció van kijelölve.](media/end-user-report-filter/power-bi-treemap-filters.png)

> [!TIP]
> Egyszerre több szűrőérték kiválasztásához tartsa lenyomva a CTRL billentyűt. A legtöbb szűrő támogatja a több elem kiválasztását.

### <a name="reset-filter-to-default"></a>Szűrő alaphelyzetbe állítása

Ha szeretné visszaállítani a szűrőkön végzett összes módosítást, válassza a felső menüsávon a **Visszaállítás alapértelmezettre** lehetőséget.  Ez visszaállítja a szűrők eredeti állapotát, amelyet a jelentés tervezője állított be.

![Képernyőkép a Visszaállítás alapértelmezettre lehetőségről.](media/end-user-report-filter/power-bi-reset-icon.png)

### <a name="clear-a-filter"></a>Szűrők törlése

A szűrő alaphelyzetbe (Mind) állításához törölje az a szűrő neve melletti radír ikon kiválasztásával.

![A Radír ikon képernyőképe.](media/end-user-report-filter/power-bi-eraser.png)
  
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