---
title: A szeletelők szinkronizálásának engedélyezése Power BI-vizualizációkban
description: Ez a cikk azt írja le, hogyan engedélyezhető a szeletelők szinkronizálása Power BI-vizualizációkban.
author: EugeneElkin
ms.author: v-evelk
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 4d7b73a5d06f34fd197464d4444d0e19d6c1c026
ms.sourcegitcommit: b602cdffa80653bc24123726d1d7f1afbd93d77c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/03/2019
ms.locfileid: "70237212"
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
