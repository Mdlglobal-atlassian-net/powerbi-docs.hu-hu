---
title: A Vizualizációs szűrők API Power BI-vizualizációkban
description: Ez a cikk más vizualizációk Power BI-vizualizációk általi szűrését mutatja be.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 95e661e81e7753d0a28806cca5d652f8e92666a8
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "80114106"
---
# <a name="the-visual-filters-api-in-power-bi-visuals"></a>A Vizualizációs szűrők API Power BI-vizualizációkban

A Vizualizációs szűrők API az adatok szűrését teszi lehetővé Power BI-vizualizációkban. A más kijelölésekkel szembeni fő különbség az, hogy más vizualizációk a kiemelés támogatása ellenére is tetszőlegesen szűrhetők.

A vizualizáció szűrésének engedélyezéséhez annak tartalmaznia kell egy `filter` objektumot a *capabilities.json* kód `general` szakaszában.

```json
"objects": {
        "general": {
            "displayName": "General",
            "displayNameKey": "formattingGeneral",
            "properties": {
                "filter": {
                    "type": {
                        "filter": true
                    }
                }
            }
        }
    }
```

A Vizualizációs szűrők API-interfészek a [powerbi-models](https://www.npmjs.com/package/powerbi-models) csomagban érhetők el. A csomag osztályokat is tartalmaz a szűrőpéldányok létrehozásához.

```cmd
npm install powerbi-models --save
```

Ha az eszközök korábbi (3.x.x előtti) verzióját használja, a `powerbi-models` csomagot is bele kell foglalnia a vizualizáció-csomagba. További információt [A Speciális szűrő API hozzáadása az egyéni vizualizációhoz](https://github.com/Microsoft/powerbi-visuals-sampleslicer/blob/master/doc/AddingAdvancedFilterAPI.md) című rövid útmutatóban talál.

Minden szűrő az `IFilter` interfészt terjeszti ki, ahogyan az alábbi kódban látható:

```typescript
export interface IFilter {
    $schema: string;
    target: IFilterTarget;
}
```
Ebben a kódban:
* `target` a tábla oszlopa az adatforrásban.

## <a name="the-basic-filter-api"></a>Az Alapszintű szűrő API

Az alábbi kód alapszintű szűrőinterfészt mutat be:

```typescript
export interface IBasicFilter extends IFilter {
    operator: BasicFilterOperators;
    values: (string | number | boolean)[];
}
```

Ebben a kódban:
* `operator` enumerálás az *In*, *NotIn* és *All* értékekkel.
* `values` a feltételhez tartozó értékekből áll.

Példa alapszintű szűrőre:

```typescript
let basicFilter = {
    target: {
        column: "Col1"
    },
    operator: "In",
    values: [1,2,3]
}
```

A szűrő jelentése: „adj meg minden sort, ahol a `col1` értéke 1, 2 vagy 3”.

Ennek SQL-megfelelője:

```sql
SELECT * FROM table WHERE col1 IN ( 1 , 2 , 3 )
```

Szűrő létrehozásához használhatja a `powerbi-models`-beli BasicFilter osztályt.

Ha az eszköz régebbi verzióját használja, az ablakobjektumban a `window['powerbi-models']` használatával kell lekérnie a modellek egy példányát, ahogyan az alábbi kódban látható:

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')),
    column: categories.source.displayName
};

let values = [ 1, 2, 3 ];

let filter: IBasicFilter = new window['powerbi-models'].BasicFilter(target, "In", values);
```

A vizualizáció az applyJsonFilter() metódus használatával hívja meg a szűrőt a vizualizációhoz a konstruktorban megadott IVisualHost gazdainterfészen.

```typescript
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

## <a name="the-advanced-filter-api"></a>A Speciális szűrő API

A [Speciális szűrő API](https://github.com/Microsoft/powerbi-models) összetett vizualizációközi adatpont-kijelölési és szűrési lekérdezéseket tesz lehetővé, amelyek több feltételre (például *LessThan*, *Contains*, *Is*, *IsBlank* stb.) épülnek.

A szűrő a Vizualizációk API 1.7.0 verziójában lett bevezetve.

A Speciális szűrő API-hoz `target` is szükséges a `table` és a `column` névvel. A Speciális szűrő API két operátora viszont az *And* és az *Or*. 

Emellett a szűrő értékek helyett feltételeket használ az interfészhez:

```typescript
interface IAdvancedFilterCondition {
    value: (string | number | boolean);
    operator: AdvancedFilterConditionOperators;
}
```

Az `operator` paraméter feltételoperátorai a következők: *None*, *LessThan*, *LessThanOrEqual*, *GreaterThan*, *GreaterThanOrEqual*, *Contains*, *DoesNotContain*, *StartsWith*, *DoesNotStartWith*, *Is*, *IsNot*, *IsBlank* és „IsNotBlank”

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')), // table
    column: categories.source.displayName // col1
};

let conditions: IAdvancedFilterCondition[] = [];

conditions.push({
    operator: "LessThan",
    value: 0
});

let filter: IAdvancedFilter = new window['powerbi-models'].AdvancedFilter(target, "And", conditions);

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

Ennek SQL-megfelelője:

```sql
SELECT * FROM table WHERE col1 < 0;
```

A Speciális szűrő API használatát bemutató teljes mintakódot a [Sampleslicer vizualizációs adattárban](https://github.com/Microsoft/powerbi-visuals-sampleslicer) találhatja meg.

## <a name="the-tuple-filter-api-multi-column-filter"></a>A Rekordszűrő API (többoszlopos szűrő)

A Rekordszűrő API a Vizualizációk API 2.3.0 verziójában lett bevezetve. Az Alapszintű szűrő API-hoz hasonlít, de több oszlopra vagy táblára vonatkozó feltételek definiálását is lehetővé teszi.

Az alábbi kód a szűrőinterfészt mutatja be: 

```typescript
interface ITupleFilter extends IFilter {
    $schema: string;
    filterType: FilterType;
    operator: TupleFilterOperators;
    target: ITupleFilterTarget;
    values: TupleValueType[];
}
```

Ebben a kódban:
* `target` oszlopokból álló tömb táblanevekkel:

    ```typescript
    declare type ITupleFilterTarget = IFilterTarget[];
    ```

  A szűrő különböző táblákban lévő oszlopokra is hivatkozhat.

* A `$schema` értéke https://powerbi.com/product/schema#tuple.

* A `filterType` értéke *FilterType.Tuple*.

* Az `operator` csak az *In* operátorban való használatot engedélyezi.

* A `values` értékrekordokból álló tömb, és minden rekord a cél oszlopértékek egy megengedett kombinációjának felel meg. 

```typescript
declare type TupleValueType = ITupleElementValue[];

interface ITupleElementValue {
    value: PrimitiveValueType
}
```

A teljes példa:

```typescript
let target: ITupleFilterTarget = [
    {
        table: "DataTable",
        column: "Team"
    },
    {
        table: "DataTable",
        column: "Value"
    }
];

let values = [
    [
        // the first column combination value (or the column tuple/vector value) that the filter will pass through
        {
            value: "Team1" // the value for the `Team` column of the `DataTable` table
        },
        {
            value: 5 // the value for the `Value` column of the `DataTable` table
        }
    ],
    [
        // the second column combination value (or the column tuple/vector value) that the filter will pass through
        {
            value: "Team2" // the value for `Team` column of `DataTable` table
        },
        {
            value: 6 // the value for `Value` column of `DataTable` table
        }
    ]
];

let filter: ITupleFilter = {
    $schema: "https://powerbi.com/product/schema#tuple",
    filterType: FilterType.Tuple,
    operator: "In",
    target: target,
    values: values
}

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

> [!IMPORTANT]
> Számít az oszlopnevek és feltételértékek sorrendje.

Ennek SQL-megfelelője:

```sql
SELECT * FROM DataTable WHERE ( Team = "Team1" AND Value = 5 ) OR ( Team = "Team2" AND Value = 6 );
```  

## <a name="restore-the-json-filter-from-the-data-view"></a>A JSON-szűrő visszaállítása az adatnézetből

Az API 2.2-es verziójától kezdve a JSON-szűrő visszaállítható a *VisualUpdateOptions* alapján, ahogyan az alábbi kódban látható:

```typescript
export interface VisualUpdateOptions extends extensibility.VisualUpdateOptions {
    viewport: IViewport;
    dataViews: DataView[];
    type: VisualUpdateType;
    viewMode?: ViewMode;
    editMode?: EditMode;
    operationKind?: VisualDataChangeOperationKind;
    jsonFilters?: IFilter[];
}
```

Könyvjelző váltásakor a Power BI a vizualizáció `update` metódusát hívja meg, a vizualizáció pedig lekér egy megfelelő `filter` objektumot. További információ: [A könyvjelzők támogatásának hozzáadása Power BI-vizualizációkban](bookmarks-support.md).

### <a name="sample-json-filter"></a>Minta JSON-szűrő

Az alábbi ábrán egy minta JSON-szűrő kódja látható:

![JSON-szűrő kódja](media/filter-api/json-filter.png)

### <a name="clear-the-json-filter"></a>A JSON-szűrő törlése

A szűrő API a szűrő `null` értékét *alaphelyzetbe állításként* vagy *törlésként* értelmezi.

```typescript
// invoke the filter
visualHost.applyJsonFilter(null, "general", "filter", FilterAction.merge);
```
