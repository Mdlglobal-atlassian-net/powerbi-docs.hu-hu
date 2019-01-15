---
title: X és Y tengely tulajdonságainak testreszabása
description: X és Y tengely tulajdonságainak testreszabása
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: 9DeAKM4SNJM
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/06/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c6395785c3d3e386aa2ac735439a265f5fe3fb02
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54287002"
---
# <a name="customize-x-axis-and-y-axis-properties"></a>X és Y tengely tulajdonságainak testreszabása
Az oktatóanyag segítségével elsajátíthatja a vizualizációk X és Y tengelyének testreszabását lehetővé tevő módok végrehajtását. Nem minden vizualizáció rendelkezik tengelyekkel vagy testreszabási lehetőségekkel. Például a kördiagramoknak nincsenek tengelyei. Ráadásul a testreszabási lehetőségek minden vizualizáció esetében különböznek, és túl sok lehetőség létezik ahhoz, hogy egyetlen cikkben mindet ismertessük. Így a leggyakrabban használt tengelyek testreszabási lehetőségeit fogjuk átvenni, hogy Ön kényelmesen elsajátíthassa a vizualizációk formázási lapjának használatát a Power BI-jelentések vásznán.  

> [!NOTE]
> A tartalom a Power BI szolgáltatásra és a Power BI Desktopra is vonatkozik. Azok a testreszabási lehetőségek, amelyek a **Formázás** elem (a festőhenger ikon ![](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-paintroller.png)) kiválasztásával érhetők el, a Power BI Desktopban is elérhetők.  
>
>

Figyelje meg, ahogy Amanda testreszabja az X és Y tengelyt, és bemutatja az összefűző vezérlésének különböző módjait a felhatolás és lehatolás használatakor. Ezután a videó alatt látható részletes utasításokat követve próbálkozzon meg a feladat elvégzésével, a Kiskereskedelmi elemzési minta használatával.

<iframe width="560" height="315" src="https://www.youtube.com/embed/9DeAKM4SNJM" frameborder="0" allowfullscreen></iframe>


## <a name="customizing-visualization-x-axes-in-reports"></a>Az X tengely vizualizációjának testreszabása jelentésekben
## <a name="create-a-stacked-chart-visualization"></a>Halmozott diagramos vizualizáció létrehozása
Jelentkezzen be a Power BI szolgáltatásba, és nyissa meg a **Kiskereskedelmi elemzési minta** jelentést [Szerkesztési nézetben](../service-interact-with-a-report-in-editing-view.md). A további lépések követéséhez [kapcsolódjon a Kiskereskedelmi elemzési mintához](../sample-datasets.md).

1. Hozzon létre egy oszlopdiagramot, amely az idei és az előző évi értékesítések értékét jeleníti meg pénzügyi hónapok szerinti bontásban.
2. Alakítsa át a diagramot halmozott oszlopdiagrammá.

    ![](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-create-chart.png)

## <a name="customize-the-x-axis"></a>Az X tengely testreszabása
1. A Vizualizációk és szűrők ablaktáblán válassza a **Formázás** lehetőséget (a festőhenger ikont ![](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-paintroller.png)), hogy láthatóvá váljanak a testreszabási lehetőségek.
2. Bontsa ki az X tengely beállításait.

   ![](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-x-axis.png)
3. A Be (vagy Ki) csúszka kiválasztásával be- és kikapcsolhatja az X tengelyt. Egyelőre hagyja **Be** állásban.  Az X tengely kikapcsolásának az egyik lehetséges oka az lehet, hogy ezzel helyet hagyjunk még több adatnak.

    ![](media/power-bi-visualization-customize-x-axis-and-y-axis/onoffslider.png)
