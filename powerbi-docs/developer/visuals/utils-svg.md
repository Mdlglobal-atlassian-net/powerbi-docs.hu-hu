---
title: Az SVG-eszközök használatának bemutatása a Power BI-vizualizációkban
description: Ez a cikk bemutatja, hogyan használhatók az SVG-eszközök arra, hogy egyszerűbbé tegye az SVG-kezelést a Power BI-vizualizációknál
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: aa1ac8074e842a51b369c48f57c4b5016a80140c
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/14/2020
ms.locfileid: "79377972"
---
# <a name="svg-utils"></a>SVG-eszközök

Az SVGUtils a Power BI-vizualizációk SVG-kezelését egyszerűbbé tevő függvények és osztályok gyűjteménye

## <a name="installation"></a>Telepítés

A csomag telepítéséhez az alábbi parancsot kell futtatni az aktuális vizualizációt tartalmazó mappában:

```bash
npm install powerbi-visuals-utils-svgutils --save
```

## <a name="cssconstants"></a>CssConstants

A `CssConstants` modul biztosítja a speciális függvényeket és felületet ahhoz, hogy az osztály-választókkal dolgozhasson.

A `powerbi.extensibility.utils.svg.CssConstants` modul a következő függvényeket és interfészeket biztosítja:

## <a name="classandselector"></a>ClassAndSelector

Ez az interfész az osztályválasztó gyakori tulajdonságait írja le.

```typescript
interface ClassAndSelector {
  class: string;
  selector: string;
}
```

### <a name="createclassandselector"></a>createClassAndSelector

Ez a függvény létrehozza a ClassAndSelector egy példányát az osztály megadott nevével.

```typescript
function createClassAndSelector(className: string): ClassAndSelector;
```

Például:

```typescript
import { CssConstants } from "powerbi-visuals-utils-svgutils";
import createClassAndSelector = CssConstants.createClassAndSelector;
import ClassAndSelector = CssConstants.ClassAndSelector;

let divSelector: ClassAndSelector = createClassAndSelector("sample-block");

divSelector.selector === ".sample-block"; // returns: true
divSelector.class === "sample-block"; // returns: true
```

## <a name="manipulation"></a>manipulation

A `manipulation` speciális függvényeket biztosít sztringek létrehozásához az SVG-átalakítási tulajdonság használatával.

A modul a következő függvényeket biztosítja:

### <a name="translate"></a>translate

Ez a függvény egy fordítási sztringet hoz létre az SVG-átalakító tulajdonsággal való használathoz.

```typescript
function translate(x: number, y: number): string;
```

Például:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translate(100, 100);

// returns: translate(100,100)
```

### <a name="translatexwithpixels"></a>translateXWithPixels

Ez a függvény egy translateX sztringet hoz létre az SVG-átalakító tulajdonsággal való használathoz.

```typescript
function translateXWithPixels(x: number): string;
```

Például:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateXWithPixels(100);

// returns: translateX(100px)
```

### <a name="translatewithpixels"></a>translateWithPixels

Ez a függvény egy fordítási sztringet hoz létre az SVG-átalakító tulajdonsággal való használathoz.

```typescript
function translateWithPixels(x: number, y: number): string;
```

Például:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateWithPixels(100, 100);

// returns: translate(100px,100px)
```

### <a name="translateandrotate"></a>translateAndRotate

Ez a függvény egy translate-rotate sztringet hoz létre az SVG-átalakító tulajdonsággal való használathoz.

```typescript
function translateAndRotate(
  x: number,
  y: number,
  px: number,
  py: number,
  angle: number
): string;
```

Például:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateAndRotate(100, 100, 50, 50, 35);

// returns: translate(100,100) rotate(35,50,50)
```

### <a name="scale"></a>scale

Ez a függvény létrehoz egy méretezési karakterláncot, melyet az transform CSS-tulajdonságban használhat.

```typescript
function scale(scale: number): string;
```

Például:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.scale(50);

// returns: scale(50)
```

### <a name="transformorigin"></a>transformOrigin

Ez a függvény létrehoz egy transform-origin karakterláncot, melyet az transform-origin CSS-tulajdonságban használhat.

```typescript
function transformOrigin(xOffset: string, yOffset: string): string;
```

Például:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.transformOrigin(5, 5);

// returns: 5 5
```

### <a name="flushalld3transitions"></a>flushAllD3Transitions

