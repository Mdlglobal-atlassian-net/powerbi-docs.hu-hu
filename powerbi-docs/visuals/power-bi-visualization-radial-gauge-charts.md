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
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 8b0db9aebe72d54aa464ec012e614ae0ec5bc723
ms.sourcegitcommit: 1c96b65a03ec0a0612e851dd58c363f4d56bca38
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/25/2019
ms.locfileid: "67390642"
---
# <a name="radial-gauge-charts-in-power-bi"></a>A Power BI kör alakú mérőműszer-diagramjai

A tárcsadiagramok egyetlen értéket jeleznek ki egy köríven. Ez mérhet egy cél felé megtett előrehaladást vagy egy fő teljesítménymutatót (KPI). A vonal (vagy *mutató*) a kitűzött célértéket jelzi. Az árnyékolás a cél elérésében tett előrehaladást mutatja. Az íven belüli érték az előrehaladás értéke. A Power BI minden lehetséges értéket egyenlően oszt el az íven, minimálistól (bal szélső érték) a maximálisig (jobb szélső érték).

![Tárcsadiagram képernyőképe.](media/power-bi-visualization-radial-gauge-charts/gauge_m.png)

Ebben a példában Ön autókereskedő, aki az értékesítési csapat havi értékesítési átlagát követi nyomon. A mutató a 140 autó eladásában meghatározott célt jelenti. Az értékesítések lehetséges minimális átlaga 0, maximuma pedig 200.  A kék árnyékolás azt mutatja, hogy a csapat átlagosan körülbelül 120 értékesítést hajtott végre ebben a hónapban. Szerencsére van még egy hetük a cél elérésére.

Megtekintheti a videót, amelyben bemutatjuk, hogyan hozhat létre egyetlen mutatószámos vizualizációkat: kijelzőket, kártyákat és KPI-ket.

<iframe width="560" height="315" src="https://www.youtube.com/embed/xmja6EpqaO0?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="when-to-use-a-radial-gauge"></a>Mikor érdemes mérőműszer-diagramot használni?

A mérőműszer-diagram remek választás:

* Egy cél elérésében megtett előrehaladás mutatására.

* Százalékos mérőszám, például fő teljesítménymutató jelölésére.

* Egyetlen mérték állapotának mutatására.

* Információk gyorsan átlátható és érthető megjelenítésére.

## <a name="prerequisites"></a>Előfeltételek

* A Power BI szolgáltatás vagy a Power BI Desktop

