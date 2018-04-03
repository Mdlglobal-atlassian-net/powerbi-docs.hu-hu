---
title: "Csatlakozás az Adobe Analyticshez a Power BI Desktopban (előzetes verzió)"
description: "Könnyedén csatlakozhat az Adobe Analyticshez, és használhatja azt a Power BI Desktopban"
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
ms.date: 03/09/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: efd6d066e2f98f86248730917c2f4aa0c8a39983
ms.sourcegitcommit: 4217430c3419046c3a90819c34f133ec7905b6e7
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/12/2018
---
# <a name="connect-to-adobe-analytics-in-power-bi-desktop-preview"></a>Csatlakozás az Adobe Analyticshez a Power BI Desktopban (előzetes verzió)
A **Power BI Desktopban** csatlakozhat az **Adobe Analyticshez**, és úgy használhatja az alapul szolgáló adatokat, mint a Power BI Desktop bármely más adatforrását. 

![Adatok lekérése az Adobe Analytics szolgáltatásból](media/desktop-connect-adobe-analytics/connect-adobe-analytics_01.png)

## <a name="enable-the-adobe-analytics-connector-preview"></a>Az Adobe Analytics-összekötő előzetes verziójának engedélyezése 
Mivel az **Adobe Analytics**-összekötő jelenleg előzetes verzióként érhető el, az előzetes verziójú funkció engedélyezése szükséges ahhoz, hogy az összekötő használható legyen az **Adatok lekérése** ablakban. Az összekötő előzetes verziójának engedélyezéséhez válassza a **Fájl > Lehetőségek és beállítások > Beállítások > Előzetes verziójú funkciók** lehetőséget a Power BI Desktopban, majd jelölje be a **Könyvjelzők** elem melletti jelölőnégyzetet. 

![Az Adobe Analytics-összekötő előzetes verziójának engedélyezése a Beállítások között](media/desktop-connect-adobe-analytics/connect-adobe-analytics_02.png)

Az Adobe Analytics-összekötő előzetes verziójának engedélyezésre után újra kell indítania a **Power BI Desktopot**.

## <a name="connect-to-adobe-analytics-data"></a>Kapcsolódás az Adobe Analytics adataihoz
Ha csatlakozni kíván az **Adobe Analytics** adataihoz, válassza az **Adatok lekérése** lehetőséget a Power BI Desktop **Kezdőlap** menüszalagján. A bal oldali kategóriák közül válassza az **Online szolgáltatások** lehetőséget, ekkor megjelenik az **Adobe Analytics-összekötő**.

![Adatok lekérése az Adobe Analytics szolgáltatásból](media/desktop-connect-adobe-analytics/connect-adobe-analytics_01.png)

A megjelenő **Adobe Analytics** ablakban válassza a **Bejelentkezés** gombot, majd hitelesítő adatai megadásával jelentkezzen be Adobe Analytics-fiókjába. Megjelenik az Adobe bejelentkezési ablaka, ahogyan a következő ábra mutatja.

![Bejelentkezés az Adobe Analyticsbe](media/desktop-connect-adobe-analytics/connect-adobe-analytics_03.png)

Ha a rendszer kéri, adja meg a felhasználónevét és a jelszavát. Miután a kapcsolat létrejött, többféle dimenzió és mérték előnézetére és kiválasztására is lehetősége van a Power BI **Kezelő** párbeszédpaneljén az egyszerű táblázatos kimenet létrehozásához. A kijelölt elemekhez szükséges bemenő paramétereket is megadhatja. 

![Adatok kijelölése a Kezelő használatával](media/desktop-connect-adobe-analytics/connect-adobe-analytics_04.png)

A kiválasztott táblát **betöltheti**, amellyel az egész tábla bekerül a **Power BI Desktopba**, vagy **szerkesztheti** is a lekérdezést. Ekkor megnyílik a **Lekérdezésszerkesztő**, amellyel szűrheti vagy finomíthatja a használni kívánt adatokat, majd a finomított adatkészletet betöltheti a **Power BI Desktopba**.

![Adatok betöltése vagy szerkesztése a Kezelőben](media/desktop-connect-adobe-analytics/connect-adobe-analytics_05.png)


## <a name="next-steps"></a>Következő lépések
A Power BI Desktop használatával számos adatforráshoz csatlakozhat. Az adatforrásokkal kapcsolatos információkért lásd az alábbi forrásanyagokat:

* [Első lépések a Power BI Desktopban](desktop-getting-started.md)
* [Adatforrások a Power BI Desktopban](desktop-data-sources.md)
* [Adatok formázása és kombinálása a Power BI Desktoppal](desktop-shape-and-combine-data.md)
* [Kapcsolódás az Excelhez a Power BI Desktopban](desktop-connect-excel.md)   
* [Adatok közvetlen bevitele a Power BI Desktopba](desktop-enter-data-directly-into-desktop.md)   
