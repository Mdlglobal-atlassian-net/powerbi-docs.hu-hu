---
title: Kapcsolódás a Smartsheethez a Power BI-jal
description: Smartsheet Power BI-hoz
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/26/2019
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: 841201aa87139b9630d6fc076d57109fb2b09804
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "64578902"
---
# <a name="connect-to-smartsheet-with-power-bi"></a>Kapcsolódás a Smartsheethez a Power BI-jal
Ez a cikk végigvezeti a Power bi-ban sablon alkalmazás használatával a Smartsheet-fiók adatainak lekérése. A Smartsheet könnyen használható platformot kínál az együttműködéshez és fájlmegosztáshoz. A Power bi-hoz készült Smartsheet sablon alkalmazás tartalmaz egy irányítópultot, jelentéseket és adatkészletet a Smartsheet-fiók áttekintését megjelenítő. Is [Power BI Desktop](desktop-connect-to-data.md) , a fiók egyes lapjaihoz közvetlenül csatlakozhat. 

Ha már telepítette a sablonalapú alkalmazásként, módosíthatja az irányítópultot és jelentést. Majd terjesztheti azt munkatársainak alkalmazásként a szervezet.

Csatlakozás a [Smartsheet sablonalapú alkalmazásként](https://app.powerbi.com/groups/me/getdata/services/smartsheet) a Power bi-hoz.

>[!NOTE]
>A Smartsheet-rendszergazdai fiók részesíti előnyben a csatlakozás és betöltése a Power bi-ban sablon alkalmazást, mert további hozzáférési.

## <a name="how-to-connect"></a>Csatlakozás

[!INCLUDE [powerbi-service-apps-get-more-apps](./includes/powerbi-service-apps-get-more-apps.md)]

3. Válassza ki **Smartsheet** \> **Letöltés most**.
4. A **a Power BI-alkalmazás telepítése?** kiválasztása **telepítése**.
4. Az a **alkalmazások** panelen válassza a **Smartsheet** csempére.

    ![A Power BI Smartsheet alkalmazás csempe](media/service-connect-to-smartsheet/power-bi-smartsheet-tile.png)

6. A **az új alkalmazás használatának első lépései**válassza **adatok**.

    ![Első lépések az új alkalmazással](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect-data.png)

4. A Hitelesítési módszernél válassza az **oAuth2 \> Bejelentkezés** lehetőséget.
   
   Amikor a rendszer kéri, adja meg saját Smartsheet-beli hitelesítő adatait, majd haladjon végig a hitelesítési folyamaton.
   
   ![A Smartsheet-hitelesítő adatok](media/service-connect-to-smartsheet/creds.png)
   
   ![A Smartsheet-bejelentkezés](media/service-connect-to-smartsheet/creds2.png)

5. Miután a Power BI importálta az adatokat, a Smartsheet-irányítópult megnyitása.
   
   ![A Smartsheet-irányítópult](media/service-connect-to-smartsheet/power-bi-smartsheet-dashboard.png)

## <a name="modify-and-distribute-your-app"></a>Módosíthatja, és az alkalmazás terjesztése

A Smartsheet-sablon alkalmazást telepítette. Ez azt jelenti, hogy a Smartsheet alkalmazás-munkaterület is létrehozott. A munkaterületen a jelentések és irányítópultok módosítsa, majd ezután osztja el, mint egy *alkalmazás* munkatársaknak a szervezetben. 

1. Az új Smartsheet-munkaterületen a tartalmát megtekintéséhez a bal oldali navigációs sávon válassza **munkaterületek** > **Smartsheet**. 

    ![A Smartsheet-munkaterület a bal oldali navigációs panelen](media/service-connect-to-smartsheet/power-bi-smartsheet-workspace.png)

    Ez a nézet a munkaterület számára a tartalmak listája. A jobb felső sarokban látható **app frissítése**. Ha már készen áll az alkalmazást a munkatársai, ez az először lesz. 

    ![A Smartsheet-tartalmak listája](media/service-connect-to-smartsheet/power-bi-smartsheet-workspace-content.png)

2. Válassza ki **jelentések** és **adatkészletek** a munkaterület az egyéb elemek megtekintéséhez.

    További információ [alkalmazások terjesztése](service-create-distribute-apps.md) munkatársainak.

## <a name="whats-included"></a>Tartalom
Sablonalapú alkalmazásként Power bi-ban, a számát, például a Smartsheet-fiók áttekintését tartalmazza a jelentések és a lapok Smartsheet rendelkezik, hogy módosításakor stb. Rendszergazda felhasználók a felhasználók körül információk is megjelennek a rendszer, például a legtöbb lapot létrehozó.  

Egyéni lapokhoz való közvetlen kapcsolódáshoz a fiókban használhatja a Smartsheet-összekötőt a [Power BI Desktop](desktop-connect-to-data.md) alkalmazásban.  

## <a name="next-steps"></a>Következő lépések

* [Az új munkaterületek létrehozása a Power bi-ban](service-create-the-new-workspaces.md)
* [Alkalmazások telepítése és használata a Power BI-ban](consumer/end-user-apps.md)
* [Csatlakozás a Power BI alkalmazások külső szolgáltatásokhoz](service-connect-to-services.md)
* Kérdése van? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)