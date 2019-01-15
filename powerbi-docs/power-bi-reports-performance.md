---
title: Ajánlott eljárások a Power BI teljesítményének javításához
description: A cikkből megtudhatja, hogyan hozhat létre gyors és megbízható jelentéseket a Power BI-ban.
author: MarkMcGeeAtAquent
ms.author: kfile
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/18/2018
LocalizationGroup: Reports
ms.openlocfilehash: f603a733c6c604a89b0b9608904acdf13b66b713
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54287784"
---
# <a name="power-bi-performance-best-practices"></a>Ajánlott eljárások a Power BI teljesítményének javításához

A cikk azt mutatja be, hogyan hozhat létre gyors és megbízható jelentéseket a Power BI-ban.  

## <a name="use-filters-to-limit-report-visuals-to-display-only-whats-needed"></a>Csak a szükséges adatok megjelenítése a jelentések vizualizációiban szűrők használatával 

Minél több adatot jelenítenek meg a vizualizációk, annál lassabban töltődnek be. Még ha ez nyilvánvalónak is tűnik, könnyű megfeledkezni róla. Tegyük fel például, hogy egy nagyméretű adathalmazon dolgozik, és létrehoz egy olyan, erre épülő jelentést, amely tartalmaz egy táblát. A végfelhasználók szeletelőkkel szűrnek a kívánt sorokra a lapon – jellemzően csak néhány tucatnyi sor érdekli őket.

Gyakori hiba ilyen esetben, hogy a tábla alapértelmezett nézete szűretlen – vagyis az összes sort tartalmazza, mely akár 100 milliónál is több lehet. Ezeknek a soroknak az adatait minden egyes frissítéskor be kell töltenie a rendszernek a memóriába, majd ki kell tömörítenie. Ez hatalmas memóriaterhelést eredményezhet. A megoldás az, hogy csökkenteni kell a táblában maximálisan megjeleníthető elemek számát a „Felső N” szűrővel. A maximális elemszám lehet a felhasználók által jellemzően igényelt sorszámnál jóval magasabb is, például 10 000. Ha így tesz, az a végfelhasználók használati élményét nem befolyásolja, de a jelentés memóriahasználatát több nagyságrenddel csökkenti, ami ennek megfelelően javítja a teljesítményt.

A fentihez hasonló megközelítés a jelentésekben található összes vizualizációhoz ajánlott. Mindig tegye fel a kérdést: Minden adatra szükség van ebből a vizualizációból? Le lehet szűkíteni a vizualizációban megjelenített adatmennyiséget úgy, hogy az csak minimálisan befolyásolja a végfelhasználói élményt? Fontos megjegyezni, hogy a táblák teljesítményigényesek lehetnek.

## <a name="limit-visuals-on-report-pages"></a>A jelentéslapokon megjelenő vizualizációk számának korlátozása

A fenti elv az egyes jelentésekben megjelenített vizualizációk számára is ugyanúgy igaz. Erősen javasolt, hogy a jelentésekben csak annyi vizualizációt jelenítsen meg, amennyi valóban szükséges. A részletező lapok nagyszerű megoldást nyújtanak arra, hogy további részleteket tudjon biztosítani anélkül, hogy még több vizualizációt kellene bezsúfolnia a jelentésbe.  

## <a name="optimize-your-model"></a>A modell optimalizálása

Néhány ajánlott eljárás:

- Távolítsa el a nem használt táblákat és oszlopokat, ha lehetséges. 
- Lehetőség szerint ne alkalmazzon darabszámmértéket nagy számosságú (például több milliónyi egyéni értéket tartalmazó) mezőkre.  
- Igyekezzen kerülni a szükségtelenül nagy pontosságú és nagy számosságú mezők használatát. Az egyedi dátum- és időértékeket például feloszthatja különálló oszlopokra – például hónap, év, dátum, stb. Vagy ahol lehetséges, kerekítheti a nagy pontosságú mezőket a számosság csökkentése érdekében (példa: 13,29889 -> 13,3).
- Ahol lehetséges, használjon egész számokat sztringek helyett.
- Legyen óvatos az olyan DAX-függvényekkel, amelyeknek tesztelnie kell a tábla összes sorát (mint például RANKX), mert az ilyen függvények a legrosszabb esetben akár exponenciálisan is növelhetik a futásidőt és a memóriahasználatot a táblaméret lineáris növekedésével párhuzamosan.
- Ha DirectQuery segítségével csatlakozik adatforrásokhoz, fontolja meg a gyakorta ismételten szűrt vagy szeletelt oszlopok indexelését – ez nagyban megnöveli a jelentés válaszképességét.  

Az adatforrások DirectQueryhez való optimalizálásáról bővebben a [DirectQuery az SQL Server 2016 Analysis Services szolgáltatásban](https://blogs.msdn.microsoft.com/analysisservices/2017/04/06/directquery-in-sql-server-2016-analysis-services-whitepaper/) című cikkben olvashat.

## <a name="directquery-and-live-connection-understand-underlying-data-source-performance"></a>DirectQuery és élő kapcsolat: az alapul szolgáló adatforrás teljesítményének ismertetése

Ha DirectQueryt vagy élő kapcsolatot használ, akkor amikor a felhasználók megnyitnak egy Power BI-jelentést, a Power BI valós időben küld lekérdezéseket az alapul szolgáló adatforrásnak. A jelentés csak azután jelenik meg, hogy az adatforrás visszaadta a kért adatokat. Emiatt a jelentés teljesítménye ilyen esetekben nagyban függ az alapul szolgáló adatforrás teljesítményétől.

Ezekben az esetekben fontos tisztában lennie azzal, hogy milyen teljesítményt nyújt az alapul szolgáló adatforrás. A különböző adatforrások esetében különböző eszközökkel tudja felmérni a teljesítményt. Az SQL Server és az Azure SQL esetében például használhatja a lekérdezéstárat, mely rögzíti a korábban végrehajtott lekérdezéseket és azok futásidejének statisztikai adatait.

Javasolt, hogy a DirectQueryt és élő kapcsolatokat használó Power BI-jelentések üzembe helyezésekor próbálja ki a Power BI Desktop alkalmazásban azokat a műveleteket, amelyeket a végfelhasználók végre fognak hajtani. Ha a jelentés túlzottan lassan tölt be a Power BI Desktop alkalmazásban, akkor szinte biztosan lassan fog betöltődni a szolgáltatásban is a végfelhasználóknak. 

## <a name="directquery-best-practices"></a>Ajánlott eljárások a DirectQuery használatához

Az alábbi szakasz néhány olyan általános ajánlott eljárást ismertet, amelyek a DirectQuery segítségével való csatlakozásra vonatkoznak.
  
### <a name="db-design-guidance"></a>Adatbázis-tervezési tanácsok

- Vigye át a számított oszlopokat és a mértékeket a forrásba, amikor csak lehetséges – minél közelebb vannak a forráshoz, annál jobb lesz a teljesítmény.
- Végezzen optimalizálást! Ismerje meg a lekérdezések végrehajtási tervét, adjon hozzá indexeket a gyakran szűrt oszlopokhoz, és így tovább.

### <a name="modeling-guidance"></a>Modellezési útmutató

- Kezdjen a Power BI Desktop alkalmazásban.
- Kerülje az összetett lekérdezések használatát a Lekérdezésszerkesztőben.
- Ne használjon relatív dátum szerinti szűrést a Lekérdezésszerkesztőben.  
- Tartsa a mértékeket kezdetben egyszerűen, és csak fokozatosan növelje az összetettségüket.
- Kerülje a számított oszlopok és az egyedi azonosítót tartalmazó oszlopok közötti kapcsolatokat.
- Próbálja meg megadni a „Hivatkozási integritás feltételezése” beállítást a kapcsolatokhoz – ez sok esetben jelentősen megnövelheti a lekérdezések teljesítményét.  

### <a name="general"></a>Általános

- Alkalmazzon szűrőket már kezdetben is.
- Fontolja meg, hogy kikapcsolja a vizualizációk közötti interakciókat – ez csökkenti a lekérdezési terhelést, amikor a felhasználók keresztkiemelést végeznek.
- Korlátozza a vizualizációk számát és a vizualizációnként megjelenített adatok mennyiségét, a fentebb ismertetettek szerint.
- A sorszintű biztonság engedélyezése jelentős hatással lehet a teljesítményre. Mindenképp tesztelje a felhasználók által használandó különféle sorszintű biztonsági szerepköröket.
- A szolgáltatásban érvényben vannak bizonyos lekérdezésszintű időkorlátok annak érdekében, hogy a sokáig futó lekérdezések ne tudják kisajátítani a rendszer erőforrásait. A 225 másodpercnél hosszabb ideig futó lekérdezéseknél időtúllépés történik, ami vizualizációs szintű hibát okoz.

## <a name="understand-dashboards-and-query-caches"></a>Az irányítópultok és a lekérdezési gyorsítótárak ismertetése

Az irányítópultokhoz rögzített vizualizációkat a lekérdezési gyorsítótár szolgáltatja az irányítópult betöltésekor. Ezzel ellentétben a jelentések megnyitásakor a lekérdezések valós időben futnak az adatforráson – mely vagy a Power BI szolgáltatás (importálás esetén), vagy pedig a megadott adatforrás (DirectQuery vagy élő kapcsolat esetén).  

> [!NOTE]
> Amikor élő jelentések csempéit rögzíti egy irányítópultra, ezek nem a lekérdezési gyorsítótárból lesznek szolgáltatva – ehelyett jelentésként viselkednek, és valós idejű lekérdezéseket küldenek a háttéralkalmazás magjainak.

Ahogy azt a neve alapján sejtheti, az adatok lekérdezési gyorsítótárból való beolvasása jobb és egységesebb teljesítményt nyújt, mintha közvetlenül az adatforrásra támaszkodna. E funkcionalitás kihasználásának egyik módja, ha az irányítópultokat kezdőlapként állítja be a felhasználók számára. A gyakran használt és sokak által igényelt vizualizációkat rögzítse az irányítópultokra. Ily módon az irányítópultok egy olyan értékes „első védelmi vonalként” szolgálnak, amely egységes teljesítményt nyújt, és csökkenti a kapacitás terhelését. A felhasználók pedig továbbra is elérhetik a jelentést, és elemezhetik a részletes adatokat.  
 

DirectQuery és élő kapcsolat esetében ez a lekérdezési gyorsítótár időszakosan frissül az adatforrás lekérdezésével. Alapértelmezés szerint ez óránként történik, de ez konfigurálható az adathalmaz beállításainál. A rendszer a lekérdezési gyorsítótár minden egyes frissítésekor lekérdezéseket küld az alapul szolgáló adatforrásnak a gyorsítótárban szereplő adatok frissítése céljából. A generált lekérdezések számát az határozza meg, hogy hány olyan vizualizáció van az irányítópultokon rögzítve, amely az adott adatforrásra támaszkodik. Tartsa szem előtt, hogy ha engedélyezve van a sorszintű biztonság, a rendszer minden egyes biztonsági környezethez külön lekérdezéseket generál. Ha például a felhasználók két különböző szerepkörre vannak osztva, és az adatok két különböző nézetét látják, akkor a lekérdezési gyorsítótár frissítésekor a rendszer két készletnyi lekérdezést generál. 

## <a name="understand-custom-visual-performance"></a>Az egyéni vizualizációk teljesítményének ismertetése 

Tesztelje az összes egyéni vizualizációt annak megállapításához, hogy biztosan megfelelő teljesítményt nyújtanak-e. A rosszul optimalizált egyéni vizualizációk a teljes jelentés teljesítményére negatív hatással lehetnek. 

## <a name="deep-dive-into-query-performance-with-sql-profiler-and-power-bi-desktop"></a>A lekérdezések teljesítményének részletes elemzése az SQL Profiler és a Power BI Desktop használatával

Ha szeretné részletesebben megismerni, hogy mely vizualizációk igényelnek a legtöbb időt és erőforrást, csatlakoztathatja az SQL Profiler eszközt a Power BI Desktop alkalmazáshoz, és megtekintheti a lekérdezések részletes teljesítményadatait.

> [!NOTE]
> A Power BI Desktop támogatja a diagnosztikai portokhoz való csatlakozást. A diagnosztikai port lehetővé teszi, hogy más eszközök csatlakozzanak és diagnosztikai célú nyomkövetést végezzenek. *A modell semmiféle módosítása sem támogatott! A modell megváltoztatása adatsérülést és adatvesztést okozhat.*

A teendők a következők:
  
1. **Telepítse az SQL Server Profiler eszközt, és indítsa el a Power BI Desktop alkalmazást**

   Az SQL Server Profiler eszköz az SQL Server Management Studio részeként érhető el.

2. **Határozza meg a Power BI Desktop által használt portot**

   Nyisson meg egy parancssor- vagy PowerShell-ablakot rendszergazdai engedélyekkel, majd a „netstat” parancs futtatásával állapítsa meg, hogy a Power BI Desktop alkalmazás mely portot használja:

   `> netstat -b -n`

   A kimenetben az alkalmazások, illetve az egyes alkalmazások által megnyitott portok listájának kell megjelennie, például a következőképpen:  

   `TCP    [::1]:55786            [::1]:55830            ESTABLISHED`

   [msmdsrv.exe]

   Keresse meg az msmdsrv.exe által használt portot, és jegyezze fel későbbi használat céljából. A fenti példában a portszám 55786.
3. **Csatlakoztassa az SQL Server Profiler eszközt a Power BI Desktop alkalmazáshoz**

   - Indítsa el az SQL Server Profilert a **Start** menüből.
   - Válassza a **File** (Fájl)  > **New Trace** (Új nyomkövetés) lehetőséget.
   - Kiszolgáló típusa: Analysis Services
   - Adja meg a Server name (Kiszolgáló neve) beállításnál a következő értéket: localhost:[a fentebb feljegyzett portszám]
   - A következő képernyőn válassza a **Run** (Futtatás) lehetőséget.
   - Ezzel aktiválta az SQL Profilert, mely ettől kezdődően gyűjteni fogja a Power BI Desktop alkalmazásból küldött lekérdezések adatait. 
   - A lekérdezések végrehajtásakor láthatja az azokhoz tartozó időtartamokat és processzoridőket – ezen információ alapján pedig megállapíthatja, mely lekérdezések korlátozzák leginkább a teljesítményt.  

Az SQL Profilerrel azonosíthatja a legtöbb processzoridőt használó lekérdezéseket, melyek általában a teljesítmény fő korlátozói. Ezután az optimalizálás folytatásakor az ezeket a lekérdezéseket végrehajtó vizualizációkra érdemes összpontosítani.

## <a name="gateway-best-practices"></a>Átjárókkal kapcsolatos ajánlott eljárások

A helyszíni adatátjárók a Power BI szolgáltatás helyszíni adatokhoz való csatlakoztatásának kiváló eszközei. Ha azonban nem megfelelően vannak megtervezve, nagyban korlátozhatják a jelentések teljesítményét. Ez különösképpen igaz a DirectQueryt vagy élő kapcsolatokat használó adathalmazok esetén, mivel ezeknél az összes lekérdezés és lekérdezésre adott válasz áthalad az átjárón. A nagy teljesítményű átjárók létrehozásának legfőbb szempontjai a következők: 

- **Használja a Vállalati üzemmódot**, és ne pedig a személyes módot.
- **Az átjáróra vonatkozó hardverkövetelményeknek** – 8 CPU-mag, 16 GB RAM.
- **Figyelés beállítása** – Állítson be teljesítményfigyelést az átjárót üzemeltető számítógépen, hogy értesülni tudjon róla, ha az átjáró a teljesítmény szűk keresztmetszetévé válik túlterhelődés miatt. További információért olvassa el a [Helyszíni adatátjárókkal kapcsolatos hibák elhárítása](service-gateway-onprem-tshoot.md) című témakört.
- **Vertikális vagy horizontális felskálázás** – Ha az átjáró szűk keresztmetszetté válik, fontolja meg az átjáró vertikális felskálázását (vagyis erősebb processzorral és több memóriával felszerelt számítógépre való áttelepítését) vagy horizontális felskálázását (például az adathalmazok különböző átjárók közötti felosztását). 
- **Az importálást és a DirectQuery szétválasztása** – Horizontális felskálázás esetén fontolja meg az importálási lekérdezésekért, illetve a DirectQuery-lekérdezésekért felelős átjárók szétválasztását.

## <a name="network-latency"></a>Hálózati késés

A hálózati késés hatással van a jelentések teljesítményére, hiszen megnöveli azt az időt, amely a kérések Power BI szolgáltatásba való eljuttatásához, illetve a válaszok kézbesítéséhez szükséges. A Power BI-bérlők egy adott régióhoz vannak társítva. Ha szeretné megtekinteni a bérlő „saját” régióját, nyissa meg a powerbi.com webhelyet, és válassza az ?** ikont a jobb felső sarokban, majd pedig **A Power BI névjegye** lehetőséget. Amikor egy bérlő felhasználói hozzáférnek a Power BI szolgáltatáshoz, a kéréseiket a rendszer mindig ehhez a régióhoz irányítja. Miután a kérések megérkeztek a Power BI szolgáltatásba, a szolgáltatás további kéréseket küldhet, például az alapul szolgáló adatforrásnak vagy az átjárónak, melyekre szintén érvényes a hálózati késés.

Bizonyos eszközök, például az [Azure Speed Test](http://azurespeedtest.azurewebsites.net/), segíthetnek megállapítani, hogy mekkora a hálózati késés az ügyfél és az Azure-régió között. A hálózati késés hatásának minimalizálásához általánosságban igyekezzen minél közelebb tartani egymáshoz az adatforrásokat, az átjárókat és a Power BI-fürtöt. Ha a hálózati késés problémát okoz, megpróbálhatja az átjárókat és az adatforrásokat közelebb helyezni a Power BI-fürthöz, például úgy, hogy áthelyezi őket virtuális gépekre.

A hálózati késés további javításához fontolja meg az [Azure ExpressRoute](https://azure.microsoft.com/services/expressroute/) szolgáltatás használatát, mellyel gyorsabb és megbízhatóbb hálózati kapcsolatokat hozhat létre az ügyfelei és az Azure-adatközpontok között.

## <a name="next-steps"></a>Következő lépések

- [A Power BI vállalati bevezetésének megtervezése](https://aka.ms/pbienterprisedeploy) – Teljes körű útmutatás a nagyméretű Power BI-példányok üzembe helyezéséhez
- [DirectQuery az SQL Server 2016 Analysis Services szolgáltatásban](https://blogs.msdn.microsoft.com/analysisservices/2017/04/06/directquery-in-sql-server-2016-analysis-services-whitepaper/)
- [[YouTube] Gyors és megbízható jelentések létrehozása a Power BI-ban](https://www.youtube.com/watch?v=GhiJABR7XX0)
- [[YouTube] A Power BI vállalati bevezetése](https://www.youtube.com/watch?v=K-zEWICvICM)