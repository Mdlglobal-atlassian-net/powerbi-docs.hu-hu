---
title: Fő teljesítménymutató (KPI) vizualizációk
description: Fő teljesítménymutató (KPI) vizualizációk létrehozása a Power BI-ban
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: xmja6EpqaO0
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 8fa39c7cc57e24f0c19e1a484c0e925bfeec94f7
ms.sourcegitcommit: 1c96b65a03ec0a0612e851dd58c363f4d56bca38
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/25/2019
ms.locfileid: "67389576"
---
# <a name="key-performance-indicator-kpi-visuals"></a>Fő teljesítménymutató (KPI) vizualizációk

A fő teljesítménymutató (KPI) olyan vizuális jel, amely egy mérhető cél terén elért előrehaladás mértékét jelzi. A fő teljesítménymutatókról a [Fő teljesítménymutatók (KPI-k) a PowerPivotban](/previous-versions/sql/sql-server-2012/hh272050(v=sql.110)) című cikk ír bővebben.

Megtekintheti a videót, amelyben bemutatjuk, hogyan hozhat létre egyetlen mutatószámos vizualizációkat: kijelzőket, kártyákat és KPI-ket.

<iframe width="560" height="315" src="https://www.youtube.com/embed/xmja6EpqaO0?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="when-to-use-a-kpi"></a>Mikor érdemes KPI-t használni?

A KPI remek választás:

* A haladás mérésére. A „mivel haladok jól, és mivel vagyok lemaradva?” kérdés megválaszolására.

* A cél távolságának mérésére. A „mennyivel járok előrébb, vagy vagyok lemaradva?” kérdés megválaszolására.

## <a name="kpi-requirements"></a>KPI-követelmények

A tervezők egy adott mértékre alapozzák a KPI-vizualizációkat. A KPI rendeltetése egy metrika aktuális mérőszámának és állapotának kiértékelése egy meghatározott célhoz viszonyítva. Egy a KPI-vizualizációhoz egy meghatározható értékű *alapmértékre*, egy *célmértékre* vagy célértékre, valamint egy *küszöbértékre* vagy *célra* szükség.

A KPI-adathalmazoknak tartalmazniuk kell egy KPI célértékeit. Ha az adathalmaz nem tartalmaz célértékeket, létrehozhatja azokat, ha hozzáad egy célokat tartalmazó Excel-munkalapot az adatmodellhez vagy PBIX-fájlhoz.

## <a name="prerequisites"></a>Előfeltételek

Ha még nem regisztrált a Power BI-ra, a kezdés előtt [hozzon létre egy ingyenes próbaverziós fiókot](https://app.powerbi.com/signupredirect?pbi_source=web).

* [Power BI Desktop](https://powerbi.microsoft.com/get-started/) – ingyenes!

* [A Kiskereskedelmi elemzési minta PBIX-fájlja](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)

## <a name="how-to-create-a-kpi"></a>KPI létrehozása

A bemutatott lépések elvégzéséhez a Power BI Desktopban nyissa meg a [Kiskereskedelmi elemzési minta .PBIX-fájlját](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix). Létre fog hozni egy KPI-t, amely egy értékesítési cél irányába tett előrehaladást méri.

1. Nyissa meg a **Kiskereskedelmi elemzési mintát** jelentésnézetben ![A jelentésnézet ikon képernyőképe.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Kiválasztás ![A sárga fül képernyőképe.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) új oldal hozzáadásához.

1. A **Mezők** panelen válassza az **Értékesítés > Idei összes egység** mezőt.  Ez az érték lesz a mutató.

1. Adjon hozzá **Time > FiscalMonth** (Időpont > Pénzügyi hónap) értékeket.  Ez az érték adja meg a trendet.

1. A vizualizáció jobb felső sarkában válassza a három pontot, és ellenőrizze, hogy a Power BI **FiscalMonth** szerint növekvő sorrendbe rendezte-e az oszlopokat.

    > [!IMPORTANT]
    > Miután átalakítja a vizualizációt KPI-vé, rendezésre már **nincs** lehetőség. Most kell megfelelően rendeznie.

    ![Képernyőkép a kibontott három pontos menüről a Rendezés növekvő sorrendben és a FiscalMonth oszlop kijelölésével.](media/power-bi-visualization-kpi/power-bi-ascending-by-fiscal-month.png)

    A helyesen rendezett vizualizáció az alábbihoz hasonló:

    ![Képernyőkép a megfelelően rendezett vizualizációról.](media/power-bi-visualization-kpi/power-bi-chart.png)

1. Alakítsa át a vizualizációt **KPI**-vé a KPI ikon kiválasztásával a **Vizualizációk** panelen.

    ![Képernyőkép a Vizualizációk panelről, kiemelt KPI ikonnal mezővel.](media/power-bi-visualization-kpi/power-bi-kpi-template.png)

1. Cél hozzáadásához húzza a **Total Units Last Year** (Tavalyi összes egység) mezőt a **Célkitűzések** mezőbe.

    ![Képernyőkép a kész KPI-vizualizációról és a Mezők panelről az értékek ábrázolásával.](media/power-bi-visualization-kpi/power-bi-kpi-done.png)

1. Ha szeretné, formázza a KPI-t a festőhenger ikon kiválasztásával, amely megnyitja Formátum panelt.

    * **Mutató** – szabályozza a mutatószám megjelenítési egységeit és tizedesjegyeit.

    * **Trendtengely** – amikor **Be** értékre van állítva, a vizualizáció a trendtengelyt a KPI-vizualizáció háttereként jeleníti meg.  

    * **Célok** – amikor **Be** értékre van állítva, a vizualizáció megjeleníti a célt és a távolságot a céltól százalékban.

    * **Színkódok > Irány** – néhány KPI *magasabb* értékek, néhány pedig *alacsonyabb* értékek esetén minősül jobbnak. Vessük össze például a bevételeket a várakozási idővel. Általában a bevételek magasabb értéke jobbnak tekinthető, míg a várakozási idő magasabb értéke nem. Válassza a **magas jó** lehetőséget, és igény szerint módosítsa a színbeállításokat.

KPI-k a Power BI szolgáltatásban és a mobileszközökön is elérhetők. Ez lehetőséget kínál arra, hogy mindig az üzlet pulzusán tartsa az ujját.

## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás

Amennyiben a KPI-je nem hasonlít a fentire, lehetséges, hogy nem a **FiscalMonth** mező szerint rendezte sorba. A KPI-k nem rendezhetők. Elölről kell kezdenie, ás a pénzügyi hónapok (**FiscalMonth**) szerinti rendezést még *az előtt* kell elvégeznie, hogy átalakítja a vizualizációt KPI-vé.

## <a name="next-steps"></a>Következő lépések

* [Tippek és trükkök térképvizualizációkhoz a Power BI-ban](power-bi-map-tips-and-tricks.md)

* [Vizualizációtípusok a Power BI-ban](power-bi-visualization-types-for-reports-and-q-and-a.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
