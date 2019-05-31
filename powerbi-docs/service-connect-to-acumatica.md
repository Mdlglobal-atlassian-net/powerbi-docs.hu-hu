---
title: Csatlakozás az Acumatica eszközhöz a Power BI-ban
description: Acumatica a Power BI-ban
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: aec463a4ce72f89f0cbbcf1bd42737605657a43c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61181158"
---
# <a name="connect-to-acumatica-with-power-bi"></a>Csatlakozás az Acumatica eszközhöz a Power BI-ban
A Power BI-hoz készült Acumatica tartalomcsomaggal gyors elemzéseket kaphat a lehetőségadatokról. A Power BI lekéri többek között a lehetőségek, a fiókok és az ügyfelek adatait, majd ezek alapján felépíti az alapértelmezett irányítópultot és a kapcsolódó jelentéseket.

Kapcsolódjon az [Acumatica tartalomcsomaghoz](https://app.powerbi.com/getdata/services/acumatica), vagy tájékozódjon bővebben az [Acumatica és a Power BI integrációjáról](https://powerbi.microsoft.com/integrations/acumatica).

>[!NOTE]
>Ehhez a tartalomcsomaghoz az Acumatica v5.2-es vagy újabb verziója szükséges.

## <a name="how-to-connect"></a>A csatlakozás menete
1. A bal oldali navigációs ablaktábla alján kattintson az **Adatok lekérése** elemre.
   
   ![](media/service-connect-to-acumatica/getdata3.png)
2. A **Szolgáltatások** mezőben kattintson a **Beolvasás** elemre.
   
   ![](media/service-connect-to-acumatica/getdata2.png)
3. Kattintson az **Acumatica** \> **Beolvasás** elemre.
   
   ![](media/service-connect-to-acumatica/acumatica.png)
4. Adja meg az Acumatica OData-végpontját. Az OData-végpont teszi lehetővé, hogy egy külső rendszer adatokat kérjen az Acumatica eszköztől. Az Acumatica OData-végpontja az alábbiak szerint van formázva, és HTTPS-t használ:
   
     `https://[sitedomain]/odata/[companyname]`
   
   A Cég neve adatra csak akkor van szükség, ha többvállalatos üzemelő példánnyal dolgozik. Az Acumatica-fiók ezen paraméterének megkereséséről alább talál további információkat.
   
   ![](media/service-connect-to-acumatica/parameters.png)
5. A Hitelesítési módszer beállításánál válassza az **Alapszintű** lehetőséget. Adja meg az Acumatica-fiókhoz tartozó felhasználónevét és a jelszavát, majd kattintson a **Bejelentkezés** elemre.
   
    ![](media/service-connect-to-acumatica/creds2.png)
6. Miután a Power BI importálta az adatokat, egy új irányítópult, jelentés és adatkészlet jelenik meg a bal oldali navigációs panelen. Az új elemeket sárga csillag jelöli \*, amely a rákattintás után eltűnik; az irányítópult kijelölése után az alábbi képhez hasonló elrendezés jelenik meg:
   
    ![](media/service-connect-to-acumatica/dashboard.png)

**Mi a következő lépés?**

* [Kérdéseket tehet fel a Q&A mezőben](consumer/end-user-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](consumer/end-user-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

## <a name="system-requirements"></a>Rendszerkövetelmények
Ehhez a tartalomcsomaghoz az Acumatica v5.2-es vagy újabb verziója szükséges, ezért kérjük, hogy ellenőrizze a verziót az Acumatica rendszergazdájának segítségével.

## <a name="finding-parameters"></a>Paraméterek keresése
**Acumatica OData-végpont**

Az Acumatica OData-végpontja az alábbiak szerint van formázva, és HTTPS-t használ:

    https://[sitedomain]/odata/[companyname]

Ha be van jelentkezve az Acumatica szolgáltatásba, az alkalmazástartomány a böngésző címsorában látható. Az alábbi példában a webhely tartománya `https://pbi.acumatica.com`, így a megadandó OData-végpont `https://pbi.acumatica.com/odata` lesz.

 ![](media/service-connect-to-acumatica/url.png)

A Cég neve adatra csak akkor van szükség, ha többvállalatos üzemelő példánnyal dolgozik. Ez az információ az Acumatica bejelentkezési oldalán található.

![](media/service-connect-to-acumatica/signin2.png)

## <a name="troubleshooting"></a>Hibaelhárítás
Ha nem tud bejelentkezni, ellenőrizze hogy a helyesen formázott Acumatica OData-végpontot adta-e meg.

    https://<application site domain>/odata/<company name>

Ha nem sikerül a csatlakozás, kérje a rendszergazda segítségét az Acumatica verziójának ellenőrzéséhez. Ehhez a tartalomcsomaghoz 5.2-es, vagy újabb verzióra van szükség.

## <a name="next-steps"></a>Következő lépések
[Első lépések a Power BI-ban](service-get-started.md)

[Adatok lekérése a Power BI-ban](service-get-data.md)

