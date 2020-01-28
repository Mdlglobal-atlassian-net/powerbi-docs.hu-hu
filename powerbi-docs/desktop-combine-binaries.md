---
title: Fájlok (bináris fájlok) egyesítése a Power BI Desktopban
description: A fájl- (bináris) adatforrások egyszerűen egyesíthetők a Power BI Desktopban
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/13/2020
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 07381461375ea7b9707b91c807e92cdb85c1d440
ms.sourcegitcommit: 3d6b27e3936e451339d8c11e9af1a72c725a5668
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/17/2020
ms.locfileid: "76161104"
---
# <a name="combine-files-binaries-in-power-bi-desktop"></a>Fájlok (bináris fájlok) egyesítése a Power BI Desktopban

Az alábbi hatékony megközelítéssel importálhatja az adatokat a **Power BI Desktopba**: Ha több, ugyanazzal a sémával rendelkező fájlja van, egyetlen logikai táblában egyesítheti azokat. Ez a népszerű technikát tették kényelmesebbé és kiterjedtebbé.

Az egyazon mappában lévő fájlok ötvözése folyamatának megkezdéséhez válassza az **Adatok lekérése**, majd a **Fájl** > **Mappa**, végül a **Csatlakozás** lehetőséget.

![Csatlakozás mappafájlhoz, Adatok lekérése párbeszédpanel, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_1.png)

Adja meg a mappa elérési útját, és válassza az **OK**, majd az **Adatok átalakítása** lehetőséget a mappa fájljainak a Power Query-szerkesztőben való megtekintéséhez.

## <a name="combine-files-behavior"></a>A fájlok egyesítésének működése

A bináris fájlok Power Query-szerkesztőben való egyesítéséhez válassza a **Tartalom** lehetőséget (az első oszlop címkéjét), majd a **Kezdőlap** > **Fájlok egyesítése** lehetőséget. Másik lehetőségként választhatja egyszerűen a **Fájlok egyesítése** ikont a **Tartalom** elem mellett.

![Fájlok egyesítése parancs, Power Query-szerkesztő, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_2a.png)

A *fájlok egyesítése* átalakítás az alábbiak szerint működik:

* A „fájlok egyesítése” átalakítás elemzi az egyes bemeneti fájlokat, hogy meghatározza a használandó megfelelő fájlformátumot (példa: *szövegfájl*, *Excel-munkafüzet* vagy *JSON-fájl*).
* Az átalakítással kiválaszthat egy adott objektumot az első fájlból, például egy Excel-munkafüzetből, amelyet ki szeretne nyerni.
  
  ![Fájlok egyesítése párbeszédpanel, Power Query-szerkesztő, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_3.png)
* A „fájlok egyesítése” átalakítás automatikusan végrehajtja a következő műveleteket:
  
  * Létrehoz egy példalekérdezést, amely végrehajtja a kinyeréshez szükséges lépéseket egyetlen fájlban.
  * Létrehoz egy *függvénylekérdezést*, amely felparaméterezi a fájl/bináris fájl bemenetet a *példalekérdezéshez*. A példalekérdezés és a függvénylekérdezés össze van kapcsolva, így a példalekérdezésen végrehajtott módosítások a függvénylekérdezésben is megjelennek.
  * A *függvénylekérdezést* az eredeti lekérdezésre alkalmazza a bemeneti bináris fájlokkal, például a *Mappa* lekérdezésre. A bináris bemenetek függvénylekérdezését alkalmazza az egyes sorokra, majd legfelső szintű oszlopokként bontja ki az eredményül kapott adatkinyerést.

    ![A „fájlok egyesítése” párbeszédpanel eredményei, Power Query-szerkesztő, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_4.png)

> [!NOTE]
> A Excel-munkafüzetben végzett kijelölés befolyásolja a bináris fájlok egyesítésének folyamatát. Kijelölhet például egy munkalapot, hogy csak azt a munkalapot egyesítse, vagy a gyökeret, hogy a teljes fájl egyesítve legyen. Egy mappa kijelölésével a mappában található fájlok egyesíthetők. 

A fájlok egyesítésének működése révén könnyedén egyesítheti az egy adott mappában lévő összes fájlt, amennyiben egyazon fájltípussal és szerkezettel (azaz ugyanazokkal az oszlopokkal) rendelkeznek.

Emellett további átalakítási és kinyerési műveleteket is könnyen alkalmazhat az automatikusan létrehozott példalekérdezés módosításával anélkül, hogy módosítania kellene a függvénylekérdezés lépéseit, vagy újakat kellene létrehoznia. A példalekérdezés bármilyen módosítása automatikusan létrejön a vele összekapcsolt függvénylekérdezésben.

## <a name="next-steps"></a>Következő lépések

A Power BI Desktop használatával sokféle adatforráshoz csatlakozhat. Az adatforrásokkal kapcsolatos információkért lásd az alábbi forrásanyagokat:

* [Mi az a Power BI Desktop?](desktop-what-is-desktop.md)
* [Adatforrások a Power BI Desktopban](desktop-data-sources.md)
* [Adatok formázása és kombinálása a Power BI Desktoppal](desktop-shape-and-combine-data.md)
* [Csatlakozás CSV-fájlokhoz a Power BI Desktopban](desktop-connect-csv.md)
* [Adatok közvetlen bevitele a Power BI Desktopba](desktop-enter-data-directly-into-desktop.md)
