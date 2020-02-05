---
title: Útmutató automatikus dátum/időhöz a Power BI Desktopban
description: Útmutató a Power BI Desktop automatikus dátum/idő funkciójának használatához.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/23/2019
ms.author: v-pemyer
ms.openlocfilehash: 30bfacc1024035f0849440eec8b1c7051ff4d82a
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/04/2020
ms.locfileid: "75002443"
---
# <a name="auto-datetime-guidance-in-power-bi-desktop"></a>Útmutató automatikus dátum/időhöz a Power BI Desktopban

Ez a cikk azoknak az adatmodellezőknek szól, akik importálási vagy összetett modelleket fejlesztenek a Power BI Desktopban. Útmutatást, javaslatokat és szempontokat nyújt a Power BI Desktop _automatikus dátum/idő_ funkciójának konkrét helyzetekben való használatához. Az _automatikus dátum/idő_ funkció általános áttekintését és bevezetését lásd [A Power BI Desktop automatikus dátum/idő funkciója](../desktop-auto-date-time.md) című részben.

Az _automatikus dátum/idő_ lehetőség kényelmes, gyors és könnyen használható időintelligenciát biztosít. A jelentéskészítők az időintelligenciát a naptári időszakokban történő szűréshez, csoportosításhoz és részletezéshez használhatják.

## <a name="considerations"></a>Megfontolandó szempontok

Az alábbi felsorolási lista az _automatikus dátum/idő_ lehetőséghez kapcsolódó szempontokat és lehetséges korlátozásokat írja le.

- **Az összesre vagy egyikre sem érvényes:** Ha az _automatikus dátum/idő_ lehetőség be van kapcsolva, akkor az importált táblázatok összes olyan dátumoszlopára vonatkozik, amely nem a kapcsolat &quot;több&quot; oldalán van. Nem engedélyezhető vagy tiltható le szelektíven az egyes oszlopokon oszlop alapján.
- **Csak naptári időszakok:** Az év és a negyedév oszlopok a naptári időszakokhoz kapcsolódnak. Ez azt jelenti, hogy az év január 1-én kezdődik, és december 31-én fejeződik be. Az év kezdetének (és végének) testre szabására nincs lehetőség.
- **Testreszabás:** Az időszakok leírására szolgáló értékek testre szabására nincs lehetőség. Ezenkívül további oszlopok hozzáadására sincs lehetőség más időszakok, például hetek leírásához.
- **Év szűrése:** A **Negyedév**, a **Hónap**, és a **Nap** oszlopértékek nem tartalmazzák az év értéket. Például a **Hónap** oszlop csak a hónapok nevét (január, február stb.) tartalmazza. Az értékek nem teljesen önleíróak, és egyes jelentés-kialakításokban előfordulhat, hogy nem közlik az év szűrő kontextusát.

    Ezért fontos, hogy a szűrés és a csoportosítás az **Év** oszlopban menjen végbe. Hierarchia alapján végzett lefúrás esetén a szűrés az évre vonatkozik, kivéve ha az **Év** szintje szándékosan el lett távolítva. Ha nincs évre vonatkozó szűrő vagy csoport, akkor például egy havi csoportosítás az összes év adott hónapjára vonatkozó értékeket összegzi.
- **Dátumszűrés egyetlen táblázatban:** Mivel minden dátumoszlop létrehozza a saját (rejtett) automatikus dátum/idő táblázatát, nem lehet egy táblázatra időszűrőt alkalmazni és több modelltáblázatra kiterjeszteni. Ez a szűrésforma általános modellezési követelmény az olyan többszörös tárgyú jelentések (tény típusú táblázatok) létrehozásakor, mint az értékesítés és az értékesítési költségkeret. A jelentéskészítőnek az automatikus dátum/idő használatakor minden dátumoszlophoz külön szűrőt kell alkalmaznia.
- **A modell mérete:** Ez minden egyes (rejtett) automatikus dátum/idő táblázatot létrehozó dátumoszlop esetén nagyobb modellméretet és hosszabb adatfrissítési időt eredményez.

## <a name="recommendations"></a>Javaslatok

Javaslatunk szerint az _automatikus dátum/idő_ funkciót csak akkor kell bekapcsolt állapotban hagynia, ha naptári időszakokkal dolgozik, és az idővel kapcsolatban egyszerű modellkövetelményeket használ. Ez a lehetőség akkor is kényelmes megoldás, ha egyszeri modelleket hoz létre, vagy adatfeltárást, illetve profilkészítést végez.

Ha az adatforrás már meghatároz egy dátumdimenzió-táblát, ezt a táblát a cégen belül konzisztensen kell használni az idő meghatározására. Ha az adatforrás egy adattárház, akkor biztosan ez lesz a helyzet. A modellben szereplő dátumtáblázatokat létrehozhatja a DAX [CALENDAR](/dax/calendar-function-dax) vagy [CALENDARAUTO](/dax/calendarauto-function-dax) függvények használatával is. Ezt követően hozzáadhat számított oszlopokat az ismert időszűrési és csoportosítási igények támogatására. Ez a tervezési módszer lehetővé teszi egy minden ténytípusú táblázatra propagálódó egyetlen dátumtáblázat létrehozását, ez pedig egyetlen táblázatot eredményezhet az időszűrők alkalmazásához. A dátumtáblázatok létrehozásáról a [Dátumtáblázatok beállítása és használata Power BI Desktopban](../desktop-date-tables.md) című cikkben talál további információkat.

Ha az _automatikus dátum/idő_ funkciónak nincs jelentősége a projektjeiben, akkor a globális _automatikus dátum/idő_ funkció kikapcsolását javasoljuk. Ezzel biztosíthatja, hogy az újonnan létrehozott Power BI Desktop-fájlok egyike se kapcsolja be az _automatikus dátum/idő_ funkciót.

## <a name="next-steps"></a>Következő lépések

Ezzel a cikkel kapcsolatosan a következő forrásanyagokban talál további információt:

- [Automatikus dátum/idő a Power BI Desktopban](../desktop-auto-date-time.md)
- [Dátumtáblák beállítása és használata a Power BI Desktopban](../desktop-date-tables.md)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
