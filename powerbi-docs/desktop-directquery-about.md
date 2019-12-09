---
title: DirectQuery használata a Power BI-ban
description: A DirectQuery használatának bemutatása a Power BI-ban
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/19/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 13ca0b53bb1aed2d4323afdc99a97f8b9cfa5567
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/03/2019
ms.locfileid: "73868341"
---
# <a name="using-directquery-in-power-bi"></a>DirectQuery használata a Power BI-ban
Számos különböző adatforrást kapcsolhat össze a **Power BI Desktop** vagy a **Power BI szolgáltatás** használatával, és ezeket az adatkapcsolatokat többféleképpen is létrehozhatja. *Importálhat* adatokat a Power BI-ba, ez az adatok lekérésének leggyakoribb módja, vagy közvetlenül is csatlakozhat az eredeti forrásadattárukban lévő adatokhoz, ez az eljárás **DirectQuery** néven ismert. Ez a cikk a **DirectQuery** szolgáltatást és annak képességeit mutatja be:

* A DirectQuery különféle kapcsolódási lehetőségei
* Útmutatás arra vonatkozóan, hogy mikor érdemes megfontolni a DirectQuery használatát importálás helyett
* A DirectQuery használatának hátrányai
* Ajánlott eljárások a DirectQuery használatához

Röviden összefoglalva az importálást a DirectQuery helyett az alábbi ajánlott eljárások szerint érdemes használni:

* Amikor csak lehetősége van rá, az adatokat érdemes **importálni** a Power BI-ba. Az importálással kihasználhatók a Power BI nagy teljesítményű lekérdezési motorjának előnyei, valamint interaktív és teljes körű funkciókat biztosít az adatok használatához.
* Ha szükséges célok nem érhetők el az adatok importálásával, fontolja meg a **DirectQuery** használatát. Ha például az adatok gyakran változnak, a jelentésekkel pedig a legfrissebb adatokat szeretné bemutatni, akkor valószínűleg a DirectQuery a legjobb választás. A DirectQuery használata azonban csak akkor megvalósítható, ha az alapul szolgáló adatforrások interaktív (5 másodpercnél rövidebb) lekérdezéseket biztosítanak a szokványos összesítő lekérdezésekhez, valamint képesek az ezáltal létrejött lekérdezési terhelés kezelésére. Ezenkívül a DirectQuery használatához társuló korlátozásokat érdemes alaposan megfontolni.

A Power BI által nyújtott képességeket idővel mind az importálás, mind a DirectQuery esetében bővíteni és fejleszteni fogjuk. Ez vonatkozik az importált adatok használatának rugalmasságára abban az értelemben, hogy az importálás több esetben legyen használható, valamint a DirectQuery használatával kapcsolatos hátrányok kiküszöbölésére is. A fejlesztésektől függetlenül a DirectQuery esetében az alapul szolgáló adatforrás teljesítménye mindig az első számú megfontolandó szempontok közé fog tartozni. Ha az alapul szolgáló adatforrás lassú, akkor a DirectQuery használata ahhoz az adatforráshoz nem lesz megvalósítható.

