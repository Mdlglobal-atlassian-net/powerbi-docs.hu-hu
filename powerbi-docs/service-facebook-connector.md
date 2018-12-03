---
title: 'Külső szolgáltatás: Facebook-összekötő a Power BI Desktophoz'
description: 'Külső szolgáltatás: Facebook-összekötő a Power BI Desktophoz'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 66f6fa32ecabecfbaa178b5744e71c80a6020ebd
ms.sourcegitcommit: 2ae660a7b70fce23eb58b159d049eca44a664f2c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/30/2018
ms.locfileid: "52669658"
---
# <a name="facebook-connector-for-power-bi-desktop"></a>Facebook-összekötő a Power BI Desktophoz
A **Power BI Desktop** Facebook-összekötője a Facebook Graph API-ra támaszkodik, ezért az idő során változhatnak a funkciók, és módosulhat az elérhetőség.

Tekintse meg [a Power BI Desktophoz készült Facebook-összekötő útmutatóját](desktop-tutorial-facebook-analytics.md).

A Facebook Graph API 1.0-s verziója 2015. április 30-<sup>án</sup> lejárt. A Power BI a Facebook-összekötő hátterében működő Graph API-t használja az adatokhoz történő csatlakozáshoz és az adatelemzéshez.

Lehet, hogy a 2015. április 30<sup></sup>. előtt készült lekérdezések már nem működnek, vagy kevesebb adatot adnak vissza. 2015. április 30<sup></sup>. óta a Power BI a Facebook API-ra érkező összes híváshoz a 2.8-as verziót használja. Ha a lekérdezése 2015. április 30. előtt készült, és azóta nem használta, valószínűleg újra kell hitelesítenie, hogy jóváhagyást kapjon az általunk kért új engedélyekre.

Bár minden változást igyekszünk követni a frissítések kibocsátásával, az API esetleges módosulásai befolyásolhatják az általunk létrehozott lekérdezések eredményeit. Egyes esetekben előfordulhat, hogy bizonyos lekérdezések már nem kapnak támogatást. E függőség miatt az említett összekötő használata esetén nem garantálhatjuk az eredményes lekérdezéseket.

A Facebook API változásáról további részleteket tekinthet meg [itt](https://developers.facebook.com/docs/apps/changelog#v2_0).

