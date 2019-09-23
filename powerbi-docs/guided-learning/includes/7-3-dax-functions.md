---
ms.openlocfilehash: 06ee6ad7ade46d811c6340d905150c6dd3810c55
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61273390"
---
A DAX számos függvényt biztosít az adatok alakításához, formálásához vagy más típusú elemzéséhez. Ezek a függvények az alábbi kategóriákba sorolhatók:

* **Összesítésfüggvények**
* **Számlálófüggvények**
* **Logikai függvények**
* **Információs függvények**
* **Szövegfüggvények**
* **Dátumfüggvények**

Hasonlóan ahhoz, ahogy az Excelben történik, amikor elkezd beírni egy képletet a Power BI Desktop **képletsávjába**, megjelenik a rendelkezésre álló függvények listája, hogy segítsen kiválasztani a használandó függvényt. A billentyűzet **felfelé** és **lefelé** mutató nyilait használva bármelyik rendelkezésre álló függvény kiválasztható, amivel egyidejűleg megjelenik a függvény rövid leírása.

A Power BI az aktuálisan beírt betűknek megfelelő függvényeket jeleníti meg. Például, ha beír egy *S* betűt, csak az *S*-el kezdődő függvények jelennek meg a listán. Ha *Su*-t ír be, akkor csak azok a függvények fognak megjelenni a listán, amelyek neve *tartalmazza* az *Su* betűsort (a névnek nem kell *Su*-val kezdődnie, csak az a fontos, hogy tartalmazza a beírt betűsort).

![](media/7-3-dax-functions/dax-functions_1.png)

Ilyen módon könnyen kitapasztalhatja a DAX működését, és megtalálhatja a Power BI-ban rendelkezésre álló különböző DAX-függvényeket. Mindössze el kell kezdenie gépelni, a Power BI közben segíteni fog.

Most, hogy már tudja, hogyan kell elkezdeni egy DAX-képletet, tekintse át az egyes függvénykategóriákat.

## <a name="aggregation-functions"></a>Összesítésfüggvények
A DAX-ban számos **összesítésfüggvény** elérhető, többek közt az alábbi gyakran használt függvények is:

* SUM
* AVERAGE
* MIN
* MAX
* SUMX (és más *X* függvények)

Ezek a függvények csak numerikus oszlopokhoz használhatók, és általában egyszerre egy oszlopot tudnak összesíteni.

Ugyanakkor az **X**-re végződő speciális összesítőfüggvények, mint amilyen a **SUMX** több oszlopot is kezelni tudnak. Ezek a függvények iterálódnak a táblában, és minden sorra vonatkozóan kiértékelik a kifejezést.

## <a name="counting-functions"></a>Számlálófüggvények
A DAX-ban gyakran használt **számlálófüggvényei** többek között az alábbiak:

* COUNT
* COUNTA
* COUNTBLANK
* COUNTROWS
* DISTINCTCOUNT

Ezek a függvények megszámolják a különböző elemeket, például a különböző értékeket, a nem üres értékeket és a táblák sorait.

## <a name="logical-functions"></a>Logikai függvények
A DAX többek között az alábbi **logikai függvényeket** tartalmazza:

* AND
* OR
* NOT
* IF
* IFERROR

Ezek a speciális függvények *műveleti jelekkel* is kifejezhetők. Például az **AND** helyett az **&&** is beírható a DAX-képletbe.

Műveleti jeleket (például az **&&** jelet) akkor érdemes használni, ha egynél több feltételre van szükség a képletben. Más esetekben a legjobb magának a függvénynek a nevét (például az **AND** nevet) használni a DAX-kód könnyebb olvashatósága érdekében.

## <a name="information-functions"></a>Információs függvények
A DAX **információs függvényei** többek között:

* ISBLANK
* ISNUMBER
* ISTEXT
* ISNONTEXT
* ISERROR

Bár ezek a függvények esetenként hasznosak lehetnek, jobb előre tisztában lenni az oszlopok adattípusával, mint arra támaszkodni, hogy ezek a függvények adjanak információt az adattípusról.

A **MAX** és a **MIN** függvényeket a DAX értékek *összesítéséhez* és *összehasonlításához* is használja.

## <a name="text-functions"></a>Szövegfüggvények
A DAX **szövegfüggvényei** többek között az alábbiak:

* CONCATENTATE
* REPLACE
* SEARCH
* UPPER
* FIXED

Ezek a **szövegfüggvények** hasonló módon működnek, mint az Excel ugyanilyen nevű függvényei. Ha már van tapasztalata azzal kapcsolatban, hogy az Excel hogyan kezeli a szövegfüggvényeket, máris egy lépéssel előrébb jár. Ha nincs ilyen tapasztalata, kísérletezzen bátran ezekkel a függvényekkel a Power BI-ban, és tanulmányozza, hogyan viselkednek.

## <a name="date-functions"></a>Dátumfüggvények
A DAX a következő **dátumfüggvényeket** tartalmazza:

* DATE
* HOUR
* NOW
* EOMONTH
* WEEKDAY

Noha ezek a függvényekkel jól hasznosíthatók *dátum* értékeken alapuló információk kiszámításához és a bennük tárolt információk kinyeréséhez, dátumtáblát használó időelemzésre nem alkalmasak.

> A videótartalomért köszönet illeti [Alberto Ferrarit az SQLBI-tól](http://www.sqlbi.com/learning-dax)
> 
> 

