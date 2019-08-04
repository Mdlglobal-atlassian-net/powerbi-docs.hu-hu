---
title: Adatnézet-leképezések
description: Hogyan alakítja át a Power BI az adatokat, mielőtt átadja őket a vizualizációknak
author: asander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: ff70b2f12921694617a736164484df1326471eea
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425183"
---
# <a name="data-view-mappings-in-power-bi-visuals"></a>Adatnézeti leképezések Power BI-vizualizációkban

A `dataViewMappings` azt írja le, hogy az adatszerepkörök hogyan kapcsolódnak egymáshoz, és lehetővé teszi a rájuk vonatkozó feltételes követelmények megadását is.
Minden `dataMappings` rendelkezik egy szakasszal.

Minden érvényes leképezés létrehoz egy `DataView`-t, de jelenleg egy vizualizációban csak egy lekérdezést támogatunk, így a legtöbb esetben csak egy `DataView` szerepel majd. Ugyanakkor több, különböző feltételekkel rendelkező adatleképezést is biztosíthat, amelyek lehetővé teszik a következőt

```json
"dataViewMappings": [
    {
        "conditions": [ ... ],
        "categorical": { ... },
        "single": { ... },
        "table": { ... },
        "matrix": { ... }
    }
]
```

> [!NOTE]
> Fontos megjegyezni, hogy Power BI kizárólag akkor hoz létre leképezést DataView-ra, ha az érvényes leképezés ki van töltve a `dataViewMappings`-ben.

Más szóval, ha a `categorical` definiálva van a `dataViewMappings`-ben, de más leképezések, például a `table` vagy a `single` nincs, a következő példához hasonlóan:
```json
"dataViewMappings": [
    {
        "categorical": { ... }
    }
]
```

A Power BI létrehoz egy `DataView`-t egyetlen `categorical` leképezéssel (a `table` és az egyéb leképezések `undefined` lesznek):
```javascript
{
    "categorical": {
        "categories": [ ... ],
        "values": [ ... ]
    },
    "metadata": { ... }
}
```

## <a name="conditions"></a>Feltételek

Egy adott adatleképezés feltételeit írja le. Több feltételcsoportot is megadhat, és ha az adat megfelel a feltételcsoportok valamelyikének, a vizualizáció érvényesként fogadja el az adathalmazt.

Jelenleg minden mezőnél megadhatja a minimum és a maximum értéket. Ez az adatszerepkörhöz köthető mezők számát jelöli. 

> [!NOTE]
> Ha a feltétel nem tartalmaz adatszerepkört, akkor tetszőleges számú mezővel rendelkezhet.

### <a name="example-1"></a>1\. példa

Több mezőt is áthúzhat az egyes adatszerepkörökbe. Ebben a példában a kategóriát egy adatmezőre korlátozzuk, a mértéket pedig két adatmezőre.

```json
"conditions": [
    { "category": { "max": 1 }, "y": { "max": 2 } },
]
```

### <a name="example-2"></a>2\. példa

Ebben a példában két feltétel egyikét kell megadnia. Vagy pontosan egy kategóriába tartozó adatmező és pontosan két mérték, vagy pedig pontosan két kategória és pontosan egy mérték.

```json
"conditions": [
    { "category": { "min": 1, "max": 1 }, "measure": { "min": 2, "max": 2 } },
    { "category": { "min": 2, "max": 2 }, "measure": { "min": 1, "max": 1 } }
]
```

## <a name="single-data-mapping"></a>Egyirányú adatleképezés

Az egyirányú adatleképezés az adatleképezés legegyszerűbb formája. Egyetlen mértékmezőt fogad el, és megadja a teljes értéket. Ha a mező numerikus, akkor az összeget adja. Ellenkező esetben az egyedi értékek számát adja.

Egyirányú adatleképezés használatához meg kell adnia a leképezni kívánt adatszerepkör nevét. Ez a leképezés csak egyetlen mértékmezővel működik. Ha hozzá van rendelve egy második mező, a rendszer nem hoz létre adatnézetet. ezért érdemes egy olyan feltételt is felvenni, amely egyetlen mezőre korlátozza az adatokat.

> [!NOTE]
> Ez az adatleképezés nem használható más adatleképezéssel együtt. A célja az, hogy egyetlen numerikus értékre csökkentse az adatokat.

### <a name="example-3"></a>3\. példa

```json
"dataViewMappings": {
    "conditions": [
        { "Y": { "max": 1 } }
    ],
    "single": {
        "role": "Y"
    }
}  
```

Az eredményül kapott adatnézet továbbra is tartalmazni fogja a többi típust (táblázatos, kategorikus stb.), de minden leképezés csak egyetlen értéket fog tartalmazni. Az ajánlott eljárás az, ha csak az egyedi értékhez fér hozzá.

