---
title: Kártyavizualizációk (más néven nagy méretű numerikus csempék)
description: Kártyavizualizáció létrehozása a Power BI-ban
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 2bd35e5c2bc92ee660a9524754a3daef95e6e83d
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54275801"
---
# <a name="card-visualizations"></a>Kártyavizualizációk
Néha csupán egyetlen szám a legfontosabb, amit nyomon szeretne követni a Power BI-irányítópulton vagy -jelentésben, például az összesített értékesítés, az egy évre vetített piaci részesedés, vagy a lehetőségek száma összesen. Az ilyen típusú vizualizációkat *Kártyáknak* nevezzük. Csakúgy, mint szinte minden natív Power BI-vizualizáció, a Kártyák is a jelentésszerkesztővel vagy a Q&A-val hozhatók létre.

![kártyavizualizáció](media/power-bi-visualization-card/pbi_opptuntiescard.png)

## <a name="create-a-card-using-the-report-editor"></a>Kártyák létrehozása a jelentésszerkesztővel
Ez az útmutatás a Kiskereskedelmi elemzési mintát használja. Annak érdekében, hogy követni tudja a lépéseket, [töltse le a mintát](../sample-datasets.md), mely a Power BI szolgáltatásban (az app.powerbi.com webhelyen) vagy a Power BI Desktopban használható.   

1. Kezdjen egy üres jelentésoldalon, és válassza a **Store** \> **Open store count** (Üzlet > Nyitva lévő üzletek száma) mezőt. Ha a Power BI szolgáltatást használja, a [Szerkesztési nézetében](../service-interact-with-a-report-in-editing-view.md) kell megnyitnia a jelentést.

    A Power BI létrehoz egy oszlopdiagramot ezzel az egy számmal.

   ![](media/power-bi-visualization-card/pbi_rptnumbertilechart.png)
2. A Megjelenítések ablaktáblán kattintson a Kártya ikonra.

   ![](media/power-bi-visualization-card/power-bi-templates.png)
6. A vizualizáció az irányítópulton való rögzítéséhez vigye a kurzort a kártya fölé, és válassza a rögzítés ikonját ![](media/power-bi-visualization-card/pbi_pintile.png).

   ![](media/power-bi-visualization-card/power-bi-pin-icon.png)
7. A csempét egy meglévő vagy egy új irányítópultra is rögzítheti.

   * Meglévő irányítópult: válassza ki az irányítópult nevét a legördülő listából.
   * Új irányítópult: írja be az új irányítópult nevét.
8. Válassza a **Rögzítés** lehetőséget.

   Megjelenik egy üzenet (a jobb felső sarok közelében), amely értesíti, hogy sikeresen hozzáadta a vizualizációt az irányítópultjához csempeként.

   ![](media/power-bi-visualization-card/power-bi-success2.png)
9. Válassza az **Ugrás az irányítópultra** lehetőséget. Itt [szerkesztheti és áthelyezheti](../service-dashboard-edit-tile.md) a rögzített vizualizációt.


