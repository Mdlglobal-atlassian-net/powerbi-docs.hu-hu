---
title: Vizualizációs API
description: Ez a cikk az IVisual API Power BI-vizualizációkkal való használatát ismerteti
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/19/2020
ms.openlocfilehash: 6ec30fdd4812427ae855ff9a167d946d2a415c28
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83302966"
---
# <a name="visual-api"></a>Vizualizációs API
Minden vizualizáció egy osztállyal kezdődik, amely implementálja az `IVisual` felületet. Az osztálynak bármilyen nevet adhat, ha pontosan egy olyan osztály van, amely implementálja az `IVisual` felületet.

> [!NOTE]
> A vizualizációosztály nevének meg kell egyeznie a *pbiviz.json* fájlban megadott névvel.

Tekintse meg a minta vizualizációosztályt az alábbi implementálandó metódusokkal:

* `constructor`, egy standard konstruktor a vizualizáció állapotának inicializálásához
* `update` a vizualizáció adatainak frissítéséhez
* `enumerateObjectInstances`, amely objektumokat ad vissza a tulajdonságpanel kitöltéséhez (formázási lehetőségek), ahol szükség szerint módosíthatók
* `destroy`, standard destruktor a tisztításhoz

```typescript
class MyVisual implements IVisual {
    
    constructor(options: VisualConstructorOptions) {
        //one time setup code goes here (called once)
    }
    
    public update(options: VisualUpdateOptions): void {
        //code to update your visual goes here (called on all view or data changes)
    }

    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
        //returns objects to populate the property pane (called for each object defined in capabilities)
    }
    
    public destroy(): void {
        //one time cleanup code goes here (called once)
    }
}
```

## <a name="constructor"></a>konstruktor

A vizualizációs osztály konstruktorát a vizualizáció példányosításakor hívja meg a rendszer. A vizualizáció számára szükséges bármilyen beállítási művelethez használható.

```typescript
constructor(options: VisualConstructorOptions)
```

**VisualConstructorOptions**

* `element: HTMLElement`, hivatkozás a DOM-elemre, amely tartalmazza a vizualizációt
* `host: IVisualHost`, tulajdonságok és szolgáltatások gyűjteménye, amelyek a vizualizációs gazdagéppel (Power BI) való interakcióhoz használhatók

   Az `IVisualHost` az alábbi szolgáltatásokat tartalmazza:

   ```typescript
   export interface IVisualHost extends extensibility.IVisualHost {
       createSelectionIdBuilder: () => visuals.ISelectionIdBuilder;
       : () => ISelectionManager;
       colorPalette: ISandboxExtendedColorPalette;
       persistProperties: (changes: VisualObjectInstancesToPersist) => void;
       applyJsonFilter: (filter: IFilter[] | IFilter, objectName: string, propertyName: string, action: FilterAction) => void;
       tooltipService: ITooltipService;
       telemetry: ITelemetryService;
       authenticationService: IAuthenticationService;
       locale: string;
       allowInteractions: boolean;
       launchUrl: (url: string) => void;
       fetchMoreData: () => boolean;
       instanceId: string;
       refreshHostData: () => void;
       createLocalizationManager: () => ILocalizationManager;
       storageService: ILocalVisualStorageService;
       eventService: IVisualEventService;
       switchFocusModeState: (on: boolean) => void;
   }
   ```
   * `createSelectionIdBuilder`, metaadatokat hoz létre és tárol a vizualizációban kiválasztható elemek számára
   * `createSelectionManager`, létrehozza azt a kommunikációs hidat, amely értesíti a vizualizáció gazdagépét a kiválasztási állapot változásairól, lásd: [Kiválasztási API](./selection-api.md).
   * `createLocalizationManager`, létrehoz egy kezelőt, amely a [Honosítást](./localization.md) segíti
   * `allowInteractions: boolean`, egy logikai jelölő, amely azt jelzi, hogy a vizualizációnak interaktívnak kell-e lennie
   * `applyJsonFilter`, adott szűrőtípusokat alkalmaz, lásd: [Szűrő API](./filter-api.md)
   * `persistProperties`, lehetővé teszi a felhasználók számára, hogy megőrizzék és a vizualizáció definíciójával együtt mentsék a tulajdonságokat, hogy a következő újratöltéssel elérhetők legyenek
   * `eventService`, visszaad egy [eseményszolgáltatást](./event-service.md) a **Renderelési** események támogatásához
   * `storageService`, visszaad egy szolgáltatást, amely a [helyi tárterület](./local-storage.md) vizualizációban való használatát segíti
   * `authenticationService`, létrehoz egy szolgáltatást, amely a felhasználói hitelesítést segíti
   * `tooltipService`, visszaad egy [elemleírási szolgáltatást](./add-tooltips.md), amely az elemleírások vizualizációban való használatát segíti
   * `launchUrl`, segít a következő lapon lévő [URL elindításában](./launch-url.md)
   * `locale`, visszaad egy területi beállítás típusú sztringet, lásd: [Lokalizáció](./localization.md)
   * `instanceId`, visszaad egy sztringet az aktuális vizualizációpéldány azonosításához
   * `colorPalette`, visszaadja az adatok színbeállításához szükséges színpalettát
   * `fetchMoreData`, támogatja a standard határértéknél (ezer sor) nagyobb adatfelhasználást
   * `switchFocusModeState`, segít módosítani a fókusz mód állapotát

