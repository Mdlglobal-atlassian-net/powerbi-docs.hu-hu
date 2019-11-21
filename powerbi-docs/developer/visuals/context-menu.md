---
title: Power BI-vizualizációk képességei és tulajdonságai
description: Ez a cikk a Power BI-vizualizációk képességeit és tulajdonságait ismerteti.
author: asander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 206f1aec7c76b00b6f725d8469eb3e483a01c653
ms.sourcegitcommit: f7b28ecbad3e51f410eff7ee4051de3652e360e8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/13/2019
ms.locfileid: "74061776"
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