4. Formázza a szöveg színét, méretét és betűtípusát. Ebben a példában a **szöveg színe** fekete, a **szöveg mérete** 14 értékű, a **betűtípus** pedig az Arial Black.  
5. Kapcsolja **Be** az X tengely címét, és jelenítse meg az X tengely nevét, ami ebben az esetben **Pénzügyi hónap**.  
6. Formázza a cím szövegének színét, méretét és betűtípusát.  Ebben a példában a **Cím színe** narancssárga, a **Tengely címe** **Pénzügyi hónap**, a **Cím szövegének mérete** pedig 21.
7. A pénzügyi hónap szerinti rendezéshez a diagram jobb felső sarkában kattintson a három pontra (…), és válassza a **Pénzügyi hónap szerinti rendezés** lehetőséget.

    A testreszabás elvégzése után az oszlopdiagramnak a következőhöz hasonlóan kell kinéznie:

     ![](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-customize-axis.png)

Az X tengelyen eddig végrehajtott testreszabások visszavonásához válassza a **Visszaállítás alapértelmezettre** lehetőséget az **X tengely** testreszabási ablaktáblájának alján.

## <a name="customize-the-y-axis"></a>Az Y tengely testreszabása
1. Bontsa ki az Y tengely beállításait.

   ![](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-y-axis.png)

2. A Be (vagy Ki) csúszka kiválasztásával be- és kikapcsolhatja az Y tengelyt. Egyelőre hagyja **Be** állásban.  Az Y tengely kikapcsolásának az egyik lehetséges oka az lehet, hogy ezzel helyet hagyjunk még több adatnak.
   
    ![](media/power-bi-visualization-customize-x-axis-and-y-axis/onoffslider.png)
3. Állítsa át az Y tengely **Pozícióját** a jobb oldalra.
4. Formázza a szöveg színét, méretét és betűtípusát. Ebben a példában a **szöveg színe** fekete, a **szöveg mérete** 14 értékű, a **betűtípus** pedig az Arial Black.  
5. Hagyja meg a **Megjelenítési egységek** beállításnál a milliók, az **Értékek tizedesjegyei** beállításnál pedig a 0 értéket.
6. Ennél a vizualizációnál az Y tengely címe nem tesz hozzá a vizualizációhoz, így hagyja a **Cím** beállítást kikapcsolva.  
7. Emeljük ki a rácsvonalakat úgy, hogy a **Szín** beállítást sötétszürkére változtatjuk, a **Vonás vastagsága** beállítást pedig 2-re növeljük.

    A testreszabás elvégzése után az oszlopdiagramnak a következőhöz hasonlóan kell kinéznie:

     ![](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-y-axis-complete.png)

## <a name="customizing-visualizations-with-dual-y-axes"></a>Dupla Y tengellyel rendelkező vizualizációk testreszabása
Először létrehozunk egy kombinált diagramot, amely azt ábrázolja, hogy a boltok számának milyen hatása van az értékesítésekre.  Ez a diagram ugyanaz, amelyet a [Kombinált diagram oktatóanyagban](power-bi-visualization-combo-chart.md) létrehoztunk. Ezután megformázzuk a dupla Y tengelyt.

