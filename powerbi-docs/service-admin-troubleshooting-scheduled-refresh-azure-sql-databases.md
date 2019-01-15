---
title: Az Azure SQL Database ütemezett frissítésének hibaelhárítása
description: Az Azure SQL Database ütemezett frissítésének hibaelhárítása a Power BI-ban
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 17ee932bf0331940c7b30b020ab8fc43cdc9fdf5
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54274675"
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Az Azure SQL Database ütemezett frissítésének hibaelhárítása a Power BI-ban
Az ütemezett frissítés beállításának részletes leírásáért tekintse meg az [adatok a Power BI-ban történő frissítését](refresh-data.md) ismertető témakört.

Amikor ütemezett frissítést hoz létre egy Azure SQL Database-hez, és 400-as számú hibaüzenetet kap a hitelesítő adatok szerkesztése során, a következő módon állíthatja be a megfelelő tűzfalszabályt:

1. Jelentkezzen be az Azure felügyeleti portálján.
2. Keresse meg azt az Azure SQL Servert, amelyhez be kívánja állítani a frissítést.
3. Jelölje be a „Windows Azure-szolgáltatások” elemet az engedélyezett szolgáltatások szakaszában.

![Engedélyezett Azure-szolgáltatások](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

