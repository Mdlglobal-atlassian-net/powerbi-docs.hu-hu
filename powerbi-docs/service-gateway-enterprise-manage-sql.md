---
title: Adatforrások kezelése – SQL
description: A helyszíni adatátjáró és az átjáróhoz tartozó adatforrások kezelésének módja.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 01/24/2018
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 6771e2da33448fe3aa54a0184a220437ffb54fce
ms.sourcegitcommit: 5e83fa6c93a0bc6599f76cc070fb0e5c1fce0082
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/13/2019
ms.locfileid: "56215856"
---
# <a name="manage-your-data-source---sql-server"></a>Adatforrások kezelése – SQL Server
A helyszíni adatátjáró telepítése után az átjáróval használható adatforrásokat adhat hozzá. Ez a cikk bemutatja, hogyan lehet használni az átjárókat és az adatforrásokat. Az SQL Server-adatforrás ütemezett frissítéshez vagy DirectQueryhez is használható.

## <a name="download-and-install-the-gateway"></a>Az átjáró letöltése és telepítése
Az átjárót a Power BI szolgáltatásból töltheti le. Válassza a **Letöltések** > **Data Gateway** lehetőséget, vagy lépje az [átjáró letöltési oldalára](https://go.microsoft.com/fwlink/?LinkId=698861).

![](media/service-gateway-enterprise-manage-sql/powerbi-download-data-gateway.png)

## <a name="add-a-gateway"></a>Átjáró hozzáadása
Egy átjáró hozzáadásához egyszerűen [töltse le](https://go.microsoft.com/fwlink/?LinkId=698861) és telepítse az átjárót egy kiszolgálóra a környezetében. Miután telepítette az átjárót, az megjelenik az átjárók listáiban az **Átjárók kezelése** területen.

> [!NOTE]
> Az **Átjárók kezelése** nem jelenik meg, amíg nem rendszergazdája legalább egy átjárónak. Ez úgy lehetséges, hogy rendszergazdaként hozzáadják egy átjáróhoz, vagy saját maga telepít és konfigurál egy átjárót.
> 
> 

## <a name="remove-a-gateway"></a>Átjáró eltávolítása
Egy átjáró eltávolítása az átjáró alatti adatforrásokat is törli.  Az adott adatforrásokra támaszkodó irányítópultok és jelentések sem fognak működni.

1. Válassza ki a fogaskerék ikont ![](media/service-gateway-enterprise-manage-sql/pbi_gearicon.png) a jobb felső sarokban, majd az **Átjárók kezelése** lehetőséget.
2. Átjáró > **Eltávolítás**
   
   ![](media/service-gateway-enterprise-manage-sql/datasourcesettings7.png)

## <a name="add-a-data-source"></a>Adatforrások felvétele
Az adatforrások felvételének egyik módja az, ha kiválaszt egy átjárót, és az **Adatforrás hozzáadása** lehetőségre kattint, a másik pedig az, ha az Átjáró > **Adatforrás hozzáadása** elemhez lép.

![](media/service-gateway-enterprise-manage-sql/datasourcesettings1.png)

Ez után kiválaszthatja az **Adatforrástípust** a listából.

![](media/service-gateway-enterprise-manage-sql/datasourcesettings2.png)

> [!NOTE]
> DirectQuery használatakor az átjáró csak az **SQL Server 2012 SP1** és későbbi verzióit támogatja.
> 
> 

Ez után az adatforrás információit, köztük a **Kiszolgálót** és az **Adatbázist** is kell megadnia.  

**Hitelesítési módszert** is választania kell.  Ez lehet **Windows** vagy **Egyszerű**.  Az **Egyszerű** lehetőséget akkor kell választani, ha Windows-hitelesítés helyett SQL-hitelesítést fog használni. Végül adja meg az ehhez az adatforráshoz használandó hitelesítő adatokat.

> [!NOTE]
> Az adatforráson minden lekérdezés ezekkel a hitelesítő adatokkal fog futni, hacsak nincs hozzá konfigurálva és engedélyezve a Kerberos használata egyszeri bejelentkezéshez (SSO). Egyszeri bejelentkezés (SSO) használata esetén az importált adatkészletek a tárolt hitelesítő adatokat használják, a DirectQuery-adatkészletek viszont az aktuális Power BI-felhasználó nevében, SSO használatával futtatják a lekérdezéseket. A helyszíni adatátjáróról szóló fő cikkben bővebben tájékozódhat a [hitelesítő adatok](service-gateway-onprem.md#credentials) tárolásáról. További információ: [a Kerberos használata egyszeri bejelentkezéshez (SSO) a Power BI-ból helyszíni adatforrásokba](service-gateway-sso-kerberos.md).
> 
> 

![](media/service-gateway-enterprise-manage-sql/datasourcesettings3.png)

Miután minden információt megadott, kattintson a **Hozzáadás** lehetőségre.  Az adatforrás ettől kezdve használható ütemezett frissítéshez vagy DirectQuery-lekérdezéshez egy helyszíni SQL Server kiszolgálón. Siker esetén az *A kapcsolat sikeresen létrejött* üzenet jelenik meg.

![](media/service-gateway-enterprise-manage-sql/datasourcesettings4.png)

### <a name="advanced-settings"></a>Speciális beállítások
Konfigurálhatja az adatforrás adatvédelmi szintjét. Ez vezérli, hogy hogyan fűzhetők össze adatok. Ez csak ütemezett frissítéshez használható. Mindez nem érvényes a DirectQueryre. [További információ](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540)

![](media/service-gateway-enterprise-manage-sql/datasourcesettings9.png)

## <a name="remove-a-data-source"></a>Adatforrás eltávolítása
Ha eltávolít egy adatforrást, akkor leáll minden olyan irányítópult vagy jelentés is, amely az adott adatforrásra támaszkodik.  

Egy adatforrás eltávolításához lépjen az Adatforrás > **Eltávolítás** elemhez.

![](media/service-gateway-enterprise-manage-sql/datasourcesettings6.png)

## <a name="manage-administrators"></a>Rendszergazdák kezelése
Az átjárókhoz tartozó Rendszergazdák lapon felvehet és eltávolíthat az átjáró kezelésére jogosult felhasználókat (vagy biztonsági csoportokat).

![](media/service-gateway-enterprise-manage-sql/datasourcesettings8.png)

## <a name="manage-users"></a>Felhasználók kezelése
Az adatforráshoz tartozó Felhasználók lapon felveheti és eltávolíthatja az adatforrás használatára jogosult felhasználókat vagy biztonsági csoportokat.

> [!NOTE]
> A felhasználók listája csak azt szabályozza, ki tehet közzé jelentéseket. A jelentéstulajdonosok létrehozhatnak irányítópultokat vagy tartalomcsomagokat, és megoszthatják azokat más felhasználókkal.
> 
> 

![](media/service-gateway-enterprise-manage-sql/datasourcesettings5.png)

## <a name="using-the-data-source"></a>Az adatforrás használata
Miután létrehozta az adatforrást, használhatja DirectQuery-kapcsolatokkal vagy ütemezett frissítéssel is.

> [!NOTE]
> A kiszolgáló és az adatbázis nevének egyeznie kell a Power BI Desktopban és az adatforrásban a helyszíni adatátjárón belül.
> 
> 

Az adatkészlet és az adatforrás közötti kapcsolat az átjárón belül a kiszolgáló nevén és az adatbázis nevén alapul. Ezeknek egyezniük kell. Ha például IP-címet ad meg a kiszolgáló neveként a **Power BI Desktopban**, akkor az átjáró konfigurációjában is az IP-címet kell megadnia az adatforráshoz. Ha a Power BI Desktopban a *KISZOLGÁLÓ\PÉLDÁNY* formát használta, az átjáró konfigurációjában is ezt kell megadnia az adatforráshoz.

Ez a DirectQuery és az ütemezett frissítés esetén egyaránt érvényes.

### <a name="using-the-data-source-with-directquery-connections"></a>Az adatforrás használata DirectQuery-kapcsolatokkal
Gondoskodjon róla, hogy a kiszolgáló- és adatbázis-név megegyezzen a **Power BI Desktopban** és a helyszíni adatátjáróban konfigurált adatforrásban. DirectQuery-adatkészletek közzétételéhez arról is gondoskodnia kell, hogy a felhasználója szerepeljen az adatforrás **Felhasználók** lapján. A DirectQuery esetén a kiválasztásra az első adatimportáláskor kerül sor a Power BI Desktopon belül. [További információ](desktop-use-directquery.md)

Miután elvégezte a közzétételt a Power BI Desktopból vagy az **Adatok lekérése** területről, el kell kezdeni működniük a jelentéseknek. Az átjárón belüli adatforrás létrehozása után több percbe telhet, amíg a kapcsolat használhatóvá válik.

### <a name="using-the-data-source-with-scheduled-refresh"></a>Az adatforrás használata ütemezett frissítéssel
Ha szerepel az átjárón belül konfigurált adatforrás **Felhasználók** lapján, és a kiszolgáló és az adatbázis neve egyezik, az átjáró megjelenik lehetőségként az ütemezett frissítésnél.

![](media/service-gateway-enterprise-manage-sql/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="next-steps"></a>Következő lépések
* [Helyszíni adatátjáró](service-gateway-onprem.md)  
* [Helyszíni adatátjáró – részletek](service-gateway-onprem-indepth.md)  
* [A Helyszíni adatátjáróval kapcsolatos hibák elhárítása](service-gateway-onprem-tshoot.md)
* [Kerberos használata egyszeri bejelentkezéshez (SSO) a Power BI-ból a helyszíni adatforrásokhoz](service-gateway-sso-kerberos.md). 
* További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