Ez a cikk a DirectQuery és a Power BI együttes használatát tárgyalja, az SQL Server Analysis Services szolgáltatást nem. A DirectQueryt az **SQL Server Analysis Services** is használja, és az alábbiakban tárgyalt részletek nagy része annak használatára is vonatkozik, a kettő között azonban fontos különbségek is vannak. A DirectQuery és az SQL Server Analysis Services együttes használatával kapcsolatos információkért keresse fel a [DirectQuery SQL Server Analysis Services 2016-os verziójában való használatát bemutató tanulmányt](https://download.microsoft.com/download/F/6/F/F6FBC1FC-F956-49A1-80CD-2941C3B6E417/DirectQuery%20in%20Analysis%20Services%20-%20Whitepaper.pdf).  

Ez a cikk a DirectQueryhez tartozó ajánlott munkafolyamatokra koncentrál, amely esetben a jelentés **Power BI Desktopban** jön létre, viszont a **Power BI szolgáltatáshoz** való közvetlen kapcsolódás témájával is foglalkozik.

## <a name="power-bi-connectivity-modes"></a>A Power BI kapcsolódási módjai
A Power BI rengeteg különféle adatforráshoz képes csatlakozni, többek között az alábbiakhoz:

* Online szolgáltatások (Salesforce, Dynamics 365 stb.)
* Adatbázisok (SQL Server, Access, Amazon Redshift stb.)
* Egyszerű fájlok (Excel, JSON stb.)
* Egyéb adatforrások (Spark, webhelyek, Microsoft Exchange stb.)

Ezen adatforrások esetén az adatok importálhatók a Power BI-ba. Néhány adatforráshoz a DirectQuery használatával is lehet kapcsolódni. A DirectQuery használatát támogató adatforrások részletes listájáért tekintse meg [a DirectQuery által támogatott adatforrásokkal](desktop-directquery-data-sources.md) foglalkozó cikket. A jövőben további források is elérhetőek lesznek a DirectQuery használatával. Ezek elsősorban olyan források lesznek, amelyek megfelelő teljesítményű, interaktív lekérdezésre képesek.

Az **SQL Server Analysis Services** speciális esetnek számít. Az SQL Server Analysis Serviceshez való kapcsolódáskor választhat az adatok importálása vagy az *élő kapcsolat* használata között.  Az élő kapcsolat használata abban hasonlít a DirectQueryhez, hogy nincs szükség az adatok importálására, illetve hogy az alapul szolgáló adatok rendszeres lekérdezésével frissülnek a vizualizációk. Az *élő kapcsolat* azonban számos más tekintetben eltér attól, ezért használunk rá más kifejezést (*élő* kapcsolat a *DirectQuery* helyett).

Az adatokhoz való kapcsolódás ezen három lehetőségét, az **importálás**, a **DirectQuery** és az **élő kapcsolat** használatát, a következő szakaszokban részletesen is bemutatjuk.

### <a name="import-connections"></a>Importálási kapcsolatok
Ha az **Adatok lekérése** utasítást használja a **Power BI Desktopban** az adatforráshoz, például az SQL-kiszolgálóhoz való csatlakozáshoz, és az **importálás** lehetőséget választja, az adott kapcsolat működése a következőképpen alakul:

* Az **Adatok lekérése** utasítás használatakor a kiválasztott táblák listája mind egy-egy lekérdezést határoz meg, amely egy adatkészletet ad vissza (ezek a lekérdezéseket az adatok betöltése előtt szerkesztheti, például szűrőkkel láthatja el, összesítheti az adatokat, vagy egyesíthet különféle táblákat).
* Betöltéskor a rendszer a lekérdezések által meghatározott adatokat importálja a Power BI gyorsítótárába.
* A **Power BI Desktopban** egy vizualizáció létrehozásakor a rendszer lekéri az importált adatokat. A Power BI-tároló biztosítja a lekérdezés gyorsaságát, így a vizualizációt érintő minden változás azonnal megjelenik.
* Az alapul szolgáló adatokkal kapcsolatos változások egyik vizualizációban sem jelennek meg. Fontos a *Frissítés* funkció használata, amellyel a rendszer újraimportálja az adatokat.
* A jelentés (.pbix-fájl) **Power BI szolgáltatásban** való közzétételekor, egy adatkészlet jön létre, amely fel lesz töltve a Power BI szolgáltatásba.  Az importált adatok ebbe az adatkészletbe kerülnek. Ezt követően lehetősége van az említett adatok ütemezett frissítésére, például az adatok naponta történő újraimportálására. Az eredeti adatforrás helyétől függően szükség lehet egy Helyszíni adatátjáró konfigurálására.
* A meglévő jelentés **Power BI szolgáltatásban** való megnyitásakor vagy új jelentés létrehozásakor a rendszer az interaktivitás fenntartása érdekében ismét lekéri az importált adatokat.
* A vizualizációk vagy teljes jelentésoldalak csempék formájában kitűzhetők az irányítópultokra. A csempék automatikusan frissülnek az alapul szolgáló adatkészlet frissítésekor.  

### <a name="directquery-connections"></a>DirectQuery-kapcsolatok
Ha az **Adatok lekérése** utasítást használja a **Power BI Desktopban** az adatforráshoz való csatlakozáshoz, és a **DirectQuery** lehetőséget választja, az adott kapcsolat működése a következőképpen alakul:

* Az **Adatok lekérése** használatának első lépéseként ki kell választani a forrást. Relációs források esetén ez azt jelenti, hogy több tábla lesz kiválasztva, amelyek mindegyike továbbra is egy olyan lekérdezést határoz meg, amely logikailag ad vissza egy adatkészletet. Többdimenziós források, például SAP BW esetén csak a forrás lesz kiválasztva.
* Betöltéskor azonban a rendszer semmilyen adatot nem importál a Power BI-tárolóba. Ehelyett a **Power BI Desktopban** egy vizualizáció létrehozásakor a rendszer a szükséges adatok lekéréséhez az alapul szolgáló adatforráshoz küldi a lekérdezést. A vizualizáció frissítéséhez szükséges idő a háttéradatforrás teljesítményétől függ.
* Az alapul szolgáló adatokkal kapcsolatos változások egyik meglévő vizualizációban sem jelennek meg azonnal. A frissítés használatára továbbra is szükség van, amikor is a rendszer a szükséges lekérdezéseket minden vizualizáció esetén újraküldi, a vizualizáció pedig szükség esetén frissül.
* A jelentés **Power BI szolgáltatásban** való közzétételekor az importáláshoz hasonlóan szintén létrejön egy adatkészlet a Power BI szolgáltatásban. Azonban ebbe az adatkészletbe *nem kerülnek adatok*.
* Meglévő jelentés a **Power BI szolgáltatásban** való megnyitásakor vagy új jelentés létrehozásakor a szükséges adatok lékéréséhez a rendszer ismét lekérdezi az alapul szolgáló adatokat. Az eredeti adatforrás helyétől függően szükség lehet egy helyszíni adatátjáró konfigurálására, hasonlóan az importáláshoz az adatok frissítésekor.
* A vizualizációk vagy teljes jelentésoldalak csempék formájában kitűzhetők az irányítópultokra. Az irányítópult gyors megnyithatósága érdekében a csempék automatikusan, ütemezés szerint frissülnek (például óránként). A frissítés gyakorisága szabályozható, az adatok változásának gyakorisága, illetve az alapján, hogy mennyire fontos a legfrissebb adatok megjelenítése. Így az irányítópult megnyitásakor a csempék az utolsó frissítésből származó adatokat fogják megjeleníteni, tehát az alapul szolgáló forrás legutóbbi változásai nem feltétlenül jelennek meg. A megnyitott irányítópult a naprakész adatok megtekintése érdekében bármikor frissíthető.    

### <a name="live-connections"></a>Élő kapcsolatok
Az **SQL Server Analysis Services** (SSAS) szolgáltatáshoz való kapcsolódáskor lehetőség van a kiválasztott adatmodell adatainak importálására, vagy az azokhoz való élő kapcsolódásra. Ha az **importálás** mellett dönt, akkor egy lekérdezést határoz meg a külső SSAS-forráshoz, a rendszer pedig a szokásos módon importálja az adatokat. Ha az **élő kapcsolat** mellett dönt, akkor nem határoz meg lekérdezést, és az egész külső modell megjelenik a mezők listájában.

Az előző bekezdésben leírt szituáció az alábbi forrásokhoz való csatlakozásra is vonatkozik, azzal a kivétellel, hogy nincs lehetőség az adatok importálására:

* Power BI-adatkészletek (például egy korábban létrehozott, és a szolgáltatásban közzétett Power BI-adatkészlethez való kapcsolódáskor, az adatokra épülő új jelentés létrehozása esetén)
* Common Data Service-szolgáltatások

Az SSAS alapján létrehozott jelentések működése a **Power BI szolgáltatásban** való közzétételkor a következő szempontokból hasonlít a DirectQuery-jelentésekhez:

* Egy meglévő jelentés **Power BI szolgáltatásban** való megnyitásakor vagy új jelentés létrehozásakor a rendszer az alapul szolgáló SSAS-ről kéri le az adatokat (amelyhez valószínűleg egy helyszíni adatátjáróra lesz szükség)
* Az irányítópult csempéi automatikusan, ütemezés szerint frissülnek (például óránként, vagy bármely egyéb megadott gyakorisággal)

Azonban vannak fontos különbségek, többek között az, hogy az élő kapcsolatok esetén a jelentést megnyitó felhasználó identitását a rendszer mindig átadja az alapul szolgáló SSAS-forrásnak.

Az eddig leírt összehasonlítások után a cikk további részében a **DirectQuery** használatával foglalkozunk.

## <a name="when-is-directquery-useful"></a>Mikor hasznos a DirectQuery?
Az alábbi tábla olyan forgatókönyveket ír le, amelyekben a DirectQueryvel való kapcsolódás különösen hasznosnak bizonyul, köztük olyan eseteket, amelyekben érdemes az adatokat az eredeti forrásban hagyni. A leírásban arról is szó lesz, hogy a bemutatott forgatókönyv elérhető-e a Power BI-ban.

| Korlátozás | Leírás |
| --- | --- |
| Az adatok gyakran változnak, és közel „valós idejű” jelentéskészítésre van szükség |Az importált adatokat használó modellek legfeljebb óránként egyszer frissíthetők. Ezért ha az adatok folyamatosan változnak, és fontos, hogy a jelentések a legfrissebb adatokat jelenítsék meg, akkor előfordulhat, hogy az importálás és az ütemezett frissítés használata nem lesz elegendő. Fontos megjegyezni, hogy az adatok közvetlenül is streamelhetők a Power BI-ba, bár ebben az esetben adatmennyiségi korlátozásokkal kell számolni. <br/> <br/> Ezzel ellentétben a DirectQuery használata azt jelenti, hogy egy jelentés vagy irányítópult megnyitásakor vagy frissítésekor mindig a forrásban szereplő legfrissebb adatok jelennek meg. Emellett az irányítópult csempéi gyakrabban (akár 15 percenként) frissíthetők. |
| Nagy méretű adatok |Nagyon nagy méretű adatok esetén az összes adat importálása egyértelműen nem megvalósítható. A DirectQuery esetén ezzel ellentétben nincs szükség nagy mennyiségű adatátvitelre, mivel a lekérdezés helyben történik. <br/> <br/> Azonban a nagy méretű adatok esetén az is előfordulhat, hogy az alapul szolgáló forrásra irányuló lekérdezések lassúak (amint a cikk későbbi részében található, *A DirectQuery használatának következményei* című szakaszban is tárgyaljuk). Nincs mindig szükség az összes részletes adat importálására. Ehelyett az adatok előzetes összesítésére is lehetőség van importálás során (a **Lekérdezésszerkesztő** pedig pontosan ezt teszi lehetővé). Szélsőséges esetben lehetséges lenne minden vizualizációhoz pontosan a szükséges összesített adatokat importálni. Így habár a DirectQuery a legegyszerűbb módja nagy mennyiségű adat feldolgozásának, mindig tartsa észben, hogy az összesített adatok importálása is megoldás lehet, ha az alapul szolgáló adatforrás túl lassú. |
| A biztonsági szabályok meghatározása az alapul szolgáló adatforrásban történik |Az adatok importálásakor a Power BI kapcsolódik az adatforráshoz az aktuális felhasználói hitelesítő adatokkal (a Power BI Desktopból) vagy az ütemezett frissítés részeként megadott hitelesítő adatokkal (a Power BI szolgáltatásból). Ennélfogva az ilyen jelentések közzétételekor és megosztásakor ügyelni kell arra, hogy csak olyan felhasználókkal osszuk meg a jelentést, akik jogosultak az adatok megtekintésére, vagy határozzunk meg sorszintű biztonságot az adatkészletben. <br/> <br/> Ideális esetben – mivel a DirectQuery mindig lekérdezi az alapul szolgáló forrást – ezzel a módszerrel az adott forrás minden biztonsági intézkedése alkalmazható lenne. Azonban jelenleg a Power BI mindig az importáláshoz használt hitelesítő adatok használatával kapcsolódik az alapul szolgáló forráshoz. <br/> <br/> Ezáltal amíg a Power BI nem teszi lehetővé, hogy a jelentés fogyasztójának identitása továbbítódjon az alapul szolgáló forrás felé, addig a DirectQuery semmilyen előnyt nem nyújt az adatforrások biztonsága szempontjából. |
| Az adatok szuverenitására korlátozások vonatkoznak |Egyes intézmények házirendekkel szabályozzák az adatok szuverenitását, ami azt jelenti, hogy az adatok nem hagyhatják el az intézmény területét. Egy importáláson alapuló megoldás bizonyosan problémákat okozna. Ezzel szemben a DirectQuery használatakor az adatok az alapul szolgáló forrásban maradnak. <br/> <br/> Megjegyzendő azonban, hogy még a DirectQuery használatakor is bizonyos gyorsítótárazott adatok a vizualizáció szintjén megmaradnak a Power BI szolgáltatásban (a csempék ütemezett frissítéséből adódóan). |
| Az alapul szolgáló adatforrás egy OLAP-forrás, amely mértékeket tartalmaz |Ha az alapul szolgáló adatforrás *mértékeket* tartalmaz (például SAP HANA vagy SAP Business Warehouse), akkor az adatok importálása további problémákat is felvet. Ez azt jelenti, hogy a rendszer az adatokat egy bizonyos összesítési szinten importálja, ahogy azt a lekérdezés meghatározza. Tegyük fel például, hogy felmérjük az összes értékesítést (TotalSales) osztály, év és város szerint. Ebben az esetben, ha létrehozunk egy vizualizációt, amely egy magasabb összesítési szinten kér adatokat (például összes értékesítés év szerint), az még tovább összesíti az összesített értéket. Ez nem okoz gondot az additív mértékeknél (például Sum, Min), de problémát jelent a nem additív mértékeknél (például Average, DistinctCount). <br/> <br/> Hogy könnyebb legyen a megfelelő összesített adatokat közvetlenül a forrástól lekérni (azokat, amelyek az adott vizualizációhoz szükségesek), a lekérdezéseket vizualizációnként kellene elküldeni, mint a DirectQueryben. <br/> <br/> Egy SAP Business Warehouse (BW) forráshoz való kapcsolódáskor a DirectQuery használatával lehetővé válik a mértékek ily módon való kezelése. Az SAP BW támogatásáról bővebben [A DirectQuery és az SAP BW](desktop-directquery-sap-bw.md) témakörben olvashat. <br/> <br/> Azonban jelenleg az SAP HANA-val használt DirectQuery ugyanúgy kezeli, mint egy relációs forrást, így importáláskor ugyanúgy is viselkedik. Erről bővebben [A DirectQuery és az SAP HANA](desktop-directquery-sap-hana.md) témakörben olvashat. |

Összegezve, a Power BI-ban a DirectQuery képességeit tekintve a következő helyzetekben szolgál előnyökkel:

* Az adatok gyakran változnak, és közel „valós idejű” jelentéskészítésre van szükség
* A kezelt adatok mennyisége rendkívül nagy, előzetes összesítésre nincs szükség
* Az adatok szuverenitására korlátozások vonatkoznak
* Az forrás egy többdimenziós forrás, amely mértékeket tartalmaz (például az SAP BW)

Az előző lista részletei csak a Power BI használatára vonatkoznak. Mindig ott van az a lehetőség is, hogy ehelyett importáljuk az adatokat egy külső SQL Server Analysis Services (vagy Azure Analysis Services) modell használatával, majd a Power BI segítségével kapcsolódjunk ehhez a modellhez. Habár ez a módszer nagyobb szakértelmet igényel, ugyanakkor nagyobb rugalmasságot is biztosít. Például sokkal nagyobb mennyiségű adatot lehet importálni, és nincs korlátozva az adatok frissítésének gyakorisága.

## <a name="implications-of-using-directquery"></a>A DirectQuery használatának következményei
A **DirectQuery** használata negatív következményekkel is járhat, amelyeket ez a szakasz ismertet. Ezen korlátozások némelyike kis mértékben különbözhet az itt leírtaktól, a pontos használt forrástól függően. Adott esetben a témakör ezt jelzi, a jelentősen különböző forrásokat pedig külön cikkek ismertetik.  

### <a name="performance-and-load-on-the-underlying-source"></a>Az alapul szolgáló forrás teljesítménye és terhelése
A **DirectQuery** használatakor az összteljesítmény nagyban függ az alapul szolgáló adatforrás teljesítményétől. Ha az egyes vizualizációk frissítése (például egy szeletelő értékének módosítása után) eltart néhány másodpercig (5 mp-nél nem tovább), akkor a teljesítmény még elfogadható, ugyanakkor már lassúnak érződik ahhoz az azonnali válaszidőhöz képest, amely az adatok Power BI-ba való importálásakor megszokott. Ha a forrás lassúsága azt eredményezi, hogy az egyes vizualizációk ennél is hosszabb időt (több tíz másodpercet) vesznek igénybe, akkor a teljesítmény rendkívül gyenge lesz, akár annyira is, hogy a lekérdezések időtúllépésekbe ütközzenek.

Az alapul szolgáló forrás teljesítménye mellett alaposan át kell gondolni azt is, hogy a DirectQuery mekkora terhelést kap majd (mivel ez is hatással van a teljesítményre). Ahogy azt a cikk később részletezi: minden felhasználó, aki megnyit egy megosztott jelentést, és minden időszakosan frissített irányítópult-csempe legalább vizualizációnként egy lekérdezést küld az alapul szolgáló forrás felé. Emiatt szükséges, hogy a forrás kezelni tudjon egy ekkora lekérdezés-terhelést, miközben továbbra is megfelelő teljesítményt nyújt.

### <a name="security-implications-when-combining-data-sources"></a>Az adatforrások egyesítésének biztonsági vonatkozásai
Egy DirectQuery-modellben, ahogyan adatok importálásakor is, több adatforrást is használhat az [Összetett modellek](desktop-composite-models.md) funkcióval. Ilyen esetben fontos tisztában lennie azzal, hogy az adatok hogyan mozognak a mögöttes adatforrásokban, valamint ennek [biztonsági vonatkozásaival](desktop-composite-models.md#security-implications).

### <a name="limited-data-transformations"></a>Korlátozott adatátalakítások
Hasonlóképp korlátozások vonatkoznak a **Lekérdezésszerkesztőben** elvégezhető adatátalakításokra is. Az importált adatok esetében egyszerűen alkalmazhatók olyan átalakítások, amelyek megtisztítják és átformálják az adatokat, mielőtt azokból egy vizualizációt hoznánk létre (például JSON-dokumentumok elemzését, vagy egy oszlop adatainak kimutatását sor formában). Ezek az átalakítások korlátozottabbak a DirectQueryben. Először is az OLAP-forrásokhoz, például az SAP Business Warehouse-hoz való kapcsolódáskor egyáltalán nem lehet átalakításokat meghatározni, a forrás teljes külső „modelljét” átveszi a rendszer. A relációs források, például az SQL Server esetében meg lehet adni átalakításokat lekérdezéseként, de teljesítményi okokból ezek is korlátozottak. Minden ilyen átalakítást az alapul szolgáló forrás minden egyes lekérdezésénél alkalmazni kell, ahelyett, hogy egyszerre, az adatok frissítésekor alkalmaznánk őket, ezért aztán csak azok az átalakítások használhatók, amelyek lefordíthatók egyetlen natív lekérdezésbe. A túl összetett átalakítási műveletek egy hibaüzenetet eredményeznek, amely szerint vagy törölni kell az átalakítást, vagy a modellt át kell váltani Importálás módba.

Emellett az **Adatok lekérése** párbeszédpanelen vagy a **Lekérdezésszerkesztővel** létrehozott lekérdezések a létrehozott és a vizualizációhoz szükséges adatok lekérése céljából elküldött lekérdezések egy részkiválasztásában lesznek használva. Ezért a Lekérdezésszerkesztőben megadott lekérdezéseknek érvényesnek kell lenniük ebben a kontextusban. Ez egészen pontosan azt jelenti, hogy nem használhatók az olyan lekérdezések, amelyek közös táblakifejezéseket használnak vagy tárolt eljárásokat hívnak meg.

### <a name="modeling-limitations"></a>Modellezési korlátozások
A *modellezés* kifejezés ebben a kontextusban a nyers adatok pontosítását és bővítését jelenti, egy jelentés létrehozása keretében. Példák:

* Táblák közti kapcsolatok meghatározása
* Új számítások hozzáadása (számított oszlopok és mértékek)
* Oszlopok és mértékek átnevezése és elrejtése
* Hierarchiák meghatározása
* Egy oszlop formázásának, alapértelmezett összegzésének és rendezési sorrendjének meghatározása
* Értékek csoportosítása vagy fürtösítése

A **DirectQuery** használatával ezen modellbővítések nagy részét el lehet végezni, és természetesen érvényes a nyers adatok bővítésének elve, a későbbi fogyaszthatóság javítása céljából. Ugyanakkor bizonyos modellezési funkciók vagy nem, vagy csak korlátozottan érhetők el a DirectQuery használatakor. A korlátozások általánosságban a teljesítményproblémák elkerülését szolgálják. A minden DirectQuery-forrásra egységesen jellemző korlátozásokat a következő felsorolás ismerteti. Egyes forrásokra további korlátozások is vonatkozhatnak, amelyeket a jelen cikk vége felé található, az *adatforrás-specifikus részletekkel* foglalkozó szakasz ismertet.

* **Nincs beépített dátumhierarchia:** Az adatok importálásakor alapértelmezés szerint minden dátum- és dátum/idő-oszlop rendelkezik egy beépített dátumhierarchiával. Például ha importálunk egy megrendeléseket tartalmazó táblát, amely tartalmaz egy OrderDate (Megrendelés dátuma) oszlopot, majd ezen oszlopot felhasználjuk egy vizualizációhoz, akkor kiválasztható lesz a vizualizációban használandó szint (év, hónap, nap). A DirectQuery módban ez a beépített dátumhierarchia nem elérhető el. Azonban fontos megjegyezni, hogy ha az alapul szolgáló forrásban van egy elérhető Date (Dátum) tábla (ami az adattárházak körében gyakori), akkor a DAX Időintelligencia függvények a szokott módon használhatók.
* **Dátum és idő legfeljebb másodperces precizitással támogatott:** Ha az adathalmazban idő jellegű oszlopok szerepelnek, a Power BI csak másodperces részletességű lekérdezéseket végez a mögöttes forráson. Ezredmásodpercekre vonatkozó lekérdezések nem lesznek a DirectQuery-forráshoz továbbítva, tehát a forrás oszlopaiban az időértékeknek ezt a részét el kell távolítania.
* **Számított oszlopok korlátozásai:** A számított oszlopoknak soron belülinek kell lenniük, azaz csak ugyanazon tábla más oszlopainak értékeire hivatkozhatnak, összesítési függvények használata nélkül. Emellett a DAX skaláris függvények (pl. LEFT ()) közül csak azok engedélyezettek, amelyek egyszerűen leküldhetők az alapul szolgáló forrás felé – hogy ezek melyek, az a forrás konkrét képességeitől függ. A nem támogatott függvények nem lesznek felsorolva az automatikus kiegészítési lehetőségek között a számított oszlop DAX-függvényeinek szerkesztésekor, és ha használni próbálja őket, hibát eredményeznek.
* **A szülő–gyermek DAX-függvények nem támogatottak:** A DirectQuery modellben nem használható a DAX PATH() függvénycsalád, amely általában a szülő–gyermek struktúrákat kezeli (például fiókok ábrázolásakor vagy az alkalmazotti hierarchiákban).
* **A számított táblák nem támogatottak:** A DirectQuery módban nem támogatott a számított táblázatok meghatározása egy DAX-kifejezés használatával.
* **Kapcsolatszűrés:** A kétirányú szűrés használatát [ez a tanulmány](https://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx) ismerteti részletesebben (a tanulmány az SQL Server Analysis Services kontextusában hoz példákat, de az alapvető pontok a Power BI-ra is ugyanúgy érvényesek).

* **Nincs fürtszolgáltatás:** A DirectQuery használatakor nem használható a Fürtszolgáltatás funkció csoportok automatikus megkereséséhez.

### <a name="reporting-limitations"></a>Jelentéskészítési korlátozások
A DirectQuery-modellek majdnem minden jelentéskészítési funkciót támogatnak. Ennélfogva amíg az alapul szolgáló forrás megfelelő teljesítményt nyújt, addig ugyanazok a vizualizációk használhatók. Azonban néhány fontos korlátozás vonatkozik a **Power BI szolgáltatás** képességeire egy jelentés közzététele után, amelyeket a következő lista ír le:

* **A Quick Insights nem támogatott:** A Power BI Quick Insights kifinomult algoritmusok alkalmazásával részhalmazokat keres az adatkészletben potenciálisan érdekes összefüggések feltárásához. A nagy lekérdezési teljesítmény igénye miatt a DirectQuery használatakor ez a lehetőség nem használható az adatkészleteken.
* **A Q&A szolgáltatás nem támogatott:** A Power BI Q&A szolgáltatása lehetővé teszi az adatok felderítését intuitív, természetes nyelvi képességek segítségével, majd diagramok és grafikonok formájában adja meg válaszokat. Ez azonban a DirectQueryt használó adatkészletek esetében jelenleg nem támogatott.
* **Az Excelbeli kezelés feltehetően gyenge teljesítményt eredményez:** Az adatok egy adathalmazban a „Kezelés az Excelben” képesség használatával is kezelhetők. A képesség lehetővé teszi kimutatástáblák és kimutatásdiagramok létrehozását az Excelben. Noha a DirectQuery támogatja e képesség használatát az adatkészleteken, de a teljesítmény általánosságban lassabb lesz tőle, mintha vizualizációkat hoznánk létre a Power BI-ban. Ennélfogva ha az Excel használata fontos az Ön forgatókönyvei számára, akkor számoljon ezzel a tényezővel, amikor a DirectQuery használata mellett vagy ellen dönt.

### <a name="security"></a>Biztonság
Ahogy a cikk korábbi része is említette, a **DirectQueryt** használó jelentések mindig ugyanazokat a rögzített hitelesítő adatokat használják az alapul szolgáló adatforrás eléréséhez a **Power BI szolgáltatásban** való közzététel után. Ez kimondottan csak a DirectQueryre vonatkozik, nem az SQL Server Analysis Serviceshez létesített élő kapcsolatokra, amelyek ebből a szempontból eltérőek. Ezért közvetlenül egy DirectQuery-jelentés közzététele után meg kell adni a használandó felhasználó hitelesítő adatait. Amíg ez nem történt meg, a jelentés megnyitása a Power BI szolgáltatásban hibát fog eredményezni.

A hitelesítő adatok megadását követően a rendszer mindig ezeket a hitelesítő adatokat használja, *függetlenül arról, hogy a jelentést melyik felhasználó nyitja meg*. Ez pontosan ugyanolyan, mint az importált adatok, abból a szempontból, hogy minden felhasználó ugyanazokat az adatokat látja, kivéve, ha sorszintű biztonsági intézkedések lettek megadva a jelentés részeként. Ezért ugyanolyan körültekintőnek kell lenni a jelentés megosztásakor is azt illetően, hogy vannak-e biztonsági szabályok megadva az alapul szolgáló forrásban.

### <a name="behavior-in-the-power-bi-service"></a>Viselkedés a Power BI szolgáltatásban
Ez a szakasz leírja a **DirectQuery**-jelentések viselkedését a **Power BI szolgáltatásban**, elsősorban azzal a céllal, hogy felmérhető legyen a háttérbeli adatforrás terhelésének mértéke, figyelembe véve, hogy a jelentés és az irányítópult hány felhasználóval lesz megosztva, hogy a jelentés mennyire összetett, és hogy a jelentésben van-e meghatározva sorszintű biztonság.

#### <a name="reports--opening-interacting-with-editing"></a>Jelentések – megnyitás, használat, szerkesztés
Egy jelentés megnyitásakor az épp látható oldalon található összes vizualizáció frissül. Általában mindegyik vizualizáció legalább egy lekérdezést igényel az alapul szolgáló forrás felé. Egyes vizualizációk egynél több lekérdezést is igényelhetnek (például ha két különböző ténytábla összesített értékeit mutatják, vagy egy összetettebb mértéket tartalmaznak, vagy olyan nem additív mértékek összegeit, mint az Eltérők darabszáma). Egy új lapra áthelyezéskor a vizualizációk eredményei frissülnek, amihez újabb lekérdezéseket kell indítani az alapul szolgáló forrás felé.

A jelentéssel kapcsolatos minden felhasználói interakció a vizualizációk frissítését eredményezheti. Ha például egy másik értéket választunk ki egy szeletelőn, ahhoz új lekérdezéseket kell elküldeni az összes érintett vizualizáció frissítése céljából. Ugyanez igaz akkor is, ha rákattintunk egy vizualizációra egy másik vizualizáció keresztkiemeléséhez, vagy módosítunk egy szűrőt.  

Emellett az új jelentés szerkesztésének minden lépésénél is új lekérdezéseket kell elküldeni, a kívánt végső vizualizáció létrehozásához.

A rendszer gyorsítótáraz bizonyos eredményeket, így ha egy lekérdezésnek már megvannak az eredményei, akkor a vizualizáció azonnal frissül. Az ilyen gyorsítótárakat nem lehet több felhasználó között megosztani, ha a jelentésben meg van adva bármilyen sorszintű biztonság.

#### <a name="dashboard-refresh"></a>Irányítópult frissítése
Egy-egy vizualizáció vagy teljes oldalak is kitűzhetők az irányítópultokra csempék formájában. A **DirectQuery**-adatkészleteken alapuló csempék ezután automatikusan frissíthetők egy ütemezés szerint, aminek hatására a rendszer lekérdezéseket küld a háttérrendszeri adatforrás felé. Ez alapértelmezés szerint óránként egyszer történik meg, de az adatkészlet beállításai között időintervallumok széles skálája megadható, egy héttől 15 percig.

Ha a modell nem tartalmaz Sorszintű biztonságot, akkor a rendszer minden csempét egyszer frissít, az eredményeket pedig megosztja az összes felhasználóval. Ha meg van adva Sorszintű biztonság, az jelentős többszöröző hatással bír – minden csempéhez felhasználónként kell lekérdezéseket küldeni az alapul szolgáló forrás felé.  

Így egy tíz csempéből álló, 100 felhasználóval megosztott irányítópult, amely a **DirectQueryvel** és Sorszintű biztonsággal lett létrehozva, és 15 percenkénti frissítésre van konfigurálva, 15 percenként legalább 1000 lekérdezést küld a háttérrendszeri kiszolgáló felé.

Ezért kell alaposan megfontolni a Sorszintű biztonság használatát és a frissítési ütemezés beállítását.

#### <a name="timeouts"></a>Időtúllépések
A **Power BI szolgáltatásban** minden egyes lekérdezésre négy perces időtúllépési idő vonatkozik, az ennél tovább tartó lekérdezések pedig sikertelenek lesznek. Ahogy korábban is hangsúlyoztuk, a DirectQueryt olyan adatforrásokhoz javasolt használni, amelyek közel interaktív lekérdezési teljesítménnyel bírnak, így ennek a korlátozásnak a célja is a túl hosszú végrehajtási időkből eredő problémák megelőzése.

### <a name="other-implications"></a>Egyéb következmények
A **DirectQuery** használatának egyéb általános következményei közé tartoznak a következők:

* **Az adatok módosítása esetén a legújabb adatok megjelenítéséhez frissítés szükséges:** A gyorsítótárak használata miatt nem biztosítható, hogy a vizualizáció mindig a legfrissebb adatokat jelenítse meg. Mutathatják például az elmúlt egy nap tranzakcióit. Majd egy szeletelő módosítása miatt a vizualizáció frissül, és már az elmúlt két nap tranzakcióit mutatja, beleértve egy friss, újonnan érkezett tranzakciót. Ha a szeletelőt visszaállítjuk az eredeti értékére, akkor újra a korábban gyorsítótárazott értéket fogja mutatni, amely nem tartalmazza az imént látott, újonnan érkezett tranzakciót.
  
  A Frissítés kiválasztásakor a gyorsítótárak törlődnek, az oldalon található vizualizációk pedig frissülnek, és a legújabb adatokat jelenítik meg.
* **Változó adatok esetén a vizualizációk közötti konzisztencia nem garantálható:** Az azonos vagy külön oldalon lévő különböző vizualizációk más időpontban frissülhetnek. Ennélfogva az alapul szolgáló forrás változásakor nincs garancia arra, hogy az adatokat megjelenítő minden vizualizáció ugyanabban az időpontban fog frissülni. Sőt, tekintve, hogy néha egyetlen vizualizációhoz is több lekérdezés szükséges (például a részletek és az összegek lekéréséhez), még az egyes vizualizációkon belüli konzisztencia sem garantált. Ehhez arra lenne szükség, hogy bármely vizualizáció frissítésekor az összes vizualizáció frissüljön, az olyan költséges funkciókkal együtt, mint a pillanatkép-elkülönítés az alapul szolgáló adatforrásban.
  
  E probléma jelentősen enyhíthető a Frissítés újbóli választásával, mellyel frissítheti az adott oldalon található összes vizualizációt. Fontos megjegyezni, hogy még az Importálás módban is hasonlóan problémás a konzisztencia biztosítása, ha egynél több táblából importálunk adatokat.
* **A metaadatok változásainak megjelenéséhez a Power BI Desktopban végzett frissítés szükséges:** Egy jelentés közzététele után a Frissítés művelet a jelentésbeli vizualizációkat frissíti. Ha az alapul szolgáló forrás sémája megváltozott, akkor a változások nem módosítják automatikusan az elérhető mezőket a mezőlistában. Ezáltal ha a forrásból táblák vagy oszlopok lettek eltávolítva, az a lekérdezés sikertelenségéhez vezethet frissítéskor. A jelentés megnyitása a Power BI Desktopban és a Frissítés parancs kiválasztása frissíti a mezőket a modellben, hogy tükrözzék a változásokat.
* **Legfeljebb egymillió sor adható vissza bármely lekérdezésre:** Van egy olyan korlátozás, hogy legfeljebb egymillió sor adható vissza az alapul szolgáló forrás felé irányuló minden önálló lekérdezésre. Ennek általában semmilyen gyakorlati következménye nincs, mivel a vizualizációk nem jelenítenek meg ennyi pontot. Azonban olyan esetekben teljesülhet ez a határérték, amikor a Power BI nem optimalizálja teljesen az elküldött lekérdezéseket, és valamilyen köztes eredményt kérdez le, amely meghaladja ezt a határértéket. Előfordulhat még vizualizációk létrehozása közben is, a vizualizációk végső állapotának elérése előtt. Például a Customer (Ügyfél) és a TotalSalesQuantity (Értékesítések teljes száma) belefoglalásával beteljesül a határérték, ha több mint egymillió ügyfél szerepel a forrásban, hacsak nem alkalmazunk valamilyen szűrőt.
  
  Az ekkor megjelenő hibaüzenet a következő: „A külső adatforráshoz intézett lekérdezés eredményhalmaza meghaladta a(z) „1000000” maximális sorszámot.”
* **Nem lehet az importálásról DirectQuery módra váltani:**  Habár általánosságban át lehet váltani egy modellt a DirectQuery módból az importálási mód használatára, de ez azzal jár, hogy az összes szükséges adatot importálni kell. Ezenkívül nem lehet visszaváltani (elsősorban azért, mert a DirectQuery mód nem támogatja a funkciók készletét). A többdimenziós forrásokkal, például az SAP BW-vel használt DirectQuery-modelleket szintén nem lehet átváltani DirectQuery módból importálási módba, a külső mértékek eltérő kezelése miatt.

## <a name="directquery-in-the-power-bi-service"></a>DirectQuery a Power BI szolgáltatásban
A **Power BI Desktop** által támogatott összes forrás támogatott. Egyes források elérhetők közvetlenül a **Power BI szolgáltatásból** is. Az üzleti felhasználók például megtehetik, hogy a Power BI segítségével kapcsolódnak a Salesforce-ban található adataikhoz, és azonnal lekérnek egy irányítópultot, a **Power BI Desktop** használata nélkül.

A DirectQueryt támogató források közül csak kettő érhető el közvetlenül a szolgáltatásban:

* Spark
* Azure SQL Data Warehouse

Ajánlott azonban az ezzel a két forrással kapcsolatos bármilyen **DirectQuery**-műveletet a **Power BI Desktopból** elindítani. Ennek az az oka, hogy a **Power BI szolgáltatásban** az első kapcsolódáskor számos kulcskorlátozás áll fenn, vagyis habár a kezdőpont (a Power BI szolgáltatásból kezdés) könnyű volt, de a jelentés további bővítése korlátokba ütközik (például nem lehet számításokat létrehozni, vagy használni számos elemzési funkciót, vagy egyáltalán frissíteni a metaadatokat, hogy tükrözzék az alapul szolgáló sémát).   

## <a name="guidance-for-using-directquery-successfully"></a>Útmutatás a DirectQuery sikeres használatához
Ha a **DirectQuery** mellett dönt, akkor ebben a szakaszban részletes útmutatást talál a használatáról. A szakaszban található útmutatás a DirectQuery használatának jelen cikkben leírt következményeiből van levezetve.

### <a name="backend-data-source-performance"></a>Háttérrendszeri adatforrások teljesítménye
Célszerű ellenőriznie, hogy az egyszerű vizualizációk ésszerű időn belül – interaktív funkciók esetében 5 másodpercen belül – frissíthetők-e. Ha a vizualizációk frissítése 30 másodpercnél több időt vesz igénybe, akkor igen valószínű, hogy további problémák is fel fognak lépni a jelentés közzétételét követően, így e megoldás nem használható.

Ha a lekérdezések lassúak, akkor először meg kell vizsgálni az alapul szolgáló forrás felé küldött lekérdezéseket, és a lekérdezések teljesítménye megfigyelésének okát. A jelen cikk nem tartalmazza az összes lehetséges alapul szolgáló forrásra vonatkozó számos ajánlott eljárást, azonban alkalmazható a legtöbb esetben érvényes szabványos adatbázis-kezelési gyakorlatokra:

* Az egész számokat tartalmazó oszlopokon alapuló kapcsolatok általában jobban teljesítenek, mint az egyéb adattípusú oszlopokhoz való csatlakozások
* Létre kell hozni a megfelelő indexeket, ami általában az oszloptárindexek használatát jelenti azon forrásokban, amelyek támogatják ezeket (például az SQL Server).
* Frissíteni kell minden szükséges statisztikát a forrásban

### <a name="model-design-guidance"></a>Modelltervezési útmutatás
Modellek meghatározásakor fontolja meg az alábbiakat:

* **Kerülje az összetett lekérdezéseket a Lekérdezésszerkesztőben.** A Lekérdezésszerkesztőben meghatározott lekérdezéseket a rendszer lefordítja önálló SQL-lekérdezésekké, amelyeket aztán belefoglal az adott tábla részére elküldött összes lekérdezés részkiválasztásába. Ha ez a lekérdezés túl összetett, az rossz hatással lehet az összes elküldött lekérdezés teljesítményére. A több lépésre vonatkozó SQL-lekérdezéseket lekérheti, ha a Lekérdezésszerkesztőben az utolsó lépésnél kiválasztja a helyi menüből a *Natív lekérdezés megtekintése* lehetőséget.
* **Használjon egyszerű mértékeket.** Ajánlott a mértékeket egyszerű összegekre korlátozni, kezdetben legalábbis. Ha ezek megfelelően teljesítenek, később összetettebb mértékeket is megadhat, de mindegyiknek figyeljen a teljesítményére.
* **Kerülje a számított oszlopokra mutató kapcsolatokat.** Ez olyan adatbázisok esetében igaz, ahol több oszlophoz kell kapcsolódást végrehajtani. A Power BI jelenleg nem engedi, hogy a kapcsolatok több oszlopon alapuljanak – mint a Külső kulcs/Elsődleges kulcs. A leggyakoribb megkerülő megoldás az oszlopok összefűzése egy számított oszlop használatával, majd kapcsolódás ehhez az oszlophoz. Ez a megoldás importált adatok esetében jól működik, a **DirectQuery** esetében azonban azt eredményezi, hogy a kapcsolódás egy kifejezéshez vezet, ami általában meggátolja az indexek használatát és gyenge teljesítményt eredményez. Az egyetlen valós megoldás az, ha a több oszlopot az alapul szolgáló adatbázisban vonjuk össze egyetlen oszlopba.
* **Kerülje a uniqueidentifier típusú oszlopokra mutató kapcsolatokat.** A Power BI nem támogatja natív módon a uniqueidentifier adattípust. Ezért ha egy uniqueidentifier típusú oszlophoz adunk meg egy kapcsolatot, az egy olyan lekérdezést eredményez, amelyben egy kapcsolat egyik tagja egy Cast. Ez általában szintén gyenge teljesítményt eredményez. Amíg nem kerül sor ennek az esetnek a külön optimalizálására, az egyetlen megkerülő megoldás az lesz, ha az alapul szolgáló adatbázisban más típust adunk meg az oszlopokhoz.
* **Rejtse el a *to* oszlopot a kapcsolatokban.** A kapcsolatok *to* oszlopát (jellemzően a *to* tábla elsődleges kulcsát) érdemes elrejteni, hogy ne jelenjen meg a mezőlistában, és így ne is legyen használható a vizualizációkban. A kapcsolatok alapjául szolgáló oszlopok valójában gyakran *rendszeroszlopok* (például helyettesítő kulcsok egy adattárházban), és az ilyen oszlopokat eleve érdemes elrejteni. Ha az oszlopnak van jelentése, akkor hozzon létre egy számított oszlopot, amely látható, és egy egyszerű kifejezést tartalmaz, amely azonos az elsődleges kulccsal. Például:
  
      ProductKey_PK   (Destination of a relationship, hidden)
      ProductKey (= [ProductKey_PK],   visible)
      ProductName
      ...
  
  Ennek oka egyszerűen az, hogy elkerüljünk egy teljesítményproblémát, amely akkor fordulhat elő, ha egy vizualizáció tartalmazza az elsődleges kulcsoszlopot.
* **Vizsgálja meg a számított oszlopok és az adattípus-módosítások összes felhasználását.** Ezen funkciók használata nem feltétlenül káros, mivel azt eredményezik, hogy az alapul szolgáló forrás felé küldött lekérdezések kifejezéseket tartalmazzanak egyszerű oszlophivatkozások helyett, ami szintén ahhoz vezet, hogy nem lesznek indexek használva.  
* **Kerülje a kétirányú keresztszűrés használatát a kapcsolatokban.** A kétirányú keresztszűrés használata olyan lekérdezési utasításokhoz vezethet, melyek teljesítménye nem megfelelő.
* **Kísérletezzen a *Hivatkozási integritás feltételezése* beállítással.** A kapcsolatok *Hivatkozási integritás feltételezése* beállítása lehetővé teszi, hogy a lekérdezések INNER JOIN utasításokat használjanak az OUTER JOIN helyett. Ez általában javítja a lekérdezések teljesítményét, bár ez az adatforrás pontos jellemzőitől is függ.
* **Ne használja a relatív adatszűrést a Lekérdezésszerkesztőben.** Lehetőség van relatív dátumszűrés megadására a Lekérdezésszerkesztőben. Például ki lehet szűrni az olyan sorokat, amelyek dátuma az elmúlt 14 napon belülre esik.
  
  ![](media/desktop-directquery-about/directquery-about_02.png)
  
  Ezt azonban a rendszer egy rögzített dátumon alapuló szűrőnek fordítja le, amely a lekérdezés létrehozási dátumához képest működik. Ez a natív lekérdezés megtekintésekor látható.
  
  ![](media/desktop-directquery-about/directquery-about_03.png)
  
  Szinte biztos, hogy az eredeti cél nem ez volt. Ahhoz, hogy a szűrő ehelyett a jelentés végrehajtásának dátumát vegye alapul, alkalmazza a szűrőt a jelentésben jelentésszűrőként. Ezt jelenleg úgy lehet megtenni, ha létrehoz egy számított oszlopot, amely kiszámolja, hogy a dátum hány nappal ezelőtt volt (a DAX DATE() függvény használatával), majd ezt a számított oszlopot használja szűrőként.

### <a name="report-design-guidance"></a>Jelentéstervezési útmutatás
DirectQuery-kapcsolat használatával történő jelentéskészítéskor tartsa be a következő útmutatást:

* **Fontolja meg a lekérdezések csökkentésének lehetőségét:** A Power BI-ban beállítható, hogy a jelentések kevesebb számú lekérdezést küldjenek, és letiltható néhány olyan interakció is, amelynek a végrehajtása hosszú időt igényel, és így negatívan befolyásolhatja a felhasználói élményt. A **Power BI Desktopban** ezeket a beállításokat a **Fájl > Lehetőségek és beállítások > Beállítások** menüpont alatt a **Lekérdezések csökkentése** lehetőségnél találja meg. 

   ![](media/desktop-directquery-about/directquery-about_03b.png)

    A **Lekérdezések csökkentése** területen lehetősége van letiltani a keresztkiemeléseket a teljes jelentésre vonatkozóan. Ezen kívül megjeleníthető egy *Alkalmaz* gomb is a szeletelők és/vagy a szűrők kiválasztásánál, ami lehetővé teszi, hogy még az alkalmazás előtt kiválasszon több szeletelőt vagy szűrőt, ez pedig azt eredményezi, hogy addig nem történik lekérdezés, amíg nem kattint az **Alkalmaz** gombra a szeletelőnél. Ezt követően a szeletelőkkel elvégezhető az adatszűrés.

    Ezek a beállítások érvényesek a jelentésre a **Power BI Desktop** használatánál, valamint akkor is, ha a felhasználók a **Power BI szolgáltatásban** használják a jelentést.

* **Először alkalmazza a szűrőket:** A vonatkozó szűrőket mindig alkalmazza a vizualizáció létrehozásának legelején. Például ahelyett, hogy behúzná a TotalSalesAmount és ProductName oszlopokat, majd rászűrne egy adott évre, alkalmazza az év szerinti szűrést rögtön a legelején. Ez azért fontos, mert a vizualizációk létrehozásának minden lépése elküld egy lekérdezést, és lehet ugyan módosításokat végezni az első lekérdezés teljesítése után is, de ez csak feleslegesen terheli az alapul szolgáló forrást. A szűrők korai alkalmazása általában csökkenti a közbeeső lekérdezések költségeit. Emellett a szűrők korai alkalmazásának elmulasztása esetén átlépheti a fentebb említett egymillió soros határértéket.
* **Korlátozza az egy oldalon található vizualizációk számát:** Az oldalak megnyitásakor (vagy valamilyen oldalszintű szeletelő vagy szűrő módosításakor) az oldal összes vizualizációja frissül. Korlátozva van a párhuzamosan elküldhető lekérdezések száma is, így ahogy a vizualizációk száma növekszik, egyes vizualizációk csak egymás után frissülnek, ami növeli az egész oldal frissítéséhez szükséges időt. Emiatt ajánlott korlátozni az egy oldalon található vizualizációk számát, és ehelyett több, egyszerűbb oldalt készíteni.
* **Vegye fontolóra a vizualizációk közti interakció kikapcsolását:** Alapértelmezés szerint egy jelentésoldal vizualizációi az oldal további vizualizációinak keresztszűréséhez és keresztkijelöléséhez használhatók. Ha például a kördiagramon kiválasztja „1999”-et, az oszlopdiagramon keresztkiemeléssel jelennek meg az „1999”-re vonatkozó értékesítések, kategóriák szerint.                                                                  
  
  ![](media/desktop-directquery-about/directquery-about_04.png)
  
  A DirectQueryben az ilyen keresztszűréshez és keresztkiemeléshez lekérdezéseket kell küldeni az alapul szolgáló forrás felé, ezért érdemes az interakciót kikapcsolni, ha túl hosszú lenne az az idő, amíg a rendszer reagál a felhasználók kiválasztásaira. Ez az interakció azonban ki is kapcsolható akár a teljes jelentésre vonatkozóan (lásd fentebb a *Lekérdezések csökkentésének beállításánál*), vagy külön-külön is az [ebben a cikkben](consumer/end-user-interactions.md) leírtak alapján.

A fenti javaslatok mellett vegye figyelembe, hogy a következő jelentéskészítési funkciók is okozhatnak teljesítményproblémákat:

* **Mértékszűrők:** A mértékeket (vagy mértékek összegeit) tartalmazó vizualizációk a mértékeken belüli szűrőket is tartalmazhatnak. Például az alábbi vizualizáció az értékesített mennyiségeket mutatja kategóriák szerint, de csak a 20 milliós értékesítés feletti kategóriákat tartalmazza.
  
  ![](media/desktop-directquery-about/directquery-about_05.png)
  
  Ehhez két lekérdezést kell elküldeni az alapul szolgáló forrás felé:
  
  * Az első lekérdezés lekéri a feltételnek (20 millió fölötti értékesítés) megfelelő kategóriákat.
  * Ezután a második lekérdezés lekéri a vizualizációhoz szükséges adatokat, beleértve a kategóriákat, amelyek megfeleltek a WHERE utasításban szereplő feltételeknek.  
  
  Ez a módszer általában jól működik, ha néhány száz vagy ezer kategória van, mint ebben a példában. Ha a kategóriák száma sokkal több, a teljesítmény csökken (ráadásul ha egymilliónál több kategória felel meg a feltételnek, akkor a lekérdezés sikertelen lesz, a korábban említett egymillió soros korlátozás miatt).
* **Legjobb N szűrők:** Megadhatók fejlettebb szűrők, amelyek egy adott mérték által rangsorolt első (vagy utolsó) N számú értéket szűrik ki, például csak az első 10 kategóriát a fenti vizualizációban. Ehhez szintén két lekérdezést kell elküldeni az alapul szolgáló forrás felé. Az első lekérdezésre azonban az alapul szolgáló forrás az összes kategóriát visszaadja, majd a legjobb N értéket a visszaadott eredmények alapján választja ki a rendszer. Ez az érintett oszlop számosságától függően teljesítményproblémákat okozhat (vagy a lekérdezés sikertelenségét az egymilliós határérték miatt).
* **Medián:** Általában a rendszer minden összesítést (Összeg, Eltérők darabszáma stb.) elküld az alapul szolgáló forrásnak. Ez azonban nem igaz a Középérték esetében, mivel ezt az összesítést az alapul szolgáló források általában nem támogatják. Ezekben az esetekben a Power BI részletadatokat kérdez le az alapul szolgáló forrástól, és ezek visszaadott eredményei alapján számítja ki a középértéket. Ez megfelelő megoldás lehet, ha viszonylag kis számú eredmény mediánját kell kiszámolni, de teljesítményproblémákat okozhat, ha a számosság nagy (vagy sikertelen lekérdezéseket az 1 milliós határérték miatt).  Például egy megye lakosságának mediánját jól ki lehet számolni, de az értékesítési árak mediánját már nem biztos.
* **Speciális szövegszűrők („tartalmaz” és hasonlók):** Egy szöveges oszlop szűrésekor a speciális szűrők között megtalálhatók a „tartalmaz”, „kezdődik” és hasonló szűrők. Ezek teljesítménycsökkenést okozhatnak bizonyos adatforrások esetében. Konkrétan a „tartalmaz” szűrőt nem szabad használni, ha pontos találatokra van szükség („egyezik” vagy „nem egyezik”). Bár az eredmények ugyanazok lehetnek, a konkrét adatoktól függően a teljesítményben komoly különbségek mutatkozhatnak az indexek használata miatt.
* **Többszörös kijelölés szeletelőkben:** Alapértelmezés szerint a szeletelők csak egyetlen kijelölést engedélyeznek. A szűrők között a többszörös kijelölés engedélyezése teljesítményproblémákat okozhat, mivel ahogy a felhasználó kiválaszt néhány elemet a szeletelőből (például tíz terméket, ami érdekli), minden egyes új kijelöléssel új lekérdezések történnek a háttérrendszeri forrás felé. Bár a felhasználó még a lekérdezés teljesítése előtt kijelölheti a következő elemet, de ez így is felesleges terhelést okoz az alapul szolgáló forráson.

* **Fontolja meg az összegzések kikapcsolását a vizualizációkban:** A táblázatok és mátrixok alapértelmezés szerint összegeket és részösszegeket is megjelenítenek. Ezeknek az eredményeknek e lekérdezéséhez azonban sok esetben külön lekérdezést kell küldeni az alapul szolgáló adatkészlethez. Ez történik minden olyan esetben, amikor *DistinctCount* összesítést használ, illetve ha az SAP BW-re vagy az SAP HANA-ra irányuló DirectQueryt használ. Ha nincs szüksége rá, ezeket az összegzéseket ajánlatos kikapcsolni (a **Formázás** panel használatával). 

### <a name="maximum-number-of-connections-option-for-directquery"></a>A DirectQuery-kapcsolatok maximális számának beállítása

Minden mögöttes adatforráshoz beállíthatja a DirectQuery által megnyitott kapcsolatok maximális számát, így vezérelheti az egyes adatforrásoknak egyidejűleg küldött lekérdezések számát. 

Ekkor ez lesz a DirectQuery által egyidejűleg megnyitott kapcsolatok alapértelmezett maximális száma. Ezt módosíthatja az aktuális fájlhoz a **Power BI Desktop** **Fájl > Lehetőségek és beállítások > Beállítások** területén, a bal oldali panel **Aktuális fájl** szakaszában, a **DirectQuery** lehetőség kiválasztásával. 

![A DirectQuery-kapcsolatok maximális számának engedélyezése](media/desktop-directquery-about/directquery-about_05b.png)

Ez a beállítás csak akkor van engedélyezve, ha legalább egy DirectQuery-forrás található az aktuális jelentésben. Az érték minden DirectQuery-forrásra vonatkozik, valamint a jelentéshez adott új DirectQuery-forrásokra is.

A **kapcsolatok maximális számának** (a megadott mennyiségig történő) növelésével több lekérdezés küldését teheti lehetővé a mögöttes adatforrásnak, ami hasznos lehet, ha számos vizualizáció található egyetlen lapon, vagy sok felhasználó szeretne egyszerre hozzáférni egy jelentéshez. A kapcsolatok maximális számának elérése után a lekérdezések üzenetsorba kerülnek, amíg egy kapcsolat elérhetővé nem válik. A korlát növelése nagyobb terhelést eredményez a mögöttes forráson, a beállítás használata így nem garantál jobb teljesítményt.

A jelentés közzététele után a mögöttes adatforrásnak egyidejűleg küldött lekérdezések maximális száma szintén rögzített korlátokon alapul, amely pedig a közzétett jelentés célkörnyezetétől függ. Különböző környezetek (például a Power BI, a Power BI Premium vagy a Power BI jelentéskészítő kiszolgáló) különböző korlátokat szabhatnak.

### <a name="diagnosing-performance-issues"></a>Teljesítményproblémák diagnosztizálása
Ez a szakasz leírja, hogyan diagnosztizálhatja a teljesítményproblémákat, vagy hogyan kérhet le részletesebb információkat, amelyek lehetővé teszik a jelentések optimalizálását.

Erősen ajánlott a teljesítményproblémák diagnosztizálását a **Power BI Desktopban** elkezdeni, nem a **Power BI szolgáltatásban**. A teljesítményproblémákat gyakran egyszerűen az alapul szolgáló forrás teljesítményszintje okozza, ezeket pedig könnyebb azonosítani és diagnosztizálni a **Power BI Desktop** sokkal elkülönítettebb környezetében, illetve ezzel bizonyos összetevők is kiiktathatók (például a Power BI átjáró). Csak akkor érdemes a Power BI szolgáltatásban a jelentés jellemzői közt vizsgálódni, ha a Power BI Desktopban nem észleli a teljesítményproblémákat. A [teljesítményelemző](desktop-performance-analyzer.md) hasznos eszköz a folyamat során felmerülő problémák azonosításához.

Hasonlóképp ajánlott a problémákat először egy különálló vizualizációban azonosítani, nem egy sok vizualizációt tartalmazó oldalon.

Tegyük fel, hogy elvégeztük ezeket a lépéseket (a szakasz előző bekezdéseiben felsoroltakat), és most egyetlen vizualizációnk van egy oldalon a **Power BI Desktopban**, amely még mindig lassú. A Power BI Desktop által a mögöttes forrásnak küldött lekérdezések meghatározásához használja a [teljesítményelemzőt](desktop-performance-analyzer.md). Áttekintheti a mögöttes forrás által esetlegesen kiadott nyomkövetési és diagnosztikai adatokat. Ezek a nyomkövetési adatok hasznos információkat tartalmazhatnak a lekérdezés végrehajtásának részleteiről és a lekérdezés javításának lehetőségeiről is.

Emellett még ha az ilyen nyomkövetési adatok hiányoznak is a forrásból, akkor is megtekinthetők a Power BI által küldött lekérdezések és a végrehajtási idejük a következő módon.

#### <a name="determining-the-queries-sent-by-power-bi-desktop"></a>A Power BI Desktop által küldött lekérdezések azonosítása
Alapértelmezés szerint a **Power BI Desktop** az egy adott munkamenet során történt eseményeket egy nyomkövetési fájlban rögzíti, amelynek a neve FlightRecorderCurrent.trc.

Egyes **DirectQuery**-források esetében ez a naplófájl tartalmazza az alapul szolgáló adatforrás felé küldött összes lekérdezést (a további DirectQuery-források lekérdezései a jövőbeli verziókban kerülnek be ebbe a fájlba). A következő források továbbítják a lekérdezéseket a naplóba:

* SQL Server
* Azure SQL Database
* Azure SQL Data Warehouse
* Oracle
* Teradata
* SAP HANA

A nyomkövetési fájl az aktuális felhasználó **AppData** mappájában található:

    \<User>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces

Ez a mappa a legkönnyebben a következő módon érhető el: A **Power BI Desktopban** válassza a **Fájl > Lehetőségek és beállítások > Beállítások**, majd a **Diagnosztika** elemet. Megjelenik a következő párbeszédablak:

![](media/desktop-directquery-about/directquery-about_06.png)

Amikor kiválasztja a *Nyomkövetési mappa megnyitása* hivatkozást, a **Diagnosztikai beállítások** alatt megnyílik a következő mappa:

    \<User>\AppData\Local\Microsoft\Power BI Desktop\Traces

E mappa szülő könyvtárába lépve megjelenik az *AnalysisServicesWorkspaces* mappa, amelyben újabb almappák találhatók a **Power BI Desktop** minden egyes megnyitott példányához. Ezek az almappák egész szám utótagokkal vannak elnevezve, például *AnalysisServicesWorkspace2058279583*.

Az almappákban van egy *\\Data* almappa, ebben található az aktuális Power BI-munkamenethez tartozó FlightRecorderCurrent.trc fájl. A Power BI Desktop-munkamenet befejezésekor az ahhoz tartozó munkaterületi mappa törlődik.

A nyomkövetési fájlok az **SQL Server Profiler** eszközzel olvashatók, amely az **SQL Server Management Studio** részeként ingyenesen letölthető. Ez az eszköz [innen](https://msdn.microsoft.com/library/mt238290.aspx) tölthető le.

Ha letöltötte és telepítette az **SQL Server Management Studio** eszközt, futtassa az **SQL Server Profiler** eszközt.

![](media/desktop-directquery-about/directquery-about_07.png)

A nyomkövetési fájl megnyitásához hajtsa végre a következő lépéseket:

1. Az **SQL Server Profiler** eszközben válassza a **File (Fájl) > Open (Megnyitás) > Trace file (Nyomkövetési fájl)** lehetőséget.
2. Írja be a jelenleg megnyitott Power BI-munkamenethez tartozó nyomkövetési fájl elérési útját, például:
   
         C:\Users\<user>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces\AnalysisServicesWorkspace2058279583\Data
3. Open FlightRecorderCurrent.trc

Megjelenik az aktuális munkamenet összes eseménye. Alább láthat egy jelmagyarázattal kiegészített példát, amely eseménycsoportokat emel ki. A csoportok a következőkkel rendelkeznek:

* Egy *Query Begin* (Lekérdezés kezdete) és egy *Query End* (Lekérdezés vége) esemény, amelyek egy felhasználói felületen (például egy vizualizációból vagy a szűrőfelület egy értéklistájából) létrehozott DAX-lekérdezés elejét és végét jelölik.
* Egy vagy több pár *DirectQuery Begin* (DirectQuery kezdete) és *DirectQuery End* (DirectQuery vége) esemény, amelyek egy-egy lekérdezés elküldését jelölik az alapul szolgáló adatforrás felé a DAX lekérdezés kiértékelésének keretében.

Vegye figyelembe, hogy több DAX-lekérdezés is végrehajtható párhuzamosan, így a különböző csoportok eseményei összefonódhatnak. Az ActivityID (Tevékenységazonosító) segítségével azonosítható, hogy mely események tartoznak ugyanazon csoporthoz.

![](media/desktop-directquery-about/directquery-about_08.png)

A további lényeges oszlopok a következők:

* **TextData:** Az esemény szöveges részletezése. A „Lekérdezés kezdete/vége” eseményeknél ez jelöli a DAX-lekérdezést. A „DirectQuery kezdete/vége” eseményeknél ez jelöli az alapul szolgáló forrásnak elküldött SQL-lekérdezést. A jelenleg kiválasztott esemény szöveges adatai az alsó régióban is megjelennek.
* **EndTime:** Az esemény befejezésének időpontja.
* **Duration:** A DAX- vagy SQL-lekérdezés végrehajtásához szükséges időtartam, ezredmásodpercben.
* **Error:** Jelzi, ha hiba történt (ez esetben az esemény vörös színnel jelenik meg).

A fenti képen néhány kevésbé lényeges oszlop keskenyítve lett, hogy a lényeges oszlopok jobban láthatók legyenek.

A potenciális teljesítményproblémák diagnosztizálásához szükséges nyomkövetés rögzítése az alábbi eljárással hajtható végre:

* Nyisson meg egyetlen **Power BI Desktop**-munkamenetet (a munkaterületi mappák összekeverésének elkerülése érdekében)
* Végezze el a vonatkozó műveleteket a **Power BI Desktopban**. Ezután végezzen el még néhány további műveletet, hogy a lényeges események biztosan bekerüljenek a nyomkövetési fájlba.
* Nyissa meg az **SQL Server Profiler** eszközt, és vizsgálja meg a nyomkövetési adatokat a fentebb leírt módon. Ne feledje, hogy a nyomkövetési fájl a **Power BI Desktop** bezárásakor törlődik. Emellett a Power BI Desktopban elvégzett további műveletek nem jelennek meg azonnal – az új események megtekintéséhez be kell zárni és újra megnyitni a nyomkövetési fájlt.
* Fogja rövidre az egyes munkameneteket (néhány tíz másodpercre, ne több százra), hogy könnyebb legyen értelmezni a nyomkövetési fájlt (már csak azért is, mert a nyomkövetési fájl mérete korlátozott, így a nagyon hosszú munkamenetek esetén megvan az esélye a korai események eltűnésének).

#### <a name="understanding-the-form-of-query-sent-by-power-bi-desktop"></a>A Power BI Desktop által küldött lekérdezések formátumának értelmezése
A **Power BI Desktop** által létrehozott és elküldött lekérdezések általános formátuma részkiválasztásokat használ minden egyes hivatkozott táblához, ahol a részkiválasztásokat a **Lekérdezésszerkesztőben** meghatározott lekérdezés határozza meg. Vegyük például az alábbi TPC-DS táblákat az SQL Server-kiszolgálón:

![](media/desktop-directquery-about/directquery-about_09.png)

Tekintse meg a következő lekérdezést:

![](media/desktop-directquery-about/directquery-about_10.png)

A lekérdezés eredménye a következő vizualizáció lesz:

![](media/desktop-directquery-about/directquery-about_11.png)

A vizualizáció frissítésének eredménye a következő bekezdés alatt látható SQL-lekérdezés lesz. Ahogy látható, három részkiválasztás van: Web Sales, Item és Date_dim, amelyek mindegyike visszaadja az adott táblákon található összes oszlopot, noha a vizualizáció összesen csak négy oszlopra hivatkozik. A részkiválasztásokban található lekérdezések (ezek árnyékoltak) pontosan a **Lekérdezésszerkesztővel** megadott lekérdezések eredményei. A részkiválasztások ily módon való használata az eddigi tapasztalatok szerint nem befolyásolja a teljesítményt a DirectQuery által jelenleg támogatott adatforrások esetében. Az SQL Server és hasonló adatforrások kioptimalizálják a hivatkozásokat a többi oszlopból.

A Power BI azért ezt a mintát használja, mert így a használt SQL-lekérdezést az elemzést végző személy közvetlenül adhatja meg, így pontosan a „megadott” állapotában használható, újraírási kísérlet nélkül.

![](media/desktop-directquery-about/directquery-about_12.png)

## <a name="next-steps"></a>Következő lépések
Ez a cikk a **DirectQuery** azon tulajdonságait írja le, amelyek minden adatforrás esetében közösek. Vannak bizonyos részletek, amelyek csak az egyes forrásokra érvényesek. Tekintse meg az egyes forrásokkal foglalkozó cikkeket is:

* [DirectQuery és SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery és SAP BW](desktop-directquery-sap-bw.md)

A **DirectQueryvel** kapcsolatos további információkért tekintse meg az alábbi forrásanyagokat:

* [A DirectQuery által támogatott adatforrások](desktop-directquery-data-sources.md)

