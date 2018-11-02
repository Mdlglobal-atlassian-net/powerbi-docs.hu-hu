---
title: Összetett modellek használata a Power BI Desktopban (előzetes verzió)
description: Több adatkapcsolattal és több-a-többhöz kapcsolatokkal rendelkező adatmodellek létrehozása a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 10/02/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 49540dd491d02c6a6b474ff80690a75eecfd27db
ms.sourcegitcommit: b8461c1876bfe47bf71c87c7820266993f82c0d3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/15/2018
ms.locfileid: "49336990"
---
# <a name="composite-models-in-power-bi-desktop-preview"></a>Összetett modellek a Power BI Desktopban (előzetes verzió)

Ha korábban a **Power BI Desktopban** DirectQueryt használt egy jelentésben, akkor más, akár DirectQuery vagy Importálás módú adatkapcsolatra sem volt lehetőség az adott jelentésben. Az **összetett modellekkel** ez a kötöttség megszűnik, és egy jelentés problémamentesen tartalmazhat több DirectQuery vagy Importálás módú adatkapcsolatot, bármilyen kívánt összetételben.

![összetett modellek a Power BI Desktopban](media/desktop-composite-models/composite-models_01.png)

Az **összetett modellek** használatának lehetősége a **Power BI Desktopban** három összefüggő funkcióból áll:

* **Összetett modellek** – Lehetővé teszi, hogy egy jelentés több adatkapcsolattal, köztük DirectQuery-kapcsolatokkal és importtal, vagy ezek bármilyen kombinációjával rendelkezzen.
* **Több-a-többhöz kapcsolatok** – Az **összetett modellekkel** a táblák között **több-a-többhöz kapcsolatok** hozhatók létre, kiküszöbölve ezzel az egyedi értékek követelményét, és szükségtelenné téve a korábbi kerülő megoldásokat, amilyen például új táblák bevezetése a kapcsolatok létrehozásához. 
* **Tárolási mód** – Mostantól megadható, hogy mely vizualizációk igényelnek a háttér-adatforrásokba irányuló lekérdezéseket. Azok, amelyekhez erre nincs szükség, importálva lesznek még akkor is, ha DirectQuery-alapúak. Ezáltal javul a teljesítmény, és csökken a háttérbeli adatforgalom. Korábban még az olyan egyszerű vizualizációk, mint a szeletelők is kezdeményeztek a háttérbeli forrásokba irányuló lekérdezéseket. 

Az **összetett modelleknek** ezt a három, egymással összefüggő funkcióját külön cikkek ismertetik:

* Az **összetett modelleket** ez a cikk írja le részletesen.
* A **több-a-többhöz kapcsolatokról** a következő cikk szól részletesen: [Több-a-többhöz kapcsolatok a Power BI Desktopban (előzetes verzió)](desktop-many-to-many-relationships.md).
* A **tárolási módokról** a következő cikk szól részletesen: [Tárolási mód a Power BI Desktopban (előzetes verzió)](desktop-storage-mode.md).

## <a name="enabling-the-composite-models-preview-feature"></a>Az előzetes verziójú Összetett modell funkció engedélyezése

Az **Összetett modellek** előzetes verziójú funkció, és azt a **Power BI Desktopban** engedélyezni kell. Az **Összetett modellek** funkció engedélyezéséhez válassza a **Fájl > Lehetőségek és beállítások > Lehetőségek > Előzetes verziójú funkciók** lehetőséget, majd jelölje be az **összetett modellek** jelölőnégyzetet. 

![előzetes funkciók engedélyezése](media/desktop-composite-models/composite-models_02.png)

Ahhoz, hogy a funkció engedélyezve legyen, újra kell indítania a **Power BI Desktopot**.

![a változások érvénybe léptetéséhez újraindítás szükséges](media/desktop-composite-models/composite-models_03.png)


## <a name="using-composite-models"></a>Az összetett modellek használata

