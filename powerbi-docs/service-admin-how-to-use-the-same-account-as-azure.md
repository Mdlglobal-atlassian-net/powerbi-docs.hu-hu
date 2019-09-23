---
title: Ugyanazon bejelentkezési fiók használata a Power BI-hoz és az Azure-hoz
description: Ugyanazon bejelentkezési fiók használata a Power BI-hoz és az Azure-hoz
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: f9659ad657c4466ad58eb40d4a07916b46f9536a
ms.sourcegitcommit: 6a44cb5b0328b60ebe7710378287f1e20bc55a25
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70877765"
---
# <a name="using-the-same-account-for-power-bi-and-azure"></a>Ugyanazon bejelentkezési fiók használata a Power BI-hoz és az Azure-hoz

Ha Ön a Power BI és az Azure felhasználója, ugyanazokat a bejelentkezési adatokat használhatja mindkét szolgáltatásban, így nem kell kétszer megadnia a jelszót.

A Power BI a munkahelyi vagy iskolai e-mail-címéhez társított felhasználói fiókjával lépteti be Önt.  Az Azure egy Microsoft-fiókkal vagy egy munkahelyi fiókkal lépteti be Önt.

Ha ugyanazokat a bejelentkezési adatokat szeretné használni az Azure-ban és a Power BI-ban, ügyeljen arra, hogy a munkahelyi fiókjával jelentkezzen be az Azure-ba.

**Mi történik, ha már be vagyok bejelentkezve az Azure-ban egy Microsoft-fiókkal?**

A munkahelyi fiókját társ-rendszergazdaként veheti fel az Azure-ban az alábbi lépések végrehajtásával:

1. Jelentkezzen be az [Azure Portalra](http://portal.azure.com/). Ha Ön több Azure-címtár felhasználója, az **Előfizetések** elemet választva szűrhet, hogy csak a szerkeszteni kívánt címtárat és előfizetéseket lássa.

1. A navigációs panelen válassza a **Hozzáférés-vezérlés (IAM)** lehetőséget, majd a **Hozzáadás** \> **Társ-rendszergazda hozzáadása** menüpontot.

    ![Társ-rendszergazda hozzáadása az Azure Portalon](media/service-admin-how-to-use-the-same-account-as-azure/add-co-administrator.png)

1. Adja meg a munkahelyi fiókjához társított e-mail-címet, majd válassza a **Hozzáadás** lehetőséget.

1. Amikor legközelebb bejelentkezik az Azure Portalon, használja a munkahelyi e-mail-címét.

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
