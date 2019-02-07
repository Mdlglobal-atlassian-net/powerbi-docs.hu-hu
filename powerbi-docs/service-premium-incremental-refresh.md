---
title: Növekményes frissítés a Power BI Premium szolgáltatásban
description: Megismerheti, hogyan használhat rendkívül nagyméretű adatkészleteket a Power BI Premium szolgáltatásban.
author: christianwade
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 10/19/2018
ms.author: chwade
LocalizationGroup: Premium
ms.openlocfilehash: 92bd4043e4cfa37bd8f712491ccbc2990dc0b6a9
ms.sourcegitcommit: 54d44deb6e03e518ad6378656c769b06f2a0b6dc
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/07/2019
ms.locfileid: "55794363"
---
# <a name="incremental-refresh-in-power-bi-premium"></a>Növekményes frissítés a Power BI Premium szolgáltatásban

A növekményes frissítés lehetővé teszi a rendkívül nagyméretű adatkészletek használatát a Power BI Premium szolgáltatásban az alábbi előnyökkel:

- **A frissítés gyorsabb lesz.** Csak a módosult adatokat szükséges frissíteni. Frissítheti például egy 10 éves adatkészletnek csak az utolsó öt napját.

- **A frissítések megbízhatóbbak.** Nem szükséges például hosszú futású kapcsolatokat fenntartani alacsony megbízhatóságú forrásrendszerekkel.

- **Alacsonyabb erőforrásigény.** A kevesebb frissítendő adat csökkenti a frissítési művelet által igényelt memóriamennyiséget és más erőforrásokat.

## <a name="how-to-use-incremental-refresh"></a>A növekményes frissítés használata

A növekményes frissítési szabályzatok a Power BI Desktopban definiálhatók, majd az alkalmazásukhoz közzé kell tenni azokat a Power BI szolgáltatásban.

Első lépésként engedélyezze a növekményes frissítést az előzetes verziójú funkciók között.

![Beállítások – Előzetes verziójú funkciók](media/service-premium-incremental-refresh/preview-features.png)

### <a name="filter-large-datasets-in-power-bi-desktop"></a>Nagyméretű adatkészletek szűrése a Power BI Desktopban

A potenciálisan több milliárd sort tartalmazó nagyméretű adatkészletek nem biztos, hogy betölthetők a Power BI Desktop alkalmazásba, mivel ez az alkalmazás a felhasználó asztali számítógépének erőforrásai által korlátozott. Ezeket az adatkészleteket ezért gyakran szűrjük importáláskor, hogy elférjenek a Power BI Desktopban. Ez a gyakorlat független attól, hogy növekményes frissítést használ-e vagy sem.

#### <a name="rangestart-and-rangeend-parameters"></a>RangeStart és RangeEnd paraméter

A növekményes frissítés Power BI szolgáltatásban való használatához szűrnie kell az adatokat dátum/idő típusú Power Query-paraméterekkel, amelyeknek a **RangeStart** és a **RangeEnd** fenntartott nevet kell adnia, a kis- és nagybetűk különbségére is ügyelve.

A közzététel után a paraméterek értékét automatikusan felülbírálja a Power BI szolgáltatás. Nem szükséges a szolgáltatásban az adatkészlet beállításainál megadnia őket.

Fontos elküldeni a szűrőt a forrásrendszernek, amikor elküldi a lekérdezéseket a frissítési műveletekhez. A szűrés elküldéséhez az adatforrásnak támogatnia kell a „query folding” (lekérdezésdelegálás) elnevezésű technika használatát. A legtöbb SQL-lekérdezéseket támogató adatforrás támogatja a lekérdezésdelegálást. Bizonyos adatforrások, például az egybesimított fájlok, a blobok, a webes és az OData-csatornák alapvetően nem támogatják a használatát. Mivel az egyes adatforrások különböző szinten támogatják a lekérdezésdelegálást, ajánlott ellenőrizni azt, hogy a szűrési logika szerepel-e a forráslekérdezésekben. Ha az adatforrás háttérfolyamata nem támogatja a szűrőt, akkor az nem küldhető tovább. Ilyen esetben az adategyesítési motor a szűrő helyi alkalmazásával kompenzál, amelyhez valószínűleg a teljes adatkészletet le kell kérni az adatforrásból. Ez jelentősen lelassíthatja a növekményes frissítést, és a folyamat kifogyhat az erőforrásokból a Power BI szolgáltatásban vagy a helyszíni adatátjárón (ha azt használja).

A szűrő használatával tartományokra bontja az adatokat a Power BI szolgáltatásban. Nem a szűrt dátumoszlop frissítésének támogatására lett tervezve. A frissítés beszúrásként és törlésként lesz értelmezve (nem frissítésként). Ha a törlés az előzménytartományban és nem a növekményes tartományban történik, az nem lesz kiválasztva. Ez a partíciókulcs-ütközés miatt adatfrissítési hibákat okozhat.

