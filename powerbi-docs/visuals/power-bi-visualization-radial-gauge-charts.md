---
title: A Power BI kör alakú mérőműszer-diagramjai
description: A Power BI kör alakú mérőműszer-diagramjai
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: xmja6Epqa
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/21/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 079494a47452ca0ca043032f78fa35c7d1755d11
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54282563"
---
# <a name="radial-gauge-charts-in-power-bi"></a>A Power BI kör alakú mérőműszer-diagramjai
A mérőműszer-diagram köríves alakú és egyetlen értéket jelenít meg, amely egy cél/KPI elérésében tett előrehaladást méri.  A célt vagy a célértéket a vonal (tű) jelzi. A cél elérésében tett előrehaladást az árnyékolás mutatja.  Az előrehaladást ábrázoló érték pedig félkövér betűvel van feltüntetve az ív belsejében. Minden lehetséges érték egyenlően oszlik el az íven, minimálistól (bal szélső érték) a maximálisig (jobb szélső érték).

Az alábbi példában autókereskedők vagyunk, akik értékesítési csapatuk havi átlagos értékesítését követik nyomon. A célunk 140, amit a fekete tű jelöl.  A lehetséges minimális átlagos értékesítés 0, és a maximális értéket 200-ban határoztuk meg.  A kék árnyékolás azt mutatja, hogy a jelenlegi átlag körülbelül 120 értékesítés ebben a hónapban. Szerencsére még van egy hetünk, hogy elérjük a célunkat.

![](media/power-bi-visualization-radial-gauge-charts/gauge_m.png)

## <a name="when-to-use-a-radial-gauge"></a>Mikor érdemes mérőműszer-diagramot használni?
A mérőműszer-diagram remek választás:

* a cél elérésében megtett előrehaladás mutatására.
* percentilis mérőszám, például KPI jelölésére.
* egyetlen mérték állapotának a mutatására.
* gyorsan áttekinthető és megérthető információk megjelenítésére.

