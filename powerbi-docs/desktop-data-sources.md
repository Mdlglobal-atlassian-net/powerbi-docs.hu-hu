---
title: Adatforrások a Power BI Desktopban
description: Adatforrások a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 10/15/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: a5a4f6532fe127fe01b699ee9d9e89693fdb369e
ms.sourcegitcommit: b8461c1876bfe47bf71c87c7820266993f82c0d3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/15/2018
ms.locfileid: "49336898"
---
# <a name="data-sources-in-power-bi-desktop"></a>Adatforrások a Power BI Desktopban
A Power BI Desktoppal különböző forrásokból származó adatokhoz csatlakozhat. Az elérhető adatforrások teljes listája az oldal alján látható.

Az adatokhoz való csatlakozáshoz válassza a **Kezdőlap** menüszalag **Lekérdezés** lehetőségét. A lefelé mutató nyíl vagy a gomb **Lekérdezés** feliratának kiválasztásával megjelenik a **Leggyakoribb** adattípusok menüje, ahogyan az a következő képen látható:

![Adatok lekérése a Power BI Desktopban](media/desktop-data-sources/data-sources_01.png)

A **Továbbiak...** lehetőség a **Leggyakoribb** menüből való kiválasztásakor megjelenik a **Lekérdezés** ablak. A **Lekérdezés** ablakot (a **Leggyakoribb** menü kihagyásával) a **Lekérdezés** **ikongomb** közvetlen kiválasztásával is megjelenítheti.

![Adatok lekérése gomb](media/desktop-data-sources/data-sources_02.png)

> [!NOTE]
> A Power BI csapata folyamatosan bővíti a **Power BI Desktop** és a **Power BI szolgáltatás** számára elérhető adatforrásokat. Ezért gyakran láthatja majd a fejlesztés alatt álló adatforrások előzetes verzióit *bétaverzió* vagy *előzetes verzió* felirattal. A *bétaverzió* vagy *előzetes verzió* felirattal ellátott adatforrások támogatása és működése korlátozott, használatuk éles környezetben nem ajánlott.
> 
> 

## <a name="data-sources"></a>Adatforrások
Az adattípusok a következő kategóriákba vannak csoportosítva:

* Összes
* Fájl
* Adatbázis
* Power BI
* Azure
* Online szolgáltatások
* Egyéb

A **Mind** kategória az összes kategóriába tartozó adatkapcsolat-típusokat tartalmazza.

A **Fájl** kategória a következő adatkapcsolatokat biztosítja:

* Excel
* Szöveg/CSV
* XML
* JSON
* Mappa
* PDF (bétaverzió)
* SharePoint-mappa

A következő képen a **Lekérdezés** ablak látható, amelyen a **Fájl** kategória ki van választva.

![Lekérdezés > Fájl](media/desktop-data-sources/data-sources_03.png)

Az **Adatbázis** kategória a következő adatkapcsolatokat biztosítja:

* SQL Server-adatbázis
* Access-adatbázis
* SQL Server Analysis Services-adatbázis
* Oracle Database
* IBM DB2-adatbázis
* IBM Informix-adatbázis (bétaverzió)
* IBM Netezza
* MySQL-adatbázis
* PostgreSQL-adatbázis
* Sybase-adatbázis
* Teradata-adatbázis
* SAP HANA-adatbázis
* SAP Business Warehouse-alkalmazáskiszolgáló
* SAP Business Warehouse üzenetkezelési kiszolgáló
* Amazon Redshift
* Impala
* Google BigQuery
* Snowflake
* Dremio (bétaverzió)
* Exasol (bétaverzió)
* Jethro (bétaverzió)
* Kyligence Enterprise (bétaverzió)

> [!NOTE]
> Egyes adatbázis-összekötőket engedélyezni kell a **Fájl > Lehetőségek és beállítások > Beállítások** elem, majd az **Előzetes verziójú funkciók** lehetőség kiválasztásával és az adott összekötő engedélyezésével. Ha a fentiekben említett összekötők nem jelennek meg itt, és használni kívánja őket, ellenőrizze az **Előzetes verziójú funkciók** beállításait. Vegye figyelembe azt is, hogy a *bétaverzió* vagy *előzetes verzió* felirattal ellátott adatforrások támogatása és működése korlátozott, használatuk éles környezetben nem ajánlott.
> 
> 

A következő képen a **Lekérdezés** ablak látható, amelyen az **Adatbázis** kategória ki van választva.

![Lekérdezés > Adatbázisok](media/desktop-data-sources/data-sources_04.png)

A **Power BI** kategória a következő adatkapcsolatokat biztosítja:

* Power BI-adathalmazok
* Power BI-adatfolyamok (bétaverzió)

A következő képen az **Lekérdezés** ablak látható, amelyen az **Power BI** kategória ki van választva.

![Lekérdezés > Power BI](media/desktop-data-sources/data-sources_05.png)

Az **Azure** kategória a következő adatkapcsolatokat biztosítja:

* Azure SQL Database
* Azure SQL Data Warehouse
* Azure Analysis Services-adatbázis
* Azure Blob-tároló
* Azure Table Storage
* Azure Cosmos DB (bétaverzió)
* Azure Data Lake Store
* Azure HDInsight (HDFS)
* Azure HDInsight Spark
* HDInsight interaktív lekérdezés
* Azure KustoDB (bétaverzió)

