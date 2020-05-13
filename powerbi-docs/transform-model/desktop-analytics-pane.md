---
title: Az Elemzés panel használata a Power BI Desktopban
description: Dinamikus referenciavonalak létrehozása vizualizációkhoz a Power BI Desktopban
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/10/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 71fbdfda6675585d861b1447ce3d37e83b660825
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83349540"
---
# <a name="use-the-analytics-pane-in-power-bi-desktop"></a>Az Elemzés panel használata a Power BI Desktopban

A Power BI Desktop **Elemzés** paneljén dinamikus *referenciavonalak* adhatók hozzá a vizualizációkhoz, így irányítva rá a figyelmet a fontos trendekre vagy elemzésekre. Az **Elemzés** ikon és panel a Power BI Desktop **Vizualizációk** területén található.

![Elemzések panel, Vizualizációk, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_1.png)

> [!NOTE]
> Az **Elemzés** panel csak akkor jelenik meg, ha a Power BI Desktop vásznán kiválaszt egy vizualizációt.

## <a name="search-within-the-analytics-pane"></a>Keresés az Elemzési panelen

A Power BI Desktop 2018. februári kiadásától kezdve (2.55.5010.201-es vagy újabb verzió) a **Vizualizációk** panelen alszakaszként megtalálható **Elemzés** panelen is végezhető keresés. A keresőmező az **Elemzés** ikon kiválasztásakor jelenik meg.

![Keresőmező, Elemzések panel, Vizualizációk, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_1b.png)

## <a name="use-the-analytics-pane"></a>Az Elemzés panel használata

Az **Elemzés** panelen a következő típusú dinamikus referenciavonalak hozhatók létre:

* Állandó-vonal az X tengelyen
* Állandó-vonal az Y tengelyen
* Min. vonal
* Max. vonal
* Átlagos vonal
* Középérték-vonal
* Percentilis-vonal
* Szimmetriaárnyékolás

> [!NOTE]
> Nem mindegyik vonal érhető el az összes vizualizációtípushoz.

Az alábbi szakaszok az **Elemzés** panel és a dinamikus referenciavonalak vizualizációkban történő használatát mutatják be.

A vizualizációkhoz elérhető dinamikus referenciavonalak a következő lépések végrehajtásával jeleníthetők meg:

1. Válasszon ki vagy hozzon létre egy vizualizációt, majd válassza ki az **Elemzés** ikont a **Vizualizációk** szakaszban.

    ![Vizualizáció elemzéseinek megtekintése, Vizualizációk panel, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_2.png)

2. Válassza ki a létrehozni kívánt vonaltípust a beállítások körének kibontásához. Ebben az esetben most az **Átlagos vonal** típust választjuk.

    ![Átlagos vonal, Elemzések panel, Vizualizációk, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_3.png)

3. Új vonal létrehozásához válassza a **+&nbsp;Hozzáadás** lehetőséget. Ezután megnevezheti a sort. Kattintson duplán a szövegmezőre, majd adja meg a nevét.

    Mostantól számos lehetőség közül választhat a vonalhoz. Megadhatja annak **színét**, **átlátszósági** százalékát, **vonalstílusát**és **pozícióját** (a vizualizáció adatelemeihez képest). Azt is megadhatja, hogy tartalmazzon-e **adatfeliratot**. A vonal alapját képező vizualizációmérték megadásához válassza a **Mérték** legördülő listát, amely automatikusan ki van töltve a vizualizáció adatelemeivel. Ebben az esetben mértékként a **Culture** (Kultúra) elemet választjuk ki, ehhez az *Average of Culture* (Átlagos kultúra) feliratot rendeljük, és testreszabunk néhány egyéb beállítást is.

    ![Átlagos kultúravonal, Elemzések panel, Vizualizációk, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_4.png)

4. Ha adatfeliratot kíván megjeleníteni, módosítsa az **Adatfelirat** csúszkát **kikapcsoltról** **bekapcsolt** állapotra. Ilyenkor az adatcímke számos további beállítása is megadható.

    ![Adatfelirat-beállítások, Elemzések panel, Vizualizációk, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_5.png)

5. Az **Elemzés** panel **Átlagos vonal** eleme mellett egy szám jelenik meg. Ez a szám azt mutatja meg, hogy jelenleg hány dinamikus vonal található a vizualizáción, és hogy ezek milyen típusúak. Ha felveszünk egy **Max. vonalat** az **Affordability** (Megélhetés) elemhez, az **Elemzés** panelen az látható, hogy már egy **Max. vonal** dinamikus referenciavonalat is alkalmaztunk erre a vizualizációra.

    ![Max. vonal és átlagos vonal összege, Elemzések panel, Vizualizációk, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_6.png)

