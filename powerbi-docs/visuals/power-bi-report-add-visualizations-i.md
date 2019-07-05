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
ms.date: 06/17/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c5838d12351c06d0a76a975c9c473b1c00856d97
ms.sourcegitcommit: 90aa7ea5fcc7cf0fd7f6c3c1efeff5f27e8ef0dd
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/20/2019
ms.locfileid: "67299237"
---
# <a name="part-1-add-visualizations-to-a-power-bi-report"></a>1\. rész – Vizualizációk hozzáadása Power BI-jelentéshez

A cikk röviden bemutatja a vizualizációk jelentésekben történő létrehozását. Tartalma a Power BI szolgáltatásra és a Power BI Desktopra is vonatkozik. Magasabb szintű ismertetést ennek a sorozatnak a [2. része](power-bi-report-add-visualizations-ii.md) kínál. Amanda bemutatja, hogyan lehet különbözőképpen létrehozni, szerkeszteni és formázni a vizualizációkat a jelentésvásznon. Ezután Ön is megpróbálhatja létrehozni a saját jelentését a [Értékesítési és marketing minta](../sample-datasets.md) segítségével.

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

## <a name="open-a-report-and-add-a-new-page"></a>Jelentés megnyitása és egy üres lap hozzáadása

1. Nyisson meg egy [jelentést Szerkesztési nézetben](../service-interact-with-a-report-in-editing-view.md).

    Ez az oktatóanyag az [Értékesítési és marketing mintát](../sample-datasets.md) használja.

1. Ha a **Mezők** panel nem látható, a nyíl ikonnal tudja megnyitni.

   ![](media/power-bi-report-add-visualizations-i/pbi_nancy_fieldsfiltersarrow.png)

1. Adjon hozzá egy üres lapot a jelentéshez.

## <a name="add-visualizations-to-the-report"></a>Vizualizációk hozzáadása a jelentéshez

1. A vizualizáció létrehozásához válasszon egy mezőt a **Mezők** panelen.

    Kiindulhat egy numerikus mezőből, például: **Értékesítési adatok** > **Értékesítési összeg**. A Power BI létrehoz egy oszlopdiagramot egyetlen oszloppal.

    ![Egyetlen oszlopból álló oszlopdiagram képernyőképe.](media/power-bi-report-add-visualizations-i/pbi_onecolchart.png)

    Kezdheti olyan kategóriamezővel is, mint a **Név** vagy a **Termék**. A Power BI egy táblázatot hoz létre, és hozzáadja az adott mezőt az **Értékek** területhez.

    ![GIF-ábra táblázat létrehozásáról a Termék, majd egy kategória kiválasztásával.](media/power-bi-report-add-visualizations-i/pbi_agif_createchart3.gif)

    Kiindulhat akár olyan földrajzi mezőből is, mint a **Földrajzi hely** > **Város**. a Power BI a Bing Maps segítségével egy térképi vizualizációt hoz létre.

    ![Térkép vizualizáció képernyőképe.](media/power-bi-report-add-visualizations-i/power-bi-map.png)

1. Hozzon létre egy vizualizációt, majd módosítsa a típusát. Válassza ki a **Termék** > **Kategória**, majd a **Termék** > **Termékek száma** lehetőséget, és adja hozzá mindkettőt az **Értékekhez**.

   ![A Mezők panel képernyőképe az Értékek terület kiemelésével.](media/power-bi-report-add-visualizations-i/part1table1.png)

1. Módosítsa a vizualizációt oszlopdiagrammá a **Halmozott oszlopdiagram** ikon választásával.

   ![Képernyőkép a Vizualizációk panelről, a Halmozott oszlopdiagram ikon kiemelésével.](media/power-bi-report-add-visualizations-i/part1converttocolumn.png)

1. Ha vizualizációkat hoz létre egy jelentésben, [rögzítheti őket az irányítópulton](../service-dashboard-pin-tile-from-report.md). A vizualizáció rögzítéséhez kattintson a rajzszög ikonra ![A rajzszög ikon képernyőképe.](media/power-bi-report-add-visualizations-i/pinnooutline.png).

   ![Oszlopdiagram vizualizáció képernyőképe a rajzszög ikon kiemelésével.](media/power-bi-report-add-visualizations-i/part1pin1.png)
  
## <a name="next-steps"></a>Következő lépések

 Folytatás:

* [2. rész: Vizualizációk hozzáadása Power BI-jelentésekhez](power-bi-report-add-visualizations-ii.md)

* [Használhatja a vizualizációkat](../consumer/end-user-reading-view.md) a jelentésben.

* [Még hatékonyabban használhatja a vizualizációkat](power-bi-report-visualizations.md).

* [Mentheti a jelentést](../service-report-save.md).
