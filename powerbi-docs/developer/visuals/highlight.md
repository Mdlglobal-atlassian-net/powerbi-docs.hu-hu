---
title: Kiemelés
description: Adatpont-kijelölések kiemelése Power BI-vizualizációkban
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 1ee45781ddc29eee9eeab23a5d748fb7752fe907
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424815"
---
# <a name="highlight-data-points-in-power-bi-visuals"></a>Adatpontok kiemelése Power BI-vizualizációkban

Egy elem kijelölésekor a `dataView` objektum `values` tömbje alapértelmezés szerint csak a kijelölt értékekre lesz szűrve. Emiatt az oldal többi vizualizációja csak a kijelölt adatokat jeleníti meg.

![highlight `dataview` default behavior](./media/highlight-dataview.png)

Ha `capabilities.json` fájl `supportsHighlight` tulajdonságát `true` értékre állítja, a teljes szűretlen `values` tömböt kapja eredményül egy `highlights` tömbbel együtt. A `highlights` tömb az értékek tömbjével megegyező hosszúságú lesz, a nem kijelölt értékek pedig `null` lesznek beállítva. A tulajdonság engedélyezésével a vizualizáció felelősségévé válik a megfelelő adatok kiemelése – `values` a tömb `highlights` a tömbbel való összehasonlításával.

![highlight `dataview` supportshighlight](./media/highlight-dataview-supports.png)

A példában egy sáv van kijelölve. Ez az egyetlen érték a kiemelt tömbben. Fontos megjegyezni, hogy több kijelölés, valamint részleges kiemelés is szerepelhet. Az értékek és kiemelési tömbök megfelelő numerikus értékei megjelennek, azonban eltérnek.
