---
title: Power BI-jelentés létrehozása a Power BI jelentéskészítő kiszolgálóhoz
description: Ismerje meg, hogy miképpen hozhat létre Power BI-jelentést a Power BI jelentéskészítő kiszolgálóra néhány egyszerű lépésben.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 02/03/2020
ms.author: maggies
ms.openlocfilehash: 69ebfa9b1d2ef500b388a1bbb57926dc53ff2607
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "76975010"
---
# <a name="create-a-power-bi-report-for-power-bi-report-server"></a>Power BI-jelentés létrehozása a Power BI jelentéskészítő kiszolgálóhoz
A Power BI-jelentéseket helyszínen is tárolhatja és kezelheti a Power BI jelentéskészítő kiszolgáló webportálján, illetve tárolhatja őket a felhőbeli Power BI szolgáltatásban (https://powerbi.com) ). A jelentéseket a Power BI Desktopban hozhatja létre, majd közzéteheti a webportálon. Ekkor a jelentések megtekinthetővé válnak a cégen belüli olvasók számára egy böngésző vagy egy Power BI-mobilalkalmazás használatával.

![Power BI-jelentés a webportálon](media/quickstart-create-powerbi-report/report-server-powerbi-report.png)

Íme négy gyors lépés a kezdéshez.

## <a name="step-1-install-power-bi-desktop-optimized-for-power-bi-report-server"></a>1\. lépés: A Power BI jelentéskészítő kiszolgálóhoz optimalizált Power BI Desktop telepítése

Ha már létrehozott jelentéseket a Power BI Desktopban, akkor gyakorlatilag a Power BI jelentéskészítő kiszolgálóra is létrehozhat Power BI-jelentéseket. Javasoljuk, hogy a kiszolgáló és az alkalmazás folyamatos szinkronizálása érdekében telepítse a Power BI Desktop Power BI jelentéskészítő kiszolgálóra optimalizált verzióját. Ugyanazon a számítógépen a Power BI Desktop mindkét változata telepítve lehet.

1. A jelentéskészítő kiszolgáló webportálján kattintson a **Letöltés** nyíl > **Power BI Desktop** lehetőségre.

    ![A Power BI Desktop letöltése a webportálról](media/quickstart-create-powerbi-report/report-server-download-web-portal.png)

    Megnyithatja a [Power BI jelentéskészítő kiszolgáló](https://powerbi.microsoft.com/report-server/) kezdőlapját is, ahol kiválaszthatja a **Speciális letöltési beállítások** lehetőséget.

2. A letöltőközpontlapon kattintson a **Letöltés** gombra.

3. A számítógépétől függően válassza az alábbiak egyikét:

    - **PBIDesktopRS.msi** (32 bites verzió) vagy

    - **PBIDesktopRS_x64.msi** (64 bites verzió).

4. A telepítő letöltése után indítsa el a Power BI Desktop (2019. szeptember) telepítő varázslóját.

2. A telepítés végén kattintson a **Power BI Desktop azonnali indítása** lehetőségre.
   
    A folyamat automatikusan elindul, és máris hozzákezdhet. A címsorban látható **Power BI Desktop (2019. szeptember)** feliratból láthatja, hogy a megfelelő verziót töltötte le.

    ![Power BI Desktop 2019. szeptember](media/quickstart-create-powerbi-report/power-bi-report-server-desktop-sept-2019.png)

3. Ha még nem ismeri a Power BI Desktopot, érdemes megtekintenie az üdvözlőképernyőn látható videókat.
   
    ![A Power BI Destop üdvözlőképernyője](media/quickstart-create-powerbi-report/report-server-powerbi-desktop-start.png)

## <a name="step-2-select-a-data-source"></a>2\. lépés: Adatforrás kiválasztása
Számos adatforráshoz kapcsolódhat. További információkért lásd: [Kapcsolódás az adatforrásokhoz](connect-data-sources.md).

1. Az üdvözlőképernyőn kattintson az **Adatok beolvasása** elemre.
   
    Vagy a **Kezdőlap** lapon kattintson az **Adatok beolvasása** elemre.
2. Válassza ki az adatforrást – ebben a példában ez az**Analysis Services**.
   
    ![Adatforrás kiválasztása](media/quickstart-create-powerbi-report/power-bi-report-server-get-data-ssas.png)
3. Adja meg a **Kiszolgálót** és igény szerint az **Adatbázist**. Győződjön meg róla, hogy az **Élő csatlakozás** elem ki van jelölve > **OK**.
   
    ![A kiszolgáló neve](media/quickstart-create-powerbi-report/report-server-ssas-server-name.png)
4. Válassza ki azt a jelentéskészítő kiszolgálót, amelyen menteni fogja jelentéseket.
   
    ![Jelentéskészítő kiszolgáló kiválasztása](media/quickstart-create-powerbi-report/report-server-select-server.png)

## <a name="step-3-design-your-report"></a>3\. lépés: A jelentés megtervezése
Most jön a legérdekesebb rész: Az adatokat illusztráló vizualizációk létrehozása.

Például tölcsérdiagramot hozhat létre az éves jövedelem alapján csoportokba rendezett ügyfelekről.

![Jelentés megtervezése](media/quickstart-create-powerbi-report/report-server-create-funnel.png)

1. A **Megjelenítések** ablaktáblán kattintson a **Tölcsérdiagram** lehetőségre.
2. Húzza a megszámlálandó mezőt az **Értékek** oszlopba. Ha nem numerikus mezőről van szó, a Power BI Desktop automatikusan hozzáteszi a *Count of* (Száma) kiegészítést.
3. A csoportosítandó mezőt húzza a **Csoport** oszlopba.

További információk a [Power BI-jelentés megtervezéséről](../desktop-report-view.md).

## <a name="step-4-save-your-report-to-the-report-server"></a>4\. lépés: Mentse a jelentést a jelentéskészítő kiszolgálón
A kész jelentést mentse a 2. lépésben kiválasztott Power BI jelentéskészítő kiszolgálón.

1. A **Fájl** menüben kattintson a**Mentés másként** > **Power BI jelentéskészítő kiszolgáló** elemre.
   
    ![Mentés a jelentéskészítő kiszolgálón](media/quickstart-create-powerbi-report/report-server-save-as-powerbi-report-server.png)
2. Most már megtekintheti a jelentést a webportálon.
   
    ![A jelentés megtekintése a webportálon](media/quickstart-create-powerbi-report/report-server-powerbi-report.png)
    
> [!NOTE]
> Ha a későbbiekben módosítja a jelentést, az asztalon megjelenő jelentésadatok mindig a jelentés első létrehozásakor gyorsítótárazott adatok lesznek.  Ha a jelentés szerkesztésekor a legfrissebb adatokat szeretné megtekinteni, frissítenie kell az adatokat a Power BI Desktop alkalmazásban.

## <a name="next-steps"></a>Következő lépések
### <a name="power-bi-desktop"></a>Power BI Desktop
A Power BI Desktop számos nagyszerű erőforrással segíti a jelentéskészítést. Egy jó kiindulási pont ez a hivatkozás.

* [Első lépések a Power BI Desktopban](../desktop-getting-started.md)
* Interaktív tanulás: [Ismerkedés a Power BI Desktoppal](/learn/modules/get-data-power-bi/2-getting-started-power-bi-desktop)

### <a name="power-bi-report-server"></a>Power BI jelentéskészítő kiszolgáló
* [A Power BI jelentéskészítő kiszolgálóhoz optimalizált Power BI Desktop telepítése](install-powerbi-desktop.md)  
* [Mi a Power BI jelentéskészítő kiszolgáló?](get-started.md)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
