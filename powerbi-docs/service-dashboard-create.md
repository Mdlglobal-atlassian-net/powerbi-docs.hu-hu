---
title: Power BI-irányítópult létrehozása jelentésből
description: Power BI-irányítópult létrehozása jelentésből
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/02/2018
ms.author: maggies
ms.openlocfilehash: c42aa07fd78430c5692067ae8476b22288470c8c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61152315"
---
# <a name="create-a-power-bi-dashboard-from-a-report"></a>Power BI-irányítópult létrehozása jelentésből
Áttekintette [A Power BI-irányítópultok](service-dashboards.md) részben leírtakat, és most saját irányítópultot kíván létrehozni. Az irányítópultok létrehozásának számos különböző módja van: többek között jelentésből, az alapoktól, adatkészletből, illetve egy meglévő irányítópult megkettőzésével is létrehozhatók stb.  

A kezdés sokak számára bonyolult lehet, ezért egy gyorsan és egyszerűen elkészíthető irányítópulttal kezdünk, amelyre már elkészült jelentésből fogunk vizualizációkat rögzíteni. A rövid útmutató elvégzése után már érteni fogja a jelentések és az irányítópultok közötti kapcsolatot, tudni fogja, hogyan lehet megnyitni egy jelentést Szerkesztési nézetben a jelentésszerkesztőben, hogyan lehet csempéket rögzíteni, és hogyan lehet mozogni az irányítópult és a jelentés között. Később a bal oldalon található Tartalomjegyzék hivatkozásait vagy a lap alján lévő **Következő lépések** hivatkozást használva léphet tovább magasabb szintű témákra.

## <a name="who-can-create-a-dashboard"></a>Ki hozhat lére irányítópultot?
Az irányítópult létrehozása **létrehozói** művelet, ezért csak akkor végezheti el, ha jogosultsága van a jelentést szerkeszteni. Szerkesztési jogosultsággal a jelentés létrehozója rendelkezik, valamint azok, akikek a létrehozó engedélyezte ezt. Ha például Dávid létrehoz egy jelentést az ABC munkaterületen, majd hozzáadja Önt ehhez a munkaterülethez, akkor Ön is és Dávid is rendelkezik majd szerkesztési jogosultsággal. Ha azonban a jelentést megosztották Önnel akár közvetlenül, akár egy [Power BI-alkalmazás](service-create-distribute-apps.md) részeként (más szóval ha Ön a jelentés **felhasználója**), akkor Ön nem fog tudni csempéket rögzíteni az irányítópultra.

> **MEGJEGYZÉS**: Az irányítópult a Power BI szolgáltatás, nem pedig a Power BI Desktop funkciója. Power BI-mobileszközökön csak [megtekinteni és megosztani](consumer/mobile/mobile-apps-view-dashboard.md) lehet az irányítópultokat, létrehozni nem.
>
> 

![irányítópult](media/service-dashboard-create/power-bi-completed-dashboard-small.png)

## <a name="video-create-a-dashboard-by-pinning-visuals-and-images-from-a-report"></a>Videó: Irányítópult létrehozása jelentésből származó vizualizációk és képek rögzítésével
Tekintse meg, ahogy Amanda bemutatja egy új irányítópult létrehozását jelentésből származó vizualizációk rögzítésével. Ezután a videó alatt látható lépeseket követve próbálkozzon meg a feladattal saját maga is a Beszerzéselemzési minta használatával.

<iframe width="560" height="315" src="https://www.youtube.com/embed/lJKgWnvl6bQ" frameborder="0" allowfullscreen></iframe>

### <a name="prerequisites"></a>Előfeltételek
A lépések követéséhez le kell töltenie a „Beszerzéselemzési” mintát Excel-munkafüzet formátumban, és meg kell nyitnia a Power BI Szolgáltatásban (app.powerbi.com).

## <a name="import-a-dataset-with-a-report"></a>Adatkészlet importálása jelentés használatával
A Power BI egyik mintaként szolgáló adatkészletét fogjuk importálni, majd egy új irányítópult létrehozására felhasználni. Az itt használt minta egy olyan Excel-munkafüzet, amelyben két PowerView-munkalap található. Amikor a Power BI importálja a munkafüzetet, egy adatkészletet és egy jelentést is hozzáad a munkaterülethez.  A rendszer a jelentést automatikusan hozza létre a PowerView-munkalapokból.

