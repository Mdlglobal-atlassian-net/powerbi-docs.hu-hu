---
title: Renderelési események Power BI-vizualizációkban
description: A Power BI-vizualizációk értesíthetik a Power BI-t arról, hogy készek a PowerPointba vagy PDF-fájlba exportálásra.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: c54aaa92f3463ce1102866c8d3b69532c8b25cf7
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "79380249"
---
# <a name="render-events-in-power-bi-visuals"></a>Renderelési események Power BI-vizualizációkban

Az új API három olyan metódusból áll (`started`, `finished` vagy `failed`), amelyeket a renderelés során kell meghívni.

A renderelés indításakor a Power BI-vizualizáció kódja meghívja a `renderingStarted` metódust, amely jelzi, hogy a renderelési folyamat elindult.

Ha a renderelés sikeres volt, a Power BI-vizualizáció kódja azonnal meghívja a `renderingFinished` metódust, amely értesíti a figyelőket (elsősorban az *Exportálás PDF-be* és az *Exportálás PowerPointba* figyelőt), hogy a vizualizáció képe exportálásra kész.

Ha a folyamat közben probléma lép fel, a Power BI-vizualizáció sikeres renderelése meghiúsul. A Power BI-vizualizáció kódjának ekkor a `renderingFailed` metódus hívásával kell értesítenie a figyelőket arról, hogy a renderelési folyamat nem fejeződött be. Ez a metódus emellett választhatóan egy sztringet is visszaadhat, amely a hiba okáról nyújt tájékoztatást.

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
     * Should be called just before the actual rendering starts, 
     * usually at the start of the update method
     *
     * @param options - the visual update options received as an update parameter
     */
    renderingStarted(options: VisualUpdateOptions): void;

    /**
     * Should be called immediately after rendering finishes successfully
     * 
     * @param options - the visual update options received as an update parameter
     */
    renderingFinished(options: VisualUpdateOptions): void;

    /**
     * Called when rendering fails, with an optional reason string
     * 
     * @param options - the visual update options received as an update parameter
     * @param reason - the optional failure reason string
     */
    renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```

### <a name="sample-the-visual-displays-no-animations"></a>Minta: A vizualizáció nem jelenít meg animációt

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

### <a name="sample-the-visual-displays-animations"></a>Minta: A vizualizáció animációkat jelenít meg

Ha a vizualizáció animációkat vagy aszinkron renderelési függvényeket tartalmaz, a `renderingFinished` metódust az animáció után vagy az aszinkron függvényen belül kell meghíni.

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
            // Learn more at https://github.com/d3/d3-transition/blob/master/README.md#transition_end
            d3.select(this.element).transition().duration(100).style("opacity","0").end().then(() => {
                // renderingFinished called after transition end
                this.events.renderingFinished(options);
            });
        }
```

## <a name="rendering-events-for-visual-certification"></a>Események renderelése a vizualizáció minősítéséhez

A vizualizációk minősítésének egyik követelménye a renderelési eseményeknek a vizualizáció általi támogatása. További információt a [minősítési követelményekben](power-bi-custom-visuals-certified.md#certification-requirements) talál.