## <a name="create-a-card-from-the-qa-question-box"></a>Kártya létrehozása a Q&A kérdésmezőben
Kártyák legkönnyebben a Q&A kérdésmezőben hozhatók létre. A Q&A kérdésmező a Power BI szolgáltatásban az irányítópultokon és jelentésekben vagy a Desktop jelentés nézetében érhető el. A következő lépések azt írják le, hogyan hozható létre egy Kártya a Power BI szolgáltatás irányítópultjain. Ha a Power BI Desktopban szeretne létrehozni egy kártyát a Q&A-val, a Q&A a Desktophoz készült előzetes verziójának jelentései esetében [ezt az útmutatást kövesse](https://powerbi.microsoft.com/en-us/blog/power-bi-desktop-december-feature-summary/#QandA).

1. Hozzon létre egy [irányítópultot](../service-dashboards.md), és [kérje le az adatokat](../service-get-data.md). Ebben a példában a [Lehetőségelemzési mintát](../sample-opportunity-analysis.md) használjuk.

1. Az irányítópult tetején angolul kezdje beírni a kérdés mezőbe, hogy mire is kíváncsi az adatokkal kapcsolatban. 

   ![](media/power-bi-visualization-card/power-bi-q-and-a-box.png)

> [!TIP]
> A Power BI szolgáltatás jelentéseiben, a szerkesztési nézetben válassza a **Kérdés feltevése** lehetőséget a felső menüsorban. A Power BI Desktop jelentéseiben keressen egy üres területet a jelentésben, majd kattintson rá duplán a kérdésmező megnyitásához.

3. Például írja be a „number of opportunities” (lehetőségek száma) kifejezést a kérdés mezőbe.

   ![](media/power-bi-visualization-card/power-bi-q-and-a.png)

   A kérdésmező javaslatokkal és újrafogalmazásokkal segíti, és végül megjeleníti az összesített számot.  
4. A kártyát a jobb felső sarokban lévő rögzítési ikonnal ![](media/power-bi-visualization-card/pbi_pintile.png) adhatja hozzá egy irányítópulthoz.

   ![](media/power-bi-visualization-card/power-bi-pin.png)
5. A kártyát egy meglévő vagy egy új irányítópulton is rögzítheti csempeként.

   * Meglévő irányítópult: válassza ki az irányítópult nevét a legördülő listából. Csak az aktuális munkaterületeken lévő irányítópultok közül választhat.
   * Új irányítópult: írja be az új irányítópult nevét, és az létrejön a munkaterületen.
6. Válassza a **Rögzítés** lehetőséget.

   A jobb felső sarokban megjelenik a sikert jelző üzenet, amely tájékoztatja arról, hogy a vizualizáció csempeként hozzá lett adva az irányítópulthoz.  

   ![](media/power-bi-visualization-card/power-bi-success2.png)
7. Az új csempe megtekintéséhez kattintson az **Ugrás az irányítópultra** lehetőségre. Itt [többek között átnevezheti, átméretezheti és áthelyezheti a csempét az irányítópulton, és hivatkozást adhat hozzá](../service-dashboard-edit-tile.md).

   ![](media/power-bi-visualization-card/power-bi-pinned.png)

## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás
- Ha a kereső mező nem látható, forduljon a rendszerszintű vagy a bérlői rendszergazdához.    
- Ha a Power BI Desktopot használja, és nem jelenik meg a Q&A, amikor duplán kattint egy üres területre egy jelentésben, lehetséges, hogy engedélyeznie kell azt.  Válassza a **Fájl > Lehetőségek és beállítások > Beállítások > Előzetes verziójú funkciók > Q&A** lehetőséget, majd indítsa újra a Power BI Desktopot.

## <a name="format-a-card"></a>Kártya formázása
A címkék, szöveg, színét és egyebek módosításához több lehetőség áll rendelkezésre. A tanulás legjobb módja, ha létrehoz egy kártyát, és azután részletesebben is megismerkedik a Formázás ablaktábla lehetőségeivel. Bemutatunk néhányat az elérhető formázási lehetőségek közül. 

1. Kezdő lépésként nyissa meg a Formázás ablaktáblát a festőhenger ikon kiválasztásával. 

    ![kártya, amelyen a festőhenger kiemelve látható](media/power-bi-visualization-card/power-bi-format-card.png)
2. Bontsa ki az **Adatfelirat** elemet, majd módosítsa a színt, a méretet és a betűtípust. Ha több ezer üzlettel rendelkezik, akkor a **Megjelenítési egységek** használatával ezresével jelenítheti meg az üzleteket, és beállíthatja a tizedesjegyeket is. Például 125,8 e a 125 832,00 helyett.

3.  Bontsa ki a **Kategóriacímke** elemet, majd módosítsa a színt és a méretet.

    ![a választott szín a sötétkék](media/power-bi-visualization-card/power-bi-card-format.png)

4. Bontsa ki a **Háttér** elemet, és a csúszkát tolja „On” (Be) állásba.  Mostantól módosíthatja a háttérszínt és az átlátszóságot.

    ![csúszka ON (BE) állásban](media/power-bi-visualization-card/power-bi-format-color.png)

5. Folytassa is a formázási beállítások felfedezését, amíg a kártya pontosan olyan nem lesz, amilyennek kívánja. 

    ![A kártya az összes formázási művelet elvégzése után](media/power-bi-visualization-card/power-bi-formatted.png)

## <a name="next-steps"></a>Következő lépések
[Kombinált diagramok a Power BI-ban](power-bi-visualization-combo-chart.md)

[Vizualizációtípusok a Power BI-ban](power-bi-visualization-types-for-reports-and-q-and-a.md)
