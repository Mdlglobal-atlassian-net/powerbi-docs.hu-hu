---
title: Adatvédelmi metrikák jelentése
description: Az adatvédelmi metrikákról szóló jelentés bemutatása
author: paulinbar
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: e16acffd683b14eb48a6e21ddc456caeac25efc3
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83132001"
---
# <a name="data-protection-metrics-report-preview"></a>Adatvédelmi metrikákról készült jelentés (előzetes verzió)

## <a name="what-is-the-data-protection-metrics-report"></a>Mi az adatvédelmi metrikákról készült jelentés?
Az adatvédelmi metrikákról készült dedikált jelentéssel a [Power BI-rendszergazdák](../admin/service-admin-role.md) figyelhetik és követhetik az adatbizalmassági címkék használatát és a bérlőn belüli alkalmazását.

![Adatvédelmi metrikák jelentése](./media/service-security-data-protection-metrics-report/protection-metrics-seven-days-1.png)
 
A jelentés a következőket tartalmazza:
* Egy 100%-ig halmozott oszlopdiagramot, amely a bizalmassági címkék napi használatát mutatja meg a bérlőben az elmúlt 7, 30 vagy 90 napra vonatkozóan. A diagram segítségével könnyen nyomon követhető a különböző címketípusok egymáshoz viszonyított időbeli használata.
* Perecdiagramok, amelyek a bizalmassági címkék bérlőbeli használatának aktuális állapotát mutatják az irányítópultokra, jelentésekre, adathalmazokra és adatfolyamokra vonatkozóan.
* A Cloud App Security portálra mutató hivatkozás, ahol a Power BI riasztásai, kockázatnak kitett felhasználói, tevékenységnaplói és más információi tekinthetők meg. További információ: [A Microsoft Cloud App Security vezérlőinek használata a Power BI-ban (előzetes verzió)](./service-security-using-microsoft-cloud-app-security-controls.md).

A jelentés 24 óránként frissül.

## <a name="viewing-the-data-protection-metrics-report"></a>Az adatvédelmi metrikákról készült jelentés megtekintése

A jelentés megnyitásához és megtekintéséhez rendelkeznie kell a [Power BI-rendszergazdai szerepkörrel](../admin/service-admin-role.md).
A jelentés megtekintéséhez nyissa meg a **Beállítások > Felügyeleti portál** elemet, majd válassza **Védelmi metrikák (előzetes verzió)** .

![Védelmi metrikák a felügyeleti portálon](./media/service-security-data-protection-metrics-report/protection-metrics-admin-portal.png)
 
 
Amikor először nyitja meg az adatvédelmi metrikákról készülő jelentést, annak betöltése eltarthat néhány másodpercig. Létrejön egy jelentés és egy **Adatvédelmi metrikák (automatikusan előállított)** adathalmaz a privát környezetében, a Saját munkaterület részben. Nem javasoljuk, hogy itt tekintse meg – ez nem a teljeskörű jelentés. A jelentést érdemesebb a fent leírt módon, a Felügyeleti portálon megtekinteni.

> [!CAUTION]
> A jelentést és az adathalmazt semmilyen módon ne módosítsa, mivel időközönként megjelennek a jelentés újabb verziói, és az eredeti jelentésen végzett módosítások felül lesznek írva az új verzióra frissítéskor.

## <a name="report-updates"></a>A jelentés frissítései

Az adatvédelmi metrikákról készülő jelentés javított verziói szabályos időközönként jelennek meg. Ha a jelentés megnyitásakor elérhető újabb verzió, a rendszer rákérdez, hogy az új verziót szeretné-e megnyitni. Ha igennel válaszol, a jelentés új verziója lesz betöltve, amely felülírja a régit. Az előző jelentésen és/vagy adathalmazon esetleg végrehajtott összes módosítás elveszik. Dönthet úgy, hogy nem az új verziót nyitja meg, de ilyenkor nem tudja kihasználni az új verzió fejlesztéseinek előnyeit. 
## <a name="notes-and-considerations"></a>Megjegyzések és megfontolandó szempontok
* Az adatvédelmi metrikákról készülő jelentés sikeres generálásához a bérlőben engedélyezni kell az [információvédelmet](./service-security-enable-data-sensitivity-labels.md), és [bizalmassági címkéket kell alkalmazni](../collaborate-share/service-security-apply-data-sensitivity-labels.md). 
* A Cloud App Security információi csak akkor érhetők el, ha a vállalat rendelkezik a megfelelő [Cloud App Security-licenccel](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls#microsoft-cloud-app-security-licensing).
* Ha úgy dönt, hogy olyan felhasználóval oszt meg az adatvédelmi metrikákról készült jelentésből származó információkat, aki nem Power BI-rendszergazda, szem előtt kell tartania, hogy ez a jelentés bizalmas információkat tartalmaz a vállalatról.
* Az adatvédelmi metrikákról készülő jelentés speciális jelentés, amely nem jelenik meg a Velem megosztva, a Legutóbbiak és a Kedvencek listában sem.
* Az adatvédelmi metrikákról szóló jelentés nem érhető el [külső felhasználók számára (Azure Active Directory B2B-vendégfelhasználók)](../admin/service-admin-azure-ad-b2b.md).
## <a name="next-steps"></a>További lépések
* [Adatvédelem a Power BI-ban (előzetes verzió)](./service-security-data-protection-overview.md)
* [A Microsoft Cloud App Security vezérlőinek használata a Power BI-ban (előzetes verzió)](./service-security-using-microsoft-cloud-app-security-controls.md)
* [A Power BI-szolgáltatásgazda szerepkör ismertetése](../admin/service-admin-role.md)
* [Bizalmassági adatcímkézés engedélyezése a Power BI-ban](./service-security-enable-data-sensitivity-labels.md)