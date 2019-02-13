---
title: Irányítópultcsempék a Power BI szolgáltatás tervezői számára – bevezetés
description: Minden, amit a Power BI irányítópult csempékről tudni érdemes. Ide tartoznak az SQL Server Reporting Services (SSRS) jelentéseiből létrehozott csempék is.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/21/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: c8b5728c951bc1a25e71da8885997814c5485cd4
ms.sourcegitcommit: 5e83fa6c93a0bc6599f76cc070fb0e5c1fce0082
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/13/2019
ms.locfileid: "56215987"
---
# <a name="intro-to-dashboard-tiles-for-power-bi-designers"></a>Irányítópultcsempék a Power BI szolgáltatás tervezői számára – bevezetés

A csempék az adatokról készített és az irányítópultra kitűzött pillanatfelvételek. Csempe létrehozható jelentésből, adatkészletből, irányítópultból, a Q&A mezőjéből, az Excelből, az SQL Server Reporting Services (SSRS) jelentéseiből és sok minden másból.  Ezen a képernyőfelvételen több irányítópultra tűzött csempe látható.

![Power BI-irányítópult](media/service-dashboard-tiles/power-bi-dashboard.png)

Az irányítópultok és az irányítópulton található csempék nem a Power BI Desktophoz, hanem a Power BI szolgáltatáshoz tartozó funkciók. Mobileszközön nem hozhat létre irányítópultokat, azonban [megtekintheti és megoszthatja](mobile-apps-view-dashboard.md) őket.

A kitűzés mellett önálló csempéket is létrehozhat közvetlenül az irányítópulton a [Csempe hozzáadása](service-dashboard-add-widget.md) lehetőséggel. Önmagukban álló csempék lehetnek többek között szövegmezők, képek, videók, streaming-adatok, webtartalmak.

További segítségre van szüksége annak megértéséhez, hogy milyen elemekből épül fel a Power BI?  Tekintse meg a [Power BI alapfogalmait](service-basic-concepts.md) ismertető cikket.

> [!NOTE]
> A csempe létrehozásához használt vizualizációs elem változásakor a csempe nem változik.  Például ha kitűz egy sávdiagramot egy jelentésből, majd a sávdiagramot oszlopdiagramra cseréli, az irányítópulton megjelenő csempén továbbra is sávdiagram lesz látható. Az adatok frissülni fognak, de a diagram típusa nem.
> 
> 

## <a name="pin-a-tile-from"></a>Csempe kitűzése
Az irányítópultokra többféleképpen lehet felvenni (kitűzni) csempét. Csempék kitűzhetők:

