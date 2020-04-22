---
title: A Power BI Premium Metrics alkalmazás
description: Megtudhatja, hogyan használhatja a Power BI Premium Metrics alkalmazást, és háríthatja el a prémium szintű kapacitás problémáit.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/17/2020
LocalizationGroup: Premium
ms.openlocfilehash: 80f870f1657e629786cec299484f3b3c97609e79
ms.sourcegitcommit: d43761104f7daf4b2f297648855bb573b53e6d8c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/18/2020
ms.locfileid: "81637941"
---
# <a name="power-bi-premium-metrics-app"></a>A Power BI Premium Metrics alkalmazás

A **Power BI Premium Metrics alkalmazással** kezelheti a Power BI Premium-előfizetés állapotát és kapacitását. Az alkalmazásban a rendszergazdák az alkalmazás **Kapacitásállapot-központjában** láthatják és kezelhetik az indikátorokat, amelyek a prémium szintű kapacitásuk állapotát figyelik. A Metrics alkalmazás egy **Kapacitásállapot-központ** nevű kezdőlapot, illetve három fontos metrika részleteit tartalmazza:

* Aktív memória
* Lekérdezési várakozások
* Frissítési várakozások

![A Power BI Premium Metrics alkalmazás](media/service-premium-metrics-app/premium-metrics-app-00.png)

A következő szakaszok részletesen ismertetik a kezdőlapot és a három metrika jelentéslapjait. 





## <a name="premium-capacity-health-center"></a>Prémium szintű kapacitás állapotközpontja

Amikor megnyitja a **Power BI Premium Metrics alkalmazást**, a **Kapacitásállapot-központ** jelenik meg, amelyen a Power BI Premium-kapacitás állapotának áttekintése látható.

![A kapacitásállapot-központ a Premium Metrics alkalmazásban](media/service-premium-metrics-app/premium-metrics-app-01.png)

Ha a szervezet több prémium szintű előfizetéssel rendelkezik, a kezdőlapon kiválaszthatja a megtekinteni kívánt Power BI Premium-kapacitást. A prémium szintű kapacitás megtekintéséhez válassza az oldal tetején található, **Válasszon kapacitást a metrikáinak megjelenítéséhez** nevű legördülő menüt.

A három KPI a kiválasztott prémium szintű kapacitás aktuális állapotát jeleníti meg a három KPI mindegyikére alkalmazott beállítások alapján. 

Ha meg szeretné tekinteni az egyes KPI-k részleteit, válassza az egyes KPI-vizualizációk alján található **Böngészés** gombot, és ekkor megjelenik annak Részletek lapja. A következő szakaszok az egyes KPI-ket és a lapjukon elérhető adatokat ismertetik.

## <a name="the-active-memory-metric"></a>Az aktív memória metrika

Az **aktív memória** metrikája a *kapacitástervezési* kategóriába tartozik, amely egy kiváló állapotjelző a kapacitás erőforrás-felhasználásának kiértékeléséhez, mely alapján szükség szerint módosíthatja a kapacitást a kapacitás méretezésének megtervezéséhez. 

![Az aktív memória KPI](media/service-premium-metrics-app/premium-metrics-app-02.png)

Az **aktív memória** az a memória, amely a jelenleg használatban lévő adathalmazok feldolgozásához van használva, és így nem lesz kiürítve, ha szükség van a memóriára. Az aktív memória metrika azt jelzi, hogy a kapacitás képes-e további terhelést kezelni, vagy már az aktuális terhelése mellett is közelít a befogadóképességéhez, vagy túllépte azt. A jelenleg használatban lévő aktív memória azt jelenti, hogy a további frissítések és lekérdezések támogatásához kevesebb memória áll rendelkezésre. 

Az **aktív memória** KPI azt méri, hogy a kapacitás aktív memóriája hány alkalommal lépte át a 70%-os küszöbértéket 50-szer (a jelölő az elmúlt hét nap 30%-ára van beállítva), ami azt jelzi, hogy a kapacitás közeledik ahhoz a ponthoz, amelyen a felhasználók a lekérdezések teljesítményével kapcsolatos problémákat kezdhetnek észlelni.

