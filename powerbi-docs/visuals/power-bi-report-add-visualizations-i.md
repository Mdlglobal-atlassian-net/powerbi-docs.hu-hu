---
title: 1\. rész – Vizualizációk hozzáadása Power BI-jelentéshez
description: 1\. rész – Vizualizációk hozzáadása Power BI-jelentéshez
author: mihart
ms.reviewer: rien
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/06/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: fda9c63abbf20eb08adbebacc3f9351c80a2847b
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83147997"
---
# <a name="add-visuals-to-a-power-bi-report-part-1"></a>Vizualizációk hozzáadása Power BI-jelentéshez (1. rész)

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

A cikk röviden bemutatja a vizualizációk jelentésekben történő létrehozását. Tartalma a Power BI szolgáltatásra és a Power BI Desktopra is vonatkozik. Magasabb szintű ismertetést ennek a sorozatnak a [2. része](power-bi-report-add-visualizations-ii.md) kínál.

## <a name="prerequisites"></a>Előfeltételek

Ez az oktatóanyag az [Értékesítési és marketing PBIX-fájlt](https://download.microsoft.com/download/9/7/6/9767913A-29DB-40CF-8944-9AC2BC940C53/Sales%20and%20Marketing%20Sample%20PBIX.pbix) használja.

1. A Power BI Desktop menüsorának bal felső részén válassza a **Fájl** > **Megnyitás** lehetőséget
   
2. Keresse meg az **Értékesítési és marketing minta PBIX-fájl** példányát

1. Nyissa meg az **Értékesítési és marketing minta PBIX-fájlt** jelentésnézetben ![A jelentésnézet ikon képernyőképe.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Kiválasztás ![A sárga fül képernyőképe.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) új oldal hozzáadásához.

> [!NOTE]
> A jelentés egy Power BI-munkatárssal való megosztásához mindkettőjüknek Power BI Pro-licenccel kell rendelkezniük, vagy a jelentésnek egy Premium kapacitásban kell lennie. Lásd a [jelentések megosztását](../collaborate-share/service-share-reports.md) ismertető szakaszt.

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
