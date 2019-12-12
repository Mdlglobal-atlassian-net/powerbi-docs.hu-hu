---
title: 'DAX: Változók használata a képletek tökéletesítéséhez'
description: Ez a cikk a DAX-kifejezésekben használható változókkal kapcsolatban nyújt útmutatást.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/23/2019
ms.author: v-pemyer
ms.openlocfilehash: f352cbbd7c42aa54ae876e73c0ed821eccda59c8
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/02/2019
ms.locfileid: "74700708"
---
# <a name="dax-use-variables-to-improve-your-formulas"></a>DAX: Változók használata a képletek tökéletesítéséhez

A DAX-számítások írása és hibakeresése kihívást jelenthet az adatmodellezők számára. Az összetett számítások esetén gyakran összetett vagy bonyolult kifejezések írására van szükség. Az összetett kifejezések több beágyazott függvény használatát igényelhetik, és sok esetben a kifejezés logikájának ismételt felhasználása is szükséges.

A változók megkönnyítik és hatékonyabbá teszik az összetett DAX-képletek írását. A változókkal:

- [javíthatja a teljesítményt](#improve-performance)
- [javíthatja az olvashatóságot](#improve-readability)
- [leegyszerűsítheti a hibakeresést](#simplify-debugging)
- [csökkentheti az összetettséget](#reduce-complexity)

Ebben a cikkben az első három előnyt fogjuk demonstrálni egy évenkénti értékesítési növekedésre vonatkozó mérték példáján keresztül. (Az évenkénti értékesítési növekedés képlete: az adott időszakban teljesített értékesítések száma _mínusz az egy évvel korábban ugyanabban az időszakban teljesített értékesítések száma, _osztva_ az egy évvel korábban ugyanabban az időszakban teljesített értékesítések számával.)

Kezdjük a következő mérték definíciójával:

```dax
Sales YoY Growth % =
DIVIDE(
    ([Sales] - CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))),
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
)
```

A mérték helyes eredményt ad, de nézzük meg, hogy hogyan lehetne javítani rajta.

## <a name="improve-performance"></a>A teljesítmény javítása

Figyelje meg, hogy a képletben ismétlődik az „ugyanaz az időszak a múlt évben” kiszámítására szolgáló kifejezés. Ez a képlet nem hatékony, mivel a Power BI-nak kétszer kell kiértékelnie ugyanazt a kifejezést. Egy változó használatával hatékonyabbá teheti a mérték definícióját.

A következő mértékdefiníció már tartalmazza a javítást. A definícióban az „ugyanaz az időszak a múlt évben” műveletet egy kifejezéssel a **SalesPriorYear** változóhoz rendeltük. Ezt a változót kétszer is felhasználtuk a RETURN kifejezésben.

```dax
Sales YoY Growth % =
VAR SalesPriorYear =
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
RETURN
    DIVIDE(([Sales] - SalesPriorYear), SalesPriorYear)
```

A mérték továbbra is a helyes eredményt adja, de a lekérdezési idő körülbelül a felére csökkent.

## <a name="improve-readability"></a>Az olvashatóság javítása

Figyelje meg, hogy a RETURN kifejezés átláthatóbbá vált az előző mértékdefinícióban használt változónévnek köszönhetően. A kifejezés rövidebb lett, és lényege első pillantásra megérthető.

## <a name="simplify-debugging"></a>A hibakeresés egyszerűsítése

A változók a képletek hibakeresésében is segíthetnek. A változóhoz rendelt kifejezés teszteléséhez írja át ideiglenesen úgy a RETURN kifejezést, hogy a változót adja vissza.

Az alábbi mértékdefiníció kizárólag a **SalesPriorYear** változót adja vissza. Láthatja, hogy a kívánt RETURN kifejezés most megjegyzés formájában jelenik meg. Ez a módszer lehetővé teszi, hogy a hibakeresés befejezése után visszaállítsa az eredeti formába a kifejezést.

```dax
Sales YoY Growth % =
VAR SalesPriorYear =
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
RETURN
    --DIVIDE(([Sales] - SalesPriorYear), SalesPriorYear)
    SalesPriorYear
```

## <a name="reduce-complexity"></a>Az összetettség csökkentése

A DAX korábbi verziói nem támogatták a változókat. Az új szűrőtartalmakat bevezető, összetett kifejezéseknél az [EARLIER](/dax/earlier-function-dax) vagy az [EARLIEST](/dax/earliest-function-dax) DAX-függvényeket kellett használni a külső szűrőkontextusokra való hivatkozáshoz. Sajnos az adatmodellezők általában nehezen érthetőnek és nehezen használhatónak találták ezeket a függvényeket.

A változókat mindig a RETURN kifejezés által alkalmazott szűrőkön kívül kell kiértékelni. Ezért ha egy módosított szűrőkontextuson belül használja a változót, ugyanazt az eredményt fogja elérni, mint az EARLIEST függvénnyel. Ezért az EARLIER és az EARLIEST függvényekre mostantól nincs szükség. Ez azt jelenti, hogy mostantól egyszerűbb, átláthatóbb függvényeket írhat.

Nézze meg az alábbi számítottoszlop-definíciót, amelyet hozzáadtunk a **Subcategory** táblához. A definíció a **Subcategory Sales** oszlopban szereplő értékek alapján rangot rendel az egyes termékalkategóriákhoz.

```dax
Subcategory Sales Rank =
COUNTROWS(
    FILTER(
        Subcategory,
        EARLIER(Subcategory[Subcategory Sales]) < Subcategory[Subcategory Sales]
    )
) + 1
```

Az EARLIER függvénnyel hivatkozunk a **Subcategory Sales** oszlop értékére _az aktuális sor kontextusában_.

A számítottoszlop-definíciót hatékonyabbá tehetjük, ha az EARLIER függvény helyett egy változót használunk. A **CurrentSubcategorySales** változó tárolja a **Subcategory Sales** oszlop értékét _az aktuális sor kontextusában_, és a RETURN kifejezés ezt használja a módosított szűrőkontextusban.

```dax
Subcategory Sales Rank =
VAR CurrentSubcategorySales = Subcategory[Subcategory Sales]
RETURN
    COUNTROWS(
        FILTER(
            Subcategory,
            CurrentSubcategorySales < Subcategory[Subcategory Sales]
        )
    ) + 1
```

## <a name="next-steps"></a>Következő lépések

Erről a cikkről a következő forrásanyagokban talál további információt:

- DAX-cikk a [VAR](/dax/var-dax) kifejezésről
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
