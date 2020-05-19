---
title: A Power BI visuals API változásnaplója
description: Ez a cikk a Power BI visuals API különböző verziói közötti főbb változásokat ismerteti
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/13/2019
ms.openlocfilehash: fa8759d7edb519240140263bcd01bfdddd9c7d86
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83141050"
---
# <a name="power-bi-visuals-api-changelog"></a>A Power BI visuals API változásnaplója
Ezen az oldalon találja a különböző API-verziók rövid összegzését. Az itt felsorolt verziók stabilnak tekinthetők, és nem fognak változni.

## <a name="api-v26"></a>API v2.6
  * Hozzáadja az **isInFocus** metódust a frissítési beállításhoz, valamint a **switchFocusModeState** metódust a vizualizációs gazdához
  * Támogatja a **részösszegek** testreszabását

## <a name="api-v25"></a>API v2.5
  * Támogatja az **[Elemzési panelt](./analytics-pane.md)**
  * Támogatja a `SelectionIdBuilder` **withMatrixNode** és **withTable** metódusokat
  * Már nem támogatja a `DataRepetitionSelector` felületet, amelyet a `data.CustomVisualOpaqueIdentity` felület vált fel

## <a name="api-v23"></a>API v2.3
  * **[Landing Page API](./landing-page.md)**
  * **[Local Storage API](./local-storage.md)**
  * **[Tuple filter API (többoszlopos szűrő)](./filter-api.md#the-tuple-filter-api-multi-column-filter)**
  * **[Rendering Events API](./event-service.md#render-events-in-power-bi-visuals)**

## <a name="api-v22"></a>API v2.2
  * Támogatja a **[JSON-szűrő DataView-ból való visszaállítását](./filter-api.md#restore-the-json-filter-from-the-data-view)**
  * **[ContextMenu API](./context-menu.md)**

## <a name="api-v21"></a>API v2.1
  * Teljesítménybeli továbbfejlesztések:
    * Gyorsabb betöltési idő
    * Kisebb memóriaigény
    * Optimalizált adat- és eseménytranzakciók  

**Kibocsátási megjegyzések**
* Az átdolgozott szűrési API-k az API 2.2-ben lesznek elérhetők, és az API 2.1-ben nem támogatottak.
* A vizualizációk csak a képességeikben deklarált dataView-típusokat kapják meg. A frissítés miatt a több dataView-típust használó vizualizációk nem fognak működni.
* Már nem támogatja a `DataViewScopeIdentity` felületet, amelyet a `data.DataRepetitionSelector` felület vált fel. Ha Ön használta a `DataViewScopeIdentity` felület kulcstulajdonságát, akkor lecserélheti a következőre: `JSON.stringify(identity)`
* Az `undefined` tulajdonságot a `null` váltja fel a dataView-ban. A `var item in myArray` tulajdonságot használó tömbbel való iteráláskor a rendszer átugorja a `undefined` tulajdonságot, de a `null` tulajdonságot nem. Előfordulhat, hogy a frissítés miatt nem fognak működni azok a vizualizációk, amelyek ezt a mintát használják. Mindenképpen ellenőrizze a `null` tulajdonságot a tömbökben:
   ```typescript
   for (var item in myArray) {
     if (!item) {
       continue;
     }
     console.log(item);
   }
   ```
* A `proto` tulajdonság már nem tárol rejtett metaadatokat\adatokat a dataView-ban. Előfordulhat, hogy a frissítés miatt nem fognak működni azok a vizualizációk, amelyek a `proto` használatával férnek hozzá a tulajdonságokhoz.

## <a name="api-v113"></a>API v1.13
* Támogatja a **[szeletelők szinkronizálását](./enable-sync-slicers.md)** , azonban ez csak az egymezős szeletelők esetében működik a PBI aktuális kódállapota miatt. [További információt itt talál](/power-bi/desktop-slicers).
* Kisegítő lehetőségek: [Kontrasztos megjelenítés támogatása](./high-contrast-support.md) 
* Kisegítő lehetőségek: Billentyűzetfókusz jelző engedélyezése

## <a name="api-v112"></a>API v1.12
* Témák támogatása
* A **[fetchMoreData](./fetch-more-data.md)** támogatása. Vegye figyelembe, hogy a **Fetch More Data API** révén túlléphető a 30 ezer adatpontos szigorú korlát
* **[Canvas Tooltips API](./add-tooltips.md#add-report-page-tooltips)**

## <a name="api-v111"></a>API v1.11
* **[FilterManager API](./filter-api.md)**
* Támogatja a **[Könyvjelzőket](./bookmarks-support.md)** 

## <a name="api-v110"></a>API v1.10
* Hozzáadja a következőt: `ILocalizationManager`
* **Authentication API**

## <a name="api-v19"></a>API v1.9
* **[launchUrl API](./launch-url.md)**

## <a name="api-v18"></a>API v1.8
* Támogatja az **fillRule** típust (gradiens) a képességek sémájában
* Támogatja a **rule** tulajdonságot az objektumtulajdonságok képességek sémájában

## <a name="api-v17"></a>API v1.7
* Támogatja a **[RESJSON](./localization.md#resource-file)** erőforrásfájlokat

## <a name="api-v162"></a>API v1.6.2
* Támogatja a **[Szerkesztési módot](./advanced-edit-mode.md)** a vizualizációk esetében a vizualizáción belüli szerkesztési módba való belépéshez
* Támogatja a html-alapú **[Interaktív (html) R Power BI-vizualizációkat](https://microsoft.github.io/PowerBI-visuals/tutorials/building-r-powered-custom-visual/creating-r-visuals.md)**

## <a name="api-v150"></a>API v1.5.0
* Támogatja az **[Interakciók engedélyezését](./visuals-interactions.md)** a vizualizációk interaktivitása érdekében

## <a name="api-v140"></a>API v1.4.0
* Támogatja a **[Honosítást](./localization.md)**

## <a name="api-v130"></a>API v1.3.0
* Támogatja az **[Elemleírásokat](./add-tooltips.md)**

## <a name="api-v120"></a>API v1.2.0
* A **colorPalette** hozzáadásával segíti a vizualizációban használt színek kezelését.
* Támogatja a **Többszörös kijelölést** – a selectionManager képes elfogadni a `SelectionId` egy tömbjét.
* Támogatja az R-szkripteket használó **[R-vizualizációkat](https://microsoft.github.io/PowerBI-visuals/tutorials/building-r-powered-custom-visual/creating-r-visuals.md)**

## <a name="api-v110"></a>API v1.1.0
* Támogatja a hibakeresési vizualizációt az iFrame-ben
* Hozzáad egy olyan egyszerű tesztkörnyezetet, amelyben gyorsabban végbemegy az iFrame inicializálása
* Orvosolja a [Capabilities.objects nem támogatja a „szöveg” típust](https://github.com/Microsoft/PowerBI-visuals-tools/issues/12) problémát
* A `pbiviz update` támogatása a vizualizáció API-típusa definícióinak és sémáinak frissítéséhez
* Támogatja a `pbiviz new` `--api-version` jelzőjét specifikus API-verziókkal rendelkező vizualizációk létrehozása céljából
* Támogatja az API v1.2.0 alfaverziós kiadását

**Vizualizációs gazda**
* A **createSelectionIdBuilder** hozzáadása az adatkijelöléshez használt egyedi azonosítók létrehozásához
* A **createSelectionManager** hozzáadása a vizualizáció kijelölési állapotának kezeléséhez, valamint a módosítások kommunikálása a vizualizációs gazda felé
* Több alapértelmezett, a vizualizációkban használható **szín** hozzáadása.

## <a name="api-v100"></a>API v1.0.0
* Kezdeti API-kiadás
