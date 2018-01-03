---
title: "A Power BI Desktop adatvédelmi szintjeinek megismerése"
description: "A Power BI Desktop adatvédelmi szintjei"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/12/2017
ms.author: davidi
ms.openlocfilehash: 733e24f44c63b8887c3c8b00999f7cea22581a86
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/15/2017
---
# <a name="power-bi-desktop-privacy-levels"></a>A Power BI Desktop adatvédelmi szintjei
A **Power BI Desktop** adatvédelmi szintjei egy elkülönítési szintet adnak meg, amely meghatározza, hogy az adott adatforrás milyen mértékben lesz elkülönítve a többi adatforrástól. A korlátozó elkülönítési szint azonban gátolja az adatforrások közötti információcserét, csökkentheti a funkcionalitást és hatással lehet a teljesítményre.

A **Fájl > Lehetőségek és beállítások > Beállítások** majd az **Aktuális fájl > Adatvédelem** helyen található **Adatvédelmi szintek** beállításai megadják, hogy a Power BI Desktop használja-e az adatvédelmi szint beállításait az adatok ötvözése során. A párbeszédpanelen a Power BI Desktop Adatvédelmi szintekről szóló dokumentációjára és az Adatvédelmi szintek dokumentációjára (ez a cikk) mutató hivatkozás található.

![](media/desktop-privacy-levels/desktop_privacylevels1.png)

 Az adatforrások **Adatvédelmi** beállítások párbeszédpanele a **Fájl > Lehetőségek és beállítások > Adatforrás beállításai** alatt található. Válassza ki az adatforrást, majd kattintson a **Szerkesztés** elemre. Megjelenik az **Adatforrás beállításai** párbeszédpanel, ahol a panel alján található legördülő menüből kiválaszthatja a megfelelő adatvédelmi szintet, az alábbi képen is látható módon.

 ![](media/desktop-privacy-levels/desktop_privacylevels2.png)

> [!CAUTION]
> A rendkívül bizalmas vagy titkos adatokat tartalmazó adatforrást célszerű **Privát** láthatóságúra állítani.
> 
> 

## <a name="configure-a-privacy-level"></a>Adatvédelmi szint beállítása
Az adatvédelmi szint beállításaival megadhat egy elkülönítési szintet, amely meghatározza, hogy az adott adatforrást milyen mértékben kell elkülöníteni a többi adatforrástól.

| Beállítás | Leírás | Adatforrások példái |
| --- | --- | --- |
| **Privát adatforrás** |Egy **Privát** adatforrás bizalmas vagy titkos információt tartalmaz, és az adatforrást csak a jogosult felhasználók láthatják. A privát adatforrás teljesen el van különítve az egyéb adatforrásoktól. |A Facebook-adatok, tőzsdei juttatásokat tartalmazó szöveges fájlok vagy az alkalmazottak felülvizsgálatát tartalmazó munkafüzet. |
| **Szervezeti adatforrás** |A **Szervezeti** adatforrás személyek megbízható csoportjára korlátozza egy adatforrás láthatóságát. A **Szervezeti** adatforrás el van különítve az összes **Nyilvános** adatforrástól, de látható az egyéb **Szervezeti** adatforrások számára. |Egy intranetes SharePoint-webhelyen található **Microsoft Word**-dokumentum, megbízható csoport számára biztosított engedélyekkel. |
| **Nyilvános adatforrás** |Egy **Nyilvános** adatforrás mindenki számára láthatóvá teszi az adatforrásban található adatokat. Csak a fájlok, internetes adatforrások vagy egy munkafüzet adatai jelölhetők meg **nyilvánosként**. |A Microsoft Azure Piactér ingyenes adatai, egy Wikipédia-oldal adatai, vagy egy nyilvános webhelyről másolt adatokat tartalmazó helyi fájl |

## <a name="configure-privacy-level-settings"></a>Adatvédelmi szintek beállításainak konfigurálása
Az adatforrások **Adatvédelmi** beállítások párbeszédpanele a **Fájl > Lehetőségek és beállítások > Adatforrás beállításai** alatt található.

Egy adatforrás adatvédelmi szintjének konfigurálásához válassza ki az adatforrást, majd kattintson a **Szerkesztés** elemre. Megjelenik az **Adatforrás beállításai** párbeszédpanel, ahol a panel alján található legördülő menüből kiválaszthatja a megfelelő adatvédelmi szintet, az alábbi képen is látható módon.

![](media/desktop-privacy-levels/desktop_privacylevels2.png)

> [!CAUTION]
> A rendkívül bizalmas vagy titkos adatokat tartalmazó adatforrást célszerű **Privát** láthatóságúra állítani.
> 

## <a name="configure-privacy-levels"></a>Adatvédelmi szintek konfigurálása
Az **Adatvédelmi szintek** egy olyan beállítás, amely alapértelmezés szerint az **Adatok összevonása forrásonként az adatvédelmiszint-beállításoknak megfelelően** értékre van beállítva, ami azt jelenti, hogy az **Adatvédelmi szintek** nincsenek engedélyezve.

| Beállítás | Leírás |
| --- | --- |
| **Adatok összevonása forrásonként az adatvédelmiszint-beállításoknak megfelelően** (bekapcsolva, alapértelmezett beállítás) |Az adatvédelmi szintek beállításai az adatforrások közötti elkülönítés szintjének megállapítására használhatók az adatok összevonása során. |
| **A teljesítmény lehetséges javítása az adatvédelmi szintek figyelmen kívül hagyásával** (kikapcsolva) |Az adatok összevonása során az adatvédelmi szintek nem lesznek figyelembe véve, ami az adatok teljesítményének és funkcionalitásának növekedésével járhat. |

> **Biztonsági megjegyzés:** Ha engedélyezi az **Adatvédelmi szinteket** **A teljesítmény lehetséges javítása az adatvédelmi szintek figyelmen kívül hagyásával** az **Adatvédelmi szintek** párbeszédpanelen történő kiválasztásával együtt, arra jogosulatlan személyek számára is hozzáférhetővé teheti a bizalmas adatokat. Ne engedélyezze az **Adatvédelmi szinteket**, csak ha biztos abban, hogy az adatforrások nem tartalmaznak bizalmas vagy titkos adatokat.
> 
> 

**Adatvédelmi szintek konfigurálása**

A Power BI Desktopban vagy a Lekérdezésszerkesztőben válassza a **Fájl > Lehetőségek és beállítások > Beállítások** elemet, majd kattintson az **Aktuális fájl > Adatvédelem** elemre.

a. Ha az **Adatok összevonása forrásonként az adatvédelmiszint-beállításoknak megfelelően** van kiválasztva, az adatok az adatvédelmi szintek beállításai szerint lesznek összevonva. Az adatok adatvédelmi elkülönítési zónákon keresztül való egyesítése adatpufferelést eredményezhet.

b. Ha **A teljesítmény lehetséges javítása az adatvédelmi szintek figyelmen kívül hagyásával** van kiválasztva, az adatok az adatvédelmi szintek figyelmen kívül hagyásával lesznek összevonva, ami bizalmas vagy titkos adatokat fedhet fel egy jogosulatlan személy előtt. A beállítás azonban javíthatja a teljesítményt és a funkcionalitást.

> **Biztonsági megjegyzés:** **A teljesítmény lehetséges javítása az adatvédelmi szintek figyelmen kívül hagyásával** javíthatja a teljesítményt, azonban ilyenkor a Power BI Desktop nem garantálja a Power BI Desktop-fájlban egyesített adatok adatvédelmét.
> 
> 

