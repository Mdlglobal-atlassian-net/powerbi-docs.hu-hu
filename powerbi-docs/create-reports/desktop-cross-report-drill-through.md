---
title: Jelentésközi részletezés a Power BI Desktopban
description: Útmutató egy jelentésből a másikba átnyúló részletezéshez a Power BI Desktopban
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/16/2019
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 178ad340a9a3ccd9d6427dc6bad03b6d8d08ce90
ms.sourcegitcommit: 250242fd6346b60b0eda7a314944363c0bacaca8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/20/2020
ms.locfileid: "83694071"
---
# <a name="use-cross-report-drillthrough-in-power-bi"></a>Jelentésközi részletezés a Power BI-ban

A Power BI *Jelentésközi részletezés* funkciójával környezetfüggően ugorhat egyik jelentésről a másikra ugyanazon a Power BI-beli szolgáltatás-munkaterületen vagy alkalmazáson belül. Jelentésközi részletezéssel összeköthet kettő vagy több kapcsolódó tartalommal rendelkező jelentést, és a jelentésközi kapcsolaton keresztül átadhatja a szűrési környezetet. 

A jelentésközi részletezés kezdeményezéséhez válasszon ki egy adatpontot egy *forrásjelentés* *forrásvizualizációjában*, majd válassza ki a jelentésközi **Részletezés** célt a helyi menüből. 

