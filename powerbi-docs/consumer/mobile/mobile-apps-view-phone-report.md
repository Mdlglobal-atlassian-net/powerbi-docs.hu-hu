---
title: Telefonra optimalizált Power BI-jelentések megtekintése
description: Itt a Power BI telefonos alkalmazásokban való megtekintésre optimalizált jelentésoldalak használatáról olvashat.
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 09/14/2018
ms.author: mshenhav
ms.openlocfilehash: 99f40837f4b2c188120c4ca0311be3e9ded5fe95
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54276906"
---
# <a name="view-power-bi-reports-optimized-for-your-phone"></a>Telefonra optimalizált Power BI-jelentések megtekintése

A következőkre vonatkozik:

| ![iPhone](./media/mobile-apps-view-phone-report/ios-logo-40-px.png) | ![Android rendszerű telefon](./media/mobile-apps-view-phone-report/android-logo-40-px.png) |
|:--- |:--- |
| iPhone-ok |Android rendszerű telefonok |

Amikor létrehoz egy Power BI-jelentést a Power BI Desktopban vagy a Power BI szolgáltatásban, [létrehozhatja a Power BI telefonos alkalmazásokban való megtekintésre optimalizált jelentésverziót](../../desktop-create-phone-report.md).

Ezután, ha megnyit egy Power BI-jelentést a telefonján, a Power BI felderíti, ha a jelentésnek van telefonra optimalizált változata, és automatikusan azt nyitja meg álló tájolásban.

![Jelentés álló tájolásban](./media/mobile-apps-view-phone-report/07-power-bi-phone-report-portrait.png)

Ha a jelentésnek nem létezik telefonra optimalizált változata, a jelentés akkor is megnyílik, azonban a nem optimalizált fekvő tájolásban. Még a telefonra optimalizált jelentések esetében is, ha a telefont oldalra fordítja, a jelentés a nem optimalizált nézetben jelenik meg az eredeti jelentéselrendezésben. Ha csak egyes oldalak vannak optimalizálva, álló tájolásban egy üzenet jelenik meg, amely értesíti, hogy a jelentés fekvő tájolásban tekinthető meg.

![Nem optimalizált jelentésoldal](./media/mobile-apps-view-phone-report/06-power-bi-phone-report-page-not-optimized.png)

A Power BI jelentések többi funkciója továbbra is működik a telefonra optimalizált jelentésekben. Ismerje meg részletesebben az alábbiak kínálta lehetőségeket:

* [Jelentések iPhone készülékeken](mobile-reports-in-the-mobile-apps.md). 
* [Jelentések Android telefonokon](mobile-reports-in-the-mobile-apps.md).

## <a name="filter-the-report-page-on-a-phone"></a>Jelentésoldalak szűrése telefonon
Ha egy telefonra optimalizált jelentéshez szűrők vannak definiálva, a jelentés telefonon való megtekintésekor alkalmazhatja ezeket a szűrőket. A jelentés azokra a weben beállított értékekre szűrve jelenik meg a telefonon egy üzenettel, hogy az oldalon aktív szűrő működik. A szűrők a telefonon módosíthatók.

1. Koppintson a Szűrő ikonra ![Szűrő ikon a telefonon](./media/mobile-apps-view-phone-report/power-bi-phone-filter-icon.png) a lap alján. 
2. Az alapszintű és a speciális szűrők használatával az Ön számára érdekes eredményeket jelenítheti meg.
   
    ![Telefonos BI-jelentés speciális szűrője](./media/mobile-apps-view-phone-report/power-bi-iphone-advanced-filter-toronto.gif)

## <a name="cross-highlight-visuals"></a>Vizualizációk keresztkiemelése
A vizualizációk keresztkiemelése telefonos jelentésekben ugyanúgy működik, mint a Power BI szolgáltatásban, és telefonokon a fekvő tájolású jelentésekben: Ha egy vizualizáción ki van jelölve egy adat, akkor az ahhoz kapcsolódó adatok is ki lesznek emelve az oldal többi vizualizációjában.

