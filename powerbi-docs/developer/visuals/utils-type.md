---
title: A típuseszközök használatának bemutatása a Power BI-vizualizációkban
description: Ez a cikk bemutatja, hogyan bővíthetők ki a Power BI-vizualizációkhoz kapcsolódó alapvető típusok az SVG-eszközök segítségével.
author: vtkalek
ms.author: asander
manager: asander
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 16645dc70cc236f809a2f2977a2b2fc1a048c254
ms.sourcegitcommit: 4359baa43ca01b179d28ec59f4e61ba8c07ee288
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/20/2019
ms.locfileid: "75308548"
---
# <a name="type-utils"></a>Írási eszközök

A TypeUtils olyan függvényeket és osztályokat tartalmaz, amelyekkel kibővítheti a Power BI-vizualizációkban használt alapvető típusokat.

## <a name="installation"></a>Telepítés

A csomag telepítéséhez az alábbi parancsot kell futtatni az aktuális egyéni vizualizációt tartalmazó mappában:

npm install powerbi-visuals-utils-typeutils --save Ezzel a paranccsal telepítheti a csomagot, és felveheti függőségként a csomagot a package.json fájlba.

## <a name="double"></a>Double

A `Double` segítségével befolyásolhatja a számok pontosságát.

A modul a következő függvényeket biztosítja:

### <a name="pow10"></a>pow10

Az alábbi függvény a 10 hatványait adja vissza.

```typescript
function pow10(exp: number): number;
```

Például:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.pow10(25);

// returns: 1e+25
```

### <a name="log10"></a>log10

Ez a függvény a szám 10-es alapú logaritmusát adja vissza.

```typescript
function log10(val: number): number;
```

Például:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.log10(25);

// returns: 1
```

## <a name="getprecision"></a>getPrecision

Ez a függvény a 10 hatványát adja vissza, amely a szám pontosságát képviseli.

```typescript
function getPrecision(x: number, decimalDigits?: number): number;
```

Például:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.getPrecision(562344, 6);

// returns: 0.1
```

### <a name="equalwithprecision"></a>equalWithPrecision

Ez a függvény ellenőrzi, hogy a két szám közötti különbség kisebb-e a megadott pontosságnál.

```typescript
function equalWithPrecision(x: number, y: number, precision?: number): boolean;
```

Például:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.equalWithPrecision(1, 1.005, 0.01);

// returns: true
```

### <a name="lesswithprecision"></a>lessWithPrecision

Ez a függvény ellenőrzi, hogy az első érték kisebb-e a második értéknél.

```typescript
function lessWithPrecision(x: number, y: number, precision?: number): boolean;
```

Például:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.lessWithPrecision(0.995, 1, 0.001);

// returns: true
```

### <a name="lessorequalwithprecision"></a>lessOrEqualWithPrecision

Ez a függvény ellenőrzi, hogy az első érték kisebb-e a második értéknél, vagy egyenlő-e azzal.

```typescript
function lessOrEqualWithPrecision(x: number, y: number, precision?: number): boolean;
```

Például:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.lessOrEqualWithPrecision(1.005, 1, 0.01);

// returns: true
```

### <a name="greaterwithprecision"></a>greaterWithPrecision

Ez a függvény ellenőrzi, hogy az első érték nagyobb-e a második értéknél.

```typescript
function greaterWithPrecision(x: number, y: number, precision?: number): boolean;
```

Például:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.greaterWithPrecision(1, 0.995, 0.01);

// returns: false
```

### <a name="greaterorequalwithprecision"></a>greaterWithPrecision

Ez a függvény ellenőrzi, hogy az első érték nagyobb-e a második értéknél, vagy egyenlő-e azzal.

```typescript
function greaterOrEqualWithPrecision(x: number, y: number, precision?: number): boolean;
```

Például:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.greaterOrEqualWithPrecision(1, 1.005, 0.01);

// returns: true
```

### <a name="floorwithprecision"></a>floorWithPrecision

Ez a függvény a szám alsó egészrészét adja meg a kívánt pontossággal.

```typescript
function floorWithPrecision(x: number, precision?: number): number;
```

Például:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.floorWithPrecision(5.96, 0.001);

// returns: 5
```

### <a name="ceilwithprecision"></a>ceilWithPrecision

Ez a függvény (`ceils`) a szám felső egészrészét adja meg a kívánt pontossággal.

```typescript
function ceilWithPrecision(x: number, precision?: number): number;
```

Például:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ceilWithPrecision(5.06, 0.001);

// returns: 6
```

### <a name="floortoprecision"></a>floorToPrecision

