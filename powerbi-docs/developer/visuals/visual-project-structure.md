---
title: A Power BI-vizualizáció projekt szerkezete
description: A cikk a vizualizációs projektek szerkezetét ismerteti
author: zBritva
ms.author: v-ilgali
ms.reviewer: ''
ms.service: powerbi
ms.topic: tutorial
ms.subservice: powerbi-custom-visuals
ms.date: 03/15/2019
ms.openlocfilehash: 728aba749f80710fdc0bb1e180b3318e63caa88c
ms.sourcegitcommit: 331ebf6bcb4a5cdbdc82e81a538144a00ec935d4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/28/2019
ms.locfileid: "75542093"
---
# <a name="power-bi-visual-project-structure"></a>A Power BI-vizualizáció projekt szerkezete

A pbiviz new `<visual project name>` parancs végrehajtása után az eszköz létrehozza a mappák és fájlok alapvető struktúráját a(z) `<visual project name>` mappában.

## <a name="visual-project-structure"></a>Vizualizációs projekt szerkezete

![Vizualizációs projekt szerkezete](./media/visual-project-structure.png)

* `.vscode` – a projekt beállításait tartalmazza a VS Code számára. A munkaterület a `.vscode/settings.json` fájl szerkesztésével konfigurálható. [A VS Code beállításairól a dokumentációban](https://code.visualstudio.com/docs/getstarted/settings) olvashat.

* Az `assets` mappa csak az `icon.png` fájlt tartalmazza. Az eszköz ezt a fájlt használja a vizualizáció ikonjaként a Power BI Vizualizációk paneljén.

    ![A Vizualizációk panel](./media/visualization-pane-analytics-tab.png)

* A `node_modules` mappa tartalmazza [a Node Package Manager által telepített](https://docs.npmjs.com/files/folders.html) összes csomagot.

* Az `src` mappa a vizualizáció forráskódját tartalmazza. Az eszköz alapértelmezés szerint két fájlt hoz létre:

  * `visual.ts` – a vizualizáció fő forráskódja.

  * `settings.ts` – a vizualizáció beállításainak kódja. A fájlbeli osztályok egyszerűbbé teszik a [vizualizáció tulajdonságaival végzett munkát](./objects-properties.md#properties).

* A `style` mappa a `visual.less` fájlt tartalmazza a vizualizációhoz tartozó stílusokkal.

* A `capabilities.json` fájl a vizualizáció fő tulajdonságait is beállításait tartalmazza. Ezt teszi lehetővé a vizualizáció számára a támogatott funkciók, objektumok, tulajdonságok és adatnézet-leképezések deklarálását.

    [A képességekről a dokumentációban](./capabilities.md) olvashat.

* A `package-lock.json` fájl automatikusan lesz generálva minden olyan művelethez, amelyben az NPM a `node_modules` fát vagy a `package.json` fájlt módosítja.

    [A `package-lock.json` fájlról az NPM hivatalos dokumentációjában](https://docs.npmjs.com/files/package-lock.json) talál további információt.

* A `package.json` fájl a projektcsomagot írja le. Általában a projektről, annak készítőiről, leírásáról és függőségeiről tartalmaz információkat.

    [A `package.json` fájlról az NPM hivatalos dokumentációjában](https://docs.npmjs.com/files/package.json.html) talál további információt.

* A `pbiviz.json` fájl a vizualizáció metaadatait tartalmazza. A vizualizáció metaadatai ebben a fájlban adhatók meg.

    A fájl jellemző tartalma a következő:

  ```json
    {
        "visual": {
            "name": "<visual project name>",
            "displayName": "<visual project name>",
            "guid": "<visual project name>23D8B823CF134D3AA7CC0A5D63B20B7F",
            "visualClassName": "Visual",
            "version": "1.0.0",
            "description": "",
            "supportUrl": "",
            "gitHubUrl": ""
        },
        "apiVersion": "2.6.0",
        "author": { "name": "", "email": "" },
        "assets": { "icon": "assets/icon.png" },
        "externalJS": null,
        "style": "style/visual.less",
        "capabilities": "capabilities.json",
        "dependencies": null,
        "stringResources": []
    }
  ```

    Ebben a kódban:

  * `name` – a vizualizáció belső neve.

  * `displayName` – a vizualizáció megnevezése a Power BI felhasználói felületén.

  * `guid` – a vizualizáció egyedi azonosítója.

  * `visualClassName` – a vizualizáció fő osztályának neve. A Power BI ennek az osztálynak egy példányát hozza létre a vizualizáció Power BI jelentésben történő használatának megkezdéséhez.

  * `version` – a vizualizáció verziószáma.

  * `author` – a készítő nevét és kapcsolattartási e-mail-címét tartalmazza.

  * az `assets` elemen belüli `icon` – a vizualizáció ikonfájljának elérési útja.

  * `externalJS` – a vizualizációban használt JS-kódtárak elérési útjait tartalmazza.

    > [!IMPORTANT]
    > Az eszköz legfrissebb, 3.x.x vagy annál újabb verziói már nem használják az `externalJS`-t.

  * `style` – a stílusfájlok elérési útja.

  * `capabilities` – a `capabilities.json` fájl elérési útja.

  * `dependencies` – a `dependencies.json` fájl elérési útja. `dependencies.json` – az R-alapú vizualizációkban használt R-csomagokkal kapcsolatos információkat tartalmaz.

  * `stringResources` – honosítási fájlok elérési útjait tartalmazó tömb.

  [A vizualizációk nyelvi beállításairól a dokumentációban](./localization.md) talál további információt.

* `tsconfig.json` – konfigurációs fájl a TypeScripthez.

    [A TypeScript konfigurálásáról a hivatalos dokumentációban](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) talál további információt.

    A `files` szakaszban lévő `tsconfig.json` fájlnak tartalmaznia annak a *.ts fájlnak az elérési útját, ahol a vizualizáció fő osztálya megtalálható a `pbiviz.json` fájlban, a `visualClassName` tulajdonság által megadott helyen.

* A `tslint.json` fájl a TSLint-konfigurációt tartalmazza.

    [A TSLint konfigurálásáról a hivatalos dokumentációban](https://palantir.github.io/tslint/usage/configuration/) talál további információt.

## <a name="next-steps"></a>Következő lépések

* A [vizualizáció fogalmáról](./power-bi-visuals-concept.md) bővebben is tájékozódhat, hogy jobban megismerje a vizualizáció, a felhasználó és a Power BI közötti együttműködést.

* Saját, teljesen új Power BI-vizualizációk fejlesztést kezdheti meg egy [lépésenkénti útmutató](./custom-visual-develop-tutorial.md) segítségével.
