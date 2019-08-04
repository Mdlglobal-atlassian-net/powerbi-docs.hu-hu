---
title: Funkciók
description: A Power BI-vizualizációk funkciói és tulajdonságai
author: asander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: f6bb4293a44f98f2f8098fb197c7b406b618d211
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425459"
---
# <a name="power-bi-visual-capabilities"></a>A Power BI-vizualizációk funkciói

A funkciók a vizualizációval kapcsolatos információkat közlik a gazdagéppel. A Funkciók modell tulajdonságai mind `optional`

A vizualizációk funkcióinak gyökérobjektumai a `dataRoles`, `dataViewMappings`és így tovább.

```json
{
    "dataRoles": [ ... ],
    "dataViewMappings": [ ... ],
    "objects":  { ... },
    "supportsHighlight": true|false,
    "advancedEditModeSupport": 0|1|2,
    "sorting": { ... }
}

```

## <a name="define-the-data-fields-your-visual-expects---dataroles"></a>Adja meg a vizualizáció által várt adatmezőket – `dataRoles`

Az adatokhoz köthető mezők definiálásához a `dataRoles` elemet használjuk, amely `DataViewRole`-objektumok egy tömbjét veszi alapul, és meghatározza a szükséges tulajdonságokat.

### <a name="properties"></a>Tulajdonságok

* **name** – az adatmező belső neve (egyedinek kell lennie)
* **kind** – a mező jellege:
    * `Grouping` – A mértékmezők csoportosításához használt, különálló értékek
    * `Measure` – Numerikus adatértékek
    * `GroupingOrMeasure` – Csoportosításként vagy mértékként is használható
* **displayName** – a Tulajdonságok panelen a felhasználó számára megjelenő név
* **description** – a mező rövid leírása (választható)
* **requiredTypes** – az adatszerepkörhöz szükséges adattípus. A nem egyező értékek null értékre lesznek állítva (választható)
* **preferredTypes** – az adatszerepkörhöz választott adattípus (választható)

### <a name="valid-data-types-in-requiredtypes-and-preferredtypes"></a>A „requiredTypes” és a „preferredTypes” érvényes adattípusai

* **bool** – logikai érték
* **integer** – egész szám értéke
* **numeric** – numerikus érték
* **text** – szöveges érték
* **geography** – földrajzi adatok

### <a name="example"></a>Példa

```json
"dataRoles": [
    {
        "displayName": "My Category Data",
        "name": "myCategory",
        "kind": "Grouping",
        "requiredTypes": [
            {
                "text": true
            },
            {
                "numeric": true
            },
            {
                "integer": true
            }
        ],
        "preferredTypes": [
            {
                "text": true
            }
        ]
    },
    {
        "displayName": "My Measure Data",
        "name": "myMeasure",
        "kind": "Measure",
        "requiredTypes": [
            {
                "integer": true
            },
            {
                "numeric": true
            }
        ],
        "preferredTypes": [
            {
                "integer": true
            }
        ]
    },
    {
        "displayNameKey": "Visual_Location",
        "name": "Locations",
        "kind": "Measure",
        "displayName": "Locations",
        "requiredTypes": [
            {
                "geography": {
                    "address": true
                }
            },
            {
                "geography": {
                    "city": true
                }
            },
            {
                "geography": {
                    "continent": true
                }
            },
            {
                "geography": {
                    "country": true
                }
            },
            {
                "geography": {
                    "county": true
                }
            },
            {
                "geography": {
                    "place": true
                }
            },
            {
                "geography": {
                    "postalCode": true
                }
            },
            {
                "geography": {
                    "region": true
                }
            },
            {
                "geography": {
                    "stateOrProvince": true
                }
            }
        ]
    }
]
```

A fenti adatszerepkörök a következő mezőket hozzák létre

![Megjelenített adatszerepkör](./media/data-role-display.png)

## <a name="define-how-you-want-the-data-mapped---dataviewmappings"></a>Az adatleképezés módjának megadása – `dataViewMappings`

A DataViewMapping azt írja le, hogy az adatszerepkörök hogyan kapcsolódnak egymáshoz, és lehetővé teszi a rájuk vonatkozó feltételes követelmények megadását is.

A legtöbb vizualizáció egyetlen leképezést biztosít, Ön azonban több dataViewMappings elemet is megadhat. Minden érvényes leképezés létrehoz egy DataView elemet eredményez. 

```json
"dataViewMappings": [
    {
        "conditions": [ ... ],
        "categorical": { ... },
        "table": { ... },
        "single": { ... },
        "matrix": { ... }
    }
]
```

[További információ a DataViewMappings elemekről](dataview-mappings.md)

## <a name="define-property-pane-options---objects"></a>A Tulajdonságok panel beállításainak meghatározása – `objects`

Az objektumok a vizualizációhoz társított testreszabható tulajdonságokat írják le.
Az objektumok több tulajdonsággal rendelkezhetnek, és mindegyik tulajdonsághoz tartozik egy típus.
A típusok azt jelzik, hogy mi lesz a tulajdonság. Alább további információt találhat a típusokról.

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

[További információ az objektumokról](objects-properties.md)

## <a name="handle-partial-highlighting---supportshighlight"></a>Részleges kiemelés kezelése – `supportsHighlight`

Alapértelmezés szerint ez az érték false (hamis), ami azt jelenti, hogy az „Értékek” terület automatikusan szűrve lesz, ha Ön kijelöl valamit az oldalon. Ez frissíti a vizualizációt, és csak a kijelölt értéket jeleníti meg. Ha meg szeretné jeleníteni az összes adatot, azonban csak a kijelölt elemeket szeretné kiemelni, a `supportsHighlight` elem értékét igazra kell állítania a capabilities.json fájlban.

[További információ a kiemelésről](highlight.md)

## <a name="handle-advanced-edit-mode---advancededitmodesupport"></a>Speciális szerkesztési mód kezelése – `advancedEditModeSupport`

A vizualizációk támogathatják a Speciális szerkesztési módot.
Alapértelmezés szerint a vizualizációk nem támogatják a Speciális szerkesztési módot, kivéve, ha a capabilities.json fájl máshogy nem szabja meg.

[További információ az advancedEditModeSupport beállításról](advanced-edit-mode.md)

## <a name="data-sorting-options-for-visual---sorting"></a>Adatrendezési beállítások a vizualizációhoz – `sorting`

A vizualizációk a funkcióikkal definiálhatják rendezési viselkedésüket.
Alapértelmezés szerint a vizualizáció nem támogatja a rendezési sorrend módosítását, kivéve, ha a capabilities.json fájl máshogy nem szabja meg.

[További információ a rendezésről](sort-options.md)
