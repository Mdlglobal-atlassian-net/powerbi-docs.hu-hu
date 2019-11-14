---
title: 2\. rész – Vizualizációk hozzáadása Power BI-jelentésekhez
description: 2\. rész – Vizualizációk hozzáadása Power BI-jelentésekhez
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/28/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: e9759f69668780b450117e5e6255e7f5cb7e67f5
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73881020"
---
# <a name="part-2-add-visualizations-to-a-power-bi-report"></a>2\. rész – Vizualizációk hozzáadása Power BI-jelentésekhez

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Az [1. részben](power-bi-report-add-visualizations-i.md) alapszintű képi megjelenítéseket hozott létre a mezők neve melletti jelölőnégyzetek bejelölésével.  A 2. részben megtudhatja, hogyan hozhat létre és módosíthat vizualizációkat az egér húzásával, valamint a **Mezők** és a **Vizualizációk** panel nyújtotta lehetőségek teljes körű kiaknázásával.


## <a name="create-a-new-visualization"></a>Új képi megjelenítés létrehozása
Ebben az oktatóanyagban a Kiskereskedelmi elemzés adathalmaz felhasználásával létrehozunk néhány fontosabb vizualizációt.

## <a name="prerequisites"></a>Előfeltételek

Ez az oktatóanyag a [Kiskereskedelmi elemzési minta PBIX-fájlt](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) használja.

1. A Power BI Desktop menüsorának bal felső részén válassza a **Fájl** > **Megnyitás** lehetőséget.
   
2. Keresse meg a **Kiskereskedelmi elemzési minta PBIX-fájlt**

1. Nyissa meg a **Kiskereskedelmi elemzési minta PBIX-fájlt** jelentésnézetben ![A jelentésnézet ikon képernyőképe.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Kiválasztás ![A sárga fül képernyőképe.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) új oldal hozzáadásához.

## <a name="add-visualizations-to-the-report"></a>Vizualizációk hozzáadása a jelentéshez

A vizualizáció létrehozásához válasszon egy mezőt a **Mezők** panelen. A létrehozott vizualizáció típusa a kiválasztott mező típusától függ. A Power BI az adattípus alapján határozza meg, milyen vizualizáción jelenítse meg az eredményeket. A vizualizáció úgy módosítható, hogy a Vizualizációk panel kiválaszt egy másik ikont. Vegye figyelembe, hogy nem minden vizualizáció lesz alkalmas az adott adatok megjelenítésére. Földrajzi adatok például nem ábrázolhatók jól tölcsér- vagy vonaldiagramon. 


### <a name="add-an-area-chart-that-looks-at-this-years-sales-compared-to-last-year"></a>A folyó évi értékesítési adatokat a tavalyiakkal összevető területdiagram felvétele

1. Az **Értékesítés** táblában válassza az **Idei értékesítés** > **Érték** és a **Tavalyi értékesítések** mezőket. A Power BI létrehoz egy oszlopdiagramot.  Ez a diagram érdekes, és érdemes lehet jobban feltárni. Hogy néz ki az értékesítés havi bontásban?  
   
   ![Oszlopdiagram képernyőképe](media/power-bi-report-add-visualizations-ii/power-bi-start.png)

2. Az Idő tábláról húzza a **FiscalMonth** elemet a **Tengely** területre.  
   ![A FiscalMonth értéket egy tengelyen ábrázoló oszlopdiagram képernyőképe](media/power-bi-report-add-visualizations-ii/power-bi-fiscalmonth.png)

3. [Módosítása a vizualizációt](power-bi-report-change-visualization-type.md) területdiagramra.  Számos különféle vizualizációtípusból választhat – ha segítségre van szüksége a választáshoz, olvassa át [az egyes típusok leírását, a bevált gyakorlatokra vonatkozó tanácsokat és az oktatóanyagokat](power-bi-visualization-types-for-reports-and-q-and-a.md). Válassza ki a területdiagram ikont a Vizualizációk panelen.![Területdiagram ikon a Vizualizációk panelről](media/power-bi-report-add-visualizations-ii/power-bi-area-chart.png).

4. Rendezze a vizualizációt a **További műveletek** (...) lehetőség, majd a **Rendezés alapja** >  **FiscalMonth** elem kiválasztásával.

5. [A képi megjelenítés átméretezéséhez](power-bi-visualization-move-and-resize.md) jelölje ki a képi megjelenítést, majd fogja meg és húzza a külső körvonalak valamelyikét. Legyen elég széles ahhoz, hogy a görgetősáv már eltűnjön, de egy másik képi megjelenítés még elférjen mellette.
   
   ![képernyőkép a területdiagram vizualizációról](media/power-bi-report-add-visualizations-ii/pbi_part2_7b.png)
6. [Mentse a jelentést](../service-report-save.md).

### <a name="add-a-map-visualization-that-looks-at-sales-by-location"></a>Térképi megjelenítés hozzáadása az értékesítések helyek szerinti megjelenítéséhez

1. Az **Üzletek** táblában válassza a **Terület** elemet. Húzza az **Összes üzlet** elemet a Méret területre. A Power BI felismeri, hogy a Terület helyet jelöl, ezért egy térképi megjelenítést hoz létre.  
   ![Területdiagram](media/power-bi-report-add-visualizations-ii/power-bi-map1.png)

2. Adjon hozzá egy jelmagyarázatot.  Ha az adatokat az üzletek neve szerint szeretné ábrázolni, húzza a Jelmagyarázat területre a **Store** > **Chain** (Üzlet>Üzletlánc) elemet.  
   ![jelentésvászon a mezőlistában a Láncból a Jelmagyarázat gyűjtő láncba](media/power-bi-report-add-visualizations-ii/power-bi-chain.png)

## <a name="next-steps"></a>Következő lépések
* További információk [a Power BI-jelentésekben lévő vizualizációkról](power-bi-report-visualizations.md).  
* További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

