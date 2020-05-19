---
title: 'Oktatóanyag: React-alapú vizualizáció létrehozása a Power BI-hoz'
description: Ez az oktatóanyag bemutatja, hogyan hozhat létre Power BI-vizualizációt a React használatával. Egy körben egy érték jelenik meg. Ez a méretezési és beállítási lehetőségekkel testreszabható.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 03/30/2020
ms.openlocfilehash: 2b1b28608799616f4bc75837f82521ae345cf186
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83148877"
---
# <a name="tutorial-create-a-react-based-visual"></a>Oktatóanyag: React-alapú vizualizáció létrehozása

Ez az oktatóanyag bemutatja, hogyan hozhat létre Power BI-vizualizációt a [React](https://reactjs.org/) használatával. A vizualizáció egy körben egy értéket jelenít meg. A vizualizáció módosítható mérettel és beállításokkal rendelkezik a testreszabáshoz. A cikkben szereplő információk alapján létrehozhatja saját Power BI-vizualizációját a Reacttel.

![A ColoredCircleCard típusú Power BI-vizualizáció](./media/create-react-visual/powerbi-visuals-colored-circle-card.png)

Az oktatóanyag a következőket ismerteti:

> [!div class="checklist"]
>
> * A fejlesztési környezet beállítása
> * React-vizualizáció létrehozása
> * A vizualizáció képességeinek konfigurálása
> * Adatok megjelenítése a Power BI-ból
> * A vizualizáció átméretezése
> * A vizualizáció testreszabhatóvá tétele

## <a name="prerequisites"></a>Előfeltételek

* Egy **Power BI Pro-fiók**. Mielőtt hozzáfogna, [regisztráljon az ingyenes próbaverzióra](https://powerbi.microsoft.com/pricing/).
* [Visual Studio Code](https://www.visualstudio.com/).
* Windows-felhasználóknak a [Windows PowerShell](https://docs.microsoft.com/powershell/scripting/install/installing-windows-powershell?view=powershell-6) 4-es vagy újabb verziójára, OSX-felhasználóknak a [Terminal](https://macpaw.com/how-to/use-terminal-on-mac) segédprogramra van szükségük.
* [A fejlesztői környezet beállítása](custom-visual-develop-tutorial.md#setting-up-the-developer-environment) című fejezetben bemutatott környezet szükséges.

## <a name="getting-started"></a>Első lépések

Kezdésképp hozzon létre egy minimális Power BI-vizualizációt a `pbiviz` használatával. A projektekkel és a projektek felépítésével kapcsolatos további információt a [Power BI-vizualizációs projekt szerkezetének bemutatásánál](visual-project-structure.md) találja. A vizualizáció teljes forráskódja a [Circle Card React-vizualizáció](https://github.com/Microsoft/powerbi-visuals-circlecard-react) leírásában érhető el.

A vizualizáció teljes forráskódja letölthető vagy klónozható a [GitHubról](https://github.com/Microsoft/powerbi-visuals-circlecard-react).

1. Nyissa meg a PowerShellt, és futtassa az alábbi parancsot:

   ```powershell
   pbiviz new ReactCircleCard
   ```

   A parancs egy mappát hoz létre *ReactCircleCard* néven.

1. Módosítsa a könyvtárakat erre a mappára, és nyissa meg a Visual Studio Code-ot.

   ```powershell
   cd ./ReactCircleCard
   code .
   ```

1. Indítsa el a vizualizáció fejlesztői kiszolgálóját.

   ```powershell
   pbiviz start
   ```

   ![A React-vizualizáció frissítése](./media/create-react-visual/update-react-visual.png)

Ez az alapszintű vizualizáció a frissítések számát jelöli. Következő lépésként át fogjuk alakítani egy kerek kártyává.

## <a name="change-the-visual-to-a-circle-card"></a>A vizualizáció átalakítása kerek kártyává

Ez az alapszintű vizualizáció a frissítések számát jelöli. A következő lépésben alakítsa át egy kerek kártyává, amely egy mértéket és annak címét jelöli.

1. Futtassa az alábbi parancsot a szükséges függőségek telepítéséhez:

   ```powershell
   npm i react react-dom
   ```

1. Futtassa az alábbi parancsot a React 16, illetve a `react-dom` és a tipizálások megfelelő verzióinak telepítéséhez:

   ```powershell
   npm i @types/react @types/react-dom
   ```

1. Hozzon létre egy React-összetevőosztályt. A Visual Studio Code-ban válassza a **Fájl** > **Új fájl** elemet. Másolja a következő kódot a fájlba.

    ```typescript
    import * as React from "react";

    export class ReactCircleCard extends React.Component<{}>{
        render(){
            return (
                <div className="circleCard">
                    Hello, React!
                </div>
            )
        }
    }

    export default ReactCircleCard;
    ```

1. Válassza a **Mentés másként** lehetőséget. Nyissa meg az *src* könyvtárat. Adja meg a név *összetevőt*. **Fájltípusként** adja meg a **TypeScript React** lehetőséget.

1. Nyissa meg az *src/visual.ts* fájlt. Cserélje le a jelenlegi kódot a következőre:

    ```typescript
    "use strict";
    import powerbi from "powerbi-visuals-api";

    import DataView = powerbi.DataView;
    import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions;
    import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions;
    import IVisual = powerbi.extensibility.visual.IVisual;

    import "./../style/visual.less";

    export class Visual implements IVisual {

        constructor(options: VisualConstructorOptions) {

        }

        public update(options: VisualUpdateOptions) {

        }
    }
    ```

1. Importálja a React-függőségeket és az imént hozzáadott összetevőt.

    ```typescript
    import * as React from "react";
    import * as ReactDOM from "react-dom";
    ...
    import ReactCircleCard from "./component";
    ```

   A Power BI alapértelmezett TypeScript-beállításai nem fogadják el a React *tsx*-fájljait. A `component` esetében a Visual Studio Code hibát jelez.

1. Nyissa meg a *tsconfig.json* fájlt, és adjon hozzá két sort a `compilerOptions` elem elejéhez.

    ```json
    {
      "compilerOptions": {
        "jsx": "react",
        "types": ["react", "react-dom"],
        //...
      }
    }
    ```

   A `component`-hibának el kell tűnnie.

   Az összetevő megjelenítéséhez adja hozzá a cél HTML-elemet. Az elem a `HTMLElement` a `VisualConstructorOptions`-ben, amelyet a rendszer továbbít a konstruktorba.

1. Módosítsa a `Visual` osztályt az alábbi kódban szereplő módon:

    ```typescript
      private target: HTMLElement;
      private reactRoot: React.ComponentElement<any, any>;

      constructor(options: VisualConstructorOptions) {
          this.reactRoot = React.createElement(ReactCircleCard, {});
          this.target = options.element;

          ReactDOM.render(this.reactRoot, this.target);
      }
    ```

1. Mentse a módosításokat, és futtassa a meglévő kódot a következő paranccsal:

    ```bash
    pbiviz start
    ```

   > [!NOTE]
   > Ha korábban már futtatta a `pbiviz` eszközt, újra kell indítania a *tsconfig.json* fájl módosításainak alkalmazásához.

  ![„Hello React” üzenet a vizualizációban](./media/create-react-visual/hello-react-message-visual.png)

## <a name="configure-capabilities"></a>A képességek konfigurálása

Konfigurálhatja a vizualizáció képességeit.

1. Nyissa meg a következő fájlt: `capabilities.json`. Távolítsa el a `Category Data` objektumot a `dataRoles` kulcsból. A `ReactCircleCard` egy értéket jelenít meg, így csak a `Measure Data` szükséges. A `dataRoles` kulcsnak most így kell kinéznie:

    ```json
    "dataRoles": [
        {
            "displayName": "Measure Data",
            "name": "measure",
            "kind": "Measure"
        }
    ],
    ```

1. Távolítsa el az `objects` kulcs összes tartalmát. Ezt majd később kitölti.

    ```json
        "objects": {},
    ```

1. Másolja ki a `dataViewMappings` tulajdonság alábbi kódját. A `max: 1` azt jelenti, hogy csak az egyetlen mértékoszlop küldhető el.

    ```json
        "dataViewMappings": [
            {
                "conditions": [
                    {
                        "measure": {
                            "max": 1
                        }
                    }
                ],
                "single": {
                    "role": "measure"
                }
            }
        ]
    ```

Most már áthelyezhet adatokat a `Fields` ablaktáblából a vizualizációs beállításokba.

![Adatok mérése a Power BI-ban](./media/create-react-visual/measure-data-powerbi-react-visual.png)

## <a name="receive-properties-from-power-bi"></a>Tulajdonságok fogadása a Power BI-ból

A React használatával adatokat jeleníthet meg. Az összetevő a saját állapotából származó adatok megjelenítésére képes.

1. Módosítsa az *src/component.tsx* fájlt.

    ```javascript
    export interface State {
        textLabel: string,
        textValue: string
    }

    export const initialState: State = {
        textLabel: "",
        textValue: ""
    }

    export class ReactCircleCard extends React.Component<{}, State>{
        constructor(props: any){
            super(props);
            this.state = initialState;
        }

        render(){
            const { textLabel, textValue } = this.state;

            return (
                <div className="circleCard">
                    <p>
                        {textLabel}
                        <br/>
                        <em>{textValue}</em>
                    </p>
                </div>
            )
        }
    }
    ```

1. A *styles/visual.less* szerkesztésével stílusokat adhat hozzá az új kódhoz.

    ```css
    .circleCard {
        position: relative;
        box-sizing: border-box;
        border: 1px solid #000;
        border-radius: 50%;
        width: 200px;
        height: 200px;
    }

    p {
        text-align: center;
        line-height: 30px;
        font-size: 20px;
        font-weight: bold;

        position: relative;
        top: -30px;
        margin: 50% 0 0 0;
    }
    ```

1. A vizualizációk az `update` metódus argumentumaként kapják meg az aktuális adatokat. Nyissa meg az *src/visual.ts* fájlt, és adja hozzá a kódot a következőhöz: `ReactCircleCard.update`.

    ```typescript
    //...
    import { ReactCircleCard, initialState } from "./component";
    //...

    export class Visual implements IVisual {
        //...
        public update(options: VisualUpdateOptions) {

            if(options.dataViews && options.dataViews[0]){
                const dataView: DataView = options.dataViews[0];

                ReactCircleCard.update({
                    textLabel: dataView.metadata.columns[0].displayName,
                    textValue: dataView.single.value.toString()
                });
            }
            } else {
                this.clear();
            }
        }

        private clear() {
            ReactCircleCard.update(initialState);
        }
    }
    ```

    A kód kiválasztja a `DataView` `textLabel` és `textValue` elemét, és ha az adatok léteznek, frissíti az összetevő állapotát.

1. Ahhoz, hogy frissítéseket lehessen küldeni az összetevőpéldányra, be kell illesztenie a `ReactCircleCard` osztályba a következő kódot:

    ```typescript
        private static updateCallback: (data: object) => void = null;

        public static update(newState: State) {
            if(typeof ReactCircleCard.updateCallback === 'function'){
                ReactCircleCard.updateCallback(newState);
            }
        }

        public state: State = initialState;

        public componentWillMount() {
            ReactCircleCard.updateCallback = (newState: State): void => { this.setState(newState); };
        }

        public componentWillUnmount() {
            ReactCircleCard.updateCallback = null;
        }
    ```

1. Tesztelje a vizualizációt. Ellenőrizze, hogy a `pbiviz start` futtatása megtörtént-e, és mentse az összes fájlt. Frissítse a vizualizációt.

   ![Körben megjelenített érték a React vizualizációjában](./media/create-react-visual/value-display-circle-powerbi-react.png)

## <a name="make-component-resizable"></a>Összetevő méretezhetővé tétele

Ebben a szakaszban méretezhetővé fogja tenni az összetevőt. Jelenleg az összetevő rögzített szélességgel és magassággal rendelkezik.

Kérdezze le a vizualizáció nézőpontjának aktuális méretét az `options` objektumból.

1. Nyissa meg az *src/visual.ts* fájlt. Importálja az `IViewport` felületet, és adja hozzá a `viewport` tulajdonságot a `visual` osztályhoz.

    ```typescript
    import IViewport = powerbi.IViewport;

    //...

    export class Visual implements IVisual {
        private viewport: IViewport;
        //...
    }
    ```

1. Adja hozzá a következő kódot a `visual` `update` metódusához.

    ```typescript
      if (options.dataViews && options.dataViews[0]) {
          const dataView: DataView = options.dataViews[0];

          this.viewport = options.viewport;
          const { width, height } = this.viewport;
          const size = Math.min(width, height);

          ReactCircleCard.update({
              size,
              //...
          });
      }
    ```

1. Adjon meg tulajdonságokat a `State` felülethez az *src/component.tsx* fájlban.

    ```typescript
    export interface State {
        //...
        size: number
    }

    const initialState: State = {
        //...
        size: 200
    }
    ```

1. Hajtsa végre a `render` metódus következő módosításait az *src/component.tsx* fájlban:

    ```typescript
        render() {
            const { textLabel, textValue, size } = this.state;

            const style: React.CSSProperties = { width: size, height: size };

            return (
                <div className="circleCard" style={style}>
                    {/* ... */}
                </div>
            )
        }
    ```

1. A `width` és `height` szabályokat cserélje a `min-width` és `min-height` szabályokra a *style/visual.less* fájlban.

    ```css
        min-width: 200px;
        min-height: 200px;
    ```

Ezután átméretezheti a nézőpontot. A kör átmérője a minimális méretnek felel meg a szélesség vagy a magasság vonatkozásában.

## <a name="make-your-power-bi-visual-customizable"></a>A Power BI-vizualizáció testreszabhatóvá tétele

Ebben a szakaszban testreszabhatóvá fogja tenni a vizualizációt.

1. Nyissa meg a *capabilities.json* fájlt. Adja hozzá a következő beállításokat az `objects` tulajdonsághoz.

    ```json
    //...
        "objects": {
            "circle": {
                "displayName": "Circle",
                "properties": {
                    "circleColor": {
                        "displayName": "Color",
                        "description": "The fill color of the circle.",
                        "type": {
                            "fill": {
                                "solid": {
                                    "color": true
                                }
                            }
                        }
                    },
                    "circleThickness": {
                        "displayName": "Thickness",
                        "description": "The circle thickness.",
                        "type": {
                            "numeric": true
                        }
                    }
                }
            }
        },
    //...
    ```

1. Cserélje le az *src/settings.ts* fájlban szereplő kódot a következőre:

    ```typescript
    "use strict";

    import { dataViewObjectsParser } from "powerbi-visuals-utils-dataviewutils";
    import DataViewObjectsParser = dataViewObjectsParser.DataViewObjectsParser;

    export class CircleSettings {
        public circleColor: string = "white";
        public circleThickness: number = 2;
    }

    export class VisualSettings extends DataViewObjectsParser {
        public circle: CircleSettings = new CircleSettings();
    }
    ```

1. Az *src/visual.ts* kódfájl tetején adja hozzá a következő `import` utasításokat:

    ```typescript
    import VisualObjectInstance = powerbi.VisualObjectInstance;
    import EnumerateVisualObjectInstancesOptions = powerbi.EnumerateVisualObjectInstancesOptions;
    import VisualObjectInstanceEnumerationObject = powerbi.VisualObjectInstanceEnumerationObject;

    import { VisualSettings } from "./settings";

    ```

1. Adja hozzá az `enumerateObjectInstances` metódust az *src/visual.ts* fájlhoz. Ez a metódus a vizualizációs beállítások alkalmazására szolgál.

    ```typescript
    export class Visual implements IVisual {
        private settings: VisualSettings;

        //...

        public enumerateObjectInstances(
            options: EnumerateVisualObjectInstancesOptions
        ): VisualObjectInstance[] | VisualObjectInstanceEnumerationObject {

            return VisualSettings.enumerateObjectInstances(this.settings || VisualSettings.getDefault(), options);
        }
    }
    ```

1. A kód hozzáadását követően a `dataView` objektum fogadni tudja a beállításokat.

    ```typescript
        public update(options: VisualUpdateOptions) {

            if(options.dataViews && options.dataViews[0]){
                //...
                this.settings = VisualSettings.parse(dataView) as VisualSettings;
                const object = this.settings.circle;

                ReactCircleCard.update({
                    borderWidth: object && object.circleThickness ? object.circleThickness : undefined,
                    background: object && object.circleColor ? object.circleColor : undefined,
                    //...
                });
            }
        }
    }
    ```

1. Alkalmazza a megfelelő módosításokat az *src/component.tsx* fájlra. Ehhez először adja hozzá ezeket az értékeket a `State` függvényhez:

    ```typescript
    export interface State {
        //...
        background?: string,
        borderWidth?: number
    }
    ```

1. Ezután szúrja be a `render` metódusba az alábbi kódot:

    ```typescript
        const { /*...*/ background, borderWidth } = this.state;

        const style: React.CSSProperties = { /*...*/ background, borderWidth };
    ```

    ![A végleges ColoredCircleCard típusú Power BI-vizualizáció](./media/create-react-visual/powerbi-visuals-colored-circle-card.png)

## <a name="next-steps"></a>Következő lépések

A Power BI-fejlesztéssel kapcsolatos további információért lásd [a Power BI-vizualizációkhoz készült útmutatót](guidelines-powerbi-visuals.md) és [a Power BI-vizualizációk leírását](power-bi-visuals-concept.md).