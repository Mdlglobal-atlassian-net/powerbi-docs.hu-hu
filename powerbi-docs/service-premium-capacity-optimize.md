---
title: Microsoft Power BI Premium-kapacitások optimalizálása
description: A Power BI Premium-kapacitások optimalizálási stratégiáinak ismertetése.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/09/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 4d03419105244b7fddafea3b26b69e4f4f5f874c
ms.sourcegitcommit: 320d83ab392ded71bfda42c5491acab3d9d357b0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/10/2019
ms.locfileid: "74958540"
---
# <a name="optimizing-premium-capacities"></a>Prémium szintű kapacitások optimalizálása

Ha teljesítménybeli problémák merülnek fel a Premium-kapacitásban, gyakori első lépés a megoldások optimalizálása vagy finomhangolása az elfogadható válaszidők visszaállításához. Így elkerülhető a további Premium-kapacitások vásárlása, hacsak ez nem indokolt.

Ha további Premium-kapacitásra van szükség, két lehetősége van, amelyeket a cikk ismertet:

- Meglévő Premium-kapacitás vertikális felskálázása
- Új Premium-kapacitás hozzáadása

A cikk vége a tesztelést és a Premium-kapacitás méretezését ismerteti.

## <a name="best-practices"></a>Ajánlott eljárások

Ha a lehető legjobb kihasználtságot és teljesítményt szeretné elérni, használhat bizonyos ajánlott eljárásokat:

- Munkaterületek használata személyes munkaterületek helyett.
- Az üzleti szempontból kritikus és az önkiszolgáló BI (SSBI) szétválasztása eltérő kapacitásokra.

  ![Az üzleti szempontból kritikus és az önkiszolgáló BI szétválasztása eltérő kapacitásokra](media/service-premium-capacity-optimize/separate-capacities.png)

- Ha csak Power BI Pro-felhasználókkal oszt meg tartalmat, azokat nem kell dedikált kapacitásban tárolni.
- Dedikált kapacitást akkor érdemes használni, ha egy adott frissítési időt szeretne elérni, vagy ha bizonyos funkciókra van szüksége. Ilyenek lehetnek a nagyméretű adatkészletek vagy a lapszámozott jelentések.

### <a name="addressing-common-questions"></a>Válaszok a gyakori kérdésekre

A Power BI Premium üzemelő példányainak optimalizálása összetett témakör, amelyhez szükséges a számítási feladatok követelményeinek, a rendelkezésre álló erőforrásoknak, és ezek hatékony használatának megértése.

Ez a cikk hét gyakori támogatási kérdést jár körül, majd ismerteti az ezekkel kapcsolatos vélhető problémákat és megoldásokat, valamint az ezek azonosítására és megoldására vonatkozó információkat.

### <a name="why-is-the-capacity-slow-and-what-can-i-do"></a>Miért lassú a kapacitás, és mit tehetek ez ügyben?

A lassú Premium-kapacitásnak számos oka lehet. Ehhez a kérdéshez tisztáznunk kell, mit is jelent a lassú. Lassú a jelentések betöltése? Esetleg egyáltalán nem töltenek be? A jelentések vizualizációi lassan töltenek be vagy frissülnek, amikor a felhasználók használatba veszik a jelentést? A frissítések a vártnál vagy a korábban tapasztaltaknál tovább tartanak?

Az ok megértése után megkezdődhet a vizsgálat. A következő hat kérdésre adott válaszokkal konkrétabb problémákat oldhat meg.

### <a name="what-content-is-using-up-my-capacity"></a>Milyen tartalom használja a kapacitásom?

A **Power BI Premium-kapacitásmetrikák** alkalmazással kapacitás szerint szűrhet, és áttekintheti a munkaterületek tartalmának teljesítménymetrikáit. Így áttekintheti a Premium-kapacitások tartalmának teljesítménymetrikáit és erőforrás-használatát az elmúlt hét napra visszamenőleg. A Premium-kapacitások teljesítményével kapcsolatos problémák esetén gyakran a figyelés az első lépés a hibaelhárításhoz.

A figyelendő fontosabb metrikák:

- Az átlagos CPU-kihasználtság és a magas kihasználtság száma.
- Az átlagos memóriahasználat és a magas kihasználtság száma, valamint az egyes adatkészletek, adatfolyamok és lapszámozott jelentések memóriahasználata.
- A memóriában betöltött aktív adatkészletek.
- A lekérdezések átlagos és maximális időtartama.
- Lekérdezésekre való várakozás átlagos időtartama.
- Az adatkészletek és a adatfolyamok átlagos frissítési ideje.

