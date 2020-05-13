---
title: A Teljesítményelemző használata a jelentéselemek teljesítményének vizsgálatához a Power BI Desktopban
description: Ismerje meg, milyen teljesítményt nyújtanak a vizualizációk és a jelentéselemek az erőforrás-használat és a válaszkészség szempontjából
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/23/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: fd172cc41dce432e7e8f2c7f9b9f3ff67caaef4b
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83348252"
---
# <a name="use-performance-analyzer-to-examine-report-element-performance"></a>A Teljesítményelemző használata a jelentéselemek teljesítményének vizsgálatához

A **Power BI Desktopban** megtudhatja, milyen teljesítményt nyújtanak az egyes jelentéselemek, például a vizualizációk és a DAX-képletek. A **Teljesítményelemző** segítségével megtekintheti és rögzítheti azokat a naplókat, amelyek felmérik az egyes jelentéselemek teljesítményét, amikor a felhasználók használják őket, valamint hogy a teljesítményük mely szempontból terheli a leginkább (vagy legkevésbé) az erőforrásokat.

![Teljesítményelemző](media/desktop-performance-analyzer/performance-analyzer-01.png)

A Teljesítményelemző megvizsgálja és megjeleníti, hogy mennyi idő szükséges a felhasználói műveletek által kezdeményezett vizualizációfrissítésekhez, és bemutatja az adatokat megtekinthető, részletezhető és exportálható formában. A Teljesítményelemző segít azonosítani azokat a vizualizációkat, amelyek hatással vannak a jelentések teljesítményére, és segít meghatározni a hatás okát.

## <a name="displaying-the-performance-analyzer-pane"></a>A Teljesítményelemző ablaktábla megjelenítése

A **Power BI Desktopban** válassza ki a **Nézet** menüszalagot. A **Nézet** menüszalag **Megjelenítés** területén jelölje be a **Teljesítményelemző** jelölőnégyzetét a Teljesítményelemző megjelenítéséhez.

![A Teljesítményelemző kiválasztása a Nézet menüszalagon](media/desktop-performance-analyzer/performance-analyzer-02.png)

A kiválasztás után a Teljesítményelemző egy külön ablaktáblán jelenik meg, a jelentésvászontól jobbra.

## <a name="using-performance-analyzer"></a>A Teljesítményelemző használata

A Teljesítményelemző a jelentéselemek frissítésének feldolgozási idejét méri (beleértve a vizualizációk létrehozásához vagy frissítéséhez szükséges időt) az olyan felhasználói műveleteket követően, amelyek egy lekérdezés futtatásához vezetnek. Például egy szelet elhúzásakor módosítani kell a szelet vizualizációját, el kell küldeni egy lekérdezést az adatmodellbe, és az új beállítások miatt frissíteni kell az érintett vizualizációkat. 

Ahhoz, hogy a Teljesítményelemző megkezdje a rögzítést, egyszerűen válassza a **Rögzítés indítása** lehetőséget.

![Rögzítés indítása](media/desktop-performance-analyzer/performance-analyzer-03.png)

A jelentésben elvégzett összes művelet megjelenik és naplózva lesz a Teljesítményelemző ablaktáblán, abban a sorrendben, ahogy a Power BI betölti a vizualizációt. Például tegyük fel, hogy van egy jelentése, amelyről a felhasználók jelezték, hogy sokáig tart a frissítése. Vagy egy jelentés bizonyos vizualizációs elemei lassan jelennek meg egy csúszka módosítását követően. A Teljesítményelemző képes megmondani, hogy ezért melyik vizualizáció a felelős, és megállapítja, hogy a vizualizáció melyik részének a feldolgozása tart a legtöbb ideig. 

Ha elindította a rögzítést, a **Rögzítés indítása** gomb szürkére vált (inaktív lesz, mivel a rögzítés már zajlik), és a **Leállítás** gomb lesz aktív. 

A Teljesítményelemző valós időben gyűjti és jeleníti meg a teljesítményre vonatkozó mérési adatokat. Így minden alkalommal, amikor Ön egy vizualizációra kattint, elhúz egy szeletet, vagy elvégez bármilyen más műveletet, a Teljesítményelemző ablaktábláján azonnal megjelennek a teljesítményre vonatkozó eredmények.

Ha az ablaktábla több információt tartalmaz, mint amennyi egyszerre megjeleníthető, akkor megjelenik egy görgetősáv, amellyel elérhetők a további információk.

Minden művelethez tartozik egy szakaszazonosító az ablaktáblán, amely leírja, hogy milyen művelet kezdeményezte az adott naplóbejegyzéseket. A következő képen a művelet az volt, hogy a felhasználó elhúzott egy szeletet.

![Szakaszok művelettípusok szerint](media/desktop-performance-analyzer/performance-analyzer-04.png)