### <a name="create-a-chart-with-two-y-axes"></a>Két Y tengellyel rendelkező diagram létrehozása
1. Hozzon létre egy új vonaldiagramot, amely az **Értékesítés > Tavalyi bruttó nyereség (%)** adatokat követi **Idő > Pénzügyi hónap** szerint.
2. A vizualizáció hónapok szerinti rendezéséhez válassza a három pontot (…), majd a **Rendezés hónapok szerint** lehetőséget.

    ![](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-line-chart.png)

    > [NOTE]: For help sorting by month, see [sorting by other criteria](../consumer/end-user-change-sort.md#other)

    A januári bruttó nyereség 35% volt, áprilisban egy 45%-os csúcs következett, amelyet júliusban egy esés, augusztusban pedig egy újabb csúcs követett. Az idei év értékesítéseire vonatkozóan is hasonló mintát fogunk látni, mint tavaly?
     
3. Adja hozzá a vonaldiagramhoz az **Idei értékesítés > Érték** és a **Múlt évi értékesítés** mezőt. A **Tavalyi bruttó nyereség (%)** (a 0%-os rácsvonal mellett futó kék vonal) mérete sokkal kisebb, mint az **Értékesítés** mérete, ami megnehezíti az összehasonlítást. Az Y tengely címkéjének százalékos értékei pedig nevetségesek.      

    ![](media/power-bi-visualization-customize-x-axis-and-y-axis/flatline_new.png)

5. Annak érdekében, hogy a vizualizáció könnyebben olvasható és értelmezhető legyen, alakítsa át a vonaldiagramot egy vonal- és halmozott oszlopdiagrammá.

   ![](media/power-bi-visualization-customize-x-axis-and-y-axis/converttocombo_new.png)

6. Húzza át a **Tavalyi bruttó nyereség (%)** értéket az **Oszlopértékek** közül a **Sorértékek** közé. Ekkor a fentebb létrehozott halmozott oszlopdiagramot látjuk, ***valamint*** egy vonaldiagramot.  (Tetszés szerint a fentebb ismertetett módon a tengelyek betűszíne és betűmérete is formázható.)
   
   A Power BI létrehoz két tengelyt, ezzel lehetővé téve az adatkészletek eltérő skálázását: a bal tengely méri a pénzösszeget, a jobb pedig a százalékokat.

   ![](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-dual-axes-new.png)

### <a name="format-the-secondary-y-axis"></a>A másodlagos Y tengely formázása
1. A **Vizualizációk** ablaktáblán válassza a festőhenger ikont, hogy láthatóvá váljanak a formázási lehetőségek.    
2. Bontsa ki az Y tengely beállításait a lefelé mutató nyílra kattintva.    
3. Görgessen lefelé a listában, amíg meg nem látja a **Másodlagos megtekintése** lehetőség beállításait. Állítsa a **Másodlagos megtekintése** lehetőséget **Ki** állásból **Be** állásba.    

   ![](media/power-bi-visualization-customize-x-axis-and-y-axis/combo3.png)

   ![](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-dual-axes.png)

4. (Opcionális) Szabja testre a két tengelyt. Ha átállítja akár az oszloptengely, akár a sortengely **Pozíció** beállítását, akkor a két tengely helyet cserél.

   ![](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-y-axes-options.png)

### <a name="add-titles-to-both-axes"></a>Címek hozzáadása a tengelyekhez
Ilyen összetett vizualizációk esetében sokat segíthet, ha címeket adunk a tengelyeknek.  A címek segítségével a munkatársai jobban megérthetik a vizualizáció által elmondott történetet.

1. Állítsa a **Cím** lehetőséget **Be** állásba az **Y tengely (Oszlop)** és az **Y tengely (Sor)** esetén is.
2. Állítsa be a **Stílus** beállításnál a **Csak a cím megjelenítése** lehetőséget.

   ![](media/power-bi-visualization-customize-x-axis-and-y-axis/yaxissettings.png)    
3. A kombinált diagram ekkor a dupla tengelyt címekkel együtt jeleníti meg.

   ![](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-combo-chart.png)

További információkért lásd [a színek formázásához, a címkézéshez és a tengelyek tulajdonságainak beállítására szolgáló tippeket és trükköket](service-tips-and-tricks-for-color-formatting.md).

## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás
Ha a jelentés tulajdonosa az X tengelyt adat típusúként kategorizálta, akkor megjelenik a **Típus** beállítás, amelynél a folyamatos és a kategorikus beállítások közül lehet választani.

## <a name="next-steps"></a>Következő lépések
További információk [a Power BI-jelentésekben lévő vizualizációkról](power-bi-report-visualizations.md)

[C](power-bi-visualization-customize-title-background-and-legend.md)[ímek, hátterek és jelmagyarázatok testreszabása](power-bi-visualization-customize-title-background-and-legend.md)

[Színek és tengelytulajdonságok testreszabása](service-getting-started-with-color-formatting-and-axis-properties.md)

[Power BI – Alapfogalmak](../consumer/end-user-basic-concepts.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
