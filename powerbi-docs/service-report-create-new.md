---
title: Jelentés létrehozása adatkészletből
description: A Power BI-jelentés létrehozása adatkészletből.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 6b69c2b1fa811d395a26403de852c44af33491c7
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770232"
---
# <a name="create-a-report-in-the-power-bi-service-by-importing-a-dataset"></a>Hozzon létre egy jelentést a Power BI szolgáltatásban adatkészlet importálásával
Már elolvasta a [Jelentések a Power BI-ban](consumer/end-user-reports.md) című cikket, és szeretne létrehozni egy saját jelentést. Különböző módon hozhat létre egy jelentést. Ebben a cikkben fogja először létrehozunk egy alapszintű jelentést egy Excel-adatkészletből a Power BI szolgáltatásban. Ha már megismerte a jelentés létrehozásának alapjait, tekintse meg a [további lépések](#next-steps) további végén speciális jelentés témaköröket.  

## <a name="prerequisites"></a>Előfeltételek
- [Regisztráció a Power BI szolgáltatásra](service-self-service-signup-for-power-bi.md). A jelentések készítéséhez a Power BI Desktop használatával, lásd: [Desktop jelentés nézet](desktop-report-view.md). 
- [Töltse le a kiskereskedelmi elemzési minta Excel-adatkészletét](http://go.microsoft.com/fwlink/?LinkId=529778) , és mentse helyileg vagy a vállalati OneDrive-bA.

## <a name="import-the-dataset"></a>Adatkészlet importálása
Ha ezzel a módszerrel hoz létre egy jelentést, akkor annak kiindulópontja egy adatkészlet és egy üres jelentésvászon lesz. A kiskereskedelmi elemzési minta Excel-adatkészletét a tudja követni.

1. Azt fogjuk a jelentés létrehozása egy Power BI szolgáltatás munkaterületén, ezért válasszon ki egy meglévő munkaterületet vagy hozzon létre egy egyet.
   
   ![Alkalmazás-munkaterületek listája](media/service-report-create-new/power-bi-workspaces2.png)
2. A bal oldali navigációs ablaktábla alján válassza **adatok**.
   
   ![Adatok lekérése](media/service-report-create-new/power-bi-get-data3.png)
3. Válassza a **Fájlok** lehetőséget, majd navigáljon arra a helyre, ahova a Kiskereskedelmi elemzési mintát mentette.
   
    ![a Fájlok lehetőség kiválasztása](media/service-report-create-new/power-bi-select-files.png)
4. Ehhez a gyakorlathoz válassza az **Importálás** lehetőséget.
   
   ![az Importálás kiválasztása](media/service-report-create-new/power-bi-import.png)
5. Ha megtörtént az adatkészlet importálása, válassza az **Adatkészlet megtekintése** lehetőséget.
   
   ![az Adatkészlet megtekintése lehetőség kiválasztása](media/service-report-create-new/power-bi-view-dataset.png)
6. Ha megtekint egy adatkészletet, azzal tulajdonképpen a jelentésszerkesztőt nyitja meg.  Egy üres vásznat fog látni, és a jelentések készítéséhez szükséges eszközöket.
   
   ![jelentésszerkesztő](media/service-report-create-new/power-bi-blank-report.png)

> [!TIP]
> Ha ismeri a Jelentésszerkesztő vásznat, vagy felfrissíteni ismereteit, [a Jelentésszerkesztő bemutatása](service-the-report-editor-take-a-tour.md) a folytatás előtt. > 
> 

## <a name="add-a-radial-gauge-to-the-report"></a>Mérőműszer felvétele jelentésbe
Most hogy már importáltuk az adatkészletünket, kezdjük el megválaszolni a kérdéseket.  A marketingigazgató tudni szeretné, hogy mennyire állunk közel ahhoz, hogy elérjük az idei év értékesítési célkitűzéseit. A mérőműszer [vizualizáció egy jó választás](visuals/power-bi-report-visualizations.md), ha ilyen típusú adatokat szeretnénk megjeleníteni.

1. A Mezők ablaktáblán válassza a **Sales** > **This Year Sales** > **Érték** elemet.
   
    ![sávdiagram a jelentésszerkesztőben](media/service-report-create-new/power-bi-report-step1.png)
2. Konvertálja a vizualizációt mérőműszerré. Ehhez válassza a **Vizualizációk** ablaktáblán a Mérőműszer ![Mérőműszer ikon](media/service-report-create-new/powerbi-gauge-icon.png) sablont.
   
    ![Mérőműszer vizualizáció a jelentésszerkesztőben](media/service-report-create-new/power-bi-report-step2.png)
3. Húzza a **Sales** > **This Year Sales** > **Cél** elemet a **Célérték** gyűjtőbe. Úgy látszik, nagyon közel vagyunk a célkitűzésünk eléréséhez.
   
    ![Mérőműszer vizualizáció a Cél elemmel mint Célérték](media/service-report-create-new/power-bi-report-step3.png)
4. Most már lehet egy időben, a jelentés mentéséhez.
   
   ![Fájl menü](media/service-report-create-new/powerbi-save.png)

## <a name="add-an-area-chart-and-slicer-to-the-report"></a>Területdiagram és szeletelő felvétele a jelentésbe
Meg kell válaszolnunk a marketingigazgató újabb kérdéseit. Szeretné tudni, hogy milyenek az idei év értékesítési mutatói a tavalyi évhez képest. És ezt az egyes körzetekre lebontva szeretné látni.

1. Először is csináljunk egy kis helyet a vásznunkon. Válassza ki a Mérőműszert és helyezze a jobb felső sarokba. Ezután fogja meg az egyik sarkát és kicsinyítse le.
2. Szüntesse meg a mérőműszer kijelölt állapotát. A Mezők ablaktáblán válassza a **Sales** > **This Year Sales** > **Érték**, majd a **Sales** > **Last Year Sales** elemeket.
   
    ![jelentésszerkesztő egy Mérőműszerrel és egy sávdiagrammal](media/service-report-create-new/power-bi-report-step4.png)
3. Konvertálja a vizualizációt területdiagrammá. Ehhez válassza a **Vizualizációk** ablaktáblán a Területdiagram ![diagramikon](media/service-report-create-new/power-bi-areachart-icon.png) sablont.
4. Adja hozzá a **Time** > **Period** elemet a **Tengely** gyűjtőhöz.
   
    ![jelentésszerkesztő aktív Területdiagrammal](media/service-report-create-new/power-bi-report-step5.png)
5. A vizualizáció időszakok szerinti rendezéséhez válassza a három pontot (...), majd a **Rendezés szempontja: Időszak** lehetőséget.
6. És most vegyük fel a szeletelőt. Válassza ki a vászon egy üres területét, majd a Szeletelő ![Szeletelő ikon](media/service-report-create-new/power-bi-slicer-icon.png) sablont. A vászon egy üres szeletelő most már van.
   
    ![A jelentésvászon](media/service-report-create-new/power-bi-report-step6.png)    
7. A Mezők ablaktáblán válassza a **District** > **District** elemet. Helyezze át és méretezze át a szeletelőt.
   
    ![Jelentésszerkesztő, Kerület hozzáadása](media/service-report-create-new/power-bi-report-step7.png)  
8. A szeletelő használatával mintákat és összefüggéseket kereshet az egyes körzetek szerint.
   
   ![videó a szeletelő használatáról](media/service-report-create-new/power-bi-slicer-video2.gif)  

Az adatokat tovább vizsgálhatja, és vizualizációkat is adhat hozzá. Ha különösen érdekes információt talál, azt [rögzítheti egy irányítópultra](service-dashboard-pin-tile-from-report.md).

## <a name="next-steps"></a>Következő lépések

* Tudnivalók arról, hogyan történik a [vizualizációk rögzítése egy irányítópulton](service-dashboard-pin-tile-from-report.md)   
* További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

