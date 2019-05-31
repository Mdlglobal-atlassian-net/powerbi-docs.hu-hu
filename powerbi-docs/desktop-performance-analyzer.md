---
title: Vizsgálja meg a Power BI Desktopban jelentés elem teljesítmény Performance Analyzer használatával
description: Ismerje meg, hogyan Vizualizációk és a jelentés elemeinek végez erőforrás-használat és a válaszképesség
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/15/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 1851e0a55bf01073a6591f64de43830a72eca89b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65854413"
---
# <a name="use-performance-analyzer-to-examine-report-element-performance"></a>Vizsgálja meg a jelentés elemének teljesítmény Performance Analyzer használatával

A **Power BI Desktop** találja ki, hogyan egyes Vizualizációk és DAX-képleteket, például a jelentéselemek hajt végre. Használatával a **Performance Analyzer**, láthatja, és a rekordot, amely naplózza mérheti, hogy hogyan mindegyike a jelentés elemeinek hajt végre, ha a felhasználók használják őket, és a teljesítményük mely aspektusainak a legtöbb (vagy legalább) erőforrás-igényes.

![Teljesítmény-elemző eszköz](media/desktop-performance-analyzer/performance-analyzer-01.png)

Performance Analyzer megvizsgálja és megjeleníti az összes Vizualizáció frissítéshez szükséges időtartam kezdeményezhet a felhasználói interakció érdekében, és megadja az adatokat, így megtekintését, részletes elemzést és exportálhatja az eredményeket. Performance Analyzer segítségével azonosíthatja a vizualizációkat, amelyek negatív hatással vannak a jelentések teljesítményét, és azonosíthatja a hatás az az oka.

## <a name="displaying-the-performance-analyzer-pane"></a>A Performance Analyzer ablaktábla megjelenítése

A **Power BI Desktop** válassza ki a **nézet** menüszalagon. Az a **megjelenítése** területén a **nézet** jelölőnégyzetet is jelölje a menüszalag **Performance Analyzer** Performance Analyzer panel megnyitásához.

![A nézet menüszalagon Performance analyzer kiválasztása](media/desktop-performance-analyzer/performance-analyzer-02.png)

A kijelölt a Performance Analyzer saját panel jobb oldalán a jelentésvásznon jelenik meg.

## <a name="using-performance-analyzer"></a>Performance Analyzer használatával

Elemző korrelálására a feldolgozási idő (beleértve a létrehozni vagy frissíteni a vizualizációt az idő), amely egy lekérdezés futtatása a felhasználói beavatkozás következtében kezdeményezett jelentéselemek frissítéséhez szükséges. Például egy szeletelő módosítása a szeletelő Vizualizáció módosítható egy lekérdezést kell küldeni az adatmodellt, és szükséges érintett vizualizációkat, amelyeket frissíteni kell az új beállítások miatt. 

Ahhoz, hogy a rögzítés megkezdéséhez Performance Analyzer, egyszerűen válassza **elindítani a felvételt.**

![Rögzítés indítása](media/desktop-performance-analyzer/performance-analyzer-03.png)

A jelentés minden olyan műveletek jelenik meg, és a Performance Analyzer ablaktáblán, az ahhoz, hogy a Vizualizáció betöltése a Power BI által naplózott. Például például hogy egy jelentést, amely a felhasználók rendelkeznek mondta frissítése hosszú időt vesz igénybe. Vagy az egyes jelentésekben a vizualizációkban megjelenített egy csúszkát úgy kell beállítani, hosszú időt igénybe. Teljesítményét elemző utasíthatja a vizualizációt a probléma oka, és azonosítja a Vizualizáció mely aspektusainak a leghosszabb időtartamú feldolgozása tovább tart. 

Felvétel elindítását követően a **elindítani a felvételt** gomb szürkén jelenik out (inaktív, mert azt már elkezdte a rögzítés) és a **leállítása** gomb nincs aktív. 

