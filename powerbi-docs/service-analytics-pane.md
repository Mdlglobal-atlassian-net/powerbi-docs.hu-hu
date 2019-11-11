---
title: Dinamikus referenciavonalak létrehozása vizualizációkhoz
description: Dinamikus referenciavonalak létrehozása vizualizációkhoz a Power BI szolgáltatásban
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/14/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: ab8fb8daa46a21676925de16a068f2d2029954d2
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73855914"
---
# <a name="create-dynamic-reference-lines-for-visuals-in-the-power-bi-service"></a>Dinamikus referenciavonalak létrehozása vizualizációkhoz a Power BI szolgáltatásban

A **Power BI szolgáltatás** **Elemzés** paneljével dinamikus *referenciavonalak* adhatók a vizualizációkhoz, kiemelve a fontos trendeket vagy elemzési eredményeket.

![](media/service-analytics-pane/power-bi-analytics-pane.png)

> [!NOTE]
> Az **Elemzés** panel csak akkor jelenik meg, ha egy vizualizáció ki van jelölve a jelentés vásznon.
> 
> 

## <a name="use-the-analytics-pane"></a>Az Elemzés panel használata
Az **Elemzés** panelen a következő típusú dinamikus referenciavonalak hozhatók létre (nem mindegyik vonal érhető el az összes vizualizációtípushoz):

* Állandó-vonal az X tengelyen
* Állandó-vonal az Y tengelyen
* Min. vonal
* Max. vonal
* Átlagos vonal
* Középérték-vonal
* Percentilis-vonal


Az adott vizualizáció esetében rendelkezésre álló dinamikus referenciavonalak megtekintéséhez hajtsa végre a következő lépéseket:

1. Jelöljön ki vagy hozzon létre egy vizualizációt, majd kattintson a **Megjelenítések** panel **Elemzés** ikonjára ![](media/service-analytics-pane/power-bi-analytics-icon.png).

2. Válassza a kívánt vonaltípus melletti lefelé mutató nyilat a lehetőségek kibontásához. Ebben az esetben most az **Átlagos vonal** típust választjuk.
   
   ![átlagos vonal hozzáadása](media/service-analytics-pane/power-bi-add.png)

3. Egy új sor hozzáadásához válassza a **+ Hozzáadás** lehetőséget, majd válassza ki a vonal létrehozásához használandó mértéket.  A rendszer automatikusan feltölti a **Mérték** legördülő listát a kiválasztott vizualizáció elérhető adataival. Válassza az **Open store count** (Nyitva lévő üzletek száma) lehetőséget.

5. Számos olyan beállítási lehetőség áll rendelkezésére a vonalhoz kapcsolódóan, mint például a szín, az átlátszóság, a stílus és a pozíció (a vizualizáció adatelemeihez képest). Ha szeretné feliratokkal ellátni a vonalat, adjon neki címet, majd állítsa az **Adatfelirat** csúszkát a **Be** állásba.  Ebben a példában az *Avg # Open Stores* (Nyitva lévő üzletek átlagos száma) címet adjuk a vonalnak, és néhány további beállítást is testre szabunk az alábbiak szerint.
   
   ![az Átlagos vonal elemzésének testreszabása](media/service-analytics-pane/power-bi-average-line2.png)

1. Az **Elemzés** panel **Átlagos vonal** eleme mellett egy szám jelenik meg. Ez a szám azt mutatja meg, hogy jelenleg hány dinamikus vonal található a vizualizáción, és hogy ezek milyen típusúak. Ha felvesz egy **Konstans vonalat** az üzletek számára kijelölt 9 célértékkel, akkor az **Elemzés** panelen látható, hogy már egy **Konstans vonal** referenciavonal is tartozik a vizualizációhoz.
   
   ![](media/service-analytics-pane/power-bi-reference-lines.png)
   

Sokféle érdekes elemzést emelhet ki dinamikus referenciavonalak létrehozásával az **Elemzés** panelen.

## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás

Ha a kiválasztott vizualizációra nem lehet dinamikus referenciavonalat alkalmazni (ebben az esetben a **Térkép** vizualizációról van szó), akkor az **Elemzés** panelre kattintva az alábbiakat fogja látni.
   
![az elemzések nem érhetők el](media/service-analytics-pane/power-bi-no-lines.png)

A dinamikus referenciavonalak használatának lehetősége az éppen használt vizualizáció típusán alapul. Az alábbi listában az egyes vizualizációkhoz jelenleg rendelkezésre álló dinamikus vonalak vannak felsorolva:

A dinamikus vonalak teljes körű alkalmazása a következő vizualizációk esetében lehetséges:

* Területdiagram
* Vonaldiagram
* Pontdiagram
* Fürtözött oszlopdiagram
* Fürtözött sávdiagram

A következő vizualizációk esetében csak az *Állandó-vonal* típus érhető el az **Elemzés** panelen:

* Halmozott terület
* Halmozott sáv
* Halmozott oszlop
* 100%-ig halmozott sáv
* 100%-ig halmozott oszlop

A következő vizualizációk esetében csak a *Trendvonal* típus érhető el:

* Nem halmozott vonal
* Fürtözött oszlopdiagram

Végül pedig a nem Descartes-féle vizualizációk esetében jelenleg nem alkalmazhatók dinamikus vonalak az **Elemzés** panelen. Ilyen vizualizációk például:

* Mátrix
* Tortadiagram
* Gyűrű
* Tábla

## <a name="next-steps"></a>További lépések
[Az Elemzés panel a Power BI Desktopban](desktop-analytics-pane.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