**Összetett modellek** használatával számos különböző adatforrást kapcsolhat össze a **Power BI Desktop** vagy a **Power BI szolgáltatás** segítségével, és ezeket az adatkapcsolatokat többféleképpen is létrehozhatja. Importálhat adatokat a Power BI-ba, ez az adatok lekérésének leggyakoribb módja, vagy közvetlenül is csatlakozhat az eredeti forrásadattárukban lévő adatokhoz a DirectQuery használatával. A DirectQueryről a [DirectQuery használata a Power BI-ban](desktop-directquery-about.md) című cikkben talál további részletes információkat.

DirectQuery használata esetén **összetett modellekkel** létrehozható egy olyan Power BI-modell (például egy különálló .pbix Power BI Desktop-fájl), amely a következőket végzi el:

* egy vagy több DirectQuery-forrásból származó adatokat egyesít, és/vagy
* DirectQuery-forrásokból származó és importált adatokat egyesít

**Összetett modellek** használatával készíthető például olyan modell, amely egy vállalat adattárházából származó értékesítési adatokat egyesít egy részleg SQL Server-adatbázisában tárolt értékesítési cél adatokkal és egy munkafüzetből származó adatokkal. Az egynél több DirectQuery-forrás adatait egyesítő, vagy DirectQuery- és importált adatokat egyesítő modelleket *összetett modellnek* nevezzük.

> [!NOTE]
> A **Power BI Desktop** 2018. októberi kiadásától kezdődően összetett modelleket *tehet közzé* a Power BI szolgáltatásban. A Power BI szolgáltatásban az összetett modellek az ütemezett frissítések és az irányítópult csempéinek frissítései esetén ugyanúgy viselkednek, mint az importálási modellek. 

A táblák között ugyanúgy hozhat létre kapcsolatokat mint eddig, még akkor is, ha a táblák különböző forrásokból származnak, a következő megkötésekkel: a források közötti minden kapcsolatnak **több-a-többhöz** számosságúnak kell lennie, függetlenül a tényleges számosságuktól. Az ilyen kapcsolatok a **több-a-többhöz** kapcsolatok szokásos módján működnek. Ezt a [Több-a-többhöz kapcsolatok a Power BI Desktopban (előzetes verzió)](desktop-many-to-many-relationships.md) című cikk ismerteti. Lényeges, hogy az összetett modellek körében minden importált tábla egyetlen adatforrásként jelenik meg, függetlenül az alapjukat képező adatforrástól, ahonnan ténylegesen importálva lettek.   

## <a name="example-of-using-composite-models"></a>Példa összetett modellek használatára

Az **összetett modelleket** bemutató példaként tekintsünk egy jelentést, amely egy vállalati adattárházhoz (SQL Serverhez) csatlakozott DirectQuery használatával, az adattárház pedig az alábbi ábrán bemutatott módon a következő adatokat tartalmazza: *Sales by Country* (értékesítés országonként), *Quarter* (negyedév), és *Bike (Product)* (Kerékpár (Termék)).

![összetett modell kapcsolatok nézete](media/desktop-composite-models/composite-models_04.png)

Ebben a helyzetben egyszerű vizualizációkat készíthet a forrás mezőinek felhasználásával. A következő vizualizáció például a megadott negyedévben értékesített teljes mennyiséget mutatja be terméknevenként (*ProductName*). 

![adatokon alapuló vizualizáció](media/desktop-composite-models/composite-models_05.png)

