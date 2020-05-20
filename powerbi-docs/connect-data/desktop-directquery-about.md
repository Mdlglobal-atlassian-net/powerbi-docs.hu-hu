---
title: DirectQuery használata a Power BI-ban
description: A DirectQuery Power BI-beli használata, a DirectQuery használatát indokló helyzetek és más lehetőségek ismertetése
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/09/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: dfd44b7130c1c7e4e1d2d7a9c9f15208cb0d9b0c
ms.sourcegitcommit: a72567f26c1653c25f7730fab6210cd011343707
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/19/2020
ms.locfileid: "83563287"
---
# <a name="about-using-directquery-in-power-bi"></a>DirectQuery használata a Power BI-ban

Számos különböző adatforrást kapcsolhat össze a *Power BI Desktop* vagy a *Power BI szolgáltatás* használatával, és ezeket az adatkapcsolatokat többféleképpen is létrehozhatja. *Importálhat* adatokat a Power BI-ba, ez az adatok lekérésének leggyakoribb módja, vagy közvetlenül is csatlakozhat az eredeti forrásadattárban lévő adatokhoz, ez az eljárás *DirectQuery* néven ismert. Ez a cikk a DirectQuery szolgáltatás képességeit mutatja be:

* A DirectQuery különféle kapcsolódási lehetőségei
* Útmutatás arra vonatkozóan, hogy mikor érdemes megfontolni a DirectQuery használatát importálás helyett
* A DirectQuery használatának hátrányai
* Ajánlott eljárások a DirectQuery használatához

Az ajánlott eljárások alapján választhat az importálás és a DirectQuery használata között:

* Amikor csak lehetősége van rá, az adatokat érdemes importálni a Power BI-ba. Importálással kihasználhatók a Power BI nagy teljesítményű lekérdezési motorjának előnyei, valamint interaktív és teljes körű funkciókat biztosít.
* Ha szükséges célok nem érhetők el az adatok importálásával, fontolja meg a DirectQuery használatát. Ha például az adatok gyakran változnak, a jelentésekkel pedig a legfrissebb adatokat szeretné bemutatni, akkor valószínűleg a DirectQuery a legjobb választás. A DirectQuery használata azonban csak akkor megvalósítható, ha az alapul szolgáló adatforrások interaktív, 5 másodpercnél rövidebb lekérdezéseket biztosítanak a szokványos összesítő lekérdezésekhez, valamint képesek az ezáltal létrejött lekérdezési terhelés kezelésére. Ezenkívül érdemes alaposan megfontolni a DirectQuery használatára vonatkozó korlátozásokat.

A Power BI importáláshoz és DirectQueryhez kínált képességei is folyamatosan fejlődnek. A változás vonatkozik az importált adatok használatának rugalmasságára abban az értelemben, hogy az importálás több esetben legyen használható, valamint a DirectQuery használatával kapcsolatos hátrányok kiküszöbölésére is. A fejlesztésektől függetlenül a DirectQuery esetében az alapul szolgáló adatforrás teljesítménye mindig az első számú megfontolandó szempontok közé fog tartozni. Ha az alapul szolgáló adatforrás lassú, a DirectQuery használata ahhoz az adatforráshoz nem lesz megvalósítható.

