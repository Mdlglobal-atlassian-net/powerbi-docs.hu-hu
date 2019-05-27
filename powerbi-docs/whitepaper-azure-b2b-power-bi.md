---
title: Külső vendégfelhasználóknak az Azure Active Directory B2B használatával a Power BI-tartalom terjesztése
description: Tanulmány, amely leírja a Power BI terjesztése külső vendégfelhasználóknak az Azure Active Directory B2B használatával
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/07/2019
ms.author: davidi
LocalizationGroup: Conceptual
ms.openlocfilehash: 79b8ae80413cc54b065d12bf36ccb1651a670812
ms.sourcegitcommit: ec5b6a9f87bc098a85c0f4607ca7f6e2287df1f5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66051604"
---
# <a name="distribute-power-bi-content-to-external-guest-users-using-azure-active-directory-b2b"></a>Külső vendégfelhasználóknak az Azure Active Directory B2B használatával a Power BI-tartalom terjesztése

**Összefoglalás:** Ez az egy technikai tanulmány, megtudhatja, hogyan terjesztheti a tartalmat az Azure Active Directory-vállalatok (Azure AD B2B) integrációjával cégen kívüli felhasználóknak.

**Írók:** Lukasz Pawlowski, Kasper de Jonge

**Műszaki véleményezők:** ADAM Wilson, Sheng Liu, Qian Liang, Sergei Gundorov, Jacob Grimm, Adam Saxton, a Maya alkalmazáshoz Shenhav, Nimrod Shalit, Elisabeth Olson

> [!NOTE]
> A tanulmányt a böngésző **Nyomtatás** > **Mentés PDF-ként** lehetőségével mentheti vagy kinyomtathatja.

## <a name="introduction"></a>Bevezetés

A Power BI révén a szervezetek üzleti 360 fokos nézetével, és ezen adatok segítségével intelligens döntéseket szervezetek szolgálatában. A legtöbb szervezetek rendelkezik, a külső partnerek, ügyfelek és alvállalkozók erős és megbízható kapcsolatokat. Ezek a szervezetek kell adnia a biztonságos hozzáférés a Power BI-irányítópultok és jelentések ezek a külső partnerek a felhasználók számára.

A Power BI integrálható az [Azure Active Directory-vállalatok (Azure AD B2B)](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b) való biztonságos elosztását a Power BI tartalmak a szervezet – kívüli vendégfelhasználókkal engedélyezése közben továbbra is az irányítás és szabályozzák a hozzáférést belső adatok.

Ez a tanulmány bemutatja az összes részletet a Power BI-integráció az Azure Active Directory B2B ismernie kell. Bemutatjuk, hogy a leggyakoribb használati eset, a telepítő, licencek és sorszintű biztonság.

> [!NOTE]
> Során ez a tanulmány azt tekintse meg az Azure ad-ben, az Azure Active Directory és az Azure Active Directory vállalatközi, az Azure AD B2B.

## <a name="scenarios"></a>Forgatókönyvek

Contoso-autógyártás gyártó, és együttműködik számos különböző szállítók, akik bocsátania az összetevők, anyagokat és a gyártási műveletek végrehajtásához szükséges szolgáltatásokat. A Contoso biztosítani szeretné az ellátási lánc logisztikai és a terveket ellenőrizhet fontos teljesítménymutatókat, az ellátási lánc a Power BI segítségével leegyszerűsíthető. A Contoso biztosítani szeretné megosztása külső ellátási lánc partnerek elemzési, biztonságos és kezelhető.

Contoso engedélyezheti a következő funkciókat a Power BI és az Azure AD B2B használatával külső felhasználók számára.

### <a name="ad-hoc-per-item-sharing"></a>Ad hoc / elem megosztása

Contoso működik együtt a szállító, aki a Contoso autók radiátor épít. Gyakran előfordul szükségük az összes Contoso autókból származó radiátor megbízhatóságának optimalizálása érdekében. Az elemzőknek contoso Power BI használatával egy szakértővel, a nyertes fűtőtest megbízhatósági jelentés megosztása. A visszafejtés kap egy e-mailt, egy hivatkozás a jelentés megtekintéséhez.

Üzleti felhasználók szükség szerint alapon e ad hoc megosztása végzi a fentiekben ismertetettek szerint. A kapcsolat, a külső felhasználó a Power BI által küldött egy Azure AD B2B meghívás hivatkozását. A külső felhasználó a hivatkozás megnyílik, amikor a rendszer megkéri, a Contoso Azure ad-ben szervezet meg vendégként csatlakozni. A meghívó elfogadása után a hivatkozás megnyílik az adott jelentés vagy irányítópult. Külső felhasználók a szervezet meghívása engedélyt ad az Azure Active Directory-rendszergazda, és úgy dönt, hogy ezek a felhasználók mit tehetnek Amint elfogadják a meghívó a Cégirányítási szakasz ebben a dokumentumban leírtak szerint. A Contoso elemző meghívhatja a meghívott felhasználónak csak, mert az Azure AD-rendszergazda engedélyezett, a művelet és a Power BI rendszergazdai engedélyezett felhasználók meghívhatnak vendégeket tartalom megtekintése a Power BI bérlői beállításokat.

![A Power BI AAD-vendégek meghívása](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_01.png)

1. A folyamat egy belső Contoso-felhasználó, egy irányítópult vagy jelentés megosztása külső felhasználóval kezdődik. A külső felhasználó még nem a Vendég a Contoso Azure AD-ben meghívást kaptak. E-mailt küldeni az e-mail-címükkel, amely tartalmazza a meghívót a Contoso Azure AD
2. A címzett elfogadja a meghívást, a Contoso Azure ad, és hozzá Vendég felhasználóként a Contoso Azure AD.
3. A címzett ezután rendszer átirányítja a Power BI-irányítópultot, jelentést vagy alkalmazást, amely a felhasználó csak olvashatók.

A folyamat ad hoc számít, mivel az üzleti felhasználók a Contoso az üzleti célú igény szerint meghívó művelet végrehajtása. Minden elem megosztott használ, egy hivatkozás a külső felhasználó hozzáférhessen a tartalom megtekintéséhez.

Contoso erőforrások eléréséhez a külső felhasználó kapott meghívót, miután egy árnyékmásolat-fiókot hozhat létre számára azokat a Contoso Azure AD, és nem kell újra lehet meghívni.  Az első alkalommal próbál hozzáférni a Power BI-irányítópulton, például a Contoso erőforrás, próbálja ki egy hozzájárulási folyamat, amely a meghívó visszaváltja.  Ezek nem fejeződnek be a jóváhagyás, ha azok nem fér hozzá egyik Contoso-tartalom.  Ha hiba történt a meghívót keresztül megadott eredeti hivatkozás váltja be rendelkeznek, Azure AD-rendszergazda beváltásához, hogy egy adott meghívó hivatkozást is elküldésével.

### <a name="planned-per-item-sharing"></a>Tervezett / elem megosztása

Contoso megbízhatóság elemzését, radiátor alvállalkozó együttműködik. Az alvállalkozónak 10 személyek, akik hozzáférhetnek az adatokhoz a Power BI-környezetbe a Contoso csapata rendelkezik. A Contoso Azure AD-rendszergazda az érintett összes felhasználó meghívása, és bármely hozzáadások vagy a változtatásokat a elszámoltathatóságának módosításakor személyzet kezelését. Az Azure AD-rendszergazda alvállalkozó lévő összes alkalmazott egy biztonsági csoportot hoz létre. A biztonsági csoport használatával, a Contoso-alkalmazott egyszerűen jelentésekhez való hozzáférés kezelése, és biztosítani a munkatársak szükséges elszámoltathatóságának fér hozzá a szükséges jelentések, irányítópultok és a Power BI-alkalmazások. Az Azure AD-rendszergazda is elkerülheti az is részt vesz a meghívási folyamatot érvényesítette időben személyzet biztosítása érdekében a Contoso és a elszámoltathatóságának lévő megbízható alkalmazott meghívó jogokat delegálni kiválasztásával felügyeleti.