Ez a függvény a szám alsó egészrészét adja meg a kívánt pontosságra.

```typescript
function floorToPrecision(x: number, precision?: number): number;
```

Például:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.floorToPrecision(5.96, 0.1);

// returns: 5.9
```

### <a name="ceiltoprecision"></a>ceilToPrecision

Ez a függvény (`ceils`) a szám felső egészrészét adja meg a kívánt pontosságra.

```typescript
function ceilToPrecision(x: number, precision?: number): number;
```

Például:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ceilToPrecision(-506, 10);

// returns: -500
```

### <a name="roundtoprecision"></a>roundToPrecision

Ez a függvény a kívánt pontossággal kerekíti a számot.

```typescript
function roundToPrecision(x: number, precision?: number): number;
```

Például:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.roundToPrecision(596, 10);

// returns: 600
```

### <a name="ensureinrange"></a>ensureInRange

Ez a függvény egy, a minimum és a maximum közötti számot ad vissza.

```typescript
function ensureInRange(x: number, min: number, max: number): number;
```

Például:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ensureInRange(-27.2, -10, -5);

// returns: -10
```

### <a name="round"></a>round

Ez a függvény kerekíti a számot.

```typescript
function round(x: number): number;
```

Például:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.round(27.45);

// returns: 27
```

### <a name="removedecimalnoise"></a>removeDecimalNoise

Ez a függvény eltávolítja a szám tizedesvessző utáni részét.

```typescript
function removeDecimalNoise(value: number): number;
```

Például:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.removeDecimalNoise(21.493000000000002);

// returns: 21.493
```

### <a name="isinteger"></a>isInteger

Ez a függvény ellenőrzi, hogy a szám egész szám-e.

```typescript
function isInteger(value: number): boolean;
```

Például:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.isInteger(21.493000000000002);

// returns: false
```

### <a name="toincrement"></a>toIncrement

Ez a függvény a megadott számmal növeli a számot, majd ezt a számot kerekíti.

```typescript
function toIncrement(value: number, increment: number): number;
```

Például:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.toIncrement(0.6383723, 0.05);

// returns: 0.65
```

## <a name="prototype"></a>Prototype

A `Prototype` lehetőségeket kínál az objektumok örökítésére.

A modul a következő függvényeket biztosítja:

## <a name="inherit"></a>inherit

Ez a függvény egy új objektumot ad vissza, amelynek a megadott objektum szolgál prototípusául.

```typescript
function inherit<T>(obj: T, extension?: (inherited: T) => void): T;
```

Például:

```typescript
import { prototype } from "powerbi-visuals-utils-typeutils";
// ...

let base = { Microsoft: "Power BI" };

prototype.inherit(base);

/* returns: {
    __proto__: {
        Microsoft: "Power BI"
    }
}*/
```

## <a name="inheritsingle"></a>inheritSingle

Ez a függvény egy új objektumot ad vissza, amelynek a megadott objektum szolgál prototípusául, de akkor, és csak akkor, ha a prototípust nem állították be.

```typescript
function inheritSingle<T>(obj: T): T;
```

Például:

```typescript
import { prototype } from "powerbi-visuals-utils-typeutils";
// ...

let base = { Microsoft: "Power BI" };

prototype.inheritSingle(base);

/* returns: {
    __proto__: {
        Microsoft: "Power BI"
    }
}*/
```

## <a name="pixelconverter"></a>PixelConverter

A `PixelConverter` lehetőséget kínál a képpontok pontokká alakítására, és fordítva.

A modul a következő függvényeket biztosítja:

## <a name="tostring"></a>toString

Ez a függvény a képpontértéket sztringgé alakítja.

```typescript
function toString(px: number): string;
```

Például:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.toString(25);

// returns: 25px
```

## <a name="frompoint"></a>fromPoint

Ez a függvény a megadott pontértéket képpontértékké alakítja, majd visszaad egy sztringalapú értelmezést.

```typescript
function fromPoint(pt: number): string;
```

Például:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.fromPoint(8);

// returns: 33.33333333333333px
```

## <a name="frompointtopixel"></a>fromPointToPixel

Ez a függvény képpontértékké alakítja a megadott pontértéket.

```typescript
function fromPointToPixel(pt: number): number;
```

Például:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.fromPointToPixel(8);

// returns: 10.666666666666666
```

## <a name="topoint"></a>toPoint

Ez a függvény pontértékké alakítja a képpontértéket.

```typescript
function toPoint(px: number): number;
```

Például:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.toPoint(8);

// returns: 6
```
