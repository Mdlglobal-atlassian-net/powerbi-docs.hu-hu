---
title: Prémium szintű Power BI-kapacitás újraindítása
description: Útmutató teljesítmény-problémák kezeléséhez prémium szintű Power BI-kapacitás újraindításával.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/17/2019
LocalizationGroup: Premium
ms.openlocfilehash: 1622e06cd7aa394d384954b393d1e547e87df10a
ms.sourcegitcommit: 57e45f291714ac99390996a163436fa1f76db427
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71305656"
---
# <a name="restart-a-power-bi-premium-capacity"></a>Prémium szintű Power BI-kapacitás újraindítása

Megtörténhet, hogy Power BI-rendszergazdaként újra kell indítania egy prémium szintű kapacitást. Ez a cikk a kapacitások újraindításának módját ismerteti, és az újraindítással és teljesítménnyel kapcsolatos más kérdésekre is kitér.

## <a name="why-does-power-bi-provide-this-option"></a>Miért kínálja a Power BI ezt a lehetőséget?

A Power BI óriási adattömegeken végzett összetett elemzések lehetőségét kínálja a felhasználóknak. Sajnos a felhasználók teljesítmény-problémákat is okozhatnak azzal, hogy túlterhelik a Power BI szolgáltatást feladatokkal, túlságosan bonyolult lekérdezések írásával, körkörös hivatkozások létrehozásával, és sok más módon is.

A megosztott Power BI-kapacitás azáltal nyújt némi védelmet az ilyen helyzetek ellen, hogy korlátozásokat érvényesít a fájlméretre, a frissítés ütemezésére, és a szolgáltatás más jellemzőire. Prémium szintű Power BI-kapacitásban azonban ezek a korlátok többnyire magasabbak. Ennek következtében egy helytelen DAX-kifejezést vagy nagyon összetett modellt tartalmazó egyetlen jelentés is jelentős teljesítménybeli problémákat okozhat. A feldolgozás során a jelentés akár a kapacitásban rendelkezésre álló összes erőforrást is felhasználhatja. 

A Power BI egyre fejlettebb módokon védi a prémium szintű kapacitások felhasználóit az ilyen problémákkal szemben. A rendszergazdákat is ellátjuk olyan eszközökkel, amelyekkel elemezni tudják a kapacitások túlterhelését és annak okait. Erről [rövid tanfolyamunkon](https://www.youtube.com/watch?v=UgsjMbhi_Bk&feature=youtu.be) és [hosszabb tanfolyamunkon](https://www.microsoft.com/businessapplicationssummit/video/BAS2018-2174) tudhat meg többet. Mindezek mellett a felmerülő súlyos problémák következményeinek mérséklésére is képesnek kell lennie. Az ilyen problémák leggyorsabb megoldása a kapacitás újraindítása.

## <a name="is-the-restart-process-safe-will-i-lose-any-data"></a>Biztonságos az újraindítási eljárás? Veszíthetek adatot?

A kapacitásában lévő összes mentett adat, definíció, jelentés és irányítópult teljesen sértetlen marad az újraindítás során. Egy kapacitás újraindításának idejére minden folyamatban lévő ütemezett vagy alkalmi frissítés le lesz állítva. A szolgáltatás újra megkísérli a frissítéseket, amikor a kapacitás elérhetővé válik. A kapacitást használó felhasználók nem mentett munkája elvész. Nekik az újraindítás befejeződése után frissíteniük kell a böngészőjüket.

## <a name="how-do-i-restart-a-capacity"></a>Hogyan indíthatok újra egy kapacitást?

Kapacitás az alábbi lépésekben indítható újra.

1. Keresse meg kapacitását a Power BI felügyeleti portáljának **Kapacitásbeállítások** lapján. 

1. A kapacitás URL-címéhez fűzze hozzá a **CapacityRestart** *funkciójelzőt*: https://app.powerbi.com/admin-portal/capacities/<YourCapacityId>?capacityRestartButton=true.

1. A **Speciális beállítások** > **KAPACITÁS ÚJRAINDÍTÁSA** alatt válassza a **Kapacitás újraindítása** lehetőséget.

    ![Kapacitás újraindítása](media/service-admin-premium-restart/restart-capacity.png)

1. A **Kapacitás újraindítása** párbeszédablakban válassza az **Igen, újraindítom a kapacitást** választ.

    ![Újraindítás jóváhagyása](media/service-admin-premium-restart/confirm-restart.png)

## <a name="how-can-i-prevent-issues-from-happening-in-the-future"></a>Hogyan akadályozhatom meg a problémák jövőbeni keletkezését?

A problémák elkerülésének legjobb módszere hatékony adatmodellezésre tanítani a felhasználókat. További információt [képzési anyagunkban](https://www.microsoft.com/businessapplicationssummit/video/BAS2018-2170) talál.

Emellett javasoljuk a [kapacitások rendszeres figyelését](service-admin-premium-monitor-capacity.md) a mögöttes problémákra utaló trendek felismerése érdekébe. Tervezzük a figyelő alkalmazás és sok más eszköz rendszeres frissítését, hogy Ön még hatékonyabban figyelhesse és kezelhesse kapacitásait.

## <a name="next-steps"></a>Következő lépések

[Mi a Power BI Premium?](service-premium-what-is.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
