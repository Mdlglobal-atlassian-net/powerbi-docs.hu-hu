---
title: Többoldalas jelentés létrehozása a Power BI jelentéskészítő kiszolgálóhoz
description: Ismerje meg, hogyan hozhat létre többoldalas jelentést a Power BI jelentéskészítő kiszolgálóra néhány egyszerű lépésben.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 10/22/2018
ms.author: maggies
ms.openlocfilehash: 9e3a45e7648fd38413c2d45582981bac5e91cd2a
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770512"
---
# <a name="create-a-paginated-report-for-power-bi-report-server"></a>Többoldalas jelentés létrehozása a Power BI jelentéskészítő kiszolgálóhoz
Mint ahogyan az elnevezés is sugallja, a többoldalas jelentések egyszerre több oldalon is átnyúlhatnak. Az elrendezésük rögzített formátumban történik, és precíz testreszabási lehetőségeket biztosítanak. A többoldalas jelentések .rdl-fájlok.

A többoldalas jelentéseket a Power BI jelentéskészítő kiszolgáló webportálján és az SQL Server Reporting Services (SSRS) webportálján tárolhatja és kezelheti. Létrehozhatja őket a Jelentéskészítőben vagy az SQL Server Data Tools (SSDT) eszközkészletben található Jelentéstervező használatával, majd közzéteheti őket az egyiknek a webportálján. Ekkor a jelentések megtekinthetővé válnak a cégen belüli olvasók számára egy böngészőben, vagy a Power BI mobilalkalmazás használatával a mobileszközeiken.

![Power BI jelentéskészítő kiszolgáló többoldalas jelentése](media/quickstart-create-paginated-report/reportserver-paginated-report.png)

Ha már hozott létre többoldalas jelentéseket a Jelentéskészítőben vagy a Jelentéstervezőben, akkor készen áll arra, hogy a Power BI jelentéskészítő kiszolgálóra is létrehozzon ilyen jelentéseket. Ha még nem hozott létre ilyeneket, akkor néhány gyors lépésben felkészülhet rá.

## <a name="step-1-install-and-start-report-builder"></a>1. lépés: Töltse le és indítsa el a Jelentéskészítőt
Lehet, hogy korábban már telepítette a Jelentéskészítőt, hogy jelentéseket hozzon létre egy SSRS-kiszolgálóra. Használhatja ugyanezt a verziójú Jelentéskészítőt arra is, hogy a Power BI jelentéskészítő kiszolgálóra hozzon létre jelentéseket. Ha még nem telepítette, akkor ezt egyszerűen megteheti.

1. A Power BI jelentéskészítő kiszolgáló webportálján válassza az **New** (Új) > **Paginated Report** (Többoldalas jelentés) lehetőséget.
   
    ![Új többoldalas jelentés menüje](media/quickstart-create-paginated-report/reportserver-new-paginated-report-menu.png)
   
    Ha a Jelentéskészítő nincs telepítve a számítógépén, akkor ez a lépés végigvezeti a telepítés folyamatán.
2. A telepítést követően megnyílik a Jelentéskészítő az **Új jelentés vagy adatkészlet** képernyőn.
   
    ![Új jelentés vagy adatkészlet képernyő](media/quickstart-create-paginated-report/reportserver-paginated-new-report-screen.png)
3. Válassza ki a létrehozni kívánt jelentés típusának varázslóját:
   
   * Táblázat vagy mátrix
   * Diagram
   * Térkép
   * Üres
4. Kezdjük a Diagram varázslóval.
   
    A Diagram varázsló végigvezeti azokon a lépéseken, amelyekkel létrehozhat egy egyszerű diagramot egy jelentésben. Onnan már szinte korlátlan lehetőségei lesznek a jelentése testreszabására.

## <a name="step-2-go-through-the-chart-wizard"></a>2. lépés: Haladjon végig a Diagram varázsló lépésein
A Diagram varázsló végigvezeti azokon az alapvető lépéseken, amelyekkel létrehozhat egy vizualizációt egy jelentésben.

