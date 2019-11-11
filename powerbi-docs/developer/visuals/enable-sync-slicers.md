---
title: A szeletelők szinkronizálásának engedélyezése Power BI-vizualizációkban
description: Ez a cikk azt írja le, hogyan engedélyezhető a szeletelők szinkronizálása Power BI-vizualizációkban.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 055878988a197b80a8e4842a6567966f75af2ce5
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73880146"
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

![A „Szeletelők szinkronizálása” panel](./media/sync-slicers-panel.png)

A **Szeletelők szinkronizálása** panelen láthatja, hogy a szeletelő láthatósága és szűrése több jelentésoldalra is alkalmazható.
