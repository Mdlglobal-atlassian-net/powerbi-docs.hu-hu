---
title: Bevezetés a jelentésvizualizációk formázásába
description: Bevezetés a jelentésvizualizációk formázási beállításainak használatába
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/30/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 2433f030f00ec8cd337d97c4402b83ed6c4c5a00
ms.sourcegitcommit: 64a270362c60581a385af7fbc31394e3ebcaca41
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/31/2020
ms.locfileid: "76895231"
---
# <a name="getting-started-with-the-formatting-pane"></a>A Formázás panel bemutatása
Ha egy jelentéshez szerkesztési engedélyekkel rendelkezik, számos formázási lehetőséget érhet el. A Power BI-jelentésekben módosíthatja az adatsorozatok és adatpontok színét, sőt akár a vizualizációk hátterét is. Megváltoztathatja az X és az Y tengely megjelenését. Emellett a vizualizációk, alakzatok és címek betűtípus-tulajdonságait is beállíthatja. A Power BI-jelentések megjelenését teljes körűen vezérelheti.

Első lépésként nyisson meg egy jelentést a Power BI Desktopban vagy a Power BI szolgáltatásban. Mindkettő szinte azonos formázási beállításokat kínál. Ha a Power BI szolgáltatásban nyit meg jelentést, mindenképpen válassza a menüsáv **Szerkesztés** elemét. 

![Menüsor a Szerkesztés lehetőséggel](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-edit.png)

Ha egy jelentést szerkeszt, és ki van jelölve egy vizualizáció, megjelenik a **Megjelenítések** panel. Ezen a panelen módosíthatja a vizualizációkat. Közvetlenül a **Megjelenítések** panel alatt három ikon látható: a **Mezők** (sávok), a **Formátum** (festőhenger), és az **Analitika** (nagyító). Az alábbi ábrán a **Mezők** ikon van kijelölve, amit az ikon alatti sárga sáv jelez.

![](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-format.png)

Ha a **Formátum** ikonra kattint, az alatta lévő terület a jelenleg kijelölt vizualizációhoz elérhető testreszabásokat jeleníti meg.  

![](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-format-selected.png)

Az egyes vizualizációk számos elemét testre szabhatja. Az elérhető lehetőségek a választott vizualizációtól függenek. Néhány elérhető lehetőség:

* Jelmagyarázat
* X tengely
* Y tengely
* Adatszínek
* Adatfeliratok
* Alakzatok
* Rajzterület
* Cím
* Háttér
* Zárolási helyzet
* Szegély
* Elemleírások
* Vizualizációs fejlécek
* Alakzatok
* Pozíció    
és további lehetőségek.


> [!NOTE]
>  
> Ezen elemek nem mindegyike látható az összes vizualizációs típus esetében. A választott vizualizáció hatással lesz az elérhető testreszabásokra; például tortadiagram kijelölése esetén nem látható X tengely, mivel a tortadiagramoknak nincs X tengelye.

Vegye figyelembe azt is, hogy ha még nincs vizualizáció kijelölve, akkor az ikonok helyett a **Szűrők** elem jelenik meg, amely lehetővé teszi szűrők alkalmazását az oldalon lévő összes vizualizációra.

A formázási beállításokat úgy ismerheti meg a legjobban, ha kipróbálja őket. A módosításait bármikor visszavonhatja, vagy visszaállhat az alapértelmezett beállításokra. Nagyon sok lehetőség érhető el, és a lista folyamatosan bővül. Egyetlen cikkben nem lehet leírni az összes formázási beállítást. Kezdésképpen azonban tekintsünk meg néhányat közösen. 

1. A vizualizáció színeinek módosítása   
2. Stílus beállítása    
3. Értéktengely tulajdonságainak módosítása    
4. Adatfeliratok hozzáadása    




## <a name="working-with-colors"></a>Színek használata

Vegyük végig a vizualizáció színeinek testreszabásához szükséges lépéseket.

1. Aktiváljon egy vizualizációt annak kijelölésével.

2. A festőhenger ikonra kattintva nyissa meg a Formázás lapot. A Formázás lap megjeleníti a kijelölt vizualizációhoz elérhető összes formázási elemet.

    ![Diagram a kijelölt Formázás panellel](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-formatting.png)

3. Az **Adatszínek** elemet kijelölve jelenítse meg a rendelkezésre álló testreszabásokat.  

    ![Diagram a megnyitott Formázás panellel és a kibontott Adatszínekkel](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-data-colors.png)

