---
title: Egyéni oszlop hozzáadása a Power BI Desktopban
description: Új egyéni oszlop gyors létrehozása a Power BI Desktopban
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/18/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 443053bc973005d3e2a655b1222d049a4251e7d7
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73878880"
---
# <a name="add-a-custom-column-in-power-bi-desktop"></a>Egyéni oszlop hozzáadása a Power BI Desktopban

A Power BI Desktop Lekérdezésszerkesztőjével egyszerűen adhat hozzá új egyéni adatoszlopokat a modellekhez. A Lekérdezésszerkesztővel hozhat létre és nevezhet át egyéni oszlopot az egyéni oszlopot definiáló, [M-képleteket használó PowerQuery-lekérdezések](https://docs.microsoft.com/powerquery-m/quick-tour-of-the-power-query-m-formula-language) létrehozásához. Az M-képleteket használó PowerQuery-lekérdezések [átfogó függvényreferencia-tartalomkészlettel](https://docs.microsoft.com/powerquery-m/power-query-m-function-reference) rendelkeznek. 

Amikor egyéni oszlopot hoz létre a Lekérdezésszerkesztőben, a Power BI Desktop ezt **Alkalmazott lépésként** vesz fel a **Lekérdezés beállításaiban**. Ez bármikor megváltoztatható, áthelyezhető és módosítható.

![Egyéni oszlop hozzáadása oldal](media/desktop-add-custom-column/add-custom-column_01.png)

## <a name="use-query-editor-to-add-a-custom-column"></a>Egyéni oszlop hozzáadása a Lekérdezésszerkesztő használatával

Egy egyéni oszlop létrehozásának első lépései a következők:

1. Indítsa el a Power BI Desktopot, és töltsön be adatokat.

2. A menüszalag **Kezdőlapján** válassza a **Lekérdezések szerkesztése** lehetőséget, majd a **Lekérdezések szerkesztése** menüpontot.

   ![A Lekérdezések szerkesztése lehetőség kiválasztása](media/desktop-add-custom-column/add-column-from-example_02.png)

   Megnyílik a **Lekérdezésszerkesztő** ablaka. 

2. A menüszalag **Oszlop hozzáadása** lapján válassza az **Egyéni oszlop** lehetőséget.

   ![Az Egyéni oszlop lehetőség kiválasztása](media/desktop-add-custom-column/add-custom-column_02.png)

   Megnyílik az **Egyéni oszlop hozzáadása** ablak.

## <a name="the-add-custom-column-window"></a>Az Egyéni oszlop hozzáadása ablak

Az **Egyéni oszlop hozzáadása** ablak funkciói a következők: 
- Tartalmazza az elérhető oszlopok listáját a jobb oldali **Elérhető oszlopok:** listában.

- Az egyéni oszlop kezdeti neve az **Új oszlop neve** mezőben látható. Az oszlop nevét megváltoztathatja.

- [M-képletet használó PowerQuery-lekérdezések](https://docs.microsoft.com/powerquery-m/power-query-m-function-reference) az **Egyéni oszlop képlete** mezőben. Ezeket a lekérdezéseket annak a képletnek a megírásával hozza létre, amellyel az új oszlopot definiálja. 

   ![Egyéni oszlop hozzáadása oldal](media/desktop-add-custom-column/add-custom-column_03.png)

## <a name="create-formulas-for-your-custom-column"></a>Képletek létrehozása az egyéni oszlopokhoz

1. Jelöljön ki egy oszlopot a jobb oldali **Elérhető oszlopok:** listában. Ezt a lista alatti **Beszúrás** gombbal szúrhatja be az egyéni oszlop képletébe. Oszlopot úgy is beszúrhat, hogy duplán kattint rá a listában.

2. A képlet bevitele és az oszlop elkészítése során tartsa szemmel az **Egyéni oszlop hozzáadása** ablak alján lévő kijelzőt. 

   Ha nincs hiba, akkor itt egy zöld pipa és a *Nem észlelhető szintaktikai hiba* üzenet látható.

   ![Sikeres szintaktikai ellenőrzés az Egyéni oszlop hozzáadása oldalon](media/desktop-add-custom-column/add-custom-column_04.png)

   Szintaktikai hiba esetén sárga figyelmeztető ikon jelenik meg a hiba képletbeli helyére mutató hivatkozással.

   ![Hiba az Egyéni oszlop hozzáadása oldalon](media/desktop-add-custom-column/add-custom-column_05.png)

3. Kattintson az **OK** gombra. 

   A Power BI Desktop felveszi az egyéni oszlopot a modellbe, és a **Lekérdezés beállításaiban** felveszi az **Egyéni hozzáadva** lépést az **Alkalmazott lépések** listájára.

   ![Egyéni oszlop hozzáadása a Lekérdezés beállításaiban](media/desktop-add-custom-column/add-custom-column_06.png)

4. Az egyéni oszlop módosításához kattintson duplán az **Egyéni hozzáadva** lépésre az **Alkalmazott lépések** listájában. 

   Megjelenik az **Egyéni oszlop hozzáadása** ablak a létrehozott egyéni oszlopképlettel.

## <a name="use-the-advanced-editor-for-custom-columns"></a>A Speciális szerkesztő használata egyéni oszlopokhoz

A lekérdezés létrehozása után a **Speciális szerkesztő** használatával is módosíthatja a lekérdezés bármelyik lépését. Ehhez kövesse az alábbi lépéseket:

1. A **Lekérdezésszerkesztő** ablakban válassza a menüszalag **Nézet** lapját. 

2. Válassza az **Advanded Editor** (Speciális szerkesztő) lehetőséget.

   Megnyílik a **Speciális szerkesztő** oldal, amelyen tetszőlegesen módosíthatja a lekérdezést. 

   ![A Speciális szerkesztő oldal](media/desktop-add-custom-column/add-custom-column_07.png)

   
## <a name="next-steps"></a>Következő lépések

- Egyéni oszlopot más módokon is létrehozhat, például a Lekérdezésszerkesztőben megadott példák alapján. További információ: [Oszlop hozzáadása példából a Power BI Desktopban](desktop-add-column-from-example.md).

- Power Query M-referenciákat a [Power Query M-függvények referenciája](/powerquery-m/power-query-m-function-reference) tartalmaz.

