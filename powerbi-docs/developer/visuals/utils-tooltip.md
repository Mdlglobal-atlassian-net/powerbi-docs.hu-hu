---
title: Az elemleírási eszközök használatának bemutatása a Power BI-vizualizációkban
description: Ez a cikk bemutatja, hogyan használhatja az elemleírási eszközöket az elemleírások testreszabásának leegyszerűsítésére a Power BI-vizualizációkban
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/14/2020
ms.openlocfilehash: 6f4aa276438d84825c4c7aba6872210b5f3a6564
ms.sourcegitcommit: d55d3089fcb3e78930326975957c9940becf2e76
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/04/2020
ms.locfileid: "78264220"
---
# <a name="tooltip-utils"></a>Elemleírási eszközök
Ez a cikk segít telepíteni, importálni és használni az elemleírási eszközöket. Az eszközöket Power BI-vizualizációk bármilyen elemleírásának testreszabásához használhatja.

## <a name="requirements"></a>Követelmények
A csomag használatához a következőkre lesz szüksége:
* [node.js](https://nodejs.org) (a legújabb LTS-verziót ajánljuk)
* [npm](https://www.npmjs.com/) (a minimális támogatott verzió a 3.0.0)
* A [PowerBI-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools) által létrehozott egyéni vizualizáció

## <a name="installation"></a>Telepítés

A csomag telepítéséhez az alábbi parancsot kell futtatni az aktuális vizualizációt tartalmazó mappában:

```bash
npm install powerbi-visuals-utils-colorutils --save
```
Ez a parancs telepíti a csomagot, és függőségként hozzáad egy csomagot a ```package.json``` fájlhoz

## <a name="usage"></a>Használat

> A használati útmutató a csomag nyilvános API-ját ismerteti. A csomag minden nyilvános felületéhez találhat egy leírást és néhány példát.

Ezzel a csomaggal `TooltipServiceWrapper` elemet és olyan metódusokat hozhat létre, amelyekkel kezelheti az elemleírás-műveleteket. A következő elemleírás-felületeket használja: `ITooltipServiceWrapper`, `TooltipEventArgs`, `TooltipEnabledDataPoint`. 

Emellett a mobilos fejlesztéshez kapcsolódó konkrét metódusokat (érintéses események kezelői) tartalmaz: `touchEndEventName`, `touchStartEventName`, `usePointerEvents`.

A `TooltipServiceWrapper` a legegyszerűbb módja az elemleírások módosításának.

Ez a modul a következő függvényt és interfészet biztosítja:
* [ITooltipServiceWrapper](#itooltipservicewrapper)
  * [addTooltip](#itooltipservicewrapperaddtooltip)
  * [hide](#itooltipservicewrapperhide)

* [Interfészek](#interfaces)
  * [TooltipEventArgs](#tooltipeventargs)
  * [TooltipEnabledDataPoint](#tooltipenableddatapoint)
  * [TooltipServiceWrapperOptions](#tooltipservicewrapperoptions)
* [Érintéses események](#touch-events)

### `createTooltipServiceWrapper`
Ez a függvény létrehozza az ITooltipServiceWrapper egy példányát.

```typescript
function createTooltipServiceWrapper(tooltipService: ITooltipService, rootElement: Element, handleTouchDelay?: number,  getEventMethod?: () => MouseEvent): ITooltipServiceWrapper;
```

Az ```ITooltipService``` a [IVisualHost](https://github.com/microsoft/PowerBI-visuals-tools/blob/master/templates/visuals/.api/v2.6.0/PowerBI-visuals.d.ts#L1335) területen érhető el.

**Példa:**

```typescript
import { createTooltipServiceWrapper } from "powerbi-visuals-utils-tooltiputils";

export class YourVisual implements IVisual {
    // implementation of IVisual.

    constructor(options: VisualConstructorOptions) {
        createTooltipServiceWrapper(
            options.host.tooltipService,
            options.element);

        // returns: an instance of ITooltipServiceWrapper.
    }
}
```

Az egyéni vizualizáció példakódjára [itt](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L391) vethet egy pillantást.

### `ITooltipServiceWrapper`
Ez az interfész a TooltipService nyilvános metódusait ismerteti.

```typescript
interface ITooltipServiceWrapper {
    addTooltip<T>(selection: d3.Selection<any, any, any, any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => powerbi.extensibility.VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => powerbi.visuals.ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
    hide(): void;
}
```

#### `ITooltipServiceWrapper.addTooltip`

Ez a metódus elemleírásokat a jelenlegi kijelöléshez.

```typescript
addTooltip<T>(selection: d3.Selection<any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
```

**Példa:**

```typescript
import { createTooltipServiceWrapper, TooltipEventArgs, ITooltipServiceWrapper, TooltipEnabledDataPoint } from "powerbi-visuals-utils-tooltiputils";

let bodyElement = d3.select("body");

let element = bodyElement
    .append("div")
    .style({
        "background-color": "green",
        "width": "150px",
        "height": "150px"
    })
    .classed("visual", true)
    .data([{
        tooltipInfo: [{
            displayName: "Power BI",
            value: 2016
        }]
    }]);

let tooltipServiceWrapper: ITooltipServiceWrapper = createTooltipServiceWrapper(tooltipService, bodyElement.get(0)); // tooltipService is from the IVisualHost.

tooltipServiceWrapper.addTooltip<TooltipEnabledDataPoint>(element, (eventArgs: TooltipEventArgs<TooltipEnabledDataPoint>) => {
    return eventArgs.data.tooltipInfo;
});

// You will see a tooltip if you mouseover the element.
```

Az egyéni vizualizáció példakódjára [itt](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L2931) vethet egy pillantást.

Figyelje meg a Gantt egyéni vizualizációjához tartozó elemleírások testreszabását az alábbi példában, [itt](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L573-L648)

### `ITooltipServiceWrapper.hide`

Ez a metódus elrejti az elemleírást.

```typescript
hide(): void;
```

**Példa:**

```typescript
import {createTooltipServiceWrapper} from "powerbi-visuals-utils-tooltiputils";

let tooltipServiceWrapper = createTooltipServiceWrapper(options.host.tooltipService, options.element); // options are from the VisualConstructorOptions.

tooltipServiceWrapper.hide();
```
### `Interfaces`
Ezek a felületek a TooltipServiceWrapper létrehozásakor és használata közben használatosak. Emellett az előző témakörben szereplő példákban is szerepeltek, [itt](#itooltipservicewrapperaddtooltip).

#### `TooltipEventArgs`
```typescript
interface TooltipEventArgs<TData> {
    data: TData;
    coordinates: number[];
    elementCoordinates: number[];
    context: HTMLElement;
    isTouchEvent: boolean;
}
```

#### `TooltipEnabledDataPoint`
```typescript
interface TooltipEnabledDataPoint {
    tooltipInfo?: powerbi.extensibility.VisualTooltipDataItem[];
}
```

#### `TooltipServiceWrapperOptions`
```typescript
interface TooltipServiceWrapperOptions {
    tooltipService: ITooltipService;
    rootElement: Element;
    handleTouchDelay: number;
    getEventMethod?: () => MouseEvent;
```

### `Touch events`

Az új elemleírási eszközök már számos, mobilos fejlesztéshez hasznos érintéses eseményt képesek kezelni.

#### `touchStartEventName`
```typescript
function touchStartEventName(): string
```
Ez a metódus az érintéses indítási esemény nevét adja vissza.

#### `touchEndEventName`
```typescript
function touchEndEventName(): string
```
Ez a metódus az érintéses indítási esemény nevét adja vissza.

#### `usePointerEvents`
```typescript
function usePointerEvents(): boolean
```
Ez a metódus megállapítja, hogy az aktuális touchStart-esemény kapcsolódik-e egy mutatóhoz.
