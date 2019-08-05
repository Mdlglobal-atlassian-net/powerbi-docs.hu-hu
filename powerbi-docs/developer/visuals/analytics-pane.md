---
title: Az Elemzési panel
description: Dinamikus referenciavonalak létrehozása a Power BI-vizualizációkban
author: Guy-Moses
ms.author: guymos
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: b3b50f8dbcf40a3923e86422e24f8ed020894445
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425528"
---
# <a name="analytics-pane-in-power-bi-visuals"></a>Az Elemzés panel Power BI-vizualizációkban

Az **Elemzés panel** 2018 novemberében lett [bevezetve natív vizualizációkhoz](https://docs.microsoft.com/power-bi/desktop-analytics-pane).
Egyéni vizualizációk az API 2.5.0-ás verziójával jeleníthetik meg és kezelhetik tulajdonságaikat az **Elemzés panelen**.

![Elemzés panel](./media/visualization-pane-analytics-tab.png)

A kezelése a [tulajdonságok Formázás panelen végzett kezeléséhez](https://docs.microsoft.com/power-bi/developer/custom-visual-develop-tutorial-format-options) hasonlóan, a vizualizáció capabilities.json fájljában definiált objektummal végezhető. 

A különbségek a következők:

1. Az `object` definíciója alatt egy 2 értékű `objectCategory` objektumot kell felvenni.

    > [!NOTE]
    > Az `objectCategory` az API 2.5.0 verziójában bevezetett választható mező. A vizualizációnak az objektum által vezérelt jellemzőjét határozza meg (1 = Formázás, 2 = Elemzés). A „Formázás” a megjelenésre, színekre, tengelyekre, címkékre stb. vonatkozik. Az „Elemzés” előrejelzésekhez, trendvonalakhoz, referenciavonalakhoz, alakzatokhoz és hasonlókhoz használható.
    >
    > Ha nincs megadva, az `objectCategory` alapértelmezett értéke „Formázás”.

2. Az objektumnak rendelkeznie kell az alábbi két tulajdonsággal:
    1. A `show` logikai típusú, alapértelmezetten hamis.
    2. A `displayName` szöveg típusú. Ennek az alapértelmezettnek választott értéke lesz a példány kezdeti megjelenítendő neve.

```json
{
  "objects": {
    "YourAnalyticsPropertiesCard": {
      "displayName": "Your analytics properties card's name",
      "objectCategory": 2,
      "properties": {
        "show": {
          "type": {
            "bool": true
          }
        },
        "displayName": {
          "type": {
            "text": true
          }
        },
      ... //any other properties for your Analytics card
      }
    }
  ...
  }
}
```

Minden más tulajdonság a formázási objektumoknál is használt módon határozható meg. Az objektumenumerálás pontosan úgy végezhető, mint a **Formázás panelen**.

***Ismert korlátozások és problémák***

  1. Több példány egyelőre nem támogatott. Az objektumokhoz nem tartozhat más [selector](https://microsoft.github.io/PowerBI-visuals/docs/concepts/objects-and-properties/#selector), csak statikus (tehát „selector”: null), és az egyéni vizualizációk nem rendelkezhetnek egy kártya több, felhasználó által definiált példányával.
  2. Az `integer` típusú tulajdonságok megjelenítése nem megfelelő. Ennek elkerülésére használható a `numeric` típus.

> [!NOTE]
> Az Elemzési panelt csak olyan objektumokhoz érdemes használni, amelyek új információkat nyújtanak, vagy új megvilágításba helyezik a megjelenített információt. Ilyenek például a lényeges trendeket bemutató dinamikus referenciavonalak.
> A vizualizáció megjelenését szabályozó beállításokat, például a formázást ajánlott a Formázás panelen tartani.
