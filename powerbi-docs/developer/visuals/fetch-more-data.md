---
title: További adatok lekérése
description: Nagyméretű adatkészletek szegmentált beolvasásának engedélyezése Power BI-vizualizációkhoz
author: AviSander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: bc8ff673927fd66bf44164e4e9950c279b98c6c1
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425068"
---
# <a name="fetch-more-data-from-power-bi"></a>Több adat beolvasása a Power BI-ból

Az API-val több adatot tölthet be, és meghaladhatja a 30-K adatpont korlátját. Az adatokat részletenként olvashatja be. Az adatrészletek mérete úgy konfigurálható, hogy javítsa a teljesítményt a használati eset alapján.  

## <a name="enable-segmented-fetch-of-large-datasets"></a>Nagyméretű adatkészletek szegmentált beolvasásának engedélyezése

A `dataview` szegmentálási módhoz definiáljon egy „ablakot” (dataReductionAlgorithm) a szükséges dataViewMapping elemhez a vizualizáció `capabilities.json` fájljában.
A `count` meghatározza az ablak méretét, amely korlátozza az új frissítések `dataview` elemét kiegészítő új adatsorok számát.

Hozzáadás a capabilities.json fájlhoz

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

## <a name="usage-in-the-custom-visual"></a>Használat egyéni vizualizációkban

Az, hogy az adatok léteznek-e, a `dataView.metadata.segment` elem meglétének ellenőrzésével állapítható meg:

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

Az `options.operationKind` ellenőrzésével megállapíthatja azt is, hogy ez az első vagy egy későbbi frissítés.

A `VisualDataChangeOperationKind.Create` jelenti az első szegmenst, míg a `VisualDataChangeOperationKind.Append` a további szegmenseket.

Egy példamegvalósítást találhat az alábbi kódrészletben:

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subesquent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Append) {

    }

    // complete update implementation
}
```

A `fetchMoreData` metódus is meghívható egy felhasználói felületi eseménykezelőből

```typescript
btn_click(){
{
    // check if more data is expected for the current dataview
    if (dataView.metadata.segment) {
        //request for more data if available, as resopnce Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData();
        // handle rejection
        if (!request_accepted) {
            // for example when the 100 MB limit has been reached
        }
    }
}
```

A Power BI a `this.host.fetchMoreData` metódusra adott válaszként meghívja a vizualizáció `update` metódusát az új adatszegmensekkel.

> [!NOTE]
> A Power BI a beolvasott adatmennyiséget **100 MB-ban** korlátozza, hogy ne forduljon elő memóriakorlátozás az ügyféloldalon. Ha a fetchMoreData() függvény „false” választ eredményez, meghaladta a korlátot.*
