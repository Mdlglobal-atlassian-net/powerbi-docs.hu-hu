---
title: OneDrive-on található Excel-fájlra hivatkozó irányítópult megosztása ‒ Power BI
description: Útmutatás a OneDrive-on található Excel-munkafüzetekhez csatlakozó, a munkafüzetből kitűzött csempéket tartalmazó irányítópultok megosztásához.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/02/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 9a99344438108d2f092220dfa1c66895355aeda0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61402991"
---
# <a name="share-a-power-bi-dashboard-that-links-to-an-excel-file-in-onedrive"></a>OneDrive-on található Excel-fájlra hivatkozó Power BI-irányítópult megosztása
A Power BI-ból csatlakozhat a [OneDrive Vállalati verzióján tárolt Excel-munkafüzetekhez](service-excel-workbook-files.md), és a munkafüzetekből csempéket tűzhet ki az irányítópultokra. Ha megoszt egy ilyen irányítópultot, vagy létrehoz egy tartalomcsomagot, amely tartalmazza az irányítópultot:

* Kollégái akkor is megnézhetik a csempéket, ha nincs engedélyük a munkafüzethez. A tartalomcsomagokat annak tudatában hozhatja létre, hogy kollégái megtekinthetik a OneDrive-on található Excel-munkafüzetekből létrehozott csempéket.
* A csempékre kattintva a munkafüzet megnyitható a Power BI szolgáltatásban. A munkafüzet azonban csak akkor nyílik meg, ha munkatársainak legalább [olvasási jogosultsága](https://support.office.com/article/Share-documents-or-folders-in-Office-365-1fe37332-0f9a-4719-970e-d2578da4941c) van a OneDrive Vállalati verzióján tárolt munkafüzethez.

## <a name="share-a-dashboard-that-contains-workbook-tiles"></a>Munkafüzetcsempéket tartalmazó irányítópult megosztása
A OneDrive Vállalati verzióban tárolt Excel-munkafüzetre hivatkozó irányítópultok megosztásával kapcsolatban tekintse át az [Irányítópultok megosztását](service-share-dashboards.md) bemutató cikket. A különbség csak annyi, hogy lehetősége van a hivatkozott Excel-munkafüzethez tartozó jogosultságok módosítására.

  ![Irányítópult megosztása párbeszédpanel](media/service-share-dashboard-that-links-to-excel-onedrive/pbi_share_workbk.png)

1. Adja meg kollégái e-mail-címét.
2. Az Excel-munkafüzet a Power BI szolgáltatásban történő megtekintésének az engedélyezéséhez kattintson a **Munkafüzet engedélyeinek beállítása** lehetőségre.
3. A OneDrive-on [módosítsa az engedélyeket](https://support.office.com/article/Share-files-and-folders-and-change-permissions-9fcc2f7d-de0c-4cec-93b0-a82024800c07) igény szerint.
4. Kattintson a **Megosztás** lehetőségre.

>[!NOTE]
>Kollégái nem fognak tudni további csempéket kitűzni a munkafüzetből, illetve nem fogják tudni módosítani az Excel-munkafüzetet a Power BI-ból.
> 
> 

## <a name="create-an-organizational-content-pack-with-a-dashboard-that-contains-workbook-tiles"></a>Munkafüzet-csempéket megjelenítő irányítópultot tartalmazó szervezeti tartalomcsomag létrehozása
Amikor [közzétesz egy tartalomcsomagot](service-organizational-content-pack-create-and-publish.md) munkatársainak egyéni, illetve csoportos hozzáférést biztosíthat ahhoz. Amikor közzétesz egy munkafüzet-hivatkozásokat tartalmazó tartalomcsomagot, lehetősége lesz módosítani az Excel-munkafüzetre vonatkozó engedélyeket.

1. A **Tartalomcsomag létrehozása** képernyőn, adja meg az e-mail címeket, a csomag címét és leírását, és töltsön fel egy képet.
2. Válassza ki a OneDrive Vállalati verzión tárolt Excel-munkafüzetre hivatkozó irányítópultot és/vagy jelentést.
   
    ![Excel-munkafüzet egy tartalomcsomagban](media/service-share-dashboard-that-links-to-excel-onedrive/pbi_contpack_workbk.png)
3. Kattintson a **Munkafüzet engedélyeinek beállítása** lehetőségre.
4. A OneDrive-on [módosítsa az engedélyeket](https://support.office.com/article/Share-files-and-folders-and-change-permissions-9fcc2f7d-de0c-4cec-93b0-a82024800c07) igény szerint.
5. Kattintson a **Közzététel** lehetőségre.

## <a name="share-a-dashboard-from-a-power-bi-workspace"></a>Irányítópult megosztása Power BI-munkaterületről
Power BI-munkaterületről ugyanúgy oszthat meg irányítópultot, mint egy saját munkaterületről, azzal a különbséggel, hogy míg az egyik esetben a fájlok egy Office 365 munkaterület-webhelyen találhatók, a másik esetben a saját OneDrive Vállalati verzió webhelyén. Ha munkaterületen kívüli személyekkel is meg szeretné osztani az irányítópultot, akkor módosítsa az Excel-munkafüzethez tartozó engedélyeket még a megosztás előtt.

![Megosztás OneDrive-ról](media/service-share-dashboard-that-links-to-excel-onedrive/pbi_onedriveshare.png)

## <a name="next-steps"></a>Következő lépések
* [Csempe rögzítése Power BI-irányítópultra Excelből](service-dashboard-pin-tile-from-excel.md)
* [A Power BI alapvető fogalmai](consumer/end-user-basic-concepts.md)
* További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

