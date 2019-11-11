---
title: Szalagdiagramok használata a Power BI-ban
description: Szalagdiagramok létrehozása és felhasználása a Power BI Desktopban
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/10/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 1cee814b5013ece3a847aeb3660f1257c69be125
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73871143"
---
# <a name="use-ribbon-charts-in-power-bi"></a>Szalagdiagramok használata a Power BI-ban

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Szalagdiagramok használatával megjelenítheti az adatokat, és gyorsan felderítheti a legmagasabb rangú (legnagyobb értéket képviselő) adatkategóriát. A szalagdiagramokkal hatékonyan ábrázolható a rangok időbeli változása: minden időszakban a legmagasabb rangú (értékű) kategória látható felül. 

![menüszalag-diagram](media/desktop-ribbon-charts/ribbon-charts-01.png)

## <a name="prerequisites"></a>Előfeltételek

Ez az oktatóanyag a [Kiskereskedelmi elemzési minta PBIX-fájlt](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) használja.

1. A menüsor bal felső részén válassza a **Fájl** > **Megnyitás** lehetőséget
   
2. Keresse meg a **Kiskereskedelmi elemzési minta PBIX-fájlt**

1. Nyissa meg a **Kiskereskedelmi elemzési minta PBIX-fájlt** jelentésnézetben ![A jelentésnézet ikon képernyőképe.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Kiválasztás ![A sárga fül képernyőképe.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) új oldal hozzáadásához.

## <a name="create-a-ribbon-chart"></a>Szalagdiagram létrehozása

1. Szalagdiagram létrehozásához válassza a **szalagdiagram** lehetőséget a **Vizualizációk** panelen.

    ![vizualizációs sablonok](media/desktop-ribbon-charts/power-bi-template.png)

    A szalagdiagramok szalagok segítségével kapcsolják az adatkategóriákat a vizualizált időfolyamhoz, így megtekintheti, hogy az egyes kategóriák milyen rangsorban állnak egymáshoz képest a diagram x tengelyén (amely általában az idővonal).

2. Válassza ki a **Tengely**, **Jelmagyarázat** és **Érték** mezőket.  Ebben a példában a következőket választottuk: **Üzlet** > **NyitásiDátum**, **Elem** > **Kategória**, valamint **Értékesítés** > **Idei értékesítések** > **Érték**.  

    ![választott mezők](media/desktop-ribbon-charts/power-bi-ribbon-values.png)

    Mivel az adathalmaz csak egy év adatait tartalmazza, az **Év** és a **Negyedév** mezőt is eltávolítottuk a **Tengelyről**.

3. A szalagdiagram minden hónapra bemutatja a rangsorolást. Figyelje meg a rang időbeli változását. A Kezdőlap kategóriája például februártól márciusig a másodiktól az ötödikig napig mozog.

    ![menüszalag-diagram](media/desktop-ribbon-charts/power-bi-ribbon.png)

## <a name="format-a-ribbon-chart"></a>Szalagdiagram formázása
Szalagdiagram létrehozásakor a formázási lehetőségek a **Vizualizációk** panel **Formázás** szakaszában találhatók. A szalagdiagramok formázási lehetőségei a halmozott oszlopdiagramokéhoz hasonlóak, amelyeken kívül további, csak a szalagokra vonatkozó formázási lehetőségeket is tartalmaznak.

![menüszalagsablon a Vizualizációk panelen](media/desktop-ribbon-charts/power-bi-format-ribbon.png)

A szalagdiagramok formázási beállításaival módosításokat végezhet.

* A **Térköz** beállítással módosíthatja a szalagok közötti üres terület méretét. A szám az oszlop maximális magasságának százalékos arányát jelenti.
* Az **Egyeztetés a sorozat színével** beállítással megadhatja, hogy a szalagok színe megegyezzen az adatsorozat színével. Ha **ki** van kapcsolva, a szalagok szürke színűek.
* Az **Átlátszóság** beállítással megadhatja a szalagok átlátszóságának mértékét. Az alapértelmezett érték 30.
* A **Határ** beállítással sötét szegélyt állíthat be a szalagok felső és alsó határához. A szegélyek alapértelmezés szerint ki vannak kapcsolva.

Mivel a szalagdiagram y tengelyén nincsenek feliratok, érdemes lehet adatfeliratokat felvenni. A Formázás panelen válassza az **Adatfeliratok** lehetőséget. 

![adatfeliratok formázási lehetőségei](media/desktop-ribbon-charts/power-bi-labels.png)

Állítsa be adatfeliratai formázását. Példánkban a szöveg színét fehérre, a megjelenítési egységeket pedig ezresekre módosítottuk.

![menüszalagsablon a Vizualizációk panelen](media/desktop-ribbon-charts/power-bi-data-labels.png)

## <a name="next-steps"></a>Következő lépések

[Pontdiagramok és buborékdiagramok a Power BI-ban](power-bi-visualization-scatter.md)

[Vizualizációtípusok a Power BI-ban](power-bi-visualization-types-for-reports-and-q-and-a.md)
