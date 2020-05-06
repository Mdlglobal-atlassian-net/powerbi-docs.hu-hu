---
ms.openlocfilehash: f22c12ec0ad5bd413f3658704132143c878df1aa
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "73799905"
---
A **változók** a DAX-kifejezések rendkívül hatékonyan használható részei.

![](media/7-4-dax-expressions/dax-variables_1.png)

A DAX-kifejezésen belül bárhol definiálhat változót a következő szintaxis segítségével:

    VARNAME = RETURNEDVALUE

Bármilyen adattípus lehet változó, akár teljes táblázatok is.

Ne feledje, hogy valahányszor változóra hivatkozik a DAX-kifejezésen belül, a Power BI-nak a megadott definíció szerint újra kell számítania az értéket. Emiatt tanácsos kerülni a változók ismétlését a függvényben.

> A videótartalomért köszönet illeti [Alberto Ferrarit az SQLBI-tól](https://www.sqlbi.com/learning-dax)
> 
> 

