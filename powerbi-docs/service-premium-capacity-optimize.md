---
title: A Microsoft Power BI Premium kapacitásaihoz optimalizálása
description: Ismerteti a stratégiák optimalizálása a Power BI Premium-kapacitásait.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/09/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 06712b6bcf57ca84ec03d2c7b99b32ea61ad8c71
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565335"
---
# <a name="optimizing-premium-capacities"></a>Prémium szintű kapacitások optimalizálása

Ha prémium szintű kapacitás teljesítménybeli problémák merülnek fel, a közös először megközelítést az optimalizálásában vagy finomhangolása a megoldások elfogadható válaszidők visszaállításához. A közösségértékek, elkerülheti a további prémium szintű kapacitás vásárlásával, kivéve a folyamatban.

Ha további prémium szintű kapacitáshoz szükség, két lehetőség van a cikkben leírt:

- Vertikális felskálázás egy meglévő prémium szintű kapacitás
- Adjon hozzá egy új prémium szintű kapacitás

Végül tesztelési módszer és a prémium szintű kapacitás méretezése utasításoknak megfelelően ez a cikk.

## <a name="best-practices"></a>Ajánlott eljárások

Amikor próbálja ajánlott kihasználtságát és a teljesítmény, van néhány gyakorlati, beleértve:

- Alkalmazás-munkaterületek használatával személyes munkaterületek helyett.
- Kritikus fontosságú üzleti és önkiszolgáló bi-ban (összetett) szétválasztása eltérő kapacitások be.

  ![Kritikus fontosságú üzleti és az önkiszolgáló BI szétválasztása eltérő kapacitások be](media/service-premium-capacity-optimize/separate-capacities.png)

- Tartalom megosztása csak a Power BI Pro-felhasználók, ha előfordulhat, hogy nem tárolhatja a tartalmakat egy dedikált kapacitást kell lennie.
- Használja a dedikált kapacitást, ha egy adott frissítés idejének eléréséhez, vagy ha az adott funkciók szükségesek. Ha például a nagy méretű adatkészletek és többoldalas jelentéseket.

### <a name="addressing-common-questions"></a>Gyakori kérdések-címzés

A Power BI Premium üzemelő példányok optimalizálásához összetett művelet, amely magában foglaló munkaterhelési követelményeinek, a rendelkezésre álló erőforrások és a hatékony használati megismerése.

Ez a cikk foglalkozik hét gyakori kérdésekre, leíró lehetséges problémák és magyarázatok és tájékoztatást arról, hogyan azonosíthatja és azok megoldását.

### <a name="why-is-the-capacity-slow-and-what-can-i-do"></a>Miért van a lassú kapacitást, és mi a teendő?

Nincsenek számos oka lehet, amely hozzájárulhat a lassú prémium-kapacitás. Ez a kérdés további információra van szüksége, megismerheti, mit kell érteni lassú. Azok a jelentések betöltődni? Vagy azok sikertelen betöltéséhez? Lassúak a jelentésvizualizációk betölteni vagy frissíteni, ha a felhasználók használják a jelentést? Frissülnek véve hosszabb, mint a várt, vagy a korábban észlelt?

Kellene szerzett megértéséhez okát, majd elkezdheti vizsgálatára. Az alábbi hat kérdésekre adott válaszok segítségével történő több konkrét problémák.

### <a name="what-content-is-using-up-my-capacity"></a>Milyen tartalmat használ fel saját kapacitása?

Használhatja a **Power BI Premium kapacitás-metrikák** alkalmazás szűrés a kapacitást, és tekintse át a munkaterület-tartalom a teljesítmény-mérőszámon. Tekintse át a teljesítmény-mérőszámok és erőforrás-használatra óránként egy prémium szintű kapacitáson belül tárolt összes tartalom az elmúlt hét nap, lehetőség. Figyelés gyakran, ha a prémium szintű kapacitás teljesítményével kapcsolatos általános gondja hibaelhárítás első lépése.

Alapvető metrikák figyelése a következők:

- Átlagos CPU és a magas kihasználtság számát.
- Átlagos memória és a magas kihasználtság száma és a memóriahasználat, adott adatkészletek, adatfolyamok és többoldalas jelentések.
- Aktív adatkészlet a memóriába való betöltéskor.
- Átlagos és maximális lekérdezés időtartamának összegénél.
- A lekérdezés átlagos várakozási időt.
- Átlagos adatkészletet és adatfolyam frissítse alkalommal.

