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
ms.date: 06/20/2018
LocalizationGroup: Data from databases
ms.openlocfilehash: f03f4933566a8c18510ef0ce07b71db61ecfa8fd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770604"
---
# <a name="azure-sql-database-with-directquery"></a>Az Azure SQL Database DirectQueryvel

Ismerje meg, hogyan lehet az Azure SQL Database-hez közvetlenül kapcsolódni, és élő adatok használatával jelentéseket létrehozni. Nem szükséges az adatok a saját forrásukból a Power BI-ba juttatni.

A DirectQuery használatával, miközben a jelentés nézetben feltárja az adatokat, lekérdezéseket küld vissza az Azure SQL Database-nek. Ez a kezelőfelület olyan felhasználók számára javasolt, akik már ismerik az adatbázisokat és azokat az entitásokat, amelyekhez az adatbázisok kapcsolódnak.

**Megjegyzések:**

* A kapcsolódáskor a teljes szervernevet adja meg (további részleteket lejjebb talál)
* Győződjön meg arról, hogy az adatbázisra vonatkozó tűzfalszabályokban konfigurálva van az [Azure-szolgáltatásokhoz való hozzáférés engedélyezése](https://msdn.microsoft.com/library/azure/ee621782.aspx)
* Minden művelet, mint például egy oszlop kiválasztása vagy egy szűrő felvétele, visszaküld egy lekérdezést az adatbázisnak
* A csempék óránként frissülnek (a frissítést nem szükséges ütemezni). Ezen a csatlakozáskor lehet módosítani, a Speciális beállítások között.
* A Q&A nem érhető el DirectQuery-adatkészletek esetén
* A sémaváltozások felvétele nem automatikus

Ezek a korlátozások és megjegyzések a kezelőfelület további fejlesztése folyamán változhatnak. Alább láthatók a kapcsolódás lépéseinek részletei.

> [!Important]
> Továbbfejlesztettük az Azure SQL Database-kapcsolódást.  Az Azure SQL Database-beli adatforráshoz való kapcsolódás leghatékonyabb módja a Power BI Desktop használata.  Miután elkészítette a modellt és a jelentést, közzéteheti a Power BI szolgáltatásban.  Az Azure SQL Database a Power BI szolgáltatásban használt közvetlen összekötője elavult.

## <a name="power-bi-desktop-and-directquery"></a>A Power BI Desktop és a DirectQuery

A Power BI Desktop használata szükséges ahhoz, hogy az Azure SQL Database-hez DirectQueryvel kapcsolódhasson. Ez a megközelítés nagyobb rugalmasságot és további képességeket biztosít. A Power BI Desktoppal létrehozott jelentések közzétehetők a Power BI szolgáltatásban. További tudnivalók arról, hogyan kapcsolódhat az [Azure SQL Database-hez DirectQuery használatával](desktop-use-directquery.md) a Power BI Desktopban.

## <a name="single-sign-on"></a>Egyszeri bejelentkezés

Miután közzétett egy Azure SQL DirectQuery-adathalmazt a szolgáltatásban, engedélyezheti az Azure Active Directory (Azure AD) OAuth2 használatával való egyszeri bejelentkezést (SSO) a végfelhasználók számára.

Az egyszeri bejelentkezés engedélyezéséhez nyissa meg az adathalmaz beállításait, majd az **Adatforrások** lapot, és jelölje be az Egyszeri bejelentkezés jelölőnégyzetet.

![Az Azure SQL DQ konfigurálása párbeszédpanel](media/service-azure-sql-database-with-direct-connect/sso-dialog.png)

Ha az egyszeri bejelentkezési beállítás engedélyezve van, és a felhasználók használják az adatforrásra épülő jelentéseket, a Power BI elküldi a hitelesített Azure AD-beli hitelesítő adataikat a lekérdezésekben az Azure SQL Database-adatbázisnak. Ez lehetővé teszi a Power BI számára, hogy figyelembe vegye az adatforrás szintjén konfigurált biztonsági beállításokat.

Az egyszeri bejelentkezési beállítás az adatforrást használó összes adathalmazra érvényes lesz. Az importálási forgatókönyvekhez használt hitelesítési módszerre nincs hatással.

> [!Note]
> Az Azure Multi-Factor Authentication (MFA) nem támogatott. Azokat a felhasználókat, akik egyszeri bejelentkezést kívánnak használni az Azure SQL DirectQueryvel, ki kell vonni az MFA hatálya alól.

## <a name="finding-parameter-values"></a>Paraméterértékek megkeresése

A teljes szervernevet és adatbázisnevet az Azure Portalon találhatja meg.

![Új Azure-port update](media/service-azure-sql-database-with-direct-connect/azureportnew_update.png)

![Az Azure portál frissítése](media/service-azure-sql-database-with-direct-connect/azureportal_update.png)

## <a name="next-steps"></a>Következő lépések

* [A DirectQuery használata a Power BI Desktopban](desktop-use-directquery.md)  
* [Mi az a Power BI?](power-bi-overview.md)  
* [Power BI – Adatok lekérése](service-get-data.md)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