De mi volna, ha további információkkal rendelkezne az egyes termékekhez rendelt termékmenedzserekről és a marketing-prioritásokról, ezek pedig egy Excel-munkafüzetben lennének kezelve? Érdemes volna termékmenedzserenként (*Product Manager*) látni az értékesített mennyiséget (*Sales Amount*), a helyszíni adatokat hozzáadatni a vállalati adattárházhoz viszont bizonyára kivitelezhetetlen, vagy legalábbis hónapokig tartana. Lehetséges ugyan importálni az értékesítési adatokat az adattárházból (a DirectQuery használata helyett), így egyesíthetők lesznek a munkafüzetből importált adatokkal, ez a megoldás azonban éppen a DirectQuery használatát indokló okok miatt ésszerűtlen – ilyen ok az alapul szolgáló forrásnál érvényben lévő biztonsági szabályok valamilyen kombinációja, a legfrissebb adatok megjelenésének igénye és az adatok puszta tömege. 

Ilyen helyzetben hasznosak az **összetett modellek**. Az összetett modellek lehetőséget kínálnak arra, hogy a DirectQuery használatával kapcsolódjon az adattárházhoz, ugyanakkor a GetData használatával további adatforrásokhoz is. Ebben az esetben DirectQuery-kapcsolatot hozunk létre a vállalati adattárházzal, majd a GetDatát használjuk és az Excelt választjuk, megnyitjuk a helyszíni adatokat tartalmazó munkafüzetet, és importálni tudjuk a termékneveket (*ProductNames*), a hozzájuk rendelt termékmenedzsereket (*SalesManager*) és a prioritást (*Priority*) tartalmazó munkalapot.  

![Navigátor ablak](media/desktop-composite-models/composite-models_06.png)

A **Mezők** listában most megjelenik az eredeti *Bike* tábla (az SQL Serverről), és a *ProductManagers* tábla (az Excelből importált adatokkal). 

![Mezők nézetben megjelenő táblák](media/desktop-composite-models/composite-models_07.png)

Ehhez hasonló módon a **Power BI Desktopban** **kapcsolatok nézetben** egy újabb, *Product Managers* nevű tábla is látható. 

![táblák kapcsolatok nézetben](media/desktop-composite-models/composite-models_08.png)

Most ezt kell kapcsolatba hoznunk a modell többi táblájával a szokásos módon, egy kapcsolatot létrehozva a *Bike* tábla (az SQL Serveren) és a *ProductManagers* tábla (amelyet importáltunk) között, például a *Bike[ProductName]* és a *ProductManagers[ProductName]* mezők között. Mint a cikk korábbi részében leírtuk, minden különböző források közötti kapcsolatnak **több-a-többhöz** számosságúnak kell lennie, ezért alapértelmezés szerint ez a számosság van kijelölve. 

![kapcsolat létrehozása párbeszédpanel](media/desktop-composite-models/composite-models_09.png)

A kapcsolat annak létrehozása után megjelenik a **Power BI Desktop** **kapcsolatok nézetében**, ahogyan várható volt.

![új kapcsolatok nézet](media/desktop-composite-models/composite-models_10.png)

A táblák közötti kapcsolatok létrehozása után már a **Mezők** listában szereplő mezők bármelyikének felhasználásával létre lehet hozni vizualizációkat, amelyek problémamentesen egyesítik a több forrásból származó adatokat. Az alábbi vizualizáció például az egyes termékmenedzserekhez (*Product Manager*) tartozó teljes értékesített mennyiséget (*Sales Amount*) ábrázolja. 

![vizualizáció a Mezők panellel](media/desktop-composite-models/composite-models_11.png)

Ez a példa azt a gyakori esetet szemlélteti, amikor egy *dimenziótáblát* (amilyen a *Product* vagy a *Customer*) máshonnan importált adatokkal bővítenek ki. Így a táblák a DirectQuery használatával is kapcsolódhatnak különböző forrásokhoz. A példát továbbgondolva tegyük fel, hogy az értékesítési célok (*SalesTargets*) országonként (*Country*) és időszakonként (*Period*) egy részleg egy külön adatbázisában vannak tárolva. Ezekhez az adatokhoz a szokásos módon kapcsolódhat a **GetData** használatával, amint az alábbi ábrán látható. 

