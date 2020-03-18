---
title: Kiemelés
description: Adatpont-kijelölések kiemelése Power BI-vizualizációkban
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 10/31/2019
ms.openlocfilehash: d406396db64b52326bbd8ea2aa485cd3d7451294
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380036"
---
# <a name="highlight-data-points-in-power-bi-visuals"></a>Adatpontok kiemelése Power BI-vizualizációkban

Egy elem kijelölésekor a `dataView` objektum `values` tömbje alapértelmezés szerint csak a kijelölt értékekre lesz szűrve. Emiatt az oldal többi vizualizációja csak a kijelölt adatokat jeleníti meg.

![highlight `dataview` default behavior](media/highlight/highlight-dataview.png)

Ha `capabilities.json` fájl `supportsHighlight` tulajdonságát `true` értékre állítja, a teljes szűretlen `values` tömböt kapja eredményül egy `highlights` tömbbel együtt. A `highlights` tömb az értékek tömbjével megegyező hosszúságú lesz, a nem kijelölt értékek pedig `null` lesznek beállítva. A tulajdonság engedélyezésével a vizualizáció felelősségévé válik a megfelelő adatok kiemelése – `values` a tömb `highlights` a tömbbel való összehasonlításával.

![A `dataview` támogatja a kiemelést](media/highlight/highlight-dataview-supports.png)

A példában megfigyelheti, hogy 1 sáv ki van jelölve. Ez az egyetlen érték a kiemelt tömbben. Emellett fontos megjegyezni, hogy több kijelölés, valamint részleges kiemelés is szerepelhet. A kiemelt értékek az adatnézetben jelennek meg.

> [!NOTE]
> A táblázatos adatnézet leképezése nem támogatja a kiemelés funkciót.

## <a name="highlight-data-points-with-categorical-data-view-mapping"></a>Az adatpontok kiemelése kategorikus adatnézet-leképezéssel

A kategorikus adatnézet-leképezést tartalmazó vizualizációk `capabilities.json` fájljában szerepel a `"supportsHighlight": true` paraméter. Például:

```json
{
    "dataRoles": [
        {
            "displayName": "Category",
            "name": "category",
            "kind": "Grouping"
        },
        {
            "displayName": "Value",
            "name": "value",
            "kind": "Measure"
        }
    ],
    "dataViewMappings": [
        {
            "categorical": {
                "categories": {
                    "for": {
                        "in": "category"
                    }
                },
                "values": {
                    "for": {
                        "in": "value"
                    }
                }
            }
        }
    ],
    "supportsHighlight": true
}
```

A felesleges kód eltávolítását követően az alapértelmezett vizualizációs forráskód a következőképpen fog kinézni:

```typescript
"use strict";

// ... default imports list

import DataViewCategorical = powerbi.DataViewCategorical;
import DataViewCategoryColumn = powerbi.DataViewCategoryColumn;
import PrimitiveValue = powerbi.PrimitiveValue;
import DataViewValueColumn = powerbi.DataViewValueColumn;

import { VisualSettings } from "./settings";

export class Visual implements IVisual {
    private target: HTMLElement;
    private settings: VisualSettings;

    constructor(options: VisualConstructorOptions) {
        console.log('Visual constructor', options);
        this.target = options.element;
        this.host = options.host;

    }

    public update(options: VisualUpdateOptions) {
        this.settings = Visual.parseSettings(options && options.dataViews && options.dataViews[0]);
        console.log('Visual update', options);

    }

    private static parseSettings(dataView: DataView): VisualSettings {
        return <VisualSettings>VisualSettings.parse(dataView);
    }

    /**
     * This function gets called for each of the objects defined in the capabilities files and allows you to select which of the
     * objects and properties you want to expose to the users in the property pane.
     *
     */
    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstance[] | VisualObjectInstanceEnumerationObject {
        return VisualSettings.enumerateObjectInstances(this.settings || VisualSettings.getDefault(), options);
    }
}
```

A Power BI-ból származó adatok feldolgozásához szükséges interfészek importálása:

```typescript
import DataViewCategorical = powerbi.DataViewCategorical;
import DataViewCategoryColumn = powerbi.DataViewCategoryColumn;
import PrimitiveValue = powerbi.PrimitiveValue;
import DataViewValueColumn = powerbi.DataViewValueColumn;
```

A gyökérszintű `div` elem létrehozása a kategóriaértékekhez:

