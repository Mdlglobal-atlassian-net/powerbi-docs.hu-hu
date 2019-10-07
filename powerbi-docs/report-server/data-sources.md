---
title: A Power BI-jelentések adatforrásai a Power BI jelentéskészítő kiszolgálón
description: A Power Bi-jelentések számos adatforráshoz csatlakozhatnak. Az adatok használatának módjától függően eltérő adatforrások érhetők el.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/17/2018
ms.author: maggies
ms.openlocfilehash: 9b7f3adfc7702dee36c43308b227baf72328935a
ms.sourcegitcommit: b7a9862b6da940ddebe61bc945a353f91cd0e4bd
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/04/2019
ms.locfileid: "71945831"
---
# <a name="power-bi-report-data-sources-in-power-bi-report-server"></a>A Power BI-jelentések adatforrásai a Power BI jelentéskészítő kiszolgálón
A Power Bi-jelentések számos adatforráshoz csatlakozhatnak. Az adatok használatának módjától függően eltérő adatforrások érhetők el. Az adatok importálhatók, vagy közvetlenül DirectQuery- vagy élő SQL Server Analysis Services-kapcsolattal lehet lekérdezni azokat.

Ezek az adatforrások a Power BI jelentéskészítő kiszolgálón használt adott Power BI-jelentésekkel kapcsolatosak. További információ a többoldalas jelentésekben (.rdl) támogatott adatforrásokról: [A Reporting Services által támogatott adatforrások](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs).

> [!IMPORTANT]
> A Power BI Desktop-jelentésben szereplő összes adatforrásnak támogatnia kell az ütemezett frissítés konfigurálását.
>  

## <a name="list-of-supported-data-sources"></a>Támogatott adatforrások listája

Más adatforrások is működhetnek annak ellenére, hogy a támogatott listán nem szerepelnek.

| **Adatforrás** | **Gyorsítótárban lévő adatok** | **Ütemezett frissítés** | **Élő lekérdezés/DirectQuery** |
| --- | --- | --- | --- |
| SQL Server-adatbázis |Igen |Igen |Igen |
| SQL Server Analysis Services |Igen |Igen |Igen |
| Azure SQL Database |Igen |Igen |Igen |
| Azure SQL Data Warehouse |Igen |Igen |Igen |
| Excel |Igen |Igen |Nem |
| Hozzáférés az adatbázishoz |Igen |Igen |Nem |
| Active Directory |Igen |Igen |Nem |
| Amazon Redshift |Igen |Nem |Nem |
| Azure Blob Storage |Igen |Igen |Nem |
| Azure Data Lake Store |Igen |Nem |Nem |
| Azure HDInsight (HDFS) |Igen |Nem |Nem |
| Azure HDInsight (HDFS) |Igen |Igen |Nem |
| Azure Table Storage |Igen |Igen |Nem |
| Dynamics 365 (online) |Igen |Nem |Nem |
| Facebook |Igen |Nem |Nem |
| Mappa |Igen |Igen |Nem |
| Google Analytics |Igen |Nem |Nem |
| Hadoop-fájl (HDFS) |Igen |Nem |Nem |
| IBM DB2-adatbázis |Igen |Igen |Nem |
| Impala |Igen |Nem |Nem |
| JSON |Igen |Igen |Nem |
| Microsoft Exchange |Igen |Nem |Nem |
| Microsoft Exchange Online |Igen |Nem |Nem |
| MySQL-adatbázis |Igen |Igen |Nem |
| OData-csatorna |Igen |Igen |Nem |
| ODBC |Igen |Igen |Nem |
| OLE DB |Igen |Igen |Nem |
| Oracle Database |Igen |Igen |Igen |
| PostgreSQL-adatbázis |Igen |Igen |Nem |
| Power BI szolgáltatás |Nem |Nem |Nem |
| R szkript |Igen |Nem |Nem |
| Salesforce-objektumok |Igen |Nem |Nem |
| Salesforce-jelentések |Igen |Nem |Nem |
| SAP Business Warehouse-kiszolgáló |Igen |Igen |Igen |
| SAP HANA-adatbázis |Igen |Igen |Igen |
| SharePoint-mappa (helyszíni) |Igen |Igen |Nem |
| SharePoint-lista (helyszíni) |Igen |Igen |Nem |
| SharePoint Online-lista |Igen |Nem |Nem |
| Snowflake |Igen |Nem |Nem |
| Sybase-adatbázis |Igen |Igen |Nem |
| Teradata |Igen |Igen |Igen |
| Szöveges/CSV |Igen |Igen |Nem |
| Webes |Igen |Igen |Nem |
| XML |Igen |Igen |Nem |
| appFigures (bétaverzió) |Igen |Nem |Nem |
| Azure Analysis Services-adatbázis |Igen |Nem |Igen |
| Azure Cosmos DB (bétaverzió) |Igen |Nem |Nem |
| Azure HDInsight Spark (bétaverzió) |Igen |Nem |Nem |
| Common Data Service (bétaverzió) |Igen |Nem |Nem |
| comScore Digital Analytix (bétaverzió) |Igen |Nem |Nem |
| Dynamics 365 for Customer Insights (bétaverzió) |Igen |Nem |Nem |
| Dynamics 365 for Financials (bétaverzió) |Igen |Nem |Nem |
| GitHub (bétaverzió) |Igen |Nem |Nem |
| Google BigQuery (bétaverzió) |Igen |Nem |Nem |
| IBM Informix-adatbázis (bétaverzió) |Igen |Nem |Nem |
| IBM Netezza (bétaverzió) |Igen |Nem |Nem |
| Kusto (bétaverzió) |Igen |Nem |Nem |
| MailChimp (bétaverzió) |Igen |Nem |Nem |
| Microsoft Azure Consumption Insights (bétaverzió) |Igen |Nem |Nem |
| Mixpanel (bétaverzió) |Igen |Nem |Nem |
| Planview Enterprise (bétaverzió) |Igen |Nem |Nem |
| Projectplace (bétaverzió) |Igen |Nem |Nem |
| QuickBooks Online (bétaverzió) |Igen |Nem |Nem |
| Smartsheet |Igen |Nem |Nem |
| Spark (bétaverzió) |Igen |Nem |Nem |
| SparkPost (bétaverzió) |Igen |Nem |Nem |
| SQL Sentry (bétaverzió) |Igen |Nem |Nem |
| Stripe (bétaverzió) |Igen |Nem |Nem |
| SweetIQ (bétaverzió) |Igen |Nem |Nem |
| Troux (bétaverzió) |Igen |Nem |Nem |
| Twilio (bétaverzió) |Igen |Nem |Nem |
| tyGraph (bétaverzió) |Igen |Nem |Nem |
| Vertica (bétaverzió) |Igen |Nem |Nem |
| Visual Studio Team Services (bétaverzió) |Igen |Nem |Nem |
| Webtrends (bétaverzió) |Igen |Nem |Nem |
| Zendesk (bétaverzió) |Igen |Nem |Nem |

