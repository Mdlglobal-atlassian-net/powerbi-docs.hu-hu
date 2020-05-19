---
title: A supportsMultiVisualSelection funkció
description: Ez a cikk a supportsMultiVisualSelection funkció Power BI-vizualizációkban való használatát és annak követelményeit ismerteti.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 6ad986308fb82f8191829d29654bb96b55d0fbd0
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83272695"
---
# <a name="use-the-supportsmultivisualselection-feature"></a>A supportsMultiVisualSelection funkció használata

A `supportsMultiVisualSelection` funkció lehetővé teszi, hogy egy jelentés több vizualizációjában használhasson kiválasztást.

## <a name="example"></a>Példa

Az egynél több vizualizációt tartalmazó jelentésekben két érték kiválasztásával más vizualizációkra is alkalmazhatja azokat. Például a [Kiskereskedelmi elemzési mintában](../../create-reports/sample-retail-analysis.md) válassza a **Fashions Direct** értéket egy vizualizációban. A ctrl billentyű lenyomása mellett válassza a **Jan** értéket egy másik vizualizációban. A jelentésben a kiválasztások a funkció használatát támogató többi vizualizációra is érvényesek lesznek. Az egyéb vizualizációk hatóköre innentől kiterjed a **Fashions Direct** és **Jan** értékre.

## <a name="requirements"></a>Követelmények

Ehhez a funkcióhoz 3.2.0-s vagy újabb verziójú API szükséges.

Ez a funkció képvizualizációkra nem alkalmazható. Nem alkalmazható olyan speciális vizualizációkra, mint a fő tényező, a dekompozíciós fa, a kérdések és válaszok típusú vizualizációk, a szövegmező és a mérőműszer-diagramok.

## <a name="usage"></a>Használat

A `supportsMultiVisualSelection` funkció használatához adja hozzá az alábbi kódot a vizualizáció `capabilities.json` fájljához.

```json
    {   
            ...
        "supportsMultiVisualSelection": true
            ...
    }
```

## <a name="next-steps"></a>Következő lépések

A Power BI alapfogalmainak megismeréséhez tekintse meg a [Vizualizációk a Power BI-ban](power-bi-visuals-concept.md) című ismertetőt.

A Power BI-fejlesztés kipróbálásához tekintse meg a [Power BI-vizualizáció fejlesztése](custom-visual-develop-tutorial.md) című ismertetőt.