A Power Query-szerkesztőben válassza a **Paraméterek kezelése** lehetőséget a paraméterek alapértelmezett értékkel való definiálásához.

![Paraméterek kezelése](media/service-premium-incremental-refresh/manage-parameters.png)

A paraméterek definiálása után alkalmazhatja a szűrőt úgy, hogy az **Egyéni szűrő** menüpontot választja a kívánt oszlopnál.

![Egyéni szűrő](media/service-premium-incremental-refresh/custom-filter.png)

A sorokat úgy kell szűrnie, hogy az oszlopérték *nem korábbi, mint* szűrőjéhez a **RangeStart** paramétert választja, a *korábban, mint* szűrőjéhez pedig a **RangeEnd** paramétert.

![Sorok szűrése](media/service-premium-incremental-refresh/filter-rows.png)

> [!TIP]
> A paraméterek adattípusának dátum/időnek kell lennie, de átkonvertálhatja őket, hogy megfeleljenek az adatforrás követelményeinek. Az alábbi Power Query-függvény például átkonvertálja a dátum/idő értéket oly módon, hogy az egész szám típusú helyettes kulcsot alkosson *ééééhhnn* formátumban, melynek használata elterjedt gyakorlat az adatraktárakban. A függvényt a szűrési lépéssel hívhatja meg.
>
> `(x as datetime) => Date.Year(x)*10000 + Date.Month(x)*100 + Date.Day(x)`

Válassza a **Bezárás és alkalmazás** lehetőséget a Power Query-szerkesztőben. Ezután az adatkészlet egy alkészletével dolgozhat a Power BI Desktopban.

### <a name="define-the-refresh-policy"></a>Frissítési szabályzat definiálása

A növekményes frissítést a táblák helyi menüjében érheti el, kivéve az élő kapcsolatú modellek esetében.

![Frissítési szabályzat](media/service-premium-incremental-refresh/refresh-policy.png)

#### <a name="incremental-refresh-dialog"></a>Növekményes frissítés párbeszédpanel

Ekkor megjelenik a Növekményes frissítés párbeszédpanel. A párbeszédpanelt az alábbi váltógombbal engedélyezheti.

![Frissítés részletei](media/service-premium-incremental-refresh/refresh-details.png)

> [!NOTE]
> Ha a tábla Power Query-kifejezése nem hivatkozik a fenntartott nevű paraméterekre, a váltógomb letiltva jelenik meg.

A fejlécszöveg rövid magyarázatot nyújt az alábbiakról:

- A növekményes frissítést csak a prémium szintű kapacitáson tárolt munkaterületek támogatják. A frissítési szabályzatokat a Power BI Desktopban definiálhatja, és a frissítési művelet alkalmazza őket a szolgáltatásban.

- Ha sikerül is letöltenie a növekményes frissítési szabályzatot tartalmazó PBIX-fájlt a Power BI szolgáltatásból, nem fog megnyílni a Power BI Desktopban. Hamarosan már a letöltés sem fog működni. A jövőben elképzelhető, hogy a rendszer támogatni fogja ezt a használati módot, de tartsa szem előtt, hogy ezek az adatkészletek akkorára nőhetnek, hogy problémákba ütközhet, ha átlagos asztali számítógépen próbálja letölteni és megnyitni őket.

#### <a name="refresh-ranges"></a>Tartományok frissítése

A következő példa egy frissítési szabályzatot mutat be, az adatok öt naptári évig tartó tárolásához, valamint az aktuális év adatait a jelenlegi dátumig, és 10 nap adatainak növekményes frissítését. Az első frissítési művelet az előzményadatokat tölti be. A további frissítések növekményesek lesznek, és (napi szinten történő futtatás mellett) az alábbi műveleteket végzik el.

- Új napnyi adatok hozzáadása.

- Az adatok frissítése az aktuális dátumtól számított 10 napra visszamenőleg.

- Az aktuális dátumtól számított öt évnél régebbi naptári évek eltávolítása. Ha például az aktuális dátum 2019. január 1., a 2013-as évet eltávolítja a rendszer.

A Power BI szolgáltatás által végzett első frissítés tovább tarthat, mert itt öt teljes naptári évet kell importálni. A későbbi frissítések végrehajtása már sokkal rövidebb időt fog igénybe venni.

![Tartományok frissítése](media/service-premium-incremental-refresh/refresh-ranges.png)

**Előfordulhat, hogy ezeknek a tartományoknak a definiálásán kívül semmilyen más teendője nincs. Ez esetben közvetlenül a lentebb lévő közzétételi lépésekhez ugorhat. A többi legördülő lista speciális funkciók használatához készült.**

### <a name="advanced-policy-options"></a>Speciális szabályzabeállítások

#### <a name="detect-data-changes"></a>Adatváltozások észlelése

