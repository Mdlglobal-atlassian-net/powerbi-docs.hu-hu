---
title: Egységtesztek hozzáadása Power BI-vizualizációs projektekhez - Bevezetés
description: Ez a cikk egységtesztek írását mutatja be Power BI-vizualizációs projektekhez
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 06/18/2019
ms.openlocfilehash: 996e409e634292ca0767f34c49931cfbcdcd4b94
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/14/2020
ms.locfileid: "79379555"
---
# <a name="tutorial-add-unit-tests-for-power-bi-visual-projects"></a>Oktatóanyag: Egységtesztek hozzáadása Power BI-vizualizációs projektekhez

Ez a cikk a Power BI-vizualizációkhoz készült egységtesztek írásának alapjait ismerteti, köztük az alábbiakat:

* A Karma JavaScript-tesztfuttatási keretrendszer, a Jasmine beállítása.
* A powerbi-visuals-utils-testutils csomag használata.
* Utánzatok és hamis elemek beállítása a Power BI-vizualizációk egységtesztelésének leegyszerűsítéséhez.

## <a name="prerequisites"></a>Előfeltételek

* Telepített Power BI-vizualizációs projekt
* Konfigurált Node.js-környezet

## <a name="install-and-configure-the-karma-javascript-test-runner-and-jasmine"></a>A Karma JavaScript-tesztfuttató és a Jasmine telepítése és konfigurálása

Vegye fel a szükséges kódtárakat a *package.json* fájl `devDependencies` szakaszába:

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