Egyes szervezetek szükséges jobban szabályozhatja, ha a külső felhasználók kerülnek, számos olyan külső szervezeti felhasználóknak, vagy számos külső szervezet fióknevet. Ezekben az esetekben tervezett megosztása használható megosztási, a munkahelyi házirendeknek az érvényesítését, és akár meghívása és a külső felhasználók kezelése a megbízható személyek jogokat delegálni a méretezési csoport kezeléséhez. Az Azure AD B2B támogatja közvetlenül küldendő tervezett meghívások [egy informatikai rendszergazda által az Azure Portalról](https://docs.microsoft.com/azure/active-directory/b2b/add-users-administrator), vagy a Kiszolgálókezelő [a meghívó Managerrel API PowerShell](https://docs.microsoft.com/azure/active-directory/b2b/customize-invitation-api) ahol a felhasználók egy meghívható a művelet. Használatával a tervezett meghívások megközelítés, szabályozhatja, hogy a szervezet ki felhasználókat meghívni, és jóváhagyási folyamatok megvalósításához. Speciális Azure AD-képességekhez, például a dinamikus csoportok teheti, hogy könnyen kezelhető a biztonsági csoport tagsága automatikusan.


![Vezérlőelem, mely vendégek látható tartalom](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_02.png)



1. A folyamat csillagok a rendszergazda manuálisan vagy az API-n keresztül az Azure Active Directory által biztosított a vendégfelhasználó meghívásával
2. A felhasználó elfogadja a meghívást, a szervezet számára.
3. Miután a felhasználó elfogadta a meghívást, a Power bi-ban megosztásának egy jelentés vagy irányítópult a külső felhasználó vagy a biztonsági csoport. Csakúgy, mint a rendszeres megosztása a Power bi-ban a külső felhasználó kap egy e-mailt, az a elemre mutató hivatkozást.
4. Ha a külső felhasználó hozzáfér a hivatkozást, a címtárban hitelesítésüket átadódik a Contoso Azure ad, és a Power BI-tartalmak eléréséhez használt.

### <a name="ad-hoc-or-planned-sharing-of-power-bi-apps"></a>Ad hoc vagy a Power BI-alkalmazásokat a tervezett megosztása

Contoso rendelkezik a jelentések és irányítópultok szükségük van egy vagy több szállítók megoszthatja. Annak érdekében, hogy az összes szükséges külső felhasználók férhetnek hozzá ehhez a tartalomhoz, akkor van csomagolva Power BI-alkalmazásként. A külső felhasználókat vagy kerülnek, közvetlenül az alkalmazás-hozzáférési listához, vagy biztonsági csoportok segítségével. Valaki contoso Ezután elküldi az alkalmazás URL-CÍMÉT az összes a külső felhasználók számára, például az e-mailt. Ha a külső felhasználók a hivatkozás megnyitásához, látják egyetlen minden tartalom könnyen navigálhat a felhasználói élményt.

A Power BI alkalmazással megkönnyíti a Contoso beszállítói hozhat létre olyan BI-portálon. Egyetlen hozzáférési lista szabályozza a hozzáférést a szükséges tartalom elpazarolt idő ellenőrzése és elem szintű engedélyek beállításáról csökkentése. Az Azure AD B2B fenntartja a biztonsági hozzáférést, a nyertes natív azonosítójának használatával, így a felhasználóknak nem kell további bejelentkezési hitelesítő adatok. Használatával a tervezett meghívások biztonsági csoportokkal, ha az alkalmazás hozzáférés-kezelés, csoporthoz vagy onnan máshová a projekt elforgatása egyszerűsített. Tagság a biztonsági csoportok, manuálisan vagy [dinamikus csoportok](https://docs.microsoft.com/azure/active-directory/b2b/use-dynamic-groups), hogy a külső felhasználók olyan szállítótól automatikusan hozzáadódnak a megfelelő biztonsági csoporthoz.


![A vezérlő tartalom AAD-ben](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_03.png)

1. A folyamat elindul, a felhasználó meghívásának a Contoso Azure ad-ben szervezet az Azure Portalon vagy a Powershellen keresztül
2. A felhasználó egy felhasználói csoportot is hozzáadhatók az Azure ad-ben. Statikus vagy dinamikus felhasználói csoport is használható, de dinamikus csoportok csökkenti a manuális tevékenység.
3. A külső felhasználók kapjanak hozzáférést a Power BI-alkalmazás a felhasználói csoport keresztül. Az alkalmazás URL-cím legyen közvetlenül továbbítja a külső felhasználó vagy helyez egy helyen az hozzáféréssel rendelkeznek. A Power BI lehetővé teszi egy ajánlott annak érdekében, hogy az alkalmazás hivatkozást tartalmazó e-mail küldése a külső felhasználók számára, de amelynek tagsága is megváltozhat felhasználói csoportok használatakor a Power BI jelenleg nem kezelhető a felhasználói csoportok minden külső felhasználóját küldhet.
4. A külső felhasználó hozzáfér a Power BI alkalmazás URL-címe, csak a hitelesítést a Contoso Azure ad-vel, az alkalmazás telepítve van a felhasználó számára, és a felhasználó számára látható az összes abban található jelentések és irányítópultok az alkalmazáson belül.

Alkalmazások is egyedi szolgáltatás lehetővé teszi, hogy a felhasználó bejelentkezésekor elérhető legyen az alkalmazás automatikusan a felhasználó számára, való vállalatialkalmazás-készítőkben való. Ez a funkció csak automatikusan telepíti a külső felhasználók, akik már időben az alkalmazás van közzétéve, vagy frissítve a Contoso szervezet része. Így a legjobban a a tervezett meghívások módszer használható, és attól függ, hogy az alkalmazás megjelenésének vagy frissítésének időpontja után a felhasználók hozzáadódnak a Contoso Azure AD. A külső felhasználók is telepítheti az alkalmazást az alkalmazásra mutató hivatkozás használatával.

### <a name="commenting-and-subscribing-to-content-across-organizations"></a>Megjegyzéseket, és iratkozzon fel a tartalom a szervezetek között

Contoso továbbra is működik együtt az alvállalkozók vagy a szállítók, mert a külső mérnökök kell szorosan együttműködik a Contoso-elemzők. A Power BI számos olyan együttműködési funkciók, amelyek segítségével a felhasználók használhatnak fel, hogy a tartalommal kapcsolatos kommunikációt biztosít. Irányítópult megjegyzéseket (és hamarosan a megjegyzéseket jelentés) lehetővé teszi a felhasználóknak adatpontok, tekintse meg, és a jelentéskészítők tehet fel és kommunikálni tárgyalják.

Jelenleg külső vendég felhasználók részt vehetnek megjegyzések megjegyzések elhagyó, és a válaszok olvasása. Azonban a belső felhasználók eltérően vendégfelhasználók nem lehet @mentioned nem kapják meg, hogy azok Megjegyzés érkezett értesítések. Vendég felhasználók nem használhatják a Power BI-ban az előfizetéseket funkció írásának időpontjában. Egy soron következő kiadásban korlátozások azonnal fel kell oldani, és a vendégfelhasználó fog kapni egy e-mailt, amikor egy megjegyzést @mentions őket, vagy ha egy előfizetés kézbesíti a rendszer a tartalmat a Power bi-ban mutató hivatkozást tartalmazó e-mailjeiket.

### <a name="access-content-in-the-power-bi-mobile-apps"></a>A Power BI-mobilalkalmazásokban tartalmának eléréséhez

Egy soron következő kiadásban Ha a Contoso felhasználók jelentések vagy irányítópultok megosztása külső Vendég megfelelőik, a Power BI küld e-mail-értesítést a Vendég. A Vendég felhasználó megnyitja a hivatkozásra kattintva a jelentést vagy irányítópultot a mobil eszközén, amikor a tartalom nyílik meg a natív Power BI mobile-alkalmazások az eszközön, ha vannak telepítve. A vendégfelhasználó tudnak a külső bérlőben, és vissza a saját tartalmait a saját bérlőjén velük megosztott tartalmak között.

> [!NOTE]
> A Vendég felhasználó nem a Power BI mobilalkalmazásban nyissa meg azonnal nyissa meg a külső bérlő, és azokat a külső bérlő-elemre mutató hivatkozást kell kezdődnie. Általános megoldások ismertetett a [terjesztése a szülő szervezeti Power BI-ban tartalmakra mutató hivatkozásokat](#distributing-links-to-content-in-the-parent-organizations-power-bi) a dokumentum későbbi szakaszában.

### <a name="cross-organization-editing-and-management-of-power-bi-content"></a>Szervezetszintű szerkesztése és kezelése a Power BI-tartalmakat

Contoso és a szállítók és az alvállalkozók együttműködve egyre szorosan. Alvállalkozó, az elemzőknek gyakran további metrikákat, vagy adatokat Vizualizációk Contoso megosztotta velük jelentést adni van szüksége. A Contoso Power BI-bérlő kell tárolni az adatokat, de a külső felhasználók szerkeszthetik, létrehozhat új tartalmakat és még osztja el a megfelelő egyéni felhasználóknak képesnek kell lennie.

Power bi-ban, amely lehetővé teszi, hogy lehetőséget biztosít **külső vendégfelhasználóknak szerkesztése, és a tartalomkezelésről** a szervezetben. Alapértelmezés szerint a külső felhasználók számára egy csak olvasható consumption-orientált tapasztalattal rendelkezik. Azonban ez a beállítás lehetővé teszi, hogy választania, melyik külső felhasználók szerkesztése és kezelése a Power BI felügyeleti saját szervezeten belüli tartalom. Ha engedélyezve van, a külső felhasználó is szerkeszt jelentéseket, irányítópultokat, közzététele vagy alkalmazások frissítése, verziójában a munkaterületek és csatlakozhat az adataihoz azok engedélye a használatára.

Ebben a forgatókönyvben a szakasz engedélyezése külső felhasználók szerkeszthetik és kezelhetik a tartalmak Power BI-ban a jelen dokumentum részletesen ismerteti.

## <a name="organizational-relationships-using-power-bi-and-azure-ad-b2b"></a>A Power BI és az Azure AD B2B használatával szervezeti kapcsolatok

Ha a Power BI a felhasználók a szervezeten belüli, hiba, a nem szükséges, az Azure AD B2B használata. Azonban ha két vagy több szervezet szeretne adatokat és elemzéseket másokkal közös használatához, az Azure AD B2B támogatása a Power BI segítségével könnyen és ehhez a költséghatékony.

Az alábbiakban általában ütközött szervezeti struktúrák, amelyek kifejezetten az Azure AD B2B stílus szervezetek közötti együttműködés a Power bi-ban. A legtöbb esetben működik az Azure AD B2B, de bizonyos esetekben az általános megközelítés lehetséges Ez a dokumentum végén található kezelt mellett szóló érvek.

### <a name="case-1-direct-collaboration-between-organizations"></a>1. eset: Szervezet közötti közvetlen együttműködés

A Contoso kapcsolattal fűtőtest szolgáltatójának, amelyek a szervezetek közötti közvetlen együttműködés. Mivel a Contoso viszonylag kevés felhasználók vannak, és az Azure AD B2B használatával fűtőtest megbízhatóság információk elérését igénylő szolgáltatójának-alapú külső megosztás ideális. Ahhoz, hogy adminisztrálja egyszerű és könnyen kezelhető legyen. Ez akkor is a tanácsadási szolgáltatások gyakori minta ahol a tanácsadó kell előfordulhat, hogy egy szervezet tartalmat összeállításához.

![Szervezet közötti megosztása](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_04.png)


Általában a megosztás akkor fordul elő, elem megosztásának / Ad-hoc kezdetben használatával. Azonban csapatok növekedhet és kapcsolatok mélyebb, elem megosztásának száma a tervezett megközelítés válik az előnyben részesített módszer a felügyeleti terhek csökkentése érdekében. Emellett az Ad hoc vagy tervezett megosztása a Power BI-alkalmazások, megjegyzésekkel és a szervezetek közötti tartalom előfizetés, a mobile apps a tartalmakhoz való hozzáférést is jut play, szervezetek közötti szerkesztése és kezelése a Power BI-tartalmakat. Fontosabb Ha mindkét szervezet felhasználók a megfelelő szervezeteik Power BI Pro licenccel rendelkezik, használhatják ezeket a Pro-licenceket a többi összes Power BI-környezetekben. Ez lehetővé teszi, hogy előnyös licencelési, mivel a meghívó szervezetet előfordulhat, hogy nem kell fizetnie, a Power BI Pro licenccel a külső felhasználók számára. Ezekről a licencelés szakaszban Ez a dokumentum későbbi részében részletesebben.

### <a name="case-2-parent-and-its-subsidiaries-or-affiliates"></a>2. eset: Szülő- és annak leányvállalatai vagy társvállalatai

Néhány szervezetben struktúrák olyan összetettebb, beleértve a részlegesen vagy teljesen tulajdonú leányvállalatok, vállalatait vagy felügyelt szolgáltatás szolgáltató kapcsolatok. Ezek a szervezetek van egy szülő szervezet például egy, de az alapul szolgáló szervezetek melyek önállóan, néha eltérő regionális követelmények alapján működnek. Ez minden olyan szervezet, a saját Azure AD-környezetet, és külön Power BI-bérlők vezet.

![Leányvállalatai használata](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_05.png)


Ez a struktúra a szülő szervezeti általában kell annak leányvállalatai szabványos elemzéseket terjesztése. Általában a megosztás történik az Ad hoc vagy tervezett megosztását, ahogyan az alábbi képen, mivel lehetővé teszi a szabványos mérvadó tartalmak széles körű terjesztése a Power BI-alkalmazások módszer használatával. Az eljárás a jelen dokumentum korábbi említett összes forgatókönyv kombinációját használják.

![Forgatókönyvek kombinálása](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_06.png)


Ez a következő folyamatot követi:

1. Minden egyes az leányvállalatának felhasználók meghívást kapott a Contoso Azure AD
2. Majd közzé van téve a Power BI alkalmazásban ezek a felhasználók hozzáférést adhat a szükséges adatokhoz
3. Végül nyissa meg a felhasználók az alkalmazást a jelentések megtekintéséhez készítésű hivatkozás segítségével

Ez a struktúra a szervezetek által számos fontos kihívások néz szembe:

- Miként ossza el a tartalmat a szülő szervezeti Power BI-ban mutató hivatkozások
- Hogyan teszi lehetővé a leányvállalat felhasználók férhetnek hozzá a szülő szervezet adatforrás

#### <a name="distributing-links-to-content-in-the-parent-organizations-power-bi"></a>A szülő szervezeti Power BI-ban tartalmakra mutató hivatkozásokat terjesztése

Három módszer gyakran használják a tartalmakra mutató hivatkozásokat terjeszteni. Az első és a legtöbb alapszintű a hivatkozást küld az alkalmazásnak, hogy a szükséges felhasználókat vagy be a SharePoint Online-helyhez, amelyből segítségével lehet megnyitni. Felhasználók majd is könyvjelzőzze a hivatkozást, a böngészőjük gyorsabb hozzáférés a számukra szükséges adatokkal.

A második megközelítéssel próbálkozzon a szervezetek közötti szerkesztési és a Power BI-tartalom funkció felügyeleti támaszkodik. A szülő szervezeti lehetővé teszi a leányvállalatai a a Power bi-ban, és mi eléréséhez keresztül engedély szabályozza. Ez hozzáférést biztosít a Power BI kezdőlap ahol a az leányvállalatának a felhasználónál a szülő szervezet bérlője a velük megosztott tartalmak átfogó listáját. Majd a szülőszervezetek Power BI-környezet URL-címe van megadva a leányvállalatai a felhasználókra.

A végső megközelítés a Power BI-bérlő esetében minden egyes az leányvállalatának belül létrehozott Power BI-alkalmazás használ. A Power BI alkalmazás tartalmaz egy irányítópultot, a [csempék a külső hivatkozás beállítással konfigurált](https://docs.microsoft.com/power-bi/service-dashboard-edit-tile#hyperlink). Amikor a felhasználó megnyomja a csempét, akkor megnyílik a megfelelő jelentés, irányítópultot vagy alkalmazást a szülő szervezeti Power BI-ban. Ennek a megközelítésnek vannak előnye, hogy az alkalmazás automatikusan települ az leányvállalatának lévő összes felhasználó számára, és érhető el őket, amikor bejelentkeznek a saját Power BI-környezetbe. Hozzáadott Ez a megközelítés előnye, hogy a Power BI mobilalkalmazásokban, amelyek natív módon tudja megnyitni a hivatkozást a működik. Kombinálhatja is ez a második megközelítéssel engedélyezéséhez a könnyebb Váltás a Power BI-környezetek között.

#### <a name="allowing-subsidiary-users-to-access-data-sources-hosted-by-the-parent-organization"></a>Így a leányvállalat felhasználók hozzáférni az adatforrásokhoz a szülő-szervezet

Gyakran, az leányvállalatának elemzők kell létrehoznia a saját analytics, a szülő szervezet által szolgáltatott adatokkal. Ebben az esetben a gyakran felhőbeli adatforrások arra használhatók a probléma megoldása érdekében.

Az első módszer kihasználja [Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-overview) hozhat létre egy vállalati szintű adattárház, amely szükséges a elemzők a szülő és annak leányvállalatai a következő képen látható módon. Contoso az adatokat tárolni és képességeinek használatához, mint a sorszintű biztonság annak biztosítása érdekében az egyes az leányvállalatának felhasználók is hozzáférhetnek az adataikhoz csak is. Minden egyes szervezetben elemzők az adatraktár elérheti a Power BI desktopban, és eredményül kapott elemzések közzététele a saját Power BI-bérlők.

![Megosztás hogyan történik a Power BI-bérlők](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_07.png)


A második megközelítéssel kihasználja [Azure SQL Database](https://azure.microsoft.com/services/sql-database/) adatokhoz hozzáférést biztosítania a relációs adattárház létrehozásához. Ez a módszer hasonlóan az Azure Analysis Services megközelítés azonban bizonyos funkciók, például sorszintű biztonság nehezebb lehet telepíteni és fenntartani leányvállalatai között.

Kifinomultabb megközelítések is is lehetségesek, de messze a leggyakrabban használt a fenti sem.

### <a name="case-3-shared-environment-across-partners"></a>3. eset: Partnerek között megosztott környezetben

Contoso előfordulhat, hogy adja meg azokat a versenytársak közösen hozhat létre egy autó megosztott szerelvény sorban, de osztja meg a jármű különböző márkái alatt vagy eltérő régiókban partneri. Ehhez a széles körű együttműködést, és adatokat, intelligenciát és elemzési művelésének szervezetek között. Ez a struktúra az is közös tanácsadási szolgáltatások iparág ahol tanácsadók csapata teheti meg, projekt-alapú elemzési ügyfél számára.

![Partnerek között megosztott környezetben](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_08.png)



A gyakorlatban ezen szerkezetek összetett, az alábbi képen látható módon, és személyzet fenntartásához szükséges. A hatékony Ez a struktúra támaszkodik a szervezetek közötti szerkesztési és a Power BI-tartalom funkció felügyeleti mivel lehetővé teszi a szervezetek számára, hogy újból felhasználhatja a saját Power BI-bérlők megvásárolt Power BI Pro licenccel.

![Licencek és a megosztott céges tartalomcsomagok](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_09.png)



Egy közös Power BI-bérlő létrehozásához, egy Azure Active Directory kell létrehozni, és legalább egy Power BI Pro felhasználói fiókkal kell vásárolnia egy felhasználónak, hogy az active Directoryban. Ez a felhasználó a megosztott szervezet számára a szükséges felhasználókat felkéri. Fontosabb ebben a forgatókönyvben a Contoso felhasználók kezeli, külső felhasználók számára, ha ugyanúgy működnek, a megosztott szervezeti Power BI-ban.

A folyamat a következőképpen történik:

1. A megosztott szervezeti létrejön egy új Azure Active Directory, és hozza létre az új szervezeti legalább egy felhasználói fiókot. A felhasználó egy Power BI Pro licenccel kell rendelkeznie.
2. Ez a felhasználó ezután hozza létre a Power BI-bérlő, és felkéri a szükséges felhasználókat a Contoso és a fiókpartner-szervezet. A felhasználó is létrehoz az Azure Analysis Services bármely megosztott adatok-eszközeivel. A Contoso és a Partner felhasználók hozzáférhetnek a megosztott szervezeti Power BI vendégként. Ha a Szerkesztés és a tartalomkezelésről a Power bi-ban a külső felhasználók is otthoni használata a Power bi-ban, munkaterületek, a feltöltési vagy a tartalom szerkesztése és jelentések megosztása. Általában megosztott tárolja, és a megosztott szervezeti érhető el.
3. Attól függően, hogyan a felek elfogadják, működhet együtt a saját szellemi tulajdont képező adatokat és az analytics használatával a megosztott adatok adatraktár eszközök fejlesztéséhez minden szervezet számára. Ezek juttathatja el azokat a megfelelő, azok belső Power BI-bérlők használatával a belső felhasználók számára.

### <a name="case-4-distribution-to-hundreds-or-thousands-of-external-partners"></a>4. eset: Több száz vagy ezer külső partnerek számára

Bár a Contoso egyik szállító fűtőtest megbízhatóság jelentést hoz létre, most Contoso kívánja szállítók több száz szabványos jelentések létrehozása. Ez lehetővé teszi, hogy a Contoso, összes szállító rendelkezésre áll a elemzési tökéletesítjük vagy gyártási hibák kijavításához szükséges.

![Számos partnere számára](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_10.png)


Ha a szervezet a szabványos és elemzéseket nyújt számos külső felhasználók/szervezetek, használhatják a Power BI-alkalmazások forgatókönyv Ad hoc vagy tervezett megosztását a BI-portálon hozhat létre, gyors és széles körű szoftverfejlesztési költségek nélkül. A folyamat létrehozása a portál egy Power BI alkalmazással az esettanulmány foglalkozik: A Power BI segítségével történő BI portálon + az Azure AD B2B – részletes utasításokat a jelen dokumentum létrehozásához.

Ebben az esetben a gyakori változatát akkor, ha a szervezet próbál elemzések megosztása a fogyasztókat, különösen akkor, ha szeretné az Azure B2C használata a Power bi-JAL. A Power BI nem támogatja natív módon az Azure B2C. Ha lehetőségei ebben az esetben a mérlegeli, fontolja meg, 2. lehetőség alternatív. használja az általános megközelítés lehetséges a rész a jelen dokumentum.

## <a name="case-study-building-a-bi-portal-using-power-bi--azure-ad-b2b--step-by-step-instructions"></a>Esettanulmány: Létrehozását olyan BI-portálon, a Power bi + az Azure AD B2B – részletes útmutató

A Power BI-integráció az Azure AD B2B a BI-portálon való biztonságos hozzáférést biztosíthat a Vendég számára egy könnyen használható, zökkenőmentes megoldást kínál az Contoso. Contoso állíthatja ezt a három lépést:

![A portál létrehozása](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_11.png)


1. BI Portal létrehozása a Power BI-ban

    Az első tevékenység contoso, ha azok a BI-portálon a Power bi-ban. A Contoso BI portálon áll, célirányosan kialakított irányítópultok és jelentések, amelyet számos belső és a vendég felhasználók rendelkezésére fog gyűjteménye. Az ajánlott módszer a Power BI-ban mindezt a Power BI-alkalmazás létrehozásához. Tudjon meg többet [a Power BI](https://powerbi.microsoft.com/blog/distribute-to-large-audiences-with-power-bi-apps/).

- A Contoso BI csapata egy alkalmazás-munkaterületet a Power bi-ban hoz létre.

    ![Alkalmazás-munkaterület](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_12.png)
    

- Más szerzők kerülnek a munkaterületre

    ![Szerzők hozzáadása](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_13.png)


- Hozza létre a tartalmat a munkaterületen belül

    ![A munkaterületen belüli tartalom létrehozása](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_14.png)


    Most, hogy a tartalom jön létre az alkalmazás-munkaterületen, Contoso készen áll a vendégfelhasználók meghívása az erőforráspartner-szervezetek a tartalom felhasználásához.

2. Vendégfelhasználók meghívása

    Vendégfelhasználók a BI-portálon, a Power bi-ban a Contoso két módja van:

    * Tervezett meghívások
    * Az ad hoc meghívások

    **Tervezett meghívások**

    Ebben a megközelítésben Contoso meghívót küld a vendégfelhasználók időben az Azure ad-hez, és ezután terjeszti a Power BI-tartalmak hozzájuk. Contoso az Azure Portalon vagy a PowerShell-lel vendégfelhasználókat is meghívhat. Az Azure Portalról vendégfelhasználók lépései a következők:

    - A Contoso Azure AD-rendszergazda navigál **az Azure portal > Azure Active Directory > felhasználók és csoportok > minden felhasználó > új vendégfelhasználó**

    ![A vendégfelhasználók](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_15.png)


    - Adjon meg egy a vendégfelhasználó meghívó üzenetet, majd kattintson a meghívó

    ![Adja hozzá a meghívót](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_16.png)


    > [!NOTE]
    > Az Azure Portalról vendégfelhasználók meghívása, kell a bérlő az Azure Active Directory-rendszergazda.

    Számos vendégfelhasználók a Contoso biztosítani szeretné, ha nem ezt a PowerShell használatával. A Contoso Azure AD-rendszergazda az e-mail-címeit minden vendégfelhasználó CSV-fájl tárolja. Az alábbiakban [Azure Active Directory B2B együttműködési kódmintát és PowerShell-minták](https://docs.microsoft.com/azure/active-directory/b2b/code-samples) és utasításokat.

    A meghívó után a vendégfelhasználók kap egy e-mailt a meghívó hivatkozást tartalmazó.

    ![Meghívó-hivatkozás](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_17.png)


    Után a vendégfelhasználót a hivatkozásra kattint, hozzáférhet a tartalmat a Contoso Azure AD-bérlőben.

    > [!NOTE]
    > A meghívó e-mailt a szolgáltatással az Azure AD márkajelzési leírtak szerint, az elrendezést módosítani lehet [Itt](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-invitation-email).


    **Az ad hoc meghívások**

    Contoso mi történik, ha nem tudja időben meghívni szeretné minden vendégfelhasználó? Vagy, mi történik, ha a Contoso az elemző, aki létrehozta a BI-portálon szeretné terjeszteni a tartalmakat a vendégfelhasználók herself? Is támogatott ebben a forgatókönyvben a Power bi-ban az ad-hoc módon.

    Az elemző egyszerűen hozzáadhatja a külső felhasználók a hozzáférés-listához, az alkalmazás közzétételekor azok vannak. A vendégfelhasználók lekérdezi a meghívót, és amint elfogadják, a rendszer automatikusan átirányítja a Power BI-tartalmakat.

    ![Külső felhasználó hozzáadása](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_18.png)


    > [!NOTE]
    > Meghívók csak az első alkalommal egy külső felhasználót a cégbe van szükség.


3. Tartalomelosztás

    Most, hogy a Contoso BI csapata a BI-portálon létrehozott és vendégfelhasználókat, azok vendégfelhasználók hozzáférést ad az alkalmazásnak, és közzéteheti úgy juttathatja el a portálon a végfelhasználók számára. A Power BI automatikusan kiegészíti a Contoso bérlő a korábban hozzáadott vendég felhasználók neve. Ad hoc ad hoc meghívások többi Vendég számára ezen a ponton is hozzáadhatók.

    > [!NOTE]
    > Biztonsági csoportok használata kezelheti az alkalmazás külső felhasználók számára a hozzáférést, ha a tervezett meghívások a módszert akkor használja, és az alkalmazásra mutató hivatkozás közvetlen megosztása minden kell-e férni külső felhasználó. Ellenkező esetben a külső felhasználót nem lehet telepíteni, vagy az alkalmazáson belüli tartalom megtekintését. _

    Vendégfelhasználók kap egy e-mailt, az alkalmazás hivatkozását.

    ![E-mailben meghívást hivatkozás](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_19.png)


    Erre a hivatkozásra kattint, a Vendég rendszer kéri a felhasználóktól a saját szervezet identitás a hitelesítéshez.

    ![Bejelentkezési oldala](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_20.png)


    Miután sikeresen hitelesítik, a rendszer átirányítja a Contoso BI alkalmazás.

    ![Tekintse meg a megosztott tartalom](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_21.png)

    Vendég felhasználók ezt követően férhetnek hozzá a Contoso-alkalmazást az e-mailben lévő hivatkozásra kattintva, vagy a csatolás megjelölése könyvjelzővel. Contoso is egyszerűbbé teheti a vendégfelhasználók számára ez a hivatkozás hozzáadásával bármely meglévő extranetes portál, a vendég felhasználók által már használt.

4. Következő lépések

    Egy Power BI alkalmazás és az Azure AD B2B használatával, Contoso volt képes gyorsan létrehozhat egy BI portál beszállítói kód nélküli módon. Ez jelentősen egyszerűbb terjesztése szabványos analyticsben, hogy minden a szállítók, akik éppen szüksége van rá.

    A példa bemutatta, hogyan sikerült-e a egyetlen közös jelentés elosztott szállítók között, miközben a Power BI sokkal tovább meg. Annak érdekében, hogy egyes partnerek a saját magukat csak adatokat lát, sorszintű biztonság is hozzáadhatók egyszerűen a jelentés és egy adatmodellt. Külső partnerekkel rész a jelen dokumentum az adatok biztonságát a részletek a folyamatát ismerteti.

    Gyakran az egyes jelentések és irányítópultok kell egy meglévő portál beilleszthető. Ez is elvégezhető újbóli használata számos, a technikák, a példában látható. Azonban az ilyen helyzetek egyszerűbb lehet beágyazni a jelentésekben és irányítópultokon közvetlenül egy munkaterületről. A folyamat a fióknevet és a biztonsági engedélyek hozzárendelése a igényelnek a felhasználók nem változik.

## <a name="under-the-hood-how-is-lucy-from-supplier1-able-to-access-power-bi-content-from-contosos-tenant"></a>Technikai részletek: Miben különbözik a Power BI-tartalmakat, a Contoso bérlő elérhetik Supplier1 Lucy?

Most, hogy úgy találtuk, hogyan Contoso gond nélkül terjesztheti a Power BI-tartalmakat a fiókpartner-szervezetek, tekintsük át ennek működéséről a motorháztető alatt.

Ha a Contoso meghívott [ lucy@supplier1.com ](mailto:lucy@supplier1.com) a címtárban, az Azure AD közötti hivatkozást hoz létre [ Lucy@supplier1.com ](mailto:Lucy@supplier1.com) és a Contoso Azure AD-bérlő. Ez a hivatkozás lehetővé teszi, hogy tudja, hogy az Azure AD Lucy@supplier1.com is hozzáférhetnek a tartalomhoz, a Contoso bérlő.

Lucy megpróbál hozzáférni a Contoso Power BI alkalmazást, ha az Azure AD ellenőrzi, hogy e Lucy férhet hozzá a Contoso bérlő majd biztosít a Power BI egy jogkivonatot, amely azt jelzi, hogy Lucy hozzáférhetnek a tartalomhoz, a Contoso bérlő van hitelesítve. A Power BI a jogkivonattal engedélyezheti, és győződjön meg arról, hogy Lucy férhet hozzá a Contoso Power BI-alkalmazáshoz.

![Hitelesítési és engedélyezési](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_22.png)

A Power BI-integráció az Azure AD B2B működik együtt az összes üzleti e-mail-címeket. Ha a felhasználó nem rendelkezik egy Azure AD-identitásnak, azok kérheti hozzon létre egyet. Az alábbi képen látható a részletes folyamat:

![Integráció folyamatábra](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_23.png)


Fontos felismerje, hogy az Azure AD-fiókot használni vagy létrehozni a külső féltől származó Azure AD-ben Ez a márka, lehet, hogy Lucy használhatja a saját felhasználónevét és jelszavát, és a hitelesítő adataival automatikusan működése leáll más bérlők minden alkalommal, amikor marcela elhagyja a céget, amikor a saját szervezete is használja az Azure ad-ben.

## <a name="licensing"></a>Licencelés

Contoso három megközelítések egyikét licenccel a vendégfelhasználók közül választhat a szállítók és a partnerszervezetek Power BI-tartalmak eléréséhez.

> [!NOTE]
> _Az Azure AD B2B ingyenes szint ez elegendő az Azure AD B2B használata a Power bi-ban. Az Azure AD B2B bizonyos összetettebb funkciókat, például a dinamikus csoportok külön engedélye szükséges. További információt az Azure AD B2B dokumentációjában talál:_ [_https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance_](https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance)

### <a name="approach-1-contoso-uses-power-bi-premium"></a>1. módszer: Contoso használja a Power BI Premium

Ezt a módszert használja a Contoso Power BI Premium-kapacitást vásárol, és hozzárendeli a portál BI-tartalmak a kapacitás. Ez lehetővé teszi a vendégfelhasználók a fiókpartner-szervezetek bármely Power BI-licenc nélkül a Contoso Power BI alkalmazás eléréséhez.

A külső felhasználók a használati tapasztalatok csak "Ingyenes" a felhasználók rendelkezésére a Power BI használatakor a Power BI Premium-tartalmakat is vonatkozik.

Contoso is kihasználhatja az alkalmazásokhoz, például a nagyobb gyakoribb frissítéseket, dedikált kapacitást és nagy modellméretet más Power BI prémium szintű funkcióit.

![További képességei](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_24.png)


### <a name="approach-2-contoso-assigns-power-bi-pro-licenses-to-guest-users"></a>2. módszer: Contoso Power BI Pro-licenceket rendel a vendégfelhasználók

Ezzel a módszerrel Contoso rendeli hozzá a pro-licencek Vendégfelhasználók partner szervezet – ezt megteheti a Contoso Microsoft 365 felügyeleti központban. Ez lehetővé teszi a vendégfelhasználók a fiókpartner-szervezetek magukat licenc megvásárlása nélkül a Contoso Power BI alkalmazás eléréséhez. Ez akkor lehet megfelelő, amelyek a szervezet nem fogadta el a Power BI még külső felhasználókkal való megosztás.

> [!NOTE]
> _A Contoso pro-licenccel a vendégfelhasználók csak akkor, ha a Contoso bérlő tartalmakhoz férhetnek vonatkozik. Pro-licencek engedélyezze a hozzáférést a tartalomhoz, amely nem szerepel a Power BI prémium-kapacitás. Azonban a Pro-licenccel rendelkező külső felhasználók korlátozva vannak alapértelmezés szerint egy használatalapú csak felhasználói felületre. Változás ismertetett megközelítéssel is lehet a_ _külső felhasználók szerkesztése és kezelése a Power BI-tartalmakat_ _a dokumentum későbbi szakaszában._

![Licencinformációk](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_25.png)


### <a name="approach-3-guest-users-bring-their-own-power-bi-pro-license"></a>3. módszer: Vendég felhasználók a saját Power BI Pro licenc használata

Ezzel a módszerrel szállítói 1 rendel a Power BI Pro-licenc Lucy. Marcela ezután hozzáférhetnek a Contoso Power BI alkalmazást a jelen licenc. Egy külső Power BI-környezetbe való hozzáféréskor Lucy saját Pro-licenc is használja saját szervezet, mivel ez a módszer van más néven _saját licenc használata_ (BYOL). Mindkét szervezetben használ a Power bi-ban, ha ez előnyös licencelése a teljes analytics megoldás kínál, és minimálisra csökkenti a licencek hozzárendelése külső felhasználókhoz járó többletterhelést.

> [!NOTE]
> _A pro-licenc Lucy szállítói 1 által adott bármilyen Lucy esetén a vendégfelhasználó Power BI-bérlő vonatkozik. Pro-licencek engedélyezze a hozzáférést a tartalomhoz, amely nem szerepel a Power BI prémium-kapacitás. Azonban a Pro-licenccel rendelkező külső felhasználók korlátozva vannak alapértelmezés szerint egy használatalapú csak felhasználói felületre. Változás ismertetett megközelítéssel is lehet a_ _külső felhasználók szerkesztése és kezelése a Power BI-tartalmakat_ _a dokumentum későbbi szakaszában._

![Pro-licenc követelmények](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_26.png)

## <a name="data-security-for-external-partners"></a>A külső partnerei által nyújtott Adatbiztonság

Általában akkor, amikor több külső szállítók dolgozik, Contoso meg kell győződnie arról, hogy minden szállítói csak a saját termékekre vonatkozó adatokat lát-e. Felhasználó-alapú biztonsági és a dinamikus sorszintű biztonság legyen ez könnyen megoldható a Power bi-JAL.

### <a name="user-based-security"></a>Felhasználó-alapú biztonság

A leghatékonyabb szolgáltatása a Power bi egyik, a sorszintű biztonság. Ez a funkció lehetővé teszi, hogy a Contoso egy jelentés és adatkészlet létrehozása, de továbbra is érvényesek lesznek a különböző biztonsági szabályokat minden felhasználó számára. Egy részletes ismertetése: [sorszintű biztonság (RLS)](https://powerbi.microsoft.com/documentation/powerbi-admin-rls/).

A Power BI-integráció az Azure AD B2B lehetővé teszi, hogy a Contoso sorszintű biztonsági szabályok hozzárendelése vendégfelhasználók, amint a meghívásuk a Contoso bérlő. Úgy találtuk, mielőtt a Contoso adhat hozzá vendégfelhasználókat keresztül vagy tervezett vagy ad-hoc meghívások. Ha a Contoso sorszintű biztonság érvényre szeretné juttatni, erősen ajánlott tervezett meghívások használata előtt időt és a tartalom megosztása előtt a biztonsági szerepköröket hozzárendelné azokat a vendégfelhasználók hozzáadása. Ha inkább használja a Contoso ad-hoc meghívások, lehetséges, hogy rövid idő alatt, a vendég felhasználók nem fognak tudni jelennek meg adatok.

> [!NOTE]
> Ezt a késést, ha használatával ad-hoc meghívások RLS által védett adatok eléréséhez támogatja az informatikai csapat kérelmeket, mert a felhasználók látnak, üres vagy nem működő jelentéseket és irányítópultokat szeretne, ha az e-mailben kapott hivatkozás megnyitása a megosztási vezethet. Ezért erősen ajánlott tervezett meghívások használata a scenario.* *

Nézzük végig, ez egy példával szemlélteti.

Ahogy korábban említettük, Contoso rendelkezik-e a világ minden pontján szállítók, és győződjön meg arról, hogy a felhasználók a szolgáltató szervezetek nyerjen ki adatokat a saját területükön csak szeretne.  De a Contoso felhasználók férhetnek hozzá az összes adatot. Ahelyett, hogy több különböző jelentést hoz létre, Contoso egyetlen jelentést hoz létre, és a szűrők az adatok alapján a felhasználó, tekintse meg.

![A megosztott tartalom](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_27.png)

Ahhoz, hogy a Contoso ki csatlakozik alapján szűrheti, két szerepkör jönnek létre a Power BI desktopban. Az egyik a SalesTerritory "Európa" az összes adatot, és egy másik, "Észak-Amerikában" szűréséhez.

![Szerepkörök kezelése](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_28.png)

Amikor a szerepkörök határozzák meg a jelentést, a felhasználó hozzáférhet az adatokhoz, hogy egy adott szerepkörrel kell rendelni. A Power BI szolgáltatáson belül történik, a szerepkör-hozzárendelés ( **adatkészletek > biztonsági** )

![Biztonság beállítása](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_29.png)

Ekkor megnyílik egy oldala, ahol megtekintheti a Contoso BI csapatának, a két szerepkörök hozza létre őket.  Most már a Contoso BI csapata felhasználókat rendelhet a szerepköröket.

![Sorszintű biztonság](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_30.png)

A példában a Contoso egy felhasználó egy fiókpartner-szervezet e-mail-címmel van hozzáadása "[adam@themeasuredproduct.com](mailto:adam@themeasuredproduct.com)" az Európa szerepkörhöz:

![A sorszintű biztonsági beállítások](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_31.png)

Ez lekéri oldja meg az Azure AD, ha a Contoso a neve látható az ablakban készen áll a tekintheti meg:

![Szerepkörök megjelenítése](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_32.png)

Most ennek a felhasználónak a vele megosztott alkalmazás megnyílik, amikor csak látja egy jelentést, Európa származó adatokkal:

![Tartalom megtekintése](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_33.png)

### <a name="dynamic-row-level-security"></a>A dinamikus sorszintű biztonság

A témakör egy másik érdekes, hogy tekintse meg, hogyan a dinamikus sorszintű biztonság (RLS) használata az Azure AD B2B.

Röviden a dinamikus sorszintű biztonság a Power bi-t kapcsolódás személy felhasználóneve alapján a modellben található adatok szűrésével működik. Több szerepkör a csoportok számára, hanem a modell határozhatja meg a felhasználókat. A minta részletesen itt nem ismertetünk. A sorszintű biztonság minden fajtájában Kasper de Jong kínál az részletes írási [Power BI Desktop dinamikus biztonság – adatlap](https://www.kasperonbi.com/power-bi-desktop-dynamic-security-cheat-sheet/), majd a [ebben a tanulmányban](https://msdn.microsoft.com/library/jj127437.aspx) .

Lássunk erre egy kis példát – Contoso értékesítési csoportok szerint egy egyszerű jelentés rendelkezik:

![Minta-tartalom](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_34.png)

Most ezt a jelentést megosztani a két vendég felhasználók és a egy belső felhasználót kell – a belső felhasználó számára látható, minden rendben, de a vendégfelhasználók csak a csoportok látható hozzáféréssel rendelkeznek. Ez azt jelenti, hogy kell szűrje az adatokat, csak a vendégfelhasználók számára. A megfelelő szűrje az adatokat, a Contoso a dinamikus rls-t mintát alkalmaz a a tanulmány és blog bejegyzés leírtak szerint. Ez azt jelenti, hogy Contoso ad hozzá a felhasználónevek magukhoz az adatokhoz:

![Rls-t felhasználók megtekintése magukhoz az adatokhoz](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_35.png)

Ezt követően a Contoso a megfelelő adatmodell, amely szűri az adatokat a megfelelő kapcsolatokat a megfelelő hoz létre:

![Megfelelő adat jelenik meg](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_36.png)

Az adatok alapján automatikusan ki van bejelentkezve szűrésére, Contoso kell, amelyet átad szerepkör létrehozása a felhasználó, aki csatlakozik a. Ebben az esetben a Contoso létrehoz két szerepkör – az első az a "securityrole" szűri az aktuális felhasználónévvel, a Power bi-hoz (ez működik, akár az Azure AD B2B vendégfelhasználók) bejelentkezett felhasználó a felhasználói tábla.

![Szerepkörök kezelése](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_37.png)

A belső felhasználók is megjelenne is létrehoz egy másik "AllRole" contoso – Ez a szerepkör nem rendelkezik minden olyan biztonsági predikátum.

A szolgáltatáshoz a Power BI asztali fájl feltöltése után Contoso vendégfelhasználók rendelhet az "SecurityRole" és a belső felhasználók számára a "AllRole"

Most amikor a vendégfelhasználók nyissa meg a jelentést, azok csak lát csoport: történő értékesítések

![Csak a-csoport](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_38.png)

A mátrix a jobb oldalon láthatja is a vendég felhasználók e-mail címét adja vissza a USERNAME() és a usernameprincipal() függvény eredménye.

A belső felhasználói most már megtekintheti az összes adat beolvasása:

![Minden adat látható](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_39.png)

Amint láthatja, dinamikus rls-t mind a belső, vagy a vendég felhasználók működik.

> [!NOTE]
> Ebben a forgatókönyvben is használható, amikor egy modell segítségével az Azure Analysis Servicesben. Általában ugyanazt az Azure AD, a Power BI csatlakozik az Azure Analysis Services – ebben az esetben az Azure Analysis Services az Azure AD B2B keresztül meghívott vendég felhasználók is felismeri.

## <a name="connecting-to-on-premises-data-sources"></a>Csatlakozás az helyszíni adatforrásokkal

A Power BI lehetőséget nyújt a kihasználhatja a helyszíni adatforrásokhoz, például a Contoso [SQL Server Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/) vagy [SQL Server](https://powerbi.microsoft.com/documentation/powerbi-gateway-kerberos-for-sso-pbi-to-on-premises-data/) közvetlenül köszönhetően a a [a helyszíni adatátjáró](https://powerbi.microsoft.com/documentation/powerbi-gateway-onprem/). Jelentkezzen be az adatforrások a Power bi-ban használt azonos hitelesítő adatokkal, még akkor is lehetőség.

> [!NOTE]
> Szeretne csatlakozni a Power BI-bérlője átjáró telepítésekor a felhasználók által létrehozott a bérlőn belül kell használnia. Külső felhasználók nem lehet átjárót telepíteni, és csatlakoztassa a bérlőn. _

Külső felhasználók számára ez lehet bonyolultabb, mint a külső felhasználók általában nem ismeri a helyszíni AD. Azáltal, hogy a külső Felhasználónevek leképezése belső felhasználónevek, a Contoso rendszergazdák Power BI által az a megkerülő [az adatforrás kezelése – Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/). Ha például [ lucy@supplier1.com ](mailto:lucy@supplier1.com) is le lehet képezni [lucy\_supplier1\_com #EXT@contoso.com](mailto:lucy_supplier1_com).

![Felhasználónevek leképezése](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_40.png)

Ez a módszer is megfelel, ha a Contoso csak akkor van néhány olyan felhasználók, vagy ha a Contoso a külső felhasználókat leképezhet egy olyan belső fiók. Összetettebb esetekhez, ahol a minden felhasználó a saját hitelesítő adatokat igényel, van egy speciális megközelítés használó [egyéni AD-attribútumok](https://technet.microsoft.com/library/cc961737.aspx) a leképezés elvégzésére, leírtak szerint [az adatforrás kezelése – Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/). Ez lehetővé tenné, hogy a Contoso rendszergazda meghatározhatja a minden felhasználó leképezése az Azure ad (is külső B2B-felhasználók).  Ezek az attribútumok a Contoso teljesen automatizálható a leképezést a meghívó vagy ütemezett kiadása ütemben történik parancsfájlokat vagy kód használatával AD hálózatiobjektum-modellt állíthatja be.

## <a name="enabling-external-users-to-edit-and-manage-content-within-power-bi"></a>Külső felhasználók szerkesztése és kezelése a Power BI-tartalmakat

Contoso engedélyezheti a külső felhasználók számára a szervezeten belül tartalmat közreműködőként, a szervezetek közötti szerkesztése és kezelése a Power BI-tartalom szakasz a korábban ismertetett módon.

> [!NOTE]
> Szerkesztheti, és kezelheti a tartalmakat a szervezet a Power BI-ban, a felhasználó a saját munkaterületen kívül munkaterületen kell rendelkeznie a Power BI Pro-licencre. A felhasználók beszerezhetik a Pro-licencek the_ leírtaknak megfelelően _Licensing__section ebben a dokumentumban._

A Power BI felügyeleti Portáljához biztosít a **külső vendégfelhasználóknak szerkeszthetik és kezelhetik a szervezeten belüli tartalom engedélyezése** beállítása a bérlői beállításokat. Alapértelmezés szerint a beállítás le van tiltva, ami azt jelenti, a külső felhasználók egy korlátozott írásvédett tapasztalatokat szerezhet, alapértelmezés szerint értéke. A beállítás csak a felhasználók számára a UserType Vendég beállítása az Azure ad-ben. Az alábbi táblázat ismerteti a felhasználói élmény a UserType és a beállítások konfigurációjától függően viselkedést.

| **Az Azure AD-felhasználó típusa** | **Külső vendég felhasználók szerkesztése és tartalmi beállításának kezeléséhez** | **Viselkedés** |
| --- | --- | --- |
| Vendég | Le van tiltva, a felhasználónak (alapértelmezés) | Egy elem használatalapú egyetlen nézetben. Lehetővé teszi, hogy a jelentések, irányítópultok és a egy URL-címet a meghívott felhasználónak küldött tekinthetők meg az alkalmazások csak olvasási hozzáféréssel. A Power BI Mobile-alkalmazások, a vendégfelhasználó adjon meg egy csak olvasható nézet. |
| Vendég | A felhasználó engedélyezve | A külső felhasználó hozzáférést kap a teljes körű Power BI használatával, bár egyes funkciók nem érhetők el nekik. A külső felhasználó be kell jelentkeznie a Power BI használatával a Power BI szolgáltatás URL-címe tartalmazza a bérlő adatokkal. A felhasználó lekérdezi a kezdőlap élmény, a saját munkaterület és alapján engedélyek megnyithatja, megtekintheti, és a tartalom létrehozása. </br></br> A Power BI Mobile-alkalmazások, a vendégfelhasználó adjon meg egy csak olvasható nézet. |

> [!NOTE]
> Az Azure AD külső felhasználók is megadható a UserType tag. Jelenleg nem támogatott a Power bi-ban ez.

A Power BI felügyeleti portálon a beállítás a következő képen látható.

![Rendszergazdai beállítások](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_41.png)

A csak olvasható alapértelmezett felhasználói élményt, és amely is szerkesztése és a tartalomkezelésről a vendég felhasználók kapnak. Alapértelmezés szerint le van tiltva, ami azt jelenti, minden vendégfelhasználó a csak olvasható tapasztalattal rendelkezik. A Power BI felügyeleti vagy engedélyezheti a beállítást a szervezet minden vendégfelhasználó vagy az Azure ad-ben meghatározott biztonsági csoportokat. Az alábbi ábrán a Contoso Power BI felügyeleti létrehozott egy biztonsági csoportot az Azure AD külső felhasználók is szerkesztheti, és a tartalomkezelésről a Contoso bérlő kezeléséhez.

Annak érdekében, ezek a felhasználók a Power bi-bA bejelentkezni, adja meg azokat a bérlői URL-címet. A bérlői URL-cím megkereséséhez kövesse az alábbi lépéseket.

1. A Power BI szolgáltatásban, a felső menüben válassza ki a Súgó ( **?** ) majd **a Power BI bemutatása**.
2. Nézze meg a **bérlői URL-cím**. Ez az a bérlői URL-cím, megoszthatja a vendégfelhasználókat.

    ![Bérlői URL-cím](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_42.png)

A külső vendég felhasználók szerkesztése és a tartalomkezelésről a szervezetben való használatakor a megadott vendég felhasználók eléréséhez a szervezet Power bi-ba, és bármilyen tartalom, amely engedéllyel rendelkeznek. Ezek kezdőlap hozzáférhetnek, keresse meg és munkaterületek hozzájárulhasson, telepítik az alkalmazásokat, ahol a hozzáférési listán, és rendelkezik a saját munkaterületen. Létrehozhatnak olyan munkaterületeket, illetve ezek rendszergazdái lehetnek, amelyek az új munkaterületi felületet alkalmazzák.

> [!NOTE]
> Ha ezzel a lehetőséggel ellenőrizze, hogy tekintse át a cégirányítási szakasz ebben a dokumentumban, mivel az alapértelmezett Azure AD beállításai nem használ bizonyos funkciókat, mint ami csökkentett experience.* * személyek színválasztó vendégfelhasználók

A vendégfelhasználók számára a engedélyezése külső vendégfelhasználóknak szerkeszthetik és kezelhetik a tartalom a szervezet bérlői beállítás engedélyezését bizonyos elemek nem érhető el hozzájuk. Frissítéséhez, vagy tegye közzé jelentéseket, vendégfelhasználók kell használnia a Power BI szolgáltatás webes felhasználói felületén, beleértve az adatok lekérése a Power BI Desktop-fájlok feltöltéséhez. A következő műveletek nem támogatottak:

- Közvetlen közzététel a Power BI Desktopból a Power BI szolgáltatásba
- A vendégfelhasználók nem csatlakozhatnak a Power BI szolgáltatás szolgáltatói adatkészleteihez a Power BI Desktoppal
- Office 365-csoportokhoz kötött klasszikus munkaterületek: A vendégfelhasználók nem hozhatnak létre ilyen munkaterületeket, és nem lehetnek ezek rendszergazdái. Csak tagok lehetnek.
- Az ad-hoc meghívások nem támogatottak a munkaterületek hozzáférési listáiban
- A vendégfelhasználók számára nem támogatott a Power BI Publisher for Excel
- A vendégfelhasználók nem telepíthetik a Power BI Gateway szolgáltatást, és nem csatlakoztathatják az Ön szervezetéhez
- A vendégfelhasználók nem telepíthetnek alkalmazásokat, és nem tehetnek közzé tartalmakat a teljes szervezet számára
- A vendégfelhasználók nem használhatnak, hozhatnak létre, frissíthetnek vagy telepíthetnek szervezeti tartalomcsomagokat
- A vendégfelhasználók nem használhatják az Elemzés az Excelben funkciót
- Nem lehet a vendégfelhasználók @mentioned a megjegyzéseket (Ez a funkció a hozzáadja egy soron következő kiadásban)
- Vendég felhasználók nem használhatják az előfizetések (Ez a funkció a hozzáadja egy soron következő kiadásban)
- Azon vendégfelhasználóknak, akik ezt a funkciót veszik igénybe, munkahelyi vagy iskolai fiókkal kell rendelkezniük. Személyes fiókot használó vendégfelhasználókat élmény bejelentkezési korlátozások miatt további korlátozások.



## <a name="governance"></a>Irányítás

### <a name="additional-azure-ad-settings-that-affect-experiences-in-power-bi-related-to-azure-ad-b2b"></a>A Power bi-ban az Azure AD B2B kapcsolatos élményt érintő további Azure AD beállításai

Az Azure AD B2B megosztásakor az Azure Active Directory-rendszergazda szabályozza a külső felhasználói élmény aspektusait. Ezek a külső együttműködési beállítások oldalon belül az Azure Active Directory-beállítások a Bérlőhöz tartozó szabályozza.

A beállítások részletei itt érhető el:

[https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations](https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations)

> [!NOTE]
> Alapértelmezés szerint a vendégfelhasználók engedélyei korlátozottak beállítás az Igen értékre van állítva, így a Power BI-ban a vendégfelhasználók csak korlátozottan élményt különösen körülvevő megosztása, ahol személyválasztója előkészíthetik nem működik azoknak a felhasználóknak. Fontos, hogy annak biztosítása érdekében egy jó experience.* * alább látható módon nem, állítsa be az Azure AD-rendszergazdáját használata

![Külső együttműködési beállítások](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_43.png)


### <a name="control-guest-invites"></a>Vezérlő Vendég meghívók

A Power BI-rendszergazdák szabályozhatja a külső megosztás csak a Power BI látogasson el a Power BI felügyeleti portáljához. De a bérlői rendszergazdák is szabályozhatja a különböző Azure AD-házirendek használatával külső megosztás.  Ezek a szabályzatok engedélyezése a bérlői rendszergazdák számára

- Kapcsolja ki a végfelhasználók meghívások
- Csak rendszergazdák és a Vendégmeghívó szerepkörű felhasználók küldhetnek meghívót
- A rendszergazdák, a Vendégmeghívó szerepkörrel és tagok küldhetnek meghívót
- Minden felhasználó,-Vendégek esetén is küldhetnek meghívót

További információ ezeket a szabályzatokat [Azure Active Directory B2B együttműködés meghívók delegálása](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-delegate-invitations).

Külső felhasználók által az összes Power BI-műveletek egyúttal [rögzítése a naplózási portál](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/).

### <a name="conditional-access-policies-for-guest-users"></a>A vendégfelhasználók számára feltételes hozzáférési szabályzatok

Contoso kényszerítheti a feltételes hozzáférési szabályzatokat a vendégfelhasználók számára, ki férhet hozzá a Contoso bérlő. A részletes utasításokat talál [feltételes hozzáférés B2B-együttműködés felhasználók](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-mfa-instructions).

## <a name="common-alternative-approaches"></a>Közös alternatív módszerek

Az Azure AD B2B megkönnyíti az adatok és jelentések megosztása a szervezetek számára, amíg nincsenek számos más megközelítés, amely gyakran használják, és lehet, hogy kiváló bizonyos esetekben.

### <a name="alternative-option-1-create-duplicate-identities-for-partner-users"></a>Alternatív 1. lehetőség: Ismétlődő identitásainak partner felhasználók létrehozása

Ezzel a beállítással Contoso kellett a Contoso bérlő partner felhasználók ismétlődő identitásait manuális létrehozásához a következő képen látható módon. Power BI-ban Contoso is oszthatja a hozzárendelt identitások, a megfelelő jelentések, irányítópultok vagy alkalmazások.

![Megfelelő leképezések és nevének beállítása](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_44.png)

Ez a megoldás kiválasztásához okok:

- A felhasználó identitását a szervezet által szabályozott, mivel minden kapcsolódó, például az e-mailben SharePoint szolgáltatást, stb. is a szervezet irányítása alatt. A rendszergazdák új jelszót, fiókokhoz való hozzáférés letiltása, vagy ezeket a szolgáltatásokat a tevékenységek naplózása.
- Felhasználók, akik a személyes fiókok használata az üzleti gyakran korlátozva vannak az egyes szolgáltatásokhoz ezért előfordulhat, hogy kell szervezeti fiókkal.
- Néhány szolgáltatás csak a szervezet felhasználói munkára. Ha például az Intune használata kezelheti a tartalmakat a külső felhasználók Azure B2B használatával a személyes/mobile rendszerű eszközökön nem lehetséges.

Ez a megoldás kiválasztása, nem okok:

- Partnerszervezetek felhasználóinak fontos figyelembe venni két készletnyi hitelesítő adatokat – egy, a másik pedig a saját cég hozzáférhessen a tartalomhoz a Contoso tartalmainak eléréséhez. Ez a vendégfelhasználóknak módon gondoskodik, és számos vendégfelhasználók rendszer eleinte a felhasználói élményt.
- Contoso kell vásárolni és a felhasználónkénti licenceket hozzárendelni ezeket a felhasználókat. Ha egy felhasználó e-maileket kapni, vagy használja az office-alkalmazások, a megfelelő licencekkel, beleértve a Power BI Pro szerkesztheti és megoszthatja a Power BI tartalmait is szükségük van.
- Előfordulhat, hogy a Contoso szeretne szigorúbb engedélyezési és a belső felhasználók képest külső felhasználók számára a cégirányítási szabályzatok kényszerítése. Ennek érdekében a Contoso létre kell hoznia egy belső fejlesztésű elnevezéseket a külső felhasználók számára, és minden Contoso-felhasználó kell részesíteni a elnevezéseket kapcsolatos kell.
- Amikor a felhasználó elhagyja a szervezet, továbbra is rendelkezik a Contoso-erőforrásokhoz való hozzáférést, amíg a Contoso rendszergazdája nem törli a fiók
- Contoso rendszergazdák rendelkeznek az identitások kezelésére a vendégfürtök, beleértve a létrehozási, új jelszó kérésekor, stb.

### <a name="alternative-option-2-create-a-custom-power-bi-embedded-application-using-custom-authentication"></a>Alternatív 2. lehetőség: Hozzon létre egy egyéni-hitelesítést használó egyéni Power BI Embedded-alkalmazások

A Contoso egy másik lehetőség az, hogy a saját egyéni beágyazott Power BI-alkalmazás létrehozása az egyéni hitelesítéssel (["Alkalmazás az adatok tulajdonosa"](https://docs.microsoft.com/power-bi/developer/embed-sample-for-customers)). Bár számos szervezet nincs ideje vagy erőforrása hozhat létre ahhoz, hogy külső partnerei tartalom terjesztése a Power BI egyéni alkalmazást, egyes szervezetek számára ez a legjobb módszer, amely szempont hozhatja létre.

Gyakran előfordul, a szervezet rendelkezik a meglévő partner portálok központosíthatja az összes szervezeti erőforrásokhoz való hozzáférés a partnerek számára, elkülönítését a belső vállalati erőforrásokhoz, és biztosít zökkenőmentes élményt partnerek számára, támogatja a számos partnere biztosít, és az egyes felhasználók.

![Számos partneri portálok](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_45.png)

Minden szállítói bejelentkezési felhasználóit a Contoso-Partner portálra a fenti példában az identitás-szolgáltatóként, amely használ aad-ben. Azt AAD B2B, az Azure B2C-vel, a natív identitások használhatja, vagy az egyéb identitás-szolgáltatóktól tetszőleges számú összevonni. A felhasználó jelentkezzen be és hozzáférés a partner portál hozhat létre Azure-webalkalmazás vagy egy hasonló infrastruktúra használatával.

A webalkalmazáson belül a Power BI-jelentéseket a Power BI Embedded telepítéséből beágyazott. A webalkalmazás lenne biztosít könnyű hozzáférést a jelentéseket, és megkönnyítik a Contoso interakcióba szállítók irányuló összefüggő élmény kapcsolódó szolgáltatásokat. A portál környezet különítve a Contoso belső AAD és a Contoso belső Power BI-környezetbe annak biztosítása érdekében a szállítók nem érhető el ezeket az erőforrásokat. Jellemzően adatok lennének tárolva egy külön Partner data warehouse annak biztosítására, valamint az adatok elkülönítését. Ez az elkülönítés előnye van, mert azt korlátozza a közvetlen hozzáférést a munkahelyi adatokat, a külső felhasználók korlátozása, hogy milyen adatok esetleg hiányozhat a külső felhasználók számára elérhető, és korlátozza a véletlen megosztása külső felhasználókkal.

Használja a Power BI Embedded, a portál kihasználhatják a legelőnyösebb licencelési, alkalmazás-jogkivonatára vagy a fő felhasználó- és prémium szintű kapacitás használata megvásárolt Azure modell, amely leegyszerűsíti a licencek hozzárendelése a végfelhasználók aggályait, és elvégezhetik a különféle skálázási/le-alapú a várt használat. Mivel a partnerek eléréséhez az összes egy partner által létrehozott igényeinek szem előtt készült egyetlen portál a portálon egy összességében jobb minőségű és egységes felhasználói élményt is kínálnak. Végül mivel a Power BI Embedded-alapú megoldások általában több-bérlős tervezték, lehetővé teszi, hogy könnyebb biztosítani, hogy a fiókpartner-szervezetek elkülönítését.

Ez a megoldás kiválasztásához okok:

- Könnyebben kezelhető, mint a fiókpartner-szervezetek száma növekszik. Partnerek vesznek fel egy külön könyvtárba, a Contoso belső AAD-címtárában elkülönítve, mert egyszerűbbé teszi az irányítási feladatokat, és segít megakadályozni, hogy a külső felhasználók számára a belső adatok véletlen megosztását.
- Tipikus Partner portálok magas egységes felületeket környezeteket márkás partnerek között, és hatékonyabbá tipikus partnerek igényeinek. Contoso ezért elérhetővé teheti egy jobban összteljesítmény partnerei számára az összes szükséges szolgáltatást egy portálon történő integrálásával.
- Licencelési költségeit a speciális alkalmazási szerkesztési tartalmakat a Power BI Embedded az Azure hatálya alá tartozik, mint a Power BI Premiumot vásárolta meg, és nem igényli a Power BI Pro-licencek felhasználókhoz hozzárendelését.
- Ha egy több-bérlős megoldásként tervezésnek biztosítja a jobb elkülönítése partnerek között.
- A Partnerportálon gyakran hozzátartozik, hogy más eszközök mellett a Power BI jelentések, irányítópultok és alkalmazások partner.

Ez a megoldás kiválasztása, nem okok:

- Jelentős erőfeszítéssel hozhat létre, működtetéséhez és karbantartásához, így jelentős befektetéseket erőforrással és idővel a portál.
- Megoldás ideje sokkal hosszabb, mint B2B megosztásakor gondos tervezés óta, és a végrehajtása több workstreams között szükség.
- Amennyiben a partnerek kisebb számú Ez a megoldás a szükséges munkát, valószínűleg túl nagy ahhoz, hogy adja meg.
- Együttműködés az ad hoc megosztása a szervezet által tapasztalható az elsődleges forgatókönyv.
- A jelentések és irányítópultok eltérőek az egyes partnerekhez. Ez a megoldás felügyeleti többletterhelést túli csak megosztása közvetlenül a partnerek mutatja be.



## <a name="faq"></a>Gyakori kérdések

**Contoso meghívót küldhet, amely automatikusan be, így a felhasználó csak "készen áll"? Vagy a felhasználó mindig rendelkezik, kattintással lépjen a beváltási URL-cím?**

A felhasználó a jóváhagyási felületen keresztül mindig kell kattintson a tartalom eléréséhez.

Ha a rendszer számos vendégfelhasználók meghívása, javasoljuk, hogy delegálni Ez a alapvető Azure AD-rendszergazdák által a [felhasználók hozzáadása az erőforrás-szervezet vendégmeghívói szerepköréhez](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-add-guest-to-role). Ez a felhasználó meghívhatja a a fiókpartner-szervezet többi felhasználója a bejelentkezési felhasználói felület használatával, PowerShell-szkriptek, vagy API-k. Ez csökkenti a felügyeleti megoldás az Azure AD-rendszergazdái ismerősök meghívásához vagy elküldésével meghívók a fiókpartner-szervezet felhasználói számára.

**Contoso kényszerítheti a többtényezős hitelesítést a vendégfelhasználók Ha partnerei nem rendelkeznek a multi-factor authentication?**

Igen. További információkért lásd: [feltételes hozzáférés B2B-együttműködés felhasználók](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-mfa-instructions).

**Hogyan működik a B2B-együttműködés a Ha a meghívott partner összevonási segítségével adja hozzá a saját helyszíni hitelesítéssel?**

Ha a partner van összevonva a helyszíni hitelesítési infrastruktúráját az Azure AD-bérlő, a helyszíni egyszeri bejelentkezés (SSO) automatikusan érhető el. Ha a partner Azure AD-bérlő nem rendelkezik, az Azure AD-fiókot az új felhasználók előfordulhat, hogy hozhatók létre.

**A fogyasztói e-mail-fiókokat vendégfelhasználókat is meghívhat?**

A Power bi-ban támogatott vendégfelhasználók a fogyasztói e-mail-fiókokat. Ez magában foglalja például hotmail.com, Outlook.com-os és a gmail.com tartományok. Azonban ezek a felhasználók találkozhatnak korlátozások mellett a felhasználók munkahelyi vagy iskolai fiókok észlel.
