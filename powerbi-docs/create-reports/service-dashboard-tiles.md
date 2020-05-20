---
title: Irányítópultcsempék a Power BI szolgáltatás tervezői számára – bevezetés
description: Ez a cikk a Power BI-beli irányítópult-csempéket, köztük az SQL Server Reporting Services- (SSRS-) jelentésekből létrehozott csempéket ismerteti.
author: maggiesMSFT
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/17/2020
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 96a780d7d7b100acb283623107d4ec841666bb8f
ms.sourcegitcommit: a72567f26c1653c25f7730fab6210cd011343707
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561662"
---
# <a name="intro-to-dashboard-tiles-for-power-bi-designers"></a>Irányítópultcsempék a Power BI szolgáltatás tervezői számára – bevezetés

A csempék az adatokról készített és az irányítópultra kitűzött pillanatfelvételek. Csempe létrehozható jelentésből, adatkészletből, irányítópultból, a Q&A mezőjéből, az Excelből, az SQL Server Reporting Services (SSRS) jelentéseiből és sok minden másból.  Ezen a képernyőfelvételen több irányítópultra tűzött csempe látható.

![Power BI-irányítópult](media/service-dashboard-tiles/power-bi-dashboard.png)

Az irányítópultok és az irányítópulton található csempék nem a Power BI Desktophoz, hanem a Power BI szolgáltatáshoz tartozó funkciók. Mobileszközön nem hozhat létre irányítópultokat, azonban [megtekintheti és megoszthatja](../consumer/mobile/mobile-apps-view-dashboard.md) őket.

A csempék rögzítése mellett önálló csempéket is létrehozhat közvetlenül az irányítópulton a [Csempe hozzáadása](service-dashboard-add-widget.md) vezérlő használatával. Önmagukban álló csempék lehetnek többek között szövegmezők, képek, videók, streaming-adatok, webtartalmak.

További segítségre van szüksége annak megértéséhez, hogy milyen elemekből épül fel a Power BI? Lásd: [A Power BI szolgáltatás alapfogalmai tervezők számára](../fundamentals/service-basic-concepts.md).

> [!NOTE]
> A csempe létrehozásához használt vizualizációs elem változásakor a csempe nem változik.  Például ha kitűz egy sávdiagramot egy jelentésből, majd a sávdiagramot oszlopdiagramra cseréli, az irányítópulton megjelenő csempén továbbra is sávdiagram lesz látható. Az adatok frissülni fognak, de a diagram típusa nem.
> 
> 

## <a name="pin-a-tile"></a>Csempe rögzítése
Az irányítópultokra többféleképpen lehet felvenni (kitűzni) csempét. Csempéket a következő helyekről rögzíthet:

* [Power BI Q&A-ből](service-dashboard-pin-tile-from-q-and-a.md)
* [Jelentésből](service-dashboard-pin-tile-from-report.md)
* [Másik irányítópultról](service-pin-tile-to-another-dashboard.md)
* [OneDrive vállalati verzión található Excel-munkafüzetből](service-dashboard-pin-tile-from-excel.md)
* [Quick Insights (Gyors elemzések)](service-insights.md)
* [Helyszíni többoldalas jelentés a Power BI jelentéskészítő kiszolgálóban vagy az SQL Server Reporting Servicesben](https://docs.microsoft.com/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards)

A képek, szövegdobozok, videók, streamelési adatok és webtartalmak különálló csempéit közvetlenül az irányítópulton hozhatja létre a [Csempe hozzáadása](service-dashboard-add-widget.md) vezérlő használatával.

  ![Csempe hozzáadása ikon](media/service-dashboard-tiles/add_widgetnew.png)

## <a name="interact-with-tiles-on-a-dashboard"></a>Irányítópulton levő csempék használata
Az irányítópulton rögzített csempéket áthelyezheti és átméretezheti, vagy megváltoztathatja azok megjelenését és viselkedését.

### <a name="move-and-resize-a-tile"></a>Csempék mozgatása és átméretezése
Fogja meg az egyik csempét, és [mozgassa körbe az irányítópulton](service-dashboard-edit-tile.md). A csempe átméretezéséhez kattintson a csempe fogópontjára ![Csempe fogópontja](media/service-dashboard-tiles/resize-handle.jpg).

### <a name="hover-over-a-tile-to-change-the-appearance-and-behavior"></a>Csempék megjelenésének és működésének módosítása a csempére pozicionálva
1. A három pont megjelenítéséhez vigye a kurzort a csempe fölé.
   
    ![Csempe három pontja](media/service-dashboard-tiles/ellipses_new.png)
2. A három pont választásával nyissa meg a csempeműveletek menüjét.
   
    ![Három pont ikon](media/service-dashboard-tiles/power-bi-tile-menu.png)
   
    Ebből a menüből:
   
     * [Megjegyzéseket adhat az irányítópulthoz](../consumer/end-user-comment.md).
     * [Megnyithatja a csempe létrehozásához használt jelentést](../consumer/end-user-reports.md).  
     * [Megnyithatja a csempét fókusz módban](../consumer/end-user-focus.md).   
     * [Exportálhatja a csempéhez használt adatokat](../visuals/power-bi-visualization-export-data.md).
     * [Szerkesztheti a címet és az alcímet, és hivatkozást vehet fel](service-dashboard-edit-tile.md). 
     * [Elemzéseket futtathat](service-insights.md). 
     * [Kitűzheti a csempét egy másik irányítópultra](service-pin-tile-to-another-dashboard.md).
     * [Törölheti a csempét](service-dashboard-edit-tile.md).

3. A műveleti menü bezárásához kattintson egy üres területre az irányítópulton.

### <a name="select-a-tile"></a>Csempe kiválasztása
Az, hogy mi történik, amikor rákattint valamelyik csempére, attól függ, hogyan lett létrehozva a csempe. Ellenkező esetben a csempére kattintáskor a létrehozásához használt jelentéshez, Excel Online-munkafüzethez, helyszíni Reporting Services-jelentéshez vagy Q&A-kérdéshez irányítja a rendszer. Ha tartozik hozzá [egyéni hivatkozás](service-dashboard-edit-tile.md), a csempe kiválasztásakor a rendszer a hivatkozott oldalra lépteti.

> [!NOTE]
> Ez alól kivételt képeznek a közvetlenül az irányítópulton, a **Csempe hozzáadása** funkcióval létrehozott videócsempék. Amikor egy így létrehozott videócsempére kattint, a rendszer közvetlenül az irányítópulton játssza le a videót.   
> 
> 

## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás

* Ha a vizualizáció létrehozásához használt jelentés nem lett mentve, akkor a csempe kiválasztásakor nem történik semmi.
* Ha a csempe Excel Online-munkafüzetből lett létrehozva, a munkafüzethez legalább olvasási engedélyre lesz szüksége. Ellenkező esetben a csempe kiválasztásakor nem nyílik meg a munkafüzet az Excel Online-ban.
* Tegyük fel, hogy közvetlenül az irányítópulton hozta létre a csempét a **Csempe hozzáadása** művelettel, majd egy egyéni hivatkozást állított be hozzá. Ha így történt, a cím, alcím vagy csempe kiválasztásakor megnyílik az adott URL-cím. Ellenkező esetben a közvetlenül az irányítópulton kép, webkód vagy szövegdoboz részére létrehozott csempe kiválasztása nem indít el semmilyen műveletet.
* Csempék létrehozhatók helyszíni többoldalas jelentésekből a Power BI jelentéskészítő kiszolgálóban vagy az SQL Server Reporting Servicesben. Ha nem rendelkezik a helyszíni jelentés eléréséhez szükséges engedéllyel, a csempe kiválasztásakor megnyíló oldal arról tájékoztatja, hogy nincs hozzáférése (rsAccessDenied).
* Tegyük fel, hogy helyszíni többoldalas jelentésből a Power BI jelentéskészítő kiszolgálóban vagy az SQL Server Reporting Servicesben létrehozott csempét választ ki. Ha nincs hozzáférése ahhoz a hálózathoz, ahol a jelentéskészítő kiszolgáló található, akkor a többoldalas jelentésből létrehozott csempe kiválasztásakor a rendszer megjelenít egy oldalt, amely azt jelzi, hogy a kiszolgáló nem található (HTTP 404). Ahhoz, hogy meg tudja tekinteni a jelentést, az Ön eszközének hálózati hozzáféréssel kell rendelkeznie a jelentéskészítő kiszolgálóhoz.
* A csempe létrehozásához használt vizualizáció változásakor a csempe nem változik. Például ha kitűz egy sávdiagramot egy jelentésből, majd a sávdiagramot oszlopdiagramra cseréli, az irányítópulton megjelenő csempén továbbra is sávdiagram lesz látható. Az adatok frissülnek, de a vizualizáció típusa nem.

## <a name="next-steps"></a>Következő lépések
- [Kártyák (nagy méretű numerikus csempék) létrehozása az irányítópulthoz](../visuals/power-bi-visualization-card.md)
- [Irányítópultok bemutatása Power BI-tervezők számára](service-dashboards.md)  
- [Adatfrissítés a Power BI-ban](../connect-data/refresh-data.md)
- [A Power BI szolgáltatás alapfogalmai tervezők számára](../fundamentals/service-basic-concepts.md)
- [Power BI-csempe Office-dokumentumba integrálása](https://powerbi.microsoft.com/blog/integrating-power-bi-tiles-into-office-documents/)
- [Reporting Services-elem rögzítése Power BI-irányítópulton](/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/).
