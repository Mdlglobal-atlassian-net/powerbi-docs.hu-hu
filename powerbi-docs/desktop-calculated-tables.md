---
title: Számított táblázatok használata a Power BI Desktopban
description: Számított táblázatok a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: ffa49cc65c28e0fafb8ca72cb7a1a5bbde798861
ms.sourcegitcommit: 5e83fa6c93a0bc6599f76cc070fb0e5c1fce0082
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/13/2019
ms.locfileid: "56216332"
---
# <a name="using-calculated-tables-in-power-bi-desktop"></a>Számított táblázatok használata a Power BI Desktopban
A számított táblázatokkal új táblázatokat adhat a modellhez. De ahelyett, hogy értékeket kellene lekérdeznie és betöltenie egy adatforrásból az új táblázat oszlopaiba, létrehozhat egy Data Analysis Expressions- (DAX-) képletet, amely meghatározza a táblázat értékeit. A számított táblázatok a Power BI Desktopban az Új táblázat funkcióval hozhatók létre Jelentés nézetben vagy Adatnézetben.

A legtöbb esetben külső adatforrásból importál adatokat a modellbe. Azonban a számított táblázatok bizonyos előnyöket nyújtanak. A számított táblázatok általában köztes számításokhoz és olyan adatokhoz ideálisak, amelyeket a modell részeként kíván tárolni menet közbeni vagy lekérdezés részeként történő számítás helyett.

A lekérdezések részeként létrehozott táblázatokkal ellentétben a Jelentés nézetben vagy Adatnézetben létrehozott számított táblázatok a modellbe már betöltött adatokon alapulnak. Választhatja például két táblázat unióját vagy keresztillesztését.

A normál táblázatokhoz hasonlóan a számított táblázatoknak lehetnek kapcsolataik más táblázatokkal. A számított táblázatban lévő oszlopok rendelkezhetnek adattípusokkal és formázással, és tartozhatnak adatkategóriához. Tetszőleges nevet adhat az oszlopoknak, és hozzáadhatja őket egy jelentés vizualizációjához az egyéb mezőkhöz hasonlóan. A rendszer újraszámítja a számított táblázatokat, ha valamely olyan táblázat bármely módon frissül vagy módosul, amelyről adatokat kér le.

A számított táblázatok a [Data Analysis Expressions](https://msdn.microsoft.com/library/gg413422.aspx) (DAX) használatával számítják ki az eredményeket. Ez a képletnyelv olyan relációs adatok használatához készült, amilyeneket a Power BI Desktop is használ. A DAX több mint 200 függvényt, operátort és szerkezetet tartalmazó kódtárat tartalmaz, így rendkívüli rugalmasságot biztosít a képletek létrehozása során, amelyek szinte bármilyen adatelemzési igényhez képesek eredményeket számítani.

## <a name="lets-look-at-an-example"></a>Vegyünk egy példát.
Jeff, a Contoso egyik projektmenedzsere két táblázattal rendelkezik, az egyikben az északnyugati régió alkalmazottai szerepelnek, a másikban a délnyugati régió alkalmazottai. Jeff egyetlen táblázatba szeretné egyesíteni a két táblázatot.

**NorthwestEmployees**

 ![](media/desktop-calculated-tables/calctables_nwempl.png)

**SouthwestEmployees**

 ![](media/desktop-calculated-tables/calctables_swempl.png)

A két táblázat nagyon könnyen egyesíthető egy számított táblázattal. Bár Jeff a Jelentés nézetben és az Adatnézetben is létrehozhat számított táblázatot, ez az Adatnézetben könnyebb, mert ott azonnal láthatja az új számított táblázatot.

Az **Adatnézet** **Modellezés** lapján Jeff az **Új táblázat** lehetőségre kattint. Megjelenik egy képletsáv.

 ![](media/desktop-calculated-tables/calctables_formulabarempty.png)

Jeff ezután beírja a következő képletet:

 ![](media/desktop-calculated-tables/calctables_formulabarformula.png)

Létrejön egy új, Western Region Employees (Nyugati régió alkalmazottai) nevű táblázat.

 ![](media/desktop-calculated-tables/calctables_westregionempl.png)

Jeff új Western Region Employees nevű táblázata ugyanúgy jelenik meg, mint bármely más táblázat a Mezők listában. Kapcsolatokat hozhat létre más táblákkal, számított oszlopokat és mértékeket adhat hozzá, és a táblázat bármelyik mezőjét jelentésekhez adhatja, csakúgy, mint bármely más táblázat esetén.

 ![](media/desktop-calculated-tables/calctables_fieldlist.png)

## <a name="functions-for-calculated-tables"></a>Számított táblázatok függvényei
A számított táblázatok bármely, táblázatot visszaadó DAX-kifejezéssel meghatározhatók, beleértve a másik táblázatokra mutató egyszerű hivatkozásokat. Például:

 ![](media/desktop-calculated-tables/calctables_formulabarsimpleformula.png)

Számos elemzési probléma megoldásához használhatja a számított táblázatokat a DAX-szal. Itt csak röviden bemutattuk a számított táblázatokat. A számított táblázatok használatának megkezdéséhez íme néhány gyakori DAX-táblázatfüggvény, amely hasznos lehet:

* DISTINCT
* ÉRTÉKEK
* CROSSJOIN
* UNION
* NATURALINNERJOIN
* NATURALLEFTOUTERJOIN
* INTERSECT
* CALENDAR
* CALENDARAUTO

Tekintse meg a [DAX-függvények referencia-útmutatóját](https://msdn.microsoft.com/ee634396.aspx) ezekért és más, táblázatokat visszaadó DAX-függvényekért.

