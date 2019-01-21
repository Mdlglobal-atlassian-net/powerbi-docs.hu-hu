---
title: 'Új jelentés létrehozása adatkészletből '
description: Hozzon létre egy új Power BI-jelentést egy adatkészletből.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/24/2018
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 31a7221d3b284e6342b192384f92616a52e12631
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54280252"
---
# <a name="create-a-new-report-in-power-bi-service-by-importing-a-dataset"></a>Új jelentés létrehozása a Power BI szolgáltatásban adatkészlet importálásával
Már elolvasta a [Jelentések a Power BI-ban](consumer/end-user-reports.md) című cikket, és szeretne létrehozni egy saját jelentést. A jelentések több különböző módon is létrehozhatók. Ebben a cikkben kezdésként egy Excel-adatkészletből egy alapszintű jelentést fogunk létrehozni a Power BI szolgáltatásban. Ha már megismerte a jelentés létrehozásának alapjait, akkor a lap alján található **Következő lépések** hivatkozással továbbhaladhat a jelentésekkel kapcsolatos összetettebb témakörökre is.  

## <a name="prerequisites"></a>Előfeltételek
> - A Power BI szolgáltatás (arról, hogy hogyan hozhat létre jelentést a Power BI Desktopban lásd: [Desktop jelentés nézet](desktop-report-view.md) )  
> - A Kiskereskedelmi elemzési minta adatkészlete

