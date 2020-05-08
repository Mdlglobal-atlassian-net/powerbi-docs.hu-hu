---
title: Interaktivitási eszközök Power BI-vizualizációkhoz
description: Ez a cikk azt ismerteti, hogy hogyan adhatók kijelölések Power BI-vizualizációkhoz interaktivitási eszközök használatával
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 02/24/2020
ms.openlocfilehash: f4d47347c98d19afdfbf07615842bfb4649dc1b9
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "79379260"
---
# <a name="power-bi-visuals-interactivity-utils"></a>Interaktivitási eszközök Power BI-vizualizációkhoz

Az interaktivitási eszközök (`InteractivityUtils`) olyan függvények és osztályok készlete, amelyek egyszerűbbé teszik a keresztkijelölés és keresztszűrés megvalósítását.

> [!NOTE]
> Az interaktivitási eszközök új frissítései csak az eszközök legújabb verzióját támogatják (3.x.x és újabb).

## <a name="installation"></a>Telepítés

1. A csomag telepítéséhez futtassa az alábbi parancsot az aktuális Power BI vizualizációs projektet tartalmazó könyvtárban.

    ```bash
    npm install powerbi-visuals-utils-interactivityutils --save
    ```

2. Ha az eszköz 3.0-s vagy újabb verzióját használja, telepítse a következőt a függőségek feloldásához: `powerbi-models`.

    ```bash
    npm install powerbi-models --save
    ```

3. Az interaktivitási eszközök használatához importálja a szükséges összetevőt a Power BI-vizualizáció forráskódjába.

    ```typescript
    import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";
    ```

### <a name="including-the-css-files"></a>A CSS-fájlok belefoglalása

Ha a csomagot a Power BI-vizualizációval kívánja használni, importálja a CSS-fájlt a `.less` fájlba.

`node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css`

A CSS-fájlt `.less` fájlként kell importálni, mivel a Power BI-vizualizációk eszköz burkolja a külső CSS-szabályokat.

```less
@import (less) "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css";
```

## <a name="selectabledatapoint-properties"></a>SelectableDataPoint tulajdonságok

Az adatpontok általában kijelöléseket és értékeket tartalmaznak. Az interfész a `SelectableDataPoint` interfészt terjeszti ki.

A `SelectableDataPoint` már tartalmazza az alább ismertetett tulajdonságokat.

```typescript
  /** Flag for identifying that a data point was selected */
  selected: boolean;

  /** Identity for identifying the selectable data point for selection purposes */
  identity: powerbi.extensibility.ISelectionId;

  /*
   * A specific identity for when data points exist at a finer granularity than
   * selection is performed.  For example, if your data points select based
   * only on series, even if they exist as category/series intersections.
   */

  specificIdentity?: powerbi.extensibility.ISelectionId;
```

## <a name="defining-an-interface-for-data-points"></a>Interfész meghatározása az adatpontok számára

1. Hozzon létre egy példányt az interaktivitási eszközökből, és mentse az objektumot a vizualizáció tulajdonságaként

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

2. Terjessze ki az alapszintű viselkedésosztályt.

    > [!NOTE]
    > A `BaseBehavior` az [interaktivitási eszközök 5.6.x verziójában](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0) jelent meg. Ha régebbi verziót használ, hozzon létre egy viselkedésosztályt az alábbi minta segítségével.

3. Adja meg az interfészt a viselkedésosztály beállításai számára.

    ```typescript
    import { SelectableDataPoint } from "./interactivitySelectionService";

    import {
        IBehaviorOptions,
        BaseDataPoint
    } from "./interactivityBaseService";

    export interface BaseBehaviorOptions<SelectableDataPointType extends BaseDataPoint> extends IBehaviorOptions<SelectableDataPointType> {

    /** d3 selection object of the main elements on the chart */
    elementsSelection: Selection<any, SelectableDataPoint, any, any>;

    /** d3 selection object of some elements on backgroup, to hadle click of reset selection */
    clearCatcherSelection: d3.Selection<any, any, any, any>;
    }
    ```

4. Definiálja a `visual behavior` viselkedését. Vagy terjessze ki a `BaseBehavior` osztályt.

    **Osztály megadása a `visual behavior`** számára

    Az osztály felel a `click` `contextmenu` egéresemények kezeléséért.

    Amikor a felhasználó rákattint az adatelemekre, a vizualizáció a kijelöléskezelőt hívja meg az adatpontok kijelöléséhez. Ha a felhasználó a vizualizáció háttérelemére kattint, meghívja a kijelöléstörlés-kezelőt.

    Az osztály a következő megfeleltetési metódusokkal rendelkezik:
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`.

    ```typescript
    export class Behavior<SelectableDataPointType extends BaseDataPoint> implements IInteractiveBehavior {

        /** d3 selection object of main elements in the chart */
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

    **A `BaseBehavior` osztály kiterjesztése**

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

5. Az elemekre való kattintások kezeléséhez hívja meg a *d3* objektumkijelölés `on` metódusát. Ez a következőkre is vonatkozik: `elementsSelection` és `clearCatcherSelection`.

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

6. A kijelöléskezelő `contextmenu` metódusának meghívásához adjon hozzá egy hasonló kezelőt a `showContextMenu` eseményhez.

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

7. Az interaktivitási eszközök a `bindEvents` metódust hívják meg a függvények kezelőkhöz való hozzárendeléséhez. Adja hozzá a következő hívásokat a `bindEvents` metódushoz:
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`

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

8. A vizualizáció diagramelemei állapotának frissítését a `renderSelection` metódus végzi. Íme egy példa a `renderSelection` megvalósítására.

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

9. Az utolsó lépés egy `visual behavior` példány létrehozása és az interaktivitási eszközök példány `bind` metódusának meghívása.

    ```typescript
    this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
        behavior: this.behavior,
        dataPoints: this.categories,
        clearCatcherSelection: select(this.target),
        elementsSelection: selectionMerge
    });
    ```

    * A `selectionMerge` a *d3* objektumkijelölése, amely a vizualizáció kijelölhető elemeit képviseli.
    * A `select(this.target)` a *d3* kijelölésobjektuma, amely a vizualizáció fő DOM-elemeit képviseli.
    * A `this.categories` elemekkel rendelkező adatpontokat jelöl, ahol az interfész `VisualDataPoint` vagy `categories: VisualDataPoint[];`.
    * A `this.behavior` a `visual behavior` új példánya, amelyet a vizualizáció konstruktorában hoztak létre az alább látható módon.

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
## <a name="next-steps"></a>További lépések

* [Tudnivalók a kijelölések kezeléséről könyvjelzőváltáskor](bookmarks-support.md#visuals-with-selection)

* [Tudnivalók a vizualizációk adatpontjaihoz adható helyi menüről](context-menu.md)

* [Tudnivalók kijelölések Power BI-vizualizációkhoz adásáról a kijelöléskezelő használatával](selection-api.md)
