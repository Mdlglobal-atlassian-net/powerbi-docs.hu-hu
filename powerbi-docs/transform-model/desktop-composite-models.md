---
title: Összetett modellek használata a Power BI Desktopban
description: Több adatkapcsolattal és több-a-többhöz kapcsolatokkal rendelkező adatmodellek létrehozása a Power BI Desktopban
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 5d7e4be9e3b864e2ccfccf64ac0d4460d0821e0a
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83326587"
---
# <a name="use-composite-models-in-power-bi-desktop"></a>Összetett modellek használata a Power BI Desktopban

Ha korábban a Power BI Desktopban DirectQueryt használt egy jelentésben, akkor más, akár DirectQuery vagy importálási módú adatkapcsolatra sem volt lehetőség az adott jelentésben. Az összetett modellekkel ez a kötöttség megszűnik. Egy jelentés problémamentesen tartalmazhat több, DirectQuery vagy importálás típusú adatkapcsolatot bármilyen kívánt kombinációban.

Az összetett modellek használatának lehetősége a Power BI Desktopban három összefüggő funkcióból áll:

* **Összetett modellek**: Lehetővé teszik, hogy egy jelentés több adatkapcsolattal, köztük DirectQuery és importálás típusú kapcsolatokkal, vagy ezek bármilyen kombinációjával rendelkezzen. Ez a cikk részletesen tárgyalja az összetett modelleket.

* **Több a többhöz kapcsolatok**: Az összetett modellekkel a táblák között *több-a-többhöz kapcsolatok* hozhatók létre. Ez a megközelítés kiküszöböli, hogy egyedi értékeket kelljen használni a táblákban. Korábbi áthidaló megoldásokat is szükségtelenné tesz, például új táblák bevezetését a kapcsolatok létrehozásához. További információk: [Több-a-többhöz kapcsolatok a Power BI Desktopban](desktop-many-to-many-relationships.md).

* **Tárolási mód**: Mostantól megadható, hogy mely vizualizációk kérdeznek le háttér-adatforrásokat. Azok a vizualizációk, amelyekhez nincs szükség lekérdezésre, importálva lesznek még akkor is, ha DirectQuery-alapúak. Ez a funkció segíti a teljesítmény javulását, és csökkenti a háttérrendszerek leterheltségét. Korábban még az egyszerű vizualizációk, például a szeletelők is kezdeményeztek a háttérbeli forrásokra irányuló lekérdezéseket. További információk: [A tárolási mód kezelése a Power BI Desktopban](desktop-storage-mode.md).

## <a name="use-composite-models"></a>Az összetett modellek használata

Összetett modellek használatával számos különböző típusú adatforráshoz csatlakozhat a Power BI Desktop vagy a Power BI szolgáltatás használatával. Ezeket az adatkapcsolatokat többféleképpen is létrehozhatja:

* Az adatok a Power BI-ba importálásával, ami az adatok lekérésének leggyakoribb módja.
* Közvetlen csatlakozással az adatokhoz az eredeti forrásadattárban a DirectQuery használatával. Ha szeretne többet megtudni a DirectQueryről, tekintse meg [A DirectQuery használata a Power BI-ban](../connect-data/desktop-directquery-about.md) című részt.

DirectQuery használata esetén összetett modellekkel létrehozható egy olyan Power BI-modell (például egy különálló *.pbix* Power BI Desktop-fájl), amely elvégzi a következő műveleteket vagy azok valamelyikét:

* Egy vagy több DirectQuery-forrásból származó adatokat egyesít.
* A DirectQuery-forrásokból származó és az importált adatokat egyesíti.

Összetett modellekkel például olyan modellt is összeállíthat, amely a következő adattípusokat egyesíti:

* Vállalati adattárházból származó értékesítési adatok.
* Értékesítési célokra vonatkozó adatok egy részlegszintű SQL Server-adatbázisból.
* Táblázatból importált adatok.

A több DirectQuery-forrás adatait egyesítő vagy DirectQuery- és importált adatokat egyesítő modelleket összetett modellnek nevezzük.