A jelen szakaszban bemutatott kijelző vizualizáció azt mutatja, hogy a jelentés legutóbbi frissítése óta eltelt hét nap során a kapacitás négyszer érte el a 70%-os küszöbértéket, óránkénti gyűjtőkre osztva. A kijelző maximális értéke, a 168 az elmúlt hét napot jelöli, órában megadva.

Az aktív memória KPI részleteinek megismeréséhez kattintson a **Böngészés** gombra; ekkor megjelenik egy jelentéslap, amelyen a részletes metrikáinak konkrét vizualizációi, illetve a lap jobb oldali oszlopában egy hibaelhárítási útmutató látható. 

Két forgatókönyv van ismertetve, amelyek megjeleníthetők a jelentés lapon az **1. forgatókönyv** vagy a **2. forgatókönyv** lehetőségre kattintva a lapon. 

![Az aktív memória Részletek lapja](media/service-premium-metrics-app/premium-metrics-app-03.png)

Az egyes forgatókönyvekhez tartozó hibaelhárítási útmutatók részletes magyarázatot nyújtanak arról, hogy mit jelentenek a metrikák, így jobban átláthatja a kapacitás állapotát, és azt, hogy mit tehet az esetleges problémák megoldása érdekében. 

A következő szakaszokban ez a két forgatókönyv van leírva.

### <a name="scenario-one---current-load-is-too-high"></a>Első forgatókönyv – túl magas az aktuális terhelés 

Annak megállapításához, hogy a kapacitásnak van-e elegendő memóriája ahhoz, hogy elvégezze számítási feladatait, tekintse meg az oldalon szereplő első vizualizációt: **A: A felhasznált memória százalékos arányai**, amely azt a memóriát jeleníti meg, amelyet az aktív feldolgozás alatt álló adathalmazok használnak, ezért nem üríthető ki.

A riasztási küszöbérték – a piros pontozott vonal – a 90%-os memória-használatú incidenseket jelöli.

A figyelmeztetési küszöbérték – a sárga pontozott vonal – a 70%-os memória-használatú incidenseket jelöli. 

A fekete pontozott vonal a memória-használat trendvonalát jelöli az aktuális kapacitás a diagram idővonalán való memóriahasználata alapján.

A riasztási küszöbérték feletti aktív memória gyakori előfordulása (a piros pontozott vonal) és a memória trendvonala (a fekete pontozott vonal) jelzi a memóriakapacitás-igényt, ami megakadályozhatja a további adathalmazok memóriába való betöltését ebben az időszakban. 

Ha ilyen esetek fordulnak elő, alaposan meg kell vizsgálnia a lapon található további diagramokat, hogy jobban meg tudja határozni, hogy mi és miért használ ilyen sok memóriát ilyen gyakran, és hogy miként lehet terheléselosztást vagy optimalizálást végezni, vagy ha szükséges, vertikálisan felskálázni a kapacitást. 

Az oldalon szereplő második vizualizáció, **a B: Az óránként betöltött aktív adathalmazok** azt jeleníti meg óránkénti gyűjtőkben, hogy mennyi volt a memóriába betöltött adathalmazok maximális száma. 

A harmadik vizualizáció, **a C: A Miért vannak az adathalmazok a memóriában** egy olyan táblázat, amelyben a munkaterület neve, az adathalmaz neve, az adathalmazok nem tömörített memóriabeli mérete alapján vannak listázva az adathalmazok, és szerepel a memóriába való betöltésének oka (például frissítés, lekérdezés vagy mindkettő).

#### <a name="diagnosing-scenario-one"></a>Az első forgatókönyv diagnosztizálása

Ha az aktív memóriahasználat folyamatosan magas, az aktívan használt adathalmazok kiürítésének kényszerítését eredményezheti, vagy megakadályozhatja, hogy be lehessen tölteni új adathalmazokat. A következő lépések segíthetnek a problémák diagnosztizálásában

