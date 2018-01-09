---
title: "Adatriasztások beállítása a Power BI mobilalkalmazásokban"
description: "Megtudhatja, hogyan állíthat be olyan adatriasztásokat a Power BI-mobilalkalmazásokban, amelyek figyelmeztetik, ha az irányítópultokon lévő adatok meghaladják a beállított korlátokat."
services: powerbi
documentationcenter: 
author: maggiesMSFT
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
ms.date: 12/18/2017
ms.author: maggies
ms.openlocfilehash: c6406a6d1ad4269352ce8421b91f4304fd35c78f
ms.sourcegitcommit: ea247cb3cfc1cac076d4b076c1ad8e2fc37e15a1
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/19/2017
---
# <a name="set-data-alerts-in-the-power-bi-mobile-apps"></a>Adatriasztások beállítása a Power BI mobilalkalmazásokban
A következőkre vonatkozik:

| ![iPhone](media/mobile-set-data-alerts-in-the-mobile-apps/iphone-logo-50-px.png) | ![iPad](media/mobile-set-data-alerts-in-the-mobile-apps/ipad-logo-50-px.png) | ![Android rendszerű telefon](media/mobile-set-data-alerts-in-the-mobile-apps/android-phone-logo-50-px.png) | ![Android rendszerű táblagép](media/mobile-set-data-alerts-in-the-mobile-apps/android-tablet-logo-50-px.png) | ![Android rendszerű táblagép](media/mobile-set-data-alerts-in-the-mobile-apps/win-10-logo-50-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhone-ok |iPadek |Android rendszerű telefonok |Android rendszerű táblagépek |Windows 10-eszközök |

Beállíthat riasztásokat az irányítópulton a Power BI-mobilalkalmazásokban és a Power BI szolgáltatásban is. A riasztások figyelmeztetik, ha egy csempe adatainak változásai meghaladják a beállított korlátokat. A riasztások az egyetlen értéket tartalmazó csempékkel, például kártyákkal és mérőműszerekkel működnek, a streamelési adatokkal azonban nem. A mobileszközön beállított adatriasztásokat megtekintheti a Power BI szolgáltatásban és viszont. Mindenki csak a saját maga által beállított adatriasztásokat látja, még az irányítópultnak vagy a csempe pillanatképének a megosztása esetén is.

Ha Power BI Pro-licenccel rendelkezik, vagy ha ingyenes Power BI-licenccel rendelkezik és a megosztott irányítópult prémium szintű kapacitást használ, beállíthat riasztásokat csempékhez. 

> [!WARNING]
> Az adatalapú riasztások értesítései az adatokkal kapcsolatos információkat tartalmaznak. Ha a mobileszközét ellopják, javasoljuk, hogy a Power BI szolgáltatásban tiltsa le az összes adatalapú riasztási szabályt. 
> 
> További információk [az adatriasztások kezeléséről a Power BI szolgáltatásban](service-set-data-alerts.md).
> 
> 

## <a name="data-alerts-on-an-iphone-or-ipad"></a>Adatriasztások iPhone vagy iPad készüléken
### <a name="set-an-alert-on-an-iphone-or-ipad"></a>Riasztások beállítása iPhone vagy iPad készüléken
1. Koppintson az irányítópult egyik számot vagy mérőműszert tartalmazó csempéjére annak fókusz módban való megnyitásához.  
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-card-visual.png)
2. Riasztás hozzáadásához koppintson a harang ikonra ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-alert-icon.png).  
3. Koppintson a **Riasztási szabály felvétele** gombra.
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-add-alert-rule.png)
4. Válassza ki, hogy egy adott érték felett vagy alatt aktiválódjon a riasztás, majd adja meg az értéket.
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-set-alert-threshold.png)
5. Döntse el, hogy óránként vagy naponta szeretne riasztást kapni, és hogy riasztásokról e-mailben is kapjon-e értesítést.
   
   > [!NOTE]
   > Az óránkénti vagy napi riasztásokat csak abban az esetben kapja meg, ha az érték az adott időtartamban ténylegesen változott.
   > 
   > 
