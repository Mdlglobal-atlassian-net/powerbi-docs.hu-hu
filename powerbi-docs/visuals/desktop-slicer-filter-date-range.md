---
title: Relatívdátum-szeletelő vagy -szűrő használata a Power BI-ban
description: Útmutató a relatív dátumtartományok szeletelővel vagy szűrővel végzett korlátozásához a Power BI-ban.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/05/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: f63a56ea350d089b82eb7a18470e1bcc439d1151
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/06/2020
ms.locfileid: "82866518"
---
# <a name="creating-a-relative-date-slicer-and-filter-in-power-bi"></a>Relatívdátum-szeletelő és -szűrő létrehozása a Power BI-ban

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

A **relatív dátumszeletelővel** vagy **relatív dátumszűrővel** időalapú szűrőket alkalmazhat az adatmodellek bármely dátumoszlopára. A **relatív dátumszeletelővel** például a megjelenítést az utóbbi 30 napban (vagy hónapban, naptári hónapban stb.) történt értékesítési eseményekre korlátozhatja. Az adatok frissítésekor a relatív időszak automatikusan alkalmazza a vonatkozó relatív dátumkorlátokat.

![Képernyőkép egy jelentésről, ahol a nyíl a relatív dátumszeletelőre mutat.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-01.png)

A jelentés egy Power BI-munkatárssal való megosztásához mindkettőjüknek Power BI Pro-licenccel kell rendelkezniük, vagy a jelentésnek egy Premium kapacitásban kell lennie.

## <a name="create-the-relative-date-range-slicer"></a>A relatív dátumtartomány-szeletelő létrehozása

A relatív dátumszeletelőt bármely más szeletelőhöz hasonlóan használhatja. Hozzon létre egy **szeletelő** vizualizációt a jelentéshez, majd válasszon ki egy dátumértéket a **Mező** értékeként. A következő képen az *OrderDate* mező van kiválasztva.

![Képernyőkép a Vizualizációk panelről, ahol a nyilak a szeletelő vizualizáció ikonjára és a Mező területre mutatnak.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-02.png)

Válassza ki a szeletelőt a vásznon, majd a lefelé mutató nyilat a szeletelő vizualizáció jobb felső sarkában. Ha a vizualizáció rendelkezik dátumadatokkal, a menüben megjelenik a **Relatív** beállítás.

![Képernyőkép a szeletelő vizualizációról, amelyen a lefelé mutató nyíl ki van emelve, és a nyíl a Relatív beállításra mutat.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-03.png)

A relatív dátumszeletelőnél válassza a *Relatív* lehetőséget.

Ezután válassza ki a beállításokat.

A *relatív dátumszeletelő* első beállításainál a következő lehetőségek közül választhat:

![Képernyőkép a Relatív konfigurálási beállításokról, amelyen az első beállítás van kiemelve.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-04.png)

* Utolsó

* Tovább

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

* ami a május 21-tól július 20-ig (a mai napig) tartó időszakot jelenti.

Összehasonlításképp, ha a *Hónapok (naptár)* elemet választotta volna, a vizualizációk a május 1-től június 30-ig tartó időszakra (az utolsó két teljes naptári hónapra) lennének korlátozva.

## <a name="create-the-relative-date-range-filter"></a>A relatív dátumtartomány-szűrő létrehozása

Relatív dátumtartomány-szűrőt is létrehozhat az egyes jelentésoldalakhoz vagy a teljes jelentéshez. Ehhez húzzon egy dátummezőt a **Lapszintű szűrők** vagy a **Jelentési szint szűrői** területre a **Mező** panelen:

![Képernyőkép a lapszintű szűrők területre húzott OrderDate mezőről.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-06.png)

Itt már módosíthatja a relatív dátumtartományt. Az eljárás a **relatív dátumszeletelő** testreszabásához hasonlít. Válassza a **Relatív dátum szerinti szűrés** lehetőséget a **Szűrő típusa** legördülő menüből.

![Képernyőkép a Szűrő típusa legördülő menüvel, amelyen az egérmutató a Relatív dátum szerinti szűrés beállításra mutat.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-07.png)

A **Relatív dátum szerinti szűrés** kiválasztása után itt is három beállítás módosítható, köztük a középső numerikus mező, ahogy a szeletelő esetében is.

![Képernyőkép a Jelentési szint szűrőiről, amelyen a nyilak az „Elemek megjelenítése, amikor az érték:” beállításra mutatnak.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-08.png)

## <a name="limitations-and-considerations"></a>Korlátozások és szempontok

A **relatív dátumtartomány-szeletelők** és -szűrők használatára jelenleg a következő korlátozások és szempontok vonatkoznak.

* A **Power BI** adatmodelljei nem tartalmaznak időzóna-információkat. A modellek tudják tárolni az időadatokat, de nem jelölik az időzónákat.

* A szeletelők és a szűrők minden esetben az UTC-időn alapulnak. Így ha beállít egy szűrőt egy jelentésben, majd elküldi azt egy másik időzónában tartózkodó munkatársának, mindketten ugyanazokat az adatokat fogják látni. Hacsak nem a UTC időzónában vannak, Önnek és a munkatársának figyelembe kell vennie az időeltolódást.

* A helyi időzónában rögzített adatok a **Lekérdezésszerkesztővel** alakíthatók át UTC-idővé.

## <a name="next-steps"></a>Következő lépések

- [Relatívdátum-szeletelő és -szűrő használata a Power BI-ban](desktop-slicer-filter-date-range.md)
- [Szeletelők a Power BI-ban](power-bi-visualization-slicers.md)