4. Módosítsa **Az összes megjelenítése** lehetőséget Bekapcsolva értékre, majd jelöljön ki különböző színeket az oszlopokhoz.

    ![Diagram a néhány oszlopra alkalmazott új színekkel](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-change-colors.png)

Alább néhány tippet talál a színek használatával kapcsolatosan. Az alábbi listán szereplő számok a következő képernyőn is megjelennek, jelezve, hol érheti el vagy módosíthatja ezeket a hasznos elemeket.

1. Nem megfelelő a szín? Semmi probléma, csak válassza a **Visszaállítás alapértelmezettre** lehetőséget, és a kijelölés visszaáll az alapértelmezett beállításra. 

2. Nem megfelelők a módosított színek? Válassza a **Visszaállítás alapértelmezettre** lehetőséget az **Adatok színe** szakaszban, és a színek visszaállnak az alapértelmezett beállításokra. 

3. Szeretne egy olyan színt használni, amely nem jelenik a palettán? Egyszerűen válassza az **Egyéni szín** elemet, és válasszon a színspektrumból.  

   ![Adatok színe szakasz a megnyitott színpalettával](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-color-extras.png)

Nincs elragadtatva az előbb végzett módosítástól? A szokásos **CTRL + Z** billentyűkombinációval visszavonhatja.

## <a name="applying-a-style-to-a-table"></a>Stílus alkalmazása egy táblázatra
Néhány Power BI-vizualizáció esetén elérhető a **Stílus** beállítás. Egyetlen kattintással egyszerre alkalmazhat több formázási beállítást a vizualizációjára. 

1. Jelöljön ki egy táblázatot vagy mátrixot, hogy az aktív legyen.   
1. Nyissa meg a Formázás panelt, és válassza ki a **Stílus** elemet.

   ![Stílus kiválasztása a Formázás lapon](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-style.png)


1. A legördülő listából válasszon ki egy stílust. 

   ![Ugyanaz a tábla félkövér fejlécű, feltűnő sorokkal](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-style-flashy.png)

A stílus alkalmazása után is módosíthatja a vizualizáció formázási tulajdonságait, például a színeket.


## <a name="changing-axis-properties"></a>Tengely tulajdonságainak módosítása

Gyakran érdemes módosítani az X vagy az Y tengelyt. A színek használatához hasonlóan a módosítani kívánt tengely mellett balra látható lefelé mutató nyíl ikonra kattintva módosíthatja, a következő ábrán látható módon.  
![](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-y-axis.png)

Az alábbi példában az Y tengelyt a következőképpen formáztuk:
- a címkéket áthelyeztük a vizualizáció jobb oldalára

- a kezdő értéket nullára módosítottuk

- a címke szövegszínét feketére módosítottuk

- a címke betűméretét 12-es méretre módosítottuk

- címet adtunk az Y tengelyhez


    ![ugyanaz az oszlopdiagram az Y tengely számos formázása után](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-axis-changes.png)

Teljesen eltávolíthatja a tengelyek feliratait, ehhez kattintson az **X tengely** vagy az **Y tengely** melletti választógombra. A tengelycímek be- és kikapcsolására is lehetősége van a **Cím** melletti választógomb bejelölésével.  



## <a name="adding-data-labels"></a>Adatfeliratok hozzáadása    

Mielőtt elkezdené önállóan is felfedezni ezeket, íme még egy példa.  Adjunk hozzá adatfeliratokat egy területdiagramhoz. 

Ez az *„előtte”* kép. 

![formázatlan területdiagram](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-area-chart.png)


Ez pedig az *„utána”* kép.

![formázott területdiagram](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-data-labels.png)

Kiválasztottuk a vizualizációt, hogy aktív legyen, és megnyitottuk a Formázás lapot.  Kiválasztottuk az **Adatfeliratok** lehetőséget, és bekapcsoltuk. Ezután megnöveltük a betűméretet 12-esre, a betűcsaládot Arial Blackre módosítottuk, a **Háttér megjelenítése** beállítást pedig fehér, 5%-os átlátszóság értékkel bekapcsoltuk.

Ez csak néhány példa az elérhető formázási lehetőségek közül. Nyisson meg egy jelentést Szerkesztési módban, és ismerkedjen meg a Formázási panellel, hogy gyönyörű és informatív vizualizációkat hozhasson létre.

## <a name="next-steps"></a>Következő lépések
További információkat a következő cikkekben talál:  

* [Tippek és trükkök a színformázáshoz a Power BI-ban](service-tips-and-tricks-for-color-formatting.md)  
* [Táblázatok feltételes formázása](../desktop-conditional-table-formatting.md)

