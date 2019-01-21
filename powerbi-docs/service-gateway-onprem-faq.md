---
title: Helyszíni adatátjáró – GYIK
description: Itt olvashatók a helyszíni adatátjáró gyakori kérdései. Ezen az oldalon összegyűjtve olvashatók az adatátjáróval kapcsolatos gyakori kérdések.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 01/24/2018
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: b1c74968365db59d51f7c0a7bdb356552cc75596
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54283782"
---
# <a name="on-premises-data-gateway-faq"></a>Helyszíni adatátjáró – GYIK
<!-- Shared FAQ shared Include -->
[!INCLUDE [gateway-onprem-faq-shared-include](./includes/gateway-onprem-faq-shared-include.md)]

## <a name="analysis-services"></a>Analysis Services
**Kérdés:** Létrehozhatom az msdmpump.dll-lel az érvényben lévő felhasználónév egy egyéni leképezését az Analysis Serviceshez?  
**Válasz:** Nem. Ez jelenleg nem támogatott.

**Kérdés:** Kapcsolódhatok az átjáróval egy többdimenziós (OLAP-) példányhoz?  
**Válasz:** Igen. A helyszíni átjáró az Analysis Services táblázatos és többdimenziós modelljei esetén is támogatja az élő kapcsolatokat.

**Kérdés:** Mi történik akkor, ha az átjárót egy olyan Windows-hitelesítést használó számítógépre telepítem, amelyik nem ugyanabban a tartományban található, mint a saját helyszíni kiszolgálóm?  
**Válasz:** A működés ilyen esetben nem garantálható. Azon múlik minden, hogy a két tartomány között milyen megbízhatósági kapcsolat van. Ha a két különböző tartomány egy megbízható tartománymodellben van, akkor lehetséges, hogy az adatátjáró képes lesz csatlakozni az Analysis Serviceshez, és az érvényben lévő felhasználónév feloldható lesz. Ha ez nem áll fenn, akkor előfordulhat, hogy bejelentkezési hibába ütközik.

**Kérdés:** Hol tudom megnézni, hogy melyik érvényben lévő felhasználónév kerül átadásra a helyszíni Analysis Services-kiszolgálómnak?  
**Válasz:** Erre a kérdésre a [hibaelhárítási cikkben](service-gateway-onprem-tshoot.md) találja meg a választ.

**Kérdés:** 25 adatbázisom van az Analysis Servicesben. Van arra lehetőség, hogy mindegyiket egyszerre engedélyezzem az átjáróban?  
**Válasz:** Nem. Ez már tervbe van véve, de még nincs kitűzött időpontja.

## <a name="administration"></a>Felügyelet
**Kérdés:** Lehet egy átjárónak több rendszergazdája is?  
**Válasz:** Igen. Egy átjáró felügyelete során a rendszergazda lapon további rendszergazdák is felvehetők.

**Kérdés:** Az átjáró rendszergazdájának azon a számítógépen is rendszergazdának kell lennie, amelyiken az átjáró telepítve van?  
**Válasz:** Nem. Az átjáró rendszergazdája a szolgáltatásból felügyeli az átjárót.

**Kérdés:** Megakadályozhatom valahogy, hogy a cégem felhasználói átjárókat hozzanak létre?  
**Válasz:** Nem. Ez már tervbe van véve, de még nincs kitűzött időpontja.

**Kérdés:** Lekérhetek használati és statisztikai információkat a cégem átjárójával kapcsolatban?  
**Válasz:** Nem. Ez már tervbe van véve, de még nincs kitűzött időpontja.

## <a name="power-bi"></a>Power BI
**Kérdés:** Kell frissítenem a személyes átjárót?
**Válasz:** Nem, a személyes átjárót továbbra is használhatja a Power BI-hoz.

**Kérdés:** A Power BI-ban milyen gyakran frissülnek egy irányítópult csempéi, ha egy helyszíni adatátjárón keresztül kapcsolódnak?  
**Válasz:** Körülbelül 10 percenként. Ezek a DirectQuery-kapcsolatok. Ez azonban nem azt jelenti, hogy egy csempe tíz percenként elvégez egy lekérdezést az Ön helyszíni kiszolgálója felé, és megjeleníti az új adatokat.

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

## <a name="next-steps"></a>Következő lépések
[Helyszíni adatátjáró](service-gateway-onprem.md)  
[Helyszíni adatátjáró – részletes](service-gateway-onprem-indepth.md)  
[A Helyszíni adatátjáróval kapcsolatos hibák elhárítása](service-gateway-onprem-tshoot.md)  
További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

