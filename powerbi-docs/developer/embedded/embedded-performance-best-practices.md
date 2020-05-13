---
title: Ajánlott eljárások a Power BI Embedded teljesítményének javításához
description: Ez a cikk a beépített elemzésekhez ajánlott eljárásokhoz nyújt útmutatást
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 12/12/2018
ms.openlocfilehash: c619f37ac062eec02eb379ba7cd97731254a171a
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83279388"
---
# <a name="power-bi-embedded-performance-best-practices"></a>Ajánlott eljárások a Power BI Embedded teljesítményének javításához

Ez a cikk az alkalmazásban lévő jelentések, irányítópultok és csempék gyorsabb rendereléséhez ad tanácsokat.

> [!Note]
> Ne feledje, hogy a betöltési idő elsősorban a jelentéssel és magukkal az adatokkal kapcsolatos elemektől függ. Ilyen tényező a vizualizációk száma, az adatok mérete, valamint a lekérdezések és a számított mértékek bonyolultsága. További információt a [Power BI optimalizálási útmutatójában](../../guidance/power-bi-optimization.md) talál.

## <a name="update-tools-and-sdk-packages"></a>Frissítési eszközök és SDK-csomagok

Tartsa naprakészen az eszközöket és SDK-csomagokat.

* Mindig a [Power BI Desktop](https://powerbi.microsoft.com/desktop/) legújabb verzióját használja.

* Telepítse a [Power BI-ügyfél SDK](https://github.com/Microsoft/PowerBI-JavaScript) legújabb verzióját. Ellenőrizze időnként a folyamatosan megjelenő további fejlesztéseket.

## <a name="embed-parameters"></a>Paraméterek beágyazása

A `powerbi.embed(element, config)` metódus egy elemet és egy konfigurációt kap. A konfigurációs paraméter olyan mezőket tartalmaz, amelyek hatással vannak a teljesítményre.

### <a name="embed-url"></a>Beágyazási URL-cím

Kerülje a beágyazási URL-cím saját generálását. A beágyazási URL-t állítsa elő inkább a [Get reports](/rest/api/power-bi/reports/getreportsingroup), a [Get dashboards](/rest/api/power-bi/dashboards/getdashboardsingroup) vagy a [Get tiles](/rest/api/power-bi/dashboards/gettilesingroup) API hívásával. Az URL-hez hozzáadtunk egy új, **_config_** nevű paramétert, amely a teljesítmény javítására szolgál.

### <a name="permissions"></a>Engedélyek

Ha nem Szerkesztési nézetben kíván beágyazni egy jelentést, akkor adjon **Megtekintési** jogosultságot. A beágyazási kód így nem inicializálja a Szerkesztési módhoz használt összetevőket.

### <a name="filters-bookmarks-and-slicers"></a>Szűrők, könyvjelzők és szeletelők

A jelentés vizualizációi általában a gyorsítótárazott adatokkal vannak mentve. A tapasztalt teljesítmény a gyorsítótárazott adatok használatával van megadva. A jelentések gyorsítótárazott adatokat renderelnek a lekérdezések végrehajtása során. Ha szűrőket, könyvjelzőket vagy szeletelőket ad meg, a gyorsítótárazott adatok nem relevánsak, a rendszer így a vizualizációs lekérdezés után rendereli a vizualizációkat.

Ha azonos szűrőkkel, könyvjelzőkkel vagy szeletelőkkel ágyaz be jelentéseket, akkor a jelentéseket a szűrők, könyvjelzők és szeletelők alkalmazása után mentse a jobb teljesítmény érdekében. Ez rendereli a jelentést a gyorsítótárazott adatokkal, amely szűrőket, könyvjelzőket és szeletelőket tartalmaz.

## <a name="switching-between-reports"></a>Váltás a jelentések között

Amikor több jelentést ágyaz be ugyanazon iFrame-be, ne hozzon létre új iFrame-et minden jelentéshez. Ehelyett használja a `powerbi.embed(element, config)` metódust egy másik konfigurációval az új jelentés beágyazásához.

> [!NOTE]
> Alkalmazás tulajdonában lévő adatok esetén előfordulhat, hogy nem hatékony megoldás a jelentések közötti váltás, mivel így új beágyazási tokent kell létrehozni.

## <a name="query-caching"></a>Lekérdezések gyorsítótárazása

A Power BI Premium- vagy Power BI Embedded-kapacitással rendelkező cégek kihasználhatják a lekérdezések gyorsítótárazása funkciót az adatkészletekhez társított jelentések felgyorsítására.

[További információ a Power BI lekérdezési gyorsítótárazásáról](../../connect-data/power-bi-query-caching.md).

## <a name="preload"></a>Előzetes betöltés

A `powerbi.preload()` használatával javíthatja a végfelhasználói élményt. A `powerbi.preload()` metódus javascript- és css-fájlokat, valamint a jelentésbe ágyazáshoz később használható más összetevőket tölt le.

A `powerbi.preload()` metódust akkor hívja meg, ha nem azonnal ágyazza be a jelentést. Ha például a beágyazott Power BI-tartalom nem jelenik meg a kezdőlapon, akkor a tartalom beágyazásához használt összetevők letöltéséhez és gyorsítótárazásához használja a `powerbi.preload()` metódust.

## <a name="bootstrapping-the-iframe"></a>Az iFrame rendszerindítása

> [!NOTE]
> Az iFrame rendszerindítással történő előkészítéséhez a [Power BI-ügyfél SDK](https://github.com/Microsoft/PowerBI-JavaScript) 2.9-es verziója szükséges.

A `powerbi.bootstrap(element, config)` lehetővé teszi a beágyazás megkezdését, mielőtt az összes szükséges paraméter elérhetővé válik. A bootstrap (rendszerindítási) API előkészíti és inicializálja az iframe-et.
A bootstrap API használatakor továbbra is meg kell hívni a `powerbi.embed(element, config)` metódust ugyanazon a HTML-elemen.

Ennek a funkciónak a egyik használati esete például az, amikor az iframe-rendszerindítást a háttérhívásoknál futtatjuk párhuzamosan a beágyazáshoz.
> [!TIP]
> A rendszerindítási API-t akkor érdemes használni, ha az iframe-et létre lehet hozni, mielőtt az láthatóvá válik a végfelhasználó számára.

[További információ az iFrame-ek rendszerindításáról](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bootstrap-For-Better-Performance).

## <a name="measure-performance"></a>Teljesítménymérés

### <a name="performance-events"></a>Teljesítményesemények

A beágyazott teljesítmény méréséhez két eseményt használhat:

1. Betöltött esemény: A jelentés inicializálásáig eltelt idő (a Power BI emblémája eltűnik, ha a betöltés véget ért).
2. Renderelt esemény: A jelentés tényleges adatokkal való teljes rendereléséig eltelt idő. A renderelési esemény minden alkalommal aktiválódik, ha a jelentés újra van renderelve (tehát a szűrők alkalmazása után). Egy jelentés méréséhez a számításokat mindenképpen az elsőként bekövetkező eseményre végezze el.

A gyorsítótárazott adatokat a rendszer akkor rendereli, amikor azok elérhetővé válnak, azonban nem hoz létre további eseményeket.

[További információ az események kezeléséről](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Handling-Events).

### <a name="performance-analyzer"></a>Teljesítményelemző

A jelentéselemek teljesítményének vizsgálatához használhatja a Power BI Desktop Teljesítményelemzőjét.
A Teljesítményelemzővel megtekintheti és rögzítheti azokat a naplókat, amelyek a jelentéselemek működését mérik.

[További információ a Teljesítményelemzőről](../../create-reports/desktop-performance-analyzer.md).

> [!NOTE]
> A beágyazott jelentések teljesítményét célszerű gyakran összehasonlítani a powerbi.com teljesítményével. Így könnyebben azonosíthatja a teljesítménnyel kapcsolatos problémák gyökerét

## <a name="next-steps"></a>Következő lépések

* [Optimalizálási útmutató a Power BI-hoz](../../guidance/power-bi-optimization.md)
* [A Power BI Embeddeddel kapcsolatos problémák elhárítása](embedded-troubleshoot.md)
* [Power BI Embedded GYIK](embedded-faq.md)
