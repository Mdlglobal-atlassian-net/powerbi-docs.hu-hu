---
title: Gombok használata a Power BI-ban
description: A Power BI-jelentésekhez gombokat adhat, amelyek az alkalmazásokéhoz hasonlóvá teszik a jelentés működését, és mélyebb interakciót kínálnak a felhasználókkal.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/12/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: c703a4b67b642af5199413e80ff1e140905a2338
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83298550"
---
# <a name="use-buttons-in-power-bi"></a>Gombok használata a Power BI-ban
A Power BI-ban elérhető **gombokkal** alkalmazásokhoz hasonlóan működő jelentéseket hozhat létre, melyekben a felhasználók az elemekre kattintva és mutatva interaktívabban használhatják a Power BI-tartalmakat. Gombokat a **Power BI Desktopban** és a **Power BI szolgáltatásban** is felvehet a jelentésekhez. Ha a jelentéseket a Power BI szolgáltatásban osztja meg, az alkalmazásokéhoz hasonló felületet kínálhat a felhasználóknak.

![Gombok a Power BI-ban](media/desktop-buttons/power-bi-buttons.png)

## <a name="create-buttons-in-reports"></a>Gombok létrehozása jelentésekben

### <a name="create-a-button-in-power-bi-desktop"></a>Gomb létrehozása a Power BI Desktopban

A **Power BI Desktopban** gomb beszúrásához válassza a **Beszúrás** menüszalag **Gombok** elemét. Ez után kiválaszthatja a kívánt gombot az elérhető lehetőségek legördülő menüjéből, ahogy azt az alábbi kép szemlélteti. 

![Gomb vezérlő hozzáadása a Power BI Desktopban](media/desktop-buttons/power-bi-button-dropdown.png)

### <a name="create-a-button-in-the-power-bi-service"></a>Gomb létrehozása a Power BI szolgáltatásban

A **Power BI szolgáltatásban** gomb létrehozásához nyissa meg a jelentést Szerkesztés nézetben. Válassza a felső menüsáv **Gombok** elemét, majd válassza ki a kívánt gombot az elérhető lehetőségek legördülő menüjéből, ahogy azt az alábbi kép szemlélteti. 

![Gomb vezérlő hozzáadása a Power BI szolgáltatásban](media/desktop-buttons/power-bi-button-service-dropdown.png)

## <a name="customize-a-button"></a>Gomb testreszabása

Az eljárás a továbbiakban ugyanaz, akár a Power BI Desktopban, akár a Power BI szolgáltatásban hozta létre a gombot. Ha kijelöl egy gombot a jelentésvásznon, a **Vizualizációk** panelen láthatja a gomb testreszabásának különféle lehetőségeit. Be- és kikapcsolhatja például a **Gomb szövegét** a **Vizualizációk** panel vonatkozó kártyáján lévő csúszkával. Módosíthatja emellett a gomb ikonját, kitöltését és címét, a gomb kiválasztásakor a jelentésen végrehajtandó műveletet, valamint egyéb tulajdonságokat is testreszabhat.

![Gomb formázása Power BI-jelentésben](media/desktop-buttons/power-bi-button-properties.png)

## <a name="set-button-properties-when-idle-hovered-over-or-selected"></a>A tétlen, a rámutatott és a választott gombállapot tulajdonságainak megadása

A Power BI a gombok három állapotát különbözteti meg: tétlen (a gomb alapértelmezett megjelenése), rámutatott és választott (más néven *kattintott*). A **Vizualizációk** panel sok kártyája állapotonként módosítható, így a gombokat rugalmasan testreszabhatja.

A **Vizualizációk** panel alábbi kártyáival módosíthatja a gomb formázását vagy működését a fenti három állapot mindegyike esetében:

* Gomb szövege
* Ikon
* Körvonal
* Kitöltés

Ha szeretné megadni a gomb formázását az egyes állapotokhoz, bontsa ki a kártyák egyikét, és válasszon a kártya tetején megjelenő legördülő menüből. Az alábbi képen láthatja a kibontott **Ikon** kártyán megjelenő legördülő menüt, mellyel választhat a három állapot közül.

![A gombok három állapota a Power BI-jelentésekben](media/desktop-buttons/power-bi-button-format.png)


## <a name="select-the-action-for-a-button"></a>Gombművelet megadása

Megadhatja, hogy milyen művelet legyen végrehajtva, amikor a felhasználó a gombot választja a Power BI-ban. A gombműveletek beállításait a **Vizualizációk** panel **Művelet** kártyáján találhatja meg.

![Gombművelet megadása a Power BI Desktopban](media/desktop-buttons/power-bi-button-action.png)

Az alábbi gombműveleteket választhatja:

- A **Vissza** lehetőség visszairányítja a felhasználót a jelentés előző oldalára. Ez jól használható a részletező oldalakon.
- A **Könyvjelző** lehetőség megjeleníti az aktuális jelentéshez definiált egyik könyvjelzőhöz tartozó jelentésoldalt. Tovább információk: [Könyvjelzők a Power BI-ban](desktop-bookmarks.md). 
- A **Részletezés (előzetes verzió)** könyvjelző használata nélkül egy, az általa végzett kijelölésnek megfelelően szűrt részletező oldalra viszi a felhasználót. További információ: [Részletezési gombok jelentésekben](desktop-drill-through-buttons.md).
- Az **Oldalnavigáció** a jelentés egy másik oldalára viszi a felhasználót, szintén könyvjelzők használata nélkül. További részleteket a cikk [Oldalnavigáció létrehozása](#create-page-navigation) című szakaszában talál.
- A **Q&A** új **Q&A Explorer**-ablakot nyit meg. 

Egyes gombokhoz automatikusan ki van választva egy alapértelmezett művelet. A **Q&A** gombtípusnál például automatikusan be lesz állítva a **Q&A** lehetőség alapértelmezett műveletként. A **Q&A Explorer** ablakról bővebben [ebben a blogbejegyzésben](https://powerbi.microsoft.com/blog/power-bi-desktop-april-2018-feature-summary/#Q&AExplorer) tájékozódhat.

Tesztelheti is a jelentéséhez létrehozott gombokat úgy, hogy a *CTRL* billentyűt lenyomva tartva kattint a kívánt gombra. 

### <a name="create-page-navigation"></a>Oldalnavigáció létrehozása

Az **Oldalnavigáció** **Művelet**-típussal gyorsan kialakíthat egy teljes navigációs felületet anélkül, hogy könyvjelzőket kellene mentenie vagy kezelnie.

Oldalnavigációs gomb beállításához hozzon létre egy **Oldalnavigáció** művelettípusú gombot, majd válassza ki a **Cél** oldalt.

![Oldalnavigáció művelet](media/desktop-buttons/power-bi-page-navigation.png)

Gyorsan készíthet egyéni navigációs panelt. Így elkerülheti, hogy könyvjelzőket kelljen szerkeszteni és kezelni a navigációs panelen megjelenő oldalak megadásához.

![Navigációs panel létrehozása](media/desktop-buttons/power-bi-build-navigation-pane.png)

Emellett feltételesen formázhatja us az elemleírást, ahogyan a többi gombtípus esetében is.

## <a name="next-steps"></a>További lépések
A gombokhoz hasonló vagy azokkal együtt használható funkciókkal kapcsolatos részletesebb információkat az alábbi cikkekben talál:

* [Részletezés használata Power BI-jelentésekben](desktop-drillthrough.md)
* [Elemzések megosztása és történetek felépítése a Power BI könyvjelzőivel](desktop-bookmarks.md)

