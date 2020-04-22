---
title: Adatfrissítés a Power BI-ban
description: Ez a cikk elméleti szinten ismerteti a Power BI adatfrissítési funkcióit és azok függőségeit.
author: davidiseminger
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/26/2020
ms.author: davidi
LocalizationGroup: Data refresh
ms.openlocfilehash: e51361d910c558824f33fb9ed00f6332aa3bba07
ms.sourcegitcommit: b2cb0b02bdc451bf11a92a68f2c4d560a811f563
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81440032"
---
# <a name="data-refresh-in-power-bi"></a>Adatfrissítés a Power BI-ban

A Power BI segítségével gyorsan eljuthat az adatoktól az elemzési eredményeken át a cselekvésig, ugyanakkor gondoskodnia kell arról, hogy a Power BI-jelentések és irányítópultok adatai naprakészek legyenek. Az adatfrissítés módjának ismerete gyakran elengedhetetlen a pontos eredmények biztosításához.

Ez a cikk elméleti szinten ismerteti a Power BI adatfrissítési funkcióit és azok függőségeit. Emellett ajánlott eljárásokat és tippeket is kínál a gyakori frissítési problémák elkerüléséhez. A cikk tartalma megalapozza az adatfrissítés működésének megértését. Az adatfrissítés konfigurálásának célzott, lépésenkénti ismertetését a Következő lépések szakaszban, a cikk végén felsorolt oktatóanyagokban és útmutatókban találhatja meg.

## <a name="understanding-data-refresh"></a>Az adatfrissítés ismertetése

Az adatok frissítésekor a Power BI-nak le kell kérdeznie a mögöttes adatforrásokat, esetleg be kell töltenie a forrást egy adathalmazba, hogy frissíthesse az éppen frissített adathalmazra épülő jelentések és irányítópultok vizualizációit. A teljes folyamat az alábbi szakaszokban kifejtettek szerint az adathalmazok tárolási módjától függően több fázisból áll.

Az adathalmazok, jelentések és irányítópultok Power BI általi frissítésének megértéséhez tisztában kell lennie az alábbi fogalmakkal:

- **Tárolási módok és adathalmaz-típusok**: A Power BI által támogatott tárolási módok és adathalmaz-típusok különböző frissítési követelményekkel járnak. Dönthet úgy, hogy újra importálja az adatokat a Power BI-ba, hogy lássa az összes változást, vagy lekérdezheti az adatokat közvetlenül a forrásnál is.
- **Frissítési típusok a Power BI-ban**: A különböző frissítési típusok ismerete az adathalmaz sajátosságaitól függetlenül is segíthet megérteni, hogy mit végez el a Power BI a frissítési műveletek során. Ezek a részletek a tárolási mód jellemzőivel együtt segítenek megérteni, hogy mit tesz pontosan a Power BI, amikor Ön az **Azonnali frissítés** lehetőséget választja egy adathalmazhoz.

### <a name="storage-modes-and-dataset-types"></a>Tárolási módok és adathalmaz-típusok

A Power BI-adathalmazok az alábbi módszerekkel férhetnek hozzá különböző adatforrások adataihoz. További információt a [Tárolási mód a Power BI Desktopban](desktop-storage-mode.md) című cikkben talál.

- Importálás mód
- DirectQuery mód
- LiveConnect mód
- Leküldés mód

Az alábbi diagram a különböző adatfolyamokat szemlélteti a tárolási mód alapján. A leglényegesebb szempont, hogy csak az Importálás módú adathalmazok igénylik a forrásadatok frissítését. Ez a frissítés azért szükséges, mert az ilyen típusú adathalmaz importálja az adatokat az adatforrásból, és az importált adatok rendszeresen vagy alkalmi jelleggel frissítve lehetnek. A DirectQuery módú adathalmazok, és az Analysis Serviceshez LiveConnect módban kapcsolódó adathalmazok nem importálnak adatokat. Ezek minden felhasználói beavatkozáskor lekérdezik a mögöttes adatforrást. A Leküldés módú adathalmazok egyetlen adatforráshoz sem férnek hozzá közvetlenül, hanem a Power BI-ba leküldött adatokra várnak. Az adathalmaz-frissítés követelményei a tárolási módtól és az adathalmaz típusától függően változnak.

![Tárolási módok és adathalmaz-típusok](media/refresh-data/storage-modes-dataset-types-diagram.png)

#### <a name="datasets-in-import-mode"></a>Importálás módú adathalmazok

A Power BI az eredeti adatforrásokból az adathalmazba importálja az adatokat. A Power BI-jelentések és irányítópultok adathalmazra irányuló lekérdezései az importált táblákból és oszlopokból adják vissza az eredményeket. Egy ilyen adathalmaz pillanatképszerű másolatként is felfogható. Mivel a Power BI másolatot készít az adatokról, az adathalmazt frissíteni kell, hogy beolvassa a változásokat a mögöttes adatforrásokból.

Mivel a Power BI gyorsítótárazza az adatokat, az Importálás módú adathalmazok mérete jelentős lehet. Az alábbi táblázat a maximális adathalmaz-méretet tartalmazza kapacitásonként. Érdemes jóval a maximális adathalmaz-méret alatt maradni az olyan frissítési problémák elkerülése érdekében, amelyek akkor lépnek fel, ha az adathalmaz a rendelkezésre álló erőforrásoknál többet igényelne a frissítési művelet során.

| Kapacitástípus | Maximális adathalmaz-méret |
| --- | --- |
| Megosztott, A1, A2 vagy A3 | 1 GB |
| A4 vagy P1 | 3 GB |
| A5 vagy P2 | 6 GB |
| A6 vagy P3 | 10 GB |
| | |

#### <a name="datasets-in-directqueryliveconnect-mode"></a>DirectQuery/LiveConnect módú adathalmazok

DirectQuery/LiveConnect módban működő kapcsolatokban a Power BI nem importál adatokat. Ehelyett az adathalmaz ad vissza eredményeket a mögöttes adatforrásból, amikor egy jelentés vagy irányítópult lekérdezi az adathalmazt. A Power BI átalakítja és az adatforráshoz továbbítja a lekérdezéseket.

