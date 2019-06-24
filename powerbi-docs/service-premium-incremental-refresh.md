---
title: Növekményes frissítés a Power BI Premium szolgáltatásban
description: Megismerheti, hogyan használhat rendkívül nagyméretű adatkészleteket a Power BI Premium szolgáltatásban.
author: christianwade
manager: kfile
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 05/10/2019
ms.author: chwade
LocalizationGroup: Premium
ms.openlocfilehash: 55676dc2ba2978fb2847543c670726582c589d53
ms.sourcegitcommit: 81ba3572531cbe95ea0b887b94e91f94050f3129
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/06/2019
ms.locfileid: "66751141"
---
# <a name="incremental-refresh-in-power-bi-premium"></a>Növekményes frissítés a Power BI Premium szolgáltatásban

A növekményes frissítés lehetővé teszi a rendkívül nagyméretű adatkészletek használatát a Power BI Premium szolgáltatásban az alábbi előnyökkel:

- **Gyorsabb frissítés** – Csak a módosult adatokat szükséges frissíteni. Frissítheti például egy 10 éves adatkészletnek csak az utolsó öt napját.

- **Megbízhatóbb frissítés** – Nem szükséges a továbbiakban hosszú futású kapcsolatokat fenntartani alacsony megbízhatóságú forrásrendszerekkel.

- **Csökkentett erőforrás-felhasználás** – A kevesebb frissítendő adat csökkenti a frissítési művelet által igényelt memóriamennyiséget és más erőforrásokat.

## <a name="configure-incremental-refresh"></a>A növekményes frissítés konfigurálása

A növekményes frissítési szabályzatok a Power BI Desktopban definiálhatók, majd az alkalmazásukhoz közzé kell tenni azokat a Power BI szolgáltatásban.

Első lépésként engedélyezze a növekményes frissítést az **előzetes verziójú funkciók** között.

![Beállítások – Előzetes verziójú funkciók](media/service-premium-incremental-refresh/preview-features.png)

### <a name="filter-large-datasets-in-power-bi-desktop"></a>Nagyméretű adatkészletek szűrése a Power BI Desktopban

A potenciálisan több milliárd sort tartalmazó nagyméretű adatkészletek nem biztos, hogy betölthetők egy Power BI Desktop-modellbe, mivel a PBIX-fájl a felhasználó asztali számítógépének memória-erőforrásai által korlátozott. Ezeket az adatkészleteket ezért gyakran szűrjük az importáláskor. Ez a fajta szűrés független attól, hogy növekményes frissítést használ-e vagy sem. Növekményes frissítés esetén a Power Query dátum/idő paramétereinek segítségével végez szűrést.

#### <a name="rangestart-and-rangeend-parameters"></a>RangeStart és RangeEnd paraméter

A növekményes frissítés esetén az adatokat dátum/idő típusú Power Query-paraméterekkel szűrheti, amelyeknek a **RangeStart** és a **RangeEnd** fenntartott nevet kell adnia, a kis- és nagybetűk különbségére is ügyelve. Ezekkel a paraméterekkel szűrhetők a Power BI Desktopba importált adatok, valamint dinamikusan tartományokba particionálhatók, miután közzétette őket a Power BI szolgáltatásban. A paraméterértékeket a szolgáltatás helyettesíti az egyes partíciók szűréséhez. A közzététel után a paraméterek értékét automatikusan felülbírálja a Power BI szolgáltatás. Nem szükséges a szolgáltatásban az adatkészlet beállításainál megadnia őket. A közzététel után a paraméterek értékét automatikusan felülbírálja a Power BI szolgáltatás. 

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

#### <a name="filter-date-column-updates"></a>A dátum oszlop frissítéseinek szűrése

A dátum oszlop szűrőjének használatával dinamikusan tartományokra bontja az adatokat a Power BI szolgáltatásban. A növekményes frissítés nem támogat olyan eseteket, amelyekben a szűrt dátum oszlop a forrásrendszerben van frissítve. A frissítés beszúrásként és törlésként lesz értelmezve (nem tényleges frissítésként). Ha a törlés az előzménytartományban és nem a növekményes tartományban történik, az nem lesz kiválasztva. Ez a partíciókulcs-ütközés miatt adatfrissítési hibákat okozhat.

#### <a name="query-folding"></a>Lekérdezésdelegálás

