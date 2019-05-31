---
title: Beágyazott Power BI-tartalommal rendelkező egyéni elrendezések
description: További információ az egyéni elrendezésekről Power BI-tartalmak az alkalmazásba való beágyazása esetén.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 12/19/2017
ms.openlocfilehash: 28d11a30f7998dc63f86b98fd72d18968480e711
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61344174"
---
# <a name="custom-layouts"></a>Egyéni elrendezések

Egyéni elrendezések használatával az eredeti jelentésétől eltérő elrendezésű jelentéseket ágyazhat be. Az új elrendezések definiálása csupán egy oldalméret megadásától a vizualizációk méretének, pozíciójának és láthatóságának szabályozásáig terjedhet.

Egy egyéni elrendezés megadásához definiáljon egy egyéni elrendezési objektumot, és adja át azt a beállítási objektumnak a beágyazás konfigurációjában. Emellett állítsa a LayoutType tulajdonságot a Custom (Egyéni) értékre. További tudnivalókért lásd: [A beágyazási konfiguráció részletei](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details).

```javascript
var embedConfig = {
    ...
    settings: {
            layoutType: models.LayoutType.Custom
    customLayout: {...}
    }
};
```

## <a name="object-definition"></a>Objektumdefiníció

```javascript
interface ICustomLayout {
  pageSize?: IPageSize;
  displayOption?: DisplayOption;
  pagesLayout?: PagesLayout;
}

enum PageSizeType {
  Widescreen,
  Standard,
  Cortana,
  Letter,
  Custom
}
interface IPageSize {
  type: PageSizeType;
}
interface ICustomPageSize extends IPageSize {
  width?: number;
  height?: number;
}

enum DisplayOption {
  FitToPage,
  FitToWidth,
  ActualSize
}
```

- `pageSize`: Az oldalmérettel szabályozhatja a vászonterület (azaz a jelentés fehér területének) méretét.
- `displayOptions`: Lehetséges értékek: FitToWidth (Szélességhez igazítás), FitToPage (Laphoz igazítás) vagy ActualSize (Tényleges méret). Azt szabályozza, hogy a rendszer hogyan méretezze a vásznat, hogy az illeszkedjen az IFrame elembe.
- `pagesLayout`: Az egyes vizualizációk elrendezését szabályozza. További információért lásd a PagesLayout objektumot.

## <a name="pages-layout"></a>Lapok elrendezése

A lapok elrendezési objektumának definiálása alapvetően azt jelenti, hogy minden egyes laphoz, és az egyes lapokon minden egyes vizualizációhoz definiál egy elrendezést.
A lapelrendezés megadása nem kötelező. Ha egy laphoz nem ad meg elrendezést, a rendszer (a jelentésben mentett) alapértelmezett elrendezést alkalmazza rá.

A PagesLayout objektum a lapnevek PageLayout objektumokhoz való hozzárendelése. Definíció:

```javascript
type PagesLayout = { [key: string]: IPageLayout; };
```

A PageLayout objektum a vizualizációk elrendezésének leképezése, amely minden egyes vizualizáció nevét egy vizualizációelrendezési objektumhoz rendeli hozzá:

```javascript
interface IPageLayout {
  visualsLayout: { [key: string]: IVisualLayout; };
}
```

## <a name="visual-layout"></a>Vizualizációelrendezés

Egy vizualizáció elrendezésének definiálásához egy új pozíciót és méretét, illetve egy új láthatósági állapotot kell átadnia.

```javascript
interface IVisualLayout {
  x?: number;
  y?: number;
  z?: number;
  width?: number;
  height?: number;
  displayState?: IVisualContainerDisplayState;
}

interface IVisualContainerDisplayState {
  mode: VisualContainerDisplayMode;
}

enum VisualContainerDisplayMode {
  Visible,
  Hidden
}
```

- `x,y,z`: A vizualizáció új pozícióját határozza meg.
- `width`, magasság: A vizualizáció új méretét határozza meg.
- `displayState`: Azt határozza meg, hogy a vizualizáció látható-e.

## <a name="update-layout"></a>Elrendezés frissítése

Az updateSettings metódussal bármikor frissítheti egy jelentés elrendezését a jelentés betöltése közben. Lásd: [Beállítások frissítése](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Update-Settings).

## <a name="code-example"></a>Példakód

```javascript
// Get models. models contains enums that can be used.
var models = window['powerbi-client'].models;

var embedConfiguration = {
    type: 'report',
    id: '5dac7a4a-4452-46b3-99f6-a25915e0fe55',
    embedUrl: 'https://app.powerbi.com/reportEmbed',
    tokenType: models.TokenType.Embed,
    accessToken: 'H4...rf',
    settings: {
            layoutType: models.LayoutType.Custom
        customLayout: {
            pageSize: {
                type: models.PageSizeType.Custom,
                width: 1600,
                height: 1200
            },
            displayOption: models.DisplayOption.ActualSize,
            pagesLayout: {
                "ReportSection1" : {
                    visualsLayout: {
                        "VisualContainer1": {
                            x: 1,
                            y: 1,
                            z: 1,
                            width: 400,
                            height: 300,
                            displayState: {
                                mode: models.VisualContainerDisplayMode.Visible
                            }
                        },
                        "VisualContainer2": {
                            displayState: {
                                mode: models.VisualContainerDisplayMode.Hidden
                            }
                        },
                    }
                }
            }
        }
    }
};

// Get a reference to the embedded report HTML element
var embedContainer = document.getElementById('embedContainer');

// Embed the report and display it within the div container.
var report = powerbi.embed(embedContainer, embedConfiguration);
```

## <a name="see-also"></a>Lásd még:

[Power BI-irányítópultok, -jelentések és -csempék beágyazása](embedding-content.md)   
[Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)