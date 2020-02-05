---
title: Interaktivitási eszközök Power BI-vizualizációkhoz
description: Ez a cikk azt ismerteti, hogy hogyan adhatók kijelölések Power BI-vizualizációkhoz interaktivitási eszközök használatával
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: be7a708dfcc6ebc40c62a1a9075e2cbf134363b1
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/04/2020
ms.locfileid: "76818686"
---
# <a name="microsoft-power-bi-visuals-interactivity-utils"></a>Interaktivitási eszközök Microsoft Power BI-vizualizációkhoz

Az InteractivityUtils függvények és osztályok olyan gyűjteménye, amely egyszerűbbé teszi a keresztkijelölés és keresztszűrés megvalósítása az egyéni Power BI-vizualizációkban.

## <a name="installation"></a>Telepítés

> [!NOTE]
> Ha még a powerbi-visuals-tools régi (3.x.x-nél alacsonyabb verziószámú) verzióját használja, telepítse az eszközök új (3.x.x) verzióját.

> [!IMPORTANT]
> Az interaktivitási eszközök új frissítései csak az eszközök legújabb verzióját fogják támogatni. [További tudnivalók a vizualizációk kódjának módosításáról a legújabb eszközökkel való használathoz](migrate-to-new-tools.md)

A csomag telepítéséhez az alábbi parancsot kell futtatni az aktuális egyéni vizualizációt tartalmazó mappában:

```bash
npm install powerbi-visuals-utils-interactivityutils --save
```

A 3.0 és újabb verziókhoz a ```powerbi-models``` telepítése is szükséges a függőségek feloldásához.

```bash
npm install powerbi-models --save
```

Az interaktivitási eszközök használatához importálnia kell a szükséges összetevőket a vizualizáció forráskódjában.

```typescript
import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";
```

### <a name="including-css-artifacts-to-the-custom-visual"></a>CSS-összetevők belefoglalása az egyéni vizualizációba

Ahhoz, hogy a csomagot egyéni vizualizációkkal használhassa, importálnia kell az alábbi CSS-fájlt a `your.less` fájlba:

`node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css`

Ennek eredménye a következő fájlstruktúra lesz:

```less
@import (less) "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css";
```

> [!NOTE]
> A .css-fájlt azért kell .less-fájlként importálnia, mert a Power BI vizualizációs eszközök becsomagolják a külső CSS-szabályokat.

## <a name="usage"></a>Használat

### <a name="define-interface-for-data-points"></a>Adatinterfész adatpontokhoz

Az adatpontok általában kijelöléseket és értékeket tartalmaznak. Az interfész a `SelectableDataPoint` interfész kiterjesztése. A `SelectableDataPoint` már tartalmaz tulajdonságokat:

```typescript
  /** Flag for identifying that data point was selected */
  selected: boolean;
  /** Identity for identifying the selectable data point for selection purposes */
  identity: powerbi.extensibility.ISelectionId;
  /**
   * A specific identity for when data points exist at a finer granularity than
   * selection is performed.  For example, if your data points should select based
   * only on series even if they exist as category/series intersections.
   */
  specificIdentity?: powerbi.extensibility.ISelectionId;
```

Az interaktivitási eszközök használatának első lépése az interaktivitási eszközök egy példányának létrehozása, és az objektum mentése a vizualizáció tulajdonságaként

```typescript
export class Visual implements IVisual {
  // ...
  private interactivity: interactivityBaseService.IInteractivityService<VisualDataPoint>;
  // ...
  constructor(options: VisualConstructorOptions) {
      // ...
      this.interactivity = interactivitySelectionService.createInteractivitySelectionService(this.host);
      // ...
  }
}
```

```typescript
import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";

export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
    value: powerbi.PrimitiveValue;
}
```

A következő lépés az alap viselkedési osztály kiterjesztése:

> [!NOTE]
> A BaseBehavior az [interaktivitási eszközök 5.6.x verziójában](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0) lett bevezetve. Ha régebbi verziót használ, a viselkedési osztályt az alábbi példából hozhatja létre (a `BaseBehavior` osztály ugyanaz):

Definiáljon interfészt a viselkedési osztály beállításaihoz:

```typescript
import { SelectableDataPoint } from "./interactivitySelectionService";

import {
    IBehaviorOptions,
    BaseDataPoint
} from "./interactivityBaseService";

export interface BaseBehaviorOptions<SelectableDataPointType extends BaseDataPoint> extends IBehaviorOptions<SelectableDataPointType> {
    /** D3 selection object of main elements on the chart */
    elementsSelection: Selection<any, SelectableDataPoint, any, any>;
    /** D3 selection object of some element on backgroup to hadle click of reset selection */
    clearCatcherSelection: d3.Selection<any, any, any, any>;
}
```

