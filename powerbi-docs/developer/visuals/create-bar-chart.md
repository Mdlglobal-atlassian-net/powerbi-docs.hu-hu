---
title: Sávdiagram készítése
description: Ez az útmutató lépésről lépésre mutatja be, hogyan lehet létrehozni egy egyszerű Power BI sávdiagramos vizualizációt kód használatával.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 05/01/2020
ms.openlocfilehash: 0f8f97e5f707e813d316ae4d5388f0793f8c1aa0
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83149079"
---
# <a name="build-a-bar-chart"></a>Sávdiagram készítése

Ez a cikk lépésről lépésre mutatja be, hogyan lehet létrehozni egy minta Power BI sávdiagramos vizualizációt kód használatával. A teljes kódpélda itt érhető el: [https://github.com/Microsoft/PowerBI-visuals-sampleBarChart](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart).

## <a name="view-model"></a>Nézetmodell
Először is meg kell határozni a sávdiagram nézetmodelljét, és a vizualizáció készítése során iterálással ellenőrizni kell, hogy mi jelenik meg.

```typescript
/**
 * Interface for BarCharts viewmodel.
 *
 * @interface
 * @property {BarChartDataPoint[]} dataPoints - Set of data points the visual will render.
 * @property {number} dataMax                 - Maximum data value in the set of data points.
 */
interface BarChartViewModel {
    dataPoints: BarChartDataPoint[];
    dataMax: number;
};

/**
 * Interface for BarChart data points.
 *
 * @interface
 * @property {number} value    - Data value for the point.
 * @property {string} category - Corresponding category of the data value.
 */
interface BarChartDataPoint {
    value: number;
    category: string;
};
```

### <a name="use-static-data"></a>Statikus adatok használata

A statikus adatok használata remek módja a vizualizáció adatkötés nélküli tesztelésének. A nézetmodell akkor sem változik, ha egy későbbi lépésben adatkötést ad hozzá.

```typescript
let testData: BarChartDataPoint[] = [
    {
        value: 10,
        category: 'a'
    },
    {
        value: 20,
        category: 'b'
    },
    {
        value: 1,
        category: 'c'
    },
    {
        value: 100,
        category: 'd'
    },
    {
        value: 500,
        category: 'e'
    }];

let viewModel: BarChartViewModel = {
    dataPoints: testData,
    dataMax: d3.max(testData.map((dataPoint) => dataPoint.value))
};
```

## <a name="data-binding"></a>Adatkötés 
Az adatkötés hozzáadásához meg kell határozni a vizualizáció képességeit a *capabilities.json* fájlban. A mintakód már tartalmaz egy sémát, amelyet használhat.

Az adatkötés egy **Mező** szakaszban fut a Power BI-ban.

![Adatkötés egy Mező szakaszban](./media/create-bar-chart/data-binding.png)

### <a name="add-data-roles"></a>Adatszerepkörök hozzáadása
A mintakód már tartalmaz adatszerepköröket, de ezek testreszabhatók.

- A `displayName` a **Mező** szakaszban látható név.
- A `name` az adatszerepkörre való hivatkozáshoz használt belső név.
- A `kind` a mező altípusára vonatkozik. A *Csoportosítás* mezők (0) különálló értékekkel rendelkeznek. A *Mérték* mezők (1) numerikus adatértékekkel rendelkeznek.

```json
"dataRoles": [
    {
        "displayName": "Category Data",
        "name": "category",
        "kind": 0
    },
    {
        "displayName": "Measure Data",
        "name": "measure",
        "kind": 1
    }
],
```

További információért tekintse meg az [adatszerepköröket](./capabilities.md#define-the-data-fields-that-your-visual-expects-dataroles) ismertető részt.

### <a name="add-conditions-to-dataviewmapping"></a>DataViewMapping-feltételek hozzáadása
A `dataViewMappings`-ben feltételek meghatározásával adható meg, hogy az egyes mezőszakaszok hány mezőt köthetnek össze. Az egyes mezőkre az adatszerepkör belső `name` elemének használatával lehet hivatkozni.

```json
    "dataViewMappings": [
        {
            "conditions": [
                {
                    "category": {
                        "max": 1
                    },
                    "measure": {
                        "max": 1
                    }
                }
            ],
        }
    ]
```

További információért tekintse meg az [adatnézet-leképezést](./dataview-mappings.md) ismertető részt.

### <a name="define-and-use-visualtransform"></a>A visualTransform meghatározása és használata
A `DataView` az a struktúra, amelyet a Power BI biztosít a vizualizációhoz, és amely a megjeleníteni kívánt, lekérdezett adatokat tartalmazza. A `DataView` azonban különbözőképpen, például kategorikus vagy táblázatos formában is biztosíthatja az adatokat. Kategorikus vizualizáció, például sávdiagram létrehozásához csak a `DataView` kategorikus tulajdonságát kell használni. A `visualTransform` definiálása lehetővé teszi a `DataView` átalakítását a vizualizáció által használt nézetmodellbe.

A színek hozzárendelése és az egyes adatpontok definiálásakor való kiválasztása az `IVisualHost` használatával lehetséges. 

```typescript
/**
 * Function that converts queried data into a view model that will be used by the visual
 *
 * @function
 * @param {VisualUpdateOptions} options - Contains references to the size of the container
 *                                        and the dataView which contains all the data
 *                                        the visual had queried.
 * @param {IVisualHost} host            - Contains references to the host which contains services
 */
function visualTransform(options: VisualUpdateOptions, host: IVisualHost): BarChartViewModel {
    /*Convert dataView to your viewModel*/
}

```

## <a name="color"></a>Szín 
A szín az `IVisualHost` egyik szolgáltatásaként érhető el.

### <a name="add-color-to-data-points"></a>Szín hozzáadása az adatpontokhoz
Minden egyes adatpontot más szín jelöl. A színt a `BarChartDataPoint` felülethez kell hozzáadni.

```typescript
/**
 * Interface for BarChart data points.
 *
 * @interface
 * @property {number} value    - Data value for the point.
 * @property {string} category - Corresponding category of the data value.
 * @property {string} color    - Color corresponding to the data point.
 */
interface BarChartDataPoint {
    value: number;
    category: string;
    color: string;
};
```

### <a name="the-colorpalette-service"></a>A colorPalette szolgáltatás
A `colorPalette` szolgáltatással kezelhetők a vizualizációban használt színek. A példány az `IVisualHost` használatával érhető el.

### <a name="assign-color-to-data-points"></a>Szín hozzárendelése az adatpontokhoz
A `visualTransform` a megadott definíció szerint a `dataView` átkonvertálásával a sávdiagram által használható nézetmodellt hoz létre. Mivel a `visualTransform` esetében az adatpontokon keresztül végzi az iterálást, ez az ideális hely a színek hozzárendelésére is.

```typescript
let colorPalette: IColorPalette = host.colorPalette; // host: IVisualHost
for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
    barChartDataPoints.push({
        category: category.values[i],
        value: dataValue.values[i],
        color: colorPalette.getColor(category.values[i]).value,
    });
}
```

## <a name="selection-and-interactions"></a>Kiválasztás és interakciók
A kiválasztás révén a felhasználó az Ön és mások vizualizációival is interakcióba léphet. 

### <a name="add-selection-to-each-data-point"></a>Kiválasztás hozzáadása az egyes adatpontokhoz
Mivel minden adatpont egyedi, mindegyikhez adjon hozzá kijelölést. A kijelölés tulajdonságot a `BarChartDataPoint` felületen lehet hozzáadni.

```typescript
/**
 * Interface for BarChart data points.
 *
 * @interface
 * @property {number} value             - Data value for the point.
 * @property {string} category          - Corresponding category of data value.
 * @property {string} color             - Color corresponding to data point.
 * @property {ISelectionId} selectionId - Id assigned to data point for cross filtering
 *                                        and visual interaction.
 */
interface BarChartDataPoint {
    value: number;
    category: string;
    color: string;
    selectionId: ISelectionId;
};
```

### <a name="assign-selection-ids-to-each-data-point"></a>Kiválasztási azonosítók hozzáadása az egyes adatpontokhoz
Mivel a `visualTransform`-ban halad végig iterálással az összes adatponton, ez ideális hely a kiválasztási azonosítók létrehozására is. A gazdagép változója egy `IVisualHost`, amely a vizualizációhoz használható szolgáltatásokat, például szín- vagy kiválasztásszerkesztőt tartalmaz. 

A `createSelectionIdBuilder` példányosító metódust az `IVisualHost`-on használva hozzon létre egy új kiválasztási azonosítót. Az egyes adatpontokhoz új kiválasztásszerkesztőt kell létrehozni.

Mivel csak a kategórián alapuló kiválasztást végez, csak a `withCategory` kiválasztásokat kell meghatároznia.

```typescript
for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
    barChartDataPoints.push({
        category: category.values[i],
        value: dataValue.values[i],
        color: colorPalette.getColor(category.values[i]).value,
        selectionId: host.createSelectionIdBuilder()
            .withCategory(category, i)
            .createSelectionId()
    });
}
```

További információért lásd [a kiválasztásszerkesztő példányának létrehozását](./selection-api.md#create-an-instance-of-the-selection-builder) ismertető részt.

### <a name="interact-with-data-points"></a>Az adatpontokkal végzett interakció
A sávdiagram összes sávját kezelheti, ha az adatponthoz hozzá van rendelve egy kiválasztási azonosító. A sávdiagram a `click` eseményeket figyeli.

A `selectionManager` példányosító metódust az `IVisualHost`-on használva hozzon létre egy kiválasztáskezelőt a keresztszűrés és a kiválasztások törlésének engedélyezéséhez.

```typescript
let selectionManager = this.selectionManager;

//This must be an anonymous function instead of a lambda because
//d3 uses 'this' as the reference to the element that was clicked.
bars.on('click', function(d) {
    selectionManager.select(d.selectionId).then((ids: ISelectionId[]) => {
        bars.attr({
            'fill-opacity': ids.length > 0 ? BarChart.Config.transparentOpacity : BarChart.Config.solidOpacity
        });

        d3.select(this).attr({
            'fill-opacity': BarChart.Config.solidOpacity
        });
    });

    (<Event>d3.event).stopPropagation();
});
```

A további részletek [a SelectionManager használatáról szóló szakaszban](./selection-api.md#how-to-use-selectionmanager-to-select-data-points) érhetők el.

## <a name="static-objects"></a>Statikus objektumok

A vizualizáció további testreszabása érdekében objektumokat adhat hozzá a **Tulajdonság** ablaktáblához. A testreszabások közé a felhasználói felület módosításai vagy a lekérdezett adatokhoz kapcsolódó módosítások tartoznak. A minta statikus objektumokat használ a sávdiagram x tengelyének megjelenítéséhez.

Az objektumokat a **Tulajdonság** ablaktáblán lehet be- és kikapcsolni.

![Objektumok a Tulajdonságok ablaktáblán](./media/create-bar-chart/property-pane.png)

### <a name="define-objects-in-capabilities"></a>Objektumok meghatározása képességekben
Határozzon meg egy `objects` tulajdonságot a *capabilities.json* fájlban a **Tulajdonság** ablaktáblán megjelenítendő objektumokhoz.
- Az `enableAxis` a `dataView` által hivatkozott belső név. 
- A `displayName` a **Tulajdonság** ablaktáblán megjelenő név.
- A `bool` egy primitív érték, amelyet általában statikus objektumok, például szövegmezők vagy kapcsolók esetében használnak.
- A `show` a `properties` egyik különleges tulajdonsága, amely az objektumra vonatkozóan engedélyezi a `show` kapcsolót. Mivel a `show` egy kapcsoló, a típusa szerint `bool`.

![Objektumon engedélyezett show kapcsoló](./media/create-bar-chart/object-show-property.png)

```typescript
"objects": {
    "enableAxis": {
        "displayName": "Enable Axis",
        "properties": {
            "show": {
                "displayName": "Enable Axis",
                "type": { "bool": true }
            }
        }
    }
}
```

További információt [az objektumokkal foglalkozó szakaszban](./objects-properties.md) talál.

### <a name="define-property-settings"></a>Tulajdonságbeállítások meghatározása

A következő szakaszok a tulajdonságbeállítások meghatározásának alapelveit mutatják be. Használhatja a `powerbi-visuals-utils-dataviewutils` csomagban meghatározott segédeszközosztályokat is a tulajdonságbeállítások meghatározásához. További információt a [DataViewObjectsParser](https://github.com/Microsoft/powerbi-visuals-utils-dataviewutils/blob/master/docs/api/data-view-objects-parser.md) osztály dokumentációjában és mintáiban talál.


Bár nem kötelező, érdemes a legtöbb beállítást egyetlen objektumra honosítani az egyszerű hivatkozás érdekében.

```typescript
/**
 * Interface for BarCharts viewmodel.
 *
 * @interface
 * @property {BarChartDataPoint[]} dataPoints - Set of data points the visual will render.
 * @property {number} dataMax                 - Maximum data value in the set of data points.
 * @property {BarChartSettings} settings      - Object property settings
 */
interface BarChartViewModel {
    dataPoints: BarChartDataPoint[];
    dataMax: number;
    settings: BarChartSettings;
};

/**
 * Interface for BarChart settings.
 *
 * @interface
 * @property "show" enableAxis - Object property that allows axis to be enabled.
 */
interface BarChartSettings {
    enableAxis: {
        show: boolean;
    };
}
```

### <a name="define-and-use-objectenumerationutility"></a>Az ObjectEnumerationUtility meghatározása és használata
Az objektum-tulajdonságértékek a `dataView` metaadataiként érhetők el, de nincs olyan szolgáltatás, amely segítene a tulajdonságok lekérésében. Az `ObjectEnumerationUtility` olyan statikus függvények készlete, amelyekkel lekérheti az objektumok értékeit a `dataView`-ból, illetve más vizualizációs projektekhez is használható. Az `ObjectEnumerationUtility` használata nem kötelező, de remek eszköz a `dataView` alkalmazásával végzett iterálás során az objektum tulajdonságainak lekéréséhez.

```typescript
/**
 * Gets property value for a particular object.
 *
 * @function
 * @param {DataViewObjects} objects - Map of defined objects.
 * @param {string} objectName       - Name of desired object.
 * @param {string} propertyName     - Name of desired property.
 * @param {T} defaultValue          - Default value of desired property.
 */
export function getValue<T>(objects: DataViewObjects, objectName: string, propertyName: string, defaultValue: T ): T {
    if(objects) {
        let object = objects[objectName];
        if(object) {
            let property: T = object[propertyName];
            if(property !== undefined) {
                return property;
            }
        }
    }
    return defaultValue;
}
```

A forráskód az [objectEnumerationUtility.ts](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/objectEnumerationUtility.ts) fájlban található.

### <a name="retrieve-property-values-from-dataview"></a>Tulajdonságértékek lekérése a dataView-ból
A `visualTransform` ideális hely a vizualizáció nézetmodelljének kezeléséhez. A minta folytatásához kérje le az objektum tulajdonságait a `dataView`-ból.

Határozza meg a tulajdonság alapértelmezett állapotát, és a `getValue` használatával kérje le a tulajdonságot a `dataView`-ból.

```typescript
let defaultSettings: BarChartSettings = {
    enableAxis: {
        show: false,
    }
};

let barChartSettings: BarChartSettings = {
    enableAxis: {
        show: getValue<boolean>(objects, 'enableAxis', 'show', defaultSettings.enableAxis.show),
    }
}
```

### <a name="populate-property-pane-with-enumerateobjectinstances"></a>A Tulajdonság ablaktábla feltöltése az enumerateObjectInstances alkalmazásával
Az `IVisual` esetében választható `enumerateObjectInstances` metódus számba veszi az összes objektumot, és elhelyezi őket a **Tulajdonság** ablaktáblán. Az egyes objektumok meghívása az `enumerateObjectInstances` használatával történik. Az objektum neve az `EnumerateVisualObjectInstancesOptions` révén érhető el.

A tulajdonságot minden objektum esetében az aktuális állapota szerint kell meghatározni.

```typescript
/**
 * Enumerates through the objects defined in the capabilities and adds the properties to the format pane
 *
 * @function
 * @param {EnumerateVisualObjectInstancesOptions} options - Map of defined objects
 */
public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
    let objectName = options.objectName;
    let objectEnumeration: VisualObjectInstance[] = [];

    switch(objectName) {
        case 'enableAxis':
            objectEnumeration.push({
                objectName: objectName,
                properties: {
                    show: this.barChartSettings.enableAxis.show,
                },
                selector: null
            });
    };

    return objectEnumeration;
}
```

### <a name="control-property-update-logic"></a>A tulajdonságfrissítési logika vezérlése
Ha egy objektumot hozzáadnak a **Tulajdonság** ablaktáblához, minden kapcsolás frissítést aktivál. A specifikus objektumlogika hozzáadása `if` blokkokban történik:

```typescript
if(settings.enableAxis.show) {
    let margins = BarChart.Config.margins;
    height -= margins.bottom;
}
```

## <a name="databound-objects"></a>Adathoz kötött objektumok
Az adathoz kötött objektumok hasonlók a statikus objektumokhoz, de általában az adatkijelöléssel foglalkoznak. Módosíthatják például az adatponthoz társított színt.

![Az adathoz kötött objektum tulajdonságai](./media/create-bar-chart/object-databound-property.png)

### <a name="define-object-in-capabilities"></a>Objektum meghatározása képességekben
A statikus objektumokhoz hasonlóan a *capabilities.json* fájlban definiálhat egy másik objektumot. 
- Az `colorSelector` a `dataView` által hivatkozott belső név.
- A `displayName` a **Tulajdonság** ablaktáblán megjelenő név.
- A `fill` egy strukturális objektumérték, amelyhez nem tartozik primitív típus.

```typescript
"colorSelector": {
    "displayName": "Data Colors",
    "properties": {
        "fill": {
            "displayName": "Color",
            "type": {
                "fill": {
                    "solid": {
                        "color": true
                    }
                }
            }
        }
    }
}
```

További információt [az objektumokkal foglalkozó szakaszban](./objects-properties.md) talál.

### <a name="use-objectenumerationutility"></a>Az ObjectEnumerationUtility használata
A statikus objektumoknál megszokott módon le kell kérni az objektumadatokat a `dataView`-ból. Azonban ahelyett, hogy az objektumértékek a metaadatok között szerepelnének, az objektumok értékei az egyes kategóriákhoz vannak társítva.

```typescript
/**
 * Gets property value for a particular object in a category.
 *
 * @function
 * @param {DataViewCategoryColumn} category - List of category objects.
 * @param {number} index                    - Index of category object.
 * @param {string} objectName               - Name of desired object.
 * @param {string} propertyName             - Name of desired property.
 * @param {T} defaultValue                  - Default value of desired property.
 */
export function getCategoricalObjectValue<T>(category: DataViewCategoryColumn, index: number, objectName: string, propertyName: string, defaultValue: T): T {
    let categoryObjects = category.objects;

    if(categoryObjects) {
        let categoryObject: DataViewObject = categoryObjects[index];
        if(categoryObject) {
            let object = categoryObject[objectName];
            if(object) {
                let property: T = object[propertyName];
                if(property !== undefined) {
                    return property;
                }
            }
        }
    }
    return defaultValue;
}
```

A forráskód az [objectEnumerationUtility.ts](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/objectEnumerationUtility.ts) fájlban található.

### <a name="define-default-color-and-retrieve-categorical-object-from-dataview"></a>Alapértelmezett szín definiálása és kategorikus objektum beolvasása a dataView-ból
Az egyes színek mostantól a `dataView` kategóriáihoz vannak társítva. Az egyes adatpontokhoz beállíthatja a megfelelő színt.

```typescript
for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
    let defaultColor: Fill = {
        solid: {
            color: colorPalette.getColor(category.values[i]).value
        }
    }

    barChartDataPoints.push({
        category: category.values[i],
        value: dataValue.values[i],
        color: getCategoricalObjectValue<Fill>(category, i, 'colorSelector', 'fill', defaultColor).solid.color,
        selectionId: host.createSelectionIdBuilder()
            .withCategory(category, i)
            .createSelectionId()
    });
}
```

### <a name="populate-property-pane-with-enumerateobjectinstances"></a>A Tulajdonság ablaktábla feltöltése az enumerateObjectInstances alkalmazásával
Az `enumerateObjectInstances` használatával feltöltheti a **Tulajdonság** ablaktáblát objektumokkal. 

A jelen példány esetében vegyen fel egy színválasztót az egyes kategóriák **Tulajdonság** ablaktáblán történő megjelenítéséhez. Ehhez adjon hozzá egy további esetet a `colorSelector` `switch` utasításához, és végezzen iterációt az egyes adatpontok esetében a társított színnel. 

A kiválasztás mindenképpen szükséges a szín és a megfelelő adatpont társításához.

```typescript
/**
 * Enumerates through the objects defined in the capabilities and adds the properties to the format pane
 *
 * @function
 * @param {EnumerateVisualObjectInstancesOptions} options - Map of defined objects
 */
public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
    let objectName = options.objectName;
    let objectEnumeration: VisualObjectInstance[] = [];

    switch(objectName) {
        case 'enableAxis':
            objectEnumeration.push({
                objectName: objectName,
                properties: {
                    show: this.barChartSettings.enableAxis.show,
                },
                selector: null
            });
            break;
        case 'colorSelector':
            for(let barDataPoint of this.barDataPoints) {
                objectEnumeration.push({
                    objectName: objectName,
                    displayName: barDataPoint.category,
                    properties: {
                        fill: {
                            solid: {
                                color: barDataPoint.color
                            }
                        }
                    },
                    selector: barDataPoint.selectionId.getSelector()
                });
            }
            break;
    };

    return objectEnumeration;
}
```

Ha már minden tulajdonsághoz megadott egy választót, a következő `dataView`-objektumtömböt kapja:

![Adathoz kötött tulajdonságok a forrásban](./media/create-bar-chart/object-databound-property-source.png)

A `dataViews[0].categorical.categories[0].objects` tömb minden eleme az adathalmaz konkrét kategóriájához tartozik.

A `getCategoricalObjectValue` függvény csak a tulajdonságok kényelmesebb elérését teszi lehetővé a kategóriaindexük alapján. Meg kell adnia egy olyan `objectName` és `propertyName` értéket, amely megfelel a *capabilities.json* fájlban található objektumnak és tulajdonságnak.

## <a name="other-features"></a>Egyéb jellemzők 
A sávdiagramhoz csúszkavezérlőt és eszköztippeket is hozzá lehet adni. Az ehhez szükséges kódért tekintse meg a következő témakörökben szereplő véglegesítéseket: [Csúszka hozzáadása a Tulajdonságok ablaktáblán az átlátszatlanság vezérléséhez](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/e2e0bc5888d9a3ca305a7a7af5046068645c8b30) és [Eszköztipp-támogatás hozzáadása](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/981b021612d7b333adffe9f723ab27783c76fb14). Az eszköztippekkel kapcsolatos további információk [a Power BI-vizualizációk eszköztippjeivel foglalkozó szakaszban](./add-tooltips.md) érhetők el.

## <a name="packaging"></a>Csomagolás

Ahhoz, hogy betölthesse a vizualizációt a [Power BI Desktopba](https://powerbi.microsoft.com/desktop/), vagy megoszthassa a közösséggel a [Power BI-vizualizációk katalógusában](https://visuals.powerbi.com/), be kell csomagolnia. Navigáljon a vizualizációs projekt gyökérkönyvtárához, ahol a *pbiviz.json* fájl található, és a *pbiviz* fájl létrehozásához használja a következő parancsot:

```bash
pbiviz package
```
Ez a parancs létrehoz egy *pbiviz* fájlt a vizualizációs projekt *dist/* könyvtárában, és felülírja a korábbi csomagműveletekből származó *pbiviz* fájlokat.

## <a name="next-steps"></a>Következő lépések
Igény szerint a következő képességeket is hozzáadhatja a vizualizációhoz:
* [Helyi menü hozzáadása a vizualizációhoz](./context-menu.md)
* [Kezdőlap](./landing-page.md)
* [Indítási URL-cím](./launch-url.md)
* [Területi támogatás](./localization.md)