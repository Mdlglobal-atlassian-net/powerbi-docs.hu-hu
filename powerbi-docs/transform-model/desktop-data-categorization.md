---
title: Adatkategorizáció a Power BI Desktopban
description: Adatkategorizáció a Power BI Desktopban
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 4ce9946672514d3d3f181c573789b256888a4372
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83325851"
---
# <a name="specify-data-categories-in-power-bi-desktop"></a>Adatkategóriák meghatározása a Power BI Desktopban
A Power BI Desktopban megadhatja egy oszlop *adatkategóriáját*, így a Power BI Desktop tudni fogja, hogyan kezelje az értékeit egy vizualizációban.

Amikor a Power BI Desktop adatokat importál, az adatok mellett más információkat is beolvas, például a táblák és oszlopok neveit, és hogy az adat elsődleges kulcs-e. Ezen információk alapján a Power BI Desktop feltételezéseket tesz arról, hogyan biztosíthat nagyszerű alapértelmezett élményt a vizualizáció létrehozásakor.
Ha egy oszlop például numerikus értékeket tartalmaz, valószínűleg összesíteni szeretné valamilyen módon, ezért a Power BI Desktop a **Vizualizációk** panel **Értékek** területén helyezi el. Vagy egy vonaldiagramban dátum- és időértékekkel rendelkező oszlopa esetében a Power BI Desktop azt feltételezi, hogy valószínűleg időhierarchia-tengelyként szeretné használni.

De néhány feladat, például a földrajzi hely nagyobb kihívást jelent. Vegyük például az alábbi, egy Excel-munkalapról származó táblázatot:

![](media/desktop-data-categorization/datacategorizationtable.png)

A Power BI Desktop egy ország vagy egy USA-beli állam rövidítéseként kezelje-e a kódokat a **GeoCode** oszlopban?  Ez nem egyértelmű, mivel az ehhez hasonló kódok bármelyiket jelenthetik. Például az AL rövidítés jelentheti Alabamát és Albániát is, az AR Arkansas-t vagy Argentínát, a CA pedig Kaliforniát vagy Kanadát. Ez akkor számít igazán, ha a GeoCode-mezőt egy térképen fogjuk ábrázolni. 

A Power BI Desktopnak a világtérképet kellene megjelenítenie az országok kiemelésével? Vagy az Egyesült Államok képét, amelyen az államok vannak kiemelve?  Az ilyen adatokhoz adatkategóriát határozhat meg. Az adatkategorizáció a legjobb vizualizáció biztosítása érdekében tovább finomítja azokat az információkat, amelyeket a Power BI Desktop használhat.  

**Adatkategória megadása**

1. **Jelentés** vagy **Adat** nézetben a **Mezők** listából válassza ki azt a listát, amelyet más kategorizáció szerint szeretne rendezni.
2. A menüszalagon **Modellezés** lapjának **Tulajdonságok** területén válassza az **Adatkategória** melletti legördítő nyilat.  Ez a lista az oszlophoz választható adatkategóriákat sorolja fel. Előfordulhat, hogy néhány kiválasztás le van tiltva, ha nem működnek az oszlop aktuális adattípusával.  Például ha egy oszlop dátum vagy idő adattípusú, a Power BI Desktop nem engedi a földrajzi adatkategóriák kiválasztását. 
3. Válassza ki a kívánt kategóriát.

   ![](media/desktop-data-categorization/desktop-data-categorization.png)

Érdekelhetik még további információk a [földrajzi szűrésről a Power BI mobilalkalmazásokhoz](desktop-mobile-geofiltering.md).

