---
title: Földrajzi szűrők beállítása mobilalkalmazásokhoz a Power BI Desktopban
description: Ha földrajzi szűrést állított be a Power BI Desktopban található modellben, automatikusan tartózkodási helye szerint szűrheti az adatokat a Power BI mobilalkalmazásokban.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/16/2018
ms.author: maggies
LocalizationGroup: Model your data
ms.openlocfilehash: b8887ba39d3c6d3123d3308eddba2994fbfe6485
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61296039"
---
# <a name="set-geographic-filters-in-power-bi-desktop-for-the-mobile-apps"></a>Földrajzi szűrők beállítása mobilalkalmazásokhoz a Power BI Desktopban
A Power BI Desktopban [kategorizálhatja egy oszlop földrajzi adatait](desktop-data-categorization.md), így a Power BI Desktop tudja, hogyan kezelje az értékeket egy jelentés vizualizációiban. További előny, hogy ha Ön vagy munkatársai a Power BI mobilalkalmazásokban tekintik meg a jelentést, a Power BI automatikusan az Ön helyzetének megfelelő földrajzi szűrést biztosít. 

Tegyük fel például, hogy az értékesítési vezető elutazik, hogy az ügyfelekkel találkozzon, meg szeretne látogatni egy bizonyos ügyfelet, és gyorsan rá szeretne szűrni ennek az ügyfélnek az összes értékesítésére és bevételére. Részletezni szeretné aktuális tartózkodási helyének adatait, például állam, város vagy egy adott cím szerint. Később, ha maradt ideje, szeretne további, a közelben lévő ügyfeleket is meglátogatni. A [jelentéseket a saját tartózkodási helye szerint is szűrheti, így megtalálhatja ezeket ügyfeleket](consumer/mobile/mobile-apps-geographic-filtering.md).

> [!NOTE]
> A mobilalkalmazásban csak akkor szűrhet tartózkodási hely szerint, ha a jelentésben a földrajzi nevek angol nyelven szerepelnek – például „New York City” vagy „Germany”.
> 
> 

## <a name="identify-geographic-data-in-your-report"></a>Földrajzi adatok azonosítása a jelentésben
1. A Power BI Desktopban váltson Adatnézetre ![Adatnézet ikonja](media/desktop-mobile-geofiltering/pbi_desktop_data_icon.png).
2. Válasszon egy földrajzi adatokkal rendelkező oszlopot – például a Város oszlopot.
   
    ![Város oszlop](media/desktop-mobile-geofiltering/power-bi-desktop-geo-column.png)
3. A **Modellezés** lapon válassza az **Adatkategória** lehetőséget, majd a megfelelő kategóriát – ebben a példában ez a **Város**.
   
    ![Adatkategória doboz](media/desktop-mobile-geofiltering/power-bi-desktop-geo-category.png)
4. Folytassa a földrajzi adatkategóriák beállítását a modell bármely mezőjéhez. 
   
   > [!NOTE]
   > Az egyes adatkategóriákhoz több oszlopot is beállíthat a modellben, de ha így tesz, a modell nem tud földrajzi helyzetre szűrni a Power BI mobilalkalmazásban. A földrajzi szűrés használatához a mobilalkalmazásokban csak egy oszlopot állítson be minden adatkategóriához – például csak egy **Város** oszlopot, egy **Állam vagy tartomány** oszlopot és egy **Ország** oszlopot. 
   > 
   > 

## <a name="create-visuals-with-your-geographic-data"></a>Vizualizáció létrehozása a földrajzi adatokkal
1. Váltson Jelentés nézetre ![Jelentés nézet ikonja](media/desktop-mobile-geofiltering/power-bi-desktop-report-icon.png), és hozza létre az adatokban szereplő földrajzi mezőket használó vizualizációt. 
   
    ![Jelentés térképpel](media/desktop-mobile-geofiltering/power-bi-desktop-geo-report.png)
   
    Ebben a példában a modell egy számított oszlopot is tartalmaz, amely a várost és az államot egy oszlopban egyesíti. További információk a [számított oszlopok létrehozásáról a Power BI Desktopban](desktop-calculated-columns.md).
   
    ![Város + Állam mező](media/desktop-mobile-geofiltering/power-bi-desktop-city-state-column.png)
2. Tegye közzé a jelentést a Power BI szolgáltatásban.

## <a name="view-the-report-in-power-bi-mobile-app"></a>A jelentés megtekintése a Power BI mobilalkalmazásban
1. Nyissa meg a jelentést bármelyik [Power BI mobilalkalmazásban](consumer/mobile/mobile-apps-for-mobile-devices.md).
2. Ha olyan földrajzi helyen tartózkodik, amelyhez adatok szerepelnek a jelentésben, automatikusan szűrheti őket a tartózkodási helyére.
   
    ![Földrajzi szűrő a mobilalkalmazásban](media/desktop-mobile-geofiltering/power-bi-mobile-geo-map-set-filter.png)

További információ a [jelentés tartózkodási hely szerinti szűréséről a Power BI mobilalkalmazásokban](consumer/mobile/mobile-apps-geographic-filtering.md).

## <a name="next-steps"></a>További lépések
* [Adatok kategorizálása a Power BI Desktopban](desktop-data-categorization.md)  
* Kérdése van? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

