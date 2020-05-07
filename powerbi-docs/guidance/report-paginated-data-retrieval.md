---
title: Adatlekérési útmutató lapszámozott jelentésekhez
description: Útmutató adatforrások és adatkészletek a Power BI lapszámozott jelentéseihez való létrehozásához.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: 067171f7ec74beccdb5a312c1cac5bbc6c87541f
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "79377650"
---
# <a name="data-retrieval-guidance-for-paginated-reports"></a>Adatlekérési útmutató lapszámozott jelentésekhez

Ez a cikk a [többoldalas](../paginated-reports/paginated-reports-report-builder-power-bi.md) Power BI-jelentéseket megtervező jelentéskészítők számára készült. Javaslatokat nyújt a hatékony adatlekéréshez.

## <a name="data-source-types"></a>Adatforrástípusok

A lapszámozott jelentések natív módon támogatják a relációs és elemzési adatforrásokat. Ezek a források tovább kategorizálhatók felhőalapúként vagy helyszíniként. A helyszíni adatforrások – akár a helyszínen, akár virtuális gépen üzemelnek – adatátjárót igényelnek a Power BI-kapcsolathoz. A felhőalapú szolgáltatás azt jelenti, hogy a Power BI közvetlenül, internetkapcsolattal csatlakozhat.

Ha ki tudja választani az adatforrás típusát (ami valószínű egy új projektnél), felhőalapú adatforrások használatát javasoljuk. A lapszámozott jelentések alacsonyabb hálózati késéssel képesek csatlakozni, különösen, ha az adatforrások a Power BI-bérlővel megegyező régióban találhatók. Emellett egyszeri bejelentkezéssel (SSO) is csatlakozhat ezekhez a forrásokhoz. Ez azt jelenti, hogy a jelentés felhasználójának identitása az adatforrásba áramlik, ami lehetővé teszi a felhasználónkénti sorszintű engedélyek kényszerítését. Az SSO jelenleg nem támogatott helyszíni adatforrásokon (az SQL Server Analysis Services tehát nem követelhet meg felhasználónkénti sorszintű engedélyeket).

> [!NOTE]
> Habár jelenleg nem lehetséges az SSO használatával csatlakozni a helyszíni adatbázisokhoz, továbbra is kikényszerítheti a sorszintű engedélyeket. Ehhez a beépített **UserID** mezőt kell elküldenie egy adatkészlet lekérdezési paraméterének. Az adatforrásnak úgy kell tárolnia az egyszerű felhasználónév (UPN) értékeit, hogy azok helyesen szűrjék a lekérdezési eredményeket.
>
> Vegyünk például egy olyan forgatókönyvet, amelyben minden értékesítő a **Salesperson** tábla egy sorát képviseli.  A táblázat oszlopai a UPN-t és az értékesítési régiókat tartalmazzák. A lekérdezéskor a jelentésfelhasználó UPN-je szűri a táblát, és egy belső összekapcsolással értékesítési tényekhez csatolja. A lekérdezés így az értékesítési ténysorokat a jelentésfelhasználó értékesítési régiója szerint szűri.

### <a name="relational-data-sources"></a>Relációs adatforrások

A relációs adatforrások általában műveleti stílusú jelentésekhez, például értékesítési számlákhoz használhatók ideálisan. Emellett olyan jelentésekhez is használhatók, amelyeknek rendkívül nagyméretű (több mint 10 000 soros) adatkészleteket kell lekérniük. A relációs adatforrások emellett tárolt eljárásokat is definiálhatnak, amelyeket a jelentés adatkészletei hajtanak végre. A tárolt eljárások számos előnnyel szolgálnak:

