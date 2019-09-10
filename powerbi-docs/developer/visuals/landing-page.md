---
title: Kezdőlap hozzáadása Power BI-vizualizációkhoz
description: Ez a cikk azt ismerteti, hogy hogyan adhat kezdőlapot a Power BI-vizualizációkhoz.
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: d15c52134fe3c8638625e50a1374867a4abed3c1
ms.sourcegitcommit: b602cdffa80653bc24123726d1d7f1afbd93d77c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/03/2019
ms.locfileid: "70236708"
---
# <a name="add-a-landing-page-to-your-power-bi-visuals"></a>Kezdőlap hozzáadása Power BI-vizualizációkhoz

Az API 2.3.0-val kezdőlapot adhat a Power BI-vizualizációkhoz. Ehhez adja hozzá a `supportsLandingPage` elemet a funkciókhoz, majd állítsa igaz értékre. Ez a művelet inicializálja és frissíti a vizualizációt, mielőtt Ön adatokat adna hozzá. Mivel a vizualizáció már nem jelenít meg vízjelet, saját kezdőlapot tervezhet, amely az adatokat nem tartalmazó vizualizáción jelenik meg.

```typescript
export class BarChart implements IVisual {
    //...
    private element: HTMLElement;
    private isLandingPageOn: boolean;
    private LandingPageRemoved: boolean;
    private LandingPage: d3.Selection<any>;

    constructor(options: VisualConstructorOptions) {
            //...
            this.element = options.element;
            //...
    }

    public update(options: VisualUpdateOptions) {
    //...
        this.HandleLandingPage(options);
    }

    private HandleLandingPage(options: VisualUpdateOptions) {
        if(!options.dataViews || !options.dataViews.length) {
            if(!this.isLandingPageOn) {
                this.isLandingPageOn = true;
                const SampleLandingPage: Element = this.createSampleLandingPage(); //create a landing page
                this.element.appendChild(SampleLandingPage);
                this.LandingPage = d3.select(SampleLandingPage);
            }

        } else {
                if(this.isLandingPageOn && !this.LandingPageRemoved){
                    this.LandingPageRemoved = true;
                    this.LandingPage.remove();
                }
        }
    }
```

A következő képen egy példát láthat a kezdőlapra:

![képernyőkép a kezdőlapról](./media/landing-page.png)
