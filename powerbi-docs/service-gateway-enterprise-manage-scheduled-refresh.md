---
title: Az adatforrás kezelése – Importálás/Ütemezett frissítés
description: A helyszíni adatátjáró és az átjáróhoz tartozó adatforrások kezelésének módja. Ez a cikk az importálás/ütemezett frissítés szolgáltatással használható adatforrásokra vonatkozik.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 8f45fbed0b2c4e5de62f8ef18ee9a552bf05486b
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54293774"
---
# <a name="manage-your-data-source---importscheduled-refresh"></a>Az adatforrás kezelése – Importálás/Ütemezett frissítés
Amint telepítette a helyszíni adatátjárót, fel kell vennie az átjáróval használható adatforrásokat. Ez a cikk bemutatja, hogyan lehet használni az ütemezett frissítéshez használt átjárókat és az adatforrásokat a DirectQuery vagy az élő kapcsolatok helyett.

## <a name="download-and-install-the-gateway"></a>Az átjáró letöltése és telepítése
Az átjárót a Power BI szolgáltatásból töltheti le. Válassza a **Letöltések** > **Data Gateway** lehetőséget, vagy lépje az [átjáró letöltési oldalára](https://go.microsoft.com/fwlink/?LinkId=698861).

![](media/service-gateway-enterprise-manage-scheduled-refresh/powerbi-download-data-gateway.png)

## <a name="add-a-gateway"></a>Átjáró hozzáadása
Egy átjáró hozzáadásához egyszerűen [töltse le](https://go.microsoft.com/fwlink/?LinkId=698863) és telepítse a vállalati átjárót egy kiszolgálóra a környezetében. Miután telepítette az átjárót, megjelenik az átjárók listáiban az **Átjárók kezelése** területen.

> [!NOTE]
> Az **Átjárók kezelése** nem jelenik meg, amíg nem rendszergazdája legalább egy átjárónak. Ez elérhető úgy, ha hozzáadják rendszergazdaként, vagy ha saját maga telepít és konfigurál egy átjárót.
> 
> 

## <a name="remove-a-gateway"></a>Átjáró eltávolítása
Egy átjáró eltávolítása az átjáró alatti adatforrásokat is törli.  Az adott adatforrásokra támaszkodó irányítópultok és jelentések sem fognak működni.

1. Válassza ki a fogaskerék ikont ![](media/service-gateway-enterprise-manage-scheduled-refresh/pbi_gearicon.png) a jobb felső sarokban, majd az **Átjárók kezelése** lehetőséget.
2. Átjáró > **Eltávolítás**
   
   ![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings7.png)

## <a name="add-a-data-source"></a>Adatforrások felvétele
Az adatforrások felvételének egyik módja az, ha kiválaszt egy átjárót, és az **Adatforrás hozzáadása** lehetőségre kattint, a másik pedig az, ha az Átjáró > **Adatforrás hozzáadása** elemhez lép.

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings1.png)

Ekkor a listáról kiválaszthatja az **Adatforrás típusa** lehetőséget. Az összes felsorolt adatforrás használható ütemezett frissítéshez a vállalati átjáróval. Az Analysis Services, az SQL Server és az SAP HANA használható ütemezett frissítéshez vagy DirectQuery/élő kapcsolatokhoz is.

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings2.png)

Ekkor kell megadni az információkat az adatforráshoz. Ebbe beletartoznak a forrásra vonatkozó információk és az adatforrás eléréséhez használt hitelesítő adatok.

> [!NOTE]
> Az adatforrás felé irányuló összes lekérdezés ezen hitelesítő adatok segítségével fut. További információkért tekintse meg a helyszíni adatátjárókat ismertető fő cikket, amelyből többet tudhat meg a [hitelesítő adatok](service-gateway-onprem.md#credentials) tárolásáról.
> 
> 

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings3-oracle.png)

Miután minden információt megadott, kattintson a **Hozzáadás** lehetőségre.  Mostantól használhatja ezt az adatforrást ütemezett frissítéshez a helyszíni adataival. Ha sikerrel járt, megjelenik a *Sikeres csatlakozás* üzenet.

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings4.png)

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-datasources-include](./includes/gateway-onprem-datasources-include.md)]

