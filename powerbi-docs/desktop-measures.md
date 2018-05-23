---
title: Mértékek használata a Power BI Desktopban
description: Mértékek a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 3246f13291b3dd46f60db9403b1b69029c65a513
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/17/2018
---
# <a name="measures-in-power-bi-desktop"></a>Mértékek a Power BI Desktopban
A **Power BI Desktop** segítségével néhány kattintással készíthet elemzéseket adatairól. Néha azonban az adatok nem tartalmaznak minden információt, amelyre a legfontosabb kérdések megválaszolásához szüksége van. Ezeket a mértékek segítségével szerezheti meg.

A leggyakoribb adatelemzések során is használunk mértékeket – például összegeket, átlagokat, minimum- és maximumértékeket, darabszámokat vagy a DAX-képletek használatával létrehozott speciális felhasználói számításokat. A mértékek számított eredménye a jelentések használata során folyamatosan változik, ami lehetővé teszi az adatok gyors és dinamikus alkalmi felderítését. Lássuk mindezt közelebbről.

## <a name="understanding-measures"></a>A mértékek ismertetése
A **Power BI Desktopban** a **Jelentés nézetben** vagy az **Adatnézetben** hozhat létre jelentéseket. A saját készítésű mértékek a Mezők listában egy számológép ikon kíséretében jelennek meg. A mértékeknek bármilyen nevet adhat, és az egyéb mezőkhöz hasonlóan hozzáadhatja őket új vagy meglévő vizualizációkhoz.

![](media/desktop-measures/measuresinpbid_measinfieldlist.png)

> [!NOTE]
> Esetleg érdekelhetik a **gyorsmérők** is, amelyek párbeszédpanelekről kiválasztható kész mértékek. Ezeken keresztül könnyen elsajátítható a mértékek létrehozása, valamint a DAX-képletek használata is, mivel az automatikusan létrehozott DAX-képleteik áttekinthetők. Lásd a következő cikket: [gyorsmérők](desktop-quick-measures.md).
> 
> 

## <a name="data-analysis-expressions"></a>Adatelemzési kifejezések
A mértékek kifejezésképletekből számítják ki az eredményeket. Az egyéni mértékek a [Data Analysis Expressions](https://msdn.microsoft.com/library/gg413422.aspx) (DAX) képletnyelv használatával hozhatók létre. A DAX több mint 200 függvényt, operátort és szerkezetet tartalmazó kódtárt tartalmaz, így rendkívüli rugalmasságot biztosít a mértékek létrehozása során, amelyek szinte bármilyen adatelemzési igényhez képesek eredményeket számítani.

A DAX-képletek nagyon hasonlóak az Excel-képletekhez. A DAX nyelvben számos Excel-függvény megtalálható, például a DATE, a SUM vagy a LEFT. A DAX-függvények azonban relációs adatok használatához készültek, amilyeneket a Power BI Desktop is használ.

## <a name="lets-look-at-an-example"></a>Vegyünk egy példát.
Jan a Contoso egyik értékesítési vezetője. Viszonteladói értékesítési előrejelzéseket kell készítenie a következő pénzügyi évre. Úgy dönt, hogy a becsléseit a múlt évben értékesített mennyiségek alapján számítja ki, és hat százalékos éves növekedéssel számol a következő hat hónapra tervezett különféle promóciók várható eredményeként.

A becslések jelentéséhez az elmúlt év értékesítési adatait importálja a Power BI Desktopba. Megkeresi a Reseller Sales (Viszonteladói értékesítések) tábla SalesAmount (Értékesítési mennyiségek) mezőjét. Mivel az importált adatok csak a múlt évre vonatkozó értékesített mennyiségeket tartalmazzák, átnevezi a SalesAmount mezőt, és a Last Years Sales (Tavalyi értékesítések) nevet adja neki. Ezután ráhúzza a Last Years Sales mezőt a jelentésvászonra. Ez egy diagramvizualizációban egyetlen értékként jelenik meg, amely a múlt évi összes viszonteladói értékesítés összegét adja meg.

Jan észreveszi, hogy bár ő maga nem adott meg számítást, a rendszer automatikusan készített egyet. A Power BI Desktop létrehozott egy saját mértéket a Last Years Sales mezőben lévő értékek összege alapján.

Jannek azonban egy olyan mértékre van szüksége, amely a következő évre vonatkozó előrejelzéseket adja meg, ami az elmúlt év értékesítési adatainak 1,06-szorosa, figyelembe véve a várható 6 százalékos üzleti növekedést. Ehhez a számításhoz létrehoz egy egyéni mértéket. Az Új mérték funkcióval létrehoz egy új mértéket, amelyben a következő DAX-képletet adja meg:

    Projected Sales = SUM('Sales'[Last Years Sales])*1.06

Jan ezután a diagramra húzza a Projected Sales (Értékesítési előrejelzés) mértéket.

![](media/desktop-measures/measuresinpbid_lastyearsales.png)

Jan így gyorsan és minimális erőfeszítéssel létrehozott egy mértéket az értékesítési előrejelzések kiszámítására. Az előrejelzéseket részletesebben is kielemezhetné, ha rászűrne adott viszonteladókra, vagy további mezőket adna a jelentéshez.

## <a name="learn-more"></a>További információk
Itt csak egy rövid áttekintést adtunk a mértékekről, azonban ennél sokkal több információ áll rendelkezésre, amelyek alapján megtanulhat saját mértékeket létrehozni. Tekintse meg az [egyéni mértékek Power BI Desktopban való létrehozásáról szóló oktatóanyagot](desktop-tutorial-create-measures.md). Ebben a cikkben egy letöltött mintafájlon keresztül lépésenként elsajátíthatja a mértékek létrehozását.  

A DAX behatóbb megismeréséhez tekintse át [a DAX Power BI Desktopban való használatának alapjait](desktop-quickstart-learn-dax-basics.md) ismertető cikket. A [Data Analysis Expressions-referencia](https://msdn.microsoft.com/library/gg413422.aspx) részletes cikkeket tartalmaz az egyes függvényekkel, szintaxisokkal, operátorokkal és elnevezési konvenciókkal kapcsolatban. A DAX már elérhető néhány éve az Excelhez készült Power Pivotban és az SQL Server Analysis Servicesben, így rengeteg további nagyszerű forrásanyag is rendelkezésre áll. Tekintse meg továbbá a [DAX forrásanyagközpont wikijét](http://social.technet.microsoft.com/wiki/contents/articles/1088.dax-resource-center.aspx), ahol a BI-közösség fontos tagjai osztják meg a DAX-szal kapcsolatos tudásukat.



