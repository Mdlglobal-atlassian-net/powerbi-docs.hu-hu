---
title: Csatlakozás a Projectplace-hez a Power BI használatával
description: Projectplace a Power BI-hoz
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 9c98257ac352893d074ea91c27e8b1cf3d83e4a3
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61168800"
---
# <a name="connect-to-projectplace-by-planview-with-power-bi"></a>Csatlakozás a Planview Projectplace tartalomcsomagjához a Power BI használatával
A Planview Projectplace tartalomcsomagjának segítségével egészen újszerű módon, közvetlenül a Power BI-ban jelenítheti meg az együttműködésen alapuló projektadatokat. A Projectplace-hez használt bejelentkezési hitelesítő adataival interaktívan tekintheti meg a Projectplace-fiók összes projektjének kulcsfontosságú statisztikáit, láthatja a csoport legaktívabb és leghatékonyabb tagjait, és azonosíthatja a kockázatos besorolású kártyákat valamint tevékenységeket. Az Ön számára legfontosabb elemzések megjelenítéséhez kibővítheti az előregyártott irányítópultot és a jelentéseket.

[Csatlakozás a Projectplace tartalomcsomaghoz a Power BI-ban](https://app.powerbi.com/getdata/services/projectplace)

>[!NOTE]
>Ahhoz, hogy a Power BI-ba importálhassa Projectplace-adatait, Projectplace-felhasználónak kell lennie. A további követelményeket alább tekintheti meg.

## <a name="how-to-connect"></a>Csatlakozás
1. A bal oldali navigációs ablaktábla alján kattintson az **Adatok lekérése** elemre.
   
    ![](media/service-connect-to-projectplace/get.png)
2. A **Szolgáltatások** mezőben kattintson a **Beolvasás** elemre.
   
    ![](media/service-connect-to-projectplace/services.png)
3. A Power BI oldalon jelölje ki a **Projectplace by Planview** lehetőséget, majd kattintson a **Beolvasás** elemre:  
   
    ![](media/service-connect-to-projectplace/projectplace.png)
4. Az OData-adatcsatorna URL-címe szövegmezőbe írja be a használni kívánt Projectplace OData-adatcsatorna URL-címét az alábbi ábra szerint:
   
    ![](media/service-connect-to-projectplace/params.png)
5. A Hitelesítési módszer listán kattintson az **OAuth** elemre, ha még nincs kijelölve. Kattintson a **Bejelentkezés** gombra, és haladjon végig a bejelentkezés folyamatán.  
   
   ![](media/service-connect-to-projectplace/creds.png)
6. A bal oldali ablaktáblán, az irányítópultok listáján válassza ki a **Projectplace** lehetőséget. A Power BI az irányítópultba importálja a Projectplace adatait. Vegye figyelembe, hogy az adatok betöltése időbe telhet.  
   
    Az irányítópult csempéi megjelenítik a Projectplace adatbázisából származó adatokat. Az alábbi mintán egy Power BI-beli alapértelmezett Projectplace-irányítópult látható.
   
    ![](media/service-connect-to-projectplace/dashboard.png)

**Hogyan tovább?**

* [Kérdéseket tehet fel a Q&A mezőben](consumer/end-user-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](consumer/end-user-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

## <a name="system-requirements"></a>Rendszerkövetelmények
Ahhoz, hogy a Power BI-ba importálhassa Projectplace-adatait, Projectplace-felhasználónak kell lennie. Ez az eljárás feltételezi, hogy már bejelentkezett a Microsoft Power BI kezdőlapjára egy Power BI-fiókkal. Ha még nincs Power BI-fiókja, látogasson el a [powerbi.com](https://powerbi.microsoft.com/get-started/) webhelyre, és a **Power BI - Felhőbeli együttműködés és megosztás** területen válassza az **Ingyenes próba** lehetőséget. Ez után kattintson az **Adatok letöltése** lehetőségre.

## <a name="next-steps"></a>Következő lépések
[Mi az a Power BI?](power-bi-overview.md)

[Power BI – Alapfogalmak](consumer/end-user-basic-concepts.md)