1. Tekintse meg az *A: A felhasznált memória százalékos arányai* diagramot

    **a.** Ha az A diagramon az látható, hogy a kapacitás sok alkalommal és/vagy több óráig folyamatosan átlépi a riasztási küszöbértéket (90%), akkor az túl gyakran fogy ki a memóriából. Az alábbi diagramon az látható, hogy a kapacitás négy alkalommal lépte át a figyelmeztetési küszöbértéket (70%).

    ![A diagram – A felhasznált memória százalékos arányai](media/service-premium-metrics-app/premium-metrics-app-04.png)

    **b.** A *B: Az óránként betöltött aktív adatkészletek* nevű diagram azt jeleníti meg óránkénti gyűjtőkben, hogy mennyi volt a memóriába betöltött adathalmazok maximális száma. Ha kiválaszt egy sávot a vizualizációban, a rendszer keresztszűrést végez a vizualizációban, amely azokat az okokat jeleníti meg, amelyek miatt az adathalmazok a memóriában vannak.  

    ![B diagram – A felhasznált memória óránként](media/service-premium-metrics-app/premium-metrics-app-05.png)     

    **c.** A **Miért vannak az adathalmazok a memóriában** táblázatban találhatja meg a memóriába betöltött adathalmazok listáját. Rendezzen az *Adathalmaz mérete (MB)* szerint, hogy kiemelje a legtöbb memóriát felhasználó adathalmazokat. A kapacitásbeli műveletek besorolása lehet *interaktív* vagy *háttérbeli*. Az interaktív műveletekhez tartoznak a képmegjelenítési kérések és a felhasználói beavatkozásra való reagálás (szűrés, Q&A-lekérdezés és egyebek). Az összes lekérdezés és az összes frissítés támpontot biztosít arra vonatkozóan, hogy vannak-e az adathalmazon végrehajtott intenzív interaktív (lekérdezési) vagy háttérbeli (frissítési) műveletek. Fontos tisztában lenni azzal, hogy az interaktív műveletek mindig elsőbbséget élveznek a háttérbeliekkel szemben, hogy a lehető legjobb felhasználói élményt nyújtsák. Ha nem áll rendelkezésre elégséges erőforrás, akkor a rendszer hozzáadja a háttérbeli műveleteket egy várakozási sorhoz, és csak azután dolgozza fel azokat, hogy erőforrások szabadulnak fel. Az olyan háttérbeli műveleteket, mint például az adathalmazok frissítése és az AI-függvények, a Power BI szolgáltatás menet közben is megállíthatja, és várakozási sorhoz adhatja.
    
    ![C táblázat – Adathalmazok listája](media/service-premium-metrics-app/premium-metrics-app-06.png)  

#### <a name="remedies-for-scenario-one"></a>Az első forgatókönyv megoldásai

Az alábbi lépésekkel oldhatja meg az első forgatókönyvhöz kapcsolódó problémákat:

1. **A kapacitás horizontális felskálázása** – a kapacitás a következő SKU-ra való horizontális felskálázása a jelenlegi SKU-hoz képest kétszeres mennyiségű memóriát tesz elérhetővé, így enyhítve a jelenleg a memóriára nehezedő terhelést.

2. **Adathalmazok áthelyezése egy másik kapacitásba** – ha rendelkezik olyan másik kapacitással, amelyben több memória áll rendelkezésre, a nagyobb adathalmazokat tartalmazó munkaterületeket áthelyezheti abba a kapacitásba.


### <a name="scenario-two---future-load-will-exceed-limits"></a>Második forgatókönyv – a jövőbeli terhelés túl fogja lépni a határértékeket

Annak megállapításához, hogy a kapacitásnak van-e elegendő memóriája ahhoz, hogy elvégezze számítási feladatait, tekintse meg az oldalon szereplő **A: A felhasznált memória százalékos arányai** nevű vizualizációt a lap tetején, amely azt a memóriát jeleníti meg, amelyet az aktív feldolgozás alatt álló adathalmazok használnak, ezért nem üríthető ki. A fekete pontozott vonal emeli ki a trendeket. Memóriaterhelés alatt álló kapacitásokban ugyanez a vizualizáció egyértelműen megjeleníti a memória növekvő trendvonalát (a fekete pontozott vonalat), ami azt jelenti, hogy ez megakadályozhatja a további adathalmazok memóriába való betöltését az adott időpontban. A trendvonal, a fekete szaggatott vonal mutatja a növekedés trendjét a hét napnyi adat alapján. 

