---
title: Csatlakozás a Webtrends eszközhöz a Power BI használatával
description: A Power BI-hoz készült Webtrends
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: e24e6f86cddcf328497c050f82612d36efa3a4ed
ms.sourcegitcommit: 762857c8ca09ce222cc3f8b006fa1b65d11e4ace
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66720494"
---
# <a name="connect-to-webtrends-with-power-bi"></a>Csatlakozás a Webtrends eszközhöz a Power BI használatával
A Power BI Webtrends-tartalomcsomagja számos azonnal használatba vehető metrikát tartalmaz, így például az összes oldalmegtekintést és az adatforgalmi forrás szerinti látogatásokat. A Webtrends-adatok Power BI-ben történő vizualizációja a Webtrends-fiókhoz való csatlakozással kezdődik. Használhatja a mellékelt irányítópultot és jelentéseket, vagy testre szabhatja őket úgy, hogy az Ön számára legfontosabb adatokat emeljék ki.  Az adatok naponta egyszer automatikusan frissülnek.

Kapcsolódjon a [Power BI Webtrends-tartalomcsomagjához](https://app.powerbi.com/getdata/services/webtrends).

## <a name="how-to-connect"></a>Csatlakozás
1. A bal oldali navigációs ablaktábla alján kattintson az **Adatok lekérése** elemre.
   
   ![](media/service-connect-to-webtrends/getdata3.png)
2. A **Szolgáltatások** mezőben kattintson a **Lekérés** elemre.
   
   ![](media/service-connect-to-webtrends/services.png)
3. Válassza a **Webtrends** \> **Lekérés** lehetőséget.
   
   ![](media/service-connect-to-webtrends/webtrends.png)
4. A tartalomcsomag egy adott Webtrends-profilazonosítóhoz kapcsolódik. [E paraméter megkeresésének](#FindingParams) részleteit alább találja.
   
   ![](media/service-connect-to-webtrends/parameters.png)
5. A csatlakozáshoz adja meg Webtrends hitelesítő adatait. Vegye figyelembe, hogy a felhasználónév mezőbe a fiók- és a felhasználónevet kell beírni. A [részletes információkat](#FindingParams) alább találja.
   
   ![](media/service-connect-to-webtrends/creds.png)
6. A jóváhagyás után automatikusan megkezdődik az importálási folyamat. Ha befejeződött, a navigációs panelen megjelenik egy új irányítópult, jelentés és modell. Válassza ki az irányítópultot az importált adatok megtekintéséhez.
   
   ![](media/service-connect-to-webtrends/dashboard.png)

**Mi a következő lépés?**

* [Kérdéseket tehet fel a Q&A mezőben](consumer/end-user-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](consumer/end-user-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

## <a name="whats-included"></a>Tartalom
<a name="Included"></a>

A Webtrends-tartalomcsomag a következő jelentésekből kér le adatokat:  

| Jelentés neve | Jelentésazonosító |
| --- | --- |
| Fő mérőszámok | |
| Helyi keresések |34awBVEP0P6 |
| Kilépési oldalak |7FshY8eP0P6 |
| Következő oldalak |CTd5rpeP0P6 |
| Előző oldalak |aSdOeaUgnP6 |
| Webhely oldalai |oOEWQj3sUo6 |
| Helyi átkattintós hirdetések |41df19b6d9f |
| Városok |aUuHskcP0P6 |
| Országok |JHWXJNcP0P6 |
| Látogatók |xPcmTDDP0P6 |
| Látogatás időtartama |U5KAyqdP0P6 |
| Keresőkifejezések |IKYEDxIP0P6 |
| Adatforgalmi források |JmttAoIP0P6 |
| Keresőmotorok |yGz3gAGP0P6 |
| Belépési oldalak |i6LrkNVRUo6 |

>[!NOTE]
>SharePoint-profilok esetében a metrikák nevei kissé eltérhetnek a Webtrends felhasználói felületén megjelenő nevektől. A következő társítás a SharePoint és a webes profilok közötti konzisztencia megtartása érdekében történik:   

    - Munkamenetek = Látogatások  
    - Új felhasználók = Új látogatók  
    - Munkamenetenkénti megtekintések száma = Látogatásonkénti oldalmegtekintések száma  
    - Átlagos napi felhasználói időtartam = Látogatónkénti átlagos webhelyen töltött idő  

## <a name="system-requirements"></a>Rendszerkövetelmények
A tartalomcsomagnak hozzáféréssel kell rendelkeznie ahhoz a Webtrends-profilhoz, amelyen a [megfelelő jelentéskészlet](#Included) engedélyezve van.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Paraméterek helye
A Webtrends-profilazonosító a profil kiválasztása után megtalálható az URL-címben:

![](media/service-connect-to-webtrends/webtrendsparameters.png)

A hitelesítő adatok ugyanazok, mint amelyeket a Webtrendsbe történő bejelentkezéskor kell megadnia, azonban a fiók- és a felhasználónevet ugyanabba a sorba kell beírni, fordított perjellel elválasztva:

![](media/service-connect-to-webtrends/webtrendscreds.png)

## <a name="troubleshooting"></a>Hibaelhárítás
A tartalomcsomag betöltése közben, a hitelesítő adatok megadása után problémát tapasztalhat. Ha betöltés közben a „Hoppá” üzenetet látja, tekintse meg az alábbi hibaelhárítási javaslatokat. Ha továbbra is problémákat tapasztal, küldjön támogatási jegyet a https://support.powerbi.com címen.

1. A megfelelő profilazonosítót használja, további részletekért lásd: [Paraméterek keresése](#FindingParams).
2. A felhasználó hozzáféréssel rendelkezik a [„Tartalom”](#Included) szakaszban felsorolt jelentésekhez

## <a name="next-steps"></a>Következő lépések
[Mi az a Power BI?](power-bi-overview.md)

[A Power BI szolgáltatás alapfogalmai tervezők számára](service-basic-concepts.md)

