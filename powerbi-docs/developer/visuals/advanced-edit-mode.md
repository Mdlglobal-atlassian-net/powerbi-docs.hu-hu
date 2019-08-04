---
title: Speciális szerkesztési mód
description: Power BI-vizualizációk fejlett felületi vezérlőkkel
author: shaym83
ms.author: shaym
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 625105aed773bce5cf70932f092faf60ea001c2c
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425551"
---
# <a name="advanced-edit-mode"></a>Speciális szerkesztési mód

A fejlett felületi vezérlőket igénylő vizualizációk támogathatják a Speciális szerkesztési módot.
Ebben az esetben a jelentésszerkesztési módban egy `Edit` gomb jelenik meg a vizualizáció menüjében.
Ha az `Edit` gombra kattint, az EditMode beállítás értéke `Advanced`lesz.
A vizualizáció az EditMode jelzővel megállapíthatja, hogy megjelenítsen-e felületi vezérlőket.

A vizualizáció alapértelmezés szerint nem támogatja a Speciális szerkesztési módot.
Eltérő viselkedés igénye esetén ezt explicit módon fel kell tüntetni a vizualizáció `capabilities.json` fájljában a `advancedEditModeSupport` tulajdonság beállításával.

Lehetséges értékek:

- 0 – NotSupported

- 1 – SupportedNoAction

- 2 – SupportedInFocus

## <a name="entering-advanced-edit-mode"></a>A Speciális szerkesztési mód elindítása

Az `Edit` gomb a következő esetekben jelenik meg:

 1 – Az `advancedEditModeSupport` tulajdonság a capabilities.json fájlban `SupportedNoAction` vagy `SupportedInFocus` értékre van állítva.

 2 – A vizualizáció jelentésszerkesztési módban van megnyitva.

Ha az `advancedEditModeSupport` tulajdonság hiányzik a capabilities.json fájlból, vagy `NotSupported` értékre van állítva, az „Edit” (Szerkesztés) gomb eltűnik.

![A szerkesztési mód megnyitása](./media/edit-mode.png)

Amikor a felhasználó az `Edit` gombra kattint, a vizualizáció frissítési hívást kap, `Advanced` értékre állított EditMode beállítással.
A capabilities fájlban beállított értékek alapján a következő műveletek mennek végbe:

* `SupportedNoAction`– Nincs szükség további lépésre a gazdagéptől.
* `SupportedInFocus` – A gazdagép fókusz módban jeleníti meg a vizualizációt.

## <a name="exiting-advanced-edit-mode"></a>Kilépés a Speciális szerkesztési módból

A `Back to report` gomb a következő esetekben jelenik meg:

1 – Az `advancedEditModeSupport` tulajdonság a capabilities.json fájlban `SupportedInFocus` értékre van állítva.