```typescript
export class Visual implements IVisual {
    private target: HTMLElement;
    private settings: VisualSettings;

    private div: HTMLDivElement; // new property

    constructor(options: VisualConstructorOptions) {
        console.log('Visual constructor', options);
        this.target = options.element;
        this.host = options.host;

        // create div element
        this.div = document.createElement("div");
        this.div.classList.add("vertical");
        this.target.appendChild(this.div);

    }
    // ...
}
```

A div elemek tartalmának törlése az új adatok renderelése előtt:

```typescript
// ...
public update(options: VisualUpdateOptions) {
    this.settings = Visual.parseSettings(options && options.dataViews && options.dataViews[0]);
    console.log('Visual update', options);

    while (this.div.firstChild) {
        this.div.removeChild(this.div.firstChild);
    }
    // ...
}
```

A kategóriák és a mértékértékek beolvasása a `dataView` objektumból:

```typescript
public update(options: VisualUpdateOptions) {
    this.settings = Visual.parseSettings(options && options.dataViews && options.dataViews[0]);
    console.log('Visual update', options);

    while (this.div.firstChild) {
        this.div.removeChild(this.div.firstChild);
    }

    const dataView: DataView = options.dataViews[0];
    const categoricalDataView: DataViewCategorical = dataView.categorical;
    const categories: DataViewCategoryColumn = categoricalDataView.categories[0];
    const categoryValues = categories.values;

    const measures: DataViewValueColumn = categoricalDataView.values[0];
    const measureValues = measures.values;
    const measureHighlights = measures.highlights;
    // ...
}
```

Ahol a `categoryValues` egy kategóriaértékekből álló tömb, a `measureValues` egy mértékekből álló tömb, és a `measureHighlights` tartalmazza az értékek kiemelt részeit.

> [!NOTE]
> A `measureHighlights` tulajdonságnak lehet kevesebb értéke, mint a `categoryValues` tulajdonságnak.
> Ez azt jelenti, hogy az értékeknek egy része lett kijelölve.

A `categoryValues` tömb enumerálása és a megfelelő értékek és kiemelések beolvasása:

```typescript
// ...
const measureHighlights = measures.highlights;

categoryValues.forEach((category: PrimitiveValue, index: number) => {
    const measureValue = measureValues[index];
    const measureHighlight = measureHighlights && measureHighlights[index] ? measureHighlights[index] : null;
    console.log(category, measureValue, measureHighlight);

});
```

A `div` és `p` elemek létrehozása a vizuális DOM adatnézet-értékeinek megjelenítéséhez és vizualizációjához:

```typescript
categoryValues.forEach((category: PrimitiveValue, index: number) => {
    const measureValue = measureValues[index];
    const measureHighlight = measureHighlights && measureHighlights[index] ? measureHighlights[index] : null;
    console.log(category, measureValue, measureHighlight);

    // div element. it contains elements to display values and visualize value as progress bar
    let div = document.createElement("div");
    div.classList.add("horizontal");
    this.div.appendChild(div);

    // div element to vizualize value of measure
    let barValue = document.createElement("div");
    barValue.style.width = +measureValue * 10 + "px";
    barValue.style.display = "flex";
    barValue.classList.add("value");

    // element to display category value
    let bp = document.createElement("p");
    bp.innerText = category.toString();

    // div element to vizualize highlight of measure
    let barHighlight = document.createElement("div");
    barHighlight.classList.add("highlight")
    barHighlight.style.backgroundColor = "blue";
    barHighlight.style.width = +measureHighlight * 10 + "px";

    // element to display highlighted value of measure
    let p = document.createElement("p");
    p.innerText = `${measureHighlight}/${measureValue}`;
    barHighlight.appendChild(bp);

    div.appendChild(barValue);

    barValue.appendChild(barHighlight);
    div.appendChild(p);
});
```

A szükséges stílusok alkalmazása az elemekre a `flex box` használatához, és a div elemek színeinek meghatározása:

```css
div.vertical {
    display: flex;
    flex-direction: column;
}

div.horizontal {
    display: flex;
    flex-direction: row;
}

div.highlight {
    background-color: blue
}

div.value {
    background-color: red;
    display: flex;
}
```

Az eredményben elvileg a vizualizáció következő nézetének kell szerepelnie.

![A kategorikus adatnézet-leképezést és kiemelést tartalmazó vizualizációk](media/highlight/dev-categorical-visual-highlight-demo.gif)

## <a name="highlight-data-points-with-matrix-data-view-mapping"></a>Az adatpontok kiemelése mátrix adatnézet-leképezéssel

