---
title: Modellbeli kapcsolatok a Power BI Desktopban
description: A Power BI Desktopban elérhető modellkapcsolatokról szóló elmélet bevezetése
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/15/2019
ms.author: v-pemyer
ms.openlocfilehash: 991f8b47337ba563ecfd223d69d687269a44ed78
ms.sourcegitcommit: 87b7cb4a2e626711b98387edaa5ff72dc26262bb
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/10/2020
ms.locfileid: "79041608"
---
# <a name="model-relationships-in-power-bi-desktop"></a>Modellbeli kapcsolatok a Power BI Desktopban

Ez a cikk a Power BI Desktopot használó importálásiadat-modellezőknek szól. Ez egy fontos modelltervezési témakör, amely kulcsfontosságú az intuitív, pontos és optimális modellek készítéséhez.

Az optimális modellfelépítésről, többek között a táblák szerepköreiről és kapcsolatairól részletesebben a [csillagsémát és annak fontosságát a Power BI-ban](guidance/star-schema.md) bemutató cikkben olvashat.

## <a name="relationship-purpose"></a>A kapcsolatok célja

A Power BI-kapcsolatok egyszerűen más modelltáblákba propagálják a modelltáblák oszlopaira alkalmazott szűrőket. A szűrők akkor propagálnak, ha van követendő kapcsolati útvonal, amely magában foglalhat több táblába való propagálást is.