6. A riasztás címét is módosíthatja.
7. Koppintson a **Mentés** gombra.
8. Egy adott csempe rendelkezhet felső és alsó küszöbértékeket jelző riasztásokkal is. A **Riasztások kezelése** felületen koppintson a **Riasztási szabály felvétele** gombra.
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-add-another-alert-rule.png)

### <a name="manage-alerts-on-your-iphone-or-ipad"></a>Riasztások kezelése iPhone vagy iPad készüléken
A riasztásokat egyenként kezelheti a mobileszközökön vagy [az összeset együtt a Power BI szolgáltatásban](service-set-data-alerts.md).

1. Koppintson az irányítópulton az egyik számot vagy mérőműszert tartalmazó csempére, amelyikhez van riasztás rendelve.  
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-card-visual.png)
2. Koppintson a harang ikonra ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-has-alert-icon.png).  
3. Koppintson a riasztás nevére annak szerkesztéséhez, a kapcsolóra az e-mail értesítések kikapcsolásához vagy a szemetesre a riasztás törléséhez.
   
    ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-edit-delete-alert.png)

## <a name="data-alerts-on-an-android-device"></a>Adatriasztások az Android-eszközökön
### <a name="set-an-alert-on-an-android-device"></a>Riasztások beállítása Android-eszközökön
1. A Power BI-irányítópulton koppintson az egyik számot vagy mérőműszert tartalmazó csempére annak megnyitásához.  
2. Riasztás hozzáadásához koppintson a harang ikonra ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-alert-icon.png).  
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-tap-alert.png)
3. Koppintson a plusz ikonra (+).
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-plus-alert.png)
4. Válassza ki, hogy egy adott érték felett vagy alatt aktiválódjon a riasztás, majd írja be az értéket.
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-tablet-set-alert-condition.png)
5. Koppintson a **Kész** gombra.
6. Döntse el, hogy óránként vagy naponta szeretne riasztást kapni, és hogy riasztásokról e-mailben is kapjon-e értesítést.
   
   > [!NOTE]
   > Az óránkénti vagy napi riasztásokat csak abban az esetben kapja meg, ha az érték az adott időtartamban ténylegesen változott.
   > 
   > 
7. A riasztás címét is módosíthatja.
8. Koppintson a **Mentés** gombra.

### <a name="manage-alerts-on-an-android-device"></a>Riasztások kezelése Android-eszközökön
A riasztásokat egyenként kezelheti a Power BI mobilalkalmazásban vagy [az összeset együtt a Power BI szolgáltatásban](service-set-data-alerts.md).

1. Koppintson az irányítópulton az egyik kártyára vagy mérőműszert tartalmazó csempére, amelyikhez van riasztás rendelve.  
2. Koppintson az egyszínű harang ikonra ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-filled-alert-bell.png).  
3. Koppintson a riasztásra, ha módosítani szeretné a küszöbértékét, vagy ki szeretné kapcsolni.
   
    ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-manage-alerts.png)
4. Koppintson a plusz ikonra (+), ha egy újabb riasztást szeretne hozzáadni ugyanahhoz a csempéhez.
5. A riasztás végleges törléséhez koppintson a szemetes ikonra ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-delete-alert-icon.png).

## <a name="data-alerts-on-a-windows-device"></a>Adatriasztások a Windows-eszközökön
### <a name="set-data-alerts-on-a-windows-device"></a>Riasztások beállítása Windows-eszközökön
1. Koppintson az irányítópult egyik számot vagy mérőműszert tartalmazó csempéjére annak megnyitásához.  
2. Riasztás hozzáadásához koppintson a harang ikonra ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-alert-bell-off.png).  
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-tap-alert.png)
3. Koppintson a plusz ikonra (+).
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-no-alerts-yet.png)
4. Válassza ki, hogy egy adott érték felett vagy alatt aktiválódjon a riasztás, majd írja be az értéket.
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-set-alert.png)
5. Döntse el, hogy óránként vagy naponta szeretne riasztást kapni, és hogy riasztásokról e-mailben is kapjon-e értesítést.
   
   > [!NOTE]
   > Az óránkénti vagy napi riasztásokat csak abban az esetben kapja meg, ha az érték az adott időtartamban ténylegesen változott.
   > 
   > 