A többoldalas jelentések sokféle adatforráshoz kapcsolódhatnak, a Microsoft SQL Servertől és a Microsoft Azure SQL Database-től kezdve egészen az Oracle-ig, a Hyperionig és egyéb adatforrásokig. További információk a [többoldalas jelentéseket támogató adatforrásokról](connect-data-sources.md).

A Diagram varázsló első lépése az **Adatkészlet kiválasztása**, ahol létrehozhat egy adatkészletet, vagy kiválaszthat egy megosztott adatkészletet egy kiszolgálóról. Az *adatkészletek* egy külső adatforráson végzett lekérdezés jelentésadatait adják vissza.

1. Válassza a **Tallózás...** lehetőséget, válasszon ki egy megosztott adatkészletet egy kiszolgálón, majd válassza a **Megnyitás** > **Tovább** lehetőségeket.
   
    ![Diagram varázsló: Adathalmaz kiválasztása](media/quickstart-create-paginated-report/reportserver-paginated-choose-dataset.png)
   
     Új adatkészletet szeretne létrehozni? Tekintse meg a [Megosztott vagy beágyazott adatkészlet létrehozása](https://docs.microsoft.com/sql/reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs) című cikket.
2. Válasszon egy diagramtípust, esetünkben a sávdiagramot.
   
    ![Diagram varázsló: Diagramtípus](media/quickstart-create-paginated-report/reportserver-paginated-choose-chart-type.png)
3. A mezők elrendezéséhez húzza őket a **Kategóriák**, **Sorozatok** és **Értékek** területekre.
   
    ![Diagram varázsló: Mezők elrendezése](media/quickstart-create-paginated-report/reportserver-paginated-arrange-fields.png)
4. Válassza a **Tovább** > **Befejezés** lehetőséget.

## <a name="step-3-design-your-report"></a>3. lépés: A jelentés megtervezése
Most már a Jelentéstervező nézetben van. Észreveheti, hogy az adatok csupán helyőrző adatok, nem az Ön saját adatai.

![Jelentéstervező nézet](media/quickstart-create-paginated-report/reportserver-paginated-preview-report.png)

* Az saját adatainak megtekintéséhez válassza a **Futtatás** lehetőséget.
  
     ![Jelentés futtatása](media/quickstart-create-paginated-report/reportserver-paginated-run-report.png)
* A Jelentéstervező nézethez való visszatéréshez válassza a **Tervezés** lehetőséget.

Módosíthatja az imént létrehozott diagramot, megváltoztathatja az elrendezését, az értékeit, a jelmagyarázatát, vagyis szinte bármit.

Sok más típusú vizualizációt is felvehet, például mérőműszereket, táblázatokat, mátrixokat, térképeket stb. Felvehet fejléceket és lábléceket több oldalhoz is. Tekintse meg [A Jelentéskészítő oktatóanyagait](https://docs.microsoft.com/sql/reporting-services/report-builder-tutorials) és próbálja ki ezeket.

![A Jelentéskészítő tervező nézete](media/quickstart-create-paginated-report/reportserver-paginated-finished-design-report.png)

## <a name="step-4-save-your-report-to-the-report-server"></a>4. lépés: Mentse a jelentést a jelentéskészítő kiszolgálón
Ha elkészült a jelentése, mentse a Power BI jelentéskészítő kiszolgálóra.

1. A **Fájl** menüben válassza a **Mentés másként** lehetőséget, majd mentse a jelentést a jelentéskészítő kiszolgálóra. 
2. Most már megtekintheti a jelentést a böngészőben.
   
    ![Többoldalas jelentés böngészőben](media/quickstart-create-paginated-report/reportserver-paginated-report.png)

## <a name="next-steps"></a>Következő lépések
Számos nagyszerű erőforrás nyújt segítséget, ha jelentést szeretne készíteni a Jelentéskészítőben vagy az SQL Server Data Tools eszközkészletben található Jelentéstervezőben. Érdemes a Jelentéskészítő oktatóanyagaival kezdeni.

* [A Jelentéskészítő oktatóanyagai](https://docs.microsoft.com/sql/reporting-services/report-builder-tutorials)
* [Mi a Power BI jelentéskészítő kiszolgáló?](get-started.md)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