* Pénzügyi adatokat tartalmazó minta Excel-munkafüzet: [a minta közvetlen letöltése](http://go.microsoft.com/fwlink/?LinkID=521962).

## <a name="create-a-basic-radial-gauge"></a>Alapszintű mérőműszer-diagram létrehozása

Ebben az útmutatóban a Power BI szolgáltatást használjuk. A lépések követéséhez jelentkezzen be a Power BI-ba, és nyissa meg a Pénzügyi minta Excel-fájlt.

### <a name="step-1-open-the-financial-sample-excel-file"></a>1\. lépés: A Pénzügyi minta Excel-fájl megnyitása

1. Ha eddig nem tette meg, töltse le a [Pénzügyi minta Excel-fájlt](../sample-financial-download.md). Jegyezze meg, hogy hová menti.

1. A Power BI szolgáltatásban válassza az **Adatok betöltése** > **Fájlok** lehetőséget.

1. Válassza a **Helyi fájl** lehetőséget, és nyissa meg a mintafájl helyét.

1. Kattintson az **Importálás** gombra. A Power BI adathalmazként a munkaterületéhez adja a Pénzügyi mintát.

1. Az **Adathalmazok** tartalomlistából válassza a **Jelentés létrehozása** lehetőséget a **Pénzügyi mintához**.

    ![Az Adathalmazok lista képernyőképe a Pénzügyi mintához tartozó Jelentés létrehozása ikonra mutató nyíllal.](media/power-bi-visualization-radial-gauge-charts/power-bi-dataset.png)

### <a name="step-2-create-a-gauge-to-track-gross-sales"></a>2\. lépés: Mérőműszer-diagram létrehozása a bruttó értékesítés nyomon követéséhez

Az előző szakaszban a **Jelentés létrehozása** ikon választáskor a Power BI üres jelentést hozott létre szerkesztési nézetben.

1. A **Mezők** panelen válassza a **Bruttó értékesítés** mezőt.

   ![](media/power-bi-visualization-radial-gauge-charts/grosssalesvalue_new.png)

1. Módosítsa az összesítést **Átlag** értékre.

   ![A Mezők panel képernyőképe a Bruttó értékesítés és az Átlag összesítés kiemelésével.](media/power-bi-visualization-radial-gauge-charts/changetoaverage_new.png)

1. Válassza a tárcsa ikont ![A tárcsa ikon képernyőképe.](media/power-bi-visualization-radial-gauge-charts/gaugeicon_new.png) Az oszlopdiagram tárcsadiagrammá alakításához.

    ![A tárcsadiagram képernyőképe.](media/power-bi-visualization-radial-gauge-charts/gauge_no_target.png)

    Attól függően, hogy mikor tölti le a **Pénzügyi minta** fájlt, az ábráétól eltérő számokat láthat.

    > [!TIP]
    > Alapértelmezés szerint a Power BI olyan tárcsadiagramot hoz létre, amelyben a jelenlegi érték (jelen esetben a **bruttó értékesítés átlaga**) az ív felezőpontján van. Mivel az **átlagos bruttó értékesítés** 182,76 ezer dollár, a kezdőérték (Minimum) 0-ra van beállítva, a záróérték (Maximum) pedig a jelenlegi érték duplája.

### <a name="step-3-set-a-target-value"></a>3\. lépés: A célérték megadása

1. Húzza az **ELÁBÉ** értéket a **Mezők** panelről a **Célérték** területre.

1. Módosítsa az összesítést **Átlag** értékre.

   A Power BI hozzáad egy tűt, amely a **145,48 ezer dolláros** célértéket mutatja.

   ![Képernyőkép az átlagos ELÁBÉ hozzáadásával készült tárcsadiagramról.](media/power-bi-visualization-radial-gauge-charts/gaugeinprogress_new.png)

    Feltűnhet, hogy meghaladtuk a célt.

   > [!NOTE]
   > Manuálisan is megadhat célértéket. Lásd az alábbi [A Minimális, a Maximális és a Célértékek manuális beállítása a formázási beállítások segítségével](#use-manual-format-options-to-set-minimum-maximum-and-target-values) szakaszt.

### <a name="step-4-set-a-maximum-value"></a>4\. lépés: A maximális érték megadása

A 2. lépésben a Power BI az **Érték** mezővel automatikusan beállította a minimális és a maximális értéket. Mi a teendő, ha saját maximális értéket szeretne megadni? Tegyük fel például, hogy a jelenlegi érték duplája helyett lehetséges maximális értéknek az adathalmaz legmagasabb bruttó értékesítési értékét szeretné megadni.

1. Húzza a **Bruttó értékesítés** értéket a **Mezők** listából a **Maximális érték** területre.

1. Módosítsa az összesítést **Maximális** értékre.

   ![A Mezők panel képernyőképe a Bruttó értékesítés és a Maximum értékelés kiemelésével.](media/power-bi-visualization-radial-gauge-charts/setmaximum_new.png)

   A rendszer újrarajzolja a mérőműszert új záróértékkel, amely 1,21 millió bruttó értékesítés.

   ![A kész tárcsadiagram képernyőképe.](media/power-bi-visualization-radial-gauge-charts/power-bi-final-gauge.png)

### <a name="step-5-save-your-report"></a>5\. lépés: Jelentés mentése

1. [Mentse a jelentést](../service-report-save.md).

1. [Adja hozzá a mérőműszer-diagramot irányítópult-csempeként](../service-dashboard-pin-tile-from-report.md). 

## <a name="use-manual-format-options-to-set-minimum-maximum-and-target-values"></a>A Minimális, a Maximális és a Célértékek manuális beállítása a formázási beállítások segítségével

1. Távolítsa el a **Gross Sales maximuma** értéket a **Maximális érték** területről.

1. Válassza a festőhenger ikont a **Formázás** panel megnyitásához.

   ![A tárcsadiagram és a Formázás panel képernyőképe a festőhenger ikon kiemelésével.](media/power-bi-visualization-radial-gauge-charts/power-bi-roller.png)

1. Bontsa ki a **Mérőtengely** elemet, és adjon meg a **Min** és a **Max** értéket.

    ![A mérőtengely beállításainak képernyőképe.](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-axis.png)

1. Törölje az **ELÁBÉ** beállítást a **Mezők** panelről a célérték eltávolításához.

    ![Képernyőkép az ELÁBÉ beállítás törléséről.](media/power-bi-visualization-radial-gauge-charts/pbi_remove_target.png)

1. Amikor megjelenik a **Cél** mező a **Mérőtengely** alatt, adjon meg egy értéket.

     ![A mérőtengely beállításainak képernyőképe a Cél kiemelésével.](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-target.png)

1. Ha szeretné, folytathatja a mérőműszer-diagram formázását.

Ha végrehajtja ezeket a lépéseket, az alábbihoz hasonló tárcsadiagramot fog kapni:

![A végleges tárcsadiagram képernyőképe.](media/power-bi-visualization-radial-gauge-charts/power-bi-final.png)

## <a name="next-step"></a>Következő lépés

* [Fő teljesítménymutató (KPI) vizualizációk](power-bi-visualization-kpi.md)

* [Vizualizációtípusok a Power BI-ban](power-bi-visualization-types-for-reports-and-q-and-a.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)