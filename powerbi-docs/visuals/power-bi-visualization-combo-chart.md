---
title: Kombinált diagram a Power BI-ban
description: Ez az oktatóanyag azt ismerteti, hogy mikor érdemes kombinált diagramokat használni, és hogy hogyan hozhatóak létre a Power BI szolgáltatásban és a Desktopban.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: lnv66cTZ5ho
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/22/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: e461480f53f4a97aeb4282e64a8a03eb8e1418d1
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66187832"
---
# <a name="combo-chart-in-power-bi"></a>Kombinált diagram a Power BI-ban
A kombinált diagramok olyan vizualizációk a Power BI-ban, amelyek egy vonaldiagramot és egy oszlopdiagramot kombinálnak egyetlen elemmé. A két diagram kombinációjával gyorsabban hasonlíthat össze adatokat.

A kombinált diagramoknak egy vagy két Y tengelyük lehet.

## <a name="when-to-use-a-combo-chart"></a>Mikor érdemes kombinált diagramokat használni?
A kombinált diagramok használata nagyszerű választás, ha:

* van egy vonaldiagramja és egy oszlopdiagramja, amelyek ugyanazt az X tengelyt használják;
* több, különböző értéktartományú mértéket szeretne összehasonlítani;
* egyetlen vizualizáción szeretné bemutatni két mérték korrelációját;
* szeretné ellenőrizni, hogy egy mérték elér-e egy adott célt, amelyet egy másik mérték határoz meg;
* kevesebb helyet szeretne felhasználni a vásznon.

