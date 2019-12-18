---
title: Adatforrások a Power BI-hoz
description: Ez a cikk felsorolja a Power BI által támogatott adatforrásokat, beleértve a DirectQueryvel és a helyszíni adatátjáróval kapcsolatos információkat is.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/22/2019
ms.author: kfollis
ms.openlocfilehash: be7f95b2bbbd6e5e6314c7fd57869a30c176746c
ms.sourcegitcommit: 320d83ab392ded71bfda42c5491acab3d9d357b0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/10/2019
ms.locfileid: "74958494"
---
# <a name="power-bi-data-sources"></a>Adatforrások a Power BI-hoz

Az alábbi táblázat bemutatja a Power BI által támogatott adatforrásokat adatkészletek használatához, beleértve a DirectQueryvel és a helyszíni adatátjáróval kapcsolatos információkat is. Az adatfolyamokkal kapcsolatos további információért lásd: [Adatforrásokhoz való csatlakozás Power BI-adatfolyamokkal](service-dataflows-data-sources.md).

| Adatforrás | Csatlakozás asztali gépről | Csatlakozás és frissítés szolgáltatásból | DirectQuery / Élő kapcsolat | Átjáró (támogatott) | Átjáró (szükséges) |
|---|---|---|---|---|---|---|---|
| Access-adatbázis | Igen | Igen | Nem | Igen <sup>1</sup> | Igen |
| ActiveDirectory | Igen | Igen | Nem | Igen | Igen |
| Adobe Analytics | Igen | Igen | Nem | Nem | Nem |
| Amazon Redshift | Igen | Igen | Igen | Igen | Nem |
| appFigures | Igen | Igen | Nem | Nem | Nem |
| AtScale-kockák | Igen | Igen | Igen | Igen | Nem |
| Azure Analysis Services | Igen | Igen | Igen | Igen <sup>2</sup> | Nem |
| Azure Blob Storage | Igen | Igen | Nem | Igen | Nem |
| Azure Cosmos DB | Igen | Igen | Nem | Nem | Nem |
| Azure Cost Management | Igen | Igen | Nem | Nem | Nem |
| Azure Data Explorer (Kusto) | Igen | Igen | Igen | Nem | Nem |
| Azure Data Lake Storage Gen1 | Igen | Igen | Nem | Nem | Nem |
| Azure Data Lake Storage Gen2 | Igen | Igen | Nem | Nem | Nem |
| Azure DevOps | Igen | Igen | Nem | Nem | Nem |
| Azure DevOps Server | Igen | Igen | Nem | Igen | Igen |
| Azure HDInsight (HDFS) | Igen | Igen | Nem | Nem | Nem |
| Azure HDInsight Spark | Igen | Igen | Igen | Nem | Nem |
| Azure SQL Database | Igen | Igen | Igen | Igen <sup>2</sup> | Nem |
| Azure SQL Data Warehouse | Igen | Igen | Igen | Nem | Nem |
| Azure Table Storage | Igen | Igen | Nem | Igen | Nem |
| BI-összekötő | Igen | Igen | Igen | Igen | Igen |
| BI360 - Budgeting & Financial Reporting | Igen | Igen | Nem | Nem | Nem |
| Common Data Service | Igen | Igen | Nem | Nem | Nem |
| Data.World – Adathalmaz lekérése | Igen | Igen | Nem | Nem | Nem |
| Denodo | Igen | Igen | Igen | Igen | Igen |
| Dremio | Igen | Igen | Igen | Igen | Igen |
| Dynamics 365 (online) | Igen | Igen | Nem | Nem | Nem |
| Dynamics 365 Business Central | Igen | Igen | Nem | Nem | Nem |
| Dynamics 365 Business Central (helyszíni) | Igen | Igen | Nem | Nem | Nem |
| Dynamics 365 Customer Insights | Igen | Igen | Nem | Nem | Nem |
| Dynamics NAV | Igen | Igen | Nem | Nem | Nem |
| Emigo-adatforrás | Igen | Igen | Nem | Nem | Nem |
| Entersoft Business Suite | Igen | Igen | Nem | Nem | Nem |
| Essbase | Igen | Igen | Igen | Igen | Igen |
| Exasol | Igen | Igen | Igen | Igen | Igen |
| Excel | Igen <sup>3</sup> | Igen <sup>3</sup> | Nem | Igen <sup>3</sup> | Nem <sup>4</sup> |
| Facebook | Igen | Igen | Nem | Nem | Nem |
| Fájl | Igen | Igen | Nem | Igen | Igen |
| Mappa | Igen | Igen | Nem | Igen | Igen |
| GitHub | Igen | Igen | Nem | Nem | Nem |
| Google Analytics | Igen | Igen | Nem | Nem | Nem |
| Google BigQuery | Igen | Igen | Nem | Nem | Nem |
| Hadoop-fájl (HDFS) | Igen | Nem | Nem | Nem | Nem |
| HDInsight interaktív lekérdezés | Igen | Igen | Igen | Nem | Nem |
| IBM DB2 | Igen | Igen | Igen | Igen | Igen |
| IBM Informix-adatbázis | Igen | Igen | Nem | Igen | Igen |
| IBM Netezza | Igen | Igen | Igen | Igen | Igen |
| Impala | Igen | Igen | Igen | Igen | Igen |
| Indexima | Igen | Igen | Igen | Igen | Igen |
| Industrial App Store | Igen | Igen | Nem | Nem | Nem |
| Information Grid | Igen | Igen | Nem | Nem | Nem |
| InterSystems IRIS | Igen | Igen | Igen | Igen | Igen |
| Intune Data Warehouse | Igen | Igen | Nem | Nem | Nem |
| Jethro ODBC | Igen | Igen | Igen | Igen | Igen |
| JSON | Igen | Igen | Nem | Igen** | Nem <sup>4</sup> |
| Kyligence Enterprise | Igen | Igen | Igen | Igen | Igen |
| MailChimp | Igen | Igen | Nem | Nem | Nem |
| Marketo | Igen | Igen | Nem | Nem | Nem |
| MarkLogic ODBC | Igen | Igen | Igen | Igen | Igen |
| Microsoft Azure – használati elemzés | Igen | Igen | Nem | Nem | Nem |
| Microsoft Exchange | Igen | Igen | Nem | Igen | Nem |
| Microsoft Exchange Online | Igen | Igen | Nem | Nem | Nem |
| Microsoft Graph Security | Igen | Igen | Nem | Igen | Nem |
| Mixpanel | Igen | Igen | Nem | Nem | Nem |
| MySQL | Igen | Igen | Nem | Igen | Igen |
| OData | Igen | Igen | Nem | Igen | Nem |
| ODBC | Igen | Igen | Nem | Igen | Igen |
| OleDb | Igen | Igen | Nem | Igen | Igen |
| Oracle | Igen | Igen | Igen | Igen | Igen |
| Paxata | Igen | Igen | Nem | Igen | Nem |
| PDF | Igen | Igen | Nem | Igen | Nem <sup>4</sup> |
| Planview Enterprise One – CTM | Igen | Igen | Nem | Nem | Nem |
| Planview Enterprise One – PRM | Igen | Igen | Nem | Nem | Nem |
| Planview Projectplace | Igen | Igen | Nem | Nem | Nem |
| PostgreSQL | Igen | Igen | Igen | Igen | Igen |
| Power BI-adatfolyamok | Igen | Igen | Nem | Nem | Nem |
| Power BI-adathalmazok | Igen | Igen | Igen | Nem | Nem |
| Power Platform-adatfolyamok | Igen | Igen | Nem | Nem | Nem |
| Python-szkript | Igen | Igen <sup>5</sup> | Nem | Igen <sup>5</sup> | Igen |
| QubolePresto | Igen | Igen | Igen | Igen | Igen |
| Quick Base | Igen | Igen | Nem | Igen | Igen |
| QuickBooks Online | Igen | Igen | Nem | Nem | Nem |
| R-szkript | Igen | Igen <sup>5</sup> | Nem | Igen <sup>5</sup> | Nem |
| Roamler | Igen | Igen | Nem | Igen | Nem |
| Salesforce-objektumok | Igen | Igen | Nem | Nem | Nem |
| Salesforce-jelentések | Igen | Igen | Nem | Nem | Nem |
| SAP Business Warehouse üzenetkezelési kiszolgáló | Igen | Igen | Igen | Igen | Igen |
| SAP Business Warehouse-kiszolgáló | Igen | Igen | Igen | Igen | Igen |
| SAP HANA | Igen | Igen | Igen | Igen | Igen |
| SharePoint-mappa | Igen | Igen | Nem | Igen | Nem <sup>4</sup> |
| SharePoint-lista | Igen | Igen | Nem | Igen | Nem <sup>4</sup> |
| SharePoint Online-lista | Igen | Igen | Nem | Igen <sup>2</sup> | Nem |
| Smartsheet | Igen | Igen | Nem | Nem | Nem |
| Snowflake | Igen | Igen | Igen | Igen | Igen |
| Spark | Igen | Igen | Igen | Igen | Nem |
| SparkPost | Igen | Igen | Nem | Nem | Nem |
| SQL Server | Igen | Igen | Igen | Igen | Igen |
| SQL Server Analysis Services | Igen | Igen | Igen | Igen | Igen |
| Stripe | Igen | Igen | Nem | Nem | Nem |
| SurveyMonkey | Igen | Igen | Nem | Igen | Nem |
| SweetIQ | Igen | Igen | Nem | Nem | Nem |
| Sybase | Igen | Igen | Nem | Igen | Igen |
| TeamDesk | Igen | Igen | Nem | Igen | Nem |
| Tenforce | Igen | Igen | Nem | Nem | Nem |
| Teradata | Igen | Igen | Igen | Igen | Igen |
| Szöveges/CSV | Igen | Igen | Nem | Igen | Nem <sup>4</sup> |
| Twilio | Igen | Igen | Nem | Nem | Nem |
| tyGraph | Igen | Igen | Nem | Nem | Nem |
| Vertica | Igen | Igen | Igen | Igen | Igen |
| Web | Igen | Igen | Nem | Igen | Igen |
| Webtrends | Igen | Igen | Nem | Nem | Nem |
| Workforce Dimensions | Igen | Igen | Nem | Igen | Nem |
| XML | Igen | Igen | Nem | Igen | Nem <sup>4</sup> |
| Zendesk | Igen | Igen | Nem | Nem | Nem |
| | | | | | | | |

