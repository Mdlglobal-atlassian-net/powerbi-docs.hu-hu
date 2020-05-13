---
title: 'Külső szolgáltatás: Facebook-összekötő a Power BI Desktophoz'
description: 'Külső szolgáltatás: Facebook-összekötő a Power BI Desktophoz'
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/20/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 882cddf7728a27e78056a35c14fde20f00678e33
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83309544"
---
# <a name="use-the-facebook-connector-for-power-bi-desktop"></a>A Power BI Desktophoz készült Facebook-összekötő használata
A **Power BI Desktop** Facebook-összekötője a Facebook Graph API-ra támaszkodik, ezért az idő során változhatnak a funkciók, és módosulhat az elérhetőség.

Tekintse meg [a Power BI Desktophoz készült Facebook-összekötő útmutatóját](desktop-tutorial-facebook-analytics.md).

> [!IMPORTANT]
> **Értesítés a Facebook-adatösszekötő elavulásáról:** 2020 áprilisától a Facebook-adatok Excelbe importálásának és frissítésének a lehetősége nem működik megfelelően. Addig még használhatja a *Beolvasás és átalakítás (Power Query)* Facebook-összekötőt. A megadott dátum után nem fog tudni a Facebookhoz csatlakozni és hibaüzenetet kap. Javasoljuk, hogy a váratlan eredmények elkerülése érdekében minél hamarabb vizsgálja felül vagy távolítsa el a Facebook-összekötőt használó *Beolvasás és átalakítás (Power Query)* meglévő lekérdezéseit.


A Facebook Graph API 1.0-s verziója 2015. április 30-án lejárt. A Power BI a Facebook-összekötő hátterében működő Graph API-t használja az adatokhoz történő csatlakozáshoz és az adatelemzéshez.

Előfordulhat, hogy a 2015. április 30. előtt készült lekérdezések már nem működnek, vagy kevesebb adatot adnak vissza. 2015. április 30. óta a Power BI a Facebook API-ra érkező összes híváshoz a 2.8-as verziót használja. Ha a lekérdezése 2015. április 30. előtt készült, és azóta nem használta, valószínűleg újra kell hitelesítenie, hogy jóváhagyást kapjon az általunk kért új engedélyekre.

Bár minden változást igyekszünk követni a frissítések kibocsátásával, az API esetleges módosulásai befolyásolhatják az általunk létrehozott lekérdezések eredményeit. Egyes esetekben előfordulhat, hogy bizonyos lekérdezések már nem kapnak támogatást. E függőség miatt az említett összekötő használata esetén nem garantálhatjuk az eredményes lekérdezéseket.

A Facebook API változásáról további részleteket tekinthet meg [itt](https://developers.facebook.com/docs/apps/changelog#v2_0).

