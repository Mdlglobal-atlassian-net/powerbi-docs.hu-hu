---
title: "Az Elemzés panel a Power BI szolgáltatásban"
description: "Dinamikus referenciavonalak létrehozása vizualizációkhoz a Power BI szolgáltatásban"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/21/2017
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: ebf3021f6afdd23730e6b971077913a886961d3b
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/24/2018
---
# <a name="analytics-pane-in-power-bi-service"></a>Az Elemzés panel a Power BI szolgáltatásban
A **Power BI szolgáltatás** **Elemzés** paneljével dinamikus *referenciavonalak* adhatók a vizualizációkhoz, kiemelve a fontos trendeket vagy elemzési eredményeket.

![](media/service-analytics-pane/power-bi-analytics-pane.png)

> [!NOTE]
> Az **Elemzés** panel csak akkor jelenik meg, ha egy vizualizáció ki van jelölve a jelentés vásznon.
> 
> 

## <a name="using-the-analytics-pane"></a>Az Elemzés panel használata
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

1. Az **Elemzés** panel **Átlagos vonal** eleme mellett egy szám jelenik meg. Ez adja meg a vizualizáción lévő dinamikus vonalak aktuális számát és típusát. Ha felvesz egy **Konstans vonalat** az üzletek számára kijelölt 9 célértékkel, akkor az **Elemzés** panelen látható, hogy már egy **Konstans vonal** referenciavonal is tartozik a vizualizációhoz.
   
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

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

