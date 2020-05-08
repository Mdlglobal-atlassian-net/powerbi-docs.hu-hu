---
title: Excel-adatok megfelelő működésének biztosítása a Q&A és a Power BI használatánál
description: Adatok megfelelő működésének biztosítása a Q&A és a Power BI használatánál
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/13/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 16d58090a9a7c6e64fbf2ace23fdf342d1768a30
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "73881088"
---
# <a name="make-excel-data-work-well-with-qa-in-power-bi"></a>Excel-adatok megfelelő működésének biztosítása a Q&A és a Power BI használatánál
Ha Ön a Power BI-jal használható adatmodelleket vagy Excel-munkafüzeteket készít, akkor olvasson tovább...

A Power BI-ban a Q&A olyan eszköz, amely strukturált adatok között keres, és kiválasztja az Ön kérdéséhez illő vizualizációt – ez teszi olyan vonzóvá a használatát.   

A Q&A bármely feltöltött Excel-fájllal működik, amely táblákat, tartományokat vagy PowerPivot-modelleket tartalmaz, de az optimalizálás és az adattisztítás még tovább fokozza a teljesítményét.  Ha az adathalmazon alapuló irányítópultokat és jelentéseket meg szeretné osztani, gondoskodnia kell arról, hogy munkatársai egyszerűen tehessenek fel kérdéseket, és hogy ezekre megfelelő válaszokat kapjanak.

## <a name="how-qa-works-with-excel"></a>A Q&A működése az Excellel
A Q&A része az alapvető természetes nyelvi értelmezési képességek halmaza, amelyek az Ön összes adatán működnek. Környezetfüggő kulcsszókeresést végez Excel-táblázatokban, -oszlopokban és számított mezőnevek között. Ezen kívül beépített képessége az adatok szűrése, rendezése, összesítése, csoportosítása és megjelenítése. 

Például egy “Eladások” nevű Excel-táblázatban, amelynek “Termék”, “Hónap”, “Eladott mennyiség”, “Bruttó bevétel” és “Nyereség” nevű oszlopai vannak, kérdéseket tehet fel ezek bármelyikével kapcsolatban.  Kérheti az eladások és az összes nyereség havonkénti kimutatását, a termékek eladott mennyiség szerinti rendezését és sok minden mást. További információk a [Q&A irányítópultokon és jelentésekben való használatáról](power-bi-tutorial-q-and-a.md), valamint [a Q&A-lekérdezésekben megadható vizualizációtípusokról](visuals/power-bi-visualization-types-for-reports-and-q-and-a.md).

## <a name="prepare-an-excel-dataset-for-qa"></a>Excel-adatkészlet előkészítése Q&A-hez
A Q&A a táblázatok, oszlopok és számított mezők neve alapján válaszolja meg az adatokra vonatkozó kérdéseket, tehát lényeges a munkafüzet entitásainak elnevezése.

Néhány tanács a Q&A legjobb kihasználásához a munkafüzetben.

* Az adatai mindenképpen Excel-táblázatban legyenek. Sajátítsa el az [Excel-táblázatok létrehozását](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-e81aa349-b006-4f8a-9806-5af9df0ac664).
* Ügyeljen rá, hogy a táblázatok, oszlopok és számított mezők neve érthető legyen természetes nyelven.
  
  Egy értékesítési adatokat tartalmazó táblázat neve például legyen “Értékesítés”. Az olyan oszlopnevek, mint “Év”, “Termék”, “Értékesítő” és “Mennyiség” jól használhatók a Q&A-ban.

* Ha a munkafüzet PowerPivot-adatmodellt tartalmaz, akkor további optimalizálást is végezhet. Ismerkedjen meg a saját nyelvszakértőinkből álló csapat [A Power BI Q&A-val kapcsolatos mítoszok eloszlatása – 2. rész](https://blogs.msdn.com/b/powerbi/archive/2014/02/27/demystifying-power-bi-q-amp-a-part-2.aspx) című cikkét.

* Az adathalmazt megnyithatja a Power BI Desktopban és új oszlopokat hozhat létre, számított mértékeket hozhat létre, mezők összefűzésével egyedi értékeket alakíthat ki, osztályozhatja az adattípusokat (például dátum, sztring, földrajzi hely, kép, URL stb. alapján), és számos más lehetőség áll még rendelkezésére.

## <a name="next-steps"></a>További lépések

- [Q&A felhasználók számára](consumer/end-user-q-and-a.md)  
- [A Q&A használata irányítópultokon és jelentésekben](power-bi-tutorial-q-and-a.md)
- [Helyszíni adatkészletek előkészítése Q&A-hez](service-q-and-a-direct-query.md)   
- [Adatbeolvasás (a Power BI-ban)](service-get-data.md)  

Több kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

