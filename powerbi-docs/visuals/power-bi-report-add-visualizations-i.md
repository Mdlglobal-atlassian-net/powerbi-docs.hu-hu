---
title: 1. rész – Vizualizációk hozzáadása Power BI-jelentésekhez
description: 1. rész – Vizualizációk hozzáadása Power BI-jelentésekhez
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 08/23/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: f2edbd7b0b977b378d25634a0f9505101350d73b
ms.sourcegitcommit: e17fc3816d6ae403414cf5357afbf6a492822ab8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/04/2018
ms.locfileid: "52829803"
---
# <a name="part-i-add-visualizations-to-a-power-bi-report"></a>1. rész – Vizualizációk hozzáadása Power BI-jelentésekhez
A cikk röviden bemutatja a vizualizációk jelentésekben történő létrehozását mind a Power BI szolgáltatás, mind pedig a Power BI Desktop használatával.  Részletesebb útmutatásért [lásd a II. részt](power-bi-report-add-visualizations-ii.md). Amanda bemutatja, hogyan lehet különbözőképpen létrehozni, szerkeszteni és formázni a vizualizációkat a jelentésvásznon. Ezután Ön is megpróbálhatja létrehozni a saját jelentését a [Értékesítési és marketing minta](../sample-datasets.md) segítségével.

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>


## <a name="open-a-report-and-add-a-new-page"></a>Jelentés megnyitása és egy üres lap hozzáadása
1. Nyisson meg egy [jelentést Szerkesztési nézetben](../consumer/end-user-reading-view.md). Ez az oktatóanyag az [Értékesítési és marketing mintát](../sample-datasets.md) használja.
2. Ha a Mezők panel nem látható, a nyíl ikonnal tudja megnyitni. 
   
   ![](media/power-bi-report-add-visualizations-i/pbi_nancy_fieldsfiltersarrow.png)
3. Adjon hozzá egy üres lapot a jelentéshez.

## <a name="add-visualizations-to-the-report"></a>Vizualizációk hozzáadása a jelentéshez
1. A vizualizáció létrehozásához válasszon egy mezőt a **Mezők** panelen.  
   
   **Kezdjen egy numerikus mezővel**, például SalesFact > Sales $. A Power BI létrehoz egy oszlopdiagramot egyetlen oszloppal.
   
   ![](media/power-bi-report-add-visualizations-i/pbi_onecolchart.png)
   
   **Ha egy kategóriamezővel kezdi**, mint a Név vagy a Termék, A Power BI egy táblát hoz létre, és hozzáadja az adott mezőt az **Értékek** területhez.
   
   ![](media/power-bi-report-add-visualizations-i/pbi_agif_createchart3.gif)
   
   **Ha egy földrajzi mezővel indít**, mint a Földrajz > Város, a Power BI a Bing Maps segítségével egy térképi vizualizációt hoz létre.
   
   ![](media/power-bi-report-add-visualizations-i/power-bi-map.png)
2. Hozzon létre egy vizualizációt, majd módosítsa a típusát. Válassza ki a **Termék > Kategória**, majd a **Termék > Termékek száma** lehetőséget, és adja hozzá mindkettőt az **Értékekhez**.
   
   ![](media/power-bi-report-add-visualizations-i/part1table1.png)
3. Az oszlopdiagram ikonra kattintva váltsa át a vizualizációt egy oszlopdiagramra.
   
   ![](media/power-bi-report-add-visualizations-i/part1converttocolumn.png)
4. Ha vizualizációkat hoz létre egy jelentésben, [rögzítheti őket az irányítópulton](../service-dashboard-pin-tile-from-report.md). A vizualizáció rögzítéséhez kattintson a rajzszög ikonra ![](media/power-bi-report-add-visualizations-i/pinnooutline.png).
   
   ![](media/power-bi-report-add-visualizations-i/part1pin1.png)
  

## <a name="next-steps"></a>Következő lépések
 Továbbléphet a következőre: [2. rész: Vizualizációk hozzáadása Power BI-jelentésekhez](power-bi-report-add-visualizations-ii.md).
   
   [Használhatja a vizualizációkat](../consumer/end-user-reading-view.md) a jelentésben.
   
   [Még hatékonyabban használhatja a vizualizációkat](power-bi-report-visualizations.md).
   
   [Mentheti a jelentést](../service-report-save.md).