A táblák között létrehozhat kapcsolatokat, mint eddig is, még akkor is, ha ezek a táblák különböző forrásokból származnak. Minden olyan kapcsolat, amely több forrásból származik, több-a-többhöz számossággal jön létre, a tényleges számosságtól függetlenül. Ezeket egy-a-sokhoz, sok-az-egyhez vagy egy-az-egyhez értékre módosíthatja. A források közötti kapcsolatok működése a beállított számosságtól függően eltérő. DAX- (Data Analysis Expressions-) függvényekkel nem kérhetők le a `one` (egy) oldalon lévő értékek a `many` (több) oldalról. A teljesítményre gyakorolt hatás is megjelenhet a több-a-többhöz kapcsolathoz viszonyítva ugyanazon a forráson belül.

> [!NOTE]
> Az összetett modellek körében minden importált tábla egyetlen adatforrásként jelenik meg, függetlenül az alapjukat képező adatforrásoktól.

## <a name="example-of-a-composite-model"></a>Példa összetett modellre

Az összetett modelleket bemutató példaként tekintsünk meg egy olyan jelentést, amely egy SQL Serveren található vállalati adattárházhoz csatlakozott DirectQuery használatával. Ebben az esetben az adattárház a következő adatokat tartalmazza: értékesítési adatok **Country** (Ország), **Quarter** (Negyedév) és **Bike (Product)** (Kerékpár (Termék)) szerint, ahogyan az a következő képen látható:

![Összetett modellek Kapcsolat nézete](media/desktop-composite-models/composite-models_04.png)

Ebben a helyzetben egyszerű vizualizációkat készíthet a forrás mezőinek felhasználásával. Az alábbi kép a kiválasztott negyedév összes értékesítését mutatja be terméknév (*ProductName*) szerint.

![Adatokon alapuló vizualizáció](media/desktop-composite-models/composite-models_05.png)

De mi lenne, ha egy Office Excel-táblázatban további adatok szerepelnének az egyes termékekhez rendelt termékmenedzserekről és a marketingprioritásokról? Ha termékmenedzserenként (**Product Manager**) szeretné megtekinteni az értékesített mennyiséget (**Sales Amount**), nem biztos, hogy lehetséges ezeket a helyi adatokat hozzáadni a vállalati adattárházhoz. De legjobb esetben is hónapokig eltarthat.

Előfordulhat, hogy az értékesítési adatok az adattárházból is importálhatók, és nem szükséges a DirectQuery használata. Ebben az esetben az értékesítési adatok egyesíthetőek a táblázatból importált adatokkal. Ez a megközelítés azonban ésszerűtlen, ugyanazon okok miatt, amelyek eredetileg a DirectQuery használatához vezetnek. Ezek az okok többek között a következők:

* Az alapul szolgáló adatforrásban kikényszerített biztonsági szabályok bizonyos kombinációja.
* Szükség van a legújabb adatok megtekintésére.
* Az adatok mennyisége.

Ilyen helyzetben hasznosak az összetett modellek. Az összetett modellek lehetővé teszik, hogy a DirectQueryvel csatlakozzon az adattárházhoz, az **Adatok lekérése** használatával pedig további adatforrásokhoz. Ebben a példában először létrehozzuk a DirectQuery és a vállalati adattárház közötti kapcsolatot. Az **Adatok lekérése** használatával kiválasztjuk az **Excel** lehetőséget, majd megkeressük azt a táblázatot, amely a helyi adatainkat tartalmazza. Végül importáljuk az a táblázatot, amely a *termékneveket*, a hozzájuk rendelt **értékesítési menedzsereket** és a **prioritást** tartalmazza.  

![Navigátor ablak](media/desktop-composite-models/composite-models_06.png)

A **Mezők** listában két táblázat látható: az eredeti **Bike** táblázat az SQL Serverről és az új **ProductManagers** táblázat. Az új táblázat az Excelből importált adatokat tartalmazza.

![Mezők nézetben megjelenő táblák](media/desktop-composite-models/composite-models_07.png)

Hasonlóan a Power BI Desktop **Kapcsolatok** nézetében egy újabb, **ProductManagers** nevű táblázat is látható.

![Táblázatok kapcsolat nézetben](media/desktop-composite-models/composite-models_08.png)

Most ezen táblázatok és a modell többi táblázata között kell kapcsolatot létesítenünk. Ahogy szoktuk, létrehozunk egy kapcsolatot az SQL Server **Bike** táblázata és az importált **ProductManagers** táblázat között. Tehát a kapcsolat a **Bike[ProductName]** és a **ProductManagers[ProductName]** között jön létre. A fentebbiekben leírtaknak megfelelően a források közötti összes kapcsolat alapértelmezetten több-a-többhöz számosságú.

