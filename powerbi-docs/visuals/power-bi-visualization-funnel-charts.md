---
title: Tölcsérdiagramok
description: Tölcsérdiagramok a Power BI-ban
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: maTzOJSRB3g
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 01/29/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: f070b6649d8d120a889961fffd6b9b923422293e
ms.sourcegitcommit: 67336b077668ab332e04fa670b0e9afd0a0c6489
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/12/2018
ms.locfileid: "44744412"
---
# <a name="funnel-charts"></a>Tölcsérdiagramok
A tölcsérdiagramok segítségével vizualizálhatja az egymást követő összekapcsolt fázisokból álló lineáris folyamatokat. Ilyen például egy értékesítési tölcsér, amelyen keresztül az ügyfelek nyomon követhetőek az egyes fázisokban: Érdeklődő \> Minősített érdeklődő \> Lehetséges ügyfél \> Szerződés \> Zárás.  A tölcsér alakja egyetlen pillantásra megmutatja a lekövetett folyamat állapotát.

A tölcsér minden egyes szakasza a teljes mennyiséghez viszonyított százalékos arányt mutatja. Így az esetek többségében a tölcsérdiagram alakja valóban egy tölcsérhez hasonlít – az első szakasz a legszélesebb, majd a rákövetkező szakaszok egyre szűkülnek.  Persze a körte alakú tölcsérek is hasznosak – segítenek azonosítani a problémákat.  Általában véve azonban az első, a „bemeneti” szakasz a legszélesebb.

![](media/power-bi-visualization-funnel-charts/funnelplain.png)

## <a name="when-to-use-a-funnel-chart"></a>Mikor érdemes tölcsérdiagramokat használni?
A tölcsérdiagram remek választás a következő esetekben:

* ha az adatok egymás követik, és legalább 4 fázisban következnek egymásból,
* ha az első fázis „elemeinek” száma várhatóan meghaladja az utolsó fáziséit,
* a fázisonkénti lehetőségek (bevétel/értékesítés/szerződések/stb.) számításához,
* a konverziós és megtartási arányok számításához,
* a lineáris folyamatok szűk keresztmetszeteinek felfedéséhez,
* a bevásárlókosár-munkafolyamatok nyomon követéséhez,
* az átkattintásos reklám-/marketingkampányok haladásának és sikerességének nyomon követéséhez.

## <a name="working-with-funnel-charts"></a>A tölcsérdiagramok használata
A tölcsérdiagramok:

* A jelentésekből és a Kérdések és válaszok felületről rögzíthetőek.
* Rendezhetőek.
* Támogatják a többszörös használatot.
* Kiemelhető és keresztszűrhető az egyazon jelentésoldalon lévő más vizualizációkkal.
* Használható az egyazon jelentésoldalon lévő más vizualizációk kiemelésére és keresztszűrésére.

## <a name="create-a-basic-funnel-chart"></a>Alapszintű tölcsérdiagram létrehozása
A videóban Will egy tölcsérdiagramot hoz létre az Értékesítési és marketing minta használatával.

<iframe width="560" height="315" src="https://www.youtube.com/embed/qKRZPBnaUXM" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>


Most hozzon létre egy saját tölcsérdiagramot az egyes értékesítési fázisokban lévő lehetőségek megjelenítéséhez.

Ezek az utasítások a Lehetőségelemzési minta használatát feltételezik. Annak érdekében, hogy követni tudja a lépéseket, [töltse le a mintát](../sample-datasets.md), mely a Power BI szolgáltatásban (az app.powerbi.com webhelyen) vagy a Power BI Desktopban használható.   

1. Kezdjen egy [üres jelentésoldalon](../power-bi-report-add-page.md), és válassza a **SalesStage** \> **Sales Stage** (Értékesítési fázis) mezőt. Ha a Power BI szolgáltatást használja, mindenképpen a [Szerkesztési nézetében](../service-interact-with-a-report-in-editing-view.md) nyissa meg a jelentést.
   
    ![](media/power-bi-visualization-funnel-charts/funnelselectfield_new.png)
2. [Konvertálja a diagramot](power-bi-report-change-visualization-type.md) egy tölcsérré. Láthatja, hogy a **Sales Stage** mező a **Csoport** területen található. 
3. A **Mezők** ablaktáblán válassza a **Fact** \> **Opportunity Count** lehetőséget.
   
    ![](media/power-bi-visualization-funnel-charts/power-bi-funnel.png)
4. A mutatót az egyes sávok fölé húzva a rendszer rengeteg információt jelenít meg.
   
   * A fázis neve
   * A jelenleg az adott fázisban lévő lehetőségek száma
   * Átfogó konverziós ráta (az érdeklődő számának százalékában kifejezve) 
   * Fázisról fázisra az előző fázishoz viszonyított (ebben az esetben ez a Proposal Stage/Solution Stage) százalékos arány (a Csökkenés mértéke)
     
     ![](media/power-bi-visualization-funnel-charts/funnelhover_new.png)
5. [Adja hozzá a tölcsért irányítópult-csempeként](../service-dashboard-tiles.md). 
6. [Mentse a jelentést](../service-report-save.md).

## <a name="highlighting-and-cross-filtering"></a>Kiemelés és keresztszűrés
A Szűrök ablaktábla használatával kapcsolatos információkért lásd: [Szűrők hozzáadása jelentésekhez](../power-bi-report-add-filter.md).

A tölcsér egyes sávjainak kiemelésével a rendszer keresztszűri a jelentésoldalon lévő többi vizualizációt... és viszont. A feladat következő lépéseként adjon hozzá néhány vizualizációt a tölcsérdiagramot tartalmazó jelentésoldalhoz.

1. A tölcséren jelölje ki a **Proposal** sávot. Ez kiemeli a lapon lévő többi vizualizáció megfelelő adatait is. A többszörös kijelöléshez használja a CTRL billentyűt.
   
   ![](media/power-bi-visualization-funnel-charts/funnelchartnoowl.gif)
2. A vizualizációk keresztkiemelési és keresztszűrési beállításaival kapcsolatban lásd: [A Power BI vizualizációk interakciója](../service-reports-visual-interactions.md)

## <a name="create-a-funnel-chart-in-qa"></a>Tölcsérdiagram létrehozása a Kérdések és válaszok felületen
Nyissa meg a Lehetőségelemzési minta irányítópultját vagy bármely más olyan irányítópultot, amelyen legalább egy vizualizáció rögzítve van a Lehetőségelemzési minta adathalmazából.  Amikor beír egy kérdést a Kérdések és válaszok felületen, a Power BI a kijelölt irányítópulttal társított (az iránytópulton rögzített csempékkel rendelkező) összes adatkészletben keresi a válaszokat. További információkért lásd: [Power BI – Alapfogalmak](../service-basic-concepts.md).

1. A Lehetőségelemzési minta irányítópultján kezdje el beírni a kérdését a Q&A-kérdésmezőbe.
   
   ![](media/power-bi-visualization-funnel-charts/funnelfromqna_new.png)
   
2. Mindenképp írja be az „as funnel” kifejezést is, hogy a Power BI tudja, milyen típusú vizualizációt szeretne.

## <a name="next-steps"></a>További lépések
[Vizualizációtípusok a Power BI-ban](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Vizualizáció rögzítése az irányítópulton](../service-dashboard-pin-tile-from-report.md)

[Power BI – Alapfogalmak](../service-basic-concepts.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

