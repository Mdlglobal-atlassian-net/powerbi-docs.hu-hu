---
title: Csatlakozás a Stripe-hoz a Power BI segítségével
description: Power BI Stripe
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: b0e8739e93d24ba10b0ffc72042b847cce1d5fe9
ms.sourcegitcommit: d441d350504f8c6d9e100d229757add6237f0bef
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/30/2019
ms.locfileid: "73060768"
---
# <a name="connect-to-stripe-with-power-bi"></a>Csatlakozás a Stripe-hoz a Power BI segítségével
A Power BI-tartalomcsomag segítségével megtekintheti és elemezheti Stripe-adatait. A Power BI Stripe-tartalomcsomag adatokat nyer ki ügyfelekről, díjakról, eseményekről és számlákról. Az adatok a legutóbbi tízezer eseményre és ötezer díjtételre vonatkoznak az utolsó 30 napra kiterjedően. A tartalom naponta egyszer automatikusan frissül az Ön által beállított ütemezés szerint. 

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Kapcsolódás a [Power BI Stripe-tartalomcsomaghoz](https://app.powerbi.com/getdata/services/stripe).

## <a name="how-to-connect"></a>A kapcsolódás menete
1. Válassza az Adatok lekérése elemet a bal oldalon lévő navigációs ablaktábla alján.  
   
    ![](media/service-connect-to-stripe/getdata.png)
2. A **Szolgáltatások** mezőben válasza a **Beolvasás** elemet.  
   
    ![](media/service-connect-to-stripe/services.png)  
3. Válassza a **Stripe** &gt; **Letöltés most** elemet.  
   
    ![](media/service-connect-to-stripe/stripe.png)  
4. A kapcsolódáshoz adja meg a Stripe-[API-kulcsát](https://dashboard.stripe.com/account/apikeys).  
   
    ![](media/service-connect-to-stripe/creds.png)
5. Az importálás automatikusan megkezdődik. Amikor befejeződik, a navigációs ablaktáblán megjelenik az új irányítópult, jelentés és modell, egy csillaggal jelölve. Az importált adatok megtekintéséhez kattintson az irányítópultra.
   
    ![](media/service-connect-to-stripe/dashboard.png)

**Mi a következő lépés?**

* [Kérdéseket tehet fel a Q&A mezőben](consumer/end-user-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](consumer/end-user-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

## <a name="next-steps"></a>Következő lépések
[Mi az a Power BI?](fundamentals/power-bi-overview.md)

[Power BI – Adatok lekérése](service-get-data.md)

