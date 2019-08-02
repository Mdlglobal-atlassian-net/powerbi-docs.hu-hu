---
title: Rendezés
description: A Power BI-vizualizációk alapértelmezett rendezési viselkedése.
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: f3d913e2bce34850dfae4c9486b2e43c78521a58
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424516"
---
# <a name="sorting-options"></a>Rendezési beállítások

A `Sorting` szabja meg a vizualizációk alapértelmezett rendezési viselkedését.
A funkcióhoz az alábbiakban ismertetett paraméterek egyike szükséges:

## <a name="default-sorting"></a>Alapértelmezett rendezés

Az `default` lehetőség a rendezés legegyszerűbb formája. Ezzel rendezhetők a „DataMappings” szakasz adatai.
Ezzel a beállítással a felhasználó rendezheti a „DataMappings” adatait, és megadhatja a rendezés irányát.

```json
    "sorting": {
        "default": {   }
    }
```

![Rendezési beállítások a helyi menüben](./media/sorting.png)

## <a name="implicit-sorting"></a>Implicit rendezés

Az `implicit` mód tömbparaméterekkel rendez – `clauses`, amelyek az egyes adatszerepkörök rendezését ismertetik.
Az `implicit` azt jelenti, hogy a vizualizáció felhasználója nem módosíthatja a rendezési sorrendet.
A Power BI nem jelenít meg rendezési beállításokat a vizualizáció menüjében. Az adatokat azonban megadott beállítások szerint rendezi.

A `clauses` paraméterek több objektumot tartalmazhatnak, két paraméterrel:

- A `role` a rendezendő `DataMapping` elemet határozza meg.

- A `direction` a rendezés irányát szabja meg (1=növekvő, 2=csökkenő).

```json
    "sorting": {
        "implicit": {
            "clauses": [
                {
                    "role": "category",
                    "direction": 1
                },
                {
                    "role": "measure",
                    "direction": 2
                }
            ]
        }
    }
```

## <a name="custom-sorting"></a>Egyéni rendezés

A `custom` azt jelenti, hogy a rendezést a fejlesztő felügyeli a vizualizáció kódjában.