Fontos elküldeni a partíciószűrőket a forrásrendszernek, amikor elküldi a lekérdezéseket a frissítési műveletekhez. A szűrés elküldéséhez az adatforrásnak támogatnia kell a lekérdezésdelegálás használatát. A legtöbb SQL-lekérdezéseket támogató adatforrás támogatja a lekérdezésdelegálást. Azonban bizonyos adatforrások, például az egybesimított fájlok, a blobok, a webes és az OData-csatornák alapvetően nem támogatják a használatát. Ha az adatforrás háttérfolyamata nem támogatja a szűrőt, akkor az nem küldhető tovább. Ilyen esetben az adategyesítési motor a szűrő helyi alkalmazásával kompenzál, amelyhez valószínűleg a teljes adatkészletet le kell kérni az adatforrásból. Ez jelentősen lelassíthatja a növekményes frissítést, és a folyamat kifogyhat az erőforrásokból a Power BI szolgáltatásban vagy a helyszíni adatátjárón (ha azt használja).

Mivel az egyes adatforrások különböző szinten támogatják a lekérdezésdelegálást, ajánlott ellenőrizni azt, hogy a szűrési logika szerepel-e a forráslekérdezésekben. Az egyszerűbb folyamat érdekében a Power BI Desktop ezt elvégezheti Ön helyett. Ha ez nem sikerül, egy figyelmeztetés jelenik meg a növekményes frissítés párbeszédpanelén a növekményes frissítés szabályzatának definiálásakor. Ez a figyelmeztetés SQL-alapú adatforrások számára lehet hasznos, például az SQL, az Oracle és a Teradata számára. Előfordulhat, hogy más adatforrások nem tudják elvégezni az ellenőrzést a lekérdezések követése nélkül. Ha a Power BI Desktop nem tudja megerősíteni a műveletet, a következő figyelmeztetés jelenik meg.

 ![Lekérdezésdelegálás](media/service-premium-incremental-refresh/query-folding.png)

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

- Ha sikerül is letöltenie a növekményes frissítési szabályzatot tartalmazó PBIX-fájlt a Power BI szolgáltatásból, az nem nyitható meg a Power BI Desktopban. A jövőben elképzelhető, hogy a rendszer támogatni fogja ezt a használati módot, de tartsa szem előtt, hogy ezek az adatkészletek akkorára nőhetnek, hogy problémákba ütközhet, ha átlagos asztali számítógépen próbálja letölteni és megnyitni őket.

#### <a name="refresh-ranges"></a>Tartományok frissítése

A következő példa egy frissítési szabályzatot mutat be az adatok öt naptári évig, valamint az aktuális év adatainak a jelenlegi dátumig tartó tárolásához és 10 nap adatainak növekményes frissítéséhez. Az első frissítési művelet az előzményadatokat tölti be. A további frissítések növekményesek lesznek, és (napi szinten történő futtatás mellett) az alábbi műveleteket végzik el:

- Új napnyi adatok hozzáadása.

- Az adatok frissítése az aktuális dátumtól számított 10 napra visszamenőleg.

- Az aktuális dátumtól számított öt évnél régebbi naptári évek eltávolítása. Ha például az aktuális dátum 2019. január 1., a 2013-as évet eltávolítja a rendszer.

A Power BI szolgáltatás által végzett első frissítés tovább tarthat, mert itt öt teljes naptári évet kell importálni. A későbbi frissítések végrehajtása már sokkal rövidebb időt fog igénybe venni.

![Tartományok frissítése](media/service-premium-incremental-refresh/refresh-ranges.png)

> [!NOTE]
> Előfordulhat, hogy ezeknek a tartományoknak a definiálásán kívül semmilyen más teendője nincs. Ez esetben közvetlenül a lentebb lévő közzétételi lépésekhez ugorhat. A többi legördülő lista speciális funkciók használatához készült.

### <a name="advanced-policy-options"></a>Speciális szabályzabeállítások

#### <a name="detect-data-changes"></a>Adatváltozások észlelése

10 napnyi adat növekményes frissítése sokkal hatékonyabb, mint öt évnyi adat teljes frissítése. De lehet, hogy ennél többet is tudunk tenni. Az **Adatváltozások észlelése** jelölőnégyzet bejelölésével megadhat egy dátum/idő oszlopot, amely alapján a rendszer azonosítani tudja, hogy mely napokon történt adatváltozás, és csak ezeket a napokat frissíti. Ez azt feltételezi, hogy található ilyen oszlop a forrásrendszerben (mely jellemzően megtalálható, naplózási célokból). **Ez nem lehet ugyanaz az oszlop, amelyet az adatoknak a RangeStart/RangeEnd paraméterekkel való particionálására használt.** Ennek az oszlopnak a maximális értékét a rendszer kiértékeli a növekményes tartományban lévő minden egyes időszak esetében. Ha nem változott az utolsó frissítés óta, akkor nem szükséges frissíteni az időszakot. A jelen példában ez tovább csökkentheti a növekményesen frissített napok számát 10-ről körülbelül 2-re.

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

## <a name="limitations"></a>Korlátozások

[Összetett modellek](desktop-composite-models.md) esetén jelenleg a növekményes frissítést csak az SQL, az Oracle és a Teradata típusú adatforrások támogatják.
