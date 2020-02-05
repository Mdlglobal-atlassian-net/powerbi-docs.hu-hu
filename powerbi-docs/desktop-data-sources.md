---
title: Adatforrások a Power BI Desktopban
description: Adatforrások a Power BI Desktopban
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/09/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 0cf9d6acd4fe5f729dafb575a2ab736b9e8db7bb
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/04/2020
ms.locfileid: "76039836"
---
# <a name="data-sources-in-power-bi-desktop"></a>Adatforrások a Power BI Desktopban

A Power BI Desktoppal különböző forrásokból származó adatokhoz csatlakozhat. Az elérhető adatforrások teljes listáját az [Adatforrások a Power BI-hoz](power-bi-data-sources.md) című szakaszban találja.

Az adatokhoz a **Kezdőlap** menüszalagon csatlakozhat. A **leggyakoribb** adattípusok menüjének megjelenítéséhez válassza az **Adatok lekérése** gombot vagy a lefelé mutató nyilat.

![A leggyakoribb adattípusok menü, Adatok lekérése a Power BI Desktopban](media/desktop-data-sources/data-sources-01.png)

Az **Adatok lekérése** párbeszédpanel megnyitásához jelenítse meg a **Leggyakoribb** adattípusok menüjét, majd válassza a **Továbbiak** lehetőséget. Az **Adatok lekérése** párbeszédpanelt (a **Leggyakoribb** menü kihagyásával) az **Adatok lekérése** ikon közvetlen kiválasztásával is megjelenítheti.

![Adatok lekérése gomb, Power BI Desktop](media/desktop-data-sources/data-sources-02.png)

> [!NOTE]
> A Power BI csapata folyamatosan bővíti a Power BI Desktop és a Power BI szolgáltatás számára elérhető adatforrásokat. Ezért gyakran láthatja majd a fejlesztés alatt álló adatforrások előzetes verzióit **bétaverzió** vagy **előzetes verzió** felirattal. A **bétaverzió** vagy **előzetes verzió** felirattal ellátott adatforrások támogatása és működése korlátozott, használatuk éles környezetben nem ajánlott. Emellett a Power BI Desktophoz **béta-** vagy **előzetes verzióként** megjelölt adatforrások nem feltétlenül használhatók a Power BI szolgáltatásban vagy más Microsoft-szolgáltatásban, amíg az adatforrás általánosan elérhető nem lesz.

> [!NOTE]
> A Power BI Desktophoz számos olyan adatösszekötő érhető el, amelyek hitelesítéséhez az Internet Explorer 10 vagy újabb verziójára van szükség. 


## <a name="data-sources"></a>Adatforrások

Az **Adatok lekérése** párbeszédpanel a következő kategóriákba rendezi az adattípusokat:

* Az összes
* Fájl
* Adatbázis
* Power Platform
* Azure
* Online szolgáltatások
* Egyéb

A **Mind** kategória az összes kategóriába tartozó adatkapcsolat-típusokat tartalmazza.

### <a name="file-data-sources"></a>Fájlok adatforrásai

A **Fájl** kategória a következő adatkapcsolatokat biztosítja:

* Excel
* Szöveg/CSV
* XML
* JSON
* Mappa
* PDF
* SharePoint-mappa

A következő képen a **Lekérdezés** ablak látható, amelyen a **Fájl** kategória ki van választva.

![Fájlok adatforrásai, Adatok lekérése párbeszédpanel, Power BI Desktop](media/desktop-data-sources/data-sources-03.png)

### <a name="database-data-sources"></a>Adatbázisok adatforrásai

Az **Adatbázis** kategória a következő adatkapcsolatokat biztosítja:

* SQL Server-adatbázis
* Access-adatbázis
* SQL Server Analysis Services-adatbázis
* Oracle-adatbázis
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
* Vertica
* Snowflake
* Essbase
* AtScale-kockák (bétaverzió)
* BI-összekötő
* Denodo
* Dremio
* Exasol
* Indexima (bétaverzió)
* InterSystems IRIS (bétaverzió)
* Jethro (bétaverzió)
* Kyligence
* MarkLogic

