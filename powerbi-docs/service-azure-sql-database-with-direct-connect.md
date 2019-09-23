---
title: Az Azure SQL Database DirectQueryvel
description: Az Azure SQL Database DirectQueryvel
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 09/16/2019
LocalizationGroup: Data from databases
ms.openlocfilehash: a80c549ab3aa61e377b657ad426d240a6a485fdd
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71074252"
---
# <a name="azure-sql-database-with-directquery"></a>Az Azure SQL Database DirectQueryvel

Ismerje meg, hogyan lehet az Azure SQL Database-hez közvetlenül kapcsolódni, és élő adatok használatával jelentéseket létrehozni. Nem szükséges az adatok a saját forrásukból a Power BI-ba juttatni.

A DirectQuery használatával, miközben a jelentés nézetben feltárja az adatokat, lekérdezéseket küld vissza az Azure SQL Database-nek. Ez a kezelőfelület olyan felhasználók számára javasolt, akik már ismerik az adatbázisokat és azokat az entitásokat, amelyekhez az adatbázisok kapcsolódnak.

**Megjegyzések:**

* A kapcsolódáskor a teljes szervernevet adja meg (további részleteket lejjebb talál).
* Győződjön meg arról, hogy az adatbázisra vonatkozó tűzfalszabályokban konfigurálva van az „[Azure-szolgáltatásokhoz való hozzáférés engedélyezése](https://docs.microsoft.com/azure/sql-database/sql-database-networkaccess-overview#allow-azure-services)”.
* Minden művelet, mint például egy oszlop kiválasztása vagy egy szűrő felvétele, visszaküld egy lekérdezést az adatbázisnak.
* A csempék óránként frissülnek (a frissítést nem szükséges ütemezni). A frissítés gyakoriságát a Speciális beállítások között módosíthatja a csatlakozáskor.
* A Q&A nem érhető el a DirectQuery-adatkészletek esetén.
* A rendszer nem követi automatikusan a sémák változásait.

Ezek a korlátozások és figyelmeztetések a felhasználói felületek fejlesztésével változhatnak. Alább láthatók a kapcsolódás lépéseinek részletei.

> [!Important]
> Továbbfejlesztettük az Azure SQL Database-kapcsolódást.  Az Azure SQL Database-beli adatforráshoz való kapcsolódás leghatékonyabb módja a Power BI Desktop használata.  Miután elkészítette a modellt és a jelentést, közzéteheti a Power BI szolgáltatásban.  Az Azure SQL Database a Power BI szolgáltatásban használt közvetlen összekötője elavult.

## <a name="power-bi-desktop-and-directquery"></a>A Power BI Desktop és a DirectQuery

Ha a DirectQueryvel szeretne az Azure SQL Database-hez kapcsolódni, a Power BI Desktopot kell használnia. Ez a megközelítés nagyobb rugalmasságot és további képességeket biztosít. A Power BI Desktoppal létrehozott jelentések közzétehetők a Power BI szolgáltatásban. További tudnivalók arról, hogyan kapcsolódhat az [Azure SQL Database-hez DirectQuery használatával](desktop-use-directquery.md) a Power BI Desktopban.

## <a name="find-parameter-values"></a>Paraméterértékek keresése

A teljes kiszolgálónevet és adatbázisnevet az Azure Portalon találhatja meg.

![Új Azure Portal-frissítés](media/service-azure-sql-database-with-direct-connect/azureportnew_update.png)

![Azure Portal-frissítés](media/service-azure-sql-database-with-direct-connect/azureportal_update.png)

[!INCLUDE [direct-query-sso](includes/direct-query-sso.md)]

## <a name="next-steps"></a>Következő lépések

* [A DirectQuery használata a Power BI Desktopban](desktop-use-directquery.md)  
* [Mi az a Power BI?](power-bi-overview.md)  
* [Adatbeolvasás a Power BI szolgáltatásban](service-get-data.md)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
