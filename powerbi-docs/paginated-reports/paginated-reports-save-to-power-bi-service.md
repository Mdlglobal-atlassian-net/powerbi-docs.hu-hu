---
title: Lapszámozott jelentés közzététele a Power BI szolgáltatásban
description: Ez az oktatóanyag arról szól, hogyan tehet közzé lapszámozott jelentéseket a Power BI szolgáltatásba, a helyi számítógépről feltöltve őket.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 05/04/2020
ms.openlocfilehash: a634844093f103c942b70cd81d93822ca240cf0a
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83272028"
---
# <a name="publish-a-paginated-report-to-the-power-bi-service"></a>Lapszámozott jelentés közzététele a Power BI szolgáltatásban

Ebből az oktatóanyagból a helyi számítógépről feltöltött lapszámozott jelentések Power BI szolgáltatásba való közzétételét sajátíthatja el. Lapszámozott jelentéseket a saját munkaterületre, vagy bármely más munkaterületre is feltölthet, ha a munkaterület prémium szintű kapacitásban van. Keresse a gyémánt ikont ![A Power BI Premium-kapacitás gyémánt ikonja](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) a munkaterület neve mellett. 

Ha a jelentés adatforrása a helyszínen található, átjárót kell létrehoznia a jelentés feltöltése után. Ehhez tekintse meg a cikk [Átjáró létrehozása](#create-a-gateway) című szakaszát.

## <a name="add-a-workspace-to-a-premium-capacity"></a>Munkaterület hozzáadása prémium szintű kapacitáshoz

Lehetséges, hogy a munkaterület mellett nincs gyémánt ikon. ![A Power BI Premium-kapacitás gyémánt ikonja](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) Ilyenkor hozzá kell adnia a munkaterületet egy prémium szintű kapacitáshoz. 

1. Válassza a **Munkaterületek** elemet, a munkaterület neve melletti három pontot ( **...** ), majd a **Munkaterület szerkesztése** lehetőséget.

    ![A Munkaterület szerkesztése elem kiválasztása](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace.png)

1. A **Munkaterület szerkesztése** párbeszédablakban bontsa ki a **Speciális** elemet, majd állítsa a **Dedikált kapacitás** kapcsolót a **Be** állásba.

    ![Dedikált kapacitás beállítása](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace-dialog.png)

   Előfordulhat, hogy ezt nem tudja módosítani. Ilyen esetben forduljon a Power BI Premium-kapacitás rendszergazdájához, és kérjen hozzárendelési jogosultságot, hogy munkaterületét felvehesse egy prémium szintű kapacitásba.

## <a name="from-report-builder-publish-a-paginated-report"></a>Lapszámozott jelentés közzététele a Jelentéskészítőből

1. Készítse el lapszámozott jelentését a Jelentéskészítőben, és mentse a helyi számítógépre.

1. A Jelentéskészítő **Fájl** menüben válassza a **Mentés másként** lehetőséget.

    ![Fájl menü > Mentés > Mentés másként](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-save-as.png)

    Ha még nem jelentkezett be Power BI-ba, jelentkezzen be vagy hozzon létre egy fiókot. A Jelentéskészítő jobb felső sarkában válassza a **Bejelentkezés** lehetőséget, majd hajtsa végre a lépéseket.

2. A bal oldali munkaterületek listájában válasszon ki egy, gyémánt ikonnal ![Power BI Premium-kapacitás gyémánt ikonja](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) ellátott munkaterületet. Írjon be egy **fájlnevet** a mezőbe, majd válassza a **Mentés** lehetőséget. 

    ![Premium-munkaterület kiválasztása](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-workspace.png)

4. Egy böngészőben nyissa meg a Power BI szolgáltatást, és keresse meg a prémium szintű munkaterületet, ahol a lapszámozott jelentést közzétette. A **Jelentések** lapon megjelenik a jelentés.

    ![Lapszámozott jelentés a Jelentések listában](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

5. Válassza ki a lapszámozott jelentést, hogy megnyissa a Power BI szolgáltatásban. Ha a jelentés paraméterekkel rendelkezik, akkor csak azok kiválasztása után tekinthető meg.

    ![Paraméterek kiválasztása](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

6. Ha a jelentés adatforrása helyszíni, a cikkből megtudhatja, hogyan [hozhat létre egy átjárót](#create-a-gateway) az adatforráshoz.

## <a name="from-the-power-bi-service-upload-a-paginated-report"></a>Lapszámozott jelentés feltöltése a Power BI szolgáltatásba

A Power BI szolgáltatásból kiindulva is feltölthet egy lapszámozott jelentést.

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

   A **Jelentések** lapon megjelenik a jelentés.

    ![Lapszámozott jelentés a Jelentések listában](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

1. Jelölje ki, és nyissa meg a Power BI szolgáltatásban. Ha a jelentés paraméterekkel rendelkezik, akkor csak azok kiválasztása után tekinthető meg.
 
    ![Paraméterek kiválasztása](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

6. Ha a jelentés adatforrása helyszíni, a cikkből megtudhatja, hogyan [hozhat létre egy átjárót](#create-a-gateway) az adatforráshoz.

## <a name="create-a-gateway"></a>Átjáró létrehozása

Mint minden Power BI-jelentésnél, itt is érvényes, hogy ha a jelentésnek helyszíni adatforrása van, akkor az adatok eléréséhez átjárót kell létrehoznia, vagy átjáróhoz kell csatlakoznia.

1. Válassza a jelentés neve melletti **Kezelés** lehetőséget.

   ![A lapszámozott jelentés kezelése](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-manage.png)

1. A részleteket és a következő lépéseket a [Mi az a helyszíni adatátjáró](../connect-data/service-gateway-onprem.md) című Power BI szolgáltatás-cikkben találja meg.



## <a name="next-steps"></a>Következő lépések

- [Lapszámozott jelentés megtekintése a Power BI szolgáltatásban](../consumer/paginated-reports-view-power-bi-service.md)
- [Mik a lapszámozott jelentések a Power BI Premiumban?](paginated-reports-report-builder-power-bi.md)
- [Oktatóanyag: Lapszámozott Power BI-jelentések beágyazása egy alkalmazásba az ügyfelek számára](../developer/embed-paginated-reports-customers.md)