> [!NOTE]
> Egyes adatbázis-összekötőket engedélyezni kell a **Fájl > Lehetőségek és beállítások > Beállítások** elem, majd az **Előzetes verziójú funkciók** lehetőség kiválasztásával és az adott összekötő engedélyezésével. Ha a fentiekben említett összekötők nem jelennek meg itt, és használni kívánja őket, ellenőrizze az **Előzetes verziójú funkciók** beállításait. Vegye figyelembe azt is, hogy a *bétaverzió* vagy *előzetes verzió* felirattal ellátott adatforrások támogatása és működése korlátozott, használatuk éles környezetben nem ajánlott.

A következő képen a **Lekérdezés** ablak látható, amelyen az **Adatbázis** kategória ki van választva.

![Adatbázisok adatforrásai, Adatok lekérése párbeszédpanel, Power BI Desktop](media/desktop-data-sources/data-sources-04.png)

### <a name="power-platform-data-sources"></a>Power Platform-adatforrások

A **Power Platform** kategória a következő adatkapcsolatokat biztosítja:

* Power BI-adathalmazok
* Power BI-adatfolyamok
* Common Data Service
* Power Platform-adatfolyamok

A következő képen a **Lekérdezés** ablak látható, amelyen a **Power Platform** kategória van kiválasztva.

![Power Platform-adatforrások, Adatok lekérése párbeszédpanel, Power BI Desktop](media/desktop-data-sources/data-sources-05.png)

### <a name="azure-data-sources"></a>Azure-beli adatforrások

Az **Azure** kategória a következő adatkapcsolatokat biztosítja:

* Azure SQL-adatbázis
* Azure SQL Data Warehouse
* Azure Analysis Services-adatbázis
* Azure Blob-tároló
* Azure Table Storage
* Azure Cosmos DB
* Azure Data Lake Storage Gen2
* Azure Data Lake Storage Gen1
* Azure HDInsight (HDFS)
* Azure HDInsight Spark
* HDInsight interaktív lekérdezés
* Azure Data Explorer (Kusto)
* Azure Cost Management
* Azure Time Series Insights (bétaverzió)

A következő képen a **Lekérdezés** ablak látható, amelyen az **Azure** kategória ki van választva.

![Azure-adatforrások, Adatok lekérése párbeszédpanel, Power BI Desktop](media/desktop-data-sources/data-sources-06.png)

### <a name="online-services-data-sources"></a>Online Services-adatforrások

Az **Online szolgáltatások** kategória a következő adatkapcsolatokat biztosítja:

* SharePoint Online-lista
* Microsoft Exchange Online
* Dynamics 365 (online)
* Dynamics NAV
* Dynamics 365 Business Central
* Dynamics 365 Business Central (helyszíni)
* Microsoft Azure Consumption Insights (bétaverzió)
* Azure DevOps (bétaverzió)
* Azure DevOps Server (bétaverzió)
* Salesforce-objektumok
* Salesforce-jelentések
* Google Analytics
* Adobe Analytics
* appFigures (bétaverzió)
* Data.World – Adathalmaz lekérése (bétaverzió)
* Facebook
* GitHub (bétaverzió)
* LinkedIn Sales Navigator (bétaverzió)
* MailChimp (bétaverzió)
* Marketo (bétaverzió)
* Mixpanel (bétaverzió)
* Planview Enterprise One - PRM (bétaverzió)
* Planview Projectplace (bétaverzió)
* QuickBooks Online (bétaverzió)
* Smartsheet
* SparkPost (bétaverzió)
* SweetIQ (bétaverzió)
* Planview Enterprise One – CTM (bétaverzió)
* Twilio (bétaverzió)
* tyGraph (bétaverzió)
* Webtrends (bétaverzió)
* Zendesk (bétaverzió)
* Dynamics 365 Customer Insights (béta)
* Emigo-adatforrás
* Entersoft Business Suite (bétaverzió)
* Industrial App Store
* Intune Data Warehouse (bétaverzió)
* Microsoft Graph Security (bétaverzió)
* Product Insights (bétaverzió)
* Quick Base
* TeamDesk (bétaverzió)
* Munkahelyi elemzés (bétaverzió)

A következő képen a **Lekérdezés** ablak látható, amelyen az **Online szolgáltatások** kategória ki van választva.

![Online Services-adatforrások, Adatok lekérése párbeszédpanel, Power BI Desktop](media/desktop-data-sources/data-sources-07.png)

### <a name="other-data-sources"></a>Más adatforrások

