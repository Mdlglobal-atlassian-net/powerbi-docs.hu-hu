---
title: Adatkategorizáció a Power BI Desktopban
description: Adatkategorizáció a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 92191c96409a3a75ad44f8d3472805a3e98da7dd
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54275709"
---
# <a name="data-categorization-in-power-bi-desktop"></a>Adatkategorizáció a Power BI Desktopban
A **Power BI Desktopban** megadhatja egy oszlop adatkategóriáját, így a Power BI Desktop tudni fogja, hogyan kezelje az értékeit egy vizualizációban.

Ha a Power BI Desktop adatokat importál, nem csak magát az adatokat kéri le, hanem olyan információkat is, mint például a táblázat és az oszlop neve, hogy az adat elsődleges kulcs-e stb.  Ezen információk alapján a Power BI Desktop feltételezéseket tesz arról, hogyan biztosíthat nagyszerű alapértelmezett élményt a vizualizáció létrehozásakor. 

Íme egy példa: Ha a Power BI Desktop egy numerikus értékkel rendelkező oszlopot észlel, valószínűleg összesíteni szeretné valamilyen módon, ezért a rendszer az Értékek területre helyezi. Vagy egy dátum- és időértékekkel rendelkező oszlop esetében a rendszer azt feltételezi, hogy valószínűleg időhierarchia-tengelyként szeretné használni egy vonaldiagramban.

De néhány feladat, például a földrajzi hely nagyobb kihívást jelent. Vegyük például az alábbi, egy Excel-munkalapról származó táblázatot:

![](media/desktop-data-categorization/datacategorizationtable.png)

A Power BI Desktop egy ország vagy egy USA-beli állam rövidítéseként kezelje-e a kódokat a GeoCode oszlopban?  Ez nem egyértelmű, mivel az ehhez hasonló kódok bármelyiket jelenthetik.  Például az AL rövidítés jelentheti Alabamát és Albániát is, az AR Arkansas-t vagy Argentínát, a CA pedig Kaliforniát vagy Kanadát. Ez akkor számít igazán, ha a GeoCode-mezőt egy térképen fogjuk ábrázolni.  A Power BI Desktop az országokat kiemelve a világtérképet jelenítse meg, vagy az Egyesült Államok térképét, kiemelve az államokat?  Az ilyen adatokhoz megadhat egy adatkategóriát. Az adatkategorizáció a legjobb vizualizáció biztosítása érdekében tovább finomítja azokat az információkat, amelyeket a Power BI Desktop használhat.  

**Adatkategória megadása**

1. Jelentés vagy Adatnézetben a **Mezők** listából válassza ki azt a listát, amelyet más kategorizáció szerint szeretne rendezni.
2. A menüszalag **Modellezés** lapján kattintson az **Adatkategória:** legördülő listára.  Ez megmutatja a lehetséges adatkategóriák listáját, így választhat egyet az oszlop számára.  Előfordulhat, hogy néhány kiválasztás le van tiltva, ha nem működnek az oszlop aktuális adattípusával.  Például ha egy oszlop bináris adattípusú, a Power BI Desktop nem engedi a földrajzi adatkategóriák kiválasztását. 

![](media/desktop-data-categorization/datacategorization.gif)

Ennyi az egész!  Ezzel minden viselkedés, amely általában egy vizualizációtól elvárható, mostantól automatikusan működik.  

Érdekelhetik még további információk a [földrajzi szűrésről a Power BI mobilalkalmazásokhoz](desktop-mobile-geofiltering.md).

