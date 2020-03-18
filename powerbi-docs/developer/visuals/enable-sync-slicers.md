---
title: A szeletelők szinkronizálásának engedélyezése Power BI-vizualizációkban
description: Ez a cikk azt írja le, hogyan engedélyezhető a szeletelők szinkronizálása Power BI-vizualizációkban.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 88e7e4b83f303f2b366f276b5020194f55f21f25
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380719"
---
# <a name="sync-slicers-in-power-bi-visuals"></a>Szeletelők szinkronizálása Power BI-vizualizációkban

A [szeletelők szinkronizálása](https://docs.microsoft.com/power-bi/desktop-slicers) funkció támogatásához az egyéni szeletelővizualizációnak az API 1.13-as vagy újabb verzióját kell használnia.

Ezen felül a beállítást a *capabilities.json* fájlban is engedélyezni kel az alábbi kódban látható módon:

```json
{
    ...
    "supportsHighlight": true,
    "suppressDefaultTitle": true,
    "supportsSynchronizingFilterState": true,
    "sorting": {
        "default": {}
    }
}
```

A *capabilities.json* fájl módosítása után az egyéni szeletelővizualizáció kiválasztásakor megtekintheti a **Szeletelők szinkronizálása** beállításait.

> [!NOTE]
> A Szeletelők szinkronizálása funkció nem támogat egynél több mezőt. Ha a szeletelő egynél több (**Kategória** vagy **Mérték**) mezőt tartalmaz, a funkció le van tiltva.

![A „Szeletelők szinkronizálása” panel](media/enable-sync-slicers/sync-slicers-panel.png)

A **Szeletelők szinkronizálása** panelen láthatja, hogy a szeletelő láthatósága és szűrése több jelentésoldalra is alkalmazható.
