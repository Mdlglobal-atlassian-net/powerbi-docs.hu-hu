---
title: A Power BI Embedded-kapacitás skálázása
description: Ez a cikk bemutatja, hogyan skálázhat egy Power BI Embedded-kapacitást a Microsoft Azure-ban.
services: power-bi-embedded
author: rkarlin
ms.author: rkarlin
manager: kfile
editor: ''
tags: ''
ms.service: power-bi-embedded
ms.topic: conceptual
ms.date: 01/31/2019
ms.openlocfilehash: b9a632fa39d320d14d1282cee5e59022a8ab0303
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61388509"
---
# <a name="scale-your-power-bi-embedded-capacity-in-the-azure-portal"></a>A Power BI Embedded-kapacitás skálázása az Azure Portalon

Ez a cikk bemutatja, hogyan skálázhat egy Power BI Embedded-kapacitást a Microsoft Azure-ban. A skálázással növelheti vagy csökkentheti a kapacitás méretét.

Ez a cikk feltételezi, hogy már létrehozott egy Power BI Embedded-kapacitást. Ha még nem, végezze el az első lépéseket a [Power BI Embedded-kapacitás létrehozása az Azure Portalon](azure-pbie-create-capacity.md) című cikk szerint.

> [!NOTE]
> A skálázási műveletek körülbelül egy percet vesznek igénybe. Ezalatt az idő alatt a kapacitás nem elérhető. Előfordulhat, hogy a beágyazott tartalmak nem töltődnek be.

## <a name="scale-a-capacity"></a>Kapacitás skálázása

1. Jelentkezzen be az [Azure Portalon](https://portal.azure.com/).

2. A kapacitások megtekintéséhez válassza a **Minden szolgáltatás** > **Power BI Embedded** lehetőséget.

    ![Minden szolgáltatás az Azure Portalon](media/azure-pbie-scale-capacity/azure-portal-more-services.png)

3. Válassza ki a skálázni kívánt kapacitást.

    ![A Power BI Embedded-kapacitások listája az Azure Portalon](media/azure-pbie-scale-capacity/azure-portal-capacity-list.png)

4. Válassza a kapacitás **Méretezés** területén a **Tarifacsomag** lehetőséget.

    ![Tarifacsomag lehetőség a méretezési menüben](media/azure-pbie-scale-capacity/azure-portal-scale-pricing-tier.png)

    A jelenlegi tarifacsomag kékkel van kiemelve.

    ![A kékkel kiemelt jelenlegi tarifacsomag](media/azure-pbie-scale-capacity/azure-portal-current-tier.png)

5. A felfelé vagy lefelé történő skálázáshoz válassza ki, melyik csomagra szeretne váltani. Új csomag kiválasztásakor egy kék szaggatott vonal jelenik meg a kijelölés körül. Az új szintre való skálázáshoz válassza a **Kiválasztás** lehetőséget.

    ![Új csomag kiválasztása](media/azure-pbie-scale-capacity/azure-portal-select-new-tier.png)

    A kapacitás skálázása egy-két percet vehet igénybe.

6. Erősítse meg a csomagot az Áttekintés lap megtekintésével. Itt megjelenik az aktuális tarifacsomag.

    ![Aktuális csomag megerősítése](media/azure-pbie-scale-capacity/azure-portal-confirm-tier.png)

## <a name="next-steps"></a>Következő lépések

Kapacitás szüneteltetéséhez vagy elindításához tekintse meg a [Power BI Embedded-kapacitás szüneteltetése és elindítása az Azure Portalon](azure-pbie-pause-start.md) című cikket.

Power BI-tartalmak beágyazásához tekintse meg a [Power BI-irányítópultok, -jelentések és -csempék beágyazása](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/) című témakört.

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