![Kezelő párbeszédpanel](media/desktop-composite-models/composite-models_12.png)

A példa korábbi részéhez hasonlóan itt is létrehozhatunk a tábla és a modell többi táblája közötti kapcsolatokat, és az azok adatait egyesítő vizualizációkat. Lássuk újra a **kapcsolatok nézetet**, ahol a példa folytatásában már létrehoztunk új kapcsolatokat.

![kapcsolatok nézet sok táblával](media/desktop-composite-models/composite-models_13.png)

A következő, az új adatokon és a most létrehozott kapcsolatokon alapuló ábrán látható, hogy a bal alsó sarokban lévő vizualizáció a értékesített mennyiséget (*Sales Amount*) az értékesítési cél (*Target*) és a kiszámított eltérés mellett mutatja be, ahol a *Sales Amount* és a *Target* értékei két különböző SQL Server-adatbázisból származnak. 

![több adatot bemutató vizualizáció](media/desktop-composite-models/composite-models_14.png)

## <a name="setting-storage-mode"></a>A tárolási mód beállítása

Az **összetett modellekben** minden táblának saját **tárolási módja** van, amely azt jelzi, hogy a tábla DirectQuery-alapú vagy importált. A **Tárolási mód** a **Tulajdonságok** panelen tekinthető meg és módosítható. Ennek eléréséhez válassza a **Mezők** lista jobb-kattintással elérhető helyi menüjének **Tulajdonságok** elemét. A következő képen a **Tárolási mód** (Storage mode) látható (a panel szélessége miatt röviden, **Storage ...** formában).

![Tárolási mód beállítás](media/desktop-composite-models/composite-models_15.png)

A **tárolási mód** az egyes táblák elemleírásán is megjelenik.

![elemleírás a tárolási móddal](media/desktop-composite-models/composite-models_16.png)

A DirectQueryből származó és importált táblákat is tartalmazó **Power BI Desktop**-fájlok (.pbix fájlok) esetén az állapotsor **Kettős** **tárolási módot** jelez. Erre a szóra kattintva az állapotsorban minden tábla egyszerűen átállítható importálandóra.

A **tárolási mód** teljes körű ismertetését a [Tárolási mód a Power BI Desktopban (előzetes verzió)](desktop-storage-mode.md) című cikk tartalmazza.  

## <a name="calculated-tables"></a>Számított táblák

A Directqueryt használó modellekhez számított táblák adhatók, a számított táblát meghatározó DAX pedig hivatkozhat importált vagy DirectQuery-táblákra, vagy akár mindkettőre. 

A számított táblák mindig importálva vannak, és az adataik a tábla frissítésekor frissülnek. Ennek következtében, ha egy számított tábla egy DirectQuery-táblára hivatkozik, akkor a DirectQuery-táblára hivatkozó vizualizációkon mindig az alapul szolgáló forrás legfrissebb adatai látszanak, a számított táblára hivatkozó vizualizációk viszont mindig a számított tábla legutóbbi frissítésekor érvényes adatokat mutatják.

## <a name="security-implications"></a>Biztonsági vonatkozások 

Az összetett modelleknek van néhány biztonsági vonatkozása. Egy adott adatforrásra irányuló lekérdezés olyan értékeket is magában foglalhat, amelyek egy másik forrásból lettek beolvasva. A cikk korábbi részében ismertetett példában az értékesített mennyiséget (*Sales Amount*) termékmenedzserenként (*Product Manager*) bemutató vizualizáció miatt egy SQL-lekérdezés lesz elküldve a **Sales** relációs adatbázisnak, ez a lekérdezés pedig a termékmenedzserek (*Product Managers*) és a hozzájuk tartozó termékek (*Products*) nevét is tartalmazhatja. 

![a biztonsági vonatkozásokat szemléltető szkript](media/desktop-composite-models/composite-models_17.png)