![Az aktív memória Részletek lapja](media/service-premium-metrics-app/premium-metrics-app-07.png)

#### <a name="diagnosing-scenario-two"></a>A második forgatókönyv diagnosztizálása

A második forgatókönyv diagnosztizálásához azt kell meghatározni, hogy a trendvonal növekvő, a figyelmeztetési vagy a riasztási küszöbérték felé tartó trendet mutat-e. 

1. Tekintsük az **A:**

    ![A felhasznált memória grafikonja diagramot](media/service-premium-metrics-app/premium-metrics-app-08.png)

    **a.** Ha a diagram növekedést mutat, ez azt jelzi, hogy az elmúlt hét napban nőtt a memóriahasználat.

    **b.** A jelenlegi növekedést feltételezve jelezzük előre, hogy a trendvonal mikor fogja átlépni a figyelmeztetési küszöbértéket (a sárga szaggatott vonalat).

    **c.** Folyamatosan ellenőrizze a trendvonalat, legalább kétnaponta, hogy lássa, folytatódik-e a trend.

#### <a name="remedies-for-scenario-two"></a>A második forgatókönyv megoldásai

Az alábbi lépésekkel oldhatja meg a második forgatókönyvhöz kapcsolódó problémákat:

1. **A kapacitás horizontális felskálázása** – a kapacitás a következő SKU-ra való horizontális felskálázása a jelenlegi SKU-hoz képest kétszeres mennyiségű memóriát tesz elérhetővé, így enyhítve a jelenleg a kapacitásra nehezedő terhelést.

2. **Adathalmazok áthelyezése egy másik kapacitásba** – ha rendelkezik olyan másik kapacitással, amelyben több memória áll rendelkezésre, a nagyobb adathalmazokat tartalmazó munkaterületeket áthelyezheti abba a kapacitásba.


## <a name="the-query-waits-metric"></a>A lekérdezés várakozások metrika

A **Lekérdezések** kategóriája azt jelzi, hogy a felhasználók találkozhatnak-e olyan jelentés-vizualizációkkal, amelyek lassan, vagy egyáltalán nem válaszolnak. A **Lekérdezési várakozások** azt adja meg, hogy mennyi időbe kerül elindítani egy lekérdezés végrehajtását az aktiválásától számítva. Ez a KPI azt méri, hogy a kiválasztott kapacitás lekérdezéseinek legalább 25%-a 100 ezredmásodpercet vagy többet várakozik-e. Akkor fordulnak elő lekérdezési várakozások, ha nem áll rendelkezésre elegendő CPU-kapacitás az összes függőben lévő lekérdezés végrehajtásához. 

![A lekérdezés várakozások kijelző](media/service-premium-metrics-app/premium-metrics-app-09.png)

Az ebben a vizualizációban szereplő kijelzőn az látható, hogy a jelentés legutóbbi frissítésétől számított utolsó hét nap során a lekérdezések 17,32%-a várt többet 100 ezredmásodpercnél. 

Ha szeretné megtudni a Lekérdezési várakozások KPI részleteit, kattintson a **Böngészés** gombra; ekkor megjelenik egy jelentéslap, amelyen a kapcsolódó metrikák vizualizációi, illetve a lap jobb oldalán egy hibaelhárítási útmutató látható. A hibaelhárítási útmutató két forgatókönyvet tartalmaz, és mindkettő részletes magyarázatot nyújt a metrikáról, a kapacitás állapotáról, valamint arról, hogy mit tehet a probléma megoldása érdekében.

Az egyes lekérdezési várakozási forgatókönyveket a következő szakaszok tárgyalják egymás után.

### <a name="scenario-one---long-running-queries-consume-cpu"></a>Első forgatókönyv – hosszú ideig futó lekérdezések használják a CPU-t

Az első forgatókönyvben a hosszú ideig futó lekérdezések túl sok CPU-kapacitást használnak fel. 