## <a name="update"></a>update

Minden vizualizációnak implementálnia kell egy nyilvános frissítési metódust, amelyet az adatok vagy a gazdakörnyezet minden módosításakor meghív a rendszer.

```typescript
public update(options: VisualUpdateOptions): void
```

**VisualUpdateOptions**

* `viewport: IViewport`, a vizualizáció renderelési mintájának méretei
* `dataViews: DataView[]`, a DataView objektum, amely tartalmazza a vizualizáció megjelenítéséhez szükséges összes adatot (a vizualizáció általában a DataView alatt található kategorikus tulajdonságot fogja használni)
* `type: VisualUpdateType`, a frissítés típusát/típusait jelző jelölő (**Data** | **Resize** | **ViewMode** | **Style** | **ResizeEnd**)
* `viewMode: ViewMode`, a vizualizáció megtekintési módját jelölő jelző (**View** | **Edit** | **InFocusEdit**)
* `editMode: EditMode`, a vizualizáció szerkesztési módját jelző jelölő (**Default** | **Advanced**) (ha a vizualizáció támogatja az **AdvancedEditMode** módot, csak akkor kell renderelnie a speciális felhasználói felületi vezérlőket, ha az **editMode** **Advanced** értékre van állítva, lásd: [AdvancedEditMode](./advanced-edit-mode.md))
* `operationKind?: VisualDataChangeOperationKind`, jelölő az adatváltozás típusának jelzésére (**Create** | **Append**)
* `jsonFilters?: IFilter[]`, alkalmazott JSON-szűrők gyűjteménye
* `isInFocus?: boolean`, jelölő annak jelölésére, hogy a vizualizáció fókusz módban van-e
    
## <a name="enumerateobjectinstances-optional"></a>enumerateObjectInstances `optional`

Ezt a metódust a képességekben felsorolt összes objektum esetén meghívja a rendszer. A kapcsolók (jelenleg csak a név) használatával egy `VisualObjectInstanceEnumeration` elemet ad vissza, amely ismerteti a tulajdonság megjelenítési módját.

```typescript
enumerateObjectInstances(options:EnumerateVisualObjectInstancesOptions):VisualObjectInstanceEnumeration
```

**EnumerateVisualObjectInstancesOptions**

* `objectName: string`, az objektum neve

## <a name="destroy-optional"></a>destroy `optional`

A destroy függvényt akkor hívja meg a rendszer, amikor eltávolítja a memóriából a vizualizációt, és olyan tisztítási feladatokhoz használható, mint például az eseményfigyelők eltávolítása.

``` typescript
public destroy(): void
```

> [!Note]
> A Power BI általában nem hívja meg a `destroy` függvényt, mert a vizualizációt tartalmazó teljes IFrame eltávolítása gyorsabb.
