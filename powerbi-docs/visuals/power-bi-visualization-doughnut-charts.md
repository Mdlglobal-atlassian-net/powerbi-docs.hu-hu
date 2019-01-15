---
title: Perecdiagramok a Power BI szolgáltatásban
description: Perecdiagramok a Power BI szolgáltatásban
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/24/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 4c69113d245d47a4d2702f16f6cea21a6cbd3b0b
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54295813"
---
# <a name="doughnut-charts-in-power-bi"></a>Perecdiagramok a Power BI szolgáltatásban
A perecdiagram a tortadiagramhoz hasonlóan a részek egészhez való viszonyát mutatja. Az egyetlen különbség az, hogy a középső rész üres, így helyet biztosít egy címkének vagy ikonnak.

## <a name="create-a-doughnut-chart"></a>Perecdiagram létrehozása
Ezen útmutatás a Kiskereskedelmi elemzési mintát használja egy olyan perecdiagram létrehozásához, mely az ez évi értékesítést jeleníti meg kategória szerint. Annak érdekében, hogy követni tudja a lépéseket, [töltse le a mintát](../sample-datasets.md), amely a Power BI szolgáltatásban vagy a Power BI Desktopban használható.

1. Kezdje a műveletet egy üres jelentésoldalon. Ha a Power BI szolgáltatást használja, mindenképpen a [Szerkesztési nézetében](../service-interact-with-a-report-in-editing-view.md) nyissa meg a jelentést.

2. A Mezők panelen válassza a **Sales** \> **Last Year Sales** (Értékesítés > Előző évi értékesítés) lehetőséget.  
   
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