Ez a függvény a D3 összes átmenetének befejeződését kényszeríti ki.

```typescript
function flushAllD3Transitions(): void;
```

Például:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.flushAllD3Transitions();

// forces every transition of D3 to complete
```

### <a name="parsetranslatetransform"></a>parseTranslateTransform

Ez a függvény elemzi az átalakítási karakterláncot a „translate (x, y)” értékkel.

```typescript
function parseTranslateTransform(input: string): { x: string; y: string };
```

Például:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.parseTranslateTransform("translate(100px,100px)");

// returns: { "x":"100px", "y":"100px" }
```

### <a name="createarrow"></a>createArrow

Ez a függvény létrehoz egy nyilat.

```typescript
function createArrow(
  width: number,
  height: number,
  rotate: number
): { path: string; transform: string };
```

Például:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.createArrow(10, 20, 5);

/* returns: {
    "path": "M0 0L0 20L10 10 Z",
    "transform": "rotate(5 5 10)"
}*/
```

## <a name="rect"></a>Rect

A `Rect` modul speciális függvényeket biztosít a téglalapok kezeléséhez.

A modul a következő függvényeket biztosítja:

### <a name="getoffset"></a>getOffset

Ez a függvény a négyszög eltolását adja vissza.

```typescript
function getOffset(rect: IRect): IPoint;
```

Például:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getOffset({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    x: 25,
    y: 25
}*/
```

### <a name="getsize"></a>getSize

Ez a függvény a téglalap méretét adja vissza.

```typescript
function getSize(rect: IRect): ISize;
```