Ez a cikk a DirectQuery és a Power BI együttes használatát tárgyalja, az *SQL Server Analysis Services* szolgáltatást nem. A DirectQuery ugyanakkor az SQL Server Analysis Services szolgáltatása is. A cikkben leírt részletek közül sok erre a szolgáltatásra is érvényes. Vannak azonban lényeges eltérések is. A DirectQuery és az SQL Server Analysis Services együttes használatról a [DirectQuery az SQL Server 2016 Analysis Servicesben](https://download.microsoft.com/download/F/6/F/F6FBC1FC-F956-49A1-80CD-2941C3B6E417/DirectQuery%20in%20Analysis%20Services%20-%20Whitepaper.pdf) című tanulmányban talál információt.

Ez a cikk a DirectQueryhez ajánlott munkafolyamatokra koncentrál, amely esetben a jelentés Power BI Desktopban jön létre, de a Power BI szolgáltatáshoz való közvetlen kapcsolódás témájával is foglalkozik.

## <a name="power-bi-connectivity-modes"></a>A Power BI kapcsolódási módjai

A Power BI rengeteg különféle adatforráshoz képes csatlakozni, többek között az alábbiakhoz:

* Online szolgáltatások (Salesforce, Dynamics 365 stb.)
* Adatbázisok (SQL Server, Access, Amazon Redshift stb.)
* Egyszerű fájlok (Excel, JSON stb.)
* Egyéb adatforrások (Spark, webhelyek, Microsoft Exchange stb.)

Ezen adatforrások esetén az adatok importálhatók a Power BI-ba. Néhány adatforráshoz a DirectQuery használatával is lehet kapcsolódni. A DirectQuery használatát támogató adatforrások összegzését a [DirectQuery által támogatott adatforrásokat](power-bi-data-sources.md) ismertető cikkben találja meg. A jövőben további források is elérhetőek lesznek a DirectQuery használatával. Ezek elsősorban olyan források lesznek, amelyek megfelelő teljesítményű, interaktív lekérdezésre képesek.

Az SQL Server Analysis Services speciális esetnek számít. Az SQL Server Analysis Serviceshez való kapcsolódáskor választhat az adatok importálása vagy az *élő kapcsolat* használata között. Az élő kapcsolatok használata a DirectQuery hasonló. A rendszer nem importál adatokat, és az alapul szolgáló adatforrást mindig lekérdezi a vizualizáció frissítéséhez. Az élő kapcsolat sok más szempontból egészen más, ezért külön fogalom az *élő kapcsolat* és a *DirectQuery*.

Az adatokhoz való kapcsolódás három lehetősége az *importálás*, a *DirectQuery* és az *élő kapcsolat*.

### <a name="import-connections"></a>Importálási kapcsolatok

Importáláskor, ha az **Adatok beolvasása** utasítást használja a Power BI Desktopban az adatforráshoz, például az SQL-kiszolgálóhoz való csatlakozáshoz, az adott kapcsolat működése a következő:

* Az adatbeolvasás kezdőfelületén kijelölt táblák mindegyike meghatároz egy lekérdezést, amely egy adathalmazt ad vissza. Ezek a lekérdezések az adatbetöltés előtt még módosíthatók például szűrőkkel, az adatok összesítésével vagy különböző táblák összekapcsolásával.
* Betöltéskor a rendszer a lekérdezések által meghatározott adatokat importálja a Power BI gyorsítótárába.
* A Power BI Desktopban egy vizualizáció létrehozásakor a rendszer lekéri az importált adatokat. A Power BI-tár biztosítja, hogy a lekérdezés gyors legyen. A vizualizáció minden módosítása azonnal megjelenik.
* A vizualizációk nem tükrözik a mögöttes adatok módosításait. Az adatimportálás megismétléséhez *ismételt frissítés* szükséges.
* Amikor a jelentés *.pbix* fájlként közzé van téve a Power BI szolgáltatásban, egy adathalmaz is létre lesz hozva és fel lesz töltve a Power BI szolgáltatásba. Az importált adatok ebbe az adatkészletbe kerülnek. Ezt követően lehetősége van az említett adatok ütemezett frissítésére, például az adatok naponta történő újraimportálására. Az eredeti adatforrás helyétől függően szükség lehet egy helyszíni adatátjáró konfigurálására.
* A meglévő jelentés Power BI szolgáltatásban való megnyitásakor vagy új jelentés létrehozásakor a rendszer az interaktivitás fenntartása érdekében ismét lekérdezi az importált adatokat.
* A vizualizációk vagy teljes jelentésoldalak csempék formájában kitűzhetők az irányítópultokra. A csempék automatikusan frissülnek az alapul szolgáló adathalmaz frissítésekor.

### <a name="directquery-connections"></a>DirectQuery-kapcsolatok

DirectQuery használatakor, ha az **Adatok beolvasása** utasítást használja a Power BI Desktopban az adatforráshoz való csatlakozáshoz, az adott kapcsolat működése a következő:

* Az Adatok betöltése kezdőfelületén ki kell választani a forrást. Relációs források esetén több tábla választható ki, amelyek mindegyike itt is meghatároz egy olyan lekérdezést, amely logikailag ad vissza egy adatkészletet. Többdimenziós források, például SAP BW esetén csak a forrás lesz kiválasztva.
* Betöltéskor azonban semmilyen adat nem lesz a Power BI-tárolóba importálva. Ehelyett a Power BI Desktopban egy vizualizáció létrehozásakor a rendszer a szükséges adatok lekéréséhez az alapul szolgáló adatforráshoz küldi a lekérdezést. A vizualizáció frissítéséhez szükséges idő a háttéradatforrás teljesítményétől függ.
* A mögöttes adatok módosításai nem jelennek meg azonnal a meglévő vizualizációkon. Azokat ebben az esetben is frissíteni kell. Az egyes vizualizációkhoz szükséges lekérdezések újra el lesznek küldve, és a vizualizáció szükség esetén frissítve lesz.
* A jelentés Power BI szolgáltatásban való közzétételekor az importáláshoz hasonlóan szintén létrejön egy adathalmaz a Power BI szolgáltatásban. Azonban ebbe az adatkészletbe *nem kerülnek adatok*.
* Meglévő jelentés a Power BI szolgáltatásban való megnyitásakor vagy új jelentés létrehozásakor a szükséges adatok lékéréséhez a rendszer ismét lekérdezi a mögöttes adatokat. Ahogyan importálás esetén, az eredeti adatforrás helyétől függően ebben az esetben is szükség lehet egy helyszíni adatátjáró konfigurálására az adatok frissítésekor.
* A vizualizációk vagy teljes jelentésoldalak csempék formájában kitűzhetők az irányítópultokra. Az irányítópult gyors megnyithatósága érdekében a csempék automatikusan, ütemezés szerint, például óránként frissülnek. A frissítés gyakorisága szabályozható, az adatok változásának gyakorisága, illetve az alapján, hogy mennyire fontos a legfrissebb adatok megjelenítése. Az irányítópult megnyitásakor a csempék az utolsó frissítésből származó adatokat fogják megjeleníteni, tehát az alapul szolgáló forrás legutóbbi változásai nem feltétlenül jelennek meg. A megnyitott irányítópultok frissíthetők, hogy biztosan aktuálisak legyenek.

### <a name="live-connections"></a>Élő kapcsolatok

Az SQL Server Analysis Services szolgáltatáshoz való kapcsolódáskor lehetőség van a kiválasztott adatmodell adatainak importálására, vagy az azokhoz való élő kapcsolódásra. Ha importálást használ, akkor egy lekérdezést határoz meg a külső SQL Server Analysis Services-forráshoz, a rendszer pedig a szokásos módon importálja az adatokat. Ha élő kapcsolatot használ, akkor nem határoz meg lekérdezést, és az egész külső modell megjelenik a mezők listájában.

Az előző bekezdésben leírt szituáció az alábbi forrásokhoz való csatlakozásra is vonatkozik, azzal a kivétellel, hogy nincs lehetőség az adatok importálására:

* Power BI-adathalmazok – például egy korábban létrehozott, és a szolgáltatásban közzétett Power BI-adathalmazhoz való kapcsolódáskor, az adatokra épülő új jelentés létrehozása esetén.
* Common Data Services.

Az SQL Server Analysis Services alapján létrehozott jelentések működése a Power BI szolgáltatásban való közzétételkor a következő szempontokból hasonlít a DirectQuery-jelentésekhez:

* Egy meglévő jelentés Power BI szolgáltatásban való megnyitásakor vagy új jelentés létrehozásakor a rendszer az alapul szolgáló SQL Server Analysis Servicesről kéri le az adatokat, amelyhez egy helyszíni adatátjáróra is szükség lehet.
* Az irányítópult csempéi automatikusan, ütemezés szerint frissülnek, például óránként.

Vannak azonban lényeges eltérések is. Például élő kapcsolatok esetén a jelentést megnyitó felhasználó identitása mindig át lesz adva a mögöttes SQL Server Analysis Services-forrásnak.

Az eddig leírt összehasonlítások után a cikk további része a DirectQuery használatával foglalkozik.

## <a name="when-is-directquery-useful"></a>Mikor hasznos a DirectQuery?

Az alábbi táblázat olyan helyzeteket foglal össze, amikor a DirectQueryvel való kapcsolódás kifejezetten hasznos lehet. Ide tartoznak azok az esetek is, amikor előnyösnek minősül meghagyni az adatokat az eredeti forrásban. A leírásban arról is szó lesz, hogy a bemutatott forgatókönyv elérhető-e a Power BI-ban.

| Korlátozás | Leírás |
| --- | --- |
| Az adatok gyakran változnak, és közel valós idejű jelentéskészítésre van szükség |Az importált adatokat tartalmazó modellek óránként legfeljebb egyszer frissíthetők (Power BI Pro vagy Power BI Premium előfizetéssel gyakrabban is). Ha az adatok folyamatosan változnak, és fontos, hogy a jelentések a legfrissebb adatokat jelenítsék meg, akkor előfordulhat, hogy az importálás és az ütemezett frissítés használata nem lesz elegendő. Az adatok közvetlenül is streamelhetők a Power BI-ba, bár ebben az esetben adatmennyiségi korlátozásokkal kell számolni. <br/> <br/> Ezzel ellentétben a DirectQuery használata azt jelenti, hogy egy jelentés vagy irányítópult megnyitásakor vagy frissítésekor mindig a forrásban szereplő legfrissebb adatok jelennek meg. Emellett az irányítópult csempéi gyakrabban, akár 15 percenként is frissíthetők. |
| Nagy méretű adatok |Nagy adattömeg esetén az összes adat betöltése nem volna megvalósítható. A DirectQueryvel viszont nincs szükség nagy mennyiségű adatátvitelre, mivel a lekérdezés helyben történik. <br/> <br/> Nagy adatmennyiség esetén azonban az is előfordulhat, hogy a mögöttes forrásra irányuló lekérdezések lassúak, amint ezt [A DirectQuery használatának következményei](#implications-of-using-directquery) című szakasz ismerteti. Nem mindig kell az összes részletes adatot importálni. Az adatok az importálás során előre összesíthetők. A *Lekérdezésszerkesztő* egyszerűvé teszi az importálás közbeni előzetes összesítést. Szélsőséges esetben lehetséges lenne minden vizualizációhoz pontosan a szükséges összesített adatokat importálni. Habár nagy mennyiségű adat feldolgozásának a DirectQuery a legegyszerűbb módja, az összesített adatok importálása is megoldás lehet, ha az alapul szolgáló adatforrás túl lassú. |
| A biztonsági szabályok meghatározása az alapul szolgáló adatforrásban történik |Az adatok importálásakor a Power BI a Power BI Desktopból az aktuális felhasználói hitelesítő adatokkal, a Power BI szolgáltatásból pedig az ütemezett frissítés részeként megadott hitelesítő adatokkal kapcsolódik az adatforráshoz. Ilyen jelentések közzétételekor és megosztásakor ügyelni kell arra, hogy csak olyan felhasználókkal osszuk meg a jelentést, akik jogosultak az adatok megtekintésére, vagy határozzunk meg sorszintű biztonságot az adathalmazban. <br/> <br/> Ideális esetben – mivel a DirectQuery mindig lekérdezi az alapul szolgáló forrást – ezzel a konfigurációval az adott forrás minden biztonsági intézkedése alkalmazható lenne. Azonban jelenleg a Power BI mindig az importáláshoz használt hitelesítő adatok használatával kapcsolódik az alapul szolgáló forráshoz. <br/> <br/> Amíg a Power BI nem teszi lehetővé, hogy a jelentés fogyasztójának identitása továbbítódjon a mögöttes forrás felé, addig a DirectQuery semmilyen előnyt nem nyújt az adatforrások biztonsága szempontjából. |
| Az adatok szuverenitására korlátozások vonatkoznak |Egyes intézmények az adatok szuverenitására vonatkozó szabályzatokat határoznak meg, ami azt jelenti, hogy az adatok nem hagyhatják el az intézmény területét. Egy importáláson alapuló megoldás bizonyosan problémákat okozna. Ezzel szemben a DirectQuery használatakor az adatok az alapul szolgáló forrásban maradnak. <br/> <br/> A csempék ütemezett frissítéséből adódóan azonban a vizualizáció szintjén gyorsítótárazott bizonyos adatok még a DirectQuery használata esetén is megmaradnak a Power BI szolgáltatásban. |
| Az alapul szolgáló adatforrás egy OLAP-forrás, amely mértékeket tartalmaz |Ha a mögöttes adatforrás *mértékeket* tartalmaz, mint például az SAP HANA vagy az SAP Business Warehouse, akkor az adatok importálása további problémákat is felvet. Ez azt jelenti, hogy a rendszer az adatokat egy bizonyos összesítési szinten importálja, ahogy azt a lekérdezés meghatározza. Ilyen mérték például a **TotalSales** (Összes értékesítés) **osztály**, **év** és **város** szerint. Ebben az esetben, ha létrehozunk egy vizualizációt, amely egy magasabb összesítési szinten kér adatokat (például **összes értékesítés** **év** szerint), az még tovább összesíti az összesített értéket. Az ilyen összesítés additív mértékeknél (például **Sum**, **Min**) nem okoz gondot, de problémát jelent a nem additív mértékeknél (például **Average**, **DistinctCount**). <br/> <br/> Hogy könnyebb legyen az adott vizualizációhoz szükséges megfelelő összesített adatokat közvetlenül a forrástól lekérni, a lekérdezéseket vizualizációnként kellene elküldeni, mint a DirectQueryben. <br/> <br/> Egy SAP Business Warehouse (BW) forráshoz való kapcsolódáskor a DirectQuery használatával lehetővé válik a mértékek ily módon való kezelése. Az SAP BW-vel kapcsolatban a [DirectQuery és az SAP BW](desktop-directquery-sap-bw.md) című cikk nyújt további információt. <br/> <br/> Az SAP HANA-val használt DirectQuery azonban jelenleg ugyanúgy kezeli, mint egy relációs forrást, és importáláskor ugyanúgy is viselkedik. Ennek működéséről bővebben a [DirectQuery és az SAP HANA](desktop-directquery-sap-hana.md) témakörben olvashat. |

Összegezve, a Power BI-ban a DirectQuery képességeit a következő helyzetekben kínálnak előnyt:

* Az adatok gyakran változnak, és közel valós idejű jelentéskészítésre van szükség.
* A kezelt adatok mennyisége rendkívül nagy, előzetes összesítésre nincs szükség.
* Az adatok szuverenitására korlátozások vonatkoznak.
* A forrás egy többdimenziós forrás, amely mértékeket tartalmaz (például az SAP BW).

Az előző lista részletei csak a Power BI használatára vonatkoznak. Az adatimportáláshoz ehelyett külső SQL Server Analysis Services- vagy Azure Analysis Services-modellt is használhat. Ehhez a modellhez csatlakozhat aztán a Power BI-jal. Habár ez a módszer több konfigurálást igényel, ugyanakkor nagyobb rugalmasságot is biztosít. Sokkal nagyobb mennyiségű adat importálható. Az adatfrissítés gyakorisága nem korlátozott.

## <a name="implications-of-using-directquery"></a>A DirectQuery használatának következményei

A DirectQuery használata negatív következményekkel is járhat, amelyeket ez a szakasz ismertet. Ezen korlátozások némelyike kis mértékben különbözhet az itt leírtaktól, a pontos használt forrástól függően. Adott esetben a témakör foglalkozik a korlátozásokkal, a jelentősen különböző forrásokat pedig külön cikkek ismertetik.

### <a name="performance-and-load-on-the-underlying-source"></a>Az alapul szolgáló forrás teljesítménye és terhelése

A DirectQuery használatakor az összteljesítmény nagyban függ a mögöttes adatforrás teljesítményétől. Ha az egyes vizualizációk frissítése például egy szeletelő-érték megváltoztatása után rövid ideig, általában kevesebb mint 5 másodpercig tart, akkor ez lehet az ésszerű megoldás. A felület lassúnak tűnhet az azonnali válaszhoz képest, amilyet az adatok Power BI-ba importálása esetén ad. Ha a forrás lassúsága miatt az egyes vizualizációk frissítése több tíz másodpercet vesz igénybe, akkor a felület kezelése rendkívül nehézkessé válik. A lekérdezések akár meg is szakadhatnak időtúllépés miatt.

A mögöttes forrás teljesítménye mellett a forrásra háruló terhelést is számításba kell venni. A terhelés befolyásolja a teljesítményt. Minden felhasználó, aki megosztott jelentést nyit meg, és minden frissülő irányítópult-csempe vizualizációnként legalább egy lekérdezést küld a mögöttes forrásnak. Emiatt szükséges, hogy a forrás kezelni tudjon egy ekkora lekérdezés-terhelést, miközben továbbra is megfelelő teljesítményt nyújt.

### <a name="security-implications-when-combining-data-sources"></a>Az adatforrások egyesítésének biztonsági vonatkozásai

Egy DirectQuery-modellben, ahogyan adatok importálásakor is, több adatforrást is használhat az [Összetett modellek](../transform-model/desktop-composite-models.md) funkcióval. Több adatforrás használata esetén fontos tisztában lenni a mögöttes adatforrások közötti adatforgalommal, valamint ennek [biztonsági vonatkozásaival](../transform-model/desktop-composite-models.md#security-implications).

### <a name="limited-data-transformations"></a>Korlátozott adatátalakítások

Hasonlóképp korlátozások vonatkoznak a Lekérdezésszerkesztőben elvégezhető adatátalakításokra is. Az importált adatok esetében egyszerűen alkalmazhatók olyan átalakítások, amelyek megtisztítják és átformálják az adatokat egy olyan vizualizáció létrehozása előtt, mint a JSON-dokumentumok feldolgozása, vagy egy oszlop adatainak sor formában való feldolgozása. Ezek az átalakítások korlátozottabbak a DirectQueryben.

Először is az OLAP-forrásokhoz, például az SAP Business Warehouse-hoz való kapcsolódáskor egyáltalán nem lehet átalakításokat meghatározni, a rendszer a forrás teljes külső modelljét átveszi. A relációs források, például az SQL Server esetében meg lehet adni átalakításokat lekérdezéseként, de teljesítmény érdekében ezek is korlátozottak.

Minden ilyen átalakítást a mögöttes forrás minden egyes lekérdezésénél alkalmazni kell ahelyett, hogy egyszerre, az adatok frissítésekor alkalmaznánk őket, ezért aztán csak azok az átalakítások használhatók, amelyek lefordíthatók egyetlen natív lekérdezésre. A túl összetett átalakítási műveletek egy hibaüzenetet eredményeznek, amely szerint vagy törölni kell az átalakítást, vagy a modellt át kell váltani Importálás módba.

Emellett az **Adatok betöltése** párbeszédpanelen vagy a Lekérdezésszerkesztővel létrehozott lekérdezések a létrehozott és a vizualizációhoz szükséges adatok lekérése céljából elküldött lekérdezések egy részkiválasztásában lesznek használva. A Lekérdezésszerkesztőben megadott lekérdezéseknek érvényesnek kell lenniük ebben a kontextusban. Nem használhatók tehát az olyan lekérdezések, amelyek közös táblakifejezéseket használnak vagy tárolt eljárásokat hívnak meg.

### <a name="modeling-limitations"></a>Modellezési korlátozások

A *modellezés* kifejezés ebben a kontextusban a nyers adatok pontosítását és bővítését jelenti, egy jelentés létrehozása keretében. Példák:

* Táblák közti kapcsolatok meghatározása
* Új számítások hozzáadása (számított oszlopok és mértékek)
* Oszlopok és mértékek átnevezése és elrejtése
* Hierarchiák meghatározása
* Egy oszlop formázásának, alapértelmezett összegzésének és rendezési sorrendjének meghatározása
* Értékek csoportosítása vagy fürtösítése

A DirectQuery használatával ezen modellbővítések nagy részét el lehet végezni, és természetesen érvényes a nyers adatok bővítésének elve, a későbbi fogyaszthatóság javítása céljából. Ugyanakkor bizonyos modellezési funkciók vagy nem, vagy csak korlátozottan érhetők el a DirectQuery használatakor. A korlátozások általánosságban a teljesítményproblémák elkerülését szolgálják. A minden DirectQuery-forrásra egységesen jellemző korlátozásokat a következő felsorolás ismerteti. Egyes forrásokra további korlátozások is vonatkozhatnak a [Következő lépések](#next-steps) című szakaszban leírtak szerint.

* **Nincs beépített dátumhierarchia:** Az adatok importálásakor minden dátum- és dátum/idő-oszlop rendelkezik egy beépített dátumhierarchiával. Például ha importálunk egy megrendeléseket tartalmazó táblát, amely tartalmaz egy **OrderDate** (Megrendelés dátuma) oszlopot, majd ezt az **OrderDate** oszlopot felhasználjuk egy vizualizációhoz, akkor kiválasztható lesz a vizualizációban használandó szint (év, hónap, nap). DirectQuery használatakor ez a beépített dátumhierarchia nem elérhető el. Ha a mögöttes forrásban van egy elérhető **Date** (Dátum) tábla, ami az adattárházak körében gyakori, akkor a DAX Időintelligencia függvények a szokott módon használhatók.
* **Dátum és idő legfeljebb másodperces precizitással támogatott:** Ha az adathalmazban idő jellegű oszlopok szerepelnek, a Power BI csak másodperces részletességű lekérdezéseket végez a mögöttes forráson. Az ezredmásodpercekre vonatkozó lekérdezések nem lesznek a DirectQuery-forráshoz továbbítva. Az időértéknek ezt a részét el kell távolítani a forrásoszlopokból.
* **Számított oszlopok korlátozásai:** A számított oszlopoknak soron belülinek kell lenniük, azaz csak ugyanazon tábla más oszlopainak értékeire hivatkozhatnak, összesítési függvények használata nélkül. A DAX megengedett skalárfüggvényei, amilyen a `LEFT()`, a mögöttes forráshoz leküldhető funkciókra vannak korlátozva. Ezek a funkciók a forrás pontos képességeitől függően változhatnak. A nem támogatott függvények nincsenek felsorolva az automatikus kiegészítési lehetőségek között a számított oszlop DAX-függvényeinek szerkesztésekor, és ha használni próbálja őket, hibát eredményeznek.
* **A szülő–gyermek DAX-függvények nem támogatottak:** A DirectQuery modellben nem használható a `DAX PATH()` függvénycsalád, amely általában a szülő–gyermek struktúrákat kezeli például fiókok ábrázolásakor vagy az alkalmazotti hierarchiákban.
* **A számított táblák nem támogatottak:** A DirectQuery módban a számított táblák DAX-kifejezéssel történő meghatározása nem támogatott.
* **Kapcsolatszűrés:** További információ a kétirányú szűrésről: [Kétirányú keresztszűrés](https://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx). Ez a tanulmány SQL Server Analysis Services-környezetben mutat be példákat. Az alapvető szempontok a Power BI-ra is ugyanúgy érvényesek.
* **Nincs fürtszolgáltatás:** DirectQuery használatakor nem használható a Fürtszolgáltatás funkció csoportok automatikus megkereséséhez.

### <a name="reporting-limitations"></a>Jelentéskészítési korlátozások

A DirectQuery-modellek majdnem minden jelentéskészítési funkciót támogatnak. Ennélfogva amíg az alapul szolgáló forrás megfelelő teljesítményt nyújt, addig ugyanazok a vizualizációk használhatók. Egy jelentés közzététele után néhány fontos korlátozás vonatkozik a Power BI szolgáltatás egyes további képességeire:

* **A gyors elemzések nem támogatottak:** A Power BI Quick Insights kifinomult algoritmusok alkalmazásával részhalmazokat keres az adatkészletben potenciálisan érdekes összefüggések feltárásához. A nagy lekérdezési teljesítmény igénye miatt a DirectQuery használatakor ez a lehetőség nem használható az adathalmazokon.
* **A Q&A nem támogatott:** A Power BI Q&A szolgáltatása lehetővé teszi az adatok felderítését intuitív, természetes nyelvi képességek segítségével, majd diagramok és grafikonok formájában adja meg válaszokat. Ez azonban a DirectQueryt használó adathalmazok esetében jelenleg nem támogatott.
* **Az Excelbeli kezelés feltehetően gyenge teljesítményt eredményez:** Egy adathalmaz adatai a Kezelés az Excelben képesség használatával is kezelhetők. Ez lehetővé teszi kimutatástáblák és kimutatásdiagramok létrehozását az Excelben. Noha a DirectQuery támogatja e képesség használatát az adathalmazokon, a teljesítmény általánosságban lassabb lesz tőle, mintha a vizualizációkat a Power BI-ban hoznánk létre. Ennélfogva ha az Excel használata fontos az Ön forgatókönyvei számára, akkor számoljon ezzel a tényezővel, amikor a DirectQuery használata mellett vagy ellen dönt.

### <a name="security"></a>Biztonság

Ahogy a cikk korábbi része is említette, a DirectQueryt használó jelentések mindig ugyanazokat a rögzített hitelesítő adatokat használják a mögöttes adatforrás eléréséhez a Power BI szolgáltatásban való közzététel után. Ez a viselkedés a DirectQueryre vonatkozik, nem az SQL Server Analysis Serviceshez létesített élő kapcsolatokra, amelyek ebből a szempontból eltérőek. Közvetlenül egy DirectQuery-jelentés közzététele után meg kell adni a használandó felhasználó hitelesítő adatait. Amíg a hitelesítő adatok konfigurálása nem történik meg, a jelentés megnyitása a Power BI szolgáltatásban hibát fog eredményezni.

A hitelesítő adatok megadását követően a rendszer mindig ezeket a hitelesítő adatokat használja, *bármelyik felhasználó nyitja meg a jelentést*. Ebből a szempontból az adatimportálással azonos. Minden felhasználó ugyanazokat az adatokat látja, kivéve akkor, ha a jelentés részeként sorszintű biztonság van megadva. A jelentés megosztásakor tehát ugyanúgy figyelni kell arra, hogy vannak-e biztonsági szabályok megadva a mögöttes forrásban.

### <a name="behavior-in-the-power-bi-service"></a>Viselkedés a Power BI szolgáltatásban

Ez a szakasz a DirectQuery-jelentések viselkedését írja le a Power BI szolgáltatásban, hogy érthetővé tegye a háttérbeli adatforrás terhelésének mértékét, figyelembe véve, hogy a jelentés és az irányítópult hány felhasználóval lesz megosztva, hogy a jelentés mennyire összetett, és hogy a jelentésben van-e meghatározva sorszintű biztonság.

#### <a name="reports--opening-interacting-with-editing"></a>Jelentések – megnyitás, használat, szerkesztés

Egy jelentés megnyitásakor az éppen látható oldalon található összes vizualizáció frissül. Általában mindegyik vizualizáció legalább egy lekérdezést igényel a mögöttes forrás felé. Bizonyos vizualizációkhoz több lekérdezés is szükséges lehet. Egy vizualizáció szemléltetheti például két különböző ténytábla összesített értékeit, tartalmazhat egy összetettebb mértéket, vagy tartalmazhatja olyan nem additív mértékek összegeit, mint az Eltérők darabszáma. Új oldalra való átlépéskor ezek a vizualizációk frissülnek. A frissítés új lekérdezéseket küld a mögöttes forráshoz.

A jelentéssel kapcsolatos minden felhasználói interakció a vizualizációk frissítését eredményezheti. Ha például egy másik értéket választunk ki egy szeletelőn, ahhoz új lekérdezéseket kell elküldeni az összes érintett vizualizáció frissítése céljából. Ugyanez igaz akkor is, ha rákattintunk egy vizualizációra egy másik vizualizáció keresztkiemeléséhez, vagy módosítunk egy szűrőt.

Emellett az új jelentés szerkesztésének minden lépésénél is új lekérdezéseket kell elküldeni a végső vizualizáció létrehozásához.

Az eredmények bizonyos mértékig gyorsítótárazva vannak. Ha egy lekérdezésnek már megvannak ugyanezek az eredményei, akkor a vizualizáció azonnal frissül. Ha nincs meghatározva sorszintű biztonság, akkor az ilyen gyorsítótárak nincsenek megosztva a felhasználók között.

#### <a name="dashboard-refresh"></a>Irányítópult frissítése

Egy-egy vizualizáció vagy teljes oldalak is kitűzhetők az irányítópultokra csempék formájában. A DirectQuery-adathalmazokon alapuló csempék az ütemezésnek megfelelően automatikusan frissülnek. A csempék lekérdezéseket küldenek a háttérbeli adatforráshoz. Az adathalmazok alapértelmezés szerint óránként egyszer frissülnek, de az adathalmaz beállításai között időintervallumok széles skálája megadható, egy héttől 15 percig.

Ha a modell nem tartalmaz sorszintű biztonságot, akkor a rendszer minden csempét egyszer frissít, az eredményeket pedig megosztja az összes felhasználóval. Ellenkező esetben a számok szorzódhatnak. Minden csempének felhasználónként külön lekérdezést kell küldenie a mögöttes adatforráshoz.

Egy 10 csempéből álló, 100 felhasználóval megosztott irányítópult, amely a DirectQueryvel és sorszintű biztonsággal lett létrehozva, és 15 percenkénti frissítésre van konfigurálva, 15 percenként legalább 1000 lekérdezést küld a háttérkiszolgáló felé.

A sorszintű biztonság használatát és a frissítési ütemezés konfigurálását gondosan mérlegelni kell.

#### <a name="time-outs"></a>Időtúllépés

A Power BI szolgáltatásban az egyes lekérdezésekre 4 perces időtúllépési korlát van érvényben. Az ennél tovább tartó lekérdezések sikertelenek. Ismételten és hangsúlyozottan javasoljuk, hogy a DirectQueryt a közel interaktív lekérdezési teljesítményt biztosító forrásokhoz használja. Ennek a korlátozásnak a célja a túl nagy végrehajtási időből eredő problémák megelőzése.

### <a name="other-implications"></a>Egyéb következmények

A DirectQuery használatának egyéb általános következményei közé tartoznak a következők:

* **Az adatok módosítása esetén a legújabb adatok megjelenítéséhez frissítés szükséges:** A gyorsítótárak használata miatt nem biztosítható, hogy a vizualizáció mindig a legfrissebb adatokat jelenítse meg. Mutathatják például az elmúlt egy nap tranzakcióit. Egy szeletelő módosítása következtében frissülhet úgy, hogy az utolsó két nap tranzakcióit mutassa. A tranzakciók között teljesen új, frissen érkezett tranzakciók is megjelenhetnek. Ha a szeletelőt visszaállítjuk az eredeti értékére, akkor újra a korábban gyorsítótárazott értéket fogja mutatni.

  A **Frissítés** kiválasztása törli a gyorsítótárakat és frissíti az oldalon található vizualizációkat, így a legújabb adatokat jelennek meg.

* **Változó adatok esetén a vizualizációk közötti konzisztencia nem garantálható:** Az azonos vagy külön oldalon lévő különböző vizualizációk más időpontban frissülhetnek. A mögöttes forrás változásakor nincs garancia arra, hogy minden vizualizáció ugyanarra az időpontra vonatkozó adatokat mutat. Sőt, tekintve, hogy néha egyetlen vizualizációhoz is több lekérdezés szükséges például a részletek és az összegek lekéréséhez, még az egyes vizualizációkon belüli konzisztencia sem garantált. Garantált konzisztenciához arra lenne szükség, hogy bármely vizualizáció frissítésekor az összes vizualizáció frissüljön, az olyan költséges funkciókkal együtt, mint a pillanatkép-elkülönítés a mögöttes adatforrásban.

  E probléma jelentősen enyhíthető a **Frissítés** újbóli választásával, mellyel az adott oldalon található összes vizualizáció frissíthető. A konzisztencia biztosítása még Importálás módban is hasonlóan problémás, ha egynél több táblából importálunk adatokat.

* **A metaadatok változásainak megjelenéséhez a Power BI Desktopban végzett frissítés szükséges:** Egy jelentés közzététele után a **Frissítés** művelet a jelentésbeli vizualizációkat frissíti. Ha a mögöttes forrás sémája megváltozott, akkor a változások nem módosítják automatikusan a mezőlistában elérhető mezőket. Ha a forrásból táblák vagy oszlopok lettek eltávolítva, az a lekérdezés sikertelenségéhez vezethet frissítéskor. A jelentés megnyitása a Power BI Desktopban és a **Frissítés** parancs kiválasztása úgy frissíti a mezőket a modellben, hogy tükrözzék a változásokat.

* **Bármely lekérdezésre legfeljebb 1 millió sor adható vissza:** Van egy olyan korlátozás, hogy legfeljebb 1 millió sor adható vissza a mögöttes forrás felé irányuló minden önálló lekérdezésre. Ennek a korlátozásnak általában semmilyen gyakorlati következménye nincs, mivel a vizualizációk nem jelenítenek meg ennyi pontot. A korlátozás érvényesülhet azonban olyan esetben, amikor a Power BI nem optimalizálja teljesen az elküldött lekérdezéseket, és valamilyen köztes eredményt kérdez le, amely meghaladja ezt a határértéket. Előfordulhat még vizualizációk létrehozása közben is, a vizualizációk végső állapotának elérése előtt. Például a **Customer** (Ügyfél) és a **TotalSalesQuantity** (Értékesítések teljes száma) belefoglalásával beteljesül a határérték, ha több mint egymillió ügyfél szerepel a forrásban, hacsak nem alkalmazunk valamilyen szűrőt.

  A visszaadott hiba a következő lesz: A külső adatforráshoz intézett lekérdezés eredményhalmaza meghaladta az 1000000 maximális sorszámot.

* **Nem lehet az importálásról DirectQuery módra váltani:** Habár általánosságban át lehet váltani egy modellt a DirectQuery módból az importálási mód használatára, de ez azzal jár, hogy az összes szükséges adatot importálni kell. Ezenkívül visszaváltani sem lehet, elsősorban a DirectQuery módban nem támogatott funkciók miatt. A többdimenziós forrásokkal, például az SAP BW-vel használt DirectQuery-modelleket szintén nem lehet átváltani DirectQuery módból importálási módba, a külső mértékek eltérő kezelése miatt.

## <a name="directquery-in-the-power-bi-service"></a>DirectQuery a Power BI szolgáltatásban

A Power BI Desktop által támogatott összes forrás támogatott. Egyes források elérhetők közvetlenül a Power BI szolgáltatásból is. Az üzleti felhasználók például megtehetik, hogy a Power BI segítségével kapcsolódnak a Salesforce-ban található adataikhoz, és azonnal lekérnek egy irányítópultot, a Power BI Desktop használata nélkül.

A DirectQueryt támogató források közül csak kettő érhető el közvetlenül a szolgáltatásban:

* Spark
* Azure SQL Data Warehouse

Ajánlott azonban az ezzel a két forrással kapcsolatos bármilyen DirectQuery-műveletet a Power BI Desktopból elindítani. Ezt az indokolja, hogy a Power BI szolgáltatásból kezdeményezett kapcsolódás esetén több lényeges korlátozás is érvényesül. Habár a Power BI szolgáltatásban egyszerű elindulni, a keletkező jelentés továbbfejlesztésének lehetőségei korlátozottak. Ilyenkor nem lehetséges például számításokat létrehozni, és sok elemzési funkció sem használható, ahogyan a metaadatoknak a mögöttes séma változásainak tükrözése érdekében végzett frissítése sem.

## <a name="guidance-for-using-directquery-successfully"></a>Útmutatás a DirectQuery sikeres használatához

Ha a DirectQuery mellett dönt, akkor ebben a szakaszban útmutatást talál annak használatáról. A szakaszban található útmutatás a DirectQuery használatának jelen cikkben leírt következményeiből van levezetve.

### <a name="back-end-data-source-performance"></a>Háttérrendszeri adatforrások teljesítménye

Ellenőrizze, hogy az egyszerű vizualizációk ésszerű időn belül frissíthetők. A kellően interaktív munkavégzéshez a frissítésnek 5 másodpercen belül meg kell történnie. Ha a vizualizációk frissítése 30 másodpercnél több időt vesz igénybe, akkor minden bizonnyal további problémák is fel fognak lépni a jelentés közzétételét követően. Ezek a problémák használhatatlanná tehetik a megoldást.

Ha a lekérdezések lassúak, vizsgálja meg a mögöttes forráshoz küldött lekérdezéseket, és a lekérdezés gyenge teljesítményének okait. A jelen cikk nem tartalmazza az összes lehetséges mögöttes forrásra vonatkozó számos ajánlott adatbázis-optimalizálási eljárást. Leírja viszont a legtöbb esetben érvényes szabványos adatbázis-kezelési eljárásokat:

* Az egész számokat tartalmazó oszlopokon alapuló kapcsolatok általában jobban teljesítenek, mint az egyéb adattípusú oszlopok közötti kapcsolatok.
* Létre kell hozni a megfelelő indexeket. Az indexek létrehozása általában az oszloptárindexek használatát jelenti azon forrásokban, amelyek támogatják ezeket, például az SQL Serveren.
* Frissíteni kell minden szükséges statisztikát a forrásban.

### <a name="model-design-guidance"></a>Modelltervezési útmutatás

A modell definiálása során vegye figyelembe az alábbi útmutatást:

* **Kerülje az összetett lekérdezéseket a Lekérdezésszerkesztőben.** A Lekérdezésszerkesztő egyetlen SQL-lekérdezésre fordít le egy összetett lekérdezést. Ez az egyszerű lekérdezés az adott táblára vonatkozó összes lekérdezés beágyazott select utasításaként jelenik meg. Ha ez a lekérdezés túl összetett, az rossz hatással lehet az összes elküldött lekérdezés teljesítményére. A több lépésre vonatkozó SQL-lekérdezéseket lekérheti, ha a Lekérdezésszerkesztőben az utolsó lépésnél kiválasztja a helyi menüből a **Natív lekérdezés megtekintése** lehetőséget.
* **Használjon egyszerű mértékeket.** A mértékeket érdemes legalább eleinte egyszerű összesítésekre korlátozni. Ha ezek megfelelően működnek, később összetettebb mértékeket is megadhat, de mindegyiknek figyeljen a teljesítményére.
* **Kerülje a számított oszlopokra mutató kapcsolatokat.** Ez az ajánlás olyan adatbázisokra vonatkozik, ahol többoszlopos kapcsolatokat kell használni. A Power BI jelenleg nem engedi, hogy a kapcsolatok több oszlopon alapuljanak – mint a Külső kulcs/Elsődleges kulcs. A leggyakoribb megkerülő megoldás az oszlopok összefűzése egy számított oszlop használatával, majd kapcsolódás ehhez az oszlophoz. Bár ez a kerülő megoldás importált adatok esetén járható út, a DirectQuery esetében egy kifejezésen alapuló kapcsolatot eredményez. Ez általában meggátolja az indexek használatát, és gyenge teljesítményhez vezet. Az egyetlen valós megoldás az, ha a több oszlopot az alapul szolgáló adatbázisban vonjuk össze egyetlen oszlopba.
* **Kerülje a uniqueidentifier típusú oszlopokra mutató kapcsolatokat.** A Power BI nem támogatja natív módon a `uniqueidentifier` adattípust. Ezért ha egy `uniqueidentifier` típusú oszlophoz adunk meg egy kapcsolatot, az egy olyan lekérdezést eredményez, amelyben egy kapcsolat egyik tagja explicit típuskonverziót végez. Ez általában szintén gyenge teljesítményt eredményez. Amíg nem kerül sor ennek az esetnek a külön optimalizálására, az egyetlen megkerülő megoldás az lesz, ha az alapul szolgáló adatbázisban más típust adunk meg az oszlopokhoz.
* **Rejtse el a céloszlopot a kapcsolatokban.** A kapcsolatok *céloszlopa* általában a *céltábla* elsődleges kulcsa. Ezt az oszlopot érdemes elrejteni. Ha rejtve van, nem jelenik meg a mezőlistában, és nem használható vizualizációkban. A kapcsolatok alapjául szolgáló oszlopok valójában gyakran *rendszeroszlopok*, például helyettesítő kulcsok egy adattárházban. Az ilyen oszlopokat eleve érdemes elrejteni. Ha az oszlopnak van jelentése, akkor hozzon létre egy látható számított oszlopot, amely egy, az elsődleges kulccsal egyenlő egyszerű kifejezést tartalmaz, ahogyan a következő példában látható:

  ```sql  
      ProductKey_PK   (Destination of a relationship, hidden)
      ProductKey (= [ProductKey_PK],   visible)
      ProductName
      ...
  ```

* **Vizsgálja meg a számított oszlopok és az adattípus-módosítások összes felhasználását.** Ezeknek a képességeknek a használata nem feltétlenül hátrányos. Tény, hogy ezek miatt a mögöttes forráshoz küldött lekérdezések egyszerű oszlophivatkozások helyett kifejezéseket tartalmaznak. Ez is az indexek használatának mellőzésével járhat.
* **Kerülje a kétirányú keresztszűrés használatát a kapcsolatokban.** A kétirányú keresztszűrés használata olyan lekérdezési utasításokhoz vezethet, melyek teljesítménye nem megfelelő.
* **Kísérletezzen a *Hivatkozási integritás feltételezése* beállítással.** A kapcsolatok Hivatkozási integritás feltételezése beállítása lehetővé teszi, hogy a lekérdezések `INNER JOIN` utasításokat használjanak az `OUTER JOIN` helyett. Ez a javasolt beállítás általában javítja a lekérdezések teljesítményét, bár ez az adatforrás pontos jellemzőitől is függ.
* **Ne használja a relatív adatszűrést a Lekérdezésszerkesztőben.** Lehetőség van relatív dátumszűrés megadására a Lekérdezésszerkesztőben. Például ki lehet szűrni az olyan sorokat, amelyek dátuma az elmúlt 14 napon belülre esik.
  
  ![Sorok szűrése az elmúlt 14 napra](media/desktop-directquery-about/directquery-about_02.png)
  
  Ez a szűrő azonban egy rögzített dátumon alapuló szűrőre lesz lefordítva, amely a lekérdezés létrehozási dátumához képest működik. Ez az eredmény látható a natív lekérdezés megtekintésekor.
  
  ![Sorok szűrése natív SQL-lekérdezésben](media/desktop-directquery-about/directquery-about_03.png)
  
  Ez feltehetően nem a kívánt eredmény. Ahhoz, hogy a szűrő ehelyett a jelentés futtatásának dátumát vegye alapul, Jelentésszűrőként alkalmazza a szűrőt a jelentésben. Ezt jelenleg úgy lehet megtenni, ha létrehoz egy számított oszlopot, amely a `DAX DATE()` függvény használatával kiszámolja, hogy a dátum hány nappal ezelőtt volt, majd ezt a számított oszlopot használja szűrőként.

### <a name="report-design-guidance"></a>Jelentéstervezési útmutatás

DirectQuery-kapcsolatot használó jelentés készítésekor kövesse az alábbi útmutatást:

* **Fontolja meg a lekérdezések csökkentésének lehetőségét:** A Power BI-ban beállítható, hogy a jelentések kevesebb számú lekérdezést küldjenek, és letiltható néhány olyan interakció is, amelynek futása hosszú időt igényel, és így negatívan befolyásolhatja a felhasználói élményt. A Power BI Desktopban ezeket a beállításokat a **Fájl** > **Lehetőségek és beállítások** > **Beállítások** menüpont alatt a **Lekérdezések csökkentése** lehetőségnél találja meg.

   ![Lekérdezések csökkentése beállítás](media/desktop-directquery-about/directquery-about_03b.png)

    A **Lekérdezések csökkentése** területen lehetősége van letiltani a keresztkiemeléseket a teljes jelentésre vonatkozóan. Egy **Alkalmazás** gombot is megjeleníthet a szeletelők vagy szűrők kijelöléséhez. Ezen a módon a szeletelők és a szűrők kijelölését azok alkalmazása előtt elvégezheti. Lekérdezés csak akkor lesz elküldve, ha a szeletelő **Alkalmazás** gombját választja. Ezt követően a szeletelőkkel elvégezhető az adatszűrés.

    Ezek a beállítások érvényesek lesznek a jelentésre, amíg a Power BI Desktopban kezeli azt. A beállítások akkor is érvényre jutnak, amikor a felhasználók a Power BI szolgáltatásban használják a jelentést.

* **Először alkalmazza a szűrőket:** A vonatkozó szűrőket mindig alkalmazza a vizualizáció létrehozásának legelején. Például ahelyett, hogy behúzná a **TotalSalesAmount** és **ProductName** oszlopokat, majd rászűrne egy adott évre, alkalmazza az **év** szerinti szűrést rögtön a legelején. A vizualizáció összeállításának minden lépése elküld egy lekérdezést. Lehet ugyan módosításokat végezni az első lekérdezés teljesítése után is, de ezzel feleslegesen terheli az alapul szolgáló forrást. A szűrők korai alkalmazása általában csökkenti a közbeeső lekérdezések költségeit. Emellett a szűrők korai alkalmazásának elmulasztása esetén átlépheti az 1 millió soros korlátot.
* **Korlátozza az egy oldalon található vizualizációk számát:** Az oldalak megnyitásakor vagy egy oldalszintű szeletelő vagy szűrő módosításakor az oldal összes vizualizációja frissül. A párhuzamosan elküldhető lekérdezések száma is korlátozott. Ahogy a vizualizációk száma növekszik, egyes vizualizációk csak egymás után frissülnek, ami növeli az egész oldal frissítéséhez szükséges időt. Emiatt ajánlott korlátozni az egy oldalon található vizualizációk számát, és ehelyett több, egyszerűbb oldalt készíteni.
* **Vegye fontolóra a vizualizációk közti interakció kikapcsolását:** Alapértelmezés szerint egy jelentésoldal vizualizációi az oldal további vizualizációinak keresztszűréséhez és keresztkijelöléséhez használhatók. Ha például a kördiagramon kiválasztja **1999**-et, az oszlopdiagramon keresztkiemeléssel jelennek meg az **1999**-re vonatkozó értékesítések, kategóriák szerint.
  
  ![Több vizualizáció keresztszűréssel és keresztkiemeléssel](media/desktop-directquery-about/directquery-about_04.png)
  
  A DirectQueryben a keresztszűréshez és keresztkiemeléshez lekérdezéseket kell átadni a mögöttes forrásnak. Ha a felhasználói kijelölésekre adott válasz ésszerűtlen mértékben késik, az interakciót ki kell kapcsolni. Az interakció kikapcsolható. Kapcsolja ki az interakciót akár a teljes jelentésre vonatkozóan, a lekérdezések csökkentésének beállításairól szóló szakasz alapján, vagy külön-külön is. További információt a [Vizualizációk közötti keresztszűrés Power BI-jelentésben](../consumer/end-user-interactions.md) című cikkben talál.

A fent leírtak mellett a következő jelentéskészítési funkciók is okozhatnak teljesítményproblémákat:

* **Mértékszűrők:** A mértékeket vagy mértékek összegzéseit tartalmazó vizualizációk a mértékeken belüli szűrőket is tartalmazhatnak. Az alábbi ábra például az **értékesített mennyiségeket** mutatja **kategóriák** szerint, de csak a **20 milliós** értékesítés feletti kategóriákat tartalmazza.
  
  ![Szűrőket tartalmazó mértékeket ábrázoló vizualizáció](media/desktop-directquery-about/directquery-about_05.png)
  
  Ennek eredményeként két lekérdezés lesz elküldve a mögöttes forráshoz:
  
  * Az első lekérdezés a **SalesAmount** nagyobb, mint 20 millió feltételnek eleget tevő kategóriákat kéri le.
  * Ez után a második lekérdezés lekéri a vizualizációhoz szükséges adatokat, beleértve azokat a kategóriákat, amelyek megfeleltek a `WHERE` utasításban megadott feltételeknek.
  
  Ez a módszer általában jól működik, ha néhány száz vagy ezer kategória van, mint ebben a példában. Sokkal több kategória esetén a teljesítmény romolhat. A lekérdezés sikertelen lesz, ha egymilliónál több kategória felel meg a feltételnek. Az 1 millió soros korlátról korábban már volt szó.

* **Legjobb N szűrők:** Speciális szűrők definiálhatók a valamely mérték szerinti rangsorban legmagasabb vagy legalacsonyabb N darab érték szűrésére. A szűrők tartalmazhatják például az előző vizualizáció első 10 kategóriáját. Ez szintén azzal jár, hogy két lekérdezés lesz elküldve a mögöttes forráshoz. Az első lekérdezésre azonban az alapul szolgáló forrás az összes kategóriát visszaadja, majd a legjobb N értéket a visszaadott eredmények alapján választja ki a rendszer. Ez a módszer az érintett oszlop számosságától függően okozhat teljesítményproblémákat, vagy az 1 milliós korlát miatt akár a lekérdezés sikertelenségét is.

* **Medián:** Az olyan összesítések, mint a `Sum` vagy a `Count Distinct` általában a mögöttes forrásnak vannak leküldve. A medián esetében azonban nem ez történik, mivel a mögöttes forrás általában nem támogatja ezt az összesítést. Ezekben az esetekben a Power BI részletadatokat kérdez le az alapul szolgáló forrástól, és a visszaadott eredmények alapján számítja ki a mediánt. Ezt a módszert akkor célszerű alkalmazni, ha viszonylag kis számú eredmény mediánját kell kiszámítani. Nagy számosság esetén teljesítményproblémák léphetnek fel, vagy a lekérdezés az 1 millió soros korlát miatt sikertelen lesz. A **megyék lakosságának mediánja** például jól kiszámítható, az **értékesítési árak mediánja** viszont nem minden esetben az.

* **Speciális szövegszűrők (_tartalmaz_ és hasonlók):** Egy szöveges oszlop szűrésekor a speciális szűrők között megtalálhatók a *tartalmaz*, *kezdődik* és hasonló szűrők. Ezek teljesítménycsökkenést okozhatnak bizonyos adatforrások esetében. Konkrétan a *tartalmaz* szűrőt nem szabad használni, ha pontos találatokra van szükség. Bár az eredmények ugyanazok lehetnek, a konkrét adatoktól függően a teljesítményben komoly különbségek mutatkozhatnak az indexek használata miatt.

* **Többszörös kijelölés szeletelőkben:** Alapértelmezés szerint a szeletelők csak egyetlen kijelölést engedélyeznek. A szűrők többszörös kijelölésének engedélyezése teljesítményproblémákat okozhat, ha a felhasználó több elemet is kijelöl a szeletelőben. Ha a felhasználó például 10 őt érdeklő terméket jelöl ki, minden kijelölés következtében lekérdezések lesznek elküldve a forráshoz. Bár a felhasználó a lekérdezés befejeződése előtt is kijelölheti a következő elemet, ezzel többletterhelést ró a mögöttes forrásra.

* **Fontolja meg az összegzések kikapcsolását a vizualizációkban:** A táblázatok és mátrixok alapértelmezés szerint összegeket és részösszegeket is megjelenítenek. Ezeknek az eredményeknek e lekérdezéséhez azonban sok esetben külön lekérdezést kell küldeni az alapul szolgáló adatkészlethez. Ez így van minden olyan esetben, amikor *DistinctCount* összesítést használ, illetve ha az SAP BW-re vagy az SAP HANA-ra irányuló DirectQueryt használ. Ezeket az összegzéseket ajánlatos a **Formázás** panel használatával kikapcsolni.

### <a name="maximum-number-of-connections-option-for-directquery"></a>A DirectQuery-kapcsolatok maximális számának beállítása

Minden mögöttes adatforráshoz beállíthatja a DirectQuery által megnyitott kapcsolatok maximális számát, amely szabályozza az egyes adatforrásoknak egyidejűleg küldött lekérdezések számát.

A DirectQuery alapértelmezés szerint legfeljebb 10 egyidejű kapcsolatot nyit meg. Az aktuális fájlra vonatkozó maximumot a Power BI Desktopban módosíthatja. Nyissa meg a **Fájl** > **Lehetőségek és beállítások** > **Beállítások** menüpontot. A bal oldali panel **Aktuális fájl** szakaszában válassza a **DirectQuery** lehetőséget.

![A DirectQuery-kapcsolatok maximális számának beállítása](media/desktop-directquery-about/directquery-about_05b.png)

Ez a beállítás csak akkor van engedélyezve, ha legalább egy DirectQuery-forrás található az aktuális jelentésben. Az érték minden DirectQuery-forrásra vonatkozik, valamint a jelentéshez adott új DirectQuery-forrásokra is.

Az **Adatforrásonkénti kapcsolatok maximális számának** növelésével érhető el, hogy több lekérdezést lehessen a mögöttes adatforráshoz küldeni. Ez akkor hasznos, ha sok vizualizáció van egy oldalon, vagy ha egyidejűleg sok felhasználó fér hozzá a jelentéshez. A kapcsolatok maximális számának elérése után a lekérdezések üzenetsorba kerülnek, amíg egy kapcsolat elérhetővé nem válik. A korlát növelése nagyobb terhelést eredményez a mögöttes forráson, a beállítás használata így nem garantál jobb teljesítményt.

Ha a modell közzé van téve, a mögöttes adatforráshoz egyidejűleg küldött lekérdezések maximális száma rögzített korlátoktól is függ. A korlátok azon a célkörnyezeten múlnak, ahol a jelentés közzé van téve. Különböző környezetek például a Power BI, a Power BI Premium vagy a Power BI jelentéskészítő kiszolgáló különböző korlátokat szabhatnak.

### <a name="diagnosing-performance-issues"></a>Teljesítményproblémák diagnosztizálása

Ez a szakasz leírja, hogyan diagnosztizálhatja a teljesítményproblémákat, vagy hogyan kérhet le részletesebb információkat, amelyek lehetővé teszik a jelentések optimalizálását.

Ajánlott a teljesítményproblémák diagnosztizálását a Power BI Desktopban elkezdeni, nem a Power BI szolgáltatásban. A teljesítményproblémák gyökere gyakran a mögöttes forrás teljesítménye. A problémák könnyebben felismerhetők és diagnosztizálhatók a Power BI Desktop jobban elkülönített környezetében. Ezen a módon eleinte kizárhatók bizonyos összetevők, például a Power BI-átjáró. Ha a teljesítményproblémák a Power BI Desktopban nem jelentkeznek, vizsgálja meg a jelentés jellemzőit a Power BI szolgáltatásban. A [teljesítményelemző](../create-reports/desktop-performance-analyzer.md) hasznos eszköz a folyamat során felmerülő problémák azonosításához.

Hasonlóképp ajánlott a problémákat először egy különálló vizualizációban azonosítani, nem egy sok vizualizációt tartalmazó oldalon.

Tegyük fel, hogy végrehajtotta a szakasz eddigi bekezdéseiben leírt lépéseket. Ha így van, akkor a Power BI Desktopban egyetlen vizualizációt lát egy oldalon, amely még mindig lassú. A [teljesítményelemző](../create-reports/desktop-performance-analyzer.md) használatával megállapíthatja, hogy milyen lekérdezéseket küld a Power BI Desktop a mögöttes forráshoz. Áttekintheti a mögöttes forrás által esetlegesen kiadott nyomkövetési és diagnosztikai adatokat is. A nyomkövetési adatok hasznos részleteket tartalmazhatnak a lekérdezés végrehajtásáról és a lekérdezés javításának lehetőségeiről is.

A következő szakaszban leírt módon a Power BI által küldött lekérdezések és végrehajtási idejük akkor is megtekinthetők, ha az ilyen nyomkövetési adatok hiányoznak a forrásból.

#### <a name="determining-the-queries-sent-by-power-bi-desktop"></a>A Power BI Desktop által küldött lekérdezések azonosítása

A Power BI Desktop alapértelmezés szerint az egy adott munkamenet során történt eseményeket egy nyomkövetési fájlban rögzíti, amelynek a neve *FlightRecorderCurrent.trc*.

Egyes DirectQuery-források esetében ez a napló a mögöttes forráshoz küldött összes lekérdezést tartalmazza. Ez a jövőben a többi DirectQuery-forrásra is igaz lesz. A naplóba az alábbi források továbbítanak lekérdezéseket:

* SQL Server
* Azure SQL Database
* Azure SQL Data Warehouse
* Oracle
* Teradata
* SAP HANA

A nyomkövetési fájl az aktuális felhasználó *AppData* mappájában található:

*\<Felhasználó>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces*

Ez a mappa a Power BI Desktopban a **Fájl** > **Lehetőségek és beállítások** > **Beállítások** menüpont, majd a **Diagnosztika** lehetőség választásával érhető el. Megnyílik a következő párbeszédpanel:

![A nyomkövetési mappa megnyitására szolgáló hivatkozás](media/desktop-directquery-about/directquery-about_06.png)

Amikor a **Diagnosztikai lehetőségek** területen az **Összeomlási memóriakép/nyomkövetési mappa megnyitása** lehetőséget választja, megnyílik az alábbi mappa: *\<Felhasználó>\AppData\Local\Microsoft\Power BI Desktop\Traces*.

E mappa szülőmappáját megnyitva az *AnalysisServicesWorkspaces* mappa jelenik meg, amelyben a Power BI Desktop minden egyes megnyitott példányához egy munkaterületi almappa található. Ezek a mappák egész szám utótagokkal vannak elnevezve, például *AnalysisServicesWorkspace2058279583*.

A mappán belül egy *\\Data* mappa található. Ez tartalmazza az aktuális Power BI-munkamenet *FlightRecorderCurrent.trc* nyomkövetési fájlját. A Power BI Desktop-munkamenet befejezésekor az ahhoz tartozó munkaterületi mappa törlődik.

A nyomkövetési fájlok az *SQL Server Profiler* eszközzel olvashatók. Ehhez az ingyenesen letölthető [SQL Server Management Studio](/sql/ssms/download-sql-server-management-studio-ssms) részeként juthat hozzá.

Ha letöltötte és telepítette az SQL Server Management Studio eszközt, futtassa az SQL Server Profilert.

![SQL Server Profiler](media/desktop-directquery-about/directquery-about_07.png)

A nyomkövetési fájl megnyitásához hajtsa végre a következő lépéseket:

1. Az SQL Server Profilerben válassza a **Fájl** > **Megnyitás** > **Nyomkövetési fájl** lehetőséget.

1. Írja be a jelenleg megnyitott Power BI-munkamenethez tartozó nyomkövetési fájl elérési útját, például: *C:\Users\<Felhasználó>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces\AnalysisServicesWorkspace2058279583\Data*.

1. Nyissa meg a *FlightRecorderCurrent.trc* fájlt.

Megjelenik az aktuális munkamenet összes eseménye. Az alábbi, jelmagyarázattal kiegészített példa kiemeli az eseménycsoportokat. Minden csoportban szerepelnek a következő események:

* Egy `Query Begin` (Lekérdezés kezdete) és egy `Query End` (Lekérdezés vége) esemény, amelyek egy felhasználói felületen, például egy vizualizációból vagy a szűrőfelület egy értéklistájából létrehozott DAX-lekérdezés elejét és végét jelölik.
* Egy vagy több `DirectQuery Begin` – `DirectQuery End` eseménypár, amelyek egy-egy lekérdezés elküldését jelölik az alapul szolgáló adatforrás felé a DAX-lekérdezés kiértékelésének részeként.

Több DAX-lekérdezés is futtatható párhuzamosan, így a különböző csoportok eseményei átfedhetik egymást. Az `ActivityID` (Tevékenységazonosító) segítségével azonosítható, hogy mely események tartoznak ugyanazon csoporthoz.

![Query Begin és Query End események az SQL Server Profilerben](media/desktop-directquery-about/directquery-about_08.png)

A további lényeges oszlopok a következők:

* **TextData:** Az esemény szöveges részletezése. A `Query Begin/End` eseményeknél a részletezés a DAX-lekérdezés. A `DirectQuery Begin/End` eseményeknél a részletezés a mögöttes forráshoz küldött SQL-lekérdezés. Az éppen kijelölt esemény **TextData** szöveges adatai az alsó régióban is megjelennek.
* **EndTime:** Az esemény befejezésének időpontja.
* **Duration:** A DAX- vagy SQL-lekérdezés végrehajtásához szükséges időtartam, ezredmásodpercben.
* **Error:** Jelzi, ha hiba történt – ez esetben az esemény vörös színnel jelenik meg.

A fenti képen néhány kevésbé lényeges oszlop keskenyítve lett, hogy a többi oszlop jobban látható legyen.

A potenciális teljesítményproblémák diagnosztizálásához szükséges nyomkövetés rögzítésére az alábbi eljárás ajánlott:

* A munkaterületi mappák összekeverésének elkerülése érdekében csak egyetlen Power BI Desktop-munkamenetet nyisson meg.
* Végezze el a vonatkozó műveleteket a Power BI Desktopban. Ez után végezzen el még néhány további műveletet, hogy a lényeges események biztosan bekerüljenek a nyomkövetési fájlba.
* Nyissa meg az SQL Server Profilert, és vizsgálja meg a nyomkövetési adatokat a korábban megismert módon. Tartsa szem előtt, hogy a Power BI Desktop bezárásával törli a nyomkövetési fájlt. Emellett a Power BI Desktopban végzett további műveletek nem jelennek meg azonnal. Az események megjelenítéséhez a nyomkövetési fájlt be kell zárni, majd újra meg kell nyitni.
* Az egyes munkamenetek legyenek viszonylag kicsik, nem több száz, inkább csak 10 másodpercnyi tevékenységgel. Így egyszerűbb lesz értelmezni a nyomkövetési fájlt. A nyomkövetési fájl mérete is korlátozott. Hosszú munkameneteknél előfordulhat, hogy a régi események már el vannak vetve.

#### <a name="understanding-the-form-of-query-sent-by-power-bi-desktop"></a>A Power BI Desktop által küldött lekérdezések formátumának értelmezése

A Power BI Desktop által létrehozott és elküldött lekérdezések általános formátuma minden egyes hivatkozott táblához beágyazott lekérdezéseket használ. A beágyazott lekérdezést a Lekérdezésszerkesztőbeli lekérdezés határozza meg. Vegyük például az alábbi TPC-DS táblákat az SQL Server-kiszolgálón:

![TPC-DS-táblák az SQL Serverben](media/desktop-directquery-about/directquery-about_09.png)

Tekintse meg a következő lekérdezést:

![Mintalekérdezés](media/desktop-directquery-about/directquery-about_10.png)

A lekérdezés eredménye a következő vizualizáció lesz:

![Lekérdezés eredménye vizualizáción](media/desktop-directquery-about/directquery-about_11.png)

A vizualizáció frissítésének eredménye az alábbi SQL-lekérdezés lesz. Ahogy látható, a három beágyazott lekérdezés: `Web Sales`, `Item` és `Date_dim` mindegyike visszaadja az adott táblák összes oszlopát, noha a vizualizáció csupán négy oszlopra hivatkozik. Az árnyékolással jelölt beágyazott lekérdezések pontosan a Lekérdezésszerkesztőben definiált lekérdezések eredményei. A beágyazott lekérdezések ily módon való használata az eddigi tapasztalatok szerint nem befolyásolja a teljesítményt a DirectQuery által jelenleg támogatott adatforrások esetében. Az SQL Server és hasonló adatforrások kioptimalizálják a hivatkozásokat a többi oszlopból.

A Power BI azért ezt a mintát követi, mert a használt SQL-lekérdezés így közvetlenül átadható az elemzőnek. Az „adott állapotában” használható, anélkül, hogy kísérletet tennénk az újraírására.

![Adott állapotában használt SQL-lekérdezés](media/desktop-directquery-about/directquery-about_12.png)

## <a name="next-steps"></a>Következő lépések

Ez a cikk a DirectQuery azon tulajdonságait írja le, amelyek minden adatforrás esetében közösek. Vannak bizonyos részletek, amelyek csak az egyes forrásokra érvényesek. Tekintse meg az egyes forrásokkal foglalkozó cikkeket is:

* [DirectQuery és SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery és SAP BW](desktop-directquery-sap-bw.md)

A DirectQueryvel kapcsolatos további információkat találhat az alábbi forrásban:

* [A DirectQuery által támogatott adatforrások](power-bi-data-sources.md)
