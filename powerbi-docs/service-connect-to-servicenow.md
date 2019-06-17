---
title: Csatlakozás a ServiceNow-hoz a Power BI használatával
description: ServiceNow a Power BI-ban
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: c4ca0332a68686feb22517ff6ac720650ce1c87d
ms.sourcegitcommit: 762857c8ca09ce222cc3f8b006fa1b65d11e4ace
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66721237"
---
# <a name="connect-to-servicenow-with-power-bi-for-incident-reporting"></a>Csatlakozás a ServiceNow-hoz a Power BI használatával incidensjelentések készítéséhez
A ServiceNow több terméket és megoldást is kínál a vállalkozások számára, köztük üzleti, üzemeltetési és informatikai felügyeleti megoldásokat. A tartalomcsomag több jelentést és elemzést is tartalmaz a nyitott, a nemrég megoldott és a nemrég lezárt incidensekkel kapcsolatban.  

Csatlakozzon a [ServiceNow-incidensekhez](https://app.powerbi.com/getdata/services/servicenow) készült Power BI-tartalomcsomaghoz.

## <a name="how-to-connect"></a>Csatlakozás
1. A bal oldali navigációs ablaktábla alján kattintson az **Adatok lekérése** elemre.
   
   ![](media/service-connect-to-servicenow/pbi_getdata.png) 
2. A **Szolgáltatások** mezőben kattintson a **Lekérés** elemre.
   
   ![](media/service-connect-to-servicenow/pbi_getservices.png) 
3. Kattintson a **ServiceNow-incidensek** \> **Lekérés** elemre.
   
   ![](media/service-connect-to-servicenow/connect.png)
4. Adja meg a ServiceNow-példánya URL-címét és a lekérni kívánt napok és rekordok tartományát. Vegye figyelembe, hogy ha a kettő korlátozás közül bármelyik teljesül, az importálás leáll.
   
   ![](media/service-connect-to-servicenow/params.png)
5. Amikor a rendszer erre kéri, adja meg a ServiceNow **Alapszintű** hitelesítő adatait. Vegye figyelembe, hogy az egyszeri bejelentkezés jelenleg nem támogatott. A rendszerkövetelményekről az alábbiakban talál pontosabb részleteket.
   
   ![](media/service-connect-to-servicenow/creds.png)
6. A bejelentkezés folyamatának végén megkezdődik az importálás folyamata. Ha befejeződött, a navigációs panelen megjelenik egy új irányítópult, jelentés és modell. Válassza ki az irányítópultot az importált adatok megtekintéséhez.
   
    ![](media/service-connect-to-servicenow/dashboard.png)

**Mi a következő lépés?**

* [Kérdéseket tehet fel a Q&A mezőben](consumer/end-user-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](consumer/end-user-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

## <a name="system-requirements"></a>Rendszerkövetelmények
A csatlakozáshoz a következőkre lesz szüksége:  

* Egy fiók, amely hozzáférhet a ceg.service-now.com címhez Alapszintű hitelesítéssel (az egyszeri bejelentkezést ez a verzió nem támogatja)  
* A fióknak rendelkeznie kell a rest_service szerepkörrel, valamint olvasási hozzáféréssel az incidens táblájához  

## <a name="troubleshooting"></a>Hibaelhárítás
Ha a betöltéskor a rendszer a hitelesítő adatokkal kapcsolatos hibát jelez, tekintse át a fenti hozzáférési követelményeket. Ha rendelkezik a helyes engedélyekkel, és így is problémákba ütközik, forduljon a ServiceNow-rendszergazdájához, hogy beszerezze mindazon további engedélyeket, amelyek az egyéni példánya esetén szükségesek lehetnek.

Ha hosszú betöltési időket tapasztal, ellenőrizze az incidensek és a napok számát, amelyeket a csatlakozáskor megadott, és esetleg csökkentse ezeket.

## <a name="next-steps"></a>Következő lépések
[Mi az a Power BI?](power-bi-overview.md)

[A Power BI szolgáltatás alapfogalmai tervezők számára](service-basic-concepts.md)

