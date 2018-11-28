---
title: 'Oktatóanyag: Adatriasztások beállítása a Power BI szolgáltatásban'
description: Ezen oktatóanyagból megtudhatja, hogyan állíthat be riasztásokat, amelyek figyelmeztetik, ha az irányítópultjain lévő adatok változásai meghaladják a Microsoft Power BI szolgáltatásban beállított korlátokat.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: JbL2-HJ8clE
ms.service: powerbi
ms.component: powerbi-service
ms.topic: tutorial
ms.date: 10/08/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 7982c2b29d5d92a992a115c92cbc7f0d128cb9d6
ms.sourcegitcommit: fdb54145f9bc93b312409c15c603749f3a4a876e
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52452591"
---
# <a name="tutorial-set-data-alerts-in-power-bi-service"></a>Oktatóanyag: Adatriasztások beállítása a Power BI szolgáltatásban
Riasztásokat állíthat be, amelyek figyelmeztetik, ha az irányítópultjain lévő adatok változásai meghaladják a beállított korlátokat. 

Ha Power BI Pro-licenccel rendelkezik, vagy ha egy [prémium szintű kapacitásból](../service-premium.md) osztottak meg Önnel egy irányítópultot, beállíthat riasztásokat a csempékhez. Csak a jelentések vizualizációiról rögzített csempéken, és kizárólag mérőműszerekhez, KPI-khez és kártyákhoz állíthatók be riasztások. A riasztásokat beállíthatja a jelentésekből az irányítópultokra rögzített streamelési adatkészletekről készített vizualizációkon, azonban az irányítópultokon a **Csempe hozzáadása** > **Egyedi folyamatos átviteli adatok** paranccsal közvetlenül létrehozott streamelési csempéken nem. 

Mindenki csak a saját riasztásait látja, még az irányítópult megosztása esetén is. A rendszer teljes mértékben szinkronizálja az adatriasztásokat a platformok között, így [a Power BI mobilalkalmazásokban](mobile/mobile-set-data-alerts-in-the-mobile-apps.md) és a Power BI szolgáltatásban is beállíthatja és megtekintheti őket. 

![címek](../media/service-set-data-alerts/powerbi-alert-types-new.png)

> [!WARNING]
> Az adatalapú riasztások értesítései az adatokkal kapcsolatos információkat tartalmaznak. Ha Power BI-adatait egy mobileszközön követi, és az adott eszközt ellopják, javasoljuk, hogy a Power BI szolgáltatásban tiltsa le az összes adatalapú riasztási szabályt.
> 

Ez az oktatóanyag a következőket mutatja be.
> [!div class="checklist"]
> * Ki állíthat be riasztásokat
> * Mely vizualizációk támogatják a riasztásokat
> * Kik láthatják a riasztásaimat
> * Működnek-e a riasztások a Power BI Desktopban és Mobile-ban
> * Hogyan hozhatok létre riasztást
> * Hol fogom megkapni a riasztásaimat

