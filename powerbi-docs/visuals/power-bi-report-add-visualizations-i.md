---
title: 1\. rész – Vizualizációk hozzáadása Power BI-jelentéshez
description: 1\. rész – Vizualizációk hozzáadása Power BI-jelentéshez
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/28/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: e25db5ab57e3a52ffc08020dc980553e515256bf
ms.sourcegitcommit: 2a61d8b1e2707a24fe1284a8a4034b11c3999842
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/29/2019
ms.locfileid: "73048979"
---
# <a name="part-1-add-visualizations-to-a-power-bi-report"></a>1\. rész – Vizualizációk hozzáadása Power BI-jelentéshez

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

A cikk röviden bemutatja a vizualizációk jelentésekben történő létrehozását. Tartalma a Power BI szolgáltatásra és a Power BI Desktopra is vonatkozik. Magasabb szintű ismertetést ennek a sorozatnak a [2. része](power-bi-report-add-visualizations-ii.md) kínál. Amanda bemutatja, hogyan lehet különbözőképpen létrehozni, szerkeszteni és formázni a vizualizációkat a jelentésvásznon. Ezután Ön is megpróbálhatja létrehozni a saját jelentését a [Értékesítési és marketing minta](../sample-datasets.md) segítségével.

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

## <a name="prerequisites"></a>Előfeltételek

Ez az oktatóanyag az [Értékesítési és marketing PBIX-fájlt](http://download.microsoft.com/download/9/7/6/9767913A-29DB-40CF-8944-9AC2BC940C53/Sales%20and%20Marketing%20Sample%20PBIX.pbix) használja.

1. A Power BI Desktop menüsorának bal felső részén válassza a **Fájl** > **Megnyitás** lehetőséget
   
2. Keresse meg az **Értékesítési és marketing minta PBIX-fájl** példányát

1. Nyissa meg az **Értékesítési és marketing minta PBIX-fájlt** jelentésnézetben ![A jelentésnézet ikon képernyőképe.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Kiválasztás ![A sárga fül képernyőképe.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) új oldal hozzáadásához.

## <a name="add-visualizations-to-the-report"></a>Vizualizációk hozzáadása a jelentéshez

1. A vizualizáció létrehozásához válasszon egy mezőt a **Mezők** panelen.

    Kezdjen egy olyan numerikus mezővel, mint például a **Sales** (Értékesítés) > **TotalSales** (Értékesítés összesen). A Power BI létrehoz egy oszlopdiagramot egyetlen oszloppal.

    ![Egyetlen oszlopból álló oszlopdiagram képernyőképe.](media/power-bi-report-add-visualizations-i/power-bi-column-chart.png)

    Kezdheti olyan kategóriamezővel is, mint a **Név** vagy a **Termék**. A Power BI egy táblázatot hoz létre, és hozzáadja az adott mezőt az **Értékek** területhez.

    ![Képernyőkép egy négy kategóriát tartalmazó táblázatról](media/power-bi-report-add-visualizations-i/power-bi-product.png)

    Kiindulhat akár olyan földrajzi mezőből is, mint a **Földrajzi hely** > **Város**. a Power BI a Bing Maps segítségével egy térképi vizualizációt hoz létre.

    ![Térkép vizualizáció képernyőképe.](media/power-bi-report-add-visualizations-i/power-bi-maps.png)

## <a name="change-the-type-of-visualization"></a>A vizualizáció típusának módosítása

 Hozzon létre egy vizualizációt, majd módosítsa a típusát. 
 
 1. Válassza ki a **Termék** > **Kategória**, majd a **Termék** > **Termékek száma** lehetőséget, és adja hozzá mindkettőt az **Értékekhez**.

    ![A Mezők panel képernyőképe az Értékek terület kiemelésével.](media/power-bi-report-add-visualizations-i/power-bi-create-visual.png)

1. Módosítsa a vizualizációt oszlopdiagrammá a **Halmozott oszlopdiagram** ikon választásával.

   ![Képernyőkép a Vizualizációk panelről, a Halmozott oszlopdiagram ikon kiemelésével.](media/power-bi-report-add-visualizations-i/power-bi-convert.png)

1. A vizualizáció rendezési módjának módosításához válassza a **További műveletek** (...) lehetőséget.  A rendezési beállításokkal módosíthatja a rendezés irányát (növekvő vagy csökkenő), és módosíthatja a rendezéshez használt oszlopot (**Rendezési szempont**).

   ![Képernyőkép a További műveletek legördülő menüről.](media/power-bi-report-add-visualizations-i/power-bi-sort.png)
  
## <a name="next-steps"></a>Következő lépések

 Folytatás:

* [2. rész: Vizualizációk hozzáadása Power BI-jelentésekhez](power-bi-report-add-visualizations-ii.md)

* [Használhatja a vizualizációkat](../consumer/end-user-reading-view.md) a jelentésben.

