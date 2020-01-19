---
title: 'DAX: Ne használja a FILTER-t szűrő argumentumaként'
description: Útmutató a FILTER függvény szűrési argumentumként való használatához.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/30/2019
ms.author: v-pemyer
ms.openlocfilehash: 935b453dabeaa731a218175526ddddeb980a2b92
ms.sourcegitcommit: b09de56e971b8844a3771413d1f56d49b31baaaf
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/07/2020
ms.locfileid: "75692459"
---
# <a name="dax-avoid-using-filter-as-a-filter-argument"></a>DAX: Ne használja a FILTER-t szűrő argumentumaként

Adatmodellezőként gyakran írhat olyan DAX-kifejezéseket, amelyeket egy módosított szűrőkontextusban kell kiértékelni. Írhat például egy olyan mértékdefiníciót, amely kiszámítja a magas árrésű termékek értékesítését. Ezt a számítást a cikk későbbi részében ismertetjük.

> [!NOTE]
> Ez a cikk különösen hasznos olyan számításokhoz, amelyek szűrők alkalmazásával importálnak táblázatokat.

A [CALCULATE](/dax/calculate-function-dax) és a [CALCULATETABLE](/dax/calculatetable-function-dax) DAX-függvények fontos és hasznos függvények. Ezekkel olyan számításokat írhat, amelyek szűrőket távolítanak el vagy adnak hozzá, vagy kapcsolati útvonalakat módosítanak. Ehhez szűrőargumentumokat ad meg, amelyek lehetnek logikai kifejezések, táblázatos kifejezések vagy speciális szűrőfüggvények. Ebben a cikkben csak a logikai és a táblázatos kifejezésekkel foglalkozunk.

Vegyük például az alábbi mértékdefiníciót, amely vörös termékek értékesítését számítja ki egy táblázatos kifejezéssel. Ez a **Product** (Termék) táblára alkalmazott összes szűrőt lecseréli.

```dax
Red Sales =
CALCULATE(
    [Sales],
    FILTER('Product', 'Product'[Color] = "Red")
)
```

A CALCULATE függvény elfogadja a [FILTER](/dax/filter-function-dax) DAX-függvény által visszaadott táblázatos kifejezést, amely a **Product** tábla minden sorának szűrőkifejezését kiértékeli. Ez kiadja a helyes eredményt – a vörös termékek értékesítési eredményét. Azonban ez sokkal hatékonyabban is elérhető egy logikai kifejezéssel.

Itt egy továbbfejlesztett mértékdefiníciót láthat, amely táblázatos helyett logikai kifejezést használ.

```dax
Red Sales =
CALCULATE(
    [Sales],
    'Product'[Color] = "Red"
)
```

Azt javasoljuk, hogy a szűrőargumentumokat logikai kifejezésként adja meg, amikor csak lehetséges. Ez azért van, mert a Modell importálása táblák memórián belüli oszloptárak. Kifejezetten oszlopok hatékony szűrésére vannak optimalizálva.

A szűrési argumentumként használt logikai függvényekre azonban bizonyos korlátozások vonatkoznak. Ezek:

- Nem hasonlíthatnak össze oszlopokat más oszlopokkal
- Nem hivatkozhatnak mértékre
- Nem használhatnak beágyazott CALCULATE függvényeket
- Nem használhatnak táblázatot vizsgáló vagy eredményező függvényeket

Összetettebb szűrési követelményekhez tehát táblázatos kifejezéseket kell használnia.

Vegyünk egy másik mértékdefiníciót.

```dax
High Margin Product Sales =
CALCULATE(
    [Sales],
    FILTER(
        'Product',
        'Product'[ListPrice] > 'Product'[StandardCost] * 2
    )
)
```

A _magas árrésű termék_ definíciója az olyan termék, amelynek listaára meghaladja a szabványos ár kétszeresét. Ebben a példában a FILTER függvényt kell használni. Ez azért van, mert a szűrési kifejezés túl összetett logikai kifejezéshez.

Íme még egy példa. A követelmény ezúttal az értékesítés kiszámítása, azonban csak a profitot termelő hónapokra.

```dax
Sales for Profitable Months =
CALCULATE(
    [Sales],
    FILTER(
        VALUES('Date'[Month]),
        [Profit] > 0)
    )
)
```

Ebben a példában is a FILTER függvényt kell használni. Ennek oka az, hogy a **profit** mértékének kiértékelésére van szükség a profitot nem termelő hónapok kizárásához. Mérték nem használható logikai kifejezésben, ha szűrési argumentumként is szolgál.

## <a name="recommendations"></a>Javaslatok

A legjobb teljesítmény érdekében azt javasoljuk, hogy logikai kifejezéseket használjon szűrési argumentumként, amikor csak lehetséges.

A FILTER függvényt tehát csak akkor használja, ha szükséges. Segítségével összetett oszlop-összehasonlításokat szűrhet. Ezek az oszlop-összehasonlítások a következőket foglalhatják magukban:

- Mértékek
- További oszlopok
- Az [OR](/dax/or-function-dax) DAX-függvény vagy az OR logikai operátor (||) használata

## <a name="next-steps"></a>Következő lépések

Erről a cikkről a következő forrásanyagokban talál további információt:

- [Data Analysis Expressions-referencia (DAX)](/dax/)
- [Szűrőfüggvények (DAX)](/dax/filter-function-dax)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
