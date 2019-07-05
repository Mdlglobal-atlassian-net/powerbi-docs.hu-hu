---
title: Szűrőtípusok Power BI-jelnetésekben
description: Oldalszűrő, vizualizációszűrő vagy jelentésszűrő hozzáadása egy jelentéshez a Power BI-ban
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/25/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 499a4f3be9f153a1994802e9707f855b71d2a506
ms.sourcegitcommit: 58c649ec5fd2447a0f9ca4c4d45a0e9fff2f1b6a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/27/2019
ms.locfileid: "67409845"
---
# <a name="types-of-filters-in-power-bi-reports"></a>Szűrőtípusok Power BI-jelnetésekben

A szűrők nem viselkednek egyformán, hiszen nem egyformán vannak létrehozva. A létrehozásuk módja befolyásolja, hogy hogyan viselkednek az új szűrőpanelen szerkesztési módban. Ez a cikk a különböző szűrőfajtákat ismerteti: a létrehozásuk különböző módjait, és a különböző feladatokat, amelyekre alkalmasak. Tájékozódhat a [szűrők jelentéshez adásáról](power-bi-report-add-filter.md). 

![Szűrőpanel](media/power-bi-report-filter-types/power-bi-filter-pane.png)

Kezdjük a két leggyakoribb szűrőtípussal, a manuálissal és az automatikussal.

## <a name="manual-filters"></a>Manuális szűrők 

A manuális szűrőket a jelentés készítője húzza az új szűrőpanel tetszőleges pontjára. A jelentésre szerkesztési engedéllyel rendelkező felhasználók szerkeszthetik, törölhetik, kiüríthetik, elrejthetik, zárolhatják, átnevezhetik vagy rendezhetik ezt a szűrőt az új panelen.

## <a name="automatic-filters"></a>Automatikus szűrők 

Az automatikus szűrők a vizualizáció készítése során automatikusan vannak felvéve a szűrőpanelre a vizualizációk szintjén. Ezek a szűrők a vizualizációt alkotó mezőkön alapulnak. A jelentéshez szerkesztési engedéllyel rendelkező felhasználók szerkeszthetik, kiüríthetik, elrejthetik, zárolhatják, átnevezhetik vagy rendezhetik ezt a szűrőt az új panelen. Automatikus szűrőket nem törölhetnek, mert a vizualizáció hivatkozik ezekre a mezőkre.

## <a name="more-advanced-filters"></a>Fejlettebb szűrők

Ezek a szűrőtípusok kevésbé elterjedtek, mégis fontos tisztában lenni a működésükkel, ha megjelennek a jelentésben. Emellett hasznosnak is bizonyulhatnak a jelentéshez leginkább megfelelő szűrő létrehozása során.

## <a name="include-and-exclude-filters"></a>Belefoglalási és kizárási szűrők

A belefoglalási és kizárási szűrők automatikusan fel lesznek véve a szűrőpanelre, amikor egy vizualizációhoz a belefoglalási vagy kizárási funkciót használja. A jelentéshez szerkesztési engedéllyel rendelkező felhasználók törölhetik, zárolhatják, elrejthetik vagy rendezhetik ezt a szűrőt az új panelen. Belefoglalási vagy kizárási szűrőt nem szerkeszthetnek, üríthetnek ki vagy nevezhetnek át, mert az a vizualizációk belefoglalási és kizárási funkciójával van társítva.

![Kizárási szűrő](media/power-bi-report-filter-types/power-bi-filters-exclude.png)

## <a name="drill-down-filters"></a>Részletezési szűrők

A részletezési szűrők automatikusan fel lesznek véve a szűrőpanelre, amikor egy vizualizációhoz a részletezési funkciót használja a jelentésben. A jelentésre szerkesztési engedéllyel rendelkező felhasználók szerkeszthetik vagy kiüríthetik ezt a szűrőt az új panelen. Ezt a szűrőt nem törölhetik, nem rejthetik el, nem zárolhatják, nem nevezhetik át és nem rendezhetik, mert az a vizualizációk részletezési funkciójával van társítva. A részletezési szűrő eltávolításához kattintson a vizualizáció Felhatolás gombjára.

![Részletezési szűrő](media/power-bi-report-filter-types/power-bi-filters-drill-down.png)

## <a name="cross-drill-filters"></a>Kereszt-részletezési szűrők

