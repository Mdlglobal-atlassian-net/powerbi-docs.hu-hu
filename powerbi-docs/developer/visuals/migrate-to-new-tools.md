---
title: Áttérés a powerbi-visuals-tools 3.x használatára
description: Első lépések a powerbi-visuals-tools új verziójával
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: cc554bff1cbd248ccd69a80ee47b60af981cdab1
ms.sourcegitcommit: f7b28ecbad3e51f410eff7ee4051de3652e360e8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/13/2019
ms.locfileid: "74061822"
---
# <a name="migrate-to-the-new-powerbi-visuals-tools-3xx"></a>Áttérés az új powerbi-visuals-tools 3.x.x használatára

A 3-as verziótól kezdődően a Power BI Visuals Tools a Webpack használatával készít egyéni vizualizációkat.
Az új verzió számos új lehetőséget kínál a fejlesztőknek vizualizációk létrehozására:

* Alapértelmezett a TypeScript v3.x.x. A TypeScript 1.5 verziótól kezdődően az elnevezések rendszere megváltozott. [További tudnivalók a TypeScript-modulokról](https://www.typescriptlang.org/docs/handbook/modules.html).

* Támogatottak az ES6 modulok. Többé nincs szükség az [externalJS](migrate-to-new-tools.md#fix-loading-external-libraries) használatára, helyette ES6-importálást használhat.

* Támogatottak a [D3v5](https://d3js.org/) és más ES6 modulalapú kódtárak új verziói.

* Kisebb csomagméret. A Webpack [Tree Shaking](https://webpack.js.org/guides/tree-shaking/) használatával távolítja el a nem használt kódot. Ez csökkenti a JS-kód méretét, ezzel pedig jobb teljesítményt eredményez a vizualizáció betöltésekor.

* Jobb API-teljesítmény.

* A globalize.js kódtár [integrálva van](migrate-to-new-tools.md#remove-globalizejs-library) a formattingutils csomagba.

* A Tools a [webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) használatával jeleníti meg a vizualizáció kódbázisát.

A cikk további része a Power BI Visuals Tools új verziójára való áttérés valamennyi lépését ismerteti.

## <a name="backward-compatibility"></a>Kompatibilitás az előző verziókkal

Az új eszközök megtartják a visszamenőleges kompatibilitást a régi vizualizációk kódbázisával, de további módosításokat igényelhetnek külső kódtárak betöltéséhez.

A modulrendszereket támogató kódtárak Webpack-csomagokként lesznek importálva. Az összes többi kódtár és vizualizáció-forráskód egy modulba lesz csomagolva.

A korábbi powerbi-visuals-tools eszközökben használt olyan globális változók, mint a JQuery és a Lodash már elavultak. Ez azt jelenti, hogy ha a régi vizualizáció kódja globális változókat használ, akkor ez a vizualizáció hibásnak bizonyulhat.

A Power BI Visuals Tools előző verziójához szükség volt a `powerbi.extensibility.visual` modul alatt definiált vizualizáció-osztályra.

## <a name="how-to-install-powerbi-visuals-tools"></a>A powerbi-visuals-tools telepítése

Az új eszközkészlet a következő paranccsal telepíthető

```cmd
npm install -g powerbi-visuals-tools
```

A SampleBarChart minta-vizualizáció és a `package.json` megfelelő [módosításai](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/package.json#L16):

```json
{
    "name": "visual",
    "version": "1.2.3",
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "test": "pbiviz package --resources --no-minify --no-pbiviz"
    },
    "devDependencies": {
      "@types/d3": "5.0.0",
      "d3": "5.5.0",
      "powerbi-visuals-tools": "^3.1.0",
      "tslint": "^4.4.2",
      "tslint-microsoft-contrib": "^4.0.0"
    }
}
```

## <a name="how-to-install-power-bi-custom-visuals-api"></a>A Power BI Custom Visuals API telepítése

A powerbi-visuals-tools új verziója nem foglal magában minden API-verziót. Ehelyett a fejlesztőnek kell telepítenie a [`powerbi-visuals-api`](https://www.npmjs.com/package/powerbi-visuals-api) csomag kívánt verzióját. A csomag verziója megegyezik a Power BI Custom Visuals API-verziójával, és minden típusdefiníciót megad a Power BI Custom Visuals API-hoz.

A `powerbi-visuals-api` az `npm install --save-dev powerbi-visuals-api` parancs végrehajtásával vehető fel a projekt függőségei közé.
A régi API-típusdefiníciókra mutató hivatkozást el kell távolítani. A `powerbi-visuals-api` csomagból származó típusokat a Webpack automatikusan befoglalja. Az erre vonatkozó módosítások a `package.json` fájlnak [ebben](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/package.json#L14) a sorában találhatók.

## <a name="update-tsconfigjson"></a>A `tsconfig.json` frissítése

Külső modulok használatához az `out` beállítást az `outDir` beállítás váltja fel.
`"out": "./.tmp/build/visual.js",` helyett `"outDir": "./.tmp/build/",`.

Ez azért szükséges, mert a TypeScript-fájlok egymástól függetlenül vannak JavaScript-fájlokká lefordítva. Ezért nem kell többé a visual.js fájlt megadni kimenetként.

A `target` beállítást is az `ES6` beállításra cserélheti, ha modern JavaScript-kimenetet szeretne. [Ez nem kötelező](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/tsconfig.json#L6).

## <a name="update-custom-visuals-utils"></a>Egyéni vizualizációs segédprogramok frissítése

Ha használja a [powerbi-visuals-utils](https://www.npmjs.com/search?q=powerbi-visuals-utils) segédprogramjainak egyikét, akkor ezeket is érdemes a legújabb verzióra frissíteni.

Futtassa az `npm install powerbi-visuals-utils-<UTILNAME> --save` parancsot (például: `npm install powerbi-visuals-utils-dataviewutils --save`), hogy megkapja az új verziót külső TypeScript-modulokkal.

Erre a MekkoChart [adattárban](https://github.com/Microsoft/powerbi-visuals-mekkochart) talál példát.
Ez a vizualizáció az összes segédprogramot használja.

## <a name="remove-globalizejs-library"></a>A Globalize.js kódtár eltávolítása

A [powerbi-visuals-utils-formattingutils@4.3](https://www.npmjs.com/package/powerbi-visuals-utils-formattingutils) új verziója eleve tartalmazza a globalize.js-t.
Ezt a kódtárat nem kell manuálisan belefoglalni a projektbe.
Minden szükséges honosítás automatikusan hozzá lesz adva a végleges csomaghoz.

## <a name="fix-loading-external-libraries"></a>Külső kódtárak betöltésének javítása

A kódtárak után foglaljon be új JS-fájlt a `pbiviz.json` fájl `externalJS` tömbjében. Például:

```JSON
"externalJS": [
    ...
    "node_modules/lodash/lodash.min.js",
    "externalJS/init.lodash.js",
    ...
]
```

Importálja a forrásbeli kódtárakat. Például a `lodash-es` esetében:

```JS
import * as _ from "lodash-es";
```

ahol `_` a `lodash` kódtárhoz tartozó globális változó.

## <a name="changes-in-the-visuals-sources"></a>A vizualizációk forrásának változásai

A legjelentősebb változás a belső modulok külsőkké konvertálása, ugyanis külső modul nem használható belső modulon belül.

Ezek a változások a SampleBarChart-mintán elvégzett módosításoknak felelnek meg.

A változások részletes leírása a következő:

1. A [forráskód](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L153) minden fájljából távolítsa el a moduldefiníciókat

    ```typescript
    module powerbi.extensibility.visual {
        ...
    }
    ```

2. [Importálja a Power BI egyéni vizualizációs API-definíciókat](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L2).

    ```typescript
    import powerbi from "powerbi-visuals-api";
    ```

3. [Importálja](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L12-L23) a szükséges interfészeket vagy osztályokat a `powerbi` belső modulból.

    ```typescript
    import PrimitiveValue = powerbi.PrimitiveValue; 
    import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions; 
    import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions; 
    import IVisualHost = powerbi.extensibility.visual.IVisualHost; 
    import IColorPalette = powerbi.extensibility.IColorPalette; 
    import IVisual = powerbi.extensibility.visual.IVisual; 
    import VisualObjectInstance = powerbi.VisualObjectInstance; 
    import VisualObjectInstanceEnumeration = powerbi.VisualObjectInstanceEnumeration; 
    import EnumerateVisualObjectInstancesOptions = powerbi.EnumerateVisualObjectInstancesOptions; 
    import Fill = powerbi.Fill; 
    import VisualTooltipDataItem = powerbi.extensibility.VisualTooltipDataItem; 
    import ISelectionManager = powerbi.extensibility.ISelectionManager; 
    ```

4. [Importálja](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L1) a D3.js kódtárat

    ```typescript
    import * as d3 from "d3";
    ```

    Azt is megteheti, hogy csak a D3 kódtár szükséges moduljait importálja

    ```typescript
    import { max, min } from "d3-array";
    ```

5. [Importálja](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L4-L10) a vizualizáció-projektben definiált segédprogramokat, osztályokat és interfészeket a fő forráskódba

    ```typescript
    import { getLocalizedString } from "./localization/localizationHelper";
    import { getValue, getCategoricalObjectValue } from "./objectEnumerationUtility";
    import {
        ITooltipServiceWrapper,
        TooltipEventArgs,
        createTooltipServiceWrapper
    } from "./tooltipServiceWrapper";
    ```

### <a name="import-css-styles"></a>CSS-stílusok importálása

Az eszközök új verzióival a fejlesztők közvetlenül a TypeScript-kódba importálhatnak CSS-, LESS-stílust.

A korábban használt [stílusdefiníciós szakaszt](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/pbiviz.json#L22) a fordító figyelmen kívül hagyja.

Saját stíluslap használatához nyissa meg a fő TypeScript-fájlt, és szúrja be a következő sort:  

```typescript
import "./../style/visual.less";
```  

A CSS és LESS stílusok automatikusan le lesznek fordítva.  

### <a name="externaljs-section-in-pbivizjson"></a>externalJS szakasz a pbiviz.json fájlban

Az eszközök [nem igénylik](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/pbiviz.json#L20) `externalJS`-lista betöltését a vizualizáció-csomagba. A Webpack ugyanis minden importált kódtárat belefoglal.

**A pbiviz.json externalJS szakaszának üresnek kell lennie.**

Használja a szokásos `npm run package` parancsot a vizualizáció-csomag létrehozásához, vagy az `npm run start` parancsot dev-server indításához.

## <a name="updating-d3js-library-to-version-5"></a>A D3.js kódtár 5-ös verzióra frissítése

Az új eszközökkel használatba veheti a D3.js kódtár új verzióját.

A D3 az alábbi parancsokkal frissíthető a vizualizáció-projektben

`npm install --save d3@5` az új D3.js telepítéséhez.

`npm install --save-dev @types/d3@5` a D3.js új típusdefinícióinak telepítéséhez.

Egyes változások megtörik a kompatibilitást, ezért a kódot módosítania kell az új D3-js használatára.

1. A `d3.Selection<T>` interfész a következőre [módosult](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR157): `Selection<GElement extends BaseType, Datum, PElement extends BaseType, PDatum>`

2. Nem alkalmazhat több attribútumot az `attr` metódus egyetlen hívásával. Minden attribútumot az `attr` metódus külön hívásával [kell átadnia](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR278). [Ugyanez](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR247) érvényes a `style` metódusra is.

3. A D3.js v4-ben lett bevezetve az új merge metódus. Ezt a metódust gyakran használják kijelölések bevitelének és frissítésének egyesítésére adatok összekapcsolása után. A D3 megfelelő használatához [hívja meg a merge metódust](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/83fe8d52d362dccd0034dd8e32c94080d9376b29#diff-433142f7814fee940a0ffc98dc75bfcbR272).

[További tudnivalók](https://github.com/d3/d3/blob/master/CHANGES.md) a D3.js kódtár változásairól.

## <a name="babel"></a>Babel

A 3.1-es verziótól kezdődően az eszközök a Babel használatával fordítják a modern JS-kódot a régi ES5-re, a sokféle böngésző támogatása érdekében.

Ez a beállítás alapértelmezés szerint engedélyezve van, de a [`@babel/polyfill`](https://babeljs.io/docs/en/babel-polyfill) csomagot manuálisan kell importálnia.

Telepítse a csomag a következő paranccsal

`npm install --save @babel/polyfill`

majd importálja a csomagot a vizualizáció kódjának kezdőpontján (általában az „SRC/visual.ts” fájlban):

`import "@babel/polyfill";`

A Babellel kapcsolatos további információk [a dokumentációban](https://babeljs.io/docs/en/).

Végül a [webpack-visualizer](https://github.com/chrisbateman/webpack-visualizer) futtatásával jelenítse meg a vizualizáció kódbázisát.  

![Vizualizáció kódjának statisztikája](./media/webpack-stats.png)