Megvizsgálhatja, hogy a jelentések gyenge teljesítményét egy túlterhelt kapacitás okozza-e, vagy egy rosszul tervezett adathalmaz vagy jelentés. Több oka is lehet annak, hogy egy lekérdezés huzamosabb ideig fut, ami alatt azt értjük, hogy a végrehajtás befejezése több mint 10 másodpercet vesz igénybe. Az adathalmaz mérete és összetettsége, valamint a lekérdezés bonyolultsága csupán néhány példa arra, hogy mi okozhat hosszú ideig futó lekérdezéseket. 

A következő vizualizációk jelennek meg a jelentéslapon: 

* A felső, **A: Hosszú várakozási idők** című táblázatban a várakozó lekérdezésekkel rendelkező adathalmazok vannak felsorolva. 
* A **B: A hosszú várakozási idők óránkénti eloszlásai** című diagramon a hosszú várakozási idők eloszlása látható. 
* A **C: A hosszú lekérdezések száma óránként** című diagram a végrehajtott hosszú ideig futó lekérdezések számát jeleníti meg, óránkénti gyűjtőkre osztva.
* Az utolsó vizualizáció, a **D: Hosszú ideig futó lekérdezések** című táblázatban a hosszú ideig futó lekérdezések és azok statisztikái vannak listázva.

![A lekérdezési várakozások Részletek lapja](media/service-premium-metrics-app/premium-metrics-app-10.png)

A következő szakaszban ismertetett lépésekkel diagnosztizálhatja és megoldhatja a lekérdezések várakozási idejével kapcsolatos problémákat.

#### <a name="diagnosing-scenario-one"></a>Az első forgatókönyv diagnosztizálása

Először is megállapíthatja, hogy folyamatban vannak-e hosszú ideig futó lekérdezések, amikor a lekérdezések várakoznak. 

![A hosszú várakozási idők táblázata](media/service-premium-metrics-app/premium-metrics-app-11.png)

Tekintse meg a **B diagramot**, amelyen a 100 ms-nál többet várakozó lekérdezések száma látható. Válasszon ki egy olyan oszlopot, amelyben nagy mennyiségű várakozás jelenik meg.

![A hosszú várakozási idők eloszlása](media/service-premium-metrics-app/premium-metrics-app-12.png)

Ha egy hosszú várakozási időt tartalmazó oszlopra kattint, a rendszer úgy szűri a **C diagramot**, hogy az adott időszakban végrehajtott, hosszú ideig futó lekérdezések számát jelenítse meg, az alábbi képen látható módon:

![A hosszú lekérdezések száma óránként](media/service-premium-metrics-app/premium-metrics-app-13.png)

Emellett a rendszer a **D diagramot** is szűri, úgy, hogy azok a lekérdezések jelenjenek meg, amelyek a kiválasztott időszakban futottak hosszú ideig.

![Hosszú ideig futó lekérdezések](media/service-premium-metrics-app/premium-metrics-app-14.png)

#### <a name="remedies-for-scenario-one"></a>Az első forgatókönyv megoldásai

Az alábbi lépésekkel oldhatja meg az első forgatókönyv problémáit:

1. **A PerfAnalyzer futtatása a jelentések és az adathalmazok optimalizálásához** – a jelentések teljesítményelemzője egy lapon megjeleníti minden egyes interakció hatását, beleértve azt is, hogy mennyi időt vesz igénybe az egyes vizualizációk frissítése, és hogy a rendszer hol tölti az időt.

2. **A kapacitás vertikális felskálázása** – a kapacitás a következő SKU-ra való horizontális felskálázása a jelenlegi SKU-hoz képest kétszeres mennyiségű CPU-kapacitást tesz elérhetővé, így enyhítve a jelenleg a CPU-ra nehezedő terhelést, amely miatt a lekérdezések hosszabb ideig futnak.

3. **Adathalmazok áthelyezése egy másik kapacitásba** – ha rendelkezik olyan másik kapacitással, amelyben több CPU-kapacitás áll rendelkezésre, azokat a munkaterületeket, amelyek a várakozó lekérdezésekkel rendelkező adathalmazokat tartalmazzák, áthelyezheti a másik kapacitásba.

### <a name="scenario-two---too-many-queries"></a>Második forgatókönyv – túl sok lekérdezés

A második forgatókönyvben túl sok lekérdezés végrehajtása van folyamatban.

