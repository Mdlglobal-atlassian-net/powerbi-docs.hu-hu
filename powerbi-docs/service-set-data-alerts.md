---
title: Adatriasztások beállítása a Power BI szolgáltatásban
description: Itt elsajátíthatja, hogyan állíthat be riasztásokat, amelyek figyelmeztetik, ha az irányítópultjain lévő adatok változásai meghaladják a Microsoft Power BI szolgáltatásban beállított korlátokat.
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: JbL2-HJ8clE
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/21/2019
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: e26b50d571cfffeae1c93f37e715eca24ff4f12e
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73871561"
---
# <a name="data-alerts-in-the-power-bi-service"></a>Adatriasztások a Power BI szolgáltatásban

Riasztásokat állíthat be, amelyek figyelmeztetik, ha az irányítópultjain lévő adatok változásai meghaladják a beállított korlátokat.

Ha Power BI Pro-licenccel rendelkezik, beállíthat riasztásokat csempékhez. Akkor is beállíthat riasztásokat, ha valaki megoszt egy [Premium-kapacitású](service-premium-what-is.md) irányítópultot. Csak a jelentések vizualizációiról rögzített csempéken, és kizárólag mérőműszerekhez, KPI-khez és kártyákhoz állíthatók be riasztások. A riasztások olyan vizualizációkon állíthatók be, amelyeket egy jelentésből egy irányítópulton rögzített streamelési adatkészletekből hozott létre. Nem állíthatók be riasztások a közvetlenül az irányítópulton, a **Csempe hozzáadása** > **Egyéni streamelési adatok** funkcióval létrehozott csempéken.

Mindenki csak a saját riasztásait látja, még az irányítópult megosztása esetén is. Az irányítópult saját nézetén beállított riasztásokat még az irányítópult tulajdonosa sem láthatja. A rendszer teljes mértékben szinkronizálja az adatriasztásokat a platformok között, így [a Power BI mobilalkalmazásokban](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md) és a Power BI szolgáltatásban is beállíthatja és megtekintheti őket. A Power BI Desktopban azonban nem érhetők el. A riasztások automatizálhatók és integrálhatók a Microsoft Flow-val is. Ezt a funkciót kipróbálhatja a [Microsoft Flow-t és a Power BI-t ismertető](service-flow-integration.md) cikkben.

![címek](media/service-set-data-alerts/powerbi-alert-types-new.png)

> [!WARNING]
> Az adatalapú riasztások értesítései az adatokkal kapcsolatos információkat tartalmaznak. Ha Power BI-adatait egy mobileszközön követi, és az adott eszközt ellopják, javasoljuk, hogy a Power BI szolgáltatásban tiltsa le az összes adatalapú riasztási szabályt.

## <a name="set-data-alerts-in-the-power-bi-service"></a>Adatriasztások beállítása a Power BI szolgáltatásban

Tekintse meg, ahogy Amanda riasztásokat ad hozzá egyes csempékhez az irányítópultján. Ezután a videó alatt látható részletes utasításokat követve próbálkozzon meg a feladat elvégzésével.

<iframe width="560" height="315" src="https://www.youtube.com/embed/JbL2-HJ8clE" frameborder="0" allowfullscreen></iframe>