1. [Kattintson erre a hivatkozásra](http://go.microsoft.com/fwlink/?LinkId=529784) a Beszerzéselemzési minta Excel-fájl letöltéséhez és mentéséhez. Javasoljuk, hogy a OneDrive Vállalati verziójában mentse azt.
2. Nyissa meg a Power BI szolgáltatást a böngészőben (app.powerbi.com).
3. Válassza a **Saját munkaterület** elemet.
4. A bal oldali navigációs panelen válassza az **Adatok lekérése** lehetőséget.

    ![bal oldali navigációs ablak](media/service-dashboard-create/power-bi-get-data3.png)
5. Válassza a **Fájlok** lehetőséget.

   ![Fájlok lekérése](media/service-dashboard-create/power-bi-select-files.png)
6. Keresse meg a helyet, ahová a Beszerzéselemzési minta Excel-fájlját mentette. Jelölje ki azt, és válassza a **Kapcsolódás** lehetőséget.

   ![csatlakozás fájlokhoz](media/service-dashboard-create/power-bi-connectnew.png)
7. Ehhez a gyakorlathoz válassza az **Importálás** lehetőséget.

    ![OneDrive Vállalati verzió ablak](media/service-dashboard-create/power-bi-import.png)
8. A sikert jelző üzenet megjelenésekor az **x** jelre kattintva zárja be azt.

   ![sikert jelző üzenet](media/service-dashboard-create/power-bi-view-datasetnew.png)

### <a name="open-the-report-and-pin-some-tiles-to-a-dashboard"></a>A jelentés megnyitása, és néhány csempe rögzítése az irányítópulton
1. Ugyanazon a munkaterületen maradva kattintson a **Jelentések** lapra. Megjelenik az újonnan importált jelentés egy sárga csillaggal. A megnyitásához kattintson a jelentés nevére.

    ![jelentések fül](media/service-dashboard-create/power-bi-reports.png)
2. A jelentés Olvasás nézetben nyílik meg. Figyelje meg, hogy alul két lapfül látható: Kedvezményelemzés és értékesítés áttekintése. Minden egyes lap a jelentés egy-egy oldalát jelképezi.
    Válassza a **Jelentés szerkesztése** elemet a jelentés Szerkesztési nézetben való megnyitásához.

    ![jelentés az Olvasó nézetben](media/service-dashboard-create/power-bi-reading-view.png)
3. A rendelkezésre álló beállítások megjelenítéséhez húzza a mutatót a vizualizáció fölé. A vizualizációnak az irányítópulthoz történő hozzáadásához kattintson a rögzítés ![](media/service-dashboard-create/power-bi-pin-icon.png) ikonra.

    ![vigye az egérmutatót egy csempe fölé](media/service-dashboard-create/power-bi-hover.png)
4. Mivel most egy új irányítópultot hozunk létre, válassza az **Új irányítópult** lehetőséget, és adjon meg egy nevet.

   ![Rögzítés az irányítópulton párbeszédablak](media/service-dashboard-create/power-bi-pin-tile.png)
5. A **Rögzítés** lehetőség kiválasztásakor a Power BI az aktuális munkaterületen létrehoz egy új irányítópultot. A **Rögzítve az irányítópulton** üzenet megjelenésekor válassza az **Ugrás az irányítópultra** lehetőséget. Ha a rendszer felkéri a jelentés mentésére, válassza a **Mentés** lehetőséget.

     ![sikert jelző üzenet](media/service-dashboard-create/power-bi-pin-success.png)
6. A Power BI ekkor megnyitja az új irányítópultot, ahol egy csempe (az imént rögzített vizualizáció) található.

   ![irányítópult egy csempével](media/service-dashboard-create/power-bi-pinned.png)
7. A jelentéshez való visszatéréshez kattintson a csempére. Rögzítsen még néhány csempét az irányítópulton. Ha a **Rögzítés az irányítópulton** ablak megjelenik, ezúttal válassza a **Meglévő irányítópult** lehetőséget.  

   ![Rögzítés az irányítópulton párbeszédablak](media/service-dashboard-create/power-bi-existing-dashboard.png)

## <a name="pin-an-entire-report-page-to-the-dashboard"></a>Teljes jelentésoldal rögzítése irányítópultra
A vizualizációk egyenkénti rögzítése helyett lehetőség van arra is, hogy [teljes jelentésoldalt rögzítsen *élő csempeként*](service-dashboard-pin-live-tile-from-report.md). Nézzük is meg, hogyan.

1. A jelentésszerkesztőben válassza a **Spend Overview** (Költségek áttekintése) lapfület, ezzel megnyitja a jelentés 2. oldalát.

   ![Jelentés lap](media/service-dashboard-create/power-bi-page-tab.png)

2. Az itt látható vizualizációk mindegyikét az irányítópultra szeretnénk rögzíteni.  Válassza a menüsáv jobb felső sarkában található **Élő oldal rögzítése** lehetőséget. Az irányítópulton az élő csempék a lap frissítésekor minden alkalommal frissülnek.

   ![a jelentésszerkesztő jobb felső sarka](media/service-dashboard-create/power-bi-pin-live.png)

3. Ha a **Rögzítés az irányítópulton** ablak megjelenik, válassza a **Meglévő irányítópult** lehetőséget.

   ![Rögzítés az irányítópulton párbeszédablak](media/service-dashboard-create/power-bi-pin-live2.png)

4. Amikor megkapja az értesítést a sikeres műveletről, válassza az **Ugrás az irányítópultra** lehetőséget. Ott találja majd a jelentésből rögzített összes csempét. Az alábbi példában az 1. oldalról két csempét rögzítettünk, és rögzítettük a jelentés 2. oldalát is, amely egy élő csempének felel meg.

   ![irányítópult](media/service-dashboard-create/power-bi-dashboard.png)

Gratulálunk, létrehozta az első irányítópultját! Most, hogy már rendelkezik irányítópulttal, számos további lehetőség nyílik meg.  Próbálja ki az alábbiakban javasolt **Következő lépések** egyikét, vagy próbálkozzon saját maga.   

## <a name="next-steps"></a>Következő lépések
* [Csempék átméretezése és áthelyezése](service-dashboard-edit-tile.md)
* [Információk az irányítópult csempéiről](service-dashboard-tiles.md)
* [Az irányítópult megosztása alkalmazás létrehozásával](service-create-workspaces.md)
* [Power BI – Alapfogalmak](service-basic-concepts.md)
* [Tippek a tökéletes irányítópult megtervezéséhez](service-dashboards-design-tips.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