### <a name="advanced-settings"></a>Speciális beállítások
Konfigurálhatja az adatforrás adatvédelmi szintjét. Ez vezérli, hogy hogyan fűzhetők össze adatok. Ez csak ütemezett frissítéshez használható. [További információ](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540)

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings9.png)

## <a name="remove-a-data-source"></a>Adatforrás eltávolítása
Ha eltávolít egy adatforrást, akkor leáll minden olyan irányítópult vagy jelentés is, amely az adott adatforrásra támaszkodik.  

Egy adatforrás eltávolításához lépjen az Adatforrás > **Eltávolítás** elemhez.

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings6.png)

## <a name="manage-administrators"></a>Rendszergazdák kezelése
Az átjárókhoz tartozó Rendszergazdák lapon felveheti és eltávolíthatja az átjáró kezelésére jogosult felhasználókat. Ekkor csak felvehet felhasználókat. Biztonsági csoportokat nem lehet hozzáadni.

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings8.png)

## <a name="manage-users"></a>Felhasználók kezelése
Az adatforráshoz tartozó Felhasználók lapon felveheti és eltávolíthatja az adatforrás használatára jogosult felhasználókat vagy biztonsági csoportokat.

> [!NOTE]
> A felhasználók listája csak azt szabályozza, ki tehet közzé jelentéseket. A jelentéstulajdonosok létrehozhatnak irányítópultokat vagy tartalomcsomagokat, és megoszthatják azokat más felhasználókkal.
> 
> 

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings5.png)

## <a name="using-the-data-source-for-scheduled-refresh"></a>Az adatforrás használata ütemezett frissítéshez
Miután létrehozta az adatforrást, használhatja DirectQuery-kapcsolatokkal vagy ütemezett frissítéssel is.

> [!NOTE]
> A kiszolgáló és az adatbázis nevének egyeznie kell a Power BI Desktopban és az adatforrásban a helyszíni adatátjárón belül.
> 
> 

Az adatkészlet és az adatforrás közötti kapcsolat az átjárón belül a kiszolgáló nevén és az adatbázis nevén alapul. Ezeknek egyezniük kell. Ha például egy IP-címet ad meg a kiszolgáló nevének, a Power BI Desktopban azt az IP-címet kell használnia az adatforráshoz az átjáró konfigurációján belül. Ha a *KISZOLGÁLÓ\PÉLDÁNY* nevet használja, a Power BI Desktopban ugyanezt kell használnia az átjáróhoz konfigurált adatforráson belül.

Ha szerepel az átjárón belül konfigurált adatforrás **Felhasználók** lapján, és a kiszolgáló és az adatbázis neve egyezik, az átjáró megjelenik lehetőségként az ütemezett frissítésnél.

![](media/service-gateway-enterprise-manage-scheduled-refresh/powerbi-gateway-enterprise-schedule-refresh.png)

> [!WARNING]
> Ha az adatkészlet több adatforrást tartalmaz, az egyes adatforrásokat hozzá kell adni az átjárón belül. Ha egy vagy több adatforrást nem ad hozzá az átjáróhoz, az átjáró nem lesz elérhető ütemezett frissítésre.
> 
> 

## <a name="limitations"></a>Korlátozások
* Az OAuth nem támogatott hitelesítési séma a helyszíni adatátjáróval. Nem vehet fel olyan adatforrásokat, amelyekhez OAuth szükséges. Ha az adatkészlet egy adatforrásához OAuth szükséges, nem fogja tudni ütemezett frissítéshez használni az átjárót.

## <a name="next-steps"></a>Következő lépések
[Helyszíni adatátjáró](service-gateway-onprem.md)  
[Helyszíni adatátjáró – részletek](service-gateway-onprem-indepth.md)  
[A Helyszíni adatátjáróval kapcsolatos hibák elhárítása](service-gateway-onprem-tshoot.md)  
További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

