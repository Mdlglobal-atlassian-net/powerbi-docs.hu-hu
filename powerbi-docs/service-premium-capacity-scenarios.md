---
title: A prémium szintű Microsoft Power BI-kapacitásokkal kapcsolatos forgatókönyvek
description: A cikk a prémium szintű Power BI-kapacitásokkal kapcsolatos gyakori forgatókönyveket ismerteti.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/09/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 9b3e06172d29f218f9234cf1f3d7e1f623495001
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "74697267"
---
# <a name="premium-capacity-scenarios"></a>Prémium szintű kapacitások forgatókönyvei

Ez a cikk olyan valós forgatókönyveket ismertet, amelyekben prémium szintű Power BI-kapacitások lettek implementálva. Bemutatja a gyakori problémákat és kihívásokat, a problémák azonosításának módját, és segítséget nyújt az elhárításukhoz:

- [Az adathalmazok naprakészen tartása](#keeping-datasets-up-to-date)
- [A lassan válaszoló adathalmazok azonosítása](#identifying-slow-responding-datasets)
- [Az adathalmazok időnként lassú válaszát kiváltó okok azonosítása](#identifying-causes-for-sporadically-slow-responding-datasets)
- [Annak meghatározása, hogy van-e elég memória](#determining-whether-there-is-enough-memory)
- [Annak meghatározása, hogy van-e elég processzorkapacitás](#determining-whether-there-is-enough-cpu)

A lépések a diagramok és táblázatok példáival együtt a **Power BI Premium Capacity Metrics alkalmazásból** származnak, amelyhez a Power BI-rendszergazdák hozzáféréssel rendelkeznek.

## <a name="keeping-datasets-up-to-date"></a>Az adathalmazok naprakészen tartása

Ebben a forgatókönyvben vizsgálat indult, mert a felhasználók arra panaszkodtak, hogy a jelentésadatok néha réginek vagy „elavultnak” tűntek.

Az alkalmazásban a rendszergazda a **Frissítések** vizualizációval rendezi az adathalmazokat a **Maximális várakozási idő** statisztika szerint csökkenő sorrendben. Ez a vizualizáció segítséget nyújt a rendszergazdának a leghosszabb várakozási idővel rendelkező adathalmazok megjelenítésére, a munkaterület neve szerint csoportosítva.

![Adathalmaz-frissítések a maximális várakozási idő szerint csökkenő sorrendbe rendezve, munkaterület szerint csoportosítva](media/service-premium-capacity-scenarios/dataset-refreshes.png)

Az **Átlagos frissítési várakozási idő óránként** vizualizációban a rendszergazda felfigyel arra, hogy a frissítések várakozási ideje rendszeresen mindennap 16 óra körül tetőzik.

![A frissítések várakozási ideje 16 órakor rendszeresen tetőzik](media/service-premium-capacity-scenarios/peak-refresh-waits.png)

Számos lehetséges magyarázat van ezekre az eredményekre:

- Előfordulhat, hogy túl sok frissítési kísérlet történik egyszerre, túllépve a kapacitás-csomópont által meghatározott korlátokat. Ebben az esetben hat egyidejű frissítés történik az alapértelmezett memóriafoglalással rendelkező P1-en.

- A frissíteni kívánt adathalmazok túl nagyok lehetnek a rendelkezésre álló memóriához képest (teljes frissítés esetén az adathalmaz méreténél kétszer több memóriára van szükség).
- A nem hatékony Power Query-logika a memóriahasználat megugrásával járhat az adathalmazok frissítése során. Gyakran használt kapacitáson ez a megugrás alkalmanként elérheti a fizikai korlátot, ami a frissítés sikertelenségével jár, és a kapacitás más jelentésmegtekintési műveleteire is hatással lehet.
- Az azon adathalmazokra irányuló lekérdezések, amelyeknek a memóriában kell maradniuk, hatással lehetnek más adathalmazok frissítésére a korlátozottan rendelkezésre álló memória miatt.

A kivizsgálást segítendő a Power BI-rendszergazda a következőknek nézhet utána:

- Kevés rendelkezésre álló memória az adatok frissítésekor, ha a rendelkezésre álló memória kisebb a frissítendő adathalmaz méretének kétszeresénél.
- Nem frissített, és a frissítés előtt a memóriában nem jelen lévő adathalmazok, amelyek mégis interaktív forgalmat kezdenek mutatni a sok frissítéssel járó időtartamok során. Annak megtekintéséhez, hogy mely adathalmazokat tölti be a rendszer a memóriába egy adott időpontban, a Power BI-rendszergazda az alkalmazás **Adatkészletek** lapjának adathalmazokat tartalmazó területén vizsgálódhat. A rendszergazda ezután keresztszűrést hajthat végre egy adott időpontra az **Óránként betöltött adatkészletek száma** valamelyik oszlopára kattintva. Az alábbi képen látható helyi megugrás jelzi azt az órát, amikor a rendszer több adathalmazt töltött be a memóriába, ami késleltetheti az ütemezett frissítések elkezdését.
- Nagyobb számban történik adathalmaz-kizárás az adatfrissítés ütemezett kezdési időpontjában. A kizárások azt jelezhetik, hogy a memóriát nagy terhelés érte, amit a túl sok különböző interaktív jelentés kiszolgálása okozott a frissítés időpontja előtt. Az **Adathalmaz-kizárások és memóriahasználat óránként** vizualizáció világosan jelezheti a kizárások megugrásait.

Az alábbi képen egy helyi megugrás látható a betöltött adathalmazokban, ami arra utal, hogy az interaktív lekérdezés késleltette a frissítések elkezdését. Ha kiválaszt egy időszakot az **Óránként betöltött adatkészletek száma** vizualizációban, azzal keresztszűrhet az **Adathalmazméretek** vizualizációra.

![Egy helyi megugrás a betöltött adathalmazokban arra utal, hogy az interaktív lekérdezés késleltette a frissítések elkezdését](media/service-premium-capacity-scenarios/hourly-loaded-dataset-counts.png)

A Power BI-rendszergazda megkísérelheti elhárítani a problémát olyan lépések megtételével, amelyekkel biztosíthatja, hogy elegendő memória álljon rendelkezésre az adatfrissítések elkezdéséhez. Ehhez a következőket teheti:

- Felveheti a kapcsolatot az adathalmazok tulajdonosaival, és megkérheti őket, hogy tolják el és időben egyenletesen osszák el az adatfrissítések ütemezését.
- Csökkentheti az adathalmaz-lekérdezésekkel járó terhelést a felesleges irányítópultok vagy irányítópult-csempék eltávolításával, különös tekintettel azokra, amelyek sorszintű biztonságot érvényesítenek.
- Felgyorsíthatja az adatfrissítéseket a Power Query-logika optimalizálásával. Javíthatja a számított oszlopok vagy táblázatok modellezését. Csökkentheti az adathalmazok méretét, vagy konfigurálhatja úgy a nagyobb adathalmazokat, hogy növekményes adatfrissítést hajtsanak végre.

## <a name="identifying-slow-responding-datasets"></a>A lassan válaszoló adathalmazok azonosítása

Ebben a forgatókönyvben vizsgálat kezdődött, mert a felhasználók arra panaszkodtak, hogy bizonyos jelentések megnyitása túl sok időt vesz igénybe, és olykor le is fagynak.

A Power BI-rendszergazda az alkalmazás **Lekérdezések időtartama** vizualizációjával határozhatja meg a legrosszabbul teljesítő adathalmazokat, az adathalmazok **Átlagos időtartam** szerint csökkenő sorrendbe rendezésével. Ez a vizualizáció az adathalmaz-lekérdezések számát is megjeleníti, így láthatja, hogy milyen gyakran kérdezték le az adathalmazokat.

![Legrosszabbul teljesítő adathalmazok](media/service-premium-capacity-scenarios/worst-performing-datasets.png)

A rendszergazda a **Lekérdezések időtartamának eloszlása** vizualizációban tekintheti meg az időkategóriákra osztott lekérdezési teljesítmény (<= 30 ezredmásodperc, 0–100 ezredmásodperc) általános eloszlását a szűrt időszakra vonatkozóan. Az egy másodpercig vagy rövidebb ideig tartó lekérdezéseket a felhasználók többsége általában gyorsnak tartja, a hosszabb ideig tartó lekérdezések azonban inkább rossz teljesítmény érzetét keltik.

A **Lekérdezések időtartamának eloszlása óránként** vizualizáció lehetővé teszi a Power BI-rendszergazdának azoknak az egyórás időszakoknak az azonosítását, amikor a kapacitásteljesítmény rossznak tekinthető. Minél nagyobbak az egy másodpercet meghaladó lekérdezési időtartamokat képviselő oszlopszegmensek, annál nagyobb annak a veszélye, hogy a felhasználók rossz teljesítményt tapasztalnak.

A vizualizáció interaktív, az oszlop egyik szegmensére kattintva a rendszer keresztszűrést hajt végre a jelentésoldalon található megfelelő **Lekérdezések időtartama** táblavizualizációra az oszlop által képviselt adathalmazok megjelenítéséhez. A keresztszűrés lehetővé teszi a Power BI-rendszergazdának a lassan válaszoló adathalmazok egyszerű azonosítását.

Az alábbi képen a **Lekérdezések időtartamának eloszlása óránként** szerint szűrt vizualizáció látható, amely a legrosszabbul teljesítő adathalmazokra összpontosít az egyórás kategóriában. 

![A legrosszabbul teljesítő adathalmazokat megjelenítő, szűrt Lekérdezések időtartamának eloszlása óránként vizualizáció](media/service-premium-capacity-scenarios/hourly-query-duration-distributions.png)

Az adott egyórás időtartamban rosszul teljesítő adathalmaz azonosítását követően a Power BI-rendszergazda kivizsgálhatja, hogy a rossz teljesítményt túlterhelt kapacitás vagy pedig rosszul megtervezett adathalmaz, illetve jelentés okozza. Ehhez a **Lekérdezésekre való várakozások időtartama** vizualizációt használva csökkenő sorrendbe rendezheti az adathalmazokat a lekérdezések átlagos várakozási ideje szerint. Ha a lekérdezések nagy százalékos arányban várakoznak, valószínűleg az adathalmazhoz kapcsolódó nagy igény okozza a túl sok lekérdezés várakozását. Ha a lekérdezések átlagos várakozási ideje jelentős (több mint 100 ezredmásodperc), érdemes lehet áttekinteni az adathalmazt és a jelentést annak megállapításához, hogy végrehajthatók-e optimalizálások rajtuk. Például: kevesebb vizualizáció a jelentésoldalakon, vagy a DAX-kifejezések optimalizálása.

![A Lekérdezésekre való várakozások időtartama vizualizáció segít megtalálni a rosszul teljesítő adathalmazokat](media/service-premium-capacity-scenarios/query-wait-times.png)

Számos lehetséges oka lehet a lekérdezésekre való várakozási idő növekedésének az adathalmazokban:

- Az optimálistól elmaradó modellterv, mérési kifejezések vagy akár jelentésterv – minden olyan körülmény, amely hozzájárulhat a CPU-t nagy mértékben igénybe vevő, hosszan futó lekérdezésekhez. Ez arra kényszeríti az új lekérdezéseket, hogy várjanak, amíg CPU-szálak válnak elérhetővé, és konvojhatást eredményezhet (mintha forgalmi dugó alakult volna ki), ami gyakori jelenség a csúcsidő során. A **Lekérdezésekre való várakozások** oldal jelenti a fő információforrást annak meghatározására, hogy az adathalmazokra irányuló lekérdezések átlagos várakozási ideje magas-e.
- Az azonos jelentést vagy adathalmazt egyidejűleg használó kapacitásfelhasználók magas száma (több száztól több ezerig). Még a jól megtervezett adathalmazok is teljesíthetnek rosszul az egyidejűségi küszöbértéken túl. Ezt általában az jelzi egy adott adathalmaznál, hogy a lekérdezések számának értéke jelentősen magasabb a többi adathalmazénál (például 300 000 lekérdezés egy adathalmaz esetén a többi adathalmaz kevesebb mint 30 000 lekérdezéséhez képest). Egy adott pontnál az adathalmazhoz kapcsolódó lekérdezések várakozási ideje elkezd ingadozni, ami a **Lekérdezések időtartama** vizualizációban látható.
- Sok különálló adathalmaz lett lekérdezve egyidejűleg, ami akadozást okoz, mivel az adathalmazokat a rendszer gyakran betölti a memóriába, és kiüríti onnan. Ennek eredményeként a felhasználók lassú teljesítményt tapasztalnak az adathalmaz memóriába való betöltésekor. Ennek ellenőrzéséhez a Power BI-rendszergazda az **Adathalmaz-kizárások és memóriahasználat óránként** vizualizációt tekintheti meg, amely jelezheti, hogy a memóriába betöltött nagy számú adathalmazt a rendszer ismételten kizárja.

## <a name="identifying-causes-for-sporadically-slow-responding-datasets"></a>Az adathalmazok időnként lassú válaszát kiváltó okok azonosítása

Ebben a forgatókönyvben vizsgálat indult, mert a felhasználók jelezték, hogy a jelentésvizualizációk néha lassan vagy akár egyáltalán nem válaszolnak, máskor azonban elfogadható a válaszidejük.

Az alkalmazásban a **Lekérdezések időtartama** szakaszt használta a rendszergazda a problémát kiváltó adathalmaz megtalálásához a következő módon:

- A **Lekérdezések időtartama** vizualizációban a rendszergazda az adathalmaz szerint szűrte az adathalmazokat (a legtöbbször lekérdezett adathalmazokkal kezdve), és megvizsgálta a keresztszűrt oszlopokat a **Lekérdezések időtartamának eloszlása óránként** vizualizációban.
- Ha egy adott egyórás oszlop jelentős változásokat mutat az összes lekérdezés időtartamcsoportjai és a többi egyórás oszlopok aránya között az adott adathalmaz esetén (például a színek közötti arányok drasztikusan változnak), az azt jelenti, hogy az adathalmaz időnkénti változást mutat a teljesítményben.
- A gyengén teljesítő lekérdezések normálistól eltérő arányát megjelenítő egyórás oszlopok olyan időtartamot jeleznek, amikor az adathalmazt a más adathalmazok tevékenységei által okozott „zajos szomszédok” hatás érte.

Az alábbi képen a január 30-i nap egy órája látható, amikor jelentős visszaesés volt tapasztalható az adathalmaz teljesítményében, amit a „(3,10 mp)” végrehajtásiidőtartam-kategória mérete jelez. Erre az egyórás oszlopra kattintva megjeleníthető az adott időpontban a memóriába betöltött adathalmazok mindegyike, feltárva a „zajos szomszédok” hatást okozó lehetséges adathalmazokat.

![A nagy arányt elérő legrosszabb teljesítményt megjelenítő oszlop](media/service-premium-capacity-scenarios/worst-performing-queries.png)

A problémás időtartam azonosítását követően (például január 30-án a fenti képen), a Power BI-rendszergazda eltávolíthatja az összes adathalmazszűrőt, majd szűrhet csak az adott időtartam szerint annak megállapításához, hogy mely adathalmazokat kérdezték le aktívan az adott időtartamban. A „zajos szomszédok” hatásért felelős adathalmaz általában a legtöbbször lekérdezett adathalmaz, vagy pedig a leghosszabb átlagos lekérdezési időtartammal rendelkező adathalmaz.

A probléma egyik megoldása lehet a bűnös adathalmazok elosztása különböző prémium szintű kapacitásokon található munkaterületekre, vagy egy megosztott kapacitásra, ha az adathalmaz mérete, a használati követelmények és az adatfrissítési minták támogatottak.

Ennek fordítottja is igaz lehet. A Power BI-rendszergazda azonosíthatja azokat az időpontokat, amikor egy adathalmaz lekérdezésének teljesítménye jelentősen javul, majd utánanézhet, hogy mi tűnt el. Ha az adott pontban hiányoznak bizonyos információk, akkor az rámutathat a kiváltó problémára.

## <a name="determining-whether-there-is-enough-memory"></a>Annak meghatározása, hogy van-e elég memória

Annak meghatározásához, hogy a kapacitás rendelkezik-e elegendő memóriával a számítási feladatai végrehajtásához, a Power BI-rendszergazda az alkalmazás **Adatkészletek** lapjának **A felhasznált memória százalékos aránya** vizualizációját használhatja. Az **Összes** (teljes) memória a memóriába betöltött adathalmazok által felhasznált memóriát jeleníti meg, függetlenül attól, hogy az adathalmazokra irányultak-e aktív lekérdezések vagy megtörtént-e a feldolgozásuk. Az **Aktív** memória az aktív feldolgozás alatt álló adathalmazok által felhasznált memóriát jeleníti meg.

Egy megfelelő állapotú kapacitás esetén a vizualizáció az alábbi képen láthatók szerint jelenik meg, eltérést mutatva az Összes (teljes) és az Aktív memória között:

![Egy megfelelő állapotú kapacitás eltérést mutat az Összes (teljes) és az Aktív memória között](media/service-premium-capacity-scenarios/memory-healthy-capacity.png)

Ha a kapacitásban a memóriát nagy terhelés éri, ugyanezen a vizualizáción egyértelműen látható lesz, hogy az aktív memória és a teljes memória közelít egymáshoz, ami azt jelenti, hogy további adathalmazok nem tölthetők be a memóriába ekkor. Ebben az esetben a Power BI-rendszergazda a **Kapacitás újraindítása** elemre kattinthat (a felügyeleti portál kapacitásbeállításokat tartalmazó területének **Speciális beállítások** részén érhető el). A kapacitás újraindítása az adathalmazok memóriából való kiürítésével jár, lehetővé téve a memóriába való ismételt, szükség szerinti betöltésüket (lekérdezésekkel vagy adatfrissítéssel).

![Az egymáshoz közelítő **Aktív** memória és **Összes** memória](media/service-premium-capacity-scenarios/memory-unhealthy-capacity.png)

## <a name="determining-whether-there-is-enough-cpu"></a>Annak meghatározása, hogy van-e elég processzorkapacitás

A kapacitás átlagos processzorhasználatának általában 80% alatt kell maradnia. Ennek az értéknek a túllépése azt jelenti, hogy a kapacitás kezdi megközelíteni a processzortelítettséget.

A processzortelítettség hatása a kellőnél hosszabb ideig tartó műveletekben jelentkezik, amit az okoz, hogy a kapacitás sok CPU-környezetváltást hajt végre, miközben megkísérli a műveletek mindegyikét feldolgozni. A sok egyidejű lekérdezéssel rendelkező prémium szintű kapacitásban ezt a lekérdezések hosszú várakozási ideje jelzi. A lekérdezések hosszú várakozási idejének egyik következménye a szokásosnál lassabb válaszidő. A **Lekérdezésekre való várakozások időtartamának eloszlása óránként** vizualizáció megtekintésével a Power BI-rendszergazda egyszerűen megállapíthatja, hogy a processzor telítve lett-e. A lekérdezések várakozási idejének ismétlődő csúcsai processzortelítettséget jelezhetnek.

![A lekérdezések várakozási idejének ismétlődő csúcsai CPU-túlterhelést jelezhetnek](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

Néha hasonló minta észlelhető a háttérműveletekben is, ha hozzájárulnak a processzor telítettségéhez. A Power BI-rendszergazda megkeresheti az ismétlődő megugrást egy adott adathalmaz frissítési idejében, ami processzortelítettséget jelezhet az adott időpontban (valószínűleg más folyamatban lévő adathalmaz-frissítések és/vagy interaktív lekérdezések miatt). Ebben az esetben az alkalmazás **Rendszer összegzése** nézetének használata nem feltétlenül mutatja ki, hogy a processzorhasználat 100%-os. A **Rendszer összegzése** nézet óránkénti átlagokat jelenít meg, a processzor azonban az erőforrás-igényes műveletek több percére válhat telítetté, ami a várakozási idők megugrásaiban jelentkezik.

A processzortelítettség hatása további finom részletekben is észrevehető. Jóllehet a várakozó lekérdezések száma fontos, a lekérdezések várakozási ideje bizonyos mértékben mindig nagyobb lesz, észrevehető teljesítményromlás nélkül. Egyes adathalmazok (amelyek hosszabb átlagos lekérdezési idővel rendelkeznek, ami összetettséget vagy nagyobb méretet jelez) érzékenyebbek a processzortelítettség hatásaira, mint mások. Ezeket az adathalmazokat úgy azonosíthatja egyszerűen a Power BI-rendszergazda, hogy megtekinti az oszlopok színösszetételének változásait a **Lekérdezésekre való várakozások időtartamának eloszlása óránként** vizualizációban. A többi közül kilógó oszlop azonosítását követően a rendszergazda megkeresheti azokat az adathalmazokat, amelyek lekérdezései várakoztak ezen idő során, és össze is hasonlítja a lekérdezések átlagos várakozási idejét a lekérdezések átlagos időtartamával. Ha ez a két metrika azonos nagyságrendű, és az adathalmazra irányuló lekérdezési számítási feladat nem jelentéktelen, az adathalmazra valószínűleg az elégtelen CPU-kapacitás van hatással.

Ez a hatás különösen akkor lehet nyilvánvaló, ha az adathalmazt több felhasználó nagy gyakoriságú lekérdezések rövid sorozataiban használja (például egy képzés alatt), ami processzortelítettséget eredményezhet az egyes sorozatok során. Ebben az esetben az adathalmazra irányuló lekérdezések várakozási ideje jelentős lesz, illetve mindez hatással lesz a kapacitás más adathalmazaira is (a „zajos szomszédok” hatás).

Egyes esetekben a Power BI-rendszergazdák megkérhetik az adathalmazok tulajdonosait, hogy tartósabb lekérdezési számítási feladatot hozzanak létre egy irányítópult létrehozásával (amely rendszeres időközönként, az adathalmazok frissítésekor kezdeményez lekérdezéseket a gyorsítótárazott csempékre vonatkozóan), jelentések létrehozása helyett. Ez meggátolhatja a megugrásokat az irányítópult betöltésekor. Ez a megoldás nem mindig lehetséges az adott üzleti követelmények miatt, azonban hatásos módja lehet a processzortelítettség elkerülésének az adathalmaz módosítása nélkül.

## <a name="acknowledgements"></a>Nyugták

A cikket Peter Myers, a [Bitwise Solutions](https://www.bitwisesolutions.com.au/) Data Platform MVP-je és független BI-szakértője szerezte.

## <a name="next-steps"></a>További lépések

> [!div class="nextstepaction"]
> [Prémium szintű kapacitások monitorozása az alkalmazással](service-admin-premium-monitor-capacity.md)    
> [!div class="nextstepaction"]
> [Kapacitások monitorozása a felügyeleti portálon](service-admin-premium-monitor-portal.md)   

Több kérdése van? [Kérdezze meg a Power BI-közösséget](https://community.powerbi.com/)

||||||