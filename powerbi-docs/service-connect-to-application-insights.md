---
title: Csatlakozás az Application Insightshoz Csatlakozás a Power BI-hoz
description: Power BI-hoz készült Application Insights
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 08/10/2018
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 34e3524d561fb6f6394d69fed55c1bd29bddf4bd
ms.sourcegitcommit: 60fb46b61ac73806987847d9c606993c0e14fb30
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/25/2018
ms.locfileid: "50100588"
---
# <a name="connect-to-application-insights-with-power-bi"></a>Csatlakozás az Application Insightshoz Power BI-jal
A Power BI használatával nagyszerű egyéni irányítópultokat hozhat létre az [Application Insights](/azure/application-insights/app-insights-overview/) telemetriai adataiból. Alkalmazásai telemetriai adatait újszerű módokon jelenítheti meg. Több alkalmazás vagy szolgáltatás mutatóit egyetlen irányítópulton egyesítheti. Az Application Insights-hoz készült Power BI tartalomcsomagnak ez az első kiadása. Olyan általánosan elterjedt, használati metrikákkal kapcsolatos widgeteket tartalmaz, mint például az aktív felhasználók száma, oldalmegtekintések, munkamenetek, böngésző- és operációsrendszer-verziók, valamint a felhasználók földrajzi eloszlása egy térképen.

Csatlakozzon a [Power BI-hoz készített Application Insights tartalomcsomaghoz](https://app.powerbi.com/getdata/services/application-insights).

>[!NOTE]
>Ez az integrációs mód már **elavult**. Ha többet szeretne megtudni az Application Insights Power BI-hoz való csatlakoztatásáról, használja az [elemzési lekérdezés exportálása funkciót](https://docs.microsoft.com/azure/application-insights/app-insights-export-power-bi#export-analytics-queries).

## <a name="how-to-connect"></a>Csatlakozás
1. Kattintson az **Adatok lekérése** elemre a bal oldalon lévő navigációs ablaktábla alján.
   
    ![Adatok lekérése gomb](media/service-connect-to-application-insights/pbi_getdata.png)
2. A **Szolgáltatások** mezőben kattintson a **Beolvasás** gombra.
   
    ![Beolvasás gomb](media/service-connect-to-application-insights/pbi_getservices.png)
3. Kattintson az **Application Insights** > **Letöltés most** lehetőségre.
   
    ![Application Insights tartalomcsomag](media/service-connect-to-application-insights/appinsights.png)
4. Adja meg annak az alkalmazásnak az adatait az **Application Insights Resource name** (Application Insights-erőforrás neve), a **Resource Group** (Erőforráscsoport) és a **Subscription** (Előfizetés azonosító) paramétereknél, amelyhez csatlakozni szeretne. Ha ezzel kapcsolatban további információra van szüksége, tekintse át alább az [Application Insights paraméterek megkeresése](#FindingAppInsightsParams) részt.
   
    ![Application Insights-kapcsolat párbeszédpanel](media/service-connect-to-application-insights/pbi_contpkappinsitconnectndialog.png)    
5. Kattintson a **Sign In** (Bejelentkezés) lehetőségre, majd a csatlakozáshoz kövesse a képernyőn olvasható lépéseket.
   
    ![Application Insights-kapcsolat bejelentkezési párbeszédpanelje](media/service-connect-to-application-insights/pbi_contpkappinsitconnectn2.png)
6. Az importálás automatikusan megkezdődik. Amikor befejeződik, megjelenik egy értesítés, a navigációs ablaktáblán pedig megjelenik egy új irányítópult, jelentés és modell, egy csillaggal jelölve.  Az importált adatok megtekintéséhez válassza ki az irányítópultot.
   
    ![Application Insights irányítópult](media/service-connect-to-application-insights/pbi_contpkappinsitdash.png)

**Hogyan tovább?**

* [Kérdéseket tehet fel a Q&A mezőben](consumer/end-user-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](consumer/end-user-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

## <a name="whats-included"></a>Tartalom
Az Application Insights tartalomcsomag a következő táblákat és metrikákat tartalmazza:  

    ´´´
    - ApplicationDetails  
    - UniqueUsersLast7Days   
    - UniqueUsersLast30Days   
    - UniqueUsersDailyLast30Days  
    - UniqueUsersByCountryLast7Days  
    - UniqueUsersByCountryLast30Days   
    - PageViewsDailyLast30Days   
    - SessionsLast7Days   
    - SessionsLast30Days  
    - PageViewsByBrowserVersionDailyLast30Days   
    - UniqueUsersByOperatingSystemLast7Days   
    - UniqueUsersByOperatingSystemLast30Days    
    - SessionsDailyLast30Days   
    - SessionsByCountryLast7Days   
    - SessionsByCountryLast30Days   
    - PageViewsByCountryDailyLast30Days  
    ´´´ 

<a name="FindingAppInsightsParams"></a>

## <a name="finding-parameters"></a>Paraméterek helye
Mind a Resource Name (Erőforrás neve), mind a Resource Group (Erőforráscsoport) és a Subscription ID (Előfizetés azonosítója) megtalálhatók az Azure Portalon. Ha a névre (Name) kattint, a rendszer megjelenít egy részteles nézetet, és az „Essentials” (Alapvető erőforrások) legördülő listából kikeresheti azokat az értékeket, amelyekre szüksége van.

![Application Insights paraméterek](media/service-connect-to-application-insights/pbi_contpkappinsitparams.png)

Másolja ki és illessze be a használni kívánt értékeket a Power BI-hoz beadandó mezőkbe:

![Application Insights paraméterek](media/service-connect-to-application-insights/pbi_contpkappinsitparam2.png)

## <a name="next-steps"></a>Következő lépések
[Első lépések a Power BI-ban](service-get-started.md)

[Adatok lekérése a Power BI-ban](service-get-data.md)