A mátrix adatnézet-leképezést tartalmazó vizualizációk `capabilities.json` fájljában szerepel a `"supportsHighlight": true` paraméter. Például:

```json
{
    "dataRoles": [
        {
            "displayName": "Columns",
            "name": "columns",
            "kind": "Grouping"
        },
        {
            "displayName": "Rows",
            "name": "rows",
            "kind": "Grouping"
        },
        {
            "displayName": "Value",
            "name": "value",
            "kind": "Measure"
        }
    ],
    "dataViewMappings": [
        {
            "matrix": {
                "columns": {
                    "for": {
                        "in": "columns"
                    }
                },
                "rows": {
                    "for": {
                        "in": "rows"
                    }
                },
                "values": {
                    "for": {
                        "in": "value"
                    }
                }
            }
        }
    ],
    "supportsHighlight": true
}
```

A mátrix adatnézet-leképezés hierarchiájának létrehozására szolgáló mintaadatok:

|   1\. sor   |   2\. sor   |   3\. sor   |   1\. oszlop   |   2\. oszlop   |   3\. oszlop   |   Értékek   |
|-----|-----|------|-------|-------|-------|-------|
|   R1   |   R11   |   R111   |   C1   |   C11   |   C111   |   1   |
|   R1   |   R11   |   R112   |   C1   |   C11   |   C112   |   2   |
|   R1   |   R11   |   R113   |   C1   |   C11   |   C113   |   3   |
|   R1   |   R12   |   R121   |   C1   |   C12   |   C121   |   4   |
|   R1   |   R12   |   R122   |   C1   |   C12   |   C122   |   5   |
|   R1   |   R12   |   R123   |   C1   |   C12   |   C123   |   6   |
|   R1   |   R13   |   R131   |   C1   |   C13   |   C131   |   7   |
|   R1   |   R13   |   R132   |   C1   |   C13   |   C132   |   8   |
|   R1   |   R13   |   R133   |   C1   |   C13   |   C133   |   9   |
|   R2   |   R21   |   R211   |   C2   |   C21   |   C211   |   10   |
|   R2   |   R21   |   R212   |   C2   |   C21   |   C212   |   11   |
|   R2   |   R21   |   R213   |   C2   |   C21   |   C213   |   12   |
|   R2   |   R22   |   R221   |   C2   |   C22   |   C221   |   13   |
|   R2   |   R22   |   R222   |   C2   |   C22   |   C222   |   14   |
|   R2   |   R22   |   R223   |   C2   |   C22   |   C223   |   16   |
|   R2   |   R23   |   R231   |   C2   |   C23   |   C231   |   17   |
|   R2   |   R23   |   R232   |   C2   |   C23   |   C232   |   18   |
|   R2   |   R23   |   R233   |   C2   |   C23   |   C233   |   19   |

Hozza létre az alapértelmezett vizualizációs projektet, és alkalmazza a `capabilities.json` mintáját.

A felesleges kód eltávolítását követően az alapértelmezett vizualizációs forráskód a következő lesz:

```typescript
"use strict";

// ... default imports

import { VisualSettings } from "./settings";

export class Visual implements IVisual {
    private target: HTMLElement;
    private settings: VisualSettings;


    constructor(options: VisualConstructorOptions) {
        console.log('Visual constructor', options);
        this.target = options.element;
        this.host = options.host;
    }

    public update(options: VisualUpdateOptions) {
        this.settings = Visual.parseSettings(options && options.dataViews && options.dataViews[0]);
        console.log('Visual update', options);

    }

    private static parseSettings(dataView: DataView): VisualSettings {
        return <VisualSettings>VisualSettings.parse(dataView);
    }

    /**
     * This function gets called for each of the objects defined in the capabilities files and allows you to select which of the
     * objects and properties you want to expose to the users in the property pane.
     *
     */
    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstance[] | VisualObjectInstanceEnumerationObject {
        return VisualSettings.enumerateObjectInstances(this.settings || VisualSettings.getDefault(), options);
    }
}
```

A Power BI-ból származó adatok feldolgozásához szükséges interfészek importálása:

```typescript
import DataViewMatrix = powerbi.DataViewMatrix;
import DataViewMatrixNode = powerbi.DataViewMatrixNode;
import DataViewHierarchyLevel = powerbi.DataViewHierarchyLevel;
```

Hozzon létre két `div` elemet a vizualizáció elrendezéséhez:

```typescript
constructor(options: VisualConstructorOptions) {
    // ...
    this.rowsDiv = document.createElement("div");
    this.target.appendChild(this.rowsDiv);

    this.colsDiv = document.createElement("div");
    this.target.appendChild(this.colsDiv);
    this.target.style.overflowY = "auto";
}
```

Ellenőrizze az `update` metódusban szereplő adatokat annak ellenőrzésére, hogy a vizualizáció kap-e adatokat:

```typescript
public update(options: VisualUpdateOptions) {
    this.settings = Visual.parseSettings(options && options.dataViews && options.dataViews[0]);
    console.log('Visual update', options);

    const dataView: DataView = options.dataViews[0];
    const matrixDataView: DataViewMatrix = dataView.matrix;

    if (!matrixDataView ||
        !matrixDataView.columns ||
        !matrixDataView.rows ) {
        return
    }
    // ...
}
```

A `div` elemek tartalmának törlése az új adatok renderelése előtt:

```typescript
public update(options: VisualUpdateOptions) {
    // ...

    // remove old elements
    // to better performance use D3js pattern:
    // https://d3js.org/#enter-exit
    while (this.rowsDiv.firstChild) {
        this.rowsDiv.removeChild(this.rowsDiv.firstChild);
    }
    const prow = document.createElement("p");
    prow.innerText = "Rows";
    this.rowsDiv.appendChild(prow);

    while (this.colsDiv.firstChild) {
        this.colsDiv.removeChild(this.colsDiv.firstChild);
    }
    const pcol = document.createElement("p");
    pcol.innerText = "Columns";
    this.colsDiv.appendChild(pcol);
    // ...
}
```

A `treeWalker` függvény létrehozása a mátrix adatstruktúrájának bejárásához:

```typescript
public update(options: VisualUpdateOptions) {
    // ...
    const treeWalker = (matrixNode: DataViewMatrixNode, index: number, levels: DataViewHierarchyLevel[], div: HTMLDivElement)  => {

    }
    // ...
}
```

Ahol a `matrixNode` az aktuális csomópont, a `levels` tartalmazza ezen hierarchiaszint metaadatoszlopait, és a `div` a gyermek HTML-elemek szülőeleme.

A `treeWalker` rekurzív függvény; létre kell hozni a `div` elem és a `p` elemet a fejlécként használt szöveghez, és a függvényt kell meghívni a csomópont gyermekelemeire:

```typescript
public update(options: VisualUpdateOptions) {
    // ...
    const treeWalker = (matrixNode: DataViewMatrixNode, index: number, levels: DataViewHierarchyLevel[], div: HTMLDivElement)  => {
        // ...

        if (matrixNode.children) {
            const childDiv = document.createElement("div");
            childDiv.classList.add("vertical");
            div.appendChild(childDiv);

            const p = document.createElement("p");
            const level = levels[matrixNode.level]; // get current level column metadata from current node
            p.innerText = level.sources[level.sources.length - 1].displayName; // get column name from metadata

            childDiv.appendChild(p); // add paragraph element to div element
            matrixNode.children.forEach((node, index) => treeWalker(node, levels, childDiv, ++levelIndex));
        }
    }
    // ...
}
```

A függvény meghívása a mátrix adatnézet-struktúra oszlopának és sorának gyökérelemére:

```typescript
public update(options: VisualUpdateOptions) {
    // ...
    const treeWalker = (matrixNode: DataViewMatrixNode, index: number, levels: DataViewHierarchyLevel[], div: HTMLDivElement)  => {
        // ...
    }
    // ...
    // remove old elements
    // ...

    // ...
    const rowRoot: DataViewMatrixNode = matrixDataView.rows.root;
    rowRoot.children.forEach((node) => treeWalker(node, matrixDataView.rows.levels, this.rowsDiv));

    const colRoot = matrixDataView.columns.root;
    colRoot.children.forEach((node) => treeWalker(node, matrixDataView.columns.levels, this.colsDiv));
}
```

A selectionID (kijelölésazonosító) generálása a csomópontokhoz, és gombok létrehozása a csomópontok megjelenítéséhez:

