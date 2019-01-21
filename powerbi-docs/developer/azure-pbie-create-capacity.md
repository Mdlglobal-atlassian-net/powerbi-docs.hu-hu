---
title: Power BI Embedded-kapacitás létrehozása az Azure Portalon | Microsoft Docs
description: Ez a cikk bemutatja, hogyan hozhat létre egy Power BI Embedded-kapacitást a Microsoft Azure-ban.
author: markingmyname
manager: kfile
ms.author: maghan
ms.service: power-bi-embedded
ms.subservice: ''
ms.devlang: csharp, javascript
ms.topic: conceptual
ms.reviewer: ''
ms.date: 07/31/2018
ms.openlocfilehash: caab7ce649687ec22d171e112382aa13d7652fb9
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54288543"
---
# <a name="create-power-bi-embedded-capacity-in-the-azure-portal"></a>Power BI Embedded-kapacitás létrehozása az Azure Portalon

Ez a cikk bemutatja, hogyan hozhat létre egy Power BI Embedded-kapacitást a Microsoft Azure-ban. A Power BI Embeddeddel lenyűgöző vizualizációkat, jelentéseket és irányítópultokat adhat gyorsan alkalmazásaihoz, így leegyszerűsítheti a Power BI funkcióit.

Ha még nincs Azure-előfizetése, kezdés előtt hozzon létre egy [ingyenes fiókot](https://azure.microsoft.com/free/).

> [!VIDEO https://www.youtube.com/embed/aXrvFfg_iSk]

## <a name="before-you-begin"></a>Előkészületek

Ennek a rövid útmutatónak az elvégzéséhez a következőkre lesz szüksége:

* **Azure-előfizetés:** Fiók létrehozásához lépjen az [Azure ingyenes próbaverziójának](https://azure.microsoft.com/free/) oldalára.
* **Azure Active Directory:** Előfizetését társítani kell egy Azure Active Directory- (AAD-) bérlővel. Továbbá ***be kell jelentkeznie az Azure-ba a bérlő egyik fiókjával***. A Microsoft-fiókok nem támogatottak. További információ: [Hitelesítés és felhasználói engedélyek](https://docs.microsoft.com/azure/analysis-services/analysis-services-manage-users).
* **Power BI-bérlő:** Az AAD-bérlő legalább egy fiókjának Power BI-regisztrációval kell rendelkeznie.
* **Erőforráscsoport:** Használjon egy meglévő erőforráscsoportot, vagy [hozzon létre egy újat](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).

## <a name="create-a-capacity"></a>Kapacitás létrehozása

1. Jelentkezzen be az [Azure Portalon](https://portal.azure.com/).

2. Válassza az **Erőforrás létrehozása** > **Adatok + analitika** lehetőséget.

3. A keresőmezőbe írja be a *Power BI Embedded* kifejezést.

4. A Power BI Embeddedben válassza a **Létrehozás** lehetőséget.

5. Adja meg a szükséges adatokat, majd válassza a **Létrehozás** lehetőséget.

    ![Új kapacitás létrehozásához kitöltendő mezők](media/azure-pbie-create-capacity/azure-portal-create-power-bi-embedded.png)

    |Beállítás |Leírás |
    |---------|---------|
    |**Erőforrás neve**|A kapacitást azonosító név. Az erőforrás neve a Power BI felügyeleti portálon, valamint az Azure Portalon jelenik meg.|
    |**Előfizetés**|Az előfizetés, amelyben létre szeretné hozni a kapacitást.|
    |**Erőforráscsoport**|Az új kapacitást tartalmazó erőforráscsoport. Választhat meglévő erőforráscsoportot, vagy létrehozhat egy újat. További információt [Az Azure Resource Manager áttekintésében](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview) találhat.|
    |**Power BI kapacitásadminisztrátor**|A Power BI kapacitás-rendszergazdái megtekinthetik a kapacitást a Power BI felügyeleti portálján, és hozzárendelési engedélyt adhatnak a felhasználóknak. A kapacitásadminisztrátor alapértelmezés szerint az Ön fiókja. A kapacitásadminisztrátornak a Power BI-bérlőn belül kell lennie.|
    |**Hely**|A Power BI bérlői szolgáltatási helye. Az alapértelmezett hely az otthoni régiója, de a [Multi-Geo-beállításokkal](embedded-multi-geo.md) módosíthatja a helyet.
    |**Tarifacsomag**|Válassza ki az igényeinek megfelelő SKU-t (virtuális magok és memóriaméret szerint)  További információt a [Power BI Embedded díjszabásában](https://azure.microsoft.com/pricing/details/power-bi-embedded/) találhat|

6. Kattintson a **Létrehozás** gombra.

A létrehozás általában egy percet sem vesz igénybe, csupán néhány másodpercet. Ha a **Rögzítés az irányítópulton** lehetőséget választja, az irányítópultra lépve megtekintheti az új kapacitást. Másik lehetőségként a **Minden szolgáltatás** > **Power BI Embedded** területre lépve megtekintheti, hogy készen áll-e az új kapacitás.

![Azure Portal-irányítópult Power BI Embedded-kapacitással](media/azure-pbie-create-capacity/azure-portal-dashboard.png)

## <a name="next-steps"></a>Következő lépések

Az új Power BI Embedded-kapacitás használatához lépjen a Power BI felügyeleti portáljára, és rendeljen hozzá munkaterületeket. További információ: [Kapacitáskezelés a Power BI Premium és a Power BI Embedded szolgáltatással](https://powerbi.microsoft.com/documentation/powerbi-admin-premium-manage/).

Ha nem szeretné használni ezt a kapacitást, szüneteltetheti a számlázás leállításához. További információ: [Power BI Embedded-kapacitás szüneteltetése és elindítása az Azure Portalon](azure-pbie-pause-start.md).

Power BI-tartalmak beágyazásához tekintse meg a [Power BI-irányítópultok, -jelentések és -csempék beágyazása](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/) című témakört.

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)