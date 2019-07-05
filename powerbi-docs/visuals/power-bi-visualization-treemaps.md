---
title: Fatérképek a Power BI-ban
description: Fatérképek a Power BI-ban
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 4c28071917dbe5669e6e35bd416236ef7047eb24
ms.sourcegitcommit: 58c649ec5fd2447a0f9ca4c4d45a0e9fff2f1b6a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/27/2019
ms.locfileid: "67408725"
---
# <a name="treemaps-in-power-bi"></a>Fatérképek a Power BI-ban

A fatérképek a hierarchikus adatokat beágyazott téglalapokként jelenítik meg. A hierarchia minden egyes szintjét egy színes téglalap (más néven „ág”) jelöli, amely további téglalapokat („leveleket”) tartalmaz. A Power BI az egyes téglalapok közötti távolságot a mért értékek alapján határozza meg. A téglalapok méret szerint vannak rendezve, a bal felső saroktól (legnagyobb), a jobb alsó sarokig (legkisebb).

![Képernyőkép a Termékek száma kategória és gyártó szerint fatérképről.](media/power-bi-visualization-treemaps/pbi-nancy-viz-treemap.png)

Ha például az értékesítést elemzi, akkor használhat legfelső szintű ágakat a ruházati kategóriákhoz: **Urban** (Város), **Rural** (Vidék), **Youth** (Fiatalok), és **Mix** (Vegyes). A Power BI a kategória téglalapjait levelekre bontja szét az adott kategórián belüli ruházati gyártók szerit. Ezek a téglalapok az eladott darabszámok alapján kapnák a méretüket és az árnyalatukat.

A fenti **Urban** ágban sok **VanArsdel** márkájú ruhát adtak el. **Natura** és **Fama** márkából kevesebbet értékesítettek. Csak néhány **Leo** márkájú fogyott. Így a fatérkép **Urban** ágában az alábbiak vannak:

* A **VanArsdel** rendelkezik a legnagyobb téglalappal a bal felső sarokban.

* Valamivel kisebb téglalapban jelenik meg a **Natura** és a **Fama**.

* Számos egyéb téglalap jelöli az összes többi ruházati márkát.

* Egy egészen kis méretű jut a **Leo** márkára.

Az egyéb ruházati kategóriákban értékesített tételek számát pedig az egyes levélcsomópontok mérete és árnyalata alapján hasonlíthatom össze: minél nagyobb és sötétebb egy adott téglalap, annál nagyobb értéket jelöl.

Szeretne előbb megnézni valaki mást, ahogyan létrehoz egy fatérképet? Ugorjon a videóban 2:10-hez, hogy megnézhesse, hogyan hoz létre Amanda egy fatérképet.

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

## <a name="when-to-use-a-treemap"></a>Mikor érdemes fatérképet használni

A fatérképek használata nagyszerű választás, ha:

* Nagy mennyiségű hierarchikus adatot szeretne megjeleníteni.

* Egy oszlopdiagram nem tudja hatékonyan kezelni a nagy mennyiségű értéket.

* Az egyes részek és az egész közötti arányokat szeretné megjeleníteni.

* A hierarchia egyes kategóriaszintjein belül megfigyelhető eloszlási mintákat szeretné megjeleníteni.

* Méret és színek alapján szeretne attribútumokat megjeleníteni.

* Mintákat, kiugró adatokat, legfontosabb résztvevőket és kivételeket szeretne azonosítani.

## <a name="prerequisites"></a>Előfeltételek

* A Power BI szolgáltatás vagy a Power BI Desktop

* Kiskereskedelmi elemzési mintajelentés

## <a name="get-the-retail-analysis-sample-report"></a>A Kiskereskedelmi elemzési mintajelentés beszerzése

Ez az útmutatás a Kiskereskedelmi elemzési mintát használja. A vizualizációk létrehozásához az adatkészletre és a jelentésre vonatkozó szerkesztési jogosultságok szükségesek. A Power BI mintái mind szerkeszthetőek. Ha mások osztanak meg Önnel jelentést, abban az esetben nem fog tudni vizualizációkat létrehozni jelentésekben. A leírás követéséhez nyissa meg a [Kiskereskedelmi elemzési minta jelentést](../sample-datasets.md).

Ha beszerezte a **Kiskereskedelmi elemzési mintát**, elkezdheti a munkát.

## <a name="create-a-basic-treemap"></a>Egyszerű fatérkép létrehozása

Létrehoz egy jelentést, és hozzáad egy egyszerű fatérképet.

1. A **Saját munkaterületen** válassza az **Adatkészletek** > **Jelentés létrehozása** lehetőséget.

    ![Képernyőkép az Adatkészletek > Jelentés létrehozása lehetőségről.](media/power-bi-visualization-treemaps/power-bi-create-a-report.png)

