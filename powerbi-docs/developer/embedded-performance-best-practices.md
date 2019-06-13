---
title: Ajánlott eljárások a Power BI Embedded teljesítményének javításához
description: Ez a cikk a beépített elemzésekhez ajánlott eljárásokhoz nyújt útmutatást
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 12/12/2018
ms.openlocfilehash: d2e4a29b3dd7e36081458ff6ca51b0006a10466f
ms.sourcegitcommit: 81ba3572531cbe95ea0b887b94e91f94050f3129
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750939"
---
# <a name="power-bi-embedded-performance-best-practices"></a>Ajánlott eljárások a Power BI Embedded teljesítményének javításához

Ez a cikk az alkalmazásban lévő jelentések, irányítópultok és csempék gyorsabb rendereléséhez ad tanácsokat

## <a name="embed-parameters"></a>Paraméterek beágyazása

A Powerbi.embed() metódus átvesz néhány paramétert egy jelentés, irányítópult vagy csempe beágyazásához. Ezek a paraméterek befolyásolják a teljesítményt.

### <a name="embed-url"></a>Beágyazási URL-cím

Kerülje a beágyazási URL-cím saját generálását. A beágyazási URL-t állítsa elő inkább a [Get reports](/rest/api/power-bi/reports/getreportsingroup), a [Get dashboards](/rest/api/power-bi/dashboards/getdashboardsingroup) vagy a [Get tiles](/rest/api/power-bi/dashboards/gettilesingroup) API hívásával. Az URL-hez hozzáadtunk egy új, **_config_** nevű paramétert, amely a teljesítmény javítására szolgál.

### <a name="permissions"></a>Engedélyek

Ha nem **Szerkesztési nézetben** kíván beágyazni egy jelentést, akkor adjon **Megtekintési** jogosultságot. A beágyazási kód így nem inicializálja a Szerkesztési módhoz használt összetevőket.

### <a name="filters-bookmarks-and-slicers"></a>Szűrők, könyvjelzők és szeletelők

A jelentés vizualizációi általában a gyorsítótárazott adatokkal vannak mentve. A tapasztalt teljesítmény a gyorsítótárazott adatok használatával van megadva. A jelentések gyorsítótárazott adatokat renderelnek a lekérdezések végrehajtása során. Szűrők, könyvjelzők vagy szeletelők megadása esetén a gyorsítótárazott adatok nem számítanak. Ilyenkor a vizualizációk csak a lekérdezés futása után lesznek renderelve.

Ha azonos szűrőkkel ágyaz be jelentéseket, akkor a jelentéseket a szűrők alkalmazása után mentse, hogy elkerülje a szűrők listájának átadását a betöltési konfigurációban.

## <a name="preload"></a>Előzetes betöltés

Az *előzetes betöltés* JavaScript API használata javítja a végfelhasználó által tapasztalt teljesítményt.
A Powerbi.preload() javascript- és css-fájlokat, valamint a jelentésbe ágyazáshoz később használható más összetevőket tölt le.

A preload metódust akkor hívja meg, ha nem azonnal ágyazza be a jelentést. Ha a jelentés például egy gombra való kattintásra van beágyazva, a preloadot érdemesebb az előző oldal betöltésekor meghívni. Így gyorsabb lesz a renderelés, amikor az alkalmazás felhasználója a gombra kattint.

## <a name="measure-performance"></a>Teljesítménymérés

A teljesítmény mérésére a következők használhatók:

1. Betöltés: a jelentés inicializálásáig eltelt idő (a felhasználó nem lát folyamatjelzőt).
2. Renderelés: a jelentés tényleges adatokkal való teljes rendereléséig eltelt idő. A renderelési esemény minden alkalommal aktiválódik, ha a jelentés újra van renderelve (tehát a szűrők alkalmazása után). Egy jelentés első méréséhez a számításokat mindenképpen az elsőként bekövetkező eseményre végezze el.

Ha elérhetők, a gyorsítótárazott adatok lesznek renderelve, ezekhez az adatokhoz azonban még nem rendelkezünk eseménnyel.

## <a name="update-tools-and-sdk-packages"></a>Frissítési eszközök és SDK-csomagok

Tartsa naprakészen az eszközöket és SDK-csomagokat.

* Mindig a [Power BI Desktop](https://powerbi.microsoft.com/desktop/) legújabb verzióját használja.

* Telepítse a [Power BI-ügyfél SDK](https://github.com/Microsoft/PowerBI-JavaScript) legújabb verzióját. Ellenőrizze időnként a folyamatosan megjelenő további fejlesztéseket.

* Telepítendő csomagok:
    * Npm-csomag: powerbi-client
    * NuGet-csomag: Microsoft.PowerBI.JavaScript

> [!Note]
> Ne feledje, hogy a betöltési idő elsősorban a jelentéssel és magukkal az adatokkal kapcsolatos elemektől függ. Ilyen tényező a vizualizációk száma, az adatok mennyisége, valamint a lekérdezések és a számított mértékek bonyolultsága. A jelentés betöltési idejét az [ajánlott eljárások](../power-bi-reports-performance.md) követésével javíthatja.

## <a name="next-steps"></a>Következő lépések

* [Ajánlott eljárások Power BI-jelentések teljesítményének javításához](../power-bi-reports-performance.md)
* [A Power BI Embeddeddel kapcsolatos problémák elhárítása](embedded-troubleshoot.md)
* [Power BI Embedded GYIK](embedded-faq.md)
