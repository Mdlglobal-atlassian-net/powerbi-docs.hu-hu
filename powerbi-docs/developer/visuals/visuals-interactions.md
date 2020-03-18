---
title: Vizuális interakciók a Power BI-vizualizációkban
description: Ez a cikk ismerteti, hogyan ellenőrizhető, hogy a Power BI-vizualizációk engedélyezik-e a vizualizációk interakcióit.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 1fb4f7d5950ab18a74dcacfdfef9c3ada90512c4
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/14/2020
ms.locfileid: "79378938"
---
# <a name="visual-interactions-in-power-bi-visuals"></a>Vizuális interakciók a Power BI-vizualizációkban

A vizualizációk lekérdezhetik az `allowInteractions` jelző értékét, amely azt jelzi, hogy a vizualizáció engedélyezi-e a vizualizáció-interakciókat. A vizualizációk például interaktívak a jelentések megtekintése vagy szerkesztése közben, azonban nem, amikor egy irányítópulton tekintik meg őket. Az ilyen interakciók a *kattintás*, a *pásztázás*, a *nagyítás*, a *kijelölés* és hasonlók. 

> [!NOTE]
> Minden forgatókönyvben engedélyeznie kell az elemleírásokat, függetlenül attól, hogy melyik jelölő van megadva.

Az `allowInteractions` jelző logikai értékként jelenik meg a vizualizáció indításakor, az IVisualHost interfész tagjaként.

Az olyan Power BI-forgatókönyvekben, amelyekben a vizualizációk nem lehetnek interaktívak (például az irányítópult-csempéken), az `allowInteractions` jelző értéke `false`. Ellenkező esetben (például jelentéseknél) az `allowInteractions` értéke `true`.

További információt a [SampleBarChart vizualizációs adattárban](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/59a47935d8f5272ce145fe804193599ddb7e2001) találhat.

```typescript
   ...
   let allowInteractions = options.host.allowInteractions;
   bars.on('click', function(d) {
       if (allowInteractions) {
           selectionManager.select(d.selectionId);
           ...
       }
   });
```
