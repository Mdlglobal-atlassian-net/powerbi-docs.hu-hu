---
ms.openlocfilehash: 4ea1b2141cf9a072f11a3a62789c7c0ec5b500a4
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "73799900"
---
A DAX használatával kétfajta elsődleges számítás hozható létre:

* **számított oszlopok**
* **számított mértékek**

Ezek részletes kifejtése előtt érdemes alaposan megismerni a DAX táblázatokra és oszlopokra érvényes szintaxisát, amelyet a **számított oszlopok** és a **számított mértékek** létrehozásához is használni fog.

## <a name="dax-table-and-column-name-syntax"></a>DAX táblázat- és oszlopnévszintaxis
Új oszlop vagy mérték létrehozásakor fontos ismerni a DAX-beli táblázatnevek általános formátumát:

    'Table Name'[ColumnName]

Ha a táblázat neve szóközöket tartalmaz (mint a fenti példában), akkor a nevet kötelező aposztrófok közé zárni. Ha a táblázat neve nem tartalmaz szóközöket, akkor az aposztrófok elhagyhatók, és a szintaxis az alábbihoz hasonló:

    TableName[ColumnName]

Az alábbi képen egy DAX-képlet létrehozása látható a Power BI-ban:

![](media/7-2-dax-calculation-types/dax-calc-types_1.png)

A táblázatnév is teljesen elhagyható, és elég csak az oszlopnevet használni, de ez az eljárás nem a legalkalmasabb áttekinthető függvények (ezáltal áttekinthető DAX-kód) írására. Az oszlopnevekhez mindig hozzátartoznak a szögletes zárójelek.

Ajánlott *mindig* a következők betartásával eljárni:

* Szóköz nélküli táblázatnevek
* A táblázat neve mindig szereplejen a képletekben (ne maradjon ki, bár a DAX ezt lehetővé teszi)

## <a name="creating-calculated-columns"></a>Számított oszlopok létrehozása
A **számított oszlopok** akkor hasznosak, ha kijelölést vagy szűrést kell végezni az érték alapján, vagy ha egy számítást egy táblázat minden sorában el kell végezni.

A Power BI Desktopban a **Modellezés** lap **Új oszlop** gombját választva lehet számított oszlopot létrehozni. Ezt érdemes **Adat** nézetben (és nem **Jelentés** vagy **Kapcsolatok** nézetben) megtenni, mert így látszik az újonnan létrehozott oszlop, a **Képletsáv** pedig aktív és készen áll a DAX-képlet beírásához.

![](media/7-2-dax-calculation-types/dax-calc-types_2a.png)

Az **Új oszlop** gombra kattintva a **képletsávban** megjelenik az alapértelmezett oszlopnév (amely természetesen a képletnek megfelelően módosítható), valamint az **=** operátor, az adatrácsban pedig megjelenik az új oszlop, ahogyan az alábbi ábra mutatja.

![](media/7-2-dax-calculation-types/dax-calc-types_3.png)

Egy számított oszlop kötelező elemei a következők:

* új oszlopnév
* legalább egy függvény vagy kifejezés

Ha a számított oszlop képlete egy táblázatra vagy oszlopra hivatkozik, akkor nem kell megadni a táblázat egy sorát – a Power BI minden számítás során az adott sorhoz számítja ki az oszlop értékét.

## <a name="creating-calculated-measures"></a>Számított mértékek létrehozása
**Számított mértékek** százalékos értékek vagy arányok kiszámításához vagy bonyolult összesítésekhez használhatók. Egy mérték DAX-képlettel való létrehozásához válassza a **Modellezés** lap **Új mérték** gombját. Ezt is a legjobb a Power BI Desktop **Adat** nézetében megtenni, mert így látszik a **képletsáv**, és megkönnyíti a DAX-képlet beírását.

![](media/7-2-dax-calculation-types/dax-calc-types_4.png)

**Mérték** esetén egy mértékikon jelenik meg a **Mezők** panelen a mérték nevével. A **képletsáv** ilyenkor is kitöltődik a DAX-képlet (ezúttal a mérték) nevével.

![](media/7-2-dax-calculation-types/dax-calc-types_5.png)

A számított mérték kötelező elemei ugyanazok, mint a számított oszlopéi:

* új mértéknév
* legalább egy függvény vagy kifejezés

> A videótartalomért köszönet illeti [Alberto Ferrarit az SQLBI-tól](https://www.sqlbi.com/learning-dax)
> 
> 

