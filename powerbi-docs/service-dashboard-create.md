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
ms.date: 07/17/2019
ms.author: maggies
ms.openlocfilehash: b50d247f54cfe2af4cefbd14b9528b1dfa263acf
ms.sourcegitcommit: bc688fab9288ab68eaa9f54b9b59cacfdf47aa2e
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/30/2019
ms.locfileid: "68624233"
---
# <a name="create-a-power-bi-dashboard-from-a-report"></a>Power BI-irányítópult létrehozása jelentésből
Áttekintette [A Power BI-irányítópultok – bevezetés](service-dashboards.md) részben leírtakat, és most saját irányítópultot kíván létrehozni. Az irányítópultok létrehozásának számos különböző módja van. Többek között jelentésből, előzmények nélkül, adatkészletből, illetve egy meglévő irányítópult megkettőzésével is létrehozhatók.  

A kezdés sokak számára bonyolult lehet, ezért egy gyorsan és egyszerűen elkészíthető irányítópulttal kezdünk, amelyre már elkészült jelentésből fogunk vizualizációkat rögzíteni. 

A rövid útmutató elvégzése után már ismerni fogja a következőket:
- A jelentések és irányítópultok közötti kapcsolat
- A Szerkesztési nézet megnyitása a jelentésszerkesztőben
- Csempék rögzítése 
- Navigálás az irányítópultokban és a jelentésekben 

## <a name="who-can-create-a-dashboard"></a>Ki hozhat lére irányítópultot?
Az irányítópult létrehozása *létrehozói* művelet, ezért csak akkor végezheti el, ha jogosultsága van a jelentést szerkeszteni. Szerkesztési jogosultsággal a jelentés létrehozója rendelkezik, valamint azok, akikek a létrehozó engedélyezte ezt. Ha például Dávid létrehoz egy jelentést az ABC munkaterületen, majd hozzáadja Önt ehhez a munkaterülethez, akkor Ön is és Dávid is rendelkezik majd szerkesztési jogosultsággal. Ha azonban a jelentést megosztották Önnel akár közvetlenül, akár egy [Power BI-alkalmazás](service-create-distribute-apps.md) részeként (más szóval ha Ön a jelentés *felhasználója*), akkor Ön nem fog tudni csempéket rögzíteni az irányítópultra.
 
![Irányítópult](media/service-dashboard-create/power-bi-completed-dashboard-small.png)

> [!NOTE] 
> Az irányítópult a Power BI szolgáltatás, nem pedig a Power BI Desktop funkciója. Power BI-mobileszközökön csak [megtekinteni és megosztani](consumer/mobile/mobile-apps-view-dashboard.md) lehet az irányítópultokat, létrehozni nem.
>
> 

