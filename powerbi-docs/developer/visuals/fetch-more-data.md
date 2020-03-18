---
title: Több adat beolvasása a Power BI-ból
description: Ez a cikk azt írja le, hogyan engedélyezhető nagyméretű adathalmazok szegmentált beolvasása Power BI-vizualizációkhoz.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 6d51a27bc5c0f18b7f784395dedd58813bfffbc0
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380686"
---
# <a name="fetch-more-data-from-power-bi"></a>Több adat beolvasása a Power BI-ból

Ez a cikk azt írja le, hogyan tölthető be több adat az adatpontokra vonatkozó rögzített 30 kB-os korlát megkerülésével. Ez a megközelítés szegmensekben biztosítja az adatokat. A teljesítmény javítása érdekében a szegmensek méretét a felhasználási helyzetnek megfelelően konfigurálhatja.  

## <a name="enable-a-segmented-fetch-of-large-datasets"></a>Nagyméretű adathalmazok szegmentált beolvasásának engedélyezése

A `dataview` szegmentálási mód használatához szükséges dataViewMapping leképezéshez definiálnia kell egy ablakméretet a dataReductionAlgorithm algoritmushoz a vizualizáció *capabilities.json* fájljában. A `count` határozza meg az ablak méretét, amely korlátozza az egyes frissítések során a `dataview` adatnézethez fűzhető új adatsorok számát.

Illessze be az alábbi kódot a *capabilities.json* fájlba:

```typescript
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                },
                "dataReductionAlgorithm": {
                    "window": {
                        "count": 100
                    }
                }
            }
    }
]
```

Az új szegmenseket a rendszer a meglévő `dataview` elemhez fűz, valamint megadja a vizualizációnak `update` hívásként.

## <a name="usage-in-the-power-bi-visual"></a>Felhasználás a Power BI-vizualizációban

Az adatok meglétét a `dataView.metadata.segment` meglétének ellenőrzésével állapíthatja meg:

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

Az `options.operationKind` ellenőrzésével azt is megállapíthatja, hogy ez az első, vagy egy későbbi frissítés. Az alábbi kódban `VisualDataChangeOperationKind.Create` az első szegmensre, `VisualDataChangeOperationKind.Append` későbbi szegmensekre hivatkozik.

Egy példamegvalósítást találhat az alábbi kódrészletben:

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subsequent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Append) {

    }

    // complete update implementation
}
```

A `fetchMoreData` metódust egy felhasználói felületi eseménykezelőből is meghívhatja az alábbiak szerint:

```typescript
btn_click(){
{
    // check if more data is expected for the current data view
    if (dataView.metadata.segment) {
        //request for more data if available; as a response, Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData();
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

A Power BI a `this.host.fetchMoreData` metódus hívására válaszul meghívja a vizualizáció `update` metódusát egy új adatszegmenssel.

> [!NOTE]
> A Power BI jelenleg összesen 100 MB-ra korlátozza a teljes beolvasott adatmennyiséget, hogy ne ütközzön az ügyfél memóriakorlátozásaiba. A korlát elérése abból látható, hogy ekkor a fetchMoreData() visszatérési értéke `false`.