Teljesítményét elemző gyűjt, és valós idejű teljesítmény mérésére információkat jeleníti meg. Így minden alkalommal, amikor egy vizualizációra kattint egy szeletelő áthelyezi vagy bármilyen egyéb módon kezelheti Performance Analyzer azonnal eredményeit jeleníti meg a teljesítmény a panelen.

Ha a panel további információkat a megjeleníthetőnél, görgetősáv úgy tűnik, hogy navigáljon a további információkat.

Minden egyes interakció a panelen, a művelet által kezdeményezett a naplóbejegyzéseket ismertető szakasz azonosítóval rendelkezik. Az alábbi ábrán a kapcsolati volt, hogy a felhasználók egy szeletelő megváltozott-e.

![A szakaszok kapcsolati típus alapján](media/desktop-performance-analyzer/performance-analyzer-04.png)

Egyes Vizualizációk adatait a következő kategóriákba tartozó feladatok végrehajtásához (időtartam) töltött időt tartalmazza:

* **DAX-lekérdezés** – egy DAX-lekérdezés volt szükség, ha ez az az idő a vizualizációt, a kérést küldő között, és az Analysis Services csak az eredményeket adja vissza.
* **Vizualizáció megjelenítési** – a képernyőre, beleértve az minden webes képet és a geokódolás fogadásához szükséges idő a vizualizációhoz szükséges időt. 
* **Más** -lekérdezés előkészítése, Várakozás az egyéb Vizualizációk végrehajtásához vagy más háttérben történő feldolgozás a Vizualizáció által szükséges időt.

![naplóadatok elemei](media/desktop-performance-analyzer/performance-analyzer-06.png)

Miután, hogy kezelhetők a szeretné mérni a teljesítményét elemző jelentés elemeinek, kiválaszthatja a **leállítása** gombra. A teljesítményadatok kiválasztása után a panelen marad **leállítása** a elemezhet.

Törölje a Performance Analyzer ablaktáblán az adatokat, válassza ki a **törölje a jelet**. Minden információt pedig törölve lesz, és a nem mentett kiválasztásakor **egyértelmű**. Tekintse meg a következő szakaszban megtudhatja, hogyan naplók az adatok mentéséhez. 

## <a name="refreshing-visuals"></a>Vizualizációk frissítése

Választhat **Vizualizációk frissítése** frissítse a jelentés az aktuális oldal minden vizualizációjához, és ezáltal Performance Analyzer minden Vizualizáció információt gyűjteni a Performance Analyzer ablaktáblán.

Az egyes Vizualizációk is frissítheti. Performance Analyzer dokumentálásakor kiválaszthatja **frissítse a Vizualizáció** egyes Vizualizációk frissítése a Vizualizáció jobb felső sarkában található, és a teljesítményadatok rögzítése.

![az egyéni Vizualizáció frissítése](media/desktop-performance-analyzer/performance-analyzer-07.png)

## <a name="saving-performance-information"></a>Teljesítmény-adatainak mentése

Az információ, amely Performance Analyzer hoz létre jelentést kattintva mentheti a **exportálása** gombra. Kiválasztásával **exportálása** egy .JSON kiterjesztésű fájlt hoz létre a Performance Analyzer panelről információkat. 

![Mentse a naplófájlt teljesítményét elemző eszköz](media/desktop-performance-analyzer/performance-analyzer-05.png)


## <a name="next-steps"></a>Következő lépések
Ha többet szeretne megtudni a **Power BI Desktopról**, illetve a szoftver használatának kezdeti lépéseiről, tekintse meg a következő cikkeket.

* [Mi az a Power BI Desktop?](desktop-what-is-desktop.md)
* [Lekérdezések áttekintése a Power BI Desktopban](desktop-query-overview.md)
* [Adatforrások a Power BI Desktopban](desktop-data-sources.md)
* [Csatlakozás adatokhoz a Power BI Desktopban](desktop-connect-to-data.md)
* [Adatok formázása és kombinálása a Power BI Desktoppal](desktop-shape-and-combine-data.md)
* [Gyakori lekérdezési feladatok a Power BI Desktopban](desktop-common-query-tasks.md)   

