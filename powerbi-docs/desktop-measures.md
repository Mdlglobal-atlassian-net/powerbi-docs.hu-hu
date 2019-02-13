---
title: Mértékek használata a Power BI Desktopban
description: Mértékek a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/08/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 56935d4c4c30e759056f3d383e40d570bfd81ae8
ms.sourcegitcommit: 5e83fa6c93a0bc6599f76cc070fb0e5c1fce0082
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/13/2019
ms.locfileid: "56215354"
---
# <a name="measures-in-power-bi-desktop"></a>Mértékek a Power BI Desktopban

A **Power BI Desktop** segítségével néhány kattintással készíthet elemzéseket adatairól. Néha azonban az adatok nem tartalmaznak minden információt, amelyre a legfontosabb kérdések megválaszolásához szüksége van. Ezeket a mértékek segítségével szerezheti meg.

Mértékeket a leggyakoribb adatelemzéseknél is használunk. Például összegeket, átlagokat, minimum- és maximumértékeket, darabszámokat vagy a DAX-képletek használatával létrehozott speciális felhasználói számításokat. A mértékek számított eredménye a jelentések használata során folyamatosan változik, ami lehetővé teszi az adatok gyors és dinamikus alkalmi felderítését. Lássuk mindezt közelebbről.

## <a name="understanding-measures"></a>A mértékek ismertetése

A **Power BI Desktopban** a **Jelentés nézetben** vagy az **Adatnézetben** hozhat létre jelentéseket. A saját készítésű mértékek a Mezők listában egy számológép ikon kíséretében jelennek meg. A mértékeknek bármilyen nevet adhat, és az egyéb mezőkhöz hasonlóan hozzáadhatja őket új vagy meglévő vizualizációkhoz.

![](media/desktop-measures/measuresinpbid_measinfieldlist.png)

> [!NOTE]
> Esetleg érdekelhetik a **gyorsmérők** is, amelyek párbeszédpanelekről kiválasztható kész mértékek. Ezeken keresztül könnyen elsajátítható a mértékek létrehozása, valamint a DAX-képletek használata is, mivel az automatikusan létrehozott DAX-képleteik áttekinthetők. Lásd a következő cikket: [gyorsmérők](desktop-quick-measures.md).
> 
> 

## <a name="data-analysis-expressions"></a>Adatelemzési kifejezések

A mértékek kifejezésképletekből számítják ki az eredményeket. Az egyéni mértékek a [Data Analysis Expressions](https://msdn.microsoft.com/library/gg413422.aspx) (DAX) képletnyelv használatával hozhatók létre. A DAX egy több mint 200 függvényt, operátort és szerkezetet tartalmazó kódtárral is rendelkezik. Ez a kódtár rendkívüli rugalmasságot biztosít a mértékek létrehozása során, amelyek szinte bármilyen adatelemzési igényhez képesek eredményeket számítani.

A DAX-képletek nagyon hasonlóak az Excel-képletekhez. A DAX nyelvben számos Excel-függvény megtalálható, például a DATE, a SUM vagy a LEFT. A DAX-függvények azonban relációs adatok használatához készültek, amilyeneket a Power BI Desktop is használ.

## <a name="lets-look-at-an-example"></a>Vegyünk egy példát.
Jan a Contoso egyik értékesítési vezetője. Viszonteladói értékesítési előrejelzéseket kell készítenie a következő pénzügyi évre. Jan úgy dönt, hogy a becsléseket a múlt évben értékesített mennyiségek alapján számítja ki, és hat százalékos éves növekedéssel számol a következő hat hónapra tervezett különféle promóciók várható eredményeként.

A becslések jelentéséhez az elmúlt év értékesítési adatait importálja a Power BI Desktopba. Megkeresi a Reseller Sales (Viszonteladói értékesítések) tábla SalesAmount (Értékesítési mennyiségek) mezőjét. Mivel az importált adatok csak a múlt évre vonatkozó értékesített mennyiségeket tartalmazzák, Jan átnevezi a SalesAmount mezőt, és a Last Years Sales (Tavalyi értékesítések) nevet adja neki. Ezután ráhúzza a Last Years Sales mezőt a jelentésvászonra. Ez egy diagramvizualizációban egyetlen értékként jelenik meg, amely a múlt évi összes viszonteladói értékesítés összegét adja meg.

Jan észreveszi, hogy bár ő maga nem adott meg számítást, a rendszer automatikusan készített egyet. A Power BI Desktop létrehozott egy saját mértéket a Last Years Sales mezőben lévő értékek összege alapján.

Jannek azonban egy olyan mértékre van szüksége, amely a következő évre vonatkozó előrejelzéseket adja meg, ami az elmúlt év értékesítési adatainak 1,06-szorosa, figyelembe véve a várható 6 százalékos üzleti növekedést. Ehhez a számításhoz létrehoz egy egyéni mértéket. Az Új mérték funkcióval létrehoz egy új mértéket, amelyben a következő DAX-képletet adja meg:

    Projected Sales = SUM('Sales'[Last Years Sales])*1.06

Jan ezután a diagramra húzza a Projected Sales (Értékesítési előrejelzés) mértéket.

![](media/desktop-measures/measuresinpbid_lastyearsales.png)

Jan így gyorsan és minimális erőfeszítéssel létrehozott egy mértéket az értékesítési előrejelzések kiszámítására. Az előrejelzéseket részletesebben is kielemezhetné, ha rászűrne adott viszonteladókra, vagy további mezőket adna a jelentéshez.

## <a name="data-categories-for-measures"></a>Adatkategóriák mértékekhez

Mértékekhez adatkategóriák is kiválaszthatók. 

Ez többek között lehetővé teszi, hogy mértékek használatával dinamikusan hozzon létre URL-eket, és hogy az adatkategóriát webes URL-ként jelölje meg. 

Például létrehozhat táblázatokat, amelyben a mértékek webes URL-címekként jelennek meg, és a kiválasztásnak megfelelően a létrehozott URL-címek kattinthatók is lesznek. Ez különösen hasznos, ha más Power BI-jelentésekhez szeretne hivatkozásokat létrehozni [URL-szűrő paraméterekkel](service-url-filters.md).

## <a name="learn-more"></a>További információ
Itt csak egy rövid áttekintést adtunk a mértékekről, azonban ennél sokkal több információ áll rendelkezésre, amelyek alapján megtanulhat saját mértékeket létrehozni. Tekintse meg a következő [oktatóanyagot: Egyéni mértékek létrehozása a Power BI Desktopban](desktop-tutorial-create-measures.md). Ebben a cikkben egy letöltött mintafájlon keresztül lépésenként sajátíthatja el a mértékek létrehozását.  

A DAX behatóbb megismeréséhez tekintse át [a DAX Power BI Desktopban való használatának alapjait](desktop-quickstart-learn-dax-basics.md) ismertető cikket. A [Data Analysis Expressions-referencia](https://msdn.microsoft.com/library/gg413422.aspx) részletes cikkeket tartalmaz az egyes függvényekkel, szintaxisokkal, operátorokkal és elnevezési konvenciókkal kapcsolatban. A DAX már elérhető néhány éve az Excelhez készült Power Pivotban és az SQL Server Analysis Servicesben, így számos további nagyszerű forrásanyag is rendelkezésre áll. Tekintse meg továbbá a [DAX forrásanyagközpont wikijét](http://social.technet.microsoft.com/wiki/contents/articles/1088.dax-resource-center.aspx), ahol a BI-közösség fontos tagjai osztják meg a DAX-szal kapcsolatos tudásukat.