```JSON
{
    "dataView": [
        {
            "metadata": null,
            "categorical": null,
            "matrix": null,
            "table": null,
            "tree": null,
            "single": {
                "value": 94163140.3560001
            }
        }
    ]
}
```

## <a name="categorical-data-mapping"></a>Kategorikus adatleképezés

A kategorikus adatleképezés használatával egy vagy két független adatcsoportot lehet beolvasni.

### <a name="example-4"></a>4\. példa

Itt látható a definíció, amelyet az adatszerepkörökről szóló előző példában láttunk.

```json
"dataRole":[
    {
        "displayName": "Category",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Y Axis",
        "name": "measure",
        "kind": "Measure"
    }
]
```

A leképezés pedig:

```json
"dataViewMappings": {
    "categorical": {
        "categories": {
            "for": { "in": "category" }
        },
        "values": {
            "select": [
                { "bind": { "to": "measure" } }
            ]
        }
    }
}
```

Ez egy egyszerű példa, amely egyszerű szavakkal fogalmazva így néz ki: „Képezd le a `category` adatszerepkörömet úgy, hogy minden olyan mezőnél, amelyet áthúzok a `category` területre, a mező adatai a `categorical.categories`-ra legyenek leképezve. A `measure` adatszerepkörömet pedig képezd le a `categorical.values`-ra.”

* **for...in** – Ebben az adatszerepkörben minden elemet vegyen fel az adatlekérdezésbe.
* **bind...to** – Ugyanazt az eredményt adja, mint a for...in, azonban azt várja, hogy a DataRole feltétele egyetlen mezőre lesz korlátozva.

### <a name="example-5"></a>5\. példa

Ebben a példában az előző példában szereplő első két DataRoles-t fogjuk használni, továbbá definiálni fogjuk a `grouping` és a `measure2` mezőket.

```json
"dataRole":[
    {
        "displayName": "Category",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Y Axis",
        "name": "measure",
        "kind": "Measure"
    },
    {
        "displayName": "Grouping with",
        "name": "grouping",
        "kind": "Grouping"
    },
    {
        "displayName": "X Axis",
        "name": "measure2",
        "kind": "Grouping"
    }
]
```

A leképezés pedig:

```json
"dataViewMappings":{
    "categorical": {
        "categories": {
            "for": { "in": "category" }
        },
        "values": {
            "group": {
                "by": "grouping",
                "select":[
                    { "bind": { "to": "measure" } },
                    { "bind": { "to": "measure2" } }
                ]
            }
        }
    }
}
```

Itt a különbség a categorical.values leképezése lesz. Itt azt mondjuk, hogy „Képezd le a `measure` és a `measure2` adatszerepkört úgy, hogy a `grouping` adatszerepkör alapján legyenek csoportosítva.”

### <a name="example-6"></a>6\. példa

Itt vannak az adatszerepkörök.

```json
"dataRoles": [
    {
        "displayName": "Categories",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Measures",
        "name": "measure",
        "kind": "Measure"
    },
    {
        "displayName": "Series",
        "name": "series",
        "kind": "Measure"
    }
]
```

Ez pedig a dataViewMapping.

```json
"dataViewMappings": [
    {
        "categorical": {
            "categories": {
                "for": {
                    "in": "category"
                }
            },
            "values": {
                "group": {
                    "by": "series",
                    "select": [{
                            "for": {
                                "in": "measure"
                            }
                        }
                    ]
                }
            }
        }
    }
]
```

A kategorikus `dataview` a következőképpen jeleníthető meg.

| Kategorikus |  |  | | | |
|-----|-----|------|------|------|------|
| | Év | 2013 | 2014 | 2015 | 2016 |
| Ország | | |
| USA | | x | x | 125 | 100 |
| Kanada | | x | 50 | 200 | x |
| Mexikó | | 300 | x | x | x |
| Egyesült Királyság | | x | x | 75 | x |

A Power BI ezt kategorikus adatnézetként fogja létrehozni. Ez a kategóriák csoportja.

```JSON
{
    "categorical": {
        "categories": [
            {
                "source": {...},
                "values": [
                    "Canada",
                    "Mexico",
                    "UK",
                    "USA"
                ],
                "identity": [...],
                "identityFields": [...],
            }
        ]
    }
}
```

Minden kategória egy értékcsoportra van leképezve. Az értékek mindegyike sorozat alapján van csoportosítva, ami itt az éveket jelenti.

Például Kanada értékesítése 2013-ra null értékű, 2014-re pedig 50.

```JSON
{
    "values": [
        {
            "source": {...},
            "values": [
                null,
                300,
                null,
                null
            ],
            "identity": [...],
        },
        {
            "source": {...},
            "values": [
                50,
                null,
                150,
                null
            ],
            "identity": [...],
        },
        {
            "source": {...},
            "values": [
                200,
                null,
                null,
                125
            ],
            "identity": [...],
        },
        {
            "source": {...},
            "values": [
                null,
                null,
                null,
                100
            ],
            "identity": [...],
        }
    ]
}
```