1. A **Mezők** panelen válassza az **Értékesítés** > **Tavalyi értékesítések** mértéket.

   ![Képernyőkép a kiválasztott Értékesítések > Tavalyi értékesítések lehetőségről és az eredményül kapott vizualizációról.](media/power-bi-visualization-treemaps/treemapfirstvalue_new.png)

1. A fatérkép ikon kiválasztása ![A fatérkép ikon képernyőképe](media/power-bi-visualization-treemaps/power-bi-treemap-icon.png) a diagram fatérképpé konvertálásához.

   ![Képernyőkép a fatérkép-diagramról konfigurálás nélkül.](media/power-bi-visualization-treemaps/treemapconvertto_new.png)

1. Húzza az **Item** > **Category** elemet a **Csoport** gyűjtőbe.

    A Power BI létrehoz egy fatérképet, amelyen a téglalapok mérete az összes eladáson alapszik, a szín pedig a kategóriát jelöli. Lényegében egy olyan hierarchiát hozott létre, amely az összes értékesítés kategóriák szerinti relatív arányát jeleníti meg. A legtöbb eladás a **Men's** (Férfi) kategóriában van, a legkevesebb pedig a **Hosiery** (Harisnya) kategóriában.

    ![Képernyőkép a konfigurált fatérképről.](media/power-bi-visualization-treemaps/power-bi-complete.png)

1. Húzza a **Store** > **Chain** elemet a **Részletek** gyűjtőbe a fatérképe kiegészítéséhez. Így már kategóriák és üzletláncok szerint is össze tudja hasonlítani a tavalyi év értékesítéseit.

   ![Képernyőkép a fatérképről az Áruház > Lánc hozzáadásával a részletekhez.](media/power-bi-visualization-treemaps/power-bi-details.png)

   > [!NOTE]
   > A Színtelítettség és a Részletek gyűjtők nem használható egyszerre.

1. Helyezze a kurzort egy **Chain** elem fölé, hogy megjelenjen az adott **Kategória** elemleírása.

    Például, ha a kurzorral a **090-Home** téglalap **Fashions Direct** levelére mutat, akkor megjelenik a Home (Otthoni) kategória Fashion Direct részéhez tartozó elemleírás.

   ![A megjelenő Kezdőlap elemleírás képernyőképe.](media/power-bi-visualization-treemaps/treemaphoverdetail_new.png)

1. Vegye fel a fatérképet egy [irányítópult-csempeként (rögzítse a vizualizációt)](../service-dashboard-tiles.md).

1. Mentse [a jelentést](../service-report-save.md).

## <a name="highlighting-and-cross-filtering"></a>Kiemelés és keresztszűrés

A **Szűrők** panel használatáról további információt talál a [Szűrő hozzáadása a jelentéshez](../power-bi-report-add-filter.md) című témakörben.

Egy **Kategória** vagy **Részlet** kiemelése egy fatérképen keresztkiemelést és keresztszűrést végez a jelentésoldalon lévő többi vizualizáción, és fordítva. A lépések elvégzéséhez adjon vizualizációkat a jelentésoldalhoz, vagy másolja a fatérképet a jelentésben szereplő egyéb oldalak egyikéhez.

1. A fatérképen válasszon egy **kategóriát**, vagy válasszon egy **láncot** egy **kategórián** belül. Ez kiemeli a lapon lévő többi vizualizáció megfelelő adatait is. A **050-Shoes** kiválasztása például megmutatja, hogy a tavalyi év cipőeladásai **3 640 471 $** értéket képviseltek, amelyből **2 174 185 $** a **Fashions Directtől** származott.

   ![A Store Sales áttekintő a jelentésének képernyőképe keresztkiemelés alkalmazásával.](media/power-bi-visualization-treemaps/treemaphiliting.png)

1. A **Last Year Sales by Chain** (Előző évi értékesítések üzletlánc szerint) tortadiagramban válassza a **Fashions Direct** szeletet, ezzel keresztszűrést végezhet a fatérképen.
   ![A keresztszűrés funkció GIF-bemutatója.](media/power-bi-visualization-treemaps/treemapnoowl.gif)

1. A keresztkiemelések és keresztszűrések használatának módját a [Vizualizációk közötti interakciók módosítása Power BI-jelentésekben](../service-reports-visual-interactions.md) című cikk ismerteti.

## <a name="next-steps"></a>Következő lépések

* [Vízesésdiagramok a Power BI-ban](power-bi-visualization-waterfall-charts.md)

* [Vizualizációtípusok a Power BI-ban](power-bi-visualization-types-for-reports-and-q-and-a.md)
