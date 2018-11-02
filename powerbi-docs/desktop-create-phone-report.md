---
title: A Power BI telefonos alkalmazásokhoz optimalizált jelentések létrehozása
description: Megtudhatja, hogyan lehet optimalizálni a Power BI telefonos alkalmazásainak jelentésoldalait a kifejezetten a telefonra tervezett jelentésverzió létrehozásával.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 09/14/2018
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 22f4d6bf3c715c390c9760593ba5afdc72ce3bf7
ms.sourcegitcommit: 698b788720282b67d3e22ae5de572b54056f1b6c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/17/2018
ms.locfileid: "45973954"
---
# <a name="create-reports-optimized-for-the-power-bi-phone-apps"></a>A Power BI telefonos alkalmazásokhoz optimalizált jelentések létrehozása
Kényelmesebbé teheti a jelentések megtekintését a telefonokon futó mobilalkalmazásokban, ha létrehoz egy, kifejezetten a telefonokra tervezett jelentésverziót. A Power BI Desktopban és a Power BI szolgáltatásban a jelentés telefonra való optimalizálása a vizualizációk átrendezését és átméretezését, esetleg egyes vizualizációk kihagyását jelenti a kényelmes használat érdekében. Emellett [*rugalmas* vizualizációkat](#optimize-a-visual-for-any-size) és [rugalmas szeletelőket](#enhance-slicers-to-to-work-well-in-phone-reports) is létrehozhat, amelyek megfelelően átméretezhetők a telefonon való megtekintéshez. Ha a jelentéshez szűrőket is hozzáad, azok automatikusan megjelennek a telefonos jelentésben. A jelentés olvasói is láthatják őket, és a használatukkal szűrhetik a jelentés adatait.

![Optimalizált jelentés egy telefonon](media/desktop-create-phone-report/desktop-create-phone-report-1.png)

## <a name="lay-out-a-report-page-for-the-phone"></a>Jelentésoldal telefonra optimalizált elrendezése

Miután létrehozott egy jelentést, optimalizálhatja azt a telefonon történő megjelenítésre.

1. A Power BI Desktop **Nézet** lapján válassza a **Telefonos elrendezés** lehetőséget.  
   
    ![Telefonos elrendezés ikon](media/desktop-create-phone-report/desktop-create-phone-report-3.png)
   
    A Power BI szolgáltatásban válassza a **Jelentés szerkesztése** > **Telefonos elrendezés** lehetőséget.

    Megjelenik egy üres telefonos vászon. Az eredeti jelentésoldalon lévő minden vizualizáció fel van sorolva a jobb oldali Vizualizációk panelen.

3. Ha hozzá szeretne adni egy vizualizációt a telefonos elrendezéshez, húzza azt a Vizualizációk panelről a telefonos vászonra.
   
    A telefonos jelentések rács elrendezésűek. Ahogy a vizualizációkat a mobil vászonra húzza, azok a rácsra illeszkednek.
   
    ![Vizualizáció áthúzása](media/desktop-create-phone-report/desktop-create-phone-report-4.gif)
   
    A telefonos jelentésoldalhoz a fő jelentésoldalon lévő mindegyik vizualizációt is hozzáadhatja, vagy kiválaszthat néhányat, amelyeket hozzá szeretne adni. Egy-egy vizualizációt csak egyszer adhat meg.

4. A rácson átméretezheti a vizualizációkat, ahogy az irányítópultokon és mobil irányítópultokon lévő csempék esetében tenné.
   
   A telefonos jelentések rácsa a különféle telefonok méretének megfelelően átméreteződik, így a jelentés kis és nagy képernyőjű telefonokon egyaránt jól fog kinézni.
   
   ![Vizualizációk átméretezése](media/desktop-create-phone-report/desktop-create-phone-report-5.gif)

## <a name="optimize-a-visual-for-any-size"></a>Vizualizációk optimalizálása bármely méretre
Beállíthatja, hogy az irányítópulton vagy a jelentésben lévő vizualizációk *rugalmas* elrendezésűek legyenek, és a képernyő méretétől függően dinamikusan a lehető legtöbb adatot és elemzést jelenítsék meg egyszerre. 

A vizualizáció méretének változásával a Power BI átrangsorolja az adatnézet elemeit, például eltávolítja a kitöltéseket, vagy automatikusan áthelyezi a jelmagyarázatot a vizualizáció tetejére, hogy az egyre kisebb méretű vizualizáció változatlanul áttekinthető maradjon.

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

## <a name="view-optimized-and-unoptimized-reports-on-a-phone"></a>Optimalizált és nem optimalizált jelentések megtekintése telefonon
A telefonos mobilalkalmazásokban a Power BI automatikusan észleli, hogy melyik jelentés optimalizált és melyik nem. Ha egy jelentésnek létezik telefonra optimalizált verziója, a Power BI telefonos alkalmazás automatikusan a telefonos módban nyitja meg a jelentést.

Ha a jelentésnek nincsen telefonra optimalizált változata, a jelentés a nem optimalizált fekvő tájolásban nyílik meg.  

Ha a telefonos jelentés megtekintése közben a telefont fekvő tájolásba fordítja, a jelentés átvált az eredeti elrendezés szerinti nem optimalizált nézetbe, akár optimalizálva van, akár nem.

Ha csak egyes oldalak vannak optimalizálva, álló tájolásban egy üzenet jelenik meg, miszerint a jelentés fekvő tájolásban tekinthető meg.

![Nem optimalizált telefonos oldal](media/desktop-create-phone-report/desktop-create-phone-report-9.png)

A jelentések olvasói a telefont oldalra fordítva fekvő tájolásban tekinthetik meg az oldalt. További információk a [telefonra optimalizált Power BI-jelentések használatáról](consumer/mobile/mobile-apps-view-phone-report.md).

## <a name="next-steps"></a>További lépések
* [Power BI-irányítópult telefonos nézetének létrehozása](service-create-dashboard-mobile-phone-view.md)
* [Telefonra optimalizált Power BI-jelentések megtekintése](consumer/mobile/mobile-apps-view-phone-report.md)
* [Bármely méretre optimalizált rugalmas vizualizációk létrehozása](visuals/desktop-create-responsive-visuals.md)
* További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

