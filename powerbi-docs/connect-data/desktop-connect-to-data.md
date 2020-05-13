---
title: Kapcsolódás adatokhoz a Power BI Desktopban
description: Kapcsolódás adatokhoz a Power BI Desktopban
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/21/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 01f012aa2a1d6b0cd1c45c8a2c5b12d6954ff91b
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83347677"
---
# <a name="connect-to-data-sources-in-power-bi-desktop"></a>Kapcsolódás adatforrásokhoz a Power BI Desktop alkalmazásban

A Power BI Desktop segítségével egyszerűen csatlakozhat az adatok egyre bővülő forrásaihoz. Ha nem rendelkezik a Power BI Desktoppal, itt [letöltheti](https://go.microsoft.com/fwlink/?LinkID=521662) és telepítheti.

A Power BI Desktopban *sokféle* adatforrás érhető el. Az alábbi kép bemutatja, hogyan csatlakozhat adatokhoz a **Adatok beolvasása** > **Egyéb** > **Web** lehetőséggel.

![Adatok beolvasása a webről](media/desktop-connect-to-data/get-data-from-the-web.png)

## <a name="example-of-connecting-to-data"></a>Példa adatokhoz való csatlakozásra

Ebben a példában egy **webes** adatforráshoz csatlakozunk.

Tegyük fel, hogy nyugdíjba megy. Olyan helyen szeretne élni, ahol sokat süt a nap, alacsonyak az adók és jó az egészségügyi ellátás. De az is lehet, hogy adatelemzőként van szüksége olyan információkra, amelyekkel segíthet az ügyfeleknek, például egy esőkabátgyártó ügyfélnek egy olyan helyre irányuló célzott értékesítésben, ahol *sokat* esik.

Mindkét esetben találhat olyan webes forrásanyagokat, amelyek releváns adatokat és egyéb információkat biztosítanak:

[https://www.bankrate.com/finance/retirement/best-places-retire-how-state-ranks.aspx](https://www.bankrate.com/finance/retirement/best-places-retire-how-state-ranks.aspx)

Válassza az **Adatok beolvasása** > **Egyéb** > **Web** lehetőséget. A **Webről** mezőbe írja be a címet.

![Webes forrás címének megadása](media/desktop-connect-to-data/connecttodata_3.png)

Amikor az **OK** gombra kattint, munkához lát a Power BI Desktop *Lekérdezés* funkciója. A Power BI Desktop csatlakozik a webes erőforráshoz, és a **Kezelő** ablak visszaadja a webhelyen talált találatokat. Ebben az esetben a webhelyen talált egy táblázatot és a teljes dokumentumot. Minket a táblázat érdekel, ezért azt választjuk ki a listáról. A **Kezelő** ablak megjelenít egy előnézetet.

![Adatok előnézete a Kezelőben](media/desktop-connect-to-data/datasources_fromnavigatordialog.png)

Ezen a ponton szerkesztheti a lekérdezést, mielőtt betöltené a táblázatot. Ehhez válassza az ablak alján látható **Adatok átalakítása** lehetőséget. Ha nem szeretné szerkeszteni, csak töltse be a táblázatot.

A táblázat betöltéséhez és a Power Query-szerkesztő megnyitásához válassza az **Adatok átalakítása** lehetőséget. Megnyílik a **Lekérdezés beállításai** panel. Ha nem, válassza a menüszalag **Nézet** elemét, majd a **Lekérdezés beállításai** lehetőséget a **Lekérdezés beállításai** panel megjelenítéséhez. Ez a következőképpen néz ki.

![A Power Query-szerkesztő a lekérdezési beállításokkal](media/desktop-connect-to-data/designer_gsg_editquery.png)

A pontszámok inkább szövegek, mint számok, nekünk pedig számokra van szükségünk. Nem gond. Kattintson a jobb gombbal az oszlop fejlécére, és válassza a **Típus módosítása** >  **Egész szám** lehetőséget a módosításhoz. Ha egynél több oszlopot szeretne kijelölni, először jelöljön ki egy oszlopot, majd a Shift billentyűt lenyomva tartva jelölje ki a szomszédos oszlopokat, és kattintson a jobb gombbal az összes kijelölt oszlop módosításához. Nem egymás melletti oszlopokat a Ctrl billentyű segítségével jelölhet ki.

![Adattípus egész számmá változtatása](media/desktop-connect-to-data/designer_gsg_changedatatype.png)

A **Lekérdezés beállításai** **ALKALMAZOTT LÉPÉSEK** területén minden végrehajtott módosítás megjelenik. Ahogy további módosításokat eszközöl az adatokon, a Power Query-szerkesztő mindent rögzít az **ALKALMAZOTT LÉPÉSEK** szakaszban, ahol az elemeket szükség szerint törölheti, áttekintheti, átrendezheti vagy törölheti.

![Alkalmazott lépések](media/desktop-connect-to-data/designer_gsg_appliedsteps_changedtype.png)

A táblán betöltés után is végezhet további módosításokat, de jelenleg ennyi is elég lesz. Ha végzett, válassza a **Bezárás és alkalmazás** lehetőséget a **Kezdőlap** menüszalagon, hogy a Power BI Desktop alkalmazza a módosításokat, és bezárja a Power Query-szerkesztőt.

![Bezárás és alkalmazás](media/desktop-connect-to-data/connecttodata_closenload.png)

Ha betöltődött az adatmodell, a Power BI Desktop **Jelentés** nézetében megkezdhetjük a vizualizációk létrehozását a mezők vászonra húzásával.

![Érték vászonra húzása](media/desktop-connect-to-data/connecttodata_dragontoreportview.png)

Ez a modell persze egyszerű, egyetlen adatkapcsolata van. A legtöbb Power BI Desktop-jelentés különböző, az igényei szerint alakított adatforrásokhoz csatlakozik, olyan kapcsolatokkal, amelyek részletes adatmodellt hoznak létre.

## <a name="next-steps"></a>További lépések
A Power BI Desktop műveletek és lehetőségek széles tárházát tartalmazza. A program képességeivel kapcsolatos további információkért lásd az alábbi forrásanyagokat:

* [Mi az a Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [A Lekérdezésszerkesztő használata a Power BI Desktopban](../transform-model/desktop-query-overview.md)
* [Adatforrások a Power BI Desktopban](desktop-data-sources.md)
* [Adatok formázása és összevonása a Power BI Desktopban](desktop-shape-and-combine-data.md)
* [Gyakori lekérdezési feladatok végrehajtása a Power BI Desktopban](../transform-model/desktop-common-query-tasks.md)   

Szeretne visszajelzést küldeni? Kitűnő! Használja a Power BI Desktop **Ötlet beküldése** menüelemét vagy keresse fel a [Közösségi visszajelzés](https://community.powerbi.com/t5/Community-Feedback/bd-p/community-feedback) oldalt. Kíváncsian várjuk a véleményét!

![Ötlet beküldése](media/desktop-connect-to-data/sendfeedback.png)
