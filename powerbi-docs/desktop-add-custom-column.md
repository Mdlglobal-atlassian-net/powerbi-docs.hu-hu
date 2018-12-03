---
title: Egyéni oszlop hozzáadása a Power BI Desktopban
description: Új egyéni oszlop gyors létrehozása a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 3ea3aa22a2ab76df115c1b4784d74dedfdf7dbf0
ms.sourcegitcommit: 05303d3e0454f5627eccaa25721b2e0bad2cc781
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52578658"
---
# <a name="add-a-custom-column-in-power-bi-desktop"></a>Egyéni oszlop hozzáadása a Power BI Desktopban
A **Power BI Desktop** **Lekérdezésszerkesztőjével** egyszerűen adhat hozzá új egyéni adatoszlopokat a modellekhez. Ha egyéni oszlopokat szeretne létrehozni vagy átnevezni, egyszerű gombműveletekkel az egyéni oszlopot definiáló [M képleteket](https://msdn.microsoft.com/library/mt270235.aspx) hozhat létre. Az M képlet egy [átfogó függvényreferencia-tartalomkészlettel](https://msdn.microsoft.com/library/mt779182.aspx) rendelkezik. 

![](media/desktop-add-custom-column/add-custom-column_01.png)

Az egyéni oszlopok létrehozása is a **Lekérdezésszerkesztőben** létrehozott lekérdezés egy **Alkalmazott lépése**, ami azt jelenti, hogy bármikor cserélhetők, előre-hátra mozgathatók vagy módosíthatók.

## <a name="use-query-editor-to-add-a-new-custom-column"></a>Új egyéni oszlop hozzáadása a Lekérdezésszerkesztővel
Új egyéni oszlop létrehozásához indítsa el a **Lekérdezésszerkesztőt**. Ehhez kattintson a **Power BI Desktop** **Kezdőlap** szalagján a **Lekérdezések szerkesztése** gombra.

![](media/desktop-add-custom-column/add-column-from-example_02.png)

Miután elindította a **Lekérdezésszerkesztőt** és betöltött néhány adatot, egyéni oszlop hozzáadásához válassza a szalag **Oszlop hozzáadása** szakaszát, majd az **Egyéni oszlop lehetőséget**.

![](media/desktop-add-custom-column/add-custom-column_02.png)

Ekkor megnyílik az **Egyéni oszlop hozzáadása** ablak, amelyet a következő szakaszban ismertetünk.

## <a name="the-add-custom-column-window"></a>Az Egyéni oszlop hozzáadása ablak
Az **Egyéni oszlop hozzáadása** ablak jobb oldali panelén az elérhető mezők listája látható, felül az egyéni oszlop nevével (ha át szeretné nevezni, csak írja be az új nevet a szövegmezőbe), valamint az új egyéni oszlopot definiáló [**M** képlettel](https://msdn.microsoft.com/library/mt779182.aspx), amelyet a jobb oldali mezők beillesztésével, operátorok hozzáadásával és egyéb módszerekkel hozhat létre (vagy írhat meg). 

![](media/desktop-add-custom-column/add-custom-column_03.png)

## <a name="create-formulas-for-your-custom-column"></a>Képletek létrehozása az egyéni oszlopokhoz
Ha kijelöl egy mezőt a jobb oldali **Elérhető oszlopok:** listában, a **<< Beszúrás** gombbal adhatja hozzá az egyéni oszlop képletéhez. A hozzáadáshoz az is elég, ha a listában duplán az oszlop nevére kattint.

A képlet beírása és az oszlop létrehozása során az ablak alján valós időben láthatja (a beírás közben), hogy a rendszer észlel-e szintaxishibát. Ha minden rendben, egy zöld pipa látható.

![](media/desktop-add-custom-column/add-custom-column_04.png)

Ha a szintaxis valamilyen hibát tartalmaz, egy sárga figyelmeztető ikon jelenik meg az észlelt hibával együtt, valamint egy hivatkozás, amely a kurzort a hiba helyére irányítja (a képletben).

![](media/desktop-add-custom-column/add-custom-column_05.png)

Az **OK** gombra kattintva a rendszer hozzáadja az egyéni oszlopot a modellhez, és az **Egyéni oszlop hozzáadva** lépéssel kiegészíti a lekérdezés **Alkalmazott lépéseit**.

![](media/desktop-add-custom-column/add-custom-column_06.png)

Ha duplán az **Egyéni oszlop hozzáadva** lépésre kattint az **Alkalmazott lépések** panelen, újra megnyílik az **Egyéni oszlop hozzáadása** ablak, amelyben az egyéni oszlop létrehozott képlete már be van töltve, és szükség esetén azonnal módosítható.

## <a name="using-the-advanced-editor-for-custom-columns"></a>A Speciális szerkesztő használata egyéni oszlopokhoz
A **Speciális szerkesztővel** is létrehozhat egyéni oszlopot (és módosíthatja a lekérdezés bármely lépését). A **Lekérdezésszerkesztőben** válassza a **Nézet** lapot, majd válassza a **Speciális szerkesztő** lehetőséget a **Speciális szerkesztő** megjelenítéséhez.

![](media/desktop-add-custom-column/add-custom-column_07.png)

A **Speciális szerkesztő** teljes körű vezérlését biztosít a lekérdezés felett.

## <a name="next-steps"></a>Következő lépések
Egyéb módokon is létrehozhat egyéni oszlopot, például a **Lekérdezésszerkesztőben** megadott példák alapján. A következő cikkben további információt talál az egyéni oszlopok példákból való létrehozásáról:

* [Oszlop hozzáadása példából a Power BI Desktopban](desktop-add-column-from-example.md)
* [Bevezetés az M-képletes nyelvbe](https://msdn.microsoft.com/library/mt270235.aspx)
* [Az M-függvény segédanyagai](https://msdn.microsoft.com/library/mt779182.aspx)  

