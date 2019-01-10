---
title: Ajánlott eljárások a Power BI Embedded teljesítményének javításához
description: Ez a cikk a beépített elemzésekhez ajánlott eljárásokhoz nyújt útmutatást
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-embedded
ms.topic: conceptual
ms.date: 12/12/2018
ms.openlocfilehash: e28801a15cf50351d737af63bc48f655ca85d28f
ms.sourcegitcommit: 750f0bfab02af24c8c72e6e9bbdd876e4a7399de
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/04/2019
ms.locfileid: "54008166"
---
# <a name="power-bi-embedded-performance-best-practices"></a>Ajánlott eljárások a Power BI Embedded teljesítményének javításához

Ez a cikk az alkalmazásban lévő jelentések, irányítópultok és csempék gyorsabb rendereléséhez ad tanácsokat

## <a name="embed-parameters"></a>Paraméterek beágyazása

A Powerbi.embed() metódus átvesz néhány paramétert egy jelentés, irányítópult vagy csempe beágyazásához. Ezek a paraméterek befolyásolják a teljesítményt.

### <a name="embed-url"></a>Beágyazási URL-cím

Kerülje a beágyazási URL-cím saját generálását. A beágyazási URL-t állítsa elő inkább a [Get reports](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Frest%2Fapi%2Fpower-bi%2Freports%2Fgetreportsingroup&data=02%7C01%7CMark.Ghanayem%40microsoft.com%7C07ca68ceb37a48e3f3de08d64968707a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636777110256168308&sdata=22lkqRM2w1MQfrM8dooedaPqqIU8PufTq9TT4VDzRo0%3D&reserved=0), a [Get dashboards](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Frest%2Fapi%2Fpower-bi%2Fdashboards%2Fgetdashboardsingroup&data=02%7C01%7CMark.Ghanayem%40microsoft.com%7C07ca68ceb37a48e3f3de08d64968707a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636777110256168308&sdata=nfWRgbSoXVF42Rg%2Ba9491u19uksXp%2FAyz%2Fa%2Ba7%2FCtdA%3D&reserved=0) vagy a [Get tiles](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Frest%2Fapi%2Fpower-bi%2Fdashboards%2Fgettilesingroup&data=02%7C01%7CMark.Ghanayem%40microsoft.com%7C07ca68ceb37a48e3f3de08d64968707a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636777110256178318&sdata=LgZ27TynNpqQJDrb3aHWGQXIS%2FzichAO9De5M2uhF1Q%3D&reserved=0) API hívásával. Az URL-hez hozzáadtunk egy új, **_config_** nevű paramétert, amely a teljesítmény javítására szolgál.

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

* Mindig a [Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop/) legújabb verzióját használja.

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
