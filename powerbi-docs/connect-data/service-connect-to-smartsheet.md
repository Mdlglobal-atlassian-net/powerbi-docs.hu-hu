---
title: Kapcsolódás a Smartsheethez a Power BI-jal
description: Smartsheet Power BI-hoz
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 05/04/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 4498557d1bd38ce457b2e79d637e713af11c945a
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83325046"
---
# <a name="connect-to-smartsheet-with-power-bi"></a>Kapcsolódás a Smartsheethez a Power BI-jal
Ez a cikk részletesen bemutatja, hogyan kérhet le adatokat a Smartsheet-fiókjából egy Power BI-sablonalkalmazással. A Smartsheet könnyen használható platformot kínál az együttműködéshez és fájlmegosztáshoz. A Power BI-hoz készült Smartsheet-sablonalkalmazás a Smartsheet-fiók áttekintését biztosító irányítópultot, jelentéseket és adathalmazt nyújt. A fiók egyes lapjaihoz közvetlenül is kapcsolódhat a [Power BI Desktop](desktop-connect-to-data.md) használatával. 

A sablonalkalmazás telepítése után módosíthatja az irányítópultot és a jelentést. Ezután alkalmazásként terjesztheti a szervezeti munkatársai között.

Kapcsolódjon a Power BI-hoz készült [Smartsheet-sablonalkalmazáshoz](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.pbiapps-smartsheet).

>[!NOTE]
>A Power BI-sablonalkalmazás betöltéséhez és csatlakoztatásához rendszergazdai fiók szükséges a Smartsheet szolgáltatásban, mivel annak további hozzáférési engedélyei vannak.

## <a name="how-to-connect"></a>Csatlakozás

[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

3. Válassza a **Smartsheet** \> **Letöltés most** lehetőséget.
4. A **Telepíti ezt a Power BI-alkalmazást?** területen válassza a **Telepítés** lehetőséget.
4. Az **Alkalmazások** panelen válassza a **Smartsheet** lehetőséget.

    ![Power BI Smartsheet alkalmazáscsempe](media/service-connect-to-smartsheet/power-bi-smartsheet-tile.png)

6. **Az új alkalmazás használatának első lépései** résznél válassza az **Csatlakozás** lehetőséget.

    ![Első lépések az új alkalmazással](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

4. A Hitelesítési módszernél válassza az **oAuth2 \> Bejelentkezés** lehetőséget.
   
   Amikor a rendszer kéri, adja meg saját Smartsheet-beli hitelesítő adatait, majd haladjon végig a hitelesítési folyamaton.
   
   ![A Smartsheet hitelesítő adatai](media/service-connect-to-smartsheet/creds.png)
   
   ![Smartsheet-bejelentkezés](media/service-connect-to-smartsheet/creds2.png)

5. Miután a Power BI importálja az adatokat, megnyílik a Smartsheet irányítópultja.
   
   ![Smartsheet-irányítópult](media/service-connect-to-smartsheet/power-bi-smartsheet-dashboard.png)

## <a name="modify-and-distribute-your-app"></a>Az alkalmazás módosítása és terjesztése

Telepítette a Smartsheet-sablonalkalmazást. Ez azt jelenti, hogy létrehozott egy Smartsheet-munkaterületet is. A munkaterületen módosíthatja a jelentést és az irányítópultot, majd *alkalmazásként* terjesztheti azt a szervezet munkatársainak. 

1. Az új Smartsheet-munkaterület tartalmának megtekintéséhez a navigációs ablaktáblán válassza a **Munkaterületek** > **Smartsheet** lehetőséget. 

    ![Smartsheet-munkaterület a navigációs ablaktáblán](media/service-connect-to-smartsheet/power-bi-smartsheet-workspace.png)

    Ez a nézet a munkaterület tartalomlistája. A jobb felső sarokban látható az **App frissítése** elem. Ha készen áll terjeszteni az alkalmazást a munkatársainak, nekiláthat. 

    ![Smartsheet-tartalomlista](media/service-connect-to-smartsheet/power-bi-smartsheet-workspace-content.png)

2. Válassza a **Jelentések** és az **Adatkészletek** lehetőséget a munkaterület egyéb elemeinek megtekintéséhez.

    További információ az [alkalmazások terjesztéséről](../collaborate-share/service-create-distribute-apps.md).

## <a name="whats-included"></a>Tartalom
A Power BI-hoz készült Smartsheet-sablonalkalmazás tartalmazza a Smartsheet-fiók áttekintését, például a munkaterületek, jelentések és lapok számát, ezek módosításának időpontját stb. A rendszergazdák számára a rendszer felhasználóira vonatkozó információk is megjelennek, például a legtöbb lapot létrehozó felhasználók.  

Egyéni lapokhoz való közvetlen kapcsolódáshoz a fiókban használhatja a Smartsheet-összekötőt a [Power BI Desktop](desktop-connect-to-data.md) alkalmazásban.  

## <a name="next-steps"></a>Következő lépések

* [Új munkaterületek létrehozása a Power BI-ban](../collaborate-share/service-create-the-new-workspaces.md)
* [Alkalmazások telepítése és használata a Power BI-ban](../consumer/end-user-apps.md)
* [Csatlakozás külső szolgáltatásokhoz készült Power BI-alkalmazásokhoz](service-connect-to-services.md)
* Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)