<sup>1</sup>Az [ACE OLEDB-szolgáltató](https://www.microsoft.com/download/details.aspx?id=54920) támogatja, amely ugyanarra a gépre van telepítve, mint az átjáró.

<sup>2</sup>A helyszíni verzióéval megegyező M függvény támogatja.

<sup>3</sup>Az Excel 1997–2003-fájlokhoz (.xls) szükséges az [ACE OLEDB-szolgáltató](https://www.microsoft.com/download/details.aspx?id=54920).

<sup>4</sup>A technológia helyszíni verziójához szükséges.

<sup>5</sup>Csak a [személyes átjáróval](service-gateway-personal-mode.md) támogatott.

## <a name="single-sign-on-sso-for-directquery-sources"></a>Egyszeri bejelentkezés (SSO) DirectQuery-forrásokhoz

Ha az egyszeri bejelentkezési beállítás engedélyezve van, és a felhasználók használják az adatforrásra épülő jelentéseket, a Power BI elküldi a hitelesített Azure AD-beli hitelesítő adataikat a lekérdezésekben a mögöttes adatforrásnak. Ez lehetővé teszi a Power BI számára, hogy figyelembe vegye az adatforrás szintjén konfigurált biztonsági beállításokat.
Az egyszeri bejelentkezési beállítás az adatforrást használó összes adathalmazra érvényes lesz. Az importálási forgatókönyvekhez használt hitelesítési módszerre nincs hatással. Az alábbi adatforrások támogatják az egyszeri bejelentkezést a DirectQuery-n keresztüli kapcsolatokhoz:

- Azure SQL Database
- Azure SQL Data Warehouse
- Impala
- SAP HANA
- SAP BW
- SAP BW-üzenetkiszolgáló
- Spark
- SQL Server
- Teradata

> [!Note]
> Az Azure Multi-Factor Authentication (MFA) nem támogatott. Azokat a felhasználókat, akik egyszeri bejelentkezést kívánnak használni a DirectQueryvel, ki kell vonni az MFA hatálya alól.

## <a name="next-steps"></a>Következő lépések

[Csatlakozás adatokhoz a Power BI Desktopban](desktop-quickstart-connect-to-data.md)  
[DirectQuery használata a Power BI-ban](desktop-directquery-about.md)  
[Az SQL Server Analysis Services élő adatai a Power BI-ban](sql-server-analysis-services-tabular-data.md)  
[Mi az a helyszíni adatátjáró?](service-gateway-onprem.md)  
