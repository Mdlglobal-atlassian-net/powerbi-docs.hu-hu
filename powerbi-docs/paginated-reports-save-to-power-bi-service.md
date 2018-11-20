---
title: Lapszámozott jelentés közzététele a Power BI szolgáltatásban | Microsoft Docs
description: Ez az oktatóanyag arról szól, hogyan tehet közzé lapszámozott jelentéseket a Power BI szolgáltatásba, a helyi számítógépről feltöltve őket.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: report-builder
ms.topic: conceptual
ms.date: 11/05/2018
ms.author: maggies
ms.openlocfilehash: 6f2d1a4e4de87ea6eb63826b59286a9abd54b94f
ms.sourcegitcommit: b23fdcc0ceff5acd2e4d52b15b310068236cf8c7
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/07/2018
ms.locfileid: "51267971"
---
# <a name="publish-a-paginated-report-to-the-power-bi-service"></a>Lapszámozott jelentés közzététele a Power BI szolgáltatásban

Ebből az oktatóanyagból a helyi számítógépről feltöltött lapszámozott jelentések Power BI szolgáltatásba való közzétételét sajátíthatja el. Lapszámozott jelentéseket a saját munkaterületre, vagy bármely más munkaterületre is feltölthet, ha a munkaterület prémium szintű kapacitásban van. Keresse a gyémánt ikont ![A Power BI Premium-kapacitás gyémánt ikonja](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) a munkaterület neve mellett. 

Ha jelentésének helyszíni adatforrása van, akkor a jelentés feltöltése után [átjárót kell létrehoznia](#create-a-gateway-to-an-on-premises-data-source).

## <a name="add-a-workspace-to-a-premium-capacity"></a>Munkaterület hozzáadása prémium szintű kapacitáshoz

Lehetséges, hogy a munkaterület mellett nincs gyémánt ikon. ![A Power BI Premium-kapacitás gyémánt ikonja](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) Ilyenkor hozzá kell adnia a munkaterületet egy prémium szintű kapacitáshoz. 

1. Válassza a **Munkaterületek** elemet, a munkaterület neve melletti három pontot (**...**), majd a **Munkaterület szerkesztése** lehetőséget.

    ![A Munkaterület szerkesztése elem kiválasztása](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace.png)

1. A **Munkaterület szerkesztése** párbeszédablakban bontsa ki a **Speciális** elemet, majd állítsa a **Dedikált kapacitás** kapcsolót a **Be** állásba.

    ![Dedikált kapacitás beállítása](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace-dialog.png)

   Előfordulhat, hogy ezt nem tudja módosítani. Ilyen esetben forduljon a Power BI Premium-kapacitás rendszergazdájához, és kérjen hozzárendelési jogosultságot, hogy munkaterületét felvehesse egy prémium szintű kapacitásba.


## <a name="upload-a-paginated-report"></a>Lapszámozott jelentés feltöltése

1. Készítse el lapszámozott jelentését a Jelentéskészítőben, és mentse a helyi számítógépre.

1. Egy böngészőben nyissa meg a Power BI szolgáltatást, és keresse meg a prémium szintű munkaterületet, ahol a jelentést közzé szeretné tenni. Figyelje meg a gyémánt ikont. ![A Power BI Premium-kapacitás gyémánt ikonja](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) A név mellett kell lennie. 

1. Válassza az **Adatok beolvasása** lehetőséget.

    ![Adatok beolvasása a Power BI-ban](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-get-data.png)

1. A **Fájlok** mezőben válassza a **Beolvasás** lehetőséget.

    ![Fájlok beolvasása a Power BI-ban](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-files-get.png)

1. Válassza a **Helyi fájl** lehetőséget, tallózással keresse meg a lapszámozott jelentést, majd válassza a **Megnyitás** lehetőséget.

    ![Helyi fájl kiválasztása](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-local-file.png)

1. Válassza a **Tovább** > **Hitelesítő adatok szerkesztése** lehetőséget.

    ![A Hitelesítő adatok szerkesztése lehetőség kiválasztása](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-edit-credentials.png)

1. Konfigurálja hitelesítő adatait, majd válassza a **Bejelentkezés** lehetőséget.

    ![Hitelesítő adatok szerkesztése](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-credentials.png)

   Jelentése megjelenik a jelentések listájában.

    ![Lapszámozott jelentés a Jelentések listában](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

1. Jelölje ki, és nyissa meg a Power BI szolgáltatásban. Ha a jelentés paraméterekkel rendelkezik, akkor csak azok kiválasztása után tekinthető meg.
 
    ![Paraméterek kiválasztása](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

## <a name="create-a-gateway"></a>Átjáró létrehozása

Mint minden Power BI-jelentésnél, itt is érvényes, hogy ha a jelentésnek helyszíni adatforrása van, akkor az adatok eléréséhez átjárót kell létrehoznia, vagy átjáróhoz kell csatlakoznia.

1. Válassza a jelentés neve melletti **Kezelés** lehetőséget.

   ![A lapszámozott jelentés kezelése](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-manage.png)

1. A részleteket és a további teendőket a Power BI szolgáltatásról szóló, [Átjáró telepítése](service-gateway-install.md) című cikkben találja meg.

### <a name="gateway-limitations"></a>Átjárókra vonatkozó korlátozások

Az átjárók jelenleg nem támogatják a többértékű paramétereket.


## <a name="next-steps"></a>Következő lépések

- [Lapszámozott jelentés megtekintése a Power BI szolgáltatásban](paginated-reports-view-power-bi-service.md)
- [Mik azok a lapszámozott jelentések a Power BI Premiumban? (előzetes verzió)](paginated-reports-report-builder-power-bi.md)