- Paraméterezés
- A programozási logika beágyazása, amellyel összetettebb adat-előkészítést végezhet (például ideiglenes táblákat, kurzorokat, vagy felhasználók által definiált skaláris függvényeket használhat)
- Jobb karbantarthatóság, amellyel könnyen frissíthetők a tárolt eljárások logikái. Bizonyos esetekben ez a lapszámozott jelentések módosítása és újbóli közzététele nélkül elvégezhető (amennyiben az oszlopnevek és az adattípusok nem változnak).
- Jobb teljesítmény, mivel a végrehajtási tervek gyorsítótárazhatók újbóli használathoz
- Tárolt eljárások újrafelhasználása több jelentésben

A Power BI-jelentéskészítő relációs lekérdezéstervezőjével grafikusan létrehozhat egy lekérdezési utasítást – azonban csak Microsoft-adatforrásokhoz.

### <a name="analytic-data-sources"></a>Elemzési adatforrások

Az elemzési adatforrások mind műveleti, mind elemzési jelentésekhez alkalmazhatók, és gyors összefoglaló lekérdezési eredményeket nyújtanak rendkívül nagy adatmennyiség esetén is. A modellmértékek és KPI-k összetett üzleti szabályokkal összegzik az adatokat. Ezek az adatforrások azonban olyan jelentésekhez nem használhatók, amelyeknek rendkívül nagyméretű (több mint 10 000 soros) adatkészleteket kell lekérniük.

A Power BI-jelentéskészítőben két lekérdezéstervező közül választhat: Az Analysis Services DAX lekérdezéstervező, illetve az Analysis Services MDX lekérdezéstervező közül. Ezek a tervezők Power BI-adatkészletek adatforrásaihoz, vagy bármilyen, SQL Server Analysis Services- vagy Azure Analysis Services-modellhez használhatók, legyen az táblázatos vagy többdimenziós.

Mi a DAX lekérdezéstervezőt ajánljuk, amennyiben teljes mértékben megfelel az Ön igényeinek. Ha a modell nem határozza meg a szükséges mértékeket, át kell váltania a lekérdezési módra. Ebben a módban kifejezések hozzáadásával szabhatja testre a lekérdezési utasítást (az összegzéshez).

Az MDX lekérdezéstervezőhöz mértékekkel rendelkező modellre van szükség. Ez a tervező két olyan funkcióval rendelkezik, amelyet a DAX lekérdezéstervező nem támogat. Segítségével a következőket végezheti el:

- Lekérdezésszintű számított tagok definiálása (az MDX-ben).
- Adatrégiók konfigurálása úgy, hogy azok [kiszolgálóösszesítéseket](/sql/reporting-services/report-design/report-builder-functions-aggregate-function) kérjenek nem részletes csoportokban. Ha a jelentésnek fél- vagy nem additív mértékeket kell bemutatnia (például időintelligencia-számításokat vagy az eltérők darabszámait), hatékonyabb kiszolgálóösszesítéseket használni, mint alacsony szintű sorokat lekérni, majd a jelentéssel kiszámíttatni az összesítéseket.

## <a name="query-result-size"></a>Lekérdezés eredményének mérete

Általában ajánlott csak a jelentéshez szükséges adatokat lekérni. Ne kérjen le tehát olyan oszlopokat vagy sorokat, amelyekre nincs szüksége a jelentésnek.

A sorok korlátozásához a lehető legszigorúbb szűrőket célszerű alkalmaznia, valamint meg kell szabnia összesítő lekérdezéseket. Az összesítő lekérdezések a forrásadatok csoportosításával és összefoglalásával kérnek le részletesebb eredményeket. Tegyük fel például, hogy a jelentésnek egy értékesítő értékesítéseinek összegzését kell bemutatnia. Az összes értékesítési megrendelés sorának lekérése helyett hozzon létre egy olyan adatkészlet-lekérdezést, amely értékesítő szerint csoportosít, az értékesítéseket pedig minden csoporthoz külön összefoglalja.

## <a name="expression-based-fields"></a>Kifejezésalapú mezők

A jelentés adatkészlete a kifejezéseken alapuló mezőkkel kiterjeszthető. Ha például az adatkészlet az ügyfél vezeték- és keresztnevét kéri le, célszerű lehet olyan mezőt használni, amely összefűzi a két mezőt, és így kiadja az ügyfél teljes nevét. Ehhez a számításhoz két lehetőség áll rendelkezésére. A következőket teheti:

