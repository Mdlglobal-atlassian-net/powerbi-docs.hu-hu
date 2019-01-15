---
title: A Power BI szolgáltatás tartalomcsomag-programjának áttekintése
description: Tartalomcsomag-tanúsítási program
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/20/2018
ms.author: maggies
ms.openlocfilehash: c5c69bab7fb0a47e5e546dfe1b3143a13428d4bc
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54285231"
---
# <a name="overview-of-the-power-bi-service-content-pack-program"></a>A Power BI szolgáltatás tartalomcsomag-programjának áttekintése
A tartalomcsomagok olyan nem beépített tartalmakból álló csomagok, amelyekkel a felhasználók azonnali elemzésekhez juthatnak adatforrásaikból. A tartalomcsomagok általában egy adott üzleti forgatókönyvre fókuszálva elemzéseket készítenek egy szerepkörről, tartományról vagy munkafolyamatról.

A független szoftvergyártók (ISV-k) sablonalapú tartalomcsomagokat készítenek, amelyeket a felhasználók a fiókjukhoz kapcsolhatnak és példányosíthatnak. Tartományszakértőkként könnyen fogyaszthatóvá tehetik az adatokat az üzleti felhasználók számára. A tartalomcsomagok alkalmi megfigyelési és elemzési lehetőségeket biztosítanak az ügyfelek számára anélkül, hogy ehhez jelentős beruházásokra lenne szükség a jelentéskészítési infrastruktúrában.

Az említett, ISV-k által létrehozott sablonalapú tartalomcsomagokat ez után elküldheti a Power BI csapatának, így nyilvánosan is elérhetők lesznek a Power BI tartalomcsomag-katalógusában (app.powerbi.com/getdata/services), illetve a Microsoft AppSource webhelyen (appsource.microsoft.com). A nyilvános tartalomcsomagok egyik példája [itt](template-content-pack-experience.md) tekinthető meg.

## <a name="overview"></a>Áttekintés
A sablonalapú tartalomcsomagok létrehozásának és beküldésének általános folyamata több lépésből áll.

 ![Folyamat](media/service-content-pack-overview/developer-content-pack-overview.png)

1. [Tekintse át a követelményeket](#requirements), és győződjön meg arról, hogy teljesülnek
2. [Hozzon létre a tartalmat](template-content-pack-authoring.md#queries) a Power BI Desktopban
3. [Hozzon létre egy irányítópultot](template-content-pack-authoring.md#dashboard) a PowerBI.com webhelyen
4. [Tesztelje a tartalomcsomagot](template-content-pack-testing.md) saját kezűleg a cégen belül
5. [Küldje be](template-content-pack-testing.md#submission) a tartalmat a Power BI csapatának közzétételre

<a name="requirements"></a>

## <a name="requirements"></a>Követelmények
Ahhoz, hogy létrehozzon egy tartalomcsomagot, majd beküldje a Power BI szolgáltatásban és az AppSource webhelyen való közzétételre, az alábbi követelményeknek kell megfelelnie:

* Rendelkeznie kell üzleti felhasználók által használt Saas-alkalmazással.
* Az SaaS-alkalmazásnak olyan felhasználói adatokat kell tartalmaznia, amelyek megjeleníthetők a Power BI-ban.
* Az SaaS-alkalmazásnak az interneten keresztül nyilvánosan elérhető API-val kell rendelkeznie. Ideális esetben az API egy REST-alapú API vagy OData-csatorna. A Power BI tartalomcsomagok több hitelesítéstípust is támogatnak, mint az alapszintű hitelesítés, az OAuth 2.0 és az API-kulcs. 
* SaaS-alkalmazása számára engedélyezve van tartalomcsomag közzététele. Kérelem beküldése: pbiservicesapps@microsoft.com. Minden kérelmet a relevancia és a várható használat alapján értékelünk. 
* Aláírt partnerszerződéssel kell rendelkeznie. Ezt a [beküldés lépésben](template-content-pack-testing.md#submission) fogja megtenni.

Tekintse át a [tartalomkészítés](template-content-pack-authoring.md) szakaszt, amelyben részletesebben olvashat a technikai követelményekről.

## <a name="business-scenario"></a>Vállalati forgatókönyv
A tartalomcsomagok egy adott üzleti forgatókönyvre fókuszáló elemzéseket és metrikákat biztosítanak. A célközönség és a tartalomcsomagok által nyújtott előnyök megismerésével biztosítható, hogy a felhasználók eredményesen használhatják a nekik készült tartalmakat.

### <a name="tips"></a>Tippek
* Azonosítsa a közönséget, és a feladatot, amelyet el szeretnének végezni.  
* Fókuszáljon egy adott időszakra (az elmúlt 90 nap) vagy az utolsó N számú eredményre.  
* Csak a forgatókönyvéhez kapcsolódó táblákat/oszlopokat importálja.  
* Fontolja meg több tartalomcsomag felajánlását különféle egyéni forgatókönyvekhez.  

## <a name="frequently-asked-questions"></a>Gyakori kérdések
**Létrehozhatok harmadik félként Power BI szolgáltatás-tartalomcsomagot olyan SaaS-alkalmazáshoz, amely nem az én tulajdonom?**

Jelenleg partnerszerződést kell aláírnia a SaaS-alkalmazás tulajdonosával, mielőtt közzétehetné a tartalomcsomagot a szolgáltatásban. Harmadik félként partnerszerződést kell kötnie a SaaS-alkalmazás tulajdonosával.

**Nem rendelkezem nyilvános fejlesztői API-val a szolgáltatásomhoz. Így is létrehozhatok olyan Power BI szolgáltatás-tartalomcsomagot, amely közvetlenül az adattárolóból kéri le az adatokat?**

Nem, a Power BI szolgáltatáshoz készült tartalomcsomagokhoz az interneten keresztül nyilvánosan elérhető fejlesztői API-ra van szükség.

**Milyen API-kat támogatnak a szolgáltatás-tartalomcsomagok, és milyen hitelesítéstípusokkal működnek?**

A Power BI szolgáltatás-tartalomcsomagok minden REST API-t és OData-csatornát támogatnak. A Power BI több hitelesítéstípussal is működik, mint például az alapszintű hitelesítés, az Oauth 2.0 és a Webes API-kulcs. A technikai követelményekről részletesebben a [tartalomkészítésről](template-content-pack-authoring.md#dashboard) szóló cikkben olvashat.

**Közzétettem egy tartalomcsomagot a Power BI-ban. Hogyan frissíthetem?**

A közzétett tartalomcsomagok havonta frissíthetők. A [pbiservicesapps@microsoft.com](mailto:pbiservicesapps@microsoft.com) címre az aktuális hónap utolsó napja előtt beküldött frissítési kérelmek a következő hónap első hetében lesznek közzétéve.

**További kérdéseim vannak a szolgáltatás-tartalomcsomagokkal kapcsolatban. Hogyan léphetek kapcsolatba Önökkel?**

Kérdéseit elküldheti a következő e-mail-címre: [pbiservicesapps@microsoft.com](mailto:pbiservicesapps@microsoft.com)

## <a name="support"></a>Támogatás
Ha a fejlesztési fázisban van szüksége támogatásra, használja a következő webhelyet: [https://powerbi.microsoft.com/support](https://powerbi.microsoft.com/support). Az ügyfélincidensek gyorsan eljutnak a megfelelő csapathoz.

## <a name="next-step"></a>Következő lépés
[Tartalomkészítés](template-content-pack-authoring.md)