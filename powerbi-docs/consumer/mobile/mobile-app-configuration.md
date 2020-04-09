---
title: A Power BI alkalmazáskonfigurációs beállításai
description: A Power BI viselkedésének testreszabása MDM-eszközzel
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 04/05/2020
ms.author: painbar
ms.openlocfilehash: ce147be4c23b738e1a09296a5d798fb0f94efe13
ms.sourcegitcommit: 9b806dfe62c2dee82d971bb4f89d983b97931b43
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/07/2020
ms.locfileid: "80802026"
---
# <a name="remotely-configure-power-bi-app-using-mobile-device-management-mdm-tool"></a>A Power BI alkalmazás távoli konfigurálása mobileszköz-kezelési (MDM-) eszközzel

Az iOS és az Android rendszerhez készült Power BI Mobile alkalmazás olyan beállításokat támogat, amelyekkel a mobileszköz-kezelési (MDM-) szolgáltatások – például az Intune – rendszergazdái testreszabhatják az alkalmazás viselkedését.

A Power BI Mobile alkalmazás a következő konfigurációs forgatókönyveket támogatja:

* Jelentéskészítő kiszolgáló konfigurálása (iOS és Android)
* Adatvédelmi beállítások (iOS és Android)
* Interakciós beállítások (iOS és Android)

## <a name="report-server-configuration-ios-and-android"></a>A jelentéskészítő kiszolgáló konfigurálása (iOS és Android)

Az iOS és Android rendszerhez készült Power BI alkalmazással a rendszergazdák távolról küldhetik le a Jelentéskészítő kiszolgáló konfigurációs beállításait a regisztrált eszközökre.

| Kulcs | Típus | Leírás |
|---|---|---|
| com.microsoft.powerbi.mobile.ServerURL | Sztring | Jelentéskészítő kiszolgáló URL-címe.<br><br>Http/https-sel kell kezdődnie.|
| com.microsoft.powerbi.mobile.ServerUsername | Sztring | [nem kötelező]<br><br>A kiszolgálóhoz való csatlakozáshoz használandó felhasználónév.<br><br>Ha még nem létezik ilyen, az alkalmazás kérni fogja a felhasználót, hogy adja meg a kapcsolathoz a felhasználónevet.|
| com.microsoft.powerbi.mobile.ServerDisplayName | Sztring | [nem kötelező]<br><br>Az alapértelmezett érték „Report server” („Jelentéskészítő kiszolgáló”)<br><br>Az alkalmazásban használt rövid név a kiszolgáló azonosítására. |
| com.microsoft.powerbi.mobile.OverrideServerDetails | Logikai érték | [nem kötelező]<br><br>Az alapértelmezett érték True (Igaz). Ha értéke True (Igaz), felülbírálja a Jelentéskészítő kiszolgálónak a mobileszközön lévő definícióját. A már konfigurált meglévő kiszolgálók törölve lesznek. A felülbírálás True értékre állítása azt is megakadályozza, hogy a felhasználó eltávolítsa ezt a konfigurációt.<br><br>Ha „False” (Hamis) értéket használ, akkor a leküldött értékek hozzáadódnak, a már meglévő beállítások pedig megmaradnak. Ha az adott kiszolgálói URL-cím már konfigurálva van a mobilalkalmazásban, akkor az alkalmazás ezt a konfigurációt változatlanul hagyja. Az alkalmazás nem kéri fel a felhasználót, hogy újra hitelesítse magát ugyanazon a kiszolgálón. |

## <a name="data-protection-settings-ios-and-android"></a>Adatvédelmi beállítások (iOS és Android)

Az iOS-hez és Androidhoz készült Power BI mobilalkalmazással a rendszergazdák testreszabhatják a biztonsági és adatvédelmi beállítások alapértelmezett konfigurációját. iOS rendszeren megkövetelheti a felhasználóktól, hogy Face ID-t, Touch ID-t vagy hitelesítő kódot használjanak a Power BI mobilalkalmazáshoz. Android rendszeren megkövetelheti a felhasználóktól, hogy biometrikus hitelesítést használjanak (ujjlenyomat-azonosító).

