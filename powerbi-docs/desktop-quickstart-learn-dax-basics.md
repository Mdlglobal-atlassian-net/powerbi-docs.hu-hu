---
title: A DAX alapszintű használata a Power BI Desktopban
description: A DAX alapszintű használata a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 433710918cb77ca9ee002673dbe6298f0d2184aa
ms.sourcegitcommit: 42475ac398358d2725f98228247b78aedb8cbc4f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003294"
---
# <a name="dax-basics-in-power-bi-desktop"></a>A DAX alapszintű használata a Power BI Desktopban
Ez a cikk a Power BI Desktoppal még csak most ismerkedő felhasználóknak szól. A célja annak a rövid bemutatása, hogyan lehet a Data Analysis Expressions (DAX) nyelv segítségével néhány alapszintű számítási és adatelemzési problémát megoldani. Ismerteti az alapvető fogalmakat, továbbá tartalmaz néhány elvégezhető feladatot és néhány tesztkérdést az elsajátított ismeretek felmérésére, így segít a DAX nyelvvel kapcsolatos legfontosabb alapvető tudnivalók elsajátításában.

## <a name="what-is-dax"></a>Mi az a DAX?
A DAX függvények, operátorok és konstansok gyűjteménye, amelyeket képletekbe vagy más néven kifejezésekbe rendezve a rendszer különféle értékeket számít ki és ad vissza. Egyszerűbben fogalmazva, a DAX segítségével a modellben található adatok alapján új információk hozhatók létre.

## <a name="why-is-dax-so-important"></a>Mi a DAX jelentősége?
Nem nehéz létrehozni olyan új Power BI Desktop-fájlokat, amelyekbe adatokat lehet importálni. Még az adatok értékes összefüggéseit kiemelő jelentések is létrehozhatók DAX-képletek nélkül. Mi a helyzet azonban akkor, ha különböző termékkategóriák növekedési arányait kell elemezni különböző időszakokra vetítve, vagy a piaci trendekhez viszonyított éves növekedési rátákat kell kiszámítani? Az ilyen feladatok elvégzését és sok egyéb hasznos funkció használatát a DAX-képletek teszik lehetővé. Ha tisztában van vele, hogyan hozhat létre hatékony DAX-képleteket, a legtöbbet hozhatja ki adataiból. Miután kinyerte adataiból a szükséges információkat, nekiláthat megoldani a tényleges üzleti problémákat, amelyek kihatással vannak a vállalkozás eredményességére. Itt mutatkozik meg a Power BI igazi ereje, amely igazán a DAX segítségével aknázható ki.

## <a name="prerequisites"></a>Előfeltételek
Előfordulhat, hogy már rendelkezik gyakorlattal a Microsoft Excel-képletek létrehozásában. Az ilyen ismeretek hasznosak a DAX megértéséhez, de még ha nem is ismeri az Excel-képleteket, az itt ismertetett alapfogalmak mentén rögtön nekiláthat saját DAX-képletekkel valós BI-problémákat megoldani.

Szeretnénk a számításokban, különösen a mértékekben és a számított oszlopokban használt DAX-képletek bemutatására helyezni a hangsúlyt. Ehhez elengedhetetlen, hogy már ismerje a Power BI Desktopot, az adatok importálásának módját, azt, hogyan adhat hozzá mezőket egy jelentéshez, valamint a [Mértékek](desktop-measures.md) és a [Számított oszlopok](desktop-calculated-columns.md) alapvető fogalmait.

**Például szolgáló munkafüzet**