- Hozzon létre egy _számított mezőt_, amely egy kifejezésen alapuló adatkészlet.
- Töltsön be egy kifejezést közvetlenül az adatkészlet lekérdezésébe (az adatforrás natív nyelvét használva), így egy hagyományos adatkészletmezőt kap.

Amikor csak lehet, alkalmazza a második lehetőséget. Annak, hogy miért jobb kifejezéseket közvetlenül az adatkészlet lekérdezésébe illeszteni, két nyomós oka van:

- Lehetséges, hogy az adatforrás úgy van optimalizálva, hogy hatékonyabban értékelje a kifejezést a Power BI-nál (ez különösen igaz a relációs adatbázisokra).
- A jelentésteljesítmény nő, mivel a Power BI-nak nem kell materializálnia a számított mezőket a renderelés előtt. A számított mezők jelentősen kiterjeszthetik a jelentés renderelési idejét, ha az adatkészletek számos sort kérnek le.

## <a name="field-names"></a>Mezőnevek

Adatkészlet létrehozásakor a rendszer automatikusan elnevezi a mezőket a lekérdezés oszlopai után. Lehetséges, hogy ezek a nevek nem felhasználóbarátak vagy intuitívak. Az is előfordulhat, hogy a forrás lekérdezésének oszlopnevei az RDL-objektumazonosítókban tiltott karaktereket (például szóközöket és szimbólumokat) tartalmaznak. Ebben az esetben a tiltott karakterek helyére egy aláhúzásjel (_) kerül.

Azt javasoljuk, hogy először ellenőrizze, hogy az összes mezőnév felhasználóbarát- és tömör-e, ám mégis értelmes. Ha nem, célszerű őket a jelentés elrendezésének kialakítása _előtt_ átneveznie őket. Ez azért van, mert az átnevezett mezők nincsenek hatással a jelentés elrendezésében használt kifejezésekre. Ha átnevezi a mezőket a jelentés elrendezésének kialakítása után, meg kell keresnie és frissítenie kell az összes hibás kifejezést.

## <a name="filter-vs-parameter"></a>Szűrő és paraméter

Valószínű, hogy a lapszámozott jelentéstervek jelentésparaméterekkel rendelkeznek. A jelentésparaméterek gyakran kérik a jelentésfelhasználótól a jelentés szűrését. A lapszámozott jelentés szerzőjeként Önnek két lehetősége van a jelentés szűrésére. A jelentésparamétereket a következőkre képezheti le:

- Egy adatkészlet _szűrője_. Ebben az esetben a jelentésparaméter értéke szűri az adatkészlet által már lekért adatokat.
- Egy adatkészlet _paramétere_. Ebben az esetben a jelentésparaméter értéke(i) betöltődik az adatforrásnak küldött natív lekérdezésbe.

> [!NOTE]
> A rendszer _munkameneti alapon_ gyorsítótárazza a jelentés minden adatkészletét _az utolsó használattól_ számított legfeljebb 10 percig. Az adatkészletek újra felhasználhatók új paraméterértékek megadásakor (szűréskor), a jelentés más formátumban történő renderelésekor, vagy a jelentésterv használatakor (például a láthatóság ki- és bekapcsolásakor vagy a rendezéskor).

Most vegyünk egy olyan példát, amelyben az értékesítési jelentés egyetlen jelentésparaméterrel szűri egyetlen évre a jelentést. Az adatkészlet az _összes év_ értékesítéseit lekéri. Ez azért történik, mert a jelentésparamétert az adatkészlet szűrőire képezi le. A jelentés megjeleníti a kért év adatait, amely az adatkészlet adatainak részhalmaza. Ha a jelentésfelhasználó egy másik évre módosítja a jelentésparamétert, majd megtekinti a jelentést, a Power BI-nak nem kell lekérnie forrásadatokat. Ehelyett egy másik szűrőt alkalmaz a már gyorsítótárazott adatkészletre. Az adatkészlet gyorsítótárazása után a szűrés rendkívül gyors.

