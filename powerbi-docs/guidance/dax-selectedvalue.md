---
title: 'DAX: A SELECTEDVALUE használata a VALUES helyett'
description: Útmutató a SELECTEDVALUE-függvények használatához.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/20/2019
ms.author: v-pemyer
ms.openlocfilehash: 6aef2c06cc62668ea7dea9fe404e294d1a5faa93
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/04/2020
ms.locfileid: "74700478"
---
# <a name="dax-use-selectedvalue-instead-of-values"></a>DAX: A SELECTEDVALUE használata a VALUES helyett

Adatmodellezőként néha előfordulhat, hogy DAX-kifejezést kell írnia, amely teszteli, hogy az oszlopot egy adott érték szerint szűri-e.

A DAX korábbi verzióiban ezt a követelményt három DAX-függvényt tartalmazó minta használatával lehetett biztonságosan teljesíteni. A függvények az [IF](/dax/if-function-dax), a [HASONEVALUE](/dax/hasonevalue-function-dax) és a [VALUES](/dax/values-function-dax). A következő mértékdefiníció bemutat egy példát. Kiszámítja az értékesítési adó összegét, de csak az ausztráliai ügyfelek részére végzett értékesítésekhez.

```dax
Australian Sales Tax =
IF(
    HASONEVALUE(Customer[Country-Region]),
    IF(
        VALUES(Customer[Country-Region]) = "Australia",
        [Sales] * 0.10
    )
)
```

A példában a HASONEVALUE függvény csak akkor adja vissza a TRUE értéket, ha az **Ország-régió** oszlop egyetlen érték alapján szűrt. Ha az értéke TRUE, a program a VALUES függvényt az „Australia” pontos szövegével hasonlítja össze. Ha a VALUES függvény a TRUE értéket adja vissza, az **Értékesítés** mértékét a program megszorozza 0,10-del (ami 10%-nak felel meg). Ha a HASONEVALUE függvény visszaadott értéke FALSE, mivel több mint egy értékkel szűri az oszlopot, az első IF függvény a BLANK értéket adja vissza.

A HASONEVALUE használata egy védelmi technika. Ez kötelező, mert lehetséges, hogy a program több érték alapján is szűri az **Ország-régió** oszlopot. Ebben az esetben a VALUES függvény több sort tartalmazó táblát ad vissza. Több sort tartalmazó tábla skalár értékkel való összehasonlítása hibát eredményez.

## <a name="recommendation"></a>Javaslat

Javasoljuk, hogy a [SELECTEDVALUE](/dax/selectedvalue-function) függvényt használja. Ugyanarra az eredményre vezet, mint az ebben a cikkben ismertetett minta, csak hatékonyabban és elegánsabban.

A SELECTEDVALUE függvény használatával most felülírja a például megadott mértékdefiníciót.

```dax
Australian Sales Tax =
IF(
    SELECTEDVALUE(Customer[Country-Region]) = "Australia",
    [Sales] * 0.10
)
```

> [!TIP]
> A SELECTEDVALUE függvénynek _alternatív eredmény_ értéket is át lehet adni. Az alternatív eredmény visszaadása akkor történik, ha nincs kiválasztva szűrő, vagy több szűrőt is alkalmazott az oszlopra.

## <a name="next-steps"></a>Következő lépések

Erről a cikkről a következő forrásanyagokban talál további információt:

- [Data Analysis Expressions-referencia (DAX)](/dax/)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
