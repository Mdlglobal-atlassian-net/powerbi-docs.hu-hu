---
title: A numerikustartomány-szeletelő használata a Power BI Desktopban
description: Megismerheti, hogyan használhatja a szeletelőt a numerikus tartományokra való korlátozásra a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/02/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 68467894850248d6acb841dc2ed651f595f19b95
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61363681"
---
# <a name="use-the-numeric-range-slicer-in-power-bi-desktop"></a>A numerikustartomány-szeletelő használata a Power BI Desktopban
A **numerikustartomány-szeletelővel** számos különféle szűrőt alkalmazhat az adatmodellek bármely numerikus oszlopára. Választhat, hogy számok **között**, egy számnál **kisebb vagy egyenlő** vagy egy számnál **nagyobb vagy egyenlő** értékekre szűr. Egyszerűnek tűnik, de nagyon hatékony módja az adatok szűrésének.

![Vizualizáció numerikustartomány-szeletelővel](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-0.png)

## <a name="using-the-numeric-range-slicer"></a>A numerikustartomány-szeletelő használata
A numerikustartomány-szeletelőt bármely más szeletelőhöz hasonlóan használhatja. Egyszerűen hozzon létre egy **szeletelő** vizualizációt a jelentéshez, majd válasszon ki egy numerikus értéket a **Mező** értékeként. A következő képen a *LineTotal* (Sor összege) mező van kijelölve.

![Numerikustartomány-szeletelő létrehozása](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-1-create.png)

Kattintson a lefelé mutató nyilat ábrázoló hivatkozásra a **numerikustartomány-szeletelő** jobb felső sarkában, és megjelenik egy menü.

![A numerikustartomány-szeletelő menüje](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-2-between.png)

Numerikus tartományok esetében a következő három lehetőség közül választhat:

* Között
* Kisebb vagy egyenlő
* Nagyobb vagy egyenlő

Amikor a **Között** lehetőséget választja a menüből, megjelenik egy csúszka, és a számok közé eső numerikus értékekre szűrhet. A csúszka használata mellett a mezőkre kattinthat és be is írhatja az értékeket. Ez a megoldás akkor praktikus, ha adott egész számok alapján szeretne szeletelni, de a szeletelősáv mozgatásának részletessége megnehezíti a pontos szám kiválasztását.

A következő képen a jelentésoldal a 2500,00 és 6000,00 közötti tartományban lévő *LineTotal* értékekre van szűrve.

![Numerikustartomány-szeletelő a Két érték között beállítással](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-3-between-range.png)

Amikor a **Kisebb vagy egyenlő** lehetőséget választja, eltűnik a csúszkasáv bal oldali (legalacsonyabb értékhez tartozó) fogója, és csak a csúszka felső határát módosíthatjuk. A következő képen az 5928,19 maximális értékre állítjuk a csúszkasávot.

![Numerikustartomány-szeletelő a Kisebb, mint beállítással](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-4-less-than.png)

Végül ha a **Nagyobb vagy egyenlő** lehetőséget választjuk, a csúszkasáv jobb oldali (legmagasabb értékhez tartozó) fogója tűnik el, és az alacsonyabb értéket módosíthatjuk a következő képen látható módon. Most csak a 4902,99-nél nagyobb vagy azzal egyenlő *LineTotal* értékek jelennek meg a jelentésoldal vizualizációiban.

![Numerikustartomány-szeletelő a Nagyobb, mint beállítással](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-5-greater-than.png)

## <a name="snap-to-whole-numbers-with-the-numeric-range-slicer"></a>Egész számhoz illeszkedés a numerikustartomány-szeletelőnél

A numerikustartomány-szeletelő egész számokhoz illeszkedik, ha a mögöttes mező adattípusa **Egész szám**. Ezzel lehetővé válik, hogy a szeletelőn egyszerűen válasszon ki egész számokat. A **Tizedes tört** típusú mezőkkel törtszámokat írhat be. A szövegmezőre alkalmazott formázás megegyezik a mező formázásával, bár beírhat vagy kijelölhet pontosabb számokat.

## <a name="display-formatting-with-the-date-range-slicer"></a>Formázás megjelenítése a dátumtartomány-szeletelővel

Amikor egy időtartományt jelenít meg vagy állít be szeletelő használatával, a dátum mindig a **Rövid dátum** formátumban jelenik meg, a felhasználó böngészőjének vagy operációs rendszerének területi beállítása alapján. A mögöttes adatok vagy modell adattípus-beállításaitól függetlenül ez lesz a megjelenítési formátum. 

A mögöttes adattípus lehet például hosszú dátumformátumú (például *éééé. HHHH n, nnnn*, amely más vizualizációkban vagy más körülmények esetén a *2001. március 14, szerda* formában jelenne meg), a dátumtartomány-szeletelőben azonban ez a dátum *03/14/2001* lesz.

A szeletelőben a **Rövid dátum** formátum használata biztosítja, hogy a sztring hossza ne változzon, és elférjen a szeletelőben. 


## <a name="limitations-and-considerations"></a>Korlátozások és szempontok
Jelenleg a következő korlátozások és szempontok érvényesek a **numerikustartomány-szeletelőre**:

* A **numerikustartomány-szeletelő** jelenleg az adatokban lévő összes alapul szolgáló sorra szűr, nem az összesített értékekre. Ha például egy *Értékesítési összeg* mezőt használ, akkor az *Értékesítési összegen* alapuló összes tranzakcióra szűr, nem a vizualizáció egyes adatpontjai *Értékesítési összegének* összegére.
* A mértékekkel jelenleg nem működik.
* A numerikus szeletelők szövegmezőibe bármilyen számot beírhat, akkor is, ha az kívül esik mögöttes oszlop értéktartományán. Így beállíthat szűrőket, ha tudja, hogy az adatok változni fognak.
