---
title: Számított táblázatok használata a Power BI Desktopban
description: Számított táblák a Power BI Desktopban
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/02/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: c72387d40ddf4b193481a37dbcb40695668eab66
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "75837345"
---
# <a name="create-calculated-tables-in-power-bi-desktop"></a>Számított táblák létrehozása a Power BI Desktopban
A legtöbb esetben külső adatforrásból importál adatokat a modellbe, és így hoz létre táblákat. A *számított táblákkal* azonban új táblákat vehet fel a modellbe már betöltött adatok alapján. Ahelyett, hogy értékeket kellene lekérdeznie és betöltenie egy adatforrásból az új táblázat oszlopaiba, létrehozhat egy [Data Analysis Expressions- (DAX-)](/dax/index) képletet, amely meghatározza a táblázat értékeit.

A DAX egy relációs adatokhoz (például a Power BI Desktopban) használható képletnyelv. A DAX több mint 200 függvényt, operátort és szerkezetet tartalmazó kódtárat tartalmaz, így rendkívüli rugalmasságot biztosít a képletek létrehozása során, amelyek szinte bármilyen adatelemzési igényhez képesek eredményeket számítani. A számított táblázatok köztes számításokhoz és olyan adatokhoz ideálisak, amelyeket a modell részeként kíván tárolni menet közbeni vagy lekérdezés eredményeként történő számítás helyett. Választhatja például két meglévő táblázat *unióját* vagy *keresztillesztését*.

A Power BI Desktop további táblázataihoz hasonlóan a számított táblázatoknak lehetnek kapcsolataik más táblázatokkal. A számított táblázatban lévő oszlopok rendelkezhetnek adattípusokkal és formázással, és tartozhatnak adatkategóriához. Tetszőleges nevet adhat az oszlopoknak, és hozzáadhatja őket egy jelentés vizualizációjához az egyéb mezőkhöz hasonlóan. A rendszer újraszámítja a számított táblákat, ha frissítik vagy módosítják azon táblák valamelyikét, amelyből adatokat kér le.

## <a name="create-a-calculated-table"></a>Számított táblázat létrehozása

A számított táblázatok a Power BI Desktopban az **Új tábla** funkcióval hozhatók létre jelentésnézetben vagy adatnézetben.

Tegyük fel például, hogy Ön egy olyan személyzeti vezető, aki egy **Northwest Employees** (Északnyugati alkalmazottak) és egy **Southwest Employees** (Délnyugati alkalmazottak) nevű táblázattal rendelkezik. Ezeket egy táblában szeretné egyesíteni: **Western region Employees** (Nyugati alkalmazottak).

**Northwest Employees**

 ![](media/desktop-calculated-tables/calctables_nwempl.png)

**Southwest Employees**

 ![](media/desktop-calculated-tables/calctables_swempl.png)

A Power BI Desktop jelentésnézetében vagy adatnézetében, a **Modellezés** lap **Számítások** csoportjában válassza az **Új tábla**elemet. Ez egy kicsit könnyebben elvégezhető az adatnézetben, mert ezután azonnal megtekintheti az új számított táblázatot.

 ![Új tábla az adatnézetben](media/desktop-calculated-tables/calctables_formulabarempty.png)

A szerkesztőlécen adja meg a következő képletet:

```dax
Western Region Employees = UNION('Northwest Employees', 'Southwest Employees')
```

Létrejön egy **Western Region Employees** nevű táblázat, amely ugyanúgy jelenik meg, mint bármely más táblázat a **Mezők** panelen. Kapcsolatokat hozhat létre más táblákkal, számított oszlopokat és mértékeket adhat hozzá, és a mezőket jelentésekhez adhatja, csakúgy, mint bármely más táblázat esetén.

 ![Új számított táblázat](media/desktop-calculated-tables/calctables_westregionempl.png)

 ![Új tábla a Mezők panelen](media/desktop-calculated-tables/calctables_fieldlist.png)

## <a name="functions-for-calculated-tables"></a>Számított táblázatok függvényei

A számított táblázatok bármely, táblázatot visszaadó DAX-kifejezéssel meghatározhatók, beleértve a másik táblázatokra mutató egyszerű hivatkozásokat. Példa:

```dax
New Western Region Employees = 'Western Region Employees'
```

Itt csak röviden bemutattuk a számított táblázatokat. Számos elemzési probléma megoldásához használhatja a számított táblázatokat a DAX-szal. Íme néhány, táblázatokhoz gyakran használt DAX-függvény:

* DISTINCT
* VALUES
* CROSSJOIN
* UNION
* NATURALINNERJOIN
* NATURALLEFTOUTERJOIN
* INTERSECT
* CALENDAR
* CALENDARAUTO

Tekintse meg a [DAX-függvények referencia-útmutatóját](/dax/dax-function-reference) ezekért és más, táblázatokat visszaadó DAX-függvényekért.

