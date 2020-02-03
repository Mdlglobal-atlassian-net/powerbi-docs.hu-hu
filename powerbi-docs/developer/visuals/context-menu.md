---
title: Power BI-vizualizációk képességei és tulajdonságai
description: Ez a cikk a Power BI-vizualizációk képességeit és tulajdonságait ismerteti.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 7d24ea77fd73ca6a83176d1b8560c88fa98a8d6b
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/29/2020
ms.locfileid: "76819192"
---
# <a name="add-context-menu-to-power-bi-visual"></a>Környezeti menü felvétele Power BI-vizualizációba

A `selectionId` paraméterekkel és pozícióval (például `{x:, y:}` objektummal) használt `selectionManager.showContextMenu()` metódussal elérheti, hogy a Power BI helyi menüt jelenítsen meg a vizualizációhoz.

> [!IMPORTANT]
> A `selectionManager.showContextMenu()` a Vizualizációk API 2.2.0 verziójában lett bevezetve.

Általában jobb kattintásos eseményként (vagy hosszú érintéshez az érintőképernyős eszközöknél) van felvéve. Referenciaként helyi menü van hozzáadva a BarChart mintához:

```typescript
    public update(options: VisualUpdateOptions) {
        //...
        //handle context menu
        this.svg.on('contextmenu', () => {
            const mouseEvent: MouseEvent = d3.event as MouseEvent;
            const eventTarget: EventTarget = mouseEvent.target;
            let dataPoint = d3.select(eventTarget).datum();
            this.selectionManager.showContextMenu(dataPoint? dataPoint.selectionId : {}, {
                x: mouseEvent.clientX,
                y: mouseEvent.clientY
            });
            mouseEvent.preventDefault();
        });
```