A kereszt-részletezési szűrők automatikusan fel lesznek véve az új panelre, amikor egy részletezési szűrő a keresztszűrési vagy keresztkiemelési funkcióval a jelentésoldal egy másik vizualizációjának van átadva. A jelentéshez szerkesztési engedéllyel rendelkező felhasználók ezt a szűrőt nem törölhetik, üríthetik ki, rejthetik el, zárolhatják, nevezhetik át vagy rendezhetik, mert az a vizualizációk részletezési funkciójával van társítva. Ezt a szűrőt szerkeszteni sem tudják, mert egy másik vizualizációbeli részletezésből ered. A kereszt-részletezési szűrő eltávolításához kattintson annak a vizualizációnak a Felhatolás gombjára, amely a szűrőt átadja.

## <a name="drillthrough-filters"></a>Részletezési szűrők

Az átfogó részletezési szűrők az átfogó részletezés funkcióval vannak átadva egy oldalról egy másikra. Megjelennek az átfogó részletezési panelen. Az átfogó részletezési szűrőknek két típusa van. Az első az, amely meghívja a részletezést. A jelentésszerkesztők az ilyen típusú szűrőket szerkeszthetik, törölhetik, kiüríthetik, elrejthetik vagy zárolhatják. Az átfogó részletezési szűrők másik típusa az, amely a forrásoldal oldalszintű szűrői alapján van átadva a célhoz. A jelentésszerkesztők ezt az átmeneti részletezési szűrőtípust szerkeszthetik, törölhetik vagy kiüríthetik. Ezt a szűrőt nem rejthetik el vagy zárolhatják a végfelhasználók számára.

## <a name="url-filters"></a>URL-szűrők

URL-szűrők egy lekérdezési URL-paraméter felvételével vannak az új panelhez adva. A jelentéshez szerkesztési engedéllyel rendelkező felhasználók szerkeszthetik, törölhetik vagy kiüríthetik ezt a szűrőt az új panelen. Ezt a szűrőt nem rejthetik el, nem zárolhatják, nem nevezhetik át és nem rendezhetik, mert az az URL-paraméterrel van társítva. A szűrő eltávolításához távolítsa el a paramétert az URL-címből. Az alábbi példa egy paraméterrel ellátott URL-címet mutat be:

app.powerbi.com/groups/me/apps/*app-id*/reports/*report-id*/ReportSection?filter=Stores~2FStatus%20eq%20'Off'

![URL-szűrő](media/power-bi-report-filter-types/power-bi-filter-url.png)

További információ az [URL-szűrőkről](service-url-filters.md).

## <a name="pass-through-filters"></a>Továbbított szűrők

A továbbított szűrők a Q&A használatával létrehozott, vizualizációszintű szűrők. A készítők törölhetik, elrejthetik vagy rendezhetik ezeket a szűrőket az új panelen. Ezeket a szűrőket azonban nem nevezhetik át, szerkeszthetik, üríthetik vagy zárolhatják.

![Továbbított szűrő a Q&A-val](media/power-bi-report-filter-types/power-bi-filters-qna.png)

## <a name="comparing-filter-types"></a>Szűrőtípusok összehasonlítása

A táblázat összefoglalja, hogy mit tehetnek meg a készítők a különböző típusú szűrőkkel.

| Szűrő típusa | Szerkesztés | Törlés | Törlés | Elrejtés | Zárolás | Rendezés | Átnevezés |
|----|----|----|----|----|----|----|----|
| Manuális szűrők | Y | Y | Y | Y | Y | Y | Y |
| Automatikus szűrők | Y | Y | N | Y | Y | Y | Y |
| Belefoglalási/kizárási szűrők | N | N | Y | Y | Y | Y | N |
| Részletezési szűrők | Y | Y | N | N | N | N | N |
| Kereszt-részletezési szűrők | N | N | N | N | N | N | N |
| Átfogó részletezési szűrők (részletezést hív meg) | Y | Y | Y | Y | Y | N | N |
| Átfogó részletezési szűrők (átmeneti) | Y | Y | Y | N | N | N | N |
| URL-szűrők – átmeneti | Y | Y | Y | N | N | N | N |
| Továbbított szűrők | N | N | Y | Y | N | Y | N |



## <a name="next-steps"></a>Következő lépések

[Szűrők felvétele jelentésekbe](power-bi-report-add-filter.md)

[Ismerkedés a jelentések Szűrők panelével](consumer/end-user-report-filter.md)

[Szűrők és kiemelések a jelentésekben](power-bi-reports-filters-and-highlighting.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

