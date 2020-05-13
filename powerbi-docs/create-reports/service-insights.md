---
title: Adatelemzések automatikus generálása a Power BI-jal
description: Ismerje meg, hogyan kaphat elemzési információkat az adatkészletekről és az irányítópult-fájlokról.
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: et_MLSL2sA8
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/06/2019
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 4178d9cc5ce6f8e671c0d996bb64ee9a1389acdb
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83306600"
---
# <a name="generate-data-insights-automatically-with-power-bi"></a>Adatelemzések automatikus generálása a Power BI-jal
Van egy új adatkészlete, de nem tudja, hogy kezdje el feldolgozni?  Gyorsan létre kell hoznia egy irányítópultot?  Szeretne felfedezni eddig hiányzó összefüggéseket?

A Gyors elemzéseket futtatva érdekes interaktív vizualizációkat hozhat létre adataiból. Gyors elemzések egy teljes adatkészleten (gyors elemzések), illetve egy adott irányítópult-csempén is futtathatók (hatókörön belüli elemzés). Elemzésen is futtatható elemzés.

> [!NOTE]
> Az elemzési funkció nem működik a DirectQueryvel, csak a Power BI-ba feltöltött adatokkal használható.
> 

Az elemzés szolgáltatás a Microsoft Research-csel együttműködésben fejlesztett, egyre növekvő számú [haladó szintű elemzési algoritmusra épül](../consumer/end-user-insight-types.md). A Microsoft Research egyre több ember számára teszi lehetővé adatai újszerű és intuitív módszerekkel történő elemzését.

## <a name="run-quick-insights-on-a-dataset"></a>Gyors elemzések futtatása adatkészleteken
Tekintse meg, hogyan futtat Amanda gyors elemzést egy adatkészleten, hogyan nyit meg egy elemzést Fókusz módban, hogyan tűzi ki egy ilyen elemzést irányítópultjára csempeként, és hogyan kér gyors elemzést egy irányítópult-csempéhez kapcsolódóan.

<iframe width="560" height="315" src="https://www.youtube.com/embed/et_MLSL2sA8" frameborder="0" allowfullscreen></iframe>


Most Ön következik. Fedezze fel az elemzések szolgáltatást a [Szállítói minőségelemzési mintát](sample-supplier-quality.md) használva.

1. Az **Adatkészletek** lapon válassza a **További beállítások** (...), majd a **Gyorselemzések lekérése** lehetőséget.
   
    ![Adatkészletek lap](media/service-insights/power-bi-ellipses.png)
   
    ![Három pont menü](media/service-insights/power-bi-tab.png)
2. A Power BI [különböző algoritmusokat](../consumer/end-user-insight-types.md) használ az adatkészlet trendjeinek kimutatásához.
   
    ![Elemzések keresése párbeszédpanel](media/service-insights/pbi_autoinsightssearching.png)
3. Az elemzés másodpercek alatt elkészül.  A vizualizációk megjelenítéséhez kattintson az **Elemzések megtekintése** lehetőségre.
   
    ![Sikert jelző üzenet](media/service-insights/pbi_autoinsightsuccess.png)
   
    > [!NOTE]
    > Egyes adathalmazok nem tudnak elemzéseket létrehozni, mert az adatok nem bírnak statisztikai jelentőséggel.  Ha ezzel kapcsolatban további információra van szüksége, tekintse át az [Adatok elemzésekhez történő optimalizálását](service-insights-optimize.md) bemutató cikket.
    > 
    
4. A vizualizációk a **Gyors elemzések** speciális vásznán jelennek meg, akár 32 különálló elemzéskártyán. Minden kártyán egy-egy diagram vagy ábra és egy rövid leírás látható.
   
    ![Gyors elemzések vászon](media/service-insights/power-bi-insights.png)

## <a name="interact-with-the-insight-cards"></a>Az elemzéseket megjelenítő kártyák interaktív használata

1. A vizualizáció irányítópultra történő felvételéhez vigye a kurzort az egyik kártya fölé, és válassza a kitűzés ikont.

2. Mutasson egy kártyára, és válassza a **További beállítások** (...) lehetőséget, majd az **Elemzések megtekintése** elemet. 

    Az elemzési képernyő fókusz módban nyílik meg.
   
    ![Elemzés Fókusz módban](media/service-insights/power-bi-insight-focus.png)
3. Fókusz módban a következő műveleteket végrehajtására van lehetőség:
   
   * Vizualizációk szűrése. Ha a **Szűrők** panel még nincs megnyitva, bontsa ki azt az ablak jobb oldalán található nyílra kattintva.

       ![Az elemzés kibontott Szűrők menüje](media/service-insights/power-bi-insights-filter-new.png)
   * Az elemzéskártyát a **Vizualizáció rögzítése** lehetőséget választva tűzheti ki egy irányítópultra.
   * Futtassa az elemzést a kártyán. Ezt gyakran *hatókörön belüli elemzésnek* is nevezik. Válassza a jobb felső sarokban látható villanykörte ikont ![Elemzések lekérése ikon](media/service-insights/power-bi-bulb-icon.png) vagy az **Elemzések lekérése** lehetőséget.
     
       ![Elemzések lekérése ikon](media/service-insights/pbi-autoinsights-tile.png)
     
     A bal oldalon megjelennek az elemzések, a jobb oldalon pedig új kártyák láthatók, melyeket kizárólag az adott elemzésben szereplő adatok alapján készített a rendszer.
     
       ![Egymáson lévő elemzések](media/service-insights/power-bi-insights-on-insights-new.png)
4. Az eredeti elemzéseket tartalmazó vászonra a bal felső sarokban látható **Kilépés a fókusz módból** lehetőséget választva léphet vissza.

## <a name="run-insights-on-a-dashboard-tile"></a>Irányítópult csempére vonatkozó elemzések futtatása
Teljes adatkészletek összefüggéseinek feltárása helyett egyetlen irányítópult-csempe létrehozásához használt adatok hatókörön belüli elemzésével is szűkíthető az elemzés. 

1. Nyisson meg egy irányítópultot.
2. Vigye az egérmutatót egy csempe fölé. Válassza a **További beállítások** (...) lehetőséget, majd az **Elemzések megtekintése** elemet. A csempe [Fókusz módban](../consumer/end-user-focus.md) nyílik meg, és a jobb oldalán jelennek meg az elemzéskártyák.    
   
    ![Fókusz mód](media/service-insights/pbi-insights-tile.png)    
3. Felkeltette valamelyik elemzés az érdeklődését? Az adott elemzéskártyát kiválasztva az adatok mélyebb szintjére is leáshat. A kiválasztott elemzés a bal oldalon fog megjelenni, az új, kizárólag az adott elemzés adatain alapuló új elemzéskártyák pedig a jobb oldalon.    
4. Az adatok mélyebb szintjeinek feltárását tovább folytatva az érdekes elemzéseket a jobb felső sarokban látható **Vizualizáció rögzítése** lehetőséget választva tűzheti ki az irányítópultra.

## <a name="next-steps"></a>További lépések
- Ha Ön az adatkészlet tulajdonosa, [optimalizálhatja azt gyors elemzések készítéséhez](service-insights-optimize.md).
- További tudnivalók a [Gyors elemzések típusaival kapcsolatban](../consumer/end-user-insight-types.md).

Több kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/).
