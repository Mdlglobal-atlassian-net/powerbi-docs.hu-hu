---
title: Hivatkozási integritás feltételezése beállítás a Power BI Desktopban
description: A DirectQuery használatával megtudhatja, hogyan feltételezhet a Power BI Desktop hivatkozási integritást
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 4d478396f88a1443c0d23d64199d84f0b615b1da
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761818"
---
# <a name="apply-the-assume-referential-integrity-setting-in-power-bi-desktop"></a>A Hivatkozási integritás feltételezése beállítás alkalmazása a Power BI Desktopban
Amikor a **DirectQuery** használatával csatlakozik egy adatforráshoz, a **Hivatkozási integritás feltételezése** lehetőséggel engedélyezheti a hatékonyabb lekérdezések futtatását az adatforráson. Ez a funkció a felállít néhány követelményt a mögöttes adatokkal szemben, és csak a **DirectQuery** használatakor érhető el.

A **Hivatkozási integritás feltételezése** beállítás lehetővé teszi, hogy az adatforráson a lekérdezések **INNER JOIN** utasításokat használjanak az **OUTER JOIN** helyett, ami javítja a lekérdezés hatékonyságát.

![](media/desktop-assume-referential-integrity/assume-referential-integrity_1.png)

## <a name="requirements-for-using-assume-referential-integrity"></a>A hivatkozási integritás feltételezése használatának követelményei
Ez egy speciális beállítás, és csak akkor engedélyezett, ha a **DirectQuery** használatával csatlakozik az adatokhoz. A következő utasításokra van szükség a **Hivatkozási integritás feltételezése** funkció megfelelő működéséhez:

* A Kapcsolat **Forrás** oszlopában lévő adatok soha nem *Null* értékűek vagy *üresek*
* A **Forrás** oszlop minden értékéhez található megfelelő érték a **Cél** oszlopban

Ebben a környezetben a **Forrás** oszlop az *Egy-a-többhöz* kapcsolat *Több* oldala, vagy pedig az *Egy-az-egyhez* kapcsolatban lévő első táblázat.

## <a name="example-of-using-assume-referential-integrity"></a>A hivatkozási integritás feltételezése használatának példája
A következő példa bemutatja, hogyan viselkedik a **Hivatkozási integritás feltételezése** az adatkapcsolatokban. A példa egy olyan adatforráshoz csatlakozik, amelyben egy **Orders** (Megrendelések) táblázat, egy **Products** (Termékek) táblázat és egy **Depots** (Raktárak) táblázat található van.

1. Az **Orders** (Megrendelések) táblázat és a **Products** (Termékek) táblázat következő képén figyelje meg, hogy hivatkozási integritás áll fenn az **Orders[ProductID]** (Megrendelések[Termékazonosító]) és a **Products[ProductID]** (Termékek[Termékazonosító]) között. Az **Orders** (Megrendelések) táblázat **[ProductID]** ([Termékazonosító]) oszlopa soha nem *Null* értékű, és minden érték megjelenik a **Products** (Termékek) táblázatban is. Így érdemes beállítani a **Hivatkozási integritás feltételezése** funkciót, hogy hatékonyabb értékeket szerezhessen be (a beállítás nem módosítja a vizualizációkban látható értékeket).
   
   ![](media/desktop-assume-referential-integrity/assume-referential-integrity_2.png)
2. A következő képen figyelje meg, hogy nem létezik hivatkozási integritás az **Orders[DepotID]** (Megrendelések[Raktárazonosító]) és a **Depots[DepotID]** (Raktárak[Raktárazonosító]) között, mert a **DepotID** ([Raktárazonosító]) egyes *Orders* (Megrendelések) mezők esetén *Null* értékű. Így a **Hivatkozási integritás feltételezése** funkció *nem* állítható be.
   
   ![](media/desktop-assume-referential-integrity/assume-referential-integrity_3.png)
3. Végül, nem áll fenn hivatkozási integritás az **Orders[CustomerID]** (Megrendelések[Ügyfélazonosító]) és a **Customers[CustID]** (Ügyfelek[Ügyfélazonosító]) között a következő táblázatokban; a **CustomerID** ([Ügyfélazonosító]) olyan értéket is tartalmaz (ebben az esetben *CustX*), amely nem létezik a *Customers* (Ügyfelek) táblázatban. Így a **Hivatkozási integritás feltételezése** funkció *nem* állítható be.
   
   ![](media/desktop-assume-referential-integrity/assume-referential-integrity_4.png)

## <a name="setting-assume-referential-integrity"></a>Hivatkozási integritás feltételezésének beállítása
A funkció engedélyezéséhez jelölje be a **Hivatkozási integritás feltételezése** melletti jelölőnégyzetet a következő képen láthatóak szerint.

![](media/desktop-assume-referential-integrity/assume-referential-integrity_1.png)

Amikor be van jelölve, a rendszer ellenőrzi a beállítást az adatokban, hogy ne legyenek *Null* értékű vagy nem egyező sorok. *Azonban* azokban az esetekben, ahol nagyon sok érték szerepel, az ellenőrzés nem garantálja a hivatkozási integritási problémák teljes kiküszöbölését.

Ezenkívül az ellenőrzés a kapcsolat szerkesztésekor történik, és *nem* tükrözi az adatok későbbi módosításait.

## <a name="what-happens-if-you-incorrectly-set-assume-referential-integrity"></a>Mi történik, ha helytelenül állítja be a Hivatkozási integritás feltételezése funkciót?
Ha a **Hivatkozási integritás feltételezése** funkciót úgy állítja be, hogy hivatkozási integritási hibák találhatók az adatokban, az nem eredményez hibákat. Azonban ez az adatokban látszólagos ellentmondásokat eredményez. A fent leírt **Depots** (Raktárak) táblázattal való kapcsolat például a következőt eredményezné:

* A teljes *Order Qty* (Megrendelt mennyiség) értéket megjelenítő vizualizáció 40 értéket mutatna
* A teljes *Order Qty by Depot City* (Megrendelt mennyiség a raktár városa alapján) értéket megjelenítő vizualizáció csak összesen *30* értéket jelenítene meg, mert nem tartalmazná az 1. rendelésazonosítót, ahol a **DepotID** (Raktárazonosító) értéke *Null*.

## <a name="next-steps"></a>Következő lépések
További információk a [DirectQueryről](desktop-use-directquery.md)

További információk a [kapcsolatokról a Power BI szolgáltatásban](desktop-create-and-manage-relationships.md)

További információk a [Kapcsolat nézetről a Power BI Desktopban](desktop-relationship-view.md).

