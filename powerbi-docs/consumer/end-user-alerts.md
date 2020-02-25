---
title: 'Oktatóanyag: Adatriasztások beállítása a Power BI szolgáltatás irányítópultjain'
description: Ezen oktatóanyagból megtudhatja, hogyan állíthat be riasztásokat, amelyek figyelmeztetik, ha az irányítópultjain lévő adatok változásai meghaladják a Microsoft Power BI szolgáltatáshoz beállított korlátokat.
author: mihart
ms.reviewer: ''
featuredvideoid: removed
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: tutorial
ms.date: 02/18/2020
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 5f4dc1d1f3e707a59ef81e63be42714c499d050f
ms.sourcegitcommit: f9909731ff5b6b69cdc58e9abf2025b7dee0e536
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77496516"
---
# <a name="tutorial-set-alerts-on-power-bi-dashboards"></a>Oktatóanyag: Riasztások beállítása Power BI-irányítópultokon

[!INCLUDE[consumer-appliesto-ynny](../includes/consumer-appliesto-ynny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Riasztásokat állíthat be, amelyek figyelmeztetik, ha az irányítópultjain lévő adatok változásai a beállított korlátok alá vagy fölé esnek. A riasztások működnek a mérőműszereken, KPI-ken és a kártyákon. Ezt a funkciót még fejlesztjük, ezért olvassa el [az alábbi Tippek és hibaelhárítás szakaszt](#tips-and-troubleshooting).

![csempe, kártya, KPI](media/end-user-alerts/card-gauge-kpi.png)

Mindenki csak a saját riasztásait látja, még az irányítópult megosztása esetén is. A rendszer teljes mértékben szinkronizálja az adatriasztásokat a platformok között, így [a Power BI mobilalkalmazásokban](mobile/mobile-set-data-alerts-in-the-mobile-apps.md) és a Power BI szolgáltatásban is beállíthatja és megtekintheti őket. 

> [!WARNING]
> Ezek a riasztások az adatokkal kapcsolatos információval szolgálnak. Ha Power BI-adatait egy mobileszközön követi, és az adott eszközt ellopják, javasoljuk, hogy a Power BI szolgáltatásban tiltsa le az összes riasztást.
> 

Ez az oktatóanyag a következőket mutatja be.
> [!div class="checklist"]
> * Ki állíthat be riasztásokat
> * Mely vizualizációk támogatják a riasztásokat
> * Kik láthatják a riasztásaimat
> * Működnek-e a riasztások a Power BI Desktopban és Mobile-ban
> * Riasztás létrehozásának módja
> * Hol fogom megkapni a riasztásaimat

Ha még nem regisztrált a Power BI-ra, a kezdés előtt [hozzon létre egy ingyenes próbaverziós fiókot](https://app.powerbi.com/signupredirect?pbi_source=web).

Ebben a példában egy irányítópult kártyacsempéjét használjuk az Értékesítés és Marketing mintaalkalmazásból. Ez az alkalmazás a [Microsoft AppSource-on](https://appsource.microsoft.com) érhető el. Az alkalmazás beszerzésével kapcsolatban az [Alkalmazások telepítése és használata a Power BI-ban](end-user-app-view.md) című témakörben tájékozódhat.

1. Az irányítópult egyik mérőműszer-, KPI- vagy kártyacsempéjén kattintson a három pontra (…).
   
   ![kártyacsempe](media/end-user-alerts/power-bi-cards.png)
2. A harang ikon ![riasztás ikon](media/end-user-alerts/power-bi-bell-icon.png) vagy a **Riasztások kezelése** kiválasztásával adhat hozzá egy vagy több riasztást a **Total Stores** (Összes üzlet) csempéhez.

   ![kártya csempéje kijelölt ellipszisekkel](media/end-user-alerts/power-bi-ellipses.png)

   
1. A **Riasztások kezelése** panelen válassza a **+ Riasztási szabály hozzáadása** lehetőséget.  Ügyeljen rá, hogy a csúszka **Be** állásba legyen kapcsolva, és adjon címet a riasztásnak. A címek segítségével könnyebben felismerheti a riasztásokat.
   
   ![Riasztások kezelése ablak](media/end-user-alerts/power-bi-manage-alert.png)
4. Görgessen le, és adja meg a riasztás adatait.  Ebben a példában most egy olyan riasztást hozunk létre, amely naponta küld értesítést, ha a piaci részesedésünk eléri vagy meghaladja a 35 értéket. A riasztások az Értesítési központban jelennek meg. Azt is beállítjuk, hogy a Power BI egy e-mailt is küldjön.
   
   ![Riasztások kezelése ablak, küszöbérték beállítása](media/end-user-alerts/power-bi-manage-alert-details.png)
5. Válassza a **Mentés és bezárás** lehetőséget.
 
   > [!NOTE]
   > A riasztások kizárólag a frissített adatokon működnek. Az egyes adatok frissítésekor a Power BI ellenőrzi, hogy az adott adathoz van-e beállítva riasztás. Ha az adott adat elérte a riasztási küszöböt, a riasztás aktiválódik. 
   > 

## <a name="receiving-alerts"></a>Riasztások fogadása
Ha egy követett adat eléri valamelyik beállított küszöböt, több dolog történik. Először is a Power BI ellenőrzi, hogy eltelt-e legalább egy óra vagy 24 óra (a választott beállítástól függően) az utolsó riasztás óta. Ha az adat meghaladja a küszöböt, a rendszer mindenképp riasztást küld.

Ezután a Power BI egy riasztást küld az Értesítési központba, valamint választhatóan az e-mail-fiókjába is. Az egyes riasztásokban közvetlen hivatkozás mutat az adatokra. Kattintson a hivatkozásra a vonatkozó csempe megtekintéséhez.  

1. Ha úgy konfigurálta a riasztást, hogy az e-mailben is értesítse, valami ilyesmit talál majd a bejövő levelei közt. Ezt a riasztást egy másik irányítópulton állítottuk be. Ez az irányítópult a Használhatósági csapat által elvégzett feladatokat követi nyomon.
   
   ![Riasztási e-mail](media/end-user-alerts/power-bi-alert-email.png)
2. A Power BI egy üzenetet küld az **Értesítési központba**, és egy új riasztás ikont jelenít meg az érintett csempén.
   
   ![Értesítési ikon a Power BI szolgáltatásban](media/end-user-alerts/power-bi-task-alert.png)
3. A riasztás részleteinek megtekintéséhez nyissa meg az Értesítési központot.
   
    ![riasztás olvasása](media/end-user-alerts/power-bi-notification.png)
   
  

## <a name="managing-alerts"></a>Riasztások kezelése

A riasztásokat többféle módon is kezelheti: Magán az irányítópult csempén, a Power BI Beállítások menüből, az egyes csempéken a [Power BI mobilalkalmazásban iPhone-on](mobile/mobile-set-data-alerts-in-the-mobile-apps.md), vagy [Windows 10-en a Power BI mobilalkalmazásban](mobile/mobile-set-data-alerts-in-the-mobile-apps.md).

### <a name="from-the-tile-itself"></a>Magáról a csempéről

1. Ha módosítani vagy törölni szeretné egy adott csempe valamelyik riasztását, nyissa meg újra a **Riasztások kezelése** ablakot a harang ikon ![riasztás ikon](media/end-user-alerts/power-bi-bell-icon.png) kiválasztásával. Az adott csempéhez beállított összes riasztás megjelenik.
   
    ![Riasztások kezelése ablak](media/end-user-alerts/power-bi-manage-alerts.png).
2. A riasztás módosításához válassza a neve mellett balra található nyilat.
   
    ![Riasztás neve melletti nyíl](media/end-user-alerts/power-bi-modify-alert.png).
3. A riasztás módosításához válassza a neve mellett jobbra található kukát.
   
      ![Kuka ikon kiválasztva](media/end-user-alerts/power-bi-alert-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>A Power BI Beállítások menüjéből

1. Kattintson a fogaskerék ikonra a Power BI menüsorán.
   
    ![fogaskerék ikon](media/end-user-alerts/powerbi-gear-icon.png).
2. A **Beállítások** alatt válassza a **Riasztások** elemet.
   
    ![Riasztások fül a Beállítások ablakban](media/end-user-alerts/power-bi-alert-settings.png)
3. Erről a felületről be- és kikapcsolhatja a riasztásokat, megnyithatja a **Riasztások kezelése** ablakot a riasztás módosításához, vagy akár törölheti is a riasztást.

## <a name="tips-and-troubleshooting"></a>Tippek és hibaelhárítás 

* Riasztásokat csak mérőműszereken, KPI-ken és kártyákon lehet beállítani.
* Ha nem tud riasztást beállítani mérőműszerre, KPI-re vagy kártyára, kérjen segítséget a rendszergazdától. Időnként a riasztások ki vannak kapcsolva, vagy nem érhetők el az irányítópulthoz vagy az irányítópult-csempék bizonyos típusaihoz.
* A riasztások kizárólag a frissített adatokon működnek. Statikus adatokon nem. A Microsoft által megadott minták többsége statikus. 
* Nem a *fogyasztók* hozzák létre saját irányítópultjaikat, irányítópultokat a *készítők* hoznak létre és osztanak meg a fogyasztókkal. Megosztott tartalom fogadásához és megtekintéséhez Power BI Pro vagy Prémium licenc szükséges. További információ: [Milyen licenccel rendelkezem?](end-user-license.md) 


## <a name="clean-up-resources"></a>Erőforrások felszabadítása
A riasztások törlésére vonatkozó utasítások fent olvashatók. Röviden összefoglalva válassza a fogaskerék ikont a Power BI menüsorán. A **Beállítások** alatt válassza a **Riasztások** elemet, és törölje a riasztást.

> [!div class="nextstepaction"]
> [Adatriasztások beállítása mobileszközökön](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)


