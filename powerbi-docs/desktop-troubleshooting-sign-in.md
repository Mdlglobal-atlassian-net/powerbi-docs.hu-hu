---
title: Bejelentkezési problémák elhárítása a Power BI Desktopban
description: Gyakori Power BI Desktop bejelentkezési problémák megoldása
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: f8ceeddea7a8a9b7a63043cc7e91269da570790b
ms.sourcegitcommit: 2ae660a7b70fce23eb58b159d049eca44a664f2c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/30/2018
ms.locfileid: "52670990"
---
# <a name="troubleshooting-sign-in-for-power-bi-desktop"></a>Bejelentkezés hibaelhárítása a Power BI Desktopban
Előfordulhat, hogy amikor megkísérel bejelentkezni a **Power BI Desktopba**, hibát tapasztal. A bejelentkezési hibáknak két fő oka lehet: **proxy-hitelesítési hibák** és **Nem-HTTPS URL-cím átirányítási hibái**. 

A bejelentkezési hiba okának megállapításához az első lépés kapcsolatba lépni a rendszergazdával, aki megadja a probléma okának meghatározásához szükséges diagnosztikai információkat. A bejelentkezési problémához tartozó hibák nyomon követésével a rendszergazdák el tudják dönteni, hogy a következő hibák melyike következett be Önnél. 

Vegyük sorra ezeket a hibákat. Ennek a cikknek a vége a *nyomkövetési* adatok Power BI-beli rögzítését tárgyalja, amely a problémák felderítésében segíthet.


## <a name="proxy-authentication-required-error"></a>Hiba: Proxyhitelesítés szükséges

A következő képernyőkép a *Proxyhitelesítés szükséges* hibára mutat egy példát.

![Bejelentkezési hiba proxyhitelesítési hiba miatt](media/desktop-troubleshooting-sign-in/desktop-tshoot-sign-in_01.png)

A *Power BI Desktop* nyomkövetési fájljaiban a következő hibák társulnak ehhez a hibához:

* *Microsoft.PowerBI.Client.Windows.Services.PowerBIWebException*
* *HttpStatusCode: ProxyAuthenticationRequired*

Ilyen hiba esetén a legvalószínűbb ok az, hogy a hálózat proxyhitelesítő kiszolgálója blokkolja a **Power BI Desktop** által kiadott webkérelmeket. 

Ha a hálózata proxyhitelesítő kiszolgálót használ, akkor a rendszergazda tudja megoldani ezt a problémát a következő tartományok engedélyezésével a proxyhitelesítő kiszolgálón:

* app.powerbi.com
* api.powerbi.com
* a *.analysis.windows.net névtérben lévő tartományok

A kormányzati felhőhöz tartozó ügyfelek esetében a hiba a következő tartományoknak a proxyhitelesítő kiszolgálón való engedélyezésével oldható meg:

* app.powerbigov.us
* api.powerbigov.us
* a *.analysis.usgovcloudapi.net névtérben lévő tartományok

## <a name="non-https-url-redirect-not-supported-error"></a>Hiba: Nem-HTTPS URL-címekre való átirányítás nem támogatott

A **Power BI Desktop** jelenlegi verziói az Active Directory hitelesítési tár (ADAL) aktuális verzióját használják, amely nem támogatja a nem biztonságos (nem-HTTPS) URL-címekre való átirányítást. 

A *Power BI Desktop* nyomkövetési fájljaiban a következő hibák társulnak ehhez a hibához:

* *Microsoft.IdentityModel.Clients.ActiveDirectory.AdalServiceException: Non-HTTPS url redirect is not supported in webview*
* *ErrorCode: non_https_redirect_failed*

Az *ErrorCode: non_https_redirect_failed* előfordulása azt jelenti, hogy az átirányítási láncban egy vagy több oldal vagy szolgáltató nem HTTPS-védelmű végpont, vagy hogy egy vagy több átirányítás tanúsítványának kibocsátója nem szerepel az eszköz megbízható főtanúsítványai között. A bejelentkezéses átirányítási láncban minden szolgáltatónak HTTPS URL-címet kell használnia. A probléma megoldásához forduljon a rendszergazdához, és kérje, hogy a hitelesítő webhelyeken biztonságos URL-címet használjanak. 

## <a name="how-to-collect-a-trace-in-power-bi-desktop"></a>Nyomkövetési adatok gyűjtése a Power BI Desktopban

Nyomkövetési adatok a következő lépésekkel gyűjthetők a **Power BI Desktopban**:

1. A nyomkövetés a **Power BI Desktopban** a **File > Lehetőségek és beállítások > Beállítások**, majd a bal oldali panel lehetőségei közül a **Diagnosztika** választásával engedélyezhető. A megjelenő panelen jelölje be a következő képen látható **Nyomkövetés engedélyezése** lehetőség melletti jelölőnégyzetet. Lehetséges, hogy újra kell indítania a **Power BI Desktopot**.
   
   ![Nyomkövetés engedélyezése a Power BI Desktopban](media/desktop-troubleshooting-sign-in/desktop-tshoot-sign-in_02.png)

2. Ismételje meg a hibához vezető lépéseket. Amikor bekövetkezik, a **Power BI Desktop** hozzáírja az eseményeket a helyszíni számítógépen tárolt nyomkövetési naplóhoz.

3. Keresse meg a Nyomkövetési adatok (Traces) mappát a számítógépen. A mappára mutató hivatkozás megtalálható a **Diagnosztika** panelen, ahol a nyomkövetést engedélyezte. A fenti képen *Open crash dump/traces folder* (összeomlási memóriakép/nyomkövetési adatok mappa megnyitása) formában látható. A helyszíni számítógépen ez gyakran a következő helyen található:

    `C:\Users/<user name>/AppData/Local/Microsoft/Power BI Desktop/Traces`

A mappa sok nyomkövetési fájlt tartalmazhat. A rendszergazdának csak az utolsó fájlokat küldje el, hogy gyorsan azonosíthassa a hibát. 

