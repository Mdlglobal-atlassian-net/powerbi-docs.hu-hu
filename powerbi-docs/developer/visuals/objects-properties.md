---
title: Objektum és tulajdonságok
description: Power BI-vizualizációk testreszabható tulajdonságai
author: MrMeison
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: c22a1cfb281c9902d490e2320b85c2f6bbb63468
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424608"
---
# <a name="object-and-properties"></a>Objektum és tulajdonságok

Az objektumok a vizualizációhoz társított testreszabható tulajdonságokat írják le.
Az objektumok több tulajdonsággal rendelkezhetnek, és mindegyik tulajdonsághoz tartozik egy típus.
A típusok azt jelzik, hogy mi lesz a tulajdonság. Alább további információt találhat a típusokról.

`myCustomObject` az objektumra a `dataView` és `enumerateObjectInstances` metóduson belüli hivatkozáshoz használt belső név

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

## <a name="display-name"></a>Megjelenített név

`displayName` a tulajdonságpanelen megjelenítendő név.

## <a name="properties"></a>Tulajdonságok

`properties` a fejlesztő által definiált tulajdonságok leképezése.

```json
"properties": {
    "myFirstProperty": {
        "displayName": "firstPropertyName",
        "type": ValueTypeDescriptor | StructuralTypeDescriptor
    }
}
```

> [!NOTE]
> A `show` speciális tulajdonság, amely az objektum ki-bekapcsolására alkalmas kapcsolót engedélyez.

Például:

```json
"properties": {
    "show": {
        "displayName": "My Property Switch",
        "type": {"bool": true}
    }
}
```

### <a name="property-types"></a>Tulajdonságtípusok

A tulajdonságtípusoknak két típusa van: `ValueTypeDescriptor` és `StructuralTypeDescriptor`.

#### <a name="value-type-descriptor"></a>Értéktípus-leíró

A `ValueTypeDescriptor` típusok többnyire primitívek, és általában statikus objektumokként vannak használva.
Az alábbiak például gyakori `ValueTypeDescriptor` típusok

```typescript
export interface ValueTypeDescriptor {
    text?: boolean;
    numeric?: boolean;
    integer?: boolean;
    bool?: boolean;
}
```

#### <a name="structural-type-descriptor"></a>Szerkezettípus-leíró

A `StructuralTypeDescriptor` típusokat többnyire adathoz kötött objektumokhoz használják.
A leggyakoribb `StructuralTypeDescriptor` a Fill (kitöltés)

```typescript
export interface StructuralTypeDescriptor {
    fill?: FillTypeDescriptor;
}
```

## <a name="gradient-property"></a>A Gradient (színátmenet) tulajdonság

A színátmenet tulajdonság nem állítható be standard tulajdonságként. Ehelyett egy szabályt kell felállítani a színválasztó tulajdonság (kitöltési típus) helyettesítésére.
Ez az alábbi példán látható:

```json
"properties": {
    "showAllDataPoints": {
        "displayName": "Show all",
        "displayNameKey": "Visual_DataPoint_Show_All",
        "type": {
            "bool": true
        }
    },
    "fill": {
        "displayName": "Fill",
        "displayNameKey": "Visual_Fill",
        "type": {
            "fill": {
                "solid": {
                    "color": true
                }
            }
        }
    },
    "fillRule": {
        "displayName": "Color saturation",
        "displayNameKey": "Visual_ColorSaturation",
        "type": {
            "fillRule": {}
        },
        "rule": {
            "inputRole": "Gradient",
            "output": {
                "property": "fill",
                    "selector": [
                        "Category"
                    ]
            }
        }
    }
}
```

Figyelje meg a `"fill"` és a `"fillRule"` tulajdonságot. Az első a színválasztó, a második a `visually` „fill” tulajdonság helyét a feltételek teljesülése esetén átvevő színátmenet helyettesítési szabálya.

A fill tulajdonság és a helyettesítési szabály közötti kapcsolatot a `"fillRule"` tulajdonság `"rule"`->`"output"` szakasza állítja be.

