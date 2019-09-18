---
title: Helyszíni jelentések és KPI-k megtekintése a Power BI-mobilalkalmazásokban
description: A Power BI Mobile-alkalmazások élő, érintésvezérelt mobilhozzáférést biztosítanak helyszíni üzleti adataihoz a Microsoft SQL Server Reporting Services és a Power BI jelentéskészítő kiszolgáló használatával.
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 06/13/2018
ms.author: mshenhav
ms.openlocfilehash: c735b5e1abbed0c733ca4414e15fc44b741349d8
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/16/2019
ms.locfileid: "61343884"
---
# <a name="view-on-premises-report-server-reports-and-kpis-in-the-power-bi-mobile-apps"></a>Helyszíni jelentéskészítő kiszolgálói jelentések és KPI-k megtekintése a Power BI-mobilalkalmazásokban

A Power BI Mobile-alkalmazások élő, érintésvezérelt mobilhozzáférést biztosítanak helyszíni üzleti adataihoz a Power BI jelentéskészítő kiszolgáló és az SQL Server 2016 Reporting Services (SSRS) használatával.

A következőkre vonatkozik:

| ![iPhone](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/iphone-logo-50-px.png) | ![iPad](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/ipad-logo-50-px.png) | ![Android rendszerű telefon](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-phone-logo-50-px.png) | ![Android rendszerű táblagép](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-tablet-logo-50-px.png) |
|:--- |:--- |:--- |:--- |
| iPhone-ok |iPadek |Android rendszerű telefonok |Android rendszerű táblagépek |


![A jelentéskészítő kiszolgáló kezdőlapja a mobilalkalmazásokban](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ipad-pbi-report-server-home.png)

## <a name="first-things-first"></a>Kezdjük az elején
**A mobilalkalmazásokban megtekinteni lehet a Power BI-tartalmat, létrehozni nem.**

