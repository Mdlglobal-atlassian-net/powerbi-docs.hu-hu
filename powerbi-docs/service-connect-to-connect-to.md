---
title: Csatlakozás a comScore Digital Analytix eszközhöz a Power BI használatával
description: comScore Digital Analytix a Power BI-hoz
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 01/30/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 49ac1f917a5f3095c1dbc13c644061859389fe74
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61174770"
---
# <a name="connect-to-comscore-digital-analytix-with-power-bi"></a>Csatlakozás a comScore Digital Analytix eszközhöz a Power BI használatával
A Power BI-tartalomcsomag segítségével a Power BI-ban jelenítheti meg és elemezheti a comScore Digital Analytix adatait. Az adatok naponta egyszer automatikusan frissülnek.

Csatlakozzon a [Power BI-hoz készült comScore-tartalomcsomaghoz.](https://app.powerbi.com/getdata/services/comscore)

>[!NOTE]
>A tartalomcsomaghoz történő csatlakozáshoz szüksége van egy comScore DAx felhasználói fiókra, valamint hozzáféréssel kell rendelkeznie a comScore API-hoz. A [részleteket](#Requirements) alább találja.

## <a name="how-to-connect"></a>A csatlakozás menete
1. Válassza az Adatok lekérése elemet a bal oldalon lévő navigációs ablaktábla alján.
   
   ![](media/service-connect-to-connect-to/getdata.png)
2. A **Szolgáltatások** mezőben válasza a **Beolvasás** elemet.
   
   ![](media/service-connect-to-connect-to/services.png)
3. Kattintson a **comScore Digital Analytix** \> **Get** elemre.
   
   ![](media/service-connect-to-connect-to/comscore.png)
4. Adja meg az adatközpontot, a comScore ügyfél-azonosítót és azt a webhelyet, amelyhez kapcsolódni szeretne. A felsorolt adatok megtalálásáról lejjebb, a [comScore-paraméterek keresése](#FindingParams) részben tájékozódhat.
   
   ![](media/service-connect-to-connect-to/parameters.png)
5. A csatlakozáshoz adja meg comScore-felhasználónevét és -jelszavát. Az adat megtalálásáról lejjebb tájékozódhat.
   
   ![](media/service-connect-to-connect-to/creds.png)
6. Az importálási folyamat automatikusan elindul. Ha befejeződött, a navigációs panelen megjelenik egy új irányítópult, jelentés és modell. Válassza ki az irányítópultot az importált adatok megtekintéséhez.

**Mi a következő lépés?**

* [Kérdéseket tehet fel a Q&A mezőben](consumer/end-user-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](consumer/end-user-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

<a name="Requirements"></a>

## <a name="system-requirements"></a>Rendszerkövetelmények
A kapcsolódáshoz comScore DAx felhasználói fiókkal és comScore DAx API-hoz való hozzáféréssel kell rendelkeznie. Kérjük, forduljon a comScore DAx-rendszergazdához a fiók megerősítéséhez.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Paraméterek keresése
Az alábbiakban olvashatók a comScore-paraméterek megkereséséhez szükséges információk.

**Adatközpont**

A csatlakoztatott adatközpontot a comScore-ból elért URL-cím határozza meg.

![](media/service-connect-to-connect-to/comscore_url.png) 

**Ügyfél**

Az Ügyfél ugyanaz, mint amit a comScore DAx szolgáltatásba történő bejelentkezéskor ad meg.

![](media/service-connect-to-connect-to/comscore_signin.png) 

**Webhely**

A comScore-webhely azt határozza meg, hogy melyik webhelyről érkező adatokat kívánja megtekinteni. A comScore-fiókból elérheti a webhelyek listáját.

![](media/service-connect-to-connect-to/comscore_sites.png)

## <a name="next-steps"></a>További lépések
[Első lépések a Power BI-ban](service-get-started.md)

[Adatok lekérése a Power BI-ban](service-get-data.md)