A legjobban úgy sajátíthatja el a DAX használatát, ha létrehoz néhány alapvető képletet, azokat tényleges adatokkal használja, és megvizsgálja a kapott eredményeket. Az itt található példák és feladatok Power BI Desktop előzetes verziójához készült Contoso értékesítési mintára épülnek. Ez ugyanaz a mintafájl, amelyet a [saját mértékek Power BI Desktopban való létrehozását ismertető oktatóanyag](desktop-tutorial-create-measures.md) is használ. A mintafájlt [innen töltheti le](http://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20for%20Power%20BI%20Designer.zip).

## <a name="lets-begin"></a>Lássunk is hozzá!
A DAX nyelvvel kapcsolatos ismeretek három alapvető fogalom köré fűzhetőek fel: *Szintaxis*, *Függvények* és *Környezet*. Természetesen léteznek egyéb fontos fogalmak is a DAX-ban, de ennek a három alapvető fogalomnak az elsajátítása a többi megismerését elősegítő kellő alapot.

### <a name="syntax"></a>Szintaxis
Mielőtt elkezdene saját képleteket létrehozni, tekintsük át a DAX-képletek szintaxisát. A szintaxis a képletet alkotó elemeket vagy egyszerűbben a képlet írásmódját foglalja magában. Vegyük például egy mérték egyszerű DAX-képletét.

![](media/desktop-quickstart-learn-dax-basics/qsdax_1_syntax.png)

A szintaxis képletet alkotó elemei a következők:

**A.** A mérték neve a **Total Sales** (Értékesítések teljes összege).

**B.** Az egyenlőségjel operátor (**=**) jelöli a képlet kezdetét. A kiszámításakor a képlet egy eredményt ad vissza.

**C.** A **SUM** DAX-függvény összegzi a **Sales[SalesAmount]** (Értékesítések[ÉrtékesítésekÖsszege]) oszlopban lévő összes számot. A függvényekre a későbbiekben térünk vissza.

**D.** Az egy vagy több argumentumot tartalmazó kifejezéseket zárójelek **()** zárják közre. Mindegyik függvényhez legalább egy argumentumot meg kell adni. Az argumentumokkal értékek adhatók a függvényekbe.

**E.** A hivatkozott tábla a **Sales** (Értékesítések) tábla.

**F.** A hivatkozott oszlop a Sales tábla **[SalesAmount]** (ÉrtékesítésekÖsszege) oszlopa. Ebből az argumentumból tudja a SUM függvény, hogy melyik oszlop értékeit kell összegezni.

A DAX-képletek megértéséhez érdemes lehet az egyes elemeket lebontani egy olyan nyelvre, amelyet a mindennapok során is használunk. Ez a képlet például a következőképp olvasható ki:

> *A Total Sales nevű mértékhez számítsuk ki (=) a Sales tábla [SalesAmount] oszlopában lévő értékek összegét (SUM).*
> 
> 

Ha ezt a mértéket egy jelentéshez adjuk, kiszámítja az összes többi szerepeltetett mező (például: Mobiltelefonok az Egyesült Államok területén) értékesítési értékeinek összegét.

Most talán azt gondolja, hogy „ez a mérték nem ugyanazt csinálja, mintha hozzáadnám a SalesAmount mezőt a jelentéshez?” Voltaképpen igen. Megvan azonban az oka, hogy miért hozunk létre egy külön saját mértéket, amely összegzi a SalesAmount mező értékeit: ezt a mértéket ugyanis használhatjuk argumentumként más képletekben. Lehet, hogy ez elsőre nem egyértelmű, ahogy azonban jobban megismeri a DAX-képleteket, ennek a segítségével sokkal hatékonyabb képleteket és modelleket hozhat majd létre. A későbbiekben viszont is fogja látni a Total Sales mértéket más képletek argumentumaként.

Lássunk még néhány dolgot ezzel a képlettel kapcsolatban. Kiemelendő, hogy a részeként egy függvényt is bemutattunk, a [SUM](https://msdn.microsoft.com/library/ee634387.aspx) függvényt. A függvények előre megírt képletek, amelyek használatával bonyolultabb számításokat és átalakításokat végezhet többek között számokkal, dátum- és időértékekkel, valamint szövegekkel. A függvényekre a későbbiekben térünk vissza.

Azt is láttuk, hogy a [SalesAmount] oszlop előtt szerepelt a Sales tábla is, amelyhez az oszlop tartozik. Amennyiben az oszlop neve előtt a tábla neve is szerepel, azt teljes oszlopnévnek nevezzük. A saját táblájukban hivatkozott oszlopoknál a tábla nevét nem kell megadni a képletben. Így a több oszlopra is hivatkozó hosszabb képletek lerövidíthetők, ami megkönnyíti az olvasásukat. A mértékképletek esetében azonban hasznos a tábla nevét is szerepeltetni, még ha a saját táblájukon belül hivatkozunk is rájuk.

> [!NOTE]
> Ha valamely tábla neve szóközt, fenntartott kulcsszavakat vagy tiltott karaktereket tartalmaz, aposztrófok közé kell foglalni. Ugyanígy idézőjelek közé kell foglalni azokat a táblaneveket, amelyek az ANSI alfanumerikus karakterskálán kívül eső karaktereket tartalmaznak, függetlenül attól, hogy a területi beállítások támogatják-e az adott karakterkészletet.
> 
> 

Fontos, hogy a képletekben a megfelelő szintaxist alkalmazza. Hibás szintaxis esetén a rendszer általában szintaxishibát jelez. Az is előfordulhat, hogy a szintaxis helyes ugyan, a visszaadott értékek mégsem felelnek meg az elvárásoknak. A Power BI Desktop DAX-szerkesztője tartalmaz egy javaslatokat nyújtó funkciót is, mely segít a megfelelő elemek kiválasztásával szintaktikailag helyes képleteket előállítani.

Hozzunk létre egy egyszerű képletet. Ez a feladat segít jobban megérteni a képletek szintaxisát és a képletsáv javaslatokat nyújtó funkciójának működését.

### <a name="task-create-a-measure-formula"></a>Feladat: Mértékképlet létrehozása
A feladat végrehajtásához nyissa meg a Contoso értékesítési minta Power BI Desktop-fájlt.
    
1. A Jelentés nézet mezőlistájában kattintson jobb gombbal a **Sales** táblára, majd kattintson az **Új mérték** gombra.
    
2. A szerkesztőlécben írja a **Mérték** helyőrző helyére az új mérték nevét: **Previous Quarter Sales** (Előző negyedévi értékesítések).
    
3. Az egyenlőségjel után írja be az első néhány betűt (**CAL**), majd kattintson duplán a használni kívánt függvényre. Ebben a képletben használja a **CALCULATE** függvényt.

   A CALCULATE függvénnyel a függvénynek átadott argumentum alapján szűrheti az összegezni kívánt összegeket. Ezt nevezzük a függvények beágyazásának. A CALCULATE függvény legalább két argumentumot vesz fel. Az első a kiértékelendő kifejezés, a második pedig egy szűrő.
   
4. A **CALCULATE** függvény nyitó zárójele **(** után írja be a **SUM** függvényt, majd nyisson még egy zárójelet **(**. Most adja meg a SUM függvény argumentumát.

5. Kezdje el begépelni a **Sal** kifejezést, majd válassza ki a **Sales[SalesAmount]** argumentumot, és zárja be a zárójelet **)**. Ez a CALCULATE függvény első kifejezésargumentuma.
    
6. Írjon be egy vesszőt (**,**), aztán egy szóközt az első szűrő megadásához, majd írja be a **PREVIOUSQUARTER** kifejezést. Ez lesz a szűrőnk.
    
   A PREVIOUSQUARTER időintelligencia-függvény segítségével szűrhetjük a SUM eredményeit az előző negyedévre.
    
7. A PREVIOUSQUARTER függvény nyitó zárójele **(** után írja be a **Calendar[DateKey]** argumentumot.
    
   A PREVIOUSQUARTER függvénynek egy argumentuma van, egy egybefüggő dátumtartományt tartalmazó oszlop. Ebben az esetben ez a Calendar (Naptár) táblázat DateKey oszlopa.
    
8. A PREVIOUSQUARTER függvénynek átadott mindkét argumentumot és a CALCULATE függvényt is mindenképpen két zárójellel **))** zárja le.
    
   A képletnek most így kell kinéznie:
    
   **Previous Quarter Sales = CALCULATE(SUM(Sales[SalesAmount]), PREVIOUSQUARTER(Calendar[DateKey]))**
    
9. A képlet érvényesítéséhez és a modellhez való hozzáadásához kattintson a pipa jelre ![](media/desktop-quickstart-learn-dax-basics/qsdax_syntax_taskcheckmark.png) a szerkesztőlécen vagy nyomja le az Enter billentyűt.

És kész is! Épp most hozott létre egy mértéket a DAX használatával, és nem is egy egyszerűt. Ez a képlet az előző negyedévi teljes értékesítést számítja ki a jelentésben alkalmazott szűrők alapján. Például ha felvesszük a SalesAmount mezőt és az új Previous Quarter Sales mértéket egy diagramra, majd hozzáadjuk a Year és a QuarterOfYear mezőt szeletelőként, valami ilyesmit kapunk:

![](media/desktop-quickstart-learn-dax-basics/qsdax_3_chart.png)

Most több fontos dolgot s megtanult a DAX-képletekkel kapcsolatban. Először is ez a képlet két függvényt tartalmazott. Láthatjuk, hogy a [PREVIOUSQUARTER](https://msdn.microsoft.com/library/ee634385.aspx) időintelligencia-függvény a [CALCULATE](https://msdn.microsoft.com/library/ee634825.aspx) szűrőfüggvénynek átadott argumentumként van beágyazva. A DAX-képletek legfeljebb 64 beágyazott függvényt tartalmazhatnak. Valószínűtlen, hogy bármelyik képlet valaha is tartalmazna ennyi beágyazott függvényt. Egy ilyen képlet egyébként is meglehetősen nehezen létrehozható és korrigálható, és valószínűleg nem is lenne valami gyors.

Ebben a képletben szűrőket is alkalmaztunk. A szűrők leszűkítik a kiszámítandó értékek halmazát. Esetünkben egy szűrőt választottunk argumentumként, amely egy másik függvény eredménye. A szűrőkre a későbbiekben térünk vissza.

Végül pedig a CALCULATE függvényt használtuk. Ez az egyik leghasznosabb DAX-függvény. A modellek készítése és a bonyolultabb képletek összeállítása során valószínűleg igen sokszor fogja majd alkalmazni ezt a függvényt. Jelen cikknek a CALCULATE függvény ismertetése nem képezi a részét, azonban a DAX-ismeretei növelése során érdemes külön figyelmet szentelnie ennek a függvénynek.

### <a name="syntax-quickquiz"></a>Szintaxis-gyorsteszt
1. Mire jó ez a gomb itt, a szerkesztőlécen?
   
   > ![](media/desktop-quickstart-learn-dax-basics/qsdax_2_syntaxquiz.png)
   > 
   > 
2. Mit kell mindig az oszlopok neve köré írni a DAX-képletekben?

A válaszokat a cikk végén találja.

### <a name="functions"></a>Függvények
A függvények előre definiált képletek, amelyek adott sorrendben vagy struktúrában megadott értékek, az úgynevezett argumentumok alapján végeznek számításokat. Az argumentumok lehetnek más függvények, egy másik képlet vagy kifejezés, oszlophivatkozások, számok, szövegek, logikai értékek (IGAZ vagy HAMIS) vagy konstansok.

A DAX a következő függvénykategóriákat tartalmazza: [Dátum és idő](https://msdn.microsoft.com/library/ee634786.aspx), [Időintelligencia](https://msdn.microsoft.com/library/ee634763.aspx), [Információs](https://msdn.microsoft.com/library/ee634552.aspx), [Logikai](https://msdn.microsoft.com/library/ee634365.aspx), [Matematikai](https://msdn.microsoft.com/library/ee634241.aspx), [Statisztikai](https://msdn.microsoft.com/library/ee634822.aspx), [Szöveg](https://msdn.microsoft.com/library/ee634938.aspx), [Szülő/gyermek](https://msdn.microsoft.com/library/mt150102.aspx) és [Egyéb](https://msdn.microsoft.com/library/mt150101.aspx) függvények. Ha már ismeri az Excel-képletekben használt függvényeket, a DAX-függvények nagy része ismerősnek fog hatni, azonban a DAX-függvények a következő szempontokból egyedinek tekinthetők:

* A DAX-függvény minden esetben egy oszlopra vagy táblára hivatkozik. Ha csak bizonyos értékeket szeretne egy táblából vagy oszlopból használni, kiegészítheti szűrőkkel a képletet.
* Ha a számításokat soronként testre szeretné szabni, a DAX-ben léteznek olyan függvények, amelyeknek az aktuális sor értékét vagy egy kapcsolódó értéket átadhat argumentumként, így környezetfüggő számításokat végezhet. A környezetekre a későbbiekben térünk vissza.
* A DAX számos függvénye nem értéket, hanem egy táblát ad vissza. A tábla nem jelenik meg, hanem értékeket ad át más függvényeknek. Például le lehet kérni egy táblát, és megszámolni benne az eltérő értékeket, vagy szűrt táblák és oszlopok dinamikus összegeit kiszámítani.
* A DAX különböző időintelligencia-függvényeket is tartalmaz. Ezekkel a függvényekkel megadhat vagy kiválaszthat dátumtartományokat, és azokon dinamikus számításokat hajthat végre. Például összehasonlíthat párhuzamos időszakokra vonatkozó összegeket.
* Az Excel egyik nagyon népszerű függvénye a HKERES. Ellentétben az Excel HKERES függvényével, a DAX-függvényeknek nem adható át hivatkozásként cella vagy cellatartomány. A DAX-függvényeknek oszlopok vagy táblák adhatók át hivatkozásként. Mindig tartsa szem előtt, hogy a Power BI Desktopban relációs adatmodellekkel dolgozik. Egy másik tábla valamelyik értékének megkeresése igazán egyszerű dolog, és sokszor még csak képlet sem kell hozzá.
  
  Amint látható, a DAX függvényeivel nagyon hatékony képletek hozhatóak létre. Eddig még csak alapszinten tekintettük át a képleteket. Ahogy egyre jobban elsajátítja a DAX használatát, számos különböző függvényt alkalmaz majd a képletekben. A DAX-függvényekkel kapcsolatos információkért leginkább a [DAX-függvények referencia-útmutatóját](https://msdn.microsoft.com/en-us/query-bi/dax/data-analysis-expressions-dax-reference) érdemes tanulmányoznia.

### <a name="functions-quickquiz"></a>Függvények-gyorsteszt
1. Mire hivatkoznak minden esetben a függvények?
2. Tartalmazhat egy képlet egynél több függvényt is?
3. Melyik kategória valamelyik függvényét alkalmazná két szöveges sztring egybefűzésére?

A válaszokat a cikk végén találja.

### <a name="context"></a>Környezet
A környezet a DAX egyik legfontosabb alapfogalma. A DAX-ben kétféle környezet létezik: a sorkörnyezet és a szűrőkörnyezet. Először a sorkörnyezettel foglalkozunk.

**Sorkörnyezet**

A sorkörnyezetet a legegyszerűbb úgy elképzelni, mint az adott sort. Akkor van jelentősége, ha egy képlet valamelyik függvénye olyan szűrőket alkalmaz, amelyek egy tábla egyetlen sorát azonosítják. A függvény automatikusan sorkörnyezetet alkalmaz a szűrt tábla minden egyes sorára. Az ilyen típusú sorkörnyezet leggyakrabban a mértékek esetén merül fel.

**Szűrőkörnyezet**

A szűrőkörnyezet már egy kicsit összetettebb, mint a sorkörnyezet. A legegyszerűbben így értelmezhető: egy adott számításban alkalmazott egy vagy több szűrő, amely egy eredményt vagy értéket határoz meg.

A szűrőkörnyezet nem a sorkörnyezetet váltja ki, hanem amellett alkalmazandó. Például az egy adott számításban foglalt értékek további szűkítéséhez alkalmazhat egy szűrőkörnyezetet, amely nem csupán a sorkörnyezetet határozza meg, hanem azon belül egy adott értéket (szűrő).

A szűrőkörnyezet könnyen megfigyelhető a jelentésekben. Például ha felveszi a TotalCost mezőt egy vizualizációra, majd hozzáadja Year és a Region mezőt, egy szűrőkörnyezetet határoz meg, amely az adatok egy részhalmazát adja meg egy adott év és régió alapján.

Miért olyan fontos a szűrőkörnyezet a DAX esetén? Bár a legkönnyebben a mezők a vizualizációkhoz adásával alkalmazhatóak, a szűrőkörnyezeteket a DAX-képletekben is használhatja, ha az ALL, RELATED, FILTER, CALCULATE függvények, kapcsolatok vagy más mértékek és oszlopok segítségével meghatároz egy szűrőt. Tekintsük például a következő képletet a Store Sales elnevezésű mértékben:

![](media/desktop-quickstart-learn-dax-basics/qsdax_4_context.png)

Hogy jobban megértsük, a képletet más képletekhez hasonlóan részekre bonthatjuk.

A szintaxis képletet alkotó elemei a következők:

**A.** A mérték neve a **Store Sales** (Áruházi értékesítés).

**B.** Az egyenlőségjel operátor (**=**) jelöli a képlet kezdetét.

**C.** A **CALCULATE** függvény a megadott szűrők által módosított környezetben értékel ki egy argumentumként megadott kifejezést.

**D.** Az egy vagy több argumentumot tartalmazó kifejezéseket zárójelek **()** zárják közre.

**E.** A **[Total Sales]** mérték ugyanabban a táblázatban kifejezésként. A Total Sales mérték képlete: =SUM(Sales[SalesAmount]).

**F.** Pontosvessző (**;**) választja el az első kifejezés argumentumát a szűrőargumentumtól.

**G.** A hivatkozott oszlop teljes neve: **Channel[ChannelName]**. Ez a sorkörnyezetünk. Ebben az oszlopban minden sor egy értékesítési csatornát ad meg: Store (Áruház), Online stb.

**H.** Az adott **Store** érték mint szűrő. Ez a szűrőkörnyezetünk.

Ez a képlet garantálja, hogy a rendszer csak a Total Sales mérték által megadott értékesítési mennyiségeket veszi számításba a Channel[ChannelName] oszlop a „Store” szűrő által meghatározott soraiban.

Ha belegondolunk, láthatjuk, hogy a szűrőkörnyezetek képletekben való megadásával milyen hatalmas és sokoldalú lehetőségek nyílnak meg előttünk. Az, hogy egy kapcsolódó tábla egy adott értékére hivatkozunk, csak egy ezek közül. Ne aggódjon, ha egyelőre még nem teljesen látja át a környezeteket. Ahogy majd elkezd saját képleteket létrehozni, jobban megérti a környezet fogalmát, és hogy miért olyan fontos a szerepe a DAX-ben.

### <a name="context-quickquiz"></a>Környezet-gyorsteszt
1. Milyen két típusa van a környezetnek?
2. Mi a szűrőkörnyezet?
3. Mi a sorkörnyezet?

A válaszokat a cikk végén találja.

## <a name="summary"></a>Összefoglalás
Most, hogy valamelyest megismerte a DAX legfontosabb alapfogalmait, elkezdhet kísérletezgetni mértékek DAX-képleteinek létrehozásával. A DAX elsajátítása talán nem a legegyszerűbb dolog, de rengeteg forrásanyag áll rendelkezésre. A cikk átolvasása után, és miután már kísérletezgetett saját képletek összeállításával is, a DAX más fogalmaival és képleteivel is megismerkedhet, amelyek segíthetnek megoldást találni üzleti problémáira. A számos elérhető DAX-forrásanyag közül a legfontosabb a [Data Analysis Expressions (DAX) referencia-útmutatója](https://msdn.microsoft.com/library/gg413422.aspx).

A DAX néhány éve már jelen van más microsoftos üzletiintelligencia-eszközben, például a Power Pivot és az Analysis Services táblázatos modelljeiben, így rengeteg további nagyszerű forrásanyag is elérhető. További információkat találhat még a mind a Microsoft, mind a vezető üzletiintelligencia-szakemberek tollából született könyvekben, tanulmányokban és blogokon. [A TechNeten a DAX-forrásanyagközpont wikije](http://social.technet.microsoft.com/wiki/contents/articles/dax-resource-center.aspx) szintén nagyszerű kiindulópontot jelenthet.

### <a name="quickquiz-answers"></a>A gyorstesztek válaszai
Szintaxis:

1. Ellenőrzi a mértéket, és átadja a modellnek.
2. Szögletes zárójeleket [].

Függvények:

1. Egy táblára és egy oszlopra.
2. Igen. Az egyes képletek akár 64 beágyazott függvényt is tartalmazhatnak.
3. A [szöveges függvények](https://msdn.microsoft.com/library/ee634938.aspx) kategóriájáét.

Környezet:

1. A sorkörnyezet és a szűrőkörnyezet.
2. Egy adott számításban alkalmazott egy vagy több szűrő, amely egy értéket határoz meg.
3. Az aktuális sor.

