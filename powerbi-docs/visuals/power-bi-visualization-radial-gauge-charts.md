---
title: A Power BI kör alakú mérőműszer-diagramjai
description: A Power BI kör alakú mérőműszer-diagramjai
author: mihart
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/05/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 7c6c4dbe9f17464483f5b44542ffbe04f715d4bd
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/06/2020
ms.locfileid: "82866932"
---
# <a name="radial-gauge-charts-in-power-bi"></a>A Power BI kör alakú mérőműszer-diagramjai

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

A tárcsadiagramok egyetlen értéket jeleznek ki egy köríven. Ez mérhet egy cél felé megtett előrehaladást vagy egy fő teljesítménymutatót (KPI). A vonal (vagy *mutató*) a kitűzött célértéket jelzi. Az árnyékolás a cél elérésében tett előrehaladást mutatja. Az íven belüli érték az előrehaladás értéke. A Power BI minden lehetséges értéket egyenlően oszt el az íven, minimálistól (bal szélső érték) a maximálisig (jobb szélső érték).

![Tárcsadiagram képernyőképe.](media/power-bi-visualization-radial-gauge-charts/gauge-m.png)

Ebben a példában Ön autókereskedő, aki az értékesítési csapat havi értékesítési átlagát követi nyomon. A mutató a 140 autó eladásában meghatározott célt jelenti. Az értékesítések lehetséges minimális átlaga 0, maximuma pedig 200.  A kék árnyékolás azt mutatja, hogy a csapat átlagosan körülbelül 120 értékesítést hajtott végre ebben a hónapban. Szerencsére van még egy hetük a cél elérésére.

> [!NOTE]
> A jelentés egy Power BI-munkatárssal való megosztásához mindkettőjüknek Power BI Pro-licenccel kell rendelkezniük, vagy a jelentésnek egy Premium kapacitásban kell lennie.

## <a name="when-to-use-a-radial-gauge"></a>Mikor érdemes mérőműszer-diagramot használni?

A mérőműszer-diagram remek választás:

* Egy cél elérésében megtett előrehaladás mutatására.

* Százalékos mérőszám, például fő teljesítménymutató jelölésére.

* Egyetlen mérték állapotának mutatására.

* Információk gyorsan átlátható és érthető megjelenítésére.

## <a name="prerequisites"></a>Előfeltételek

Ez az oktatóanyag a [Pénzügyi minta Excel-fájlt](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) használja.

1. A menüsor bal felső részén válassza az **Adatok beolvasása** > **Excel** lehetőséget
   
2. Keresse meg a **Pénzügyi minta Excel-fájl** példányát

