---
title: Könyvjelzők
description: A Power BI-vizualizációk kezelni tudják a könyvjelzőváltást
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 90e3fc73cd49a5c84a5c2acc68a8cf5e0e4aa42b
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425505"
---
# <a name="add-bookmarks-support-for-power-bi-visuals"></a>Könyvjelzők támogatásának hozzáadása Power BI-vizualizációkhoz

A Power BI-jelentések könyvjelzőivel rögzíthető egy jelentésoldal konfigurált nézete, és a vizualizáció kijelölési és szűrési állapota. Ez azonban további tevékenységet igényel az egyéni vizualizációk részéről a könyvjelző támogatása és a változásokra való helyes reagálás érdekében.

A könyvjelzőkről a [dokumentációban](https://docs.microsoft.com/power-bi/desktop-bookmarks) olvashat bővebben

## <a name="report-bookmarks-support-in-your-visual"></a>Jelentésbeli könyvjelzők támogatása vizualizációban

Ha a vizualizáció más vizualizációkkal áll kölcsönhatásban, más vizualizációk adatpontjait jelöli ki vagy szűri azokat, akkor az állapotot a tulajdonságokból kell helyreállítania.

## <a name="how-to-add-report-bookmarks-support"></a>Jelentésbeli könyvjelzők támogatásának hozzáadása

1. Telepítse (vagy frissítse) a szükséges segédprogramot: `powerbi-visuals-utils-interactivityutils`(https://github.com/Microsoft/PowerBI-visuals-utils-interactivityutils/) 3.0.0 vagy újabb verzió. Ez további, állapotkijelöléssel vagy szűréssel kezelhető osztályokat tartalmaz. Szűrővizualizációkhoz és az `InteractivityService` modult használó vizualizációkhoz szükséges.

2. Frissítse a vizualizáció API-t az 1.11.0 verzióra a `registerOnSelectCallback` használatához a `SelectionManager` példányában. Olyan nem szűrő vizualizációkhoz szükséges, amelyek az `InteractivityService` helyett a `SelectionManager`t használják.

### <a name="how-custom-visuals-interact-with-power-bi-in-the-report-bookmarks-scenario"></a>Egyéni vizualizációk kölcsönhatása a Power BI-jal a jelentésbeli könyvjelzők szempontjából

Vizsgáljuk meg a következő példát: Egy felhasználó néhány könyvjelzőt hoz létre a jelentésoldalon, és mindegyiknek más a kijelölési állapota.

A felhasználó először egy adatpontot jelöl ki a vizualizációban. A vizualizáció azzal hat a Power BI-ra és a többi vizualizációra, hogy továbbadja a kijelöléseket a gazdagépnek. A felhasználó ez után a `Bookmark panel` „Hozzáadás” lehetőségét választja, és a Power BI menti az aktuális kijelöléseket az új könyvjelzőhöz.

Ez többször is megismétlődik, miközben a felhasználó módosítja a kijelölést és új könyvjelzőket vesz fel.
Miután elkészültek, a felhasználó válthat a könyvjelzők között.

Amikor a felhasználó kiválaszt egy könyvjelzőt, a Power BI helyreállítja a mentett szűrési vagy kijelölési állapotot, és továbbadja azt a vizualizációknak. Más vizualizációk is a könyvjelzőben tárolt állapot alapján lesznek kiemelve vagy szűrve. A műveleteket a Power BI-gazdagép végzi. A vizualizáció feladata, hogy helyesen tükrözze az új kijelölési állapotot (például a renderelt adatpontok színének megváltoztatásával).

Az új kijelölési állapot az `update` metóduson keresztül van átadva a vizualizációnak. Az `options` argumentum tartalmaz egy speciális tulajdonságot: `options.jsonFilters`. Ebben a JSONFilter tulajdonság tartalma lehet `Advanced Filter` vagy `Tuple Filter`.

A vizualizációnak vissza kell állítania a szűrőértékeket, hogy a vizualizáció a kiválasztott könyvjelzőnek megfelelő állapotot jelenítse meg.

Használhatja a speciális visszahívási függvényhívást, az ISelectionManager regisztrált `registerOnSelectCallback` metódusát, ha a vizualizáció csak kijelöléseket használ.

### <a name="visuals-with-selections"></a>Kijelöléseket tartalmazó vizualizációk

Ha a vizualizációk [kijelölések](https://github.com/Microsoft/PowerBI-visuals/blob/master/Tutorial/Selection.md) használatával hatnak más vizualizációkra, két módon vehet fel könyvjelzőket.

* Használhatja a `FilterManager.restoreSelectionIds` metódust, a korábban **nem használta az [`InteractivityService`](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md)** modult a vizualizációban.

* Ha a vizualizáció már az **[`InteractivityService`](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md)** használatával kezeli a vizualizációkat, az `applySelectionFromFilter` metódust kell használnia az `InteractivityService` példányában.

#### <a name="using-iselectionmanagerregisteronselectcallback"></a>Az `ISelectionManager.registerOnSelectCallback` használata

Amikor egy felhasználó könyvjelzőkre kattint, a Power BI meghívja a vizualizáció `callback` metódusát a megfelelő kijelölésekkel. 

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        //called when a selection was set by Power BI
    });
);
```

Tegyük fel, hogy a [`'visualTransform'`](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts#L74) metódosban létrehozott vizualizáció tartalmaz egy adatpontot.

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

Adottak tehát az adatpontok, mint `visualDataPoints`, és a `callback` függvénynek átadott `ids` tömb.

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

### <a name="using-interactivityservice-for-control-selections-in-the-visual"></a>A vizualizáció kijelöléseinek vezérlése az `InteractivityService` használatával

Ha a vizualizáció az `InteractivityService` modult használja, nincs szükség további műveletre ahhoz, hogy a könyvjelzők támogatva legyenek a vizualizációban.

A vizualizáció kijelölési állapotát a segédprogram kezeli, amikor a felhasználó kiválasztja a könyvjelzőket.

### <a name="visuals-with-filter"></a>Vizualizációk szűrőkkel

Tegyük fel, hogy a vizualizáció adattartományon alapuló adatszűrőt hoz létre. A tartomány kezdetét és végét a `startDate` és az `endDate` adja meg.
A vizualizáció speciális szűrőt hoz létre, majd az `applyJsonFilter` gazdametódus hívásával szűri az adatokat a vonatkozó feltételek alapján.
A `target` a szűrendő táblázat.

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

Amikor egy felhasználó egy könyvjelzőre kattint, az egyéni vizualizáció egy `update` hívást kap.

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

Ez után a vizualizációnak meg kell változtatnia a belső állapotát – az adatpontokat és vizualizációs objektumokat (vonalak, téglalapok stb.) –, hogy az az aktuális feltételeket tükrözze.

> [!IMPORTANT]
> A jelentés könyvjelzőinek esetében a vizualizációnak nem kell az `applyJsonFilter` hívásával szűrnie a többi vizualizációt – azok szűrését már elvégzi a Power BI.

Az Idővonal-szeletelő az adattartományoknak megfelelően változtatja a tartományválasztót.

További információt az [Idővonal-szeletelő adattárában](https://github.com/Microsoft/powerbi-visuals-timeline/commit/606f1152f59f82b5b5a367ff3b117372d129e597?diff=unified#diff-b6ef9a9ac3a3225f8bd0de84bee0a0df) talál.

### <a name="filter-state-to-save-visual-properties-in-bookmarks"></a>Szűrési állapot vizualizációtulajdonságok könyvjelzőkbe mentéséhez

A `filterState` tulajdonság a szűrés részévé tesz egy tulajdonságot. A vizualizáció különböző értékeket tárolhat könyvjelzőkben.

A tulajdonság értékének szűrési állapotként való mentéséhez az objektumtulajdonságnak `"filterState": true`-ként megjelölve kell szerepelnie a `capabilities.json` fájlban.

Például: A `Timeline Slicer` szűrőben tárol `Granularity` tulajdonságértékeket. Lehetővé teszi az aktuális részletesség módosítását a könyvjelző felhasználó általi módosításakor.

További információ: [Idővonal-szeletelő adattár](https://github.com/microsoft/powerbi-visuals-timeline/commit/8b7d82dd23cd2bd71817f1bc5d1e1732347a185e#diff-290828b604cfa62f1cb310f2e90c52fdR334);
