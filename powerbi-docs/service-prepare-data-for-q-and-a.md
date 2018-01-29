---
title: "Excel-adatok megfelelő működésének biztosítása a Q&A és a Power BI használatánál"
description: "Adatok megfelelő működésének biztosítása a Q&A és a Power BI használatánál"
services: powerbi
documentationcenter: 
author: mihart
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
ms.date: 01/18/2018
ms.author: mihart
ms.openlocfilehash: 92d75bc3df3a3403f77fb350b4acfe1325e707d2
ms.sourcegitcommit: d803e85bb0569f6b357ba0586f5702c20d27dac4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-make-your-excel-data-work-well-with-qa-in-power-bi"></a>Excel-adatok megfelelő működésének biztosítása a Q&A és a Power BI használatánál
Ha Ön a Power BI-jal használható adatmodelleket vagy Excel-munkafüzeteket készít, akkor olvasson tovább...

A Power BI-ban a Q&A olyan eszköz, amely strukturált adatok között keres, és kiválasztja az Ön kérdéséhez illő vizualizációt – ez teszi olyan vonzóvá a használatát.   

A Q&A bármely feltöltött Excel-fájllal működik, amely táblákat, tartományokat vagy PowerPivot-modelleket tartalmaz, de az optimalizálás és az adattisztítás még tovább fokozza a teljesítményét.  Ha az adathalmazon alapuló irányítópultokat és jelentéseket meg szeretné osztani, gondoskodnia kell arról, hogy munkatársai egyszerűen tehessenek fel kérdéseket, és hogy ezekre megfelelő válaszokat kapjanak.

### <a name="how-qa-works-with-excel"></a>A Q&A működése az Excellel
A Q&A része az alapvető természetes nyelvi értelmezési képességek halmaza, amelyek az Ön összes adatán működnek. Környezetfüggő kulcsszókeresést végez Excel-táblázatokban, -oszlopokban és számított mezőnevek között. Ezen kívül beépített képessége az adatok szűrése, rendezése, összesítése, csoportosítása és megjelenítése. 

Például egy “Eladások” nevű Excel-táblázatban, amelynek “Termék”, “Hónap”, “Eladott mennyiség”, “Bruttó bevétel” és “Nyereség” nevű oszlopai vannak, kérdéseket tehet fel ezek bármelyikével kapcsolatban.  Kérheti az eladások és az összes nyereség havonkénti kimutatását, a termékek eladott mennyiség szerinti rendezését és sok minden mást. Ismerje meg alaposabban [a feltehető kérdések fajtáit](power-bi-q-and-a.md) és a [Q&A-lekérdezésben megadható vizualizációtípusokat](power-bi-visualization-types-for-reports-and-q-and-a.md).

### <a name="prepare-an-excel-dataset-for-qa"></a>Excel-adatkészlet előkészítése Q&A-hez
A Q&A a táblázatok, oszlopok és számított mezők neve alapján válaszolja meg az adatokra vonatkozó kérdéseket, tehát lényeges a munkafüzet entitásainak elnevezése.

Néhány tanács a Q&A legjobb kihasználásához a munkafüzetben.

* Az adatai mindenképpen Excel-táblázatban legyenek. Sajátítsa el az [Excel-táblázatok létrehozását](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-e81aa349-b006-4f8a-9806-5af9df0ac664?ui=en-US&rs=en-US&ad=US).
* Ügyeljen rá, hogy a táblázatok, oszlopok és számított mezők neve érthető legyen természetes nyelven.
  
  Egy értékesítési adatokat tartalmazó táblázat neve például legyen “Értékesítés”. Az olyan oszlopnevek, mint “Év”, “Termék”, “Értékesítő” és “Mennyiség” jól használhatók a Q&A-ban.

* Ha a munkafüzet PowerPivot-adatmodellt tartalmaz, akkor további optimalizálást is végezhet. Ismerkedjen meg a saját nyelvszakértőinkből álló csapat [A Power BI Q&A-val kapcsolatos mítoszok eloszlatása – 2. rész](http://blogs.msdn.com/b/powerbi/archive/2014/02/27/demystifying-power-bi-q-amp-a-part-2.aspx) című cikkét.

* Az adathalmazt megnyithatja a Power BI Desktopban és új oszlopokat hozhat létre, számított mértékeket hozhat létre, mezők összefűzésével egyedi értékeket alakíthat ki, osztályozhatja az adattípusokat (például dátum, sztring, földrajzi hely, kép, URL stb. alapján), és számos más lehetőség áll még rendelkezésére.

## <a name="next-steps"></a>Következő lépések
Vissza a [Q&A a Power BI-ban](power-bi-q-and-a.md) című témakörhöz  
[Helyszíni adatkészlet előkészítése Q&A-hez](service-q-and-a-direct-query.md)   
[Rövid útmutató a Q&A használatához](power-bi-visualization-introduction-to-q-and-a.md)  
[Adatbeolvasás (a Power BI-ban)](service-get-data.md)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

