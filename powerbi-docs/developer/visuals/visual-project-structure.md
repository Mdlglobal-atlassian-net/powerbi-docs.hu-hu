---
title: A Power BI-vizualizáció projekt szerkezete
description: Ez a cikk egy Power BI-vizualizációs projekt mappa- és fájlszerkezetét ismerteti
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 01/12/2020
ms.openlocfilehash: 16e7a317102602ffb4faf04da0ed2cae588a2a4d
ms.sourcegitcommit: 052df769e6ace7b9848493cde9f618d6a2ae7df9
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/14/2020
ms.locfileid: "75925535"
---
# <a name="power-bi-visual-project-structure"></a>A Power BI-vizualizáció projekt szerkezete

Egy új Power BI-vizualizáció létrehozásának legjobb módja a [pbiviz](https://www.npmjs.com/package/powerbi-visuals-tools) eszköz használata.

Új vizualizáció létrehozásához lépjen arra a könyvtárra, amelyben tárolni szeretné a vizualizációt, majd futtassa a következő parancsot:

`pbiviz new <visual project name>`

A parancs futtatása létrehoz egy Power BI-vizualizációs mappát, amely a következő fájlokat tartalmazza:

```markdown
project
├───.vscode
│   ├───launch.json
│   └───settings.json
├───assets
│   └───icon.png
├───node_modules
├───src
│   ├───settings.ts
│   └───visual.ts
├───style
│   └───visual.less
├───capabilities.json
├───package-lock.json
├───package.json
├───pbiviz.json
├───tsconfig.json
└───tslint.json
```

## <a name="folder-and-file-description"></a>Mappa és fájl leírása

Ez a szakasz a **pbiciz** eszköz által létrehozott könyvtár mappáit és fájljait mutatja be.  

### <a name="vscode"></a>.vscode

Ez a mappa tartalmazza a VS Code-projekt beállításait tartalmazza.

A munkaterület konfigurálásához szerkessze a `.vscode/settings.json` fájlt.

További információ: [Felhasználói és munkaterület-beállítások](https://code.visualstudio.com/docs/getstarted/settings)

### <a name="assets"></a>kapcsolatobjektumok

Ez a mappa tartalmazza az `icon.png` fájlt.

A Power BI-vizualizációs eszköz ezt a fájlt használja új Power BI-vizualizációs ikonként a Power BI vizualizációs paneljén.

<!--- ![Visualization pane](./media/visualization-pane-analytics-tab.png) --->

### <a name="src"></a>src

Ez a mappa tartalmazza a vizualizáció forráskódját.

Ebben a mappában a Power BI-vizualizációs eszköz a következő fájlokat hozza létre:
* `visual.ts` – A vizualizáció fő forráskódja.
* `settings.ts` – A vizualizáció beállításainak kódja. A fájl osztályai definiálják a [vizualizáció tulajdonságait](./objects-properties.md#properties).

### <a name="style"></a>stílus

Ez a mappa tartalmazza a vizualizáció stílusainak tárolására szolgáló `visual.less` fájlt.

### <a name="capabilitiesjson"></a>capabilities.json

A fájl a vizualizáció fő tulajdonságait és beállításait (vagy [funkcióit](./capabilities.md)) tartalmazza. Ez teszi lehetővé a vizualizáció számára a támogatott funkciók, objektumok, tulajdonságok és [adatnézet-leképezések](./dataview-mappings.md) deklarálását.

### <a name="package-lockjson"></a>package-lock.json

A fájl automatikusan létrejön minden olyan művelethez, amelyben az *npm* a `node_modules` fát vagy a `package.json` fájlt módosítja.

További információt a fájlról a hivatalos [npm-package-lock.json](https://docs.npmjs.com/files/package-lock.json) dokumentációban találhat.

### <a name="packagejson"></a>package.json

A fájl a projektcsomagot írja le. A projektről, annak készítőiről, leírásáról és függőségeiről tartalmaz információkat.

További információt a fájlról a hivatalos [npm-package.json](https://docs.npmjs.com/files/package.json.html) dokumentációban találhat.

### <a name="pbivizjson"></a>pbiviz.json

A fájl a vizualizáció metaadatait tartalmazza.

Ha egy metaadat-bejegyzéseket ismertető megjegyzésekkel ellátott `pbiviz.json` mintafájlt szeretne megtekinteni, lépjen a [metaadat-bejegyzések](#metadata-entries) szakaszra.

### <a name="tsconfigjson"></a>tsconfig.json

Konfigurációs fájl a [TypeScripthez](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

A fájlnak tartalmaznia annak a **\*.ts** fájlnak az elérési útját, ahol a vizualizáció fő osztálya megtalálható a `pbiviz.json` fájlban, a `visualClassName` tulajdonság által megadott helyen.

### <a name="tslintjson"></a>tslint.json

A fájl a [TSLint-konfigurációt](https://palantir.github.io/tslint/usage/configuration/) tartalmazza.

## <a name="metadata-entries"></a>Metaadat-bejegyzések

A `pbiviz.json` fájl következő kódrészletében szereplő megjegyzések a metaadat-bejegyzéseket ismertetik.

> [!NOTE]
> * A **pbiciz** eszköz 3.x.x verziójától kezdve az `externalJS` nem támogatott.
> * A honosítási támogatáshoz [adja hozzá a Power BI területi beállítását a vizualizációhoz](./localization.md).

```json
{
  "visual": {
     // The visual's internal name.
    "name": "<visual project name>",

    // The visual's display name.
    "displayName": "<visual project name>",

    // The visual's unique ID.
    "guid": "<visual project name>23D8B823CF134D3AA7CC0A5D63B20B7F",

    // The name of the visual's main class. Power BI creates the instance of this class to start using the visual in a Power BI report.
    "visualClassName": "Visual",

    // The visual's version number.
    "version": "1.0.0",
    
    // The visual's description (optional)
    "description": "",

    // A URL linking to the visual's support page (optional).
    "supportUrl": "",

    // A link to the source code available from GitHub (optional).
    "gitHubUrl": ""
  },
  // The version of the Power BI API the visual is using.
  "apiVersion": "2.6.0",

  // The name of the visual's author and email.
  "author": { "name": "", "email": "" },

  // 'icon' holds the path to the icon file in the assets folder; the visual's display icon.
  "assets": { "icon": "assets/icon.png" },

  // Contains the paths for JS libraries used in the visual.
  // Note: externalJS' isn't used in the Power BI visuals tool version 3.x.x or higher.
  "externalJS": null,

  // The path to the 'visual.less' style file.
  "style": "style/visual.less",

  // The path to the `capabilities.json` file.
  "capabilities": "capabilities.json",

  // The path to the `dependencies.json` file which contains information about R packages used in R based visuals.
  "dependencies": null,

  // An array of paths to files with localizations.
  "stringResources": []
}
```

## <a name="next-steps"></a>Következő lépések

* A vizualizációk, felhasználók és a Power BI közötti interakciók megismeréséhez tekintse meg [A Power BI-vizualizáció működési elve](./power-bi-visuals-concept.md) című cikket.

* Saját, teljesen új Power BI-vizualizációk fejlesztését kezdheti meg egy [lépésenkénti útmutató](./custom-visual-develop-tutorial.md) segítségével.