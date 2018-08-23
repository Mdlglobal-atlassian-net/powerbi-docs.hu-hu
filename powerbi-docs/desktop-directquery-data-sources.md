---
title: A DirectQuery által támogatott adatforrások a Power BI-ban
description: A DirectQuery használatát támogató adatforrások listája.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 08/10/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: d37ed22c0abba4e843d37fd6df465f9a755fbdc6
ms.sourcegitcommit: 126e5eca8bfab6273581dabd7603df88be755240
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/11/2018
ms.locfileid: "40257008"
---
# <a name="data-sources-supported-by-directquery-in-power-bi"></a>A DirectQuery által támogatott adatforrások a Power BI-ban
A **Power BI Desktopban** és a **Power BI szolgáltatásban** számos adatforráshoz csatlakozhat, és hozzáférhet ezek adataihoz. Ez a cikk azt ismerteti, hogy a Power BI mely adatforrásai támogatják a **DirectQuery** néven ismert kapcsolódási módszert. További, a DirectQueryre vonatkozó információkért lásd [**a DirectQuery Power BI-ban történő használatát**](desktop-directquery-about.md) ismertető cikket.

A következő adatforrások támogatják a DirectQueryt a Power BI-ban:

* Amazon Redshift
* Azure Databricks
* Azure HDInsight Spark (bétaverzió)
* Azure SQL Database
* Azure SQL Data Warehouse
* Google BigQuery (bétaverzió)
* IBM Netezza (bétaverzió)
* Impala (2.x-es verzió)
* Oracle Database (12-es és újabb verzió)
* SAP Business Warehouse-alkalmazáskiszolgáló
* SAP Business Warehouse üzenetkezelési kiszolgáló (bétaverzió)
* SAP HANA
* Snowflake
* Spark (bétaverzió) (0.9-es és újabb)
* SQL Server
* Teradata-adatbázis
* Vertica (bétaverzió)

Azok az adatforrások, amelyek neve mögött szerepel a **(bétaverzió)** vagy az **(előzetes verzió)**, módosulhatnak, és a használatuk éles környezetben nem támogatott. Az is előfordulhat, hogy akkor sem támogatottak, miután közzétett egy jelentést a **Power BI szolgáltatásban**, és ezért egy közzétett jelentés megnyitása vagy az adatkészlet felderítése hibát okozhat.

Az egyetlen különbség a **(bétaverzió)** és az **(előzetes verzió)** kifejezéssel jelölt adatforrások között, hogy az **(előzetes verziójú)** forrásokat engedélyezni kell Előzetes verziójú funkcióként, mielőtt használni lehetne őket. Egy **(előzetes verziójú)** adatösszekötő engedélyezéséhez a **Power BI Desktopban** lépjen a **Fájl > Lehetőségek és beállítások > Beállítások** területre, és válassza az **Előzetes verziójú funkciók** lehetőséget.

> [!NOTE]
> Az SQL Serverre irányuló DirectQuery-lekérdezések a hozzáférés létrehozásához az aktuális windowsos hitelesítő adatokkal vagy adatbázisbeli hitelesítő adatokkal való hitelesítést igényelnek. Alternatív hitelesítő adatok nincsenek támogatva.
>

## <a name="on-premises-gateway-requirements"></a>Helyszíni átjáróra vonatkozó követelmények
Az alábbi tábla meghatározza, hogy szükség van-e **helyszíni adatátjáróra** az adott adatforráshoz való csatlakozáshoz, miután közzétett egy jelentést a **Power BI szolgáltatásban**.

| Forrás | Szükség van átjáróra? |
| --- | --- |
| SQL Server |Igen |
| Azure SQL Database |Nem |
| Azure SQL Data Warehouse |Nem |
| SAP HANA |Igen |
| Oracle Database |Igen |
| Teradata-adatbázis |Igen |
| Amazon Redshift |Nem |
| Impala (2.x-es verzió) |Igen |
| Snowflake |Igen |
| Spark (bétaverzió) (0.9-es és újabb) |Még nem támogatott a **Power BI szolgáltatásban** |
| Azure HDInsight Spark (bétaverzió) |Nem |
| IBM Netezza |Igen |
| SAP Business Warehouse-alkalmazáskiszolgáló |Igen |
| SAP Business Warehouse üzenetkezelési kiszolgáló |Még nem támogatott a **Power BI szolgáltatásban** |
| Google BigQuery |Nem |


## <a name="next-steps"></a>Következő lépések
Ha többet szeretne megtudni a DirectQueryről, tekintse át a következő forrásanyagokat:

* [A DirectQuery használata a Power BI-ban](desktop-directquery-about.md)
* [A DirectQuery és az SAP HANA](desktop-directquery-sap-hana.md)
* [A DirectQuery és az SAP BW](desktop-directquery-sap-bw.md)
* [Helyszíni adatátjáró](service-gateway-onprem.md)

