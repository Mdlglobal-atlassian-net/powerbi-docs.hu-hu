---
title: Adatok és rekordok megtekintés a Power BI Desktop vizualizációiban
description: A Power BI Desktop Adatok megjelenítése és Rekordok megjelenítése funkciójának használata a részletek feltárásához
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 6e425f146228d0139b9eec914a44ed5dc732fe98
ms.sourcegitcommit: 10a87c016f497dbeba32f94ed1f3688a70816fea
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65514774"
---
# <a name="use-see-data-and-see-records-in-power-bi-desktop"></a>A Power BI Desktop Adatok megjelenítése és Rekordok megjelenítése funkciójának használata
A **Power BI Desktopban** a vizualizációkat részletesen feltárhatja, és megtekintheti a mögöttes adatok szöveges alakját vagy a kijelölt vizualizáció egyes adatrekordjait. Ezeket a szolgáltatásokat időnként *átkattintásnak*, *áthatolásnak* vagy *részletezésnek* is nevezik.

Az **Adatok megtekintése** segítségével a kiválasztott vizualizációban használt értékek szöveges verzióját, a **Rekordok megtekintése** funkcióval pedig egy kiválasztott rekordhoz vagy adatponthoz tartozó összes adatot tekintheti meg. 

![Adatok megtekintése és Rekordok megtekintése](media/desktop-see-data-see-records/see-data-record.png)

>[!IMPORTANT]
>Az **Adatok megtekintése** és a **Rekordok megtekintése** funkció csak a következő vizualizációtípusokat támogatja:
>  - Sávdiagram
>  - Oszlopdiagram
>  - Fánkdiagram
>  - Kartogram
>  - Tölcsér
>  - Térkép
>  - Tortadiagram
>  - Fatérkép

## <a name="use-see-data-in-power-bi-desktop"></a>Az Adatok megtekintése funkció használata Power BI Desktopban

Az **Adatok megtekintése** funkció a vizualizációk alapjául szolgáló mögöttes adatokat jeleníti meg. Az **Adatok megtekintése** funkció az adott vizualizáció kijelölése esetén a menüszalag **Vizuális eszközök** eszközcsoportjában, az **Adatok/Részletezés** lapon jelenik meg.

![Adatok megtekintése a menüszalagon](media/desktop-see-data-see-records/see-data1.png)

Az adatok úgy is megtekinthetők, ha az adott vizualizáció jobb gombbal kattint, majd a megjelenő menüből az **Adatok megjelenítése** lehetőséget választja, vagy az adott vizualizáció jobb felső sarkában a három ponttal (...) jelzett **További lehetőségek** funkciót, majd onnan az **Adatok megjelenítése** lehetőséget választja.

![Adatok megjelenítése kattintás jobb gombbal](media/desktop-see-data-see-records/see-data2.png)&nbsp;&nbsp;![Adatok megjelenítése További lehetőségek](media/desktop-see-data-see-records/see-data3.png)

> [!NOTE]
> Az egérmutatót a vizualizáció egy adatpontja fölé kell vinnie, hogy elérhető legyen a helyi menü.

Az **Adatok megtekintése** vagy az **Adatok megjelenítése** lehetőség választása esetén a Power BI Desktop vászon a vizualizációt és az adatok szöveges formáját is megjeleníti. A *vízszintes nézetben* a vizualizáció a vászon felső felén jelenik meg, az adatok pedig az alsó felén látszanak. 

![vízszintes nézet](media/desktop-see-data-see-records/see-data4a.png)

A vászon jobb felső sarokban található ikonnal válthat a vízszintes és a *függőleges nézet* között.

![függőleges nézet váltás](media/desktop-see-data-see-records/see-data4.png)

A jelentéshez való visszatéréshez a vászon bal felső sarkában válassza a **< Vissza a jelentéshez** lehetőséget.

![Vissza a jelentéshez](media/desktop-see-data-see-records/see-data5.png)

## <a name="use-see-records-in-power-bi-desktop"></a>Rekordok megtekintése funkció használata Power BI Desktopban

A vizualizációk egy-egy adatrekordja is a középpontba állítható, és részletesen megvizsgálhatók az alapjául szolgáló mögöttes adatok. A **Rekordok megtekintése** használatához jelöljön ki egy vizualizációt, és a menüszalag **Vizuális eszközök** eszközcsoportjában, az **Adatok/Részletezés** lapon válassza a **Rekordok megtekintése** funkciót, majd utána jelölje ki a vizualizáció egyik adatpontját vagy sorát. 

![Rekordok megtekintése a menüszalagon](media/desktop-see-data-see-records/see-record1.png)

> [!NOTE]
> Ha a menüszalagon a **Rekordok megtekintése** gomb le van tiltva és ki van szürkítve, az azt jelenti, hogy a kijelölt vizualizáció nem támogatja a **Rekordok megtekintése** funkciót.

Jobb gombbal is kattinthat egy adatelemen, majd a megjelenő menüben is választhatja a **Rekordok megtekintése** lehetőséget.

![Rekordok megtekintése jobb gombbal](media/desktop-see-data-see-records/see-record2.png)

Ha egy adatelem esetén a **Rekordok megtekintése** lehetőséget választja, a Power BI Desktop vászon a kijelölt elemhez kapcsolódó összes adatot megjeleníti. 

![](media/desktop-see-data-see-records/see-record3.png)

A jelentéshez való visszatéréshez a vászon bal felső sarkában válassza a **< Vissza a jelentéshez** lehetőséget.

![](media/desktop-see-data-see-records/see-record4.png)

> [!NOTE]
>A **Rekordok megtekintése** funkcióra a következő korlátozások vonatkoznak:
> - A **Rekordok megtekintése** nézetben az adatok nem módosíthatók és nem menthetők vissza a jelentésbe.
> - A **Rekordok megjelenítése** nem használható, ha a vizualizáció kiszámított mértéket használ.
> - A **Rekordok megjelenítése** nem használható, ha egy élő többdimenziós (multidimensional, MD) modellt használ.

## <a name="next-steps"></a>Következő lépések
A **Power BI Desktopban** sokféle jelentésformázási és adatkezelési szolgáltatás érhető el. A következő forrásanyagok ezekből ismertetnek néhányat:

* [Csoportosítás és dobozolás használata a Power BI Desktopban](desktop-grouping-and-binning.md)
* [Rácsvonalak, rácshoz illesztés, mélységi (Z) index, igazítás és disztribúció használata a Power BI Desktop-jelentésekben](desktop-gridlines-snap-to-grid.md)