![A „Kapcsolat létrehozása” ablak](media/desktop-composite-models/composite-models_09.png)

A kapcsolat a létrehozását követően megjelenik a Power BI Desktop **Kapcsolat** nézetében, ahogyan várható volt.

![Az új Kapcsolat nézet](media/desktop-composite-models/composite-models_10.png)

A **Mezők** listában szereplő mezők bármelyikének felhasználásával létrehozhatunk vizualizációkat. Ez a megközelítés problémamentesen ötvözi a több forrásból származó adatokat. Például a teljes értékesítési összeg (*SalesAmount*) termékmenedzserenként (*Product Manager*) látható a következő képen:

![A Mezők panel](media/desktop-composite-models/composite-models_11.png)

A következő példa azt a gyakori esetet szemlélteti, amikor egy *dimenziótáblát*, amilyen a **Product** (Termék) vagy a **Customer** (Ügyfél), más helyről importált adatokkal bővítenek ki. A táblázatok a DirectQuery használatával is csatlakozhatnak különböző forrásokhoz. A példát továbbgondolva tegyük fel, hogy az értékesítési célok (**Sales Targets**) országonként (**Country**) és időszakonként (**Period**) egy részleg egy külön adatbázisában vannak tárolva. Ezekhez az adatokhoz a szokásos módon csatlakozhat az **Adatok lekérése** használatával, az alábbi képen látható módon:

![A Kezelő ablaka](media/desktop-composite-models/composite-models_12.png)

A korábbiakhoz hasonlóan most is létrehozhatunk az új táblázat és a modell többi táblázata között kapcsolatokat, és aztán létrehozhatunk a táblázatok adatait egyesítő vizualizációkat. Tekintsük meg újra a **Kapcsolat** nézetet, ahol létrehoztuk az új kapcsolatokat:

![A Kapcsolat nézet sok táblázattal](media/desktop-composite-models/composite-models_13.png)

A következő kép az új adatok és a létrehozott kapcsolatok alapján készült. A bal alsó sarokban lévő vizualizáció a teljes értékesített mennyiséget (*Sales Amount*) mutatja a célhoz képest (*Target*), és a kiszámított eltérés mutatja meg a két érték közötti különbséget. Az értékesített mennyiséggel (**Sales Amount**) és a céllal (**Target**) kapcsolatos adatok két különböző SQL Server-adatbázisból származnak.

![Több adatot mutató kép](media/desktop-composite-models/composite-models_14.png)

## <a name="set-the-storage-mode"></a>A tárolási mód beállítása

Az összetett modellekben minden táblázatnak saját tárolási módja van, amely azt jelzi, hogy a táblázat DirectQuery-alapú vagy importált. A tárolási mód a **Tulajdonságok** panelen tekinthető meg és módosítható. A tárolási mód megjelenítéséhez a **Mezők** listában kattintson a jobb gombbal egy táblázatra, majd válassza a **Tulajdonságok** lehetőséget. A következő képen a **SalesTargets** táblázat tárolási módja látható.

A tárolási mód az egyes táblázatok elemleírásán is megtekinthető.

![A tárolási módot megjelenítő eszköztipp](media/desktop-composite-models/composite-models_16.png)

A DirectQueryből származó és importált táblázatokat is tartalmazó Power BI Desktop-fájlok ( *.pbix* fájlok) esetén az állapotsor úgynevezett **Vegyes** tárolási módot jelenít meg. Az állapotsorban erre a kifejezésre kattintva minden táblázat egyszerűen átállítható importálás értékűre.

A tárolási móddal kapcsolatos további információért lásd: [A tárolási mód kezelése a Power BI Desktopban](desktop-storage-mode.md).  

> [!NOTE]
> A *Vegyes* tárolási módot a Power BI Desktopban és a Power BI szolgáltatásban használhatja.

## <a name="calculated-tables"></a>Számított táblák

Számított táblázatokat adhat a DirectQueryt használó modellekhez. A számított táblázatokat meghatározó Data Analysis Expressions (DAX) kifejezések importált vagy DirectQuery-táblázatokra, vagy a kettő kombinációjára is hivatkozhatnak.