Ha többet szeretne megtudni a *package.json*ról, tekintse meg a leírást az [npm-package.json](https://docs.npmjs.com/files/package.json) helyen.

Mentse a *package.json* fájl, majd futtassa az alábbi parancsot a `package.json`-fájl helyén:

```cmd
npm install
```

A csomagkezelő telepíti a *package.json* fájlba felvett összes új csomagot.

Egységtesztek futtatásához konfigurálja a tesztfuttatót és a `webpack` konfigurációját.

Az alábbi kód a *test.webpack.config.js* fájlra mutat egy példát:

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

Az alábbi kód a *karma.conf.ts* fájlra mutat egy példát:

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

Ezt a konfigurációt szükség esetén módosíthatja.

A *karma.conf.js* a következő változókat tartalmazza:

* `recursivePathToTests`: A teszt kódjának helyét adja meg

* `srcRecursivePath`: A JavaScript kimenet fordítás utáni helyét adja meg

* `srcCssRecursivePath`: A CSS kimenet helyét adja meg stílusokat tartalmazó Less-fájlok fordítása után

* `srcOriginalRecursivePath`: A vizualizáció forráskódjának helyét adja meg

* `coverageFolder`: Meghatározza, hogy a rendszer létrehozzon-e lefedettségi jelentést

A konfigurációs fájl az alábbi tulajdonságokat tartalmazza:

* `singleRun: true`: A tesztek futhatnak folyamatos integrációs (CI) rendszeren, vagy egy alkalommal. A tesztek hibakereséséhez a *false* értékre módosíthatja ezt a beállítást. A Karma futni hagyja a böngészőt, hogy használhassa a konzolt a hibakereséshez.

* `files: [...]`: Ebben a tömbben a böngészőbe betöltendő fájlokat adhatja meg. Itt általában forrásfájlok, tesztesetek és kódtárak (jasmine, tesztelési segédprogramok) találhatók. Igény szerint további fájlokat is felvehet a listára.

* `preprocessors`: Ebben a szakaszban az egységtesztek előtt futtatandó műveleteket konfigurálhatja. Ezek előfordítják a TypeScriptet JavaScriptre, majd előkészítik a térképfájlokat, és egy kódlefedési jelentést hoznak létre. A tesztek hibakeresése alatt a `coverage` letiltható. A lefedettség további kódokat hoz létre a tesztlefedettséghez, ez pedig bonyolíthatja a hibakeresési teszteket.

Az összes Karma-konfiguráció leírását megtalálhatja a [Karma konfigurációs fájlját](https://karma-runner.github.io/1.0/config/configuration-file.html) ismertető oldalon.

A kényelem érdekében felvehet egy tesztelési parancsot a `scripts` szakaszba:

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

Már minden készen áll az egységtesztek írásának megkezdéséhez.

## <a name="check-the-dom-element-of-the-visual"></a>A vizualizáció DOM-elemének ellenőrzése

A vizualizáció teszteléséhez először hozza létre annak egy példányát.

### <a name="create-a-visual-instance-builder"></a>Vizualizációpéldány-készítő létrehozása

A *test* könyvtárba vegyen fel egy *visualBuilder.ts*fájlt az alábbi kód használatával:

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

A vizualizációpéldány létrehozásához használja a `build` metódust. A `mainElement` egy GET metódus, amely a „root” dokumentum-objektummodell (DOM) elem egy példányát adja vissza a vizualizációban. A beolvasó használata nem kötelező, de megkönnyíti az egységteszt írását.

Most már rendelkezik a vizualizáció egy példányának egy buildjével. Írjuk meg a tesztelési esetet. A teszteset a vizualizáció megjelenésekor létrehozott SVG-elemeket ellenőrzi.

### <a name="create-a-typescript-file-to-write-test-cases"></a>TypeScript-fájl létrehozása a tesztesetek írásához

Vegyen fel egy *visualTest.ts* fájlt a tesztesetekhez az alábbi kód használatával:

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

Több metódus van meghívva:

* [`describe`](https://jasmine.github.io/api/2.6/global.html#describe): A tesztesetet írja le. A Jasmine-keretrendszerben gyakran specifikációcsomagot vagy -csoportot ír le.

* `beforeEach`: Az `it` metódus minden hívása előtt meg lesz hívva, amely a [`describe`](https://jasmine.github.io/api/2.6/global.html#beforeEach) metódusban van definiálva.

* [`it`](https://jasmine.github.io/api/2.6/global.html#it): Egyetlen specifikációt definiál. Az `it` metódusnak egy vagy több `expectations` elemet kell tartalmaznia.

* [`expect`](https://jasmine.github.io/api/2.6/global.html#expect): Egy specifikáció elvárásait hozza létre. A specifikáció akkor sikeres, ha minden elvárás hiba nélkül megvalósul.

* `toBeInDOM`: Az *egyeztetési* metódusok egyike. Az egyeztetőkről a [Jasmin névtér: egyeztetők](https://jasmine.github.io/api/2.6/matchers.html) című cikkben olvashat.

A Jasmine keretrendszerről a [Jasmine keretrendszer dokumentációs](https://jasmine.github.io/) oldalán talál további információt.

### <a name="launch-unit-tests"></a>Egységtesztek elindítása

Ez a teszt ellenőrzi, létrejött-e a vizualizációk SVG-gyökéreleme. Az egységteszt futtatásához írja be az alábbi parancsot a parancssori eszközbe:

```cmd
npm run test
```

A `karma.js` a Chrome böngészőben futtatja a tesztesetet.

![A Chrome böngészőben futó Karma-JavaScript](media/unit-tests-introduction/karmajs-chrome.png)

> [!NOTE]
> A Google Chrome böngészőt helyileg kell telepítenie.

A parancssori ablakban a következő kimenet jelenik meg:

```cmd
> karma start

23 05 2017 12:24:26.842:WARN [watcher]: Pattern "E:/WORKSPACE/PowerBI/PowerBI-visuals-sampleBarChart/data/*.csv" does not match any file.
23 05 2017 12:24:30.836:WARN [karma]: No captured browser, open https://localhost:9876/
23 05 2017 12:24:30.849:INFO [karma]: Karma v1.3.0 server started at https://localhost:9876/
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

A *test* könyvtárban hozza lére a *visualData.ts*fájlt az alábbi kód használatával:

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

A `SampleBarChartDataBuilder` osztály kiterjeszti a `TestDataViewBuilder` elemet, és implementálja a `getDataView` absztrakt metódust.

Amikor adatmezőgyűjtőkbe helyezi az adatokat, a Power BI egy kategorikus `dataview` objektumot hoz létre az adatok alapján.

![Adatmezőgyűjtők](media/unit-tests-introduction/fields-buckets.png)

Az egységtesztek során nem állnak rendelkezésére a Power BI alapvető funkciói az adatok reprodukálásához. A statikus adatokat azonban le kell képeznie a kategorikus `dataview` elemekre. A leképezésben a `TestDataViewBuilder` osztály segíthet.

Az adatnézet-leképezésről a [DataViewMappings](https://github.com/Microsoft/PowerBI-visuals/blob/master/Capabilities/DataViewMappings.md) oldalon talál további információt.

A `getDataView` metódusban a `createCategoricalDataViewBuilder` metódust hívja meg az adatokkal.

A `sampleBarChart` vizualizáció [capabilities.json](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/capabilities.json#L2) fájljában dataRoles és dataViewMapping-objektumok találhatók:

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

Itt `this.valuesCategory` egy kategóriákból álló tömb:

```ts
public valuesCategory: string[] = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"];
```

A `this.valuesMeasure` viszont mértékekből álló tömb az egyes kategóriákhoz:

```ts
public valuesMeasure: number[] = [742731.43, 162066.43, 283085.78, 300263.49, 376074.57, 814724.34, 570921.34];
```

Most már felhasználhatja a `SampleBarChartDataBuilder` osztályt az egységtesztben.

A `ValueType` osztály a powerbi-visuals-utils-testutils csomagban van definiálva. A `createCategoricalDataViewBuilder` metódushoz a `lodash` kódtár szükséges.

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

Most már futtathatja újra az egységtesztet. Az alábbi kimenetet kell kapnia:

```cmd
> karma start

23 05 2017 16:19:54.318:WARN [watcher]: Pattern "E:/WORKSPACE/PowerBI/PowerBI-visuals-sampleBarChart/data/*.csv" does not match any file.
23 05 2017 16:19:58.333:WARN [karma]: No captured browser, open https://localhost:9876/
23 05 2017 16:19:58.346:INFO [karma]: Karma v1.3.0 server started at https://localhost:9876/
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

A vizualizáció az alábbi ábrán látható módon megnyílik a Chrome böngészőben:

![UT-indítások a Chrome-ban](media/unit-tests-introduction/karmajs-chrome-ut-runned.png)

Az összegzés a lefedettség növekedését mutatja. Az aktuális kódlefedettségről a következő helyen találhat további információkat: `coverage\index.html`.

![UT-lefedettségi index](media/unit-tests-introduction/code-coverage-index.png)

Megtekintheti az `src` könyvtár hatókörét is:

![Az scr könyvtár lefedettsége](media/unit-tests-introduction/code-coverage-src-folder.png)

A fájl hatókörében megtekintheti a forráskódot. A `Coverage` segédprogramok piros színnel emelik ki a sort, ha valamely kód nincs végrehajtva az egységteszt során.

![A visual.ts fájl kódlefedettsége](media/unit-tests-introduction/code-coverage-visual-src.png)

> [!IMPORTANT]
> A kódlefedettség nem jelenti azt, hogy jó a vizualizáció funkciólefedettsége. Egy egyszerű egységteszt több, mint 96%os lefedettséget biztosít a `src\visual.ts` fájlban.

## <a name="next-steps"></a>Következő lépések

A kész vizualizációt beküldheti közzétételre. További információ: [Power BI-vizualizációk közzététele az AppSource-ban](office-store.md).
