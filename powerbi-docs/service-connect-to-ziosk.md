---
title: Kapcsolódás a Ziosk Survey Analytics szolgáltatáshoz a Power BI-t használva
description: A Power BI-hoz készült Ziosk
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: d22f67f52d0abe0621e244874def845c7d25c15b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61138514"
---
# <a name="connect-to-ziosk-survey-analytics-with-power-bi"></a>Kapcsolódás a Ziosk Survey Analytics szolgáltatáshoz a Power BI-t használva
A Power BI-hoz készített Ziosk Survey Analytics tartalomcsomag Ziosk táblagépekkel használva egyedülálló módon tárja az éttermek elé a Ziosk felmérések adataiból felismerhető összefüggéseket, többek között nap, hely és alkalmazott szerint is szegmentálva.

Kapcsolódjon a Power BI-hoz készített [Ziosk Survey Analytics tartalomcsomaghoz](https://app.powerbi.com/getdata/services/ziosk-survey-analytics).

## <a name="how-to-connect"></a>A kapcsolódás menete
1. A bal oldali navigációs ablaktábla alján kattintson az **Adatok lekérése** elemre.  
   
    ![](media/service-connect-to-ziosk/getdata.png)
2. A **Szolgáltatások** mezőben kattintson a **Beolvasás** gombra.  
   
    ![](media/service-connect-to-ziosk/services.png)
3. Kattintson a **Ziosk Survey Analytics**, majd a **Beolvasás** lehetőségre.  
   
    ![](media/service-connect-to-ziosk/ziosk.png)
4. Válassza ki az **OAuth 2**, majd a **Bejelentkezés** lehetőséget. Amikor a rendszer kéri, adja meg az Ziosk-fiókja hitelesítő adatait.
   
    ![](media/service-connect-to-ziosk/creds.png)
   
    ![](media/service-connect-to-ziosk/creds2.png)
5. A kapcsolódás után automatikusan betöltődik egy irányítópult, egy jelentés és egy adatkészlet. A befejezést követően a csempék frissülni fognak az Ön Ziosk-fiókjából származó adatokkal.
   
    ![](media/service-connect-to-ziosk/dashboard.png)

**Hogyan tovább?**

* [Kérdéseket tehet fel a Q&A mezőben](consumer/end-user-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](consumer/end-user-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

## <a name="whats-included"></a>Tartalom
A tartalomcsomag a következő táblák adatait tartalmazza:  

    - Alkohol kategória  
    - Előétel kategória  
    - CommentKeywords  
    - Dátum  
    - Napszak  
    - Desszert kategória  
    - Freeform  
    - Gyerek kategória  
    - Üzenetek  
    - Prémium tartalom kategória  
    - Kérdés  
    - Áruház  
    - Felmérések  
    - Hétköznap  


## <a name="system-requirements"></a>Rendszerkövetelmények
A tartalomcsomag példányának létrehozásához egy olyan Ziosk-fiók szükséges, amely rendelkezik engedélyekkel a fenti táblázatokhoz.

## <a name="next-steps"></a>Következő lépések
[Mi az a Power BI?](power-bi-overview.md)

[Power BI – Alapfogalmak](consumer/end-user-basic-concepts.md)

