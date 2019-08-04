---
title: Kezdőlap
description: Kezdőlap hozzáadása Power BI-vizualizációkhoz
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 44cc9314b31803c97d3203d4aab846685d8f88fa
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424884"
---
# <a name="landing-page"></a>Kezdőlap

Az API 2.3.0-val kezdőlapot adhat a vizualizációihoz. Ehhez adja hozzá a `supportsLandingPage` elemet a funkciókhoz, majd állítsa igazra. A vizualizáció így már azelőtt elindul és frissül, hogy adatokat adna hozzá (azaz nem jelenít meg vízjelet), Ön pedig megtervezheti, hogyan nézzen ki saját kezdőlapja, amíg a vizualizáció nem tartalmaz adatokat.

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

Minta

![képernyőkép a kezdőlapról](./media/landing-page.png)
