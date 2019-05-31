---
title: Telefonra optimalizált Power BI-jelentések megtekintése
description: Itt a Power BI telefonos alkalmazásokban való megtekintésre optimalizált jelentésoldalak használatáról olvashat.
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 04/22/2019
ms.author: mshenhav
ms.openlocfilehash: 79ca47f83bb39ab9d6df141b5a26dcb54e00c72c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65101004"
---
# <a name="view-power-bi-reports-optimized-for-your-phone"></a>Telefonra optimalizált Power BI-jelentések megtekintése

A következőkre vonatkozik:

| ![iPhone](./media/mobile-apps-view-phone-report/ios-logo-40-px.png) | ![Android rendszerű telefon](./media/mobile-apps-view-phone-report/android-logo-40-px.png) |
|:--- |:--- |
| iPhone-ok |Android rendszerű telefonok |

A Power BI-jelentés telefonon való megtekintésekor a Power BI ellenőrzi, hogy ha a jelentés telefonra optimalizált. Ha igen, a Power BI automatikusan nyitja meg álló tájolásban.

![Jelentés álló tájolásban](./media/mobile-apps-view-phone-report/07-power-bi-phone-report-portrait.png)

Ha a jelentésnek nem létezik telefonra optimalizált változata, a jelentés akkor is megnyílik, azonban a nem optimalizált fekvő tájolásban. Még a telefonra optimalizált jelentések esetében is, ha a telefont oldalra fordítja, a jelentés a nem optimalizált nézetben jelenik meg az eredeti jelentéselrendezésben. Ha csak egyes oldalak vannak optimalizálva, álló tájolásban egy üzenet jelenik meg, amely értesíti, hogy a jelentés fekvő tájolásban tekinthető meg.

![Nem optimalizált jelentésoldal](./media/mobile-apps-view-phone-report/06-power-bi-phone-report-page-not-optimized.png)

A Power BI jelentések többi funkciója továbbra is működik a telefonra optimalizált jelentésekben. Ismerje meg részletesebben az alábbiak kínálta lehetőségeket:

* [Jelentések iPhone készülékeken](mobile-reports-in-the-mobile-apps.md). 
* [Jelentések Android telefonokon](mobile-reports-in-the-mobile-apps.md).

## <a name="filter-the-report-page-on-a-phone"></a>Jelentésoldalak szűrése telefonon
Ha egy telefonra optimalizált jelentéshez szűrők vannak definiálva, a jelentés telefonon való megtekintésekor alkalmazhatja ezeket a szűrőket. Ekkor megnyílik a jelentés a telefonján, a jelentés a weben beállított értékekre szűrve. Egy üzenet tájékoztat arról, hogy az oldalon aktív szűrés van érvényben. A szűrők a telefonon módosíthatók.

1. Koppintson a Szűrő ikonra ![Szűrő ikon a telefonon](./media/mobile-apps-view-phone-report/power-bi-phone-filter-icon.png) a lap alján. 
2. Az alapszintű és a speciális szűrők használatával az Ön számára érdekes eredményeket jelenítheti meg.
   
    ![Telefonos BI-jelentés speciális szűrője](./media/mobile-apps-view-phone-report/power-bi-iphone-advanced-filter-toronto.gif)

## <a name="cross-highlight-visuals"></a>Vizualizációk keresztkiemelése
Vizualizációk keresztkiemelése a fekvő nézetben ugyanúgy működik, a Power BI szolgáltatásban és a fekvő tájolású: Ha egy vizualizáción ki van jelölve egy adat, akkor az ahhoz kapcsolódó adatok is ki lesznek emelve az oldal többi vizualizációjában.

A [Power BI szűrés és kiemelés funkcionalitásáról itt talál](../../power-bi-reports-filters-and-highlighting.md) további információkat.

## <a name="select-visuals"></a>Vizualizációk kijelölése
Amikor a telefonos jelentésekben kijelöl egy vizualizációt, a telefonos jelentés kiemeli és középre fókuszálja az adott vizualizációt, és kikapcsolja a vászonmozdulatokat.

Ha egy vizualizáció van kijelölve, azon belül végezhet különféle mozdulatokat, például görgetést. A vizualizáció kijelölésének megszüntetéséhez csak érintse meg a képernyőt a vizualizáció területén kívül.

## <a name="open-visuals-in-focus-mode"></a>Vizualizáció megnyitása fókusz módban
Telefonos jelentések is rendelkeznek fókusz móddal: Kinagyíthatja az egyes visual, és Fedezze fel egyszerűen.

* A telefonos jelentésben koppintson a vizualizáció jobb felső sarkában a három pontra ( **...** ), majd a **Kiterjesztés fókusz módra** lehetőségre.
  
    ![Kiterjesztés fókusz módra](././media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)

Ehhez a csempét fókusz módban végrehajtott módosítások megjelennek a jelentésvásznon és viszont. Például ha jelöljön ki egy értéket egy vizualizációban, majd térjen vissza a teljes jelentésre, a jelentés szűrt a vizualizációban kiemelt értékre.

Egyes műveletek a képernyőméret-korlátok miatt csak fókusz módban hajthatóak végre:

* A vizualizációban megjelenő információk **részletes elemzése**. A telefonos jelentésekben [a részletes elemzések kibontásáról és összecsukásáról](mobile-apps-view-phone-report.md#drill-down-in-a-visual) az alábbiakban olvashat.
* A vizualizációban lévő értékek **rendezése**.
* **Visszaállítás**: A vizualizáció vizsgálata során végrehajtott lépések törlése, és a jelentés létrehozásakor megadott definíciók visszaállítása.
  
    Az összes vizsgálati lépés a vizualizációról való törléséhez koppintson a három pontra ( **...** ), majd a **Visszaállítás** lehetőségre.
  
    ![Visszaállítás](././media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)
  
    Visszaállítás a jelentés szintjén, minden Vizualizáció vizsgálati törlése vagy törlése a kijelölt Vizualizáció feltárása, a Vizualizáció szintjén érhető el.   

## <a name="drill-down-in-a-visual"></a>Vizualizációk részletes elemzése
Ha a vizualizációban vannak hierarchiaszintek definiálva, részletes elemzést végezhet a vizualizációban megjelenő részletes információk szintjén majd onnan vissza léphet. A [vizualizációk részletes elemzési funkcionalitását](../end-user-drill.md) a Power BI szolgáltatásban vagy a Power BI Desktopban adhatja hozzá.

Részletezés néhány típusa van:

### <a name="drill-down-on-a-value"></a>Részletezés érték
1. Mennyi ideig koppintson egy egy vizualizációban az adatpontra (Koppintson és tartsa).
2. Elemleírás fog megjelenni, és ha hierarchiában van megadva, majd az elemleírás élőláb jeleníti meg részletes elemzés és Felhatolás nyílra.
3. Koppintson a lefelé mutató nyílra a részletezés

    ![Koppintson a részletezés](././media/mobile-apps-view-phone-report/report-drill-down.png)
    
4. Koppintson a Felhatolás a felfelé mutató nyílra.

### <a name="drill-to-next-level"></a>A következő szintre feltárása
1. A telefonos jelentésben koppintson a jobb felső sarokban a három pontra ( **...** ), majd a **Kiterjesztés fókusz módra** lehetőségre.
   
    ![Kiterjesztés fókusz módra](././media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)
   
    Ebben a példában a sávok az államokra vonatkozó értékeket mutatják.
2. Koppintson a Vizsgálat ikonra ![Vizsgálat ikon](./media/mobile-apps-view-phone-report/power-bi-phone-report-explore-icon.png) a bal alsó.
   
    ![Vizsgálat mód](./media/mobile-apps-view-phone-report/power-bi-phone-report-explore-mode.png)
3. Koppintson **A következő szint megjelenítése** vagy a **Kibontás a következő szintre** lehetőségre.
   
    ![Kibontás a következő szintre](./media/mobile-apps-view-phone-report/power-bi-phone-report-expand-levels.png)
   
    Most a sávok a városokra vonatkozó értékeket mutatják.
   
    ![Kibontott szintek](./media/mobile-apps-view-phone-report/power-bi-phone-report-expanded-levels.png)
4. Ha a bal felső sarokban lévő nyílra koppint, visszatérhet a telefonos jelentéshez, miközben az értékek még mindig az alsóbb szinten vannak kibontva.
   
    ![Még mindig az alsóbb szinten kibontva](./media/mobile-apps-view-phone-report/power-bi-back-to-phone-report-expanded-levels.png)
5. Az eredeti szintre való visszalépéshez koppintson ismét a három pontra ( **...** ), majd a **Visszaállítás** lehetőségre.
   
    ![Visszaállítás](././media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)

## <a name="drill-through-from-a-value"></a>Áthatoló részletezést értékét a
Jelenítse meg a jelentés egyéb oldalain egy jelentésoldalon, az értékek kapcsolódik. Áthatoló részletezést-ből egy adatpont másik jelentésoldalra, amikor az adatpontérték segítségével szűrheti a feltárása oldalán keresztül, vagy a kijelölt adatok kontextusában lesz.
Jelentések szerzői is [jelenítse meg a definiálása](https://docs.microsoft.com/power-bi/desktop-drillthrough) a jelentés létrehozásakor.

1. Mennyi ideig koppintson egy egy vizualizációban az adatpontra (Koppintson és tartsa).
2. Elemleírás fog megjelenni, és ha jelenítse meg van adva, majd az elemleírás élőláb jeleníti meg jelenítse meg a nyíl.
3. Koppintson a nyílra a kódig

    ![Koppintson a részletezés](././media/mobile-apps-view-phone-report/report-drill-through1.png)

4. Válassza ki, melyik jelentésoldal áthatoló részletezést

    ![Válassza ki a jelentésoldal](././media/mobile-apps-view-phone-report/report-drill-through2.png)

5. A Vissza gombot, használja az alkalmazás fejléc a használatát a lapra való visszatéréshez.


## <a name="next-steps"></a>Következő lépések
* [A Power BI telefonos alkalmazásokhoz optimalizált jelentések létrehozása](../../desktop-create-phone-report.md)
* [Power BI-irányítópult telefonos nézetének létrehozása](../../service-create-dashboard-mobile-phone-view.md)
* [Bármely méretre optimalizált rugalmas vizualizációk létrehozása](../../visuals/desktop-create-responsive-visuals.md)
* További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

