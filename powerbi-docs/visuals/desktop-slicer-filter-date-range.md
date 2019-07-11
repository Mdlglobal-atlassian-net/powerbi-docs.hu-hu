---
title: Relatív dátumszeletelő vagy -szűrő használata a Power BI Desktopban
description: Ismerje meg, hogyan használhat szeletelőket és szűrőket a relatív dátumtartományok korlátozására a Power BI Desktopban.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Create reports
ms.openlocfilehash: c039b00ced1bf62c8be72d218177d04a9fd3accf
ms.sourcegitcommit: e67bacbfc5638ee97e3d2e0e7f5bd2d9aac78f9c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67532751"
---
# <a name="use-a-relative-date-slicer-and-filter-in-power-bi-desktop"></a>Relatív dátumszeletelő és -szűrő használata a Power BI Desktopban

A **relatív dátumszeletelővel** vagy **relatív dátumszűrővel** időalapú szűrőket alkalmazhat az adatmodellek bármely dátumoszlopára. A **relatív dátumszeletelővel** például a megjelenítést az utóbbi 30 napban (vagy hónapban, naptári hónapban stb.) történt értékesítési eseményekre korlátozhatja. Az adatok frissítésekor a relatív időszak automatikusan alkalmazza a vonatkozó relatív dátumkorlátokat.

![Képernyőkép egy jelentésről, ahol a nyíl a relatív dátumszeletelőre mutat.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-01.png)

## <a name="use-the-relative-date-range-slicer"></a>A relatív dátumtartomány-szeletelő használata

A relatív dátumszeletelőt bármely más szeletelőhöz hasonlóan használhatja. Hozzon létre egy **szeletelő** vizualizációt a jelentéshez, majd válasszon ki egy dátumértéket a **Mező** értékeként. A következő képen az *OrderDate* mező van kiválasztva.

![Képernyőkép a Vizualizációk panelről, ahol a nyilak a szeletelő vizualizáció ikonjára és a Mező területre mutatnak.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-02.png)

Válassza ki a szeletelőt a vásznon, majd a lefelé mutató nyilat a szeletelő vizualizáció jobb felső sarkában. Ha a vizualizáció rendelkezik dátumadatokkal, a menüben megjelenik a **Relatív** beállítás.

![Képernyőkép a szeletelő vizualizációról, amelyen a lefelé mutató nyíl ki van emelve, és a nyíl a Relatív beállításra mutat.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-03.png)

A relatív dátumszeletelőnél válassza a *Relatív* lehetőséget.

Ezután válassza ki a beállításokat.

A *relatív dátumszeletelő* első beállításainál a következő lehetőségek közül választhat:

![Képernyőkép a Relatív konfigurálási beállításokról, amelyen az első beállítás van kiemelve.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-04.png)

* Utolsó

* Következő

* Ez a

A *relatív dátumszeletelő* második (középső) beállításában egy szám beírásával megadhatja a relatív dátumtartományt.

![Képernyőkép a Relatív konfigurálási beállításokról, amelyen a második beállítás van kiemelve.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-04a.png)

A harmadik beállításban kiválaszthatja a dátummértéket. A következők közül választhat:

![Képernyőkép a Relatív konfigurálási beállításokról, amelyen a harmadik beállítás van kiemelve.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-05.png)

* Napok

* Hetek

* Hetek (naptári)

* Hónapok

* Hónapok (naptári)

* Évek

* Évek (naptári)

Ha kiválasztja a **Hónapok** lehetőséget a listából, és megadja a *2* értéket a középső beállításban, a következő fog történni:

* ha ma július 20-a van,

* a szeletelő által korlátozott vizualizációk adatai az előző két hónapra korlátozva jelennek meg,

* ami a május 20-tól július 20-ig (a mai napig) tartó időszakot jelenti.

Összehasonlításképp, ha a *Hónapok (naptár)* elemet választotta volna, a vizualizációk a május 1-től június 30-ig tartó időszakra (az utolsó két teljes naptári hónapra) lennének korlátozva.

## <a name="using-the-relative-date-range-filter"></a>A relatív dátumtartomány-szűrő használata

Relatív dátumtartomány-szűrőt is létrehozhat az egyes jelentésoldalakhoz vagy a teljes jelentéshez. Ehhez húzzon egy dátummezőt a **Lapszintű szűrők** vagy a **Jelentési szint szűrői** területre a **Mező** panelen:

![Képernyőkép a lapszintű szűrők területre húzott OrderDate mezőről.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-06.png)

Itt már módosíthatja a relatív dátumtartományt. Az eljárás a **relatív dátumszeletelő** testreszabásához hasonlít. Válassza a **Relatív dátum szerinti szűrés** lehetőséget a **Szűrő típusa** legördülő menüből.

![Képernyőkép a Szűrő típusa legördülő menüvel, amelyen az egérmutató a Relatív dátum szerinti szűrés beállításra mutat.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-07.png)

A **Relatív dátum szerinti szűrés** kiválasztása után itt is három beállítás módosítható, köztük a középső numerikus mező, ahogy a szeletelő esetében is.

![Képernyőkép a Jelentési szint szűrőiről, amelyen a nyilak az „Elemek megjelenítése, amikor az érték:” beállításra mutatnak.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-08.png)

## <a name="limitations-and-considerations"></a>Korlátozások és szempontok

A **relatív dátumtartomány-szeletelők** és -szűrők használatára jelenleg a következő korlátozások és szempontok vonatkoznak.

* A **Power BI** adatmodelljei nem tartalmaznak időzóna-információkat. A modellek tudják tárolni az időadatokat, de nem jelölik az időzónákat.

* A szeletelők és a szűrők minden esetben az UTC-időn alapulnak. Így ha beállít egy szűrőt egy jelentésben, majd elküldi azt egy másik időzónában tartózkodó munkatársának, mindketten ugyanazokat az adatokat fogják látni. Hacsak nem az UTC időzónában vannak, Önnek és a munkatársának figyelembe kell vennie az időeltolódást.

* A helyi időzónában rögzített adatok a **Lekérdezésszerkesztővel** alakíthatók át UTC-idővé.

## <a name="next-steps"></a>Következő lépések

A következőkben megismerheti [a csoportosítás és dobozolás használatát a Power BI Desktopban](../desktop-grouping-and-binning.md).
