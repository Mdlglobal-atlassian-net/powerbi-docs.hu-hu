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
ms.date: 05/30/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: dcf62925d8e5eef07fb6295f8d8141413947f8fb
ms.sourcegitcommit: d88cc6a87d4ba82ad2c4d496a3634f927e4ac529
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/30/2019
ms.locfileid: "66413123"
---
# <a name="take-a-tour-of-the-report-filters-pane"></a>Ismerkedés a jelentések Szűrők panelével
Ez a cikk a jelentések szűrők panelének tekintse meg a Power BI szolgáltatásban vesz igénybe. A szűrők segítségével az adatok új elemzéseket deríthet fel.

Az adatok szűrésének számos módja áll rendelkezésre a Power BI-ban, ezért javasoljuk, hogy először olvassa el a [szűrőkkel és a kiemeléssel](../power-bi-reports-filters-and-highlighting.md) foglalkozó szakaszt.

![jelentés a böngészőben](media/end-user-report-filter/power-bi-browser-new2.png)

## <a name="working-with-the-report-filters-pane"></a>A jelentések Szűrők panelének használata
Amikor a munkatársa megoszt Önnel egy jelentést, mindenképp keresse meg a **Szűrők** panelt. Előfordulhat, hogy össze van csukva a jelentés jobb szélén. Kattintson rá a kibontáshoz.   

![jelentés a böngészőben](media/end-user-report-filter/power-bi-filter-pane.png)

A Szűrők panel olyan szűrőket tartalmaz, amelyekkel a jelentés *tervezője* látta el a jelentést. *A fogyasztók* , kezelhetik a meglévő szűrőket, és mentse a módosításokat, de nem adhatnak hozzá új szűrőket a jelentéshez. A fenti képernyőképen például a tervező két oldalszintű szűrőt adott hozzá: Szegmens és futó éves. Kezelheti és módosíthatja ezeket a szűrőket, de nem adhat hozzá egy harmadik oldalszintű szűrőt.

A Power BI szolgáltatásban a jelentések megtartják a szűrők panel választja ki, és ezek a módosítások is alkalmazzák őket a jelentés mobilos verziójára. A Szűrő panelnek a tervező alapértelmezett értékeire való visszaállításához válassza ki a felső menüsáv **Visszaállítás alapértelmezettre** lehetőségét.  

![Alapértelmezések visszaállítása](media/end-user-report-filter/power-bi-reset-to-default.png)   

## <a name="view-all-the-filters-for-a-report-page"></a>A jelentésoldal összes szűrők megjelenítése
A szűrők panel megjelenik a jelentés által hozzáadott összes szűrőt a *designer*. A szűrők panel is az a terület, ahol a szűrőkkel kapcsolatos információk megtekintéséhez és interakcióba lép velük. Mentheti a módosításokat, akkor győződjön meg arról, vagy használjon **visszaállítás alapértelmezettre** visszaállítani az eredeti szűrési beállítások.

Ha szeretné menteni a módosításokat, személyes könyvjelző is létrehozhat.  További információkért lásd: [könyvjelző hozzáadása egy jelentéshez](end-user-bookmarks.md).

Nincsenek számos különböző típusú Jelentésszűrők, amelyek jelenik meg, és a szűrők panelen, a felügyelt alkalmazott a vizualizációhoz, a jelentésoldal és a teljes jelentéshez.

Ebben a példában egy vizualizációt, 2 szűrőket választottuk ki. A jelentés oldalon is rendelkezik, alatt felsorolt szűrők a **ezen az oldalon szűrők** fejléc. És a teljes jelentés dátum szűrő van.

![szűrők listája](media/end-user-report-filter/power-bi-all-filters2.png)

Némelyik szűrő mellett a **Mind** szó szerepel, ami azt jelzi, hogy a szűrő az összes értékre kiterjed.  Ha például **Segment(All)** a fenti képernyőképen tudatja velünk, hogy a jelentésoldal összes termék szegmens adatait tartalmazza.  Másfelől, a lapszintű szűrő **régió van Nyugat** tudatja velünk, hogy a jelentésoldal csak tartalmazza az adatokat a nyugati régiójában.