A Power BI Premium-kapacitásmetrikák alkalmazásban az aktív memória egy jelentéshez tartozó összes memóriát jeleníti meg, amely nem zárható ki, mivel használatban volt az elmúlt három percben. A frissítési várakozási idők megugrása összefügghet egy nagy és/vagy aktív adatkészlettel.

A **Top 5 by Average Duration** (Átlagos időtartam szerinti 5 legmagasabb) nevű diagram a kapacitás-erőforrásokat legnagyobb mértékben felhasználó öt adatkészletet, lapszámozott jelentést és adatfolyamot emeli ki. Az ötös listák tartalma jó jelöltnek számít a vizsgálathoz és a potenciális optimalizáláshoz.

### <a name="why-are-reports-slow"></a>Miért lassúak a jelentések?

Az alábbi táblázatokban láthatók a lehetséges problémák, valamint azok azonosításának és kezelésének módjai.

#### <a name="insufficient-capacity-resources"></a>Nincs elég kapacitás-erőforrás

| Lehetséges magyarázatok | Az azonosítás módja | A megoldás módja |
| --- | --- | --- |
| Magas összesített aktív memória (a modellt nem lehet kizárni, mert az elmúlt három percben használatban volt).<br><br> Több kiugró érték a lekérdezések várakozási idejében.<br><br> Több kiugró érték a frissítések várakozási idejében. | Figyelje a memória mérőszámait \[[1](#endnote-1)\] és a kizárási számokat \[[2](#endnote-2)\]. | Csökkentse a modell méretét, vagy váltson DirectQuery módra. Tekintse meg a cikk [Modellek optimalizálása](#optimizing-models) című szakaszát.<br><br> Skálázza vertikálisan a kapacitást.<br><br> Rendelje hozzá a tartalmat egy másik kapacitáshoz. |

#### <a name="inefficient-report-designs"></a>Nem hatékony jelentéskialakítások

| Lehetséges magyarázatok | Az azonosítás módja | A megoldás módja |
| --- | --- | --- |
| A jelentés oldalai túl sok vizualizációt tartalmaznak (az interaktív szűrés legalább egy lekérdezést elindít vizualizációnként).<br><br> A vizualizációk a szükségesnél több adatot kérnek le. | Tekintse át a jelentések kialakítását.<br><br> Kérdezze meg a jelentés felhasználóitól, hogy hogyan használják a jelentéseket.<br><br> Figyelje az adatkészlet lekérdezési metrikáit \[[3](#endnote-3)\]. | Tervezze újra a jelentéseket kevesebb oldalankénti vizualizációval. |

#### <a name="dataset-is-slow-especially-when-reports-have-previously-performed-well"></a>Az adatkészlet lassú, különösen olyan esetekben, amelyekben a jelentések korábban jól teljesítettek

| Lehetséges magyarázatok | Az azonosítás módja | A megoldás módja |
| --- | --- | --- |
| Egyre nagyobb mennyiségű importált adat.<br><br> Összetett vagy nem hatékony számítási logika, például RLS-szerepkörök.<br><br> A modell nincs teljesen optimalizálva.<br><br> (DQ/LC) Átjárókésés.<br><br> Lassú válaszidő a DQ forráslekérdezéseinél. | Tekintse át a modellek kialakítását.<br><br> Figyelje az átjáró teljesítményszámlálóit. | Tekintse meg a cikk [Modellek optimalizálása](#optimizing-models) című szakaszát. |

#### <a name="high-concurrent-report-usage"></a>Nagy mértékű párhuzamos jelentéshasználat

| Lehetséges magyarázatok | Az azonosítás módja | A megoldás módja |
| --- | --- | --- |
| Magas lekérdezésekre való várakozási idő.<br><br> CPU-telítettség.<br><br> Túllépett DQ/LC-kapcsolatkorlátok. | Figyelje a CPU-kihasználtságot \[[4](#endnote-4)\], a lekérdezések várakozási idejét, és a DQ/LC-kihasználtság \[[5](#endnote-5)\] metrikáit, illetve a lekérdezések időtartamát. Ha ingadoznak, az párhuzamossági problémákra utalhat. | Skálázza fel vertikálisan a kapacitást, vagy rendelje hozzá a tartalmat egy másik kapacitáshoz.<br><br> Tervezze újra a jelentéseket kevesebb oldalankénti vizualizációval. |

**Megjegyzések:**    
<a name="endnote-1"></a>\[1\] Átlagos memóriahasználat (GB), és maximális memóriahasználat (GB).   
<a name="endnote-2"></a>\[2\] Adathalmaz-kizárások.   
<a name="endnote-3"></a>\[3\] Adatkészlet-lekérdezések, adatkészletek átlagos lekérdezési időtartama (ms), adatkészletek várakozási száma, és adatkészletek átlagos várakozási ideje (ms).   
<a name="endnote-4"></a>\[4\] a magas CPU-kihasználtság száma és a legmagasabb CPU-kihasználtság ideje (az elmúlt hét napban).   
<a name="endnote-5"></a>\[5\] a magas DQ/LC-kihasználtság száma és a legmagasabb DQ/LC-kihasználtság ideje (az elmúlt hét napban).   

### <a name="why-are-reports-not-loading"></a>Miért nem töltenek be a jelentések?

Ha a jelentések nem töltődnek be, az biztos jele annak, hogy a kapacitás nem rendelkezik elegendő memóriával, és túlterhelődött. Ez akkor fordulhat elő, ha az összes betöltött modell aktív lekérdezést végez, így nem zárható ki, a frissítési műveletek pedig szünetelnek vagy késnek. A Power BI szolgáltatás 30 másodpercig megkísérli betölteni az adatkészletet, a felhasználót pedig értesíti a hibáról, és későbbi újrapróbálkozásra kéri.

Jelenleg nem létezik metrika a jelentések betöltési hibáinak figyelésére. A hiba előfordulási valószínűségét a rendszermemória figyelésével állapíthatja meg, különösképp a legmagasabb kihasználtság és annak ideje figyelésével. A nagy mennyiségű adatkészlet-kizárás és az adatkészletek frissítésének átlagos várakozási ideje arra utalhat, hogy ez a probléma.

Ha ez csak ritkán fordul elő, nem tekintendő kritikus problémának. A jelentés felhasználóit értesíti a szolgáltatás, hogy elfoglalt, és próbálkozzanak újra később. Ha ez túl gyakran fordul elő, a probléma megoldható a Premium-kapacitás vertikális felskálázásával vagy a tartalom egy másik kapacitáshoz rendelésével.

A kapacitás-rendszergazdák (és a Power BI szolgáltatás rendszergazdái) a **Lekérdezési hibák** metrikával állapíthatják meg, hogy ez mikor fordul elő. Túlterhelt rendszer esetén emellett újraindíthatják a kapacitást, ezzel alaphelyzetbe állítva az összes műveletet.

### <a name="why-are-refreshes-not-starting-on-schedule"></a>Miért nem kezdődnek időben az ütemezett frissítések?

Az ütemezett frissítések kezdési ideje nem garantált. Ne felejtse el, hogy a Power BI szolgáltatás mindig az interaktív műveleteket részesíti előnyben a háttérműveletekkel szemben. A frissítés egy háttérművelet, amely két feltétel teljesülése esetén megy végbe:

- Rendelkezésre áll elegendő memória
- A Premium-kapacitás támogatott egyidejű frissítéseinek száma nem haladja meg a korlátot

Ha a feltételek nem teljesülnek, a frissítés várólistára kerül mindaddig, amíg a feltételek nem megfelelőek.

A teljes frissítéshez az aktuális adatkészlet memóriaméretének legalább kétszeresére van szükség. Ha nem áll rendelkezésre elegendő memória, a frissítés nem kezdődik el addig, amíg a modellkizárás memóriát nem szabadít fel. Ezt azt jelenti, hogy késések jelentkeznek mindaddig, amíg egy vagy több adatkészlet inaktívvá és kizárhatóvá nem válik.

Az egyidejű frissítések maximális támogatott száma a háttérbeli virtuális magok másfélszerese (felfelé kerekítve).

Az ütemezett frissítés sikertelen lesz, ha nem kezdődhet el a következő ütemezett frissítés előtt. A felhasználói felületről manuálisan elindított frissítés háromszor kísérel meg futni, mielőtt meghiúsul.

A kapacitás-rendszergazdák (és a Power BI szolgáltatás rendszergazdái) **A frissítésre várakozás átlagos időtartama (percben)** metrikával állapíthatják meg az ütemezett idő és a művelet kezdete közötti átlagos késést.

Bár ez általában nem elsődleges rendszergazdai szempont, a pontos adatfrissítések érdekében ügyeljen arra, hogy elegendő memória áll rendelkezésre. Ehhez előfordulhat, hogy adatkészleteket kell elkülönítenie elegendő erőforrásokkal rendelkező kapacitásokban. A rendszergazdák emellett az adatkészletek tulajdonosaival együttműködve lépcsőzetesen feloszthatják vagy csökkenthetik az ütemezett adatfrissítési időket az ütközések minimalizálása érdekében. A rendszergazdák nem tekinthetik meg a frissítési várakozási sort, és nem kérhetik le az adatkészletek ütemterveit.

### <a name="why-are-refreshes-slow"></a>Miért lassú a frissítés?

A frissítések lassúak lehetnek – vagy annak tűnhetnek – (ahogy erre kitért az előző gyakori kérdés).

Ha a frissítés valóban lassú, annak számos oka lehet:

- Nincs elegendő CPU-teljesítmény (a frissítés rendkívül nagy processzorteljesítményt igényelhet).
- Nincs elegendő memória, ami a frissítés szüneteltetését eredményezi (ami miatt a frissítés csak akkor indul újra, ha az ehhez szükséges feltételek adottak).
- Kapacitástól független okok, például az adatforrás rendszerének válaszideje, hálózati késés, érvénytelen engedélyek vagy az átjáró átviteli sebessége.
- Adatmennyiség – jó ok a növekményes frissítés konfigurálására, ahogy azt lentebb részletezzük.

A kapacitás-rendszergazdák (és a Power BI szolgáltatás rendszergazdái) **A frissítés átlagos időtartama (percben)** metrikával állapíthatják meg az összehasonlítási alapot, **A frissítésre várakozás átlagos időtartama (percben)** metrikával pedig ütemezett idő és a művelet kezdete közötti átlagos késést.

A növekményes frissítés jelentősen csökkentheti az adatfrissítés időtartamát, különösen a nagyméretű modelltáblák esetében. A növekményes frissítés négy előnnyel jár:

- **A frissítések gyorsabbak** – Csak a tábla egy részhalmazát kell betölteni, ami csökkenti a CPU- és memóriahasználatot, a több partíció frissítése pedig nagyobb szintű párhuzamosságot nyújt.
- **A frissítések csak szükség esetén mennek végbe** – A növekményes frissítési szabályzatok úgy konfigurálhatók, hogy csak az adatok változásakor töltsenek be.
- **Megbízhatóbb frissítések** – Az alacsony megbízhatóságú adatforrás-rendszerekhez való rövid futású kapcsolatok ritkábban szűnnek meg.
- **A modellek rövidek maradnak** – A növekményes frissítési szabályzatok úgy konfigurálhatók,hogy automatikusan eltávolítsák egy időbeli csúszóablak előzményeit.

További információ: [Növekményes frissítés a Power BI Premium szolgáltatásban](service-premium-incremental-refresh.md).

### <a name="why-are-data-refreshes-not-completing"></a>Miért nem mennek végbe az adatfrissítések?

Ha egy adatfrissítés elkezdődik, azonban nem fejeződik be, annak számos oka lehet:

- Nincs elég memória, még akkor is, ha csak egy modell található a Premium-kapacitásban, azaz a modell mérete nagyon nagy.
- Kapacitástól független okok, például az adatforrás rendszerének leválasztása, érvénytelen engedélyek vagy átjáróhiba.

A kapacitás-rendszergazdák (és a Power BI szolgáltatás rendszergazdái) a **Refresh Failures due to out of Memory** (Memóriahiányból adódó frissítési hibák) metrikát figyelhetik.

## <a name="optimizing-models"></a>Modellek optimalizálása

Az optimális modellkialakítás kritikus fontosságú a hatékony és méretezhető megoldások fejlesztésében. Azonban ez a cikk erről nem értekezik részletesen. Ez a szakasz a modelloptimalizálás legfontosabb szempontjait ismerteti.

### <a name="optimizing-power-bi-hosted-models"></a>Power BI-ban üzemeltetett modellek optimalizálása

A Premium-kapacitásban üzemeltetett modellek optimalizálása az adatforrás(ok) és a modell szintjén történik.

Tekintse át az importálási modell optimalizálási lehetőségeit:

![Egy importálási modell optimalizálási lehetőségei](media/service-premium-capacity-optimize/import-model-optimizations.png)

Az adatforrás szintjén:

- A relációs adatforrások úgy optimalizálhatók, hogy a lehető leggyorsabb frissítést nyújtsák az adatok előzetes integrálásával, a megfelelő indexek alkalmazásával, a növekményes frissítési időszakokhoz igazodó táblapartíciók definiálásával, és a számítások materializálásával (számított modelltáblák és oszlopok helyett) vagy számítási logika a nézetekhez való hozzáadásával.
- A nem relációs adatforrások előzetesen integrálhatók a relációs forrásokkal.
- Ügyeljen arra, hogy az átjárók elegendő erőforrással rendelkeznek, lehetőleg dedikált gépeken, megfelelő hálózati sávszélességgel, és az adatforrásokhoz közel.

A modell szintjén:

- A Power Query-tervek minimalizálhatnak vagy eltávolíthatnak összetett átalakításokat, különösen azokat, amelyek eltérő adatforrásokat egyesítenek (az adattárházak ezt a Kinyerés–Átalakítás–Betöltés fázisban végzik el). Emellett az adatforrások megfelelő adatvédelmi szintjeinek beállításával elkerülhető, hogy a Power BI-nak a teljes eredményeket be kelljen töltenie a lekérdezéseken átívelő egyesített eredményekhez.
- A modell szerkezete meghatározza a betöltendő adatmennyiséget, és közvetlen hatással van a modell méretére. Oszlopok és sorok (különösen régi adatok) eltávolításával vagy (részletes helyett) összegzett adatok betöltésével kialakítható úgy, hogy elkerülhető legyen a felesleges adatok betöltése. Jelentős méretcsökkenést érhet el, ha eltávolítja azokat a számossági oszlopokat (kifejezetten a szöveges oszlopokat), amelyek a megfelelő módon tárolnak vagy tömörítenek adatokat.
- A modellek lekérdezési teljesítménye egyirányú kapcsolatok konfigurálásával javítható, kivéve, ha feltétlen szükség van kétirányú szűrésre. Érdemes megfontolni a [CROSSFILTER](https://docs.microsoft.com/dax/crossfilter-function) függvény használatát a kétirányú szűrés helyett.
- Az összesítési táblázatok gyors lekérdezési válaszokat eredményezhetnek az előre összefoglalt adatok betöltésével, azonban ez megnöveli a modell méretét, és hosszabb frissítési időt eredményezhet. Az összesítési táblák általában nagyon nagy méretű modellekhez vagy összetett modellkialakításokhoz használatosak.
- A számított táblák és oszlopok növelik a modellméretet, és hosszabb frissítési időt eredményeznek. A kisebb tárméret és a gyorsabb frissítési idő általában az adatok az adatforrásban való materializálásával vagy számításával érhető el. Ha ez nem lehetséges, a Power Query egyéni oszlopai fejlett tárhelytömörítést nyújtanak.
- Emellett DAX-kifejezéseket is használhat mértékekhez és RLS-szabályokhoz, valamint átírhatja a logikát a költséges képletek elkerüléséhez
- A növekményes frissítés jelentősen csökkentheti a frissítési időt, valamint memóriát és processzorteljesítményt takarít meg. A növekményes frissítés emellett konfigurálható úgy, hogy eltávolítsa a régi adatokat, így korlátozza a modellméreteket.
- A modellek újratervezhetők két modellként, ha a lekérdezési minták eltérnek és ütköznek. Egyes jelentések például magas szintű összesítéseket jelenítenek meg minden előzménnyel, és 24 órás késést is képesek tolerálni. Más jelentések csak a mai adatokat nézik, és részletes hozzáférésre van szükségük az egyes tranzakciókhoz. Ahelyett, hogy egyetlen modellt tervezne minden jelentéshez, létrehozhat két modellt, amelyet az egyes követelményekhez optimalizál.

Tekintse át egy DirectQuery-modell optimalizálási lehetőségeit. Mivel a modell lekérdezési kéréseket küld a mögöttes adatforrásnak, az adatforrás-optimalizálás kritikus fontosságú a rugalmas modell-lekérdezésekhez.

 ![Egy DirectQuery-modell optimalizálási lehetőségei](media/service-premium-capacity-optimize/direct-query-model-optimizations.png)

Az adatforrás szintjén:

- Az adatforrás az adatok előzetes integrálásával (amely nem lehetséges a modell szintjén), a megfelelő indexek alkalmazásával, a táblapartíciók definiálásával, az összesített adatok (indexelt nézetekkel történő) materializálásával és a számítási mennyiség minimalizálásával úgy optimalizálható, hogy a lehető leggyorsabb lekérdezést nyújtsa. A legjobb megoldást alkalmazta, ha az átmenő lekérdezésekhez csak szűrésre és belső illesztésekre van szükség az indexelt táblák vagy nézetek esetén.
- Ügyeljen arra, hogy az átjárók elegendő erőforrással rendelkeznek, lehetőleg dedikált gépeken, megfelelő hálózati sávszélességgel, és az adatforrásokhoz közel.

A modell szintjén:

- A Power Query lekérdezési terveinek ideális esetben nem szabad átalakításokat végezniük. Ha mégis így történik, célszerű ezek számát minimálisra csökkenteni.
- A modellek lekérdezési teljesítménye egyirányú kapcsolatok konfigurálásával javítható, kivéve, ha feltétlen szükség van kétirányú szűrésre. A modellkapcsolatokat úgy érdemes konfigurálni, hogy azok feltételezzék a hivatkozási integritás kényszerítését (amennyiben ez teljesül). Ennek eredményeképp az adatforrások lekérdezései hatékonyabb belső illesztéseket használhatnak (külső illesztések helyett).
- Ne hozzon létre Power Query-lekérdezésekben egyéni oszlopokat vagy -modellekben számított oszlopokat – ezeket lehetőség szerint inkább az adatforrásban materializálja.
- Emellett DAX-kifejezéseket is használhat mértékekhez és RLS-szabályokhoz, valamint átírhatja a logikát a költséges képletek elkerüléséhez.

Tekintse át az összetett modell optimalizálási lehetőségeit. Az összetett modellek importálási és DirectQuery-táblák egyvelegét teszik elérhetővé.

![Egy összetett modell optimalizálási lehetőségei](media/service-premium-capacity-optimize/composite-model-optimizations.png)

- Az importálási és a DirectQuery-modellek optimalizálása általában az ilyen tárolási módokat alkalmazó összetett modelltáblákra is alkalmazható.
- Célszerű általában egy kiegyensúlyozott kialakításra törekedni. Ehhez konfigurálhat dimenzió típusú táblákat (amelyek üzleti entitásokat képviselnek) kettős tárolási módúként, valamint tény típusú táblákat DirectQuery tárolási módúként. A kettős tárolási mód az importálási és a DirectQuery tárolási módot jelenti együtt, aminek keretében a Power BI szolgáltatás megállapíthatja a leghatékonyabb tárolási módot áthaladó natív lekérdezések létrehozásához.
- Ügyeljen arra, hogy az átjárók elegendő erőforrással rendelkeznek, lehetőleg dedikált gépeken, megfelelő hálózati sávszélességgel, és az adatforrásokhoz közel
- Az importálási tárolási módúként konfigurált összesítési táblák jelentős lekérdezésteljesítménybeli növekedést érhetnek el, ha segítségükkel DirectQuery tárolási módú, tény típusú táblákat összegez. Ebben az esetben az összesítési táblák növelik a modell méretét és a frissítési időt, ami a legtöbbször elfogadható a gyorsabb lekérdezések fényében.

### <a name="optimizing-externally-hosted-models"></a>Külsőleg üzemeltetett modellek optimalizálása

A [Power BI-ban üzemeltetett modellek optimalizálása](#optimizing-power-bi-hosted-models) című szakaszban tárgyalt optimalizálási lehetőségek közül számos az Azure Analysis Services és az SQL Server Analysis Services szolgáltatással fejlesztett modellekre is vonatkozik. Ez alól kivételt képeznek egyes funkciók, amelyeket a program jelenleg nem támogat, például az összetett modellek és az összesítési táblák.

A külsőleg üzemeltetett adatkészletek esetén egy további szempont az adatbázis-üzemeltetés és a Power BI szolgáltatás kapcsolata. Az Azure Analysis Services esetén ez azt jelenti, hogy az Azure-erőforrást ugyanabban a régióban kell létrehozni, mint amelyben a Power BI-bérlő található (saját régió). Az SQL Server Analysis Services esetén ez azt jelenti, hogy IaaS-környezetben a virtuális gépet ugyanabban a régióban kell üzemeltetni, helyszíni környezetben pedig hatékony átjáróbeállítást kell megadni.

Nem árt tudnia, hogy az Azure Analysis Services adatbázisai és az SQL Server Analysis Services táblázatos adatbázisai megkövetelik, hogy a modellek teljes mértékben be legyenek töltve a memóriába, valamint ott is maradjanak a lekérdezések támogatásához. A Power BI szolgáltatáshoz hasonlóan elegendő memóriának kell rendelkezésre állnia a frissítéshez, ha a modellnek online állapotban kell maradnia a frissítés közben. A Power BI szolgáltatástól a modellek nem kerülnek be automatikusan a memóriába vagy ki abból a használattól függően. A Power BI Premium így hatékonyabb módot kínál a modell-lekérdezések maximalizálására, alacsonyabb memóriahasználattal.

## <a name="capacity-planning"></a>Kapacitástervezés

A Premium-kapacitás mérete meghatározza a rendelkezésre álló memóriát processzor-erőforrásokat és a kapacitásra vonatkozó korlátokat. A Premium-kapacitások számát is figyelembe kell venni, mivel több Premium-kapacitással könnyebb elkülöníteni egymástól a számítási feladatokat. A tárhely kapacitás-csomópontonként 100 TB, amely valószínűleg elegendő bármilyen számítási feladathoz.

A Premium-kapacitások méretének és számának megállapítása kihívást jelenthet, különösen az első néhány kapacitás esetében. A kapacitások méretezésekor az első lépés a mindennapos használatot képviselő átlagos számításifeladat-mennyiség felmérése. Fontos tisztában lenni azzal, hogy nem minden számítási feladat egyenlő. Ha az egyik végletet nézzük például, 100 felhasználó, aki egyidejűleg fér hozzá egy egyetlen vizualizációt tartalmazó jelentésoldalhoz, könnyen kivitelezhető. Míg – a másik végletet vizsgálva – 100 felhasználó, akik egyidejűleg 100 eltérő jelentéshez férnek hozzá, amelyek mindegyike 100 vizualizációt tartalmaz a jelentésoldalon, nagyon nehezen kivitelezhető a kapacitás-erőforrások szempontjából.

A kapacitás-rendszergazdáknak ezért számos, a környezetre, a tartalomra és a várt használatra vonatkozó szempontot figyelembe kell venniük. A fő cél a kapacitás-kihasználtság maximalizálása konzisztens lekérdezési idő, elfogadható várakozási idő és kizárási arány mellett. A megfontolandó tényezők a következők lehetnek:

- **A modell méretének és adatainak jellemzői** – Az importálási modelleket teljes mértékben be kell tölteni a memóriába a lekérdezés vagy a frissítés engedélyezéséhez. Az LC/DQ-adatkészletek jelentős mértékű feldolgozási időt és memóriát igényelnek az összetett mértékek vagy RLS-szabályok kiértékeléséhez. A memória- és processzorméretet, valamint az LC/DQ-lekérdezések átviteli sebességét a kapacitásméret szabja meg.
- **Egyidejű aktív modellek** – A különböző importálási modellek egyidejű lekérdezése akkor eredményezi a legnagyobb rugalmasságot és teljesítményt, ha a modellek a memóriában maradnak. Elegendő memóriának kell lennie az összes nagymértékben lekérdezett modell üzemeltetéséhez, és további memóriával kell rendelkezni a frissítéshez.
- **Importálási modell frissítése** – A frissítés típusa (teljes vagy növekményes), a Power Query-lekérdezések időtartama és összetettsége, valamint a számított tábla- vagy oszloplogikák összetettsége mind hatással lehet a memóriára, a processzorhasználatra pedig még inkább. Az egyidejű frissítések korlátait a kapacitásméret határozza meg (1,5 x a háttérrendszeri virtuális magok száma, felfelé kerekítve).
- **Egyidejű lekérdezések** – Számos egyidejű lekérdezés eredményezhet nem válaszoló jelentést, ha a processzor- vagy az LC/DQ-kapcsolatok meghaladják a kapacitáskorlátot. Ez különösen igaz a sok vizualizációt tartalmazó jelentésoldalakra.
- **Adatfolyamok és lapszámozott jelentések** – A kapacitás konfigurálható úgy, hogy támogassa az adatfolyamokat és a lapszámozott jelentéseket, amelyekhez külön-külön konfigurálható a kapacitásmemória maximális mértéke. A memória adatfolyamokhoz dinamikusan, lapszámozott jelentésekhez viszont statikusan van lefoglalva.

Mindemellett a kapacitás-rendszergazdák több kapacitást is létrehozhatnak. Több kapacitással elkülöníthetők a számítási feladatok, valamint garantálhatók az erőforrások a fontosabb számítási feladatok számára. Létrehozhat például két kapacitást: egyet az üzleti szempontból kritikus fontosságú számítási feladatokhoz, egyet pedig az önkiszolgáló BI (SSBI) számítási feladatokhoz. Az üzleti szempontból kritikus kapacitással elkülöníthetők a nagy vállalati modellek, garantálhatók számukra az erőforrások, és szerzői hozzáférés adható kizárólag az informatikai részlegnek. Az SSBI kapacitással egyre több kisméretű modellt üzemeltethet amelyekhez az üzleti elemzők férnek hozzá. Az SSBI kapacitásban időnként tűrhető lekérdezési vagy frissítési várakozás fordulhat elő.

Az idő múlásával a kapacitás-rendszergazdák kiegyensúlyozhatják a munkaterületek elosztását a kapacitások között, ha szabadon mozgatják a tartalmat a munkaterületek között, a munkaterületeket a kapacitások között, vagy vertikálisan fel- vagy leskálázzák a kapacitásokat. A nagyobb modellek üzemeltetéséhez általában vertikális felskálázásra van szükség, a nagyobb mértékű egyidejűséghez pedig horizontális felskálázásra.

Licenc vásárlásával a bérlő virtuális magokhoz juthat. Egy **P3** előfizetés vásárlásával akár négy Premium-kapacitás is létrehozható, például egy P3-as, két P2-es vagy négy P1-es. Mielőtt továbbfejleszt egy P2-es kapacitást egy P3-asra, fontolja meg, hogy nem célszerűbb-e a virtuális magokat elosztani, és létrehozni két P1-es kapacitást.

## <a name="testing-approaches"></a>Tesztelési módszerek

A kapacitás méretének eldöntése után felügyelt környezet létrehozásával tesztelést végezhet. Praktikus és gazdaságos megoldás létrehozni egy Azure- (A SKU) kapacitást, figyelembe véve, hogy a P1 kapacitás mérete megegyezik az A4 kapacitáséval, a P2 és a P3 kapacitások méretei pedig megegyeznek az A5 és az A6 kapacitások méreteivel. Az Azure-kapacitások gyorsan létrehozhatók, számlázásuk pedig óránként történik. Így a tesztelés befejezése után egyszerűen törölhetők, tehát nem járnak további költségekkel.

A teszt tartalma hozzáadható az Azure-kapacitásban létrehozott munkaterületekhez, amit követően egy felhasználó jelentések futtatásával valósághű és reprezentatív, lekérdezéseket tartalmazó számítási feladatokat hozhat létre. Ha importálási modelleket is használ, célszerű mindegyiket frissíteni. Figyelési eszközökkel áttekinthető minden metrika, így könnyebben megérthető az erőforrás-felhasználás.

Fontos tudni, hogy a tesztek megismételhetők. A teszteket célszerű többször futtatni, a futásoknak pedig azonos eredménnyel kell járniuk. Az eredmények átlagából kikövetkeztethető és megbecsülhető, hogy egy számítási feladat hogyan teljesít valós éles körülmények között.

Ha már rendelkezik a tesztelendő kapacitással és jelentésekkel, a [PowerShell terhelés-létrehozási eszközével](https://aka.ms/PowerBILoadTestingTool) gyorsan létrehozhat egy terheléses tesztet. Az eszközzel megbecsülheti, hogy a kapacitás hány példányt tud futtatni az egyes jelentésekből egy óra alatt. Az eszközzel kiértékelheti, hogy a kapacitás milyen szinten képes renderelni egy-egy jelentést, vagy párhuzamosan több jelentést. További információt a [Microsoft Power BI: Premium-kapacitás](https://www.youtube.com/watch?time_continue=1860&v=C6vk6wk9dcw) című videóban találhat.

Összetettebb teszt létrehozásához fejlesszen egy terheléses tesztalkalmazást, amely valósághű számítási feladatot szimulál. További információt a [Load Testing Power BI Applications with Visual Studio Load Test](https://powerbi.microsoft.com/blog/week-4-11-webinars-load-testing-power-bi-applications-with-visual-studio-load-test-and-getting-started-with-cds-for-apps-based-model-driven-apps/) (Power BI-alkalmazások terheléses tesztelése a Visual Studio terheléses tesztjeivel) című webináriumban találhat.

## <a name="acknowledgements"></a>Nyugták

A cikket Peter Myers, a [Bitwise Solutions](https://www.bitwisesolutions.com.au/) Data Platform MVP-je és független BI-szakértője szerezte.

## <a name="next-steps"></a>Következő lépések

> [!div class="nextstepaction"]
> [Premium-kapacitások forgatókönyvei](service-premium-capacity-scenarios.md)   
  
További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)