* [Power BI Q&A-ből](service-dashboard-pin-tile-from-q-and-a.md)
* [jelentésből](service-dashboard-pin-tile-from-report.md)
* [másik irányítópultról](service-pin-tile-to-another-dashboard.md)
* [OneDrive vállalati verzión található Excel-munkafüzetből](service-dashboard-pin-tile-from-excel.md)
* [az Excelhez készült Power BI Publisherből](publisher-for-excel.md)
* [Gyors elemzések](service-insights.md)
* [Reporting Services](https://docs.microsoft.com/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards)

A képek, szövegdobozok, videók, streamelési adatok és webtartalmak különálló csempéi közvetlenül az irányítópulton is létrehozhatók a [Csempe hozzáadása](service-dashboard-add-widget.md) lehetőséget használva.

  ![Csempe hozzáadása ikon](media/service-dashboard-tiles/add_widgetnew.png)

## <a name="interacting-with-tiles-on-a-dashboard"></a>Az irányítópulton levő csempék használata
### <a name="move-and-resize-a-tile"></a>Csempék mozgatása és átméretezése
Fogja meg az egyik csempét, és [mozgassa körbe az irányítópulton](service-dashboard-edit-tile.md). A csempe átméretezéséhez kattintson a csempe fogópontjára ![fogópont](media/service-dashboard-tiles/resize-handle.jpg).

### <a name="hover-over-a-tile-to-change-the-appearance-and-behavior"></a>Csempék megjelenésének és működésének módosítása a csempére pozicionálva
1. A három pont megjelenítéséhez álljon a csempe fölé.
   
    ![csempe három pont](media/service-dashboard-tiles/ellipses_new.png)
2. A három pontra kattintva nyissa meg a csempeműveletek menüjét.
   
    ![három pont ikon](media/service-dashboard-tiles/power-bi-tile-menu.png)
   
    Ebből a menüből:
   
   * [Megnyithatja a csempe létrehozásához használt jelentést](service-reports.md) ![jelentés ikon](media/service-dashboard-tiles/chart-icon.jpg)  
   
   * [Megnyithatja a csempe létrehozásához használt munkafüzetet](service-reports.md) ![munkafüzet ikon](media/service-dashboard-tiles/power-bi-open-worksheet.png)  
     
    * [Megnyithatja a csempét fókusz módban](service-focus-mode.md) ![fókusz ikon](media/service-dashboard-tiles/fullscreen-icon.jpg)  
     * [Exportálhatja a csempéhez használt adatokat](visuals/power-bi-visualization-export-data.md) ![Adatok exportálása ikon](media/service-dashboard-tiles/export-icon.png)
     * [Cím és alcím szerkesztése, egy hivatkozás felvétele](service-dashboard-edit-tile.md) ![szerkesztés ikon](media/service-dashboard-tiles/pencil-icon.jpg)
     * [Elemzéseket futtathat ](service-insights.md) ![elemzések ikon](media/service-dashboard-tiles/power-bi-insights.png)
     * [Kitűzheti a csempét egy másik irányítópultra](service-pin-tile-to-another-dashboard.md)
       ![gombostű ikon](media/service-dashboard-tiles/pin-icon.jpg)
     * [Eltávolíthatja a csempét](service-dashboard-edit-tile.md)
     ![törlés ikon](media/service-dashboard-tiles/trash-icon.png)
3. A művelet menü bezárásához kattintson egy üres területre a vásznon.

### <a name="select-click-a-tile"></a>Csempék kiválasztása
Az, hogy mi történik, amikor rákattint valamelyik csempére, attól függ, hogyan lett létrehozva a csempe. Ha tartozik hozzá [egyedi hivatkozás](service-dashboard-edit-tile.md), a csempe kiválasztásakor a rendszer a hivatkozott oldalra lépteti. Ellenkező esetben a csempére kattintáskor a létrehozásához használt jelentéshez, Excel Online-munkafüzethez, helyszíni Reporting Services-jelentéshez vagy Q&A-kérdéshez irányítja a rendszer.

> [!NOTE]
> Ez alól csak a közvetlenül az irányítópulton, a **Csempe hozzáadása** funkcióval létrehozott videócsempék képeznek kivételt. Amikor egy így létrehozott videócsempére kattint, a rendszer közvetlenül az irányítópulton játssza le a videót.   
> 
> 

## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás

* Ha a vizualizáció létrehozásához használt jelentés nem lett mentve, akkor nem történik semmi a csempére kattintáskor.
* Ha a csempe Excel Online-munkafüzetből lett létrehozva, a munkafüzethez legalább olvasási engedélyre lesz szüksége. Ellenkező esetben a csempe kiválasztásakor nem nyílik meg a munkafüzet az Excel Online-ban.
* Tegyük fel, hogy közvetlenül az irányítópulton hozta létre a csempét a **Csempe hozzáadása** művelettel, majd egy egyéni hiperhivatkozást állított be hozzá. Ha így történt, a cím, alcím vagy csempe kiválasztásakor megnyílik az adott URL-cím. Ellenkező esetben a közvetlenül az irányítópulton kép, webkód vagy szövegdoboz részére létrehozott csempe kiválasztása nem indít el semmilyen műveletet.
* Ha a Reporting Servicesben nem jogosult egy jelentés használatára, a Reporting Services-jelentés alapján létrehozott csempék kiválasztásakor a rendszer megjelenít egy oldalt, amely jelzi, hogy nem rendelkezik megfelelő hozzáféréssel (rsAccessDenied).
* Ha nincs hozzáférése ahhoz a hálózathoz, ahol a Reporting Services-kiszolgáló található, egy Reporting Servicesből létrehozott csempe kiválasztásakor a rendszer megjelenít egy oldalt, amely azt jelzi, hogy a kiszolgáló nem található (HTTP 404). Ahhoz, hogy meg tudja tekinteni a jelentést, az Ön eszközének hálózati hozzáféréssel kell rendelkeznie a jelentéskészítő kiszolgálóhoz.
* A csempe létrehozásához használt vizualizációs elem változásakor a csempe nem változik.  Például ha kitűz egy sávdiagramot egy jelentésből, majd a sávdiagramot oszlopdiagramra cseréli, az irányítópulton megjelenő csempén továbbra is sávdiagram lesz látható. Az adatok frissülni fognak, de a diagram típusa nem.

## <a name="next-steps"></a>Következő lépések
[Kártyák (nagy méretű numerikus csempék) létrehozása az irányítópulthoz](power-bi-visualization-card.md)

[A Power BI-irányítópultok](service-dashboards.md)  

[Adatfrissítés](refresh-data.md)

[Power BI – alapfogalmak](service-basic-concepts.md)

[Csempe exportálása Power Pointba](http://blogs.msdn.com/b/powerbidev/archive/2015/09/28/integrating-power-bi-tiles-into-office-documents.aspx)

[Reporting Services-elemek kitűzése Power BI-irányítópultokra](https://msdn.microsoft.com/library/mt604784.aspx)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

