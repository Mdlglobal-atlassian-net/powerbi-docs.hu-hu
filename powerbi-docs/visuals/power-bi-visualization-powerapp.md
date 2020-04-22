---
title: Új Power App-alkalmazás beágyazása egy Power BI-jelentésbe
description: Alkalmazás beágyazása, amely ugyanazt az adatforrást használja, és ugyanúgy szűrhető, mint a jelentés többi eleme
author: mihart
manager: kvivek
ms.reviewer: tapan maniar
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 03/17/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 5628a114b872b7c0d92d5079198616a20fe85b87
ms.sourcegitcommit: d43761104f7daf4b2f297648855bb573b53e6d8c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/18/2020
ms.locfileid: "81637812"
---
# <a name="tutorial-embed-a-power-apps-visual-in-a-power-bi-report"></a>Oktatóanyag: Power Apps-vizualizáció beágyazása egy Power BI-jelentésbe

Ebben az útmutatóban a PowerApps-vizualizáció használatával fog létrehozni egy új alkalmazást, amelyet egy Power BI-mintajelentésbe ágyaz. Az alkalmazás a jelentés többi vizualizációjához is kapcsolódni fog.

Ha még nincs PowerApps-előfizetése, kezdés előtt [hozzon létre egy ingyenes fiókot](https://web.powerapps.com/signup?redirect=marketing&email=).

Az oktatóanyag a következőket ismerteti:
> [!div class="checklist"]
> * Power Apps-vizualizáció hozzáadása Power BI-jelentéshez
> * Új alkalmazás létrehozása a Power Apps szolgáltatásban, amely a Power BI-jelentés adatait használja
> * A Power Apps-vizualizáció megtekintése és használata a jelentésben

## <a name="prerequisites"></a>Előfeltételek

* [Google Chrome](https://www.google.com/chrome/browser/) vagy [Microsoft Edge](https://www.microsoft.com/windows/microsoft-edge) böngésző
* [Power BI-előfizetés](https://docs.microsoft.com/power-bi/service-self-service-signup-for-power-bi) telepített [Lehetőségelemzési mintával](https://docs.microsoft.com/power-bi/sample-opportunity-analysis#get-the-content-pack-for-this-sample)
* Ismeretek a következőkkel kapcsolatban: [Alkalmazások létrehozása a PowerAppsben](https://docs.microsoft.com/powerapps/maker/canvas-apps/data-platform-create-app-scratch) és [Power BI-jelentések szerkesztése](https://docs.microsoft.com/power-bi/service-the-report-editor-take-a-tour)



## <a name="create-a-new-app"></a>Új alkalmazás létrehozása
Amikor a Power Apps-vizualizációt hozzáadja a jelentéshez, elindul a Power Apps Studio, és élő adatkapcsolatot hoz létre a Power Apps és a Power BI között.

1. Nyissa meg a Lehetőségelemzési mintajelentést, majd válassza az *Upcoming Opportunities* (Jövőbeli lehetőségek) lapot. 


2. Helyezze és méretezze át a jelentés néhány csempéjét, hogy az új vizualizáció elférhessen.

    ![Jelentések csempéinek áthelyezése és átméretezése](media/power-bi-visualization-powerapp/power-bi-report-page.jpg)

2. A Vizualizációk panelen válassza ki a Power Apps-ikont, majd méretezze át a vizualizációt úgy, hogy az illeszkedjen a létrehozott területhez.

    ![A Vizualizációk panel a kijelölt Power Apps-ikonnal](media/power-bi-visualization-powerapp/power-bi-powerapps-icon.jpg)

3. A **Mezők** ablaktáblában válassza ki a **Name** (Név), **Product Code** (Termékkód) és **Sales Stage** (Értékesítési szakasz) mezőket. 

    ![mezők kijelölése](media/power-bi-visualization-powerapp/power-bi-fields.png)

4. A Power Apps-vizualizáció csempéjén válassza ki azt a Power Apps-környezetet, amelyben az alkalmazást szeretné létrehozni, majd válassza az **Új létrehozása** lehetőséget.

    ![Új alkalmazás létrehozása](media/power-bi-visualization-powerapp/power-bi-create-new-powerapp.png)

    A Power Apps Studióban létrejött egy alapszintű alkalmazás egy *katalógussal*, amely a Power BI-ban kiválasztott mezők egyikét jeleníti meg.

    ![Megnyílik a Power Apps](media/power-bi-visualization-powerapp/power-bi-power-app.png)

5.  Méretezze át a katalógust úgy, hogy az csak a képernyő felét foglalja el. 

6. A bal oldali ablaktáblában válassza a **Screen1** lehetőséget, majd állítsa a képernyő **Kitöltés** tulajdonságát „LightBlue” (Világoskék) értékre, hogy az jobban kitűnjön a jelentésben.

    ![színpaletta](media/power-bi-visualization-powerapp/power-bi-powerapps-fill.png)

6. Csináljon helyet egy felirat típusú vezérlőnek. 

    ![a katalógusméret módosítása](media/power-bi-visualization-powerapp/power-bi-powerapps-gallery.png)


8. A **katalógus** alatt szúrjon be egy szöveges felirat típusú vezérlőelemet.

   ![feliratvezérlő](media/power-bi-visualization-powerapp/power-bi-label.png)

7. Húzza a feliratot a vizualizáció aljára. Állítsa a **Text** tulajdonságot `"Opportunity Count: " & CountRows(Gallery1.AllItems)` értékre. A címke mostantól a jövőbeli lehetőségek számát jeleníti meg.

    ![Alkalmazás átméretezett katalógussal](media/power-bi-visualization-powerapp/power-bi-power-app-label.png)

    ![Frissített címkés alkalmazás](media/power-bi-visualization-powerapp/power-bi-label-live.png)

7. Mentse el az alkalmazást „Opportunities app” néven. 

    ![az alkalmazás mentése](media/power-bi-visualization-powerapp/power-bi-save-powerapp.png)


## <a name="view-the-app-in-the-report"></a>Az alkalmazás megtekintése a jelentésben
Az alkalmazás most már elérhető a Power BI-jelentésben, és a többi vizualizációval is kapcsolatban áll, mert ugyanazt az adatforrást használja.

![Alkalmazás a Power BI-jelentésben](media/power-bi-visualization-powerapp/power-bi-powerapps-visual.png)

A Power BI-jelentésben a **Jan** lehetőséget kiválasztva a dátumszeletelőben szűrést alkalmazhat a teljes jelentésre, beleértve az alkalmazásban szereplő adatokat is.

![szűrt jelentés](media/power-bi-visualization-powerapp/power-bi-last.png)

Megfigyelheti, hogy a lehetőségek száma az alkalmazásban megegyezik a jelentés bal felső sarkában szereplő számmal. A jelentés más elemeit kiválasztva az alkalmazásban szereplő adatok is frissülnek.


## <a name="clean-up-resources"></a>Erőforrások felszabadítása
Ha már nem szeretné tovább használni a Lehetőségelemzési mintát, akkor nyugodtan törölheti az irányítópultot, a jelentést és az adatkészletet.


## <a name="next-steps"></a>Következő lépések
[Q&A – vizualizáció](power-bi-visualization-types-for-reports-and-q-and-a.md)    
[Oktatóanyag: Power Apps-vizualizáció beágyazása egy Power BI-jelentésbe](https://docs.microsoft.com/powerapps/maker/canvas-apps/powerapps-custom-visual)