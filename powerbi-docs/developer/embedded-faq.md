---
title: Gyakori kérdések – Power BI Embedded
description: Az alábbiakban a Power BI Embeddeddel kapcsolatos gyakori kérdések és válaszok listáját tekintheti át.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/05/2019
ms.openlocfilehash: 54d768e4d2ad1b2eab4559ee5d9db0705fb55542
ms.sourcegitcommit: 0abcbc7898463adfa6e50b348747256c4b94e360
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/06/2019
ms.locfileid: "55762651"
---
# <a name="frequently-asked-questions-about-power-bi-embedded"></a>Gyakori kérdések – Power BI Embedded

* Ha bármilyen egyéb kérdése van, [kérdezze meg a Power BI közösségét](http://community.powerbi.com/).
* Továbbra sem találja a megoldást? Keresse fel a [Power BI támogatási oldalát](https://powerbi.microsoft.com/support/).

## <a name="general"></a>Általános

### <a name="what-is-power-bi-embedded"></a>Mi az a Power BI Embedded?

A [Microsoft Power BI Embedded (PBIE)](azure-pbie-what-is-power-bi-embedded.md) használatával az alkalmazások fejlesztői lenyűgöző és teljes mértékben interaktív jelentéseket ágyazhatnak alkalmazásaikba, így nem kell időt és pénzt fordítaniuk arra, hogy az alapokról építsék fel saját adatvizualizációikat és vezérlőelemeiket.

### <a name="who-is-the-target-audience-for-power-bi-embedded"></a>Ki a Power BI Embedded célközönsége?

Az alkalmazásokat készítő fejlesztők és szoftvercégek, más néven a független szoftvergyártók (ISV-k).

### <a name="how-is-power-bi-embedded-different-from-power-bi-the-service"></a>Mi a különbség a Power BI Embedded és a Power BI szolgáltatás között?

A Power BI Embedded független szoftvergyártók vagy fejlesztők számára készült, akik alkalmazásokat készítenek és vizualizációkat ágyaznak be bennük, hogy ezzel segítsék ügyfeleik döntéseit, de ne kelljen az alapoktól kezdve elemzési megoldásokat létrehozniuk. A [beágyazott elemzések](embedding.md) használatával a vállalati felhasználók az alkalmazáson belül férhetnek hozzá a vállalati adataikhoz, és készíthetnek elemzéseket lekérdezések végrehajtásával.

A Power BI egy olyan elemzési szolgáltatottszoftver-megoldás, amely vállalatok számára teszi lehetővé a legfontosabb üzleti adataik egyszerű megtekintését.

### <a name="what-is-the-difference-between-power-bi-premium-and-power-bi-embedded"></a>Mi a különbség a Power BI Premium és a Power BI Embedded között?

A Power BI Premium-kapacitás azokat a nagyvállalatokat célozza meg, akik egy teljes körű Power BI-megoldást szeretnének, amellyel egyetlen helyről áttekinthetik vállalatukat, partnereiket, ügyfeleiket és szállítóikat. A Power BI Premium segítséget nyújt vállalata döntéshozatalaiban. A Power BI Premium egy szolgáltatottszoftver-termék, amely a Power BI portálon, a mobilalkalmazáson és belsőleg fejlesztett alkalmazásokon keresztül a felhasználók számára is lehetővé teszi a tartalmak használatát.

A Power BI Embedded független szoftvergyártók vagy fejlesztők számára készült, akik alkalmazásokat készítenek, és vizualizációkat ágyaznak be bennük. A Power BI Embedded az Ön ügyfelei számára nyújt segítséget a döntéshozatalaik során, ugyanis a Power BI Embedded alkalmazások fejlesztőinek készült, és ezeknek az alkalmazásoknak a vállalaton belüli és kívüli ügyfelei egyaránt használhatják a Power BI Embedded-kapacitásokban tárolt tartalmakat. A Power BI Embedded-kapacitástartalmak nem oszthatók meg egy kattintásos közzététellel a weben vagy a SharePointban, és nem támogatják az SSRS-jelentéseket sem.

### <a name="what-is-the-microsoft-recommendation-for-when-a-customer-should-buy-power-bi-premium-vs-power-bi-embedded"></a>A Microsoft javaslata alapján mikor érdemes megvásárolni a Power BI Premiumot, és mikor a Power BI Embeddedet?

A Microsoft ajánlása alapján a vállalatoknak a Power BI Premiumot érdemes megvásárolniuk, amely egy nagyvállalati szintű, felhőbeli önkiszolgáló BI-megoldás, a független szoftvergyártóknak pedig a Power BI Embeddedet érdemes megvásárolniuk, amely felhőalapú beágyazott elemzési összetevőket biztosít számukra. Azonban nincsenek korlátozások arra vonatkozóan, hogy ügyfeleink melyik terméket vásárolhatják meg.

Előfordulhatnak olyan esetek, amikor független szoftvergyártók (általában nagyobb méretűek) egy P termékváltozatot szeretnének használni, hogy kihasználhassák az előrecsomagolt Power BI szolgáltatás előnyeit a vállalatukon belül és az alkalmazásaikba ágyazva egyaránt. Egyes nagyvállalatok akkor is dönthetnek az Azure-beli A termékváltozatok használata mellet, ha csak az üzletági alkalmazások fejlesztése és az elemzési képességek beágyazása érdekli őket, és nem szeretnék az előrecsomagolt Power BI szolgáltatást használni.

### <a name="how-many-embed-tokens-can-i-create"></a>Hány beágyazási tokent hozhatok létre?

A PRO licenccel a beágyazási tokenek elsődlegesen fejlesztési tesztelésre használhatók, ezért a Power BI fő fiókja vagy a [szolgáltatásnév](embed-service-principal.md) csak korlátozott mennyiségű beágyazási tokent tud előállítani. Éles környezetben használt beágyazásokhoz [vásároljon kapacitást](#technical). Kapacitásvásárlás esetén nincs korlátja a beágyazási tokenek előállításának. Az [Elérhető szolgáltatások](https://docs.microsoft.com/rest/api/power-bi/availablefeatures) oldalon ellenőrizheti a használati értéket, amely százalékosan jelzi az aktuális beágyazott használatot.

## <a name="technical"></a>Műszaki

### <a name="what-is-the-difference-between-the-a-skus-in-azure-and-the-em-skus-in-office-365"></a>Mi a különbség az Azure-beli „A” termékváltozatok és az Office 365-beli „EM” termékváltozatok között?

A PowerBI.com egy vállalati megoldás, amely számos képességet kínál, többek között közösségi együttműködés lehetőségét és e-mailekre való feliratkozást. egy szoftverfrissítési szolgáltatásként

A Power BI Embedded egy fejlesztők számára készült API-gyűjtemény, amellyel platformszolgáltatásokba ágyazhatnak be elemzési megoldásokat. A beágyazott elemzések forgatókönyve esetén a PowerBI.com segítséget nyújt a független szoftvergyártóknak és a fejlesztőknek a beágyazott elemzési megoldásaik tartalmainak és a bérlői beállításaiknak a kezeléséhez.

Itt látható egy részlet a különbségek listájából, amely mindkét megoldás esetén hasznos lehet.

| Funkció | Power BI Embedded | Power BI Premium-kapacitás | Power BI Premium-kapacitás |
|----------------------------------------------------------------------------------|-------------------|---------------------------|---------------------------|
|   | (A termékváltozatok) | (EM termékváltozatok) | (P termékváltozatok) |
| Összetevők beágyazása Power BI alkalmazás munkaterületeiről | Azure-kapacitás | Office 365-kapacitás | Office 365-kapacitás |
| Power BI-jelentések használata Embedded-alkalmazásokban | Igen | Igen | Igen |
| Power BI-jelentések használata SharePointban | Nem | Igen | Igen |
| Power BI-jelentések használata Dynamicsben | Nem | Igen | Igen |
| Power BI-jelentések használata Teamsben (a mobil alkalmazás kivételével) | Nem | Igen | Igen |
| Hozzáférés a tartalomhoz INGYENES Power BI-licenccel a Powerbi.com oldalon és a Power BI Mobile-on | Nem | Nem | Igen |
| Hozzáférés a tartalomhoz INGYENES, MS Office-alkalmazásokba beágyazott Power BI-licenccel | Nem | Igen | Igen |

### <a name="power-bi-now-offers-three-skus-for-embedding-a-skus-em-skus-and-p-skus-which-one-should-i-purchase-for-my-scenario"></a>A Power BI három típusú termékváltozatot kínál a beágyazásra: az A termékváltozatokat, az EM termékváltozatokat és a P termékváltozatokat. Melyiket vásároljam meg a saját forgatókönyvemhez?

|  |A termékváltozat (Power BI Embedded)  |EM termékváltozat (Power BI Premium)  |P termékváltozat (Power BI Premium)  |
|---------|---------|---------|---------|
|Vásárlás  |Azure Portal |Office |Office |
|Felhasználási módok | Tartalmak beágyazása saját alkalmazásba | <li> Tartalmak beágyazása saját alkalmazásba <br><br></br> <li> Tartalmak beágyazása MS Office-alkalmazásokba: <br> - [SharePoint](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/) <br> - [Teams (a mobilalkalmazás kivételével)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) <br> - [Dynamics 365](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard) | <li> Tartalmak beágyazása saját alkalmazásba <br><br></br> <li> Tartalmak beágyazása MS Office-alkalmazásokba: <br> - [SharePoint](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/) <br> - [Teams (a mobilalkalmazás kivételével)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) <br> - [Dynamics 365](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard) <br><br></br> <li> Tartalom megosztása Power BI-felhasználókkal a [Power BI szolgáltatásban](https://powerbi.microsoft.com/)  |
|Számlázás |Óránként |Havonta |Havonta |
|Kötelezettségvállalás  |Nincs kötelezettségvállalás |Éves  |Havi/Éves |
|Megkülönböztetés |Az Azure Portalon vagy API-kon keresztül teljes mértékű rugalmasságot tesz lehetővé, vagyis felfelé és lefelé történő méretezhetőséget, illetve az erőforrások felfüggesztését és folytatását  |Tartalmak beágyazására használható a SharePoint Online-ban és a Microsoft Teamsben (a mobilalkalmazás kivételével) |Egy kapacitáson belül egyesíti az alkalmazásokba történő beágyazásokat és a Power BI szolgáltatás használatát |

### <a name="what-are-the-prerequisites-to-create-a-pbie-capacity-in-azure"></a>Milyen feltételekkel hozható létre PBIE-kapacitás az Azure-ban?

* Jelentkezzen be a vállalati címtárba (MSA-fiókok nincsenek támogatva).
* Power BI-bérlővel kell rendelkeznie, azaz a címtár legalább egy felhasználójának regisztrálva kell lennie a Power BI-ban. 
* A vállalati címtárban szerepelnie kell egy Azure-előfizetésnek.

### <a name="how-can-i-monitor-power-bi-embedded-capacity-consumption"></a>Hogyan figyelhetem meg a Power BI Embedded kapacitásfogyasztását?

* [A Power BI felügyeleti portál](../service-admin-portal.md#power-bi-embedded) használata.

* A [metrikai alkalmazás](https://review.docs.microsoft.com/power-bi/service-admin-premium-monitor-capacity) letöltése a Power BI-ban.

* Az [Azure-beli diagnosztikai naplózás](azure-pbie-diag-logs.md) használata.

### <a name="can-my-capacity-scale-automatically-to-adjust-to-the-consumption-of-my-app"></a>Méretezi magát a kapacitásom automatikusan, hogy igazodjon az alkalmazásom felhasználásához?

Jelenleg nincs automatikus méretezés, ugyanakkor bármikor bármelyik API méretezhető.

### <a name="why-creatingscalingresuming-a-capacity-results-in-putting-the-capacity-into-a-suspended-state"></a>Miért módosítja a kapacitás létrehozása/méretezése/folytatása a kapacitás állapotát felfüggesztettre?

A kapacitás kiépítése (méretezés/folytatás/létrehozás) sikertelen lehet. A kiépítési hívás hívójának ellenőriznie kell a kapacitás ProvisioningState tulajdonságát a Részletek beolvasása API-val: [Kapacitások – Részletek beolvasása](https://docs.microsoft.com/rest/api/power-bi-embedded/capacities/getdetails).

### <a name="can-i-only-create-power-bi-embedded-capacities-in-a-specific-region"></a>Csak egy megadott régióban tudok Power BI Embedded-kapacitásokat létrehozni?

A [Multi-Geo (előzetes verzió)](embedded-multi-geo.md) funkcióval a saját Power BI-bérlője helyétől eltérő régióban is vásárolhat [Power BI Embedded-kapacitást](azure-pbie-create-capacity.md).

### <a name="how-can-i-find-what-is-my-pbi-tenant-region"></a>Hogyan találhatom meg a PBI-bérlőm régióját?

A PBI-portál használatával megtudhatja, melyik régió a PBI-bérlőjének régiója.

[https://app.powerbi.com/](https://app.powerbi.com/) > ? > A Power BI bemutatása

![A Power BI bemutatása](media/embedded-faq/about-01.png)
![Bérlői régió](media/embedded-faq/tenant-location-01.png)

### <a name="what-is-supported-by-the-cloud-solution-provider-csp-channel"></a>Mi támogatott a Cloud Solution Provider (CSP) csatornával?

* A CSP előfizetési típusú bérlőjéhez létrehozhat PBIE-t
* A partnerfiók bejelentkezhet az ügyfélbérlőbe, vásárolhat PBIE-t az ügyfélbérlőhöz, és meghatározhatja az ügyfélbérlő felhasználóját a Power BI-kapacitás rendszergazdájaként

### <a name="why-do-i-get-an-unsupported-account-message"></a>Miért kapok „nem támogatott fiók” üzenetet?

A Power BI megköveteli, hogy céges fiókkal jelentkezzen be. A Power BI-ra MSA-val (Microsoft-fiókkal) történő regisztráció nem támogatott.

### <a name="can-i-use-apis-to-create--manage-azure-capacities"></a>Használhatok API-kat Azure-képességek létrehozására és kezelésére?

Igen, vannak PowerShell-parancsmagok és Azure Resource Manager API-k, amelyeket használhat PBIE-erőforrások létrehozására és kezelésére.

* REST API-k – https://docs.microsoft.com/rest/api/power-bi-embedded/
* PowerShell-parancsmagok – https://docs.microsoft.com/powershell/module/azurerm.powerbiembedded/

### <a name="what-is-the-pbi-embedded-dedicated-capacity-role-in-a-pbi-embedded-solution"></a>Mi az a PBI Embedded elkülönített kapacitási szerepkör a PBI Embedded megoldásban?

Annak érdekében, hogy a [megoldást elő lehessen léptetni az éles környezetbe](https://docs.microsoft.com/power-bi/developer/embedding-content#step-3-promote-your-solution-to-production), szükséges, hogy a Power BI-tartalom (az alkalmazásban használt alkalmazás-munkaterület) hozzá legyen rendelve egy Power BI Embedded- (A termékváltozat) kapacitáshoz.

### <a name="what-are-the-azure-regions-pbi-embedded-is-available"></a>Mely Azure-régiókban érhető el a PBI Embedded?

[PAM](https://ecosystemmanager.azurewebsites.net/home) (EcoManager) – lásd termékrendelkezésre állás-kezelő

Elérhető régiók (16 – ugyanazok a régiók, mint a Power BI-ban)

* US (6) – USA keleti régiója, USA 2. keleti régiója, USA északi középső régiója, USA déli középső régiója, USA nyugati régiója, USA 2. nyugati régiója
* Európa (2) – Észak-Európa, Nyugat-Európa
* Ázsia és a Csendes-óceáni térség (2) – Délkelet-Ázsia, Kelet-Ázsia
* Brazília (1) – Dél-Brazília
* Japán (1) – Kelet-Japán
* Ausztrália (1) – Délkelet-Ausztrália
* India (1) Nyugat-India
* Kanada (1) – Közép-Kanada
* Egyesült Királyság (1) Egyesült Királyság déli régiója

### <a name="what-is-the-authentication-model-for-power-bi-embedded"></a>Milyen hitelesítési modellt használ a Power BI Embedded?

A Power BI Embedded továbbra is az Azure AD használatával hitelesíti a fő felhasználót (a Power BI Pro-licenccel rendelkező kijelölt felhasználót), vagy [szolgáltatásnevet](embed-service-principal.md) használ a Power BI-ban található alkalmazás hitelesítéséhez.  

Az alkalmazások felhasználóinak hitelesítését és engedélyezését a független szoftvergyártó implementálja, így a független szoftvergyártók használhatnak saját hitelesítést az alkalmazásaikban.

Ha már rendelkezik egy Azure AD-bérlővel, akkor használhatja meglévő címtárát, vagy létrehozhat egy új Azure AD-bérlőt a beágyazott alkalmazásai tartalmainak biztonságához.

AAD-token beszerzéséhez használhatja az [Azure Active Directory valamely hitelesítési kódtárát](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries). Ügyfélkódtárak több platformhoz is elérhetőek.

### <a name="my-application-already-uses-aad-for-user-authentication-how-can-we-use-this-identity-when-authenticating-to-power-bi-in-a-user-owns-data-scenario"></a>Az alkalmazásom már AAD-t használ a felhasználói hitelesítéshez. Hogyan használhatjuk ezt az identitást, a „Felhasználó az adatok tulajdonosa” forgatókönyvek esetében a Power BI-ban való hitelesítésekor?

Ez egy szokásos, más nevében történő OAuth-hitelesítési folyamat (https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#web-application-to-web-api) Az alkalmazást úgy kell konfigurálni, hogy engedélyt kérjen a Power BI szolgáltatáshoz (a szükséges hatókörökkel), és ha már rendelkezik felhasználói tokennel az alkalmazáshoz, egyszerűen csak hívnia kell az ADAL API AcquireTokenAsync metódust a felhasználói hozzáférési tokennel, és meg kell adnia a Power BI-erőforrás URL-címét erőforrás-azonosítóként. Tekintse át az alábbi kódrészletet, amely bemutatja ennek módját:

```csharp
var context = new AD.AuthenticationContext(authorityUrl);
var userAssertion = new AD.UserAssertion(userAccessToken);
var clientAssertion = new AD.ClientAssertionCertificate(MyAppId, MyAppCertificate)
var authenticationResult = await context.AcquireTokenAsync(resourceId, clientAssertion, userAssertion);
```

### <a name="how-is-power-bi-embedded-different-from-other-azure-services"></a>Miben különbözik a Power BI Embedded más Azure-szolgáltatásoktól?

A független szoftvergyártónak vagy a fejlesztőnek rendelkeznie kell egy Power BI-fiókkal, mielőtt az Azure-ban megvásárolná a Power BI Embeddedet. A Power BI Embedded üzembe helyezési régiója határozza meg a Power BI-fiókját. A Power BI Embedded-kapacitását az Azure-ban kezelheti:

* Méretezheti felfelé vagy lefelé
* Felvehet kapacitás-rendszergazdákat
* Szüneteltethet és folytathat szolgáltatásokat

A PowerBI.com használatával munkaterületeket rendelhet a Power BI Embedded-kapacitásához, vagy megszüntetheti a hozzárendeléseket.

### <a name="what-deploy-regions-are-supported"></a>Mely üzembe helyezési régiók támogatottak?

Délkelet-Ausztrália, Dél-Brazília, Közép-Kanada, USA 2. keleti régiója, Nyugat-India, Kelet-Japán, USA északi középső régiója, Észak-Európa, USA déli középső régiója, Délkelet-Ázsia, Egyesült Királyság déli régiója, Nyugat-Európa, az USA nyugati régiója és az USA 2. nyugati régiója.

### <a name="what-type-of-content-pack-data-can-be-embedded"></a>Milyen típusú tartalomcsomagot lehet beágyazni?

A tartalomcsomagok adathalmazaiból készült **irányítópultokat** és **csempéket** *nem lehet beágyazni*, a tartalomcsomagok adathalmazaiból készült **jelentések** viszont *beágyazhatók*.

### <a name="what-is-the-difference-between-using-rls-vs-javascript-filters"></a>Mi a különbség az RLS- és a JavaScript-szűrők használata között?

Gyakran van keveredés akörül, mikor érdemes használni az RLS-, és mikor a JavaScript a szűrőket, mert az egyik módszer azt szabályozza, hogy mit láthat a megadott felhasználó, a másik pedig a felhasználói nézet optimalizálása.

Az RLS-nél a független szoftverszállító szabályozza az adatszűrést a modell létrehozásának és a beágyazott token generálásának részeként. A végfelhasználó csak azt látja, amit a független szoftverszállító engedélyez a számára. Ebben az esetben a felhasználó dönthet úgy, hogy kevesebb adatot jelenít meg, mint amennyi a szűrővel látható, de nem tudja megkerülni az RLS-konfigurációt, és a megengedettnél több adatot nem tud megjeleníteni.

Az ügyféloldali szűrés (JavaScript) alkalmazásakor a független szoftverszállító meghatározhatja, mit láthat a végfelhasználó a kezdeti nézetben, de nem szabályozhatja, hogy a végfelhasználó milyen módosításokat alkalmazhat magára a nézetre. Bár lehetséges adatszűrés a háttéralkalmazásban, ezt a JavaScript-ügyfélkód váltja ki, ezért a végfelhasználó módosíthatja, és nem tekinthető biztonságosnak.

További részletekért lásd [Az RLS- és a JavaScript-szűrők összehasonlítása](embedded-row-level-security.md#using-rls-vs-javascript-filters) szakaszt.

### <a name="how-do-i-manage-permissions-for-service-principals-with-power-bi"></a>Hogyan kezelhetem az engedélyeket a szolgáltatásnevekhez a Power BI-jal?

Ha engedélyezi a [szolgáltatásnevek](embed-service-principal.md) használatát a Power BI-ban, az alkalmazás AD-engedélyei többé nem lesznek érvényesek. Az alkalmazás engedélyeit ekkor a Power BI felügyeleti portálján lehet kezelni.

A szolgáltatásnevek a biztonsági csoportjukból öröklik az engedélyeket a Power BI összes bérlői beállításához. Az engedélyek korlátozásához hozzon létre egy külön biztonsági csoportot a szolgáltatásneveknek, majd adja hozzá az Egyes biztonsági csoportok kivételével listához a vonatkozó, engedélyezett Power BI-beállítások esetében.

Ennek akkor van jelentősége, amikor **rendszergazdaként** felveszi a szolgáltatásnevet az új munkaterületre. Ezt a feladatot kezelheti az [API-kon](https://docs.microsoft.com/rest/api/power-bi/groups/addgroupuser) keresztül vagy a Power BI szolgáltatásban.

### <a name="when-to-use-an-application-id-vs-a-service-principal-object-id"></a>Mikor érdemes alkalmazásazonosítót használni a szolgáltatásnév objektumazonosítója helyett?

Az **[alkalmazásazonosító](embed-sample-for-customers.md#application-id)** a hozzáférési jogkivonat létrehozására szolgál az alkalmazásazonosító hitelesítés céljából történő átadásakor.

A műveletek végrehajtásakor egy szolgáltatásnévre történő hivatkozáshoz vagy módosítások végzéséhez a **[szolgáltatásnév objektumazonosítóját](embed-service-principal.md#how-to-get-the-service-principal-object-id)** használja, például úgy, hogy a szolgáltatásnevet adminisztrátorként alkalmazza a munkaterületre.

### <a name="can-you-manage-an-on-premises-data-gateway-with-service-principal"></a>Kezelheti az helyszíni adatátjárót szolgáltatásnévvel?

Helyszíni adatátjárót (adatátjárót) nem kezelheti ugyanúgy a [szolgáltatásnévvel](embed-service-principal.md), ahogyan azt a fő fiókkal teheti.

Fő fiókkal telepíthet adatátjárót, hozzáadhat felhasználókat az átjáróhoz, csatlakozhat adatforráshoz, és elvégezhet egyéb felügyeleti feladatokat.

Szolgáltatásnévvel konfigurálhat [sorszintű biztonságot (RLS-t)](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal-preview) az SQL Server Analysis Services (SSAS) helyszíni, élő kapcsolattal rendelkező adatforrásával. Így kezelheti a felhasználókat és az adatelérésüket az SSAS-ben a **Power BI Embedded** szolgáltatásnévvel létrehozott integrációjakor.

### <a name="can-you-sign-into-the-power-bi-service-with-service-principal"></a>Bejelentkezhet a Power BI szolgáltatásba szolgáltatásnévvel?

Nem, a Power BI-ba szolgáltatásnévvel nem lehet bejelentkezni.

Emellett nem használhat fel tartalmat felhasználóként külső alkalmazásokban (SaaS-beágyazás), csak akkor, ha létrehoz egy beágyazási tokent.

### <a name="what-are-the-best-practices-to-improve-performance"></a>Mik a teljesítmény növelése érdekében ajánlott eljárások?

[A Power BI Embedded teljesítménye](embedded-performance-best-practices.md)

## <a name="licensing"></a>Licencelés

### <a name="how-do-i-purchase-power-bi-embedded"></a>Hogyan tudom megvásárolni a Power BI Embeddedet?

A Power BI Embedded az Azure-on keresztül érhető el.

### <a name="what-happens-if-i-already-purchased-power-bi-premium-and-now-i-want-some-of-the-benefits-of-power-bi-embedded-in-azure"></a>Mi történik akkor, ha már megvásároltam a Power BI Premiumot és szeretném használni az Azure-beli Power BI Embedded néhány előnyös funkcióját?

Az ügyfelek továbbra is fizetnek a megvásárolt Power BI Premiumukért az aktuális megállapodásuk szerinti időszak végéig, ezt követően igényeik szerint válthatnak a megvásárolt Power BI Premiumukról.

### <a name="do-i-still-have-to-buy-power-bi-premium-to-get-access-to-power-bi-embedded"></a>Meg kell vásárolnom a Power BI Premiumot, hogy hozzáférhessek a Power BI Embeddedhez?

Nem, a Power BI Embedded magában foglalja a megoldásainak üzembe helyezéséhez és terjesztéséhez szükséges Azure-alapú kapacitást.

### <a name="whats-the-purchase-commitment-for-power-bi-embedded"></a>Milyen kötelezettségeket kell vállalni a Power BI Embedded megvásárlásakor?

Ügyfeleink a használatukat óránként módosíthatják. A Power BI Embedded szolgáltatás esetén nincs havi vagy éves kötelezettségvállalás.

### <a name="how-does-the-usage-of-power-bi-embedded-show-up-on-my-bill"></a>Hogyan jelenik meg a Power BI Embedded használata a számlámon?

A Power BI Embedded költségeinek számlázása könnyen előrejelezhető módon, óránként történik az üzembe helyezett csomópont(ok) típusa alapján. Ha az erőforrása aktív, akkor is díjat számolunk fel, ha nem történik tényleges használat. Ha nem szeretne díjat fizetni, akkor az erőforrást kifejezetten szüneteltetnie kell.

### <a name="who-needs-a-power-bi-pro-license-for-power-bi-embedded-and-why"></a>Kinek van szüksége a Power BI Embeddedhez Power BI Pro-licencre, és miért?

Azoknak a fejlesztőknek, akiknek szükségük van a REST API-k használatára, Power BI Pro-licenccel vagy [szolgáltatásnévvel](embed-service-principal.md) kell rendelkezniük. Azoknak az elemzőknek, akiknek jelentéseket kell hozzáadniuk egy Power BI-munkaterülethez, Power BI-licenccel kell rendelkezniük, vagy szolgáltatásnevet kell használniuk. Azoknak a bérlői rendszergazdáknak, akiknek a Power BI-bérlőt és -kapacitást kell kezelniük, Power BI Pro-licenccel kell rendelkezniük.

A Power BI Embedded a beágyazott tartalmak jóváhagyása és kezelése céljából engedélyezi a Power BI-portál használatát, ezért a PowerBI.com-on belül található alkalmazás hitelesítéséhez Power BI Pro-licenc szükséges, hogy az alkalmazás hozzáférhessen a megfelelő adattárakban található jelentésekhez.

A [beágyazott jelentések létrehozásához/szerkesztéséhez](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Create-Report-in-Embed-View) a saját alkalmazásán belül a végfelhasználónak mégsem kell Pro-licenccel rendelkeznie, mivel nem követelmény, hogy Power BI-felhasználó legyen.

### <a name="can-i-get-started-for-free"></a>Elkezdhetem ingyen a használatát?

Igen, használhatja az [Azure-kreditjeit](https://azure.microsoft.com/free/) a Power BI Embeddedhez.

### <a name="can-i-get-a-trial-experience-for-power-bi-embedded-in-azure"></a>Van lehetőség az Azure-beli Power BI Embedded kipróbálására?

Mivel a Power BI Embedded az Azure része, így használhatja ezt a szolgáltatást az [Azure-regisztráció során kapott 200 USD értékű kreditjéből](https://azure.microsoft.com/free/).

### <a name="is-power-bi-embedded-available-for-sovereign-clouds-us-government-germany-china"></a>Elérhető a Power BI Embedded a szuverén felhőkben (US Government, Németország, Kína)?

A Power BI Embedded csak bizonyos [szuverén felhőkben](embed-sample-for-customers-sovereign-clouds.md) érhető el. A kínai felhőben **nem**.

### <a name="is-power-bi-embedded-available-for-non-profits-and-educational"></a>Létezik non-profit vagy oktatási intézményeknek szánt Power BI Embedded?

A non-profit és oktatási intézmények megvásárolhatják az Azure-t. Nincs az Azure-ban különleges díjszabásunk az ilyen típusú ügyfeleink számára.

## <a name="power-bi-workspace-collection"></a>Power BI-munkaterületcsoport

### <a name="what-is-power-bi-workspace-collection"></a>Mi a Power BI-munkaterületcsoport?

A **Power BI-munkaterület-csoport** (a **Power BI Embedded** 1 verziója) egy olyan megoldás, amely a **Power BI-munkaterületcsoport** nevű Azure-erőforráson alapul. Ez a megoldás **Power BI Embedded**-alkalmazások létrehozását teszi lehetővé az ügyfelek részére a **Power BI-munkaterületcsoporton** belüli Power BI tartalmak, megoldások és dedikált API-k segítségével, valamint munkaterületcsoport-kulcsokkal az alkalmazás Power BI-ban történő hitelesítéséhez.

### <a name="can-i-migrate-from-power-bi-workspace-collection-to-power-bi-embedded"></a>Áttelepíthetem-e a Power BI-munkaterületcsoport tartalmait a Power BI Embeddedbe?

1. Az áttelepítési eszközzel klónozhatja a **Power BI-munkaterületcsoport** tartalmát a Power BI-ba – https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded#content-migration.

2. Kezdje a Power BI-tartalmakat használó **Power BI Embedded** kísérleti (POC) alkalmazással.

3. Ha készen áll a munkára, szerezzen be dedikált kapacitást a **Power BI Embedded** használatához, és rendelje hozzá a saját Power BI-tartalmat (munkaállomást).

    > [!Note]
    > Miközben párhuzamosan létrehozza a **Power BI Embedded** megoldást, tovább használhatja a **Power BI-munkaterületcsoportot** is. Miután elkészült, áttelepítheti az ügyfelet az új **Power BI Embedded** megoldásba, majd kivezetheti a **Power BI-munkaterületcsoportot**.

További információkért lásd: [Power BI-munkaterületcsoport tartalmainak áttelepítése a Power BI Embeddedbe](https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded)

### <a name="is-power-bi-workspace-collection-on-a-path-to-be-deprecated"></a>Nemsokára elavul a Power BI-munkaterületcsoport?

Igen, de a  **Power BI-munkaterületcsoport** meglévő felhasználói tovább használhatják azt az elavulás időpontjáig. Az ügyfelek egyaránt létrehozhatnak új munkaterületcsoportokat és **Power BI-munkaterületcsoportot** még használó **Power BI Embedded**-alkalmazásokat is.

Ez azonban azzal jár, hogy a **Power BI-munkaterületcsoportokban** már nem jelennek meg új funkciók, és az ügyfeleknek érdemes lesz megtervezni a tartalmak áttelepítését a **Power BI Embedded** megoldásba.

### <a name="when-is-power-bi-workspace-collection-support-discontinued"></a>Mikor szűnik meg a Power BI-munkaterületcsoport támogatása?

A **Power BI-munkaterületcsoportot** használó ügyfelek 2018 június végéig, vagy a támogatási szerződésük lejártáig folytathatják a használatot.

### <a name="in-what-regions-can-pbi-workspace-collection-be-created"></a>Mely régiókban hozható létre a PBI-munkaterületcsoport?

Az elérhető régiók Délkelet-Ausztrália, Dél-Brazília, Közép-Kanada, az USA 2. keleti régiója, Kelet-Japán, az USA északi középső régiója, Észak-Európa, az USA déli középső régiója, Délkelet-Ázsia, az Egyesült Királyság déli régiója, Nyugat-Európa, Nyugat-India és az USA nyugati régiója.

### <a name="why-should-i-migrate-from-pbi-workspace-collection-to-power-bi-embedded"></a>Miért kell áttelepítenem a PBI-munkaterületcsoportot a Power BI Embeddedbe?

A **Power BI Embedded** megoldás rendelkezik néhány olyan új funkcióval és képességgel, amelyek a **Power BI-munkaterületcsoportban** nem valósíthatók meg.

Néhány ilyen funkció:

* A PBI esetében minden adatforrás támogatott, szemben a **Power BI-munkaterületcsoport** két adatforrásával. 
* Számos új funkció, köztük a Q&A, a Frissítés, a könyvjelzők, az irányítópultok és csempék beágyazása és az egyéni menü csak a **Power BI Embedded** megoldásban van támogatva.
* Kapacitás-számlázási modell.

## <a name="embedding-setup-tool"></a>Beágyazáshoz szükséges telepítési eszköz

### <a name="what-is-the-embedding-setup-tool"></a>Mi a beágyazáshoz szükséges telepítési eszköz?

A [beágyazáshoz szükséges telepítési eszköz](https://aka.ms/embedsetup) használatával egyszerűen elvégezheti az első lépéseket, és letölthet egy mintaalkalmazást, amellyel elkezdheti a beágyazást a Power BI-jal.

### <a name="which-solution-should-i-choose"></a>Melyik megoldást válasszam?

* A [Beágyazás az ügyfelek számára](embedding.md#embedding-for-your-customers) használatával irányítópultokat és jelentéseket ágyazhat be olyan felhasználók számára, akik nem rendelkeznek Power BI-fiókkal. Futtassa a [Beágyazás az ügyfelek számára](https://aka.ms/embedsetup/AppOwnsData) megoldást.
* A [Beágyazás a cég számra](embedding.md#embedding-for-your-organization) használatával kiterjesztheti a Power BI szolgáltatást. Futtassa a [Beágyazás a cég számára](https://aka.ms/embedsetup/UserOwnsData) megoldást.

### <a name="ive-downloaded-the-sample-app-which-solution-do-i-choose"></a>Letöltöttem a mintaalkalmazást. Melyik megoldást válasszam?

A **Beágyazás az ügyfelek számára** használatához mentse és csomagolja ki a *PowerBI-Developer-Samples.zip* fájlt. Nyissa meg a *PowerBI-Developer-Samples-master\App Owns Data* mappát, majd futtassa a *PowerBIEmbedded_AppOwnsData.sln* fájlt.

A **Beágyazás a cég számára** használatához mentse és csomagolja ki a *PowerBI-Developer-Samples.zip* fájlt. Nyissa meg a *PowerBI-Developer-Samples-master\User Owns Data\integrate-report-web-app* mappát, és futtassa a *pbi-saas-embed-report.sln* fájlt.

### <a name="how-can-i-edit-my-registered-application"></a>Hogyan szerkeszthetem a regisztrált alkalmazásomat?

Az AAD-ben regisztrált alkalmazások szerkesztéséről [itt](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications#updating-an-application) olvashat.

### <a name="how-can-i-edit-my-power-bi-user-profile-or-data"></a>Hogyan szerkeszthetem a Power BI-felhasználói profilt vagy adatokat?

A Power BI-adatok szerkesztéséről [itt](https://docs.microsoft.com/power-bi/service-basic-concepts) olvashat.

További információ: [A beágyazott alkalmazás hibaelhárítása](embedded-troubleshoot.md).

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)