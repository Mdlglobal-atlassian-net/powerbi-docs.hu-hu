---
title: 'DAX: Ne konvertálja a BLANK-eket értékekre'
description: Útmutatás a BLANK-ek értékekre való konvertálásához.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/24/2019
ms.author: v-pemyer
ms.openlocfilehash: 2f70b98ed540a2e5b87e5a949e30b0c1c02069d1
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/04/2020
ms.locfileid: "74700386"
---
# <a name="dax-avoid-converting-blanks-to-values"></a>DAX: Ne konvertálja a BLANK-eket értékekre

Adatmodellezőként mértékkifejezések írásakor olyan esetekkel találkozhat, ahol nem kaphat értelmes értéket eredményül. Ezekben az esetekben kísértést érezhet arra, hogy inkább egy értéket adjon eredményül, például a nullát. Azt javasoljuk, jól gondolja át, hogy ez a kialakítás hatékony és praktikus-e.

Tekintse meg a következő mértékdefiníciót, amely explicit módon konvertál BLANK-eredményeket nullára.

```dax
Sales (No Blank) =
IF(
    ISBLANK([Sales]),
    0,
    [Sales]
)
```

Tekintse meg a másik mértékdefiníciót, amely szintén BLANK-eredményeket konvertál nullára.

```dax
Profit Margin =
DIVIDE([Profit], [Sales], 0)
```

A [DIVIDE](/dax/divide-function-dax) függvény a **Profit** mértéket osztja el a **Sales** (Értékesítés) mértékkel. Ha az eredmény nulla vagy BLANK, egy harmadik argumentumot – a nem kötelező alternatív eredményt – kap eredményül. Ebben a példában, mivel az alternatív eredmény a nulla, a mérték garantáltan mindig értéket ad vissza.

Ezek a mértékkialakítások nem hatékonyak, és rossz jelentéskialakításokhoz vezethetnek.

Ha egy jelentés vizualizációjához adja őket, a Power BI megkísérli lekérni a szűrőkontextus összes csoportosítását. A nagy mennyiségű lekérdezéseredmény kiértékelése és lekérése gyakran lassú jelentésrenderelést eredményez. Minden példamérték egy ritka számításból egy sűrűt készít, így arra késztetve a Power BI-t, hogy az a szükségesnél több memóriát használjon.

A túl sok csoportosítás emellett túlterhelheti a jelentésfelhasználókat.

Nézzük meg, mi történik, ha a **Profit Margin** (Fedezeti mutató) mértékét hozzáadjuk egy táblázatos vizualizációhoz, ügyfél szerinti csoportosítással.

![A táblázatos vizualizáció három oszlopot tartalmaz: Customer (Ügyfél), Sales (Értékesítés), és Profit Margin (Haszonkulcs). A táblázat körülbelül 10 sornyi adatot jelenít meg, a függőleges görgetősáv mégis jelzi, hogy sokkal több sor is megjeleníthető lenne. A Sales oszlopban semmilyen érték nem jelenik meg. A Profit Margin oszlop csak nulla értékeket jelenít meg.](media/dax-avoid-converting-blank/table-visual-poor.png)

A táblázatos vizualizáció túl sok sort tartalmaz. (A modellben valójában 18 484 ügyfél szerepel, így a táblázat megpróbálja mindet megjeleníteni.) Látható, hogy az nézetben szereplő ügyfelek nem végeztek értékesítést. Azonban mivel a **Profit margin** mérték mindig értéket ad vissza, mégis megjelennek.

> [!NOTE]
> Ha begy vizualizáció túl sok megjelenítendő adatpontot tartalmaz, a Power BI adatcsökkentési stratégiákkal próbálja meg eltávolítani vagy összesíteni a nagy mennyiségű lekérdezéseredményt. További információ: [Adatpontkorlátok és -stratégiák vizualizációtípus szerint](../visuals/power-bi-data-points.md).

Nézzük meg, mi történik, ha a továbbfejlesztjük a **Profit Margin** mérték definícióját. Így csak akkor eredményez értéket, ha a **Sales** mérték nem BLANK (vagy nulla).

```dax
Profit Margin =
DIVIDE([Profit], [Sales])
```

A táblázatos vizualizáció most azokat az ügyfeleket jeleníti meg, akik az aktuális szűrőkontextusban végeztek értékesítést. A továbbfejlesztett mérték hatékonyabb és praktikusabb jelentésfelhasználói élményt eredményez.

![Ugyanez a táblázatos vizualizáció most négy sornyi adatot jelenít meg. Minden sor egy olyan ügyfélhez tartozik, amely értékesítési értékkel rendelkezik, és a Profit Margin értéke nem nulla.](media/dax-avoid-converting-blank/table-visual-good.png)

> [!TIP]
> Szükség esetén konfigurálhatja a vizualizációt úgy, hogy a szűrő minden csoportosítását (amely értékeket vagy BLANK eredményt ad) megjelenítse. Ehhez engedélyeznie kell az [Adatot nem tartalmazó elemek megjelenítése](../desktop-show-items-no-data.md) beállítást.

## <a name="recommendation"></a>Javaslat

Azt javasoljuk, hogy a mértékek BLANK eredményt adjanak, ha nem eredményezhetnek értelmes értéket.

Ez a kialakítás hatékony, és így a Power BI is gyorsabban renderelheti a jelentéseket. A BLANK érték visszaadása emellett azért is jobb választás, mert a jelentésvizualizációk alapértelmezés szerint eltávolítják a csoportosításokat, ha az összegzések BLANK értékűek.

## <a name="next-steps"></a>Következő lépések

Erről a cikkről a következő forrásanyagokban talál további információt:

- [Data Analysis Expressions-referencia (DAX)](/dax/)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