Emiatt a munkafüzetben tárolt információ egy olyan lekérdezés része lesz, amely a relációs adatbázisnak lesz elküldve. Ha ez az információ bizalmas, akkor figyelembe kell venni ennek biztonsági vonatkozásait. Különösen érdemes megfontolni az alábbi következményeket:

* Az adatbázis nyomkövetéseket vagy auditnaplókat megtekinteni jogosult rendszergazdák akkor is láthatják ezt az információt, ha nincs engedélyük az eredeti forráshoz (ebben az esetben az Excel-fájlhoz).

* Figyelembe kell venni mindegyik forrás titkosítási beállításait, elkerülendő, hogy az egyik forrásból titkosított kapcsolaton keresztül beolvasott információ akaratlanul egy olyan lekérdezésbe kerüljön, amely titkosítatlan kapcsolaton át lesz elküldve egy másik forrásnak. 

A **Power BI Desktop** figyelmeztetést jelenít meg az összetett modellek létrehozásának műveletéhez, ahol megerősítheti, hogy minden biztonsági vonatkozást figyelembe vett.  

Hasonló okokból nagy körültekintéssel kell eljárni egy nem megbízható forrásból származó **Power BI Desktop**-fájl megnyitásakor. Ha ez a fájl összetett modelleket tartalmaz, akkor az egyik forrásból (a fájlt megnyitó felhasználó hitelesítő adataival) beolvasott információ egy másik forrásnak lesz elküldve a lekérdezés részeként (ahol esetleg a Power BI Desktop-fájl rosszindulatú készítője is láthatja). Ez az oka, hogy a több forrást tartalmazó Power BI Desktop-fájlok első megnyitásakor figyelmeztetés jelenik meg. Ez a figyelmeztetés ahhoz hasonló, amely natív SQL-lekérdezéseket tartalmazó fájlok megnyitásakor jelenik meg.  

## <a name="performance-implications"></a>A teljesítményt befolyásoló következmények  

A DirectQuery használata során mindig mérlegelni kell a teljesítményt, elsősorban abból a szempontból, hogy a háttérbeli forrás kellő erőforrásokkal rendelkezzen a jó felhasználói élmény biztosításához. A jó élmény azt jelenti, hogy a vizualizációk 5 másodperc alatt, vagy ennél gyorsabban frissülnek. Érdemes betartani a [DirectQuery használata a Power BI-ban](desktop-directquery-about.md) című cikk teljesítménnyel kapcsolatos ajánlásait is. Az összetett modellek használata a teljesítménnyel kapcsolatos további szempontokat von magával, hiszen egyetlen vizualizáció több forráshoz is küldhet lekérdezéseket, és gyakran adja tovább egy lekérdezés eredményeit egy második forrásnak. Ez a helyzet a következő végrehajtási módokhoz vezethet:

* **Nagy számú szöveges értéket tartalmazó SQL-lekérdezés** – Például egy olyan lekérdezésnek, amely a teljes értékesített mennyiséget (*Sales Amount*, az SQL-adatbázisból) kéri a termékmenedzserek (*Product Managers*) egy adott köréhez (a munkafüzetből importált, kapcsolódó táblából), ki kell keresnie az adott termékmenedzserekhez tartozó termékeket (*Products*), mielőtt elküldi az összes termékazonosítót egy *WHERE* záradékban tartalmazó SQL-lekérdezést.

* **Kisebb részletességet kívánó SQL-lekérdezés, amelynek adatai a helyszínen lesznek összesítve** – Ha az előző bekezdésben is használt példában a termékmenedzserek (*Product Manager*) alapján szűrt termékek (*Products*) száma nagyon nagyra nő, egy határon túl már ésszerűtlen vagy kivitelezhetetlen lesz mindegyiket belefoglalni egy *WHERE* záradékba. Ehelyett a termék (*Product*) alacsonyabb szintjén kell lekérdezni a relációs forrást, majd az eredményeket helyben összesíteni. Ha a termékek (*Products*) száma meghaladja az 1 milliót, a lekérdezés sikertelen lesz.

