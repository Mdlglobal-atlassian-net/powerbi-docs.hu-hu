---
title: Helyszíni adatátjáró – Gyakori kérdések – Power BI
description: Itt olvashatók a Power BI helyszíni adatátjáróival kapcsolatos gyakori kérdések. Ezen az oldalon összegyűjtve olvashatók a Power BI adatátjáróival kapcsolatos gyakori kérdések.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 99a03f88ed5f6585ca8ed6d64f396e70cdd046e5
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68272746"
---
# <a name="on-premises-data-gateway-faq---power-bi"></a>Helyszíni adatátjáró – Gyakori kérdések – Power BI

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

## <a name="power-bi"></a>Power BI

**Kérdés:** Kell frissítenem a személyes átjárót?  
**Válasz:** Nem, a személyes átjárót továbbra is használhatja a Power BI-hoz.

**Kérdés:** Szükség van különleges engedélyekre az átjárók telepítéséhez és a Power BI szolgáltatásban való kezeléséhez?
**Válasz:** Nincs szükség speciális engedélyekre.

**Kérdés:** Feltölthetek olyan, Power Pivot adatmodellt használó Excel-munkafüzeteket, amelyek helyszíni adatforrásokhoz kapcsolódnak? Ilyen forgatókönyv esetén kell átjárót használnom?  
**Válasz:** Igen, feltöltheti a munkafüzetet. És nem, nem kell átjárót használnia. Mivel azonban az adatok egy Excel-adatmodellben helyezkednek el, az Excel-munkafüzet adatain alapuló Power BI-jelentések nem élő jelentések lesznek. Ahhoz, hogy a jelentések frissüljenek a Power BI-ban, minden alkalommal újra fel kell töltenie a frissített munkafüzetet. Vagy használhat egy átjárót is ütemezett frissítéssel.

**Kérdés:** Ha a felhasználók olyan irányítópultokat osztanak meg, amelyeknek DirectQuery-kapcsolataik vannak, akkor azok a felhasználók, akikkel megosztották az irányítópultokat, láthatják az adatokat annak ellenére, hogy nem rendelkeznek ugyanazokkal az engedélyekkel?  
**Válasz:** Az Analysis Serviceshez kapcsolódó irányítópultok esetén a felhasználók csak azokat az adatokat láthatják, amelyekhez hozzáféréssel rendelkeznek. Ha a felhasználók nem rendelkeznek ugyanazokkal az engedélyekkel, nem fognak látni semmilyen adatot. Más adatforrások esetén az összes felhasználó ugyanazokat a hitelesítő adatokat használja, amelyeket az adatforrás rendszergazdája megadott.

**Kérdés:** Miért nem tudok kapcsolódni az Oracle-kiszolgálómhoz?  
**Válasz:** Előfordulhat, hogy telepítenie kell az Oracle-ügyfelet, és konfigurálnia a tnsnames.ora fájlt a megfelelő kiszolgálóadatokkal, hogy kapcsolódni tudjon az Oracle-kiszolgálójához. Ez egy külön telepítés, amely az átjárón kívül esik. További információ: [Az Oracle-ügyfél telepítése](service-gateway-onprem-manage-oracle.md#installing-the-oracle-client).

**Kérdés:** Működik az átjáró az ExpressRoute-tal?  
**Válasz:** Igen. Az ExpressRoute és a Power BI közös használatáról további információt [A Power BI és az ExpressRoute](service-admin-power-bi-expressroute.md) című cikkben olvashat.

**Kérdés:** R-szkripteket használok. Ez támogatott?
**Válasz**: Az R-szkriptek csak személyes módhoz támogatottak.

## <a name="analysis-services-in-power-bi"></a>Power BI Analysis Services

**Kérdés:** Létrehozhatom az msdmpump.dll-lel az érvényben lévő felhasználónév egy egyéni leképezését az Analysis Serviceshez?  
**Válasz:** Nem. Ez jelenleg nem támogatott.

**Kérdés:** Kapcsolódhatok az átjáróval egy többdimenziós (OLAP-) példányhoz?  
**Válasz:** Igen. A helyszíni átjáró az Analysis Services táblázatos és többdimenziós modelljei esetén is támogatja az élő kapcsolatokat.

**Kérdés:** Mi történik akkor, ha az átjárót egy olyan Windows-hitelesítést használó számítógépre telepítem, amelyik nem ugyanabban a tartományban található, mint a saját helyszíni kiszolgálóm?  
**Válasz:** A működés ilyen esetben nem garantálható. Azon múlik minden, hogy a két tartomány között milyen megbízhatósági kapcsolat van. Ha a két különböző tartomány egy megbízható tartománymodellben van, akkor lehetséges, hogy az adatátjáró képes lesz csatlakozni az Analysis Serviceshez, és az érvényben lévő felhasználónév feloldható lesz. Ha ez nem áll fenn, akkor előfordulhat, hogy bejelentkezési hibába ütközik.

**Kérdés:** Hol tudom megnézni, hogy melyik érvényben lévő felhasználónév kerül átadásra a helyszíni Analysis Services-kiszolgálómnak?  
**Válasz:** Erre a kérdésre a [hibaelhárítási cikkben](service-gateway-onprem-tshoot.md) találja meg a választ.

## <a name="next-steps"></a>Következő lépések

* [A helyszíni adatátjáró hibaelhárítása](/data-integration/gateway/service-gateway-tshoot)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
