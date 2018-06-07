---
title: Telepített jelentéskészítő kiszolgáló migrálása
description: Cikkünkből megtudhatja, hogyan migrálhatja meglévő SQL Server Reporting Services-példányát egy Power BI jelentéskészítő kiszolgálói példányba.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 09/05/2017
ms.author: maghan
ms.openlocfilehash: 0bfad6dba38cce4bd170bb3f3bd7f9a7877b6174
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34480934"
---
# <a name="migrate-a-report-server-installation"></a>Telepített jelentéskészítő kiszolgáló migrálása
Cikkünkből megtudhatja, hogyan migrálhatja meglévő SQL Server Reporting Services-példányát (SSRS-példányát) egy Power BI jelentéskészítő kiszolgálói példányba.

A migráció fogalmán itt az alkalmazás adatfájljainak egy új Power BI jelentéskészítő kiszolgálói példányba való áthelyezését értjük. A telepítés migrálásának hátterében a következő gyakori okok állhatnak:

* Át szeretne térni az SQL Server Reporting Servicesről a Power BI jelentéskészítő kiszolgálóra
  
  > [!NOTE]
  > Az SQL Server Reporting Services telepítéseit nem lehet helyben frissíteni a Power BI jelentéskészítő kiszolgálóra. Migráció szükséges.
  > 
  > 
* Nagy méretű környezetről van szó, vagy frissítési követelményeket kell betartani.
* Módosítja a telepített környezet hardverét vagy topológiáját.
* A frissítést megakadályozó hibába ütközik.

## <a name="migrating-to-power-bi-report-server-from-ssrs-native-mode"></a>Migráció a natív módú SSRS-ről a Power BI jelentéskészítő kiszolgálóra
A natív módú SSRS szolgáltatásnak a Power BI jelentéskészítő kiszolgálóra történő migrálása néhány lépésből áll.

![](media/migrate-report-server/migrate-from-ssrs-native.png "Migráció a natív módú SSRS-ről a Power BI jelentéskészítő kiszolgálóra")

> [!NOTE]
> A migrációt az SQL Server 2008 Reporting Services és újabb verziók esetében támogatjuk.
> 
> 

* Készítse el az adatbázis, az alkalmazás és a konfigurációs fájlok biztonsági másolatát.
* Készítse el a titkosítási kulcsok biztonsági másolatát.
* Klónozza a jelentéseket kezelő jelentéskészítő kiszolgáló adatbázisát.
* Telepítse a Power BI jelentéskészítő kiszolgálót. Ha ugyanazt a hardvert használja, telepítheti a Power BI jelentéskészítő kiszolgálót ugyanarra a kiszolgálóra, mint amelyen az SSRS-példány fut. A Power BI jelentéskészítő kiszolgáló telepítéséről [A Power BI jelentéskészítő kiszolgáló telepítése](install-report-server.md) című cikk nyújt részletesebb tájékoztatást.

> [!NOTE]
> A Power BI jelentéskészítő kiszolgáló példányának neve *PBIRS* lesz.
> 
> 

* Konfigurálja a jelentéskészítő kiszolgálót a Jelentéskészítő kiszolgáló – konfigurációkezelő segítségével, és csatlakozzon a klónozott adatbázishoz.
* Szükség szerint törölje a natív módú SSRS-példány után megmaradó fölösleges elemeket.

## <a name="migration-to-power-bi-report-server-from-ssrs-sharepoint-integrated-mode"></a>SharePoint-integrált módú SSRS migrálása Power BI jelentéskészítő kiszolgálóra
A SharePoint-integrált módú SSRS-t nem olyan egyszerű migrálni Power BI jelentéskészítő kiszolgálóra, mint a natív módút. Az itt közölt lépések szolgálnak ugyan némi útmutatással, a SharePointon belül előfordulhatnak azonban más olyan fájlok és objektumok, amelyeket kezelni kell ezeken a lépéseken túlmenően.

