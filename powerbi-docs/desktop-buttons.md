---
title: Gombok használata a Power BI-ban
description: Gombok segítségével mélyebb interakciót kínáló, alkalmazásként működő jelentéseket és irányítópultokat hozhat létre a Power BI Desktop alkalmazásban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 9d884df7fdfa6d0f16e7963c00a1100186d70546
ms.sourcegitcommit: b11e908650379913d00673215e3eaf25d712b122
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/07/2019
ms.locfileid: "65239494"
---
# <a name="using-buttons-in-power-bi"></a>Gombok használata a Power BI-ban
A Power BI-ban elérhető **gombokkal** alkalmazásokhoz hasonlóan működő jelentéseket és irányítópultokat hozhat létre, melyekben a felhasználók az elemekre kattintva és mutatva interaktívabban használhatják a Power BI-tartalmakat. Adhat hozzá gombokat a jelentésekhez a **Power BI Desktop** alkalmazásban, majd megoszthatja vagy közzéteheti ezeket a jelentéseket a Power BI szolgáltatásban, hogy elérhetők legyenek a felhasználóknak alkalmazásként működő irányítópultokként.

![Gombok a Power BI-ban](media/desktop-buttons/desktop-buttons_01.png)

A **Power BI Desktop** alkalmazásban létrehozott gombok elérhetők a **Power BI szolgáltatásban** közzétett jelentésekben és irányítópultokban.

## <a name="creating-buttons-in-reports"></a>Gombok létrehozása a jelentésekben
Ha szeretne gombot létrehozni egy jelentésben a **Power BI Desktop** alkalmazással, válassza a **Kezdőlap** menüszalaglapon a **Gombok** lehetőséget. Ezután kiválaszthatja a kívánt gombot az elérhető lehetőségek legördülő menüjéből, ahogy azt az alábbi kép szemlélteti. 

![Gomb vezérlő hozzáadása a Power BI Desktopban](media/desktop-buttons/desktop-buttons_02.png)

Ha létrehoz egy gombot, majd kijelöli azt a jelentésvásznon, a **Vizualizációk** panelen láthatja a gomb testreszabásának különféle lehetőségeit. Be- és kikapcsolhatja például a **Gomb szövegét** a **Vizualizációk** panel vonatkozó kártyáján lévő csúszkával. Módosíthatja emellett a gomb ikonját, kitöltését és címét, a gombra való kattintáskor a jelentésen vagy az irányítópulton végrehajtott műveletet, illetve egyéb tulajdonságokat is testreszabhat.

![Gomb formázása a Power BI Desktopban](media/desktop-buttons/desktop-buttons_03.png)

## <a name="set-button-properties-when-idle-hovered-over-or-selected"></a>A tétlen, a rámutatott és a választott gombállapot tulajdonságainak megadása

A Power BI a gombok három állapotát különbözteti meg: tétlen (a gomb alapértelmezett megjelenése), rámutatott és választott (más néven *kattintott*). A **Vizualizációk** panel sok kártyája állapotonként módosítható, így a gombokat rugalmasan testreszabhatja.

A **Vizualizációk** panel alábbi kártyáival módosíthatja a gomb formázását vagy működését a fenti három állapot mindegyike esetében:

* Gomb szövege
* Ikon
* Körvonal
* Kitöltés

Ha szeretné megadni a gomb formázását az egyes állapotokhoz, bontsa ki a kártyák egyikét, és válasszon a kártya tetején megjelenő legördülő menüből. Az alábbi képen láthatja a kibontott **Körvonal** kártyán megjelenő legördülő menüt, mellyel választhat a három állapot közül:

![A gombok három állapota a Power BI Desktopban](media/desktop-buttons/desktop-buttons_04.png)


## <a name="select-the-action-for-a-button"></a>Gombművelet megadása

Megadhatja, hogy milyen művelet legyen végrehajtva, amikor a felhasználó a gombot választja a Power BI-ban. A gombműveletek beállításait a **Vizualizációk** panel **Művelet** kártyáján találhatja meg.

![Gombművelet megadása a Power BI Desktopban](media/desktop-buttons/desktop-buttons_05.png)

Az alábbi gombműveleteket választhatja:

* Vissza
* Könyvjelző
* Q&A

A **Vissza** lehetőség választása esetén a gomb visszairányítja a felhasználót a jelentés előző oldalára. Ez különösen hasznos lehet a részletező lapokon.

A **Könyvjelző** lehetőség választása esetén a gomb megjeleníti az aktuális jelentéshez definiált egyik könyvjelzőhöz tartozó jelentésoldalt. Ha szeretne, [többet is megtudhat a könyvjelzők Power BI-beli használatáról](desktop-bookmarks.md). 

A **Q&A** lehetőség választása esetén a gomb megjeleníti a **Q&A Explorer** ablakot. 

Egyes gombokhoz tartozik alapértelmezett művelet. A **Q&A** gombtípusnál például automatikusan be lesz állítva a **Q&A** lehetőség alapértelmezett műveletként. A **Q&A Explorer** ablakról bővebben [ebben a blogbejegyzésben](https://powerbi.microsoft.com/blog/power-bi-desktop-april-2018-feature-summary/#Q&AExplorer) tájékozódhat.

Tesztelheti is a jelentéséhez létrehozott gombokat úgy, hogy a *CTRL* billentyűt lenyomva tartva kattint a kívánt gombra. 

## <a name="next-steps"></a>Következő lépések
A gombokhoz hasonló vagy azokkal együtt használható funkciókkal kapcsolatos részletesebb információkat az alábbi cikkekben talál:

* [Részletezés használata a Power BI Desktopban](desktop-drillthrough.md)
* [Irányítópult-csempe vagy jelentésvizualizáció megjelenítése Fókusz módban](consumer/end-user-focus.md)
* [Elemzések megosztása és történetek felépítése a Power BI könyvjelzőivel](desktop-bookmarks.md)

