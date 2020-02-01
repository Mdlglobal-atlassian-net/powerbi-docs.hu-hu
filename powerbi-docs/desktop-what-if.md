---
title: Lehetőségelemzési paraméterek használata változók megjelenítésére
description: Saját lehetőségelemzési változó létrehozása változók elképzeléséhez és megjelenítéséhez Power BI-jelentésekben
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/21/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 8a72bc43bcceae6e676728934ceec81c8cb27d04
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/23/2020
ms.locfileid: "76539413"
---
# <a name="create-and-use-what-if-parameters-to-visualize-variables-in-power-bi-desktop"></a>Lehetőségelemzési paraméter létrehozása és használata változók vizualizációjához a Power BI Desktopban

A *Power BI Desktop* 2018. augusztusi kiadásától kezdve létrehozhat *lehetőségelemzési* változókat a jelentésekhez, szeletelőként dolgozhat a változókkal, valamint megjelenítheti és számszerűsítheti a jelentésekben szereplő különböző kulcsértékeket.

![Új paraméter beállítása](media/desktop-what-if/what-if_01.png)

*Lehetőségelemzési* paramétert a Power BI Desktop **Modellezés** lapján hozhat létre. Ennek kiválasztáskor megjelenik egy párbeszédpanel, ahol beállíthatja a paramétert.

## <a name="creating-a-what-if-parameter"></a>Lehetőségelemzési paraméter létrehozása

Lehetőségelemzési paraméter létrehozásához válassza a Power BI Desktop **Modellezés** lapjának **Új paraméter** elemét. Az alábbi képen létrehoztunk egy *Kedvezmény százaléka* nevű paramétert, és az adattípusát **Tizedes törtre** állítottuk. A **minimális** érték nulla. A **maximum** 0,50 (50 százalék). A **Növekményt** 0,05-re, vagyis 5%-ra állítottuk. Ennyit fog a paraméter módosítani, ha egy jelentésben dolgozik vele.

![Lehetőségelemzési paraméterértékek](media/desktop-what-if/what-if_02.png)

> [!NOTE]
> Tizedes törtek esetén mindig írja ki a tizedesjel előtti nullát (például 0,50 a ,50 alak helyett). Ellenkező esetben a szám nem lesz érvényesítve, és az **OK** gomb nem válaszható ki.
> 
> 

Kényelmi funkcióként a **Szeletelő hozzáadása az oldalhoz** jelölőnégyzet automatikusan elhelyez egy szeletelőt a lehetőségelemzési paraméterrel a jelentés aktuális oldalán.

![Új szeletelő az aktuális jelentésoldalon](media/desktop-what-if/what-if_03.png)

Egy Lehetőségelemzési paraméter létrehozása a paraméter mellet egy mértéket is létrehoz, amely a lehetőségelemzési paraméter aktuális értékének megjelenítésére használható.

![Lehetőségelemzési paraméterhez létrehozott mérték](media/desktop-what-if/what-if_04.png)

Érdemes és hasznos megjegyezni, hogy miután létrehozott egy lehetőségelemzési paramétert, a paraméter és a mérték is a modell része lesz. Ezért elérhetők a jelentésen keresztül, és a jelentés egyéb oldalain is használhatók. Emellett, mivel ezek a modell részei, a szeletelőt törölheti is a jelentésoldalról. Ha vissza szeretné állítani, csak húzza át a lehetőségelemzési paramétert a **Mezők** listájából a vászonra, majd állítsa át szeletelőre a vizualizációt.

## <a name="using-a-what-if-parameter"></a>Lehetőségelemzési paraméter használata

Hozzunk létre egy, a lehetőségelemzési paraméter használatát bemutató, egyszerű példát. A lehetőségelemzési paramétert már létrehoztuk az előző szakaszban. Most egy új mérték létrehozásával vesszük használatba, amelynek az értéke a csúszka helyzetének megfelelően változik.

![Paraméterrel használt új mérték felvétele](media/desktop-what-if/what-if_05.png)

Az új mérték egyszerűen a teljes értékesítés mennyisége lesz, a kedvezménnyel együtt. Összetett és érdekes mértékeket is létrehozhat, amelyek lehetővé teszik a jelentések felhasználói számára, hogy megjelenítsék a lehetőségelemzési paraméter változóját. Például létrehozhat egy jelentést, amely lehetővé teszi az értékesítés területén dolgozó személyeknek a kompenzáció megtekintését, ha elérnek bizonyos értékesítési célokat vagy százalékokat, vagy megtekinthetik a megnövekedett értékesítés nagyobb kedvezményekre gyakorolt hatását.

Írja be a mérték képletét a képletsávba, és adja a képletnek az *Értékesítés kedvezmény után* nevet.

![Az Értékesítés kedvezmény után képlet definíciója](media/desktop-what-if/what-if_06.png)

Ezután létrehozunk egy oszlopvizualizációt **OrderDate** névvel a tengelyen, valamint a **SalesAmount** és a most létrehozott **Értékesítés kedvezmény után** mértékkel mint értékekkel.

![A SalesAmount vizualizációja](media/desktop-what-if/what-if_07.png)

Ezután ahogy mozgatjuk a csúszkát, láthatjuk, hogy az **Értékesítés kedvezmény után** oszlop a kedvezményes értékesítések mennyiségét tükrözi.

![Vizualizációval használt csúszka](media/desktop-what-if/what-if_08.png)

Ennyi az egész! Lehetőségelemzési paraméterek sokféle helyzetben használhatók. Ilyen paraméterekkel lehetővé teheti a jelentések felhasználói számára, hogy a jelentésekben létrehozott különböző forgatókönyvekkel dolgozzanak.
