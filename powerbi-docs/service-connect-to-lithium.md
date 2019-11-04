---
title: Kapcsolódás a Power BI-ból a Lithiumhoz
description: Lithium a Power BI-hoz
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: tebercov
LocalizationGroup: Connect to services
ms.openlocfilehash: 9a02c642d0b5d766b22b3b8c3853da2d4d773cbd
ms.sourcegitcommit: d441d350504f8c6d9e100d229757add6237f0bef
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/30/2019
ms.locfileid: "73060556"
---
# <a name="connect-to-lithium-with-power-bi"></a>Kapcsolódás a Power BI-ból a Lithiumhoz

A Lithium megbízható kapcsolatokat épít ki a világ legjobb márkái és az ügyfeleik között, és segít az embereknek választ kapni a kérdéseikre és megosztani a tapasztalataikat. Ha csatlakoztatja a Lithium-tartalomcsomagot a Power BI-hoz, akkor mérni tudja az online közössége legfontosabb metrikáit, így serkentheti az eladásokat, csökkentheti a szolgáltatási díjakat és növelheti ügyfelei hűségét. 

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Kapcsolódjon a Power BI-hoz készült [Lithium-tartalomcsomaghoz](https://app.powerbi.com/getdata/services/lithium).

>[!NOTE]
>A Power BI-tartalomcsomag a Lithium API-t használja. A túlzottan sok API-hívás további költségeket vonhat maga után a Lithium oldaláról. Kérjük, egyeztessen a Lithium-rendszergazdájával.

## <a name="how-to-connect"></a>A kapcsolódás menete
1. A bal oldali navigációs ablaktábla alján kattintson az **Adatok lekérése** elemre.
   
   ![](media/service-connect-to-lithium/pbi_getdata.png) 
2. A **Szolgáltatások** mezőben válasza a **Beolvasás** elemet.
   
   ![](media/service-connect-to-lithium/pbi_getservices.png) 
3. Válassza a **Lithium** \> **Beolvasás** lehetőséget.
   
   ![](media/service-connect-to-lithium/lithiumconnect.png)
4. Adja meg a Lithium-közössége URL-címét. Ennek formátuma: *https://community.yoursite.com* .
   
   ![](media/service-connect-to-lithium/params.png)
5. Amikor a rendszer kéri, adja meg a Lithium-fiókja hitelesítő adatait. Válassza ki az **oAuth 2** hitelesítési mechanizmust, kattintson a **Bejelentkezés** elemre, majd kövesse a Lithium-fiók hitelesítési folyamatát.
   
   ![](media/service-connect-to-lithium/creds.png)
   
   ![](media/service-connect-to-lithium/creds2.png)
6. A sikeres bejelentkezési folyamat után megkezdődik az importálási folyamat. Ha befejeződött, a navigációs panelen megjelenik egy új irányítópult, jelentés és modell. Válassza ki az irányítópultot az importált adatok megtekintéséhez.
   
    ![](media/service-connect-to-lithium/lithium.png)

**Mi a következő lépés?**

* [Kérdéseket tehet fel a Q&A mezőben](consumer/end-user-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](consumer/end-user-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

## <a name="system-requirements"></a>Rendszerkövetelmények
A Lithium-tartalomcsomaghoz 15.9-es vagy újabb verziójú Lithium-közösség szükséges. A verzió megerősítéséhez, kérjük, egyeztessen Lithium-rendszergazdájával.

## <a name="next-steps"></a>Következő lépések
[Mi az a Power BI?](fundamentals/power-bi-overview.md)

[A Power BI szolgáltatás alapfogalmai tervezők számára](service-basic-concepts.md)