A kapcsolati útvonalak mindig determinisztikusak, vagyis a szűrők mindig ugyanúgy lesznek propagálva, véletlenszerű eltérések nélkül. Ám a kapcsolatok le is tilthatóak, vagy a szűrőkörnyezet módosítható bizonyos DAX-funkciókat használó modellszámításokkal. További információkat a cikk későbbi szakaszában, a [Kapcsolódó DAX-funkciók](#relevant-dax-functions) című témakörben talál.

> [!IMPORTANT]
> Fontos tudni, hogy a modellkapcsolatok nem kényszerítik ki az adatintegritást. További információkat a cikk későbbi szakaszában, a [Kapcsolatok kiértékelése](#relationship-evaluation) című témakörben talál. Ez a témakör azt mutatja be, hogy a modellkapcsolatok hogyan viselkednek, amikor az adatokkal kapcsolatban adatintegritási problémák merülnek fel.

Nézzük meg egy animált példán, hogy a kapcsolatok hogyan propagálják a szűrőket.

![A szűrők kapcsolatok általi propagálása, animált példa](media/desktop-relationships-understand/animation-filter-propagation.gif)

Ebben a példában a modell négy táblából áll: **Category**, **Product**, **Year** és **Sales**. A **Category** tábla a **Product** táblához kapcsolódik, a **Product** tábla pedig a **Sales** táblához. Emellett a **Year** tábla is kapcsolódik a **Sales** táblához. Az összes kapcsolat egy-a-többhöz típusú (ennek részleteiről a cikk későbbi részében lesz szó).

Tegyük fel, hogy egy például Power BI kártyavizualizáció által előállított lekérdezés lekéri a teljes értékesítési mennyiséget azokra az értékesítési megrendelésekre vonatkozóan, amelyek a **Cat-A** kategóriába, illetve a **CY2018** évbe tartoznak. Ezért vannak szűrők alkalmazva a **Category** és **Year** táblákra. A **Category** táblára alkalmazott szűrő a **Product** táblába propagál, ahol elkülönít két terméket, amelyek a **Cat-A** kategóriához vannak rendelve. Ezután a **Product** tábla szűrője a **Sales** táblába propagál, ahol elkülönít összesen két értékesítési sort ezekhez a termékekhez. Ez a két értékesítési sor jelöli a **Cat-A** kategóriához rendelt termékek értékesítését. Az együttes mennyiségük 14 egység. Ugyanakkor a **Year** tábla szűrője a **Sales** táblába propagál, amelyet tovább szűr. Ennek eredménye az az egyetlen értékesítési sor, amely a **Cat-A** kategóriába tartozó, **CY2018** évben megrendelt termékekre vonatkozik. A lekérdezés 11 egységet ad vissza eredményként. Érdemes tudni, hogy amikor egy táblára több szűrőt alkalmaznak (ahogyan ebben a példában a **Sales** táblára), az mindig AND művelet, amelyhez az szükséges, hogy az összes feltétel igaz legyen.

### <a name="disconnected-tables"></a>Nem kapcsolódó táblák

Szokatlan megoldás, ha egy modelltábla nem áll kapcsolatban másik modelltáblával. Az érvényes modelltervekben az ilyen táblákra _nem kapcsolódó táblaként_ hivatkozunk. A nem kapcsolódó táblának nem célja, hogy szűrőket propagáljon más modelltáblákba. A felhasználó által megadott adatok fogadására szolgál (esetlegesen szeletelő vizualizációval), és lehetővé teszi a modellszámítások számára, hogy értelmezhetően használják fel a megadott értéket. Például vegyünk egy nem kapcsolódó táblát, amely valutaátváltási árfolyamok értékeit tartalmazza. Ha szűrő van alkalmazva egy árfolyamérték alapján való szűréshez, az értéket egy mértékkifejezés értékesítési értékek átváltására használhatja.

A Power BI Desktop lehetőségelemzési paramétere olyan funkció, amely egy nem kapcsolódó táblát hoz létre. További információt a [Lehetőségelemzési paraméter létrehozása és használata változók vizualizációjához a Power BI Desktopban](desktop-what-if.md) című cikkben találhat.

## <a name="relationship-properties"></a>A kapcsolatok tulajdonságai

A modellkapcsolatok egy tábla egy oszlopát egy másik tábla oszlopával kapcsolják össze. (Ez a feltétel mindössze egyetlen speciális esetben nem érvényesül: a DirectQuery-modellekben lévő többoszlopos kapcsolatok esetén. Ezzel kapcsolatban lásd a [COMBINEVALUES](/dax/combinevalues-function-dax) DAX-funkcióról szóló cikket.)

> [!NOTE]
> Egy adott táblában lévő oszlopot nem lehet egy _ugyanabban a táblában_ található oszloppal összekapcsolni. Ezt olykor összekeverik a relációs adatbázis külső kulcsaira vonatkozó korlátozás meghatározásával, amely a tábla tekintetében önmagára hivatkozó. Ezt a relációsadatbázis-koncepciót szülő–gyerek kapcsolatok tárolására lehet használni (például minden alkalmazotti rekord össze van kapcsolva egy „felettes” alkalmazottal). Az ilyen típusú kapcsolaton alapuló modellhierarchiát nem lehet modellkapcsolatok létrehozásával összeállítani. Ezzel kapcsolatban lásd a [szülő és gyermek funkciókat](/dax/parent-and-child-functions-dax) ismertető cikket.

### <a name="cardinality"></a>Számosság

Minden modellkapcsolatot egy számosságtípussal kell meghatározni. Négyféle számosságtípus érhető el, amelyek a „forrás” és a „cél” oszlopok adatjellemzőit adják meg. Az „egy” oldal azt jelenti, hogy az oszlop egyedi értékeket tartalmaz; a „kettő” oldal azt jelenti, az oszlop duplikált értékeket tartalmazhat.

> [!NOTE]
> Ha egy adatfrissítési művelet duplikált értékeket kísérel meg betölteni az „egy” oldali oszlopba, a teljes adatfrissítés sikertelen lesz.

A négy lehetőség leírását – rövidített jelöléseikkel együtt – a következő felsorolás tartalmazza:

- Egy-a-többhöz (1:\*)
- Több-az-egyhez (\*:1)
- Egy-az-egyhez (1:1)
- Több-a-többhöz (\*:\*)

Amikor létrehoz egy kapcsolatot a Power BI Desktopban, a tervező automatikusan felismeri és beállítja a számosságtípust. A tervező lekérdezi a modellből, hogy mely oszlopok tartalmaznak egyedi értékeket. Az importálási modellekhez belső tárolási statisztikákat használ a DirectQuery-modellekhez pedig profilkészítési lekérdezéseket küld az adatforrásnak. Esetenként azonban előfordul, hogy az eredmény helytelen. Ez azért történhet, mert a táblákba még nincsenek betöltve adatok, vagy azért, mert azok az oszlopok, amelyektől azt várta, hogy duplikált értékeket tartalmazzanak, jelenleg egyedi értékeket tartalmaznak. Bármelyikről is legyen szó, a számosságtípus frissíthető, ha az „egy” oldali oszlopok egyedi értékeket tartalmaznak (vagy ha a táblákba még nincsenek betöltve adatsorok).

Az **egy-a-többhöz** és a **több-az-egyhez** számossági lehetőségek lényegében azonosak, és ezek a leggyakoribb számosságtípusok.

Egy-a-többhöz vagy több-az-egyhez kapcsolatok konfigurálásakor azt válassza, amely megegyezik az oszlopok összekapcsolásának sorrendjével. Fontolja meg, hogy konfigurálná a **Product** tábla és a **Sales** tábla közötti kapcsolatot a mindkét táblában megtalálható **ProductID** oszlop használatával. A számosságtípus _egy-a-többhöz_ lenne, mivel a **ProductID** oszlop a **Product** táblában egyedi értékeket tartalmaz. Ha a táblákat fordított irányban kapcsolná össze, a **Sales** táblát a **Product** táblával, akkor a számosság _több-az-egyhez_ lenne.

Az **egy-az-egyhez** kapcsolat azt jelenti, hogy mindkét oszlop egyedi értékeket tartalmaz. Ez a számosságtípus nem gyakori, és valószínűleg kevéssé optimális modelltervet eredményez a redundáns adatok tárolása miatt. A számosságtípusok használatával kapcsolatban az [Útmutató egy-az-egyhez kapcsolatokhoz](guidance/relationships-one-to-one.md) című cikk nyújt további információt.

A **több-a-többhöz** kapcsolat azt jelenti, hogy mindkét oszlop tartalmazhat duplikált értékeket. Ez a számosságtípus nem gyakori. Leginkább összetett modellkövetelmények tervezésekor hasznos. A számosságtípus használatával kapcsolatos útmutatót itt találja meg: [Útmutató a több-a-többhöz kapcsolatokhoz](guidance/relationships-many-to-many.md).

> [!NOTE]
> A több-a-többhöz számosságtípus jelenleg nem támogatott a Power BI jelentéskészítő kiszolgálóhoz tervezett modellek esetén.

> [!TIP]
> A Power BI Desktop modellnézetében egy kapcsolat számosságtípusát a kapcsolatvonal két oldalán található jelzők (1 vagy \*) alapján lehet megállapítani. Annak megtekintéséhez, hogy mely oszlopok vannak összekapcsolva, válassza ki a kapcsolatot jelző vonalat (vagy vigye fölé az egérmutatót) az oszlopok kiemeléséhez.

### <a name="cross-filter-direction"></a>Szűrő irányának keresztezése

Minden modellkapcsolatot a keresztszűrés irányával kell meghatározni. Ez a beállítás meghatározza az irány(oka)t, amelybe a szűrők propagálni fognak. Az elérhető keresztszűrési lehetőségek a számosságtípustól függnek.

| Számosságtípus | Keresztszűrési lehetőségek |
| --- | --- |
| Egy-a-többhöz (vagy több-az-egyhez) | Egyirányú<br>Mindkettő |
| Egy-az-egyhez | Mindkettő |
| Több-a-többhöz | Egy (1. tábla–2. tábla)<br>Egy (2. tábla–1. tábla)<br>Mindkettő |

Az _Egyirányú_ keresztszűrés jelentése „egy irányba”, míg a _Mindkettő_ jelentése „mindkét irányba”. Azt a kapcsolatot, amely mindkét irányba szűr, _kétirányúnak_ hívjuk.

Egy-a-többhöz kapcsolatok esetében a keresztszűrés iránya mindig az „egy” oldaltól indul, illetve választhatóan a „több” oldaltól is (kétirányú). Egy-az-egyhez kapcsolatok esetében a keresztszűrés iránya mindig mindkét táblától értendő. Végül több-a-többhöz kapcsolatok esetében a keresztszűrés iránya indulhat a táblák egyikétől (bármelyiktől), vagy mindkettőtől. Amikor a számosságtípusban található „egy” oldal, a szűrők mindig arról az oldalról fognak propagálni.

Ha a keresztszűrű beállítása **Kétirányú**, egy további tulajdonság is rendelkezésre áll. Ez kétirányú szűrést alkalmazhat olyan esetben, amikor sorszintű biztonsági (RLS) szabályok vannak érvényben. Az RLS-sel kapcsolatban a [Sorszintű biztonság (RLS) a Power BI Desktoppal](desktop-rls.md) című cikk nyújt további információt.

A kapcsolat keresztszűrési irányának módosítását – beleértve a szűréspropagálás letiltását – modellszámítással is el lehet végezni. Ez a [CROSSFILTER](/dax/crossfilter-function) DAX-funkcióval érhető el.

A kétirányú kapcsolatok negatív hatással lehetnek a teljesítményre. Továbbá a kétirányú kapcsolatok konfigurálására tett kísérlet nem egyértelmű szűrőpropagációs útvonalakat eredményezhet. Ilyenkor előfordulhat, hogy a Power BI Desktop nem tudja véglegesíteni a kapcsolat módosítását, amit hibaüzenettel jelez. Egyes esetekben azonban a Power BI Desktop lehetővé teszi nem egyértelmű kapcsolati útvonalak meghatározását táblák között. Az egyértelműség hiányának észlelésére és az útvonalfeloldásra kiható elsőbbségi szabályokról a cikk későbbi, [elsőbbségi szabályokat](#precedence-rules) ismertető témakörében lesz szó.

Ajánlott a kétirányú szűrést csak szükség esetén használni. További információ: [Útmutatás kétirányú kapcsolatokhoz](guidance/relationships-bidirectional-filtering.md).

> [!TIP]
> A Power BI Desktop modellnézetében egy kapcsolat keresztszűrési irányának megállapításához tekintse meg a nyílhegyeket a kapcsolatot jelölő vonal mentén. Egyetlen nyílhegy egyirányú szűrőt jelent, a nyílhegy irányában; a dupla nyílhegy pedig kétirányú kapcsolatot jelez.

### <a name="make-this-relationship-active"></a>A kapcsolat aktívvá tétele

Egyszerre csak egy aktív szűrőpropagálási útvonal lehet két modelltábla között. Lehetséges további kapcsolati útvonalakat is létrehozni, ám az összes ilyen kapcsolatot _inaktívként_ kell konfigurálni. Az inaktív kapcsolatokat csak a modellszámítások kiértékelése során lehet aktívvá tenni. Ez a [USERELATIONSHIP](/dax/userelationship-function-dax) DAX-funkcióval végezhető el.

További információ: [Útmutató aktív vagy inaktív kapcsolatokhoz](guidance/relationships-active-inactive.md).

> [!TIP]
> A Power BI Desktop modellnézetében meg lehet állapítani, hogy egy kapcsolat aktív vagy inaktív állapotú. Az aktív kapcsolatot folyamatos vonal, míg az inaktív kapcsolatot szaggatott vonal jelöli.

### <a name="assume-referential-integrity"></a>Hivatkozási integritás feltételezése

A _Hivatkozási integritás feltételezése_ tulajdonság csak egy-a-többhöz és egy-az-egyhez kapcsolatok esetén érhető el két olyan DirectQuery tárolási módú tábla között, amelyek ugyanarra az adatforrásra épülnek. Amikor ez engedélyezve van, az adatforrásnak küldött natív lekérdezések KÜLSŐ ILLESZTÉS helyett BELSŐ ILLESZTÉSSEL kapcsolják össze egymással a két táblát. Ennek a tulajdonságnak az engedélyezése általában javítja a lekérdezések teljesítményét, bár ez az adatforrás pontos jellemzőitől is függ.

Mindig engedélyezze ezt a tulajdonságot, ha a két tábla között az adatbázis külső kulcsára vonatkozó korlátozás van érvényben. A tulajdonság akkor is engedélyezhető, ha nem létezik külső kulcsra vonatkozó korlátozás, ha biztos benne, hogy van adatintegritás.

> [!IMPORTANT]
> Ha az adatintegritás veszélybe kerül, a belső illesztés el fogja távolítani a táblák közötti nem egyező sorokat. Tekintsük például egy modell **Sales** tábláját a **ProductID** oszlopértékkel, amely nem létezett a kapcsolódó **Product** táblában. A **Product** táblából a **Sales** táblába történő szűrőpropagálás el fogja távolítani ismeretlen termékekhez tartozó értékesítési sorokat. Ez azt eredményezi, hogy az értékesítési eredmények a valósnál alacsonyabbak lesznek.
>
> További információkat a [Hivatkozási integritás feltételezése beállítások a Power BI Desktopban](desktop-assume-referential-integrity.md) című cikkben talál.

## <a name="relevant-dax-functions"></a>Kapcsolódó DAX-funkciók

Több DAX-funkció is használható a modellkapcsolatokhoz. Az egyes funkciók rövid leírását az alábbi felsorolás tartalmazza:

- [RELATED](/dax/related-function-dax): Lekéri az értéket az „egy” oldalról.
- [RELATEDTABLE](/dax/relatedtable-function-dax): A „több” oldalról kér le egy sorokból álló táblát.
- [USERELATIONSHIP](/dax/userelationship-function-dax): Kikényszeríti egy adott inaktív modellkapcsolat használatát.
- [CROSSFILTER](/dax/crossfilter-function): Módosítja a kapcsolat keresztszűrési irányát (egyirányúra vagy mindkettőre), vagy letiltja a szűrőpropagálást (egyik sem).
- [COMBINEVALUES](/dax/combinevalues-function-dax): Két vagy több szöveges sztringet egyetlen szöveges sztringgé egyesít. Ennek a funkciónak az a célja, hogy támogassa a többoszlopos kapcsolatokat a DirectQuery-modellekben.
- [TREATAS](/dax/treatas-function): Egy táblakifejezés eredményét alkalmazza szűrőként egy nem kapcsolódó tábla oszlopaira.
- [Szülő és gyermek funkciók](/dax/parent-and-child-functions-dax): Egymáshoz kapcsolódó funkciók családja, amelyet számított oszlopok létrehozására lehet használni, egy szülő–gyermek hierarchia megvalósításához. Ezután ezekből az oszlopokból rögzített szintű hierarchiát lehet létrehozni.

## <a name="relationship-evaluation"></a>A kapcsolatok kiértékelése

Kiértékelési szempontból a modellkapcsolatok _erősként_ vagy _gyengeként_ kategorizálhatóak. Ez a kapcsolati tulajdonság nem konfigurálható, hanem a számosságtípusból és a két összekapcsolt tábla adatforrásából lesz származtatva. Fontos ismerni a kiértékelési típust, mivel ha az adatintegritás veszélybe kerül, az teljesítménybeli vagy egyéb következményeket vonhat maga után. Ezeknek a kockázatoknak és integritással kapcsolatos következményeknek a leírása ebben a témakörben található.

A kapcsolatok kiértékelésének teljes körű megértéséhez először is egy kis modellezési elmélet szükséges.

Az importálási vagy DirectQuery-modellek adatforrásként a Vertipaq-gyorsítótárat, vagy a forrásadatbázist használják. A Power BI mindkét esetben képes megállapítani, hogy létezik-e a kapcsolatnak „egy” típusú oldala.

Ám az összetett modellek különféle tárolási módokat (importálás, DirectQuery vagy kettős) használó táblákból vagy több DirectQuery-forrásból is állhatnak. Minden forrás, beleértve az importálási adatokhoz tartozó Vertipaq-gyorsítótárat is, _adatszigetnek_ tekinthető. Ez alapján a modellkapcsolatok _szigeten belüliként_ vagy _szigetek közöttiként_ kategorizálhatóak. A szigeten belüli kapcsolat egy adott adatszigeten belüli két táblát kapcsol össze, míg a szigetek közötti kapcsolat két, különböző adatszigeten található táblát kapcsol össze. Fontos tudni, hogy az importálási és a DirectQuery-modellekben lévő kapcsolatok mindig a szigeten belüli kategóriába tartoznak.

Lássunk egy példát összetett modellre.

![Példa egy két szigetből álló összetett modellre](media/desktop-relationships-understand/data-island-example.png)

Ebben a példában az összetett modell két szigetből áll: egy Vertipaq-adatszigetből és egy DirectQuery-forrásadatszigetből. A Vertipaq-adatsziget három táblából, a DirectQuery-forrásadatsziget két táblából áll. Létezik egy szigetek közötti kapcsolat, amely a Vertipaq-adatsziget egyik tábláját a DirectQuery-forrásadatsziget egy táblájával kapcsolja össze.

### <a name="strong-relationships"></a>Erős kapcsolatok

Egy modellkapcsolat akkor _erős_, ha a lekérdezési motor meg tudja határozni a kapcsolat „egy” típusú oldalát. Megerősítéssel rendelkezik arról, hogy az „egy” oldali oszlop egyedi értékeket tartalmaz. Az összes egy-a-többhöz típusú szigetek közötti kapcsolat erős kapcsolat.

A következő példában két erős kapcsolat látható, mindkettő az **S** betűvel van jelölve. A kapcsolatok között találunk még a Vertipaq-szigeten belüli egy-a-többhöz kapcsolatot, valamint a DirectQuery-forrásban található egy-a-többhöz kapcsolatot.

![Példa egy két szigetből álló összetett modellre, amelyben az erős kapcsolatok meg vannak jelölve](media/desktop-relationships-understand/data-island-example-strong.png)

Az importálási modellek esetén, ahol az összes adat tárolása a Vertipaq-gyorsítótárban történik, minden erős kapcsolathoz egy adatstruktúra jön létre az adatok frissítésekor. Az adatstruktúrák az oszlop-az-oszlophoz értékek indexelt leképezéseiből állnak, és az a céljuk, hogy gyorsítsák a táblák illesztését lekérdezéskor.

A lekérdezés során az erős kapcsolatok lehetővé teszik, hogy _táblabővítésre_ kerüljön sor. A táblabővítés eredményeként létrejön egy virtuális tábla, amely tartalmazza az alaptábla natív oszlopait, majd kapcsolódó táblákba bővül. Importálási táblák esetén ez a lekérdezési motorban megy végbe. DirectQuery-táblák esetén a forrásadatbázisnak elküldött natív lekérdezésben történik (ha a **Hivatkozási integritás feltételezése** beállítás nincs engedélyezve). Ezután a lekérdezési motor a bővített táblát használja: szűrőket alkalmaz, és a bővített tábla oszlopaiban lévő értékek alapján csoportosít.

> [!NOTE]
> Az inaktív kapcsolatok is bővülnek akkor is, ha az adott kapcsolatot egy számítás sem használja. A kétirányú kapcsolatok nem befolyásolják a táblabővítést.

Egy-a-többhöz kapcsolat esetén a táblabővítés a „több” oldalról az „egy” oldalra történik BAL OLDALI KÜLSŐ ILLESZTÉS szemantika használatával. Ha a „több” oldaltól az „egy” oldal felé nem létezik megegyező érték, az „egy” oldali táblához egy üres virtuális sor lesz hozzáadva.

Egy-az-egyhez típusú szigeten belüli kapcsolatok esetében is történik táblabővítés, azonban a TELJES KÜLSŐ ILLESZTÉS szemantikával. Ez biztosítja, hogy szükség esetén mindkét oldalon hozzá legyenek adva üres virtuális sorok.

Az üres virtuális sorok gyakorlatilag _ismeretlen tagok_. Az ismeretlen tagok a hivatkozásintegritás megsértését jelentik, amikor a „több” oldali értékhez nincs megfelelő „egy” oldali érték. Ideális esetben ezek az üres soroknak nem kellene létezniük. A forrásadatok megtisztításával vagy javításával megszüntethetőek.

Egy animált példán keresztül tekintsük át, hogyan működik a táblabővítés.

![Táblabővítés, animált példa](media/desktop-relationships-understand/animation-expanded-table.gif)

Ebben a példában a modell három táblából áll: **Category**, **Product** és **Sales**. A **Category** tábla a **Product** táblához kapcsolódik egy-a-többhöz kapcsolattal, a **Product** tábla pedig a **Sales** táblához kapcsolódik egy-a-többhöz kapcsolattal. A **Category** tábla két soros, a **Product** tábla három soros, a **Sales** tábla pedig öt soros. Az összes kapcsolat mindkét oldalán vannak egymásnak megfelelő adatok, tehát a hivatkozásintegritás nem sérül. Egy lekérdezéskor bővített tábla kerül feltárásra. Ez a tábla mindhárom tábla oszlopait tartalmazza. Ez gyakorlatilag a három táblában található adatok denormalizált nézete. Egy új sor lesz hozzáadva a **Sales** táblához, és ez olyan gyártási azonosító értékkel (9) rendelkezik, amelyhez nincs megfelelő érték a **Product** táblában. Ez a hivatkozásintegritás megsértését jelenti. A bővített táblában az új sor (Blank) értékeket tartalmaz a **Category** és a **Product** tábla oszlopaihoz.

### <a name="weak-relationships"></a>Gyenge kapcsolatok

Egy modellkapcsolat akkor _gyenge_, ha nincs garantált „egy” oldala. Ez két okból fordulhat elő:

- A kapcsolat több-a-többhöz számosságtípust használ (akkor is, ha az egyik vagy mindkét oszlop tartalmaz egyedi értékeket)
- A kapcsolat szigetek közötti típusú (ez kizárólag összetett modellek esetén lehetséges)

A következő példában két gyenge kapcsolat látható, mindkettőt a **W** betű jelöli. Ide tartozik a Vertipaq-szigeten belüli több-a-többhöz kapcsolat, valamint az egy-a-többhöz szigetek közötti kapcsolat.

![Példa egy két szigetből álló összetett modellre, amelyben a gyenge kapcsolatok meg vannak jelölve](media/desktop-relationships-understand/data-island-example-weak.png)

Importálási modellek esetén a gyenge kapcsolatokhoz nem jönnek létre adatstruktúrák. Tehát a táblaillesztéseket a lekérdezéskor kell feloldani.

Gyenge kapcsolatok esetében sosem történik táblabővítés. A táblaillesztések BELSŐ ILLESZTÉS használatával jönnek létre, és emiatt nem lesznek hozzáadva üres virtuális sorok a hivatkozásintegritás megsértésének kompenzálására.

További korlátozások is léteznek a gyenge kapcsolatokra vonatkozóan:

- A RELATED DAX-funkciót nem lehet az oszlopértékek „egy” oldalának lekérésére használni
- Az RLS kikényszerítésére topológiakorlátozások vonatkoznak

> [!NOTE]
> A Power BI Desktop modellnézetében nem mindig lehet megállapítani, hogy egy modellkapcsolat erős vagy gyenge. A több-a-többhöz kapcsolat mindig gyenge, ahogyan az egy-a-többhöz kapcsolat is, ha szigetek közötti kapcsolatról van szó. Annak megállapításához, hogy szigetek közötti kapcsolatról van-e szó, meg kell vizsgálni a táblatárolási módokat és az adatforrásokat.

### <a name="precedence-rules"></a>Elsőbbségi szabályok

A kétirányú kapcsolatok többszörös – és ezáltal nem egyértelmű – szűrőpropagálási útvonalakat vezethetnek be a modelltáblák között. A következő lista azokat az elsőbbségi szabályokat mutatja be, amelyeket a Power BI az egyértelműség hiányának feltárásához és az útvonalfeloldáshoz használ:

1. Több-az-egyhez és egy-az-egyhez kapcsolatok, beleértve a gyenge kapcsolatokat is
2. Több-a-többhöz kapcsolatok
3. Kétirányú kapcsolatok az ellenkező irányban (tehát a „több” oldalról)

### <a name="performance-preference"></a>Teljesítménypreferencia

A következő lista szűrőpropagálási teljesítmény szerint rangsorolja a kapcsolatokat a leggyorsabbtól a leglassabbig:

1. Egy-a-többhöz típusú szigetek közötti kapcsolatok
2. Több-a-többhöz számosságú kapcsolatok
3. Köztes táblával elért több-a-többhöz modellkapcsolatok, amelyek között van legalább egy kétirányú kapcsolat
4. Szigetek közötti kapcsolatok

## <a name="next-steps"></a>Következő lépések

Erről a cikkről a következő forrásanyagokban talál további információt:

- [A csillagséma és a Power BI-ban játszott szerepének a bemutatása](guidance/star-schema.md)
- [Útmutató egy-az-egyhez kapcsolatokhoz](guidance/relationships-one-to-one.md)
- [Útmutató a több-a-többhöz kapcsolatokhoz](guidance/relationships-many-to-many.md)
- [Útmutató aktív vagy inaktív kapcsolatokhoz](guidance/relationships-active-inactive.md)
- [Útmutatás kétirányú kapcsolatokhoz](guidance/relationships-bidirectional-filtering.md)
- [Kapcsolatok hibaelhárítási útmutatója](guidance/relationships-troubleshoot.md)
- Videó: [A Power BI-kapcsolatok használatakor ajánlott és kerülendő megoldások](https://www.youtube.com/watch?v=78d6mwR8GtA)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
- Javaslatai vannak? [A Power BI javítására vonatkozó ötletek beküldése](https://ideas.powerbi.com/)