```typescript
public update(options: VisualUpdateOptions) {
    // ...
    const treeWalker = (matrixNode: DataViewMatrixNode, index: number, levels: DataViewHierarchyLevel[], div: HTMLDivElement)  => {
        const selectionID: ISelectionID = this.host.createSelectionIdBuilder()
            .withMatrixNode(matrixNode, levels)
            .createSelectionId();

        let nodeBlock = document.createElement("button");
        nodeBlock.innerText = matrixNode.value.toString();

        nodeBlock.addEventListener("click", (event) => {
            // call select method in the selection manager
            this.selectionManager.select(selectionID);
        });

        nodeBlock.addEventListener("contextmenu", (event) => {
            // call showContextMenu method to display context menu on the visual
            this.selectionManager.showContextMenu(selectionID, {
                x: event.clientX,
                y: event.clientY
            });
            event.preventDefault();
        });
        // ...
    }
    // ...
}
```

A kiemelés használatának fő lépése az értékek kiegészítő tömbjének feldolgozása.

A végcsomópont objektumát megvizsgálva látható, hogy az értékek tömbjének két tulajdonsága van – value (érték) és highlight (kiemelés):

```javascript
JSON.stringify(options.dataViews[0].matrix.rows.root.children[0].children[0].children[0], null, " ");
```

```json
{
 "level": 2,
 "levelValues": [
  {
   "value": "R233",
   "levelSourceIndex": 0
  }
 ],
 "value": "R233",
 "identity": {
  "identityIndex": 2
 },
 "values": {
  "0": {
   "value": null,
   "highlight": null
  },
  "1": {
   "value": 19,
   "highlight": 19
  }
 }
}
```

Ahol a `value` (érték) tulajdonság jelöli a csomópont értékét egy másik vizualizációból való kijelölés alkalmazása nélkül, és a highlight (kiemelés) tulajdonság azt jelzi, hogy az adatok melyik része lett kijelölve.

> [!NOTE]
> A `highlight` (kiemelés) tulajdonságnak lehet kevesebb értéke, mint a `value` (érték) tulajdonságnak.
> Ez azt jelenti, hogy az értékeknek egy része lett kijelölve.

A csomópont `values` (értékek) tömbjének – ha meg van jelenítve – feldolgozására szolgáló kód beszúrása:

```typescript
public update(options: VisualUpdateOptions) {
    // ...
    const treeWalker = (matrixNode: DataViewMatrixNode, index: number, levels: DataViewHierarchyLevel[], div: HTMLDivElement)  => {
        // ...

        if (matrixNode.values) {
            const sumOfValues = Object.keys(matrixNode.values) // get key property of object (value are 0 to N)
                .map(key => +matrixNode.values[key].value) // convert key property to number
                .reduce((prev, curr) => prev + curr) // sum of values

            let sumOfHighlights = sumOfValues;
            sumOfHighlights = Object.keys(matrixNode.values) // get key property of object (value are 0 to N)
                .map(key => matrixNode.values[key].highlight ? +matrixNode.values[key].highlight : null ) // convert key property to number if it exists
                .reduce((prev, curr) => curr ? prev + curr : null) // convert key property to number

            // create div container for value and highlighted value
            const vals = document.createElement("div");
            vals.classList.add("vertical")
            vals.classList.replace("vertical", "horizontal");
            // create paragraph element for label
            const highlighted = document.createElement("p");
            // Display complete value and highlighted value
            highlighted.innerText = `${sumOfHighlights}/${sumOfValues}`;

            // create div container for value
            const valueDiv = document.createElement("div");
            valueDiv.style.width = sumOfValues * 10 + "px";
            valueDiv.classList.add("value");

            // create div container for highlighted values
            const highlightsDiv = document.createElement("div");
            highlightsDiv.style.width = sumOfHighlights * 10 + "px";
            highlightsDiv.classList.add("highlight");
            valueDiv.appendChild(highlightsDiv);

            // append button and paragraph to div containers to parent div
            vals.appendChild(nodeBlock);
            vals.appendChild(valueDiv);
            vals.appendChild(highlighted);
            div.appendChild(vals);
        } else {
            div.appendChild(nodeBlock);
        }

        if (matrixNode.children) {
            // ...
        }
    }
    // ...
}
```

A visszaadott eredmény a vizualizáció, gombokkal és a `highlighted value/default value` (kiemelt érték/alapértelmezett érték) értékekkel

![Vizualizáció mátrix adatnézet-leképezéssel és kiemeléssel](media/highlight/dev-matrix-visual-highlight-demo.gif)

## <a name="next-steps"></a>Következő lépések

* [További információ a mátrix adatnézet-leképezésről](dataview-mappings.md#matrix-data-mapping)

* [További információ a vizualizáció képességeiről](capabilities.md)
