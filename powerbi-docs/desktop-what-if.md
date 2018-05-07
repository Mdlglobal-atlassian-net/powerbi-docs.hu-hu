---
title: Változók vizualizációja lehetőségelemzési paraméterek használatával a Power BI Desktopban
description: Létrehozhatja a saját Lehetőségelemzési változóját, hogy elképzelhesse és megjeleníthesse a változókat a Power BI-jelentésekben
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
LocalizationGroup: Create reports
ms.openlocfilehash: 5c6aa2639b8991cd7a9e1527c780bdbe21ad64b9
ms.sourcegitcommit: 312390f18b99de1123bf7a7674c6dffa8088529f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/16/2018
---
# <a name="create-and-use-a-what-if-parameter-to-visualize-variables-in-power-bi-desktop"></a>Lehetőségelemzési paraméter létrehozása és használata változók vizualizációjához a Power BI Desktopban
A **Power BI Desktop** 2017 augusztusi kiadásától kezdve létrehozhat **Lehetőségelemzési** változókat a jelentésekhez, szeletelőként dolgozhat a változókkal, és így a jelentésekben szereplő különböző kulcsértékeket jeleníthet meg és számszerűsíthet.

![](media/desktop-what-if/what-if_01.png)

A **Lehetőségelemzési** paraméter a **Power BI Desktop** **Modellezés** lapján található. A kiválasztáskor megjelenik egy párbeszédpanel, ahol beállíthatja a paramétert.

## <a name="creating-a-what-if-parameter"></a>Lehetőségelemzési paraméter létrehozása
**Lehetőségelemzési** paraméter létrehozásához kattintson a **Lehetőségelemzés** gombra a **Power BI Desktop** **Modellezés** lapján. Az alábbi képen létrehoztunk egy *Kedvezmény százaléka* nevű paramétert, és az adattípusát *Tizedes törtre* állítottuk. A *Minimális* érték nulla, a *Maximális* érték 0,50 (ötven százalék). A *Növekményt* 0,05-re, vagyis 5%-ra állítottuk. Ennyit fog a paraméter módosítani, ha egy jelentésben dolgozik vele.

![](media/desktop-what-if/what-if_02.png)

> [!NOTE]
> Tizedes törtek esetében ügyeljen arra, hogy nullával kezdje a számot, például 0,50 szerepeljen ,50 helyett. Ellenkező esetben a szám nem lesz érvényesítve, és az **OK** gomb nem válaszható ki.
> 
> 

Kényelmi funkcióként a **Szeletelő hozzáadása az oldalhoz** jelölőnégyzet automatikusan elhelyez egy szeletelőt a **Lehetőségelemzési** paraméterrel a jelentés aktuális oldalán.

![](media/desktop-what-if/what-if_03.png)

Továbbá a paraméter létrehozása mellett egy **Lehetőségelemzési** paraméter létrehozása egy mértéket is létrehoz, amely a **Lehetőségelemzési** paraméter aktuális értékének megjelenítésére használható.

![](media/desktop-what-if/what-if_04.png)

Érdemes és hasznos megjegyezni, hogy miután létrehozott egy **Lehetőségelemzési** paramétert, a paraméter és a mérték is a modell része lesz. Ezért elérhetők a jelentésen keresztül, és a jelentés egyéb oldalain is használhatók. Mivel a modell részei, törölheti a szeletelőt a jelentés oldaláról, és ha vissza szeretné kapni, fogja meg a **Lehetőségelemzési** paramétert a **Mezők** listájából, és húzza a vászonra (majd módosítsa a vizualizációt szeletelőre), így egyszerűen visszahelyezheti a paramétert a jelentésbe.

## <a name="using-a-what-if-parameter"></a>Lehetőségelemzési paraméter használata
Hozzunk létre egy, a **Lehetőségelemzési** paraméter használatáról szóló, egyszerű példát. Az előző szakaszban létrehoztunk egy **Lehetőségelemzési** paramétert, most pedig használatba állítjuk egy új mérték létrehozásával, amelynek az értéke egy csúszkával állítható. Ehhez létrehozunk egy új mértéket.

![](media/desktop-what-if/what-if_05.png)

Az új mérték egyszerűen a teljes értékesítés mennyisége lesz, a kedvezménnyel együtt. Természetesen összetett és érdekes mértékeket is létrehozhat, amelyek lehetővé teszik a jelentések felhasználói számára, hogy megjelenítsék a **Lehetőségelemzési** paraméter változóit. Például létrehozhat egy jelentést, amely lehetővé teszi az értékesítés területén dolgozó személyeknek a kompenzáció megtekintését, ha elérnek bizonyos értékesítési célokat vagy százalékokat, vagy megtekintsék a megnövekedett értékesítés nagyobb kedvezményekre gyakorolt hatását.

Miután beírtuk a mérték képletét a képletsávba, és az **Értékesítés kedvezmény után** nevet adtuk neki, megjelennek az eredmények:

![](media/desktop-what-if/what-if_06.png)

Ezután létrehozunk egy oszlopvizualizációt *OrderDate* névvel a tengelyen, valamint a *SalesAmount* és a most létrehozott *Értékesítés kedvezmény után* mértékkel mint értékekkel.

![](media/desktop-what-if/what-if_07.png)

Ezután ahogy mozgatjuk a csúszkát, láthatjuk, hogy az *Értékesítés kedvezmény után* oszlop a kedvezményes értékesítések mennyiségét tükrözi.

![](media/desktop-what-if/what-if_08.png)

Ennyi az egész! Bármilyen esetben használhatja a **Lehetőségelemzési** paramétereket, így lehetővé teheti a jelentések felhasználói számára, hogy a jelentésekben létrehozott különböző forgatókönyvekkel dolgozzanak.

