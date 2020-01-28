---
title: Útmutató a több-a-többhöz kapcsolatokhoz
description: Útmutató több-a-többhöz típusú modellkapcsolatok kialakításához.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/25/2019
ms.author: v-pemyer
ms.openlocfilehash: 6ce82516413fe43cfbc1336e2f6f51003277fb4a
ms.sourcegitcommit: 3d6b27e3936e451339d8c11e9af1a72c725a5668
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/17/2020
ms.locfileid: "76161294"
---
# <a name="many-to-many-relationship-guidance"></a>Útmutató a több-a-többhöz kapcsolatokhoz

Ez a cikk a Power BI Desktopot használó adatmodellezőknek szól. Három különböző több-a-többhöz típusú modellezési forgatókönyvet ismertet. Emellett útmutatást nyújt a kapcsolatok sikeres kialakításához.

> [!NOTE]
> A modellkapcsolatok bemutatása nem képezi a cikk részét. Ha nincs tisztában a kapcsolatokkal, azok tulajdonságaival és konfigurálási módjával, először olvassa el a [Modellbeli kapcsolatok a Power BI Desktopban](../desktop-relationships-understand.md) című cikket.
>
> Emellett fontos, hogy ismerje a csillagséma-kialakítást is. További információ: [A csillagséma és a Power BI-ban játszott szerepének a bemutatása](star-schema.md) című cikkben talál további információt.

Három több-a-többhöz típusú kapcsolatot különböztetünk meg. Ezek a következő esetekben merülhetnek fel:

- [Két dimenzió típusú tábla összekapcsolásakor](#relate-many-to-many-dimensions)
- [Két tény típusú tábla összekapcsolásakor](#relate-many-to-many-facts)
- [Részletes tény típusú táblák összekapcsolásakor](#relate-higher-grain-facts), ha a tény típusú tábla részletesebb adatokkal tárolja a sorokat, mint a dimenzió típusú tábla

## <a name="relate-many-to-many-dimensions"></a>Több-a-többhöz típusú dimenziók összekapcsolása

Tekintsünk meg egy példát az első több-a-többhöz típusú forgatókönyvről. A klasszikus forgatókönyv két entitást kapcsol össze: banki ügyfeleket és bankszámlákat. Az ügyfelek több bankszámlával is rendelkezhetnek, egy bankszámlához pedig több ügyfél is tartozhat. Ha egy számlához több ügyfél tartozik, őket általában _közös számlatulajdonosnak_ nevezzük.

Az ilyen entitások modellezése egyszerű. Egy dimenzió típusú tábla tárolja a számlákat, és egy másik az ügyfeleket. Ahogy a dimenzió típusú tábláknál ez jellemző, minden tábla tartalmaz egy azonosító oszlopot. A két tábla közötti kapcsolat modellezéséhez egy harmadik táblára van szükség. Ezt a táblázatot általában _áthidaló táblának_ nevezzük. Ebben a példában ez egy-egy sorban tárolja az ügyfél–számla párokat. Érdekes módon, ha ez a tábla csak azonosító oszlopokat tartalmaz, [_tények nélküli ténytáblának nevezzük_](star-schema.md#factless-fact-tables).

Íme egy egyszerű modelldiagram a három tábláról.

![A modelldiagram három táblázatot tartalmaz. A terv a következő bekezdésben olvasható.](media/relationships-many-to-many/bank-account-customer-model-example.png)

Az első táblázat neve **Account**, és két oszlopot tartalmaz: **AccountID** és **Account**. A második táblázat neve **AccountCustomer**, és két oszlopot tartalmaz: **AccountID** és **CustomerID**. A harmadik táblázat neve **Customer**, és két oszlopot tartalmaz: **CustomerID** és **Customer**. A táblák között nincs kapcsolat.

Kettő egy-a-többhöz kapcsolatot adunk a táblákhoz, hogy összekössük azokat. Íme az összekapcsolt táblák frissített modelldiagramja. Hozzáadtunk egy **Transaction** nevű ténytáblát is. Ez fióktranzakciókat tartalmaz. Az áthidaló táblázat és az összes azonosító oszlop rejtve van.

![A modelldiagram így jelenleg négy táblázatot tartalmaz. Egy-a-többhöz kapcsolatokkal összekötöttük az összes táblát.](media/relationships-many-to-many/bank-account-customer-model-related-tables-1.png)

A kapcsolati szűrőpropagálás működésének bemutatása érdekében a modelldiagramot úgy módosítottuk, hogy láthatók legyenek benne a táblázat sorai.

> [!NOTE]
> A táblázatsorok nem jeleníthetők meg a Power BI Desktop modelldiagramjában. Ebben a cikkben az egyértelmű példák jegyében jelenítettük meg őket.

![A modelldiagramban most látszanak a táblázatsorok. A sorok adatait az alábbi bekezdésben ismertetjük.](media/relationships-many-to-many/bank-account-customer-model-related-tables-2.png)

A négy táblázat sorainak adatai a következő listában találhatók:

- Az **Account** táblázat két sorból áll:
  - Az **AccountID** 1 az Account-01-hez tartozik
  - Az **AccountID** 2 az Account-02-höz tartozik
- A **Customer** táblázat két sort tartalmaz:
  - A **CustomerID** 91 a Customer-91-hez tartozik
  - A **CustomerID** 92 a Customer-92-höz tartozik
- Az **AccountCustomer** táblázat három sorból áll:
  - Az **AccountID** 1 a **CustomerID** 91-hez van társítva
  - Az **AccountID** 1 a **CustomerID** 92-höz van társítva
  - Az **AccountID** 3 a **CustomerID** 92-höz van társítva
- A **Transaction** táblázat három sort tartalmaz:
  - **Date** January 1 2019, **AccountID** 1, **Amount** 100
  - **Date** February 2 2019, **AccountID** 2, **Amount** 200
  - **Date** March 3 2019, **AccountID** 1, **Amount** -25

Nézzük meg, mi történik a modell lekérdezése esetén.

Az alábbiakban a **Transaction** tábla **Amount** oszlopát összegző két vizualizációt láthat. Az első vizualizáció bankszámla szerint csoportosít, az **Amount** oszlopok összege így a _számlaegyenlegnek_ felel meg. A második vizualizáció ügyfél szerint csoportosít, az **Amount** oszlopok összege így az _ügyfélegyenlegnek_ felel meg.

![Két jelentésvizualizációt láthatunk egymás mellett. A vizualizációkat az alábbi bekezdésben ismertetjük.](media/relationships-many-to-many/bank-account-customer-model-queried-1.png)

Az első vizualizáció neve **Account Balance** (Számlaegyenleg), és két oszlopot tartalmaz: **Account** és **Amount**. Ennek eredménye a következő:

- Az Account-01 egyenlege 75
- Az Account-02 egyenlege 200
- Az összeg 275

A második vizualizáció neve **Customer Balance** (Ügyfélegyenleg), és két oszlopot tartalmaz: **Customer** és **Amount**. Ennek eredménye a következő:

- A Customer-91 egyenlege 275
- A Customer-92 egyenlege 275
- Az összeg 275

A táblázatsorokra és az **Account Balance** vizualizációra pillantva láthatjuk, hogy az eredmény helyes a bankszámlák és a végösszeg szempontjából is. Ez azért van, mert a számlacsoportosítások a számla **Transaction** táblázatának szűrőpropagálását eredményezik.

Azonban valami nem stimmel a **Customer Balance** vizualizációval. A **Customer Balance** vizualizáció minden ügyfelének egyenlege megegyezik az egyenlegek összegével. Ez csak akkor lehetne pontos, ha minden ügyfél minden bankszámla közös tulajdonosa lenne. Ebben a példában azonban nem erről van szó. A probléma a szűrőpropagáláshoz köthető. Ez ugyanis nem jut el a **Transaction** tábláig.

Kövesse a kapcsolati szűrő irányát a **Customer** táblától a **Transaction** tábláig. Látnia kell, hogy az **Account** és az **AccountCustomer** tábla közti kapcsolat nem a megfelelő irányba van propagálva. A kapcsolat szűrőjének irányát **Both** (Mindkettő) beállításra kell állítani.

![Frissítettük a modelldiagramot. Egyetlen módosítást végeztünk az Account és az AccountCustomer tábla között. Így most már mindkét irányba végez szűrést.](media/relationships-many-to-many/bank-account-customer-model-related-tables-3.png)

![Ugyanazt a két jelentésvizualizációt láthatunk egymás mellett. Az első vizualizáció nem módosult. A második vizualizáció más eredményt mutat, amelyet a következő bekezdések ismertetnek.](media/relationships-many-to-many/bank-account-customer-model-queried-2.png)

Ahogy vártuk, az **Account Balance** vizualizáció nem módosult.

A **Customer Balance** vizualizációk azonban már az alábbi eredményt mutatják:

- A Customer-91 egyenlege 75
- A Customer-92 egyenlege 275
- Az összeg 275

A **Customer Balance** vizualizáció már a megfelelő eredményt mutatja. Kövesse a szűrő irányát, és tekintse meg az ügyfélegyenlegek kiszámításának módját. Tartsa észben, hogy a vizualizáció összege _minden ügyfélre_ vonatkozik.

Akik nem ismerik a modellkapcsolatokat, azt gondolhatják, hogy az eredmény hibás. Az alábbi kérdés merülhet fel bennük: _A **Customer-91** és **Customer-92** egyenlegének összege miért nem 350 (75 + 275)?_

A válasz a több-a-többhöz típusú kapcsolatban rejlik. Minden ügyfélegyenleg képviselheti több számlaegyenleg összegét, így az ügyfélegyenlegek _nem additívak_.

### <a name="relate-many-to-many-dimensions-guidance"></a>Több-a-többhöz típusú dimenziók összekapcsolása – útmutató

Dimenzió típusú táblázatok közötti, több-a-többhöz típusú kapcsolatokhoz kövesse az alábbi útmutatást:

- Adja hozzá a több-a-többhöz típusú, kapcsolódó entitásokat modelltáblázatként, és győződjön meg róla, hogy tartalmaz egy egyéni azonosítóval rendelkező oszlopot
- Adjon hozzá egy áthidaló táblázatot a társított entitások tárolása érdekében
- Hozzon létre egy-a-többhöz típusú kapcsolatokat a három tábla között
- Konfiguráljon **egy** kétirányú kapcsolatot a ténytáblázatok irányába haladó szűrőpropagálás engedélyezéséhez
- Ha nem szerepelhetnek hiányzó azonosítóértékek, állítsa az azonosítóoszlopok **Is Nullable** tulajdonságát FALSE (HAMIS) értékre. Az adatfrissítés így meghiúsul hiányzó értékek esetén
- Rejtse el az áthidaló táblázatot (kivéve, ha az a jelentéshez szükséges további oszlopokat vagy mértékeket tartalmaz)
- Rejtse el a jelentéshez nem használható azonosítóoszlopokat (például a helyettes kulcsként használt azonosítók esetében)
- Ha úgy dönt, hogy láthatóként szeretne hagyni egy azonosítóoszlopot, ügyeljen rá, hogy az a kapcsolat „egy” oldalán legyen, és mindig rejtse el a „több” oldali oszlopot. Ez garantálja az optimális szűrőteljesítményt.
- A zavar és félreértések elkerülése végett nyújtson magyarázatokat a jelentésfelhasználóknak – szövegmezővel rendelkező leírásokat, vagy [vizualizáció-fejlécben található elemleírásokat](report-page-tooltips.md) adhat hozzá

Nem ajánlott a több-a-többhöz típusú dimenziótáblákat közvetlenül összekapcsolni. Ehhez a kialakításhoz egy több-a-többhöz számosságú kapcsolatot kell konfigurálni. Ez elméletileg lehetséges, azonban azt feltételezi, hogy az összekapcsolt oszlopok ismétlődő értékeket tartalmaznak. Általánosan elfogadott kialakítási gyakorlat azonban, hogy a dimenzió típusú táblák rendelkeznek egy azonosítóoszloppal. A dimenziótábláknak mindig a kapcsolat „egy” oldalaként kell használniuk az azonosítóoszlopot.

## <a name="relate-many-to-many-facts"></a>Több-a-többhöz típusú tények összekapcsolása

A második több-a-többhöz típusú forgatókönyvben két tény típusú táblát kapcsolunk össze. Ezek közvetlenül is összekapcsolhatók. Ez a kialakítási technika hasznos gyors és egyszerű adatfeltáráshoz. Azonban általában nem javasoljuk ezt a módszert. Ennek okát a szakasz egy későbbi részében magyarázzuk meg.

Vegyünk például egy két tény típusú táblát tartalmazó esetet: **Order** és **Fulfillment**. Az **Order** tábla rendeléssoronként egy sort tartalmaz, a **Fulfillment** tábla pedig nulla vagy több sort tartalmazhat rendeléssoronként. Az **Order** tábla sorai az értékesítési megrendelések. A **Fulfillment** tábla sorai a kézbesített megrendelések. Egy több-a-többhöz kapcsolat összekapcsolja a két **OrderID** oszlopot, a szűrőpropagálás pedig csak az **Order** táblából indul ki (az **Order** szűri a **Fulfillmentet**).

![A modelldiagram két táblázatot tartalmaz: Order és Fulfillment. Egy több-a-többhöz típusú kapcsolat összekapcsolja a két OrderID oszlopot, a szűrés iránya pedig az Order felől a Fulfillment felé mutat.](media/relationships-many-to-many/order-fulfillment-model-example.png)

A kapcsolat számossága több-a-többhöz értékre van állítva, hogy támogassa mindkét táblában az ismételt **OrderID** értékek tárolását. Az **Order** táblában szerepelhetnek ismétlődő **OrderID** értékek, mivel egy rendeléshez több sor is tartozhat. A **Fulfillment** táblában szerepelhetnek ismétlődő **OrderID** értékek, mivel a rendelésekhez több sor is tartozhat, a rendeléssorok pedig teljesíthetők több csomaggal.

Most tekintsük meg a táblasorokat. A **Fulfillment** tábla rendeléssorai több csomaggal teljesíthetők. (A rendeléssor hiánya azt jelenti, hogy a megrendelés még nem teljesült.)

![A modelldiagramban most látszanak a táblázatsorok. A sorok adatait az alábbi bekezdésben ismertetjük.](media/relationships-many-to-many/order-fulfillment-model-related-tables.png)

A két táblázat sorainak adatai a következő listában találhatók:

- Az **Order** táblázat öt sorral rendelkezik:
  - **OrderDate** January 1 2019, **OrderID** 1, **OrderLine** 1, **ProductID** Prod-A, **OrderQuantity** 5, **Sales** 50
  - **OrderDate** January 1 2019, **OrderID** 1, **OrderLine** 2, **ProductID** Prod-B, **OrderQuantity** 10, **Sales** 80
  - **OrderDate** February 2 2019, **OrderID** 2, **OrderLine** 1, **ProductID** Prod-B, **OrderQuantity** 5, **Sales** 40
  - **OrderDate** February 2 2019, **OrderID** 2, **OrderLine** 2, **ProductID** Prod-C, **OrderQuantity** 1, **Sales** 20
  - **OrderDate** March 3 2019, **OrderID** 3, **OrderLine** 1, **ProductID** Prod-C, **OrderQuantity** 5, **Sales** 100
- A **Fulfillment** táblázat négy sorral rendelkezik:
  - **FulfillmentDate** January 1 2019, **FulfillmentID** 50, **OrderID** 1, **OrderLine** 1, **FulfillmentQuantity** 2
  - **FulfillmentDate** February 2 2019, **FulfillmentID** 51, **OrderID** 2, **OrderLine** 1, **FulfillmentQuantity** 5
  - **FulfillmentDate** February 2 2019, **FulfillmentID** 52, **OrderID** 1, **OrderLine** 1, **FulfillmentQuantity** 3
  - **FulfillmentDate** January 1 2019, **FulfillmentID** 53, **OrderID** 1, **OrderLine** 2, **FulfillmentQuantity** 10

Nézzük meg, mi történik a modell lekérdezése esetén. Íme egy táblavizualizáció, amely az **Order** táblázat **OrderID** oszlopának rendelési és teljesítési mennyiségeit hasonlítja össze.

![A táblázatos vizualizáció három oszlopot tartalmaz: OrderID, OrderQuantity, és FulfillmentQuantity. Három sort láthatunk; rendelésenként egyet. A 2 és a 3 OrderID azonosítóval rendelkező rendelések nincsenek teljesítve.](media/relationships-many-to-many/order-fulfillment-model-queried.png)

A vizualizáció pontos eredményt ad. A modell hasznossága azonban korlátozott – szűrést vagy csoportosítást csak az **Order** tábla **OrderID** oszlopa alapján végezhet.

### <a name="relate-many-to-many-facts-guidance"></a>Több-a-többhöz típusú tények összekapcsolása – útmutató

Általában nem ajánlott két tény típusú táblát közvetlenül, több-a-többhöz típusú számossággal összekapcsolni. Ennek legfőbb oka, hogy a modell nem lesz rugalmas a jelentésvizualizációk szűrésekor vagy csoportosításakor. A példában a vizualizációk csak az **Order** tábla **OrderID** oszlopa alapján szűrhetnek vagy csoportosíthatnak. A másodlagos ok az adatok minőségére vonatkozik. Ha az adatintegritással problémák adódnak, előfordulhat, hogy bizonyos sorok kimaradnak a lekérdezés során a _gyenge kapcsolatok_ miatt. További információ: [A kapcsolatok kiértékelése](../desktop-relationships-understand.md#relationship-evaluation).

A tény típusú táblák közvetlen összekapcsolása helyett [csillagséma](star-schema.md) típusú tervezési alapelvek bevezetését javasoljuk. Ezt dimenzió típusú táblák hozzáadásával teheti meg. A dimenzió típusú táblák ezután egy-a-többhöz típusú kapcsolatokkal összekapcsolhatók a tény típusúakkal. Ez egy robusztus tervezési módszer, amely rugalmas jelentéskészítési lehetőségeket nyújt. Így Ön bármilyen dimenzió típusú oszlop alapján szűrhet vagy csoportosíthat, és bármilyen kapcsolódó, tény típusú táblát összegezhet.

Vizsgáljunk meg egy jobb megoldást.

![Egy modelldiagram hat táblázatot tartalmaz: OrderLine, OrderDate, Order, Fulfillment, Product, és FulfillmentDate. Mindegyik tábla össze van kapcsolva. A terv a következő bekezdésben olvasható.](media/relationships-many-to-many/order-fulfillment-model-improved.png)

Figyelje meg a következő tervbeli változásokat:

- A modell négy táblával bővült: **OrderLine**, **OrderDate**, **Product**, és **FulfillmentDate**
- A négy további tábla mind dimenzió típusú, és egy-a-többhöz kapcsolattal kapcsolódik a tény típusú táblákhoz
- Az **OrderLine** tábla egy **OrderLineID** oszlopot, amely az **OrderID** 100-zal megszorzott értékét képviseli, valamint az **OrderLine** értéket tartalmazza, amely a rendeléssorok egyedi azonosítója
- Az **Order** és a **Fulfillment** tábla már tartalmaz egy **OrderLineID** oszlopot, az **OrderID** és **OrderLine** oszlopot pedig nem
- A **Fulfillment** tábla már tartalmazza az **OrderDate** és **ProductID** oszlopot
- A **FulfillmentDate** tábla csak a **Fulfillment** táblához kapcsolódik
- Mindegyik egyedi azonosítót tartalmazó oszlop el van rejtve

A csillagsémás tervezési alapelvek alkalmazása a következő előnyökkel jár:

- A jelentésvizualizációk a dimenzió típusú táblák bármelyik látható oszlopa alapján _szűrhetnek vagy csoportosíthatnak_
- A jelentésvizualizációk a tény típusú táblák bármelyik látható oszlopa alapján _összegezhetnek_
- Az **OrderLine**, **OrderDate**, vagy **Product** táblára alkalmazott szűrők mindkét tény típusú táblához propagálhatnak
- Mindegyik kapcsolat egy-a-többhöz típusú, és mindegyik _erős kapcsolat_. Az adatintegritásbeli problémák nem lesznek elrejtve. További információ: [A kapcsolatok kiértékelése](../desktop-relationships-understand.md#relationship-evaluation).

## <a name="relate-higher-grain-facts"></a>Részletesebb tények összekapcsolása

Ez a több-a-többhöz típusú forgatókönyv nagyban eltér a két korábbitól.

Vegyük alapul az alábbi négy táblát tartalmazó példát: **Date**, **Sales**, **Product**, és **Target**. A **Date** és a **Product** dimenzió típusú táblák, és egy-a-többhöz típusú kapcsolatokkal kapcsolódnak a **Sales** tény típusú táblához. Ez eddig egy jó csillagsémás kialakítás. A **Target** tábla azonban még nincs másikhoz kapcsolva.

![Egy modelldiagram négy táblázatot tartalmaz: Date, Sales, Product, és Target. A Target tábla nem kapcsolódik egyik táblához sem. A terv a következő bekezdésben olvasható.](media/relationships-many-to-many/sales-targets-model-example.png)

A **Target** tábla három oszlopot tartalmaz: **Category**, **TargetQuantity**, és **TargetYear**. A táblázat sorai évek és termékkategóriák szintű részletességgel rendelkeznek. Más szóval célok – amelyek az értékesítési teljesítményt mérik – vannak megadva minden évben minden termékkategóriához.

![A Target tábla három oszloppal rendelkezik: TargetYear, Category, és TargetQuantity. A 2019-es és 2020-as év céljait hat sor rögzíti, mindegyik három kategóriában.](media/relationships-many-to-many/sales-targets-model-target-rows.png)

Mivel a **Target** tábla magasabb szinten tárolja az adatokat a dimenzió típusú tábláknál, nem hozható létre egy-a-többhöz kapcsolat. Ez csak a kapcsolatok egyikére igaz. Tekintsük meg, hogyan kapcsolható össze a **Target** tábla a dimenzió típusú táblákkal.

### <a name="relate-higher-grain-time-periods"></a>Részletesebb időszakok összekapcsolása

A **Date** és a **Target** tábla kapcsolatának egy-a-többhöz típusúnak kell lennie. Ez amiatt van, hogy a **TargetYear** oszlop értékei dátumok. Ebben a példában a **TargetYear** oszlop minden értéke a célul szolgáló év első dátuma.

> [!TIP]
> Ha a napi szintnél részletesebben tárol tényeket, állítsa az oszlop adattípusát **Date** (vagy dátum típusú kulcsok esetén **Whole number**) értékre. Az oszlopban az időszak első napját képviselő érték szerepeljen. Egy egy éves időszak például január 1-ként legyen rögzítve, egy egy hónapos időszak pedig a hónap első napjaként.

Ügyeljen azonban arra, hogy a hónap vagy dátum szintű szűrők értelmes eredményt adjanak. Speciális számítási logika nélkül a jelentésvizualizációk azt mutathatják, hogy a céldátumok az egyes évek első napjai. Az összes többi nap – és január kivételével hónap – BLANK (ÜRES) értékként összegzi a célmennyiséget.

Az alábbi mátrixvizualizáció bemutatja, mi történik, ha a jelentés felhasználója egy évet részletez hónapok szerint. A vizualizáció a **TargetQuantity** oszlopot foglalja össze. (Az [Adatot nem tartalmazó elemek megjelenítése](../desktop-show-items-no-data.md) lehetőség engedélyezve van a mátrixsorokhoz.)

![A mátrixvizualizáción láthatjuk, hogy a 2020-as év célmennyisége 270. Ha ezt 2020 hónapjaira részletezzük, a január értéke 270, a többi hónapszintű cél mennyisége pedig BLANK.](media/relationships-many-to-many/sales-targets-model-matrix-blank-months-bad.png)

Ennek elkerülése érdekében azt javasoljuk, hogy mértékekkel vezérelje a tényadatok összegzését. Ennek egyik módja a BLANK eredményezése alacsonyabb szintű időszakok lekérdezésekor. Egy másik módszer – amelyet kifinomult DAX definiál – az értékek felosztása az alacsonyabb szintű időszakok között.

Vegyük például az [ISFILTERED](/dax/isfiltered-function-dax) DAX-függvényt használó mértékdefiníciót. Ez csak akkor ad vissza értéket, ha a **Date** vagy a **Month** oszlop nincs szűrve.

```dax
Target Quantity =
IF(
    NOT ISFILTERED('Date'[Date])
        && NOT ISFILTERED('Date'[Month]),
    SUM(Target[TargetQuantity])
)
```

Az alábbi mátrixvizualizáció már a **Target Quantity** mértéket használja. Ezen láthatjuk, hogy minden havi célmennyiség BLANK.

![A mátrixvizualizáción láthatjuk, hogy a 2020-as év célmennyisége 270. Ha ezt 2020 hónapjaira részletezzük, minden hónapszintű cél mennyisége BLANK.](media/relationships-many-to-many/sales-targets-model-matrix-blank-months-good.png)

### <a name="relate-higher-grain-non-date"></a>Részletesebb, nem dátum típusú adatok összekapcsolása

Dimenzió típusú tábla nem dátum típusú oszlopainak (a dimenzió típusú táblánál részletesebb) tény típusú táblához való összekapcsolásakor eltérő kialakítási megközelítésre van szükség.

A **Product** és a **Target** tábla **Category** oszlopai ismétlődő értékeket tartalmaznak. Így nincs „egy” oldala az egy-a-többhöz típusú kapcsolatnak. Ebben az esetben több-a-többhöz típusú kapcsolatot kell létrehozni. A kapcsolatnak egyetlen irányba kell propagálnia a szűrőket: a dimenzió típusú táblától a tény típusú tábla felé.

![A modelldiagram egy darabja a Target és a Product táblát jeleníti meg. A két táblát egy több-a-többhöz kapcsolat köti össze. A szűrő iránya a Product táblától a Target felé mutat.](media/relationships-many-to-many/sales-targets-model-relate-non-date.png)

Most tekintsük meg a táblasorokat.

![A modelldiagram két táblázatot tartalmaz: Target és Product. A két Category oszlopot egy több-a-többhöz kapcsolat köti össze. A sorok adatait az alábbi bekezdésben ismertetjük.](media/relationships-many-to-many/sales-targets-model-relate-non-date-tables.png)

A **Target** táblában négy sor található: célévenként (2019 és 2020) két sor, valamint két kategória (Clothing és Accessories). A **Product** táblában három termék található. Kettő a Clothing (Ruházat) kategóriába tartozik, egy pedig az Accessories (Kiegészítők) kategóriába. A ruhaszínek egyike zöld, míg a másik kettő kék.

A **Product** tábla **Category** oszlopa alapján csoportosító táblavizualizáció az alábbi eredményt adja.

![A táblázatos vizualizáció két oszlopot tartalmaz: Category és TargetQuantity. Az Accessories 60, a Clothing is 40, az összeg pedig 100.](media/relationships-many-to-many/sales-targets-model-visual-category-targets.png)

A vizualizáció helyes eredményt ad. Most vizsgáljuk meg, mi történik, ha a **Product** tábla **Color** oszlopát használjuk a célmennyiség csoportosításához.

![A táblázatos vizualizáció két oszlopot tartalmaz: Color és TargetQuantity. A Blue 100, a Green 40, az összeg pedig 100.](media/relationships-many-to-many/sales-targets-model-visual-color-targets-bad.png)

A vizualizáció helytelenül reprezentálja az adatokat. Mi történik?

A **Product** tábla **Color** oszlopának egyik szűrője két sort eredményez. Az egyik sor a Clothing kategóriához tartozik, a másik pedig az Accessories kategóriához. A két kategóriaérték szűrőként van propagálva a **Target** táblához. Más szóval: mivel a kék színt két kategória termékei használják, _ezek a kategóriák_ szűrik a célokat.

Ennek elkerülése érdekében azt javasoljuk, hogy mértékekkel vezérelje a tényadatok összegzését.

Vizsgáljuk meg a következő mértékdefiníciót. Így a **Product** tábla minden, a kategóriaszint alatti oszlopát teszteljük szűrőkhöz.

```dax
Target Quantity =
IF(
    NOT ISFILTERED('Product'[ProductID])
        && NOT ISFILTERED('Product'[Product])
        && NOT ISFILTERED('Product'[Color]),
    SUM(Target[TargetQuantity])
)
```

Az alábbi táblavizualizáció már a **Target Quantity** mértéket használja. Ezen láthatjuk, hogy minden szín célmennyisége BLANK.

![A táblázatos vizualizáció két oszlopot tartalmaz: Color és TargetQuantity. A Blue BLANK, a Green BLANK, az összeg pedig 100.](media/relationships-many-to-many/sales-targets-model-visual-color-targets-good.png)

A végső modellterv az alábbihoz hasonlít.

![A modelldiagramon láthatjuk, hogy a Date és a Target tábla között egy egy-a-többhöz kapcsolat áll. A Product és a Target tábla több-a-többhöz típusú kapcsolattal van összekapcsolva, a szűrés iránya pedig a Producttól a Target felé mutat.](media/relationships-many-to-many/sales-targets-model-example-final.png)

### <a name="relate-higher-grain-facts-guidance"></a>Részletesebb tények összekapcsolása – útmutató

Ha dimenzió típusú táblát kell tény típusú táblával összekapcsolnia, az utóbbi pedig nagyobb részletességű sorokat tárol, mint az előbbi, kövesse az alábbi útmutatást:

- Részletesebb ténydátumok esetén:
  - A tény típusú táblában az időszak első dátumát tárolja
  - Hozzon létre egy egy-a-többhöz típusú kapcsolatot a dátumtábla és a tény típusú tábla között
- Egyéb részletesebb tények esetén:
  - Hozzon létre egy több-a-többhöz típusú kapcsolatot a dimenzió típusú tábla és a tény típusú tábla között
- Mindkét típus esetén:
  - Az összegzést mértéklogikával vezérelje – ha alacsonyabb szintű, dimenzió típusú oszlopokkal szűr vagy csoportosít, eredményezzen BLANK értéket
  - Rejtse el az összefoglalható, tény típusú táblák oszlopait – így csak mértékekkel összegezhető a tény típusú tábla

## <a name="next-steps"></a>Következő lépések

Ezzel a cikkel kapcsolatosan a következő forrásanyagokban talál további információt:

- [Modellbeli kapcsolatok a Power BI Desktopban](../desktop-relationships-understand.md)
- [A csillagséma és a Power BI-ban játszott szerepének a bemutatása](star-schema.md)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
