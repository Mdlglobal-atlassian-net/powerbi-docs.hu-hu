---
title: 'DAX: A COUNTROWS használata a COUNT helyett'
description: Útmutató a COUNTROWS függvények használatához.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/23/2019
ms.author: v-pemyer
ms.openlocfilehash: fd3b50e9016298db8b692d6a2f3549b770f143e8
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/02/2019
ms.locfileid: "74700662"
---
# <a name="dax-use-countrows-instead-of-count"></a>DAX: A COUNTROWS használata a COUNT helyett

Adatmodellezőként néha szüksége lehet olyan DAX-kifejezés írására, amely megszámlálja a táblasorokat. A tábla lehet egy modelltábla vagy egy táblát visszaadó kifejezés.

A követelmény két módon is megvalósítható. Az oszlopok értékeinek számlálásához használhatja a [COUNT](/dax/count-function-dax) függvényt, vagy használhatja a [COUNTROWS](/dax/countrows-function-dax) függvényt a tábla sorainak számlálásához. Mindkét függvény ugyanazt az eredményt fogja visszaadni, feltéve, hogy a számított oszlop nem tartalmaz ÜRES értékeket.

A következő mértékdefiníció bemutat egy példát. Kiszámítja az **OrderDate** oszlop számának értékeit.

```dax
Sales Orders =
COUNT(Sales[OrderDate])
```

Feltéve, hogy a **Sales** (Értékesítések) tábla részletessége értékesítési megrendelésenként egy sor, és az **OrderDate** oszlop nem tartalmaz ÜRES értékeket, a mérték a helyes eredményt adja vissza.

A következő mértékdefiníció azonban jobb megoldás.

```dax
Sales Orders =
COUNTROWS(Sales)
```

Három oka van, amiért a második mértékdefiníció jobb megoldás:

- Hatékonyabb, így jobb teljesítményt nyújt.
- Nem vesz figyelembe a tábla egyetlen oszlopában található ÜRES értékeket sem.
- A képlet célja világosabb, olyannyira, hogy már önmagát magyarázza.

## <a name="recommendation"></a>Javaslat

Ha a célja a tábla sorainak megszámlálása, javasoljuk, hogy mindig a COUNTROWS függvényt használja.

## <a name="next-steps"></a>Következő lépések

Erről a cikkről a következő forrásanyagokban talál további információt:

- [Data Analysis Expressions-referencia (DAX)](/dax/)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
