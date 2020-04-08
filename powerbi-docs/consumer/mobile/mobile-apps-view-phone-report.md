---
title: Telefonra optimalizált Power BI-jelentések megtekintése
description: Itt a Power BI telefonos alkalmazásokban való megtekintésre optimalizált jelentésoldalak használatáról olvashat.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: painbar
ms.openlocfilehash: 91fc7e9e3664f21d50b475f316a9a6c64875fab4
ms.sourcegitcommit: 9b806dfe62c2dee82d971bb4f89d983b97931b43
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/07/2020
ms.locfileid: "80802128"
---
# <a name="view-power-bi-reports-optimized-for-your-phone"></a>Telefonra optimalizált Power BI-jelentések megtekintése

A következőkre vonatkozik:

| ![iPhone](./media/mobile-apps-view-phone-report/ios-logo-40-px.png) | ![Android rendszerű telefon](./media/mobile-apps-view-phone-report/android-logo-40-px.png) |
|:--- |:--- |
| iPhone-ok |Android rendszerű telefonok |

Ha egy Power BI-jelentést a telefonon tekint meg, a Power BI ellenőrzi, hogy a jelentés optimalizálva lett-e telefonokra. Ha igen, a Power BI automatikusan álló nézetben nyitja meg az optimalizált jelentést.

![Jelentés álló tájolásban](./media/mobile-apps-view-phone-report/07-power-bi-phone-report-portrait.png)

Ha a jelentésnek nem létezik telefonra optimalizált változata, a jelentés megnyílik, azonban a nem optimalizált fekvő tájolásban. Még a telefonra optimalizált jelentések esetében is, ha a telefont oldalra fordítja, a jelentés a nem optimalizált nézetben jelenik meg az eredeti jelentéselrendezésben. Ha csak egyes oldalak vannak optimalizálva, álló tájolásban egy üzenet jelenik meg, amely értesíti, hogy a jelentés fekvő tájolásban tekinthető meg.

![Nem optimalizált jelentésoldal](./media/mobile-apps-view-phone-report/06-power-bi-phone-report-page-not-optimized.png)

A Power BI jelentések többi funkciója továbbra is működik a telefonra optimalizált jelentésekben. Ismerje meg részletesebben az alábbiak kínálta lehetőségeket:

* [Jelentések iPhone készülékeken](mobile-reports-in-the-mobile-apps.md). 
* [Jelentések Android telefonokon](mobile-reports-in-the-mobile-apps.md).

## <a name="filter-the-report-page-on-a-phone"></a>Jelentésoldalak szűrése telefonon
Ha egy telefonra optimalizált jelentéshez szűrők vannak definiálva, a jelentés telefonon való megtekintésekor alkalmazhatja ezeket a szűrőket. A jelentés a weben beállított értékekre szűrve jelenik meg a telefonon. Egy üzenet tájékoztat arról, hogy az oldalon aktív szűrés van érvényben. A szűrők a telefonon módosíthatók.

1. Koppintson a Szűrő ikonra ![Szűrő ikon a telefonon](./media/mobile-apps-view-phone-report/power-bi-phone-filter-icon.png) a lap alján.

2. Az alapszintű és a speciális szűrők használatával az Ön számára érdekes eredményeket jelenítheti meg.
   
    ![Telefonos BI-jelentés speciális szűrője](./media/mobile-apps-view-phone-report/power-bi-iphone-advanced-filter-toronto.png)

## <a name="cross-highlight-visuals"></a>Vizualizációk keresztkiemelése
A vizualizációk keresztkiemelése telefonos jelentésekben ugyanúgy működik, mint a Power BI szolgáltatásban, és telefonokon a fekvő tájolású jelentésekben: Ha egy vizualizáción ki van jelölve egy adat, akkor az ahhoz kapcsolódó adatok is ki lesznek emelve az oldal többi vizualizációjában.

A [Power BI szűrés és kiemelés funkcionalitásáról itt talál](../../power-bi-reports-filters-and-highlighting.md) további információkat.

## <a name="select-visuals"></a>Vizualizációk kijelölése
Amikor a telefonos jelentésekben kijelöl egy vizualizációt, a telefonos jelentés kiemeli és középre fókuszálja az adott vizualizációt, és kikapcsolja a vászonmozdulatokat.

Ha egy vizualizáció van kijelölve, azon belül végezhet különféle mozdulatokat, például görgetést. A vizualizáció kijelölésének megszüntetéséhez csak érintse meg a képernyőt a vizualizáció területén kívül.

## <a name="open-visuals-in-focus-mode"></a>Vizualizáció megnyitása fókusz módban
A telefonos jelentések a fókusz módot is támogatják: Nagyobb áttekintést kaphat egy adott vizualizációról, és könnyebben megismerheti azt.

* A telefonos jelentésben koppintson a vizualizáció jobb felső sarkában a három pontra ( **...** ), majd a **Kiterjesztés fókusz módra** lehetőségre.
  
    ![Kiterjesztés fókusz módra](././media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)

A fókusz módban végrehajtott módosítások megjelennek a jelentésvásznon és viszont. Ha például kiemel egy értéket egy vizualizációban, majd visszavált a teljes jelentésre, a jelentés a vizualizációban kiemelt értékre szűrve jelenik meg.

Egyes műveletek a képernyőméret-korlátok miatt csak fókusz módban hajthatóak végre:

* A vizualizációban megjelenő információk **részletes elemzése**. A telefonos jelentésekben [a részletes elemzések kibontásáról és összecsukásáról](mobile-apps-view-phone-report.md#drill-down-in-a-visual) az alábbiakban olvashat.
* A vizualizációban lévő értékek **rendezése**.
* **Visszaállítás**: A vizualizáció vizsgálata során végrehajtott lépések törlése, és a jelentés létrehozásakor megadott definíciók visszaállítása.
  
    Az összes vizsgálati lépés a vizualizációról való törléséhez koppintson a három pontra ( **...** ), majd a **Visszaállítás** lehetőségre.
  
    ![Visszaállítás](././media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)
  
    A visszaállítás a jelentés szintjén (az összes vizualizáció minden vizsgálati lépésének törlése) vagy az egyes vizualizációk szintjén (egy kiválasztott vizualizáció minden vizsgálati lépésének törlése) lehetséges.   

## <a name="drill-down-in-a-visual"></a>Vizualizációk részletes elemzése
Ha a vizualizációban vannak hierarchiaszintek definiálva, részletes elemzést végezhet a vizualizációban megjelenő részletes információk szintjén majd onnan vissza léphet. A [vizualizációk részletes elemzési funkcionalitását](../end-user-drill.md) a Power BI szolgáltatásban vagy a Power BI Desktopban adhatja hozzá.

A részletezésnek néhány típusa van:

### <a name="drill-down-on-a-value"></a>Részletezés egy érték alapján
1. Hosszú koppintás (koppintás és nyomva tartás) egy vizualizáció adatpontjára.
2. Megjelenik az elemleírás, és ha definiálva van a hierarchia, akkor az elemleírás láblécében megjelenik a részletezés felfelé és lefelé mutató nyila.
3. Koppintson a lefelé mutató nyílra a részletezéshez

    ![Koppintás a részletezésre](././media/mobile-apps-view-phone-report/report-drill-down.png)
    
4. Koppintson a felfelé mutató nyílra a felhatoláshoz.

### <a name="drill-to-next-level"></a>Részletezés a következő szintre
1. A telefonos jelentésben koppintson a jobb felső sarokban a három pontra ( **...** ), majd a **Kiterjesztés fókusz módra** lehetőségre.
   
    ![Kiterjesztés fókusz módra](././media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)
   
    Ebben a példában a sávok az államokra vonatkozó értékeket mutatják.
2. Koppintson a Vizsgálat ikonra ![Vizsgálat ikon](./media/mobile-apps-view-phone-report/power-bi-phone-report-explore-icon.png) a bal alsó sarokban.
   
    ![Vizsgálat mód](./media/mobile-apps-view-phone-report/power-bi-phone-report-explore-mode.png)
3. Koppintson **A következő szint megjelenítése** vagy a **Kibontás a következő szintre** lehetőségre.
   
    ![Kibontás a következő szintre](./media/mobile-apps-view-phone-report/power-bi-phone-report-expand-levels.png)
   
    Most a sávok a városokra vonatkozó értékeket mutatják.
   
    ![Kibontott szintek](./media/mobile-apps-view-phone-report/power-bi-phone-report-expanded-levels.png)
4. Ha a bal felső sarokban lévő nyílra koppint, visszatérhet a telefonos jelentéshez, miközben az értékek még mindig az alsóbb szinten vannak kibontva.
   
    ![Még mindig az alsóbb szinten kibontva](./media/mobile-apps-view-phone-report/power-bi-back-to-phone-report-expanded-levels.png)
5. Az eredeti szintre való visszalépéshez koppintson ismét a három pontra ( **...** ), majd a **Visszaállítás** lehetőségre.
   
    ![Visszaállítás](././media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)

## <a name="drill-through-from-a-value"></a>Részletezés egy értékről
Az áthatolásos részletezés az egyik jelentésoldal értékeit más jelentésoldalakkal kapcsolja össze. Ha egy adatpontról egy másik jelentéslapra végez részletezést, a rendszer az adatpontok értékeit használja az áthatolásos részletezésű oldal szűrésére, vagy a kijelölt adatok kontextusát használja majd.
A jelentés szerzője a jelentés létrehozásakor [definiálhatja az áthatolásos részletezést](https://docs.microsoft.com/power-bi/desktop-drillthrough).

1. Hosszú koppintás (koppintás és nyomva tartás) egy vizualizáció adatpontjára.
2. Megjelenik az elemleírás, és ha definiálva van az áthatolás, akkor az elemleírás láblécében megjelenik az áthatolást jelző nyíl.
3. Koppintson az áthatolást jelző nyílra

    ![Koppintás az áthatolásra](././media/mobile-apps-view-phone-report/report-drill-through1.png)

4. Az áthatoláshoz használandó jelentésoldal kiválasztása

    ![Jelentésoldal kiválasztása](././media/mobile-apps-view-phone-report/report-drill-through2.png)

5. Az alkalmazás fejlécében található Vissza gombbal visszaléphet arra az oldalra, ahonnan indult.


## <a name="next-steps"></a>Következő lépések
* [A Power BI telefonos alkalmazásokhoz optimalizált jelentések létrehozása](../../desktop-create-phone-report.md)
* [Power BI-irányítópult telefonos nézetének létrehozása](../../service-create-dashboard-mobile-phone-view.md)
* [Bármely méretre optimalizált rugalmas vizualizációk létrehozása](../../visuals/desktop-create-responsive-visuals.md)
* További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

