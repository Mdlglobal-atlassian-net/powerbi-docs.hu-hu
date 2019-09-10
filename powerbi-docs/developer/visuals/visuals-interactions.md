---
title: Vizuális interakciók a Power BI-vizualizációkban
description: Ez a cikk ismerteti, hogyan ellenőrizhető, hogy a Power BI-vizualizációk engedélyezik-e a vizualizációk interakcióit.
author: shaym83
ms.author: shaym
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: f2fb2d451deb63b5e9c08472654e28d0e1a469db
ms.sourcegitcommit: b602cdffa80653bc24123726d1d7f1afbd93d77c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/03/2019
ms.locfileid: "70236624"
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
