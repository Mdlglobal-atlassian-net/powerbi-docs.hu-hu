---
title: 2\. rész – Vizualizációk hozzáadása Power BI-jelentésekhez
description: 2\. rész – Vizualizációk hozzáadása Power BI-jelentésekhez
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/23/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c42d96fea37a6309908dd357425c3d0504e18397
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61410188"
---
# <a name="part-2-add-visualizations-to-a-power-bi-report"></a>2\. rész – Vizualizációk hozzáadása Power BI-jelentésekhez
Az [1. részben](power-bi-report-add-visualizations-ii.md) alapszintű képi megjelenítéseket hozott létre a mezők neve melletti jelölőnégyzetek bejelölésével.  A 2. részben megtudhatja, hogyan hozhat létre és módosíthat képi megjelenítéseket az egér húzásával, valamint a **Mezők** és a **Képi megjelenítések** panelek nyújtotta lehetőségek teljes körű kiaknázásával.

### <a name="prerequisites"></a>Előfeltételek
- [1. rész](power-bi-report-add-visualizations-ii.md)
- Power BI Desktop – a jelentésekhez a Power BI szolgáltatás vagy a Power BI Desktop használatával adhatók hozzá vizualizációk. Ebben az oktatóanyagban a Power BI Desktopot fogjuk használni. 
- [Kiskereskedelmi elemzési minta](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)

## <a name="create-a-new-visualization"></a>Új képi megjelenítés létrehozása
Ebben az oktatóanyagban a Kiskereskedelmi elemzés adatkészlet felhasználásával létrehozunk néhány fontosabb képi megjelenítést.

### <a name="open-a-report-and-add-a-new-blank-page"></a>Nyisson meg egy jelentést, és adjon hozzá egy üres oldalt.
1. Nyissa meg a Kiskereskedelmi elemzési minta .PBIX-fájlját a Power BI Desktopban. 
   ![](media/power-bi-report-add-visualizations-ii/power-bi-open-desktop.png)   

2. A vászon aljánál lévő sárga plusz ikonra kattintva adhat hozzá egy új oldalt.

### <a name="add-a-visualization-that-looks-at-this-years-sales-compared-to-last-year"></a>Adjon hozzá egy olyan képi megjelenítést, amely az idei értékesítési adatokat a tavalyiakkal veti össze.
1. Az **Értékesítés** táblában válassza az **Idei értékesítés** > **Érték** és a **Tavalyi értékesítések** mezőket. A Power BI létrehoz egy oszlopdiagramot.  Ez valamelyest azért érdekes, és nem árt a mélyére ásni. Hogy néz ki az értékesítés havi bontásban?  
   
   ![](media/power-bi-report-add-visualizations-ii/power-bi-barchart.png)
2. Az Idő tábláról húzza a **FiscalMonth** elemet a **Tengely** területre.  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-month.png)
3. [Módosítása a képi megjelenítést](power-bi-report-change-visualization-type.md) területdiagramra.  Számos különféle képi megjelenítési típusból választhat – ha segítségre van szüksége a választáshoz, olvassa át [az egyes típusok leírását, a bevált gyakorlatokra vonatkozó tanácsokat és az oktatóanyagokat](power-bi-visualization-types-for-reports-and-q-and-a.md). A Képi megjelenítések panelen válassza a Területdiagram ikont ![](media/power-bi-report-add-visualizations-ii/power-bi-areachart.png).
4. A képi megjelenítés rendezéséhez válassza a három pontot (...), majd a **Rendezés pénzügyi hónapok szerint** lehetőséget.
5. [A képi megjelenítés átméretezéséhez](power-bi-visualization-move-and-resize.md) jelölje ki a képi megjelenítést, majd fogja meg és húzza a külső körvonalak valamelyikét. Legyen elég széles ahhoz, hogy a görgetősáv már eltűnjön, de egy másik képi megjelenítés még elférjen mellette.
   
   ![](media/power-bi-report-add-visualizations-ii/pbi_part2_7b.png)
6. [Mentse a jelentést](../service-report-save.md).

### <a name="add-a-map-visualization-that-looks-at-sales-by-location"></a>Térképi megjelenítés hozzáadása az értékesítések helyek szerinti megjelenítéséhez
1. Az **Üzletek** táblában válassza a **Terület** elemet. A Power BI felismeri, hogy a Terület helyet jelöl, ezért egy térképi megjelenítést hoz létre.  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-map.png)
2. Húzza az **Összes üzlet** elemet a Méret területre.  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-map2.png)
3. Adjon hozzá egy jelmagyarázatot.  Ha szeretné az adatokat az üzletek neve alapján megjeleníteni, húzza a **Lánc** mezőt a Jelmagyarázat területre.  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-legend.png)

## <a name="next-steps"></a>Következő lépések
* További információk [a Power BI-jelentésekben lévő vizualizációkról](power-bi-report-visualizations.md).  
* További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

