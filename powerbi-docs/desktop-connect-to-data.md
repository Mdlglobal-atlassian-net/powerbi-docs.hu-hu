---
title: Csatlakozás adatokhoz a Power BI Desktopban
description: Csatlakozás adatokhoz a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 0a582eb5c160685784c6db497353f92d2dd3d2cf
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514098"
---
# <a name="connect-to-data-in-power-bi-desktop"></a>Csatlakozás adatokhoz a Power BI Desktopban
A Power BI Desktop segítségével egyszerűen csatlakozhat az adatok egyre bővülő forrásaihoz. Ha nem rendelkezik a Power BI Desktoppal, itt [letöltheti](http://go.microsoft.com/fwlink/?LinkID=521662) és telepítheti.

A Power BI Desktopban *sokféle* adatforrás érhető el. Az alábbi kép bemutatja, hogyan csatlakozhat adatokhoz a **Fájl** menüszalag **Lekérdezés \> Továbbiak** menüpontjában.

![](media/desktop-connect-to-data/getdatavid_smallv2.gif)

## <a name="example-of-connecting-to-data"></a>Példa adatokhoz való csatlakozásra
Ebben a példában egy **webes** adatforráshoz csatlakozunk.

Vegyük például azt az esetet, ha valaki nyugdíjba megy, és olyan helyen szeretne élni, ahol sokat süt a nap, alacsonyak az adók és jó az egészségügyi ellátás. De az is lehet, hogy adatelemzőként van szüksége olyan információkra, amelyekkel segíthet az ügyfeleknek, például egy esőkabátgyártó ügyfélnek egy olyan helyre irányuló célzott értékesítésben, ahol *sokat* esik.

Mindkét esetben találhat olyan webes forrásanyagokat, amelyek releváns adatokat és egyéb információkat biztosítanak:

[*http://www.bankrate.com/finance/retirement/best-places-retire-how-state-ranks.aspx*](http://www.bankrate.com/finance/retirement/best-places-retire-how-state-ranks.aspx)

Válassza ki a **Lekérdezés \> Web** lehetőséget, és írja be a címet.

![](media/desktop-connect-to-data/connecttodata_3.png)

Amikor az **OK** gombra kattint, munkához lát a Power BI Desktop **Lekérdezés** funkciója. A Power BI Desktop csatlakozik a webes erőforráshoz, és a **Kezelő** ablak visszaadja a webhelyen talált találatokat. Ebben az esetben a webhelyen talált egy táblát (0. tábla) és a teljes dokumentumot. Minket a tábla érdekel, ezért azt választjuk ki a listáról. A **Kezelő** ablak megjelenít egy előnézetet.

![](media/desktop-connect-to-data/datasources_fromnavigatordialog.png)

Ezen a ponton szerkesztheti a lekérdezést, mielőtt betöltené a táblát. Ehhez válassza az ablak alján látható **Szerkesztés** gombot. Ha nem szeretné szerkeszteni, csak töltse be a táblát.

Ha a **Szerkesztés** lehetőséget választja, a rendszer betölti a táblát, és a Lekérdezésszerkesztő elindul. Megjelenik a **Lekérdezés beállításai** panel (ha nem, válassza a **Nézet** lehetőséget a menüszalagról, majd a **Megjelenítés \> Lekérdezés beállításai** lehetőséget a **Lekérdezés beállításai** panel megjelenítéshez). Ez a következőképpen néz ki.

![](media/desktop-connect-to-data/designer_gsg_editquery.png)

A pontszámok inkább szövegek, mint számok, nekünk pedig számokra van szükségünk. Ez nem jelent problémát. Csak kattintson a jobb gombbal az oszlop fejlécére, és válassza a **Típus módosítása \> Egész szám** lehetőséget a módosításukhoz. Ha egynél több oszlopot szeretne kijelölni, először jelöljön ki egy oszlopot, majd a **SHIFT** billentyűt lenyomva tartva jelölje ki a szomszédos oszlopokat, és kattintson a jobb gombbal az összes kijelölt oszlop módosításához. Nem egymás melletti oszlopokat a **CTRL** gomb segítségével jelölhet ki.

![](media/desktop-connect-to-data/designer_gsg_changedatatype.png)

A **Lekérdezés beállításai** **Alkalmazott lépések** területén minden végrehajtott módosítás megjelenik. Ahogy további módosításokat eszközöl az adatokon, a Lekérdezésszerkesztő mindent rögzít az **Alkalmazott lépések** szakaszban, ahol az elemeket szükség szerint törölheti, áttekintheti, átrendezheti vagy törölheti.

![](media/desktop-connect-to-data/designer_gsg_appliedsteps_changedtype.png)

A táblán további módosításokat a betöltés után is elvégezhet, de jelenleg ennyi elég is lesz. Ha végzett, válassza ki a **Bezárás és alkalmazás** lehetőséget a **Kezdőlap** menüszalagon, hogy a Power BI Desktop alkalmazza a módosításokat, és bezárja a Lekérdezésszerkesztőt.

![](media/desktop-connect-to-data/connecttodata_closenload.png)

Ha betöltődött az adatmodell, a Power BI Desktop **Jelentés** nézetében megkezdhetjük a vizualizációk létrehozását a mezők vászonra húzásával.

![](media/desktop-connect-to-data/connecttodata_dragontoreportview.png)

Ez persze egy egyszerű, egyetlen adatkapcsolattal rendelkező modell; a legtöbb Power BI Desktop-jelentés különböző, az igényei szerint alakított adatforrásokhoz csatlakozik, olyan kapcsolatokkal, amelyek részletes adatmodellt hoznak létre. 

## <a name="next-steps"></a>Következő lépések
A Power BI Desktop műveletek és lehetőségek széles tárházát tartalmazza. A program képességeivel kapcsolatos további információkért lásd az alábbi forrásanyagokat:

* [Mi az a Power BI Desktop?](desktop-what-is-desktop.md)
* [Lekérdezések áttekintése a Power BI Desktopban](desktop-query-overview.md)
* [Adatforrások a Power BI Desktopban](desktop-data-sources.md)
* [Adatok formázása és kombinálása a Power BI Desktoppal](desktop-shape-and-combine-data.md)
* [Gyakori lekérdezési feladatok a Power BI Desktopban](desktop-common-query-tasks.md)   

Szeretne visszajelzést küldeni? Használja a Power BI Desktop **Ötlet beküldése** menüelemét vagy keresse fel a [Közösségi visszajelzés](http://community.powerbi.com/t5/Community-Feedback/bd-p/community-feedback) oldalt. Kíváncsian várjuk a véleményét!

![](media/desktop-connect-to-data/sendfeedback.png)

