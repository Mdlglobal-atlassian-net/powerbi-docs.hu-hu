---
title: 'Céges tartalomcsomagok: Hozzáférés és másolás'
description: Információ a Power BI vállalatitartalomcsomag-másolatok létrehozásáról és az azokhoz való hozzáférési problémák hibaelhárításáról
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/02/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: f22cac734d98e98cd17a915c09d6705e2cad121a
ms.sourcegitcommit: 378265939126fd7c96cb9334dac587fc80291e97
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/07/2019
ms.locfileid: "57580059"
---
# <a name="organizational-content-packs-copy-refresh-and-get-access"></a>Céges tartalomcsomagok: Másolás, frissítés és hozzáférés

Amikor közzétesz egy vállalati tartalomcsomagot, minden címzett ugyanazt az irányítópultot, jelentéseket, Excel-munkafüzeteket, adatkészleteket és adatokat látja (kivéve, ha SQL Server Analysis Services (SSAS) adatforrásról van szó).  A tartalomcsomagot csak a [tartalomcsomag létrehozója szerkesztheti és teheti újra közzé](service-organizational-content-pack-manage-update-delete.md).  Minden címzett menthet egy, az eredetivel párhuzamosan létező másolatot a tartalomcsomagról.

A tartalomcsomagok létrehozása nem azonos az irányítópultok megosztásával vagy az azokon való közös munkával. Olvassa el [Az irányítópultokon és jelentéseken végzett közös munka, illetve azok megosztása](service-how-to-collaborate-distribute-dashboards-reports.md) szakaszt, hogy eldönthesse, melyik lehetőség felel meg legjobban a helyzetének.

> [!NOTE]
> Nem lehet létrehozni vagy telepíteni céges tartalomcsomagokat az új munkaterületi felhasználói felület előzetes verziójában. Ha még nem kezdte el, ideje frissítenie az alkalmazásokhoz tartozó tartalomcsomagokat. További információ az [új munkaterületi felhasználói felületről](service-create-the-new-workspaces.md).
>

## <a name="create-a-copy-of-an-organizational-content-pack"></a>Másolat készítése egy vállalati tartalomcsomagról
Hozza létre a saját, mások által nem látható másolatát a tartalomcsomagról.

1. Válassza a tartalomcsomag irányítópultja mellett a három pontot (...) > a Másolat készítése lehetőséget.

    ![](media/service-organizational-content-pack-copy-refresh-access/power-bi-create-copy-organizational-content-pack.png)
2. Kattintson a **Mentés** gombra.  

Ezzel lett egy másolata, amelyet módosíthat. A módosításokat más nem fogja látni.

> [!NOTE]
> Korábban minden alkalommal, amikor telepített egy tartalomcsomagot vagy létrehozott egy másolatot, megjelent egy új adatkészlet a munkaterület tartalomlistájában. Egy közelmúltbeli frissítés leegyszerűsítette a folyamatot, így csak egy, a hivatkozott adatkészlet ikonját használó elem jelenik meg:
>
> ![adatbázis a hivatkozás ikonnal](media/service-organizational-content-pack-copy-refresh-access/power-bi-dataset-reference-icon.png)
>

## <a name="help--i-can-no-longer-access-the-content-pack"></a>Segítség!  Már nem férek hozzá a tartalomcsomaghoz
Ennek több oka is lehet:

* **A tagságot érintő változások**:  A tartalomcsomagok közzététele e-mailes terjesztési listák, biztonsági csoportok és az [Office 365-ön alapuló Power BI-csoportok](https://support.office.com/article/Create-a-group-in-Office-365-7124dc4c-1de9-40d4-b096-e8add19209e9) számára történik.  Ha eltávolították a csoportból, nem lesz többé hozzáférése a tartalomcsomaghoz.
* **A terjesztést érintő változások**: A tartalomcsomag létrehozója módosítja a terjesztést. Ha például eredetileg az egész vállalat számára közzétették a tartalomcsomagot, de a létrehozó újból közzétette egy szűkebb közönség számára, lehet, hogy már nem tartozik a címzettek közé.
* **A biztonsági beállításokat érintő változások**: Ha az irányítópult és a jelentések helyszíni SSAS-adatforrásokhoz csatlakoznak, és módosítják a biztonsági beállításokat, előfordulhat, hogy visszavonták a kiszolgálóra vonatkozó engedélyeit.

## <a name="how-are-organizational-content-packs-refreshed"></a>Hogyan frissülnek a vállalati tartalomcsomagok?
Amikor egy tartalomcsomag létrejön, a frissítési beállításokat örökli az adatkészlettől.  Amikor másolatot készít egy tartalomcsomagról, az új verzió megtartja az eredeti adatkészletre mutató hivatkozást és a frissítési ütemezését.

Lásd: [Vállalati tartalomcsomagok kezelése, frissítése és törlése](service-organizational-content-pack-manage-update-delete.md).

## <a name="next-steps"></a>Következő lépések
* [A vállalati tartalomcsomagok bemutatása](service-organizational-content-pack-introduction.md)
* [Csoportok létrehozása a Power BI-ban](service-create-distribute-apps.md)
* További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
