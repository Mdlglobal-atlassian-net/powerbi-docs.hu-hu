---
title: A teszteszközök használatának bemutatása a Power BI-vizualizációkban
description: Ez a cikk azt mutatja be, hogy a teszteszközök miképpen egyszerűsíthetik a Power BI-vizualizációk egységtesztjeihez használt utánzatokat és adott metódusokat
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/14/2020
ms.openlocfilehash: c50ad894b2e1f5eb838abdd4442f473f8bcbbb10
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82196606"
---
# <a name="power-bi-visuals-test-utils"></a>A Power BI-vizualizációk teszteszközei

Ez a cikk a Power BI-vizualizációk teszteszközeinek telepítéséhez, importálásához és használatához nyújt segítséget. A teszteszközök az egységtesztekhez használhatók, és olyan elemek utánzatait és metódusait tartalmazzák, mint az adatnézetek, a kiválasztások és a színsémák.

## <a name="requirements"></a>Követelmények

A csomag használatához a következőket kell telepítenie:

* [node.js](https://nodejs.org), a LTS verzió használatát javasoljuk
* [npm](https://www.npmjs.com/), 3.0.0-s vagy újabb verzió
* The [PowerBI vizualizációs eszközcsomag](https://github.com/Microsoft/PowerBI-visuals-tools) telepítése

## <a name="installation"></a>Telepítés

A teszteszközök telepítéséhez és a függőségek *package.json* fájlhoz való hozzáadásához futtassa az alábbi parancsot a saját Power BI vizualizációs könyvtárából:

```bash
npm install powerbi-visuals-utils-testutils --save
```

Az alábbi felsorolás a teszteszközökhöz tartozó nyilvános API-k leírását és példáit tartalmazza.

## <a name="visualbuilderbase"></a>VisualBuilderBase

A **VisualBuilder** ezt az eszközt használja az egységtesztekben a leggyakoribb `build`, `update`, és `updateRenderTimeout` metódusokkal. 

A `build` metódus a vizualizáció létrehozott példányát adja vissza.

Az `enumerateObjectInstances` és az `updateEnumerateObjectInstancesRenderTimeout` metódusra a gyűjtő és a formázás beállításmódosításainak ellenőrzéséhez van szükség.

```typescript
abstract class VisualBuilderBase<T extends IVisual> {
    element: JQuery;
    viewport: IViewport;
    visualHost: IVisualHost;
    protected visual: T;
    constructor(width?: number, height?: number, guid?: string, element?: JQuery);
    protected abstract build(options: VisualConstructorOptions): T;
     nit(): void;
    destroy(): void;
    update(dataView: DataView[] | DataView): void;
    updateRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    updateEnumerateObjectInstancesRenderTimeout(dataViews: DataView[] | DataView, options: EnumerateVisualObjectInstancesOptions, fn: (enumeration: VisualObjectInstance[]) => void, timeout?: number): number;
    updateFlushAllD3Transitions(dataViews: DataView[] | DataView): void;
    updateflushAllD3TransitionsRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstance[];
}
```

> [!NOTE]
> További példákért lásd: [VisualBuilderBase egységtesztek írása](./unit-tests-introduction.md#create-a-visual-instance-builder) és [egy valóságos VisualBuilderBase használati eset](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualBuilder.ts).

## <a name="dataviewbuilder"></a>DataViewBuilder

Ez a **TestDataViewBuilder** által használt modul egy **CategoricalDataViewBuilder** osztályt biztosít a `createCategoricalDataViewBuilder` metódushoz. Ezenkívül megadja azokat az interfészeket és metódusokat, amelyek az egységtesztelés során a **DataView** utánzatával való munkához szükségesek.

* A `withValues` statikus adatsorozat-oszlopokat, a `withGroupedValues` dinamikus adatsorozat-oszlopokat vesz fel

  Vizuális **DataViewCategorical** esetén ne alkalmazza egyszerre a dinamikus és a statikus adatsorozatokat. Csak olyan **DataViewCategorical** lekérdezésben használhatja mindkettőt, ahol a **DataViewTransform** várhatóan különálló vizuális **DataViewCategorical**-objektumokban osztja szét őket.

* A `build` metaadatokat és DataViewCategorical értéket ad hozzá a visszaadott DataView értékhez

  A `build` akkor ad vissza **Nem definiált** értéket, ha a paraméterek kombinációja nem engedélyezett, ilyen például a dinamikus és statikus adatsorok egyidejű felvétele a vizuális **DataView** elemhez.

```typescript
class CategoricalDataViewBuilder implements IDataViewBuilderCategorical {
    withCategory(options: DataViewBuilderCategoryColumnOptions): IDataViewBuilderCategorical;
    withCategories(categories: DataViewCategoryColumn[]): IDataViewBuilderCategorical;
    withValues(options: DataViewBuilderValuesOptions): IDataViewBuilderCategorical;
    withGroupedValues(options: DataViewBuilderGroupedValuesOptions): IDataViewBuilderCategorical;
    build(): DataView;
}

function createCategoricalDataViewBuilder(): IDataViewBuilderCategorical;
```

## <a name="testdataviewbuilder"></a>TestDataViewBuilder

A **VisualData** létrehozására szolgál az egységtesztekben. Amikor az adatok adatmezőgyűjtőkbe kerülnek, a Power BI egy kategorikus **DataView** objektumot hoz létre az adatok alapján. A **TestDataViewBuilder** a kategorikus **DataView** létrehozásának szimulációját segíti.

```typescript
abstract class TestDataViewBuilder {
    static DataViewName: string;
    private aggregateFunction;
    static setDefaultQueryName(source: DataViewMetadataColumn): DataViewMetadataColumn;
    static getDataViewBuilderColumnIdentitySources(options: TestDataViewBuilderColumnOptions[] | TestDataViewBuilderColumnOptions): DataViewBuilderColumnIdentitySource[];
    static getValuesTable(categories?: DataViewCategoryColumn[], values?: DataViewValueColumn[]): any[][];
    static createDataViewBuilderColumnOptions(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], filter?: (options: TestDataViewBuilderColumnOptions) => boolean, customizeColumns?: CustomizeColumnFn): DataViewBuilderAllColumnOptions;
    static setUpDataViewBuilderColumnOptions(options: DataViewBuilderAllColumnOptions, aggregateFunction: (array: number[]) => number): DataViewBuilderAllColumnOptions;
    static setUpDataView(dataView: DataView, options: DataViewBuilderAllColumnOptions): DataView;
    protected createCategoricalDataViewBuilder(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], columnNames: string[], customizeColumns?: CustomizeColumnFn): IDataViewBuilderCategorical;
    abstract getDataView(columnNames?: string[]): DataView;
}
```

  Alább láthatók a `testDataView` létrehozásához leggyakrabban használt interfészek:

  ```typescript
  interface TestDataViewBuilderColumnOptions extends DataViewBuilderColumnOptions {
      values: any[];
  }

  interface TestDataViewBuilderCategoryColumnOptions extends TestDataViewBuilderColumnOptions {
      objects?: DataViewObjects[];
      isGroup?: boolean;
  }

  interface DataViewBuilderColumnOptions {
      source: DataViewMetadataColumn;
  }

  interface DataViewBuilderSeriesData {
      values: PrimitiveValue[];
      highlights?: PrimitiveValue[];
      /** Client-computed maximum value for a column. */
      maxLocal?: any;
      /** Client-computed maximum value for a column. */
      minLocal?: any;
  }

  interface DataViewBuilderColumnIdentitySource {
      fields: any[];
      identities?: CustomVisualOpaqueIdentity[];
  }
  ```
   
> [!NOTE]
> További példákért lásd: [TestDataViewBuilder egységtesztek írása](./unit-tests-introduction.md#how-to-add-static-data-for-unit-tests) és [egy valóságos TestDataViewBuilder használati eset](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualData.ts).

## <a name="mocks"></a>Utánzatok

### <a name="mockivisualhost"></a>MockIVisualHost

Az **IVisualHost** elemet implementálja olyan, külső függőségek nélküli Power BI-vizualizációk teszteléséhez, mint a Power BI Framework.

Hasznos metódus többek között a `createSelectionIdBuilder`, a `createSelectionManager`, a `createLocalizationManager`, és a tulajdonságbeolvasó.

```typescript
import powerbi from "powerbi-visuals-api";

import VisualObjectInstancesToPersist = powerbi.VisualObjectInstancesToPersist;
import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
import ISelectionManager = powerbi.extensibility.ISelectionManager;
import IColorPalette = powerbi.extensibility.IColorPalette;
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import ITooltipService = powerbi.extensibility.ITooltipService;
import IVisualHost = powerbi.extensibility.visual.IVisualHost;

class MockIVisualHost implements IVisualHost {
      constructor(
          colorPalette?: IColorPalette,
          selectionManager?: ISelectionManager,
          tooltipServiceInstance?: ITooltipService,
          localeInstance?: MockILocale,
          allowInteractionsInstance?: MockIAllowInteractions,
          localizationManager?: powerbi.extensibility.ILocalizationManager,
          telemetryService?: powerbi.extensibility.ITelemetryService,
          authService?: powerbi.extensibility.IAuthenticationService,
          storageService?: ILocalVisualStorageService,
          eventService?: IVisualEventService);
      createSelectionIdBuilder(): ISelectionIdBuilder;
      createSelectionManager(): ISelectionManager;
      createLocalizationManager(): ILocalizationManager;
      colorPalette: IColorPalette;
      locale: string;
      telemetry: ITelemetryService;
      tooltipService: ITooltipService;
      allowInteractios: boolean;
      storageService: ILocalVisualStorageService;
      eventService: IVisualEventService;
      persistProperties(changes: VisualObjectInstancesToPersist): void;
}
```
   
- A `createVisualHost` létrehozza és visszaadja az **IVisualHost** egy példányát, amely valójában a **MockIVisualHost**
  ```typescript
  function createVisualHost(locale?: Object, allowInteractions?: boolean, colors?: IColorInfo[], isEnabled?: boolean, displayNames?: any, token?: string): IVisualHost;
  ```

    Példa
    ```typescript
    import { createVisualHost } from "powerbi-visuals-utils-testutils"

    let host: IVisualHost = createVisualHost();
    ```

> [!IMPORTANT]
> A **MockIVisualHost** a **IVisualHost** hamis implementációja, és csak egységteszteléshez használható.

### <a name="mockicolorpalette"></a>MockIColorPalette

Az **IColorPalette** elemet implementálja olyan, külső függőségek nélküli Power BI-vizualizációk teszteléséhez, mint a Power BI Framework.

A **MockIColorPalette** hasznos tulajdonságokat biztosít a színséma vagy a nagy kontrasztú mód ellenőrzéséhez az egységtesztekben.

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IColorPalette = powerbi.extensibility.ISandboxExtendedColorPalette;
  import IColorInfo = powerbi.IColorInfo;

  class MockIColorPalette implements IColorPalette {
      constructor(colors?: IColorInfo[]);
      getColor(key: string): IColorInfo;
      reset(): IColorPalette;
      isHighContrastMode: boolean;
      foreground: {value: string};
      foregroundLight: {value: string};
      ...
      background: {value: string};
      backgroundLight: {value: string};
      ...
      shapeStroke: {value: string};
  }
  ```
  - A `createColorPalette` létrehozza és visszaadja az **IColorPalette** egy példányát, amely valójában a **MockIColorPalette**
    ```typescript
    function createColorPalette(colors?: IColorInfo[]): IColorPalette;
    ```

    Példa
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let colorPalette: IColorPalette = createColorPalette();
    ```
    
> [!IMPORTANT]
> A **MockIColorPalette** az **IColorPalette** hamis implementációja, amely csak egységtesztekhez használható.

### <a name="mockiselectionid"></a>MockISelectionId

Az **ISelectionId** elemet implementálja olyan, külső függőségek nélküli Power BI-vizualizációk teszteléséhez, mint a Power BI Framework.

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import Selector = powerbi.data.Selector;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionId implements ISelectionId {
      constructor(key: string);
      equals(other: ISelectionId): boolean;
      includes(other: ISelectionId, ignoreHighlight?: boolean): boolean;
      getKey(): string;
      getSelector(): Selector;
      getSelectorsByColumn(): Selector;
      hasIdentity(): boolean;
  }
  ```

  - A `createSelectionId` létrehozza és visszaadja az **ISelectionId** egy példányát, ami valójában a **MockISelectionId**
    ```typescript
    function createSelectionId(key?: string): ISelectionId;
    ```

    Példa
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let selectionId: ISelectionId = createSelectionId();
    ```
    
> [!NOTE]
> A **MockISelectionId** az **ISelectionId** hamis implementációja, amely csak egységtesztekhez használható.

### <a name="mockiselectionidbuilder"></a>MockISelectionIdBuilder

Az **ISelectionIdBuilder** elemet implementálja olyan, külső függőségek nélküli Power BI-vizualizációk teszteléséhez, mint a Power BI Framework. 

  ```typescript
  import DataViewCategoryColumn = powerbi.DataViewCategoryColumn;
  import DataViewValueColumn = powerbi.DataViewValueColumn;
  import DataViewValueColumnGroup = powerbi.DataViewValueColumnGroup;
  import DataViewValueColumns = powerbi.DataViewValueColumns;
  import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionIdBuilder implements ISelectionIdBuilder {
      withCategory(categoryColumn: DataViewCategoryColumn, index: number): this;
      withSeries(seriesColumn: DataViewValueColumns, valueColumn: DataViewValueColumn | DataViewValueColumnGroup): this;
      withMeasure(measureId: string): this;
      createSelectionId(): ISelectionId;
      withMatrixNode(matrixNode: DataViewMatrixNode, levels: DataViewHierarchyLevel[]): this;
      withTable(table: DataViewTable, rowIndex: number): this;
  }
  ```

  - A `createSelectionIdBuilder` létrehozza és visszaadja az **ISelectionIdBuilder** egy példányát, amely valójában a **MockISelectionIdBuilder**
    ```typescript
    function createSelectionIdBuilder(): ISelectionIdBuilder;
    ```

    Példa
    ```typescript
    import { selectionIdBuilder } from "powerbi-visuals-utils-testutils";

    let selectionIdBuilder = createSelectionIdBuilder();
    ```

> [!NOTE]
> A **MockISelectionIdBuilder** a **ISelectionIdBuilder** hamis implementációja, amely csak egységtesztekhez használható.

### <a name="mockiselectionmanager"></a>MockISelectionManager

Az **ISelectionManager** elemet implementálja olyan, külső függőségek nélküli Power BI-vizualizációk teszteléséhez, mint a Power BI Framework. 

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IPromise = powerbi.IPromise;
  import ISelectionId = powerbi.visuals.ISelectionId;
  import ISelectionManager = powerbi.extensibility.ISelectionManager;

  class MockISelectionManager implements ISelectionManager {
      select(selectionId: ISelectionId | ISelectionId[], multiSelect?: boolean): IPromise<ISelectionId[]>;
      hasSelection(): boolean;
      clear(): IPromise<{}>;
      getSelectionIds(): ISelectionId[];
      containsSelection(id: ISelectionId): boolean;
      showContextMenu(selectionId: ISelectionId, position: IPoint): IPromise<{}>;
      registerOnSelectCallback(callback: (ids: ISelectionId[]) => void): void;
      simutateSelection(selections: ISelectionId[]): void;
  }
  ```

  - A `createSelectionManager` létrehozza és visszaadja az **ISelectionManager** egy példányát, amely valójában a **MockISelectionManager**
    ```typescript
    function createSelectionManager(): ISelectionManager
    ```

    Példa
    ```typescript
    import { createSelectionManager } from "powerbi-visuals-utils-testutils";

    let selectionManager: ISelectionManager = createSelectionManager();
    ```

> [!NOTE]
> A **MockISelectionManager** a **ISelectionManager** hamis implementációja, amely csak egységtesztekhez használható.

### <a name="mockilocale"></a>MockILocale

  Elvégzi a területi beállítást, és az egységtesztelési folyamat során az igényeinek megfelelően módosítja azt.
  ```typescript
  class MockILocale {
      constructor(locales?: Object): void; // Default locales are en-US and ru-RU 
      locale(key: string): void;// setter property
      locale(): string; // getter property
  }
  ```
  - A `createLocale` létrehozza és visszaadja a **MockILocale** egy példányát
    ```typescript
    funciton createLocale(locales?: Object): MockILocale;
    ```

### <a name="mockitooltipservice"></a><a id="mockitooltipservice"></a> MockITooltipService
Szimulálja a `TooltipService` elemet, és az igényeinek megfelelően meghívja az egységtesztelés során.
  ```typescript
  class MockITooltipService implements ITooltipService {
      constructor(isEnabled: boolean = true);
      enabled(): boolean;
      show(options: TooltipShowOptions): void;
      move(options: TooltipMoveOptions): void;
      hide(options: TooltipHideOptions): void;
  }
  ```
  - A `createTooltipService` létrehozza és visszaadja a **MockITooltipService** egy példányát
    ```typescript
    function createTooltipService(isEnabled?: boolean): ITooltipService;
    ```

### <a name="mockiallowinteractions"></a>MockIAllowInteractions

```typescript
export class MockIAllowInteractions {
    constructor(public isEnabled?: boolean); // false by default
}
```
  - A `createAllowInteractions` létrehozza és visszaadja a **MockIAllowInteractions** egy példányát
    ```typescript
    function createAllowInteractions(isEnabled?: boolean): MockIAllowInteractions;
    ```

### <a name="mockilocalizationmanager"></a><a id="mockilocalizationmanager"></a> MockILocalizationManager
Biztosítja a **LocalizationManager** egységteszteléshez szükséges alapképességeit.
```typescript
class MockILocalizationManager implements ILocalizationManager {
    constructor(displayNames: {[key: string]: string});
    getDisplayName(key: string): string; // returns default or setted displayNames for localized elements
}
```
  - A `createLocalizationManager` létrehozza és visszaadja az **ILocalizationManager** egy példányát, amely valójában a **MockILocalizationManager**
    ```typescript
    function createLocalizationManager(displayNames?: any): ILocalizationManager;
    ```

    Példa
    ```typescript
    import { createLocalizationManager } from "powerbi-visuals-utils-testutils";
    let localizationManagerMock: ILocalizationManager = createLocalizationManager();
    ```

### <a name="mockitelemetryservice"></a>MockITelemetryService
A **TelemetryService** használatát szimulálja.
```typescript
class MockITelemetryService implements ITelemetryService {
    instanceId: string;
    trace(veType: powerbi.VisualEventType, payload?: string) {
    }
}
```
  `MockITelemetryService` létrehozása
    ```typescript
    function createTelemetryService(): ITelemetryService;
    ```
### <a name="mockiauthenticationservice"></a>MockIAuthenticationService
Az **AuthenticationService** munkáját szimulálja egy AAD-tokenutánzat biztosítása révén.
```typescript
class MockIAuthenticationService implements IAuthenticationService  {
    constructor(token: string);
    getAADToken(visualId?: string): powerbi.IPromise<string>
}
```
  - A `createAuthenticationService` létrehozza és visszaadja az **IAuthenticationService** egy példányát, amely valójában a **MockIAuthenticationService**
    ```typescript
    function createAuthenticationService(token?: string): IAuthenticationService;
    ```

### <a name="mockistorageservice"></a>MockIStorageService
Lehetővé teszi a **LocalStorage** elemmel azonos viselkedésű **ILocalVisualStorageService** használatát.
```typescript
class MockIStorageService implements ILocalVisualStorageService {
  get(key: string): IPromise<string>;
  set(key: string, data: string): IPromise<number>;
  remove(key: string): void;
}
```
  - A `createStorageService` létrehozza és visszaadja az **ILocalVisualStorageService** egy példányát, amely valójában a **MockIStorageService**
    ```typescript
    function createStorageService(): ILocalVisualStorageService;
    ```

### <a name="mockieventservice"></a>MockIEventService
```typescript
import powerbi from "powerbi-visuals-api";
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import VisualUpdateOptions = powerbi.extensibility.VisualUpdateOptions;

class MockIEventService implements IVisualEventService {
      renderingStarted(options: VisualUpdateOptions): void;
      renderingFinished(options: VisualUpdateOptions): void;
      renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```
  - A `createEventService` létrehozza és visszaadja az **IVisualEventService** egy példányát, amely valójában a **MockIEventService**
    ```typescript
    function createEventService(): IVisualEventService;
    ```

## <a name="utils"></a>Eszközök

Az eszközök közé tartoznak a Power BI-vizualizációk egységtesztelésénél használt, például színekhez, számokhoz és eseményekhez kapcsolódó segédmetódusok.

- A `renderTimeout` az időtúllépést adja vissza
  ```typescript
  function renderTimeout(fn: Function, timeout: number = DefaultWaitForRender): number
  ```

- A `testDom` az egységtesztek rögzített adatainak beállításában segít
  ```typescript
  function testDom(height: number | string, width: number | string): JQuery
  ```
  Példa
  ```typescript
  import { testDom }  from "powerbi-visuals-utils-testutils";
  describe("testDom", () => {
      it("should return an element", () => {
          let element: JQuery = testDom(500, 500);
          expect(element.get(0)).toBeDefined();
      });
  });
  ```

### <a name="color-related-helper-methods"></a>Színekkel kapcsolatos segítő metódusok

- `getSolidColorStructuralObject`
  ```typescript
  function getSolidColorStructuralObject(color: string): any
  ```
  A következő szerkezetet adja vissza:

  ```json
  { solid: { color: color } }
  ```

- A `assertColorsMatch` összehasonlítja a bemeneti karakterláncokból elemzéssel kapott **RgbColor** objektumokat
  ```typescript
  function assertColorsMatch(actual: string, expected: string, invert: boolean = false): boolean
  ```

- Az `parseColorString` elemzi a bemeneti karakterlánc színét, és a felülethez tartozó adott **RgbColor** formában adja vissza
  ```typescript
  function parseColorString(color: string): RgbColor
  ```

### <a name="number-related-helper-methods"></a>Számokkal kapcsolatos segítő metódusok

- A `getRandomNumbers` véletlenszerű számot hoz létre egy minimális és egy maximális érték használatával. Megadhat egy `exceptionList` értéket és egy függvényt az eredmény módosításához.
  ```typescript
  function getRandomNumber(
      min: number,
      max: number,
      exceptionList?: number[],
      changeResult: (value: any) => number = x => x): number
  ```

- A `getRandomNumbers` véletlenszerű számok tömbjét adja meg, amelyeket a `getRandomNumber` metódus hozott létre konkrét minimális és maximális értékek használatával
  ```typescript
  function getRandomNumbers(count: number, min: number = 0, max: number = 1): number[]
  ```

### <a name="event-related-helper-methods"></a>Eseményekkel kapcsolatos segítő metódusok
Az alábbi metódusok használatával weblapok eseményei szimulálhatók az egységtesztekben.

- A `clickElement` kattintást szimulál egy adott elemen
  ```typescript
  function clickElement(element: JQuery, ctrlKey: boolean = false): void
  ```

- A `createTouch` egy **Touch** (Érintés) objektumot ad vissza az érintés eseményének szimulációjához
  ```typescript
  function createTouch(x: number, y: number, element: JQuery, id: number = 0): Touch
  ```

- A `createTouchesList` a szimulált **Touch** (Érintés) események listáját adja vissza
  ```typescript
  function createTouchesList(touches: Touch[]): TouchList
  ```

- A `createContextMenuEvent` a **MouseEvent** elemet adja vissza
  ```typescript
  function createContextMenuEvent(x: number, y: number): MouseEvent
  ```

- A `createMouseEvent` létrehozza és visszaadja a **MouseEvent** elemet
  ```typescript
  function createMouseEvent(
      mouseEventType: MouseEventType,
      eventType: ClickEventType,
      x: number,
      y: number,
      button: number = 0): MouseEvent
  ```

- `createTouchEndEvent`
  ```typescript
  function createTouchEndEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchMoveEvent`
  ```typescript
  function createTouchMoveEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchStartEvent`
  ```typescript
  function createTouchStartEvent(touchList?: TouchList): UIEvent
  ```

### <a name="d3-event-related-helper-methods"></a>D3-eseményekkel kapcsolatos segédmetódusok

Az alábbi metódusok D3-események szimulálására szolgálnak az egységtesztekben.

- A `flushAllD3Transitions` kikényszeríti az összes D3-átmenet végrehajtását

  ```typescript
  function flushAllD3Transitions()
  ```
  
  > [!NOTE]
  > A rendszer általában pillanatnyi késleltetéssel (<10 ms) hajtja végre a nulla késleltetésű átmenetet, de ez a képernyő villódzásához vezethet, ha a böngésző kétszer jeleníti meg a lapot. Először az első eseményhurok végén, majd másodszor azonnal az időzítő első visszahívása után.
  >
  > Ez a villódzás jobban látszik az IE-ben és nagyszámú webnézet esetén, az iOS esetében pedig nem ajánlott.
  > 
  > Ha az időzítő várólistáját az első eseményhurok végén kiüríti, akkor azonnal futtathatja a nulla késleltetésű átmeneteket, és elkerülheti a villódzást.

Ide tartoznak az alábbi metódusok is:
```typescript
function d3Click(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseUp(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseDown(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOver(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseMove(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOut(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3KeyEvent(element: JQuery, typeArg: string, keyArg: string, keyCode: number): void
function d3TouchStart(element: JQuery, touchList?: TouchList): void
function d3TouchMove(element: JQuery, touchList?: TouchList): void
function d3TouchEnd(element: JQuery, touchList?: TouchList): void
function d3ContextMenu(element: JQuery, x: number, y: number): void
```

### <a name="helper-interfaces"></a>Segítő felületek
Segítő funkcióban az alábbi felületek és enumerációk használhatók.

```typescript
interface RgbColor {
    R: number;
    G: number;
    B: number;
    A?: number; 
}

enum ClickEventType {
    Default = 0,
    CtrlKey = 1,
    AltKey = 2,
    ShiftKey = 4,
    MetaKey = 8,
}

enum MouseEventType {
    click,
    mousedown,
    mouseup,
    mouseover,
    mousemove,
    mouseout,
}
```

## <a name="next-steps"></a>Következő lépések

A Webpack-alapú Power BI-vizualizációkhoz használt egységtesztek, valamint a `karma` és a `jasmine` elemeket tartalmazó egységtesztek írását például itt ismerheti meg: [Oktatóanyag: Egységtesztek hozzáadása Power BI-vizualizációs projektekhez](./unit-tests-introduction.md).