| Kulcs | Típus | Leírás |
|---|---|---|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | Logikai érték | Az alapértelmezett érték False (Hamis). <br><br>Az alkalmazás használatához megkövetelhető biometrikus adatok, például a TouchID vagy a FaceID (iOS) illetve ujjlenyomat-azonosító (Android) használata. Ez esetben ezekre is szükség van a hitelesítésen felül.<br><br>Alkalmazásvédelmi szabályzatok használata esetén a Microsoft azt javasolja, hogy tiltsa le ezt a beállítást, így elkerülhetők a kettős hozzáférési kérelmek. |

>[!NOTE]
>Az adatvédelmi beállítások csak a biometrikus hitelesítést támogató Android-eszközökön lesznek alkalmazva.

## <a name="interaction-settings-ios-and-android"></a>Interakciós beállítások (iOS és Android)

Az iOS-hez és Androidhoz készült Power BI alkalmazással a rendszergazdák konfigurálhatják a kezelési beállításokat, ha úgy döntenek, hogy az alapértelmezett kezelési beállításokat a felhasználók egy vállalaton belüli csoportja számára módosítani kell.

>[!NOTE]
>Jelenleg nem támogatott minden interakció az összes eszközön. A [Jelentések interakciós beállításainak konfigurálása](mobile-app-interaction-settings.md) részben talál egy olyan diagramot, amely felsorolja a jelenleg rendelkezésre álló eszközöket.

| Kulcs | Típus | Értékek | Leírás |
|---|---|---|---|
| com.microsoft.powerbi.mobile.ReportTapInteraction | Sztring |  <nobr>single-tap</nobr><br><nobr>double-tap</nobr> | Annak konfigurálása, hogy a vizualizáción való koppintás egyben adatpont-kiválasztás is legyen-e. |
| com.microsoft.powerbi.mobile.EnableMultiSelect | Logikai érték |  <nobr>True</nobr><br><nobr>False</nobr> | Konfigurálhatja, hogy egy adatpontra koppintás lecseréli-e az aktuális kijelölést, vagy az az aktuális kijelöléshez legyen hozzáadva. |
| com.microsoft.powerbi.mobile.RefreshAction | Sztring |  <nobr>pull-to-refresh</nobr><br>gombra | Annak konfigurálása, hogy a jelentés frissítéséhez rendelkezésre áll-e a felhasználónak egy gomb, vagy a frissítés húzással műveletet kell-e használnia. |
| com.microsoft.powerbi.mobile.FooterAppearance | Sztring |  docked<br>dynamic | Annak konfigurálása, hogy a jelentés lábléce a jelentés alján rögzített vagy automatikusan rejtett legyen-e. |

## <a name="deploying-app-configuration-settings"></a>Alkalmazáskonfigurációs beállítások bevezetése

Alkalmazáskonfigurációs szabályzatot az alábbi lépésekben hozhat létre. A konfigurációs szabályzat létrehozása után felhasználói csoportokhoz rendelheti annak beállításait.

1. Csatlakoztassa az MDM eszközt.
2. Hozzon létre egy új alkalmazáskonfigurálási szabályzatot, és nevezze el.
3. Válassza ki, hogy mely felhasználóknak szeretné terjeszteni ezt az alkalmazáskonfigurálási szabályzatot.
4. Hozzon létre kulcs-érték párokat a leküldeni kívánt beállításhoz.

Az Intune portál alkalmazáskonfigurációs szabályzataival a rendszergazdák könnyen üzembe helyezhetik ezeket a beállításokat a Power BI alkalmazásban. Azonban minden MDM-szolgáltató támogatott. Ha nem Intune-t használ, a beállítások üzembe helyezéséhez tekintse meg a használt MDM-megoldás dokumentációját.

## <a name="next-steps"></a>Következő lépések

* A Power BI mobilalkalmazás az [App Store-ból](https://apps.apple.com/app/microsoft-power-bi/id929738808) és a [Google Play áruházból](https://play.google.com/store/apps/details?id=com.microsoft.powerbim&amp;amp;clcid=0x409) szerezhető be
* Kövessen minket [@MSPowerBI a Twitteren](https://twitter.com/MSPowerBI)
* Csatlakozzon a beszélgetéshez a [Power BI-közösségben](https://community.powerbi.com/)