Az **Egyéb** kategória a következő adatkapcsolatokat biztosítja:

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
* BI360 - Budgeting & Financial Reporting (bétaverzió)
* Information Grid (bétaverzió)
* Paxata
* QubolePresto (bétaverzió)
* Roamler (bétaverzió)
* Siteimprove (bétaverzió)
* SurveyMonkey (bétaverzió)
* Tenforce (Smart)List (bétaverzió)
* Vena (bétaverzió)
* Workforce Dimensions (bétaverzió)
* Üres lekérdezés

A következő képen a **Lekérdezés** ablak látható, amelyen az **Egyéb** kategória ki van választva.

![Egyéb adatforrások, Adatok lekérése párbeszédpanel, Power BI Desktop](media/desktop-data-sources/data-sources-08.png)

> [!NOTE]
> Jelenleg nem lehetséges olyan egyéni adatforrásokhoz csatlakozni, amelyek védelmét az Azure Active Directory biztosítja.

## <a name="connecting-to-a-data-source"></a>Csatlakozás adatforráshoz

Egy adott adatforráshoz való csatlakozáshoz válassza ki azt a **Lekérdezés** ablakban, majd válassza a **Kapcsolódás** lehetőséget. A következő képen a **Web** lehetőség van kiválasztva az **Egyéb** adatkapcsolat-kategórián belül.

![Csatlakozás a webhez, Adatok lekérése párbeszédpanel, Power BI Desktop](media/desktop-data-sources/data-sources-08.png)

Ekkor megjelenik egy, az adott adatkapcsolatra jellemző csatlakozási ablak. Ha hitelesítő adatok szükségesek, a rendszer ezek megadására kéri. A következő képen a Web típusú adatforráshoz való csatlakozáshoz szükséges URL-cím megadása látható.

![Bemeneti URL, Webes tartalomból párbeszédpanel, Power BI Desktop](media/desktop-data-sources/datasources-fromwebbox.png)

Adja meg az URL-címet vagy az erőforrás csatlakozási adatait, majd kattintson az **OK** gombra. A Power BI Desktop csatlakozik az adatforráshoz, és megjeleníti az elérhető adatforrásokat a **Kezelőben**.

![Kezelő párbeszédpanel, Power BI Desktop](media/desktop-data-sources/datasources-fromnavigatordialog.png)

Az adatok betöltéséhez válassza a **Kezelő** panel alján lévő **Betöltés** gombot. A lekérdezés a Power Query-szerkesztőben való átalakításához vagy szerkesztéséhez az adatok beöltése előtt válassza az **Adatok átalakítása** gombot.

Ilyen egyszerűen csatlakozhat adatforrásokhoz a Power BI Desktopban. Egyre több adatforrás közül választhat, és a lista folyamatosan bővül, ezért érdemes gyakran visszatérnie.

## <a name="using-pbids-files-to-get-data"></a>PBIDS-fájlok használata az adatok beolvasásához

A PBIDS-fájlok olyan Power BI Desktop-fájlok, amelyek adott struktúrával rendelkeznek, és .PBIDS kiterjesztésűek, ami Power BI adatforrás-fájlként azonosítja őket.

.PBIDS-fájl létrehozásával egyszerűsítheti a szervezet jelentéskészítőinek munkáját az **adatbeolvasási** folyamatnál. Annak érdekében, hogy egy új jelentésszerző használhassa a PBIDS-fájlokat, javasoljuk, hogy ezeket egy rendszergazda hozza létre a gyakori kapcsolatokhoz.

Amikor egy szerző megnyit egy PBIDS-fájlt, megnyílik a Power BI Desktop, és bekéri a felhasználótól a hitelesítő adatokat a hitelesítéshez és a fájlban megadott adatforráshoz való kapcsolódáshoz. Megjelenik a **navigációs** párbeszédpanel, és a felhasználónak ki kell választania az adatforrásból azokat a táblákat, melyeket be szeretne tölteni a modellbe. A felhasználónak ki kell választania az adatbázis(oka)t is, ha az nem lett megadva a PBIDS-fájlban.

Ettől kezdve a felhasználó megkezdheti a vizualizációk létrehozását, vagy a **Legutóbbi források** használatával betölthet a modellbe egy új táblacsoportot.

A PBIDS-fájlok jelenleg csak egyetlen adatforrást támogatnak egy adott fájlban. Egynél több adatforrás megadása hibát eredményez.