10 napnyi adat növekményes frissítése természetesen sokkal hatékonyabb, mint öt évnyi adat teljes frissítése. De lehet, hogy ennél többet is tudunk tenni. Az **Adatváltozások észlelése** jelölőnégyzet bejelölésével megadhat egy dátum/idő oszlopot, amely alapján a rendszer azonosítani tudja, hogy mely napokon történt adatváltozás, és csak ezeket a napokat frissíti. Ez azt feltételezi, hogy található ilyen oszlop a forrásrendszerben (mely jellemzően megtalálható, naplózási célokból). **Ez nem lehet ugyanaz az oszlop, amelyet az adatoknak a RangeStart/RangeEnd paraméterekkel való particionálására használt.** Ennek az oszlopnak a maximális értékét a rendszer kiértékeli a növekményes tartományban lévő minden egyes időszak esetében. Ha nem változott az utolsó frissítés óta, akkor nem szükséges frissíteni az időszakot. A jelen példában ez tovább csökkentheti a növekményesen frissített napok számát 10-ről akár 2-re.

![Változások észlelése](media/service-premium-incremental-refresh/detect-changes.png)

> [!TIP]
> A jelenlegi architektúra megköveteli az adatváltozás-észlelési oszlop megőrzését és memóriában való gyorsítótárazását. A számosság és a memóriahasználat csökkentéséhez tanácsos lehet megfontolnia az alábbi technikák egyikének használatát.
>
> Csak az oszlop maximális értékét őrizze meg frissítéskor, például egy Power Query-függvénnyel.
>
> Csökkentse a pontosságot egy olyan szintre, amely a frissítési gyakorisággal kapcsolatos követelmények vonatkozásában még elfogadható.
>
> Tervezzük az adatváltozás-észleléshez használható egyéni lekérdezések definiálásának támogatását. Ez segítene abban, hogy ne kelljen megőrizni az oszlopértéket.

#### <a name="only-refresh-complete-periods"></a>Csak teljes időszakok frissítése

Tegyük fel, hogy a frissítés mindennap hajnali 4 órára van ütemezve. Ha a forrásrendszerbe e 4 óra során adat kerül be, akkor elképzelhető, hogy azt nem szeretné figyelembe venni. Egyes üzleti mérőszámok – például a hordók száma naponta az olaj- és gáziparban – nem értelmezhetők részleges naponként.

További példaként tegyük fel, hogy az adatokat egy pénzügyi rendszerből frissítjük, ahol az elmúlt hónapra vonatkozó adatok a hónap 12. napján vannak jóváhagyva. Ilyen esetben beállíthatja a növekményes tartományt 1 hónapra, és a frissítést ütemezheti úgy, hogy a hónap 12. napján fusson le. Ennek a jelölőnégyzetnek a bejelölése esetén például a januári adatokat a rendszer csak február 12-én frissíti.

![Teljes időszakok](media/service-premium-incremental-refresh/complete-periods.png)

> [!NOTE]
> A szolgáltatás az UTC időzóna szerint hajtja végre a frissítési műveleteket. Ez befolyásolhatja az aktuális dátumot és a teljes időszakokat. Tervezzük egy olyan funkció hozzáadását, amellyel felülbírálható az aktuális dátum a frissítési műveletekben.

## <a name="publish-to-the-service"></a>Közzététel a szolgáltatásban

Mivel a növekményes frissítés egy prémium szintű szolgáltatás, a közzétételi párbeszédpanel csak prémium szintű kapacitásban tárolt munkaterület kiválasztását támogatja.

![Közzététel a szolgáltatásban](media/service-premium-incremental-refresh/publish.png)

Ezután készen áll a modell frissítésére. Az első frissítés tovább tarthat az előzményadatok importálása miatt. A későbbi frissítések azonban sokkal gyorsabban lesznek a növekményes frissítésnek köszönhetően.

## <a name="query-timeouts"></a>Lekérdezési időtúllépések

A [frissítéssel kapcsolatos hibák elhárítását tárgyaló cikkünk](https://docs.microsoft.com/power-bi/refresh-troubleshooting-refresh-scenarios) kitér rá, hogy a Power BI időtúllépés miatt leállíthatja a frissítési műveleteket. A lekérdezéseket emellett az adatforrás alapértelmezett időtúllépési beállítása is korlátozhatja. A legtöbb relációs forrás támogatja az időtúllépési érték M kifejezésben való felülbírálását. Az alábbi kifejezés például az [SQL Server data-access függvényével](https://msdn.microsoft.com/query-bi/m/sql-database) 2 órára állítja az időtúllépést. A szabályzatban megadott tartomány minden egyes időszaka elküld egy lekérdezést, mely tartalmazza ezt az időtúllépési beállítást.

```
let
    Source = Sql.Database("myserver.database.windows.net", "AdventureWorks", [CommandTimeout=#duration(0, 2, 0, 0)]),
    dbo_Fact = Source{[Schema="dbo",Item="FactInternetSales"]}[Data],
    #"Filtered Rows" = Table.SelectRows(dbo_Fact, each [OrderDate] >= RangeStart and [OrderDate] < RangeEnd)
in
    #"Filtered Rows"
```
