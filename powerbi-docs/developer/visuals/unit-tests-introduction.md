---
title: Egységtesztek – bevezetés
description: Egységtesztek írása Power BI-vizualizációs projektekhez
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 06/18/2019
ms.openlocfilehash: 4b16eaad9b541bf6e5d8df49ffda99d9bbd5bbf2
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424539"
---
# <a name="tutorial-add-unit-tests-for-power-bi-visual-projects"></a>Oktatóanyag: Egységtesztek hozzáadása Power BI-vizualizációs projektekhez

Ez az oktatóanyag a Power BI-vizualizációkhoz készült egységtesztek írásának alapjait ismerteti.

Az oktatóanyagban a következőkkel foglalkozunk

* a karma.js tesztfuttató és a jasmine.js tesztelési keretrendszer használata
* a powerbi-visuals-utils-testutils csomag használata
* utánzatok és hamis elemek beállítása a Power BI-vizualizációk egységtesztelésének leegyszerűsítéséhez.

## <a name="prerequisites"></a>Előfeltételek

* Egy Power BI-vizualizációs projekt
* Konfigurált Node.JS-környezet

## <a name="install-and-configure-karmajs-and-jasmine"></a>A karma.js és a jasmine telepítése és konfigurálása

Adja hozzá a szükséges kódtárakat a package.json fájlhoz, a `devDependencies` szakaszban:

```json
"@babel/polyfill": "^7.2.5",
"@types/d3": "5.5.0",
"@types/jasmine": "2.5.37",
"@types/jasmine-jquery": "1.5.28",
"@types/jquery": "2.0.41",
"@types/karma": "3.0.0",
"@types/lodash-es": "4.17.1",
"coveralls": "3.0.2",
"istanbul-instrumenter-loader": "^3.0.1",
"jasmine": "2.5.2",
"jasmine-core": "2.5.2",
"jasmine-jquery": "2.1.1",
"jquery": "3.1.1",
"karma": "3.1.1",
"karma-chrome-launcher": "2.2.0",
"karma-coverage": "1.1.2",
"karma-coverage-istanbul-reporter": "^2.0.4",
"karma-jasmine": "2.0.1",
"karma-junit-reporter": "^1.2.0",
"karma-sourcemap-loader": "^0.3.7",
"karma-typescript": "^3.0.13",
"karma-typescript-preprocessor": "0.4.0",
"karma-webpack": "3.0.5",
"puppeteer": "1.17.0",
"style-loader": "0.23.1",
"ts-loader": "5.3.0",
"ts-node": "7.0.1",
"tslint": "^5.12.0",
"webpack": "4.26.0"
```

A csomagról további információt a lenti leírásban találhat.

Mentse a `package.json` fájlt, és hajtsa végre a parancssorban a `package.json` helyen:

```cmd
npm install
```

A csomagkezelő telepíti a `package.json` fájlhoz adott összes új csomagot

Egységtesztek futtatásához konfigurálnunk kell a tesztfuttatót és a `webpack` konfigurációját. A konfiguráció mintája itt megtalálható

Minta – `test.webpack.config.js`:

```typescript
const path = require('path');
const webpack = require("webpack");

module.exports = {
    devtool: 'source-map',
    mode: 'development',
    optimization : {
        concatenateModules: false,
        minimize: false
    },
    module: {
        rules: [
            {
                test: /\.tsx?$/,
                use: 'ts-loader',
                exclude: /node_modules/
            },
            {
                test: /\.json$/,
                loader: 'json-loader'
            },
            {
                test: /\.tsx?$/i,
                enforce: 'post',
                include: /(src)/,
                exclude: /(node_modules|resources\/js\/vendor)/,
                loader: 'istanbul-instrumenter-loader',
                options: { esModules: true }
            },
            {
                test: /\.less$/,
                use: [
                    {
                        loader: 'style-loader'
                    },
                    {
                        loader: 'css-loader'
                    },
                    {
                        loader: 'less-loader',
                        options: {
                            paths: [path.resolve(__dirname, 'node_modules')]
                        }
                    }
                ]
            }
        ]
    },
    externals: {
        "powerbi-visuals-api": '{}'
    },
    resolve: {
        extensions: ['.tsx', '.ts', '.js', '.css']
    },
    output: {
        path: path.resolve(__dirname, ".tmp/test")
    },
    plugins: [
        new webpack.ProvidePlugin({
            'powerbi-visuals-api': null
        })
    ]
};
```

