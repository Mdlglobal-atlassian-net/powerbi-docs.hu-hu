---
title: Vízesésdiagramok a Power BI-ban
description: Vízesésdiagramok a Power BI-ban
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: maTzOJSRB3g
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c9ad87d851f52db6cd2720c9e3bd5d4bb7b189a7
ms.sourcegitcommit: 58c649ec5fd2447a0f9ca4c4d45a0e9fff2f1b6a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/27/2019
ms.locfileid: "67409004"
---
# <a name="waterfall-charts-in-power-bi"></a>Vízesésdiagramok a Power BI-ban

A vízesésdiagramok göngyölített összeget jelenítenek meg, amint a Power BI az értékeket összeadja vagy kivonja. Ez hasznos annak megértéséhez, hogy egy kezdeti értékre (pl. nettó bevétel) hogyan hat egy sornyi pozitív és negatív változás.

Az oszlopok színkódolással rendelkeznek, így gyorsan megállapíthatja az értékek növekedését és csökkenését. A kezdeti és végértékeket tartalmazó oszlopok gyakran [a vízszintes tengelyről indulnak](https://support.office.com/article/Create-a-waterfall-chart-in-Office-2016-for-Windows-8de1ece4-ff21-4d37-acd7-546f5527f185#BKMK_Float "a vízszintes tengelyről indulnak"), míg a középső értékek lebegő oszlopokat képeznek. Emiatt a stílus miatt a vízesésdiagramokat híddiagramoknak is nevezik.

<iframe width="560" height="315" src="https://www.youtube.com/embed/qKRZPBnaUXM" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

## <a name="when-to-use-a-waterfall-chart"></a>Mikor érdemes vízesésdiagramot használni?

A vízesésdiagram remek választás a következőkhöz:

* Ha a mérték az idősorok vagy különböző kategóriák között is változik.

* Ha naplózni kívánja az összértéket befolyásoló főbb változásokat.

* Ha a vállalat éves profitját szeretné ábrázolni különféle bevételi források megjelenítésével, majd az összbevétel (vagy veszteség) kiemelésével.

* Ha a vállalat alkalmazottainak számát szeretné ábrázolni az év eleji és év végi értékekkel.

* Ha szeretné megjeleníteni, hogy mennyi pénzt keresett és költött az egyes hónapok során, valamint a fiók folyóegyenlegét.

## <a name="prerequisites"></a>Előfeltételek

* A Power BI szolgáltatás vagy a Power BI Desktop

* Kiskereskedelmi elemzési mintajelentés

## <a name="get-the-retail-analysis-sample-report"></a>A Kiskereskedelmi elemzési mintajelentés beszerzése

Ez az útmutatás a Kiskereskedelmi elemzési mintát használja. A vizualizációk létrehozásához az adatkészletre és a jelentésre vonatkozó szerkesztési jogosultságok szükségesek. A Power BI mintái mind szerkeszthetőek. Ha mások osztanak meg Önnel jelentést, abban az esetben nem fog tudni vizualizációkat létrehozni jelentésekben. A leírás követéséhez nyissa meg a [Kiskereskedelmi elemzési minta jelentést](../sample-datasets.md).

Ha beszerezte a **Kiskereskedelmi elemzési mintát**, elkezdheti a munkát.

## <a name="create-a-waterfall-chart"></a>Vízesésdiagram létrehozása

Olyan vízesésdiagramot fog létrehozni, amely megjeleníti a havi értékesítési eltérést (a becsült és a tényleges értékek közötti különbséget).

1. A **Saját munkaterületen** válassza az **Adatkészletek** > **Jelentés létrehozása** lehetőséget.

    ![Képernyőkép az Adatkészletek > Jelentés létrehozása lehetőségről.](media/power-bi-visualization-waterfall-charts/power-bi-create-a-report.png)

1. A **Mezők** panelen válassza az **Értékesítés** > **Teljes értékesítési eltérés** lehetőséget.

   ![Az Értékesítés > Teljes értékesítési eltérés kiválasztása és az eredményül kapott vizualizáció képernyőképe.](media/power-bi-visualization-waterfall-charts/power-bi-first-value.png)

1. Válassza a vízesés ikont ![A vízesés ikon képernyőképe](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-icon.png) a diagram fatérképpé konvertálásához.

    Ha a **Teljes értékesítési eltérés** nem az **Y tengely** területén található, húzza át oda.

    ![Vizualizációs sablonok](media/power-bi-visualization-waterfall-charts/convertwaterfall.png)

1. Válassza az **Idő**  > **FiscalMonth** (Pénzügyi hónap) lehetőséget, és adja hozzá a **Kategória** területhez.

    ![vízesés](media/power-bi-visualization-waterfall-charts/power-bi-waterfall.png)

1. Ügyeljen rá, hogy a Power BI időrendi sorrendben rendezze a vízesésdiagramot. Válassza a diagram jobb felső sarkában található három pontot (...).

    Ellenőrizze, hogy megjelenik-e egy sárga jelzés a **Rendezés növekvő sorrendben** és a **PénzügyiHónap** lehetőségek bal oldalán

    ![Rendezés szempontjának kiválasztása > FiscalMonth (Pénzügyi hónap)](media/power-bi-visualization-waterfall-charts/power-bi-sort-by.png)

    Ha megnézi az X tengely értékeit is, láthatja, hogy azok is sorrendben jelennek meg **januártól** **augusztusig**.

    Derítse ki részletesebben, hogy mi járul hozzá legnagyobb mértékben az egyes hónapok közötti változáshoz.

1. Húzza a **Tároló** > **Terület** elemet a **Lebontás** gyűjtőbe.

    ![Megjeleníti a Lebontás gyűjtőben található tárolót](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown.png)

    A Power BI alapértelmezés szerint a havi növekedésekhez és csökkenésekhez hozzájáruló 5 fő tényezőt adja hozzá.

    ![Megjeleníti a Lebontás gyűjtőben található tárolót](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-initial.png)

    Minket azonban csak az első 2 közreműködő érdekel.

1. A **Formázás** panelen válassza a **Lebontás** lehetőséget, és a **Maximum lebontás** beállítást állítsa **2** értékre.

    ![Formázás > Lebontás](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-maximum.png)

    A vízesésdiagram gyors áttekintéséből kiderül, hogy Ohio és Pennsylvania területek járulnak hozzá a változáshoz a legnagyobb (negatív és pozitív) mértékben.

    ![vízesésdiagram](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-axis.png)

    Ez érdekes eredmény. Vajon azért van Ohio és Pennsylvania ilyen jelentős befolyással, mert ezen a két területen jóval több az értékesítés, mint a többin? Ezt könnyedén ellenőrizhetjük.

1. Hozzon létre egy térképet az idei értékesítési érték és a tavalyi értékesítési érték terület szerinti megjelenítéséhez.

    ![PA és Ohio térképe közelről](media/power-bi-visualization-waterfall-charts/power-bi-map.png)

    A térkép alátámasztja ezt az elméletet. Látható, hogy ezen a 2 területen volt a legmagasabb az értékesítés a tavalyi (buborék mérete) és az idei évben (buborék árnyékolása).

## <a name="highlighting-and-cross-filtering"></a>Kiemelés és keresztszűrés

További információ a **Szűrők** panel használatáról: [Szűrők hozzáadása jelentésekhez Szerkesztés nézetben](../power-bi-report-add-filter.md).

A vízesésdiagram egyes oszlopainak kiemelésével a rendszer keresztszűri a jelentésoldalon lévő többi vizualizációt és viszont. Az **Összesen** oszlop azonban nem aktivál kiemelést, és nem reagál a keresztszűrésre.

## <a name="next-steps"></a>Következő lépések

* [Vizualizációk Power BI-jelentésen belüli működésének módosítása](../service-reports-visual-interactions.md)

* [Vizualizációtípusok a Power BI-ban](power-bi-visualization-types-for-reports-and-q-and-a.md)
