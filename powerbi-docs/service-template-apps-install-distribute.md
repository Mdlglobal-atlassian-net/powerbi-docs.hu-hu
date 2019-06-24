---
title: Sablonalkalmazások terjesztése a szervezetnél – Power BI (előzetes verzió)
description: Elsajátíthatja, hogyan telepíthet, szabhat testre és terjeszthet sablonalkalmazásokat a szervezetnél a Power BI-ban.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/19/2019
ms.author: maggies
ms.openlocfilehash: 0671dfb324b3d66a9dee9585f94d3cb6825fb5eb
ms.sourcegitcommit: 81ba3572531cbe95ea0b887b94e91f94050f3129
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/06/2019
ms.locfileid: "66751228"
---
# <a name="install-and-distribute-template-apps-in-your-organization---power-bi-preview"></a>Sablonalkalmazások telepítése és terjesztése a szervezetnél – Power BI (előzetes verzió)

Ön Power BI-elemző? Ha igen, ebből a cikkből megtudhatja, hogyan telepíthet *sablonalkalmazásokat*, amelyekkel könnyedén kapcsolódhat a vállalkozása működtetéséhez használt olyan szolgáltatásokhoz, mint például a Salesforce, a Microsoft Dynamics és a Google Analytics. Módosíthatja az irányítópultot és a jelentéseket, hogy megfeleljen a szervezet követelményeinek, majd terjesztheti azokat *alkalmazásként* a munkatársainak. 

![Telepített Power BI-alkalmazások](media/service-template-apps-install-distribute/power-bi-get-apps.png)

Ha érdekli, hogyan hozhat létre sablonalkalmazásokat, hogy saját maga terjeszthesse azokat, akkor olvassa el a [Sablonalkalmazás létrehozása a Power BI-ban](service-template-apps-create.md) cikket. A Power BI-partnerek kevés kódolással vagy anélkül hozhatnak létre Power BI-alkalmazásokat, és helyezhetik üzembe azokat bármely Power BI-ügyfél részére. 

## <a name="prerequisites"></a>Előfeltételek  

Az alábbiakban a sablonalkalmazások telepítésének, testreszabásának és terjesztésének követelményeit olvashatja: 

- Egy [Power BI Pro-licenc](service-self-service-signup-for-power-bi.md)
- A [Power BI alapvető fogalmainak](service-basic-concepts.md) ismerete
- Érvényes telepítési hivatkozás a sablonalkalmazás létrehozójától vagy az AppSource-ból. 
- Engedélyek sablonalkalmazások telepítéséhez. 

## <a name="install-a-template-app"></a>Sablonalkalmazás telepítése

Kaphat egy sablonalkalmazásra mutató hivatkozást. Ellenkező esetben kereshet az AppSource-ban egy Önt érdeklő sablonalkalmazást. A telepítése után mindkét esetben módosíthatja azt, és terjesztheti a saját cégén belül.

### <a name="search-appsource-from-a-browser"></a>Keresés az AppSource-ban egy böngészőből

A böngészőben kattintson erre a hivatkozásra az AppSource Power BI-alkalmazásokat megjelenítő szűrővel történő megnyitásához:

- https://appsource.microsoft.com/marketplace/apps?product=power-bi

### <a name="search-appsource-from-the-power-bi-service"></a>Keresés az AppSource-ban a Power BI szolgáltatásból

1. A Power BI szolgáltatás bal oldali navigációs paneljén válassza az **Alkalmazások** > **Alkalmazások letöltése** lehetőséget.

    ![Alkalmazások letöltése](media/service-template-apps-install-distribute/power-bi-get-apps-arrow.png)

2. Válassza az AppSource-ban az **Alkalmazások** lehetőséget.

    ![Keresés az AppSource-ban](media/service-template-apps-install-distribute/power-bi-appsource.png)

3. Tallózzon az alkalmazáshoz, vagy keresse meg azt, majd válassza a **Letöltés most** lehetőséget.

2. A párbeszédpanelen válassza a **Telepítés** lehetőséget.

    Ha Power BI Pro-licenccel rendelkezik, az alkalmazás telepítése a társított alkalmazás-munkaterülettel együtt történik. Az alkalmazást a társított munkaterületen szabhatja testre.

    Ha a telepítés sikeres, megjelenik egy értesítés, hogy az új alkalmazás készen áll a használatra. 

3. Válassza az **Ugrás az alkalmazásra** lehetőséget.
4. **Az új alkalmazás használatának első lépései** szakaszban három lehetőség közül választhat:

    ![Az alkalmazás használatának első lépései](media/service-template-apps-create/power-bi-template-app-get-started.png)

    - **Az alkalmazás felfedezése**: Alapszintű példa adatfeltárás. Kezdjen itt az alkalmazás működésének megtapasztalásához. 
    - **Adatok csatlakoztatása**: Módosítsa az adatforrást a mintaadatokról a saját adatforrására. Újra meghatározhatja az adatkészlet paramétereit és az adatforráshoz tartozó hitelesítő adatokat. Tekintse át az [Ismert korlátozások](service-template-apps-tips.md#known-limitations) szakaszt a sablonalkalmazásokra vonatkozó tippeket tartalmazó cikkben. 
    - **Ugrás a munkaterületre** (a legspeciálisabb beállítás): az alkalmazás készítője által engedélyezett bármilyen módosítást végrehajthat.

    Vagy ezt a párbeszédpanelt kihagyva közvetlenül is hozzáférhet a társított munkaterülethez a bal oldali navigációs panel **Munkaterületek** szakaszában.   
 
5. A munkatársakkal való megosztás előtt érdemes kapcsolódni a saját adataihoz. Módosíthatja a jelentés vagy az irányítópultot is, hogy megfelelően működjön a cégében. Ekkor más jelentéseket vagy irányítópultokat is felvehet.

## <a name="update-and-distribute-the-app"></a>Az alkalmazás frissítése és terjesztése

Miután frissítette az alkalmazást a cége számára, készen áll a közzétételére. A lépések ugyanazok, mint bármely más alkalmazás közzétételekor. 

1. Amikor végzett a testreszabással, a munkaterület listanézetében válassza a jobb felső sarokban az **Alkalmazás frissítése** lehetőséget.  

    ![Az alkalmazás telepítésnek megkezdése](media/service-template-apps-install-distribute/power-bi-start-install-app.png)

2. A **Részletek** nézetben módosíthatja a leírást és a háttér színét.

   ![Alkalmazás leírásának és színének beállítása](media/service-template-apps-install-distribute/power-bi-install-app-details.png)

3. A **Tartalom** területen kiválaszthatja a kezdőlapot, amely lehet az irányítópult vagy a jelentést.

   ![Alkalmazás kezdőlapjának beállítása](media/service-template-apps-install-distribute/power-bi-install-app-content.png)

4. A **Hozzáférés** területen hozzáférést adhat a kijelölt felhasználók vagy a teljes cég számára.  

   ![Hozzáférés beállítása](media/service-template-apps-install-distribute/power-bi-install-access.png)

5. Válassza az **App frissítése** lehetőséget. 

6. Miután sikeresen közzétette, lemásolhatja a hivatkozást, és megoszthatja bárkivel, aki számára hozzáférést biztosított. Ha megosztotta velük, akkor a hivatkozást az AppSource **Saját szervezet** lapján is láthatják.

## <a name="next-steps"></a>Következő lépések 

[Munkaterületek létrehozása a munkatársakkal a Power BI-ban](service-create-workspaces.md)





￼ 

 