![Jelentésközi részletezés a Power BI-ban](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

A részletezési művelet megnyitja a *céljelentés* *céloldalát*. 

![Jelentésközi részletezés célja a Power BI Desktopban](media/desktop-cross-report-drill-through/cross-report-drill-through-01a.png)

Ez a cikk azt mutatja be, hogy miképpen állíthatja be és használhatja a jelentésrészletezést a Power BI-jelentésekhez.

> [!NOTE]
> A jelentésközi részletezést nem használhatja az egyedileg megosztott [Velem megosztott jelentésekhez](../collaborate-share/service-share-dashboards.md#share-a-dashboard-or-report). A jelentésközi részletezés használatához azon a munkaterületen kell hozzáférnie a jelentésekhez, amelynek Ön tagja.

## <a name="enable-cross-report-drillthrough"></a>Jelentésközi részletezés engedélyezése

A jelentésközi részletezés engedélyezése azzal kezdődik, hogy érvényesíti a forrás- és céljelentés adatmodelljeit. Bár az egyes jelentések sémái nem szükségszerűen ugyanazok, az átadandó mezőknek mindkét adatmodellben jelen kell lenniük. A mezők és a kapcsolódó táblák neveinek azonosaknak kell lenniük. A karakterláncoknak egyezniük kell, és számítanak a kis- és nagybetűk.

Ha például az **Amerikai államok** tábla **Állam** mezőjére vonatkozó szűrőt szeretne átadni, akkor mindkét modellben lennie kell egy **Amerikai államok** nevű táblának, azon belül pedig egy **Állam** mezőnek. Ha nem így van, a mögöttes modellben kell módosítania a mező vagy a tábla nevét. A mezők megjelenített nevének módosítása önmagában nem elég a jelentésközi részletezés megfelelő működéséhez.

A modellek érvényesítését követően engedélyezze a forrásjelentésnek a jelentésközi részletezés használatát. 

1. A Power BI Desktopban lépjen a **Fájl** > **Lehetőségek és beállítások** > **Beállítások** területre. 
1. A **Beállítások** ablak bal oldalán, az **Aktuális fájl** szakasz alján, válassza a **Jelentésbeállítások** lehetőséget. 
1. A jobb alsó sarokban, a **Jelentésközi részletezés** alatt, válassza **A jelentés vizualizációi használhatnak más jelentésekből származó részletezési célokat** lehetőséget. 
1. Kattintson az **OK** gombra. 
   
   ![Jelentésközi részletezés engedélyezése a Power BI Desktopban](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

A jelentésközi részletezést a Power BI Desktop szolgáltatásból is engedélyezheti.
1. A Power BI szolgáltatásban válassza ki azt a munkaterületet, amely a cél- és a forrásjelentéseket tartalmazza.
1. A munkaterület listán a forrásjelentés neve mellett válassza ki a **További beállítások** jelet, majd válassza a **Beállítások** lehetőséget. 
1. A **Beállítások** panel aljánál, a **Jelentésközi részletezés** alatt, jelölje be **A jelentés vizualizációi használhatnak más jelentésekből származó részletezési célokat** jelölőnégyzetet, majd kattintson a **Mentés** elemre.
   
   ![Jelentésközi részletezés engedélyezése a Power BI Desktopban](media/desktop-cross-report-drill-through/cross-report-drill-through-02a.png)

## <a name="set-up-a-cross-report-drillthrough-target"></a>Jelentésközi részletezés céljának beállítása

A jelentésközi részletezés céloldala a jelentésen belüli részletezéshez hasonló módon állítható be. A részletezés céloldalon való engedélyezése lehetővé teszi, hogy más vizualizációk célként adják meg az oldalt a részletezéshez. A részletezés egyetlen jelentésen belüli létrehozását a [Részletezés használata a Power BI Desktopban](desktop-drillthrough.md) című cikk ismerteti.

A jelentésközi részletezés célját a Power BI Desktopban vagy a Power BI szolgáltatásban állíthatja be. 
1. Szerkessze a célfájlt, és a céljelentés céloldalán válassza a **Vizualizációk** panel **Mezők** szakaszát. 
1. A **Részletezés** alatt található **Jelentésközi** csúszkát állítsa a **Be** állapotra. 
1. Húzza a részletezési célként használni kívánt mezőket a **Részletezési mezők hozzáadása** területre. Minden mezőnél válassza ki, hogy akkor engedélyezi-e a részletezést, ha a mező kategóriaként van használva, vagy akkor, ha mértékként van összesítve. 
1. Válassza ki, hogy kívánja-e az **Összes szűrő megőrzése** lehetőséget alkalmazni a vizualizációhoz. Ha nem szeretné a forrásvizualizáción alkalmazott szűrőket is átadni a részletezés célvizualizációjának, válassza a **Ki** beállítást.
   
   ![A Vizualizációk panel a Részletezési beállítások kiemelésével](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)
   
1. Ha az oldalt csak jelentésközi részletezéshez használja, törölje a vászonra automatikusan felvett **Vissza** gombot. A **Vissza** gomb csak a jelentésen belüli navigációhoz használható. 
1. A vizualizáció konfigurálása után mentse a jelentést, ha a Power BI szolgáltatásban dolgozik, illetve mentse és tegye közzé a jelentést, ha a Power BI Desktopot használja.

Ennyi az egész. A jelentések most már készen állnak a jelentésközi részletezésre. 

## <a name="use-cross-report-drillthrough"></a>Több jelentésre kiterjedő részletezés használata

A jelentésközi részletezéshez válassza ki a forrásjelentést a Power BI szolgáltatásban, majd válassza ki azt a vizualizációt, ami olyan módon használja a részletezés mezőt, ahogyan a céloldal beállítása során megadta. Kattintson a jobb gombbal egy adatpontra a vizualizáció helyi menüjének megnyitásához, válassza a **Részletezés** menüpontot, majd válassza ki a részletezés célját. A jelentésközi részletezés céljai **Oldalnév [Jelentésnév]** néven vannak formázva.

![Jelentésközi részletezés a Power BI-ban](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Az eredmények úgy jelennek meg a jelentésközi részletezés céloldalán, ahogyan a cél létrehozásakor beállította azokat. Az eredmények a részletezés beállításainak megfelelően vannak szűrve.

![Jelentésközi részletezés célja a Power BI Desktopban](media/desktop-cross-report-drill-through/cross-report-drill-through-01a.png)

> [!IMPORTANT]
> A Power BI gyorsítótárazza a jelentésközi részletezések céljait. Ha módosításokat végez, mindig frissítse az oldalt a böngészőben, ha a részletezés célja nem a várt módon jelenik meg. 

Ha a céloldal beállításánál az **Összes szűrő megőrzése** lehetőséget **Be** állapotra állítja, a forrásvizualizációból származó szűrési környezet a következőket tartalmazhatja: 

- A forrásvizualizációt befolyásoló jelentés-, oldal- és vizualizációszintű szűrők 
- A forrásvizualizációra vonatkozó keresztszűrés és keresztkiemelés 
- Az oldalon lévő szeletelők és szinkronszeletelők
- URL-paraméterek

Amikor megnyitja a részletezés céljelentését, a Power BI csak azokra a mezőkre alkalmaz szűrőket, amelyekhez a mezőnevekben és táblanevekben pontosan egyező karakterláncok tartoznak. 

A Power BI nem alkalmaz ragadós szűrőket a céljelentésből, de az Ön személyes könyvjelzőjét alkalmazza, ha rendelkezik ilyennel. Ha az Ön alapértelmezett személyes könyvjelzője például tartalmazza a *Country = US* jelentésszintű szűrőt, akkor a Power BI ezt a szűrőt alkalmazza a forrásvizualizációból származó szűrési környezet alkalmazása előtt. 

Jelentésközi részletezéshez a Power BI átadja a szűrési környezetet a céljelentés standard oldalainak. A Power BI nem adja át a szűrési környezetet az elemleírás-oldalaknak, ezek ugyanis az elemleírást meghívó forrásvizualizáció alapján vannak szűrve.

Ha a jelentésközi részletezési művelet után vissza szeretne térni a forrásjelentéshez, használja a böngésző **Vissza** gombját. 

## <a name="next-steps"></a>További lépések

Az alábbi cikkeket is érdekesnek találhatja:

- [Szeletelők a Power BI-ban](../visuals/power-bi-visualization-slicers.md)
- [Részletezés használata a Power BI Desktopban](desktop-drillthrough.md)
