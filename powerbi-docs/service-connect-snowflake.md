---
title: Kapcsolódás a Snowflake-hez a Power BI-jal
description: Snowflake használata egyszeri bejelentkezéssel a Power BI-ban
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/20/2019
ms.author: gepopell
LocalizationGroup: Connect to services
ms.openlocfilehash: 5e5519e30be30d6367791d1b6822196b407a21b1
ms.sourcegitcommit: 4d98274aa0b9aa09db99add2dda91a3ba8fed40b
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576873"
---
#  <a name="connecting-to-snowflake-in-power-bi-service"></a>Kapcsolódás a Snowflake-hez a Power BI szolgáltatásban

## <a name="introduction"></a>Bevezetés

A Snowflake-hez való kapcsolódás a Power BI szolgáltatás egyedül abban különbözik a többi összekötőtől, hogy egy további képességet kínál az AAD-hez (az egyszeri bejelentkezés lehetőségével). Az integráció különböző részeihez más-más adminisztratív szerepkörök szükségesek a Snowflake-ben, a Power BI-ban és az Azure-ban. Úgy is dönthet, hogy SSO nélkül engedélyezi az AAD-hitelesítést. Az alapszintű hitelesítés a szolgáltatáson belüli többi összekötőhöz hasonlóan működik.

Ha érdekli az AAD-integráció konfigurálása és az egyszeri bejelentkezés (SSO) választható engedélyezése:
* Ha Ön Snowflake-rendszergazda, olvassa el a Snowflake dokumentációjának [Power BI SSO to Snowflake - Getting Started](https://docs.snowflake.net/manuals/LIMITEDACCESS/oauth-powerbi.html) című cikkét.
* (SSO) Ha Ön Power BI-rendszergazda, olvassa el „A Power BI szolgáltatás konfigurálása – Felügyeleti portál” szakaszt
* (SSO) Ha Ön adathalmaz-készítő a Power BI-ban, olvassa el „A Power BI szolgáltatás konfigurálása – Adathalmaz engedélyezése” szakaszt

## <a name="power-bi-service-configuration"></a>A Power BI szolgáltatás konfigurálása

### <a name="admin-portal"></a>Felügyeleti portál

Ha engedélyezni szeretné az egyszeri bejelentkezést (SSO), a bérlői rendszergazdának meg kell nyitnia a Felügyeleti portált, és jóvá kell hagynia az AAD-beli Power BI hitelesítő adatok elküldését a Snowflake-nek.

![A Snowflake SSO bérlői rendszergazdai beállításai](media/service-connect-snowflake/snowflakessotenant.png)

Lépjen a „Felügyeleti portálra”, válassza az oldalsáv „Bérlői beállítások” elemét, görgessen le az „Integrációs beállításokig”, ahol a „Snowflake SSO” beállítása található.

A figyelmeztetésnek megfelelően ezt manuálisan kell engedélyeznie, ezzel hozzájárulva, hogy az AAD-jogkivonat elküldését a Snowflake-kiszolgálókhoz. Ennek engedélyezéshez kattintson a „Letiltva” váltókapcsolóra, válassza az Alkalmazás lehetőséget, és várjon, amíg a beállítás módosítása érvénybe lép. Egy órát is igénybe vehet, hogy a szolgáltatás továbbadja a konfigurációt.

Miután ez befejeződik, SSO-val használhat jelentéseket.

### <a name="configuring-a-dataset-with-aad"></a>Adathalmaz konfigurálása AAD-vel

Miután a Snowflake-összekötőn alapuló jelentés közzé lett téve a weben, az adathalmaz készítőjének a megfelelő munkaterületre kell navigálnia a Power BI szolgáltatásban, ahol az „Adathalmazok”, majd a „Beállítások” lehetőséget kell választania (az adott adathalmaz mellett található, további lehetőségeket kínáló „...” menüben).

A Power BI működési módja miatt az SSO csak akkor működik, ha egy adatforrás sincs a helyszíni adatátjárón keresztül futtatva.

* Ha az adatmodellben csak Snowflake-forrást használ, abban az esetben használhat SSO-t, ha úgy dönt, hogy nem használja a helyszíni adatátjárót
* Ha egy Snowflake-forrást más forrás mellett használ, abban az estben használhat SSO-t, ha a források egyike sem használja a helyszíni adatátjárót
* Amennyiben a helyszíni adatátjárón keresztül használ egy Snowflake-forrást, nem adhat meg Azure Active Directory-fiókhoz tartozó hitelesítő adatokat. Ez olyan esetben lehet lényeges, amikor egy virtuális hálózatot nem a teljes Power BI-címtartományból, hanem egyetlen IP-címről próbál elérni, amelyen telepítve van az átjáró.
* Ha egy Snowflake-forrást olyan forrás mellett használ, amely átjárót igényel, a Snowflake-et is a helyszíni adatátjárón keresztül kel használnia, és nem használhat SSO-t.

A helyszíni adatátjáró használatáról a [Mi az a helyszíni adatátjáró?](https://docs.microsoft.com/power-bi/service-gateway-onprem) című cikkben talál további információt.

Ha nem használja az átjárót, akkor minden készen áll. Ha Snowflake-beli hitelessítő adatok vannak konfigurálva a helyszíni adatátjárón, de ezt az adatforrást csak a modellben használja, az Adathalmaz beállításai oldalon a váltógombra kattintva kikapcsolhatja az átjárót ehhez az adatmodellhez.

![Adathalmaz-beállítás az átjáró kikapcsolására](media/service-connect-snowflake/snowflake_gateway_toggle_off.png)

Az adathalmaz készítőjének be kell jelentkeznie az „Adatforrásbeli hitelesítő adatok” lehetőséget választva. Az adathalmaz alapszintű hitelesítő adatokkal vagy OAuth2 (AAD) hitelesítő adatokkal jelentkeztethető be a Snowflake-be. Ha az AAD használata mellett dönt, az adathalmazhoz engedélyezhető az SSO használata. Amikor ez az első felhasználó bejelentkezik a Snowflake-be az adathalmazhoz, azt a beállítást kell választania, hogy más felhasználók az Oauth2 hitelesítő adatok használatával kérhetnek le adatokat. Ezzel engedélyezi az AAD SSO-t. Függetlenül attól, hogy az első felhasználó alapszintű vagy OAuth2 (AAD) hitelesítéssel jelentkezik be, az egyszeri bejelentkezéshez az AAD-beli hitelesítő adatok lesznek elküldve. 

![Adathalmaz-beállítások Snowflake-beli egyszeri bejelentkezéshez](media/service-connect-snowflake/snowflakessocredui.png)

Ezt követően a további felhasználók automatikusan saját AAD-beli hitelesítéssel csatlakoznak a Snowflake-adathalmazból származó adatokhoz.

Ha úgy dönt, hogy nem engedélyezi az egyszeri bejelentkezést, a jelentést frissítő felhasználók a bejelentkezett felhasználó hitelesítő adatait fogják használni, mint a többi Power BI-jelentés többsége esetében.

### <a name="troubleshooting"></a>Hibaelhárítás

Ha az integrációval kapcsolatos problémát tapasztal, kövesse a Snowflake [hibaelhárítási útmutatóját](https://docs.snowflake.net/manuals/LIMITEDACCESS/oauth-powerbi.html#troubleshooting).