A PBIDS-fájl létrehozásához a rendszergazdának meg kell adnia egy adott kapcsolat szükséges bemeneteit. A kapcsolati módot DirectQuery vagy Importálás típusúként is megadhatják. Ha a **mód** hiányzik vagy null értékű a fájlban, akkor a fájlt a Power BI Desktopban megnyitó felhasználónak ki kell választania vagy a **DirectQuery**, vagy az **Import** lehetőséget.

### <a name="pbids-file-examples"></a>Példák .PBIDS-fájlokra

Ebben a szakaszban bemutatunk néhány példát a gyakran használt adatforrásokra. A PBIDS fájltípus csak azokat az adatkapcsolatokat támogatja, amelyeket a Power BI Desktop is támogat, két kivétellel: az élő kapcsolat és az üres lekérdezés.

A PBIDS-fájl *nem* tartalmazza a hitelesítési adatokat és a táblák és a séma adatait.  

Az alábbi kódrészletekben néhány gyakori példát talál PBIDS-fájlokra. A lista nem teljes és nem átfogó. Más adatforrásokhoz tekintse meg az [Adatforrás-referencia (DSR) formátuma a protokoll- és címadatokhoz](https://docs.microsoft.com/azure/data-catalog/data-catalog-dsr#data-source-reference-specification) című cikket.

Ezeket a példákat csak segítségként mutatjuk be, azok nem teljesek, és nem tartalmazzák az összes támogatott összekötőt DSR formátumban. A rendszergazdák vagy a szervezetek saját adatforrásokat hozhatnak létre a példákat útmutatóként használva, amelyekből létrehozhatják és támogathatják a saját adatforrás-fájljaikat.

#### <a name="azure-as"></a>Azure AS

```json
{ 
    "version": "0.1", 
    "connections": [ 
    { 
        "details": { 
        "protocol": "analysis-services", 
        "address": { 
            "server": "server-here" 
        }, 
        } 
    } 
    ] 
}
```

#### <a name="folder"></a>Mappa

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "folder", 
        "address": { 
            "path": "folder-path-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="odata"></a>OData

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "odata", 
        "address": { 
            "url": "URL-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="sap-bw"></a>SAP BW

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sap-bw-olap", 
        "address": { 
          "server": "server-name-here", 
          "systemNumber": "system-number-here", 
          "clientId": "client-id-here" 
        }, 
      } 
    } 
  ] 
} 
```

#### <a name="sap-hana"></a>SAP Hana

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sap-hana-sql", 
        "address": { 
          "server": "server-name-here:port-here" 
        }, 
      } 
    } 
  ] 
} 
```

#### <a name="sharepoint-list"></a>SharePoint-lista

Az URL-címnek magára a SharePoint-webhelyre kell mutatnia, és nem a webhelyen belüli listára. A felhasználók egy kezelő használatával választhatnak ki egy vagy több listát a helyről, amelyek mindegyike a modell egy táblája lesz.

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sharepoint-list", 
        "address": { 
          "url": "URL-here" 
        }, 
       } 
    } 
  ] 
} 
```

#### <a name="sql-server"></a>SQL Server

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "tds", 
        "address": { 
          "server": "server-name-here", 
          "database": "db-name-here (optional) "
        } 
      }, 
      "options": {}, 
      "mode": "DirectQuery" 
    } 
  ] 
} 
```

#### <a name="text-file"></a>Szövegfájl

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "file", 
        "address": { 
            "path": "path-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="web"></a>Web

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "http", 
        "address": { 
            "url": "URL-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="dataflow"></a>Adatfolyam

```json
{
  "version": "0.1",
  "connections": [
    {
      "details": {
        "protocol": "powerbi-dataflows",
        "address": {
          "workspace":"workspace id (Guid)",
          "dataflow":"optional dataflow id (Guid)",
          "entity":"optional entity name"
        }
       }
    }
  ]
}
```

## <a name="next-steps"></a>Következő lépések

A Power BI Desktop műveletek és lehetőségek széles tárházát tartalmazza. A program képességeivel kapcsolatos további információkért lásd az alábbi forrásanyagokat:

* [Mi az a Power BI Desktop?](desktop-what-is-desktop.md)
* [Lekérdezések áttekintése a Power BI Desktopban](desktop-query-overview.md)
* [Adattípusok a Power BI Desktopban](desktop-data-types.md)
* [Adatok formázása és kombinálása a Power BI Desktoppal](desktop-shape-and-combine-data.md)
* [Gyakori lekérdezési feladatok a Power BI Desktopban](desktop-common-query-tasks.md)
