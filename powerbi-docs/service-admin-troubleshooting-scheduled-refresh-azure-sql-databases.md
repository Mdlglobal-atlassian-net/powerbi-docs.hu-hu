---
title: Az Azure SQL Database ütemezett frissítésének hibaelhárítása
description: Az Azure SQL Database ütemezett frissítésének hibaelhárítása a Power BI-ban
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: d1cd68fbb995b7fac420a50f97a8930385086a10
ms.sourcegitcommit: 72c9d9ec26e17e94fccb9c5a24301028cebcdeb5
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/07/2018
ms.locfileid: "53026063"
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Az Azure SQL Database ütemezett frissítésének hibaelhárítása a Power BI-ban
Az ütemezett frissítés beállításának részletes leírásáért tekintse meg az [adatok a Power BI-ban történő frissítését](refresh-data.md) ismertető témakört.

Amikor ütemezett frissítést hoz létre egy Azure SQL Database-hez, és 400-as számú hibaüzenetet kap a hitelesítő adatok szerkesztése során, a következő módon állíthatja be a megfelelő tűzfalszabályt:

1. Jelentkezzen be az Azure felügyeleti portálján.
2. Keresse meg azt az Azure SQL Servert, amelyhez be kívánja állítani a frissítést.
3. Jelölje be a „Windows Azure-szolgáltatások” elemet az engedélyezett szolgáltatások szakaszában.

![Engedélyezett Azure-szolgáltatások](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

