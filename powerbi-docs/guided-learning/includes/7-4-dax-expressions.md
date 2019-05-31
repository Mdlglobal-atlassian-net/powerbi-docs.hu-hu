---
ms.openlocfilehash: 5c2b254f20bd1eba97840a464a1b554cc4fe1238
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61273378"
---
A **változók** a DAX-kifejezések rendkívül hatékonyan használható részei.

![](media/7-4-dax-expressions/dax-variables_1.png)

A DAX-kifejezésen belül bárhol definiálhat változót a következő szintaxis segítségével:

    VARNAME = RETURNEDVALUE

Bármilyen adattípus lehet változó, akár teljes táblázatok is.

Ne feledje, hogy valahányszor változóra hivatkozik a DAX-kifejezésen belül, a Power BI-nak a megadott definíció szerint újra kell számítania az értéket. Emiatt tanácsos kerülni a változók ismétlését a függvényben.

> A videótartalomért köszönet illeti [Alberto Ferrarit az SQLBI-tól](http://www.sqlbi.com/learning-dax)
> 
> 