1. Nyissa meg a **Pénzügyi minta Excel-fájlt** jelentésnézetben ![A jelentésnézet ikon képernyőképe.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Válassza a **financials**, majd a **Sheet1** elemet

1. Kattintson a **Betöltés** gombra

1. Kiválasztás ![A sárga fül képernyőképe.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) új oldal hozzáadásához.



## <a name="create-a-basic-radial-gauge"></a>Alapszintű mérőműszer-diagram létrehozása

### <a name="step-1-create-a-gauge-to-track-gross-sales"></a>1\. lépés: Mérőműszer-diagram létrehozása a bruttó értékesítés nyomon követéséhez

1. Kezdje a műveletet egy üres jelentésoldalon

1. A **Mezők** panelen válassza a **Bruttó értékesítés** mezőt.

   ![](media/power-bi-visualization-radial-gauge-charts/grosssalesvalue-new.png)

1. Módosítsa az összesítést **Átlag** értékre.

   ![A Mezők panel képernyőképe a Bruttó értékesítés és az Átlag összesítés kiemelésével.](media/power-bi-visualization-radial-gauge-charts/changetoaverage-new.png)

1. Válassza a tárcsa ikont ![A tárcsa ikon képernyőképe.](media/power-bi-visualization-radial-gauge-charts/gaugeicon-new.png) Az oszlopdiagram tárcsadiagrammá alakításához.

    ![A tárcsadiagram képernyőképe.](media/power-bi-visualization-radial-gauge-charts/gauge-no-target.png)

    Attól függően, hogy mikor tölti le a **Pénzügyi minta** fájlt, az ábráétól eltérő számokat láthat.

    > [!TIP]
    > Alapértelmezés szerint a Power BI olyan tárcsadiagramot hoz létre, amelyben a jelenlegi érték (jelen esetben a **bruttó értékesítés átlaga**) az ív felezőpontján van. Mivel az **átlagos bruttó értékesítés** 182,76 ezer dollár, a kezdőérték (Minimum) 0-ra van beállítva, a záróérték (Maximum) pedig a jelenlegi érték duplája.

### <a name="step-3-set-a-target-value"></a>3\. lépés: A célérték megadása

1. Húzza az **ELÁBÉ** értéket a **Mezők** panelről a **Célérték** területre.

1. Módosítsa az összesítést **Átlag** értékre.

   A Power BI hozzáad egy tűt, amely a **145,48 ezer dolláros** célértéket mutatja.

   ![Képernyőkép az átlagos ELÁBÉ hozzáadásával készült tárcsadiagramról.](media/power-bi-visualization-radial-gauge-charts/gaugeinprogress-new.png)

    Feltűnhet, hogy meghaladtuk a célt.

   > [!NOTE]
   > Manuálisan is megadhat célértéket. Lásd az alábbi [A Minimális, a Maximális és a Célértékek manuális beállítása a formázási beállítások segítségével](#use-manual-format-options-to-set-minimum-maximum-and-target-values) szakaszt.

### <a name="step-4-set-a-maximum-value"></a>4\. lépés: A maximális érték megadása

A 2. lépésben a Power BI az **Érték** mezővel automatikusan beállította a minimális és a maximális értéket. Mi a teendő, ha saját maximális értéket szeretne megadni? Tegyük fel például, hogy a jelenlegi érték duplája helyett lehetséges maximális értéknek az adathalmaz legmagasabb bruttó értékesítési értékét szeretné megadni.

1. Húzza a **Bruttó értékesítés** értéket a **Mezők** listából a **Maximális érték** területre.

1. Módosítsa az összesítést **Maximális** értékre.

   ![A Mezők panel képernyőképe a Bruttó értékesítés és a Maximum értékelés kiemelésével.](media/power-bi-visualization-radial-gauge-charts/setmaximum-new.png)

   A rendszer újrarajzolja a mérőműszert új záróértékkel, amely 1,21 millió bruttó értékesítés.

   ![A kész tárcsadiagram képernyőképe.](media/power-bi-visualization-radial-gauge-charts/power-bi-final-gauge.png)

### <a name="step-5-save-your-report"></a>5\. lépés: Jelentés mentése

1. [Mentse a jelentést](../service-report-save.md).

## <a name="use-manual-format-options-to-set-minimum-maximum-and-target-values"></a>A Minimális, a Maximális és a Célértékek manuális beállítása a formázási beállítások segítségével

1. Távolítsa el a **Gross Sales maximuma** értéket a **Maximális érték** területről.

1. Válassza a festőhenger ikont a **Formázás** panel megnyitásához.

   ![A tárcsadiagram és a Formázás panel képernyőképe a festőhenger ikon kiemelésével.](media/power-bi-visualization-radial-gauge-charts/power-bi-roller.png)

1. Bontsa ki a **Mérőtengely** elemet, és adjon meg a **Min** és a **Max** értéket.

    ![A mérőtengely beállításainak képernyőképe.](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-axis.png)

1. Törölje az **ELÁBÉ** beállítást a **Mezők** panelről a célérték eltávolításához.

    ![Képernyőkép az ELÁBÉ beállítás törléséről.](media/power-bi-visualization-radial-gauge-charts/pbi-remove-target.png)

1. Amikor megjelenik a **Cél** mező a **Mérőtengely** alatt, adjon meg egy értéket.

     ![A mérőtengely beállításainak képernyőképe a Cél kiemelésével.](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-target.png)

1. Ha szeretné, folytathatja a mérőműszer-diagram formázását.

Ha végrehajtja ezeket a lépéseket, az alábbihoz hasonló tárcsadiagramot fog kapni:

![A végleges tárcsadiagram képernyőképe.](media/power-bi-visualization-radial-gauge-charts/power-bi-final.png)

## <a name="next-step"></a>Következő lépés

* [Fő teljesítménymutató (KPI) vizualizációk](power-bi-visualization-kpi.md)

* [Vizualizációtípusok a Power BI-ban](power-bi-visualization-types-for-reports-and-q-and-a.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
