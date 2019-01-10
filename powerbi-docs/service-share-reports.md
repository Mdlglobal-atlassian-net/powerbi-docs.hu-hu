---
title: Szűrt Power BI-jelentés megosztása a munkatársakkal
description: Tudnivalók arról, hogyan szűrheti a Power BI-jelentéseket, és hogyan oszthatja meg azokat munkatársaival a szervezetnél.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/21/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d5e05775d310af37b2c96c6e9e255de25fe5effe
ms.sourcegitcommit: 5206651c12f2b91a368f509470b46f3f4c5641e6
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53983439"
---
# <a name="share-a-filtered-power-bi-report-with-your-coworkers"></a>Szűrt Power BI-jelentés megosztása munkatársakkal
A *Megosztással* egyszerűen biztosíthatja néhány személy hozzáférését az irányítópultjaihoz és jelentéseihez. A Power BI-ban [többféle módon valósítható meg a jelentések közös használata és terjesztése](service-how-to-collaborate-distribute-dashboards-reports.md).

A megosztáshoz Önnek és az összes címzetteknek is [Power BI Pro-licencre](service-features-license-type.md) van szüksége, vagy pedig a tartalomnak kell egy [Prémium-kapacitásban](service-premium.md) lennie. 

Jelentéseket megoszthat munkatársaival, amennyiben ugyanazt az e-mail-tartományt használják, mint Ön. A megosztás a Power BI szolgáltatás legtöbb helyén elvégezhető, többek között a Kedvencek, a Legutóbbi, A Velem megosztva (ha a tulajdonos engedélyezte a megosztást) vagy a Saját munkaterület helyekről. A megosztott jelentést azok a munkatársak, akikkel megosztja azt megtekinthetik és használhatják, de nem szerkeszthetik. Az adatokat ugyanúgy látják, ahogyan Ön is látja a jelentésben, hacsak nem alkalmaz [sorszintű biztonságot (RLS-t)](service-admin-rls.md). 

Mi történik olyankor, ha egy jelentésnek egy szűrt verzióját szeretné megosztani? Például egy olyan jelentést, amely csak egy adott város, év vagy értékesítő adatait jeleníti meg. Próbáljon meg létrehozni egy egyéni URL-címet. A jelentés szűrt lesz, amikor a címzettek először megnyitják. Eltávolíthatják a szűrőt az URL-cím módosításával.

## <a name="filter-and-share-a-report"></a>Jelentés szűrése és megosztása

1. Nyissa meg a jelentést [Szerkesztő nézetben](consumer/end-user-reading-view.md), alkalmazza a szűrőt, majd mentse a jelentést.
   
   Ebben a példában a [Kiskereskedelmi elemzési mintát](sample-tutorial-connect-to-the-samples.md) szűrjük, hogy csak azokat az értékeket mutassa, ahol a **Territory** (Terület) **NC** (Észak-Karolnia) értékű.
   
   ![Jelentés Szűrés ablaktáblája](media/service-share-reports/power-bi-filter-report2.png)
2. Adja hozzá a jelentésoldal URL-címéhez a következőt:
   
   ?filter=*táblanév*/*mezőnév* eq *érték*
   
    A mezőnek **karakterlánc** típusúnak kell lennie. A *táblanév* vagy *mezőnév* értékei nem tartalmazhatnak szóközt.
   
   A példánkban **Store** (Üzlet) a tábla neve, **Territory** (Terület) a mező neve, és **NC** (Észak-Karolnia) az érték, amelyre szűrni szeretnénk:
   
    ?filter=Store/Territory eq 'NC'
   
   ![Szűrt jelentés URL-címe](media/service-share-reports/power-bi-filter-url3.png)
   
   A böngésző ehhez még hozzáad néhány speciális karaktert a perjelek, szóközök és aposztrófok helyettesítésére, így az eredmény a következő lesz:
   
   app.powerbi.com/groups/me/reports/010ae9ad-a9ab-4904-a7a1-xxxxxxxxxxxx/ReportSection2?filter=Store%252FTerritory%20eq%20%27NC%27

3. [Ossza meg a jelentést](service-share-dashboards.md), de törölje az **Értesítés küldése a címzetteknek e-mailben** jelölőnégyzetet. 

    ![Jelentés megosztásának párbeszédablaka](media/service-share-reports/power-bi-share-report-dialog.png)

4. Küldje el a hivatkozást a korábban létrehozott szűrővel.

## <a name="next-steps"></a>Következő lépések
* Visszajelzés küldene? Mondja el javaslatait a [Power BI-közösség webhelyén](https://community.powerbi.com/).
* [Irányítópultok és jelentések közös használata és megosztása](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Irányítópult megosztása](service-share-dashboards.md)
* További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/).