Minta – `karma.conf.ts`

```typescript
"use strict";

const webpackConfig = require("./test.webpack.config.js");
const tsconfig = require("./test.tsconfig.json");
const path = require("path");

const testRecursivePath = "test/visualTest.ts";
const srcOriginalRecursivePath = "src/**/*.ts";
const coverageFolder = "coverage";

process.env.CHROME_BIN = require("puppeteer").executablePath();

import { Config, ConfigOptions } from "karma";

module.exports = (config: Config) => {
    config.set(<ConfigOptions>{
        mode: "development",
        browserNoActivityTimeout: 100000,
        browsers: ["ChromeHeadless"], // or Chrome to use locally installed Chrome browser
        colors: true,
        frameworks: ["jasmine"],
        reporters: [
            "progress",
            "junit",
            "coverage-istanbul"
        ],
        junitReporter: {
            outputDir: path.join(__dirname, coverageFolder),
            outputFile: "TESTS-report.xml",
            useBrowserName: false
        },
        singleRun: true,
        plugins: [
            "karma-coverage",
            "karma-typescript",
            "karma-webpack",
            "karma-jasmine",
            "karma-sourcemap-loader",
            "karma-chrome-launcher",
            "karma-junit-reporter",
            "karma-coverage-istanbul-reporter"
        ],
        files: [
            "node_modules/jquery/dist/jquery.min.js",
            "node_modules/jasmine-jquery/lib/jasmine-jquery.js",
            {
                pattern: './capabilities.json',
                watched: false,
                served: true,
                included: false
            },
            testRecursivePath,
            {
                pattern: srcOriginalRecursivePath,
                included: false,
                served: true
            }
        ],
        preprocessors: {
            [testRecursivePath]: ["webpack", "coverage"]
        },
        typescriptPreprocessor: {
            options: tsconfig.compilerOptions
        },
        coverageIstanbulReporter: {
            reports: ["html", "lcovonly", "text-summary", "cobertura"],
            dir: path.join(__dirname, coverageFolder),
            'report-config': {
                html: {
                    subdir: 'html-report'
                }
            },
            combineBrowserReports: true,
            fixWebpackSourcePaths: true,
            verbose: false
        },
        coverageReporter: {
            dir: path.join(__dirname, coverageFolder),
            reporters: [
                // reporters not supporting the `file` property
                { type: 'html', subdir: 'html-report' },
                { type: 'lcov', subdir: 'lcov' },
                // reporters supporting the `file` property, use `subdir` to directly
                // output them in the `dir` directory
                { type: 'cobertura', subdir: '.', file: 'cobertura-coverage.xml' },
                { type: 'lcovonly', subdir: '.', file: 'report-lcovonly.txt' },
                { type: 'text-summary', subdir: '.', file: 'text-summary.txt' },
            ]
        },
        mime: {
            "text/x-typescript": ["ts", "tsx"]
        },
        webpack: webpackConfig,
        webpackMiddleware: {
            stats: "errors-only"
        }
    });
};
```

Ha szükséges, módosíthatja ezt a konfigurációt.

Néhány beállítás – `karma.conf.js`:

* A `recursivePathToTests` változó megkeresi a tesztek kódjainak helyét.

* a `srcRecursivePath` változó a fordítás után megkeresi a kimeneti JS-kódot.

* A `srcCssRecursivePath` változó a fordítás után megkeresi a kimeneti CSS-t.

* A `srcOriginalRecursivePath` változó megkeresi a vizualizáció forráskódját.

* A `coverageFolder` változó meghatározza a jelentés létrehozásának helyét.

A konfiguráció néhány tulajdonsága:

* `singleRun: true` – teszteli a futtatást a CI-rendszeren. Elég egy alkalommal használni.
A tesztek hibakereséséhez `false` értékre módosíthatja. A Karma továbbra is futtatja a böngészőt, segítségével pedig a konzollal elvégezheti a hibakeresést.

* `files: [...]` – Ebben a tömbben beállíthatja a böngészőbe betöltendő fájlokat.
Itt általában forrásfájlok, tesztelési esetek és kódtárak (jasmine, test utils) találhatók. Igény szerint bővítheti a listát.

