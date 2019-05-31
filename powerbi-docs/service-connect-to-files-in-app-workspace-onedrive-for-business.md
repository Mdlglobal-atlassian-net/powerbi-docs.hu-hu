---
title: Csatlakozás a Power BI alkalmazás munkaterületéhez tartozó OneDrive-ban tárolt fájlokhoz
description: Itt olvashat arról, hogy miképpen tárolhatja a Power BI alkalmazás munkaterületéhez tartozó OneDrive-ban az Excel-, a CSV-, és a Power BI Desktop-fájlokat, és hogyan csatlakozhat hozzájuk.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukasz
ms.service: powerbi
ms.topic: conceptual
ms.date: 04/15/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 52b7748b6b634caf87de01ddc965576339a04b8b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61174990"
---
# <a name="connect-to-files-stored-in-onedrive-for-your-power-bi-app-workspace"></a>Csatlakozás a Power BI alkalmazás munkaterületéhez tartozó OneDrive-ban tárolt fájlokhoz
Miután [létrehozott egy alkalmazás-munkaterületet a Power BI-ban](service-create-distribute-apps.md), a Power BI alkalmazás-munkaterülethez tartozó OneDrive Vállalati verzióban tárolhatja az Excel-, CSV-, és Power BI Desktop-fájlokat. Továbbra is a OneDrive-ban tárolt fájlok frissítése. Ezeket a frissítéseket automatikusan megjelennek a Power BI-jelentések és irányítópultok a fájlokon alapuló. 

> [!NOTE]
> Az új munkaterületi felhasználói felület változik a Power BI-munkaterületeket és az Office 365-csoportok közötti kapcsolatot. Nem automatikusan hoz létre az Office 365-csoport minden alkalommal, amikor egy új munkaterületet hoz létre. További információ [új munkaterület létrehozása](service-create-the-new-workspaces.md)

A fájlokat két lépésben adhatja hozzá az alkalmazás-munkaterülethez: 

1. Az első lépésben [töltse fel a fájlokat a OneDrive Vállalati verzióba](service-connect-to-files-in-app-workspace-onedrive-for-business.md#1-upload-files-to-the-onedrive-for-business-for-your-app-workspace) az alkalmazás-munkaterület számára.
2. A második lépésben [csatlakozzon a fájlokhoz a Power BI-ból](service-connect-to-files-in-app-workspace-onedrive-for-business.md#2-import-excel-files-as-datasets-or-as-excel-online-workbooks).

> [!NOTE]
> Az alkalmazás-munkaterületek csak a [Power BI Proban](service-features-license-type.md) érhetők el.
> 

## <a name="1-upload-files-to-the-onedrive-for-business-for-your-app-workspace"></a>1 Fájlok feltöltése az alkalmazás-munkaterülethez tartozó OneDrive Vállalati verzióba
1. A Power BI szolgáltatásban kattintson a Munkaterületek melletti nyílra > kattintson a három pontra ( **…** ) a munkaterület neve mellett. 
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-ellipsis.png)
2. Kattintson a **Fájlok** elemre az alkalmazás-munkaterülethez tartozó OneDrive Vállalati verzió megnyitásához az Office 365-ben.
   
   > [!NOTE]
   > Ha az alkalmazás-munkaterület menüben nem látja a **Fájlok** lehetőséget, az alkalmazás-munkaterülethez tartozó OneDrive Vállalati verzió megnyitásához kattintson a **Tagok** lehetőségre. Itt kattintson a **Fájlok** elemre. Az Office 365 beállít egy OneDrive-tárhelyet az alkalmazás csoportos munkaterületének fájljai számára. Ez a folyamat hosszabb időbe telhet. 
   > 
   > 
3. Itt feltöltheti a fájlokat az alkalmazás-munkaterülethez tartozó OneDrive Vállalati verzióba. Kattintson a **Feltöltés** elemre, és keresse meg a fájlokat.
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_grpfilesonedrive.png)

## <a name="2-import-excel-files-as-datasets-or-as-excel-online-workbooks"></a>2 Excel-fájlok importálása adatkészletek vagy Excel Online-munkafüzetek formájában
Miután a fájlok bekerültek a alkalmazás-munkaterülethez tartozó OneDrive Vállalati verzióba, kétféle választása van. A következőket teheti: 

* [Az adatok importálása az Excel-munkafüzet, adatkészlet](service-get-data-from-files.md). Az adatok használatával hozhat létre jelentéseket és irányítópultokat egy webböngészőben vagy mobileszközökön is megtekintheti.
* Vagy [csatlakozhat egy teljes Excel-munkafüzethez a Power BI-ban](service-excel-workbook-files.md), és pontosan olyan formában jelenítheti meg, ahogy az Excel Online-ban látható.

### <a name="import-or-connect-to-the-files-in-your-app-workspace"></a>Fájlok importálása vagy csatlakozás hozzájuk az alkalmazás-munkaterületen
1. A Power BI-ban váltson az alkalmazás-munkaterületre; ekkor az alkalmazás-munkaterület neve a bal felső sarokban jelenik meg. 
2. Kattintson az **Adatok lekérése** elemre a bal oldalon lévő navigációs ablaktábla alján. 
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-get-data-button.png)
3. A **Fájlok** mezőben kattintson a **Beolvasás** elemre.
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_getfiles.png)
4. Válassza a **OneDrive** - *Alkalmazás-munkaterület neve* lehetőséget.
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_grp_one_drive_shrpt.png)
5. Válassza ki a kívánt fájlt > **Csatlakozás**.
   
    Ezen a ponton eldöntheti, hogy e [az adatok importálása Excel-munkafüzetekből](service-get-data-from-files.md), vagy [teljes Excel-munkafüzetekhez csatlakozik](service-excel-workbook-files.md).
6. Válassza az **Importálás** vagy a **Csatlakozás** lehetőséget.
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_importexceldataorwholecrop.png)
7. Ha az **Importálás** lehetőséget választja, akkor a munkafüzet az **Adatkészletek** lapon jelenik meg. 
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-excel-file-import.png)
   
    Ha a **Csatlakozás** lehetőséget választja, akkor a munkafüzet a **Munkafüzetek** lapon jelenik meg.
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-excel-file-connect.png)

## <a name="next-steps"></a>További lépések
* [Alkalmazások és alkalmazás-munkaterületek létrehozása a Power BI-ban](service-create-distribute-apps.md)
* [Adatok importálása Excel-munkafüzetekből](service-get-data-from-files.md)
* [Csatlakozás teljes Excel-munkafüzetekhez](service-excel-workbook-files.md)
* További kérdései vannak? [Kérdezze a Power BI-közösséget!](http://community.powerbi.com/)
* Visszajelzést szeretne küldeni? Keresse fel a [Power BI Ideas](https://ideas.powerbi.com/forums/265200-power-bi) fórumot.

