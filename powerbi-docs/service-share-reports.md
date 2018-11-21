---
title: Power BI-jelentések szűrése és megosztása munkatársakkal
description: Tudnivalók arról, hogyan oszthat meg munkatársaival szűrt Power BI-jelentéseket a cégen belül.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 01/18/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 38a735a6cc258f3285787202b832ade9c6525994
ms.sourcegitcommit: a739a99e1006834a0f56e387c0bd9d945fb8a76b
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51678972"
---
# <a name="share-a-filtered-power-bi-report-with-your-coworkers"></a>Szűrt Power BI-jelentés megosztása munkatársakkal
A *Megosztással* egyszerűen biztosíthatja néhány személy hozzáférését az irányítópultjaihoz és jelentéseihez. A Power BI-ban [többféle módon valósítható meg a jelentések közös használata és terjesztése](service-how-to-collaborate-distribute-dashboards-reports.md).

A megosztáshoz Önnek és az összes címzetteknek is [Power BI Pro-licencre](service-features-license-type.md) van szüksége, vagy pedig a tartalomnak kell egy [Prémium-kapacitásban](service-premium.md) lennie. Javaslatai vannak? A Power BI csapata mindig szívesen fogadja visszajelzését, amelyet a [Power BI-közösség webhelyén](https://community.powerbi.com/) küldhet el.

Jelentéseket megoszthat munkatársaival, amennyiben ugyanazt az e-mail-tartományt használják, mint Ön. A megosztás a Power BI szolgáltatás legtöbb helyén elvégezhető, többek között a Kedvencek, a Legutóbbi, A Velem megosztva (ha a tulajdonos engedélyezte a megosztást) vagy a Saját munkaterület helyekről. A megosztott jelentés címzettjei használhatják, de nem szerkeszthetik a jelentést. Az adatokat ugyanúgy látják, ahogyan Ön is látja a jelentésben, hacsak nem alkalmaz [sorszintű biztonságot (RLS-t)](service-admin-rls.md). 

## <a name="filter-and-share-a-report"></a>Jelentés szűrése és megosztása
Mi történik olyankor, ha egy jelentésnek egy szűrt verzióját szeretné megosztani? Például egy olyan jelentést, amely csak egy adott város, év vagy értékesítő adatait jeleníti meg. Ezt egy egyedi URL-cím létrehozásával teheti meg.

1. Nyissa meg a jelentést [Szerkesztő nézetben](consumer/end-user-reading-view.md), alkalmazza a szűrőt, majd mentse a jelentést.
   
   Ebben a példában a [Kiskereskedelmi elemzési mintát](sample-tutorial-connect-to-the-samples.md) szűrjük, hogy csak azokat az értékeket mutassa, ahol a **Territory** (Terület) **NC** (Észak-Karolnia) értékű.
   
   ![Jelentés Szűrés ablaktáblája](media/service-share-reports/power-bi-filter-report2.png)
2. Adja hozzá a jelentésoldal URL-címéhez a következőt:
   
   ?filter=*táblanév*/*mezőnév* eq *érték*
   
    A mező **sztring** típusú kell hogy legyen, és sem a *táblanév*, sem pedig a *mezőnév* nem tartalmazhat szóközöket.
   
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