## <a name="table-data-mapping"></a>Táblázatos adatleképezés

A táblázatos adatnézet egy egyszerű adatleképezés. Ez lényegében adatpontok listája, ahol a numerikus adatpontok összesíthetőek.

### <a name="example-7"></a>7\. példa

A megadott képességekkel:

```json
"dataRoles": [
    {
        "displayName": "Values",
        "name": "values",
        "kind": "Measure"
    }
]
```

```json
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                }
            }
        }
    }
]
```

A táblázatos `dataview` a következőképpen jeleníthető meg.  

| Ország| Év | Értékesítés |
|-----|-----|------|
| USA | 2016 | 100 |
| USA | 2015 | 50 |
| Kanada | 2015 | 200 |
| Kanada | 2015 | 50 |
| Mexikó | 2013 | 300 |
| Egyesült Királyság | 2014 | 150 |
| USA | 2015 | 75 |

A Power BI ezt táblázatos adatnézetként fogja létrehozni. Rendezés nem feltétlenül van.

```JSON
{
    "table" : {
        "columns": [...],
        "rows": [
            [
                "Canada",
                2014,
                50
            ],
            [
                "Canada",
                2015,
                200
            ],
            [
                "Mexico",
                2013,
                300
            ],
            [
                "UK",
                2014,
                150
            ],
            [
                "USA",
                2015,
                100
            ],
            [
                "USA",
                2015,
                75
            ],
            [
                "USA",
                2016,
                100
            ]
        ]
    }
}
```

Az adatokat összesíteni lehet a kívánt mező kiválasztásával, majd a Sum (összeg) lehetőségre kattintva.  

![Adatösszesítés](./media/data-aggregation.png)

## <a name="matrix-data-mapping"></a>Mátrixos adatleképezés

A mátrixos adatleképezés hasonló a táblázatos adatleképezéshez, de a sorok hierarchikusan jelennek meg. Az `dataRole` értékek egyike pedig oszlop fejlécének értékeként is használható.

```json
{
    "dataRoles": [
        {
            "name": "Category",
            "displayName": "Category",
            "displayNameKey": "Visual_Category",
            "kind": "Grouping"
        },
        {
            "name": "Column",
            "displayName": "Column",
            "displayNameKey": "Visual_Column",
            "kind": "Grouping"
        },
        {
            "name": "Measure",
            "displayName": "Measure",
            "displayNameKey": "Visual_Values",
            "kind": "Measure"
        }
    ],
    "dataViewMappings": [
        {
            "matrix": {
                "rows": {
                    "for": {
                        "in": "Category"
                    }
                },
                "columns": {
                    "for": {
                        "in": "Column"
                    }
                },
                "values": {
                    "select": [
                        {
                            "for": {
                                "in": "Measure"
                            }
                        }
                    ]
                }
            }
        }
    ]
}
```

A Power BI hierarchikus adatstruktúrát hoz létre. A fa gyökerében a `Category` adatszerepkör első oszlopában található adatok szerepelnek az adatszerepkör második oszlopában lévő gyermekekkel.

Adatkészlet:

| Szülők | Gyermekek | Unokák | Oszlopok | Értékek |
|-----|-----|------|-------|-------|
| Parent1 | Child1 | Grand child1 | Col1 | 5 |
| Parent1 | Child1 | Grand child1 | Col2 | 6 |
| Parent1 | Child1 | Grand child2 | Col1 | 7 |
| Parent1 | Child1 | Grand child2 | Col2 | 8 |
| Parent1 | Child2 | Grand child3 | Col1 | 5 |
| Parent1 | Child2 | Grand child3 | Col2 | 3 |
| Parent1 | Child2 | Grand child4 | Col1 | 4 |
| Parent1 | Child2 | Grand child4 | Col2 | 9 |
| Parent1 | Child2 | Grand child5 | Col1 | 3 |
| Parent1 | Child2 | Grand child5 | Col2 | 5 |
| Parent2 | Child3 | Grand child6 | Col1 | 1 |
| Parent2 | Child3 | Grand child6 | Col2 | 2 |
| Parent2 | Child3 | Grand child7 | Col1 | 7 |
| Parent2 | Child3 | Grand child7 | Col2 | 1 |
| Parent2 | Child3 | Grand child8 | Col1 | 10 |
| Parent2 | Child3 | Grand child8 | Col2 | 13 |

Power BI Core Matrix vizualizációja ezt táblázatként jeleníti meg.

![Mátrix vizualizáció](./media/matrix-visual-smaple.png)

