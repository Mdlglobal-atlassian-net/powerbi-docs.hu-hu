---
title: Elemzések futtatása és megtekintése irányítópult-csempéken
description: Power BI-végfelhasználóként érdemes elsajátítania az irányítópult-csempék elemzési eredményeinek megállapítását.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: et_MLSL2sA8
ms.custom: seodec18
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 8bae8475ee4bbe91ea27f3a9e30a3323a92a8250
ms.sourcegitcommit: cd85d88fba0d9cc3c7a4dc03d2f35d2bd096759b
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/12/2018
ms.locfileid: "53280259"
---
# <a name="view-data-insights-on-dashboard-tiles-with-power-bi"></a>Adatelemzési eredmények megtekintése irányítópult-csempéken a Power BI-jal
Az irányítópulton található vizualizációs csempék mindegyike nagyszerű lehetőséget biztosít az adatfeltárással való ismerkedéshez. Ha rákattint egy csempére, megnyílik egy jelentés, amelyben szűrheti és rendezheti a jelentés alapjául szolgáló adathalmazt, és részletes elemzést végezhet rajta. Elemzések futtatásakor pedig a Power BI elvégzi Ön helyett az adatok felderítését.

A Gyors elemzéseket futtatva érdekes interaktív vizualizációkat hozhat létre adataiból. Gyors elemzéseket futtathat az irányítópult adott csempéin, és még az elemzéseken is futtathat elemzést!

Az elemzés szolgáltatás a Microsoft Research-csel együttműködésben fejlesztett, egyre növekvő számú [haladó szintű elemzési algoritmusra épül](end-user-insight-types.md). A Microsoft Research egyre több ember számára teszi lehetővé adatai újszerű és intuitív módszerekkel történő elemzését.

## <a name="run-insights-on-a-dashboard-tile"></a>Irányítópult csempére vonatkozó elemzések futtatása
Ha az irányítópult egyik csempéjén futtat elemzéseket, a Power BI megkeresi az adott csempe létrehozásához használt adatokat. 

1. [Nyisson meg egy irányítópultot](end-user-dashboards.md).
2. Vigye az egérmutatót egy csempe fölé. Válassza a három pontot (…), majd az **Elemzések megtekintése** lehetőséget. 

    ![három pont menü mód](./media/end-user-insights/power-bi-hover.png)


3. A csempe [Fókusz módban](end-user-focus.md) nyílik meg, és a jobb oldalán jelennek meg az elemzéskártyák.    
   
    ![Fókusz mód](./media/end-user-insights/pbi-insights-tile.png)    
4. Felkeltette valamelyik elemzés az érdeklődését? Az adott elemzéskártyát kiválasztva az adatok mélyebb szintjére is leáshat. A kiválasztott elemzés a bal oldalon fog megjelenni, az új, kizárólag az adott elemzés adatain alapuló új elemzéskártyák pedig a jobb oldalon.    

 ## <a name="interact-with-the-insight-cards"></a>Az elemzéseket megjelenítő kártyák interaktív használata
Egy elemzés megnyitása után folytathatja a felderítést.

   * A vizualizációt a vásznon szűrheti.  A szűrők megjelenítéshez a jobb felső sarokban látható nyilat választva nyithatja meg a Szűrők panelt.

     ![elemzés és a Szűrők menü kibontva](./media/end-user-insights/power-bi-insights-on-insights.png)
   
   * Elemzést magára az elemzés kártyájára vonatkozóan is futtathat. Ezt gyakran **kapcsolódód elemzésnek** is nevezik. Válassza a jobb felső sarokban látható villanykörte ikont ![Elemzések lekérése ikon](./media/end-user-insights/power-bi-bulb-icon.png) vagy az **Elemzések lekérése** lehetőséget.
     
     ![az Elemzések lekérése ikon a menüsávon](./media/end-user-insights/power-bi-autoinsights-tile.png)
     
     A bal oldalon megjelennek az elemzések, a jobb oldalon pedig új kártyák láthatók, melyeket kizárólag az adott elemzésben szereplő adatok alapján készített a rendszer.
     
     ![egymáson lévő elemzések](./media/end-user-insights/power-bi-insights-on-insights-new.png)

Az eredeti elemzéseket tartalmazó vászonra a bal felső sarokban látható **Kilépés a fókusz módból** lehetőséget választva léphet vissza.

## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás
- Az **Elemzések megtekintése** nem működik a DirectQueryvel, csak a Power BI-ba feltöltött adatokkal használható.
- Az **Elemzések megtekintése** az irányítópult nem minden csempetípusával használható. Például egyéni vizualizációkhoz nem érhető el.<!--[custom visuals](end-user-custom-visuals.md)-->


## <a name="next-steps"></a>Következő lépések
További tudnivalók a [Gyors elemzések típusaival kapcsolatban](end-user-insight-types.md)

