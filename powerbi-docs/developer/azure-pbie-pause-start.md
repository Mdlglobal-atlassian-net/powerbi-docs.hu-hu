---
title: Power BI Embedded-kapacitás szüneteltetése és elindítása az Azure Portalon| Microsoft Docs
description: Ez a cikk bemutatja, hogyan szüneteltethet és indíthat el egy Power BI Embedded-kapacitást a Microsoft Azure-ban.
services: power-bi-embedded
author: rkarlin
ms.author: rkarlin
manager: kfile
editor: ''
tags: ''
ms.service: power-bi-embedded
ms.topic: conceptual
ms.date: 09/28/2017
ms.openlocfilehash: 8a02654f264fb83f501679e4e205e08017f083f6
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61387473"
---
# <a name="pause-and-start-your-power-bi-embedded-capacity-in-the-azure-portal"></a>Power BI Embedded-kapacitás szüneteltetése és elindítása az Azure Portalon

Ez a cikk bemutatja, hogyan szüneteltethet és indíthat el egy Power BI Embedded-kapacitást a Microsoft Azure-ban. Ez a cikk feltételezi, hogy már létrehozott egy Power BI Embedded-kapacitást. Ha még nem, végezze el az első lépéseket a [Power BI Embedded-kapacitás létrehozása az Azure Portalon](azure-pbie-create-capacity.md) című cikk szerint.

Ha még nincs Azure-előfizetése, kezdés előtt hozzon létre egy [ingyenes fiókot](https://azure.microsoft.com/free/).

## <a name="pause-your-capacity"></a>A kapacitás szüneteltetése

A kapacitás szüneteltetése esetén nem kap róla számlát. A kapacitás szüneteltetése jó ötlet akkor, ha egy ideig nem szeretné használni. Az alkalmazás szüneteltetéséhez hajtsa végre a következő lépéseket.

> [!NOTE]
> A szüneteltetés után előfordulhat, hogy egyes Power BI-tartalmak nem érhetők el. A megszakítások elkerülése érdekében ügyeljen rá, hogy megszüntesse a kapacitások munkaterületeinek hozzárendeléseit a szüneteltetés előtt.

1. Jelentkezzen be az [Azure Portalon](https://portal.azure.com/).

2. A kapacitások megtekintéséhez válassza a **Minden szolgáltatás** > **Power BI Embedded** lehetőséget.

    ![Minden szolgáltatás az Azure Portalon](media/azure-pbie-pause-start/azure-portal-more-services.png)

3. Válassza ki a szüneteltetni kívánt kapacitást.

    ![A Power BI Embedded-kapacitások listája az Azure Portalon](media/azure-pbie-pause-start/azure-portal-capacity-list.png)

4. Válassza a **Szüneteltetés** lehetőséget a kapacitás részletei között.

    ![A kapacitás szüneteltetése](media/azure-pbie-pause-start/azure-portal-pause-capacity.png)

5. Válassza az **Igen** lehetőséget, amellyel megerősíti, hogy szüneteltetni szeretné a kapacitást.

    ![Szüneteltetés megerősítése](media/azure-pbie-pause-start/azure-portal-confirm-pause.png)

## <a name="start-your-capacity"></a>A kapacitás elindítása

A kapacitás elindításával folytathatja a használatot. Ezzel a számlázási időszakot is folytatja.

1. Jelentkezzen be az [Azure Portalon](https://portal.azure.com/).

2. A kapacitások megtekintéséhez válassza a **Minden szolgáltatás** > **Power BI Embedded** lehetőséget.

    ![Minden szolgáltatás az Azure Portalon](media/azure-pbie-pause-start/azure-portal-more-services.png)

3. Válassza ki a elindítani kívánt kapacitást.

    ![A Power BI Embedded-kapacitások listája az Azure Portalon](media/azure-pbie-pause-start/azure-portal-capacity-list.png)

4. Válassza az **Indítás** lehetőséget a kapacitás részletei között.

    ![A kapacitás elindítása](media/azure-pbie-pause-start/azure-portal-start-capacity.png)

5. Válassza az **Igen** lehetőséget, amellyel megerősíti, hogy el szeretné indítani a kapacitást.

    ![Indítás megerősítése](media/azure-pbie-pause-start/azure-portal-confirm-start.png)

Ha tartalmak vannak a kapacitáshoz rendelve, azok újra elérhetővé válnak az indítás után.

## <a name="next-steps"></a>Következő lépések

Ha felfelé vagy lefelé szeretné skálázni a kapacitást, tekintse meg a [Power BI Embedded-kapacitás skálázása](azure-pbie-scale-capacity.md) című cikket.

Power BI-tartalmak beágyazásához tekintse meg a [Power BI-irányítópultok, -jelentések és -csempék beágyazása](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/) című témakört.

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)