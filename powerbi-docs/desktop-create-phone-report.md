---
title: A telefonos alkalmazásokhoz optimalizált jelentések létrehozása
description: Megtudhatja, hogyan lehet optimalizálni a Power BI mobilalkalmazásainak jelentésoldalait a kifejezetten a telefonra és táblagépre tervezett jelentésverzió létrehozásával.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/10/2018
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 8808391d0794ec4a487526cc5bbe4216fe0f75a6
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54275318"
---
# <a name="create-reports-optimized-for-the-power-bi-mobile-apps"></a>A Power BI mobilalkalmazásokhoz optimalizált jelentések létrehozása
Javíthatja a felhasználói élményt a jelentések mobilalkalmazással, telefonon vagy táblagépen történő megtekintésénél. Létrehozhatja a jelentés kifejezetten telefonokra vagy táblagépekre tervezett álló tájolású elrendezését. A Power BI Desktopban és a Power BI szolgáltatásban a jelentés optimalizálása a vizualizációk átrendezését és átméretezését, jelenti a kényelmes használat érdekében. Nem szükséges mindegyiket felhasználni sem. Emellett [*rugalmas* vizualizációkat](#optimize-a-visual-for-any-size) és [rugalmas szeletelőket](#enhance-slicers-to-to-work-well-in-phone-reports) is létrehozhat, amelyek megfelelően átméretezhetők a telefonon való megtekintéshez. Ha a jelentéshez szűrőket is hozzáad, azok automatikusan megjelennek az optimalizált jelentésben. A jelentés olvasói is láthatják őket, és a használatukkal szűrhetik a jelentés adatait.

![Optimalizált jelentés egy telefonon](media/desktop-create-phone-report/desktop-create-phone-report-1.png)

## <a name="lay-out-a-portrait-version-of-a-report-page"></a>Jelentésoldal álló tájolású elrendezése

Miután létrehozott egy jelentést, optimalizálhatja azt a telefonon vagy táblagépen történő megjelenítésre.

1. A Power BI Desktop **Nézet** lapján válassza a **Telefonos elrendezés** lehetőséget.  
   
    ![Telefonos elrendezés ikon](media/desktop-create-phone-report/desktop-create-phone-report-3.png)
   
    A Power BI szolgáltatásban válassza a **Jelentés szerkesztése** > **Telefonos elrendezés** lehetőséget.

    Telefon formájú fekete vászon jelenik meg. Az eredeti jelentésoldalon lévő minden vizualizáció fel van sorolva a jobb oldali Vizualizációk panelen.

3. Ha hozzá szeretne adni egy vizualizációt a telefonos elrendezéshez, húzza azt a Vizualizációk panelről a telefonos vászonra.
   
    A telefonos jelentések rács elrendezésűek. Ahogy a vizualizációkat a mobil vászonra húzza, azok a rácsra illeszkednek.
   
    ![Vizualizáció áthúzása](media/desktop-create-phone-report/desktop-create-phone-report-4.gif)
   
    A telefonos jelentésoldalhoz a fő jelentésoldalon lévő mindegyik vizualizációt is hozzáadhatja, vagy kiválaszthat néhányat, amelyeket hozzá szeretne adni. Egy-egy vizualizációt csak egyszer adhat meg.

4. A rácson átméretezheti a vizualizációkat, ahogy az irányítópultokon és mobil irányítópultokon lévő csempék esetében tenné.
   
   A telefonos jelentések rácsa a különféle telefonok méretének megfelelően átméreteződik, így a jelentés kis és nagy képernyőjű telefonokon egyaránt jól fog kinézni.
   
   ![Vizualizációk átméretezése](media/desktop-create-phone-report/desktop-create-phone-report-5.gif)

## <a name="optimize-a-visual-for-any-size"></a>Vizualizációk optimalizálása bármely méretre
Az irányítópulton vagy a jelentésben a vizualizációkat *rugalmasra* is beállíthatja. Ezek a képernyő méretétől függően dinamikusan a lehető legtöbb adatot és megállapítást jeleníti meg egyszerre. 

A vizualizáció méretének változásával a Power BI átrangsorolja az adatnézet elemeit. Például eltávolítja a kitöltéseket, vagy automatikusan áthelyezi a jelmagyarázatot a vizualizáció tetejére, hogy az egyre kisebb méretű vizualizáció változatlanul áttekinthető maradjon.

![Rugalmas vizualizációk átméretezése](media/desktop-create-phone-report/desktop-create-phone-report-6.gif)

Vizualizációnként külön eldöntheti, hogy bekapcsolja-e a rugalmasságot. További információk a [vizualizációk optimalizálásáról](visuals/desktop-create-responsive-visuals.md).

## <a name="considerations-when-creating-phone-report-layouts"></a>Megfontolandó szempontok jelentések telefonos elrendezésének létrehozásához
* A többoldalas jelentések esetében eldöntheti, hogy mindegyik oldalt optimalizálja-e, vagy csak egyes oldalakat. 
* Ha adott meg háttérszínt egy adott jelentésoldalhoz, a telefonos jelentésben is ugyanaz lesz a háttérszín.
* A formázási beállítások nem vonatkozhatnak kizárólag a telefonos elrendezésre. A fő és a mobil elrendezés formázása megegyezik, például a betűméretek sem változnak.
* A vizualizációk megváltoztatásához, a formázásuk, adatkészleteik, szűrőik és bármely egyéb attribútumuk módosításához lépjen vissza a rendes jelentésszerkesztési módba.
* A Power BI alapértelmezett címeket és oldalelnevezéseket biztosít a mobilalkalmazások telefonos jelentéseihez. Ha a jelentés címeihez és oldalelnevezéseihez hozott létre szöveges vizualizációkat, ezeket nem feltétlenül érdemes szerepeltetnie a telefonos jelentésekben.     

## <a name="remove-a-visual-from-the-phone-layout"></a>Vizualizációk eltávolítása a telefonos elrendezésekből
* A vizualizációk eltávolításához kattintson az X gombra a telefonvásznon a vizualizáció jobb felső sarkában, vagy jelölje ki a vizualizációt, és nyomja le a **Delete** billentyűt.
  
   Ha itt távolítja el a vizualizációt, az csak a telefonos elrendezés vásznáról tűnik el. Magát a vizualizációt és az eredeti jelentést az eltávolítás nem érinti.
  
   ![Vizualizációk eltávolítása](media/desktop-create-phone-report/desktop-create-phone-report-7.gif)

## <a name="enhance-slicers-to-work-well-in-phone-reports"></a>Szeletelők optimalizálása a telefonos jelentésekhez
A szeletelők a jelentések adatainak szűrését teszik lehetővé a vásznon. Amikor szeletelőket tervez a rendes jelentésszerkesztő módban, módosíthatja egyes beállításukat, hogy jobban megfeleljenek a telefonos jelentésekben való használathoz:

* Döntse el, hogy a jelentés olvasói egyszerre csak egy vagy több elemet is kijelölhetnek-e.
* Helyezzen egy téglalapot a szeletelő köré, hogy a jelentés könnyebben beolvasható legyen.
* Állítsa a szeletelőt függőlegesre, vízszintesre vagy *rugalmasra*. 

Ha rugalmasra állítja a szeletelőt, akkor a méretének vagy az alakjának a módosításával bővül vagy szűkül a lehetőségek köre. Lehet magas, alacsony, széles és keskeny. Ha kellően kicsire alakítja, akkor csupán egy szűrőikon lesz belőle a jelentéslapon. 

![Rugalmas szeletők a Power BI-ban](media/desktop-create-phone-report/desktop-create-phone-report-8.png)

További információ a [rugalmas szeletelők létrehozásáról](power-bi-slicer-filter-responsive.md).

## <a name="publish-a-phone-report"></a>Telefonos jelentés közzététele
* A jelentés telefonos verziójának közzétételéhez [közzé kell tennie a fő jelentést Power BI Desktopból a Power BI szolgáltatásba](desktop-upload-desktop-files.md). Ezzel a telefonos verziót is közzéteszi.
  
    További információk [a megosztásról és az engedélyekről a Power BI-ban](service-how-to-collaborate-distribute-dashboards-reports.md).

## <a name="view-optimized-and-unoptimized-reports-on-a-phone-or-tablet"></a>Optimalizált és nem optimalizált jelentések megtekintése telefonon vagy tábalegépen
A telefonos mobilalkalmazásokban a Power BI automatikusan észleli, hogy melyik jelentés optimalizált és melyik nem. Ha egy jelentésnek létezik telefonra optimalizált verziója, a Power BI telefonos alkalmazás automatikusan a telefonos módban nyitja meg a jelentést.

Ha a jelentésnek nincsen telefonra optimalizált változata, a jelentés a nem optimalizált fekvő tájolásban nyílik meg.  

Ha a telefonos jelentés megtekintése közben a telefont fekvő tájolásba fordítja, a jelentés átvált az eredeti elrendezés szerinti nem optimalizált nézetbe, akár optimalizálva van, akár nem.

Ha csak egyes oldalak vannak optimalizálva, álló tájolásban egy üzenet jelenik meg, miszerint a jelentés fekvő tájolásban tekinthető meg.

![Nem optimalizált telefonos oldal](media/desktop-create-phone-report/desktop-create-phone-report-9.png)

A jelentések olvasói a telefont vagy a táblagépet oldalra fordítva fekvő tájolásban tekinthetik meg az oldalt. További információk az [álló tájolásra optimalizált Power BI-jelentések használatáról](consumer/mobile/mobile-apps-view-phone-report.md).

## <a name="next-steps"></a>Következő lépések
* [Power BI-irányítópult telefonos nézetének létrehozása](service-create-dashboard-mobile-phone-view.md)
* [Telefonra optimalizált Power BI-jelentések megtekintése](consumer/mobile/mobile-apps-view-phone-report.md)
* [Bármely méretre optimalizált rugalmas vizualizációk létrehozása](visuals/desktop-create-responsive-visuals.md)
* További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

