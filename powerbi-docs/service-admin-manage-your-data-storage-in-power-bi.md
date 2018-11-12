---
title: Saját tárhely kezelése
description: Ismerje meg, hogy miképpen biztosíthatja a jelentések és az adatkészletek további közzétételét az egyéni vagy az alkalmazás-munkaterületen található saját tárhely kezelésével.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 06/28/2017
ms.author: maggies
LocalizationGroup: Administration
ms.openlocfilehash: 864d50d8850a8ceed964f128cea71b0daf5d8322
ms.sourcegitcommit: ac63e6a082ca8397909217837e8d98c9389b23ac
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/01/2018
ms.locfileid: "50736872"
---
# <a name="manage-your-data-storage"></a>Saját tárhely kezelése
Ismerje meg, hogy miképpen biztosíthatja a jelentések és az adatkészletek további közzétételét az egyéni vagy az alkalmazás-munkaterületen található saját tárhely kezelésével.

A felhasználók és az alkalmazás-munkaterületek saját adatkapacitással rendelkeznek

* A felhasználók tárhelyének maximális mérete 10 GB.
* A Power BI Pro-licenccel rendelkező felhasználók több, egyenként 10 GB-os alkalmazás-munkaterületet is létrehozhatnak.

Bérlői szinten az egy Pro-felhasználóra és alkalmazás-munkaterületre jutó teljes használat nem haladhatja meg a felhasználónkénti 10 GB-ot.

További információkért tekintse meg [a Power BI díjszabási modelljét](https://powerbi.microsoft.com/pricing).

A tárhely magában foglalja a saját és a mások által Önnel megosztott adatkészleteket és Excel-jelentéseket. Adatkészlet lehet bármely adatforrás, amelyet feltöltött, vagy amelyhez kapcsolódik, beleértve a használatban lévő Power BI Desktop-fájlokat és Excel-munkafüzeteket is. A következők szintén beletartoznak az adatkapacitásba.

* Irányítópultra rögzített Excel-tartományok.
* Power BI-irányítópultra rögzített helyszíni Reporting Services-vizualizációk.
* Feltöltött képek.

Az Ön által megosztott irányítópult mérete attól függ, hogy mi van rögzítve rajta. Például ha két különböző adatkészlethez tartozó jelentésből származó elemeket rögzít, a méretbe mindkét adatkészlet bele fog tartozni.

<a name="manage"/>

## <a name="manage-items-owned-by-you"></a>Saját elemek kezelése
Megtekintheti a Power BI-fiókban aktuálisan felhasznált tárhely méretét, és kezelheti a fiókot.

1. A saját tárhely kezeléséhez nyissa meg a **Saját munkaterületet** a bal oldali navigációs ablaktáblán.
   
    ![](media/service-admin-manage-your-data-storage-in-power-bi/pbi_myworkspace.png)
2. Kattintson a fogaskerék ikonra ![](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) a jobb felső sarokban \> **Személyes tárhely kezelése**.
   
    A felső sávon látható, hogy mennyit használt fel a rendelkezésre álló tárhelyből.
   
    ![](media/service-admin-manage-your-data-storage-in-power-bi/pbi_persnlstorage.png)
   
    Az adatkészletek és a jelentések két külön lapon találhatók az alábbiak szerint:
   
    **Saját tulajdon:** Ezeket a jelentéseket és adatkészleteket, köztük az olyan szolgáltatások adatkészleteit, mint a Salesforce és a Dynamics CRM, a saját Power BI-fiókjába töltötte fel.  
    **Mások tulajdona:** Ezeket a jelentéseket és adatkészleteket mások osztották meg Önnel.
3. Adatkészlet vagy jelentés törléséhez kattintson a Kuka ikonra ![](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).

Vegye figyelembe, hogy az adatkészleteken saját vagy megosztott jelentések és irányítópultok alapulhatnak. Ha törli az adatkészletet, ezek a jelentések és irányítópultok nem fognak működni.

## <a name="manage-your-app-workspace"></a>Saját alkalmazás-munkaterület kezelése
1. Kattintson a **Munkaterületek** elem melletti nyílra, majd \> válassza ki az alkalmazás-munkaterület nevét.
   
    ![](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupworkspaces.png)
2. Kattintson a fogaskerék ikonra ![](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) a jobb felső sarokban \> **Csoporttárhely kezelése**.
   
    A felső sávon látható, hogy mennyit használtak fel a csoport rendelkezésére álló tárhelyből.
   
    ![](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupstorage.png)
   
    Az adatkészletek és a jelentések két külön lapon találhatók az alábbiak szerint:
   
    **Közös tulajdon:** Ezeket a jelentéseket és adatkészleteket, köztük az olyan szolgáltatások adatkészleteit, mint a Salesforce és a Dynamics CRM, Ön vagy valaki más töltötte fel a csoport Power BI-fiókjába.
    **Mások tulajdona:** Ezeket a jelentéseket és adatkészleteket mások osztották meg a csoporttal.
3. Adatkészlet vagy jelentés törléséhez kattintson a Kuka ikonra ![](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).
   
   > [!NOTE]
   > Egy alkalmazás-munkaterület bármely, szerkesztési engedéllyel rendelkező tagja jogosult az adatkészletek és jelentések törlésére az alkalmazás-munkaterületről.
   > 
   > 

Vegye figyelembe, hogy az adatkészleteken saját vagy a csoport más tagja által birtokolt jelentések és irányítópultok alapulhatnak. Ha törli az adatkészletet, ezek a jelentések és irányítópultok nem fognak működni.

## <a name="dataset-limits"></a>Adatkészletkorlátok
A Power BI-ba importálható egyes adatkészletek korlátja 1 GB. Ha adatimportálás helyett az Excel további használata mellett döntött, az adatkészlet korlátja 250 MB lesz.

## <a name="what-happens-when-you-hit-a-limit"></a>Mi történik, ha eléri a korlátot
Ha eléri a munkája során felhasználható adatkapacitás korlátját, a szolgáltatás figyelmeztető üzeneteket küld. 

Ha a fogaskerék ikonra ![](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) kattint, piros csík jelzi az adatkapacitás korlátjának túllépését.

![](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit.png)

Ez megjelenik a **Személyes tárhely kezelése** területen is.

 ![](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit2.png)

 Ha a korlátok bármelyikét elérő tevékenységet kísérel meg, a rendszer figyelmezteti a korlát túllépésére. Ekkor a tárhely [kezelésével](#manage) csökkentheti a tárhely méretét, és átlépheti a korlátot.

 ![](media/service-admin-manage-your-data-storage-in-power-bi/powerbi-pro-over-limit.png)

 Több kérdése van? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

