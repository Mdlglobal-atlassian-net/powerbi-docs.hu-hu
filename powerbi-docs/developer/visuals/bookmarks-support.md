---
title: Könyvjelzők támogatásának hozzáadása Power BI-vizualizációkhoz
description: A Power BI-vizualizációk kezelni tudják a könyvjelzőváltást
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: c19b67a59d0ecb4cbfbcf5ad8dd18886f440e164
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/23/2019
ms.locfileid: "71194439"
---
# <a name="add-bookmark-support-for-power-bi-visuals"></a>Könyvjelzők támogatásának hozzáadása Power BI-vizualizációkhoz

A Power BI-jelentések könyvjelzőivel rögzíthető egy jelentésoldal konfigurált nézete és a vizualizáció kijelölési és szűrési állapota. Ez azonban további műveletet igényel a Power BI-vizualizációk részéről a könyvjelző támogatása és a változásokra való helyes reagálás érdekében.

További információt az [Elemzések megosztása és történetek felépítése a Power BI könyvjelzőivel](https://docs.microsoft.com/power-bi/desktop-bookmarks) című cikkben talál.

## <a name="report-bookmarks-support-in-your-visual"></a>Jelentésbeli könyvjelzők támogatása vizualizációban

Ha a vizualizáció más vizualizációkkal áll kölcsönhatásban, más vizualizációk adatpontjait jelöli ki vagy szűri azokat, akkor az állapotot a tulajdonságokból kell helyreállítania.

## <a name="add-report-bookmarks-support"></a>Jelentésbeli könyvjelzők támogatásának hozzáadása

1. Telepítse (vagy frissítse) a szükséges segédprogramot ([powerbi-visuals-utils-interactivityutils](https://github.com/Microsoft/PowerBI-visuals-utils-interactivityutils/)) a 3.0.0 vagy újabb verzióra. Ez további, állapotkijelöléssel vagy szűréssel kezelhető osztályokat tartalmaz. Szűrővizualizációkhoz és az `InteractivityService` modult használó vizualizációkhoz szükséges.

2. Frissítse a vizualizáció API-ját az 1.11.0 verzióra, hogy használhassa a `registerOnSelectCallback`-et a `SelectionManager` egy példányában. Olyan nem szűrő vizualizációkhoz szükséges, amelyek az `InteractivityService` helyett a `SelectionManager`-t használják.

### <a name="how-power-bi-visuals-interact-with-power-bi-in-report-bookmarks"></a>Power BI-vizualizációk kölcsönhatása a Power BI-jal a jelentések könyvjelzőkiben

Vizsgáljuk meg a következő esetet: Ön néhány könyvjelzőt szeretne létrehozni a jelentésoldalon, és mindegyiknek más a kijelölési állapota.

Először egy adatpontot jelöl ki a vizualizációban. A vizualizáció azzal hat a Power BI-ra és a többi vizualizációra, hogy továbbadja a kijelöléseket a gazdagépnek. Ön ez után a **Hozzáadás** lehetőségét választja a **Könyvjelzők** panelen, és a Power BI menti az aktuális kijelöléseket az új könyvjelzőhöz.

Ez többször is megismétlődik, amikor Ön módosítja a kijelölést és új könyvjelzőket vesz fel. Miután létrehozta a könyvjelzőket, válthat is közöttük.

Amikor kiválaszt egy könyvjelzőt, a Power BI helyreállítja a mentett szűrési vagy kijelölési állapotot, és továbbadja azt a vizualizációknak. Más vizualizációk is a könyvjelzőben tárolt állapot alapján lesznek kiemelve vagy szűrve. A műveleteket a Power BI-gazdagép végzi. A vizualizáció feladata, hogy helyesen tükrözze az új kijelölési állapotot (például a renderelt adatpontok színének megváltoztatásával).

Az új kijelölési állapot az `update` metóduson keresztül van átadva a vizualizációnak. Az `options` argumentum tartalmaz egy speciális tulajdonságot: `options.jsonFilters`. Ebben a JSONFilter tulajdonság tartalma lehet `Advanced Filter` vagy `Tuple Filter`.

A vizualizációnak vissza kell állítania a szűrőértékeket, hogy a vizualizáció a kiválasztott könyvjelzőnek megfelelő állapotot jelenítse meg. Használhatja a speciális visszahívási függvényhívást, az ISelectionManager regisztrált `registerOnSelectCallback` metódusát, ha a vizualizáció csak kijelöléseket használ.

### <a name="visuals-with-selection"></a>Kijelöléseket tartalmazó vizualizációk

Ha a vizualizáció [Kijelölés](https://github.com/Microsoft/PowerBI-visuals/blob/master/Tutorial/Selection.md) használatával más vizualizációkkal is kapcsolatban van, két módon adhat hozzá könyvjelzőket:

* Ha a vizualizáció még nem használta az [InteractivityService](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md)-t, használhatja a `FilterManager.restoreSelectionIds` metódust.

* Ha a vizualizáció már használja az [InteractivityService](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md)-t a kiválasztások kezeléséhez, akkor használja az `applySelectionFromFilter` metódust az `InteractivityService` egy példányában.

#### <a name="use-iselectionmanagerregisteronselectcallback"></a>Az ISelectionManager.registerOnSelectCallback használata

Amikor egy kiválaszt egy könyvjelzőt, a Power BI meghívja a vizualizáció `callback` metódusát a megfelelő kijelölésekkel. 

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        //called when a selection was set by Power BI
    });
);
```

Tegyük fel, hogy van egy adatpontja a vizualizációban, amely a [visualTransform](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts#L74) metódusban lett létrehozva.

A `datapoints` felépítése a következő:

```typescript
visualDataPoints.push({
    category: categorical.categories[0].values[i],
    color: getCategoricalObjectValue<Fill>(categorical.categories[0], i, 'colorSelector', 'fill', defaultColor).solid.color,
    selectionId: host.createSelectionIdBuilder()
        .withCategory(categorical.categories[0], i)
        .createSelectionId(),
    selected: false
});
```

Most már adott a `visualDataPoints` adatpontokként, valamint a `callback` függvénynek átadott `ids` tömb.

Ezen a ponton a vizualizációnak össze kell hasonlítania az `ISelectionId[]` tömböt a `visualDataPoints` tömbben lévő kijelölésekkel, és kijelöltként kell megjelölnie a megfelelő adatpontokat.

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        visualDataPoints.forEach(dataPoint => {
            ids.forEach(bookmarkSelection => {
                if (bookmarkSelection.equals(dataPoint.selectionId)) {
                    dataPoint.selected = true;
                }
            });
        });
    });
);
```

Az adatpontok frissítése után azoknak tükrözniük kell a `filter` objektumban tárolt aktuális kijelölési állapotot. Az adatpontok renderelésekor az egyéni vizualizáció kijelölési állapota egyezni fog a könyvjelző állapotával.

### <a name="use-interactivityservice-for-control-selections-in-the-visual"></a>A vizualizáció kijelöléseinek vezérlése az InteractivityService használatával

Ha a vizualizáció az `InteractivityService` modult használja, nincs szükség további műveletre ahhoz, hogy a könyvjelzők támogatva legyenek a vizualizációban.

Amikor könyvjelzőket választ ki, a segédprogram kezeli a vizualizáció kiválasztási állapotát.

### <a name="visuals-with-a-filter"></a>Vizualizációk szűrőkkel

Tegyük fel, hogy a vizualizáció adattartományon alapuló adatszűrőt hoz létre. A tartomány kezdetét és végét a `startDate` és az `endDate` adja meg.

A vizualizáció speciális szűrőt hoz létre, majd az `applyJsonFilter` gazdametódus hívásával szűri az adatokat a vonatkozó feltételek alapján.

A cél a szűréshez használt tábla.

```typescript
import { AdvancedFilter } from "powerbi-models";

const filter: IAdvancedFilter = new AdvancedFilter(
    target,
    "And",
    {
        operator: "GreaterThanOrEqual",
        value: startDate
            ? startDate.toJSON()
            : null
    },
    {
        operator: "LessThanOrEqual",
        value: endDate
            ? endDate.toJSON()
            : null
    });

this.host.applyJsonFilter(
    filter,
    "general",
    "filter",
    (startDate && endDate)
        ? FilterAction.merge
        : FilterAction.remove
);
```

Amikor kiválaszt egy könyvjelzőt, az egyéni vizualizáció egy `update` hívást kap.

Az egyéni vizualizációnak ellenőriznie kell a szűrőt az objektumban:

```typescript
const filter: IAdvancedFilter = FilterManager.restoreFilter(
    && options.jsonFilters
    && options.jsonFilters[0] as any
) as IAdvancedFilter;
```

Ha a `filter` objektum nem üres, a vizualizációnak az objektumból kell visszaállítania a szűrőfeltételeket:

```typescript
const jsonFilters: AdvancedFilter = this.options.jsonFilters as AdvancedFilter[];

if (jsonFilters
    && jsonFilters[0]
    && jsonFilters[0].conditions
    && jsonFilters[0].conditions[0]
    && jsonFilters[0].conditions[1]
) {
    const startDate: Date = new Date(`${jsonFilters[0].conditions[0].value}`);
    const endDate: Date = new Date(`${jsonFilters[0].conditions[1].value}`);

    // apply restored conditions
} else {
    // apply default settings
}
```

Ez után a vizualizációnak meg kell változtatnia a belső állapotát, hogy az az aktuális feltételeket tükrözze. A belső állapot magában foglalja az adatpontokat és a vizualizációs objektumokat (vonalak, négyszögek stb.).

> [!IMPORTANT]
> A jelentés könyvjelzőinek esetében a vizualizációnak nem kell az `applyJsonFilter` hívásával szűrnie a többi vizualizációt. Azok szűrését elvégzi a Power BI.

Az Idővonal-szeletelő az adattartományoknak megfelelően változtatja a tartományválasztót.

További információt az [Idővonal-szeletelő adattárában](https://github.com/Microsoft/powerbi-visuals-timeline/commit/606f1152f59f82b5b5a367ff3b117372d129e597?diff=unified#diff-b6ef9a9ac3a3225f8bd0de84bee0a0df) talál.

### <a name="filter-the-state-to-save-visual-properties-in-bookmarks"></a>Szűrési állapot vizualizációtulajdonságok könyvjelzőkbe mentéséhez

A `filterState` tulajdonság a szűrés részévé tesz egy tulajdonságot. A vizualizáció különböző értékeket tárolhat könyvjelzőkben.

A tulajdonság értékének szűrési állapotként való mentéséhez az objektumtulajdonságnak `"filterState": true`-ként megjelölve kell szerepelnie a *capabilities.json* fájlban.

Az Idővonal szeletelő például egy szűrőben tárolja a `Granularity` tulajdonság értékeit. Ez lehetővé teszi, hogy az aktuális részletesség a könyvjelzők módosításakor változzon.

További információt az [Idővonal-szeletelő adattárában](https://github.com/microsoft/powerbi-visuals-timeline/commit/8b7d82dd23cd2bd71817f1bc5d1e1732347a185e#diff-290828b604cfa62f1cb310f2e90c52fdR334) talál.