A számított táblázatok mindig importáltak, és az adataik a táblázat frissítésekor frissülnek. Ha egy számított táblázat egy DirectQuery-táblázatra hivatkozik, akkor a DirectQuery-táblázatra hivatkozó vizualizációkon mindig az alapul szolgáló adatforrás legfrissebb értékei jelennek meg. Más esetekben a számított táblázatra hivatkozó vizualizációk a számított táblázat legutóbbi frissítésekor érvényes értékeket mutatják.

## <a name="security-implications"></a>Biztonsági vonatkozások

Az összetett modelleknek van néhány biztonsági vonatkozása. Egy adott adatforrásnak küldött lekérdezés olyan adatértékeket is magában foglalhat, amelyek egy másik forrásból lettek beolvasva. A korábbi példában az értékesített mennyiséget (**Sales Amount**) termékmenedzserenként (**Product Manager**) bemutató vizualizáció küld egy SQL-lekérdezést a Sales (Értékesítés) relációs adatbázisnak. Ez az SQL-lekérdezés a termékmenedzserek (Product Managers) és a hozzájuk tartozó termékek (Products) nevét is tartalmazhatja.

![A biztonsági vonatkozásokat szemléltető szkript](media/desktop-composite-models/composite-models_17.png)

Emiatt a táblázatban tárolt információ egy olyan lekérdezés része, amely a relációs adatbázisnak lesz elküldve. Ha ez az információ bizalmas, figyelembe kell venni ennek biztonsági vonatkozásait. Különösen a következőkre ügyeljen:

* A nyomkövetések vagy auditnaplók megtekintésére jogosult adatbázisgazdák akkor is láthatják ezeket az információkat, ha nincs engedélyük az eredeti forráshoz. Ebben a példában a rendszergazdának engedélyre lenne szüksége az Excel-fájlhoz való hozzáféréshez.

* Figyelembe kell venni mindegyik forrás titkosítási beállításait. Fontos elkerülni, hogy az egyik forrásból titkosított kapcsolattal lekért információ akaratlanul egy olyan lekérdezésben szerepeljen, amely titkosítatlan kapcsolaton lesz elküldve egy másik forrásnak.

A Power BI Desktop figyelmeztetést jelenít meg összetett modellek létrehozásakor, ahol megerősítheti, hogy minden biztonsági vonatkozást figyelembe vett.  

Hasonló okokból nagy körültekintéssel kell eljárni nem megbízható forrásból származó Power BI Desktop-fájl megnyitásakor. Ha ez a fájl összetett modelleket tartalmaz, akkor az egyik forrásból a fájlt megnyitó felhasználó hitelesítő adataival lekért információk egy másik adatforrásnak lesznek elküldve a lekérdezés részeként. Ezeket az információkat a Power BI Desktop-fájl rosszindulatú készítője is láthatja. Amikor először megnyit egy több forrást is tartalmazó Power BI Desktop-fájlt, a Power BI Desktop egy figyelmeztetést jelenít meg. Ez a figyelmeztetés ahhoz hasonló, amely natív SQL-lekérdezéseket tartalmazó fájlok megnyitásakor jelenik meg.  

## <a name="performance-implications"></a>A teljesítmény szempontjai  

A DirectQuery használata során mindig figyelembe kell venni a teljesítményt, elsősorban annak érdekében, hogy a háttérbeli forrás elegendő erőforrással rendelkezzen a jó felhasználói élmény biztosításához. A jó felhasználói élmény azt jelenti, hogy a vizualizációk legfeljebb öt másodperc alatt frissülnek. További teljesítménnyel kapcsolatos tanácsokért lásd: [DirectQuery használata a Power BI-ban](../connect-data/desktop-directquery-about.md).

Az összetett modellek használata további teljesítménnyel kapcsolatos szempontokat von maga után. Egyetlen vizualizáció több forráshoz is küldhet lekérdezéseket, és gyakran adja át a lekérdezés eredményeit egy második forrásnak. Ez a következő végrehajtási módokhoz vezethet:

* **Nagy számú literál értéket tartalmazó SQL-lekérdezés**: Például egy olyan vizualizáció, amely a teljes értékesített mennyiséget (**Sales Amount**) kéri a termékmenedzserek (**Product Managers**) egy adott köréhez, először ki kell keresnie az adott termékmenedzserekhez tartozó termékeket (**Products**). Ennek a folyamatnak végbe kell mennie, mielőtt a vizualizáció elküldi azt az SQL-lekérdezést, amely az összes termékazonosítót tartalmazza egy `WHERE` záradékban.

