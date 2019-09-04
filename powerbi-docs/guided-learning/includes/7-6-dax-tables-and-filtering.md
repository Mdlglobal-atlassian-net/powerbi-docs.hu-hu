---
ms.openlocfilehash: 629c53358f757002f2b3dcda468641bbaaa2f4d4
ms.sourcegitcommit: c0f4d00d483121556a1646b413bab75b9f309ae9
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70166725"
---
A **DAX** és az Excel képletei között az egyik lényeges különbség, hogy a DAX lehetővé teszi *teljes táblák* átadását a kifejezések között, és nem korlátozza azt egyetlen értékre. Ez azzal a jelentős előnnyel jár, hogy a DAX így lehetővé teszi a kifejezésekben a táblák szűrését, és ezt követően szűrt értékhalmazzal lehet műveleteket végezni.

![](media/7-6-dax-tables-and-filtering/dax-tables-filtering_1.png)

A DAX-szal teljesen új számított táblákat is létre lehet hozni, amelyeket más táblákhoz hasonlóan lehet kezelni, például kapcsolatokat lehet létrehozni köztük és más táblák között az adatmodellben.

## <a name="dax-table-functions"></a>A DAX táblafüggvényei
A DAX számos **táblafüggvénnyel** rendelkezik, többek között az alábbiakkal:

* FILTER
* ALL
* VALUES
* DISTINCT
* RELATEDTABLE

Ezek a függvények nem egyedi értékeket, hanem teljes táblákat adnak vissza. Egy **táblafüggvény** eredményét általában egy nagyobb kifejezés részeként további elemzéshez használjuk, és a visszaadott táblát nem végső értékként kezeljük. Fontos megjegyezni, hogy a táblafüggvények eredményei öröklik az oszlopok közötti kapcsolatokat.

A kifejezésekben kombinálhatóak a táblafüggvények, amennyiben minden felhasznált függvény táblát használ fel és táblát is ad vissza. Tekintse meg például az alábbi DAX-kifejezést:

    FILTER (ALL (Table), Condition)

Ez a kifejezés a *Table* egészére vonatkoztatja a szűrést, és figyelmen kívül hagy minden aktuális tartalomszűrést.

A DISTINCT függvény egy oszlop azon egyedi értékeit adja vissza, amelyek az aktuális kontextusban láthatóak is. Ezért ha a fenti DAX-példában a kifejezés az **ALL** függvényt tartalmazza, akkor a kifejezés figyelmen kívül hagyja a szűrőket, ha azonban az **ALL** helyett a **DISTINCT** szerepel benne, akkor figyelembe veszi őket.

## <a name="counting-values-with-dax"></a>Értékek számolása a DAX-szel
A Power BI-jelentések létrehozói számára gyakori kérdés az alábbi:

* Vajon hány érték szerepel egy adott oszlopban?

A kérdés meglehetősen egyszerűnek tűnik, ha a tábla Ön előtt van megjelenítve, a DAX azonban másféle megközelítést alkalmaz, különösen ha a táblák között kapcsolatok is vannak.

A Power BI-ban és a DAX-ban szerepelnek például olyan értékek is, amelyek nincsenek megfelelő keresztindexeléssel ellátva. Ha a bemeneti kapcsolat hibás, akkor a DAX egy olyan új sort ad hozzá a szóban forgó táblához, amely minden mezőben üres értéket tartalmaz, és a hivatkozási integritás garantálása érdekében az új sort a nem indexelt sorhoz kapcsolja. Ha a függvényben üres sorok szerepelnek – és ez gyakran előfordul például az **ALL** használatánál –, akkor a visszatérési értékben ezek az üres sorok hozzáadódnak az adott oszlop értékeinek a számához.

DAX-függvényekkel teljes, számított táblákat is létre lehet hozni. A DAX használatával létrehozott számított táblákhoz egy **NAME** és egy **TABLE** függvény is szükséges. A számított táblákat a szokásos módon, más táblákhoz hasonlóan lehet használni, így többek között kapcsolatok is létrehozhatók.

> A videótartalomért köszönet illeti [Alberto Ferrarit az SQLBI-tól](http://www.sqlbi.com/learning-dax)
> 
> 