A Power BI Premium kapacitás-metrikák alkalmazásban aktív memória mutatja az adott meg egy jelentést, amely nem dobható, mert az utolsó három percen belül használatban lévő memória teljes mennyiségétől. Egy nagy és/vagy aktív adatkészlet frissítési várakozási idő kiugróan magas sikerült megfeleltetendő.

A **által átlagos időtartama 5 legnagyobb terhelésű** diagram kiemeli az öt adatkészleteket, többoldalas jelentések és adatfolyamok kapacitás erőforrásokat. Az öt legaktívabb tartalom listák vizsgálat és a lehetséges optimalizálása a deduplikációra.

### <a name="why-are-reports-slow"></a>Miért olyan jelentések lassú?

Az alábbi táblázat ismerteti a lehetséges problémákat, és hogy hogyan azonosíthatja és kezelni őket.

#### <a name="insufficient-capacity-resources"></a>Nincs elegendő kapacitás erőforrások

| Lehetséges magyarázata | Azonosítása | Megoldását |
| --- | --- | --- |
| Összes aktív magas memóriahasználat (modell nem zárható ki, mert az utolsó három percen belül használja).<br><br> Lekérdezés több magas kiugrások várjon alkalommal.<br><br> Frissítés több magas kiugrások várjon alkalommal. | Figyelheti a mérőszámokat memória \[ [1](#endnote-1)\], és a kizárási \[ [2](#endnote-2)\]. | A modell méretének csökkentése, vagy a DirectQuery módra. Tekintse meg a [modellek optimalizálása](#optimizing-models) szakasz ebben a cikkben.<br><br> Vertikális felskálázás a kapacitást.<br><br> Rendelje hozzá a tartalmat egy másik kapacitást. |

#### <a name="inefficient-report-designs"></a>A jelentés nem elég hatékony tervek

| Lehetséges magyarázata | Azonosítása | Megoldását |
| --- | --- | --- |
| Jelentésoldalak (interaktív szűrés is indíthat vizualizációnként legalább egy lekérdezést) túl sok vizualizációt tartalmaz.<br><br> Vizualizációk a szükségesnél több adat lekérése. | Tekintse át a jelentés tervek.<br><br> Adatfelvétel jelentés felhasználóknak megérteni, hogyan használják a jelentéseket.<br><br> Adatkészlet lekérdezés metrikák figyelése \[ [3](#endnote-3)\]. | Egy-egy lapon kevesebb vizualizációt tartalmazó jelentések újratervezése. |

#### <a name="dataset-is-slow-especially-when-reports-have-previously-performed-well"></a>Adatkészlet lassú, különösen akkor, ha a jelentések végzett korábban is

| Lehetséges magyarázata | Azonosítása | Megoldását |
| --- | --- | --- |
| Adatok importálása egyre nagyobb mennyiségű.<br><br> Összetett vagy nem elég hatékony számítási logika, beleértve az RLS-szerepkörök.<br><br> A modell nem teljes mértékben optimalizálva.<br><br> (DQ/LC) Átjáró késése.<br><br> Lassú DQ forrás lekérdezések válaszidejét. | Tekintse át a modell műveletekhez.<br><br> Átjáró-teljesítményszámlálók figyelése. | Tekintse meg a [modellek optimalizálása](#optimizing-models) szakasz ebben a cikkben. |

#### <a name="high-concurrent-report-usage"></a>Egyidejű jelentés magas kihasználtsága

| Lehetséges magyarázata | Azonosítása | Megoldását |
| --- | --- | --- |
| A lekérdezési várakozási időt.<br><br> CPU színtelítettség.<br><br> DQ/LC kapcsolat korlát túllépve. | Monitorozhatja a processzorkihasználtságot \[ [4](#endnote-4)\], lekérdezés várakozási idő és a DQ/LC kihasználtság \[ [5](#endnote-5) \] metrikák + lekérdezés időtartamának összegénél. Ha ingadozik, egyidejűségi problémák adhatja meg. | Vertikális felskálázás a kapacitást, vagy rendelje hozzá a tartalmat egy másik kapacitást.<br><br> Egy-egy lapon kevesebb vizualizációt tartalmazó jelentések újratervezése. |

**Megjegyzések:**    
<a name="endnote-1"></a>\[1\] átlagos memóriahasználat (GB) és a legmagasabb memóriát (GB).   
<a name="endnote-2"></a>\[2\] adatkészlet adatbázislap.   
<a name="endnote-3"></a>\[3\] adatkészlet lekérdezések, az adatkészlet átlagos lekérdezési idő (ms), a adatkészlet várjon száma és az adatkészlet átlagos várakozási idő (ms).   
<a name="endnote-4"></a>\[4\] magas CPU-kihasználtság száma és a legnagyobb kihasználtságú (elmúlt hét napban) a CPU-idő.   
<a name="endnote-5"></a>\[5\] DQ/LC magas kihasználtság száma és a legnagyobb kihasználtságú (elmúlt hét napban) DQ/LC időpontja.   

### <a name="why-are-reports-not-loading"></a>Miért van a jelentések nem töltődik be?

Nem sikerült betölteni a jelentések, esetén a kapacitást nem rendelkezik elég memóriával, és túlterhelt fűtött meg arról, hogy bejelentkezési. Ez akkor fordulhat elő, amikor az összes betöltött modellek vannak aktívan kérdeznek le, és ezért nem dobható, és frissítési műveleteket már fel van függesztve vagy késleltetett. A Power BI szolgáltatás megkísérli az adatkészlet betöltése 30 másodpercet, és a felhasználó szabályosan értesítést kap, próbálkozzon újra hamarosan javaslatot a hiba.

Jelenleg nincs nincs a mérőszám a jelentés betöltési hibák figyelése. A probléma lehetséges monitorozási rendszer memóriájában, kifejezetten legmagasabb kihasználtsággal és idővel a legnagyobb kihasználtságú alapján azonosíthatja. Magas adatkészlet adatbázislap és hosszú az adatkészlet frissítési átlagos várakozási idő sikerült javasoljuk, hogy a probléma jelentkezett.

Ez néha csak nagyon történik, ha ez nem tekinthetők a prioritás a probléma. A jelentés felhasználók üzenetet kapnak, hogy a szolgáltatás foglalt, és, hogy azok kell próbálkoznia rövid idő múlva. Ha túl gyakran történik, a probléma a prémium szintű kapacitás vertikális felskálázásával, vagy a tartalom hozzárendelése egy másik kapacitás lehet orvosolni.

A kapacitás rendszergazdák (és a Power BI szolgáltatás-rendszergazdák) figyelheti a **sikertelen lekérdezések** metrika meghatározni, ha ez történik. Akkor is újraindíthatja a kapacitás, minden művelet esetén a rendszer túlterhelési alaphelyzetbe állítása.

### <a name="why-are-refreshes-not-starting-on-schedule"></a>Miért vannak frissítések nem indul el ütemezés szerint?

Az ütemezett frissítés kezdési idejének nem garantált. Ne felejtse el, hogy a Power BI szolgáltatás mindig rangsorolja interaktív műveletekhez háttérműveletekhez keresztül. Frissítés a háttérben futó művelet, amely akkor fordulhat elő, amikor két feltétel teljesül:

- Nincs elegendő memória
- A prémium szintű kapacitás esetén támogatott egyidejű frissítések száma nem lett túllépve

Ha a feltételek nem teljesülnek, a frissítés várólistára van állítva, addig, amíg kedvező feltételek.

A teljes frissítés, amely az aktuális adatkészlet memória méretének legalább duplán visszaírási szükség. Ha nem áll rendelkezésre elegendő memória áll rendelkezésre, majd a frissítés nem kezdhetik meg modell kiürítési szabadít fel memória – Ez azt jelenti, hogy késések mindaddig, amíg egy vagy több adatkészletet inaktívvá válik, és képes eltávolítani kívánt.

Ne felejtse el, hogy a támogatott maximális egyidejű frissítések számát értéke 1,5-szerese a háttérbeli virtuális magokkal lesz kerekítve.

Egy ütemezett frissítés meghiúsul, ha azt nem akkor kezdődik, a következő ütemezett frissítés határideje megkezdése előtt. Egy igény szerinti frissítést, a felhasználói felületen manuálisan aktivált megpróbálja legfeljebb három alkalommal futtatása korábban sikertelen.

A kapacitás rendszergazdák (és a Power BI szolgáltatás-rendszergazdák) figyelheti a **átlagos frissítése várakozási idő (perc)** metrika meghatározni a megadott időpont és a művelet kezdete közötti átlagos késés.

Amíg egy rendszergazda prioritás, kereskedelmi adatok általában nem frissül, győződjön meg arról, hogy elegendő memória áll rendelkezésre. Ez magában foglalhatja adatkészleteket, ismert elegendő erőforrással rendelkező kapacitások elkülönítése. Lehetőség arra is, hogy a rendszergazdák sikerült egyeztessen a az adatkészlet tulajdonosa szinkronizálások eltolása vagy ütemezett adatok frissítési idejének ütközések minimálisra csökkentése érdekében. Vegye figyelembe, hogy már nem a rendszergazda a frissítési várólista megtekintéséhez, vagy az adatkészlet lekéréséhez ütemezi.

### <a name="why-are-refreshes-slow"></a>Miért vannak lassú frissítések?

Frissítések lassú - vagy észlelhető (mint az előző gyakori kérdés címek) lassú lehet.

Ha a frissítés tulajdonképpen lassú, számos oka lehet:

- Nem elegendő Processzor (a frissítés nagyon CPU-igényes lehet).
- Nincs elég memória, frissítés (amely a kezdenie, ha feltételek esetén a mellőzésére kedvező újrabetöltést igényel) felfüggesztése eredményez.
- Nem-kapacitási okokból, beleértve az adatforrás rendszer válaszideje, hálózati késés, érvénytelen engedélyek vagy átjáró teljesítménye.
- Adatmennyiség - csak jó okkal növekményes konfigurálása frissül, mint az alábbiak ismertetik.

Kapacitás rendszergazdák (és a Power BI szolgáltatás-rendszergazdák) figyelheti a **frissítése átlagos időtartam (perc)** összehasonlítás a teljesítményteszt meghatározni az idő múlásával metrika és a **átlagos frissítése várakozási idő (perc)** mérőszámok megállapításához közötti átlagos késés átlagos az ütemezett idő és a művelet megkezdése között.

Növekményes frissítési adatok frissítés időtartama, különösen a nagy méretű adatmodell-táblák jelentősen csökkentheti. Nincsenek a növekményes frissítés négy előnye:

- **Frissítések gyorsabbak** – egy tábla csak egy részhalmazát kell betöltése során, és csökkenti a Processzor- és használati és párhuzamosság is magasabb lehet, több partíción frissítésekor.
- **Frissítés történik, csak szükség esetén** -növekményes frissítési szabályzatok beállíthatók úgy, hogy betölteni, csak ha adatok megváltoztak.
- **Frissítések megbízhatóbb** -rövidebb futó kapcsolatokat felejtő datasource rendszerekkel kevésbé érzékenyek, adott válaszának.
- **Modellek maradnak vágás** -növekményes frissítési szabályzatok beállíthatók úgy, hogy automatikusan eltávolítja az előzmények túl az idő csúszóablakban.

További tudnivalókért lásd: [növekményes frissítés a Power BI Premium](service-premium-incremental-refresh.md).

### <a name="why-are-data-refreshes-not-completing"></a>Miért van az adatok frissítése feladatom befejezése meghiúsul?

Amikor az Adatfrissítés megkezdése, de nem lehetett végrehajtani, számos oka lehet:

- Nincs elég memória, akkor is, ha csak egy modell található a prémium szintű kapacitás, azaz a modell mérete nagyon nagy.
- Nem-kapacitási okokból, beleértve a datasource rendszer leválasztásának, érvénytelen engedélyek vagy átjáró hiba.

A kapacitás rendszergazdák (és a Power BI szolgáltatás-rendszergazdák) figyelheti a **frissítése hibák miatt nincs elegendő szabad memória** metrika.

## <a name="optimizing-models"></a>Modellek optimalizálása

Optimális modell felépítésének elengedhetetlen egy hatékony és méretezhető megoldások kidolgozását. Azonban van ez a cikk biztosít teljes körű vita hatókörén kívül esik. Ehelyett ez a szakasz biztosít legfontosabb szempont modellek optimalizálása.

### <a name="optimizing-power-bi-hosted-models"></a>Optimalizálása a Power bi-ban üzemeltetett modellek

Prémium kapacitásban lévő üzemeltetett modellek optimalizálása a másolással történő, és a modell rétegeken lehet elérni.

Vegye figyelembe az importálás modell optimalizálási lehetőségeit:

![Az importálás modell optimalizálási lehetőségekkel](media/service-premium-capacity-optimize/import-model-optimizations.png)

Az adatforrás rétegben:

- Relációs adatforrások előre integráló adatokat, alkalmazza a megfelelő indexeket, olyan táblapartíciók meghatározása a növekményes frissítés időszakokra és számítások materializálása segítségével optimalizálható a leggyorsabb lehetséges frissítési biztosításához (helyén kiszámítása táblák és oszlopok modell) vagy a számítási logika hozzáadása a nézetekhez.
- Nem relációs adatforrások előre relációs adattárak integrálható.
- Biztosíthatja a átjárók erőforrásokkal, lehetőleg gépeken dedikált, elegendő hálózati sávszélesség és hálózatbővítési az adatforrásokhoz.

A modell rétegben:

- A Power Query lekérdezést tervek is minimálisra csökkentése vagy összetett átalakítások, és különösen azokkal, amelyek a különböző adatforrások (data warehouse-adattárházak ennek érdekében a kinyerési, átalakítási-betöltési szakaszában) egyesítése. Is biztosítja, hogy megfelelő adatforrás adatvédelmi szintjei vannak beállítva, így elkerülhető, igénylő lekérdezések között egy összesített eredményt teljes eredmények betöltése a Power bi-ban.
- A modell szerkezetét meghatározza, hogy az adatok betöltése, és a modell mérete közvetlen hatással van. Azt is úgy, hogy elkerülje a felesleges adatokat (különösen előzményadatok) sorok eltávolítását, szükségtelen oszlopok eltávolításával vagy összegzett adatokat jelez (rovására részletes adatok betöltése) betöltése. Drámai méretének csökkentése nagy számosságú oszlopokat (különösen a szöveges oszlopok), amely tárolja és nem nagyon hatékonyan tömörítése eltávolításával érhető el.
- Egyetlen irányra kapcsolatok konfigurálásával, kivéve, ha van egy jelentős indok arra, hogy engedélyezze a kétirányú szűrés modell lekérdezési teljesítmény javítása érdekében. Emellett érdemes a [CROSSFILTER](https://docs.microsoft.com/dax/crossfilter-function) helyett kétirányú szűrés funkciót.
- A táblákban összesítési kibővítése a lekérdezési válaszok betöltésével előre összegzett adatok, érhető el, azonban ez a modell és az eredmény mérete megnő a frissítés hosszabb időt. Általában a táblákban összesítési számára lefoglalt nagyon nagy méretű modellek vagy összetett modell műveletekhez.
- Számított táblázatokat, oszlopokat modell méretének növeléséhez és a frissítés hosszabb időt eredményez. Általában egy kisebb tárméret és gyorsabb frissítés érhető el, a tényleges táblán alapuló vagy az adatforrás alapján számítjuk ki. Ha ez nem lehetséges, egyéni oszlopokat a Power Query használatával elérhetővé teheti még több tárterület-tömörítést.
- Előfordulhat, hogy lehetőség a DAX-kifejezésekben a mértékek és RLS-szabályokat, például újraírását logikát, elkerülheti a költséges képletek finomhangolása
- A növekményes frissítés frissítési idő csökkentése érdekében jelentősen, és takarítson meg a memória és CPU. A növekményes frissítés eltávolítása modellméretet vágás tartja előzményadatok is konfigurálható.
- Ha másik, ütköző lekérdezési minták modell sikerült újratervezve két modell szerint. Például bizonyos összes előzmények, valamint is jelen magas szintű összesítések 24 órányi késéssel ugyan jelentéseket. Más jelentések mai adatokat tartalmazó aggódik, és az egyes tranzakciók részletes hozzáférésre van szükségük. Ahelyett, hogy tervezzen egy adott modellt felel meg az összes jelentés az egyes követelményekhez optimalizált két modell létrehozása.

Fontolja meg a DirectQuery modellben optimalizálási lehetőségeit. Ahogy a modellben a lekérdezésekre vonatkozó kérelmek problémák az alapul szolgáló adatforrás, datasource optimalizálási fontos rugalmas adatbázismodell lekérdezések továbbítása.

 ![Egy DirectQuery-modell optimalizálási lehetőségek](media/service-premium-capacity-optimize/direct-query-model-optimizations.png)

Az adatforrás rétegben:

- Az adatforrás is lehet optimalizálni annak érdekében, hogy a leggyorsabb lehetséges lekérdezése előre integrálja az adatokat (ez nem lehetséges a modell rétegben), alkalmazza a megfelelő indexeket, táblapartíciók materializálása meghatározása összegzett adatok (az indexelt nézetek), és számítási végfelhasználónak. A legjobb élményt érhető el, ha átmenő lekérdezéseket kell csak szűrését, és hajtsa végre a belső illesztések indexelt táblák vagy nézetek között.
- Biztosíthatja a átjárók erőforrásokkal, lehetőleg gépeken dedikált, elegendő hálózati sávszélesség és a datasource hálózatbővítési.

A modell rétegben:

- Power Query lekérdezéssel formátumukban kell lehetőleg átalakítások nem – ellenkező esetben megkísérlik kívül tartani átalakításokat is az abszolút minimális.
- Egyetlen irányra kapcsolatok konfigurálásával, kivéve, ha van egy jelentős indok arra, hogy engedélyezze a kétirányú szűrés modell lekérdezési teljesítmény javítása érdekében. Ezenkívül modell, kapcsolatokat konfigurálni kell, hogy feltételezik, hogy hivatkozási integritás (Ha ez a helyzet) és hatékonyabb belső illesztések használata (nem a külső illesztések) adatforrás-lekérdezéseket eredményez.
- Ne hozzon létre a Power Query lekérdezést egyéni oszlopot és a modell számított oszlop – a tényleges táblává alakíthatóak ezeket az adatforrásokat, amikor csak lehetséges.
- Előfordulhat, hogy lehetőség finomhangolása a mértékek és RLS-szabályokat, például újraírását logikát, elkerülheti a költséges képletek DAX-kifejezésekben.

Fontolja meg egy összetett modell az optimalizálási lehetőségekkel. Ne felejtse el, hogy egy összetett modell lehetővé teszi, hogy importálási és DirectQuery táblákat.

![Egy összetett modell optimalizálási lehetőségek](media/service-premium-capacity-optimize/composite-model-optimizations.png)

- Az importálási és DirectQuery-modellek az Optimalizálás általában ezek tárolási módot használó összetett adatmodell-táblák vonatkoznak.
- Általában arra törekszik, hogy egy elosztott terhelésű kialakítás megvalósítása dimenziótípusnak táblák (üzleti entitásokat képviselő) konfigurálásával táblákként kettős tárolási mód és a tény-type (gyakran nagy táblák, operatív tények képviselő), DirectQuery tárolási mód. Kettős tárolási mód azt jelenti, hogy a is importálhatja, és a DirectQuery tárolási mód, és ez lehetővé teszi a Power BI szolgáltatás egy natív lekérdezés átmenő generálása során használandó leghatékonyabb tárolási módját határozza meg.
- Győződjön meg arról, hogy átjárók lehetőleg gépeken dedikált, elegendő hálózati sávszélesség és adatforrások hálózatbővítési elegendő erőforrással rendelkezik
- Tárolási mód importálás biztosíthat DirectQuery tárolási mód (tény) típusú táblák összegzéséhez drámai lekérdezési teljesítményt érintő továbbfejlesztés összesítések táblák konfigurálva. Ebben az esetben összesítési táblák a modell méretének növekedését és növelheti a frissítés idejét, és gyakran ez a lekérdezések egy elfogadható kompromisszum.

### <a name="optimizing-externally-hosted-models"></a>Optimalizálás külsőleg üzemeltetett modellek

Számos optimalizálási lehetőségekkel tárgyalt a [optimalizálása a Power bi-ban üzemeltetett modellek](#optimizing-power-bi-hosted-models) szakaszban is alkalmazni kell az Azure Analysis Services és az SQL Server Analysis Services fejlett modellek. Egyértelmű kivétel bizonyos funkciók, amely jelenleg nem támogatottak, többek között összetett modelleket és összesítési táblák.

Egy további szempont, külsőleg üzemeltetett adatkészletek esetében, az adatbázis-üzemeltetési viszonyítva a Power BI szolgáltatásban. Az Azure Analysis Services esetén ez azt jelenti, hogy az Azure-erőforrás létrehozása a Power BI-bérlő (otthoni régiója) ugyanabban a régióban. Az SQL Server Analysis Services esetén az IaaS Ez azt jelenti, hogy ugyanabban a régióban a virtuális Gépet üzemeltető, és a helyszínen, az azt jelenti, hogy egy hatékony átjáró telepítőjének biztosítása.

Egy feltöltési, érdemes lehet, fontos megjegyezni, hogy az Azure Analysis Services-adatbázisokat és SQL Server Analysis Services táblázatos adatbázisok megkövetelése, hogy a modellek a memóriába teljes-lekérdezése támogatásához, hogy azok továbbra is van minden alkalommal. A Power BI szolgáltatásban, például szükség van elegendő memória a frissítés, ha a modell online kell maradnia a frissítés során. Ellentétben a Power BI szolgáltatásban, és nincs modellek automatikusan elavult adataikkal memória kihasználtsága alapján. A Power BI Premium, ezért maximalizálhatja a modell lekérdezés alacsonyabb memóriahasználat a hatékonyabb megközelítést kínál.

## <a name="capacity-planning"></a>Kapacitástervezés

Prémium-kapacitás mérete határozza meg, a rendelkezésre álló memória és a processzor-erőforrások és a kapacitás vonatkozó korlátozások. A prémium szintű kapacitások számát is fontos szempont, mint létrehozása több prémium szintű kapacitások segíthet egymástól számítási feladatok elkülönítésére. Vegye figyelembe, hogy storage 100 TB-os kapacitás csomópontonként, és ez valószínűleg több mint elegendő, ha bármilyen számítási feladatot.

Amely meghatározza, hogy a méretét és a prémium szintű kapacitások kihívást jelenthet, kifejezetten rendszergazdák számára a kezdeti kapacitások hoz létre. Az első lépés, ha kapacitásméretezést munkaterhelés átlagos jelölő várt mindennapos használatának megértéséhez. Fontos tudni, hogy nem minden munkaterhelésről sem egyenlő. Például: a álló kínálat - egyik végén 100 egyidejű felhasználó fér hozzá egyetlen vizualizációt tartalmazó egyetlen jelentésoldalon könnyen elérhető. Még - - spektrum másik végén 100 egyidejű felhasználó fér hozzá a különböző jelentések 100, egyenként 100 Vizualizációk a jelentés oldalon lévő hozom létre kapacitás-erőforrások különböző igényeknek.

Kapacitás-rendszergazdák ezért figyelembe kell vennie a sok tényező befolyásolja a környezet, a tartalom és a várható használat. Maximalizálhatja a tárolókapacitás kihasználtságát konzisztens gyorsaság elfogadható várakozási időt és kiürítési díjak adatbáziscsoportok legfontosabb célja. Tényezőket veszi figyelembe a következők lehetnek:

- **Modell mérete és az adatok jellemzői** -importált modelleken teljes betöltése a memóriába, hogy a lekérdezési vagy frissítése kell lennie. LC/DQ adatkészletek jelentős processzoridő- és valószínűleg jelentős összetett mértékeket és az RLS-szabályok kiértékelése lehet szükség. Memória és a feldolgozó mérete és a LC/DQ lekérdezések átviteli sebességére is korlátozza a kapacitás méretét.
- **Egyidejű aktív modellek** -különböző importált modelleken egyidejű lekérdezését fog nyújtani ajánlott válaszidejét és teljesítmény, ha azokat a memóriában marad. Gazdagép összes erősen lekérdezett modelleket, hogy a frissítéshez további memória elegendő memóriával kell lennie.
- **Importálás a modellfrissítéshez** – memória és a processzor terhelését is különösen hatással lehet a frissítés típusa (teljes vagy növekményes), az időtartam és a Power Query lekérdezéseket, és a számított tábla vagy oszlop logikai összetettségét. Egyidejű frissítések csak korlátozottan működik, a kapacitás méretét (1,5 x backend mag, kerekítve) szerint.
- **Egyidejű lekérdezések** -számos egyidejű lekérdezéseket eredményezhet a nem válaszoló jelentések mikor processzor- és LC/DQ kapcsolatok meghaladja a kapacitási korlátot. Ez különösen a helyzet sok vizualizációt tartalmazó jelentésoldalak.
- **Adatfolyamok és oldalakra osztott jelentések** -kapacitás beállítható úgy, hogy az adatfolyamok és a kapacitás memóriával konfigurálható maximális százalékos igénylő, többoldalas jelentések támogatásához. Memória adatfolyamok számára dinamikusan történik, de a többoldalas jelentések statikusan hozzá van rendelve.

Ezek a tényezők mellett a kapacitás-rendszergazdák is érdemes lehet létrehozni több kapacitások. Több kapacitás lehetővé teszik a számítási feladatok elkülönítése és beállítható úgy, hogy prioritást számítási feladatok rendelkezik garantált erőforrások biztosítása. Ha például két kapacitások üzleti szempontból kritikus fontosságú számítási feladatok elkülönítése önkiszolgáló BI összetett számítási feladatok is létrehozható. Az üzleti szempontból kritikus fontosságú kapacitása nagy vállalati modellek, így azokat a garantált erőforrásokkal rendelkező authoring hozzáférés csak az informatikai részleg számára biztosított elkülönítéséhez használható. Az összetett kapacitás, kisebb modelleket egyre nagyobb számban üzemeltetéséhez az üzleti elemzők számára biztosított hozzáférés használható. Az összetett kapacitás esetenként tapasztalhat, amelyek tolerálható lekérdezés vagy a frissítés vár.

Az idő múlásával a kapacitás-rendszergazdák tudja osztani a munkaterületek kapacitások között munkaterületek, vagy a munkaterületek között kapacitások közötti áthelyezése a tartalmat, és a kapacitások kiterjesztése vagy szűkítése. Általában a gazdagép nagyobb modellekhez, vertikális felskálázás és a magasabb szintű egyidejűség érdekében horizontális felskálázása.

Ne felejtse el, hogy a bérlő virtuális magok licencet vásárol biztosít. Vásárlása egy **P3** előfizetés segítségével hozzon létre egyet, vagy akár négy prémium szintű kapacitás, azaz P3 vagy a x P2 2 vagy 4 x 1 x P1. Emellett egy P2 szintű kapacitás, P3 kapacitásokhoz Továbbfejlesztő, mielőtt is mérlegelni történő felosztásának eredménye a virtuális magok két P1 szintű kapacitások létrehozása.

## <a name="testing-approaches"></a>Tesztelési módszer

A kapacitás méretét dönthető el, ha tesztelési végezhető létrehozása az ellenőrzött környezetben. A gyakorlati és gazdaságos lehetőség, hogy hozzon létre egy Azure (termékváltozatok) kapacitást, megjegyezni, hogy a P1 kapacitás, az A4 kapacitás, a P2 az azonos méretű és P3 kapacitások akkora, mint a A5 és az a6-os kapacitások jelölik. Azure kapacitások gyorsan létrehozhatók és óradíjat számítjuk fel. Tehát tesztelés befejezése után a egyszerűen törölje őket keletkezhetnek költségek leállítása.

A vizsgálati tartalom is hozzáadhatók a munkaterületek létrehozása az Azure kapacitás, és egyéni felhasználóként is jelentések futtatásával hozzon létre egy valósághű és reprezentatív munkaterhelés-lekérdezések. Ha importált modelleken, is minden modell frissítésének kell végrehajtani. Monitorozási eszközökkel, majd segítségével minden metrika erőforrás-használat megértéséhez tekintse át.

Fontos, hogy a vizsgálatok megismételhető-e. Tesztek többször kell futtatni, és továbbítsa körülbelül ugyanazt az eredményt, azok minden alkalommal, amikor. Ezekkel az eredményekkel átlagosan extrapolálja, és megbecsülheti a számítási feladatok valódi éles körülmények között is használható.

Szeretne létrehozni egy terhelési teszt, érdemes a terhelésteszt valósághű számítási feladatok szimulálásához alkalmazás lehet. Hogyan érhető ez tulajdonságairól Ez a cikk hatókörén kívül vannak. További információk egy kódmintát, tekintse meg a [tesztelési Power BI-alkalmazások betöltése a Visual Studio terhelési teszt](https://blogs.msdn.microsoft.com/charles_sterling/2018/04/04/webinar-load-testing-power-bi-applications-with-visual-studio-load-test/) webináriumra.

## <a name="acknowledgements"></a>Nyugtázás

Ez a cikk írásának Peter Myers, a Data Platform MVP és a független, a BI-Szakértővé [bitenként megoldások](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Következő lépések

> [!div class="nextstepaction"]
> [Prémium szintű kapacitás forgatókönyvek](service-premium-capacity-scenarios.md)   
  
További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

||||||