Definiálja a `visual behavior` viselkedését. A `click` és `contextmenu` egéreseményeket az osztály kezeli.
Az adatelemeken végzett kattintás esetén a vizualizáció a kijelöléskezelőt hívja meg az adatpontok kijelöléséhez. ha a felhasználó a vizualizáció háttérelemére kattint, az meghívja a Kijelölés törlése kezelőt. Az osztály ezt kezelő metódusai: `bindClick`, `bindClearCatcher`, `bindContextMenu`.

```typescript
export class Behavior<SelectableDataPointType extends BaseDataPoint> implements IInteractiveBehavior {
    /** D3 selection object of main elements on the chart */
    protected options: BaseBehaviorOptions<SelectableDataPointType>;
    protected selectionHandler: ISelectionHandler;

    protected bindClick() {
      // ...
    }

    protected bindClearCatcher() {
      // ...
    }

    protected bindContextMenu() {
      // ...
    }

    public bindEvents(
        options: BaseBehaviorOptions<SelectableDataPointType>,
        selectionHandler: ISelectionHandler): void {
      // ...
    }

    public renderSelection(hasSelection: boolean): void {
      // ...
    }
}
```

A `BaseBehavior` osztályt ki is terjesztheti:

```typescript
import powerbi from "powerbi-visuals-api";
import { interactivitySelectionService, baseBehavior } from "powerbi-visuals-utils-interactivityutils";

export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
    value: powerbi.PrimitiveValue;
}

export class Behavior extends baseBehavior.BaseBehavior<VisualDataPoint> {
  // ...
}
```

Az elemeken végzett kattintások kezelésére a D3 kijelölési objektum `on` metódusát hívja meg (az elementsSelection és a clearCatcherSelection esetében is):

```typescript
protected bindClick() {
  const {
      elementsSelection
  } = this.options;

  elementsSelection.on("click", (datum) => {
      const mouseEvent: MouseEvent = getEvent() as MouseEvent || window.event as MouseEvent;
      mouseEvent && this.selectionHandler.handleSelection(
          datum,
          mouseEvent.ctrlKey);
  });
}
```

Adjon hozzá hasonló kezelőt a `contextmenu` eseményhez is a kijelöléskezelő `showContextMenu` metódusának meghívására:

```typescript
protected bindContextMenu() {
    const {
        elementsSelection
    } = this.options;

    elementsSelection.on("contextmenu", (datum) => {
        const event: MouseEvent = (getEvent() as MouseEvent) || window.event as MouseEvent;
        if (event) {
            this.selectionHandler.handleContextMenu(
                datum,
                {
                    x: event.clientX,
                    y: event.clientY
                });
            event.preventDefault();
        }
    });
}
```

Az interaktivitási eszközök `bindEvents` metódusok hívásával rendelik kezelőkhöz a függvényeket. Szúrja be a `bindClick`, a `bindClearCatcher` és a `bindContextMenu` hívását a `bindEvents` metódusba:

```typescript
  public bindEvents(
      options: BaseBehaviorOptions<SelectableDataPointType>,
      selectionHandler: ISelectionHandler): void {

      this.options = options;
      this.selectionHandler = selectionHandler;

      this.bindClick();
      this.bindClearCatcher();
      this.bindContextMenu();
  }
```

A vizualizáció diagramelemei állapotának frissítését a `renderSelection` metódus végzi.

Példa a `renderSelection` metódus implementálására:

```typescript
public renderSelection(hasSelection: boolean): void {
    this.options.elementsSelection.style("opacity", (category: any) => {
        if (category.selected) {
            return 0.5;
        } else {
            return 1;
        }
    });
}
```

Az utolsó lépés a `visual behavior` egy példányának létrehozása és az interaktivitási eszközök `bind` metódusának meghívása:

```typescript
this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
    behavior: this.behavior,
    dataPoints: this.categories,
    clearCatcherSelection: select(this.target),
    elementsSelection: selectionMerge
});
```

* `selectionMerge` egy D3 kijelölési objektum, amely a vizualizáció kijelölhető elemeinek felel meg.

* `select(this.target)` egy D3 kijelölési objektum, amely a vizualizáció fő DOM-elemeinek felel meg.

* `this.categories` elemekkel rendelkező adatpontoknak felel meg, ahol az interfész `VisualDataPoint` (vagy `categories: VisualDataPoint[];`)

* `this.behavior` a `visual behavior` új példánya

  ez a vizualizáció konstruktorában lett létrehozva:

  ```typescript
  export class Visual implements IVisual {
    // ...
    constructor(options: VisualConstructorOptions) {
        // ...
        this.behavior = new Behavior();
    }
    // ...
  }
  ```

A vizualizáció így már készen áll a kijelölések kezelésére.

## <a name="next-steps"></a>Következő lépések

* [Tudnivalók a kijelölések kezeléséről könyvjelzőváltáskor](bookmarks-support.md#visuals-with-selection)

* [Tudnivalók a vizualizációk adatpontjaihoz adható helyi menüről](context-menu.md)

* [Tudnivalók kijelölések Power BI-vizualizációkhoz adásáról a kijelöléskezelő használatával](selection-api.md)
