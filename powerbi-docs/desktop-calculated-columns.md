---
title: Számított oszlopok használata a Power BI Desktopban
description: Számított oszlopok a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 805e052a2d5b493705c604d1817fc03c0a8b5376
ms.sourcegitcommit: f05ba39a0e46cb9cb43454772fbc5397089d58b4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/26/2019
ms.locfileid: "68522196"
---
# <a name="using-calculated-columns-in-power-bi-desktop"></a>Számított oszlopok használata a Power BI Desktopban
A számított oszlopokkal új adatokat adhat hozzá a modellben már meglévő táblázathoz. De ahelyett, hogy értékeket kellene lekérdeznie és betöltenie egy adatforrásból az új oszlopba, létrehozhat egy Data Analysis Expressions- (DAX-) képletet, amely meghatározza az oszlop értékeit. A számított oszlopok a Power BI Desktopban az Új oszlop funkcióval hozhatók létre Jelentés nézetben.

Az egyéni oszlopok egy kérés részeként hozhatók létre a Lekérdezésszerkesztőben az Egyéni oszlop hozzáadása paranccsal, ezzel szemben a Jelentés vagy Adatnézetben létrehozott számított oszlopok a modellbe már betöltött adatokon alapulnak. Például választhatja azt is, hogy két különböző oszlopból fűz össze adatokat két különböző, de kapcsolódó táblába, hozzáadást végez el, vagy karakterláncrészleteket nyer ki.

A létrehozott számított oszlopok a Mezők listában jelennek meg, csakúgy, mint bármely más mező, de speciális ikonnal rendelkeznek, amely azt jelzi, hogy értékeik egy képlet eredményei. Tetszőleges nevet adhat az oszlopoknak, és hozzáadhatja őket egy jelentés vizualizációjához az egyéb mezőkhöz hasonlóan.

![](media/desktop-calculated-columns/calccolinpbid_fields.png)

A számított oszlopok a [Data Analysis Expressions](https://msdn.microsoft.com/library/gg413422.aspx) (DAX) használatával számítják ki az eredményeket. Ez a képletnyelv olyan relációs adatok használatához készült, amilyeneket a Power BI Desktop is használ. A DAX több mint 200 függvényt, operátort és szerkezetet tartalmazó kódtárat tartalmaz, így rendkívüli rugalmasságot biztosít a képletek létrehozása során, amelyek szinte bármilyen adatelemzési igényhez képesek eredményeket számítani. Ha többet szeretne megtudni a DAX-ról, tekintse meg a cikk végén található További információk szakaszt.

A DAX-képletek az Excel-képletekhez hasonlók. Valójában számos DAX-függvény megegyezik az Excelben található függvényekkel. A DAX-függvényeket azonban az interaktívan szeletelt vagy szűrt adatokkal való, jelentésekben végzett munkára szánták, például a Power BI Desktopban. Az Exceltől eltérően, ahol különböző képletet használhat egy táblázat mindegyik sorában, ha DAX-képletet hoz létre egy új sorhoz, az a táblázat minden sorának értékét kiszámolja. Az oszlopértékeket szükség szerint újraszámolja a rendszer, például a mögöttes adatok frissítésekor és az értékek módosításakor.

## <a name="lets-look-at-an-example"></a>Vegyünk egy példát.
Jeff szállítmányozási vezető a Contosónál. Szeretne egy jelentést létrehozni, amely a különböző városokba érkezett szállítmányok számát mutatja. Rendelkezik egy földrajzi táblázattal, ahol a város és az állam mezők el vannak különítve. Viszont azt szeretné, hogy a jelentésben a város és az állam egyetlen értékként jelenjen meg, ugyanabban a sorban. Jelenleg a földrajzi táblázat nem rendelkezik olyan mezővel, amilyet Jeff szeretne.

![](media/desktop-calculated-columns/calccolinpbid_cityandstatefields.png)

A számított oszlopokkal Jeff összeillesztheti vagy összefűzheti a City (Város) oszlop városait a State (Állam) oszlop államaival.

Jeff a jobb gombbal rákattint a földrajzi táblázatra, majd kiválasztja az Új oszlop lehetőséget. Ezután beírja a következő DAX-képletet a képletsávba:

![](media/desktop-calculated-columns/calccolinpbid_formula.png)

Ez a képlet egyszerűen létrehoz egy új, CityState (VárosÁllam) nevű oszlopot, és a földrajzi táblázat minden sorának esetében veszi a város oszlop értékeit, beszúr egy vesszőt és egy szóközt, majd hozzáadja az állam oszlop értékeit.

Jeffnek most már rendelkezésére áll a kívánt mező.

![](media/desktop-calculated-columns/calccolinpbid_citystatefield.png)

Hozzáadhatja a jelentésvászonhoz a szállítmányok számával együtt. Gyorsan és minimális erőfeszítéssel Jeff létrehozott egy „város, állam” mezőt, melyet a vizualizációk szinte bármely típusához hozzá tud adni. Jeff látja, hogy ha létrejön egy térképi vizualizáció, a Power BI Desktop tudni fogja, hogyan olvassa be az új oszlopból a város, állam értékeket.

![](media/desktop-calculated-columns/calccolinpbid_citystatemap.png)

## <a name="learn-more"></a>További információ
Itt csak röviden bemutattuk a számított oszlopokat. Tekintse meg a következő [oktatóanyagot: Számított oszlopok létrehozása a Power BI Desktopban](desktop-tutorial-create-calculated-columns.md) oktatóanyag: letölthet egy mintafájlt, és lépésenkénti útmutatókat talál további oszlopok létrehozásáról. 

További információk a DAX-ról: [A DAX használatának alapjai a Power BI Desktopban](desktop-quickstart-learn-dax-basics.md).

A lekérdezés részeként létrehozott oszlopokról további információkért tekintse meg az Egyéni oszlopok létrehozása szakaszt a [Power BI Desktop gyakori lekérdezési feladatait ismertető](desktop-common-query-tasks.md) cikkben.  

