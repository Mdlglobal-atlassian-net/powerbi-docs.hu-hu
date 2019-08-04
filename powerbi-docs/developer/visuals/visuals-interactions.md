---
title: Vizualizációk interakciói
description: Annak ellenőrzése, hogy a Power BI-vizualizáció engedélyezi-e a vizualizáció-interakciókat
author: shaym83
ms.author: shaym
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 739e59c6da3c1e464e0462a928bc4f33ea0d01f8
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424493"
---
# <a name="visuals-interactions"></a>Vizualizációk interakciói

A vizualizációk lekérdezhetik az „allowInteractions” jelzőt, amely azt jelzi, hogy a vizualizáció engedélyezi-e a vizualizáció-interakciókat.
A vizualizációk például interaktívak a jelentések megtekintése vagy szerkesztése közben, azonban nem, amikor egy irányítópulton tekintik meg őket.
Az ilyen interakciók a kattintás, a pásztázás, a nagyítás, a kijelölés és hasonlók.
Az elemleírásokat minden forgatókönyvben engedélyezni kell, a jelzőtől függetlenül.

Az „allowInteractions” jelző logikai értékként jelenik meg a vizualizáció indításakor, az IVisualHost interfész tagjaként.

Az olyan Power BI-forgatókönyvekben, amelyekben a vizualizációk nem lehetnek interaktívak (például az irányítópult-csempéken), az „allowInteractions” jelző értéke hamis lesz.
Ellenkező esetben (például jelentésekben) az „allowInteractions” értéke igaz.

További információt a [SampleBarChart vizualizációs adattárban](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/59a47935d8f5272ce145fe804193599ddb7e2001) találhat

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