A [Power BI szűrés és kiemelés funkcionalitásáról itt talál](../../power-bi-reports-filters-and-highlighting.md) további információkat.

## <a name="select-visuals"></a>Vizualizációk kijelölése
Amikor a telefonos jelentésekben kijelöl egy vizualizációt, a telefonos jelentés kiemeli és középre fókuszálja az adott vizualizációt, és kikapcsolja a vászonmozdulatokat.

Ha egy vizualizáció van kijelölve, azon belül végezhet különféle mozdulatokat, például görgetést. A vizualizáció kijelölésének megszüntetéséhez csak érintse meg a képernyőt a vizualizáció területén kívül.

## <a name="open-visuals-in-focus-mode"></a>Vizualizáció megnyitása fókusz módban
A telefonos jelentések is rendelkeznek fókusz móddal, így ezekben is kinagyíthatja az egyes vizualizációkat azok és a jelentés részletesebb vizsgálata céljából.

* A telefonos jelentésben koppintson a vizualizáció jobb felső sarkában a három pontra (**...**), majd a **Kiterjesztés fókusz módra** lehetőségre.
  
    ![Kiterjesztés fókusz módra](././media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)

A fókusz módban végrehajtott módosítások megjelennek a jelentésvásznon és viszont, így a részletes vizsgálat zökkenőmentesen végezhető. Ha például kiemel egy értéket egy vizualizációban, majd visszavált a teljes jelentésre, a teljes jelentés a vizualizációban kiemelt értékre szűrve jelenik meg.

Egyes műveletek a képernyőméret-korlátok miatt csak fókusz módban hajthatóak végre:

* A vizualizációban megjelenő információk **részletes elemzése**. A telefonos jelentésekben [a részletes elemzések kibontásáról és összecsukásáról](mobile-apps-view-phone-report.md#drill-down-in-a-visual) az alábbiakban olvashat.
* A vizualizációban lévő értékek **rendezése**.
* **Visszaállítás**: A vizualizáció vizsgálata során végrehajtott lépések törlése, és a jelentés létrehozásakor megadott definíciók visszaállítása.
  
    Az összes vizsgálati lépés a vizualizációról való törléséhez koppintson a három pontra (**...**), majd a **Visszaállítás** lehetőségre.
  
    ![Visszaállítás](././media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)
  
    A visszaállítás a jelentés szintjén (az összes vizualizáció minden vizsgálati lépésének törlése) vagy az egyes vizualizációk szintjén (egy adott vizualizáció minden vizsgálati lépésének törlése) lehetséges.   

## <a name="drill-down-in-a-visual"></a>Vizualizációk részletes elemzése
Ha a vizualizációban vannak hierarchiaszintek definiálva, részletes elemzést végezhet a vizualizációban megjelenő részletes információk szintjén majd onnan vissza léphet. A [vizualizációk részletes elemzési funkcionalitását](../end-user-drill.md) a Power BI szolgáltatásban vagy a Power BI Desktopban adhatja hozzá. A részletes elemzés telefonon csak a telefonra optimalizált Power BI-jelentésekben elérhető. 

1. A telefonos jelentésben koppintson a jobb felső sarokban a három pontra (**...**), majd a **Kiterjesztés fókusz módra** lehetőségre.
   
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
5. Az eredeti szintre való visszalépéshez koppintson ismét a három pontra (**...**), majd a **Visszaállítás** lehetőségre.
   
    ![Visszaállítás](././media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)

## <a name="next-steps"></a>További lépések
* [A Power BI telefonos alkalmazásokhoz optimalizált jelentések létrehozása](../../desktop-create-phone-report.md)
* [Power BI-irányítópult telefonos nézetének létrehozása](../../service-create-dashboard-mobile-phone-view.md)
* [Bármely méretre optimalizált rugalmas vizualizációk létrehozása](../../visuals/desktop-create-responsive-visuals.md)
* További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

