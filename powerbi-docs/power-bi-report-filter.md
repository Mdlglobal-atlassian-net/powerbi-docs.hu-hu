---
title: A Power BI-jelentésekben elérhető új szűrési felület
description: A Power BI szűrői új funkciókat és új megjelenést kapnak.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/18/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 148f4881f78b5bba9b6936f5688ba6aaea3a0145
ms.sourcegitcommit: dc0258bb4f647ff646c6fff2aaffa29b413aa2df
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68346224"
---
# <a name="the-new-filter-experience-in-power-bi-reports"></a>A Power BI-jelentésekben elérhető új szűrési felület

A Power BI szűrői új funkciókkal és megjelenéssel rendelkeznek. Ha az új szűrőfelületet választja, a Szűrők panelt is formázhatja, hogy a megjelenése megegyezzen a jelentés többi részéével. A szűrőket zárolhatja, vagy akár el is rejtheti. Jelentés tervezésekor már egyáltalán nem jelenik meg a régi Szűrők panel a Vizualizációk panelen. A szűrők szerkesztését és formázását egyetlen Szűrők panelen végezheti. 

![Új szűrőfunkciók](media/power-bi-report-filter/power-bi-filter-reading.png)

Jelentések tervezése során a következőket végezheti el az új, egyetlen Szűrők panelen:

- A szűrés alapjául szolgáló mezők felvétele és eltávolítása. 
- A szűrő állapotának módosítása.
- A szűrőpanel formázása és testreszabása, hogy a jelentés részeként hasson.
- Megadhatja, hogy a Szűrők panel alapértelmezés szerint meg legyen nyitva, vagy össze legyen csukva, amikor egy fogyasztó megnyitja a jelentést.
- Elrejtheti a teljes szűrőpanelt, vagy azokat a szűrőket, amelyeket nem kíván megmutatni a jelentés fogyasztóinak.
- Szabályozhatja, és akár könyvjelzőzheti is az új Szűrők panel láthatóságát, valamint megnyitott vagy összecsukott állapotát.
- Zárolhat szűrőket, ha nem szeretné, hogy a fogyasztók szerkesszék őket.

Az új szűrési felülettel a jelentés felhasználói a vizualizációk fölé vitt kurzorral megjeleníthetik a vizualizációt befolyásoló összes szűrő és szeletelő csak olvasható listáját.

![Egy vizualizáció szűrőinek listája](media/power-bi-report-filter/power-bi-filter-visual.png)

## <a name="turn-on-the-new-filter-experience"></a>Az új szűrési felület bekapcsolása 

Az új jelentésekben alapértelmezés szerint be van kapcsolva az új szűrési felület. Az új felületet a Power BI Desktop vagy a Power BI szolgáltatás meglévő jelentéseihez is használhatja.

### <a name="turn-on-new-filters-for-an-existing-report-in-power-bi-desktop"></a>Új szűrők bekapcsolása meglévő jelentéshez a Power BI Desktopban

1. A Power BI Desktopban egy meglévő jelentésben válassza a **Fájl** > **Lehetőségek és beállítások** > **Beállítások** lehetőséget.
2. A bal oldali navigációs sáv **Aktuális fájl** területén válassza a **Jelentésbeállítások** szakaszt.
3. A **Szűrési felület** alatt jelölje be a **Frissített szűrőpanel engedélyezése, valamint a szűrők megjelenítése a jelentés vizualizációjának fejlécében** lehetőséget.

### <a name="turn-on-new-filters-for-an-existing-report-in-the-service"></a>Új szűrők bekapcsolása meglévő jelentéshez a szolgáltatásban

1. A Power BI szolgáltatásban válassza a **Jelentések** fület egy munkaterület tartalomlistájában.
2. Keresse meg az engedélyezni kívánt jelentést, majd válassza a **Beállítások** ikont ![Jelentés beállításai ikon](media/power-bi-report-filter/power-bi-settings-icon.png) a jelentés mellett.
3. A **Szűrési felület** alatt jelölje be a **Frissített szűrőpanel engedélyezése, valamint a szűrők megjelenítése a jelentés vizualizációjának fejlécében** lehetőséget.

    ![A frissített szűrők paneljének engedélyezése](media/power-bi-report-filter/power-bi-service-filter-enable.png)

## <a name="view-filters-for-a-visual-in-reading-mode"></a>Vizualizáció szűrőinek megtekintése olvasási módban

Ha olvasási módban egy vizualizáció szűrőikonja fölé viszi a kurzort, felugrik egy panel az összes szűrővel, szeletelővel és minden mással, ami a vizualizációt befolyásolja. A felugró szűrőpanel ugyanúgy formázható, mint a szűrőpanel. 