Most vegyünk alapul egy másik jelentéstervet. Ezúttal a jelentésterv az értékesítési év jelentésparaméterét egy adatkészlet-paraméterre képezi le. A Power BI így betölti az év értékét a natív lekérdezésbe, az adatkészlet pedig csak erre az évre vonatkozóan kéri le az adatokat. Minden alkalommal, amikor a jelentésfelhasználó módosítja a jelentésparaméter értékét, majd megtekinti a jelentést, az adatkészlet egy új lekérdezési eredményt kér le csak erre az évre vonatkozóan.

Mindkét tervtípus szűrhet jelentésadatokat, és mindkét terv jól használható a jelentésekben. Egy optimalizált terv azonban az adatok várt mennyiségétől, változékonyságától és a jelentésfelhasználók várt viselkedéstől függ.

Azt javasoljuk, hogy alkalmazzon _adatkészletszűrést_, ha arra számít, hogy az adatkészlet sorainak egy eltérő részhalmazát sokszor újra fel fogja használni (és így renderelési időt takarít meg, mivel az új adatokat nem kell lekérni). Ebben a forgatókönyvben láthatja, hogy a nagyobb adatkészlet lekérésének költsége jobban megéri, mint az újrafelhasználások száma. Így ez hasznos lehet az időigényes lekérdezéseknél. Legyen azonban óvatos – a nagyméretű adatkészletek felhasználónkénti lekérdezése rossz hatással lehet a teljesítményre és a kapacitás átviteli sebességére.

Azt javasoljuk, alkalmazzon _adatkészlet-paraméterezést_ olyan esetekben, amikor várhatóan nem valószínű, hogy az adatkészlet sorainak egy másik részhalmaza lesz lekérve, vagy amikor az adatkészlet szűrendő sorainak száma várhatóan nagyon magas (és így nem hatékonyan gyorsítótárazható). Ez a tervezési megközelítés változékony adattár esetén is hasznos. Ilyen esetben a jelentésparaméter-értékek minden változása a friss adatok lekérését eredményezi.

## <a name="non-native-data-sources"></a>Nem natív adatforrások

Ha olyan adatforrásokon alapuló lapszámozott jelentéseket kell létrehoznia, amelyeket [nem támogatnak natív módon a lapszámozott jelentések](../paginated-reports/paginated-reports-data-sources.md), először kifejleszthet egy Power BI Desktop-adatmodellt. Így több mint 100 [Power BI-adatforráshoz csatlakozhat](../power-bi-data-sources.md). Miután közzétette a Power BI szolgáltatásban, olyan lapszámozott jelentést fejleszthet, amely a Power BI-adatkészlethez csatlakozik.

## <a name="data-integration"></a>Adatintegráció

Ha több adatforrásból kell adatokat egyesítenie, erre két módja van:

- **Jelentés adatkészleteinek egyesítése**: Ha az adatforrásokat [natív módon támogatják a lapszámozott jelentések](../paginated-reports/paginated-reports-data-sources.md), célszerű lehet olyan számított mezőket létrehozni, amelyek a [Lookup](/sql/reporting-services/report-design/report-builder-functions-lookup-function) vagy a [LookupSet](/sql/reporting-services/report-design/report-builder-functions-lookupset-function) jelentéskészítő-függvényeket használják.
- **Power BI Desktop-modell fejlesztése**: Ennél azonban hatékonyabb lehet, ha egy adatmodellt fejleszt a Power BI Desktopban. A Power Queryvel egyesítheti a lekérdezéseket bármilyen [támogatott adatforrás](../power-bi-data-sources.md) alapján. Miután közzétette a Power BI szolgáltatásban, olyan lapszámozott jelentést fejleszthet, amely a Power BI-adatkészlethez csatlakozik.