Ha még nem regisztrált a Power BI-ra, a kezdés előtt [hozzon létre egy ingyenes próbaverziós fiókot](https://app.powerbi.com/signupredirect?pbi_source=web).

## <a name="set-data-alerts-in-power-bi-service"></a>Adatriasztások beállítása a Power BI szolgáltatásban
Tekintse meg, ahogy Amanda riasztásokat ad hozzá egyes csempékhez az irányítópultján. Ezután a videó alatt látható részletes utasításokat követve próbálkozzon meg a feladat elvégzésével.

<iframe width="560" height="315" src="https://www.youtube.com/embed/JbL2-HJ8clE" frameborder="0" allowfullscreen></iframe>

A példában Amanda a [Retail Analysis](http://go.microsoft.com/fwlink/?LinkId=529778) (Kiskereskedelmi elemzés) minta-irányítópultról származó kártyacsempét használ.

1. Az irányítópult egyik mérőműszer-, KPI- vagy kártyacsempéjén kattintson a három pontra (…).
   
   ![Összes üzlet csempe](media/end-user-alerts/powerbi-card.png)
2. A harang ikon ![riasztás ikon](media/end-user-alerts/power-bi-bell-icon.png) vagy a **Riasztások kezelése** kiválasztásával adhat hozzá egy vagy több riasztást a **Total Stores** (Összes üzlet) csempéhez.
   
1. A **Riasztások kezelése** panelen válassza a **+ Riasztási szabály hozzáadása** lehetőséget.  Ügyeljen rá, hogy a csúszka **Be** állásba legyen kapcsolva, és adjon címet a riasztásnak. A címek segítségével könnyebben felismerheti a riasztásokat.
   
   ![Riasztások kezelése ablak](media/end-user-alerts/powerbi-alert-title.png)
4. Görgessen le, és adja meg a riasztás adatait.  Ebben a példában most egy olyan riasztást állítunk be, amely napi küld értesítést, ha az üzletek száma 100 fölé emelkedik. A riasztások az Értesítési központban jelennek meg. Azt is beállítjuk, hogy a Power BI egy e-mailt is küldjön.
   
   ![Riasztások kezelése ablak, küszöbérték beállítása](media/end-user-alerts/power-bi-set-alert-details.png)
5. Válassza a **Mentés és bezárás** lehetőséget.

## <a name="receiving-alerts"></a>Riasztások fogadása
Ha egy követett adat eléri valamelyik beállított küszöböt, több dolog történik. Először is a Power BI ellenőrzi, hogy eltelt-e legalább egy óra vagy 24 óra (a választott beállítástól függően) az utolsó riasztás óta. Ha az adat meghaladja a küszöböt, a rendszer mindenképp riasztást küld.

Ezután a Power BI egy riasztást küld az Értesítési központba, valamint választhatóan az e-mail-fiókjába is. Az egyes riasztásokban közvetlen hivatkozás mutat az adatokra. Kattintson a hivatkozásra a vonatkozó csempe megtekintéséhez.  

1. Ha úgy konfigurálta a riasztást, hogy az e-mailben is értesítse, valami ilyesmit talál majd a bejövő levelei közt.
   
   ![Riasztási e-mail](media/end-user-alerts/powerbi-alerts-email.png)
2. A Power BI egy üzenetet küld az **Értesítési központba**, és egy új riasztás ikont jelenít meg az érintett csempén.
   
   ![Értesítési ikon a Power BI szolgáltatásban](media/end-user-alerts/powerbi-alert-notifications.png)
3. A riasztás részleteinek megtekintéséhez nyissa meg az Értesítési központot.
   
    ![riasztás olvasása](media/end-user-alerts/powerbi-alert-notification.png)
   
   > [!NOTE]
   > A riasztások kizárólag a frissített adatokon működnek. Az egyes adatok frissítésekor a Power BI ellenőrzi, hogy az adott adathoz van-e beállítva riasztás. Ha az adott adat elérte a riasztási küszöböt, a riasztás aktiválódik.
   > 
   > 

## <a name="managing-alerts"></a>Riasztások kezelése
A riasztások számos módon kezelhetők: Magával az irányítópult csempéjével, a Power BI-beállítások menüjében, illetve egy adott csempével az [iPhone-on futtatott Power BI-mobilalkalmazásban](mobile/mobile-set-data-alerts-in-the-mobile-apps.md) vagy a [Windows 10-hez készült Power BI-mobilalkalmazásban](mobile/mobile-set-data-alerts-in-the-mobile-apps.md).

### <a name="from-the-tile-itself"></a>Magáról a csempéről
1. Ha módosítani vagy törölni szeretné egy adott csempe valamelyik riasztását, nyissa meg újra a **Riasztások kezelése** ablakot a harang ikon ![riasztás ikon](media/end-user-alerts/power-bi-bell-icon.png) kiválasztásával. Az adott csempéhez beállított összes riasztás megjelenik.
   
    ![Riasztások kezelése ablak](media/end-user-alerts/powerbi-see-alerts.png).
2. A riasztás módosításához válassza a neve mellett balra található nyilat.
   
    ![Riasztás neve melletti nyíl](media/end-user-alerts/powerbi-see-alerts-arrow.png).
3. A riasztás módosításához válassza a neve mellett jobbra található kukát.
   
      ![Kuka ikon kiválasztva](media/end-user-alerts/powerbi-see-alerts-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>A Power BI Beállítások menüjéből
1. Kattintson a fogaskerék ikonra a Power BI menüsorán.
   
    ![fogaskerék ikon](media/end-user-alerts/powerbi-gear-icon.png).
2. A **Beállítások** alatt válassza a **Riasztások** elemet.
   
    ![Riasztások fül a Beállítások ablakban](media/end-user-alerts/powerbi-alert-settings.png)
3. Erről a felületről be- és kikapcsolhatja a riasztásokat, megnyithatja a **Riasztások kezelése** ablakot a riasztás módosításához, vagy akár törölheti is a riasztást.

## <a name="tips-and-troubleshooting"></a>Tippek és hibaelhárítás
* A Bing-csempék, illetve a dátum/idő mértékekkel rendelkező kártyacsempék jelenleg nem támogatják a riasztásokat.
* A riasztások kizárólag numerikus adattípusokkal működnek.
* A riasztások kizárólag a frissített adatokon működnek. Statikus adatokon nem.
* A riasztások a streamelési adatkészleteken csak akkor működnek, ha felépít egy KPI-/kártya-/mérőműszer-jelentési vizualizációt, majd rögzíti az irányítópulton.

## <a name="clean-up-resources"></a>Erőforrások felszabadítása
A riasztások törlésére vonatkozó utasítások fent olvashatók. Röviden összefoglalva válassza a fogaskerék ikont a Power BI menüsorán. A **Beállítások** alatt válassza a **Riasztások** elemet, és törölje a riasztást.

> [!div class="nextstepaction"]
> [Adatriasztások beállítása mobileszközökön](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)