Ha a végrehajtandó lekérdezések száma meghaladja a kapacitás korlátait, a rendszer várólistába helyezi a lekérdezéseket, amíg nem állnak rendelkezésre erőforrások a végrehajtásukhoz. Ha a várólista mérete túl nagyra nő, előfordulhat, hogy a várólistán lévő lekérdezések végül több mint 100 ezredmásodpercet várakoznak.

![Második forgatókönyv](media/service-premium-metrics-app/premium-metrics-app-15.png)


#### <a name="diagnosing-scenario-two"></a>A második forgatókönyv diagnosztizálása

Az **A táblázatban** válasszon ki egy olyan adathalmazt, amelynek hosszú a várakozási ideje.

![a hosszú várakozási idők táblázata](media/service-premium-metrics-app/premium-metrics-app-16.png)

Miután kiválasztott egy hosszú várakozási idejű adathalmazt, a rendszer úgy szűri a **B diagramot**, hogy azon az adott adathalmazon végzett lekérdezések várakozási idejének elmúlt hét napi eloszlása jelenjen meg. Ezután válassza ki a **B diagram** egyik oszlopát.

![a hosszú várakozási idők óránkénti eloszlásának diagramja](media/service-premium-metrics-app/premium-metrics-app-17.png)

Ezután a rendszer úgy szűri a**C diagramot**, hogy azon a várólista a B diagramon kiválasztott időpontbeli hossza jelenjen meg.

![a lekérdezések várólistájának hossza óránként](media/service-premium-metrics-app/premium-metrics-app-18.png)

Ha a várólista hossza túllépte a 20-as küszöbértéket, akkor valószínű, hogy a kijelölt adathalmazban lévő lekérdezések késnek, mert a rendszer túl sok lekérdezést próbál végrehajtani egyszerre.

![A végrehajtás alatt álló lekérdezések táblázata](media/service-premium-metrics-app/premium-metrics-app-19.png)

#### <a name="remedies-for-scenario-two"></a>A második forgatókönyv megoldásai

Az alábbi lépésekkel oldhatja meg a második forgatókönyvhöz kapcsolódó problémákat:

1. **A kapacitás horizontális felskálázása** – a kapacitás a következő SKU-ra való horizontális felskálázása a jelenlegi SKU-hoz képest kétszeres mennyiségű memóriát tesz elérhetővé, így enyhítve a jelenleg a kapacitásra nehezedő terhelést.

2. **Adathalmazok áthelyezése egy másik kapacitásba** – ha rendelkezik olyan másik kapacitással, amelyben több memória áll rendelkezésre, a nagyobb adathalmazokat tartalmazó munkaterületeket áthelyezheti abba a kapacitásba.


## <a name="the-refresh-waits-metric"></a>A frissítési várakozások metrika

A **Frissítési várakozások** metrika abba enged betekintést, hogy a felhasználók mikor találkozhatnak régi vagy elavult jelentésadatokkal. A **Frissítési várakozások** azt az időt jelöli, ameddig egy adott adatfrissítés várt a végrehajtás megkezdésére az igény szerinti aktiválás vagy az ütemezett futtatás időpontjától számítva. Ez a KPI azt méri, hogy a függőben lévő frissítési kérelmek 10%-a vagy nagyobb része 10 percig vagy tovább várakozik-e. Általában akkor fordul elő várakozás, ha nincs elegendő szabad memória vagy CPU-kapacitás.

![A frissítési várakozások kijelző](media/service-premium-metrics-app/premium-metrics-app-20.png)

Ez a kijelző azt mutatja, hogy a frissítési jelentés legutóbbi frissítésétől számított utolsó hét nap során a frissítések 3,18%-a várt 10 percnél többet. 

A **Frissítési várakozások** KPI részleteinek megismeréséhez kattintson a **Böngészés** gombra; ekkor megjelenik egy lap, amelyen metrikák, illetve a lap jobb oldali oszlopában egy hibaelhárítási útmutató látható. Az útmutató részletesen ismerteti a lapon található metrikákat, és segít megérteni a kapacitás állapotát, és azt, hogy mit tehet az esetleges problémák megoldása érdekében.

