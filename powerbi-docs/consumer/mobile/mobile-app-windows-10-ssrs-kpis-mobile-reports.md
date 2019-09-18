---
title: SSRS-mobiljelentések, KPI-k megtekintése a Windows 10-hez készült Power BI mobilalkalmazásban
description: A Windows 10-hez készült Power BI mobilalkalmazás valós idejű, érintéssel vezérelhető mobil hozzáférést biztosít a fontos helyszíni vállalati információkhoz.
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 06/28/2018
ms.author: mshenhav
ms.openlocfilehash: 98c76fd5903a44c8cc1ef5b175f235f1ec4382e9
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/16/2019
ms.locfileid: "61340847"
---
# <a name="view-reporting-services-ssrs-mobile-reports-and-kpis-in-the-windows-10-power-bi-mobile-app"></a>Reporting Services- (SSRS-) mobiljelentések és -KPI-k megtekintése a Windows 10-hez készült Power BI mobilalkalmazásban
A Windows 10-hez készült Power BI mobilalkalmazás valós idejű, érintéssel vezérelhető mobil hozzáférést biztosít az SQL Server 2016 Reporting Services szolgáltatásban található fontos helyszíni vállalati információkhoz. 

![Reporting Services-mobiljelentések](././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report.png)

## <a name="first-things-first"></a>Először a lényeg
Az SQL Server 2016 Enterprise kiadás mobiljelentés-közzétevőjének segítségével [saját Reporting Services-mobiljelentéseket hozhat létre](https://msdn.microsoft.com/library/mt652547.aspx), és közzéteheti őket a [Reporting Services webes portálon](https://msdn.microsoft.com/library/mt637133.aspx). KPI-ket hozhat létre közvetlenül a webes portálon. Mappákba rendezheti őket, és megjelölheti kedvenceit, hogy könnyedén megtalálhassa azokat. 

Ezt követően megtekintheti a mappákba rendezett vagy kedvencekként összegyűjtött mobiljelentéseket és KPI-ket a Windows 10-hez készült Power BI mobilalkalmazásban. 

> [!NOTE]
> Az eszközön a Windows 10 operációs rendszernek kell futnia. Az alkalmazás optimális működéséhez 1 GB RAM és 8 GB belső tárhely szükséges.
> 
> 

## <a name="explore-samples-without-a-sql-server-2016-reporting-services-server"></a>Minták böngészése SQL Server 2016 Reporting Services-kiszolgáló nélkül
Akkor is böngészhet a Reporting Services-mobiljelentések funkciói között, ha nem fér hozzá a Reporting Services webes portálhoz.

1. Nyissa meg a Power BI alkalmazást Windows 10-es eszközén.
2. Koppintson a globális navigációs gombra. ![Globális navigációs gomb](././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/powerbi_windows10_options_icon.png) a bal felső sarokban.
3. Koppintson a **Beállítások** ikonra ![Beállítások ikon](./././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png), kattintson a jobb gombbal vagy koppintson és tartsa nyomva a **Csatlakozás kiszolgálóhoz** elemet, majd koppintson a **Minták megtekintése** elemre.
   
   ![SSRS-minták megtekintése](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-win10-connect-ssrs-samples.png)
4. A Kiskereskedelmi jelentések vagy Értékesítési jelentések mappát megnyitva megismerheti az azokhoz tartozó KPI-ket és mobiljelentéseket.
   
   ![Minta KPI-k és mobiljelentések](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-win10-ssrs-sample-kpis.png)

Böngéssze át a mintákat a KPI-kkel és mobiljelentésekkel való interakcióhoz.

## <a name="connect-to-a-reporting-services-report-server"></a>Kapcsolódás a Reporting Services jelentéskészítő kiszolgálóhoz
1. A bal oldali navigációs ablaktábla alján koppintson a **Beállítások** ![Beállítások ikon](./././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png) elemre.
2. Koppintson a **Csatlakozás kiszolgálóhoz** lehetőségre.
3. Töltse ki a kiszolgáló címét, és adja meg felhasználónevét és jelszavát. A kiszolgáló címét az alábbi formátumban kell megadni:
   
     `http://<servername>/reports` VAGY `https://<servername>/reports`
   
   > [!NOTE]
   > Írja be a **http** vagy **https** előtagot a kapcsolati sztring elejére.
   > 
   > 
   
    Koppintson a **Speciális beállítás** lehetőségre, ha meg szeretne adni egy nevet a kiszolgáló számára.
4. Kattintson a pipa jelre a kapcsolódáshoz. 
   
   A kiszolgáló látható lesz a bal oldali navigációs sávban.
   
   ![A kiszolgáló a bal oldali navigációs sávban](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-server.png)
   
   >[!TIP]
   >A globális navigációs gombra ![Globális navigációs gomb](././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/powerbi_windows10_options_icon.png) koppintva bármikor válthat a Reporting Services-mobiljelentések és az irányítópultok között a Power BI szolgáltatásban. 
   > 

## <a name="view-reporting-services-kpis-and-mobile-reports-in-the-power-bi-app"></a>Reporting Services-KPI-k és -mobiljelentések megtekintése a Power BI alkalmazásban
A Reporting Services-KPI-k és -mobiljelentések ugyanabban a mappában találhatók, mint a Reporting Services webes portálon.

![Jelentések mappái](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-folders.png)

* Koppintson egy KPI-re annak Fókusz módban való megtekintéséhez.
  
    ![KPI megtekintése Fókusz módban](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-kpis.png)
* Koppintson egy mobiljelentésre annak a Power BI alkalmazásban történő megnyitásához és kezeléséhez.
  
    ![Reporting Services-mobiljelentés](././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report.png)

## <a name="view-your-favorite-kpis-and-reports"></a>A kedvenc KPI-jeinek és jelentéseinek megtekintése
Megjelölhet KPI-ket és mobilejelentéseket kedvencként a Reporting Services webes portálon, majd megtekintheti azokat egyetlen, kényelmesen elérhető mappában Windows 10-es eszközén, a kedvenc Power BI-irányítópultjaival és -jelentéselvei együtt.

* Koppintson a **Kedvencek** elemre.
  
   ![Kedvencek ikon](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-favorite-menu.png)
  
   A webes portálon található összes kedvencét megtalálhatja ezen az oldalon.
  
   ![Kedvencek oldal](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-windows-10-ssrs-favorites.png)

További információ a [kedvencekről a Power BI-mobilalkalmazásokban](mobile-apps-favorites.md).

## <a name="remove-a-connection-to-a-report-server"></a>Jelentéskészítő kiszolgálóval való kapcsolat eltávolítása
Egyszerre csak egy jelentéskészítő kiszolgálóhoz kapcsolódhat a Power BI mobilalkalmazásából. Ha másik kiszolgálóhoz szeretne kapcsolódni, meg kell szakítania a kapcsolatot a jelenlegivel.

1. A bal oldali navigációs ablaktábla alján koppintson a **Beállítások** ![Beállítások ikon](./././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png) elemre.
2. Koppintson azon kiszolgáló nevére, amelyhez nem szeretne a továbbiakban kapcsolódni, és tartsa nyomva.
3. Koppintson a **Kiszolgáló eltávolítása** lehetőségre.
   
    ![Kiszolgáló eltávolítása](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-windows-10-ssrs-remove-server-menu.png)

## <a name="create-reporting-services-mobile-reports-and-kpis"></a>Reporting Services-mobiljelentések és -KPI-k létrehozása
A Power BI-mobilalkalmazásban nincs lehetősége Reporting Services-KPI-k és -mobiljelentések létrehozására. Ezt az SQL Server mobiljelentés-közzétevője és egy SQL Server 2016 Reporting Services webes portál segítségével teheti meg.

* [Saját Reporting Services-mobiljelentések létrehozása](https://msdn.microsoft.com/library/mt652547.aspx) és a Reporting Services webes portálon történő közzététele.
* [KPI-k létrehozása egy Reporting Services webes portálon](https://msdn.microsoft.com/library/mt683632.aspx)

## <a name="next-steps"></a>Következő lépések
* [A Windows 10-hez készült Power BI mobilalkalmazás használatának első lépései](mobile-windows-10-phone-app-get-started.md)  
* [Mi az a Power BI?](../../power-bi-overview.md)  
* Kérdése van? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