### <a name="prerequisites"></a>Előfeltételek
A kombinált diagramok elérhetőek a Power BI szolgáltatásban és a Power BI Desktopban is. Ebben az oktatóanyagban a Power BI szolgáltatással fogunk kombinált diagramokat létrehozni. A bemutatott lépések elvégzéséhez nyissa meg a Power BI szolgáltatást, és kapcsolódjon a „Kiskereskedelmi mintához” [ehhez alább talál útmutatót](#create)).


## <a name="create-a-basic-single-axis-combo-chart"></a>Egyszerű, egytengelyes kombinált diagram létrehozása
Nézze meg, hogyan hoz létre Will egy kombinált diagramot az Értékesítési és marketing mintát használva.

<iframe width="560" height="315" src="https://www.youtube.com/embed/lnv66cTZ5ho?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>  

<a name="create"></a> A kombinált diagram létrehozásához jelentkezzen be a Power BI szolgáltatásba, válassza az **Adatok beolvasása \> Minták \> Kiskereskedelmi elemzési minta > Kapcsolódás >Ugrás az irányítópultra** lehetőséget.

1. A „Kiskereskedelmi elemzési minta” irányítópulton nyissa meg a „Kiskereskedelmi elemzési minta” jelentést a **Total Stores** (Összes áruház) csempe kiválasztásával.
2. Válassza a **Jelentés szerkesztése** elemet a jelentés Szerkesztési nézetben való megnyitásához.
3. Adjon hozzá egy új jelentésoldalt.
4. Hozzon létre egy oszlopdiagramot, amely az idei év értékesítéseit és bruttó árrését jeleníti meg havi bontásban.

    a.  A Mezők ablaktáblán válassza ki a **Sales** \> **This Year Sales** > **Érték** elemet.

    b.  Húzza a **Sales** \> **Gross Margin This Year** elemet az **Érték** gyűjtőbe.

    c. Adja hozzá a **Time** \> **FiscalMonth** elemet a **Tengely** gyűjtőhöz.

    ![](media/power-bi-visualization-combo-chart/combotutorial1new.png)
5. A vizualizáció jobb felső sarkában válassza a három pontot (...), és válassza ki a **Rendezés szempontja > FiscalMonth** lehetőséget. A rendezési sorrend módosításához válassza ismét a három pontot, és válassza a **Növekvő rendezés** vagy a **Csökkenő rendezés** elemet.

6. Konvertálja az oszlopdiagramot kombinált diagrammá. Két kombinált diagram érhető el: **Vonal- és halmozott oszlopdiagram**, illetve **Vonal- és csoportosított oszlopdiagram**. Ha az oszlopdiagram van kiválasztva, a **Megjelenítések** ablaktáblán válassza a **Vonal- és fürtözött oszlopdiagram** lehetőséget.

    ![](media/power-bi-visualization-combo-chart/converttocombo_new2.png)
7. A **Mezők** ablaktábláról húzza a **Sales** \> **Last Year Sales** elemet a **Sorértékek** gyűjtőbe.

   ![](media/power-bi-visualization-combo-chart/linevaluebucket.png)

   A kombinált diagramnak ekkor ehhez hasonlóan kell kinéznie:

   ![](media/power-bi-visualization-combo-chart/combochartdone-new.png)

## <a name="create-a-combo-chart-with-two-axes"></a>Kéttengelyes kombinált diagram létrehozása
Ebben a feladatban a bruttó árrést és az értékesítéseket fogjuk összehasonlítani.

1. Hozzon létre egy új vonaldiagramot, amely **bruttó nyereség elmúlt év %** által **FiscalMonth**. Válassza a három pontot, hogy **Hónap** és **Növekvő** sorrend szerint végezzen rendezést.  
A januári bruttó nyereség 35% volt, áprilisban egy 45%-os csúcs következett, amelyet júliusban egy esés, augusztusban pedig egy újabb csúcs követett. Az idei év értékesítéseire vonatkozóan is hasonló mintát fogunk látni, mint tavaly?

   ![](media/power-bi-visualization-combo-chart/combo1_new.png)
2. Adja hozzá a vonaldiagramhoz az **Idei értékesítés > Érték** és a **Múlt évi értékesítés** mezőt. A  **Gross Margin Last Year %** (%-os bruttó árrés a tavalyi évben) skálája sokkal kisebb, mint a **Sales** (Értékesítések) skálája, így nehéz összehasonlítani őket.      

   ![](media/power-bi-visualization-combo-chart/flatline_new.png)
3. Annak érdekében, hogy a vizualizáció könnyebben olvasható és értelmezhető legyen, alakítsa át a vonaldiagramot egy vonal- és halmozott oszlopdiagrammá.

   ![](media/power-bi-visualization-combo-chart/converttocombo_new.png)
4. Húzza át a **Tavalyi bruttó nyereség (%)** értéket az **Oszlopértékek** közül a **Sorértékek** közé. A Power BI létrehoz két tengelyt, ezzel lehetővé téve az adatkészletek eltérő skálázását: a bal tengely méri a pénzösszeget dollárban, a jobb pedig a százalékokat. És láthatjuk a választ a kérdésünkre: igen, látunk egy hasonló mintát.

   ![](media/power-bi-visualization-combo-chart/power-bi-clustered-combo.png)    

## <a name="add-titles-to-the-axes"></a>Címek felvétele tengelyekhez
1. A Formátum ablaktábla megnyitásához válassza a festőhenger ikont ![](media/power-bi-visualization-combo-chart/power-bi-paintroller.png).
2. Az **Y tengely** kibontásához válassza a lefelé mutató nyilat.
3. A **y tengely (oszlop)** állítsa be **pozíció** való **bal**állítsa be **cím** való **a**,  **Stílus** való **csak a cím megjelenítése**, és **megjelenítési egységek** , **több millió**.

   ![](media/power-bi-visualization-combo-chart/power-bi-open-y.png)
4. A **y tengely (oszlop)** , görgessen lefelé, amíg meg nem látja **másodlagos megtekintése**. Mivel az Y tengely számos lehetőség van, előfordulhat, mind a görgetősávok használatát. A másodlagos megjelenítése a szakasz a kombinált diagram sor diagram részének formázási beállítások jeleníti meg.

   ![](media/power-bi-visualization-combo-chart/power-bi-secondary.png)
5. Az **Y tengely (Sor)** részen hagyja a **Pozíció** tulajdonságot **Jobbra** értéken, kapcsolja **Be** a **Címet**, majd állítsa a **Stílust** **Csak a cím megjelenítése** értékre.

   A kombinált diagram ekkor már a címeikkel együtt jeleníti meg a két tengelyt.

   ![](media/power-bi-visualization-combo-chart/power-bi-2-titles.png)

6. Ha szeretné, módosíthatja a szöveg betűtípusát, méretét és színét, illetve más olyan beállításokat, amelyekkel javíthatja a diagram olvashatóságát és megjelenését.

Ezután az alábbiakat lehet érdemes elvégezni:

* [Kombinált diagram felvétele irányítópult-csempeként](../service-dashboard-tiles.md).
* [Mentse a jelentést](../service-report-save.md).
* [Jelentés nevének akadálymentesítése a fogyatékkal élők számára](../desktop-accessibility.md).

## <a name="cross-highlighting-and-cross-filtering"></a>Keresztkiemelés és keresztszűrés

Egy oszlop vagy egy sor kijelölése egy kombinált diagramon keresztkiemelést és keresztszűrést végez a jelentés oldalon lévő többi vizualizáción és viszont. Az alapértelmezett viselkedés módosításához használja a [Vizualizációs interakciók](../service-reports-visual-interactions.md) vezérlőt.

## <a name="next-steps"></a>Következő lépések

[Perecdiagramok a Power BI-ban](power-bi-visualization-doughnut-charts.md)

[Vizualizációtípusok a Power BI-ban](power-bi-visualization-types-for-reports-and-q-and-a.md)
