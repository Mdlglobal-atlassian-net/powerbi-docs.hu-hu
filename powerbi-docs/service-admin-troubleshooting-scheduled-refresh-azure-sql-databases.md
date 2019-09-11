---
title: Az Azure SQL Database ütemezett frissítésének hibaelhárítása
description: Az Azure SQL Database ütemezett frissítésének hibaelhárítása a Power BI-ban
author: mgblythe
manager: kfile
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/04/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 4bc14b9a3d863732c581e8a144d612d864d65af8
ms.sourcegitcommit: c799941c8169cd5b6b6d63f609db66ab2af93891
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/06/2019
ms.locfileid: "70391829"
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Az Azure SQL Database ütemezett frissítésének hibaelhárítása a Power BI-ban

A frissítésről az [Adatfrissítés a Power BI-ban](refresh-data.md) és az [Ütemezett frissítés konfigurálása](refresh-scheduled-refresh.md) című cikkekben talál részletes információkat.

Amikor ütemezett frissítést hoz létre egy Azure SQL-adatbázishoz, és 400-as kódú hibaüzenetet kap a hitelesítő adatok szerkesztésekor, a következő módon állíthatja be a megfelelő tűzfalszabályt:

1. Jelentkezzen be az [Azure Portalra](https://portal.azure.com).

1. Nyissa meg azt az Azure SQL-adatbázist, amelyhez a frissítést konfigurálja.

1. Az **Áttekintés** panel felső részén válassza a **Kiszolgálói tűzfal beállítása**.

1. A **Tűzfalbeállítások** panelen ellenőrizze, hogy **BE** van-e kapcsolva az **Azure-szolgáltatásokhoz való hozzáférés engedélyezése**.

    ![Engedélyezett Azure-szolgáltatások](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