Minden vizualizáció naplóadatai között megtalálható, hogy mennyi idő kellett a következő típusú feladatok végrehajtásához:

* **DAX-lekérdezés** – Ha szükség volt egy DAX-lekérdezésre, akkor ez az időtartam jelzi, hogy miután a vizualizáció elküldte a lekérdezést, mennyi idő telt el, míg az Analysis Services vissza nem adta az eredményeket.
* **Vizualizáció megjelenítése** – A vizualizáció képernyőn való megjelenítéséhez szükséges időtartam, beleértve a webes képek lekéréséhez vagy a geokódoláshoz szükséges időt is. 
* **Egyéb** – Ez az időtartam jelzi, hogy a vizualizáció mennyi időt töltött a lekérdezések előkészítésével, más vizualizációk teljesülésére való várakozással, vagy egyéb háttérbeli feldolgozási műveletek elvégzésével.

A **Duration (ms)** értékek az egyes műveletek *kezdési* és *befejezési* időbélyege közötti különbséget adja meg. A vásznon és a vizualizációkon végzett műveletek sorosan, egyetlen Felhasználó felületi szálon vannak végrehajtva, amelyen több művelet osztozik. A jelentett időtartam magában foglalja a többi művelet befejezésééig a várakozási sorban töltött időt is. A GitHubon megtalálható [Teljesítményelemző minta](https://github.com/microsoft/powerbi-desktop-samples/tree/master/Performance%20Analyzer) és az ahhoz tartozó [dokumentáció](https://github.com/microsoft/powerbi-desktop-samples/blob/master/Performance%20Analyzer/Power%20BI%20Performance%20Analyzer%20Export%20File%20Format.docx) részletesen leírja a vizualizációk által végzett adatlekérdezés és a renderelés menetét.


![naplóadatok elemei](media/desktop-performance-analyzer/performance-analyzer-06.png)

Miután elvégezte a jelentés elemein azokat a műveleteket, amelyeket a Teljesítményelemzővel mérni kívánt, kattintson a **Leállítás** gombra. A teljesítményadatok azután is megtekinthetők és elemezhetők maradnak az ablaktáblán, hogy Ön a **Leállítás** gombra nyomott.

A Teljesítményelemző ablaktábla adatainak törléséhez kattintson a **Törlés** gombra. A **Törlés** paranccsal a rendszer minden adatot töröl, mentés nélkül. A naplózott adatok mentésével kapcsolatban lásd a következő szakaszt. 

## <a name="refreshing-visuals"></a>Vizualizációk frissítése

A Teljesítményelemző ablaktáblán a **Vizualizációk frissítése** paranccsal frissítheti a jelentés aktuális oldalán található összes vizualizációt, amelyekről a Teljesítményelemző összegyűjti az adatokat.

Emellett a vizualizációk külön-külön is frissíthetők. Amikor a Teljesítményelemző rögzítést végez, az egyes vizualizációk jobb felső sarkában található **Vizualizáció frissítése** paranccsal frissítheti az adott vizualizációt, és rögzítheti annak teljesítményadatait.

![egyetlen vizualizáció frissítése](media/desktop-performance-analyzer/performance-analyzer-07.png)

## <a name="saving-performance-information"></a>Teljesítményadatok mentése

A Teljesítményelemző által a jelentésekről létrehozott adatokat az **Exportálás** gombbal mentheti. Az **Exportálás** egy .json-fájlba menti a Teljesítményelemző ablaktáblán található információkat. 

![A teljesítményelemző naplófájljának mentése](media/desktop-performance-analyzer/performance-analyzer-05.png)


## <a name="next-steps"></a>További lépések
Ha többet szeretne megtudni a **Power BI Desktopról**, illetve a szoftver használatának kezdeti lépéseiről, tekintse meg a következő cikkeket.

* [Mi az a Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Lekérdezések áttekintése a Power BI Desktopban](../transform-model/desktop-query-overview.md)
* [Adatforrások a Power BI Desktopban](../connect-data/desktop-data-sources.md)
* [Csatlakozás adatokhoz a Power BI Desktopban](../connect-data/desktop-connect-to-data.md)
* [Adatok formázása és kombinálása a Power BI Desktoppal](../connect-data/desktop-shape-and-combine-data.md)
* [Gyakori lekérdezési feladatok a Power BI Desktopban](../transform-model/desktop-common-query-tasks.md)   

A Teljesítményelemző mintával kapcsolatban az alábbi források kínálnak információt.

* [Teljesítményelemző minta](https://github.com/microsoft/powerbi-desktop-samples/tree/master/Performance%20Analyzer)
* [A Teljesítményelemző minta dokumentációja](https://github.com/microsoft/powerbi-desktop-samples/blob/master/Performance%20Analyzer/Power%20BI%20Performance%20Analyzer%20Export%20File%20Format.docx)
