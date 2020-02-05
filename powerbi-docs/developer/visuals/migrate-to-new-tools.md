---
title: Migrálás a powerbi-visuals-tools 3.x verziójára
description: A powerbi-visuals-tools új verziója használatának első lépései
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: d9af0ab870732990201ab3478d71fdafa9e13439
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/04/2020
ms.locfileid: "76818824"
---
# <a name="migrate-to-the-new-powerbi-visuals-tools-version-3x"></a>Migrálás a powerbi-visuals-tools új 3.*x* verziójára

A 3-as verziótól kezdődően a Power BI Visuals Tools (powerbi-visuals-tools vagy `pbiviz`) a Webpack használatával készít egyéni vizualizációkat.
Az új verzió számos fejlesztést kínál a fejlesztőknek vizualizációk létrehozásához:

- Alapértelmezés szerint a TypeScript 3.*x* verzióját használja. A TypeScript 1.5-től kezdődően megváltozott az elnevezések rendszere. [További tudnivalók a TypeScript-modulokról](https://www.typescriptlang.org/docs/handbook/modules.html).

- Támogatottak az ECMAScript 6- (ES6-) modulok. A rendszer mostantól ES6-importálásokat használ az [externalJS](migrate-to-new-tools.md#configure-loading-of-external-libraries) helyett.

- Támogatottak a Data-Driven Documents ([D3v5](https://d3js.org/)) és más ES6-modulokon alapuló kódtárak új verziói.

- Kisebb csomagméret. A Webpack a [Tree Shaking](https://webpack.js.org/guides/tree-shaking/) módszerrel távolítja el a nem használt kódot. Ez csökkenti a JavaScript-kód mennyiségét, és jobb teljesítményt nyújt a vizualizációk betöltésekor.

- Jobb API-teljesítmény.

- A Globalize.js kódtár [integrálva van](migrate-to-new-tools.md#remove-the- globalizejs-library) a FormattingUtils csomagba.

- A Power BI Visuals Tools a [webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) használatával jeleníti meg a vizualizáció kódbázisát.

A cikk a Power BI Visuals Tools új verziójára való migrálás valamennyi lépését ismerteti.

## <a name="backward-compatibility"></a>Kompatibilitás az előző verziókkal

Az új eszközök megtartják a régi vizualizációk kódbázisának visszamenőleges kompatibilitási adatait, de további módosításokat igényelhetnek külső kódtárak betöltéséhez.

A modulrendszereket támogató kódtárakat Webpack-csomagokként importálja a rendszer. A vizualizáció minden más kódtára és forráskódja egyetlen modulba van becsomagolva.

A korábbi Power BI Visuals Tools eszközökben használt olyan globális változók, mint a JQuery és a Lodash, már elavultak. Ha a vizualizáció régi kódja globális változókra támaszkodik, a vizualizáció valószínűleg nem fog működni az új eszközökkel.

A Power BI Visuals Tools előző verziójához definiálnia kellett egy vizualizációosztályt a `powerbi.extensibility.visual` modulban. Az eszközök új verziójában ehelyett a fő TypeScript- (.ts) fájlban kell definiálnia egy vizualizációosztályt. Ez a fájl általában az `src/visual.ts`.

## <a name="install-powerbi-visuals-tools"></a>A powerbi-visuals-tools telepítése

Az új eszközök telepítéséhez futtassa a következő parancsot:

```cmd
npm install -g powerbi-visuals-tools
```

A következő kód a [sampleBarChart vizualizációs adattár](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/package.json#L15) `package.json` fájljából származik, a vizualizációs projekt az új eszközök használatára való frissítése után:

```json
{
    "name": "visual",
    "version": "3.0.0",
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "package": "pbiviz package",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "test": "pbiviz package --resources --no-minify --no-pbiviz"
    },
    "devDependencies": {
        "@types/d3": "5.7.2",
        "d3": "5.12.0",
        "powerbi-visuals-api": "^2.6.1",
        "powerbi-visuals-tools": "^3.1.7",
        "powerbi-visuals-utils-dataviewutils": "^2.2.1",
        "powerbi-visuals-utils-formattingutils": "^4.4.2",
        "powerbi-visuals-utils-interactivityutils": "^5.6.0",
        "powerbi-visuals-utils-tooltiputils": "^2.3.1",
        "tslint": "^5.20.0",
        "tslint-microsoft-contrib": "^6.2.0"
    }
}
```

## <a name="install-the-power-bi-custom-visuals-api"></a>A Power BI Custom Visuals API telepítése

A powerbi-visuals-tools új verziója nem tartalmaz minden API-verziót. Ehelyett a [powerbi-visuals-api](https://www.npmjs.com/package/powerbi-visuals-api) csomag egy konkrét verzióját kell telepítenie. Válassza ki a csomag az egyéni Power BI-vizualizációk API-verziójának megfelelő verzióját. A csomag a Power BI Custom Visuals API összes típusdefinícióját tartalmazza.

A következő parancs futtatásával adja hozzá a `powerbi-visuals-api` API-t egy projekt projektfüggőségeihez:

```cmd
npm install --save-dev powerbi-visuals-api
```

Emellett távolítsa el a régi API típusdefinícióinak minden hivatkozását, mert a Webpack automatikusan a `powerbi-visuals-api` API-ból foglalja bele a típusokat. A megfelelő módosítások a [package.json](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/package.json#L14) és a [tsconfig.json](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/tsconfig.json#L14) fájlban találhatók.

## <a name="update-tsconfigjson"></a>A tsconfig.json frissítése

Külső modulok használatához módosítsa az `out` értéket az `outDir` értékre. Használja például az `"outDir": "./.tmp/build/",` értéket az `"out": "./.tmp/build/visual.js",` érték helyett.

Ez a módosítás azért szükséges, mert a rendszer egymástól függetlenül fordítja le a TypeScript-fájlokat JavaScript-fájlokká. Ezért nem kell többé a visual.js fájlt megadni kimenetként.

A `target` beállítást is az `ES6` értékre módosíthatja, ha modern JavaScript-kimenetet szeretne használni. Ez a módosítás [nem kötelező](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/tsconfig.json#L7).

## <a name="update-custom-visuals-utilities"></a>Egyéni vizualizációs segédprogramok frissítése

Ha bármelyiket haználja a [powerbi-visuals-utils](https://www.npmjs.com/search?q=powerbi-visuals-utils) csomagjai közül, akkor ezeket is érdemes a legújabb verzióra frissíteni. Ehhez futtassa a következő parancsot:

```cmd
npm install powerbi-visuals-utils-<UTILNAME> --save
```

Az új verzió külső TypeScript-modulokkal való beszerzéséhez például futtassa a következőt: 

```cmd
npm install powerbi-visuals-utils-dataviewutils --save
```

A [MekkoChart adattárban](https://github.com/Microsoft/powerbi-visuals-mekkochart) találhat példát olyan vizualizációra, amely a `powerbi-visuals-utils` összes csomagját használja.

## <a name="remove-the-globalizejs-library"></a>A Globalize.js kódtár eltávolítása

A [powerbi-visuals-utils-formattingutils@4.3](https://www.npmjs.com/package/powerbi-visuals-utils-formattingutils) új verziója tartalmazza a Globalize.js kódtárat. Így ezt a kódtárat nem kell manuálisan belefoglalni a projektbe. Minden szükséges honosítás automatikusan hozzá lesz adva a végleges csomaghoz.

## <a name="configure-loading-of-external-libraries"></a>A külső kódtárak betöltésének konfigurálása

Új JavaScript-fájlok hozzáadása a `pbiviz.json` `externalJS` tömbjében lévő kódtárak után. Például:

```JSON
"externalJS": [
    ...
    "node_modules/lodash/lodash.min.js",
    "externalJS/init.lodash.js",
    ...
]
```

Importálja a kódtárakat a forráskódban. A `lodash-es` kódtárhoz például használja az alábbi utasítást:

```JS
import * as _ from "lodash-es";
```

Az előző példában az `_` a `lodash` kódtár globális változója.

## <a name="make-changes-in-the-sources-of-your-visuals"></a>A vizualizációk forrásainak módosítása

A fő módosítás, amelyet el kell végeznie, az a belső modulok külső modulokká való konvertálása. Külső modulok nem használhatók belső modulokban.

Az elvégzendő módosítások részletes leírása az alábbiakban látható. A módosításokat a Sávdiagram egyéni vizualizációs kódmintája kontextusában ismertetjük:

1. A [forráskód](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbL1-L3) minden fájljából távolítsa el a moduldefiníciókat:

    ```typescript
    module powerbi.extensibility.visual {
        ...
    }
    ```

2. [Importálja a Power BI egyéni vizualizációs API-jának definícióit](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR4):

    ```typescript
    import powerbi from "powerbi-visuals-api";
    ```

3. [Importálja a szükséges interfészeket vagy osztályokat](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR12-R35) a `powerbi` belső modulból.

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

4. [Importálja a D3.js kódtárat](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR2):

    ```typescript
    import * as d3 from "d3";
    ```

    Azt is megteheti, hogy csak a D3 kódtár szükséges moduljait importálja:

    ```typescript
    import { max, min } from "d3-array";
    ```

5. [Importálja a vizualizációs projektben definiált segédprogramokat, osztályokat és interfészeket](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR38-R41) a forráskód fő fájljába:

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

Az eszközök új verzióival a közvetlenül a TypeScript-kódba importálhat `CSS`- és `Less`-stílusokat. A fordító most már figyelmen kívül hagyja a korábban használt [stílusszakaszt](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/pbiviz.json#L21).

Saját stíluslap használatához nyissa meg a fő TypeScript- (.ts) fájlt, és szúrja be a következő sort:  

```typescript
import "./../style/visual.less";
```  

A `CSS`- és `Less`-stílusok automatikusan le lesznek fordítva.

### <a name="externaljs-section-in-pbivizjson"></a>externalJS szakasz a pbiviz.json fájlban

Az eszközöknek [nincs szükségük a vizualizációs csomagba betöltendő `externalJS`-kódtárak](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-a1a7bbee7e7d2f9d449f4b534532bcf2R20) listájára, mert a Webpack minden importált kódtárat tartalmaz.

> [!NOTE]
> A `pbiviz.json` fájlban hagyja üresen a `externalJS` szakaszt.

A szokásos `npm run package` paranccsal hozhatja létre a vizualizációs csomagot, és az `npm run start` paranccsal indíthatja el a fejlesztői kiszolgálót.

## <a name="update-the-d3js-library-to-version-5"></a>A D3.js kódtár frissítése az 5-ös verzióra

Az új vizualizációs eszközökkel használatba veheti a D3.js kódtár új verzióját. Futtassa az alábbi parancsokat a D3 a vizualizációs projektben való frissítéséhez:

- `npm install --save d3@5` az új D3.js telepítéséhez.

- `npm install --save-dev @types/d3@5` a D3.js új típusdefinícióinak telepítéséhez.

> [!IMPORTANT]
> A D3 5-ös verziójában számos kompatibilitástörő változás jelenik meg.

Módosítsa a kódot úgy, hogy az működjön az új D3.js használatával:

- A `d3.Selection<T>` interfész a következőre [módosult](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR157): `Selection<GElement extends BaseType, Datum, PElement extends BaseType, PDatum>`.

- Nem alkalmazhat több attribútumot az `attr` metódus egyetlen hívásával. Ehelyett [minden attribútum átadásához kell meghívnia](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR278) az `attr` metódust. [A `style` metódust is külön kell meghívnia](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR247).

- A D3.js 4-es verziójában jelent meg az új `merge` metódus. Ezt a metódust gyakran használják `enter` és `update` kijelölések egyesítésére adat-összekapcsolási műveletek után. A D3 megfelelő használatához [hívja meg a `merge` metódust](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/83fe8d52d362dccd0034dd8e32c94080d9376b29#diff-433142f7814fee940a0ffc98dc75bfcbR272).

[További tudnivalók](https://github.com/d3/d3/blob/master/CHANGES.md) a D3.js kódtár változásairól.

## <a name="install-babel-and-core-js"></a>A Babel és a core-js telepítése

A 3.1-es verziótól kezdődően a vizualizációs eszközök a Babel használatával fordítják a modern JavaScript-kódot a régi ECMAScript 5-re (ES5-re), a sokféle böngésző támogatása érdekében.

A Babel ezen beállítása alapértelmezés szerint engedélyezve van, de a [`core-js`](https://www.npmjs.com/package/core-js) csomagot manuálisan kell importálnia. Futtassa a következő parancsot a csomag telepítéséhez:

```cmd
npm install --save core-js
```

Ezután importálja a csomagot a vizualizáció kódjának kezdőpontján. Ez általában az src/visual.ts fájl.

```JS
import "core-js/stable";
```

A Babellel kapcsolatos további információk [a dokumentációban](https://babeljs.io/docs/en/).
