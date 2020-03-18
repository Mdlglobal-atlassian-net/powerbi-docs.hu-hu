---
title: Power BI Embedded-kapacitás szüneteltetése és elindítása az Azure Portalon| Microsoft Docs
description: Ez a cikk bemutatja, hogyan szüneteltethet és indíthat el egy Power BI Embedded-kapacitást a Microsoft Azure-ban.
services: power-bi-embedded
author: KesemSharabi
ms.author: kesharab
editor: ''
tags: ''
ms.service: power-bi-embedded
ms.topic: how-to
ms.date: 09/28/2017
ms.openlocfilehash: 492750e232173480d71bd49b83623d41244bb83b
ms.sourcegitcommit: a175faed9378a7d040a08ced3e46e54503334c07
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/18/2020
ms.locfileid: "79495596"
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

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)