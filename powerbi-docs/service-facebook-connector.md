---
title: 'Külső szolgáltatás: Facebook-összekötő a Power BI Desktophoz'
description: 'Külső szolgáltatás: Facebook-összekötő a Power BI Desktophoz'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: a8b37606b602a24aa4a0995e138a52a86e0f945c
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54295611"
---
# <a name="facebook-connector-for-power-bi-desktop"></a>Facebook-összekötő a Power BI Desktophoz
A **Power BI Desktop** Facebook-összekötője a Facebook Graph API-ra támaszkodik, ezért az idő során változhatnak a funkciók, és módosulhat az elérhetőség.

Tekintse meg [a Power BI Desktophoz készült Facebook-összekötő útmutatóját](desktop-tutorial-facebook-analytics.md).

A Facebook Graph API 1.0-s verziója 2015. április 30-<sup>án</sup> lejárt. A Power BI a Facebook-összekötő hátterében működő Graph API-t használja az adatokhoz történő csatlakozáshoz és az adatelemzéshez.

Lehet, hogy a 2015. április 30<sup></sup>. előtt készült lekérdezések már nem működnek, vagy kevesebb adatot adnak vissza. 2015. április 30<sup></sup>. óta a Power BI a Facebook API-ra érkező összes híváshoz a 2.8-as verziót használja. Ha a lekérdezése 2015. április 30. előtt készült, és azóta nem használta, valószínűleg újra kell hitelesítenie, hogy jóváhagyást kapjon az általunk kért új engedélyekre.

Bár minden változást igyekszünk követni a frissítések kibocsátásával, az API esetleges módosulásai befolyásolhatják az általunk létrehozott lekérdezések eredményeit. Egyes esetekben előfordulhat, hogy bizonyos lekérdezések már nem kapnak támogatást. E függőség miatt az említett összekötő használata esetén nem garantálhatjuk az eredményes lekérdezéseket.

A Facebook API változásáról további részleteket tekinthet meg [itt](https://developers.facebook.com/docs/apps/changelog#v2_0).

