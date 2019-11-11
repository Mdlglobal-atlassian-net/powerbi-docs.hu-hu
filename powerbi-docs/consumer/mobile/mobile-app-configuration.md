---
title: A Power BI iOS-beli alkalmazáskonfigurációs beállításai
description: Az iOS Power BI viselkedésének testreszabása egy MDM-eszközzel
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 06/07/2019
ms.author: mshenhav
ms.openlocfilehash: c2d619489b042e523c559a16dab249b268389cd5
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73879434"
---
# <a name="remotely-configure-power-bi-ios-app-using-mobile-device-management-mdm-tool"></a>Az iOS Power BI alkalmazás távoli konfigurálása egy mobileszköz-kezelési (MDM-) eszközzel

Az iOS Power BI Mobile alkalmazás olyan beállításokat támogat, amelyekkel az Office 365 és a mobileszköz-kezelési (MDM-) eszköz – például az Intune – rendszergazdái testreszabhatják az alkalmazás viselkedését.

Az iOS Power BI Mobile a következő konfigurációs forgatókönyveket támogatja:

- A jelentéskészítő kiszolgáló konfigurálása
- Adatvédelmi beállítások

## <a name="report-server-configuration"></a>A jelentéskészítő kiszolgáló konfigurálása

Az iOS Power BI alkalmazással a rendszergazdák távolról küldhetnek le konfigurációs beállításokat a jelentéskészítő kiszolgálónak a regisztrált eszközök esetén.

| Kulcs | Típus | Leírás |
|---|---|---|
| com.microsoft.powerbi.mobile.ServerURL | Sztring | Jelentéskészítő kiszolgáló URL-címe.<br><br>Http/https-sel kell kezdődnie.|
| com.microsoft.powerbi.mobile.ServerUsername | Sztring | [nem kötelező]<br><br>A kiszolgálóhoz való csatlakozáshoz használandó felhasználónév.<br><br>Ha még nem létezik ilyen, az alkalmazás kérni fogja a felhasználót, hogy adja meg a kapcsolathoz a felhasználónevet.|
| com.microsoft.powerbi.mobile.ServerDisplayName | Sztring | [nem kötelező]<br><br>Az alapértelmezett érték „Report server” („Jelentéskészítő kiszolgáló”)<br><br>Az alkalmazásban használt rövid név a kiszolgáló azonosítására. |
| com.microsoft.powerbi.mobile.OverrideServerDetails | Logikai érték | [nem kötelező]<br><br>Az alapértelmezett érték True (Igaz). Ha értéke True (Igaz), felülbírálja a Jelentéskészítő kiszolgálónak a mobileszközön lévő definícióját. A már konfigurált meglévő kiszolgálók törölve lesznek. A felülbírálás True értékre állítása azt is megakadályozza, hogy a felhasználó eltávolítsa ezt a konfigurációt.<br><br>Ha „False” (Hamis) értéket használ, akkor a leküldött értékek hozzáadódnak, a már meglévő beállítások pedig megmaradnak. Ha az adott kiszolgálói URL-cím már konfigurálva van a mobilalkalmazásban, akkor az alkalmazás ezt a konfigurációt változatlanul hagyja. Az alkalmazás nem kéri fel a felhasználót, hogy újra hitelesítse magát ugyanazon a kiszolgálón. |

## <a name="data-protection-setting"></a>Adatvédelmi beállítások

Az iOS Power BI alkalmazással a rendszergazdák testreszabhatják a biztonsági és adatvédelmi beállítások alapértelmezett konfigurációját. Megkövetelheti a felhasználóktól, hogy Face ID-t, Touch ID-t vagy hitelesítő kódot használjanak a Power BI alkalmazáshoz.

| Kulcs | Típus | Leírás |
|---|---|---|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | Logikai érték | Az alapértelmezett érték False (Hamis). <br><br>Az alkalmazás használatához megkövetelhetők biometrikus adatok, például a TouchID vagy a FaceID használata. Ez esetben ezekre is szükség van a hitelesítésen felül.<br><br>Alkalmazásvédelmi szabályzatok használata esetén a Microsoft azt javasolja, hogy tiltsa le ezt a beállítást, így elkerülhetők a kettős hozzáférési kérelmek. |

## <a name="deploying-app-configuration-settings"></a>Alkalmazáskonfigurációs beállítások bevezetése

Az alábbi lépésekkel létrehozhat egy alkalmazáskonfigurációs szabályzatot. A konfigurációs szabályzat létrehozása után hozzárendelheti annak beállításait felhasználói csoportokhoz.

1. Csatlakoztassa az MDM eszközt.

2. Hozzon létre egy új alkalmazáskonfigurálási szabályzatot, és nevezze el.

3. Válassza ki, hogy mely felhasználóknak szeretné terjeszteni ezt az alkalmazáskonfigurálási szabályzatot.

4. Hozzon létre kulcs-érték párokat a leküldeni kívánt beállításhoz.

Az Intune portál alkalmazáskonfigurációs szabályzataival a rendszergazdák könnyen üzembe helyezhetik ezeket a beállításokat az iOS Power BI alkalmazásban.
Azonban minden MDM-szolgáltató támogatott. Ha nem Intune-t használ, a beállítások üzembe helyezéséhez tekintse meg a használt MDM-megoldás dokumentációját.

## <a name="next-steps"></a>Következő lépések

* Az [iPhone-ra készült Power BI mobilalkalmazás](https://go.microsoft.com/fwlink/?LinkId=522062) letöltése
* Kövessen minket a [@MSPowerBITwitteren](https://twitter.com/MSPowerBI)
* Csatlakozzon a beszélgetéshez a [Power BI-közösségben](https://community.powerbi.com/)
