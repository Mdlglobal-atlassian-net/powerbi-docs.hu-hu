---
title: Csatlakozás a Troux-hoz a Power BI használatával
description: Troux a Power BI-hoz
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: dbf3831264a354ec96a38751dfa7a3719c5c9f2a
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/17/2018
---
# <a name="connect-to-troux-for-power-bi"></a>Csatlakozás a Troux-hoz a Power BI használatával
A Troux-tartalomcsomaggal teljesen új módon, közvetlenül a Power BI-ban jelenítheti meg a vállalati architektúra adattárát. A tartalomcsomag az üzleti képességekről, a képességeket biztosító alkalmazásokról, és az alkalmazásokat támogató technológiákról nyújt elemzéseket, amelyek a Power BI segítségével teljes körűen testre szabhatók.

Csatlakozzon a Power BI-hoz készült [Troux-tartalomcsomaghoz](https://app.powerbi.com/getdata/services/troux).

## <a name="how-to-connect"></a>A csatlakozás menete
1. A bal oldali navigációs ablaktábla alján kattintson az **Adatok lekérése** elemre.
   
   ![](media/service-connect-to-troux/getdata.png)
2. A **Szolgáltatások** mezőben válasza a **Beolvasás** elemet.
   
   ![](media/service-connect-to-troux/services.png)
3. Kattintson a **Troux** \>  **Get** elemre.
   
   ![](media/service-connect-to-troux/troux.png)
4. Adja meg a Troux OData-csatornájának URL-címét. A [paraméterek megkereséséről](#FindingParams) alább olvashat részletesebben.
   
   ![](media/service-connect-to-troux/params.png)
5. **Hitelesítési módszerként** válassza az **Alapszintű** lehetőséget, adja meg a felhasználónevét és a jelszavát (figyeljen a kis- és nagybetűkre), majd kattintson a **Bejelentkezés** elemre.
   
    ![](media/service-connect-to-troux/creds.png)
6. A jóváhagyás után automatikusan megkezdődik az importálás. Ha befejeződött, a navigációs panelen megjelenik egy új irányítópult, jelentés és modell. Válassza ki az irányítópultot az importált adatok megtekintéséhez.
   
     ![](media/service-connect-to-troux/dashboard.png)

**Mi a következő lépés?**

* [Kérdéseket tehet fel a Q&A mezőben](power-bi-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](service-dashboard-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

## <a name="system-requirements"></a>Rendszerkövetelmények
Hozzáférés szükséges a Troux OData-adatcsatornához és a Troux 9.5.1-es vagy újabb verziójához.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Paraméterek keresése
Az egyedi Troux OData-adatcsatornája URL-címéért forduljon az Ügyféltámogatáshoz

## <a name="troubleshooting"></a>Hibaelhárítás
Ha a hitelesítő adatok megadása után időtúllépési hibát tapasztal, kísérelje meg újra a kapcsolódást.

## <a name="next-steps"></a>További lépések
[Első lépések a Power BI-ban](service-get-started.md)

[Adatok lekérése a Power BI-ban](service-get-data.md)

