---
title: A Power BI jelentéskészítő kiszolgáló telepítésének hardver- és szoftverkövetelményei
description: Ez a cikk a Power BI jelentéskészítő kiszolgáló telepítésének és futtatásának minimális hardver- és szoftverkövetelményeit ismerteti.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/21/2020
ms.openlocfilehash: 7b8c106f13df381152b6323cf1263747a3064709
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/23/2020
ms.locfileid: "76540567"
---
# <a name="hardware-and-software-requirements-for-installing-power-bi-report-server"></a>A Power BI jelentéskészítő kiszolgáló telepítésének hardver- és szoftverkövetelményei

Ez a cikk a Power BI jelentéskészítő kiszolgáló telepítésének és futtatásának minimális hardver- és szoftverkövetelményeit ismerteti.

## <a name="processor-memory-and-operating-system-requirements"></a>Processzorra, memóriára és operációs rendszerre vonatkozó követelmények

| Összetevő | Követelmény |
| --- | --- |
| NET-keretrendszer |4.6<br><br>A .NET-keretrendszert [A Windowshoz készült Microsoft .NET-keretrendszert 4.6-os verziója (webes telepítő)](https://support.microsoft.com/kb/3045560) című cikkből telepítheti manuálisan.<br/><br/> A .NET-keretrendszerrel kapcsolatos további információkért, ajánlásokért és útmutatókért tekintse meg [A .NET-keretrendszer 4.6-os verziójának üzembe helyezési útmutatója fejlesztőknek](https://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx) című cikket.<br/><br/>Windows 8.1 és Windows Server 2012 R2 rendszereken telepítenie kell a [KB2919355](https://support.microsoft.com/kb/2919355) frissítést a .NET-keretrendszer 4.6-os verziójának telepítése előtt. |
| Merevlemez |A Power BI jelentéskészítő kiszolgáló működéséhez legalább 1 GB szabad lemezterület szükséges.<br><br>További lemezterület szükséges a jelentéskészítő kiszolgáló adatbázisát üzemeltető adatbázis-kiszolgálón. |
| Memória |**Minimális:** 1 GB<br/><br/> **Ajánlott:** Legalább 4 GB |
| Processzor sebessége |**Minimum:** 64 bites processzor: 1,4 GHz<br/><br/> **Ajánlott:** 2,0 GHz vagy gyorsabb |
| Processzor típusa |64 bites processzor: AMD Opteron, AMD Athlon 64, Intel Xeon Intel EM64T-támogatással, Intel Pentium IV EM64T-támogatással |
| Operációs rendszer |Windows Server 2019 Datacenter<br><br>Windows Server 2019 Standard<br><br>Windows Server 2016 Datacenter<br><br>Windows Server 2016 Standard<br><br>Windows Server 2012 R2 Datacenter<br><br>Windows Server 2012 R2 Standard<br><br>Windows Server 2012 R2 Essentials<br><br>Windows Server 2012 R2 Foundation<br><br>Windows Server 2012 Datacenter<br><br>Windows Server 2012 Standard<br><br>Windows Server 2012 Essentials<br><br>Windows Server 2012 Foundation<br><br>Windows 10 Home<br><br>Windows 10 Professional<br><br>Windows 10 Enterprise<br><br>Windows 8.1<br><br>Windows 8.1 Pro<br><br>Windows 8.1 Enterprise<br><br>Windows 8<br><br>Windows 8 Pro<br><br>Windows 8 Enterprise |

> [!NOTE]
> A Power BI jelentéskészítő kiszolgáló telepítése csak 64 bites processzorok esetén támogatott.


## <a name="database-server-version-requirements"></a>Az adatbázis-kiszolgáló verziójával kapcsolatos követelmények

A jelentéskészítő kiszolgáló adatbázisának üzemeltetése SQL Serveren történik. Az SQL Server adatbázismotor-példánya helyi vagy távoli példány lehet. A jelentéskészítő kiszolgáló adatbázisának üzemeltetését a következő verziójú SQL Server-adatbázismotorok támogatják:

* SQL Server 2019
* SQL Server 2017
* SQL Server 2016
* SQL Server 2014
* SQL Server 2012

Ha a jelentéskészítő kiszolgáló adatbázisát egy távoli számítógépen szeretné létrehozni, akkor úgy kell konfigurálnia a kapcsolatot, hogy az egy tartományi felhasználói fiókot vagy pedig egy hálózati hozzáféréssel rendelkező szolgáltatási fiókot használjon. Ha úgy dönt, hogy egy távoli SQL Server-példányt használ, fontolja meg alaposan, hogy a jelentéskészítő kiszolgáló mely hitelesítő adatokkal kapcsolódjon az SQL Server-példányhoz. További információkért tekintse meg a [Jelentéskészítő kiszolgáló adatbázis-kapcsolatának konfigurációja](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager) című cikket.

## <a name="considerations"></a>Megfontolandó szempontok

A Power BI jelentéskészítő kiszolgáló az alapvető beállításokat a működéséhez szükséges alapértelmezett értékekkel telepíti. Ehhez a következő követelményeknek kell teljesülniük:

* A Power BI jelentéskészítő kiszolgáló támogatott nyelvei: angol, német, spanyol, japán, olasz, francia, orosz, kínai (egyszerűsített), kínai (hagyományos), portugál (brazíliai), koreai
* Rendelkezésre kell állnia egy SQL Server adatbázismotornak a jelentéskészítő kiszolgáló telepítése után, de még a jelentéskészítő kiszolgáló adatbázisának konfigurációja előtt. A jelentéskészítő kiszolgáló adatbázisát, amelyet a Reporting Services konfigurációkezelő fog létrehozni, az adatbázismotor-példány üzemelteti. A tényleges telepítési felületen nem szükséges az adatbázismotor megadása.
* A [Reporting Services Features Supported by the Editions of SQL Server](https://docs.microsoft.com/sql/reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016) (Az SQL Server kiadásai által támogatott Reporting Services-funkciók) az SQL Server kiadásai közötti különbségeket ismerteti.
* A telepítés futtatásához használt felhasználói fióknak a helyi Rendszergazdák csoport tagjának kell lennie.
* A Reporting Services konfigurációkezelőhöz használt felhasználói fióknak engedéllyel kell rendelkeznie adatbázisok létrehozásához és az adatbázisokhoz történő hozzáféréshez a jelentéskészítő kiszolgáló adatbázisát üzemeltető adatbázismotor-példányon.
* A telepítésnek működnie kell az alapértelmezett értékekkel, hogy bejegyezhesse a jelentéskészítő kiszolgáló és a webes portál elérését biztosító URL-címeket. Ezek az értékek a 80-as port, egy erős helyettesítő, és a **ReportServer** és **Reports** formátumú virtuális könyvtárnevek.

## <a name="read-only-domain-controller-rodc"></a>Írásvédett tartományvezérlő (RODC)

 A jelentéskészítő kiszolgálót telepítheti olyan környezetben, amely írásvédett tartományvezérlővel (RODC) rendelkezik. A Reporting Servicesnek azonban a megfelelő működéshez hozzáféréssel kell rendelkeznie egy írható és olvasható tartományvezérlőhöz. Ha a Reporting Services csak egy írásvédett tartományvezérlőhöz (RODC-hez) fér hozzá, akkor a szolgáltatás adminisztrálása során hibákat tapasztalhat.

## <a name="power-bi-reports-and-analysis-services-live-connections"></a>Power BI-jelentések és az Analysis Services élő kapcsolatai

Az élő kapcsolatokat táblázatos vagy többdimenziós példányokhoz használhatja. A megfelelő működéshez megfelelő verziójú és kiadású Analysis Services-kiszolgáló szükséges.

| **Kiszolgáló verziója** | **Kötelező termékváltozat** |
| --- | --- |
| 2012 SP1 CU4 vagy újabb |Business Intelligence és Enterprise termékváltozat |
| 2014 |Business Intelligence és Enterprise termékváltozatok |
| 2016 vagy újabb |Standard vagy magasabb szintű termékváltozat |

## <a name="next-steps"></a>Következő lépések

[Mi a Power BI jelentéskészítő kiszolgáló?](get-started.md)  
[Rendszergazdai áttekintés](admin-handbook-overview.md)  
[A Power BI jelentéskészítő kiszolgáló telepítése](install-report-server.md)  
[A Jelentéskészítő letöltése](https://www.microsoft.com/download/details.aspx?id=53613)  
[Az SQL Server Data Tools (SSDT) letöltése](https://go.microsoft.com/fwlink/?LinkID=616714)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