Bár a DirectQuery mód és LiveConnect mód hasonlít abban, hogy a Power BI a forráshoz továbbítja a lekérdezéseket, fontos megjegyezni, hogy LiveConnect módban a Power BI-nak nem kell átalakítania a lekérdezéseket. A lekérdezéseket közvetlenül, a megosztott kapacitás vagy prémium szintű kapacitás erőforrásainak felhasználása nélkül megkapja az adatbázist üzemeltető Analysis Services-példány.

Mivel a Power BI nem importálja az adatokat, adatfrissítés futtatására nincs szükség. A Power BI azonban végez csempefrissítéseket és esetleg jelentésfrissítéseket is a frissítési típusokról szóló következő szakaszban leírtak szerint. A csempék irányítópultra rögzített jelentésvizualizációk, és az irányítópultok csempéinek frissítése körülbelül óránként megtörténik, hogy a csempéken naprakész eredmények legyenek láthatók. Az ütemezés az adathalmaz beállításaiban, az alábbi képernyőképen látható módon módosítható, vagy manuálisan kikényszeríthető az irányítópult frissítése az **Azonnali frissítés** lehetőség használatával.

![Frissítési ütemezés](media/refresh-data/refresh-schedule.png)

> [!NOTE]
> Az **Adathalmazok** lap **Ütemezett gyorsítótár-frissítés** szakasza Importálás módú adathalmazokhoz nem érhető el. Ezek az adathalmazok nem igényelnek külön csempefrissítést, mert a Power BI automatikusan frissíti a csempéket az ütemezett vagy igény szerinti adatfrissítések során.

#### <a name="push-datasets"></a>Leküldéses adathalmazok

A Leküldés módú adathalmazok nem tartalmaznak adatforrás-definíciót, ezért nem igényelnek adatfrissítést a Power BI-ban. A frissítésükhöz olyan külső szolgáltatáson vagy folyamaton keresztül kell leküldeni az adatokat az adathalmazba, mint az Azure Stream Analytics. Ezt a módszert gyakran alkalmazzák a Power BI-jal végzett valós idejű elemzésekhez. A Power BI ilyenkor is végez gyorsítótár-frissítéseket a leküldéses adathalmazra épülő csempékhez. Részletes útmutatást az [Oktatóanyag: A Stream Analytics és a Power BI: Valós idejű elemzési irányítópult streamelési adatokhoz](/azure/stream-analytics/stream-analytics-power-bi-dashboard).

> [!NOTE]
> A Leküldés módra vonatkozik néhány, [A Power BI REST API korlátozásai](developer/automation/api-rest-api-limitations.md) című cikkben dokumentált korlátozása.

### <a name="power-bi-refresh-types"></a>Frissítési típusok a Power BI-ban

A Power BI frissítési műveletei többféle frissítéstípusból állhatnak. Ilyen az adatfrissítés, a OneDrive-frissítés, a lekérdezési gyorsítótárak frissítése, a csempefrissítés és a jelentésbeli vizualizációk frissítése. Bár a Power BI automatikusan határozza meg az egy adott adathalmazhoz szükséges frissítési lépéseket, érdemes tudni, hogy ezek hogyan járulnak hozzá a frissítési művelet összetettségéhez és időtartamához. Gyors áttekintést nyújt az alábbi táblázat.

| Tárolási mód | Adatfrissítés | OneDrive-frissítés | Lekérdezési gyorsítótárak | Csempefrissítés | Jelentésvizualizációk |
| --- | --- | --- | --- | --- | --- |
| Importálás | Ütemezett és igény szerinti | Igen, csatlakoztatott adathalmazokhoz | Ha engedélyezve van prémium szintű kapacitásban | Automatikus és igény szerinti | Nem |
| DirectQuery | Nem értelmezhető | Igen, csatlakoztatott adathalmazokhoz | Ha engedélyezve van prémium szintű kapacitásban | Automatikus és igény szerinti | Nem |
| LiveConnect | Nem értelmezhető | Igen, csatlakoztatott adathalmazokhoz | Ha engedélyezve van prémium szintű kapacitásban | Automatikus és igény szerinti | Igen |
| Leküldés | Nem értelmezhető | Nem értelmezhető | Nem praktikus | Automatikus és igény szerinti | Nem |
| | | | | | |

#### <a name="data-refresh"></a>Adatfrissítés