A példában Amanda a Retail Analysis (Kiskereskedelmi elemzés) minta-irányítópultról származó kártyacsempét használ. A leírás követéséhez nyissa meg a [Kiskereskedelmi elemzési mintát](sample-retail-analysis.md#get-the-content-pack-for-this-sample).

1. Kezdje a műveletet egy irányítópulttal. Az **Összes üzlet** csempén válassza a három pontot.

   ![Összes üzlet csempe](media/service-set-data-alerts/powerbi-card.png)

1. A harang ikon ![riasztás ikon](media/service-set-data-alerts/power-bi-bell-icon.png) kiválasztásával adjon hozzá egy vagy több riasztást a **Összes üzlet** csempéhez.

1. Először válassza a **+ Riasztási szabály hozzáadása** lehetőséget, győződjön meg arról, hogy az **Aktív** csúszka a **Be** állásba van kapcsolva, majd adjon címet a riasztásnak. A címek segítségével könnyebben felismerheti a riasztásokat.

   ![Riasztások kezelése ablak](media/service-set-data-alerts/powerbi-alert-title.png)

1. Görgessen le, és adja meg a riasztás adatait.  Ebben a példában most egy olyan riasztást állít be, amely napi küld értesítést, ha az üzletek száma 100 fölé emelkedik.

   ![Riasztások kezelése ablak, küszöbérték beállítása](media/service-set-data-alerts/power-bi-set-alert-details.png)

    A riasztások az **Értesítési központban** jelennek meg. A Power BI e-mailt is küld a riasztásról, ha Ön bejelölte az ennek megfelelő jelölőnégyzetet.

1. Válassza a **Mentés és bezárás** lehetőséget.

## <a name="receiving-alerts"></a>Riasztások fogadása

Ha a követett adatok elérik valamelyik beállított küszöböt, több dolog történik. Először is a Power BI ellenőrzi, hogy eltelt-e már több mint egy óra vagy 24 óra (a választott beállítástól függően) az utolsó riasztás óta. Ha az adat meghaladja a küszöböt, a rendszer riasztást küld.

Ezután a Power BI egy riasztást küld az **Értesítési központba**, valamint választhatóan az e-mail-fiókjába is. Az egyes riasztásokban közvetlen hivatkozás mutat az adatokra. A hivatkozásra megnyitásával megtekintheti a vonatkozó csempét, ahol részletesebb információkat találhat, valamint megoszthatja az információkat.  

* Ha úgy konfigurálta a riasztást, hogy az e-mailben is értesítse, valami ilyesmit talál majd a bejövő levelei közt.

   ![Riasztási e-mail](media/service-set-data-alerts/powerbi-alerts-email.png)

* A Power BI egy üzenetet küld az **Értesítési központba**, és egy új riasztás ikont jelenít meg az érintett csempén.

   ![Értesítési ikon a Power BI szolgáltatásban](media/service-set-data-alerts/powerbi-alert-notifications.png)

* A riasztás részletei az **Értesítési központban** jelennek meg.

    ![riasztás olvasása](media/service-set-data-alerts/powerbi-alert-notification.png)

   > [!NOTE]
   > A riasztások kizárólag a frissített adatokon működnek. Az egyes adatok frissítésekor a Power BI ellenőrzi, hogy az adott adathoz van-e beállítva riasztás. Ha az adatok elérték a riasztási küszöböt, a riasztás aktiválódik a Power BI-ban.

## <a name="managing-alerts"></a>Riasztások kezelése

A riasztásokat többféle módon is kezelheti:

* Az irányítópult csempéjéről.

* A Power BI Beállítások menüjéből.

* A [Power BI-mobilalkalmazásokban](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md), egy csempén.

### <a name="from-the-dashboard-tile"></a>Az irányítópult csempéjéről

1. Ha módosítani vagy törölni szeretné egy adott csempe valamelyik riasztását, nyissa meg újra a **Riasztások kezelése** ablakot a harang ikon ![riasztás ikon](media/service-set-data-alerts/power-bi-bell-icon.png) kiválasztásával.

    Az adott csempéhez beállított összes riasztás megjelenik.

    ![Riasztások kezelése ablak](media/service-set-data-alerts/powerbi-see-alerts.png)

1. A riasztás módosításához válassza a neve mellett balra található nyilat.

    ![Riasztás neve melletti nyíl](media/service-set-data-alerts/powerbi-see-alerts-arrow.png)

1. A riasztás módosításához válassza a neve mellett jobbra található kukát.

      ![Kuka ikon kiválasztva](media/service-set-data-alerts/powerbi-see-alerts-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>A Power BI Beállítások menüjéből

1. Kattintson a fogaskerék ikonra a Power BI menüsorán, majd válassza a **Beállítások** lehetőséget.

    ![fogaskerék ikon](media/service-set-data-alerts/powerbi-gear-icon.png).

1. A **Beállítások** alatt válassza a **Riasztások** elemet.

    ![Riasztások fül a Beállítások ablakban](media/service-set-data-alerts/powerbi-alert-settings.png)

1. Erről a felületről be- és kikapcsolhatja a riasztásokat, megnyithatja a **Riasztások kezelése** ablakot a riasztás módosításához, vagy akár törölheti is a riasztást.

## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás

* A riasztásokat a dátum/idő mértékekkel rendelkező kártyacsempék nem támogatják.
* A riasztások kizárólag numerikus adattípusokkal működnek.
* A riasztások kizárólag a frissített adatokon működnek. Statikus adatokon nem.
* A riasztások a streamelési adatkészleteken csak akkor működnek, ha felépít egy KPI-/kártya-/mérőműszer-jelentési vizualizációt, majd rögzíti az irányítópulton.


## <a name="next-steps"></a>Következő lépések

* [Adatriasztást tartalmazó Microsoft Flow létrehozása](service-flow-integration.md).

* [Adatriasztások beállítása mobileszközökön](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md).

* [Mi az a Power BI?](fundamentals/power-bi-overview.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
