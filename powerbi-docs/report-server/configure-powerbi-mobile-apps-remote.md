---
title: Mobilalkalmazás jelentéskészítő kiszolgálóhoz való hozzáférésének távoli konfigurálása
description: Útmutató mobilalkalmazások jelentéskészítő kiszolgálóhoz való távoli hozzáférésének konfigurálásához.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/07/2019
ms.author: painbar
ms.openlocfilehash: b84d7a23cf947b18302c761ff5f78143bf3356aa
ms.sourcegitcommit: 50c4bebd3432ef9c09eacb1ac30f028ee4e66d61
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/12/2019
ms.locfileid: "73925906"
---
# <a name="configure-power-bi-mobile-app-access-to-report-server-remotely"></a>Power BI mobilalkalmazás jelentéskészítő kiszolgálóhoz való hozzáférésének távoli konfigurálása

A következőkre vonatkozik:

| ![iPhone](./media/configure-powerbi-mobile-apps-remote/ios-logo-40-px.png) | ![Android rendszerű telefon](./media/configure-powerbi-mobile-apps-remote/android-logo-40-px.png) |
|:--- |:--- |
| iOS |Android |

Ebben a cikkben megismerheti, hogyan használható a cég MDM eszköze ahhoz, hogy a Power BI mobilalkalmazásának jelentéskészítő kiszolgálóhoz való hozzáférését konfigurálja. Ehhez az informatikai rendszergazdának létre kell hoznia egy alkalmazáskonfigurálási szabályzatot a megfelelő információkkal, amelyet le lehet küldeni az alkalmazásba. 

 Ha a jelentéskészítő kiszolgálóval való kapcsolat már konfigurálva van, a Power BI mobilalkalmazásának felhasználói egyszerűbben csatlakozhatnak a vállalat jelentéskiszolgálójához. 

## <a name="create-the-app-configuration-policy-in-mdm-tool"></a>Az alkalmazáskonfigurálási szabályzat létrehozása az MDM eszközzel 

Rendszergazdaként az alábbi lépéseket kell elvégeznie a Microsoft Intune-ban, hogy létrehozhassa az alkalmazáskonfigurálási szabályzatot. Más MDM-eszközökben eltérhetnek azok a lépések, amelyek az alkalmazáskonfigurálási szabályzat létrehozásához szükségesek. 

1. Csatlakoztassa az MDM eszközt. 
2. Hozzon létre egy új alkalmazáskonfigurálási szabályzatot, és nevezze el. 
3. Válassza ki, hogy mely felhasználóknak szeretné terjeszteni ezt az alkalmazáskonfigurálási szabályzatot. 
4. Hozzon létre kulcs-érték párokat. 

A párokat az alábbi táblázatban láthatja.

|Kulcs  |Típus  |Leírás  |
|---------|---------|---------|
| com.microsoft.powerbi.mobile.ServerURL | Sztring | Jelentéskészítő kiszolgáló URL-címe <br> Http/https-sel kell kezdődnie |
| com.microsoft.powerbi.mobile.ServerUsername | Sztring | [nem kötelező] <br> A kiszolgálóhoz való csatlakozáshoz használandó felhasználónév. <br> Ha még nem létezik ilyen, az alkalmazás kérni fogja a felhasználót, hogy adja meg a kapcsolathoz a felhasználónevet.| 
| com.microsoft.powerbi.mobile.ServerDisplayName | Sztring | [nem kötelező] <br> Az alapértelmezett érték „Report server” („Jelentéskészítő kiszolgáló”) <br> Az alkalmazásban használt rövid név a kiszolgáló azonosítására | 
| com.microsoft.powerbi.mobile.OverrideServerDetails | Logikai érték | Az alapértelmezett érték True (Igaz) <br>Ha értéke „True” (Igaz), felülbírálja a Jelentéskészítő kiszolgálónak a mobileszközön lévő definícióját. A már konfigurált meglévő kiszolgálók törölve lesznek. <br> A felülbírálás True értékre állítása azt is megakadályozza, hogy a felhasználó eltávolítsa ezt a konfigurációt. <br> Ha „False” (Hamis) értéket használ, akkor a leküldött értékek hozzáadódnak, a már meglévő beállítások pedig megmaradnak. <br> Ha az adott kiszolgálói URL-cím már konfigurálva van a mobilalkalmazásban, akkor az alkalmazás ezt a konfigurációt változatlanul hagyja. Az alkalmazás nem kéri fel a felhasználót, hogy újra hitelesítse magát ugyanazon a kiszolgálón. |

Az alábbiakban bemutatunk egy példát arra, hogyan állítható be a konfigurálási szabályzat az Intune-ban.

![Konfigurálási beállítások az Intune-ban](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configuration-settings.png)

## <a name="end-users-connecting-to-report-server"></a>A Jelentéskészítő kiszolgálóhoz csatlakozó végfelhasználók

 Tegyük fel, hogy az alkalmazáskonfigurálási szabályzatot egy terjesztési listán teszi közzé. Amikor a terjesztési listában szereplő felhasználók és eszközök elindítják a mobilalkalmazást, a következőket tapasztalják. 

1. Egy üzenet jelenik meg számukra arról, hogy a mobilalkalmazásuk egy Jelentéskészítő kiszolgálóval lett konfigurálva, és kéri őket a **Bejelentkezésre**.

    ![Bejelentkezés a jelentéskészítő kiszolgálóba](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-sign-in.png)

2.  A **Csatlakozás kiszolgálóhoz** oldalon a jelentéskészítő kiszolgáló adatai már ki vannak töltve. A **Csatlakozás** lehetőségre kell koppintaniuk.

    ![A jelentéskészítő kiszolgáló adatai kitöltve](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configure-connect-server.png)

3. Beírják a hitelesítéshez szükséges jelszót, majd a **Bejelentkezés** lehetőségre koppintanak. 

    ![A jelentéskészítő kiszolgáló adatai kitöltve](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-address.png)

Most már megnézhetik és használhatják a Jelentéskészítő kiszolgálón tárolt KPI-ket és Power BI-jelentéseket.

## <a name="next-steps"></a>Következő lépések

- [A Power BI Mobile távoli elérésének engedélyezése Azure AD-alkalmazásproxyval](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-integrate-with-power-bi)
- [Rendszergazdai áttekintés](admin-handbook-overview.md)  
- [A Power BI jelentéskészítő kiszolgáló telepítése](install-report-server.md)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

