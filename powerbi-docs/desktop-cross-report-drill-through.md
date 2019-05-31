---
title: Kereszt-jelentés részletezés használata a Power BI Desktopban
description: Ismerje meg, hogyan egy jelentés áthatoló részletezést végezni egy másik, a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/08/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 45a7cdd3c7b5324f3d618eaba4bdb3968a9549a5
ms.sourcegitcommit: 8bf2419b7cb4bf95fc975d07a329b78db5b19f81
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66375188"
---
# <a name="use-cross-report-drillthrough-in-power-bi-desktop"></a>Kereszt-jelentés részletezés használata a Power BI Desktopban

A Power BI Desktopban cross-jelentés részletező szolgáltatással is kontextusban ugorhat egy jelentésből egy másik jelentés. Ez igaz, mindaddig, amíg a jelentéseket lehet ugyanabban a munkaterület vagy alkalmazást a Microsoft Power BI szolgáltatásban. Kereszt-jelentés részletezés használata, a két vagy több olyan jelentéseket, amely rendelkezik a kapcsolódó tartalom, és a szűrőkörnyezet együtt a kereszt-jelentés kapcsolat át. Ebből a cikkből megtudhatja, hogyan állítható be a kereszt-jelentés részletező Power BI-jelentések, és milyen felhasználói élmény, amikor a maguk a kereszt-jelentés részletezés használata.

