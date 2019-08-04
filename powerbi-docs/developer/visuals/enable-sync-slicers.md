---
title: Szeletelők szinkronizálásának engedélyezése
description: A szeletelők szinkronizálásának engedélyezése Power BI-vizualizációkban
author: EugeneElkin
ms.author: v-evelk
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 9966475e8bcaccad2090451b47ef09ef0a9af125
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425022"
---
# <a name="sync-slicers"></a>Szeletelők szinkronizálása

A [szeletelők szinkronizálásának](https://docs.microsoft.com/power-bi/desktop-slicers) támogatásához az egyéni szeletelő vizualizációjának az API 1.13-at vagy újabb verziót kell használnia.

A második szükséges elem a `capabilities.json` fájlban engedélyezett beállítás (lásd a lenti mintát).

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

A `capabilities.json` módosítása után megjelenik a Szeletelők szinkronizálása panel, amikor az egyéni szeletelővizualizációra kattint.

> [!NOTE]
> Ha a szeletelő több mint 1 mezőt (kategóriát vagy mértéket) tartalmaz, a funkció le lesz tiltva, mert a szeletelők szinkronizálása nem támogat több mezőt.

![Szeletelők szinkronizálása panel](./media/sync-slicers-panel.png)

A panelen láthatja, hogy a szeletelő láthatósága és szűrése több jelentésoldalra is alkalmazható.
