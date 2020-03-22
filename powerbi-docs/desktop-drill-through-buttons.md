---
title: Részletezési gomb létrehozása a Power BI-ban
description: A Power BI-jelentésekhez részletezési gombokat adhat, amelyek az alkalmazásokéhoz hasonlóvá teszik a jelentés működését, és mélyebb interakciót kínálnak a felhasználókkal.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/12/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: d3cb3c8093446d4417a59c5f64ab6b85a765e3c8
ms.sourcegitcommit: 7e845812874b3347bcf87ca642c66bed298b244a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79206447"
---
# <a name="create-a-drill-through-button-in-power-bi-preview"></a>Részletezési gomb létrehozása a Power BI-ban (előzetes verzió)

Amikor a Power BI-ban hoz létre egy gombot, kiválaszthatja a **Részletezés (előzetes verzió)** műveletet. Ez a művelettípus egy olyan gombot hoz létre, amely egy fókuszba helyezett oldalt részletez, egy adott kontextus szerint szűrt adatokhoz.

A részletezési gomb akkor lehet hasznos, ha szeretné könnyebben megismerhetővé tenni a jelentések fontos részletezési forgatókönyveit.

Ebben a példában miután a felhasználó kiválasztja a Word sávot a diagramon, megjelenik a **Részletek** gomb.

![Részletek gomb](media/desktop-drill-through-buttons/power-bi-drill-through-visual-button.png)

Amikor kiválasztja a **Részletek** gombot, részletezést végez a Market Basket Analysis oldalon. Ahogyan a bal oldali vizualizáción látszik, a részletezési oldal már a Wordre van szűrve.

![Szűrt vizualizáció](media/desktop-drill-through-buttons/power-bi-drill-through-destination.png)

## <a name="set-up-a-drill-through-button"></a>Részletezési gomb beállítása

A részletezési gomb beállításához először [kell beállítania egy érvényes részletezési oldalt](desktop-drillthrough.md) a jelentésen belül. Ezután létre kell hoznia egy **részletezés** művelettípussal rendelkező gombot, és a részletezési oldalt kell megadnia **célként**.

Mivel a részletezési gomb két állapottal rendelkezik (engedélyezve és letiltva), két elemleírási lehetőséget láthat.

![A részletezési gomb beállítása](media/desktop-drill-through-buttons/power-bi-create-drill-through-button.png)

Ha üresen hagyja az elemleírások mezőit, a Power BI automatikusan létrehozza az elemleírásokat. Ezek az elemleírások a cél és a részletezés mezőin alapulnak.

Íme egy példa az automatikusan létrehozott elemleírásra, amikor a gomb le van tiltva:

„A Market Basket Analysis (céloldal) részletezéséhez válasszon ki egy adatpontit a Product (Termék) részletezési mezőben.”

![Letiltott, automatikusan létrehozott elemleírás](media/desktop-drill-through-buttons/power-bi-drill-through-tooltip-disabled.png)

És íme egy példa az automatikusan létrehozott elemleírásra, amikor a gomb engedélyezve van:

„Kattintson ide a Market Basket Analysis (céloldal) részletezéséhez.”

![Bekapcsolt, automatikusan létrehozott elemleírás](media/desktop-drill-through-buttons/power-bi-drill-through-visual-button.png)

Ha azonban egyéni elemleírásokat szeretne megadni, bármikor használhat statikus sztringet. Az elemleírások feltételes formázása még nem támogatott.

A feltételes formázással módosíthatja a gomb szövegét egy mező kiválasztott értéke alapján. Ehhez létre kell hoznia egy mértéket, amely a SELECTEDVALUE DAX-függvény alapján a kívánt sztringet eredményezi.

Íme egy példamérték, amely a „Termékadatok megtekintése” kifejezést eredményezi, ha NINCS kijelölve egy termékérték sem. Ellenkező esetben a „[Kijelölt termék] adatainak megtekintése” kifejezést eredményezi:

```
String_for_button = If(SELECTEDVALUE('Product'[Product], 0) == 0), "See product details", "See details for " & SELECTEDVALUE('Product'[Product]))
```

Miután létrehozta ezt a mértéket, válassza a **Feltételes formázás** lehetőséget a gomb szövegéhez:

![A Feltételes formázás elem kiválasztása](media/desktop-drill-through-buttons/power-bi-button-conditional-tooltip.png)

Ezután válassza ki a gomb szövegéhez létrehozott mértéket:

![Érték mező alapján](media/desktop-drill-through-buttons/power-bi-conditional-measure.png)

Ha egyetlen termék van kiválasztva, a gomb szövege a következő:

„Word-adatok megtekintése”

![Egyetlen érték kiválasztásakor](media/desktop-drill-through-buttons/power-bi-conditional-button-text.png)

Ha nincs kiválasztva termék, vagy több termék van kiválasztva, a gomb le vab tiltva, a szövege pedig a következő:

„Termékadatok megtekintése”

![Több érték kiválasztásakor](media/desktop-drill-through-buttons/power-bi-button-conditional-text-2.png)

## <a name="pass-filter-context"></a>Szűrőkörnyezet megadása

A gomb ugyanúgy működik, mint a normál részletezés, így Ön további mezőkhöz adhat meg szűrőket a részletezési mezőt tartalmazó vizualizációk keresztszűrésével. Ha például a **Ctrl** + **kattintás** és keresztszűrés műveletet használja, több szűrőt megadhat a Store-ban az oldal részletezéséhez, mivel a kijelölések keretszűrést végeznek a terméket tartalmazó vizualizáción, a részletezési mezőn:

![Szűrőkörnyezet megadása](media/desktop-drill-through-buttons/power-bi-cross-filter-drill-through-button.png)

A részletezési gomb kiválasztásakor a Store és a Termék szűrői is a céloldalhoz kerülnek:

![Szűrők ezen az oldalon](media/desktop-drill-through-buttons/power-bi-button-filters-passed-through.png)

### <a name="ambiguous-filter-context"></a>Kétértelmű szűrőkörnyezet

Mivel a részletezési gomb nincs egyetlen vizualizációhoz kötve, ha a kijelölés nem egyértelmű, akkor a gomb le lesz tiltva.

Ebben a példában a gomb le van tiltva, mert két vizualizáció egyaránt tartalmaz egyetlen kijelölést a Terméken. Nem egyértelmű, hogy melyik vizualizáció melyik adatpontjához kell kötni a részletezési műveletet:

![Kétértelmű szűrőkörnyezet](media/desktop-drill-through-buttons/power-bi-button-disabled-ambiguity.png)

## <a name="limitations"></a>Korlátozások

- Ezzel a gombbal nem használható több cél egyetlen gombbal.
- Ez a gomb csak az ugyanazon jelentésen belüli részletezéseket támogatja, azaz nem támogatja a több jelentésre kiterjedő részletezést.
- A gomb letiltott állapotának formázása a jelentés témájának színosztályaihoz van kötve. További információ a [színosztályokról](desktop-report-themes.md#setting-structural-colors).
- A részletezési művelet az összes beépített vizualizációval használható, és *néhány*, az AppSource-ból importált vizualizációval is működik. Azonban nem biztos, hogy az AppSource-ból importált *összes* vizualizációval használható.

## <a name="next-steps"></a>Következő lépések
A gombokhoz hasonló vagy azokkal együtt használható funkciókkal kapcsolatos részletesebb információkat az alábbi cikkekben talál:

* [Gombok létrehozása](desktop-buttons.md)
* [Részletezés használata Power BI-jelentésekben](desktop-drillthrough.md)
* [Elemzések megosztása és történetek felépítése a Power BI könyvjelzőivel](desktop-bookmarks.md)