* **Több, érték szerinti csoportonként egy SQL-lekérdezés** – Ha az összegzés a **DistinctCount** függvényt használja egy másik forrásban lévő oszlop alapján csoportosítva, a külső forrás pedig nem támogatja a csoportosítást meghatározó nagy számú szöveges érték hatékony átadását, akkor szükségessé válhat érték szerinti csoportonként egy külön SQL-lekérdezést küldeni. Például egy olyan vizualizációnak, amely a *CustomerAccountNumber* mező eltérő értékeinek darabszámát kéri (az SQL Serveren lévő táblából) termékmenedzserenként (*Product Manager*, a munkafüzetből importált, kapcsolódó táblából), tovább kellene adnia a *Product Managers* tábla részleteit az SQL Servernek küldött lekérdezésben. Más, például Redshift-forrásokon ez nem kivitelezhető. Ehelyett *Sales Manager* értékenként egy SQL-lekérdezés lenne elküldve (egy adott gyakorlati korlátig, amely felett a lekérdezés sikertelen lesz). 

Ezen esetek mindegyike befolyásolja a teljesítményt. A pontos részletek adatforrásonként változnak. Hasznos alapelv, hogy amíg a két forrást összekötő kapcsolatban használt oszlopok számossága alacsony (néhány ezer), addig a teljesítmény nem változik jelentősen. A számosság növekedésével egyre több figyelmet kell fordítani a végső teljesítményre gyakorolt hatásra. 

A **több-a-többhöz** kapcsolatok használata ráadásul azzal jár, hogy minden összeg/részösszeg szintjén külön lekérdezést kell küldeni az alapul szolgáló forráshoz, a részletes értékek helyi összegzése helyett. Egy egyszerű táblára épülő vizualizáció ezért nem egy, hanem két SQL-lekérdezést küld el. 

## <a name="limitations-and-considerations"></a>Korlátozások és szempontok

A **összetett modelleknek** erre a verziójára érvényes néhány korlátozás.

Az alábbi Live Connect- (többdimenziós) források nem használhatók **összetett modellekkel**:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Power BI-adathalmazok
* Azure Analysis Services

Ha ezekhez a többdimenziós forrásokhoz a DirectQuery használatával csatlakozik, nem tud ugyanakkor más DirectQuery-forráshoz is csatlakozni, és importált adatokkal kombinálni sem.

A DirectQuery használatára jelenleg vonatkozó korlátozások az **összetett modellek** használatára is érvényesek. Sok ilyen korlátozás jelenleg táblánként értendő, a tábla **tárolási módjától** függően. Egy importált tábla egy számított oszlopa például hivatkozhat más táblákra, egy DirectQuery-tábla számított oszlopai viszont továbbra is csak a táblán belüli oszlopokra hivatkozhatnak. Más korlátozások a modell egészére vonatkoznak, ha a modellen belül bármelyik tábla DirectQuery módban van. A **QuickInsights** és a **Q&A** funkciók például nem érhetők el a modellben, ha a táblák bármelyikének **tárolási módja** DirectQuery. 

## <a name="next-steps"></a>Következő lépések

Az alábbi cikkek bővebben ismertetik az összetett modelleket, és a DirectQuery részletes leírását is tartalmazzák.

* [Több-a-többhöz kapcsolatok a Power BI Desktopban (előzetes verzió)](desktop-many-to-many-relationships.md)
* [Tárolási mód a Power BI Desktopban (előzetes verzió)](desktop-storage-mode.md)

A DirectQuery-vel kapcsolatos cikkek:

* [DirectQuery használata a Power BI-ban](desktop-directquery-about.md)
* [A DirectQuery által támogatott adatforrások a Power BI-ban](desktop-directquery-data-sources.md)