* **Kisebb részletességet kívánó SQL-lekérdezés, amelynek adatai később a helyszínen lesznek aggregálva**: Ha a termékmenedzserek (**Product Manager**) szűrési feltételének megfelelő termékek (**Products**) száma nagyon nagy, lehet, hogy nem érdemes vagy nem lehetséges belefoglalni az összes terméket egy `WHERE` záradékba. Ehelyett a termék (**Product**) alacsonyabb szintjén is lekérdezheti a relációs forrást, majd az eredményeket helyben aggregálhatja. Ha a termékek (**Products**) száma meghaladja az 1 milliós korlátot, a lekérdezés sikertelen lesz.

* **Több SQL-lekérdezés, csoportosítási szempontonként egy**: Ha az aggregáció a **DistinctCount** függvényt használja, és egy másik forrásban lévő oszlop alapján van csoportosítva, és ha a külső forrás nem támogatja a csoportosítást meghatározó nagy számú literál érték hatékony átadását, szükségessé válhat csoportosítási szempontonként külön SQL-lekérdezést küldeni.

   Egy olyan vizualizációnak, amely a **CustomerAccountNumber** mező egyedi értékeinek számát kéri le az SQL Server-táblából termékmenedzserenként (**Product Manager**), a munkafüzetből importálva, meg kellene adnia a **Product Managers** táblázat adatait az SQL Servernek elküldött lekérdezésben. Más erőforrások, például a Redshift használatával ez a művelet nem végezhető el. Ehelyett **Sales Manager** értékenként egy SQL-lekérdezés lenne elküldve egy adott gyakorlati korlátig, amely felett a lekérdezés sikertelen lenne.

Ezen esetek mindegyike befolyásolja a teljesítményt, és a pontos részletek adatforrásonként változnak. A két forrást összekötő kapcsolatban használt oszlopok számossága alacsony – néhány ezer –, azonban ennek a teljesítményt nem szabad befolyásolnia. A számosság növekedésével egyre több figyelmet kell fordítani a végső teljesítményre gyakorolt hatásra.

A több-a-többhöz kapcsolatok használata ráadásul azzal jár, hogy minden összeg vagy részösszeg szintjén külön lekérdezést kell küldeni az alapul szolgáló forráshoz a részletes értékek helyi aggregálása helyett. Ezért egy egyszerű táblázatvizualizáció összegekkel nem egy, hanem két SQL-lekérdezést küld el.

## <a name="limitations-and-considerations"></a>Korlátozások és szempontok

Az összetett modelleknek erre a kiadására néhány korlátozás érvényes:

Összetett modellek esetén jelenleg a [növekményes frissítést](../admin/service-premium-incremental-refresh.md) csak az SQL, az Oracle és a Teradata típusú adatforrások támogatják.

Az alábbi többdimenziós Live Connect-források nem használhatók összetett modellekkel:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Power BI-adathalmazok
* Azure Analysis Services

Ha ezekhez a többdimenziós forrásokhoz a DirectQuery használatával csatlakozik, nem tud más DirectQuery-forráshoz csatlakozni vagy ezeket importált adatokkal kombinálni.

A DirectQueryre vonatkozó jelenlegi korlátozások az összetett modellek használatára is érvényesek. Sok ilyen korlátozás jelenleg táblánként értendő, a tábla tárolási módjától függően. Egy importált táblázat egy számított oszlopa például hivatkozhat más táblázatokra, egy DirectQuery-táblázat számított oszlopai viszont továbbra is csak a táblázaton belüli oszlopokra hivatkozhatnak. Más korlátozások a modell egészére vonatkoznak, ha a modellen belül bármelyik tábla DirectQuery módban van. A QuickInsights- és a Q&A-funkciók például nem érhetők el a modellben, ha a táblázatok bármelyikének tárolási módja DirectQuery.

## <a name="next-steps"></a>Következő lépések

Az összetett modellekkel és a DirectQueryvel kapcsolatos további információkért tekintse meg a következő cikkeket:

* [Több a többhöz kapcsolatok a Power BI Desktopban](desktop-many-to-many-relationships.md)
* [Tárolási mód a Power BI Desktopban](desktop-storage-mode.md)
* [A DirectQuery használata a Power BI-ban](../connect-data/desktop-directquery-about.md)
* [A DirectQuery által támogatott adatforrások a Power BI-ban](../connect-data/power-bi-data-sources.md)
