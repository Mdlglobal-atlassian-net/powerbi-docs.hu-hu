---
title: A numerikustartomány-szeletelő használata a Power BI-ban
description: Útmutató numerikus tartományokra szűkítő szeletelő használatához a Power BI-ban.
author: davidiseminger
ms.reviewer: ''
featuredvideoid: zIZPA0UrJyA
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/06/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: bd5f937154edf9f8b6a86fb7f53690943a7f3a53
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "81006641"
---
# <a name="use-the-numeric-range-slicer-in-power-bi"></a>A numerikustartomány-szeletelő használata a Power BI-ban

[!INCLUDE [applies-to](includes/applies-to.md)] [!INCLUDE [yes-desktop](includes/yes-desktop.md)] [!INCLUDE [yes-service](includes/yes-service.md)]

A numerikustartomány-szeletelővel számos különféle szűrőt alkalmazhat az adatmodellek bármely numerikus oszlopára. Numerikus adatok háromféleképpen szűrhetők: két szám közötti, egy számnál kisebb vagy egyenlő vagy egy számnál nagyobb vagy egyenlő értékekre szűrhet. Ezzel az egyszerű technikával hatékonyan szűrheti az adatokat.

![Vizualizáció numerikustartomány-szeletelővel](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-0.png)

## <a name="video"></a>Videó

Ebben a videóban Will lépésenként bemutatja a numerikustartomány-szeletelők létrehozását.

> [!NOTE]
> Ez a videó a Power BI Desktop egy régebbi verzióját használja.

<iframe width="560" height="315" src="https://www.youtube.com/embed/zIZPA0UrJyA" frameborder="0" allowfullscreen></iframe> 


## <a name="add-a-numeric-range-slicer"></a>Numerikustartomány-szeletelő hozzáadása

A numerikustartomány-szeletelőt bármely más szeletelőhöz hasonlóan használhatja. Csak hozzon létre egy **Szeletelő** vizualizációt a jelentéshez, majd válasszon ki egy numerikus értéket a **Mező** értékeként. A következő képen a **LineTotal** (Sor összege) mezőt jelöltük ki.

![Numerikustartomány-szeletelő létrehozása](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-1-create.png)

Kattintson a lefelé mutató nyílra a numerikustartomány-szeletelő jobb felső sarkában, és megjelenik egy menü.

![A numerikustartomány-szeletelő menüje](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-2-between.png)

Numerikus tartományok esetében a következő három lehetőség közül választhat:

* **Között**
* **Kisebb vagy egyenlő**
* **Nagyobb vagy egyenlő**

Ha a menüből a **Között** lehetőséget választja, megjelenik egy csúszka. A csúszka használatával jelölheti ki a két szám közé eső értékeket. A csúszka finom beosztása miatt olykor nem könnyű a kívánt számokat beállítani. A csúszka használatakor a két mezőbe is begépelheti a kívánt értékeket. Ez a lehetőség akkor hasznos, ha meghatározott számok alapján szeretne szeletelni.

A következő képen a jelentésoldal a 2500,00 és 6000,00 közötti tartományban lévő **LineTotal** értékekre szűr.

![Numerikustartomány-szeletelő a Két érték között beállítással](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-3-between-range.png)

Amikor a **Kisebb vagy egyenlő** lehetőséget választja, eltűnik a csúszkasáv bal oldali (legalacsonyabb értékhez tartozó) fogója, és csak a csúszka felső korlátját módosíthatja. A következő képen az 5928,19 maximális értékre állítjuk a csúszkasávot.

![Numerikustartomány-szeletelő a Kisebb, mint beállítással](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-4-less-than.png)

Végül, ha a **Nagyobb vagy egyenlő** lehetőséget választja, a csúszkasáv jobb oldali (legmagasabb értékhez tartozó) fogója tűnik el. Ilyenkor az alsó értéket állíthatja be a következő képen látható módon. Most csak a 4902,99-nél nagyobb vagy azzal egyenlő **LineTotal** értékek jelennek meg a jelentésoldal vizualizációiban.

![Numerikustartomány-szeletelő a Nagyobb, mint beállítással](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-5-greater-than.png)

## <a name="snap-to-whole-numbers-with-the-numeric-range-slicer"></a>Egész számhoz illeszkedés a numerikustartomány-szeletelőnél

A numerikustartomány-szeletelő egész számokhoz illeszkedik, ha a mögöttes mező adattípusa *Egész szám*. Ez a funkció teszi lehetővé, hogy a szeletelőt pontosan egy egész számra tudja beállítani. A *Tizedes tört* típusú mezőkbe törtszámokat írhat be. A szövegmezőben beállított formázás megegyezik a mező formázásával, bár beírhat vagy kijelölhet pontosabb számokat.

## <a name="display-formatting-with-the-date-range-slicer"></a>Formázás megjelenítése a dátumtartomány-szeletelővel

Amikor szeletelő használatával jelenít meg vagy állít be dátumtartományokat, a dátumok a *rövid dátumformátumban* jelennek meg. A dátumformátumot a felhasználó böngészőjének vagy operációs rendszerének területi beállításai határozzák meg. Emiatt a megjelenítési formátum mindig ez lesz, a mögöttes adatok vagy modellek adattípus-beállításaitól függetlenül.

Lehetséges például, hogy a mögöttes adattípus hosszú dátumformátumú. Ilyen esetben például az *éééé. hhhh nn., nnnn* dátumformátum más vizualizációkban vagy más körülmények között a *2001. március 14., szerda* megjelenítési formát eredményezné. A dátumtartomány-szeletelőben viszont a *2001. 03. 14.* formában jelenik meg ez a dátum.

A szeletelőben a Rövid dátum formátum használata biztosítja, hogy a sztring hossza ne változzon, és elférjen a szeletelőben.

## <a name="limitations-and-considerations"></a>Korlátozások és megfontolandó szempontok

A numerikustartomány-szeletelőre a következő korlátozások és szempontok érvényesek :

* A numerikustartomány-szeletelő az adatokban lévő összes alapul szolgáló sorra szűr, nem az összesített értékekre. Tegyük fel például, hogy egy *Értékesített mennyiség* mezőt használ. A szeletelő ekkor minden tranzakciót az értékesített mennyiség, és nem a vizualizáció adatpontjaira összegzett mennyiségek alapján fog szűrni.
* Ez mértékekkel jelenleg nem működik.
* A numerikus szeletelőkbe bármilyen számot beírhat, akkor is, ha az kívül esik mögöttes oszlop értéktartományán. Ezzel a lehetőséggel szűrőket állíthat be, ha tudja, hogy az adatok változni fognak.
