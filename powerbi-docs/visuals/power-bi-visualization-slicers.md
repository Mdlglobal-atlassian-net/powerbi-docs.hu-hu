---
title: Szeletelők a Power BI-ban
description: A szűrés másféle lehetőségét kínáló Power BI-szeletelőkkel az adathalmaz a jelentés más vizualizációiban szereplő részére szűkíthető.
author: v-thepet
ms.reviewer: ''
featuredvideoid: zIZPA0UrJyA
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 11/04/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 97ad95346715cd5ad38f41d6e7b9df3cc7493f40
ms.sourcegitcommit: c395fe83d63641e0fbd7c98e51bbab224805bbcc
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74265405"
---
# <a name="slicers-in-power-bi"></a>Szeletelők a Power BI-ban

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Tegyük fel, hogy a jelentést olvasók számára az összesítő értékesítési metrikák megjelenítése mellett az egyes körzeti vezetők teljesítményét és a különböző időkereteket is ki szeretné mutatni. Létrehozhat különálló jelentéseket vagy összehasonlító diagramokat. Vagy használhat szeletelőket is. A szűrés másféle lehetőségét kínáló szeletelőkkel az adathalmaz a jelentés más vizualizációiban szereplő részére szűkíthető. 

Ez az útmutató az ingyenes [Kiskereskedelmi elemzési minta](../sample-retail-analysis.md) használatával mutatja be a lista és dátumtartomány típusú szeletelők létrehozásának, formázásának és használatának lépéseit. Jó szórakozást a szeletelők formázásának és használatának felfedezéséhez! 

![Szeletelő animációja](media/power-bi-visualization-slicers/slicer2.gif)

## <a name="when-to-use-a-slicer"></a>Mikor érdemes szeletelőt használni?
A szeletelő kitűnően alkalmas a következő célokra:

* Gyakran használt vagy fontos szűrők megjelenítése a jelentésvásznon a könnyebb elérhetőség érdekében.
* Az aktuális szűrt állapot egyszerűbb megjelenítése legördülő lista használata nélkül. 
* Az adattáblák szükségtelen és rejtett oszlopai alapján történő szűrés.
* Jobban szűrt jelentések létrehozása azáltal, hogy a szeletelőket a lényeges vizualizációk mellett helyezi el.

A Power BI-szeletelők nem támogatják a következőket:

- Beviteli mezők
- Lehatolás


## <a name="create-slicers"></a>Szeletelők létrehozása

**Új szeletelő létrehozása az adatok körzeti vezető szerinti szűréséhez**