A Power BI-felhasználók szempontjából az adatfrissítés általában azzal jár, hogy ütemezetten vagy igény szerint adatokat importálnak az eredeti adatforrásokból egy adathalmazba. Naponta több adathalmaz-frissítés is végrehajtható, és szükséges is lehet, ha a mögöttes adatforrás gyakran módosul. A Power BI megosztott kapacitásban lévő adathalmazokon naponta legfeljebb nyolc frissítést engedélyez. Ha az adathalmaz prémium szintű kapacitásban van, naponta legfeljebb 48 frissítést ütemezhet az adathalmaz beállításai között. További információt a cikk egy későbbi részében, az [Ütemezett frissítés konfigurálása](#configure-scheduled-refresh) című szakaszban talál. Ha egy adathalmaz olyan Prémium szintű kapacitásban van, amelyen engedélyezve van az [XMLA-végpont](service-premium-connect-tools.md) az olvasáshoz/íráshoz, korlátlan számú frissítési művelet támogat a TMSL vagy PowerShell használatával végzett programozott konfigurálás során.

Azt is fontos hangsúlyozni, hogy a napi frissítések megosztott kapacitásokra vonatkozó korlátozása az ütemezett és az API-frissítések számának összegére vonatkozik. Igény szerinti frissítést az adathalmaz menüjének **Azonnali frissítés** elemét választva is indíthat az alábbi képernyőképen látható módon. A frissítési korlátozás az igény szerinti frissítésekre nem vonatkozik. Azt is fontos megjegyezni, hogy a prémium szintű kapacitásban lévő adathalmazok esetében nincsenek az API-frissítésekre vonatkozó korlátozások. Ha saját frissítési megoldást szeretne készíteni a Power BI REST API-jával, az [Adathalmazok – Adathalmaz frissítése](/rest/api/power-bi/datasets/refreshdataset) című cikkből tájékozódhat.

![Azonnali frissítés](media/refresh-data/refresh-now.png)

> [!NOTE]
> Az adatfrissítéseknek megosztott kapacitásban kevesebb, mint 2 óra alatt be kell fejeződniük. Ha adathalmaza ennél hosszabb frissítési műveleteket igényel, fontolja meg az adathalmaz áthelyezését prémium szintű kapacitásba. Prémium szinten a frissítés maximális időtartama 5 óra.

#### <a name="onedrive-refresh"></a>OneDrive-frissítés

Ha a OneDrive-ban vagy a SharePoint Online-ban tárolt Power BI Desktop-fájl, Excel-munkafüzet vagy vesszővel tagolt (.csv) adatfájl alapján hozott létre adathalmazokat és jelentéseket, akkor a Power BI egy másik típusú frissítést, úgynevezett OneDrive-frissítést hajt végre. További információ: [Adatok beolvasása a Power BI-ba fájlokból](service-get-data-from-files.md).

Az olyan adathalmaz-frissítésekkel ellentétben, amikor a Power BI egy adatforrásól importál adatokat egy adathalmazba, a OneDrive-frissítés az adathalmazokat és jelentéseket szinkronizálja azok forrásfájljaival. A Power BI alapértelmezés szerint körülbelül óránként ellenőrzi, hogy egy OneDrive-ban vagy SharePoint Online-ban tárolt fájlhoz csatlakozó adathalmaz igényel-e szinkronizálást.

> [!IMPORTANT]
> Legyen körültekintő a fájlok OneDrive-on történő kezelésekor. Amikor adatforrásként állít be egy OneDrive-fájlt, a Power BI a fájl tételazonosítójára hivatkozik a frissítés végrehajtásakor, ami néhány esetben problémákat okozhat. Példaként vegyünk egy olyan forgatókönyvet egy mesterfájllal (_A_), amely rendelkezik egy éles környezetbeli másolattal (_B_), és Ön beállítja, hogy a OneDrive frissítse a B fájlt. Ha ezután az A fájlt a B fájl fölé _másolja_, a másolási művelet törli a régi B fájlt, és létrehoz egy eltérő tételazonosítóval rendelkező új B fájlt, ami megszakítja a OneDrive általi frissítést. Ehelyett fel kell töltenie és le kell cserélnie a B fájlt, így megőrizve az eredeti tételazonosítót.

A fájlt áthelyezheti egy másik helyre (például áthúzással), ekkor a frissítés továbbra is működni fog, mivel a PBI továbbra is felismeri a tételazonosítót. Ha azonban egy másik helyre másolja a fájlt, egy új fájlpéldány és egy új tételazonosító jön létre. Ezért a Power BI-fájlhivatkozás már nem lesz érvényes, és a frissítés nem sikerül.

A múltbeli szinkronizálási ciklusokat a frissítési előzmények OneDrive lapján tekintheti át. Az alábbi képernyőképen egy mintaadathalmaz egy befejezett szinkronizálási ciklusa látható.

![Frissítési előzmények](media/refresh-data/refresh-history.png)

Ahogy a fenti képernyőképen látható, a Power BI **Ütemezett** frissítésként azonosította a OneDrive-frissítést, de a frissítési időköz nem konfigurálható. A OneDrive-frissítés csak az adathalmaz beállításaiban kapcsolható ki. A frissítést akkor hasznos kikapcsolni, ha nem szeretné, hogy a Power BI-beli adathalmazai és jelentései automatikusan átvegyék a forrásfájlokban történt módosításokat.

Lényeges, hogy az adathalmaz beállításainak oldalán csak akkor jelenik meg a **OneDrive-beli hitelesítő adatok** és a **OneDrive-frissítés** szakasz, ha az adathalmaz egy OneDrive- vagy SharePoint Online-beli fájlhoz csatlakozik, ahogyan az alábbi képernyőképen látható. Olyan adathalmazoknál, amelyek nem csatlakoznak a OneDrive-ban vagy a SharePoint Online-ban tárolt forrásfájlokhoz, ezek a szakaszok nem láthatók.

![OneDrive-beli hitelesítő adatok és OneDrive-frissítés](media/refresh-data/onedrive-credentials-refresh.png)

Ha egy adathalmazhoz letiltja a OneDrive-frissítést, igény szerint továbbra is szinkronizálhatja az adathalmazt az adathalmaz **Azonnali frissítés** menüpontjával. Az igény szerinti frissítés részeként a Power BI ellenőrzi, hogy a OneDrive-ban vagy a SharePoint Online-ban tárolt forrásfájl újabb-e a Power BI-beli adathalmaznál, és ha így van, szinkronizálja az adathalmazt. A **Frissítési előzmények** között ezek a műveletek igény szerinti frissítésekként jelennek meg a **OneDrive** lapon.

Ne feledje, hogy a OneDrive-frissítés nem kér le adatokat az eredeti adatforrásokból. A OneDrive-frissítés csak a .pbix-, .xlsx- vagy .csv-fájlokból származó metaadatokkal és adatokkal frissíti a Power BI-beli erőforrásokat, ahogyan az alábbi ábrán látható. Annak érdekében, hogy az adathalmaz az adatforrások legfrissebb adataival rendelkezzen, a Power BI az igény szerinti frissítsek részeként adatfrissítést is indít. Erről meggyőződhet a **Frissítési előzményekben**, ha az **Ütemezett** lapra vált.

![OneDrive-frissítés diagramja](media/refresh-data/onedrive-refresh-diagram.png)

Ha a OneDrive-frissítést engedélyezve hagyja egy OneDrive-hoz vagy SharePoint Online-hoz csatlakozó adathalmazhoz, és ütemezetten szeretne adatfrissítést végrehajtani, az ütemezést úgy konfigurálja, hogy a Power BI az adatfrissítést a OneDrive-frissítés után hajtsa végre. Ha például saját szolgáltatást vagy folyamatot hozott létre, amely a OneDrive- vagy SharePoint Online-beli forrásfájlt minden éjszaka 1 órakor frissíti, akkor az ütemezett frissítést konfigurálhatja 02:30-ra, így elég időt adva a Power BI-nak, hogy befejezze a OneDrive-frissítést az adatfrissítés megkezdése előtt.

#### <a name="refresh-of-query-caches"></a>Lekérdezési gyorsítótárak frissítése

Ha adathalmaza prémium szintű kapacitásban helyezkedik el, akkor esetleg javíthatja a hozzá társított jelentések és irányítópultok teljesítményét a lekérdezési gyorsítótár engedélyezésével, ahogyan az alábbi ábrán látható. A lekérdezések gyorsítótárazása arra utasítja a prémium szintű kapacitást, hogy a helyi gyorsítótárazási szolgáltatását használja a lekérdezések eredményeinek megtartására, így elkerülhető, hogy a mögöttes adatforrás végezze el az eredmények kiszámítását. További információ: [Lekérdezések gyorsítótárazása a Power BI Premiumban](power-bi-query-caching.md).

![Lekérdezések gyorsítótárazása](media/refresh-data/query-caching.png)

Egy adatfrissítés után azonban a korábban gyorsítótárazott lekérdezési eredmények már nem érvényesek. A Power BI elveti ezeket a gyorsítótárazott eredményeket, és újra össze kell gyűjtenie azokat. Emiatt a lekérdezések gyorsítótárazása nem feltétlenül előnyös nagyon gyakran, például naponta 48 alkalommal frissített adathalmazokhoz társított jelentések és irányítópultok esetében.

#### <a name="tile-refresh"></a>Csempefrissítés

A Power BI az irányítópult minden csempevizualizációjához fenntart egy gyorsítótárat, és előre frissíti a csempék gyorsítótárait, ha az adatok módosulnak. Ez annyit jelent, hogy adatfrissítés után a csempék frissítése automatikusan megtörténik. Ez az ütemezett és az igény szerinti frissítési műveletekre is igaz. A csempefrissítést kényszerítheti is az irányítópult jobb felső sarkában található **További lehetőségek** (…) elemet, majd **Az irányítópult csempéinek frissítése** lehetőséget választva.

![Az irányítópult csempéinek frissítése](media/refresh-data/refresh-dashboard-tiles.png)

Mivel automatikusan megtörténik, a csempefrissítés az adatfrissítés részének tekinthető. Sok más mellett az is megfigyelhető, hogy a frissítések időtartama a csempék számával együtt növekszik. A csempefrissítés jelentős többletterheléssel is járhat.

A Power BI alapértelmezés szerint minden csempéhez egyetlen gyorsítótárat tart fenn, de ha az adatokhoz való hozzáférés dinamikus biztonsággal, felhasználói szerepkörök alapján van korlátozva, a [Sorszintű biztonság (RLS) a Power BI-ban](service-admin-rls.md) című cikkben ismertetett módon, akkor a Power BI-nak minden szerepkörhöz és csempéhez külön gyorsítótárat kell fenntartania. A csempe-gyorsítótárak száma annyiszorosára nő, amennyi a szerepkörök száma.

A helyzet tovább bonyolódhat, ha az adathalmaz élő kapcsolatban van egy sorszintű biztonsággal rendelkező Analysis Services-adatmodellel, ahogyan erre a [Dinamikus sorszintű biztonság Analysis Services-beli táblázatos modellel](desktop-tutorial-row-level-security-onprem-ssas-tabular.md) című oktatóanyag rávilágít. Ilyen helyzetben a Power BI-nak gyorsítótárat kell fenntartania és frissítenie minden csempéhez és minden felhasználóhoz, aki valaha megtekintette az irányítópultot. Nem ritka eset, hogy az ilyen adatfrissítési műveletek idejéből több kell a csempefrissítéshez, mint az adatoknak a forrásból való betöltéséhez. További információ a csempefrissítésről: [Csempékkel kapcsolatos hibák elhárítása](refresh-troubleshooting-tile-errors.md).

#### <a name="refresh-of-report-visuals"></a>Jelentésvizualizációk frissítése

Ez a frissítési folyamat kevésbé fontos, mert csak az Analysis Services-zel való élő kapcsolat esetén játszik szerepet. Ilyen kapcsolatoknál a Power BI gyorsítótárazza a jelentésvizualizációk utolsó állapotát, így a jelentés újabb megtekintésekor a Power BI-nak nem kell lekérdeznie az Analysis Services-beli táblázatos modellt. A jelentés kezelése során, például egy jelentésszűrő kicserélésekor a Power BI lekérdezi a táblázatos modellt, és automatikusan frissíti a jelentés vizualizációit. Ha úgy véli, hogy a jelentés elavult adatokat mutat, a jelentés Frissítés gombját választva elindíthatja az összes jelentésvizualizáció frissítését az alábbi ábrán bemutatott módon.

![Jelentésvizualizációk frissítése](media/refresh-data/refresh-report-visuals.png)

## <a name="review-data-infrastructure-dependencies"></a>Az adatinfrastruktúra-függőségek áttekintése

A tárolási módoktól függetlenül egyetlen adatfrissítés sem lehet sikeres, ha a mögöttes adatforrások nem elérhetők. Az adatokhoz való hozzáférésnek három fő forgatókönyve van:

- Egy adathalmaz helyszíni adatforrásokat használ
- Egy adathalmaz felhőbeli adatforrásokat használ
- Egy adathalmaz helyszíni és felhőbeli adatforrásokat is használ

### <a name="connecting-to-on-premises-data-sources"></a>Csatlakozás helyszíni adatforrásokhoz

Ha az adathalmaz olyan adatforrást használ, amelyhez a Power BI nem fér hozzá közvetlen hálózati kapcsolaton keresztül, akkor csak úgy engedélyezhet frissítési ütemezést vagy hajthat végre igény szerinti adatfrissítést, ha átjárókapcsolatot konfigurál ehhez az adathalmazhoz. Az adatátjárókról és azok működéséről a [Mik azok a helyszíni adatátjárók?](service-gateway-onprem.md) című cikkből tájékozódhat.

Az alábbi lehetőségek állnak rendelkezésére:

- Kiválaszt egy vállalati adatátjárót a kívánt adatforrás-definícióval
- Személyes adatátjárót helyez üzembe

> [!NOTE]
> Az adatátjárót igénylő adatforrástípusok listáját [Az adatforrás kezelése – Importálás/Ütemezett frissítés](service-gateway-enterprise-manage-scheduled-refresh.md) című cikkben találhatja meg.

#### <a name="using-an-enterprise-data-gateway"></a>Vállalati adatátjáró használata

A Microsoft személyes átjáró helyett vállalati adatátjáró használatát javasolja az adathalmazok helyszíni adatforráshoz csatlakoztatására. Ügyeljen arra, hogy az átjáró megfelelően legyen konfigurálva, tehát rendelkezzen a legújabb frissítésekkel és minden szükséges adatforrás-definícióval. Az adatforrás-definíciók adják meg a Power BI-nak egy adott forrás kapcsolati adatait, köztük a kapcsolati végpontokat, a hitelesítési módot és a hitelesítő adatokat. Az átjárón adatforrásainak kezeléséről [Az adatforrás kezelése – Importálás/Ütemezett frissítés](service-gateway-enterprise-manage-scheduled-refresh.md) című cikkben talál további információt.

Az adathalmazok vállalati átjáróhoz csatlakoztatása viszonylag magától értetődő művelet az átjáró rendszergazdái számára. Rendszergazdai jogosultságokkal gyorsan frissíthet egy átjárót, és szükséges esetén hozzáadhatja a hiányzó adatforrásokat. Ami azt illeti, egy hiányzó adatforrást közvetlenül az adathalmaz beállításainak oldalán hozzáadhat az átjáróhoz. A váltógomb kibontásával megtekintheti az adatforrásokat, és kiválaszthatja az **Hozzáadás átjáróhoz** hivatkozást, ahogyan az alábbi képernyőképen látható. Ha azonban Ön nem az átjáró rendszergazdája, forduljon az átjáró rendszergazdájához, és kérje meg, hogy adja hozzá a szükséges adatforrás-definíciót.

> [!NOTE]
> Az átjáróhoz kizárólag az átjáró rendszergazdája adhat adatforrásokat. Ellenőrizze azt is, hogy az átjáró rendszergazdája hozzáadta-e az Ön felhasználói fiókját azoknak a felhasználóknak a listájához, akiknek engedélyezett az adatforrás használata. Az Adathalmaz beállításai oldalon csak olyan vállalati átjárót választhat ki, amelynek adatforrásának használatára Ön engedélyt kapott.

![Hozzáadás átjáróhoz](media/refresh-data/add-to-gateway.png)

Ügyeljen rá, hogy a megfelelő adatforrás-definíciót kapcsolja össze az adatforrással. Ahogy a fenti képernyőképen látható, az átjáró rendszergazdái több definíciót is létrehozhatnak egyetlen átjárón, melyek mindegyike ugyanahhoz az adatforráshoz csatlakozik, és mindegyik definícióhoz más-más hitelesítő adatok tartoznak. A fenti példában az Értékesítési osztály adattulajdonosa az AdventureWorksProducts-Sales adatforrás-definíciót választaná, míg a Támogatási osztály munkatársa az adatkészlethez az AdventureWorksProducts-Support adatforrás-definíciót rendelné. Ha az adatforrás-definíciók nevei nem érthetőek első látásra, kérdezze meg az átjáró rendszergazdáját, hogy melyiket kell választania.

> [!NOTE]
> Egy adathalmaz csak egyetlen átjárókapcsolatot használhat. Másként fogalmazva helyszíni adatforrásokat nem lehet egynél több átjárókapcsolaton keresztül elérni. Ennek megfelelően minden szükséges adatforrás-definíciót ugyanahhoz az adatforráshoz kell hozzáadni.

#### <a name="deploying-a-personal-data-gateway"></a>Személyes adatátjáró üzembe helyezése

Ha nincs hozzáférése vállalati adatátjáróhoz, és egyedül Ön kezel adatforrásokat, és ezért nem kell adatforrásokat másokkal megosztania, személyes üzemmódban is üzembe helyezhet adatátjárót. Az **Átjárókapcsolat** szakaszban a **Nincs telepítve személyes adatátjáró** alatt válassza a **Telepítés most** lehetőséget. A személyes adatátjáróra vonatkozik néhány, a [Helyszíni adatátjáró (személyes mód)](service-gateway-personal-mode.md) című cikkben dokumentált korlátozás.

A vállalati adatátjárótól eltérően egy személyes adatátjáróhoz nem kell adatforrás-definíciókat hozzáadnia. Az adatforrások konfigurációját ehelyett az adathalmaz-beállítások **Adatforrásbeli hitelesítő adatok** szakaszában konfigurálhatja, ahogyan az alábbi képernyőképen látható.

![Adatforrás hitelesítő adatainak konfigurálása átjáróhoz](media/refresh-data/configure-data-source-credentials-gateway.png)

> [!NOTE]
> A személyes adatátjáró nem támogat DirectQuery/LiveConnect módú adathalmazokat. Az adathalmaz-beállítások oldala kérheti a telepítését, de ha csak személyes átjáróval rendelkezik, nem konfigurálhat átjárókapcsolatot. Az ilyen típusú adathalmazok támogatásához mindig vállalati adatátjárót kell használnia.

### <a name="accessing-cloud-data-sources"></a>Felhőbeli adatforrások elérése

Azok az adathalmazok, amelyek olyan felhőbeli adatforrásokat használnak, mint az Azure SQL DB, nem igényelnek adatátjárót, ha a Power BI közvetlen hálózati kapcsolatot tud létesíteni a forrással. Emiatt az ilyen adatforrások konfigurációját az adathalmaz-beállítások **Adatforrásbeli hitelesítő adatok** szakaszának használatával kezelheti. Ahogyan az alábbi képernyőképen látható, átjárókapcsolatot nem kell konfigurálnia.

![Adatforrásbeli hitelesítő adatok konfigurálása átjáró nélkül](media/refresh-data/configure-data-source-credentials.png)

### <a name="accessing-on-premises-and-cloud-sources-in-the-same-source-query"></a>Helyszíni és felhőbeli források elérése egyetlen forráslekérdezésben

Egy adathalmaz több forrásból is nyerhet adatokat, ezek a források pedig helyszíniek és felhőbeliek is lehetnek. Egy adathalmaz azonban, ahogyan már említettük, csak egyetlen átjárókapcsolatot használhat. Bár a felhőbeli adatforrások nem feltétlenül igényelnek átjárót, az átjáróra szükség van akkor, ha egy adathalmaz egyetlen adategyesítési lekérdezésben helyszíni és felhőbeli forrásokhoz is kapcsolódik. Ilyen helyzetben a Power BI-nak a felhőbeli adatforrásokhoz is átjárót kell használnia. Az alábbi ábra azt szemlélteti, ahogyan egy ilyen adathalmaz hozzáfér az adatforrásaihoz.

![Felhőbeli és helyszíni adatforrások](media/refresh-data/cloud-on-premises-data-sources-diagram.png)

> [!NOTE]
> Ha egy adathalmaz külön adategyesítési lekérdezésekkel kapcsolódik a helyszíni és a felhőbeli forrásokhoz, akkor a Power BI átjárókapcsolatot használ a helyszíni források eléréséhez, és közvetlen hálózati kapcsolatot a felhőbeli forrásokhoz. Ha egy adategyesítési lekérdezés helyszíni és felhőbeli forrásokból származó adatokat egyesít vagy fűz össze, akkor a Power BI a felhőbeli forrásoknál is áttér az átjárókapcsolat használatára.

A Power BI-adathalmazok a Power Query segítségével érik el és kérik le a forrásbeli adatokat. Az alábbi adategyesítési lista egyszerű példa olyan lekérdezésre, amely helyszíni és felhőbeli forrásokból származó adatokat egyesít.

```
Let

    OnPremSource = Sql.Database("on-premises-db", "AdventureWorks"),

    CloudSource = Sql.Databases("cloudsql.database.windows.net", "AdventureWorks"),

    TableData1 = OnPremSource{[Schema="Sales",Item="Customer"]}[Data],

    TableData2 = CloudSource {[Schema="Sales",Item="Customer"]}[Data],

    MergedData = Table.NestedJoin(TableData1, {"BusinessEntityID"}, TableData2, {"BusinessEntityID"}, "MergedData", JoinKind.Inner)

in

    MergedData
```

Egy adatátjáró kétféleképpen konfigurálható helyszíni és felhőbeli források adatainak egyesítéséhez vagy összefűzéséhez:

- A helyszíni adatforrásoké mellett a felhőbeli forrás adatforrás-definícióját is hozzáadja az adatátjáróhoz.
- Bejelöli **Az ezen átjárófürtön keresztüli frissítés engedélyezése a felhasználó felhőbeli adatforrásai számára** jelölőnégyzetet.

![Frissítés átjárófürtön keresztül](media/refresh-data/refresh-gateway-cluster.png)

Ha a fenti képernyőképen látható módon bejelöli **Az ezen átjárófürtön keresztüli frissítés engedélyezése a felhasználó felhőbeli adatforrásai számára** jelölőnégyzetet az átjáró konfigurációjában, akkor a Power BI használhatja azt a konfigurációt, amelyet a felhasználó adott meg a felhőbeli forráshoz az **Adatforrásbeli hitelesítő adatok** alatt az adathalmaz beállításaiban. Ez hozzájárulhat az átjáró konfigurálásával járó többletmunka csökkentéséhez. Ha azonban jobban kézben szeretné tartani az átjáró által létesített kapcsolatokat, nem érdemes bejelölnie ezt a jelölőnégyzetet. Ilyen esetben minden felhőbeli forráshoz, amelyet támogatni szeretne explicit adatforrás-definíciót kell hozzáadnia az átjáróhoz. Azt is megteheti, hogy bejelöli a jelölőnégyzetet, és a felhőbeli forrásokhoz explicit adatforrás-definíciókat ad hozzá az átjáróhoz. Ebben az esetben az átjáró minden megfelelő forráshoz az adatforrás-definíciókat fogja használni.

### <a name="configuring-query-parameters"></a>Lekérdezési paraméterek konfigurálása

A Power Queryvel létrehozott adategyesítési lekérdezések összetettsége az egyszerű lépésektől a paraméterezett szerkezetekig változhat. Az alábbi minta egy kis adategyesítési lekérdezésminta, amely egy _SchemaName_ és egy _TableName_ nevű paraméterrel fér hozzá egy AdventureWorks adatbázis megadott táblájához.

```
let

    Source = Sql.Database("SqlServer01", "AdventureWorks"),

    TableData = Source{[Schema=SchemaName,Item=TableName]}[Data]

in

    TableData
```

> [!NOTE]
> A lekérdezési paraméterek csak Importálás módú adathalmazokhoz támogatottak. A DirectQuery/LiveConnect mód nem támogatja a lekérdezési paraméterek definiálását.

Ahhoz, hogy egy paraméteres adathalmaz a megfelelő adatokhoz férjen hozzá, konfigurálnia kell az adategyesítési lekérdezés paramétereit az adathalmaz beállításaiban. A paramétereket programozottan is módosíthatja a [Power BI REST API](/rest/api/power-bi/datasets/updateparametersingroup) használatával. Az alábbi képernyőképen látható felhasználói felületen a fenti adategyesítési lekérdezést használó adathalmaz lekérdezési paraméterei konfigurálhatók.

![Lekérdezési paraméterek konfigurálása](media/refresh-data/configure-query-parameters.png)

> [!NOTE]
> A Power BI jelenleg nem támogatja a paraméteres adatforrás-definíciókat, más néven dinamikus adatforrásokat. Az Sql.Database("SqlServer01", "AdventureWorks") adathozzáférési függvény például nem paraméterezhető. Ha adathalmaza dinamikus adatforrásokra épül, a Power BI azt jelzi, hogy ismeretlen vagy nem támogatott adatforrásokat észlelt. Az adathozzáférési függvények paramétereit statikus értékekre kell cserélnie ha azt szeretné, hogy a Power BI azonosítani tudja az adatforrásokat, és kapcsolódni tudjon azokhoz. További információ: [Nem támogatott adatforrás frissítési hibáinak elhárítása](service-admin-troubleshoot-unsupported-data-source-for-refresh.md).

## <a name="configure-scheduled-refresh"></a>Ütemezett frissítés beállítása

A Power BI és az adatforrások közötti kapcsolat kialakítása az adatfrissítés konfigurálásának kiemelkedően legnagyobb részfeladata. A további lépések viszonylag egyértelműek. Ezek közé tartozik a frissítési ütemezés beállítása és a sikertelen frissítésekről szóló értesítések engedélyezése. Ehhez az [Ütemezett frissítés konfigurálása](refresh-scheduled-refresh.md) című cikk nyújt lépésenkénti útmutatást.

### <a name="setting-a-refresh-schedule"></a>Frissítési ütemezés beállítása

Az **Ütemezett frissítés** szakaszban határozhatja meg az adatkészletek frissítésének gyakoriságát és időszakait. Bizonyára emlékszik, hogy naponta legfeljebb nyolc időpontot konfigurálhat, ha az adathalmaz megosztott kapacitásban van, és 48 időpontot a Power BI Premiumban. Az alábbi képernyőkép egy tizenkét óránként ütemezett frissítés látható.

![Ütemezett frissítés beállítása](media/refresh-data/configure-scheduled-refresh.png)

Frissítési ütemezés konfigurálása után az adathalmaz beállításainak oldala a fenti képernyőképen látható módon tájékoztatja a következő frissítés időpontjáról. Ha ennél hamarabb szeretné frissíteni az adatokat, például az átjáró és az adatforrás konfigurációjának teszteléséhez, igény szerinti frissítést hajthat végre a navigációs panel Adatkészlet menüjében található **Azonnali frissítés** lehetőséggel. Az igény szerinti frissítések nem érintik a következő ütemezett frissítés időpontját.

Azt is vegye figyelembe, hogy a frissítés konfigurált időpontja nem feltétlenül az a pontos időpont, amikor a Power BI elindítja a következő ütemezett folyamatot. A Power BI törekszik a frissítési ütemezés minél pontosabb betartására. A cél az, hogy a frissítés az ütemezett időponttól legfeljebb 15 perc eltéréssel elinduljon, de akár egyórás késés is előfordulhat, ha a szolgáltatás nem tudja korábban lefoglalni a szükséges erőforrásokat.

> [!NOTE]
> A Power BI inaktiválja a frissítési ütemezést, ha négy egymás utáni alkalommal sikertelen marad, vagy ha a szolgáltatás olyan konfigurációmódosítást igénylő, helyrehozhatatlan hibát észlel, mint az érvénytelen vagy lejárt hitelesítő adatok. Az egymást követő sikertelen próbálkozások számának küszöbértéke nem módosítható.

### <a name="getting-refresh-failure-notifications"></a>Értesítés a sikertelen frissítésekről

A Power BI alapértelmezés szerint e-mail-értesítést küld az adathalmaz tulajdonosának a sikertelen frissítésekről, hogy a tulajdonos időben közbe tudjon lépni frissítési problémák esetén. A Power BI akkor is értesítést küld, ha a szolgáltatás a sorozatos sikertelenség miatt letiltja az ütemezést. A Microsoft az **Értesítést kérek e-mailben, ha sikertelen a frissítés** jelölőnégyzet bejelölve hagyását javasolja.

Érdemes lehet további címzetteket is megadni. Ehhez használja **A felhasználók e-mailben való értesítése sikertelen frissítés esetén** szövegmezőt. Ebben az esetben a rendszer az adathalmaz tulajdonosán kívül a megadott címzetteknek is elküldi a sikertelen frissítésekre vonatkozó értesítéseket. Megadhatja például egy munkatársát, aki vállalta, hogy foglalkozik az adathalmazokkal, amíg Ön szabadságon van. De megadhatja akár az osztály vagy a szervezet frissítési problémáiért felelős támogatási csapat e-mail-aliasát is. Azzal, hogy az adathalmaz tulajdonosán kívül másoknak is elküldi a sikertelen frissítésekre vonatkozó értesítéseket, hozzájárulhat ahhoz, hogy a problémákat időben észrevegyék és megoldják.

Fontos, hogy a Power BI nem csak a sikertelen frissítésekről küld értesítést, hanem akkor is, ha a szolgáltatás inaktivitás miatt szüneteltet egy ütemezett frissítést. Ha két hónapon át egyetlen felhasználó sem látogatott meg az adathalmazon alapuló egyetlen irányítópultot és jelentést sem, a Power BI inaktívnak minősíti az adathalmazt. Ilyen esetben a Power BI e-mailt küld az adathalmaz tulajdonososának, amelyben jelzi, hogy a szolgáltatás szüneteltette az adathalmaz frissítési ütemezését. Az alábbi képernyőkép az ilyen értesítésekre mutat egy példát.

![Szüneteltetett frissítésről tájékoztató e-mail](media/refresh-data/email-paused-refresh.png)

Az ütemezett frissítés folytatásához nyisson meg egy jelentést vagy irányítópultot, amely ennek az adathalmaznak a használatával készült, vagy frissítse manuálisan az adathalmazt az **Azonnali frissítés** lehetőséggel.

### <a name="checking-refresh-status-and-history"></a>A frissítési állapot és az előzmények ellenőrzése

A sikertelenségről szóló értesítések mellett időnként érdemes ellenőrizni az adathalmazokat, hogy nem történtek-e frissítési hibák. Ennek egy gyors módja az adathalmazok listájának megtekintése a munkaterületen. A hibát tartalmazó adathalmazok mellett kis figyelmeztető ikon látható. A figyelmeztető ikon kijelölésével további információkhoz juthat, ahogyan az alábbi képernyőképen látható. Az egyes frissítési hibák elhárításáról a [Frissítési forgatókönyvekkel kapcsolatos hibák elhárítása](refresh-troubleshooting-refresh-scenarios.md) című cikk nyújt további információkat.

![Frissítési állapot – figyelmeztetés](media/refresh-data/refresh-status-warning.png)

A figyelmeztetés ikon segít az adathalmazzal kapcsolatos aktuális problémák felismerésében, de emellett érdemes időnként a frissítési előzményeket is megvizsgálni. Ahogyan a nevéből kikövetkeztető, a frissítési előzményekben áttekinthető a múltbéli szinkronizálási ciklusok sikeres vagy sikertelen állapota. Előfordulhat például, hogy egy átjáró rendszergazdája lejárt adatbázisbeli hitelesítő adatokat frissített. Az alábbi képernyőképen a frissítési előzményekből jól látható, hogy mikor kezdett ismét működni az érintett frissítés.

![Frissítési előzmények – üzenetek](media/refresh-data/refresh-history-messages.png)

> [!NOTE]
> A frissítési előzmények megjelenítéséhez az adathalmaz beállításai között található hivatkozás. A frissítési előzményeket programozottan is lekérheti a [Power BI REST API](/rest/api/power-bi/datasets/getrefreshhistoryingroup) használatával. Egyéni megoldás használatával több adathalmaz frissítési előzményeit is központosítottan figyelheti.

## <a name="automatic-page-refresh"></a>Automatikus oldalfrissítés

Az automatikus oldalfrissítés a jelentésoldal szintjén működik, és lehetővé teszi, hogy a jelentés szerzője beállítson egy frissítési időközt az oldal vizualizációjához, amely csak akkor aktív, amikor a lap használatban van. Az automatikus oldalfrissítés csak DirectQuery-adatforrások esetén érhető el. A minimális frissítési időköz attól függ, hogy a jelentés milyen típusú munkaterületen van közzétéve, valamint hogy a Prémium munkaterületekre és [beágyazott munkaterületekre](developer/embedded/embedding.md) vonatkozóan milyen kapacitásbeállításokat alkalmazott a rendszergazda.

Az automatikus oldalfrissítésről az [automatikus oldalfrissítés](desktop-automatic-page-refresh.md) című cikkben olvashat bővebben.

## <a name="best-practices"></a>Ajánlott eljárások

Az adathalmazok frissítési előzményeinek rendszeres ellenőrzése az egyik legfontosabb ajánlott eljárás, amellyel biztosítható, hogy jelentései és irányítópultjai aktuális adatokat használjanak. Ha problémákat tapasztal, azonnal kezelje azokat, szükség esetén az adatforrás-tulajdonosok és az átjáró-rendszergazdák bevonásával.

Emellett az alábbi javaslatok szem előtt tartásával alakíthat ki és tarthat fenn megbízható adatfrissítési folyamatokat az adathalmazokhoz:

- Ütemezze a frissítéseket a kevésbé forgalmas időszakokra, főleg akkor, ha adathalmazai a Power BI Premiumban vannak. Ha tágabb időtartományra osztja szét a frissítési ciklusokat, elkerülheti a kiugró terheléseket, amelyek egyébként túlterhelhetnék a rendelkezésre álló erőforrásokat. A frissítési ciklusok késése a rendszer túlterhelésére utalhat. Ha egy prémium szintű kapacitás teljesen túl van terhelve, a Power BI akár ki is hagyhat egy frissítési ciklust.
- Tartsa szem előtt a frissítésre vonatkozó korlátozásokat. Gyorsan változó forrásadatok vagy nagy adattömeg esetén az Importálás mód helyett érdemesebb lehet DirectQuery/LiveConnect módot használni, ha annak a forrásra háruló többletterhelése és a lekérdezési teljesítményben megmutatkozó következménye elfogadható. Kerülje az Importálás módú adathalmazok folyamatos frissítését. A DirectQuery/LiveConnect mód ugyanakkor több korlátozással is jár, ilyen például a visszaadott adatokra vonatkozó egymillió soros korlátozás és a futó lekérdezések 225 másodperces válaszidő-korlátja, [A DirectQuery használata a Power BI Desktopban](desktop-use-directquery.md) című dokumentációnak megfelelően. Ezen korlátozások miatt rákényszerülhet, hogy mindenképpen Importálás módot használjon. Nagyon nagy adattömeg esetén fontolja meg a [Power BI-beli összesítések](desktop-aggregations.md) használatát.
- Ügyeljen rá, hogy az adathalmaz frissítéséhez szükséges idő ne lépje túl a frissítési időtartam maximumát. A frissítés időtartamát a Power BI Desktoppal ellenőrizheti. Ha 2 óránál többet vesz igénybe, fontolja meg az adathalmaz áthelyezését a Power BI Premiumba. Előfordulhat, hogy az adathalmaz megosztott kapacitáson nem frissíthető. Olyan adathalmazokhoz, amelyek 1 GB-nál nagyobbak vagy a frissítésük több órát vesz igénybe, érdemes lehet a [Power BI Premiumban növekményes frissítést](service-premium-incremental-refresh.md) használni.
- Optimalizálhatja adathalmazait, hogy csak a jelentések és irányítópultok által használt táblákat és oszlopokat tartalmazzák. Optimalizálja az adategyesítési lekérdezéseket, és ha csak lehetséges, kerülje a dinamikus adatforrás-definíciók és költséges DAX-számítások használatát. Nagy memóriaigényük és a számítási többletterhelés miatt különösen kerülendők azok a DAX-függvények, amelyek egy tábla összes sorát megvizsgálják.
- A Power BI Desktopban használtakkal azonos adatvédelmi beállítások alkalmazásával biztosíthatja, hogy a Power BI hatékony forráslekérdezéseket generálhasson. Ne feledje, hogy a Power BI Desktop nem tesz közzé adatvédelmi beállításokat. Ezeket a beállításokat manuálisan kell újra alkalmaznia az adatforrás-definíciókban az adathalmaz közzététele után.
- Ne használjon túl sok vizualizációt az irányítópultokon, főleg ha [sorszintű biztonságot (RLS)](service-admin-rls.md) használ. A cikkben korábban kifejtettek alapján az irányítópult-csempék túl magas száma jelentősen növelheti a frissítés időtartamát.
- Adathalmazait megbízható nagyvállalati adatátjáró-példány használatával csatlakoztassa a helyszíni adatforrásokhoz. Ha az átjáró által okozott frissítési hibákat tapasztal például az átjáró elérhetetlensége vagy túlterheltsége miatt, akkor forduljon az átjáró rendszergazdáihoz, hogy további átjárókat adjanak egy meglévő fürthöz, vagy új fürtöt helyezzenek üzembe (vertikális vagy horizontális felméretezés).
- Használjon külön adatátjárókat az Importálás és a DirectQuery/LiveConnect adathalmazokhoz, hogy az ütemezett frissítésekkel járó adatimportálás ne befolyásolja a DirectQuery/LiveConnect-adathalmazokra épülő jelentések és irányítópultok teljesítményét, amelyek minden felhasználói tevékenység esetén lekérdezik az adatforrásokat.
- Gondoskodjon róla, hogy a Power BI értesítést küldhessen Önnek a sikertelen frissítésekről. A levélszemét-szűrők blokkolhatják ezeket az üzeneteket, és más mappába helyezhetik át azokat, ahol nem tűnnek fel azonnal.


## <a name="next-steps"></a>Következő lépések

[Ütemezett frissítés beállítása](refresh-scheduled-refresh.md)  
[Frissítéssel kapcsolatos hibák hibaelhárítási eszközei](service-gateway-onprem-tshoot.md)  
[Frissítési forgatókönyvekkel kapcsolatos hibák elhárítása](refresh-troubleshooting-refresh-scenarios.md)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
