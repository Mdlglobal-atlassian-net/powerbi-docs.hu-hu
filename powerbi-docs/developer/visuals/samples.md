---
title: Minta Power BI-vizualizációk
description: 'Ez a cikk minta Power BI-vizualizációkat mutat be, köztük a következőket: szeletelők, 20-nál is több különböző típusú diagram, WebGL, valamint R-vizualizációk és -szkriptek.'
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/17/2019
ms.openlocfilehash: 5e2ad0fa43a186be76a58f1ab3bb4bf054a677a5
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83132949"
---
# <a name="samples-of-power-bi-visuals"></a>Minták a Power BI-vizualizációkhoz

A Power BI-vizualizációkat a GitHubról töltheti le, illetve azon keresztül használhatja és módosíthatja őket. A minták azt mutatják be, hogy miként kezelheti a gyakran előforduló helyzeteket a Power BI használatával történő fejlesztés során.

## <a name="slicers"></a>Szeletelők

A szeletelőkkel az adatok a jelentés más vizualizációiban szereplő részükre szűkíthetők. A szeletelők használata az egyik lehetséges módja az adatok a Power BI-ban történő szűrésének.

| <img src="media/samples/chiclet-slicer.png" width="200">  | <img src="media/samples/timeline-slicer.png" width="200"> | <img src="media/samples/sample-slicer.png" width="200">|
| ------------- | ------------- | -------------|
| [Gombsorszeletelő](https://github.com/Microsoft/powerbi-visuals-chicletslicer/)  </br>Képes és/vagy szöveges gombok megjelenítése, amelyek vásznon belüli szűrőként használhatók más vizualizációkhoz | [Idővonal-szeletelő](https://github.com/Microsoft/powerbi-visuals-timeline/) </br>Dátum szerint szűrő grafikus dátumtartomány-választó | [Szeletelőminta](https://github.com/Microsoft/powerbi-visuals-sampleslicer/) </br>Az Advanced Filtering API használatát szemlélteti

## <a name="charts"></a>Diagramok

Ihletet meríthet az oszlopdiagramokat, tortadiagramokat, szófelhőket és egyebeket tartalmazó galériánkból.

| <img src="media/samples/aster-plot.png" width="200">  | <img src="media/samples/bullet-chart.png" width="200"> | <img src="media/samples/Chord.png" width="200">|
| ------------- | ------------- | -------------|
| [Őszirózsa diagram](https://github.com/Microsoft/powerbi-visuals-asterplot/)  </br>A hagyományos fánkdiagram variációja, amely egy második érték használatával vezérli a szögtartományokat | [Skáladiagram](https://github.com/Microsoft/powerbi-visuals-bulletchart/) </br>Sávdiagram további vizuális elemekkel, amelyek a célok nyomon követéséhez hasznos kontextust biztosítanak | [Húr](https://github.com/Microsoft/powerbi-visuals-chord/) </br>Egy grafikus módszer, amely egy mátrixban jeleníti meg az adatok közötti kapcsolatokat
| <img src="media/samples/dot-plot.png" width="200"> | <img src="media/samples/dual-kpi.png" width="200">| <img src="media/samples/enhanced-scatter.png" width="200"> 
| [Pöttydiagram](https://github.com/Microsoft/powerbi-visuals-dotplot/) </br>Szemléletes módon jeleníti meg a gyakoriságok eloszlását | [Kettős KPI](https://github.com/Microsoft/powerbi-visuals-dualkpi/) </br>Hatékonyan megjelenít két mértéket az időben, együttes idővonalon mutatva a trendeket | [Bővített pont](https://github.com/Microsoft/powerbi-visuals-enhancedscatter/) </br>A már meglévő pontdiagram fejlesztése
| <img src="media/samples/forcegraph.png" width="200">| <img src="media/samples/gantt.png" width="200">| <img src="media/samples/table-heatmap.png" width="200">
| [Erőegyensúlyos gráf](https://github.com/Microsoft/powerbi-visuals-forcegraph/) </br>Ívelt vonalas, erőegyensúlyos elrendezésű diagram, amely az entitások közötti kapcsolatok megjelenítésekor hasznos | [Gantt](https://github.com/Microsoft/powerbi-visuals-gantt/) </br>Olyan sávdiagram, amely egy projekt idővonalát vagy ütemezését jeleníti meg erőforrásokkal együtt | [Hőtérképtábla](https://github.com/Microsoft/powerbi-visuals-heatmap/) </br>Adatok egyszerű és intuitív összehasonlítása egy táblázatban, színek használatával
| <img src="media/samples/histogram-chart.png" width="200"> | <img src="media/samples/linedot-chart.png" width="200"> | <img src="media/samples/mekko-chart.png" width="200"> 
| [Hisztogram](https://github.com/Microsoft/powerbi-visuals-histogram/) </br>Az adatok eloszlását jeleníti meg folyamatosan vagy egy adott időtartamra vonatkozóan | [Vonalpontos diagram](https://github.com/Microsoft/powerbi-visuals-linedotchart/) </br>Egy animált pontokkal rendelkező animált vonaldiagram, amely adatok segítségével ragadja meg a közönség figyelmét | [Mekko diagram](https://github.com/Microsoft/powerbi-visuals-mekkochart/) </br>Egy 100%-ig halmozott oszlopdiagram és egy 100%-ig halmozott sávdiagram egyetlen nézetben
| <img src="media/samples/multikpi.png" width="200"> | <img src="media/samples/powerkpi.png" width="200"> | <img src="media/samples/powerkpi-matrix.png" width="200"> 
| [Több KPI](https://github.com/microsoft/PowerBI-visuals-MultiKPI/) </br> Egy hatékony, több KPI-s vizualizáció, amelyben egy központi KPI mellett több, alátámasztó adatok alapján létrehozott értékgörbe található | [Nagy teljesítményű KPI](https://github.com/microsoft/PowerBI-visuals-PowerKPI/) </br>Egy nagy teljesítményű KPI-mutató többvonalas diagrammal és a jelenlegi dátumot, az értéket és a varianciákat megjelenítő címkékkel | [Power KPI Matrix](https://github.com/microsoft/PowerBI-visuals-PowerKPIMatrix/) </br>Egy kompakt, könnyedén értelmezhető listában teszi lehetővé a kiegyensúlyozott mutatószámok, KPI-k és korlátlan számú metrika monitorozását
| <img src="media/samples/pulse-chart.png" width="200">| <img src="media/samples/radar-chart.png" width="200"> | <img src="media/samples/sankey-chart.png" width="200"> 
| [Pulzusdiagram](https://github.com/Microsoft/powerbi-visuals-pulsechart/) </br>Egy olyan kulcsfontosságú eseményekkel kiegészített vonaldiagram, amely ideális az adatok segítségével való történetmeséléshez| [Sugárdiagram](https://github.com/Microsoft/powerbi-visuals-radarchart/) </br>Több mértéket jelenít meg egyszerre egy kategorikus tengelyen, amely a különféle attribútumok összehasonlításához hasznos | [Sankey diagram](https://github.com/Microsoft/powerbi-visuals-sankey/) </br>Folyamatábra, amelyben a sorozat szélessége arányos a folyamat mennyiségével
| <img src="media/samples/stream-graph.png" width="200"> | <img src="media/samples/sunburst.png" width="200">| <img src="media/samples/tornado.png" width="200">
| [Adatfolyam-grafikon](https://github.com/Microsoft/powerbi-visuals-streamgraph/) </br>Egy olyan egyenletes interpolálású halmozott területdiagram, amelyet gyakran használnak értékek időbeli alakulásának megjelenítésére | [Többszintű gyűrű diagram](https://github.com/Microsoft/powerbi-visuals-sunburst/) </br>Egy többszintű fánkdiagram a hierarchikus adatok hatékony megjelenítéséhez| [Tornádó diagram](https://github.com/Microsoft/powerbi-visuals-tornado/) </br>Összehasonlítja két csoport változóinak relatív fontosságát
 | <img src="media/samples/word-cloud.png" width="200">
 | [Szófelhő](https://github.com/Microsoft/powerbi-visuals-wordcloud/) </br>Érdekes vizualizáció létrehozása az adatokban gyakran előforduló szövegek alapján

## <a name="webgl"></a>WebGL

A WebGL lehetővé teszi, hogy a webes tartalom OpenGL ES 2.0-alapú API-t használjon a HTML-vásznon történő 2D és 3D rendereléshez.

| <img src="media/samples/globe-map.png" width="250">|
| ------------- |
| [Földgömb térkép](https://github.com/Microsoft/powerbi-visuals-globemap/) </br>Helyek ábrázolása egy interaktív 3D térképen

## <a name="r-visuals"></a>R vizualizációk

Ezek a minták azt mutatják meg, miként lehet kihasználni az R-vizualizációk és R-szkriptek elemzési és vizuális sokoldalúságát.

| <img src="media/samples/association-rules.png" width="200">| <img src="media/samples/clustering.png" width="200">| <img src="media/samples/clustering-with-outliers.png" width="200">|
|------------- |------------- |------------- |------------- |
| [Társítási szabályok](https://github.com/Microsoft/powerbi-visuals-assorules/) </br>A látszólag nem kapcsolódó adatok közti kapcsolatok felfedése ha-akkor utasítások használatával | [Fürtözés](https://github.com/Microsoft/powerbi-visuals-clustering-kmeans/) </br>K-közép algoritmusok segítségével azonosítja az adathalmazban fellelhető hasonlósági csoportokat | [Fürtözés kiugró adatokkal](https://github.com/microsoft/PowerBI-visuals-dbscan/) </br>Segít megtalálni az adathalmaz kiugró értékeit és hasonlósági csoportjait
| <img src="media/samples/correlation-plot.png" width="200"> | <img src="media/samples/decision-tree-chart.png" width="200"> | <img src="media/samples/forecasting-tbats.png" width="200"> 
| [Korrelációs rajz](https://github.com/Microsoft/powerbi-visuals-corrplot/) </br>Kiemeli az adattábla legerősebb korrelációt mutató változóit | [Döntésifa-diagram](https://github.com/Microsoft/powerbi-visuals-decision-tree/) </br>Egy sematikus, fa alakú diagram, amelyen rekurzív particionálással állapítható meg a statisztikai valószínűség | [Előrejelzési TBATS](https://github.com/Microsoft/powerbi-visuals-forcasting-tbats/) </br>Egy idősorozat-előrejelzés olyan sorozatokhoz, amelyek több, a TBATS-modellt használó szezonalitással rendelkeznek
| <img src="media/samples/forecasting-with-ARIMA.png" width="200"> | <img src="media/samples/funnel-plot.png" width="200"> | <img src="media/samples/outliers-detection.png" width="200"> 
| [Előrejelzés az ARIMA-tól](https://github.com/Microsoft/powerbi-visuals-forcastingarima/) </br>Integrált autoregressziós mozgóátlag (ARIMA) használatával jósolja meg a jövőbeli értékeket a korábbi adatok alapján | [Tölcsérdiagram](https://github.com/Microsoft/powerbi-visuals-funnel/) </br>A tölcsérdiagrammal megtalálhatja a kiugró értékeket az adatai között | [Kiugró adatok észlelése](https://github.com/Microsoft/powerbi-visuals-outliers-det/) </br>Az arra legalkalmasabb módszert és ábrát használva találhatja meg az adathalmaz kiugró értékeit
| <img src="media/samples/spline-chart.png" width="200"> | <img src="media/samples/time-series-decomposition-chart.png" width="200"> | <img src="media/samples/time-series-forecasting-chart.png" width="200">
| [Görbe diagram](https://github.com/Microsoft/powerbi-visuals-spline/) </br>Vizualizálhatja és értelmezheti a zavaros adatokat | [Idősorfelbontási diagram](https://github.com/Microsoft/powerbi-visuals-timeseriesdecomposition/) </br>„Szezonális és trendalapú dekompozíció LOESS használatával” módszer használata az idősor komponenseinek értelmezéséhez | [Idősor-előrejelzési diagram](https://github.com/Microsoft/powerbi-visuals-forcasting-exp/) </br>Exponenciális simítási modell használata a jövőbeli értékek megjósolásához a múltban megfigyelt értékek alapján

## <a name="next-steps"></a>Következő lépések

Ha szeretné kipróbálni, hogyan lehet létrehozni Power BI-vizualizációkat, tekintse meg a következőt: [Oktatóanyagot: Power BI-vizualizáció fejlesztése](custom-visual-develop-tutorial.md).