Bárki, aki megtekinti a jelentést, kezelheti ezeket a szűrőket.

### <a name="view-only-those-filters-applied-to-a-visual"></a>Csak ezeket a szűrőket alkalmazott a vizualizációhoz megtekintése
Egy adott Vizualizáció alkalmazott szűrőkről közelebbről lekéréséhez a Vizualizáció megjelenítéséhez a szűrő ikon fölé ![ikon](media/end-user-report-filter/power-bi-filter-icon.png). Válassza ki a szűrő ikonjára a szűrőket, szeletelők és így tovább, amely hatással van a Vizualizáció egy előugró ablak. A szűrő az előugró ugyanazon jelenik meg a **szűrők** ablaktáblán. 

![szűrők listája](media/end-user-report-filter/power-bi-hover-visual-filter.png)

 
Az alábbiakban az ebben a nézetben jelenítheti szűrők típusai:
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



A példában az alábbi:
1. Láthatjuk, hogy az oszlopdiagram keresztszűrhető lett.
2. **Foglalt** tudatja velünk, hogy a keresztszűrés vonatkozik **szegmens**, és három járnak. 
3. A szeletelők alkalmazott **negyedév**.
4. **Régió** Ez a jelentés oldalon alkalmazott szűrő és
5. **isVanArsdel** és **év** vannak szűrők a vizualizációra.


![szűrők listája](media/end-user-report-filter/power-bi-visual-pop-up.png)

### <a name="search-in-a-filter"></a>Keresés szűrőben
Néha egy szűrő rendelkezhet értékek hosszú listáját. Használja a keresőmezőt, és jelölje ki a kívánt értéket. 

![Keresés szűrőben](media/end-user-report-filter/power-bi-fiter-search.png)

### <a name="display-filter-details"></a>Megjelenítési szűrő részletei
Szeretné megtudni, egy szűrőt, tekintse meg a rendelkezésre álló értékek és számát.  A szűrő részleteinek megtekintéséhez viszi, majd kijelöli a nyilat a szűrő neve mellett. 
  
![a kijelölt Lindseys megjelenítése](media/end-user-report-filter/power-bi-expand-filter.png)

### <a name="change-filter-selections"></a>Változás szűrési lehetőségek
Egy data összefüggéseket módja kezelhetik a szűrőket. A mező neve melletti legördülő nyílra használatával szűrőkiválasztást módosíthatja.  A szűrő és a szűrni kívánt adatok típusától függően a lehetőségek azonosítása dátumok vagy tartományok listáját egyszerű kijelölései fog terjedhet. Az alábbi speciális szűrő módosítottuk a szűrő **teljes egységek év elejétől számított** a fatérképen 2000 és 3000 kell esnie. Figyelje meg, hogy ezzel eltávolítja a fatérképen Prirum. 
  
![a kijelölt Fashion Direct megjelenítése](media/end-user-report-filter/power-bi-filter-treemap.png)

> [!TIP]
> Egyszerre több szűrőérték kijelöléséhez tartsa lenyomva a CTRL billentyűt. A legtöbb szűrők támogatja a többszörös kijelöléssel. 

### <a name="reset-filter-to-default"></a>Az alapértelmezett szűrő alaphelyzetbe állítása
Ha szeretne készíteni a tartományon kívül az összes módosítást a szűrőket, jelölje be végrehajtott **visszaállítás alapértelmezettre** a felső menüsávon.  Ez a szűrőket az eredeti állapotukba visszaáll a jelentés által beállított *designer*. 

![Alapértelmezések visszaállítása](media/end-user-report-filter/power-bi-reset-to-default.png)
    
### <a name="clear-a-filter"></a>Szűrők törlése
Ha van egy szűrő, adja meg, ha szeretné **(összes)** , törölje a jelölést a radír ikon kiválasztásával ![ radír ikonnal ](media/end-user-report-filter/power-bi-eraser-icon.png) a szűrő neve mellett.
  
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
[Ismerje meg, hogyan és miért történik keresztszűrés és keresztkiemelés a vizualizációknál a jelentésoldalakon.](end-user-interactions.md)