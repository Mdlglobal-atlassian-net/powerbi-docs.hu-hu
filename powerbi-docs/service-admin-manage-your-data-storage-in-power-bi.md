---
title: Adattárolás felügyelete a munkaterületein
description: Útmutató az adattárolás felügyeletéhez egyéni munkaterületen a jelentések és adathalmazok folyamatos közzététele érdekében.
author: maggiesMSFT
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/25/2020
ms.author: maggies
LocalizationGroup: Administration
ms.openlocfilehash: f5bf1b55c2e092dc755da9f391c83ce3c42661b2
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "77652519"
---
# <a name="manage-data-storage-in-power-bi-workspaces"></a>Adattárolás felügyelete Power BI-munkaterületeken

Útmutató az adattárolás felügyeletéhez egyéni munkaterületen a jelentések és adathalmazok folyamatos közzététele érdekében.

## <a name="capacity-limits"></a>Kapacitási korlátok

A munkaterület tárolási korlátai a Saját munkaterületen és az alkalmazás-munkaterületen is attól függnek, hogy a munkaterület [megosztott vagy prémium szintű kapacitásban](service-basic-concepts.md#capacities) van.

### <a name="shared-capacity-limits"></a>Megoszt kapacitás korlátai
Megosztott kapacitásban lévő munkaterület esetén: 

- Munkaterületenként 100 GB a tárterületkorlát.
- Alkalmazás-munkaterületek esetén a teljes felhasznált tárterület nem lépheti túl a bérlő 10 GB tárterületkorlátjának és a bérlőn üzemelő Pro-licencek számának szorzatát.

### <a name="premium-capacity-limits"></a>Prémium szintű kapacitás korlátai
Prémium szintű kapacitásban lévő munkaterület esetén:
- A korlát prémium szintű kapacitásonként 100 TB.
- Felhasználónkénti tárolási korlát nincs.

További információkért tekintse meg [a Power BI díjszabási modelljét](https://powerbi.microsoft.com/pricing).

## <a name="whats-included-in-storage"></a>A tárhely tartalma

A tárhely magában foglalja a saját adathalmazokat és Excel-jelentéseket, valamint a mások által Önnel megosztott elemeket. Adathalmaz minden olyan adatforrás, amelyet feltöltött, vagy amelyhez csatlakozott. Ezek közé az adatforrások közé tartoznak az Ön által használt Power BI Desktop-fájlok és Excel-munkafüzetek is. A következők szintén beletartoznak az adatkapacitásba.

* Irányítópultra rögzített Excel-tartományok.
* Power BI-irányítópultra rögzített helyszíni Reporting Services-vizualizációk.
* Feltöltött képek.

Az Ön által megosztott irányítópult mérete attól függ, hogy mi van rögzítve rajta. Ha például két különböző adathalmazhoz tartozó jelentésből származó elemeket rögzít, a méretbe mindkét adathalmaz beletartozik.

<a name="manage"/>

## <a name="manage-items-you-own"></a>Saját tulajdonban lévő elemek kezelése

Megtekintheti a Power BI-fiókban aktuálisan felhasznált tárhely méretét, és kezelheti a fiókot.

1. A saját tárhely kezeléséhez nyissa meg a **Saját munkaterületet** a navigációs ablaktáblán.
   
    ![Saját munkaterület](media/service-admin-manage-your-data-storage-in-power-bi/pbi_myworkspace.png)

2. Kattintson a fogaskerék ikonra ![Fogaskerék ikon](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) a jobb felső sarokban \> **Személyes tárhely kezelése**.
   
    A felső sávon látható, hogy mennyit használt fel a rendelkezésre álló tárhelyből.
   
    ![Tárhelykorlát kezelése](media/service-admin-manage-your-data-storage-in-power-bi/pbi_persnlstorage.png)
   
    Az adatkészletek és a jelentések két külön lapon találhatók az alábbiak szerint:
   
    **Saját tulajdon:** Ezeket a jelentéseket és adathalmazokat, köztük az olyan szolgáltatások adathalmazait, mint a Salesforce és a Dynamics CRM, Ön töltötte fel a saját Power BI-fiókjába.  

    **Mások tulajdona:** Ezeket a jelentéseket és adatkészleteket mások osztották meg Önnel.
1. Adatkészlet vagy jelentés törléséhez kattintson a Kuka ikonra ![kuka ikon](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).

Vegye figyelembe, hogy az adatkészleteken saját vagy megosztott jelentések és irányítópultok alapulhatnak. Ha törli az adatkészletet, ezek a jelentések és irányítópultok nem fognak működni.

## <a name="manage-your-workspace"></a>Saját munkaterület kezelése
1. Kattintson a **Munkaterületek** elem melletti nyílra, majd \> válassza ki a munkaterület nevét.
   
    ![Válasszon munkaterületet](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupworkspaces.png)
2. Kattintson a fogaskerék ikonra ![Fogaskerék ikon](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) a jobb felső sarokban \> **Csoporttárhely kezelése**.
   
    A felső sávon látható, hogy mennyit használtak fel a csoport rendelkezésére álló tárhelyből.
   
    ![Munkaterület tárhelyének kezelése](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupstorage.png)
   
    Az adatkészletek és a jelentések két külön lapon találhatók az alábbiak szerint:
   
    **Közös tulajdon:** Ezeket a jelentéseket és adathalmazokat, köztük az olyan szolgáltatások adathalmazait, mint a Salesforce és a Dynamics CRM, Ön vagy valaki más töltötte fel a csoport Power BI-fiókjába.

    **Mások tulajdona:** Ezeket a jelentéseket és adatkészleteket mások osztották meg az Ön csoportjával.

3. Adatkészlet vagy jelentés törléséhez kattintson a Kuka ikonra ![kuka ikon](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).
   
   > [!NOTE]
   > Vegye figyelembe, hogy az adatkészleteken saját vagy a csoport más tagja által birtokolt jelentések és irányítópultok alapulhatnak. Ha törli az adatkészletet, ezek a jelentések és irányítópultok nem fognak működni.
   
   Egy munkaterület bármely rendszergazda, tag vagy közreműködő szerepkörrel rendelkező tagja jogosult adathalmazokat és jelentéseket törölni a munkaterületről.

## <a name="dataset-limits"></a>Adatkészletkorlátok
A Power BI-ba importálható egyes adathalmazok korlátja 1 GB. Ha adatimportálás helyett az Excel további használata mellett döntött, az adathalmaz korlátja 250 MB.

## <a name="what-happens-when-you-reach-a-limit"></a>Mi történik, ha eléri a korlátot
Ha eléri a munkája során felhasználható adatkapacitás korlátját, a szolgáltatás figyelmeztető üzeneteket küld. 

A fogaskerék ikon kiválasztásakor ![fogaskerék ikon](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png), piros csík jelzi az adatkapacitás korlátjának túllépését.

![Tárhelykorlát elérése](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit.png)

Ez a korlát megjelenik a **Személyes tárhely kezelése** területen is.

 ![Személyes tárhely kezelése, tárhelykorlát-túllépés](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit2.png)

 Ha a korlátok bármelyikét elérő tevékenységet kísérel meg, üzenetet kap a korlát túllépéséről. Előfordulhat, hogy a tárhely [kezelésével](#manage) csökkenti a tárhely méretét, és így lépi át a korlátot.

 ![Túllépte a tárhelykorlátot](media/service-admin-manage-your-data-storage-in-power-bi/powerbi-pro-over-limit.png)

 ## <a name="next-steps"></a>Következő lépések

 További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

