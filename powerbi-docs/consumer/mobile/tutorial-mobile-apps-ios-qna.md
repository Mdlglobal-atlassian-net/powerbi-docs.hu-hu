---
title: 'Oktatóanyag: Kérdezés a Q&A virtuális elemzőjével iOS-alkalmazásokban'
description: Ebben az oktatóanyagban azt mutatjuk be, hogyan tehet fel a saját szavaival megfogalmazott kérdéseket a mintaadatokkal kapcsolatban az iOS-eszközökön futó Power BI mobilalkalmazás Q&A virtuális elemzőjét használva.
author: mshenhav
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: tutorial
ms.date: 11/16/2018
ms.author: mshenhav
ms.openlocfilehash: c7fd216d50f918d96392532ccb82f80d619ce8a3
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73869658"
---
# <a name="tutorial-ask-questions-about-your-data-with-the-qa-virtual-analyst-in-the-power-bi-ios-apps"></a>Oktatóanyag: Adatokkal kapcsolatos kérdések feltevése a Q&A virtuális elemzőjével az iOS-es Power BI-alkalmazásokban

Az adatokról úgy tudhat meg a legtöbbet, ha saját szavaival megfogalmazott kérdéseket tesz fel velük kapcsolatban. Ebben az oktatóanyagban azt mutatjuk be, hogyan tehet fel kérdéseket és hogyan tekinthet meg kiemelt információkat a mintaadatokkal kapcsolatban a Q&A virtuális elemző használatával a Microsoft Power BI mobilalkalmazásban iPaden, iPhone-on és iPod Touch eszközön. 

A következőkre vonatkozik:

| ![iPhone](./media/tutorial-mobile-apps-ios-qna/iphone-logo-50-px.png) | ![iPad](./media/tutorial-mobile-apps-ios-qna/ipad-logo-50-px.png) |
|:--- |:--- |
| iPhone-ok |iPadek |

