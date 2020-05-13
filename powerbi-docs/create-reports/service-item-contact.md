---
title: Kapcsolattartási adatok beállítása jelentésekhez és irányítópultokhoz
description: Útmutató jelentések és irányítópultok kapcsolattartási adatainak beállításához.
author: LukaszPawlowski-MS
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/08/2019
ms.author: lukaszp
LocalizationGroup: Common tasks
ms.openlocfilehash: 3f0d60bb780b980d3840072568e30d6b4e09da34
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83349008"
---
# <a name="set-contact-information-for-reports-and-dashboards-in-the-power-bi-service"></a>Kapcsolattartási adatok beállítása jelentésekhez és irányítópultokhoz a Power BI szolgáltatásban
Ez a cikk egy irányítópult vagy jelentés kapcsolattartási adatainak beállítását ismerteti a Power BI szolgáltatásban.

> [!NOTE]
> Az elemekhez klasszikus vagy új munkaterületen is beállíthatók kapcsolattartási adatok. A Saját munkaterületen nem állíthatók be kapcsolattartási adatok az elemekhez. Az információs kártya akkor jelenik meg, ha a jelentést vagy irányítópultot az [új arculattal](../consumer/service-new-look.md) jelenítik meg.

Egy elem kapcsolataihoz több felhasználó vagy csoport is felvehető. Ezek a következők lehetnek:
* Személy
* Office 365-csoport
* E-mailezési engedéllyel rendelkező biztonsági csoport
* Terjesztési lista

Alapértelmezés szerint az új jelentést vagy irányítópultot létrehozó személy a kapcsolattartó. A beállított érték felülírja az alapértelmezést. A kapcsolattartók listájáról természetesen az összes személy vagy csoport eltávolítható. Ilyenkor klasszikus munkaterület esetén a munkaterület Office 365-csoportja lesz megjelenítve. Az új felületű munkaterületeken a [munkaterület kapcsolatlistája](../collaborate-share/service-create-the-new-workspaces.md#workspace-contact-list) lesz használva. Ha a munkaterület kapcsolatlistája nincs beállítva, a munkaterület-rendszergazdák jelennek meg.

A kapcsolattartási adatok az elem megtekintő számára vannak megjelenítve. 

 ![szolgáltatás jelentés kapcsolattartó](media/service-item-contact/service-report-contact.png)

Ha a kapcsolattartók listájára kattint e-mail lesz létrehozva, amelyben kérdéseket tehet fel, vagy segítséget kérhet. 

 ![szolgáltatás kapcsolattartó e-mail](media/service-item-contact/service-contact-email.png)
 
A kapcsolattartók listájának adatai máshol is fel vannak használva. Bizonyos hibák esetén például megjelenik a hibáról tájékoztató párbeszédpanelen. Az elemmel kapcsolatos automatikus e-mail-üzenetek, például hozzáférési kérelmek a kapcsolattartási listának lesznek elküldve. 

> [!NOTE]
> Alkalmazás közzétételekor az egyes elemekhez beállított kapcsolattartási adatok az alkalmazást közzétevő vagy frissítő személyre lesznek beállítva. Beállítható az alkalmazás támogatási URL-címe, hogy az alkalmazás felhasználói szükség esetén segítséget kérhessenek.

## <a name="set-contact-information-for-a-report"></a>Kapcsolattartási adatok beállítása jelentéshez
1. Kattintson a **Jelentések** fülre a munkaterületén.
2. Keresse meg a kívánt jelentést, és válassza a **Beállítások** ikont.
3. Keresse meg a **Kapcsolattartó** beviteli mezőt, és adja meg annak értékét.

     ![szolgáltatás jelentés kapcsolattartó beállítás](media/service-item-contact/service-report-contact-setting.png)

## <a name="set-contact-information-for-a-dashboard"></a>Kapcsolattartási adatok beállítása irányítópulthoz
1. Kattintson az **Irányítópultok** fülre a munkaterületén.
2. Keresse meg a kívánt irányítópultot, és válassza a **Beállítások** ikont.
3. Keresse meg a **Kapcsolattartó** beviteli mezőt, és adja meg annak értékét.

     ![szolgáltatás irányítópult kapcsolattartó beállítás](media/service-item-contact/service-dashboard-contact-setting.png)

## <a name="limitations-and-considerations"></a>Korlátozások és megfontolandó szempontok
* A kapcsolattartó a Power BI szolgáltatásban létrehozott új elemekhez automatikusan be lesz állítva. A meglévő elemek alapértelmezés szerint megjelenítik a munkaterületet.
* A kapcsolattartási listára bármely felhasználó vagy csoport felvehető, de ezek nem kapnak automatikusan engedélyt az adott elemre. Használjon megosztást, vagy szerepkörön keresztül adjon hozzáférést a munkaterülethez azoknak a felhasználóknak, akiknek szükséges. 
* A rendszer nem küldi le az elemszintű címlistát az alkalmazásoknak azok közzétételekor. Az új alkalmazásnavigációs felületen található, konfigurálható támogatási URL-lel kezelheti az alkalmazás felhasználóitól érkező visszajelzéseket.


## <a name="next-steps"></a>További lépések

Több kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