Például:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getSize({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    width: 100,
    height: 100
}*/
```

### <a name="setsize"></a>setSize

Ez a függvény módosítja a négyszög méretét.

```typescript
function setSize(rect: IRect, value: ISize): void;
```

Például:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

let rectangle = { left: 25, top: 25, width: 100, height: 100 };

Rect.setSize(rectangle, { width: 250, height: 250 });

// rectangle === { left: 25, top: 25, width: 250, height: 250 }
```

### <a name="right"></a>right

Ez a függvény a téglalap megfelelő pozícióját adja vissza.

```typescript
function right(rect: IRect): number;
```

Például:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.right({ left: 25, top: 25, width: 100, height: 100 });

// returns: 125
```

### <a name="bottom"></a>bottom

Ez a függvény a négyszög alsó pozícióját adja vissza.

```typescript
function bottom(rect: IRect): number;
```

Például:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottom({ left: 25, top: 25, width: 100, height: 100 });

// returns: 125
```

### <a name="topleft"></a>topLeft

Ez a függvény a négyszög bal felső sarkát adja vissza.

```typescript
function topLeft(rect: IRect): IPoint;
```

Például:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.topLeft({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 25, y: 25 }
```

### <a name="topright"></a>topRight

Ez a függvény a négyszög jobb felső sarkát adja vissza.

```typescript
function topRight(rect: IRect): IPoint;
```

Például:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.topRight({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 125, y: 25 }
```

### <a name="bottomleft"></a>bottomLeft

Ez a függvény a négyszög bal alsó pozícióját adja vissza.

```typescript
function bottomLeft(rect: IRect): IPoint;
```

Például:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottomLeft({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 25, y: 125 }
```

### <a name="bottomright"></a>bottomRight

Ez a függvény a négyszög jobb alsó pozícióját adja vissza.

```typescript
function bottomRight(rect: IRect): IPoint;
```

### <a name="example"></a>Példa

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottomRight({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 125, y: 125 }
```

### <a name="clone"></a>clone

Ez a függvény létrehoz egy másolatot a négyszögből.

```typescript
function clone(rect: IRect): IRect;
```

Például:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.clone({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    left: 25, top: 25, width: 100, height: 100}
*/
```

### <a name="tostring"></a>toString

Ez a függvény a téglalapot karakterlánccá alakítja át.

```typescript
function toString(rect: IRect): string;
```

Például:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.toString({ left: 25, top: 25, width: 100, height: 100 });

// returns: {left:25, top:25, width:100, height:100}
```

### <a name="offset"></a>offset

Ez a függvény adott eltolást alkalmaz a négyszögre.

```typescript
function offset(rect: IRect, offsetX: number, offsetY: number): IRect;
```

Például:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.offset({ left: 25, top: 25, width: 100, height: 100 }, 50, 50);

/* returns: {
    left: 75,
    top: 75,
    width: 100,
    height: 100
}*/
```

### <a name="add"></a>add

Ez a függvény hozzáadja az első téglalapot a második téglalaphoz.

```typescript
function add(rect: IRect, rect2: IRect): IRect;
```

Például:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.add(
  { left: 25, top: 25, width: 100, height: 100 },
  { left: 50, top: 50, width: 75, height: 75 }
);

/* returns: {
    left: 75,
    top: 75,
    height: 175,
    width: 175
}*/
```

### <a name="getclosestpoint"></a>getClosestPoint

Ez a függvény a téglalap legközelebbi pontját adja vissza az adott pontra.

```typescript
function getClosestPoint(rect: IRect, x: number, y: number): IPoint;
```

Például:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getClosestPoint({ left: 0, top: 0, width: 100, height: 100 }, 50, 50);

/* returns: {
    x: 50,
    y: 50
}*/
```

### <a name="equal"></a>equal

Ez a függvény összehasonlítja a téglalapokat, és igaz értéket ad vissza, ha azonosak.

```typescript
function equal(rect1: IRect, rect2: IRect): boolean;
```

Például:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.equal(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 50, top: 50, width: 100, height: 100 }
);

// returns: false
```

### <a name="equalwithprecision"></a>equalWithPrecision

Ez a függvény összehasonlítja a téglalapokat az értékek pontosságának értékelésével.

```typescript
function equalWithPrecision(rect1: IRect, rect2: IRect): boolean;
```

Például:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.equalWithPrecision(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 50, top: 50, width: 100, height: 100 }
);

// returns: false
```

### <a name="isempty"></a>isEmpty

Ez a függvény ellenőrzi, hogy a téglalap üres-e.

```typescript
function isEmpty(rect: IRect): boolean;
```

Például:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.isEmpty({ left: 0, top: 0, width: 0, height: 0 });

// returns: true
```

### <a name="containspoint"></a>containsPoint

Ez a függvény ellenőrzi, hogy a téglalap tartalmazza-e a pontot.

```typescript
function containsPoint(rect: IRect, point: IPoint): boolean;
```

Például:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.containsPoint(
  { left: 0, top: 0, width: 100, height: 100 },
  { x: 50, y: 50 }
);

// returns: true
```

### <a name="isintersecting"></a>isIntersecting

Ez a függvény ellenőrzi, hogy a téglalapok metszik-e egymást.

```typescript
function isIntersecting(rect1: IRect, rect2: IRect): boolean;
```

Például:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.isIntersecting(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 50 }
);

// returns: true
```

### <a name="intersect"></a>intersect

Ez a függvény a téglalapok metszetét adja vissza.

```typescript
function intersect(rect1: IRect, rect2: IRect): IRect;
```

Például:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.intersect(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 50 }
);

/* returns: {
    left: 0,
    top: 0,
    width: 50,
    height: 50
}*/
```

### <a name="combine"></a>combine

Ez a függvény a téglalapokat kombinálja.

```typescript
function combine(rect1: IRect, rect2: IRect): IRect;
```

Például:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.combine(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 120 }
);

/* returns: {
    left: 0,
    top: 0,
    width: 100,
    height: 120
}*/
```

### <a name="getcentroid"></a>getCentroid

Ez a függvény a téglalap középpontját adja vissza.

```typescript
function getCentroid(rect: IRect): IPoint;
```

Például:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getCentroid({ left: 0, top: 0, width: 100, height: 100 });

/* returns: {
    x: 50,
    y: 50
}*/
```

## <a name="pointer"></a>pointer

A `pointer` modul egy speciális függvényt biztosít a mutató pozíciójának lekéréséhez.

A modul a következő függvényeket biztosítja:

### <a name="getcoordinates"></a>getCoordinates

Ez a függvény a mutató pozícióját adja vissza.

```typescript
function getCoordinates(rootNode: Element, isPointerEvent: boolean): number[];
```

Például:

```typescript
import { pointer } from "powerbi-visuals-utils-svgutils";

let bodySelection = d3.select("body");

bodySelection
  .append("div")
  .style({
    width: "100px",
    height: "100px",
    "background-color": "green"
  })
  .on("click", () => {
    pointer.getCoordinates(bodySelection.node(), true);
  });

// click element, after that you will get position of the pointer
```
