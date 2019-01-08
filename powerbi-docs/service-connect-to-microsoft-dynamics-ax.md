---
title: Csatlakozás a Power BI-ból a Microsoft Dynamics AX tartalomcsomaghoz
description: Microsoft Dynamics AX tartalomcsomag a Power BI szolgáltatáshoz
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 688f0e9bc1070c1cd9605a508d2086f52f7e5730
ms.sourcegitcommit: 750f0bfab02af24c8c72e6e9bbdd876e4a7399de
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/04/2019
ms.locfileid: "54008120"
---
# <a name="connect-to-microsoft-dynamics-ax-content-pack-with-power-bi"></a>Csatlakozás a Power BI-ból a Microsoft Dynamics AX tartalomcsomaghoz
A Microsoft Dynamics AX három Power BI-hez készült tartalomcsomaggal rendelkezik, különböző üzleti felhasználók számára. A Financial Performance tartalomcsomag, amely kifejezetten pénzügyi vezetőknek lett kifejlesztve, a szervezet pénzügyi teljesítményébe enged betekintést. A csatornafelelősök számára kialakított Retail Channel Performance tartalomcsomag az eladási teljesítményre összpontosítva, a kiskereskedelmi és kereskedelmi adatok elemzésével értékes információkat nyújt és segít előrejelezni a trendeket. A vezérigazgatók és pénzügyi vezetők számára kialakított Cost Management tartalomcsomag a műveleti teljesítményről szolgáltat részletes adatokat.

Kapcsolódjon a Power BI-kompatibilis Microsoft Dynamics AX-tartalomcsomagok egyikéhez: a [Retail Channel Performance](https://app.powerbi.com/getdata/services/dynamics-ax-retail-channel-performance), a [Financial Performance](https://app.powerbi.com/getdata/services/dynamics-ax-financial-performance) vagy a [Cost Management](https://app.powerbi.com/getdata/services/dynamics-ax-cost-management) tartalomcsomaghoz.

## <a name="how-to-connect"></a>A kapcsolódás menete
1. A bal oldali navigációs ablaktábla alján kattintson az **Adatok lekérése** elemre.
   
   ![](media/service-connect-to-microsoft-dynamics-ax/getdata.png)
2. A **Szolgáltatások** mezőben kattintson a **Beolvasás** elemre.
   
   ![](media/service-connect-to-microsoft-dynamics-ax/services.png)
3. Válasszon egy Dynamics AX-tartalomcsomagot, és kattintson a **Beolvasás** elemre.
   
   ![](media/service-connect-to-microsoft-dynamics-ax/mdax.png)
4. Adja meg a Dynamics AX 7-környezet URL-címét. A [paraméterek megkereséséről](#FindingParams) alább olvashat részletesebben.
   
   ![](media/service-connect-to-microsoft-dynamics-ax/params.png)
5. A **Hitelesítési módszer** beállításánál válassza az **oAuth2** \> **Bejelentkezés** lehetőséget. Amikor a rendszer kéri, adja meg a Dynamics AX-fiók hitelesítő adatait.
   
    ![](media/service-connect-to-microsoft-dynamics-ax/creds.png)
   
    ![](media/service-connect-to-microsoft-dynamics-ax/creds2.png)
6. A jóváhagyás után automatikusan megkezdődik az importálás. Ha befejeződött, a navigációs panelen megjelenik egy új irányítópult, jelentés és modell. Válassza ki az irányítópultot az importált adatok megtekintéséhez.
   
     ![](media/service-connect-to-microsoft-dynamics-ax/dashboard.png)

**Mi a következő lépés?**

* [Kérdéseket tehet fel a Q&A mezőben](consumer/end-user-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](consumer/end-user-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

## <a name="whats-included"></a>Tartalom
A tartalomcsomag a Dynamics AX 7 OData-csatornájából importálja a Retail Channel, a Financial, vagy a Cost Management tartalomcsomag adatait.

## <a name="system-requirements"></a>Rendszerkövetelmények
A tartalomcsomaghoz egy Dynamics AX 7-környezet URL-címe szükséges, valamint felhasználói hozzáférés az OData-csatornához.

## <a name="finding-parameters"></a>Paraméretek keresése
<a name="FindingParams"></a>

A Dynamics AX 7-környezet URL-címe a böngészőben található a felhasználó bejelentkezése után. Csak másolja be a Dynamics AX-gyökérkörnyezet URL-címét a Power BI párbeszédpanelébe.

## <a name="troubleshooting"></a>Hibaelhárítás
Az adatok betöltése a példány méretétől függően időbe telhet. Ha a Power BI szolgáltatásban üres jelentéseket lát, ellenőrizze, hogy hozzáfér-e a jelentésekhez szükséges OData-táblázatokhoz.

## <a name="next-steps"></a>Következő lépések
[Első lépések a Power BI-ban](service-get-started.md)

[Adatok lekérése a Power BI-ban](service-get-data.md)