Ha a kiválasztott vizualizációra nem lehet dinamikus referenciavonalat alkalmazni (ebben az esetben a **Térkép** vizualizációról van szó), akkor az **Elemzés** panelre kattintva az alábbi üzenetet fogja látni.

![Térkép-vizualizáció nem elérhető elemzései, Elemzések panel, Vizualizációk, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_7.png)

Számos érdekes elemzést emelhet ki dinamikus referenciavonalak létrehozásával az **Elemzés** panelen.

További funkciók és képességek bevezetését tervezzük, így például azon vizualizációk körének kiszélesítését, amelyeken dinamikus referenciavonalak alkalmazhatók. Érdemes tehát gyakran visszalátogatni ide az újdonságokért.

## <a name="apply-forecasting"></a>Előrejelzés alkalmazása

Ha az adatforrás tartalmaz időadatokat, használhatja az *előrejelzési* funkciót. Csak jelöljön ki egy vizualizációt, majd bontsa ki az **Elemzés** panel **Előrejelzés** szakaszát. Az Előrejelzést számos bemeneti paraméter megadásával módosíthatja, ilyen lehet például az **Előre jelzett hossz** vagy a **Megbízhatósági intervallum**. Az alábbi képen egy alapszintű vonalvizualizáció látható, alkalmazott előrejelzéssel. Használja a fantáziáját (és játszadozzon az előrejelzéssel), így kipróbálhatja, hogyan alkalmazhatja a modellekre.

![Előrejelzés funkció, Elemzések panel, Vizualizációk, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_8.png)

> [!NOTE]
> Az előrejelzés funkció csak vonaldiagram vizualizációkhoz érhető el.

## <a name="limitations"></a>Korlátozások

A dinamikus referenciavonalak használatának lehetősége az éppen használt vizualizáció típusán alapul. A következő lista részletesebben ismerteti ezeket a korlátozásokat.

Az alábbi vizualizáción használhat *állandó vonalat az X tengelyen*, *állandó vonalat az Y tengelyen*, valamint *szimmetriaárnyékolást*:

* Pontdiagram

Az *állandó vonal*, *min. vonal*, *max. vonal*, *átlagos vonal*, *középértékvonal*és *percentilisvonal* a következő vizualizációkban érhető el:

* Területdiagram
* Fürtözött sávdiagram
* Fürtözött oszlopdiagram
* Vonaldiagram
* Pontdiagram

A következő vizualizációk esetében csak az *Állandó-vonal* típus érhető el az **Elemzés** panelen:

* Halmozott területdiagram
* Halmozott sávdiagram
* Halmozott oszlopdiagram
* Vízesésdiagram
* 100%-os halmozott sávdiagram
* 100%-os halmozott oszlopdiagram

A következő vizualizációk használhatnak *trendvonalat*, ha rendelkeznek időértékkel:

* Területdiagram
* Fürtözött oszlopdiagram
* Vonaldiagram
* Vonaldiagram és fürtözött oszlopdiagram

Jelenleg nem alkalmazhat dinamikus vonalakat számos vizualizációra, többek között a következőkre (a lista nem teljes körű):

* Tölcsér
* Vonaldiagram és fürtözött oszlopdiagram
* Vonaldiagram és halmozott oszlopdiagram
* Szalagdiagram
* Nem Descartes-féle vizualizációk, például fánkdiagram, mérőműszer, mátrix, kördiagram, és táblázat

A percentilis vonal csak akkor áll rendelkezésre, ha importált adatokat használ a *Power BI Desktop* alkalmazásban, vagy ha élő kapcsolatban van az **Analysis Service 2016** vagy újabb verzióját vagy az **Azure Analysis Services** szolgáltatást futtató kiszolgálón található modellel vagy a Power BI szolgáltatásban egy adatkészlettel.

## <a name="next-steps"></a>További lépések

A Power BI Desktop műveletek és lehetőségek széles tárházát tartalmazza. A program képességeivel kapcsolatos további információkért lásd az alábbi forrásanyagokat:

* [A Power BI Desktop újdonságai](../fundamentals/desktop-latest-update.md)
* [A Power BI Desktop beszerzése](../fundamentals/desktop-get-the-desktop.md)
* [Mi az a Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Lekérdezések áttekintése a Power BI Desktopban](desktop-query-overview.md)
* [Adattípusok a Power BI Desktopban](../connect-data/desktop-data-types.md)
* [Adatok formázása és kombinálása a Power BI Desktoppal](../connect-data/desktop-shape-and-combine-data.md)
* [Gyakori feladatok végzése a Power BI Desktopban](desktop-common-query-tasks.md)
