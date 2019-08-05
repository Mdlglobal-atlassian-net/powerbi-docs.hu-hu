---
title: Vizualizációs szűrők API
description: Más vizualizációk szűrése Power BI-vizualizációkkal
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 50e9601faf497675ebc3f24609a856a600e3bcb1
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425045"
---
# <a name="power-bi-visual-filters-api"></a>Power BI Vizualizációs szűrők API

A szűrt vizualizációkkal adatok szűrhetők. A kijelöléssel szembeni fő különbség az, hogy más vizualizációk a kiemelés támogatása ellenére is tetszőlegesen szűrhetők.

A vizualizáció szűrésének engedélyezéséhez a vizualizációnak tartalmaznia kell egy `filter` objektumot a capabilities.json tartalom `general` szakaszában.

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

A Szűrő API-interfészek [`powerbi-models`](https://www.npmjs.com/package/powerbi-models) csomagban érhetők el. A csomag osztályokat is tartalmaz a szűrőpéldányok létrehozásához.

```cmd
npm install powerbi-models --save
```

Ha régi (3.x.x-nél kisebb verziószámú) eszközverziókat használ, ajánlott a `powerbi-models` befoglalása a vizualizációk csomagjába. [Gyors útmutató a csomag befoglalásához](https://github.com/Microsoft/powerbi-visuals-sampleslicer/blob/master/doc/AddingAdvancedFilterAPI.md)

Minden szűrő kiterjeszti az `IFilter` interfészt.

```typescript
export interface IFilter {
    $schema: string;
    target: IFilterTarget;
}
```

`target` – az adatforrásbeli tábla oszlopa.

## <a name="basic-filter-api"></a>Alapszintű szűrő API

Az alapszintű szűrő-interfész a következő:

```typescript
export interface IBasicFilter extends IFilter {
    operator: BasicFilterOperators;
    values: (string | number | boolean)[];
}
```

`operator` – enumerálás az „In”, „NotIn” és „All” értékekkel

`values` – a feltétel értékei

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

Régi eszközverziók használata esetén el kell helyeznie a modellek egy példányát az window objektumban a `window['powerbi-models']` használatával:

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

## <a name="advanced-filter-api"></a>Speciális szűrő API

A [Speciális szűrő API](https://github.com/Microsoft/powerbi-models) összetett vizualizációközi adatpont-kijelölési/szűrési lekérdezéseket tesz lehetővé több feltétel (például „LessThan”, „Contains”, „Is”, „IsBlank” stb.) alapján.

A szűrő a Vizualizációk API 1.7.0 verziójában lett bevezetve.

A Speciális szűrő API-hoz `target` szükséges a `table` és a `column` névvel. A Speciális szűrő API két operátora viszont: `"And" | "Or"`. 

Emellett a szűrő értékek helyett feltételeket használ az interface-hez:

```typescript
interface IAdvancedFilterCondition {
    value: (string | number | boolean);
    operator: AdvancedFilterConditionOperators;
}
```

Az `operator` paraméter feltétel-operátorai a következők: `"None" | "LessThan" | "LessThanOrEqual" | "GreaterThan" | "GreaterThanOrEqual" | "Contains" | "DoesNotContain" | "StartsWith" | "DoesNotStartWith" | "Is" | "IsNot" | "IsBlank" | "IsNotBlank"`

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

A Speciális szűrő API-t használó teljes mintakód megtalálható a [`Sampleslicer visual`adattárban](https://github.com/Microsoft/powerbi-visuals-sampleslicer).

## <a name="tuple-filter-api-multi-column-filter"></a>Rekordszűrő API (többoszlopos szűrő)

A Rekordszűrő API a Vizualizációk API 2.3.0 verziójában lett bevezetve.

A Rekordszűrő API az Alapszintű szűrőhöz hasonlít, de több oszlopra vagy táblára vonatkozó feltételek definiálását is lehetővé teszi.

A szűrőhöz tartozó interface: 

```typescript
interface ITupleFilter extends IFilter {
    $schema: string;
    filterType: FilterType;
    operator: TupleFilterOperators;
    target: ITupleFilterTarget;
    values: TupleValueType[];
}
```

`target` oszlopokból álló tömb táblanevekkel:

```typescript
declare type ITupleFilterTarget = IFilterTarget[];
```

  A szűrő különböző táblákban lévő oszlopokat is képes kezelni.

A `$schema` értéke „http://powerbi.com/product/schema#tuple”

A `filterType` értéke `FilterType.Tuple`

Az `operator` csak az `"In"` operátor használatát engedélyezi

A `values` értékrekordokból álló tömb, amelyben minden rekord a cél oszlopértékek egy megengedett kombinációjának felel meg 

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
        // the 1st column combination value (aka column tuple/vector value) that the filter will pass through
        {
            value: "Team1" // the value for `Team` column of `DataTable` table
        },
        {
            value: 5 // the value for `Value` column of `DataTable` table
        }
    ],
    [
        // the 2nd column combination value (aka column tuple/vector value) that the filter will pass through
        {
            value: "Team2" // the value for `Team` column of `DataTable` table
        },
        {
            value: 6 // the value for `Value` column of `DataTable` table
        }
    ]
];

let filter: ITupleFilter = {
    $schema: "http://powerbi.com/product/schema#tuple",
    filterType: FilterType.Tuple,
    operator: "In",
    target: target,
    values: values
}

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

**Az oszlopnevek és a feltételértékek sorrendje lényeges.**

Ennek SQL-megfelelője:

```sql
SELECT * FROM DataTable WHERE ( Team = "Team1" AND Value = 5 ) OR ( Team = "Team2" AND Value = 6 );
```  

## <a name="restoring-json-filter-from-dataview"></a>JSON-szűrő visszaállítása DataView alapján

Az API 2.2-es verziójával kezdődően a **JSON-szűrők** visszaállíthatók a **VisualUpdateOptions** alapján

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

A Power BI a vizualizáció `update` metódusát hívja könyvjelzőváltáskor, és a vizualizáció megkapja a megfelelő `filter` objektumot.
[További információk a könyvjelzők támogatásáról](bookmarks-support.md)

### <a name="sample-json-filter"></a>Minta JSON-szűrő

![JSON-szűrő képernyőképe](./media/json-filter.png)

### <a name="clear-json-filter"></a>JSON-szűrő törlése

A szűrő API a `null` értéket alaphelyzetbe állításként vagy törlésként fogadja el.

```typescript
// invoke the filter
visualHost.applyJsonFilter(null, "general", "filter", FilterAction.merge);
```
