---
title: SAP HANA-adatforrások kezelése
description: A helyszíni adatátjáró és az átjáróhoz tartozó adatforrások kezelésének módja. Ez a cikk kifejezetten az SAP HANA használatára vonatkozik.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 01/24/2018
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: e4fabd59396872be9ffa77d8957b06ffcf7eb45f
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54276629"
---
# <a name="manage-your-sap-hana-data-source"></a>SAP HANA-adatforrások kezelése
Amint telepítette a helyszíni adatátjárót, fel kell vennie az átjáróval használható adatforrásokat. Ez a cikk bemutatja, hogyan lehet használni az átjárókat és az adatforrásokat. Az SAP HANA-adatforrás ütemezett frissítéshez vagy DirectQueryhez is használható.

## <a name="download-and-install-the-gateway"></a>Az átjáró letöltése és telepítése
Az átjárót a Power BI szolgáltatásból töltheti le. Válassza a **Letöltések** > **Data Gateway** lehetőséget, vagy lépje az [átjáró letöltési oldalára](https://go.microsoft.com/fwlink/?LinkId=698861).

![](media/service-gateway-enterprise-manage-sap/powerbi-download-data-gateway.png)

## <a name="add-a-gateway"></a>Átjáró hozzáadása
Átjáró hozzáadásához egyszerűen [töltse le](https://go.microsoft.com/fwlink/?LinkId=698861) és telepítse az átjárót a saját környezete egyik kiszolgálóján. Az átjáró a telepítése után megjelenik az **Átjárók kezelése** alatti listában.

> [!NOTE]
> Az **Átjárók kezelése** nem jelenik meg, amíg nem rendszergazdája legalább egy átjárónak. Ez elérhető úgy, ha hozzáadják rendszergazdaként, vagy ha saját maga telepít és konfigurál egy átjárót.
> 
> 

## <a name="remove-a-gateway"></a>Átjáró eltávolítása
Egy átjáró eltávolítása az átjáró alatti adatforrásokat is törli.  Az adott adatforrásokra támaszkodó irányítópultok és jelentések sem fognak működni.

1. Válassza ki a fogaskerék ikont ![](media/service-gateway-enterprise-manage-sap/pbi_gearicon.png) a jobb felső sarokban, majd az **Átjárók kezelése** lehetőséget.
2. Átjáró > **Eltávolítás**
   
   ![](media/service-gateway-enterprise-manage-sap/datasourcesettings7.png)

## <a name="add-a-data-source"></a>Adatforrások felvétele
Az adatforrások felvételének egyik módja az, ha kiválaszt egy átjárót, és az **Adatforrás hozzáadása** lehetőségre kattint, a másik pedig az, ha az Átjáró > **Adatforrás hozzáadása** elemhez lép.

![](media/service-gateway-enterprise-manage-sap/datasourcesettings1.png)

Ezután kiválaszthatja a listából az **Adatforrástípus** elemet.

![](media/service-gateway-enterprise-manage-sap/datasourcesettings2-sap.png)

Ezt követően megadhatja az adatforrásra vonatkozó információkat, köztük a **Kiszolgálót**, a **Felhasználónevet** és a **Jelszót**.

> [!NOTE]
> Az adatforrás felé irányuló összes lekérdezés ezen hitelesítő adatok segítségével fut. További információkért tekintse meg a helyszíni adatátjárókat ismertető fő cikket, amelyből többet tudhat meg a [hitelesítő adatok](service-gateway-onprem.md#credentials) tárolásáról.
> 
> 

![](media/service-gateway-enterprise-manage-sap/datasourcesettings3-sap.png)

Miután minden információt megadott, kattintson a **Hozzáadás** lehetőségre.  Az adatforrás ettől kezdve használható ütemezett frissítéshez vagy DirectQuery-lekérdezéshez egy helyszíni SQL Server-kiszolgálón. Siker esetén megjelenik *A kapcsolat sikeresen létrejött* üzenet.

![](media/service-gateway-enterprise-manage-sap/datasourcesettings4.png)

### <a name="advanced-settings"></a>Speciális beállítások
Konfigurálhatja az adatforrás adatvédelmi szintjét. Ez vezérli, hogy hogyan fűzhetők össze adatok. Ez csak ütemezett frissítéshez használható. Mindez nem érvényes a DirectQueryre. [További információ](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540)

![](media/service-gateway-enterprise-manage-sap/datasourcesettings9.png)

## <a name="remove-a-data-source"></a>Adatforrás eltávolítása
Ha eltávolít egy adatforrást, akkor leáll minden olyan irányítópult vagy jelentés is, amely az adott adatforrásra támaszkodik.  

Egy adatforrás eltávolításához lépjen az Adatforrás > **Eltávolítás** elemhez.

![](media/service-gateway-enterprise-manage-sap/datasourcesettings6.png)

## <a name="manage-administrators"></a>Rendszergazdák kezelése
Az átjárókhoz tartozó Rendszergazdák lapon felvehet és eltávolíthat az átjáró kezelésére jogosult felhasználókat (vagy biztonsági csoportokat).

![](media/service-gateway-enterprise-manage-sap/datasourcesettings8.png)

## <a name="manage-users"></a>Felhasználók kezelése
Az adatforráshoz tartozó Felhasználók lapon felveheti és eltávolíthatja az adatforrás használatára jogosult felhasználókat vagy biztonsági csoportokat.

> [!NOTE]
> A felhasználók listája csak azt szabályozza, ki tehet közzé jelentéseket. A jelentéstulajdonosok létrehozhatnak irányítópultokat vagy tartalomcsomagokat, és megoszthatják azokat más felhasználókkal.
> 
> 

![](media/service-gateway-enterprise-manage-sap/datasourcesettings5.png)

## <a name="using-the-data-source"></a>Az adatforrás használata
Miután létrehozta az adatforrást, használhatja DirectQuery-kapcsolatokkal vagy ütemezett frissítéssel is.

> [!NOTE]
> A kiszolgáló és az adatbázis nevének egyeznie kell a Power BI Desktopban és az adatforrásban a helyszíni adatátjárón belül.
> 
> 

Az adatkészlet és az adatforrás közötti kapcsolat az átjárón belül a kiszolgáló nevén és az adatbázis nevén alapul. Ezeknek egyezniük kell. Ha például egy IP-címet ad meg a kiszolgáló nevének, a Power BI Desktopban azt az IP-címet kell használnia az adatforráshoz az átjáró konfigurációján belül. Ha a Power BI Desktopban a *KISZOLGÁLÓ\PÉLDÁNY* formát használta, az átjáró konfigurációjában is ezt kell megadnia az adatforráshoz.

Ez a DirectQuery és az ütemezett frissítés esetén egyaránt érvényes.

### <a name="using-the-data-source-with-directquery-connections"></a>Az adatforrás használata DirectQuery-kapcsolatokkal
Meg kell győződnie arról, hogy a kiszolgáló és az adatbázis neve egyezik a Power BI Desktop és az átjáró számára konfigurált adatforrás között. DirectQuery-adatkészletek közzétételéhez arról is gondoskodnia kell, hogy a felhasználója szerepeljen az adatforrás **Felhasználók** lapján. A DirectQuery-hez történő kijelölésre a Power BI Desktopban az első adatimportáláskor kerül sor. [További információk](desktop-use-directquery.md)

Miután elvégezte a közzétételt a Power BI Desktopból vagy az **Adatok lekérése** területről, el kell kezdeni működniük a jelentéseknek. Az átjárón belüli adatforrás létrehozása után több percbe telhet, amíg a kapcsolat használhatóvá válik.

### <a name="using-the-data-source-with-scheduled-refresh"></a>Az adatforrás használata ütemezett frissítéssel
Ha szerepel az átjárón belül konfigurált adatforrás **Felhasználók** lapján, és a kiszolgáló és az adatbázis neve egyezik, az átjáró megjelenik lehetőségként az ütemezett frissítésnél.

![](media/service-gateway-enterprise-manage-sap/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="next-steps"></a>Következő lépések
[Helyszíni adatátjáró](service-gateway-onprem.md)  
[Helyszíni adatátjáró – részletek](service-gateway-onprem-indepth.md)  
[A Helyszíni adatátjáróval kapcsolatos hibák elhárítása](service-gateway-onprem-tshoot.md)  
További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

