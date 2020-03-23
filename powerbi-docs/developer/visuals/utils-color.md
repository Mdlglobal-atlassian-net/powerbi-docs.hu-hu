---
title: A színeszközök használatának bemutatása a Power BI-vizualizációkban
description: Ez a cikk leírja, hogyan lehet a színeszközök segítségével egyszerűbben alkalmazni a témákat és a palettákat a vizualizáció adatpontjaira a Power BI-vizualizációkban
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 02/14/2020
ms.openlocfilehash: 8de530871739a18c1afc72cee3e0da5fc70ebb16
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/14/2020
ms.locfileid: "79379352"
---
# <a name="color-utils"></a>Színeszközök
Ez a cikk segítséget nyújt a színeszközök telepítéséhez, importálásához és használatához. Ez a cikk leírja, hogyan lehet a színeszközök segítségével egyszerűbben alkalmazni a témákat és a palettákat a vizualizáció adatpontjaira a Power BI-vizualizációkban.

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

Az interaktivitási eszközök használatához importálnia kell a szükséges összetevőket a vizualizáció forráskódjában.
```typescript
import { ColorHelper } from "powerbi-visuals-utils-colorutils";
```

Ismerje meg, hogyan telepítheti és használhatja a színeszközöket a Power BI-vizualizációkban:

* [Használati útmutató] A használati útmutató a csomag nyilvános API-ját ismerteti. A csomag minden nyilvános felületéhez találhat egy leírást és néhány példát.

