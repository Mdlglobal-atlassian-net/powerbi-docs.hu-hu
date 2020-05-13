---
title: Power BI-jelentés szűrése és megosztása
description: Tudnivalók arról, hogyan szűrheti a Power BI-jelentéseket, és hogyan oszthatja meg azokat munkatársaival a szervezetnél.
author: maggiesMSFT
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/29/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 636aaf59a3a949b5b3571012d12cecc234e9763b
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83347953"
---
# <a name="filter-and-share-a-power-bi-report"></a>Power BI-jelentés szűrése és megosztása
A *Megosztással* egyszerűen biztosíthatja néhány személy hozzáférését az irányítópultjaihoz és jelentéseihez. Mi történik olyankor, ha egy jelentésnek egy szűrt verzióját szeretné megosztani? Lehet, hogy azt szeretné, hogy a jelentésben csak egy adott város vagy üzletkötő vagy év adatai jelenjenek meg. Ez a cikk azt ismerteti, hogyan szűrheti a jelentéseket, és hogyan oszthatja meg a jelentés szűrt verzióját. A szűrt jelentések megosztásának egy másik módja, ha [lekérdezési paramétereket ad hozzá a jelentés URL-címéhez](service-url-filters.md). A jelentés mindkét esetben már szűrve lesz, amikor a címzettek először megnyitják. A felhasználók törölhetik a jelentésben szereplő szűrők kijelölését.

![Jelentés szűrve](media/service-share-reports/power-bi-share-filter-pane-report.png)

A Power BI-ban [több más módon is megvalósítható a jelentések közös használata és terjesztése](service-how-to-collaborate-distribute-dashboards-reports.md). A megosztáshoz Önnek és az összes címzetteknek is [Power BI Pro-licencre](../fundamentals/service-features-license-type.md) van szüksége, vagy pedig a tartalomnak kell egy [Prémium-kapacitásban](../admin/service-premium-what-is.md) lennie. 

## <a name="follow-along-with-sample-data"></a>A folyamat követése a mintaadatok használatával

Ez a cikk a Marketing és értékesítés mintaalkalmazás-sablont használja. Szeretné kipróbálni? 

1. Telepítse az [Értékesítési és marketing minta alkalmazássablont](https://appsource.microsoft.com/product/power-bi/microsoft-retail-analysis-sample.salesandmarketingsample?tab=Overview).
2. Válassza ki az alkalmazást, és válassza az **Alkalmazás megismerése** lehetőséget.

   ![A mintaadatok megismerése](media/service-share-reports/power-bi-sample-explore-data.png)

3. Az alkalmazással telepített munkaterület megnyitásához válassza a ceruza ikont.

    ![Alkalmazás szerkesztése ceruza ikon](media/service-share-reports/power-bi-edit-pencil-app.png)

4. A munkaterület tartalmi listájában válassza a **Jelentések** lehetőséget, majd válassza ki az **Értékesítési és marketing minta PBIX** jelentést.

    ![A mintajelentés megnyitása](media/service-share-reports/power-bi-open-sample-report.png)

    Most már dolgozhat vele.

## <a name="set-a-filter-in-the-report"></a>Szűrő beállítása a jelentésben

Nyisson meg egy jelentést [Szerkesztés nézetben](../consumer/end-user-reading-view.md), és alkalmazzon egy szűrőt.

Ebben a példában az Értékesítési és marketing minta alkalmazássablon Folyó évi kategória oldalát fogjuk szűrni, hogy csak azokat az értékeket mutassa, ahol a **Régió** értéke **Central** (Középső). 
 
![Jelentés Szűrés ablaktáblája](media/service-share-reports/power-bi-share-report-filter.png)

Mentse a jelentést.

## <a name="share-the-filtered-report"></a>A szűrt jelentés megosztása

1. Válassza a **Megosztás** lehetőséget.

   ![Megosztás választása](media/service-share-reports/power-bi-share.png)

2. Törölje az **E-mail-értesítés küldése a címzetteknek** bejelölését, hogy ehelyett egy szűrt hivatkozást küldhessen, válassza a **Jelentés megosztása az aktuális szűrőkkel és szeletelőkkel**, majd a **Megosztás** lehetőséget.

    ![Jelentés megosztása szűrőkkel](media/service-share-reports/power-bi-share-with-filters.png)

4. Válassza újra a **Megosztás** lehetőséget.

   ![Megosztás választása](media/service-share-reports/power-bi-share.png)

5. Válassza a **Hozzáférés** lapot, majd válassza a **Megosztott jelentések nézeteinek kezelése** lehetőséget.

    ![Megosztott jelentésnézetek kezelése](media/service-share-reports/power-bi-manage-shared-report-views.png)

6. Kattintson a jobb gombbal a kívánt URL-címre, majd válassza a **Hivatkozás másolása** lehetőséget.

    ![Szűrt hivatkozás másolása](media/service-share-reports/power-bi-copy-filtered-link.png)

7. Ha ezt a hivatkozást megosztja, a címzettek a szűrt jelentést fogják látni. 


## <a name="next-steps"></a>További lépések
* [A munka megosztásának módjai a Power BI-ban](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Irányítópult megosztása](service-share-dashboards.md)
* Több kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/).
* Visszajelzés küldene? Mondja el javaslatait a [Power BI-közösség webhelyén](https://community.powerbi.com/).
