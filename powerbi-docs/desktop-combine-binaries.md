---
title: Fájlok (bináris fájlok) egyesítése a Power BI Desktopban
description: A fájl- (bináris) adatforrások egyszerűen egyesíthetők a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: f43bb105f7e17ce453e96c6eff875349efd45cb2
ms.sourcegitcommit: b11e908650379913d00673215e3eaf25d712b122
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/07/2019
ms.locfileid: "65239641"
---
# <a name="combine-files-binaries-in-power-bi-desktop"></a>Fájlok (bináris fájlok) egyesítése a Power BI Desktopban
Az adatok a **Power BI Desktopba** való importálásának egy igen hatékony módja, ha az azonos sémájú fájlokat egyetlen logikai táblában egyesíti. A **Power BI Desktop** 2016 novemberi (és azt követő) kiadásaiban ez a kényelmes és népszerű megközelítés még kényelmesebbé és szélesebb körben alkalmazhatóvá vált, amint azt ez a cikk is ismerteti.

Az egyazon mappában lévő fájlok ötvözéséhez válassza az **Adatok lekérése > Fájl > Mappa** lehetőséget.

![](media/desktop-combine-binaries/combine-binaries_1.png)

## <a name="previous-combine-files-binaries-behavior"></a>A fájlok (bináris fájlok) egyesítésének korábbi működése
A **Power BI Desktop** 2016 novemberi kiadását megelőzően ennek a funkciónak **Bináris fájlok egyesítése** volt a neve, és egyesíthetett bizonyos fájltípusokat a **bináris fájlok egyesítése** átalakítással, de az alábbi korlátozásokkal:

* A rendszer az egyes fájlokat az egyetlen táblába való egyesítésüket megelőzően nem alakította át. Így sokszor a fájlok egyesítését követően a szerkesztési folyamat keretében, a sorok szűrésével ki kellett szűrni a *fejlécértékeket*.
* A **Bináris fájlok egyesítése** átalakítás kizárólag *szöveges* vagy *CSV*-fájlokon volt használható, más támogatott fájlformátumokkal, például Excel-munkafüzetekkel, JSON-fájlokkal és egyéb fájlokkal nem működött.

Az ügyfelek a **bináris fájlok egyesítése** művelet intuitívabb módon való működését kérték, ezért az átalakítást továbbfejlesztettük és átneveztük, az új neve **fájlok egyesítése**.

## <a name="current-combine-files-behavior"></a>A fájlok egyesítésének jelenlegi működése
A **Power BI Desktop** mostantól hatékonyabban végzi a  **fájlok (bináris fájlok) egyesítését**. A **fájlok egyesítése** a **Lekérdezésszerkesztő** menüszalagján a **Kezdőlapról** vagy magából az oszlopból indítható.

![](media/desktop-combine-binaries/combine-binaries_2a.png)

A **fájlok egyesítése** átalakítás mostantól az alábbiak szerint működik:

* A **fájlok egyesítése** átalakítás kielemzi az egyes bemeneti fájlokat, és meghatározza a megfelelő fájlformátumot (például: *szövegfájl*, *Excel-munkafüzet* vagy *JSON*-fájl).
* Az átalakítással kiválaszthat egy adott objektumot az első fájlból, például egy *Excel-munkafüzetből*, amelyet ki szeretne nyerni.
  
  ![](media/desktop-combine-binaries/combine-binaries_3.png)
* A **fájlok egyesítése** ekkor automatikusan végrehajtja a következők lekérdezéseket:
  
  * Létrehoz egy példalekérdezést, amely végrehajtja a kinyeréshez szükséges lépéseket egyetlen fájlban.
  * Létrehoz egy *függvénylekérdezést*, amely felparaméterezi a fájl/bináris fájl bemenetet a *példalekérdezéshez*. A példalekérdezés és a függvénylekérdezés össze van kapcsolva, így a példalekérdezésen végrehajtott módosítások a függvénylekérdezésben is megjelennek.
  * Alkalmazza a *függvénylekérdezést* az eredeti lekérdezésre a bemeneti bináris fájlokkal (például a *Mappa* lekérdezést), azaz a bináris fájlbemenetek függvénylekérdezéseit mindegyik soron alkalmazza, majd az így kinyert adatokat felsőszintű oszlopokká bontja ki.
    
    ![](media/desktop-combine-binaries/combine-binaries_4.png)

A **fájlok egyesítésének** új működése révén könnyedén egyesítheti az egy adott mappában lévő összes fájlt, amennyiben egyazon fájltípussal és szerkezettel (azaz ugyanazokkal az oszlopokkal) rendelkeznek.

Emellett további átalakítási és kinyerési műveleteket is könnyen alkalmazhat az automatikusan létrehozott *példalekérdezés* módosításával anélkül, hogy módosítania kellene a *függvénylekérdezés* lépéseit, vagy újakat kellene létrehoznia. A *példalekérdezés* bármilyen módosítása automatikusan létrejön a vele összekapcsolt *függvénylekérdezésben*.

## <a name="next-steps"></a>Következő lépések
A Power BI Desktop használatával számos adatforráshoz csatlakozhat. Az adatforrásokkal kapcsolatos információkért lásd az alábbi forrásanyagokat:

* [Mi az a Power BI Desktop?](desktop-what-is-desktop.md)
* [Adatforrások a Power BI Desktopban](desktop-data-sources.md)
* [Adatok formázása és kombinálása a Power BI Desktoppal](desktop-shape-and-combine-data.md)
* [Csatlakozás CSV-fájlokhoz a Power BI Desktopban](desktop-connect-csv.md)   
* [Adatok közvetlen bevitele a Power BI Desktopba](desktop-enter-data-directly-into-desktop.md)   

