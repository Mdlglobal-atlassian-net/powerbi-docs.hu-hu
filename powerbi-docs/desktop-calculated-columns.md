---
title: Számított oszlopok használata a Power BI Desktopban
description: Számított oszlopok a Power BI Desktopban
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 425bf50ad6eb4da9b50f7d9cdc760ef71cb7bff2
ms.sourcegitcommit: 08f65ea314b547b41b51afef6876e56182190266
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/25/2020
ms.locfileid: "76753291"
---
# <a name="create-calculated-columns-in-power-bi-desktop"></a>Számított oszlopok létrehozása a Power BI Desktopban
A számított oszlopokkal új adatokat adhat hozzá a modellben már meglévő táblázathoz. De ahelyett, hogy értékeket kellene lekérdeznie és betöltenie egy adatforrásból az új oszlopba, létrehozhat egy Data Analysis Expressions- (DAX-) képletet, amely meghatározza az oszlop értékeit. A Power BI Desktopban új oszlopok a **Jelentés** nézet új oszlop funkciójával hozhatók létre.

Eltérően az egyéni oszlopoktól, amelyeket egy lekérdezés részeként hozhat létre a Lekérdezésszerkesztőben az **Egyéni oszlop felvétele** lehetőséggel, a számított oszlopokat a modellbe már betöltött adatoktól függően a **Jelentés** vagy az **Adat** nézetben lehet létrehozni. Dönthet például úgy, hogy két különböző de kapcsolódó tábla két oszlopának értékeit fűzi össze, összeadást végez, vagy alsztringeket nyer ki.

A létrehozott számított oszlopok a **Mezők** listában jelennek meg csakúgy, mint bármely más mező, de speciális ikonnal rendelkeznek, amely azt jelzi, hogy értékeik egy képlet eredményei. Tetszőleges nevet adhat az oszlopoknak, és hozzáadhatja őket egy jelentés vizualizációjához az egyéb mezőkhöz hasonlóan.

![](media/desktop-calculated-columns/calccolinpbid_fields.png)

A számított oszlopok a DAX használatával számítják ki az eredményeket. Ez a képletnyelv olyan relációs adatok használatához készült, amilyeneket a Power BI Desktop is használ. A DAX egy több mint 200 függvényt, operátort és szerkezetet tartalmazó kódtárral is rendelkezik. Rendkívüli rugalmasságot biztosít a képletek létrehozása során, amelyek szinte bármilyen adatelemzési igényhez képesek eredményeket számítani. További információk a DAX-ról: [A DAX használatának alapjai a Power BI Desktopban](desktop-quickstart-learn-dax-basics.md).

A DAX-képletek az Excel-képletekhez hasonlók. Valójában számos DAX-függvény megegyezik az Excelben található függvényekkel. A DAX-függvényeket azonban az interaktívan szeletelt vagy szűrt adatokkal való, jelentésekben végzett munkára szánták, például a Power BI Desktopban. Az Excelben egy táblázat valamennyi sorában más képlet szerepelhet. A Power BI-ban egy új oszlophoz létrehozott DAX-képlet a tábla összes sorához kiszámít egy eredményt. Az oszlopértékeket szükség szerint újraszámolja a rendszer, például a mögöttes adatok frissítésekor és az értékek módosításakor.

## <a name="lets-look-at-an-example"></a>Vegyünk egy példát.
Jeff szállítmányozási vezető a Contosónál. Szeretne egy jelentést létrehozni, amely a különböző városokba érkezett szállítmányok számát mutatja. Rendelkezik egy **földrajzi** táblával, ahol a város és az állam mezők el vannak különítve. Jeff viszont azt szeretné, hogy a jelentésben a város és az állam értéke egyetlen értékként jelenjen meg, ugyanabban a sorban. Jelenleg a **földrajzi** tábla nem rendelkezik olyan mezővel, amilyet Jeff szeretne.

![](media/desktop-calculated-columns/calccolinpbid_cityandstatefields.png)

A számított oszlopokkal Jeff összefűzheti a **City** (Város) oszlop városait a **State** (Állam) oszlop államaival.

Jeff a jobb gombbal rákattint a **földrajzi** táblára, majd kiválasztja az **Új oszlop** lehetőséget. Ezután beírja a következő DAX-képletet a képletsávba:

![](media/desktop-calculated-columns/calccolinpbid_formula.png)

A képlet egyszerűen egy új, **CityState** nevű oszlopot hoz létre. A földrajzi **Geography** tábla minden sorának esetében veszi a **City** (város) oszlop értékeit, beszúr egy vesszőt és egy szóközt, majd hozzáadja a **State** (állam) oszlop értékeit.

Jeffnek most már rendelkezésére áll a kívánt mező.

![](media/desktop-calculated-columns/calccolinpbid_citystatefield.png)

Hozzáadhatja a jelentésvászonhoz a szállítmányok számával együtt. Jeff minimális erőfeszítéssel létrehozott egy „város, állam” tartalmú **CityState** mezőt, melyet a vizualizációk szinte bármely típusához hozzá tud adni. Amikor Jeff új térképet hoz létre, a Power BI Desktop tudni fogja, hogyan olvassa be az új oszlopból a város, állam értékeket.

![](media/desktop-calculated-columns/calccolinpbid_citystatemap.png)

## <a name="next-steps"></a>Következő lépések
Itt csak röviden bemutattuk a számított oszlopokat. További információkért tekintse meg az alábbi forrásanyagokat:

* Ebben a cikkben egy letöltött mintafájlon keresztül lépésenként sajátíthatja el az új oszlopok létrehozását: [Oktatóanyag: Számított oszlopok létrehozása a Power BI Desktopban](desktop-tutorial-create-calculated-columns.md)

* További információk a DAX-ról: [A DAX használatának alapjai a Power BI Desktopban](desktop-quickstart-learn-dax-basics.md).

* A lekérdezés részeként létrehozott oszlopokról további információkat talál a [Power BI Desktop gyakori lekérdezési feladatait](desktop-common-query-tasks.md) ismertető cikk **Egyéni oszlopok létrehozása** szakaszában.  

