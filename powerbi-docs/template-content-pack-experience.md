---
title: Sablonalapú tartalomcsomagokkal kapcsolatos felhasználó élmény a Power BI-ban
description: Sablonalapú tartalomcsomagokkal kapcsolatos felhasználó élmény
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/09/2017
ms.author: maggies
ms.openlocfilehash: f1010557bdd781fac9542c2636424e7e2bef2c26
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54288267"
---
# <a name="template-content-pack-experiences-in-power-bi"></a>Sablonalapú tartalomcsomagokkal kapcsolatos felhasználó élmény a Power BI-ban
Ez a szakasz egy tipikus felhasználó élményt emel ki, amikor egy felhasználó egy ISV-[tartalomcsomaghoz](service-connect-to-services.md) csatlakozik.

Próbálja ki maga is a csatlakozási élményt: csatlakozzon egy kiadott tartalomcsomaghoz a https://app.powerbi.com/getdata/services webhelyen (például az alább ismertetett [GitHub-tartalomcsomaghoz](https://app.powerbi.com/getdata/services/github)).

## <a name="connect"></a>Kapcsolódás
Első lépésként egy felhasználó a tartalomcsomag-katalógusban tallózással kiválaszt egy tartalomcsomagot, amelyhez kapcsolódik. A tartalomcsomag-bejegyzés a név, az ikon és a leíró szöveg révén biztosít további információkat a felhasználó számára.

![kapcsolódás](media/template-content-pack-experience/github_data.png)

![kapcsolódás](media/template-content-pack-experience/github_connect.png)

## <a name="parameters"></a>Paraméterek
A kiválasztást követően a rendszer a vállalati hitelesítő adatok megadását fogja kérni a felhasználótól (ha szükséges). A paraméterek párbeszédpanelt deklaratívan adja meg a szerző a tartalomcsomag létrehozása során.

Jelenleg a paraméterek felhasználói felületet nagyon alapszintű – nincs mód a legördülő listák számozására és az adatbemenet-ellenőrzés csak RegEx típusú lehet.

![paraméterek](media/template-content-pack-experience/github_params.png)

## <a name="credentials"></a>Hitelesítő adatok
A paraméterek után a rendszer bejelentkezésre szólítja fel a felhasználót.  Ha a forrás több hitelesítési típust támogat, a felhasználónak kell kiválasztania a megfelelő lehetőséget. Ha a forrás OAuth-hitelesítést kér, megjelenik a szolgáltatás bejelentkezési felhasználói felülete, amikor a felhasználó megnyomja a Bejelentkezés gombot.  Máskülönben a felhasználó megadhatja a hitelesítő adatait a megjelenő párbeszédpanelen.

![Hitelesítő adatok](media/template-content-pack-experience/github_login.png)

![kapcsolódás](media/template-content-pack-experience/github_creds2.png)

## <a name="instantiation"></a>Példányosítás
Amikor sikerül a bejelentkezés, a tartalomcsomagban található összetevők (modell, jelentések és irányítópult) megjelennek a navigációs sávon.  Ezeket az összetevőket a rendszer minden felhasználói fiókhoz hozzáadja.  Az adatokat a rendszer aszinkron módon tölti be az adatkészlet (modell) feltöltéséhez.  Ezután a felhasználó használhatja az irányítópultot, a jelentéseket és a modellt.

Alapértelmezés szerint a felhasználóhoz egy napi frissítési ütemezés van konfigurálva, ez újraértékeli a modellben szereplő lekérdezéseket.  A felhasználóhoz megadott hitelesítő adatoknak lehetővé kell tenniük számára, hogy az adatokat a távollétében is frissítse.

![Példányosítás](media/template-content-pack-experience/github_dashboard.png)

## <a name="exploration-and-monitoring"></a>Vizsgálat és monitorozás
Amint a tartalomcsomagot a rendszer betöltötte a felhasználó fiókjába, a felhasználó elkezdheti az adatok/elemzések vizsgálatát és monitorozását.

Ez általában a következőket jelenti:

* Az irányítópult megtekintése és testreszabása.
* A jelentés megtekintése és testreszabása.
* Kérdések feltétele az adatokkal kapcsolatban természetes nyelven
* A vizsgálati vászon használata az adatmodell adatainak vizsgálatára

Megfontolandó a természetes nyelv modellezésének (szinonimák) és érthető modellsémáknak a használata a jobb vizsgálati élmény érdekében.