![Képernyőfelvétel: a Power BI Desktop részletezési lehetőség](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Az alábbi definíciókat is fontos tudni, mielőtt megkezdjük a beállításával és használatával határokon-jelentés részletezési:

* **A forrás visual:** A vizualizációt, amely meghívja az áthatoló részletezési művelet a vizuális környezetet menü használatával.
* **Forrásjelentés:** A jelentés, amely tartalmazza a kereszt-jelentés részletező a forrásként használt vizualizációra.
* **Cél lap:** Az oldal, amely a felhasználó hajtanak végre a drillthrough művelet indítása után.
* **Cél jelentés:** A jelentés, amely tartalmazza a kereszt-jelentés részletezési cél lapját.

## <a name="enable-cross-report-drillthrough"></a>Kereszt-jelentés részletezés engedélyezése

Ahhoz, hogy egy több-a jelentés részletező célja egy jelentésben, engedélyezni kell a funkciót, hogy a jelentés a **beállítások** ablak. Lépjen a **fájl** > **lehetőségek és beállítások** > **beállítások**, majd lépjen **beállítások jelentés** közelében a a bal oldalon található az oldal alján.

Válassza ki a **lehetővé teszi a Vizualizációk a jelentés használatához a más jelentésekből részletezési cél** jelölőnégyzetet, a következő képen látható módon.

![Képernyőkép a beállítások ablakról, amelyen kiemelve jelentésbeállítások](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

Kereszt-jelentés részletezés engedélyezve van.

## <a name="set-up-cross-report-drillthrough"></a>Kereszt-jelentés a részletezés beállítása

Kereszt-jelentés a részletezés beállítása nagyon hasonlít egy jelentésen belül a részletezés beállítása. Részletezés engedélyezve van a cél lapon lehetővé teszi az egyéb Vizualizációk részletezési engedélyezett oldalán lehetőséget. A lépéseket részletezés belül egyetlen jelentés létrehozásához, lásd: [részletezés használata a Power BI Desktopban](desktop-drillthrough.md).

A telepítés megkezdéséhez szüksége néhány kezdeti lépéseket:

* Állítsa be a részletezési cél oldal, amely ezután elérhető lesz a munkaterület vagy az alkalmazás más jelentések.
* Lehetővé teszi egy jelentés kívül a saját jelentést a részletező lapok megjelenítéséhez.

A részletezés beállítások keresése a **mezők** szakaszában a **Vizualizációk** panelen, amint az alábbi képen látható.

![Képernyőkép a megjelenítések ablaktáblán, a részletezési lehetőségeket vannak kiemelve](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

A részletezés oldal engedélyezésének első lépéseként, hogy ellenőrizze az adatmodellek a forrás- és jelentésekhez. Győződjön meg arról, hogy: 

* A mezők átadni kívánt mindkét adatmodellek szerepel.
* A mezők nevét, és a táblák, amelyhez tartoznak, nevének azonosak (a karakterláncokat is egyezniük kell, és a kis-és nagybetűket).

Például, ha a mező egy szűrő átadni kívánt *ország* a táblán belül *földrajzi*, mindkét modellt rendelkeznie kell egy *földrajzi* táblát, és a egy *ország* mezőt a táblán belül. Ha nem, akkor frissítenie kell a mező nevét vagy a táblázat neve az alapul szolgáló modellből. Egyszerűen csak a megjelenített nevét, a mezők frissítése nem fog megfelelően működni a kereszt-jelentés részletező. (Ne feledje, hogy az egyes jelentések a sémák nem egyezhet meg egymással.)

A telepítő használatának megkezdéséhez szüksége, a cél lap az készen álljon. A Power BI Desktopban, lépjen a lapra, és győződjön meg arról, hogy a **Cross-jelentés** részletezési váltógomb értékre van állítva **a**. 

![A beállítandó Cross-jelentés váltó képernyőképe](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

Ezután húzza a vászonra a részletezési célként használni kívánt mezőket. Válassza ki, hogy a mező egy kategóriaként van használatban, vagy például egy mérték foglalja össze. Ezen a ponton kiválaszthatja, hogy le kívánja tiltani a **az összes szűrő megőrzése** be-vagy kikapcsolása a vizualizációhoz. Ha nem kívánja átadni a többi alkalmazott szűrők a forrás-visual a a célként megadott részletezési visual, válassza ki a **ki**.

> [!NOTE]
> Ha használja a lap csak a részletezési cross-jelentés, törölnie kell a **vissza** automatikusan hozzáadott gombra. A **vissza** gomb csak akkor működik, a nagivation belül egyetlen jelentést. 

Miután konfigurálta a vizualizációt, győződjön meg arról, mentse a jelentést, ha Ön a Power BI szolgáltatásban, vagy mentse és tegye közzé a jelentést a Power BI Desktop használata.

Az előző szakaszban leírt cross-jelentés részletezés engedélyezése a Power BI Desktop (az a **beállítások** ablakban). Ha a Power BI szolgáltatás használatával hozza létre a kereszt-jelentés részletezési cél kell cross-jelentés részletezés engedélyezése: 

1. Válassza ki a munkaterületet, amelyben a Céljelentés és a forrásjelentés található.
2. Válassza ki **jelentések**.
3. Válassza ki a **beállítások** a forrásjelentés ikonjára.
4. Ellenőrizze, hogy a kereszt-jelentés részletező váltógomb **a**.
5. A jelentés mentéséhez.

Ennyi az egész. A jelentés elkészült a kereszt-jelentés részletező élmény. 

A következő szakaszban hogy vessen egy pillantást a felhasználói élményt, a felhasználó szemszögéből.

## <a name="cross-report-drillthrough-experience"></a>Kereszt-jelentés részletező élmény

A kereszt-jelentés részletező élmény a jelentések konfigurálásakor helyezheti a funkció használatához.

Válassza ki a forrás jelentést a Power BI szolgáltatásban, és válassza ki a cél lap beállításakor megadott módon mezőket használó vizualizációt. Kattintson a jobb gombbal egy adatpontra, nyissa meg a vizuális környezetet menüt, és válassza ki **részletezési**.

![A Power BI szolgáltatásban lévő forrásjelentéssel részletezési kiemelésével – képernyőfelvétel](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Ahogy, állítsa be őket a cél létrehozásakor ekkor megjelenik a cél közötti – jelentés részletezési oldalon, az eredményeket. Az eredményeket a részletezési beállítások szerint vannak szűrve.

> [!IMPORTANT]
> A Power BI gyorsítótárazza a kereszt-jelentés részletezési cél. Ha módosít, mindenképpen frissítse a böngészőt, ha nem látja a várt módon a részletezési célokat. 

Az alábbi módon formázott Cross-jelentés célok: 

`Target Page Name [Target Report Name]`

Miután kiválasztotta a cél lap, amelyhez szeretne áthatoló részletezést, a Power BI az adott oldalra kerül. A szűrőkörnyezet a cél lap beállításai alapján továbbítja. 

A szűrőkörnyezet a forrásvizualizációból tartozhatnak a következők: 

* Jelentés lap és ez hatással lenne a forrásként használt vizualizációra vizualizációszint szűrői. 
* Keresztszűrés és keresztkiemelés, amelyek befolyásolják a forrásként használt vizualizációra. 
* Szeletelők az oldal és a szeletelők szinkronizálása.
* URL-paraméter.

A célként megadott jelentést, a részletezés megjelenni, amikor a Power bi-ban csak érvényes szűrők a mezőket, amelynek talál pontos karakterlánc megfelel a mező nevét és a tábla neve. A Power BI kiemelt szűrők nem vonatkozik a cél a jelentésből. Az alapértelmezett személyes könyvjelző azonban azt, alkalmazni, ha van ilyen. Például, ha az alapértelmezett személyes könyvjelző tartalmaz egyetlen jelentésszintű szűrő a *ország = USA*, Power bi-ban a szűrő alkalmazása először a forrásvizualizációból a szűrőkörnyezet alkalmazása előtt. 

Kereszt-jelentés részletezést, a Power BI továbbítja a szűrőkörnyezet a céljelentésben levő összes normál oldalakat. A Power BI fennakadt a szűrőkörnyezet, elemleírás-oldalt, a, mert a forrás, az elemleírás meghívó visual elemleírás-oldalt alapján szűrve.

Ha szeretné a kereszt-jelentés áthatoló részletezési művelet után térjen vissza a forrásjelentés, használja a böngésző **vissza** gombra. 

## <a name="next-steps"></a>Következő lépések

Az alábbi cikkeket is érdekesnek találhatja:

* [Szeletelők használata a Power BI Desktopban](visuals/power-bi-visualization-slicers.md)
* [Részletezés használata a Power BI Desktopban](desktop-drillthrough.md)

