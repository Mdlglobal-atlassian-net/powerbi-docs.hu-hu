---
title: Irányítópult-csempék az ügyfeleknek készült Power BI szolgáltatásban
description: Információk az ügyfeleknek készült Power BI szolgáltatás irányítópult-csempéiről. Ide tartoznak az SQL Server Reporting Services-ből (SSRS-ből) létrehozott csempék is.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: e82c82430b42874e512265b9dae113b86925a51d
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83273270"
---
# <a name="dashboard-tiles-in-power-bi"></a>Irányítópult-csempék a Power BI-ban

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-ynny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

A csempék az adatokról készített, és egy *tervező* által az irányítópultra kitűzött pillanatfelvételek. A *tervezők* létrehozhatnak csempéket jelentésből, adatkészletből, irányítópultból, a Q&A kérdésmezőjéből, az Excelből, az SQL Server Reporting Servicesből (SSRS) és sok minden másból.  Ezen a képernyőfelvételen több irányítópultra tűzött csempe látható.

![Power BI-irányítópult](./media/end-user-tiles/power-bi-dash.png)


A jelentésekből kitűzött csempék mellett a *tervezők* közvetlenül az irányítópulthoz is hozzáadhatnak önálló csempéket a **Csempe hozzáadása** paranccsal. Önmagukban álló csempék lehetnek többek között szövegmezők, képek, videók, streaming-adatok, webtartalmak.

További segítségre van szüksége annak megértéséhez, hogy milyen elemekből épül fel a Power BI?  Tekintse meg a [Power BI alapfogalmait](end-user-basic-concepts.md) ismertető cikket.


## <a name="interacting-with-tiles-on-a-dashboard"></a>Az irányítópulton levő csempék használata

1. A három pont megjelenítéséhez álljon a csempe fölé.
   
    ![csempe három pont](./media/end-user-tiles/ellipses_new.png)
2. A három pontra kattintva nyissa meg a csempeműveletek menüjét. A lehetőségek a vizualizáció típusától és a csempe létrehozásához használt módszertől függően változnak. Íme néhány példa arra, hogy mit láthat.

    - a Q&A használatával létrehozott csempe
   
        ![három pont ikon](./media/end-user-tiles/power-bi-options-1.png)

    - munkafüzetből létrehozott csempe
   
        ![három pont ikon](./media/end-user-tiles/power-bi-options-2.png)

    - jelentésből létrehozott csempe
   
        ![három pont ikon](./media/end-user-tiles/power-bi-options-3.png)
   
    Ebből a menüből:
   
   * [Megnyithatja a csempe létrehozásához használt jelentést](end-user-reports.md) ![jelentés ikon](./media/end-user-tiles/chart-icon.jpg)  
   
   * [Megnyithatja a csempe létrehozásához használt Q&A-kérdést ](end-user-reports.md) ![Q&A ikon](./media/end-user-tiles/qna-icon.png)  
   

   * [Megnyithatja a csempe létrehozásához használt munkafüzetet ](end-user-reports.md) ![munkalap ikon](./media/end-user-tiles/power-bi-open-worksheet.png)  
   * [Megtekintheti a csempét fókusz módban ](end-user-focus.md) ![fókusz ikon](./media/end-user-tiles/fullscreen-icon.jpg)  
   * [Elemzéseket tekinthet meg ](end-user-insights.md) ![elemzések ikon](./media/end-user-tiles/power-bi-insights.png)
   * [Megjegyzéseket adhat hozzá, és beszélgetést indíthat](end-user-comment.md)  ![megjegyzés ikon](./media/end-user-tiles/comment-icons.png)
   * [Kezelheti az irányítópult adott csempéjén beállított riasztásokat](end-user-alerts.md)  ![riasztás ikon](./media/end-user-tiles/power-bi-alert-icon.png)
   * [Adatokat nyithat meg az Excelben](end-user-export.md)  ![exportálás ikon](./media/end-user-tiles/power-bi-export-icon.png)


3. A művelet menü bezárásához kattintson egy üres területre a vásznon.

### <a name="select-click-a-tile"></a>Csempék kiválasztása
Az, hogy mi történik, amikor rákattint valamelyik csempére, attól függ, hogyan lett létrehozva a csempe, és hogy tartozik-e hozzá [egyedi hivatkozás](../create-reports/service-dashboard-edit-tile.md). Ha tartozik hozzá egyedi hivatkozás, a csempe kiválasztásakor a rendszer a hivatkozott oldalra lépteti. Más esetben a csempére kattintáskor a létrehozásához használt helyszíni jelentéshez, Excel-munkafüzethez, SSRS-jelentéshez vagy Q&A-kérdéshez irányítja a rendszer.

> [!NOTE]
> Ez alól csak a közvetlenül az irányítópulton, a **Csempe hozzáadása** funkcióval létrehozott videócsempék képeznek kivételt. Amikor egy így létrehozott videócsempére kattint, a rendszer közvetlenül az irányítópulton játssza le a videót.   
> 
> 

## <a name="considerations-and-troubleshooting"></a>Szempontok és hibaelhárítás
* Ha a vizualizáció létrehozásához használt jelentés nem lett mentve, akkor nem történik semmi a csempére kattintáskor.
* Ha a csempe Excel Online-munkafüzetből lett létrehozva, és a felhasználónak ahhoz nincs legalább Olvasási jogosultsága, a csempe kiválasztásakor nem fog megnyílni az Excel Online-munkafüzet.
* Olyan csempe esetén, melyet a **Csempe létrehozása** funkcióval közvetlenül az irányítópulton hozott létre a felhasználó, és beállított hozzá egy egyedi hiperhivatkozást, a csempe címére, alcímére vagy magára a csempére kattintáskor a rendszer megnyitja az adott URL-címet.  Más esetben a közvetlenül az irányítópulton kép, webkód vagy szövegdoboz részére létrehozott csempe kiválasztása nem indít el semmilyen műveletet.
* Ha az SSRS-en nem jogosult egy jelentés használatára, az SSRS alapján létrehozott csempék kiválasztásakor a rendszer megjelenít egy oldalt, amely jelezni fog, hogy a felhasználó nem rendelkezik megfelelő hozzáféréssel (rsAccessDenied).
* Ha nincs hozzáférése ahhoz a hálózathoz, ahol az SSRS található, SSRS-ből létrehozott csempe kiválasztásakor a rendszer megjelenít majd egy oldalt, amely azt jelzi, hogy a kiszolgáló nem található (HTTP 404). Ahhoz, hogy meg tudja tekinteni a jelentést, az Ön eszközének hálózati hozzáféréssel kell rendelkeznie a jelentés-kiszolgálóhoz.
* A csempe létrehozásához használt vizualizációs elem változásakor a csempe nem változik.  Ha például a *tervező* kitűz egy sávdiagramot egy jelentésből, majd a sávdiagramot oszlopdiagramra cseréli, az irányítópulton megjelenő csempén továbbra is egy sávdiagram lesz látható. Az adatok frissülni fognak, de a diagram típusa nem.

## <a name="next-steps"></a>További lépések
[Adatfrissítés](../connect-data/refresh-data.md)

[Power BI – Alapfogalmak](end-user-basic-concepts.md)


