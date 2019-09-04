---
title: Csatlakozás CSV-fájlokhoz a Power BI Desktopban
description: Könnyedén csatlakozhat CSV-fájlokhoz, és használhatja a bennük tárolt adatokat a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 8eecbfdaa948163ab6d0623a70f237d479fcdb88
ms.sourcegitcommit: a00fe5fb545c3df13b7cd13a701fd6a2b2521a17
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/31/2019
ms.locfileid: "70200925"
---
# <a name="connect-to-csv-files-in-power-bi-desktop"></a>Csatlakozás CSV-fájlokhoz a Power BI Desktopban
A Power BI Desktopban a vesszővel tagolt adatfájlhoz (*CSV*) való csatlakozás hasonlít az Excel-munkafüzethez való csatlakozáshoz. Mindkettő egyszerű, és ez a cikk lépésről lépésre bemutatja, hogyan csatlakozhat bármely CSV-fájlhoz, amelyhez hozzáfér.

Először a Power BI Desktop **Kezdőlap** szalagján válassza a **Lekérdezés > CSV** lehetőséget.

![](media/desktop-connect-csv/connect-to-csv_1.png)

Válassza ki a CSV-fájlt a megjelenő **Megnyitás** párbeszédablakból.

![](media/desktop-connect-csv/connect-to-csv_2.png)

A **Megnyitás** kiválasztása után a Power BI Desktop eléri a fájlt, és meghatároz bizonyos fájlattribútumokat, például a fájl eredetét, az elválasztó típusát, és hogy hány sort kell használni a fájlban lévő adattípusok meghatározására.

Ezek a fájlattribútumok és beállítások a legördülő listában jelennek meg a **CSV importálása** párbeszédablak tetején, az alábbiakban látható módon. Az észlelt beállítások bármelyikét manuálisan is megváltoztathatja úgy, hogy egy másik lehetőséget választ bármelyik legördülő választóból.

![](media/desktop-connect-csv/connect-to-csv_3.png)

Ha elégedett a kiválasztott beállításokkal, kattinthat a **Betöltés** gombra a fájl importálásához a Power BI Desktopba, vagy kattinthat a **Szerkesztés** gombra a **Lekérdezésszerkesztő** megnyitásához, és az adatok további formázásához vagy módosításához az importálás előtt.

Miután betöltötte az adatokat a Power BI Desktopba, megjelenik a táblázat és annak oszlopai (amelyek mezőként jelennek meg a Power BI Desktopban) a **Mezők** panelben, a Jelentés nézet jobb oldalán a Power BI Desktopban.

![](media/desktop-connect-csv/connect-to-csv_4.png)

Mindössze ennyit kell tennie. A CSV-fájl adatai már a Power BI Desktopban vannak.

Most már felhasználhatja a Power BI Desktopba bevitt adatokat vizualizációk és jelentések készítéséhez, vagy más olyan adatokkal való kommunikációhoz, amelyekhez később csatlakozni szeretne vagy amelyeket importálna, mint például Excel táblázatok, adatbázisok vagy más egyéb adatforrás.

> [!IMPORTANT]
> CSV-fájl importálásakor a Power BI Desktop a Power Query-szerkesztőben az egyik lépésként létrehoz egy *columns=x* kifejezést (ahol az *x* a CSV-fájlban található oszlopok száma a kezdeti importáláskor). Ha később további oszlopokat ad hozzá, és az adatforrás frissítése be van állítva, a rendszer az oszlopok kezdeti *x* számát nem frissíti a további oszlopokkal. 


## <a name="next-steps"></a>Következő lépések
A Power BI Desktop használatával számos adatforráshoz csatlakozhat. Az adatforrásokkal kapcsolatos információkért lásd az alábbi forrásanyagokat:

* [Mi az a Power BI Desktop?](desktop-what-is-desktop.md)
* [Adatforrások a Power BI Desktopban](desktop-data-sources.md)
* [Adatok formázása és kombinálása a Power BI Desktoppal](desktop-shape-and-combine-data.md)
* [Kapcsolódás az Excelhez a Power BI Desktopban](desktop-connect-excel.md)   
* [Adatok közvetlen bevitele a Power BI Desktopba](desktop-enter-data-directly-into-desktop.md)   