A vizualizáció az alább leírtak szerint kapja meg az adatszerkezetet (csak az első két sor jelenik meg):

```json
{
    "metadata": {...},
    "matrix": {
        "rows": {
            "levels": [...],
            "root": {
                "childIdentityFields": [...],
                "children": [
                    {
                        "level": 0,
                        "levelValues": [...],
                        "value": "Parent1",
                        "identity": {...},
                        "childIdentityFields": [...],
                        "children": [
                            {
                                "level": 1,
                                "levelValues": [...],
                                "value": "Child1",
                                "identity": {...},
                                "childIdentityFields": [...],
                                "children": [
                                    {
                                        "level": 2,
                                        "levelValues": [...],
                                        "value": "Grand child1",
                                        "identity": {...},
                                        "values": {
                                            "0": {
                                                "value": 5 // value for Col1
                                            },
                                            "1": {
                                                "value": 6 // value for Col2
                                            }
                                        }
                                    },
                                    ...
                                ]
                            },
                            ...
                        ]
                    },
                    ...
                ]
            }
        },
        "columns": {
            "levels": [...],
            "root": {
                "childIdentityFields": [...],
                "children": [
                    {
                        "level": 0,
                        "levelValues": [...],
                        "value": "Col1",
                        "identity": {...}
                    },
                    {
                        "level": 0,
                        "levelValues": [...],
                        "value": "Col2",
                        "identity": {...}
                    },
                    ...
                ]
            }
        },
        "valueSources": [...]
    }
}
```

## <a name="data-reduction-algorithm"></a>Adatcsökkentési algoritmus

A `DataReductionAlgorithm` akkor alkalmazható, ha szabályozni szeretné a DataView által fogadott adatmennyiséget.

Alapértelmezés szerint minden egyéni vizualizációnál alkalmazva van a top DataReductionAlgorithm, és a „Count” értéke 1000 adatpontra van beállítva. Ez egyenértékű a következő tulajdonságok beállításával a capabilities.json fájlban:

```json
"dataReductionAlgorithm": {
    "top": {
        "count": 1000
    }
}
```

A „Count” értékét tetszőleges egész számra módosíthatja, amely akár 30000 is lehet. Az R-alapú egyéni vizualizációk akár 150000 sort is támogatnak.

## <a name="data-reduction-algorithm-types"></a>Az adatcsökkentési algoritmusok típusai

A `DataReductionAlgorithm` beállításainak négyféle típusa létezik:

* `top` – Ha korlátozni kívánja az adatokat az adatkészlet elejétől kapott értékekre. Az első „count” számú érték lesz felhasználva az adatkészletből.
* `bottom` – Ha korlátozni kívánja az adatokat az adatkészlet végéről kapott értékekre. Az utolsó „count” számú érték lesz felhasználva az adatkészletből.
* `sample` – csökkenti az adatkészletet egy egyszerű mintavételezési algoritmussal, amely „count” számú elemre korlátozódik. Ez azt jelenti, hogy az első és az utolsó elem is szerepel, és a köztük lévő elemek száma „count” lesz, melyek között egyenlő távolság lesz.
Például ha van egy adatkészlete [0, 1, 2,... 100], és egy `count: 9` beállítása, akkor a következő értékeket fogja kapni: [0, 10, 20... 100]
* `window` - egyszerre egy „Count” számú elemet tartalmazó „ablakot” tölt be. Jelenleg a `top` és a `window` egyenértékű. Folyamatban van egy ablakkezelő-beállítás teljes körű támogatása.

## <a name="data-reduction-algorithm-usage"></a>Az adatcsökkentési algoritmusok használata

A `DataReductionAlgorithm` használható a kategorikus, a tábla vagy a mátrix típusú `dataview`-leképezésben.

Beállítható `categories` és/vagy `values` csoportszakaszaira a kategorikus adatleképezéshez.

### <a name="example-8"></a>8\. példa

```json
"dataViewMappings": {
    "categorical": {
        "categories": {
            "for": { "in": "category" },
            "dataReductionAlgorithm": {
                "window": {
                    "count": 300
                }
            }  
        },
        "values": {
            "group": {
                "by": "series",
                "select": [{
                        "for": {
                            "in": "measure"
                        }
                    }
                ],
                "dataReductionAlgorithm": {
                    "top": {
                        "count": 100
                    }
                }  
            }
        }
    }
}
```

Az adatcsökkentési algoritmus alkalmazható egy táblázat `dataview`-leképezésének `rows` szakaszára.

### <a name="example-9"></a>9\. példa

```json
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                },
                "dataReductionAlgorithm": {
                    "top": {
                        "count": 2000
                    }
                } 
            }
        }
    }
]
```

Az adatcsökkentési algoritmus alkalmazható egy `matrix` `dataview`-leképezésének `rows` vagy `columns` szakaszára.