![A frissítési várakozások metrikák böngészése](media/service-premium-metrics-app/premium-metrics-app-21.png)

Két forgatókönyv van ismertetve, amelyek megjeleníthetők a jelentés lapon az 1. forgatókönyv vagy a 2. forgatókönyv lehetőségre kattintva a lapon. Az egyes forgatókönyveket a következő szakaszok tárgyalják egymás után.

### <a name="scenario-one---not-enough-memory"></a>Első forgatókönyv – nincs elegendő memória

Az első forgatókönyvben nincs elegendő szabad memória az adathalmaz betöltéséhez. A rendszer két szituáció miatt szabályozhat frissítéseket, amikor nincs elég memória:

1. Nincs elég memória az adathalmaz betöltéséhez.
2. A frissítés egy magasabb prioritású művelet miatt megszakadt. 

Az adathalmazok betöltésének prioritása a következő:

1. Interaktív lekérdezés
2. Igény szerinti frissítés
3. Ütemezett frissítés

Ha nincs elegendő memória egy interaktív lekérdezés adathalmazának betöltéséhez, a rendszer leállítja az ütemezett frissítéseket, és eltávolítja azok adathalmazait a memóriából, amíg nem áll rendelkezésre elegendő memória. Ha így nem szabadul fel elegendő memória, a rendszer leállítja az igény szerinti frissítéseket, és eltávolítja azok adathalmazait a memóriából.

#### <a name="diagnosing-scenario-one"></a>Az első forgatókönyv diagnosztizálása

Az első forgatókönyv diagnosztizálásához először határozza meg, hogy a szabályozást az okozza-e, hogy nincs elegendő memória. A következő beállításokat kell elvégeznie.

1.    Rákattintással válassza ki a kívánt adathalmazt az **A táblázatban**: 

    ![A táblázat](media/service-premium-metrics-app/premium-metrics-app-22.png)

    a. Amikor kiválaszt egy adathalmazt az **A táblázatban**, a rendszer úgy szűri a **B diagramot**, hogy azon megjelenjen, hogy mikor történt várakozás.

    ![B diagram](media/service-premium-metrics-app/premium-metrics-app-23.png)

    b. A rendszer ezután úgy szűri a **C diagramot**, hogy azon az esetleges szabályozások jelenjenek meg; ennek magyarázata a következő lépésben olvasható. 

2. Tekintse meg a most már szűrt **C diagramon** szereplő eredményeket. Ha a diagramon az látható, hogy memóriaszabályozás történt azokban az esetekben, amikor az adathalmaz várakozott, az adathalmaz azért várakozott, mert nem volt elegendő memória.

    ![C diagram](media/service-premium-metrics-app/premium-metrics-app-24.png)

3. Végül tekintse meg a **D diagramot**, amelyen a végrehajtott frissítések típusai – ütemezett és igény szerinti – jelennek meg. A szabályozást okozhatta az, hogy egyszerre történtek igény szerinti frissítések.

    ![D diagram](media/service-premium-metrics-app/premium-metrics-app-25.png)


#### <a name="remedies-for-scenario-one"></a>Az első forgatókönyv megoldásai

Az alábbi lépésekkel oldhatja meg az első forgatókönyvhöz kapcsolódó problémákat:

1. **A kapacitás horizontális felskálázása** – a kapacitás a következő SKU-ra való horizontális felskálázása a jelenlegi SKU-hoz képest kétszeres mennyiségű memóriát tesz elérhetővé, így enyhítve a kapacitás memóriájára és CPU-kapacitására jelenleg nehezedő terhelést.

2. **Adathalmazok áthelyezése egy másik kapacitásba** – ha a várakozási időket memóriaterhelés okozza, és rendelkezik olyan másik kapacitással, amelyben több memória áll rendelkezésre, azokat a munkaterületeket, amelyek a várakozó adathalmazokat tartalmazzák, áthelyezheti a másik kapacitásba.

3. **Az ütemezett frissítések elosztása** – a frissítések elosztása segít elkerülni, hogy a rendszer egyszerre túl sok frissítést próbáljon meg végrehajtani.



### <a name="scenario-two---not-enough-cpu-for-refresh"></a>Második forgatókönyv – nincs elegendő CPU-kapacitás a frissítéshez