## <a name="video-create-a-dashboard-by-pinning-visuals-and-images-from-a-report"></a>Videó: Irányítópult létrehozása jelentésből származó vizualizációk és képek rögzítésével
Tekintse meg, ahogy Amanda bemutatja egy új irányítópult létrehozását jelentésből származó vizualizációk rögzítésével. Ezután az [Adatkészlet importálása jelentés használatával](#import-a-dataset-with-a-report) lépesekiet követve próbálkozzon meg a feladattal saját maga is a Beszerzéselemzési minta használatával.
    

<iframe width="560" height="315" src="https://www.youtube.com/embed/lJKgWnvl6bQ" frameborder="0" allowfullscreen></iframe>

## <a name="import-a-dataset-with-a-report"></a>Adatkészlet importálása jelentés használatával
A Power BI egyik mintaként szolgáló adatkészletét fogjuk importálni, majd egy új irányítópult létrehozására felhasználni. Az itt használt minta egy olyan Excel-munkafüzet, amelyben két PowerView-munkalap található. Amikor a Power BI importálja a munkafüzetet, egy adatkészletet és egy jelentést is hozzáad a munkaterülethez. A rendszer a jelentést automatikusan hozza létre a PowerView-munkalapokból.

1. Töltse le a Beszerzéselemzési minta [Excel-fájlt](http://go.microsoft.com/fwlink/?LinkId=529784). Javasoljuk, hogy a OneDrive Vállalati verziójában mentse azt.
2. Nyissa meg a Power BI szolgáltatást a böngészőben (app.powerbi.com).
3. A bal oldalon lévő navigációs panelen válassza a **Saját munkaterület**, majd az **Adatok lekérése** lehetőséget.

    ![Bal oldali navigációs ablaktábla](media/service-dashboard-create/power-bi-get-data3.png)
5. Válassza a **Fájlok** lehetőséget.

   ![Fájlok lekérése](media/service-dashboard-create/power-bi-select-files.png)
6. Keresse meg a helyet, ahová a Beszerzéselemzési minta Excel-fájlját mentette. Jelölje ki azt, és válassza a **Kapcsolódás** lehetőséget.

   ![Csatlakozás fájlokhoz](media/service-dashboard-create/power-bi-connectnew.png)
7. Ehhez a gyakorlathoz válassza az **Importálás** lehetőséget.

    ![OneDrive Vállalati verzió ablak](media/service-dashboard-create/power-bi-import.png)
8. A sikert jelző üzenet megjelenésekor az **x** jelre kattintva zárja be azt.

   ![Sikert jelző üzenet](media/service-dashboard-create/power-bi-view-datasetnew.png)

### <a name="open-the-report-and-pin-tiles-to-your-dashboard"></a>A jelentés megnyitása, és csempék rögzítése az irányítópulton
1. Ugyanezen a munkaterületen válassza a **Jelentések** lapot, majd a **Beszerzéselemzési minta** elemet a jelentés megnyitásához.

    ![Jelentések lap](media/service-dashboard-create/power-bi-reports.png) A jelentés Olvasó nézetben nyílik meg. Figyelje meg, hogy alul két lapfül látható: **Kedvezményelemzés** és **Értékesítés áttekintése**. Minden egyes lap a jelentés egy-egy oldalát jelképezi.

2. Válassza a **Jelentés szerkesztése** elemet a jelentés Szerkesztési nézetben való megnyitásához.

    ![Jelentés az Olvasó nézetben](media/service-dashboard-create/power-bi-reading-view.png)
3. A rendelkezésre álló beállítások megjelenítéséhez húzza a mutatót a vizualizáció fölé. A vizualizációnak az irányítópulthoz történő hozzáadásához kattintson a gombostű ikonra ![Gombostű ikon](media/service-dashboard-create/power-bi-pin-icon.png).

    ![Vigye az egérmutatót egy csempe fölé](media/service-dashboard-create/power-bi-hover.png)
4. Mivel most egy új irányítópultot hozunk létre, válassza az **Új irányítópult** lehetőséget, és adjon meg egy nevet.

    ![Rögzítés az irányítópulton párbeszédablak](media/service-dashboard-create/power-bi-pin-tile.png)
5. A **Rögzítés** lehetőség kiválasztásakor a Power BI az aktuális munkaterületen létrehoz egy új irányítópultot. A **Rögzítve az irányítópulton** üzenet megjelenése után válassza az **Ugrás az irányítópultra** lehetőséget. Ha a rendszer felkéri a jelentés mentésére, válassza a **Mentés** lehetőséget.

    ![Sikert jelző üzenet](media/service-dashboard-create/power-bi-pin-success.png)

    A Power BI megnyitja az új irányítópultot. Ezen egy csempe található, az imént rögzített vizualizáció.

   ![irányítópult egy csempével](media/service-dashboard-create/power-bi-pinned.png)
7. A jelentéshez való visszatéréshez kattintson a csempére. Rögzítsen még néhány csempét az irányítópulton. Ha a **Rögzítés az irányítópulton** ablak megjelenik, válassza a **Meglévő irányítópult** lehetőséget.  

   ![Rögzítés az irányítópulton párbeszédablak](media/service-dashboard-create/power-bi-existing-dashboard.png)

## <a name="pin-an-entire-report-page-to-the-dashboard"></a>Teljes jelentésoldal rögzítése irányítópultra
A vizualizációk egyenkénti rögzítése helyett lehetőség van arra is, hogy [teljes jelentésoldalt rögzítsen *élő csempeként*](service-dashboard-pin-live-tile-from-report.md). Nézzük is meg, hogyan.

1. A jelentésszerkesztőben válassza a **Költségek áttekintése** lapot, ezzel megnyitja a jelentés 2. oldalát.

   ![Jelentés lap](media/service-dashboard-create/power-bi-page-tab.png)

2. A jelentés vizualizációinak mindegyikét az irányítópultra szeretnénk rögzíteni. Válassza a menüsáv jobb felső sarkában található **Élő oldal rögzítése** lehetőséget. Az irányítópulton az élő csempék a lap frissítésekor minden alkalommal frissülnek.

   ![A jelentésszerkesztő jobb felső sarka](media/service-dashboard-create/power-bi-pin-live.png)

3. Ha a **Rögzítés az irányítópulton** ablak megjelenik, válassza a **Meglévő irányítópult** lehetőséget.

   ![Rögzítés az irányítópulton párbeszédablak](media/service-dashboard-create/power-bi-pin-live2.png)

4. Amikor megkapja az értesítést a sikeres műveletről, válassza az **Ugrás az irányítópultra** lehetőséget. Ott találja majd a jelentésből rögzített összes csempét. Az alábbi példában az 1. oldalról két csempét rögzítettünk, és rögzítettük a jelentés 2. oldalát is, amely egy élő csempének felel meg.

   ![Irányítópult](media/service-dashboard-create/power-bi-dashboard.png)

## <a name="next-steps"></a>Következő lépések
Gratulálunk, létrehozta az első irányítópultját! Most, hogy már rendelkezik irányítópulttal, számos további lehetőség nyílik meg. Tekintse át a javasolt cikkek egyikét, vagy próbálkozzon saját maga: 

* [Csempék átméretezése és áthelyezése](service-dashboard-edit-tile.md)
* [Információk az irányítópult csempéiről](service-dashboard-tiles.md)
* [Az irányítópult megosztása alkalmazás létrehozásával](service-create-workspaces.md)
* [Power BI – Alapfogalmak](service-basic-concepts.md)
* [Tippek a tökéletes irányítópult megtervezéséhez](service-dashboards-design-tips.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/).