> [!IMPORTANT]
> Az adatforrásnál konfigurált sorszintű biztonság működik egyes DirectQuery- (SQL Server, az Azure SQL Database, Oracle és Teradata) és élő kapcsolatokkal, feltéve, hogy a Kerberos megfelelően van konfigurálva a környezetben.
> 
> 

## <a name="list-of-supported-authentication-methods-for-model-refresh"></a>A modellfrissítéshez támogatott hitelesítési módszerek listája

A Power BI jelentéskészítő kiszolgáló nem támogatja az OAuth-alapú hitesítéssel végzett modellfrissítést. Egyes adatforrások, köztük az Excel- és az Access-adatbázisok, egy további lépést (például Fájl vagy Web) is használnak az adatokhoz való csatlakozás során.

| **Adatforrás** | **Névtelen hitelesítés** | **Kulcsos hitelesítés** | **Felhasználónév és jelszó** | **Windows-hitelesítés** |
| --- | --- | --- | --- | --- |
| SQL Server-adatbázis |Nem |Nem |Igen |Igen |
| SQL Server Analysis Services |Nem |Nem |Igen |Igen |
| Web |Igen |Nem |Igen |Igen |
| Azure SQL Database |Nem |Nem |Igen |Nem |
| Azure SQL Data Warehouse |Nem |Nem |Igen |Nem |
| Active Directory |Nem |Nem |Igen |Igen |
| Amazon Redshift |Nem |Nem |Nem |Nem |
| Azure Blob Storage |Igen |Igen |Nem |Nem |
| Azure Data Lake Store |Nem |Nem |Nem |Nem |
| Azure HDInsight (HDFS) |Nem |Nem |Nem |Nem |
| Azure HDInsight (HDFS) |Igen |Igen |Nem |Nem |
| Azure Table Storage |Nem |Igen |Nem |Nem |
| Dynamics 365 (online) |Nem |Nem |Nem |Nem |
| Facebook |Nem |Nem |Nem |Nem |
| Mappa |Nem |Nem |Nem |Igen |
| Google Analytics |Nem |Nem |Nem |Nem |
| Hadoop-fájl (HDFS) |Nem |Nem |Nem |Nem |
| IBM DB2-adatbázis |Nem |Nem |Igen |Igen |
| Impala |Nem |Nem |Nem |Nem |
| Microsoft Exchange |Nem |Nem |Nem |Nem |
| Microsoft Exchange Online |Nem |Nem |Nem |Nem |
| MySQL-adatbázis |Nem |Nem |Igen |Igen |
| OData-adatcsatorna |Igen |Igen |Igen |Igen |
| ODBC |Igen |Nem |Igen |Igen |
| OLE DB |Igen |Nem |Igen |Igen |
| Oracle Database |Nem |Nem |Igen |Igen |
| PostgreSQL-adatbázis |Nem |Nem |Igen |Nem |
| Power BI szolgáltatás |Nem |Nem |Nem |Nem |
| R-szkript |Nem |Nem |Nem |Nem |
| Salesforce-objektumok |Nem |Nem |Nem |Nem |
| Salesforce-jelentések |Nem |Nem |Nem |Nem |
| SAP Business Warehouse-kiszolgáló |Nem |Nem |Igen |Nem |
| SAP HANA-adatbázis |Nem |Nem |Igen |Igen |
| SharePoint-mappa (helyszíni) |Igen |Nem |Nem |Igen |
| SharePoint-lista (helyszíni) |Igen |Nem |Nem |Igen |
| SharePoint Online-lista |Nem |Nem |Nem |Nem |
| Snowflake |Nem |Nem |Nem |Nem |
| Sybase-adatbázis |Nem |Nem |Igen |Igen |
| Teradata |Nem |Nem |Igen |Igen |
| appFigures (bétaverzió) |Nem |Nem |Nem |Nem |
| Azure Analysis Services-adatbázis (bétaverzió) |Nem |Nem |Nem |Nem |
| Azure Cosmos DB (bétaverzió) |Nem |Nem |Nem |Nem |
| Azure HDInsight Spark (bétaverzió) |Nem |Nem |Nem |Nem |
| Common Data Service (bétaverzió) |Nem |Nem |Nem |Nem |
| comScore Digital Analytix (bétaverzió) |Nem |Nem |Nem |Nem |
| Dynamics 365 for Customer Insights (bétaverzió) |Nem |Nem |Nem |Nem |
| Dynamics 365 for Financials (bétaverzió) |Nem |Nem |Nem |Nem |
| GitHub (bétaverzió) |Nem |Nem |Nem |Nem |
| Google BigQuery (bétaverzió) |Nem |Nem |Nem |Nem |
| IBM Informix-adatbázis (bétaverzió) |Nem |Nem |Nem |Nem |
| IBM Netezza (bétaverzió) |Nem |Nem |Nem |Nem |
| Kusto (bétaverzió) |Nem |Nem |Nem |Nem |
| MailChimp (bétaverzió) |Nem |Nem |Nem |Nem |
| Microsoft Azure Consumption Insights (bétaverzió) |Nem |Nem |Nem |Nem |
| Mixpanel (bétaverzió) |Nem |Nem |Nem |Nem |
| Planview Enterprise (bétaverzió) |Nem |Nem |Nem |Nem |
| Projectplace (bétaverzió) |Nem |Nem |Nem |Nem |
| QuickBooks Online (bétaverzió) |Nem |Nem |Nem |Nem |
| Smartsheet |Nem |Nem |Nem |Nem |
| Spark (bétaverzió) |Nem |Nem |Nem |Nem |
| SparkPost (bétaverzió) |Nem |Nem |Nem |Nem |
| SQL Sentry (bétaverzió) |Nem |Nem |Nem |Nem |
| Stripe (bétaverzió) |Nem |Nem |Nem |Nem |
| SweetIQ (bétaverzió) |Nem |Nem |Nem |Nem |
| Troux (bétaverzió) |Nem |Nem |Nem |Nem |
| Twilio (bétaverzió) |Nem |Nem |Nem |Nem |
| tyGraph (bétaverzió) |Nem |Nem |Nem |Nem |
| Vertica (bétaverzió) |Nem |Nem |Nem |Nem |
| Visual Studio Team Services (bétaverzió) |Nem |Nem |Nem |Nem |
| Webtrends (bétaverzió) |Nem |Nem |Nem |Nem |
| Zendesk (bétaverzió) |Nem |Nem |Nem |Nem |