![Egy vizualizációt befolyásoló szűrők](media/power-bi-report-filter/power-bi-filter-per-visual.png)

Ebben a nézetben a következő szűrőtípusok jelennek meg: 
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

## <a name="build-the-new-filters-pane"></a>Az új Szűrők panel felépítése

Az új Szűrők panel az engedélyezése után a jelentésoldaltól jobbra jelenik meg, alapértelmezés szerint a jelentés aktuális beállításainak megfelelően formázva. Az új Szűrők panel használatával konfigurálhatja a belefoglalandó szűrőket, és módosíthatja a meglévőket az új panelen. Az új Szűrők panelen az jelenik meg, amit a jelentés fogyasztói fognak látni, miután Ön közzéteszi a jelentést. 

1. A jelentés felhasználói alapértelmezés szerint láthatják a Szűrők panelt. Ha nem szeretné, hogy lássák, válassza a **Szűrők** melletti szem ikont.

    ![Power BI-szűrők – szem ikon](media/power-bi-report-filter/power-bi-filter-eye.png)

2. Az új Szűrők panel kialakítását kezdje azzal, hogy a kívánt mezőket vizualizáció-, lap- vagy jelentésszintű szűrőként áthúzza az új Szűrők panelre.

Amikor vizualizációt ad egy jelentésvászonhoz, a Power BI automatikusan felvesz egy szűrőt a Szűrők panelre a vizualizációban szereplő mezők mindegyikéhez. 

## <a name="lock-or-hide-filters"></a>Szűrők zárolása vagy elrejtése

Az egyes szűrőkártyákat zárolhatja vagy el is rejtheti. Ha zárol egy szűrőt, akkor a jelentés fogyasztói azt láthatják, de nem szerkeszthetik. Ha elrejti, akkor látni sem fogják. A szűrőkártyák elrejtése általában akkor hasznos, ha az üres vagy nem várt értékek kizárására használt tisztítószűrőket kívánja elrejteni. 

- A **Szűrő zárolása** vagy a **Szűrő elrejtése** ikont az új Szűrők panelen jelölheti be, és ugyanott szüntetheti is meg a kijelölést a szűrőkártyákon.

   ![Szűrők elrejtése vagy zárolása](media/power-bi-report-filter/power-bi-filter-lock-hide.png)

Amikor ezeket a beállításokat ki- vagy bekapcsolja az új Szűrők panelen, a módosítások azonnal tükröződnek a jelentésben. A rejtett szűrők nem jelennek meg a vizualizációk felugró szűrőablakában.

Az új Szűrők panel állapotát úgy is konfigurálhatja, hogy kövesse a jelentések könyvjelzőit. A panel megnyitott, bezárt és látható állapota is könyvjelzőzhető.
 
## <a name="format-the-new-filters-pane"></a>Az új Szűrők panel formázása

A felületet jelentős újdonsága, hogy a Szűrők panel a jelentés megjelenéséhez és működéséhez igazodva formázható. A Szűrők panel a jelentés minden oldalához külön formázható. A következő elemeket formázhatja: 

- Háttérszín
- Háttér áttetszősége
- Szegély be- vagy kikapcsolása
- Szegély színe
- Fej- és lábléc betűtípusa, színe és szövegmérete

Ezeket az elemeket szűrőkártyákhoz is formázhatja attól függően, hogy alkalmazva lettek (valamire beállítva), vagy elérhetők (a tartalmuk törölve van): 

- Háttérszín
- Háttér áttetszősége
- Szegély: be- vagy kikapcsolva
- Szegély színe
- Betűtípus, szín és szövegméret
- Beviteli mező színe

### <a name="format-the-filters-pane-and-cards"></a>A Szűrők panel és a kártyák formázása

1. A jelentésben kattintson magára a jelentésre vagy a háttérre (*háttérkép*), majd a **Vizualizációk** panelen válassza a **Formátum** lehetőséget. 
    Itt találja meg a formázási lehetőségeket a jelentésoldalhoz, a háttérképhez, valamint a Szűrők panelhez és a szűrőkártyákhoz is.

    ![A Formázás ikon kiválasztása](media/power-bi-report-filter/power-bi-filter-format.png)    

1. Bontsa ki a **Szűrő panelt**, és állítsa be a háttér, az ikonok és a bal szegély színét a jelentésoldalhoz illően.

    ![A szűrőpanel kibontása](media/power-bi-report-filter/power-bi-filter-format-pane-font.png)

