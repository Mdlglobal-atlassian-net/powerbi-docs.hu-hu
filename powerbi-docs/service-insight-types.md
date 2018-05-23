---
title: A Power BI által támogatott elemzések típusai
description: Gyors elemzések és elemzések megtekintése a Power BI-jal.
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 03/02/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 44b59019f1955258716e23fb2dd55182134cc6a2
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/17/2018
---
# <a name="types-of-insights-supported-by-power-bi"></a>A Power BI által támogatott elemzések típusai
## <a name="how-does-insights-work"></a>Az elemzések működése
A Power BI kifinomult algoritmusok alkalmazásával részhalmazokat keres az adatkészletben potenciálisan érdekes összefüggések feltárásához. A Power BI adott idő alatt annyi adatot vizsgál meg az adatkészletből, amennyit csak tud.

Az elemzések egy adathalmazon vagy egy irányítópult-csempén futtathatók.   

## <a name="what-types-of-insights-can-we-find"></a>Milyen összefüggések tárhatók fel az elemzésekkel?
A rendszer többek között az alábbi algoritmusokat használja:

## <a name="category-outliers-topbottom"></a>Kiugró (alsó vagy felső) értékek a kategóriában
Az adatmodell valamely kategóriája vonatkozásában kiemeli azokat az eseteket, amelyeknél adott dimenzióban az egyik vagy másik elem értéke sokkal nagyobb vagy alacsonyabb, mint a többié.  

![Kiugró értékek a kategóriákban – példa](media/service-insight-types/pbi_auto_insight_types_category_outliers.png)

## <a name="change-points-in-a-time-series"></a>Időbeli adatsorok változási pontjai
Időbeli adatsoroknál kiemeli, hogy mikor következett be szignifikáns változás a trendekben.

![Időbeli adatsorok változási pontjai – példa](media/service-insight-types/pbi_auto_insight_types_changepoint.png)

## <a name="correlation"></a>Korreláció
Észleli, hogy az adatkészletet egy adott dimenzió mentén ábrázolva milyen eseteken korrelálnak egymással a különböző kategóriák értékei.

![Korrelációs példa](media/service-insight-types/pbi_auto_insight_types_correlation.png)

## <a name="low-variance"></a>Alacsony variancia
Észleli azokat az eseteket, melyeknél az adatpontok közel vannak az átlaghoz.

![Alacsony variancia példa](media/service-insight-types/power-bi-low-variance.png)

## <a name="majority-major-factors"></a>Többség (fő tényezők)
Megkeresi azokat az eseteket, amelyekben az összérték többségi aránya egy másik dimenzió mentén vizsgálva egyetlen tényezőnek tudható be.  

![Fő tényezők példa](media/service-insight-types/pbi_auto_insight_types_majority.png)

## <a name="overall-trends-in-time-series"></a>Időbeli adatsorok általános trendjei
Észleli az időrendben elérhető adatok növekvő és csökkenő trendjeit.

![Időbeli adatsorok általános trendjei – példa](media/service-insight-types/pbi_auto_insight_types_trend.png)

## <a name="seasonality-in-time-series"></a>Időbeli adatsorok szezonális változásai
Azt vizsgálja, hogy felfedezhetőek-e heti, havi vagy éves gyakorisággal ismétlődő minták az időbeli adatsorokban.

![Szezonalitás példa](media/service-insight-types/pbi_auto_insight_types_seasonality_new.png)

## <a name="steady-share"></a>Állandó részesedés
Kiemeli azokat az eseteket, amelyekben szülő-gyermek típusú korreláció fedezhető fel egy gyermek érték részesedése és egy folyamatos változó mentén vizsgált teljes szülő érték között.

![Állandó részesedés példa](media/service-insight-types/pbi_auto_insight_types_steadyshare.png)

## <a name="time-series-outliers"></a>Kiugró értékek egy időbeli adatsorban
Időrendben elérhető adatok esetén észleli, hogy vannak-e olyan dátumok vagy időpontok, melyeknél az érték szignifikánsan eltér a többi dátumhoz/időponthoz tartozó értéktől.

![Kiugró értékek egy időbeli adatsorban példa](media/service-insight-types/pbi_auto_insight_types_time_series_outliers.png)

## <a name="next-steps"></a>Következő lépések
[Power BI-elemzések](service-insights.md)

Ha Ön az adathalmaz tulajdonosa, [optimalizálhatja azt elemzések elvégzéséhez](service-insights-optimize.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

