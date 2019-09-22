---
title: Jelentésközi részletezés a Power BI Desktopban
description: Útmutató egy jelentésből a másikba átnyúló részletezéshez a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/10/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: e735d45a7a49c4a0365e35d5bb95957c6145f934
ms.sourcegitcommit: db4fc5da8e65e0a3dc35582d7142a64ad3405de7
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/11/2019
ms.locfileid: "70903755"
---
# <a name="use-cross-report-drillthrough-in-power-bi-desktop"></a>Jelentésközi részletezés a Power BI Desktopban

A Power BI Desktop jelentésközi részletezés funkciójával környezetfüggően ugorhat egy jelentésről egy másikra. Mindez akkor lehetséges, ha a jelentések egy munkaterületen vagy alkalmazáson belül vannak a Power BI szolgáltatásban. Jelentésközi részletezéssel kettő vagy több olyan jelentés, amelyek kapcsolódó tartalommal rendelkeznek, és átadható a szűrési környezet a jelentésközi kapcsolaton keresztül. Ebből a cikkből elsajátíthatja jelentésközi részletezések beállítását Power BI-jelentésekhez, és megtudhatja, mit tapasztalnak a jelentésközi részletezés felhasználói.

![A Power BI Desktop Részletezés lehetőségének képernyőképe](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

A jelentésközi részletezés beállításának és használatának megkezdése előtt fontos tisztában lenni az alábbi fogalmakkal:

* **Forrásvizualizáció:** Az a vizualizáció, amely a vizualizáció környezeti menüjének használatával a részletezést kezdeményezi.
* **Forrásjelentés:** A jelentésközi részletezés forrásvizualizációját tartalmazó jelentés.
* **Céloldal:** Az az oldal, amelyre a felhasználó érkezik a részletezési művelet indítása után.
* **Céljelentés:** A jelentésközi részletezés céloldalát tartalmazó jelentés.


> [!NOTE]
> A *Saját munkaterületen* belül egyénileg megosztott jelentések, amelyek a *[Velem megosztva](service-share-dashboards.md#share-a-dashboard-or-report)* területen jelennek meg, csak azon a munkaterületen érhetők el, amelyen eredetileg meg lettek osztva. 


## <a name="enable-cross-report-drillthrough"></a>Jelentésközi részletezés engedélyezése

Ahhoz, hogy egy jelentés jelentésközi részletezés célja lehessen, engedélyeznie kell ezt a funkciót a jelentéshez a **Beállítások** ablakban. Nyissa meg a **Fájl** > **Beállítások és lehetőségek** > **Beállítások** menüt, majd lépjen az oldal alja közelében a bal oldalon található **Jelentés beállításai** lehetőségre.

Jelölje be **A jelentés vizualizációi használhatnak más jelentésekből származó részletezési célokat** jelölőnégyzetet, ahogyan az alábbi ábrán látható.

![A Beállítások ablak képernyőképe a Jelentés beállításai kiemelésével](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

Így már engedélyezve van a jelentésközi részletezés.

## <a name="set-up-cross-report-drillthrough"></a>Jelentésközi részletezés beállítása

A jelentésközi részletezés a jelentésen belüli részletezéshez hasonló módon állítható be. A részletezés engedélyezve van a céloldalon, ezáltal más vizualizációk célként adhatják meg ezt az oldalt a részletezéshez. A részletezés egy jelentésen belüli létrehozásának lépéseit a [Részletezés használata a Power BI Desktopban](desktop-drillthrough.md) című cikk ismerteti.

A beállítási folyamat elindításához végre kell hajtania néhány kezdeti lépést:

* Állítson be egy részletezési céloldalt, amely elérhető lesz a munkaterületen vagy alkalmazáson belüli más jelentésekből.
* Engedélyezze egy jelentésnek, hogy az önmagán kívüli részletezési oldalakat is lássa.

A részletezési beállítások a **Vizualizációk** panel **Mezők** szakaszában találhatók, amint az alábbi ábrán látható.

![A Vizualizációk panel képernyőképe a Részletezési beállítások kiemelésével](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

A részletezés engedélyezése egy oldalhoz azzal kezdődik, hogy érvényesíti a forrás- és céljelentés adatmodelljeit. Ellenőrizze a következőket: 

* Az átadni kívánt mezők mindkét adatmodellben léteznek.
* A mezők nevei, valamint azoknak a tábláknak a nevei, amelyekhez ezek tartoznak, megegyeznek (a sztringeknek is egyezniük kell, és ezekben a kis- és nagybetűk meg vannak különböztetve).

Ha például a *Geography* tábla *Country* mezőjére vonatkozó szűrőt szeretne átadni, akkor mindkét modellben lennie kell egy *Geography* nevű táblának, azon belül pedig egy *Country* mezőnek. Ha nem így van, a mögöttes modellben kell módosítania a mező vagy a tábla nevét. A mezők megjelenített nevének módosítása önmagában nem elég a jelentésközi részletezés megfelelő működéséhez. (Megjegyzendő, hogy a jelentések sémáinak nem kell pontosan megegyezniük.)

A beállítás megkezdéséhez elő kell készítenie egy céloldalt. Nyissa meg az oldalt a Power BI Desktopban, és ellenőrizze, hogy a **Jelentésközi** részletezés kapcsolója a **Be** állásban van-e. 

![A Jelentésközi részletezés Be helyzetű kapcsolójának képernyőképe](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

Ez után húzza a vászonra a részletezés céljaként használni kívánt mezőket. Válassza ki, hogy a mezőt kategóriaként szeretné használni, vagy összesítve, mint egy mértéket. Ezen a ponton döntheti el, hogy le szeretné-e tiltani **Az összes szűrő megőrzése** kapcsolót a vizualizációhoz. Ha nem szeretne a forrásvizualizáción alkalmazott más szűrőket is átadni a részletezés célvizualizációjának, válassza a **Ki** beállítást.

> [!NOTE]
> Ha az oldalt csak jelentésközi részletezéshez használja, törölnie kell az arra automatikusan felvett **Vissza** gombot. A **Vissza** gomb csak az egy jelentésen belüli navigációhoz használható. 

A vizualizáció konfigurálása után mindenképpen mentse a jelentést, ha a Power BI szolgáltatásban dolgozik, illetve mentse és tegye közzé a jelentést, ha a Power BI Desktopot használja.

Az előző szakasz ismertette a jelentésközi részletezés engedélyezését a Power BI Desktophoz (a **Beállítások** ablakban). Ha a Power BI szolgáltatás használatával hozza létre a jelentésközi részletezés célját, a következőket kell megtennie a jelentésközi részletezés engedélyezéséhez: 

1. Jelölje ki azt a munkaterületet, amelyen a céljelentés és a forrásjelentés található.
2. Válassza a **Jelentések** lehetőséget.
3. Válassza a forrásjelentés **Beállítások** ikonját.
4. Ellenőrizze, hogy a jelentésközi részletezés kapcsolója **Be** helyzetben van.
5. Mentse a jelentést.

Ennyi az egész. A jelentés így már felhasználható a jelentésközi részletezési felületen. 

A következő szakasz a felhasználó szempontjából mutatja be ezt a felületet.

## <a name="cross-report-drillthrough-experience"></a>A jelentésközi részletezés felhasználói felülete

A funkciót akkor veheti használatba, amikor a jelentésközi részletezési felületet konfigurálja egy jelentéshez.

Válassza ki a forrásjelentést a Power BI szolgáltatásban, majd válassza ki azt a vizualizációt, amely olyan módon használja a mezőt vagy mezőket, ahogyan a céloldal beállítása során megadta. Ez után kattintson egy adatpontra a vizualizáció helyi menüjének megnyitásához, és válassza a **Részletezés** menüpontot.

![A Power BI szolgáltatásban látható forrásjelentés képernyőképe a Részletezés menüpont kiemelésével](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Az eredmények úgy jelennek meg a jelentésközi részletezés céloldalán, ahogyan a cél létrehozásakor beállította azokat. Az eredmények a részletezés beállításainak megfelelően vannak szűrve.

> [!IMPORTANT]
> A Power BI gyorsítótárazza a jelentésközi részletezések céljait. Ha módosításokat végez, mindig frissítse az oldalt a böngészőben, ha a részletezés célja nem a várt módon jelenik meg. 

A jelentésközi célok formázásának menete a következő: 

`Target Page Name [Target Report Name]`

Miután Ön kiválasztja a céloldalt, amelyre részletezni szeretne, a Power BI megnyitja ezt az oldalt. A céloldal beállításai alapján átadja a szűrési környezetet. 

A forrásvizualizációból származó szűrési környezet többek között az alábbiakat tartalmazhatja: 

* A forrásvizualizációra vonatkozó jelentés-, oldal- és vizualizációszintű szűrők. 
* A forrásvizualizációra vonatkozó keresztszűrés és keresztkiemelés. 
* Az oldalon lévő szeletelők és szinkronszeletelők.
* URL-paraméterek.

Amikor megnyitja a részletezés céljelentését, a Power BI csak azokra a mezőkre alkalmaz szűrőket, amelyekhez a mezőnevekben és táblanevekben pontosan egyező sztringeket talál. A Power BI nem alkalmaz a céljelentésből származó rögzített szűrőket. Alkalmazza viszont az alapértelmezett személyes könyvjelzőt, ha az létezik. Ha az Ön alapértelmezett személyes könyvjelzője például tartalmazza a *Country = US* jelentésszintű szűrőt, akkor a Power BI először ezt a szűrőt alkalmazza a forrásvizualizációból származó szűrési környezet alkalmazása előtt. 

Jelentésközi részletezéshez a Power BI a céljelentés összes standard oldalának átadja a szűrési környezetet. A Power BI nem adja át a szűrési környezetet az elemleírás-oldalaknak, ezek ugyanis az elemleírást meghívó forrásvizualizáció alapján vannak szűrve.

Ha a jelentésközi részletezési művelet után vissza szeretne térni a forrásjelentéshez, használja a böngésző **Vissza** gombját. 

## <a name="next-steps"></a>Következő lépések

Az alábbi cikkeket is érdekesnek találhatja:

* [Szeletelők használata a Power BI Desktopban](visuals/power-bi-visualization-slicers.md)
* [Részletezés használata a Power BI Desktopban](desktop-drillthrough.md)

