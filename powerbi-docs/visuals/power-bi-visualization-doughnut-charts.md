---
title: Perecdiagramok a Power BI szolgáltatásban
description: Perecdiagramok a Power BI szolgáltatásban
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/11/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: d90ef12e1971ddc81928746f338ba927a48d5b23
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/23/2019
ms.locfileid: "71195134"
---
# <a name="doughnut-charts-in-power-bi"></a>Perecdiagramok a Power BI szolgáltatásban

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

A perecdiagram a tortadiagramhoz hasonlóan a részek egészhez való viszonyát mutatja. Az egyetlen különbség az, hogy a középső rész üres, így helyet biztosít egy címkének vagy ikonnak.

## <a name="prerequisite"></a>Előfeltétel

Ez az oktatóanyag a [Kiskereskedelmi elemzési minta PBIX-fájlt](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) használja.

1. A menüsor bal felső részén válassza a **Fájl** > **Megnyitás** lehetőséget
   
2. Keresse meg a **Kiskereskedelmi elemzési minta PBIX-fájlt**

1. Nyissa meg a **Kiskereskedelmi elemzési minta PBIX-fájlt** jelentésnézetben ![A jelentésnézet ikon képernyőképe.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Kiválasztás ![A sárga fül képernyőképe.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) új oldal hozzáadásához.


## <a name="create-a-doughnut-chart"></a>Perecdiagram létrehozása

1. Kezdjen egy üres jelentést tartalmazó lappal, majd a Mezők panelen válassza az **Értékesítés** \> **Előző évi értékesítés** lehetőséget.  
   
3. A Megjelenítések ablaktáblán válassza a perecdiagram ikonját ![perecdiagram ikonja](media/power-bi-visualization-doughnut-charts/power-bi-icon.png) az oszlopdiagram perecdiagrammá alakításához. Ha a **Last Year Sales** (Előző évi értékesítés) nem az **Értékek** területen található, húzza át oda.
     
   ![A Vizualizációk panel a kiválasztott perecdiagram lehetőséggel](media/power-bi-visualization-doughnut-charts/power-bi-doughnut-chart.png)

4. Válassza az **Elem** \> **Kategória** lehetőséget, hogy hozzáadja az **Jelmagyarázat** területhez. 
     
    ![a perec a Mezők panel mellett](media/power-bi-visualization-doughnut-charts/power-bi-doughnut-done.png)

5. Ha szeretné, [módosíthatja a diagram szövegének méretét és színét](power-bi-visualization-customize-title-background-and-legend.md). 

## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás
* A perecdiagram értékeinek összege 100%-nak kell lennie.
* A túl sok kategória megnehezíti az átlátást és az értelmezést.
* A perecdiagramok használhatók a legjobban, hogy egy részt az egészhez hasonlítsunk, kevésbé arra, hogy külön szakaszokat vessünk össze egymással. 

## <a name="next-steps"></a>Következő lépések
[Tölcsérdiagramok a Power BI-ban](power-bi-visualization-funnel-charts.md)

[Vizualizációtípusok a Power BI-ban](power-bi-visualization-types-for-reports-and-q-and-a.md)


