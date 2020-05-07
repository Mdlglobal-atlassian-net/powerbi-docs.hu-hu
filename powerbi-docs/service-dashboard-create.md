---
title: Power BI-irányítópult létrehozása jelentésből
description: Power BI-irányítópult létrehozása jelentésből
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/17/2019
ms.author: maggies
ms.openlocfilehash: d67e7acf4309595e8bccac86119ea38f1a97797f
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "73853403"
---
# <a name="create-a-power-bi-dashboard-from-a-report"></a>Power BI-irányítópult létrehozása jelentésből
Áttekintette [A Power BI-irányítópultok – bevezetés](service-dashboards.md) részben leírtakat, és most saját irányítópultot kíván létrehozni. Az irányítópultok létrehozásának számos különböző módja van. Többek között jelentésből, előzmények nélkül, adatkészletből, illetve egy meglévő irányítópult megkettőzésével is létrehozhatók.  

Egy gyorsan és egyszerűen elkészíthető irányítópulttal kezdünk, amelyre már elkészült jelentésből fogunk vizualizációkat rögzíteni. 

Mire a cikk végére ér, tisztában lesz a következőkkel:
- A jelentések és irányítópultok közötti kapcsolat
- A Szerkesztési nézet megnyitása a jelentésszerkesztőben
- Csempék rögzítése 
- Navigálás az irányítópultokban és a jelentésekben 
 
![Irányítópult](media/service-dashboard-create/power-bi-completed-dashboard-small.png)

> [!NOTE] 
> Az irányítópult a Power BI szolgáltatás, nem pedig a Power BI Desktop funkciója. A Power BI-mobilalkalmazásokban nem hozhat létre irányítópultokat, azonban [megtekintheti és megoszthatja](consumer/mobile/mobile-apps-view-dashboard.md) azokat.
>
> 

## <a name="video-create-a-dashboard-by-pinning-visuals-and-images-from-a-report"></a>Videó: Irányítópult létrehozása jelentésből származó vizualizációk és képek rögzítésével
Tekintse meg, ahogy Amanda bemutatja egy új irányítópult létrehozását jelentésből származó vizualizációk rögzítésével. Ezután az [Adathalmaz importálása jelentés használatával](#import-a-dataset-with-a-report) című következő szakasz lépeseit követve próbálkozzon meg a feladattal saját maga is a Beszerzéselemzési minta használatával.
    

<iframe width="560" height="315" src="https://www.youtube.com/embed/lJKgWnvl6bQ" frameborder="0" allowfullscreen></iframe>

## <a name="import-a-dataset-with-a-report"></a>Adatkészlet importálása jelentés használatával
Ebben a lépésenkénti útmutatóban Power BI egyik minta-adathalmazát fogjuk importálni, majd egy új irányítópult létrehozására felhasználni. Az itt használt minta egy olyan Excel-munkafüzet, amely két PowerView-munkalapot tartalmaz. Amikor a Power BI importálja a munkafüzetet, egy adatkészletet és egy jelentést is hozzáad a munkaterülethez. A rendszer a jelentést automatikusan hozza létre a PowerView-munkalapokból.

1. Töltse le a [Beszerzéselemzési minta](https://go.microsoft.com/fwlink/?LinkId=529784) Excel-fájlt. Javasoljuk, hogy a OneDrive Vállalati verziójában mentse azt.
2. Nyissa meg a Power BI szolgáltatást a böngészőben (app.powerbi.com).
3. A navigációs panelen válassza a **Saját munkaterület**, majd az **Adatok lekérése** lehetőséget.

    ![navigációs panel](media/service-dashboard-create/power-bi-get-data-new-look.png)
5. A **Fájlok** területen válassza a **Lekérés** lehetőséget.

   ![Fájlok lekérése](media/service-dashboard-create/power-bi-select-files.png)
6. Keresse meg a helyet, ahová a Beszerzéselemzési minta Excel-fájlját mentette. Jelölje ki azt, és válassza a **Kapcsolódás** lehetőséget.

   ![Csatlakozás fájlokhoz](media/service-dashboard-create/power-bi-connectnew.png)
7. Ehhez a gyakorlathoz válassza az **Importálás** lehetőséget.

    ![OneDrive Vállalati verzió ablak](media/service-dashboard-create/power-bi-import.png)
8. A sikert jelző üzenet megjelenésekor az **x** jelre kattintva zárja be azt.

   ![Sikert jelző üzenet](media/service-dashboard-create/power-bi-view-datasetnew.png)

> [!TIP]
> Tudta? A navigációs panelt keskenyebbre méretezheti a három vonalból álló felső ikon ![a navigációs panelt elrejtő vagy megjelenítő ikon](media/service-dashboard-create/power-bi-new-look-hide-nav-pane.png) kiválasztásával. Így több hely jut magának a jelentésnek.

### <a name="open-the-report-and-pin-tiles-to-your-dashboard"></a>A jelentés megnyitása, és csempék rögzítése az irányítópulton
1. Ugyanezen a munkaterületen válassza a **Jelentések** lapot, majd a **Beszerzéselemzési minta** elemet a jelentés megnyitásához.

    ![Jelentések lap](media/service-dashboard-create/power-bi-reports.png) A jelentés Olvasó nézetben nyílik meg. Figyelje meg, hogy a bal oldalon két lapfül látható: **Kedvezményelemzés** és **Értékesítés áttekintése**. Minden egyes lap a jelentés egy-egy oldalát jelképezi.

2. Válassza a **További beállítások (...)**  > **Jelentés szerkesztése** lehetőséget, amellyel megnyitja a jelentést Szerkesztés nézetben.

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

4. Amikor megkapja az értesítést a sikeres műveletről, válassza az **Ugrás az irányítópultra** lehetőséget. Ott jelentésből rögzített összes csempét megtalálja. Az alábbi példában az 1. oldalról két csempét rögzítettünk, és rögzítettük a jelentés 2. oldalát is, amely egy élő csempének felel meg.

   ![Irányítópult](media/service-dashboard-create/power-bi-dashboard.png)

## <a name="next-steps"></a>Következő lépések
Gratulálunk, létrehozta az első irányítópultját! Most, hogy már rendelkezik irányítópulttal, számos további lehetőség nyílik meg. Tekintse át a javasolt cikkek egyikét, vagy próbálkozzon saját maga: 

* [Csempék átméretezése és áthelyezése](service-dashboard-edit-tile.md)
* [Információk az irányítópult csempéiről](service-dashboard-tiles.md)
* [Az irányítópult megosztása alkalmazás létrehozásával](service-create-workspaces.md)
* [Power BI – Alapfogalmak](service-basic-concepts.md)
* [Tippek a tökéletes irányítópult megtervezéséhez](service-dashboards-design-tips.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/).
