---
title: Számított oszlopok használata a Power BI Desktopban
description: Számított oszlopok a Power BI Desktopban
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/24/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 4a47e707969b592ec27c79558699638ce14f8640
ms.sourcegitcommit: c80fbf5b12754ce217cb47a17cb5400b1036a8f2
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/06/2018
---
# <a name="using-calculated-columns-in-power-bi-desktop"></a>Számított oszlopok használata a Power BI Desktopban
A számított oszlopokkal új adatokat adhat hozzá a modellben már meglévő táblázathoz. De ahelyett, hogy értékeket kellene lekérdeznie és betöltenie egy adatforrásból az új oszlopba, létrehozhat egy Data Analysis Expressions- (DAX-) képletet, amely meghatározza az oszlop értékeit. A számított oszlopok a Power BI Desktopban az Új oszlop funkcióval hozhatók létre Jelentés nézetben.

Az egyéni oszlopok egy kérés részeként hozhatók létre a Lekérdezésszerkesztőben az Egyéni oszlop hozzáadása paranccsal, ezzel szemben a Jelentés vagy Adatnézetben létrehozott számított oszlopok a modellbe már betöltött adatokon alapulnak. Például választhatja azt is, hogy két különböző oszlopból fűz össze adatokat két különböző, de kapcsolódó táblába, hozzáadást végez el, vagy karakterláncrészleteket nyer ki.

A létrehozott számított oszlopok a Mezők listában jelennek meg, csakúgy, mint bármely más mező, de speciális ikonnal rendelkeznek, amely azt jelzi, hogy értékeik egy képlet eredményei. Tetszőleges nevet adhat az oszlopoknak, és hozzáadhatja őket egy jelentés vizualizációjához az egyéb mezőkhöz hasonlóan.

![](media/desktop-calculated-columns/calccolinpbid_fields.png)

A számított oszlopok a [Data Analysis Expressions](https://msdn.microsoft.com/library/gg413422.aspx) (DAX) használatával számítják ki az eredményeket. Ez a képletnyelv olyan relációs adatok használatához készült, amilyeneket a Power BI Desktop is használ. A DAX több mint 200 függvényt, operátort és szerkezetet tartalmazó kódtárat tartalmaz, így rendkívüli rugalmasságot biztosít a képletek létrehozása során, amelyek szinte bármilyen adatelemzési igényhez képesek eredményeket számítani. Ha többet szeretne megtudni a DAX-ról, tekintse meg a cikk végén található További információk szakaszt.

A DAX-képletek az Excel-képletekhez hasonlók. Valójában számos DAX-függvény megegyezik az Excelben található függvényekkel. A DAX-függvényeket azonban az interaktívan szeletelt vagy szűrt adatokkal való, jelentésekben végzett munkára szánták, például a Power BI Desktopban. Az Exceltől eltérően, ahol különböző képletet használhat egy táblázat mindegyik sorában, ha DAX-képletet hoz létre egy új sorhoz, az a táblázat minden sorának értékét kiszámolja. Az oszlopértékeket szükség szerint újraszámolja a rendszer, például a mögöttes adatok frissítésekor és az értékek módosításakor.

## <a name="lets-look-at-an-example"></a>Vegyünk egy példát.
Jeff egy szállítmányozási vezető a Contosónál. Szeretne egy jelentést létrehozni, amely a különböző városokba érkezett szállítmányok számát mutatja. Jeff rendelkezik egy földrajzi táblázattal, ahol a város és az állam mezők el vannak különítve. Viszont azt szeretné, hogy a jelentésben a város és az állam egyetlen értékként jelenjen meg, ugyanabban a sorban. Jelenleg a földrajzi táblázat nem rendelkezik olyan mezővel, amilyet Jeff szeretne.

![](media/desktop-calculated-columns/calccolinpbid_cityandstatefields.png)

A számított oszlopokkal Jeff egyszerűen összeillesztheti vagy összefűzheti a City (Város) oszlop városait a State (Állam) oszlop államaival.

Jeff a jobb gombbal rákattint a földrajzi táblázatra, majd kiválasztja az Új oszlop lehetőséget. Ezután beírja a következő DAX-képletet a képletsávba:

![](media/desktop-calculated-columns/calccolinpbid_formula.png)

Ez a képlet egyszerűen létrehoz egy új, CityState (VárosÁllam) nevű oszlopot, és a földrajzi táblázat minden sorának esetében veszi a város oszlop értékeit, beszúr egy vesszőt és egy szóközt, majd hozzáadja az állam oszlop értékeit.

Jeffnek most már rendelkezésére áll az a mező, amelyet szeretett volna.

![](media/desktop-calculated-columns/calccolinpbid_citystatefield.png)

Hozzáadhatja a jelentésvászonhoz a szállítmányok számával együtt. Gyorsan és minimális erőfeszítéssel Jeff létrehozott egy „város, állam” mezőt, melyet a vizualizációk szinte bármely típusához hozzá tud adni. Jeff látja, hogy ha létrehoz egy térképi vizualizációt, a Power BI Desktop tudni fogja, hogyan olvassa be az új oszlopból a város, állam értékeket.

![](media/desktop-calculated-columns/calccolinpbid_citystatemap.png)

## <a name="learn-more"></a>További információ
Itt csak röviden bemutattuk a számított oszlopokat. Ne felejtse el megtekinteni a [Számított oszlopok létrehozása a Power BI Desktopban](desktop-tutorial-create-calculated-columns.md) oktatóanyagot, ahol letölthet egy mintafájlt, és lépésenkénti útmutatókat talál további oszlopok létrehozásáról. 

További információk a DAX-ról: [A DAX használatának alapjai a Power BI Desktopban](desktop-quickstart-learn-dax-basics.md).

A lekérdezés részeként létrehozott oszlopokról további információkért tekintse meg az Egyéni oszlopok létrehozása szakaszt a [Power BI Desktop gyakori lekérdezési feladatait ismertető](desktop-common-query-tasks.md) cikkben.  