1. Bontsa ki a **Szűrőkártyák** elemet, és állítsa be az **Elérhető** és az **Alkalmazott** színt és szegélyt. Ha az elérhető és az alkalmazott kártyákhoz más színt ad meg, akkor nyilvánvaló lesz, hogy mely szűrők lettek alkalmazva. 
  
    ![A Szűrőkártyák elem kibontása](media/power-bi-report-filter/power-bi-filter-format-card-font.png)

## <a name="theming-for-filter-pane"></a>Témák a Szűrők panelhez
A szűrőpanel alapértelmezett beállításai témafájllal módosíthatók. Az alábbi kódrészlet-minta segít az első lépéseknél:

 
```
"outspacePane": [{ 

"backgroundColor": {"solid": {"color": "#0000ff"}}, 

"foregroundColor": {"solid": {"color": "#00ff00"}}, 

"transparency": 50, 

"titleSize": 35, 

"headerSize": 8, 

"fontFamily": "Georgia", 

"border": true, 

"borderColor": {"solid": {"color": "#ff0000"}} 

}], 

"filterCard": [ 

{ 

"$id": "Applied", 

"transparency": 0, 

"backgroundColor": {"solid": {"color": "#ff0000"}}, 

"foregroundColor": {"solid": {"color": "#45f442"}}, 

"textSize": 30, 

"fontFamily": "Arial", 

"border": true, 

"borderColor": {"solid": {"color": "#ffffff"}}, 

"inputBoxColor": {"solid": {"color": "#C8C8C8"}} 

}, 

{ 

"$id": "Available", 

"transparency": 40, 

"backgroundColor": {"solid": {"color": "#00ff00"}}, 

"foregroundColor": {"solid": {"color": "#ffffff"}}, 

"textSize": 10, 

"fontFamily": "Times New Roman", 

"border": true, 

"borderColor": {"solid": {"color": "#123456"}}, 

"inputBoxColor": {"solid": {"color": "#777777"}} 

}] 
```

## <a name="sort-the-filter-pane"></a>A szűrőpanel rendezése

Az egyéni rendezés lehetősége is a szűrési felület egyik újdonsága. A jelentéskészítők húzással tetszőleges sorrendbe átrendezhetik a szűrőket.

![Szűrők sorrendjének módosítása](media/power-bi-report-filter/power-bi-filter-sort.gif)

A szűrők alapértelmezés szerint betűrendben vannak elhelyezve. Egyéni sorrend kialakításához elég új helyre áthúzni egy szűrőt. A szűrők csak azon a szinten belül rendezhetők át, amelyre érvényesek – például a vizualizációk szintjén, az oldal szintjén vagy a jelentés szintjén.

## <a name="improved-filters-pane-accessibility"></a>A Szűrők panel továbbfejlesztett akadálymentessége

Az új Szűrők panelhez továbbfejlesztettük a billentyűzetnavigációt. A tabulátorral a Szűrők panel minden részére eljuthat, a helyi menü billentyűvel vagy a Shift+F10 kombinációval pedig megnyithatja a helyi menüt.

![A Szűrők panel akadálymentessége](media/power-bi-report-filter/power-bi-filter-accessible.png)

## <a name="rename-filters"></a>Szűrők átnevezése
A Szűrők panel szerkesztésekor kattintson duplán a címre, hogy szerkeszteni tudja. Átnevezni akkor érdemes, ha az a cél, hogy a szűrőkártya érthető legyen a végfelhasználók számára. Vegye figyelemben, hogy a szűrőkártya átnevezése *nem* változtatja meg a mező megjelenített nevét a mezőlistában. Csak a szűrőkártyán használt megjelenített nevet módosítja.

![Szűrő átnevezése](media/power-bi-report-filter/power-bi-filter-rename.png)

## <a name="restrict-changes-to-filter-type"></a>Szűrőtípus módosításának korlátozása

A jelentés beállításainak Szűrési felület szakaszában beállíthatja, hogy a felhasználók megváltoztathatják-e a szűrő típusát.

![Szűrőtípus módosításának tiltása](media/power-bi-report-filter/power-bi-filter-restrict-change.png)

## <a name="next-steps"></a>Következő lépések

Próbálja ki az új szűrési felületet. Küldjön visszajelzést erről a funkcióról, és arról, hogy hogyan tehetnénk még jobbá ezt a felületet a [Power BI Ideas webhelyen](https://ideas.powerbi.com/forums/265200-power-bi). 

- [A jelentésszűrők használata](consumer/end-user-report-filter.md)
- [Szűrők és kiemelések a jelentésekben](power-bi-reports-filters-and-highlighting.md)
- [Különböző szűrők a Power BI-ban](power-bi-report-filter-types.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
