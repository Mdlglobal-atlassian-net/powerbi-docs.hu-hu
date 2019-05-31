---
title: Szűrheti a jelentéseket, és megoszthatja munkatársaival – Power bi-ban
description: Tudnivalók arról, hogyan szűrheti a Power BI-jelentéseket, és hogyan oszthatja meg azokat munkatársaival a szervezetnél.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/24/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 5f3808884e63521ec1dd775d876f1cf707bbe56b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770681"
---
# <a name="filter-a-power-bi-report-and-share-it-with-coworkers"></a>A Power BI-jelentés szűrése, és megoszthatja munkatársaival
A *Megosztással* egyszerűen biztosíthatja néhány személy hozzáférését az irányítópultjaihoz és jelentéseihez. Mi történik olyankor, ha egy jelentésnek egy szűrt verzióját szeretné megosztani? Például egy olyan jelentést, amely csak egy adott város, év vagy értékesítő adatait jeleníti meg. Próbálja ki egy jelentés szűrés és megosztást vagy egy egyéni URL-cím létrehozása. A jelentés szűrt lesz, amikor a címzettek először megnyitják. Eltávolíthatják a szűrőt az URL-cím módosításával. 

A Power BI-ban [többféle módon valósítható meg a jelentések közös használata és terjesztése](service-how-to-collaborate-distribute-dashboards-reports.md). A megosztáshoz Önnek és az összes címzetteknek is [Power BI Pro-licencre](service-features-license-type.md) van szüksége, vagy pedig a tartalomnak kell egy [Prémium-kapacitásban](service-premium-what-is.md) lennie. 

## <a name="two-ways-to-filter-a-report"></a>Két különböző módon szűrheti a jelentéseket

### <a name="set-a-filter"></a>Egy szűrő beállítása

Nyissa meg a jelentést [Szerkesztő nézetben](consumer/end-user-reading-view.md), alkalmazza a szűrőt, majd mentse a jelentést.
   
Ebben a példában a [Kiskereskedelmi elemzési mintát](sample-tutorial-connect-to-the-samples.md) szűrjük, hogy csak azokat az értékeket mutassa, ahol a **Territory** (Terület) **NC** (Észak-Karolnia) értékű.
   
![Jelentés Szűrés ablaktáblája](media/service-share-reports/power-bi-filter-report2.png)

### <a name="create-a-filter-in-the-url"></a>Az URL-szűrő létrehozása

Adja hozzá a jelentésoldal URL-címéhez a következőt:
   
?filter=*táblanév*/*mezőnév* eq *érték*
   
A mező típusa szám, datetime vagy karakterlánc kell lennie. A *táblanév* vagy *mezőnév* értékei nem tartalmazhatnak szóközt.
   
A példánkban **Store** (Üzlet) a tábla neve, **Territory** (Terület) a mező neve, és **NC** (Észak-Karolnia) az érték, amelyre szűrni szeretnénk:
   
?filter=Store/Territory eq 'NC'
   
![Szűrt jelentés URL-címe](media/service-share-reports/power-bi-filter-url3.png)
   
A böngésző ehhez még hozzáad néhány speciális karaktert a perjelek, szóközök és aposztrófok helyettesítésére, így az eredmény a következő lesz:
   
app.powerbi.com/groups/me/reports/010ae9ad-a9ab-4904-a7a1-xxxxxxxxxxxx/ReportSection2?filter=Store%252FTerritory%20eq%20%27NC%27

Tekintse meg a cikket [a jelentések szűrhetők az URL-cím lekérdezési karakterlánc paraméterei az](service-url-filters.md) sokkal részletesebben.

## <a name="share-the-filtered-report"></a>A szűrt jelentés megosztása

1. Ha Ön [megosztja a jelentést](service-share-dashboards.md), törölje a **e-mail-értesítés küldése a címzetteknek** jelölőnégyzetet.

    ![Jelentés megosztásának párbeszédablaka](media/service-share-reports/power-bi-share-report-dialog.png)

4. Küldje el a hivatkozást a korábban létrehozott szűrővel.

## <a name="next-steps"></a>Következő lépések
* Visszajelzés küldene? Mondja el javaslatait a [Power BI-közösség webhelyén](https://community.powerbi.com/).
* [Irányítópultok és jelentések közös használata és megosztása](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Irányítópult megosztása](service-share-dashboards.md)
* További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/).

