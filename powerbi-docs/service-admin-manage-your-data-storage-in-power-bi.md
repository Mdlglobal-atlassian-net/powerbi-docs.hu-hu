---
title: Adattárolás felügyelete a munkaterületein
description: Útmutató a jelentések és az adathalmazok további közzétételének biztosításához az egyéni vagy az alkalmazás-munkaterületen található adattárhely kezelésével.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/21/2018
ms.author: maggies
LocalizationGroup: Administration
ms.openlocfilehash: e1f1a8fdc5094fd13fc2894d9728951d9f6bde96
ms.sourcegitcommit: 5206651c12f2b91a368f509470b46f3f4c5641e6
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53983554"
---
# <a name="manage-data-storage-in-power-bi-workspaces"></a>Adattárolás felügyelete Power BI-munkaterületeken

Útmutató a jelentések és az adathalmazok további közzétételének biztosításához az egyéni vagy az alkalmazás-munkaterületen található adattárhely kezelésével.

A felhasználók és az alkalmazás-munkaterületek saját adatkapacitással rendelkeznek:

* A felhasználók tárhelyének maximális mérete 10 GB.
* A Power BI Pro-licenccel rendelkező felhasználók több, egyenként 10 GB-os alkalmazás-munkaterületet is létrehozhatnak.
* A prémium szintű kapacitásban lévő alkalmazás-munkaterületek nem számítanak bele a Power BI Pro-felhasználók tárhelyébe.

Bérlői szinten az egy Pro-felhasználóra és alkalmazás-munkaterületre jutó teljes használat nem haladhatja meg a felhasználónkénti 10 GB-ot.

További információkért tekintse meg [a Power BI díjszabási modelljét](https://powerbi.microsoft.com/pricing).

A tárhely magában foglalja a saját adathalmazokat és Excel-jelentéseket, valamint a mások által Önnel megosztott elemeket. Adathalmaz minden olyan adatforrás, amelyet feltöltött, vagy amelyhez csatlakozott. Ezek közé az adatforrások közé tartoznak az Ön által használt Power BI Desktop-fájlok és Excel-munkafüzetek is. A következők szintén beletartoznak az adatkapacitásba.

* Irányítópultra rögzített Excel-tartományok.
* Power BI-irányítópultra rögzített helyszíni Reporting Services-vizualizációk.
* Feltöltött képek.

Az Ön által megosztott irányítópult mérete attól függ, hogy mi van rögzítve rajta. Ha például két különböző adathalmazhoz tartozó jelentésből származó elemeket rögzít, a méretbe mindkét adathalmaz beletartozik.

<a name="manage"/>

## <a name="manage-items-you-own"></a>Saját tulajdonban lévő elemek kezelése

Megtekintheti a Power BI-fiókban aktuálisan felhasznált tárhely méretét, és kezelheti a fiókot.

1. A saját tárhely kezeléséhez nyissa meg a **Saját munkaterületet** a bal oldali navigációs ablaktáblán.
   
    ![Saját munkaterület](media/service-admin-manage-your-data-storage-in-power-bi/pbi_myworkspace.png)
2. Kattintson a fogaskerék ikonra ![Fogaskerék ikon](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) a jobb felső sarokban \> **Személyes tárhely kezelése**.
   
    A felső sávon látható, hogy mennyit használt fel a rendelkezésre álló tárhelyből.
   
    ![Tárhelykorlát kezelése](media/service-admin-manage-your-data-storage-in-power-bi/pbi_persnlstorage.png)
   
    Az adatkészletek és a jelentések két külön lapon találhatók az alábbiak szerint:
   
    **Saját tulajdon:** Ezeket a jelentéseket és adathalmazokat, köztük az olyan szolgáltatások adathalmazait, mint a Salesforce és a Dynamics CRM, Ön töltötte fel a saját Power BI-fiókjába.  
    **Mások tulajdona:** Ezeket a jelentéseket és adatkészleteket mások osztották meg Önnel.
1. Adatkészlet vagy jelentés törléséhez kattintson a Kuka ikonra ![kuka ikon](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).

Vegye figyelembe, hogy az adatkészleteken saját vagy megosztott jelentések és irányítópultok alapulhatnak. Ha törli az adatkészletet, ezek a jelentések és irányítópultok nem fognak működni.

## <a name="manage-your-app-workspace"></a>Saját alkalmazás-munkaterület kezelése
1. Kattintson a **Munkaterületek** elem melletti nyílra, majd \> válassza ki az alkalmazás-munkaterület nevét.
   
    ![Alkalmazás-munkaterület kijelölése](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupworkspaces.png)
2. Kattintson a fogaskerék ikonra ![Fogaskerék ikon](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) a jobb felső sarokban \> **Csoporttárhely kezelése**.
   
    A felső sávon látható, hogy mennyit használtak fel a csoport rendelkezésére álló tárhelyből.
   
    ![Alkalmazás-munkaterület tárhelyének kezelése](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupstorage.png)
   
    Az adatkészletek és a jelentések két külön lapon találhatók az alábbiak szerint:
   
    **Közös tulajdon:** Ezeket a jelentéseket és adathalmazokat, köztük az olyan szolgáltatások adathalmazait, mint a Salesforce és a Dynamics CRM, Ön vagy valaki más töltötte fel a csoport Power BI-fiókjába.
    **Mások tulajdona:** Ezeket a jelentéseket és adatkészleteket mások osztották meg az Ön csoportjával.
3. Adatkészlet vagy jelentés törléséhez kattintson a Kuka ikonra ![kuka ikon](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).
   
   > [!NOTE]
   > Egy alkalmazás-munkaterület bármely, szerkesztési engedéllyel rendelkező tagja jogosult az adatkészletek és jelentések törlésére az alkalmazás-munkaterületről.
   > 
   > 

Vegye figyelembe, hogy az adatkészleteken saját vagy a csoport más tagja által birtokolt jelentések és irányítópultok alapulhatnak. Ha törli az adatkészletet, ezek a jelentések és irányítópultok nem fognak működni.

## <a name="dataset-limits"></a>Adatkészletkorlátok
A Power BI-ba importálható egyes adatkészletek korlátja 1 GB. Ha adatimportálás helyett az Excel további használata mellett döntött, az adathalmaz korlátja 250 MB.

## <a name="what-happens-when-you-reach-a-limit"></a>Mi történik, ha eléri a korlátot
Ha eléri a munkája során felhasználható adatkapacitás korlátját, a szolgáltatás figyelmeztető üzeneteket küld. 

A fogaskerék ikon kiválasztásakor ![fogaskerék ikon](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png), piros csík jelzi az adatkapacitás korlátjának túllépését.

![Tárhelykorlát elérése](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit.png)

Ez a korlát megjelenik a **Személyes tárhely kezelése** területen is.

 ![Személyes tárhely kezelése, tárhelykorlát-túllépés](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit2.png)

 Ha a korlátok bármelyikét elérő tevékenységet kísérel meg, üzenetet kap a korlát túllépéséről. Előfordulhat, hogy a tárhely [kezelésével](#manage) csökkenti a tárhely méretét, és így lépi át a korlátot.

 ![Túllépte a tárhelykorlátot](media/service-admin-manage-your-data-storage-in-power-bi/powerbi-pro-over-limit.png)

 További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

