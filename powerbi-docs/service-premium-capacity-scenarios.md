---
title: A Microsoft Power BI Premium kapacitás-forgatókönyvek
description: A Power BI Premium-kapacitás gyakori forgatókönyveket ismertet.
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
ms.openlocfilehash: 1d666a6702515a935d93549d026f207848f2bca8
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565362"
---
# <a name="premium-capacity-scenarios"></a>Prémium szintű kapacitás forgatókönyvek

Ez a cikk ismerteti a valós életből vett példák, ahol a Power BI prémium szintű kapacitások végrehajtották. Gyakori problémák és kihívásokat ismerteti, is hogyan azonosíthatja a problémákat, és oldhatja meg őket:

- [Az adatkészletek frissítése](#keeping-datasets-up-to-date)
- [Az adatkészletek lassan válaszol azonosítása](#identifying-slow-responding-datasets)
- [Okainak azonosítása vonatkozó szórványosan lassú-adatkészletek](#identifying-causes-for-sporadically-slow-responding-datasets)
- [Meghatározása, hogy van-e elegendő memória](#determining-whether-there-is-enough-memory)
- [Amely meghatározza, hogy van-e elegendő Processzor](#determining-whether-there-is-enough-cpu)

A lépéseket, valamint különböző példákkal diagram és táblázat származnak az **Power BI Premium kapacitás-metrikák alkalmazás** , hogy a Power BI-rendszergazda hozzáférést kap.

## <a name="keeping-datasets-up-to-date"></a>Az adatkészletek frissítése

Ebben a forgatókönyvben vizsgálat lett elindítva, amikor a felhasználók kifogásolt, hogy a jelentés adatokat néha tűnt, régi vagy "elavult".

Az alkalmazásban a rendszergazda kommunikál a **frissíti** vizualizációt, a rendezés adatkészletek a **maximális várakozási idő** statisztika csökkenő sorrendben. Ez a Vizualizáció segít nekik a leghosszabb várakozási időt, a munkaterület neve szerint csoportosítva kellene adatkészletek felfedéséhez.

![Adatkészlet frissítések maximális várakozási idő, munkaterület szerint csoportosítva csökkenő sorrendben rendezve](media/service-premium-capacity-scenarios/dataset-refreshes.png)

Az a **óránkénti átlagos frissítése várakozási idők** vizualizációval, figyelje meg, hogy a frissítés várakozási időt kiugró következetesen körülbelül 4 du minden nap.

![Frissítés vár csúcs rendszeres időközönként du. 4:](media/service-premium-capacity-scenarios/peak-refresh-waits.png)

Nincs magyarázatairól több ezeket az eredményeket:

- Túl sok frissítési kísérlet sikerült fel egy időben, a kapacitás-csomópontot által meghatározott keretek túllépése. Ebben az esetben a P1 szintű a hat egyidejű frissítések alapértelmezés szerint memória mennyiségét.

- Lehet, hogy illeszkedjenek a rendelkezésre álló memória (igénylő legalább a teljes frissítés szükséges memória x 2) túl nagy adatkészleteket frissíteni kell.
- Nem elég hatékony Power Query-logika előfordulhat, hogy lehet eredményez memória kihasználtsága ugrásszerű adatkészlet frissítése során. A foglalt kapacitás a megnövekedett alkalmanként elérheti a fizikai korlátot, a frissítés sikertelen, és potenciálisan érintő műveletek más jelentés megtekintése a kapacitás.
- Gyakran lekérdezett adatkészleteket szeretne maradni a memóriában befolyásolhatja az egyéb adatkészletek frissítéséhez miatt korlátozni rendelkezésre álló memória.

A Power BI rendszergazdája vizsgálatáról, be is keressen:

- Az adatok időpontjában alacsony memória frissíti, ha rendelkezésre álló memória kevesebb, mint a frissítendő adatkészlet mérete x 2.
- Adatkészletek nem frissíthetők és nem a memóriában frissítése előtt, kezdett interaktív forgalom megjelenítése során (nagy erőforrásigényű) frissítési időpont. Szeretné egy adott időpontban mely adatkészleteket töltődnek be a memória, a Power BI rendszergazdája tekintse meg az adatkészletek területén **adatkészletek** lap az alkalmazásban. A rendszergazda is majd keresztszűrő egy adott idő alatt az egyik sáv kijelölését a kattintva a **óránkénti betöltött adatkészlet Counts**. Helyi ugrásszerű, az alábbi képen látható egy órát, amikor több adatkészlet is betölti a memóriába, mivel ezek tárhelyének kezdetét jelzi.
- Nagyobb adatkészletet adatbázislap véve helyezze el, amikor indítására ütemezett adatfrissítéseket. Adatbázislap szolgál a frissítés időpontja előtt túl sok különböző interaktív jelentések nagy memóriaterhelés okozta van jelezheti. A **óránkénti adatkészlet adatbázislap és memóriát** visual adatbázislap kiugrások egyértelműen utalhat.

Az alábbi képen látható helyi ugrásszerű betöltött adatkészletekben, ami arra utal, interaktív lekérdezés késleltetett frissítések kezdete. Egy adott időszakban az kiválasztása a **óránkénti betöltött adatkészlet Counts** Vizualizáció keresztszűrő a **adatkészlet méretű** visual.

![A betöltött adatkészletek helyi ugrásszerű javasol frissíti az interaktív lekérdezési Késleltetett indítás](media/service-premium-capacity-scenarios/hourly-loaded-dataset-counts.png)

A Power BI rendszergazdája is megkísérelheti a probléma megoldásához, győződjön meg arról, hogy elegendő memória áll rendelkezésre, az adatok frissülni fognak, első lépésként lépések végrehajtásával:

- Kapcsolatfelvétel az adatkészlet tulajdonosai és a rendszer arra szinkronizálások eltolása és a lemezterület-adatai frissítse ütemezések.
- Adatkészlet csökkenti a szükségtelen irányítópultok vagy az irányítópult eltávolításával lekérdezési terhelése csempéket, különösen azokkal, amelyek a sorszintű biztonság kényszerítése.
- Gyorsabbá a adatfrissítéseket optimalizálása a Power Query-logikát. Javíthatja a számított oszlopok vagy táblázatok modellezési. Csökkentse az adatkészletek mérete, vagy konfigurálja a nagyobb adatkészletből a végrehajtásához a növekményes adatok frissítése.

## <a name="identifying-slow-responding-datasets"></a>Az adatkészletek lassan válaszol azonosítása

Ebben a forgatókönyvben a vizsgálat kezdődött, amikor a felhasználók kifogásolt, hogy bizonyos jelentések túl sokáig megnyitásához, és esetenként lenne lefagy.

Az alkalmazás a Power BI-rendszergazda használhat a **lekérdezés időtartamának összegénél** vizualizációt a legrosszabbul teljesítő adatkészletek meghatározása szerint csökkenő sorrendben rendezi a adatkészletek **átlagos időtartam**. Ez a Vizualizáció is látható adatkészlet lekérdezések száma, így láthatja, hogy milyen gyakran az adatkészletek a rendszer megkérdezi.

![Legrosszabbul teljesítő adatkészletek](media/service-premium-capacity-scenarios/worst-performing-datasets.png)

A rendszergazda olvassa el a **lekérdezés időtartamok eloszlása** visual, amely bemutatja egy általános elosztásának bucketed lekérdezési teljesítmény (< 30ms, = 0 – 100 ms) a szűrt időszakra. Általában a lekérdezéseket, hogy hajtsa végre a megfelelő egy másodperc vagy kevesebb által figyelembe veendő válaszol-e a felhasználók többsége; Hozzon létre egy rossz teljesítmény érzete általában lekérdezéseket, amelyek hosszabb időt vesz igénybe.

A **óránkénti lekérdezés időtartamok eloszlása** Vizualizáció lehetővé teszi, hogy a Power BI rendszergazdáját, hogy ha a kapacitás teljesítmény sikerült rendelkezik lett által tapasztalt óránként időszakainak, gyenge. Minél nagyobb a sáv szegmensek, amelyek lekérdezési időtartamok több mint egy másodperc, a nagyobb a kockázat, hogy a felhasználók lássák fog gyenge teljesítményt eredményez.

A Vizualizáció interaktív, és ha a sáv szegmens választja, a megfelelő **lekérdezés időtartamának összegénél** visual a jelentés oldalon lévő táblázat keresztszűrhető jelöli, az adatkészletek megjelenítése. A keresztszűrés lehetővé teszi, hogy a Power BI rendszergazdáját, hogy könnyen azonosíthassa, amely adatkészletek lassan válaszol.

Az alábbi képen látható Vizualizáció szűrve **óránkénti lekérdezés időtartama Disztribúciók**, fókuszáló óránként gyűjtők a legrosszabbul teljesítő adatkészleteken. 

![Szűrt óránkénti lekérdezés időtartama Disztribúciók visual látható a még rosszabb adatkészletek végrehajtása](media/service-premium-capacity-scenarios/hourly-query-duration-distributions.png)

A gyenge teljesítő adatkészlet egy adott egy órás időtartam azonosítja, miután a Power BI rendszergazdája segítségével megvizsgálhatja, hogy gyenge teljesítményt egy túlterhelt kapacitást okozza, vagy egy rosszul miatt tervezett adatkészlet vagy jelentés. Is hivatkozhatnak a **várjon gyorsaság** Vizualizáció, és a lekérdezések átlagos várakozási idő csökkenő rendezés adatkészletek. Lekérdezések álló arra vár, ha az adatkészlet egy nagy kereslet valószínűleg nem túl sok lekérdezést vár oka. Ha az átlagos lekérdezési idő jelentősen kell (> 100 ms), akkor érdemes lehet megfontolni áttekintése az adatkészlet és jelentés megtekintéséhez, ha optimalizálást lehet végrehajtani. Például kevesebb vizualizációt megadott jelentésoldalak vagy a DAX-kifejezés optimalizálása.

![A lekérdezés várakozási idők Vizualizáció segít a gyengén teljesítő adatkészlet feltárása](media/service-premium-capacity-scenarios/query-wait-times.png)

Nincsenek lekérdezési várakozási idő felhalmozódásához adatkészletei több lehetséges oka:

- Optimálisnál rosszabb modell kialakítást, a mértékkifejezéseik vagy még jelentéstervező – minden körülmények között, amelyek hozzájárulhatnak a hosszú ideig futó lekérdezéseket, amelyek nagy mértékű CPU felhasználását. Ez kényszeríti, várja meg, amíg a szálak CPU elérhetővé válnak, és hozhat létre üzleti csúcsidőben fordul elő egy convoy hatás (csávából gondolkodási forgalmat), új lekérdezéseket. A **lekérdezési várakozások** fog a lap a fő erőforrást annak megállapításához, hogy adatkészletek rendelkeznek-e a lekérdezések magas átlagos várakozási időt.
- Nagyszámú egyidejű kapacitás felhasználók (több és több ezer) ugyanaz a jelentés vagy adatkészlet felhasználása. Akkor is a jól megtervezett adatkészletek egy egyidejűségi küszöbérték rosszul hajthat végre. Ez jelentősen nagyobb értéket megjelenítő, a lekérdezés számolja, mint a többi adatkészletek megjelenítése egyetlen adatkészlet általában jelzi (például 300 K lekérdezései képest egy adatkészlet < 30K lekérdezések minden adathalmaz esetében). Egy pont a lekérdezést vár ehhez az adatkészlethez indul ütemtervét, amely látható a **lekérdezés időtartamának összegénél** visual.
- Számos különböző adatkészletek egyidejűleg lekérdezett memóriaakadozás okoz, a memória adataikkal gyakran ciklus adatkészletek. Ennek eredményeképpen a felhasználók teljesítménycsökkenést tapasztal, ha az adatkészlet betölti a memóriába. Győződjön meg arról, hogy a Power BI-rendszergazdák az itt található a **óránkénti adatkészlet adatbázislap és memóriát** visual, ez arra utalhat, hogy nagy számú adatkészletek a memóriába betöltött vannak ismételten a kiürítés alatt.

## <a name="identifying-causes-for-sporadically-slow-responding-datasets"></a>Okainak azonosítása vonatkozó szórványosan lassú-adatkészletek

Ebben a forgatókönyvben a vizsgálatot, amikor a felhasználók ismerteti, hogy jelentésvizualizációk néha voltak lassan válaszol, vagy válaszképtelenné válik, de máskor voltak intézkedéseket válaszol-e már.

Az alkalmazáson belüli a **lekérdezés időtartamának összegénél** szakaszban használt keresse meg a hibát okozó adatkészlet a következő módon:

- Az a **lekérdezés időtartamának összegénél** vizuális a rendszergazda adatkészlet adatkészletet (a felső adatkészletek lekérdezett-gyel kezdődik) szerint szűrt és megvizsgálta a keresztszűrés szűrt sávok a **óránkénti lekérdezés Disztribúciók** visual.
- Ha egy egyetlen óránként sáv bemutatta az összes lekérdezés időtartama csoportokat és más óránként sávok az adott adatkészlethez aránya jelentős változásokat (például a arányok a színek között változik jelentősen), azt jelenti, hogy ez az adatkészlet bemutatott szórványos módosítása teljesítmény.
- A bemutató egy gyengén teljesítő lekérdezések szabálytalan része egy órás sávok jelzett timespan, ahol az adatkészlet egy zajos szomszédok hatást, egyéb adatkészletekhez tevékenységek által okozott hatással volt.

Egy adatkészlet teljesítmény jelentős setback történt, ahol a "(3,10s]"végrehajtási időtartamgyűjtő mérete által jelzett a január 30-án egy órán keresztül az alábbi kép. Adott egy órás sávon kattintással tárja fel az összes adathalmaz ideje alatt a memóriába betöltött felszínre hozza a lehetséges adatkészletek zajos szomszédok hatása okozza.

![Sáv megjelenítése a legrosszabb teljesítmény nagy által](media/service-premium-capacity-scenarios/worst-performing-queries.png)

Miután problémás lehet timespan van (például során azonosított január 30. a fenti képen) a Power BI rendszergazdája adatkészlet összes szűrő eltávolítása, majd csak az adott időtartam meghatározni, melyik adatkészleteket aktívan kérdeztek ebben az időszakban szűrése. A felső lekérdezett adatkészletet, vagy egy a leghosszabb átlagos lekérdezési idő általában a zajos szomszédok hatása sokkal adatkészlete.

Egy megoldás erre a problémára lehet terjeszteni a különböző munkaterületekhez különböző prémium szintű kapacitások vagy a megosztott kapacitás, ha az adatkészlet méretét, a felhasználási követelményeket és az adatok frissítése minták keresztül adatkészletek támogatottak nem sokkal.

Fordítva is igaz lehet. A Power BI rendszergazdája sikerült alkalommal, amikor egy adatkészlet lekérdezés jelentősen javítja a teljesítményt, azonosítása, majd keresse meg mi eltűnt. Adott időpontban hiányzik a bizonyos adatokat, majd, amely segíthet a okozó probléma mutasson.

## <a name="determining-whether-there-is-enough-memory"></a>Meghatározása, hogy van-e elegendő memória

Annak megállapításához, hogy van-e elegendő memória a kapacitás a számítási feladatok végrehajtásához, a Power BI-rendszergazdák az itt található a **felhasznált memória százalékos** Vizualizáció a a **adatkészletek** az alkalmazás lapján. **Az összes** memória (összesen) a betölti a memóriába, függetlenül attól, hogy aktívan kérdezhető le, vagy azok feldolgozott adatkészletek által felhasznált memóriát jelenti. **Aktív** memória a aktívan feldolgozott adatkészletek által felhasznált memóriát jelenti.

A megfelelő minőségben a Vizualizáció fog kinézni a, megjelenítése egy minden (összesen) közötti résnek és aktív memória:

![Egy megfelelő kapacitást jelennek meg minden (összesen) közötti eseményáramlási kimaradást és aktív memória](media/service-premium-capacity-scenarios/memory-healthy-capacity.png)

Tapasztal memóriaterhelés minőségben ugyanabban a vizualizációban egyértelműen jelennek meg a aktív memória és a teljes memória beépül, ami azt jelenti, hogy nem lehet majd betölti a memóriába további adatkészletek. Ebben az esetben a Power BI rendszergazdája kattintva **indítsa újra a kapacitás** (a **speciális beállítások** a kapacitás beállításai terület a felügyeleti portál). Újraindítás a kapacitás eredmények összes adatkészletek folyamatban van a memóriából a kiürített, és lehetővé teheti, hogy újra betölti a memóriába (lekérdezések vagy az adatok frissítése) igényeinek megfelelően.

![** Aktív ** memória beépül a ** minden ** memória](media/service-premium-capacity-scenarios/memory-unhealthy-capacity.png)

## <a name="determining-whether-there-is-enough-cpu"></a>Amely meghatározza, hogy van-e elegendő Processzor

Általában egy kapacitáshoz átlagos CPU-kihasználtsága 80 % alatt kell maradnia. Ez az érték meghaladja a kapacitás mérete hamarosan eléri a Processzor színtelítettség jelenti.

CPU színtelítettség hatásait ki, a műveletek végrehajtása sok CPU-környezetek kapcsolók megpróbálja feldolgozni az összes műveletet, a kapacitás miatt azok kell tovább tart a vártnál. Prémium szintű kapacitást a nagy számú lekérdezést Ez jelzi a lekérdezési várakozási időt. A lekérdezési várakozási időt következménye a szokásosnál lassabban válaszképességét. A Power BI rendszergazdai amikor megtekinti a Processzor megtelt könnyen azonosítható a **óránkénti lekérdezés várakozási idő Disztribúciók** visual. Lekérdezés rendszeres csúcsok várakozási számát jelzi a lehetséges CPU színtelítettség idő.

![Lekérdezés rendszeres csúcsok várakozási számát jelzi a lehetséges CPU színtelítettség idő](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

Hasonló mintát néha is észlelhető a háttérbeli műveletek, ha azok hozzájárulnak CPU színtelítettség. A Power BI-rendszergazdák is keresni rendszeres ugrásszerű CPU színtelítettség időben jelezheti (valószínűleg miatt más folyamatban lévő adatkészlet frissíti és/vagy interaktív lekérdezések) egy adott adatkészlet frissítési időpont. Ebben a példányban hivatkozó a **rendszer** megtekintése az alkalmazásban esetleg nem feltétlenül mutatja, hogy van-e a CPU 100 %-os. A **rendszer** a nézet jeleníti meg az óradíjas átlagok, de a Processzor is legyen telített (nagy erőforrásigényű) művelet több percig ami megjelenik-e csúcsok, várakozási időt.

Nincsenek egyéb CPU színtelítettség hatásának további részleteiről. Fontos, hogy várjon lekérdezések száma, amíg lekérdezés várakozási idő mindig akkor történik meg bizonyos mértékig lekérdezésteljesítmény teljesítményromlást okozó nélkül. Bizonyos adatkészletek (a hosszabb átlagos lekérdezési idő, jelezve összetettségére vagy nagy méretére) jobban ki CPU színtelítettség hatásait a többinél. Könnyedén azonosíthatja ezeket az adatkészleteket, a Power BI rendszergazdája is keresse meg a szín összeállításban gyűjteménye a módosításokat a **óránkénti várakozási idő terjesztési** visual. Után gyorsabban egy rendkívüli sáv, akkor keresse meg az adatkészleteket, akinek lekérdezést vár ebben az időszakban és is tekintse meg a lekérdezés átlagos várakozási idő átlagos lekérdezési idő képest. Ha két metrikák ugyanolyan nagyságrendű, és a lekérdezési számítási feladatok az adatkészlet nem triviális, valószínű, hogy az adatkészlet nem elegendő Processzor hatással van.

A hatás nyilvánvaló, különösen akkor lehet, ha egy adatkészlet használja fel a nagyon gyakori lekérdezések (például a betanítás), a több felhasználó által rövid adatlöketekkel CPU színtelítettség során minden egyes burst eredményez. Ebben az esetben az adatkészlethez jelentős várakozási időt is észlelt és az egyéb adatkészletekhez a kapacitást (zajos szomszédok hatás), mely negatív hatással.

Bizonyos esetekben a Power BI-rendszergazdák kérheti, hogy az adatkészlet tulajdonosa hozzon létre egy kisebb felejtő lekérdezési számítási feladatok létrehoz egy irányítópultot (melyik lekérdezések rendszeres időközönként minden olyan adatkészletben a gyorsítótárban lévő csempék frissítése) helyett egy jelentést. Ez megakadályozhatja ugrásszerűen az irányítópult betöltésekor. Ez a megoldás nem mindig lehetséges a megadott üzleti követelményeknek, ugyanakkor anélkül, hogy módosítja az adatkészletet CPU telítettséget elkerülése érdekében hatékony módja lehet.

## <a name="acknowledgements"></a>Nyugtázás

Ez a cikk írásának Peter Myers, a Data Platform MVP és a független, a BI-Szakértővé [bitenként megoldások](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Következő lépések

> [!div class="nextstepaction"]
> [Prémium szintű kapacitások az alkalmazás figyelése](service-admin-premium-monitor-capacity.md)    
> [!div class="nextstepaction"]
> [A felügyeleti portál kapacitások figyelése](service-admin-premium-monitor-portal.md)   

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

||||||