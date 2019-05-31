---
title: Vonaldiagramok Power BI-ban
description: Vonaldiagramok Power BI-ban
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 0654dccf55b1e13f26d8ecaabee0349f0e56afc6
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65535790"
---
# <a name="line-charts-in-power-bi"></a>Vonaldiagramok Power BI-ban
Egy vonaldiagramot egy sorozat pont által képviselt és csatlakoztatott egyenes vonalak adatpont. Előfordulhat, hogy egy vonaldiagramot egy vagy több sort. Vonaldiagramok az X és Y-tengely rendelkezik. 

![egyszerű vonaldiagram](media/power-bi-line-charts/power-bi-line.png)

## <a name="create-a-line-chart"></a>Hozzon létre egy vonaldiagramot
Ezen utasítások használata az értékesítési és Marketing minta alkalmazást hozhat létre egy vonaldiagramot, amely az Ez évi értékesítést jeleníti meg kategória szerint. Hogy követni tudja, lekérheti a mintaalkalmazás appsource.com.

1. Kezdje a műveletet egy üres jelentésoldalon. Ha a Power BI szolgáltatást használja, mindenképpen a [Szerkesztési nézetében](../service-interact-with-a-report-in-editing-view.md) nyissa meg a jelentést.

2. A mezők panelen válassza ki a **SalesFact** \> **egységek összesen**, és válassza ki **dátum** > **hónap**.  A Power BI létrehoz egy oszlopdiagramot a jelentésvásznon.

    ![Válassza ki a mezők panelen](media/power-bi-line-charts/power-bi-step1.png)

4. Vonaldiagram átalakítása vonal diagram sablon kiválasztásával a Vizualizációk panelen. 

    ![Vonaldiagram átalakítása](media/power-bi-line-charts/power-bi-convert-to-line.png)
   

4. Szűrheti a vonaldiagram az adatok megjelenítése a 2012-2014 évben. Ha a szűrők panel nincs kibontva, bontsa ki azt. A mezők panelen válassza ki a **dátum** \> **év** , majd húzza a szűrők panel. Dobja el, a címsor alatt **szűrők a vizualizációban**. 
     
    ![sor mellett a mezők panelen](media/power-bi-line-charts/power-bi-year-filter.png)

    Változás **speciális szűrők** való **alapszintű szűrők** válassza **2012**, **2013** és **2014**.

    ![Szűrő év](media/power-bi-line-charts/power-bi-filter-year.png)

6. Ha szeretné, [módosíthatja a diagram szövegének méretét és színét](power-bi-visualization-customize-title-background-and-legend.md). 

    ![Betűméret növelése és az Y axisfont módosítása](media/power-bi-line-charts/power-bi-line-3years.png)

## <a name="add-additional-lines-to-the-chart"></a>További sorok hozzáadása a diagram
Vonaldiagramok számos különböző sorokba is rendelkezhet. És bizonyos esetekben az értékek a sorok, hogy nem jelennek meg problémamentesen eltérő lehet. Tekintsük át az aktuális további sorokat diagram, és megismerheti, hogyan formázhatja tábláról a diagramra, amikor képviseli a sorok értékei nagyon eltérő hozzáadása. 

### <a name="add-additional-lines"></a>További sorok hozzáadása
Helyett minden régió esetében az összes egység megnézzük, a diagram egy sorba, hozzunk ossza ki az összes egység, régió szerint. Adja hozzá a további sorokat húzásával **földrajzi** > **régió** , a jelmagyarázat jól.

   ![Egy sor minden olyan régió esetében](media/power-bi-line-charts/power-bi-line-regions.png)


### <a name="use-two-y-axes"></a>Két Y tengely használata
Mi történik, ha szeretné teljes értékesítési és ugyanezen a diagramon az összes egység? Értékesítési szám, így sokkal nagyobb egység számok, így a vonaldiagram használhatatlan. Valójában a összes egység piros vonal jelenik meg nulla.

   ![magas elágazó értékek](media/power-bi-line-charts/power-bi-diverging.png)

Magas széttartó értékeket egy diagramon megjeleníthető egy kombinált diagramot használja. Olvassa el az összes talál a kombinált diagramok további [kombinált diagramok a Power bi-ban](power-bi-visualization-combo-chart.md). Az alábbi példában is megjelenítjük értékesítési és összes egység együtt egy diagramon egy második Y tengely hozzáadásával. 

   ![magas elágazó értékek](media/power-bi-line-charts/power-bi-dual-axes.png)

## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás
* Egy vonaldiagram két Y tengely nem rendelkezhet.  Használja helyette a kombinált diagram kell.
* A fenti példákban a diagramok betűméret növelése, módosítsa a betűk színe, adja hozzá a Tengelycímek, center a diagram címének és a jelmagyarázat, indítsa el mindkét tengelyt, nulla és egyéb lett formázva. A formázás ablaktáblát (festőhenger ikon) a végtelen lehetőségek, hogy a diagramok tekintse meg a kívánt módon való rendelkezik. A legjobban megérteni, hogy nyissa meg a formázás ablaktáblát, és Fedezze fel.

## <a name="next-steps"></a>Következő lépések

[Vizualizációtípusok a Power BI-ban](power-bi-visualization-types-for-reports-and-q-and-a.md)


