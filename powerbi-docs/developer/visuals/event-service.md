---
title: Események renderelése
description: A Power BI vizualizációi értesíthetik a Power BI-t arról, hogy készen állnak a PowerPointba vagy PDF-be való exportálásra
author: Yarovinsky
ms.author: alexyar
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 46166b3503a770e033b98474fcf9240235296cc2
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425091"
---
# <a name="event-service"></a>Eseményszolgáltatás

Az új API három metódusból áll (elindítva, befejezve vagy sikertelen), amelyet a renderelés során kell meghívni.

A renderelés indításakor az egyéni vizualizációs kódja meghívja a renderingStarted metódust, amely jelzi, hogy a renderelési folyamat elindult.

Ha a renderelés sikeres volt, az egyéni vizualizáció kódja azonnal meghívja a `renderingFinished` metódust, amely értesíti a figyelőket (**elsősorban az „Exportálás PDF-be” és az „Exportálás PowerPointba”** figyelőt), hogy a vizualizáció képe készen áll.

Ha a renderelés során hiba történik, az meggátolja, hogy az egyéni vizualizáció sikeresen végbemenjen. Az egyéni vizualizáció kódja ekkor meghívja a `renderingFailed` metódust, amely értesíti a figyelőt arról, hogy a renderelési folyamat nem fejeződött be. Ez a metódus emellett egy választható sztringet is nyújt a hiba okáról.

## <a name="usage"></a>Használat

```typescript
export interface IVisualHost extends extensibility.IVisualHost {
    eventService: IVisualEventService ;
}

/**
 * An interface for reporting rendering events
 */
export interface IVisualEventService {
    /**
     * Should be called just before the actual rendering was started. 
     * Usually at the very start of the update method.
     *
     * @param options - the visual update options received as update parameter
     */
    renderingStarted(options: VisualUpdateOptions): void;

    /**
     * Shoudl be called immediately after finishing successfull rendering.
     * 
     * @param options - the visual update options received as update parameter
     */
    renderingFinished(options: VisualUpdateOptions): void;

    /**
     * Called when rendering failed with optional reason string
     * 
     * @param options - the visual update options received as update parameter
     * @param reason - the option failure reason string
     */
    renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```

### <a name="simple-sample-the-visual-hasnt-any-animations-on-rendering"></a>Egyszerű minta. A vizualizáció nem rendelkezik renderelendő animációkkal

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            this.events.renderingFinished(options);
        }
```

### <a name="sample-the-visual-with-animation"></a>Minta. A vizualizáció animációval

Ha a vizualizációban animációval vagy aszinkron renderelési függvényekkel bír, a `renderingFinished` metódust kell meghíni az animáció után vagy az aszinkron függvényben.

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        private element: HTMLElement;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            this.element = options.element;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            // read more https://github.com/d3/d3-transition/blob/master/README.md#transition_end
            d3.select(this.element).transition().duration(100).style("opacity","0").end().then(() => {
                // renderingFinished called after transition end
                this.events.renderingFinished(options);
            });
        }
```

## <a name="rendering-events-for-visual-certification"></a>Események renderelése a vizualizáció minősítéséhez

A vizualizációk minősítésének egyik követelménye az események renderelésének támogatása. További információ a [minősítési követelményekről](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements)