A `"Rule"`->`"InputRole"` állítja be, melyik adatszerepkör hozza működésbe a szabályt (feltétel). Ebben a példában ha a `"Gradient"` szerepkör adatokat tartalmaz, a szabály alkalmazva lesz a `"fill"` tulajdonságra.

Az alábbi példa a kitöltési szabályt (`the last item`) aktiváló adatszabályt mutatja be.

```json
{
    "dataRoles": [
            {
                "name": "Category",
                "kind": "Grouping",
                "displayName": "Details",
                "displayNameKey": "Role_DisplayName_Details"
            },
            {
                "name": "Series",
                "kind": "Grouping",
                "displayName": "Legend",
                "displayNameKey": "Role_DisplayName_Legend"
            },
            {
                "name": "Gradient",
                "kind": "Measure",
                "displayName": "Color saturation",
                "displayNameKey": "Role_DisplayName_Gradient"
            }
    ]
}
```

## <a name="enumerateobjectinstances-method"></a>Az `enumerateObjectInstances` metódus

Az objektumok hatékony használatához egy `enumerateObjectInstances` nevű függvényre lesz szükség az egyéni vizualizációban. Ez a függvény tölti fel objektumokkal a tulajdonságpanelt, és azt is meghatározza, hogy hová legyenek kötve az objektumok a DataView nézeten belül.  

Egy jellegzetes beállítás a következő:

```typescript
public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
    let objectName: string = options.objectName;
    let objectEnumeration: VisualObjectInstance[] = [];

    switch( objectName ) {
        case 'myCustomObject':
            objectEnumeration.push({
                objectName: objectName,
                properties: { ... },
                selector: { ... }
            });
            break;
    };

    return objectEnumeration;
}
```

### <a name="properties"></a>Tulajdonságok

A `enumerateObjectInstances` metódusban szereplő tulajdonságok a képességek között definiált tulajdonságokat tükrözik. Ez látható a lap alján található példában.

### <a name="objects-selector"></a>Az objektumokra vonatkozó selector

A `enumerateObjectInstances` metódusbeli selector határozza meg, hogy hová legyenek kötve az objektumok a dataView nézetben. Négy különböző lehetőség van.

#### <a name="static"></a>Statikus

Ez az objektum a `dataviews[index].metadata.objects` metaadatokhoz lesz kötve

```typescript
selector: null
```

#### <a name="columns"></a>oszlopok

Ez az objektum oszlopokhoz lesz kötve a megfelelő `QueryName` alapján.

```typescript
selector: {
    metadata: 'QueryName'
}
```

#### <a name="selector"></a>selector

Ez az objektum ahhoz az elemhez lesz kötve, amelyhez létre lett hozva `selectionID`. Ebben a példában feltételezzük, hogy egyes adatpontokhoz létrehoztunk `selectionID` azonosítókat, és ezeken lépkedünk végig ciklikusan.

```typescript
for (let dataPoint in dataPoints) {
    ...
    selector: dataPoint.selectionID.getSelector()
}
```

#### <a name="scope-identity"></a>Hatókör-identitás

Ez az objektum adott értékekhez lesz kötve csoportok egyesítésénél. Ha adottak például a `["Jan", "Feb", "March", ...]` kategóriák és a `["Small", "Medium", "Large"]` sorozat, szükség lehet egy objektumra a `Feb` és a `Large` érték találkozásánál. Ez elérhető úgy, hogy mindkét oszlop `DataViewScopeIdentity` értékét lekérdezzük, elhelyezzük az `identities` változóban, és ezt a szintaxist használjuk a selectorral.

```typescript
selector: {
    data: <DataViewScopeIdentity[]>identities
}
```

##### <a name="example"></a>Példa

Ez a példa azt mutatja be, milyen lenne egy objectEnumeration metódus egy customColor objektummal, amelynek egyetlen tulajdonsága a `fill`. A cél az, hogy ez az objektum statikusan legyen a `dataViews[index].metadata.objects` elemhez kötve

```typescript
objectEnumeration.push({
    objectName: "customColor",
    displayName: "Custom Color",
    properties: {
        fill: {
            solid: {
                color: dataPoint.color
            }
        }
    },
    selector: null
});
```