* `preprocessors` – A konfiguráció ezen szakaszában a műveleteket konfigurálhatja, amelyek az egységtesztek végrehajtása előtt aktiválódnak. Ezek a TypeScriptet JS-ként fordítják, majd előkészítik a térképfájlokat, és egy kódlefedési jelentést hoznak létre. A `coverage` elemet letilthatja a tesztek hibakereséséhez. A lefedettség további kódokat hoz létre a tesztlefedettséghez, amely bonyolíthatja a hibakeresési teszteket.

**A karma.js [dokumentációjában](https://karma-runner.github.io/1.0/config/configuration-file.html) található összes konfiguráció leírása**

A megfelelő használat érdekében adja hozzá a tesztparancsot a `scripts` elemhez:

```json
{
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "typings":"node node_modules/typings/dist/bin.js i",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "pretest": "pbiviz package --resources --no-minify --no-pbiviz --no-plugin",
        "test": "karma start"
    }
    ...
}
```

Most már készen áll az egységtesztek írásának megkezdésére.

## <a name="simple-unit-test-for-check-dom-element-of-the-visual"></a>Egyszerű egységteszt a vizualizáció DOM elemének ellenőrzéséhez

A vizualizáció teszteléséhez létre kell hoznunk a vizualizáció egy példányát.

### <a name="creating-visual-instance-builder"></a>Vizualizációpéldány-készítő létrehozása

Adja a `visualBuilder.ts` fájlt a `test` mappához a következő kóddal:

```typescript
import {
    VisualBuilderBase
} from "powerbi-visuals-utils-testutils";

import {
    BarChart as VisualClass
} from "../src/visual";

import  powerbi from "powerbi-visuals-api";
import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions;

export class BarChartBuilder extends VisualBuilderBase<VisualClass> {
    constructor(width: number, height: number) {
        super(width, height);
    }

    protected build(options: VisualConstructorOptions) {
        return new VisualClass(options);
    }

    public get mainElement() {
        return this.element.children("svg.barChart");
    }
}
```

A vizualizációpéldány létrehozásához használja a `build` metódust. A `mainElement` egy GET metódus, amely a „root” DOM elem egy példányát adja vissza a vizualizációban. A beolvasó használata nem kötelező, de megkönnyíti az egységteszt írását.

Elkészült a vizualizáció egy példányának szerkesztője. Írjuk meg a tesztelési esetet. A tesztelési eset ellenőrzi a vizualizáció megjelenésekor létrehozott SVG-elemeket.

### <a name="creating-typescript-file-to-write-test-cases"></a>TypeScript-fájl létrehozása tesztelési esetek írásához

A tesztelési esetekhez adja hozzá a `visualTest.ts` fájlt az alábbi kódokkal:

```typescript
import powerbi from "powerbi-visuals-api";

import { BarChartBuilder } from "./VisualBuilder";

import {
    BarChart as VisualClass
} from "../src/visual";

import VisualBuilder = powerbi.extensibility.visual.test.BarChartBuilder;

describe("BarChart", () => {
    let visualBuilder: VisualBuilder;
    let dataView: DataView;

    beforeEach(() => {
        visualBuilder = new VisualBuilder(500, 500);
    });

    it("root DOM element is created", () => {
        expect(visualBuilder.mainElement).toBeInDOM();
    });
});
```

Több metódust is meg kell hívni.

* A [`describe`](https://jasmine.github.io/api/2.6/global.html#describe) metódus a tesztelési esetet ismerteti. Egy jasmine-keretrendszerben ezt gyakran csomagnak vagy specifikációcsoportnak nevezik.

* A `beforeEach` metódus minden `it` metódus előtt lesz meghívva, amely a [`describe`](https://jasmine.github.io/api/2.6/global.html#beforeEach) metódusban van meghatározva.

* Az `it` egyetlen specifikációt definiál. Az [`it`](https://jasmine.github.io/api/2.6/global.html#it) metódusnak egy vagy több `expectations` elemet kell tartalmaznia.

* [`expect`](https://jasmine.github.io/api/2.6/global.html#expect) – ez a metódus egy specifikáció elvárásait hozza létre. A specifikáció akkor sikeres, ha minden elvárás hiba nélkül megvalósul.

* `toBeInDOM` – ez az egyik az egyeztetési módszer. Az egyezésekről a jasmine-keretrendszer [dokumentációjában](https://jasmine.github.io/api/2.6/matchers.html) olvashat.

**További információ a jasmine-keretrendszerről a hivatalos [dokumentációban](https://jasmine.github.io/).**

Ezután a parancssorba beírt paranccsal futtathatja az egységtesztet.

Ez a teszt ellenőrzi, létrejött-e a vizualizációk SVG-gyökéreleme.

### <a name="launch-unit-tests"></a>Egységtesztek elindítása

Az egységteszt futtatásához írja be ezt a parancsot a parancssorba.

```cmd
npm run test
```

A `karma.js` futtatja a Chrome böngészőt, és végrehajtja a tesztelési esetet.

![A Chrome-ban indított KarmaJS](./media/karmajs-chrome.png)

> [!NOTE]
> A Google Chrome-ot helyileg kell telepíteni.

A parancssorban a következő kimenet jelenik meg:

```cmd
> karma start

23 05 2017 12:24:26.842:WARN [watcher]: Pattern "E:/WORKSPACE/PowerBI/PowerBI-visuals-sampleBarChart/data/*.csv" does not match any file.
23 05 2017 12:24:30.836:WARN [karma]: No captured browser, open http://localhost:9876/
23 05 2017 12:24:30.849:INFO [karma]: Karma v1.3.0 server started at http://localhost:9876/
23 05 2017 12:24:30.850:INFO [launcher]: Launching browser Chrome with unlimited concurrency
23 05 2017 12:24:31.059:INFO [launcher]: Starting browser Chrome
23 05 2017 12:24:33.160:INFO [Chrome 58.0.3029 (Windows 10 0.0.0)]: Connected on socket /#2meR6hjXFmsE_fjiAAAA with id 5875251
Chrome 58.0.3029 (Windows 10 0.0.0): Executed 1 of 1 SUCCESS (0.194 secs / 0.011 secs)

=============================== Coverage summary ===============================
Statements   : 27.43% ( 65/237 )
Branches     : 19.84% ( 25/126 )
Functions    : 43.86% ( 25/57 )
Lines        : 20.85% ( 44/211 )
================================================================================
```

### <a name="how-to-add-static-data-for-unit-tests"></a>Statikus adatok hozzáadása egységtesztekhez

Hozza létre a `visualData.ts` fájlt a `test` mappában. Használja ezeket a kódokat:

```typescript
import powerbi from "powerbi-visuals-api";
import DataView = powerbi.DataView;

import {
    testDataViewBuilder,
    getRandomNumbers
} from "powerbi-visuals-utils-testutils";

export class SampleBarChartDataBuilder extends TestDataViewBuilder {
    public static CategoryColumn: string = "category";
    public static MeasureColumn: string = "measure";

    public constructor() {
        super();
        ...
    }

    public getDataView(columnNames?: string[]): DataView {
        let dateView: any = this.createCategoricalDataViewBuilder([
            ...
        ],
        [
            ...
        ], columnNames).build();

        // there's client side computed maxValue
        let maxLocal = 0;
        this.valuesMeasure.forEach((item) => {
                if (item > maxLocal) {
                    maxLocal = item;
                }
        });
        (<any>dataView).categorical.values[0].maxLocal = maxLocal;
    }
}
```

A `SampleBarChartDataBuilder` osztály kiterjeszti a `TestDataViewBuilder` elemet, és a `getDataView` absztrakt metódust implementálja.

Amikor adatmezőgyűjtőkbe helyezi az adatokat, a Power BI egy kategorikus `dataview` objektumot hoz létre az adatok alapján.

![Mezőgyűjtők](./media/fields-buckets.png)

Az egységteszteket nem reprodukálhatja a Power BI alapvető funkcióival. A statikus adatokat azonban kategorikus `dataview` elemekre kell leképeznie. Az `TestDataViewBuilder` osztály ebben segít.

[További információ a DataViewMapping elemről](https://github.com/Microsoft/PowerBI-visuals/blob/master/Capabilities/DataViewMappings.md)

A `getDataView` metódusban csak a `createCategoricalDataViewBuilder` metódust hívja meg az adataival.

A `sampleBarChart` vizualizáció [capabilities.json](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/capabilities.json#L2) fájljában egy dataRoles és egy dataViewMapping-objektum található:

```json
"dataRoles": [
    {
        "displayName": "Category Data",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Measure Data",
        "name": "measure",
        "kind": "Measure"
    }
],
"dataViewMappings": [
    {
        "conditions": [
            {
                "category": {
                    "max": 1
                },
                "measure": {
                    "max": 1
                }
            }
        ],
        "categorical": {
            "categories": {
                "for": {
                    "in": "category"
                }
            },
            "values": {
                "select": [
                    {
                        "bind": {
                            "to": "measure"
                        }
                    }
                ]
            }
        }
    }
],
```

Ugyanezen leképezés létrehozásához a következő paramétereket a `createCategoricalDataViewBuilder` metódusra kell beállítania:

```typescript
([
    {
        source: {
            displayName: "Category",
            queryName: SampleBarChartData.ColumnCategory,
            type: ValueType.fromDescriptor({ text: true }),
            roles: {
                Category: true
            },
        },
        values: this.valuesCategory
    }
],
[
    {
        source: {
            displayName: "Measure",
            isMeasure: true,
            queryName: SampleBarChartData.MeasureColumn,
            type: ValueType.fromDescriptor({ numeric: true }),
            roles: {
                Measure: true
            },
        },
        values: this.valuesMeasure
    },
], columnNames)
```

Ahol a `this.valuesCategory` kategóriák egy tömbje.

```ts
public valuesCategory: string[] = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"];
```

a `this.valuesMeasure` pedig az egyes kategóriák mértékeinek tömbje. Például:

```ts
public valuesMeasure: number[] = [742731.43, 162066.43, 283085.78, 300263.49, 376074.57, 814724.34, 570921.34];
```

Most már használhatja a `SampleBarChartDataBuilder` osztályt az egységtesztben.

A `powerbi-visuals-utils-testutils` csomagban definiált `ValueType` osztály. A `createCategoricalDataViewBuilder` metódushoz a `lodash` címtár szükséges.

Adja hozzá ezeket a csomagokat a függőségekhez.

A `package.json` fájlban, a `devDependencies` szakaszban

```json
"lodash-es": "4.17.1",
"powerbi-visuals-utils-testutils": "2.2.0"
```

hívja meg a metódust

```cmd
npm install
```

a `lodash-es` címtár telepítéséhez.

Most már futtathatja újra az egységtesztet. Ennek a kimenetnek kell megjelennie

```cmd
> karma start

23 05 2017 16:19:54.318:WARN [watcher]: Pattern "E:/WORKSPACE/PowerBI/PowerBI-visuals-sampleBarChart/data/*.csv" does not match any file.
23 05 2017 16:19:58.333:WARN [karma]: No captured browser, open http://localhost:9876/
23 05 2017 16:19:58.346:INFO [karma]: Karma v1.3.0 server started at http://localhost:9876/
23 05 2017 16:19:58.346:INFO [launcher]: Launching browser Chrome with unlimited concurrency
23 05 2017 16:19:58.394:INFO [launcher]: Starting browser Chrome
23 05 2017 16:19:59.873:INFO [Chrome 58.0.3029 (Windows 10 0.0.0)]: Connected on socket /#NcNTAGH9hWfGMCuEAAAA with id 3551106
Chrome 58.0.3029 (Windows 10 0.0.0): Executed 1 of 1 SUCCESS (1.266 secs / 1.052 secs)

=============================== Coverage summary ===============================
Statements   : 56.72% ( 135/238 )
Branches     : 32.54% ( 41/126 )
Functions    : 66.67% ( 38/57 )
Lines        : 52.83% ( 112/212 )
================================================================================
```

A vizualizációban pedig az elindult Chrome böngészőnek kell megjelennie.

![UT-indítások a Chrome-ban](./media/karmajs-chrome-ut-runned.png)

Növelje a figyelemlefedettség összegzését. További információt az aktuális kódlefedettségről itt találhat: `coverage\index.html`

![UT-lefedettségi index](./media/code-coverage-index.png)

Vagy az `src` mappa hatókörében

![Az src mappa lefedettsége](./media/code-coverage-src-folder.png)

A fájl hatókörében megtekintheti a forráskódot. A `Coverage` segédeszközei pirosra állítják a sor hátterét, ha a kód nem futott az egységtesztek alatt.

![A visual.ts fájl kódlefedettsége](./media/code-coverage-visual-src.png)

> [!IMPORTANT]
> A kódlefedettség azonban nem jelenti azt, hogy jó a vizualizáció funkciólefedettsége. Az `src\visual.ts` helyen egyetlen egyszerű egységteszt több mint 96%-os lefedettséget nyújtott.

## <a name="next-steps"></a>Következő lépések

Ha a vizualizáció elkészült, közzéteheti.

[További információ a vizualizációk az AppSource-on való közzétételéről](../office-store.md)