A második forgatókönyvben nincs elég rendelkezésre álló CPU-kapacitás a frissítés végrehajtásához. 

Dedikált kapacitások esetében a Power BI korlátozza az egyidejűleg végrehajtható frissítések számát. Ezen szám értéke háttérbeli magok száma x 1,5. Egy olyan P1 szintű dedikált kapacitás például, amelynek négy háttérbeli magja van, egyszerre 6 frissítést képes futtatni. Amint a kapacitás eléri az egyidejű frissítések maximális számát, a többi frissítés várakozik, amíg egy végrehajtás alatt álló frissítés be nem fejeződik.

![Második frissítési forgatókönyv](media/service-premium-metrics-app/premium-metrics-app-26.png)

#### <a name="diagnosing-scenario-two"></a>A második forgatókönyv diagnosztizálása

A második forgatókönyv diagnosztizálásához először határozza meg, hogy a szabályozást az okozza-e, hogy a rendszer elérte a párhuzamos frissítések maximális számát. A következő beállításokat kell elvégeznie.

1.    Rákattintással válassza ki a kívánt adathalmazt az **A táblázatban**: 

    ![A táblázat](media/service-premium-metrics-app/premium-metrics-app-22.png)

    a. Amikor kiválaszt egy adathalmazt az **A táblázatban**, a rendszer úgy szűri a **B diagramot**, hogy azon megjelenjen, hogy mikor történt várakozás.

    ![B diagram](media/service-premium-metrics-app/premium-metrics-app-23.png)

    b. A rendszer ezután úgy szűri a **C diagramot**, hogy azon az esetleges szabályozások jelenjenek meg; ennek magyarázata a következő lépésben olvasható. 

2. Tekintse meg a most már szűrt **C diagramon** szereplő eredményeket. Ha a diagramon az látható, hogy *maximális párhuzamosság* következett be azokban az esetekben, amikor az adathalmaz várakozott, az adathalmaz azért várakozott, mert nem állt rendelkezésre elegendő CPU-kapacitás.

    ![C diagram](media/service-premium-metrics-app/premium-metrics-app-24.png)

3. Végül tekintse meg a **D diagramot**, amelyen a végrehajtott frissítések típusai – ütemezett és igény szerinti – jelennek meg. A szabályozást okozhatta az, hogy egyszerre történtek igény szerinti frissítések.

    ![D diagram](media/service-premium-metrics-app/premium-metrics-app-25.png)


#### <a name="remedies-for-scenario-two"></a>A második forgatókönyv megoldásai

1. **A kapacitás horizontális felskálázása** – a kapacitás a következő SKU-ra való horizontális felskálázása a jelenlegi SKU-hoz képest kétszeres mennyiségű memóriát és kétszer annyi párhuzamos frissítést tesz elérhetővé, így enyhítve a kapacitás memóriájára és CPU-kapacitására jelenleg nehezedő terhelést.

2. **Adathalmazok áthelyezése egy másik kapacitásba** – ha a várakozási időket az okozza, hogy a rendszer elérte a maximális párhuzamosságot, és rendelkezik olyan másik kapacitással, amelyben van rendelkezésre álló párhuzamosság, azokat a munkaterületeket, amelyek a várakozó adathalmazokat tartalmazzák, áthelyezheti a másik kapacitásba.

3. **Az ütemezett frissítések elosztása** – a frissítések elosztása segít elkerülni, hogy a rendszer egyszerre túl sok frissítést próbáljon meg végrehajtani.



## <a name="next-steps"></a>Következő lépések

* [Mi a Power BI Premium?](service-premium-what-is.md)
* [A Power BI Premium kibocsátási megjegyzései](service-premium-release-notes.md)
* [Microsoft Power BI Premium-tanulmány](https://aka.ms/pbipremiumwhitepaper)
* [A Power BI Enterprise üzembehelyezési előkészületeit bemutató tanulmány ](https://aka.ms/pbienterprisedeploy)
* [A Pro meghosszabbított próbaverziójának aktiválása](service-extended-pro-trial.md)
* [Power BI Embedded GYIK](developer/embedded/embedded-faq.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)