![](media/migrate-report-server/migrate-from-ssrs-sharepoint.png "Migrálás SharePoint-integrált módú SSRS-ről a Power BI jelentéskészítő kiszolgálóra")

Ebben az esetben a jelentéskészítő kiszolgáló egyedi tartalmát kell migrálni a SharePointból a Power BI jelentéskészítő kiszolgálóra. Az eljárás abból indul ki, hogy Ön korábban már telepítette a Power BI jelentéskészítő kiszolgálót valahol a környezetében. A Power BI jelentéskészítő kiszolgáló telepítéséről [A Power BI jelentéskészítő kiszolgáló telepítése](install-report-server.md) című cikk nyújt részletesebb tájékoztatást.

Ha másolni szeretné a jelentéskészítő kiszolgáló tartalmát a SharePoint-környezetéből a Power BI jelentéskészítő kiszolgálóra, akkor eszközök (például az **rs.exe**) segítségével kell másolnia a tartalmat. Az alábbi példa bemutatja, milyen szkripttel másolhatja a jelentéskészítő kiszolgáló tartalmát a SharePointból a Power BI jelentéskészítő kiszolgálóra.

> [!NOTE]
> A példában szereplő szkript a SharePoint 2010 és újabb verziók, illetve az SQL Server 2008 Reporting Services és újabb verziók esetében működik.
> 
> 

### <a name="sample-script"></a>Mintaszkript
```
Sample Script
rs.exe
-i ssrs_migration.rss -e Mgmt2010
-s http://SourceServer/_vti_bin/reportserver
-v st="sites/bi" -v f="Shared Documents“
-u Domain\User1 -p Password
-v ts=http://TargetServer/reportserver
-v tu="Domain\User" -v tp="Password"
```

## <a name="migrateing-from-one-power-bi-report-server-to-another"></a>Migráció egy Power BI jelentéskészítő kiszolgálóról egy másikra
Az egyik Power BI jelentéskészítő kiszolgálóról a másikra történő migráció folyamata megegyezik a natív módú SSRS-ről való migrációéval.

![](media/migrate-report-server/migrate-from-pbirs.png "Power BI jelentéskészítő kiszolgáló migrálása Power BI jelentéskészítő kiszolgálóra")

* Készítse el az adatbázis, az alkalmazás és a konfigurációs fájlok biztonsági másolatát.
* Készítse el a titkosítási kulcsok biztonsági másolatát.
* Klónozza a jelentéseket kezelő jelentéskészítő kiszolgáló adatbázisát.
* Telepítse a Power BI jelentéskészítő kiszolgálót. A Power BI jelentéskészítő kiszolgálót *nem telepítheti* ugyanarra a kiszolgálóra, mint amelyikről migrálja a másikat. A Power BI jelentéskészítő kiszolgáló telepítéséről [A Power BI jelentéskészítő kiszolgáló telepítése](install-report-server.md) című cikk nyújt részletesebb tájékoztatást.

> [!NOTE]
> A Power BI jelentéskészítő kiszolgáló példányának neve *PBIRS* lesz.
> 
> 

* Konfigurálja a jelentéskészítő kiszolgálót a Jelentéskészítő kiszolgáló – konfigurációkezelő segítségével, és csatlakozzon a klónozott adatbázishoz.
* Szükség szerint törölje a Power BI jelentéskészítő kiszolgáló régi telepítése után megmaradó fölösleges elemeket.

## <a name="next-steps"></a>Következő lépések
[Rendszergazdai áttekintés](admin-handbook-overview.md)  
[A Power BI jelentéskészítő kiszolgáló telepítése](install-report-server.md)  
[Az rs.exe segédprogramra és a webszolgáltatásra épülő szkriptek](https://docs.microsoft.com/sql/reporting-services/tools/script-with-the-rs-exe-utility-and-the-web-service)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

