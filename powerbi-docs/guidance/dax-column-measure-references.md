---
title: 'DAX: Oszlopok és mértékek hivatkozásai'
description: Útmutató oszlopokra való hivatkozáshoz DAX-kifejezésekben lévő mértékekben.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/18/2019
ms.author: v-pemyer
ms.openlocfilehash: 3ca49008639f7e3e084c8d045bc911aff57b7b21
ms.sourcegitcommit: 0da17de80c9651f9f4474d1abb1bdaaade8808fb
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/27/2019
ms.locfileid: "75498737"
---
# <a name="dax-column-and-measure-references"></a>DAX: Oszlopok és mértékek hivatkozásai

Adatmodellezőként készített DAX-kifejezései a modell oszlopaira és mértékeire hivatkoznak. Az oszlopok és mértékek mindig a modell tábláihoz vannak társítva, ám ezek a hozzárendelések különbözőek. Éppen ezért ajánlott másként hivatkozni rájuk a kifejezésekben.

## <a name="columns"></a>Oszlopok

Az oszlopok táblaszintű objektumok, és az oszlopneveknek a táblán belül kell egyedinek lenniük. Így lehetséges, hogy a modellben többször is ugyanazt az oszlopnevet használja, feltéve, hogy azok különböző táblákhoz tartoznak. Egy további szabály, hogy egy oszlop neve nem egyezhet meg egy olyan mérték vagy hierarchia nevével, amely ugyanabban a táblában van.

A DAX általában nem követeli meg, hogy _teljes nevén_ hivatkozzon egy oszlopra. A teljes néven való hivatkozás azt jelenti, hogy az oszlop neve elé a tábla neve is oda van írva.

Az alábbi példa egy számított oszlop csak oszlopnév-hivatkozásokat használó definícióját mutatja be. A **Sales** és a **Cost** oszlop is egy **Orders** nevű táblához tartozik.

```dax
Profit = [Sales] - [Cost]
```

Ugyanez a definíció teljes névvel megadott oszlophivatkozásokkal is átírható.

```dax
Profit = Orders[Sales] - Orders[Cost]
```

Bizonyos esetekben azonban kötelező teljes oszlopneveket használni a hivatkozásokhoz, ha a Power BI kétértelműséget észlel. Erre a képlet beírásakor piros hullámvonal és hibaüzenet figyelmeztet. Ezen kívül néhány DAX-függvény, például a [LOOKUPVALUE](/dax/lookupvalue-function-dax) is megköveteli a teljes oszlopnevek használatát.

Az oszlophivatkozásokat ajánlott mindig teljes névvel megadni. Ennek indokait az [Javaslatok](#recommendations) szakaszban adjuk meg.

## <a name="measures"></a>Mértékek

A mértékek modellszintű objektumok. Amiatt a mértékek nevének a modellen belül egyedinek kell lennie. A **Mezők** panelen viszont a jelentéskészítők az egytáblás modellekhez tartozó összes mértéket látják. Ez a hozzárendelés esztétikai okokból van beállítva, és a mérték **Kezdőtábla** tulajdonságának beállításával konfigurálható. További információ: [Mértékek a Power BI Desktopban (mértékek rendszerezése)](../desktop-measures.md#organizing-your-measures).

A kifejezésekben használható a mértékek teljes neve. A DAX IntelliSense fel is kínálja javaslatként. Ennek ellenére szükségtelen és nem ajánlott a használata. Egy mérték kezdőtáblájának módosításakor a mértékekre azok teljes nevével hivatkozó kifejezések hibássá válnak. Ilyen esetben minden hibás képletet szerkeszteni kell, hogy eltávolítsa (vagy frissítse) a mértékekre való hivatkozásokat.

Javasoljuk, hogy soha ne használjon teljes nevet a mértékekre való hivatkozásokban. Ennek indokait az [Javaslatok](#recommendations) szakaszban adjuk meg.

## <a name="recommendations"></a>Javaslatok

Javaslataink egyszerűek és könnyen megjegyezhetők:

- Mindig használjon teljes nevet az oszlopokra való hivatkozásokban
- Soha ne használjon teljes nevet a mértékekre való hivatkozásokban

Ennek indokai a következők:

- **Képletbevitel**: A képletek el lesznek fogadva, mert nem lesznek feloldandó többértelmű hivatkozások. Ezzel annak a DAX-függvényekre vonatkozó követelménynek is eleget tesz, amely a teljes nevet használó oszlophivatkozások használatát írja elő.
- **Robusztusság**: A kifejezések a mérték kezdőtáblájának helyes módosítása után is működni fognak.
- **Olvashatóság**: A kifejezések gyorsan és könnyen megérthetők – azonnal látható, hogy oszlopról vagy mértékről van szó az alapján, hogy a teljes neve van megadva vagy sem.

## <a name="next-steps"></a>Következő lépések

Erről a cikkről a következő forrásanyagokban talál további információt:

- [Data Analysis Expressions-referencia (DAX)](/dax/)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