1. Töltse le a [Kiskereskedelmi elemzési minta PBIX-fájlját](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. A Power BI Desktop menüsávban válassza a **Fájl** > **Megnyitás** elemet.
   
1. Keresse meg a **Retail Analysis sample PBIX.pbix** fájlt, majd válassza a **Megnyitás** lehetőséget.

1. A bal oldali ablaktáblán válassza a **Jelentés** ikont ![Jelentés ikon](media/power-bi-visualization-kpi/power-bi-report-view.png) a fájl jelentés nézetben való megnyitásához.

1. Új szeletelő létrehozásához az **Áttekintés** lapon (miközben a vásznon semmi ne legyen kiválasztva), a **Vizualizációk** ablaktáblán jelölje be a **Szeletelő** ikont ![szeletelő ikon](media/power-bi-visualization-slicers/slicer-icon.png). 

1. Az új szeletelőt kijelölve válassza a **Mezők** panel **Körzet** > **DM** elemét a szeletelő kitöltéséhez. 

    Az új szeletelő most ki van töltve a körzeti vezetők nevének és a jelölőnégyzeteiknek listájával.
    
    ![A körzeti vezetők neveivel kitöltött szeletelő](media/power-bi-visualization-slicers/power-bi-new-slicer.png)
    
1. A szeletelő számára a vásznon levő egyéb elemek átméretezésével, illetve elmozdításával biztosíthat helyet. Vegye figyelembe, hogy ha túl kicsire méretezi át a szeletelőt, akkor levágja az elemeit. 

1. Jelöljön be neveket a szeletelőn, és figyelje meg a hatást az oldalon levő más vizualizációkon. A nevek bejelölésének megszüntetéséhez kattintson ismét a jelölőnégyzetükre; egynél több név bejelöléséhez tartsa lenyomva a **Ctrl** billentyűt. Az összes név kiválasztása ugyanazzal az eredménnyel jár, mintha egyet sem választana ki. 

1. Vagy válassza a **Vizualizációk** ablaktáblán a **Formátum** elemet (festőhenger ikont) a szeletelő formázásához. 

   A lehetőségek száma túl nagy ahhoz, hogy mindegyiket itt ismertessük – kísérletezzen a kívánt szeletelő létrehozásához. Az alábbi képen az első szeletelő vízszintes tájolással és színes háttérrel rendelkezik az elemekhez. A második szeletelő a szabványosabb külső érdekében függőleges tájolással és színes szöveggel rendelkezik.

   ![Formázott szeletelő](media/power-bi-visualization-slicers/power-bi-filter-examples.png)

   >[!TIP]
   >Alapértelmezés szerint a szeletelő listaelemei növekvő sorrendbe vannak rendezve. A rendezés csökkenő irányba való módosításához válassza a szeletelő jobb felső sarkában levő három pontot ( **...** ), majd a **Rendezés csökkenő sorrendben** lehetőséget.

**Új szeletelő létrehozása az adatok dátumtartomány szerinti szűréséhez**

1. Válassza ki a jelentés **Áttekintés** lapját. Ha semmi sincs kiválasztva a jelentés vászonján, a **Mezők** panelen válassza a **Tárolás** >  **OpenDate** lehetőséget.

    Ez a művelet kitölti a **Vizualizációk** panel **Értékek** mezőjét egy új vizualizáció létrehozásához.

1. Az új vizualizáció szeletelővé való átalakításához a jelentésben kiválasztott új vizualizációval válassza a **Vizualizációk** panelen a **Szeletelő** ikont. Ez az **OpenDate** szeletelő egy csúszkavezérlő, amely fel van töltve a dátumtartománnyal.
    
    ![OpenDate-vizualizáció létrehozása](media/power-bi-visualization-slicers/power-bi-date-slicer.png)

1. A szeletelő számára a szeletelő és a vásznon levő egyéb elemek átméretezésével, illetve elmozdításával biztosíthat helyet. Bár a szeletelő méretének módosításával a csúszka is átméreteződik, ha a szeletelőt túl kicsire méretezi, akkor a csúszka eltűnik, és a dátumokat a rendszer levágja. 

1. A csúszkával különféle dátumtartományokat jelölhet ki, illetve egy dátummezőt kiválasztva dátumot is megadhat vagy felugró naptárt is használhat a pontosabb kijelöléshez. Figyelje meg a hatást a lapon lévő többi vizualizáción.
    
    >[!NOTE]
    >A numerikus és a dátum/idő adattípusok alapértelmezés szerint tartomány típusú csúszka szeletelőt eredményeznek. A Power BI 2018. februári frissítésétől kezdődően az egész szám adattípusú tartománycsúszkák már egész számértékekhez igazodnak, a tizedesjegyek megjelenítése helyett. 

1. A szeletelő típusának módosításához a szeletelő kijelölt állapota mellett mutasson az egérmutatóval a szeletelő jobb felső részére, válassza ki a lefelé mutató nyíl ikont, majd válasszon egy lehetőséget, például a **Lista** vagy az **Előtt** elemet. Figyelje meg a szeletelő megjelenésének és a választási lehetőségeknek a módosulását. 
 
    ![Új tartomány a szeletelőhöz](media/power-bi-visualization-slicers/power-bi-between-slicer.png)


A dátum és numerikus típusú szeletelők létrehozásáról és használatáról a következő videóból vagy [A numerikustartomány-szeletelő használata a Power BI Desktopban](../desktop-slicer-numeric-range.md) című cikkből tájékozódhat bővebben.
   > [!NOTE]
   > Ez a videó a Power BI Desktop egy régebbi verzióját használja.
   > 
   > 

<iframe width="560" height="315" src="https://www.youtube.com/embed/zIZPA0UrJyA" frameborder="0" allowfullscreen></iframe> 

## <a name="control-which-page-visuals-are-affected-by-slicers"></a>A lap szeletelők által érintett vizualizációinak kijelölése
Alapértelmezés szerint a jelentésoldalakon levő szeletelők az adott oldalon levő összes többi vizualizációra, valamint egymásra is hatással vannak. Az imént létrehozott lista és dátum típusú szeletelők értékeinek kiválasztása közben figyelje meg a többi vizualizációra gyakorolt hatásokat. A szűrt adatok a mindkét szeletelőben kijelölt értékek metszetét képezik. 

A vizualizációk interakcióival egyes oldalvizualizációkat kivonhat a többi vizualizáció hatása alól. Az **Áttekintés** oldalon a **Teljes értékesítési szórásnégyzet pénzügyi hónap és körzeti vezető szerint** diagram átfogó összehasonlító adatokat jelenít meg a körzeti vezetőkről havi bontásban, amit érdemes mindig megjelenített állapotban tartani. A vizualizációk interakcióival megakadályozhatja, hogy a szeletelők kijelölései szűrést végezzenek ezen a diagramon. 

1. Lépjen a jelentés **Áttekintés** oldalára, majd válassza ki a korábban létrehozott **DM** szeletelőt.

1. A Power BI Desktop menüben, a **Vizuális eszközök** részben válassza a **Formátum** menüt, majd válassza az **Interakciók szerkesztése** lehetőséget.
   
   A szűrővezérlők ![szűrővezérlők](media/power-bi-visualization-slicers/filter-controls.png) az egyéb vizualizációk felett jelennek meg az oldalon, egy-egy **Szűrő** és **Nincs** lehetőséggel. Kezdetben a **Szűrő** lehetőség van előre kiválasztva az összes vezérlőn.
   
1. Válassza a **Teljes értékesítési szórásnégyzet pénzügyi hónap és körzeti vezető szerint** diagram feletti **Nincs** lehetőséget a szűrővezérlőben, hogy a **DM** szeletelő ne szűrje. 

1. Válassza az **OpenDate** szeletelőt, majd válassza a **Teljes értékesítési szórásnégyzet pénzügyi hónap és körzeti vezető szerint** diagram feletti **Nincs** lehetőséget, hogy a szeletelő ne szűrje. 

   Így a **Teljes értékesítési szórásnégyzet pénzügyi hónap és körzeti vezető szerint** diagram a szeletelőkben levő nevek és dátumtartományok kiválasztása esetén is változatlan marad.

További információ az interakciók szerkesztéséről: [A vizualizációk interakciójának módosítása a Power BI-jelentésekben](../service-reports-visual-interactions.md).

## <a name="sync-and-use-slicers-on-other-pages"></a>Más oldalakon levő szeletelők szinkronizálása és használata
A Power BI 2018. februári frissítésétől kezdve a szeletelők szinkronizálhatók és egy jelentés bármely – vagy akár az összes – oldalán felhasználhatók. 

Az aktuális jelentésben a **Körzeti havi értékesítés** oldal egy **Körzeti vezető** szeletelővel rendelkezik, de mi történik, ha az **Új üzletek** oldalon is használni szeretnénk ezt a szeletelőt? Az **Új üzletek** oldalon szerepel egy szeletelő, de csak az **Üzlet nevének** információit tartalmazza. A **Szeletelők szinkronizálása** panelen ezekhez az oldalakhoz szinkronizálhatja a **Körzeti vezető** szeletelőjét, hogy bármely oldal szeletelőinek kijelölései mindhárom oldalon hatással legyenek a vizualizációkra.

1. Válassza a Power BI Desktop **Nézet** menüjének **Szeletelők szinkronizálása** elemét.

    ![Szeletelők szinkronizálásának kijelölései](media/power-bi-visualization-slicers/power-bi-slicer-view-sync.png)

    A **Szeletelők szinkronizálása** panel a **Szűrők** és a **Vizualizációk** panel között jelenik meg.

    ![Szeletelők szinkronizálása panel](media/power-bi-visualization-slicers/power-bi-slicer-sync-pane.png)

1. A jelentés **Körzeti havi értékesítés** oldalán válassza a **Körzeti vezető** szeletelőt. 

    Mivel már létrehozott egy **Körzeti vezető** (**DM**) szeletelőt az **Áttekintés** oldalon, a **Szeletelők szinkronizálása** panel a következőképpen jelenik meg:
    
    ![Körzeti havi értékesítés szinkronizálása szeletelő](media/power-bi-visualization-slicers/9-sync-slicers.png)
    
1. A **Szeletelők szinkronizálása** panel **Szinkronizálás** oszlopában válassza ki az **Áttekintés**, **Körzeti havi értékesítés** és **Új Üzletek** lapokat. 

    Ezen kijelölés miatt a rendszer mindhárom oldallal szinkronizálja a **Körzeti havi értékesítés** szeletelőt. 
    
1. A **Szeletelők szinkronizálása** panel **Látható** oszlopában válassza az **Új üzletek** oldalt. 

    Ezen kijelölés miatt a **Körzeti havi értékesítés** szeletelő mindhárom oldalon látható. A **Szeletelők szinkronizálása** panel most a következőképpen jelenik meg:

    ![Oldalak kiválasztása a szeletelők szinkronizálásában](media/power-bi-visualization-slicers/power-bi-sync-slicer-finished.png)

1. Figyelje meg a szeletelő szinkronizálásának és más oldalakon való megjelenítésének hatásait. Figyelje meg, hogy a **Körzeti havi értékesítés** oldalon a **Körzeti vezető** szeletelő most már az **Áttekintés** oldalon levő szeletelővel azonos kijelöléseket jeleníti meg. Az **Új üzletek** oldalon most látható a **Körzeti vezető** szeletelő, és a kijelölései hatással vannak az **Üzlet neve** szeletelőben látható kijelölésekre. 
    
    >[!TIP]
    >Bár a szinkronizált oldalakon a szeletelő kezdetben ugyanolyan méretben és pozícióban jelenik meg, mint az eredeti oldalon, a különböző oldalakon levő szinkronizált szeletelők egymástól függetlenül is áthelyezhetők, átméretezhetők és formázhatók. 

    >[!NOTE]
    >Ha egy szeletelőt egy adott oldalra szinkronizál, de nem teszi azt láthatóvá az adott oldalon, akkor a más oldalakon elvégzett szeletelőkijelölések továbbra is szűrik az adatokat az oldalon.
 
## <a name="format-slicers"></a>Szeletelők formázása
A szeletelő típusától függően különböző formázási beállítások érhetők el. A **Vízszintes** tájolás, a **Rugalmas** elrendezés és az **Elem** színezés használatával a szokásos listaelemek helyett gombokat vagy csempéket hozhat létre, és a szeletelő elemeket a különböző képernyőméretekhez és elrendezésekhez igazodóvá teheti.  

1. Jelölje ki bármelyik oldalon a **Körzeti vezető** szeletelőt, majd a **Vizualizációk** panelen válassza a **Formázás** ikont ![Formázás ikon](media/power-bi-visualization-slicers/power-bi-paintroller.png) a formázási vezérlők megjelenítéséhez. 
    
    ![Kijelölés formázása](media/power-bi-visualization-slicers/3-format.png)
    
1. A beállítások megjelenítéséhez és szerkesztéséhez kattintson a kategóriák melletti legördülőmenü-nyilakra. 

### <a name="general-options"></a>Általános beállítások
1. A **Formátum** területen válassza az **Általános** lehetőséget, válasszon egy piros színt a **Körvonal színe** területen, majd módosítsa a **Körvonal vastagságát***2* értékre. 

    Ez a beállítás módosítja a fejléc és az elemek körüli körvonalak és az aláhúzások színét és vastagságát.

1. **Tájolásként** alapértelmezés szerint a **Függőleges** érték van kiválasztva. Vízszintesen elrendezett csempékkel vagy gombokkal, és a szeletelőbe be nem férő elemek eléréséhez görgetőnyilakkal rendelkező szeletelő előállításához válassza a **Vízszintes** lehetőséget.
    
    ![Általános kijelölések](media/power-bi-visualization-slicers/4-horizontal.png)
    
1. A szeletelő elemek méretének és elrendezésének a megjelenítő képernyő és a szeletelő mérete alapján történő módosításához kapcsolja **be** a **Rugalmas** elrendezést. 

    Lista típusú szeletelők esetén a rugalmas elrendezés megakadályozza az elemek kisebb képernyőkön történő levágását. Ez csak vízszintes tájolásban érhető el. Tartománycsúszka típusú szeletelők esetén a rugalmas formázás módosítja a csúszka stílusát, és rugalmasabb átméretezést biztosít. Kis méretben mindkét típusú szeletelő szűrőikonná változik.
    
    ![Rugalmas elrendezés beállítása](media/power-bi-visualization-slicers/5-responsive.png)
    
    >[!NOTE]
    >A rugalmas elrendezéssel járó módosítások felülírhatják a megadott fejléc- és elemformázási beállításokat. 
    
1. A szeletelő helyzete és mérete numerikus pontossággal is megadható az **X pozíció**, **Y pozíció**, **Szélesség** és **Magasság** mezőben, vagy a szeletelő közvetlenül a vásznon is áthelyezhető és átméretezhető. 

    Kísérletezzen különböző elemméretekkel és -elrendezésekkel, majd figyelje meg, hogyan módosul ezeknek megfelelően a rugalmas formázás. Ezek a beállítások csak akkor érhetők el, ha a vízszintes tájolást választja. 

    ![Vízszintes beállítások](media/power-bi-visualization-slicers/6-buttons.png)

A vízszintes tájolásokról és a rugalmas elrendezésekről az [Átméretezhető rugalmas szeletelő létrehozása a Power BI-ban](../power-bi-slicer-filter-responsive.md) című cikk tartalmaz bővebb információt.

### <a name="selection-controls-options-list-slicers-only"></a>Kijelölési vezérlők beállításai (csak lista típusú szeletelők esetén)
1. A **Kijelölési vezérlők** területen kapcsolja **Be** **„Az összes kijelölése” beállítás megjelenítése** lehetőséget **Az összes kijelölése** elem hozzáadásához a szeletelőhöz. 

    **„Az összes kijelölése” beállítás megjelenítése** lehetőség alapértelmezés szerint **Ki** van kapcsolva. Ha engedélyezve van, a beállítás váltásával kijelölheti az összes elemet, illetve megszüntetheti az összes elem kijelölését. Ha az összes elemet kijelöli, akkor egy elem kijelölésével megszüntetheti a kijelölését, vagyis *nemleges feltételű* szűrőtípust használhat.
    
    ![Kijelölési vezérlők](media/power-bi-visualization-slicers/7-select-all.png)
    
1. Kapcsolja **Ki** az **Egyetlen elem kijelölése** beállítást, hogy több elemet is kiválaszthasson a **Ctrl** billentyű lenyomva tartása nélkül. 

    Az **Egyetlen elem kijelölése** lehetőség alapértelmezés szerint **Be** van kapcsolva. Az elemek a kiválasztással egyenként kijelölhetők, a **Ctrl** billentyű lenyomva tartása mellett pedig több elem is kijelölhető. Az elemek ismételt kijelölésével megszüntethető azok kijelölése.

### <a name="title-options"></a>Cím beállításai
A **Cím** alapértelmezés szerint **Be** van kapcsolva. Ez a kijelölés a szeletelő tetején található adatmező nevét jeleníti meg. 
- Ebben az oktatóanyagban a következőképpen formázza a cím szövegét: 
   - **Betűszín**: piros
   - **Szövegméret**: **14 pt**
   - **Igazítás**: **Középre**
   - **Betűtípus**: **Arial Black**


### <a name="items-options-list-slicers-only"></a>Elemek beállításai (csak lista típusú szeletelők esetén)
1. Ebben az oktatóanyagban a következőképpen formázza az **Elemek** beállításait:
    - **Betűszín**: fekete
    - **Háttér**: világospiros
    - **Szövegméret**: **10 pt**
    - **Betűtípus**: **Arial**
 
1. A **Körvonal** beállításnál válassza a **Keret** lehetőséget, hogy minden elem köré keretet rajzoljon az **Általános** beállítások között megadott vonalvastagsággal és színnel. 
    
    ![Keret körvonalának beállításai](media/power-bi-visualization-slicers/8-formatted.png)
    
    >[!TIP]
    >- Az **Általános** > **Tájolás** > **Vízszintes** kijelölése esetén a nem kijelölt elemek a választott szöveg- és háttérszínnel, a kijelöltek pedig a rendszer alapértelmezése szerint általában fekete háttérrel és fehér szöveggel jelennek meg.
    >- Az **Általános** > **Tájolás > Függőleges** kijelölése esetén az elemek mindig a kiválasztott színekben látszanak, a bejelölt jelölőnégyzetek pedig mindig feketék. 

### <a name="datenumeric-inputs-and-slider-options-range-slider-slicers-only"></a>Dátum vagy numerikus adatbevitel és csúszkabeállítások (csak tartománycsúszka típusú szeletelők esetén)
- Lista típusú szeletelők esetén a dátum/numerikus adatbeviteli beállítások ugyanazok, mint az **Elemek** beállítások esetén, kivéve, ha nincs körvonal vagy aláhúzás lehetőség.
- A **csúszkabeállítások** lehetővé teszik a tartománycsúszka színének beállítását, illetve a csúszka **Ki** helyzetbe kapcsolását, ami csak a numerikus adatbevitelt hagyja meg.

### <a name="other-formatting-options"></a>Egyéb formázási lehetőségek
A további formázási lehetőségek alapértelmezés szerint **Ki** vannak kapcsolva. Kapcsolja **Be** ezeket a beállításokat a következők vezérléséhez: 
- **Háttér**: Háttérszínt ad meg a teljes szeletelőhöz, és beállítja annak átlátszóságát.
- **Zárolási helyzet**: Átméretezéskor megtartja a szeletelő képarányát.
- **Szegély**: Szegélyt rajzol a szeletelő köré, és beállítja annak színét. Ez a szeletelőszegély az **Általános** beállításoktól független, azok nincsenek hatással rá. 

## <a name="next-steps"></a>Következő lépések
További információért tekintse át a következő cikkeket:

- [Vizualizációtípusok a Power BI-ban](power-bi-visualization-types-for-reports-and-q-and-a.md)

- [Táblák a Power BI-ban](power-bi-visualization-tables.md)

