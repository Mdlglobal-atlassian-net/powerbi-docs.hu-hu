---
title: A DirectQuery által támogatott adatforrások a Power BI-ban
description: A DirectQuery használatát támogató adatforrások listája.
author: davidiseminger
ms.author: davidi
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/29/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: 5455a5f3b4bda6cf6d63825222822c4acfa5f03a
ms.sourcegitcommit: c0f4d00d483121556a1646b413bab75b9f309ae9
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70159947"
---
# <a name="data-sources-supported-by-directquery-in-power-bi"></a>A DirectQuery által támogatott adatforrások a Power BI-ban

A **Power BI Desktopban** és a **Power BI szolgáltatásban** számos adatforráshoz csatlakozhat, és hozzáférhet ezek adataihoz. Ez a cikk azt ismerteti, hogy a Power BI mely adatforrásai támogatják a **DirectQuery** néven ismert kapcsolódási módszert. További, a DirectQueryre vonatkozó információkért lásd [**a DirectQuery Power BI-ban történő használatát**](desktop-directquery-about.md) ismertető cikket.

A következő adatforrások támogatják a DirectQueryt a Power BI-ban:

* Amazon Redshift
* AtScale (bétaverzió)
* Azure Data Explorer
* Azure HDInsight Spark
* [Azure SQL Database](service-azure-sql-database-with-direct-connect.md)
* [Az Azure SQL Data Warehouse](service-azure-sql-data-warehouse-with-direct-connect.md)
* Google BigQuery
* HDInsight interaktív lekérdezés
* IBM DB2-adatbázis
* IBM Netezza
* Impala (2.x-es verzió)
* MarkLogic
* Oracle Database (12-es és újabb verzió)
* Oracle Essbase
* SAP Business Warehouse-alkalmazáskiszolgáló
* SAP Business Warehouse üzenetkezelési kiszolgáló
* SAP HANA
* Snowflake
* Spark (0.9 és újabb verzió)
* SQL Server
* Teradata-adatbázis
* Vertica

Azok az adatforrások, amelyek neve mögött szerepel a **(bétaverzió)** vagy az **(előzetes verzió)** , módosulhatnak, és a használatuk éles környezetben nem támogatott. Az is előfordulhat, hogy akkor sem támogatottak, miután közzétett egy jelentést a **Power BI szolgáltatásban**, és ezért egy közzétett jelentés megnyitása vagy az adatkészlet felderítése hibát okozhat.

Az egyetlen különbség a **(bétaverzió)** és az **(előzetes verzió)** kifejezéssel jelölt adatforrások között, hogy az **(előzetes verziójú)** forrásokat engedélyezni kell Előzetes verziójú funkcióként, mielőtt használni lehetne őket. Egy **(előzetes verziójú)** adatösszekötő engedélyezéséhez a **Power BI Desktopban** lépjen a **Fájl > Lehetőségek és beállítások > Beállítások** területre, és válassza az **Előzetes verziójú funkciók** lehetőséget.

> [!NOTE]
> Az SQL Serverre irányuló DirectQuery-lekérdezések a hozzáférés létrehozásához az aktuális windowsos hitelesítő adatokkal vagy adatbázisbeli hitelesítő adatokkal való hitelesítést igényelnek. Alternatív hitelesítő adatok nincsenek támogatva.
>

## <a name="on-premises-gateway-requirements"></a>Helyszíni átjáróra vonatkozó követelmények
Az alábbi tábla meghatározza, hogy szükség van-e **helyszíni adatátjáróra** az adott adatforráshoz való csatlakozáshoz, miután közzétett egy jelentést a **Power BI szolgáltatásban**.

| Forrás | Szükség van átjáróra? |
| --- | --- |
| Amazon Redshift |Nem |
| Azure HDInsight Spark (bétaverzió) |Nem |
| Azure SQL Database |Nem |
| Azure SQL Data Warehouse |Nem |
| Google BigQuery |Nem |
| IBM Netezza |Igen |
| Impala (2.x-es verzió) |Igen |
| Oracle Database |Igen |
| SAP Business Warehouse-alkalmazáskiszolgáló |Igen |
| SAP Business Warehouse üzenetkezelési kiszolgáló |Még nem támogatott a **Power BI szolgáltatásban** |
| SAP HANA |Igen |
| Snowflake |Igen |
| Spark (bétaverzió) (0.9-es és újabb) |Igen |
| SQL Server |Igen |
| Teradata-adatbázis |Igen |

## <a name="single-sign-on-sso-for-directquery-sources"></a>Egyszeri bejelentkezés (SSO) DirectQuery-forrásokhoz

Ha az egyszeri bejelentkezési beállítás engedélyezve van, és a felhasználók használják az adatforrásra épülő jelentéseket, a Power BI elküldi a hitelesített Azure AD-beli hitelesítő adataikat a lekérdezésekben a mögöttes adatforrásnak. Ez lehetővé teszi a Power BI számára, hogy figyelembe vegye az adatforrás szintjén konfigurált biztonsági beállításokat.

Az egyszeri bejelentkezési beállítás az adatforrást használó összes adathalmazra érvényes lesz. Az importálási forgatókönyvekhez használt hitelesítési módszerre nincs hatással. Az alábbi adatforrások támogatják az egyszeri bejelentkezést a DirectQuery-n keresztüli kapcsolatokhoz:

- Azure SQL Database
- Azure SQL Data Warehouse
- Impala
- SAP HANA
- SAP BW
- Spark
- SQL Server
- Teradata

> [!Note]
> Az Azure Multi-Factor Authentication (MFA) nem támogatott. Azokat a felhasználókat, akik egyszeri bejelentkezést kívánnak használni a DirectQueryvel, ki kell vonni az MFA hatálya alól.

## <a name="next-steps"></a>Következő lépések
Ha többet szeretne megtudni a DirectQueryről, tekintse át a következő forrásanyagokat:

* [A DirectQuery használata a Power BI-ban](desktop-directquery-about.md)
* [A DirectQuery és az SAP HANA](desktop-directquery-sap-hana.md)
* [A DirectQuery és az SAP BW](desktop-directquery-sap-bw.md)
* [Helyszíni adatátjáró](service-gateway-onprem.md)

