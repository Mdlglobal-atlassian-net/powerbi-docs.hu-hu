---
title: Adatok exportálása Power BI-vizualizációból
description: Adatok exportálása jelentésvizualizációból és irányítópult-vizualizációból, és megtekintésük az Excelben.
author: mihart
manager: kvivek
ms.reviewer: cmfinlan
featuredvideoid: jtlLGRKBvXY
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/11/2019
ms.author: mihart
LocalizationGroup: Consumers
ms.openlocfilehash: 80033cafbe66303a1d6f55bba61f7d19449dc45b
ms.sourcegitcommit: f34acbf9fb1ab568fd89773aaf412a847f88dd34
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72589531"
---
# <a name="export-data-from-a-visual"></a>Adatok exportálása vizualizációból

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Ha szeretné megtekinteni a vizualizáció létrehozásához használt adatokat, [megjelenítheti az adatokat a Power BI-ban](end-user-show-data.md) vagy exportálhatja azokat az Excelbe. Az adatexportálási lehetőség használatához meghatározott típusú licenc szükséges, valamint a tartalomra vonatkozó engedélyek. Ha nem tud exportálni, lépjen kapcsolatba a Power BI rendszergazdájával. 

## <a name="from-a-visual-on-a-power-bi-dashboard"></a>Power BI-irányítópulton található vizualizációból

1. Induljon ki egy Power BI-irányítópultból. Itt a ***Értékesítés és marketing minta*** alkalmazásból származó irányítópultot fogjuk használni. Az [alkalmazást letöltheti az AppSource.com](https://appsource.microsoft.com/en-us/product/power-bi/microsoft-retail-analysis-sample.salesandmarketingsample-preview?flightCodes=e2b06c7a-a438-4d99-9eb6-4324ce87f282) webhelyről.

    ![Alkalmazásbeli irányítópult](media/end-user-export/power-bi-dashboards.png)

2. Vigye a kurzort egy vizualizáció fölé, hogy megjelenjen a három pont (...), majd kattintson rá a műveleti menü megjelenítéséhez.

    ![A három pont kiválasztásakor megjelenő menü](media/end-user-export/power-bi-action-menu.png)

3. Válassza az **Exportálás az Excel programba** lehetőséget.

4. Hogy ez után mi történik, az a böngészőtől függ. A rendszer rákérdezhet a fájl mentésére, vagy a böngésző alján jelenhet meg egy hivatkozás, amely az exportált fájlra mutat. 

    ![Chrome böngésző az exportált fájlra mutató hivatkozással](media/end-user-export/power-bi-dashboard-exports.png)

5. Nyissa meg a fájlt az Excelben.  

    ![Idei egységek teljes száma az Excelben](media/end-user-export/power-bi-excel.png)


## <a name="from-a-visual-in-a-report"></a>Vizualizációból jelentésbe
Egy jelentésben szereplő vizualizációból is exportálhat adatokat .csv vagy .xlsx (Excel-) formátumban. 

1. Egy irányítópulton egy csempe kiválasztásával nyissa meg a mögöttes jelentést.  Ebben a példában ugyanazt az *Idei egységek teljes számának százalékos változása* vizualizációt választjuk, amelyek az előbb. 

    ![Kiemelt irányítópult-csempe](media/end-user-export/power-bi-export-reports.png)

    Mivel a csempe az *Értékesítés és marketing minta* jelentésből lett létrehozva, ez a jelentés fog megnyílni. Ennek is az az oldala nyílik meg, amely a kiválasztott vizualizációt tartalmazza. 

2. Válassza ki a csempét a jelentésben. Figyelje meg a jobb oldali **Szűrők** panelt. Erre a vizualizációra nincs szűrés alkalmazva. A szűrőkről a [Szűrők használata jelentésekben](end-user-report-filter.md) című cikkben olvashat.

    ![A Szűrők panel kiemelve](media/end-user-export/power-bi-export-filter.png)


3. Válassza a vizualizáció jobb felső sarkában található három pontot. Válassza az **Adatok exportálása** menüpontot.

    ![A legördülő menüben kijelölt Adatok exportálása menüpont](media/end-user-export/power-bi-export-report.png)

4. Választhat, hogy Összesített vagy Mögöttes adatokat szeretne exportálni. Ha az *Értékesítés és marketing minta* alkalmazást használja, a **Mögöttes adatok** lehetőség le van tiltva. Más jelentéseknél azonban mindkét lehetőség engedélyezett lehet. A különbség magyarázata a következő.

    **Összegzett adatok**: Válassza ezt a lehetőséget, ha a vizualizációban látható adatokat szeretné exportálni.  Az ilyen típusú export csak azokat a vizualizáció létrehozásához felhasznált adatokat tartalmazza. Ha a vizualizáción szűrők vannak alkalmazva, akkor az exportált adatok is szűrve lesznek. Ennél a vizualizációnál például az export csak a 2014. évi adatokat tartalmazza a középső régióból, és gyártók közül is csak négy cég adatait: VanArsdel, Natura, Aliqui és Pirum.
  

    **Mögöttes adatok**: Válassza ezt a lehetőséget, ha a vizualizációban látható adatok **mellett** a mögöttes adathalmaz további adatait is exportálni szeretné.  Ezek között lehetnek olyan adatok, amelyeket az adathalmaz tartalmaz, de nincsenek felhasználva a vizualizációhoz. 

    ![A Mögöttes adatok és az Összesített adatok exportálása közötti választást felkínáló menü](media/end-user-export/power-bi-export-option.png)

5. Hogy ez után mi történik, az a böngészőtől függ. A rendszer rákérdezhet a fájl mentésére, vagy a böngésző alján megjelenhet egy hivatkozás, amely az exportált fájlra mutat. 

    ![Exportált fájl a Microsoft Edge böngészőben megjelenítve](media/end-user-export/power-bi-export-edge-browser.png)


6. Nyissa meg a fájlt az Excelben. Hasonlítsa össze az exportált adatok mennyiségét az ugyanebből a vizualizációból az irányítópulton exportáltakéval. A különbség oka, hogy ez az export a **mögöttes adatokat** is tartalmazza. 

    ![Excel-minta](media/end-user-export/power-bi-underlying.png)

## <a name="next-steps"></a>Következő lépések

[A vizualizáció létrehozásához használt adatok megjelenítése](end-user-show-data.md)