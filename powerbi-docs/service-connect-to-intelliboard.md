---
title: Kapcsolódás az IntelliBoardhoz a Power BI-jal
description: IntelliBoard a Power BI-ban
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: e912c47c58c96de8d2875b83a530468135e93ef2
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/30/2019
ms.locfileid: "70185926"
---
# <a name="connect-to-intelliboard-with-power-bi"></a>Kapcsolódás az IntelliBoardhoz a Power BI-jal
Az IntelliBoard jelentéskészítő szolgáltatások használatával biztosít egyszerűbb hozzáférést a Moodle tanuláskezelő rendszer adataihoz. A Power BI-hoz készült IntelliBoard-tartalomcsomag további elemzési lehetőségeket tartalmaz, köztük a tanfolyamok, a regisztrált felhasználók, az általános teljesítmény és az LMS-tevékenység metrikáit.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Kapcsolódjon a Power BI-hoz készült [IntelliBoard-tartalomcsomaghoz](https://app.powerbi.com/getdata/services/intelliboard).

## <a name="how-to-connect"></a>A kapcsolódás menete
1. A bal oldali navigációs ablaktábla alján kattintson az **Adatok lekérése** elemre.  
   
    ![](media/service-connect-to-intelliboard/getdata.png)
2. A **Szolgáltatások** mezőben kattintson a **Beolvasás** gombra.  
   
    ![](media/service-connect-to-intelliboard/services.png)
3. Válassza az **IntelliBoard**, majd a **Beolvasás** lehetőséget.  
   
    ![](media/service-connect-to-intelliboard/intelliboard.png)
4. Válassza ki az **OAuth 2**, majd a **Bejelentkezés** lehetőséget. Amikor a rendszer kéri, adja meg az IntelliBoard-fiókja hitelesítő adatait.
   
    ![](media/service-connect-to-intelliboard/creds.png)
   
    ![](media/service-connect-to-intelliboard/creds2.png)
5. A kapcsolódás után automatikusan betöltődik egy irányítópult, egy jelentés és egy adatkészlet. A befejezést követően a csempék frissülni fognak az Ön IntelliBoard-fiókjából származó adatokkal.
   
    ![](media/service-connect-to-intelliboard/dashboard.png)

**Hogyan tovább?**

* [Kérdéseket tehet fel a Q&A mezőben](consumer/end-user-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](consumer/end-user-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

## <a name="whats-included"></a>Tartalom
A tartalomcsomag a következő táblák adatait tartalmazza:  

    - Activity (Tevékenység)  
    - Agents (Ügynökök)  
    - Auth (Hitelesítés)  
    - Countries (Országok)  
    - CoursesProgress (Tanfolyamok haladása)  
    - Enrollments (Regisztrációk)
    - Lang (Nyelv)  
    - Platform  
    - Totals (Eredmények)  
    - UsersProgress (Felhasználók haladása)    

## <a name="system-requirements"></a>Rendszerkövetelmények
A tartalomcsomag példányának létrehozásához egy olyan IntelliBoard-fiók szükséges, amely rendelkezik engedélyekkel a fenti táblázatokhoz.

## <a name="next-steps"></a>Következő lépések
[Mi az a Power BI?](power-bi-overview.md)

[A Power BI szolgáltatás alapfogalmai tervezők számára](service-basic-concepts.md)

