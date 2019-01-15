---
title: Egy meghatározott helyre mutató hivatkozás létrehozása a Power BI-mobilalkalmazásokban
description: Megtudhatja, hogyan hozhat létre a Power BI-mobilalkalmazásban meghatározott irányítópultra, csempére vagy jelentésre mutató mélyhivatkozást URI használatával.
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 06/28/2018
ms.author: mshenhav
ms.openlocfilehash: ccb3b390b0654c7dc850cf66a7f0c9a7ec02f910
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54278400"
---
# <a name="create-a-link-to-a-specific-location-in-the-power-bi-mobile-apps"></a>A Power BI-mobilalkalmazásokon belül egy meghatározott helyre mutató hivatkozás létrehozása
URI létrehozásával és használatával a Power BI-mobilalkalmazásokon belüli meghatározott helyre mutató hivatkozást hozhat létre (*mélyhivaktozás*) az összes mobilplatformon: iOS, Android-eszközök és Windows 10.

Az URI-hivatkozások mutathatnak közvetlenül irányítópultokra, csempékre és jelentésekre.

A mélyhivatkozás célja határozza meg az URI formátumát. Kövesse ezeket a lépéseket különböző helyekre mutató mélyhivatkozások létrehozásához. 

## <a name="open-the-power-bi-mobile-app"></a>A Power BI-mobilalkalmazás megnyitása
Ezzel az URI-vel bármely eszközön megnyithatja a Power BI-mobilalkalmazást:

    mspbi://app/


## <a name="open-to-a-specific-dashboard"></a>Meghatározott irányítópult megnyitása
Ezzel az URI-vel megnyithat a Power BI-mobilalkalmazásban egy meghatározott irányítópultot:

    mspbi://app/OpenDashboard?DashboardObjectId=<36-character-dashboard-id>

A 36 karakterből álló irányítópultobjektum-azonosító megkereséséhez lépjen a Power BI szolgáltatásban az adott irányítópultra (https://powerbi.com)). Nézze meg például ennek az URL-nek a kiemelt szakaszát:

`https://powerbi.com/groups/me/dashboards/**61b7e871-cb98-48ed-bddc-6572c921e270**`

Ha az irányítópult a Saját munkaterület csoporton kívül egy másik csoportban található, adja hozzá a következőt az irányítópult azonosítója előtt vagy után: `&GroupObjectId=<36-character-group-id>`. Például: 

mspbi://app/OpenDashboard?DashboardObjectId=e684af3a-9e7f-44ee-b679-b9a1c59b5d60 **&GroupObjectId=8cc900cc-7339-467f-8900-fec82d748248**

Ne feledkezzen meg a kettő közötti és (&) jelről.

## <a name="open-to-a-specific-tile-in-focus"></a>Meghatározott csempe megnyitása fókuszált módban
Ez az URI egy meghatározott csempét nyit meg fókuszált módban a Power BI-mobilalkalmazásban:

    mspbi://app/OpenTile?DashboardObjectId=<36-character-dashboard-id>&TileObjectId=<36-character-tile-id>

Az irányítópult és a csempe 36 karakterből álló objektumazonosítójának megkereséséhez lépjen az adott irányítópultra a Power BI szolgáltatásban (https://powerbi.com)), és nyissa meg a csempét fókuszált módban. Nézze meg például ennek az URL-nek a kiemelt szakaszait:

`https://powerbi.com/groups/me/dashboards/**3784f99f-b460-4d5e-b86c-b6d8f7ec54b7**/tiles/**565f9740-5131-4648-87f2-f79c4cf9c5f5**/infocus`

Ehhez a csempéhez az URI a következő lesz:

    mspbi://app/OpenTile?DashboardObjectId=3784f99f-b460-4d5e-b86c-b6d8f7ec54b7&TileObjectId=565f9740-5131-4648-87f2-f79c4cf9c5f5

Ne feledkezzen meg a kettő közötti és (&) jelről.

Ha az irányítópult a Saját munkaterületen kívül egy másik csoportban található, adja hozzá a következőt: `&GroupObjectId=<36-character-group-id>`

## <a name="open-to-a-specific-report"></a>Meghatározott jelentés megnyitása
Ez az URI egy meghatározott jelentést nyit meg a Power BI-mobilalkalmazásban:

    mspbi://app/OpenReport?ReportObjectId=<36-character-report-id>

A 36 karakterből álló jelentésobjektum-azonosító megkereséséhez navigáljon a Power BI szolgáltatásban az adott jelentéshez (https://powerbi.com)). Nézze meg például ennek az URL-nek a kiemelt szakaszát:

`https://powerbi.com/groups/me/reports/df9f0e94-31df-450b-b97f-4461a7e4d300`

Ha a jelentés a Saját munkaterület csoporton kívül egy másik csoportban található, adja hozzá a következőt a jelentés azonosítója előtt vagy után: `&GroupObjectId=<36-character-group-id>`. Például: 

mspbi://app/OpenReport?ReportObjectId=e684af3a-9e7f-44ee-b679-b9a1c59b5d60 **&GroupObjectId=8cc900cc-7339-467f-8900-fec82d748248**

Ne feledkezzen meg a kettő közötti és (&) jelről.

## <a name="open-to-a-specific-report-page"></a>Meghatározott jelentésoldal megnyitása
Ez az URI egy meghatározott jelentésoldalt nyit meg a Power BI-mobilalkalmazásban:

    mspbi://app/OpenReport?ReportObjectId=<36-character-report-id>&reportPage=ReportSection<number>

A jelentésoldal neve „ReportSection”, amelyet egy szám követ. Nyissa meg ismét a jelentést a Power BI szolgáltatásban (https://powerbi.com)), és navigáljon az adott jelentésoldalra. 

Nézze meg például ennek az URL-nek a kiemelt szakaszát:

`https://powerbi.com/groups/me/reports/df9f0e94-31df-450b-b97f-4461a7e4d300/ReportSection11`

## <a name="open-in-full-screen-mode"></a>Megnyitás teljes képernyős módban
Egy adott jelentés teljes képernyős módban való megnyitásához adja hozzá a félkövérrel szedett paramétert:

    mspbi://app/OpenReport?ReportObjectId=<36-character-report-id>**&openFullScreen=true**

Például: 

mspbi://app/OpenReport?ReportObjectId=500217de-50f0-4af1-b345-b81027224033&openFullScreen=true

## <a name="add-context-optional"></a>Kontextus hozzáadása (nem kötelező)
A sztringhez kontextust is adhat. Ekkor, ha kapcsolatba kell lépnie velünk, a kontextus használatával szűrhetjük az adatainkat az alkalmazásához. Adja hozzá a hivatkozáshoz a következőt: `&context=<app-name>`

Nézze meg például ennek az URL-nek a kiemelt szakaszát: 

`https://powerbi.com/groups/me/reports/df9f0e94-31df-450b-b97f-4461a7e4d300/&context=SlackDeepLink`

## <a name="next-steps"></a>Következő lépések
A visszajelzése segít eldönteni, hogy milyen fejlesztésekre koncentráljunk a jövőben, ezért kérjük, ne mulasszon el szavazni más szolgáltatásokra, amelyeket szívesen látna a Power BI-mobilalkalmazásokban. 

* [Power BI-alkalmazások mobileszközökre](mobile-apps-for-mobile-devices.md)
* @MSPowerBI követése Twitteren
* Vegyen részt [a Power BI-közösség](http://community.powerbi.com/) beszélgetéseiben
* [Mi az a Power BI?](../../power-bi-overview.md)