6. A riasztás címét is módosíthatja.
7. Koppintson a pipa jelre.
8. Egy adott csempe rendelkezhet felső és alsó küszöbértékeket jelző riasztásokkal is. A **Riasztások kezelése** felületen koppintson a plusz jelre (+).
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-add-another-alert.png)

### <a name="manage-alerts-on-a-windows-device"></a>Adatriasztások kezelése Windows-eszközökön
A riasztásokat egyenként kezelheti a Power BI mobilalkalmazásban vagy [az összeset együtt a Power BI szolgáltatásban](service-set-data-alerts.md).

1. Koppintson az irányítópulton az egyik kártyára vagy mérőműszert tartalmazó csempére, amelyikhez van riasztás rendelve.  
2. Koppintson a harang ikonra ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-alert-bell-on.png).  
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-has-alerts.png)
3. Koppintson a riasztásra, ha módosítani szeretné a küszöbértékét, vagy ki szeretné kapcsolni.
   
    ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-add-another-alert.png)
4. A riasztás végleges törléséhez koppintson a **Törlés** gombra, és tartsa megérintve.

## <a name="receiving-alerts"></a>Riasztások fogadása
A riasztások a Power BI [Értesítési központjába](mobile-apps-notification-center.md) érkeznek a mobileszközön vagy a Power BI szolgáltatásban, ugyanúgy, ahogy az Önnel megosztott új irányítópultokról tájékoztató értesítések.

Az adatforrások általában napi frissítésre vannak állítva, némelyik azonban ennél gyakrabban frissül. Az irányítópultok adatainak frissítése során, ha a követett adatok valamelyike eléri valamelyik beállított küszöböt, több dolog történhet.

1. A Power BI ellenőrzi, hogy eltelt-e legalább egy óra vagy 24 óra (a választott beállítástól függően) az utolsó riasztás óta.
   
   Ha az adat meghaladja a küszöböt, a rendszer óránként vagy 24 óránként mindenképp riasztást küld.
2. Ha úgy konfigurálta a riasztást, hogy az e-mailben is értesítse, valami ilyesmit talál majd a bejövő levelei közt.
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/powerbi-alerts-email.png)
3. A Power BI egy üzenetet küld az **Értesítési központba**, és egy új riasztás ikont jelenít meg az érintett csempén ![](media/mobile-set-data-alerts-in-the-mobile-apps/powerbi-alert-tile-notification-icon.png).
4. A globális navigációs gombra ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-alert-global-nav-button.png) koppintva [nyissa meg az **Értesítési központot**](mobile-apps-notification-center.md), és tekintse meg a riasztás részleteit.
   
     ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-notifications.png) 

> [!NOTE]
> A riasztások kizárólag a frissített adatokon működnek. Az egyes adatok frissítésekor a Power BI ellenőrzi, hogy az adott adathoz van-e beállítva riasztás. Ha az adott adat elérte a riasztási küszöböt, a riasztás aktiválódik.
> 
> 

## <a name="tips-and-troubleshooting"></a>Tippek és hibaelhárítás
* A riasztásokat a Bing-csempék, illetve a dátum/idő mértékekkel rendelkező kártyacsempék jelenleg nem támogatják.
* A riasztások kizárólag numerikus adatokkal működnek.
* A riasztások kizárólag a frissített adatokon működnek. Statikus adatokon nem.
* A riasztások streamelési adatokat tartalmazó csempéken nem működnek.

## <a name="next-steps"></a>További lépések
* [Riasztások kezelése a Power BI szolgáltatásban](service-set-data-alerts.md)
* [Power BI mobil értesítési központ](mobile-apps-notification-center.md)
* Kérdése van? [Forduljon a Power BI közösségéhez](http://community.powerbi.com/)

