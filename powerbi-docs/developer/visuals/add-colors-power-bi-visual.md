---
title: Színek hozzáadása a Power BI-vizualizációkhoz
description: Ez a cikk az ismerteti, hogy miként adhat színeket Power BI-vizualizációihoz, illetve hogy miként kezelhetők a színes vizualizációk adatpontjai.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/27/2020
ms.openlocfilehash: 3f3574545d82ac11c762b7011afdc49cbe855224
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83141145"
---
# <a name="add-colors-to-your-power-bi-visuals"></a>Színek hozzáadása a Power BI-vizualizációkhoz

Ez a cikk az ismerteti, hogy miként adhat színeket vizualizációihoz, illetve hogy miként kezelhetők a színes vizualizációk adatpontjai.

A szín az `IVisualHost` egyik szolgáltatása.
A cikkben található példakód módosítja a [SampleBarChart vizualizációt](https://github.com/microsoft/PowerBI-visuals-sampleBarChart).
A forráskódért tekintse meg a következőt: [barChart.ts](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts).

A vizualizációk létrehozásának első lépéseit a következő cikkben tekintheti meg: [Power BI-vizualizáció fejlesztése](custom-visual-develop-tutorial.md).

## <a name="add-color-to-data-points"></a>Szín hozzáadása az adatpontokhoz

Minden egyes adatpontot más szín jelöl.
Adja hozzá a színt a `BarChartDataPoint` felülethez a következő példát követve:

```typescript
/**
 * Interface for BarChart data points.
 *
 * @interface
 * @property {number} value    - Data value for point.
 * @property {string} category - Corresponding category of data value.
 * @property {string} color    - Color corresponding to data point.
 */
interface BarChartDataPoint {
    value: number;
    category: string;
    color: string;
};
```

## <a name="use-the-color-palette-service"></a>A színpaletta szolgáltatás használata

A `colorPalette` szolgáltatással kezelhetők a vizualizációban használt színek.
A szolgáltatás egy példánya a következő helyen érhető el: `IVisualHost`.

A `update` metódusban határozhatja meg.

```typescript
constructor(options: VisualConstructorOptions) {
        this.host = options.host; // host: IVisualHost
        ...
    }

public update(options: VisualUpdateOptions) {

    let colorPalette: IColorPalette = host.colorPalette;
    ...
}
```

## <a name="assigning-color-to-data-points"></a>Szín hozzárendelése az adatpontokhoz

Ezután határozza meg a következőt: `dataPoints`.
Ebben a példában minden `dataPoints` rendelkezik egy értékkel, egy kategóriával és egy színnel.
Emellett minden `dataPoints` tartalmazhat egyéb tulajdonságokat is.

A `SampleBarChart` `visualTransform` metódusa magában foglalja a `dataPoints` számítást.
Ez a metódus a Sávdiagram nézetmodell részét képezi.
Mivel a metódus a `dataPoints` iterálását a `visualTransform` helyen végzi, ez ideális a színek hozzárendeléséhez, ahogy az a következő kódban is szerepel:

```typescript

public update(options: VisualUpdateOptions) {
    ....
    let viewModel: BarChartViewModel = visualTransform(options, this.host);
    ....
}

function visualTransform(options: VisualUpdateOptions, host: IVisualHost): BarChartViewModel {
    let colorPalette: IColorPalette = host.colorPalette; // host: IVisualHost
    for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
        barChartDataPoints.push({
            category: category.values[i],
            value: dataValue.values[i],
            color: colorPalette.getColor(category.values[i]).value,
        });
    }
}
```

Ezután alkalmazza a `dataPoints` adatait a `barSelection` [d3](https://d3js.org/)-kiválasztáson a `update` metódusban:

```typescript
// This code is actual for d3 v5
// in d3 v5 for this case we should use merge() after enter() and apply changes on barSelectionMerged
this.barSelection = this.barContainer
    .selectAll('.bar')
    .data(this.barDataPoints);

const barSelectionMerged = this.barSelection
    .enter()
    .append('rect')
    .merge(<any>this.barSelection);

barSelectionMerged.classed('bar', true);

barSelectionMerged
.attr("width", xScale.bandwidth())
.attr("height", d => height - yScale(<number>d.value))
.attr("y", d => yScale(<number>d.value))
.attr("x", d => xScale(d.category))
.style("fill", (dataPoint: BarChartDataPoint) => dataPoint.color)
.style("stroke", (dataPoint: BarChartDataPoint) => dataPoint.strokeColor)
.style("stroke-width", (dataPoint: BarChartDataPoint) => `${dataPoint.strokeWidth}px`);

this.barSelection
    .exit()
    .remove();
```

## <a name="next-steps"></a>Következő lépések

A Power-BI vizualizációkkal kapcsolatos további információért tekintse meg a [Power BI-vizualizációk képességei és tulajdonságai](capabilities.md) című részt.

A Power BI-vizualizációk fejlesztésével kapcsolatos további információért tekintse meg a [Power BI-vizualizációk hibakeresése](visuals-how-to-debug.md) és a [Power BI-vizualizációk hibaelhárítása](power-bi-custom-visuals-troubleshoot.md) című részt.
