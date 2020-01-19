---
title: 'Külső szolgáltatás: Facebook-összekötő a Power BI Desktophoz'
description: 'Külső szolgáltatás: Facebook-összekötő a Power BI Desktophoz'
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: dcfc695d0371cce21a827ddfe71b3b4b05863935
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/09/2020
ms.locfileid: "75762416"
---
# <a name="use-the-facebook-connector-for-power-bi-desktop"></a>A Power BI Desktophoz készült Facebook-összekötő használata
A **Power BI Desktop** Facebook-összekötője a Facebook Graph API-ra támaszkodik, ezért az idő során változhatnak a funkciók, és módosulhat az elérhetőség.

Tekintse meg [a Power BI Desktophoz készült Facebook-összekötő útmutatóját](desktop-tutorial-facebook-analytics.md).

A Facebook Graph API 1.0-s verziója 2015. április 30-án lejárt. A Power BI a Facebook-összekötő hátterében működő Graph API-t használja az adatokhoz történő csatlakozáshoz és az adatelemzéshez.

Előfordulhat, hogy a 2015. április 30. előtt készült lekérdezések már nem működnek, vagy kevesebb adatot adnak vissza. 2015. április 30. óta a Power BI a Facebook API-ra érkező összes híváshoz a 2.8-as verziót használja. Ha a lekérdezése 2015. április 30. előtt készült, és azóta nem használta, valószínűleg újra kell hitelesítenie, hogy jóváhagyást kapjon az általunk kért új engedélyekre.

Bár minden változást igyekszünk követni a frissítések kibocsátásával, az API esetleges módosulásai befolyásolhatják az általunk létrehozott lekérdezések eredményeit. Egyes esetekben előfordulhat, hogy bizonyos lekérdezések már nem kapnak támogatást. E függőség miatt az említett összekötő használata esetén nem garantálhatjuk az eredményes lekérdezéseket.

A Facebook API változásáról további részleteket tekinthet meg [itt](https://developers.facebook.com/docs/apps/changelog#v2_0).