## <a name="sql-server-complex-data-types"></a>Az SQL Server összetett adattípusai

Mivel az SQL Server egy helyszíni adatforrás, a Power BI-nak egy átjárón keresztül kell csatlakoznia hozzá. Az átjáró azonban nem támogatja az összetett adattípusok adatainak lekérését. Az összetett adattípusok olyan beépített típusokat tartalmaznak, mint a GEOMETRY és a GEOGRAPHY [térbeli adattípusok](/sql/relational-databases/spatial/spatial-data-sql-server), valamint a [hierarchyid](/sql/t-sql/data-types/hierarchyid-data-type-method-reference) típust. Emellett a Microsoft.NET keretrendszer közös nyelvi futtatókörnyezetének egy szerelvényosztályával bevezetett felhasználói típusokat is tartalmazhatnak.

A térbeli adatok és elemzések a térképes vizualizáción való ábrázolásához az SQL Server térbeli adataira van szükség. Emiatt nem használhatja a térkép vizualizációt, ha az adatforrás az SQL Server. Azonban ha Azure SQL Database az adatforrás, működni fog, mert a Power BI nem egy átjárón keresztül kapcsolódik.

## <a name="data-related-images"></a>Adatokhoz kapcsolódó képek

A képekkel emblémákat vagy képeket helyezhet el a jelentés elrendezésében. Ha a képek egy jelentés adatkészlete által lekért sorokhoz kapcsolódnak, két lehetősége van:

- Lehetséges, hogy a képadatok az adatforrásból is lekérhetők (ha egy táblázatban találhatók).
- Ha a képek egy webkiszolgálón találhatók, egy dinamikus kifejezéssel létrehozhatja a kép URL-címét.

További információ és javaslatok: [Lapszámozott jelentések – útmutató a képekhez](report-paginated-image.md).

## <a name="redundant-data-retrieval"></a>Redundáns adatlekérés

Lehetséges, hogy a jelentés felesleges adatokat kér le. Ez olyankor fordulhat elő, ha Ön törli az adatkészlet lekérdezési mezőit, vagy a jelentés nem használt adatkészleteket tartalmaz. Kerülje ezeket a helyzeteket, mivel fölösleges terhet jelenthetnek az adatforrásoknak, a hálózatnak, és a Power BI-kapacitás-erőforrásoknak.

### <a name="deleted-query-fields"></a>Törölt lekérdezési mezők

Az **Adatkészlet tulajdonságai** ablak **Mezők** lapján törölheti a _lekérdezési mezőket_ (a lekérdezési mezők az adatkészlet lekérdezése által lekért oszlopokra vannak leképezve). A jelentéskészítő azonban nem távolítja el a megfelelő oszlopokat az adatkészlet lekérdezéséből.

Ha törölni szeretne lekérdezési mezőket az adatkészletből, azt javasoljuk, hogy távolítsa el a megfelelő oszlopokat az adatkészlet lekérdezéséből. A jelentéskészítő automatikusan eltávolít minden lekérdezésmezőt. Ha mégis törölne lekérdezésmezőket, gondoskodjon arról, hogy az adatkészlet lekérdezési utasítását is módosítsa az oszlopok eltávolításához.

### <a name="unused-datasets"></a>Nem használt adatkészletek

Egy jelentés futtatásakor a rendszer minden adatkészletet kiértékel, akkor is, ha azok nincsenek a jelentés objektumaihoz kötve. Emiatt ügyelnie kell arra, hogy a jelentések közzététele előtt minden tesztelési vagy fejlesztési adatkészletet eltávolítson.

## <a name="next-steps"></a>Következő lépések

Ezzel a cikkel kapcsolatosan a következő forrásanyagokban talál további információt:

- [A Power BI lapszámozott jelentéseihez használható támogatott adatforrások](../paginated-reports/paginated-reports-data-sources.md)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
- Javaslatai vannak? [A Power BI javítására vonatkozó ötletek beküldése](https://ideas.powerbi.com/)
