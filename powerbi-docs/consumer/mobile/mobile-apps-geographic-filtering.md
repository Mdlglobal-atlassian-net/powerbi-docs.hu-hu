---
title: Jelentések szűrése földrajzi hely alapján a Power BI mobilalkalmazásban
description: Megtudhatja, hogyan szűrheti a jelentéseket földrajzi hely alapján a Microsoft Power BI mobilalkalmazásokban, ha a jelentés tulajdonosa beállított földrajzi címkéket.
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: painbar
ms.openlocfilehash: d4e8ab0effef52071f592902a6c2fdb2649ff52d
ms.sourcegitcommit: 480bba9c745cb9af2005637e693c5714b3c64a8a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/11/2020
ms.locfileid: "79114779"
---
# <a name="filter-a-report-by-geographic-location-in-the-power-bi-mobile-apps"></a>Jelentések szűrése földrajzi hely alapján a Power BI mobilalkalmazásokban
A következőkre vonatkozik:

| ![iPhone](./media/mobile-apps-geographic-filtering/iphone-logo-50-px.png) | ![iPad](./media/mobile-apps-geographic-filtering/ipad-logo-50-px.png) | ![Android rendszerű telefon](./media/mobile-apps-geographic-filtering/android-phone-logo-50-px.png) | ![Android rendszerű táblagép](./media/mobile-apps-view-dashboard/android-tablet-logo-50-px.png) | ![Windows rendszerű telefon](./media/mobile-apps-geographic-filtering/win-10-logo-50-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhone-ok |iPadek |Android rendszerű telefonok |Android rendszerű táblagépek |Windows 10 rendszerű telefonok |

A mobileszközön megjelenített Power BI-jelentés jobb felső sarkában látható egy kis gombostű? Ha igen, akkor a jelentés szűrhető földrajzi hely alapján.

> [!NOTE]
> Csak akkor szűrhet hely alapján, ha a földrajzi nevek angol nyelven szerepelnek a jelentésben – például „New York City” vagy „Germany”. A Windows 10 rendszerű táblagépek és számítógépek nem támogatják a földrajzi szűrést, a Windows 10 rendszerű telefonok azonban igen.
> 
> 

## <a name="filter-your-report-by-your-geographic-location"></a>Jelentés szűrése földrajzi hely alapján
1. Nyisson meg egy jelentést mobileszközén a Power BI mobilalkalmazásban.
2. Ha a jelentés tartalmaz földrajzi adatokat, egy üzenet jelenik meg, amely a helymeghatározás engedélyezésére kéri a Power BI számára. Kattintson az **Engedélyezés**, majd ismét az **Engedélyezés** gombra.
3. Koppintson a gombostűre. ![Gombostű ikon](./media/mobile-apps-geographic-filtering/power-bi-mobile-geo-icon.png). A jelentésben foglalt adatoktól függően szűrhet városra, államra/tartományra és országra/régióra is. A szűrő kizárólag azokat a lehetőségeket listázza, amelyek megfelelnek az aktuális helyének.
   
    ![Gombostű szűrő](./media/mobile-apps-geographic-filtering/power-bi-mobile-geo-map-set-filter.png)

## <a name="why-dont-i-see-location-tags-on-a-report"></a>Miért nem láthatók a helyek címkéi a jelentésben?
Ahhoz, hogy a helyek címkéi megjelenjenek, mindhárom alábbi feltételnek teljesülnie kell. 

* A jelentést a Power BI Desktop alkalmazásban létrehozó személynek legalább egy oszlop esetében [kategorizált földrajzi adatokat](../../desktop-mobile-geofiltering.md) (például Város, Állam vagy Ország/Régió) kellett megadnia.
* Olyan helyen tartózkodik, amelyik rendelkezik adattal a kérdéses oszlopban.
* A következő mobileszközök valamelyikét használja:
  * iOS (iPad, iPhone vagy iPod).
  * Android (telefon, táblagép).
  * Windows 10 rendszerű telefon (az egyéb Windows 10 rendszerű eszközök, például számítógépek és táblagépek nem támogatják a földrajzi szűrést).

A Power BI Desktop [földrajzi szűrésének beállításáról itt](../../desktop-mobile-geofiltering.md) olvashat további információkat.

### <a name="next-steps"></a>Következő lépések
* [Power BI-információk elérése a való világból](mobile-apps-data-in-real-world-context.md) a mobilalkalmazásokkal
* [Adatok kategorizálása a Power BI Desktopban](../../desktop-data-categorization.md) 
* Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

