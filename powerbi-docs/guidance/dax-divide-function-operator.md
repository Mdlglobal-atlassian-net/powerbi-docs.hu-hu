---
title: 'DAX: A DIVIDE függvény és a divide operátor (/)'
description: Útmutató a DAX DIVIDE függvény használatához.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: v-pemyer
ms.openlocfilehash: c20a366ef657e851ef77a9649dbcc8b66b67dac0
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/02/2019
ms.locfileid: "74695197"
---
# <a name="dax-divide-function-vs-divide-operator-"></a>DAX: A DIVIDE függvény és a divide operátor (/)

Ha adatmodellezőként egy számláló nevezővel történő elosztásához ír DAX-kifejezést, akkor választhatja a [DIVIDE](/dax/divide-function-dax) függvényt vagy az osztás operátort (/ vagy perjel).

A DIVIDE függvény használatakor számlálót és nevezőt tartalmazó kifejezéseket kell megadnia. Másik lehetőségként átadhat egy _alternatív eredményt_ jelölő értéket.

```dax
DIVIDE(<numerator>, <denominator> [,<alternateresult>])
```

A DIVIDE függvény a nullával való osztást tartalmazó esetek automatikus kezelésére lett tervezve. Ha nem ad meg alternatív eredményt, a nevező pedig nulla vagy ÜRES, a függvény eredménye ÜRES. Amikor megad egy alternatív eredményt, ÜRES helyett az lesz a visszaadott eredmény.

A DIVIDE függvény kézenfekvő, mivel segítségével a kifejezésnek nem kell tesztelnie a nevező értékét. Ez a függvény emellett jobban optimalizált a nevező értékének tesztelésére, mint az [IF](/dax/if-function-dax) függvény. A teljesítménytöbblet jelentős, mivel a nullával osztás költséges. A DIVIDE használata tömörebb és elegánsabb kifejezést eredményez.

## <a name="example"></a>Példa

A következő mértékkifejezés biztonságos osztást eredményez, azonban négy DAX-függvényt tartalmaz.

```dax
Profit Margin =
IF(
    OR(
        ISBLANK([Sales]),
        [Sales] == 0
    ),
    BLANK(),
    [Profit] / [Sales]
)
```

Ez a mértékkifejezés ugyanazt eredményezi, azonban hatékonyabban és elegánsabban.

```dax
Profit Margin =
DIVIDE([Profit], [Sales])
```

## <a name="recommendations"></a>Javaslatok

A DIVIDE függvényt olyan esetekben célszerű használnia, amikor a nevető egy olyan kifejezés, amely _lehetséges_, hogy nulla vagy ÜRES eredménnyel zárul.

Ha a nevező egy állandó érték, használja a divide operátort. Ebben az esetben az osztás mindenképpen sikeres lesz, a kifejezés pedig jobb teljesítményt nyújt, mivel elkerüli a felesleges tesztelést.

Alaposan fontolja meg, hogy a DIVIDE függvény adjon-e vissza alternatív értéket. A mértékek esetében általában jobb tervezésre vall, ha az ÜRES értéket adják vissza, ha a jelentéssel bíró eredmény nem értékelhető. További információ: [Ne konvertálja a BLANK-eket értékekre](dax-avoid-converting-blank.md).

## <a name="next-steps"></a>Következő lépések

Erről a cikkről a következő forrásanyagokban talál további információt:

- [Data Analysis Expressions-referencia (DAX)](/dax/)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
