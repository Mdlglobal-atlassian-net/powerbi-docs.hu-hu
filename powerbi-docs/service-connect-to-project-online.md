---
title: Csatlakozás a Project Online-hoz a Power BI használatával
description: Project Online a Power BI-hoz
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: a6ada87813593fd0f06d7870fa1727bc35fe7d47
ms.sourcegitcommit: fe8a25a79f7c6fe794d1a30224741e5281e82357
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/18/2019
ms.locfileid: "68324953"
---
# <a name="connect-to-project-web-app-with-power-bi"></a>Csatlakozás a Project Web Apphoz a Power BI használatával
A Microsoft Project Web App a projektportfólió-kezeléshez (PPM) és a mindennapi munkához nyújt rugalmas online megoldást. A Project Web App lehetővé teszi a cég számára, hogy megtegye az előkészületeket, rangsorolja a projektporfólió-befektetéseket, és elérje a tervezett üzleti eredményt. A Power BI Project Web App sablonalkalmazásával fontos információkat ismerhet meg a Project Web App elemzéseiből, így könnyebben kezelheti a projekteket, a portfóliókat és az erőforrásokat.

Csatlakozzon a Power BI [Project Web App sablonalkalmazásához](https://appsource.microsoft.com/product/power-bi/pbi_msprojectonline.pbi-microsoftprojectwebapp).

## <a name="how-to-connect"></a>Csatlakozás

   ![](media/service-connect-to-project-online/GetApps.png)
1. A bal oldali navigációs panelen válassza az **Alkalmazások** elemet, majd a jobb felső sarokban az **Alkalmazások letöltése** lehetőséget.
2. A **Szolgáltatások** mezőben kattintson a **Lekérés** elemre.
   
   ![](media/service-connect-to-project-online/AppSource.png)
3. Az AppSource-on válassza az **Alkalmazások** lapfület, és keresse meg/válassza ki a **Microsoft Project Web App** lehetőséget.
   
4. Amikor megjelenik a **Telepíti ezt a Power BI-alkalmazást?** kérdés, válassza a **Telepítés** lehetőséget. 

   ![](media/service-connect-to-project-online/ProjectTile.png)
5. Az **Alkalmazások** ablaktáblán válassza ki a **Microsoft Project Web App** mozaikot. 
   
   ![](media/service-connect-to-project-online/getstarted.png)
6. **Az új alkalmazás használatának első lépései** résznél válassza az **Adatok csatlakoztatása** lehetőséget.
   
   ![](media/service-connect-to-project-online/mproject.png)
7. A **Project Web App URL** (Projekt Web App URL-címe) szövegdobozba írja be a csatlakoztatni kívánt Project Web App URL-címét.  Vegye figyelembe, hogy ez az adat egyedi tartomány esetén eltérhet a példától. A **PWA Site Language** szövegmezőbe írja be a PWA-webhely nyelvének megfelelő számot. Angol nyelvhez az 1-es, franciához a 2-es, némethez a 3-as, brazil portugálhoz a 4-es, portugálhoz az 5-ös, spanyolhoz pedig a 6-os számot írja be. 
   
   ![](media/service-connect-to-project-online/params.png)
8. Az Authentication Method (Hitelesítési módszer) beállításnál válassza az **oAuth2** \> beállítást, majd a **Sign In** (Bejelentkezés) elemet. Amikor a rendszer kéri, adja meg a saját Projekt Web App hitelesítő adatait, majd haladjon végig a hitelesítési folyamaton.

    
Vegye figyelembe, hogy portfóliómegtekintő, portfóliókezelő vagy rendszergazdai engedélyekre van szüksége ahhoz a Project Web Apphez, amelyhez csatlakozik.

9. Egy értesítés jelzi, hogy az adatok betöltése folyamatban van. A fiók méretétől függően ez eltarthat egy ideig. Miután a Power BI importálta az adatokat, megjelenik az új munkaterület tartalma. Előfordulhat, hogy a legújabb elemek megjelenítéséhez frissítenie kell az adathalmazt. 

Miután a Power BI importálta az adatokat, a bal oldali navigációs ablaktáblán megjelenik a 13 oldalas jelentés, valamint az adathalmaz. 

10. Miután a jelentések elkészültek, megkezdheti a Project Web App-adatokkal való munkát. A sablonalkalmazás 13 részletgazdag jelentést tartalmaz portfólióáttekintéshez (6 jelentésoldal), erőforrás-áttekintéshez (5 jelentésoldal), valamint projektállapothoz (2 jelentésoldal). 

   ![](media/service-connect-to-project-online/report1.png)
   
   ![](media/service-connect-to-project-online/report3.png)
   
   ![](media/service-connect-to-project-online/report2.png)

**Mi a következő lépés?**

* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

**A sablonalkalmazás bővítése**

Töltse le a [GitHub PBIT-fájlt](https://github.com/OfficeDev/Project-Power-BI-Content-Packs) a tartalom további testreszabásához és frissítéséhez

## <a name="next-steps"></a>Következő lépések
[Első lépések a Power BI-ban](service-get-started.md)

[Adatok lekérése a Power BI-ban](service-get-data.md)

