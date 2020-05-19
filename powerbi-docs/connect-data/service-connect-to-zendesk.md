---
title: Csatlakozás a Zendeskhez a Power BI segítségével
description: Power BI Zendesk
author: paulinbar
ms.reviewer: sarinas
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 05/04/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 17d65296246100180f722dfccacb31ee9ebeade7
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83327162"
---
# <a name="connect-to-zendesk-with-power-bi"></a>Csatlakozás a Zendeskhez a Power BI segítségével

Ez a cikk részletesen bemutatja, hogyan kérhet le adatokat a Zendesk-fiókjáról egy Power BI-sablonalkalmazással. A Zendesk-alkalmazás egy Power BI-irányítópultot és néhány Power BI-jelentést kínál, amelyek hibajegyek és ügynöki teljesítmények elemzésében segítenek. Az adatokat naponta egyszer automatikusan frissíti a rendszer. 

A sablonalkalmazás telepítése után az irányítópultot és a jelentést személyre is szabhatja, hogy az Ön számára legfontosabb információk legyenek kiemelve. Ezután alkalmazásként terjesztheti a szervezeti munkatársai között.

Csatlakozzon a [Zendesk-sablonalkalmazáshoz](https://app.powerbi.com/getdata/services/zendesk), vagy olvasson még többet a [Zendesk](https://powerbi.microsoft.com/integrations/zendesk) és a Power BI integrációjáról.

A sablonalkalmazás telepítése után módosíthatja az irányítópultot és a jelentést. Ezután alkalmazásként terjesztheti a szervezeti munkatársai között.

>[!NOTE]
>A csatlakozáshoz Zendesk-rendszergazdai fiók szükséges. A [követelményekkel](#system-requirements) kapcsolatos további információkat lásd alább.

## <a name="how-to-connect"></a>Csatlakozás

[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

3. Válassza a **Zendesk** \> **Letöltés most** lehetőséget.
4. A **Telepíti ezt a Power BI-alkalmazást?** területen válassza a **Telepítés** lehetőséget.
4. Az **Alkalmazások** panelen válassza a **Zendesk** csempét.

    ![Power BI Zendesk-alkalmazáscsempe](media/service-connect-to-zendesk/power-bi-zendesk-tile.png)

6. **Az új alkalmazás használatának első lépései** résznél válassza az **Csatlakozás** lehetőséget.

    ![Első lépések az új alkalmazással](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

4. Adja meg a fiókjához társított URL-címet. Az URL-cím formátuma a következő: **https://company.zendesk.com** . A [paraméterek fellelhetőségével](#finding-parameters) kapcsolatos információt lásd alább.
   
   ![Csatlakozás a Zendeskhez](media/service-connect-to-zendesk/pbi_zendeskconnect.png)

5. Amikor a rendszer kéri, adja meg Zendesk-fiókja hitelesítő adatait.  Válassza ki az **oAuth 2** hitelesítési mechanizmust, és kattintson a **Bejelentkezés** elemre. Kövesse a Zendesk hitelesítési folyamatát. (Ha már bejelentkezett a Zendeskbe a böngészőjében, akkor a rendszer nem feltétlenül kéri a hitelesítő adatait.)
   
   > [!NOTE]
   > Ez a sablonalkalmazás megköveteli, hogy egy Zendesk-rendszergazdai fiókkal csatlakozzon. 
   > 
   
   ![Bejelentkezés oAuth2-vel](media/service-connect-to-zendesk/pbi_zendesksignin.png)
6. Zendesk-adatai eléréséhez kattintson az **Engedélyezés** gombra.
   
   ![Kattintson az Engedélyezés lehetőségre.](media/service-connect-to-zendesk/zendesk2.jpg)
7. Az importálás megkezdéséhez kattintson a **Csatlakozás** lehetőségre. 
8. Miután a Power BI importálta az adatokat, megjelenik a Zendesk alkalmazás tartalomlistája: egy új irányítópult, jelentés és adathalmaz.
9. A feltárási folyamat elindításához válassza ki az irányítópultot.

    ![A Zendesk irányítópultja](media/service-connect-to-zendesk/power-bi-zendesk-dashboard.png)
   
## <a name="modify-and-distribute-your-app"></a>Az alkalmazás módosítása és terjesztése

Telepítette a Zendesk-sablonalkalmazást. Ez azt jelenti, hogy létrehozta a Zendesk-munkaterületet is. A munkaterületen módosíthatja a jelentést és az irányítópultot, majd *alkalmazásként* terjesztheti azt a szervezet munkatársainak. 

1. Az új Zendesk-munkaterület teljes tartalmának megtekintéséhez a navigációs ablaktáblán válassza a **Munkaterületek** > **Zendesk** lehetőséget. 

    ![Zendesk-munkaterület a navigációs ablaktáblán](media/service-connect-to-zendesk/power-bi-zendesk-workspace-left-nav.png)

    Ez a nézet a munkaterület tartalomlistája. A jobb felső sarokban látható az **App frissítése** elem. Ha készen áll terjeszteni az alkalmazást a munkatársainak, nekiláthat. 

    ![Zendesk-tartalomlista](media/service-connect-to-zendesk/power-bi-zendesk-content-list.png)

2. Válassza a **Jelentések** és az **Adatkészletek** lehetőséget a munkaterület egyéb elemeinek megtekintéséhez.

    További információ az [alkalmazások terjesztéséről](../collaborate-share/service-create-distribute-apps.md).

## <a name="system-requirements"></a>Rendszerkövetelmények
A Zendesk-sablonalkalmazás eléréséhez Zendesk-rendszergazdai fiók szükséges. Ha Ön ügynök vagy végfelhasználó, és szeretné megtekinteni Zendesk-adatait, írja meg javaslatát, és értékelje a [Power BI Desktop](desktop-connect-to-data.md) Zendesk-összekötőjét.

## <a name="finding-parameters"></a>Paraméterek helye
A Zendesk-URL-cím megegyezik azzal, amelyet a Zendesk-fiókjába való belépéshez használ. Ha nem biztos a Zendesk-URL-címében, használhatja a Zendesk [bejelentkezési súgóját](https://www.zendesk.com/login/).

## <a name="troubleshooting"></a>Hibaelhárítás
Ha csatlakozási problémába ütközik, ellenőrizze Zendesk-URL-címét, és győződjön meg arról, hogy Zendesk-rendszergazdai fiókot használ.

## <a name="next-steps"></a>Következő lépések

* [Új munkaterületek létrehozása a Power BI-ban](../collaborate-share/service-create-the-new-workspaces.md)
* [Alkalmazások telepítése és használata a Power BI-ban](../consumer/end-user-apps.md)
* [Csatlakozás külső szolgáltatásokhoz készült Power BI-alkalmazásokhoz](service-connect-to-services.md)
* Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