A csomag az alábbi osztályokat és modulokat tartalmazza:
* [ColorHelper](#colorhelper) – segít különböző színeket létrehozni a diagramértékekhez
* [colorUtils](#colorutils) – segíti átalakítani a színformátumokat

## `ColorHelper`
A `ColorHelper` osztály a következő függvényeket és metódusokat biztosítja:

### `getColorForSeriesValue` 
Ez a metódus lekéri az adott sorozat értékének színét. Ha nincs megadva explicit szín vagy alapértelmezett szín, a metódus a színskálából osztja ki a színt a sorozat számára.
```typescript
getColorForSeriesValue(objects: IDataViewObjects, value: PrimitiveValue, themeColorName?: ThemeColorName): string;
```
#### <a name="example"></a>Példa
```typescript
import powerbi from "powerbi-visuals-api";
import { ColorHelper } from "powerbi-visuals-utils-colorutils";

import DataViewObjects = powerbi.DataViewObjects;

import DataViewValueColumns = powerbi.DataViewValueColumns;
import DataViewValueColumnGroup = powerbi.DataViewValueColumnGroup;
import DataViewObjectPropertyIdentifier = powerbi.DataViewObjectPropertyIdentifier;

import IVisual = powerbi.extensibility.visual.IVisual;
import IColorPalette = powerbi.extensibility.IColorPalette;
import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions;
import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions;

export class YourVisual implements IVisual {
    // Implementation of IVisual

    private colorPalette: IColorPalette;

    constructor(options: VisualConstructorOptions) {
        this.colorPalette = options.host.colorPalette;
    }

    public update(visualUpdateOptions: VisualUpdateOptions): void {
        const valueColumns: DataViewValueColumns = visualUpdateOptions.dataViews[0].categorical.values,
            grouped: DataViewValueColumnGroup[] = valueColumns.grouped(),
            defaultDataPointColor: string = "green",
            fillProp: DataViewObjectPropertyIdentifier = {
                objectName: "objectName",
                propertyName: "propertyName"
            };

        let colorHelper: ColorHelper = new ColorHelper(
            this.colorPalette,
            fillProp,
            defaultDataPointColor);

        for (let i = 0; i < grouped.length; i++) {
            let grouping: DataViewValueColumnGroup = grouped[i];

            let color = colorHelper.getColorForSeriesValue(grouping.objects, grouping.name); // returns a color of the series
        }
    }
}
```

### `getColorForMeasure`
Ez a metódus lekéri az adott mérték színét.
```typescript
 getColorForMeasure(objects: IDataViewObjects, measureKey: any, themeColorName?: ThemeColorName): string;
```
#### <a name="example"></a>Példa
```typescript
import powerbi from "powerbi-visuals-api";
import { ColorHelper } from "powerbi-visuals-utils-colorutils";

import DataViewObjects = powerbi.DataViewObjects;
import IVisual = powerbi.extensibility.visual.IVisual;
import IColorPalette = powerbi.extensibility.IColorPalette;
import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions;
import DataViewObjectPropertyIdentifier = powerbi.DataViewObjectPropertyIdentifier;
import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions;

export class YourVisual implements IVisual {
    // Implementation of IVisual

    private colorPalette: IColorPalette;

    constructor(options: VisualConstructorOptions) {
        this.colorPalette = options.host.colorPalette;
    }

    public update(visualUpdateOptions: VisualUpdateOptions): void {
        const objects: DataViewObjects = visualUpdateOptions.dataViews[0].categorical.categories[0].objects[0],
            defaultDataPointColor: string = "green",
            fillProp: DataViewObjectPropertyIdentifier = {
                objectName: "objectName",
                propertyName: "propertyName"
            };

        let colorHelper: ColorHelper = new ColorHelper(
            this.colorPalette,
            fillProp,
            defaultDataPointColor);

        let color = colorHelper.getColorForMeasure(objects, ""); // returns a color
    }
}
```

### <a name="static-normalizeselector"></a>statikus `normalizeSelector`
Ez a metódus a normalizált szelektort adja vissza
```typescript
static normalizeSelector(selector: Selector, isSingleSeries?: boolean): Selector;
```
#### <a name="example"></a>Példa
```typescript
import ISelectionId = powerbi.visuals.ISelectionId;
import { ColorHelper } from "powerbi-visuals-utils-colorutils";

let selectionId: ISelectionId = ...;
let selector = ColorHelper.normalizeSelector(selectionId.getSelector(), false);
```

A `getThemeColor` és a `getHighContrastColor` metódus a színtéma színeire vonatkozik.
A `ColorHelper` `isHighContrast` tulajdonsága is hasznos lehet az ellenőrzésnél.

### `getThemeColor`
Ez a metódus a téma színét adja vissza
```typescript
 getThemeColor(themeColorName?: ThemeColorName): string;
```
### `getHighContrastColor`
 Ez a metódus a kontrasztos megjelenítési mód színét adja vissza
```typescript
getHighContrastColor(themeColorName?: ThemeColorName, defaultColor?: string): string;
```
#### <a name="example-related-to-high-contrast-mode-usage"></a>Példa kontrasztos megjelenítési mód használatára:
```typescript

import { ColorHelper } from "powerbi-visuals-utils-colorutils";

export class MyVisual implements IVisual {
        private colorHelper: ColorHelper;

        private init(options: VisualConstructorOptions): void {
            this.colors = options.host.colorPalette;
            this.colorHelper = new ColorHelper(this.colors);
        } 

            private createViewport(element: HTMLElement): void {
                const fontColor: string = "#131aea";
                const axisBackgroundColor: string = this.colorHelper.getThemeColor();
                
                // some d3 code before
                d3ElementName.attr("fill", colorHelper.getHighContrastColor("foreground", fontColor);
            }
                
            public static parseSettings(dataView: DataView, colorHelper: ColorHelper): VisualSettings {
                // some code that should be applied on formatting settings
                if (colorHelper.isHighContrast) {
                        this.settings.fontColor = colorHelper.getHighContrastColor("foreground", this.settings.fontColor);
                    }
            }
}
```


## `ColorUtils`
 A modul a következő függvényeket biztosítja:

* [hexToRGBString](#hextorgbstring)
* [rotate](#rotate)
* [parseColorString](#parsecolorstring)
* [calculateHighlightColor](#calculatehighlightcolor)
* [createLinearColorScale](#createlinearcolorscale)
* [shadeColor](#shadecolor)
* [rgbBlend](#rgbblend)
* [channelBlend](#channelblend)
* [hexBlend](#hexblend)

### <a name="hextorgbstring"></a>hexToRGBString
Átalakítja a hexadecimális színeket RGB-sztringgé.

```typescript
function hexToRGBString(hex: string, transparency?: number): string
```

#### <a name="example"></a>Példa

```typescript
import  { hexToRGBString } from "powerbi-visuals-utils-colorutils";

hexToRGBString('#112233');

// returns: "rgb(17,34,51)"
```

### <a name="rotate"></a>rotate
Elforgatja az RGB-színeket.

```typescript
function rotate(rgbString: string, rotateFactor: number): string
```

#### <a name="example"></a>Példa

```typescript
import { rotate } from "powerbi-visuals-utils-colorutils";

rotate("#CC0000", 0.25); // returns: #66CC00
```

### <a name="parsecolorstring"></a>parseColorString
Elemzi a színsztringeket az RGB-formátum szerint.

```typescript
function parseColorString(color: string): RgbColor
```

#### <a name="example"></a>Példa

```typescript
import { parseColorString } from "powerbi-visuals-utils-colorutils";

parseColorString('#09f');
// returns: {R: 0, G: 153, B: 255 }

parseColorString('rgba(1, 2, 3, 1.0)');
// returns: {R: 1, G: 2, B: 3, A: 1.0 }
```

### <a name="calculatehighlightcolor"></a>calculateHighlightColor
Kiszámítja a kiemelőszínt az rgbColor-ból, a lumianceThreshold és az eltérés alapján.

```typescript
function calculateHighlightColor(rgbColor: RgbColor, lumianceThreshold: number, delta: number): string
```

#### <a name="example"></a>Példa

```typescript
import { calculateHighlightColor } from "powerbi-visuals-utils-colorutils";

let yellow = "#FFFF00",
    yellowRGB = parseColorString(yellow);

calculateHighlightColor(yellowRGB, 0.8, 0.2);

// returns: '#CCCC00'
```

### <a name="createlinearcolorscale"></a>createLinearColorScale
Visszaad egy lineáris színskálát a megadott számtartományhoz.

```typescript
function createLinearColorScale(domain: number[], range: string[], clamp: boolean): LinearColorScale
```

#### <a name="example"></a>Példa

```typescript
import { createLinearColorScale } from "powerbi-visuals-utils-colorutils";

let scale = ColorUtility.createLinearColorScale(
    [0, 1, 2, 3, 4],
    ["red", "green", "blue", "black", "yellow"],
    true);

scale(1); // returns: green
scale(10); // returns: yellow
```

### <a name="shadecolor"></a>shadeColor
Átalakítja a sztring hexadecimális kifejezését számmá, valamint kiszámítja a százalékértéket és az R, G, B csatornákat.
Alkalmazza a százalékértéket az egyes csatornákra, és visszaadja a hexadecimális értéket kettőskereszttel ellátott sztringként.

```typescript
function shadeColor(color: string, percent: number): string
```

#### <a name="example"></a>Példa

```typescript
import { shadeColor } from "powerbi-visuals-utils-colorutils";

shadeColor('#000000', 0.1); // returns '#1a1a1a'
shadeColor('#FFFFFF', -0.5); // returns '#808080'
shadeColor('#00B8AA', -0.25); // returns '#008a80'
shadeColor('#00B8AA', 0); // returns '#00b8aa'
```

### <a name="rgbblend"></a>rgbBlend
Átlátszatlan színt helyez a háttérszínre. A rendszer figyelmen kívül hagyja az alfa csatornákat.

```typescript
function rgbBlend(foreColor: RgbColor, opacity: number, backColor: RgbColor): RgbColor
```

#### <a name="example"></a>Példa

```typescript
import { rgbBlend} from "powerbi-visuals-utils-colorutils";

rgbBlend({R: 100, G: 100, B: 100}, 0.5, {R: 200, G: 200, B: 200});

// returns: {R: 150, G: 150, B: 150}
```

### <a name="channelblend"></a>channelBlend
Egyetlen csatornát kever két színhez.

```typescript
function channelBlend(foreChannel: number, opacity: number, backChannel: number): number
```

#### <a name="example"></a>Példa

```typescript
import { channelBlend} from "powerbi-visuals-utils-colorutils";

channelBlend(0, 1, 255); // returns: 0
channelBlend(128, 1, 255); // returns: 128
channelBlend(255, 0, 0); // returns: 0
channelBlend(88, 0, 88); // returns: 88
```

### <a name="hexblend"></a>hexBlend
Átlátszatlan színt helyez a háttérszínre.

```typescript
function hexBlend(foreColor: string, opacity: number, backColor: string): string
```

#### <a name="example"></a>Példa

```typescript
import { hexBlend} from "powerbi-visuals-utils-colorutils";

let yellow = "#FFFF00",
    black = "#000000",
    white = "#FFFFFF";

hexBlend(yellow, 0.5, white); // returns: "#FFFF80"
hexBlend(white, 0.5, yellow); // returns: "#FFFF80"

hexBlend(yellow, 0.5, black); // returns: "#808000"
hexBlend(black, 0.5, yellow); // returns: "#808000"
```