A következő képen a **Lekérdezés** ablak látható, amelyen az **Azure** kategória ki van választva.

![Lekérdezés > Azure](media/desktop-data-sources/data-sources_06.png)

Az **Online szolgáltatások** kategória a következő adatkapcsolatokat biztosítja:

* SharePoint Online-lista
* Microsoft Exchange Online
* Dynamics 365 (online)
* Dynamics NAV
* Dynamics 365 Business Central
* Dynamics 365 Business Central (helyszíni)
* Common Data Service for Apps (bétaverzió)
* Microsoft Azure – használati elemzés (bétaverzió)
* Visual Studio Team Services (bétaverzió)
* Salesforce-objektumok
* Salesforce-jelentések
* Google Analytics
* Adobe Analytics
* appFigures (bétaverzió)
* comScore Digital Analytix (bétaverzió)
* Dynamics 365 for Customer Insights (bétaverzió)
* Data.World – Adathalmaz lekérése (bétaverzió)
* Facebook
* GitHub (bétaverzió)
* MailChimp (bétaverzió)
* Marketo (bétaverzió)
* Mixpanel (bétaverzió)
* Planview Enterprise One - PRM (bétaverzió)
* Planview Projectplace (bétaverzió)
* QuickBooks Online (bétaverzió)
* Smartsheet
* SparkPost (bétaverzió)
* Stripe (bétaverzió)
* SweetIQ (bétaverzió)
* Planview Enterprise One - CMT (bétaverzió)
* Twilio (bétaverzió)
* tyGraph (bétaverzió)
* Webtrends (bétaverzió)
* Zendesk (bétaverzió)
* TeamDesk (bétaverzió)

A következő képen a **Lekérdezés** ablak látható, amelyen az **Online szolgáltatások** kategória ki van választva.

![Lekérdezés > Online szolgáltatások](media/desktop-data-sources/data-sources_07.png)

Az **Egyéb** kategória a következő adatkapcsolatokat biztosítja:

* Vertica
* Web
* SharePoint-lista
* OData-adatcsatorna
* Active Directory
* Microsoft Exchange
* Hadoop-fájl (HDFS)
* Spark
* R-szkript
* Python-szkript
* ODBC
* OLE DB
* Denado
* Paxata (bétaverzió)
* Üres lekérdezés

A következő képen a **Lekérdezés** ablak látható, amelyen az **Egyéb** kategória ki van választva.

![Lekérdezés > Egyéb](media/desktop-data-sources/data-sources_08.png)

> [!NOTE]
> Jelenleg nem lehetséges olyan egyéni adatforrásokhoz csatlakozni, amelyek védelmét az Azure Active Directory biztosítja.
> 
> 

## <a name="connecting-to-a-data-source"></a>Csatlakozás adatforráshoz
Egy adott adatforráshoz való csatlakozáshoz válassza ki azt a **Lekérdezés** ablakban, majd válassza a **Kapcsolódás** lehetőséget. A következő képen a **Web** lehetőség van kiválasztva az **Egyéb** adatkapcsolat-kategórián belül.

![Webes csatlakozás](media/desktop-data-sources/data-sources_08a.png)

Ekkor megjelenik egy, az adott adatkapcsolatra jellemző csatlakozási ablak. Ha hitelesítő adatok szükségesek, a rendszer ezek megadására kéri. A következő képen a Web típusú adatforráshoz való csatlakozáshoz szükséges URL-cím megadása látható.

![webes URL-cím bevitele](media/desktop-data-sources/datasources_fromwebbox.png)

Az URL-cím vagy az erőforrás csatlakozási adatainak megadása után kattintson az **OK** gombra. A Power BI Desktop csatlakozik az adatforráshoz, és megjeleníti az elérhető adatforrásokat a **Kezelőben**.

![Kezelőképernyő](media/desktop-data-sources/datasources_fromnavigatordialog.png)

Az adatokat betöltheti a **Kezelő** panel alján található **Betöltés** gombbal, vagy szerkesztheti a lekérdezést az adatok betöltése előtt a **Szerkesztés** gombbal.

Ilyen egyszerűen csatlakozhat adatforrásokhoz a Power BI Desktopban. Egyre több adatforrás közül választhat, és a lista folyamatosan bővül, ezért érdemes gyakran visszatérnie.

## <a name="next-steps"></a>Következő lépések
A Power BI Desktop műveletek és lehetőségek széles tárházát tartalmazza. A program képességeivel kapcsolatos további információkért lásd az alábbi forrásanyagokat:

* [Mi az a Power BI Desktop?](desktop-what-is-desktop.md)
* [Lekérdezések áttekintése a Power BI Desktopban](desktop-query-overview.md)
* [Adattípusok a Power BI Desktopban](desktop-data-types.md)
* [Adatok formázása és kombinálása a Power BI Desktoppal](desktop-shape-and-combine-data.md)
* [Gyakori lekérdezési feladatok a Power BI Desktopban](desktop-common-query-tasks.md)    