## <a name="list-of-supported-authentication-methods-for-directquery"></a>A DirectQueryhez támogatott hitelesítési módszerek listája

A Power BI jelentéskészítő kiszolgáló nem támogatja az OAuth-alapú hitesítést DirectQueryhez.

| **Adatforrás** | **Névtelen hitelesítés** | **Kulcsos hitelesítés** | **Felhasználónév és jelszó** | **Windows-hitelesítés** | **Integrált Windows-hitelesítés** |
| --- | --- | --- | --- | --- | --- |
| SQL Server-adatbázis |Nem |Nem |Igen |Igen |Igen |
| SQL Server Analysis Services |Nem |Nem |Igen |Igen |Igen |
| Azure SQL Database |Nem |Nem |Igen |Nem |Nem |
| Azure SQL Data Warehouse |Nem |Nem |Igen |Nem |Nem |
| Oracle Database |Nem |Nem |Igen |Igen |Igen |
| SAP Business Warehouse-kiszolgáló |Nem |Nem |Igen |Nem |Nem |
| SAP HANA-adatbázis |Nem |Nem |Igen |Igen |Nem |
| Teradata |Nem |Nem |Igen |Igen |Igen |


## <a name="next-steps"></a>Következő lépések
Most, hogy csatlakozott az adatforráshoz, az abból származó adatokat használva [hozzon létre egy Power BI-jelentést](quickstart-create-powerbi-report.md).

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