A Q&A virtuális elemző egy csevegésen alapuló BI-megoldás, amely hozzáfér az alapul szolgáló Q&A-adatokhoz a Power BI szolgáltatásban [(https://powerbi.com)](https://powerbi.com). Adatokkal kapcsolatos információkat javasol, a felületén pedig beírhatja vagy szóban felteheti saját kérdéseit is.

![Értékesítési csúcsok Q&A virtuális elemzése](./media/tutorial-mobile-apps-ios-qna/power-bi-ios-q-n-a-top-sale-intro.png)

Az oktatóanyagban a következőket végezheti el:

> [!div class="checklist"]
> * Az iOS-hez készült Power BI mobilalkalmazás telepítése
> * Minta Power BI-irányítópult és -jelentés letöltése
> * A mobilalkalmazás által javasol kiemelt elemzések megtekintése

Ha még nem regisztrált a Power BI-ra, a kezdés előtt [hozzon létre egy ingyenes próbaverziós fiókot](https://app.powerbi.com/signupredirect?pbi_source=web).

## <a name="prerequisites"></a>Előfeltételek

### <a name="install-the-power-bi-for-ios-app"></a>Az iOS-es Power BI alkalmazás telepítése
[iOS-alkalmazás letöltése](https://go.microsoft.com/fwlink/?LinkId=522062 "Az iPhone-alkalmazás letöltése") az Apple App Store-ból iPadre, iPhone-ra vagy iPod touchra.

Ezek a verziók támogatják az iOS-es Power BI alkalmazást:
- iPad iOS 10 vagy újabb verzióval.
- iPhone 5 vagy újabb iOS 10 vagy újabb rendszerrel. 
- iPod Touch iOS 10 vagy újabb rendszerrel.

### <a name="download-the-opportunity-analysis-sample"></a>A Lehetőségelemzési minta letöltése
Az oktatóanyag első lépéseként töltse le a Lehetőségelemzési mintát a Power BI szolgáltatásba.

1. Nyissa meg a Power BI szolgáltatást a böngészőben (app.powerbi.com), és jelentkezzen be.

1. A navigációs ablaktábla megnyitásához válassza a globális navigációs ikont.

    ![globális navigációs ikon](./media/tutorial-mobile-apps-ios-qna/power-bi-android-quickstart-global-nav-icon.png)

2. A navigációs ablaktáblán válassza a **Munkaterületek** > **Saját munkaterület** lehetőséget.

    ![Saját munkaterület](./media/tutorial-mobile-apps-ios-qna/power-bi-android-quickstart-my-workspace.png)

3. A bal alsó sarokban kattintson a **Lekérdezés** elemre.
   
    ![Adatok beolvasása](./media/tutorial-mobile-apps-ios-qna/power-bi-get-data.png)

3. A Lekérdezés lapon kattintson a **Minták** ikonra.
   
   ![Minták ikon](./media/tutorial-mobile-apps-ios-qna/power-bi-samples-icon.png)

4. Kattintson a **Lehetőségelemzési minta** lehetőségre.
 
    ![Lehetőségelemzési minta](./media/tutorial-mobile-apps-ios-qna/power-bi-oa.png)
 
8. Kattintson a **Csatlakozás** gombra.  
  
   ![Lehetőségelemzési minta – Csatlakozás](./media/tutorial-mobile-apps-ios-qna/opportunity-connect.png)
   
5. A Power BI importálja a mintát, majd új irányítópultot, jelentést és adatkészletet ad hozzá a Saját munkaterülethez.
   
   ![Lehetőségelemzési minta irányítópult](./media/tutorial-mobile-apps-ios-qna/power-bi-service-opportunity-sample.png)

Most már megnézheti a mintát iOS-es eszközén.

## <a name="try-featured-insights"></a>Próbálja ki a kiemelt elemzéseket
1. Nyissa meg a Power BI alkalmazást iPhone-ján vagy iPadjén, és jelentkezzen be a Power BI-fiók azon hitelesítő adataival, amelyeket a böngészőben is használt a Power BI szolgáltatáshoz.

1.  Koppintson a globális navigációs gomb ![Globális navigációs gomb](./media/tutorial-mobile-apps-ios-qna/power-bi-iphone-global-nav-button.png) > **Munkaterület** > **Saját munkaterület** lehetőségre, majd nyissa meg a Lehetőségelemzési minta irányítópultot.

2. Koppintson a Q&A virtuális elemző ikonra ![Q&A virtuális elemző ikon](./media/tutorial-mobile-apps-ios-qna/power-bi-ios-q-n-a-icon.png) az oldal alján (iPaden az oldal tetején) megjelenő műveleti menüben.

     ![Lehetőségelemzési minta irányítópult](./media/tutorial-mobile-apps-ios-qna/power-bi-ios-qna-opportunity-analysis.png)

     A Power BI Q&A virtuális elemző néhány javaslatot tesz a kezdéshez.

     ![featured insgihts (kiemelt elemzések) gomb](./media/tutorial-mobile-apps-ios-qna/power-bi-ios-qna-suggest-insights.png)
3. Koppintson a **Featured insights** (Kiemelt elemzések) gombra.

     A Q&A virtuális elemző figyelmébe ajánl néhány elemzést.
4. Görgessen jobbra, és koppintson az **Insight 2** (2-es elemzés) lehetőségre.

    ![Insight 2 (2-es elemzés) gomb](./media/tutorial-mobile-apps-ios-qna/power-bi-ios-qna-suggest-insight-2.png)

     A Q&A virtuális elemző megjeleníti a 2-es elemzést.

    ![Insight 2 (2-es elemzés)](./media/tutorial-mobile-apps-ios-qna/power-bi-ios-qna-show-insight-2.png)
5. Koppintson a diagramra fókusz nézetben történő megnyitásához.

    ![A 2-es összefüggés diagramja fókusz nézetben](./media/tutorial-mobile-apps-ios-qna/power-bi-ios-qna-open-insight-2.png)
6. A Q&A virtuális elemzőbe történő visszalépéshez koppintson a nyílra a jobb felső sarokban.

## <a name="clean-up-resources"></a>Erőforrások felszabadítása

Amikor végzett az oktatóanyaggal, nyugodtan törölheti a Lehetőségelemzési mintához tartozó irányítópultot, jelentést és adatkészletet.

1. Nyissa meg a Power BI szolgáltatást (app.powerbi.com), és jelentkezzen be.

2. A navigációs ablaktáblán válassza a **Munkaterületek** > **Saját munkaterület** lehetőséget.

3. Az **Irányítópult** lapon kattintson a **Törlés** (kuka) ikonra a Lehetőségelemzés irányítópultja mellett.

    ![A minta-irányítópult törlése](./media/tutorial-mobile-apps-ios-qna/power-bi-service-delete-opportunity-sample.png)

4. Válassza ki a **Jelentések** lapot, és ismételje meg a műveletet a Lehetőségelemzés jelentésével.

5. Válassza ki az **Adatkészletek** lapot, és ismételje meg a műveletet a Lehetőségelemzés adatkészletével.


## <a name="next-steps"></a>Következő lépések

Kipróbálta a Q&A virtuális asszisztenst az iOS-es Power BI-mobilalkalmazásban. Tájékozódjon tovább a Power BI szolgáltatás Q&A funkciójáról.
> [!div class="nextstepaction"]
> [Q&A a Power BI szolgáltatásban](../end-user-q-and-a.md)