### <a name="prerequisites"></a>Előfeltételek
 - Power BI szolgáltatás vagy Power BI Desktop
 - Pénzügyi adatokat tartalmazó minta Excel-munkafüzet: [a minta közvetlen letöltése](http://go.microsoft.com/fwlink/?LinkID=521962).

## <a name="create-a-basic-radial-gauge"></a>Alapszintű mérőműszer-diagram létrehozása
Ebben az útmutatóban a Power BI szolgáltatást használjuk. A lépések követéséhez jelentkezzen be a Power BI-ba, és nyissa meg a Pénzügyi minta Excel-fájlt.  

Másik lehetőségként tekintse meg a videót, amelyben bemutatjuk, hogyan hozhat létre egyetlen mutatószámos vizualizációkat: mérőműszereket, kártyákat és KPI-ket.

<iframe width="560" height="315" src="https://www.youtube.com/embed/xmja6EpqaO0?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

### <a name="step-1-open-the-financial-sample-excel-file"></a>1. lépés: A Pénzügyi minta Excel-fájl megnyitása
1. Ha még nem rendelkezik vele, töltse le a [Pénzügyi minta Excel-fájlt](../sample-financial-download.md). Jegyezze fel, hogy hová mentette.

2. Nyissa meg a fájlt a ***Power BI szolgáltatásban*** az **Adatok lekérése \> Fájlok** lehetőség kiválasztásával, majd a hely megkeresésével, ahová a fájlt mentette. Kattintson az **Importálás** gombra. A Pénzügyi mintát a rendszer adatkészletként adja hozzá a munkaterületéhez.

3. Az **Adatkészlet** tartalomlistában válassza ki a **Pénzügyi mintát** a megnyitásához Vizsgálat módban.

    ![](media/power-bi-visualization-radial-gauge-charts/power-bi-dataset.png)

### <a name="step-2-create-a-gauge-to-track-gross-sales"></a>2. lépés: Mérőműszer-diagram létrehozása a bruttó értékesítés nyomon követéséhez
1. A **Mezők** panelen válassza a **Gross Sales** (Bruttó értékesítés) mezőt.
   
   ![](media/power-bi-visualization-radial-gauge-charts/grosssalesvalue_new.png)
2. Módosítsa az összesítést **Átlag** értékre.
   
   ![](media/power-bi-visualization-radial-gauge-charts/changetoaverage_new.png)
3. Kattintson a mérőeszköz ikonra ![](media/power-bi-visualization-radial-gauge-charts/gaugeicon_new.png) az oszlopdiagram mérőműszer-diagrammá alakításához.
   
   Alapértelmezés szerint a Power BI olyan mérőműszer-diagramot hoz létre, amelyben a jelenlegi érték (jelen esetben a bruttó értékesítés átlaga) a mérőóra felezőpontján van. Mivel az átlagos bruttó értékesítés 182,76 ezer dollár, a kezdőérték (Minimális) 0-ban van megadva és a záróérték (Maximális) a jelenlegi érték duplája.
   
   ![](media/power-bi-visualization-radial-gauge-charts/gauge_no_target.png)

### <a name="step-3-set-a-target-value"></a>3. lépés: A célérték megadása
1. Húzza a **COGS** értéket a **Célérték** területre.
2. Módosítsa az összesítést **Átlag** értékre.
   A Power BI hozzáad egy tűt, amely a **145,48 ezer dolláros** célértéket mutatja. Feltűnhet, hogy meghaladtuk a célt.
   
   ![](media/power-bi-visualization-radial-gauge-charts/gaugeinprogress_new.png)
   
   > [!NOTE]
   > Manuálisan is megadhat célértéket.  Lásd az alábbi „A Minimális, a Maximális és a Célértékek manuális beállítása a formázási beállítások segítségével” szakaszt.
   > 
   > 

### <a name="step-4-set-a-maximum-value"></a>4. lépés: A maximális érték megadása
A 2. lépésben a Power BI az Érték mezővel automatikusan beállította a minimális (kezdő) és a maximális (záró) értéket.  De mi a teendő, ha saját maximális értéket szeretne megadni?  Tegyük fel például, hogy a jelenlegi érték duplája helyett lehetséges maximális értéknek az adatkészlet legmagasabb bruttó értékesítési értékét szeretné megadni. 

1. Húzza a **Gross Sales** értéket a **Mezők** listából a **Maximális érték** területre.
2. Módosítsa az összesítést **Maximális** értékre.
   
   ![](media/power-bi-visualization-radial-gauge-charts/setmaximum_new.png)
   
   A rendszer újrarajzolja a mérőműszert új záróértékkel, amely 1,21 millió bruttó értékesítés.
   
   ![](media/power-bi-visualization-radial-gauge-charts/power-bi-final-gauge.png)

### <a name="step-5-save-your-report"></a>5. lépés: Jelentés mentése
1. [Mentse a jelentést](../service-report-save.md).
2. [Adja hozzá a mérőműszer-diagramot irányítópult-csempeként](../service-dashboard-pin-tile-from-report.md). 

## <a name="use-formatting-options-to-manually-set-minimum-maximum-and-target-values"></a>A Minimális, a Maximális és a Célértékek manuális beállítása a formázási beállítások segítségével
1. Távolítsa el a **Gross Sales maximuma** értéket a **Maximális érték** területről.
2. Nyissa meg a Formátum panelt a festőhenger ikon kiválasztásával.
   
   ![](media/power-bi-visualization-radial-gauge-charts/power-bi-roller.png)
3. Bontsa ki a **Mérőtengelyt** és adjon meg **Min** és **Max** értékeket.
   
    ![](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-axis.png)
4. Távolítsa el a jelenlegi értéket a **COGS** melletti jelölőnégyzet jelölésének törlésével.
   
    ![](media/power-bi-visualization-radial-gauge-charts/pbi_remove_target.png)
5. Amikor megjelenik a **Cél** mező a **Mérőtengely** alatt, adjon meg egy értéket.
   
    ![](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-target.png)
6. Ha szeretné, folytathatja a mérőműszer-diagram formázását.

## <a name="next-step"></a>Következő lépés

[Mérőműszerek a Power BI-ban](power-bi-visualization-kpi.md)

[Vizualizációtípusok a Power BI-ban](power-bi-visualization-types-for-reports-and-q-and-a.md)
