---
title: A Power BI alkalmazáskonfigurációs beállításai
description: A Power BI viselkedésének testreszabása MDM-eszközzel
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 11/07/2019
ms.author: painbar
ms.openlocfilehash: a517ee4edce6e18eadcbe2b1b6765684f8121b21
ms.sourcegitcommit: 768e1e4b19fe8c7627010127c2420d63021cb542
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/20/2019
ms.locfileid: "74199424"
---
# <a name="remotely-configure-power-bi-app-using-mobile-device-management-mdm-tool"></a>A Power BI alkalmazás távoli konfigurálása mobileszköz-kezelési (MDM-) eszközzel

Az iOS és Android rendszerhez készült Power BI Mobile alkalmazás olyan beállításokat támogat, amelyekkel az Office 365 és a mobileszköz-kezelési (MDM-) szolgáltatások – például az Intune – rendszergazdái testreszabhatják az alkalmazás viselkedését.

A Power BI Mobile alkalmazás a következő konfigurációs forgatókönyveket támogatja:

- Jelentéskészítő kiszolgáló konfigurálása (iOS és Android)
- Adatvédelmi beállítások (iOS)

## <a name="report-server-configuration-ios-and-android"></a>A jelentéskészítő kiszolgáló konfigurálása (iOS és Android)

Az iOS és Android rendszerhez készült Power BI alkalmazással a rendszergazdák távolról küldhetik le a Jelentéskészítő kiszolgáló konfigurációs beállításait a regisztrált eszközökre.

| Kulcs | Típus | Leírás |
|---|---|---|
| com.microsoft.powerbi.mobile.ServerURL | Sztring | Jelentéskészítő kiszolgáló URL-címe.<br><br>Http/https-sel kell kezdődnie.|
| com.microsoft.powerbi.mobile.ServerUsername | Sztring | [nem kötelező]<br><br>A kiszolgálóhoz való csatlakozáshoz használandó felhasználónév.<br><br>Ha még nem létezik ilyen, az alkalmazás kérni fogja a felhasználót, hogy adja meg a kapcsolathoz a felhasználónevet.|
| com.microsoft.powerbi.mobile.ServerDisplayName | Sztring | [nem kötelező]<br><br>Az alapértelmezett érték „Report server” („Jelentéskészítő kiszolgáló”)<br><br>Az alkalmazásban használt rövid név a kiszolgáló azonosítására. |
| com.microsoft.powerbi.mobile.OverrideServerDetails | Logikai érték | [nem kötelező]<br><br>Az alapértelmezett érték True (Igaz). Ha értéke True (Igaz), felülbírálja a Jelentéskészítő kiszolgálónak a mobileszközön lévő definícióját. A már konfigurált meglévő kiszolgálók törölve lesznek. A felülbírálás True értékre állítása azt is megakadályozza, hogy a felhasználó eltávolítsa ezt a konfigurációt.<br><br>Ha „False” (Hamis) értéket használ, akkor a leküldött értékek hozzáadódnak, a már meglévő beállítások pedig megmaradnak. Ha az adott kiszolgálói URL-cím már konfigurálva van a mobilalkalmazásban, akkor az alkalmazás ezt a konfigurációt változatlanul hagyja. Az alkalmazás nem kéri fel a felhasználót, hogy újra hitelesítse magát ugyanazon a kiszolgálón. |

## <a name="data-protection-settings-ios"></a>Adatvédelmi beállítások (iOS)

Az iOS-hez készült Power BI alkalmazással a rendszergazdák testreszabhatják a biztonsági és adatvédelmi beállítások alapértelmezett konfigurációját. Megkövetelheti a felhasználóktól, hogy Face ID-t, Touch ID-t vagy hitelesítő kódot használjanak a Power BI alkalmazáshoz.

| Kulcs | Típus | Leírás |
|---|---|---|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | Logikai érték | Az alapértelmezett érték False (Hamis). <br><br>Az alkalmazás használatához megkövetelhetők biometrikus adatok, például a TouchID vagy a FaceID használata. Ez esetben ezekre is szükség van a hitelesítésen felül.<br><br>Alkalmazásvédelmi szabályzatok használata esetén a Microsoft azt javasolja, hogy tiltsa le ezt a beállítást, így elkerülhetők a kettős hozzáférési kérelmek. |

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