## <a name="import-the-dataset"></a>Adatkészlet importálása
Ha ezzel a módszerrel hoz létre egy jelentést, akkor annak kiindulópontja egy adatkészlet és egy üres jelentésvászon lesz. Ahhoz, hogy követhesse a lépéseket, [töltse le a Kiskereskedelmi elemzési minta Excel-adatkészletét](http://go.microsoft.com/fwlink/?LinkId=529778), és mentse a OneDrive Vállalati verzióra (javasolt) vagy lokálisan a számítógépére.

1. A jelentést a Power BI szolgáltatás egy munkaterületén fogjuk létrehozni, ezért válasszon ki egy meglévő munkaterületet, vagy hozzon létre egy újat.
   
   ![Alkalmazás-munkaterületek listája](media/service-report-create-new/power-bi-workspaces2.png)
2. A bal oldali navigációs panelen válassza az **Adatok lekérése** elemet.
   
   ![Adatok lekérése](media/service-report-create-new/power-bi-get-data3.png)
3. Válassza a **Fájlok** lehetőséget, majd navigáljon arra a helyre, ahova a Kiskereskedelmi elemzési mintát mentette.
   
    ![a Fájlok lehetőség kiválasztása](media/service-report-create-new/power-bi-select-files.png)
4. Ehhez a gyakorlathoz válassza az **Importálás** lehetőséget.
   
   ![az Importálás kiválasztása](media/service-report-create-new/power-bi-import.png)
5. Ha megtörtént az adatkészlet importálása, válassza az **Adatkészlet megtekintése** lehetőséget.
   
   ![az Adatkészlet megtekintése lehetőség kiválasztása](media/service-report-create-new/power-bi-view-dataset.png)
6. Ha megtekint egy adatkészletet, azzal tulajdonképpen a jelentésszerkesztőt nyitja meg.  Egy üres vásznat fog látni, és a jelentések készítéséhez szükséges eszközöket.
   
   ![jelentésszerkesztő](media/service-report-create-new/power-bi-blank-report.png)

> **TIPP**: Ha nem ismeri a jelentésszerkesztő vásznat, vagy szeretné felfrissíteni ismereteit, [Tekintse át a jelentésszerkesztőt](service-the-report-editor-take-a-tour.md), mielőtt továbbhaladna.
> 
> 

## <a name="add-a-radial-gauge-to-the-report"></a>Mérőműszer felvétele jelentésbe
Most hogy már importáltuk az adatkészletünket, kezdjük el megválaszolni a kérdéseket.  A marketingigazgató tudni szeretné, hogy mennyire állunk közel ahhoz, hogy elérjük az idei év értékesítési célkitűzéseit. A mérőműszer [vizualizáció egy jó választás](visuals/power-bi-report-visualizations.md), ha ilyen típusú adatokat szeretnénk megjeleníteni.

1. A Mezők ablaktáblán válassza a **Sales** > **This Year Sales** > **Érték** elemet.
   
    ![sávdiagram a jelentésszerkesztőben](media/service-report-create-new/power-bi-report-step1.png)
2. Konvertálja a vizualizációt egy Mérőműszerré, ehhez válassza a **Megjelenítések** ablaktáblán a Mérőműszer sablont ![Mérőműszer ikon](media/service-report-create-new/powerbi-gauge-icon.png).
   
    ![Mérőműszer vizualizáció a jelentésszerkesztőben](media/service-report-create-new/power-bi-report-step2.png)
3. Húzza a **Sales** > **This Year Sales** > **Cél** elemet a **Célérték** gyűjtőbe. Úgy látszik, nagyon közel vagyunk a célkitűzésünk eléréséhez.
   
    ![Mérőműszer vizualizáció a Cél elemmel mint Célérték](media/service-report-create-new/power-bi-report-step3.png)
4. Érdemes [menteni a jelentést](service-report-save.md).
   
   ![Fájl menü](media/service-report-create-new/powerbi-save.png)

## <a name="add-an-area-chart-and-slicer-to-the-report"></a>Területdiagram és szeletelő felvétele a jelentésbe
Meg kell válaszolnunk a marketingigazgató újabb kérdéseit. Szeretné tudni, hogy milyenek az idei év értékesítési mutatói a tavalyi évhez képest. És ezt az egyes körzetekre lebontva szeretné látni.

1. Először is csináljunk egy kis helyet a vásznunkon. Válassza ki a Mérőműszert és helyezze a jobb felső sarokba. Ezután fogja meg az egyik sarkát és kicsinyítse le.
2. Szüntesse meg a mérőműszer kijelölt állapotát. A Mezők ablaktáblán válassza a **Sales** > **This Year Sales** > **Érték**, majd a **Sales** > **Last Year Sales** elemeket.
   
    ![jelentésszerkesztő egy Mérőműszerrel és egy sávdiagrammal](media/service-report-create-new/power-bi-report-step4.png)
3. Konvertálja a vizualizációt egy Területdiagrammá, ehhez válassza a **Megjelenítések** ablaktáblán a Területdiagram sablont ![diagram ikon](media/service-report-create-new/power-bi-areachart-icon.png).
4. Adja hozzá a **Time** > **Period** elemet a **Tengely** gyűjtőhöz.
   
    ![jelentésszerkesztő aktív Területdiagrammal](media/service-report-create-new/power-bi-report-step5.png)
5. A vizualizáció időszakok szerinti rendezéséhez válassza a három pontot (...), majd a **Rendezés szempontja: Időszak** lehetőséget.
6. És most vegyük fel a szeletelőt. Válassza ki a vászon egy üres területét, majd a Szeletelő ![Szeletelő ikon](media/service-report-create-new/power-bi-slicer-icon.png)    sablont. Ez felvesz a vásznunkra egy üres szeletelőt.
   
    ![A jelentésvászon](media/service-report-create-new/power-bi-report-step6.png)    
7. A Mezők ablaktáblán válassza a **District** > **District** elemet. Helyezze át és méretezze át a szeletelőt.
   
    ![Jelentésszerkesztő, Kerület hozzáadása](media/service-report-create-new/power-bi-report-step7.png)  
8. A szeletelő használatával mintákat és összefüggéseket kereshet az egyes körzetek szerint.
   
   ![videó a szeletelő használatáról](media/service-report-create-new/power-bi-slicer-video2.gif)  

Az adatokat tovább vizsgálhatja, és vizualizációkat is adhat hozzá. Ha különösen érdekes információt talál, azt [rögzítheti egy irányítópultra](service-dashboard-pin-tile-from-report.md).

## <a name="next-steps"></a>Következő lépések

* Tudnivalók arról, hogyan történik a [vizualizációk rögzítése egy irányítópulton](service-dashboard-pin-tile-from-report.md)   
* További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