* Ön és cégének más jelentéskészítői a [Power BI-jelentéseket a Power BI Desktoppal hozzák létre, majd közzéteszik a Power BI jelentéskészítő kiszolgáló](../../report-server/quickstart-create-powerbi-report.md) webes portálján. 
* A [KPI-ket közvetlenül a webes portálon](https://docs.microsoft.com/sql/reporting-services/working-with-kpis-in-reporting-services) hozhatja létre, rendezheti mappákba, és itt jelölheti meg a kedvenceit is, hogy később könnyen megtalálja. 
* A [Reporting Services mobiljelentéseit](https://docs.microsoft.com/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher) az SQL Server 2016 Enterprise Edition Mobile Report Publisherrel hozhatja létre és teheti közzé a [Reporting Services webes portálján](https://docs.microsoft.com/sql/reporting-services/web-portal-ssrs-native-mode).  

Ezután a Power BI-mobilalkalmazásokban akár öt jelentéskészítő kiszolgálót is csatlakoztathat, hogy mappákba rendezve vagy a kedvencek közé gyűjtve megtekinthesse a Power BI-jelentéseket és KPI-ket. 

## <a name="explore-samples-in-the-mobile-apps-without-a-server-connection"></a>Minták megtekintése a mobilalkalmazásokban kiszolgálói kapcsolat nélkül
Még ha nincs is hozzáférése a Microsoft SQL Server Reporting Services webes portáljához, akkor is feltárhatja a Reporting Services mobiljelentéseinek és KPI-nek funkcióit. 

1. Koppintson a globális navigáció gombra ![Globális navigáció gomb](././media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-global-nav-button.png) a bal felső sarokban, majd a fogaskerék ikonra a jobb felsőben ![Fogaskerék ikon](././media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ios-settings-icon.png).
2. Koppintson a **Reporting Services-példák** elemre, majd tallózással keresse a mintául szolgáló KPI-ket és mobiljelentéseket.
   
   ![Reporting Services-minták](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-ssrs-samples.png)

## <a name="connect-to-an-on-premises-report-server"></a>Csatlakozás helyszíni jelentéskészítő kiszolgálóhoz
A helyszíni Power BI-jelentéseket, a Reporting Services mobiljelentéseit és a KPI-ket a Power BI-mobilalkalmazásokban tekintheti meg. 

1. Nyissa meg a mobileszközön a Power BI alkalmazást.
2. Ha még nem jelentkezett be a Power BI-ba, koppintson a **Jelentéskészítő kiszolgáló** gombra.
   
   ![Bejelentkezés jelentéskészítő kiszolgálóra](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-connect-to-rs-login.png)
   
   Ha már bejelentkezett a Power BI alkalmazásba, koppintson a globális navigáció gombra ![Globális navigáció gomb](././media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-global-nav-button.png), majd a fogaskerék ikonra ![Fogaskerék ikon](././media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ios-settings-icon.png) a jobb felső sarokban.
3. Koppintson a **Csatlakozás kiszolgálóhoz** elemre.
   
    ![Csatlakozás kiszolgálóhoz](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-android-server-sign-in.png)

     A mobilalkalmazásnak valamilyen módon el kell érnie a kiszolgálót. Ez többféleképpen is megoldható:

    - A legegyszerűbb, ha ugyanabban a hálózatban van vagy VPN-t használ.
    - A szervezeten kívülről való csatlakozáshoz használható Webalkalmazás-proxy. További részleteket a [Csatlakozás a Reporting Services szolgáltatáshoz OAuth használatával](mobile-oauth-ssrs.md) című témakörben találhat. 
    - Nyisson meg egy kapcsolatot (portot) a tűzfalon.

1. Töltse ki a kiszolgáló címét, és adja meg felhasználónevét és jelszavát. A kiszolgáló címét ebben a formátumban adja meg:
   
     `http://<servername>/reports`
   
     VAGY
   
     `https://<servername>/reports`
   
   A kapcsolati sztring előtt a **http** vagy **https** előtagot alkalmazza.
   
    ![Csatlakozás kiszolgálóhoz párbeszédpanel](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ios-connect-to-server-dialog.png)
5. (Nem kötelező) A **Speciális beállítások** alatt megadhatja a kiszolgáló valódi nevét, ha szeretné.
6. A kiszolgáló megjelenik a bal oldali navigációs sávon – ebben a példában a neve „power bi report server”.
   
   ![Jelentéskészítő kiszolgáló a bal oldali navigációs sávon](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-left-nav-report-server.png)

## <a name="connect-to-an-on-premises-report-server-in-ios"></a>Csatlakozás helyszíni jelentéskészítő kiszolgálóhoz iOS rendszeren

Ha az iOS-es mobilalkalmazásban tekinti meg a Power BI-t, előfordulhat, hogy a rendszergazda definiált egy alkalmazáskonfigurációs szabályzatot. Ha így van, a jelentéskészítő kiszolgálóhoz való csatlakozáshoz használt felület leegyszerűsített, és nem kell olyan sok adatot megadnia, amikor csatlakozik egy jelentéskészítő kiszolgálóhoz. 

1. Egy üzenet jelenik meg arról, hogy a mobilalkalmazás egy jelentéskészítő kiszolgálóhoz lett konfigurálva. Koppintson a **Bejelentkezés** lehetőségre.

    ![Bejelentkezés a jelentéskészítő kiszolgálóba](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-config-server-sign-in.png)

2.  A **Csatlakozás kiszolgálóhoz** oldalon már ki vannak töltve a jelentéskészítő kiszolgáló adatai. Koppintson a **Csatlakozás** lehetőségre.

    ![A jelentéskészítő kiszolgáló adatai kitöltve](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ios-remote-configure-connect-server.png)

3. Írja be a hitelesítéshez szükséges jelszót, majd koppintson a **Bejelentkezés** lehetőségre. 

    ![A jelentéskészítő kiszolgáló adatai kitöltve](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-config-server-address.png)

Most már megtekintheti és használhatja a jelentéskészítő kiszolgálón tárolt KPI-ket és Power BI-jelentéseket.

## <a name="view-power-bi-reports-and-kpis-in-the-power-bi-app"></a>Power BI-jelentések és KPI-k megtekintése a Power BI alkalmazásban
A Power BI-jelentések, a Reporting Services mobiljelentései és a KPI-k ugyanazokban a mappákban jelennek meg, amelyekben a Reporting Services webes portálján találhatók. 

* Koppintson egy Power BI-jelentésre ![Power BI-jelentés ikon](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-rs-mobile-report-icon.png). Fekvő tájolásban nyílik meg, és a Power BI alkalmazásban kezelheti.

    > [!NOTE]
  > A részletezés jelenleg nem engedélyezett a Power BI jelentéseiben és a Power BI jelentéskészítő kiszolgálón.
  
    ![Power BI-jelentés](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-report-server-report.png)
* A Power BI Desktopban a jelentések tulajdonosai [optimalizálhatják a jelentéseket](../../desktop-create-phone-report.md) a Power BI-mobilalkalmazásokhoz. Az optimalizált jelentések a mobiltelefonon különleges ikonnal ![Optimalizált Power BI-jelentés ikonja](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-rs-mobile-optimized-icon.png) és elrendezéssel rendelkeznek.
  
    ![Mobilra optimalizált Power BI-jelentés](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-rs-mobile-optimized-report.png)
* Koppintson a KPI-re a fókuszált módban való megjelenítéséhez.
  
    ![KPI fókuszált módban](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/pbi_ipad_ssmrp_tile.png)

## <a name="view-your-favorite-kpis-and-reports"></a>Kedvenc KPI-k és jelentések megtekintése
KPI-ket és jelentéseket jelölhet meg kedvencekként a webes portálon, majd a kedvenc Power BI-irányítópultjaival együtt ezeket is megtekintheti egy Önnek megfelelő mappában a mobileszközén.

* Koppintson a **Kedvencek** elemre.
  
   ![Kedvencek a bal oldali navigációs panelen](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ipad-faves-pbi-report-server-update.png)
  
   A webes portálról a kedvenc KPI-je és jelentései ezen a lapon mind megtalálhatók a Power BI szolgáltatás Power BI-irányítópultjaival együtt:
  
   ![Power BI-jelentések és -irányítópultok a Kedvencek lapon](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ipad-favorites.png)

## <a name="remove-a-connection-to-a-report-server"></a>Jelentéskészítő kapcsolatának eltávolítása
1. A bal oldali navigációs sáv alján koppintson a **Beállítások** gombra.
2. Koppintson annak a kiszolgálónak a nevére, amelyhez nem szeretne kapcsolódni.
3. Koppintson a **Kiszolgáló eltávolítása** elemre.

## <a name="next-steps"></a>Következő lépések
* [Mi az a Power BI?](../../power-bi-overview.md)  
* Kérdése van? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

