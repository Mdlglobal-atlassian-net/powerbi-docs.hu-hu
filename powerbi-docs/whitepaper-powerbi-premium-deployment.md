---
title: Üzembe helyezése és kezelése a Power BI prémium szintű kapacitások
description: Ismerje meg a Power BI Premium lehetséges, és megtudhatja, hogyan megtervezésére, üzembe helyezése, figyelése és hibaelhárítása a méretezhető megoldások.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/06/2019
LocalizationGroup: Premium
ms.openlocfilehash: fbae2a8b577c52ae597d44bd6ea9913510c4c65c
ms.sourcegitcommit: dc73e932c9982a4aa0b0ec5297fb9f94c6156bc5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/04/2019
ms.locfileid: "66518563"
---
# <a name="deploying-and-managing-power-bi-premium-capacities"></a>Üzembe helyezése és kezelése a Power BI prémium szintű kapacitások

**Összefoglalás:** A Power BI Premium stabilabb teljesítményt, a nagyméretű kötetek támogatása és a egy egységes önkiszolgáló és az enterprise BI platform rugalmasságát biztosítja a szervezet minden tagja számára. A szint 300 műszaki tanulmány kifejezetten a Power BI-rendszergazdák, és a tartalom szerzők és közzétevők került. Segíthet eligazodni a Power BI Premium lehetséges, és azt ismertetik, hogyan megtervezésére, üzembe helyezése, figyelése és hibaelhárítása a méretezhető megoldások célja.

**Szerző:** [Peter Myers](https://www.linkedin.com/in/peterjsmyers) (Data Platform MVP és bitenként megoldásokkal független BI-Szakértővé)

**Műszaki véleményezők:** ADAM Saxton, Akshai Mirchandani, Bhavik kereskedőnél, David Magar, Josh Caplan, Michael Blythe, Nimrod Shalit, Olivier Matrat, Swati Gupta

**A következőkre vonatkozik:** A Power BI szolgáltatásban, a Power BI Premium és az Azure Power BI Embedded-kapacitások

> [!NOTE]
> A tanulmányt a böngésző **Nyomtatás** > **Mentés PDF-ként** lehetőségével mentheti vagy kinyomtathatja.

## <a name="introducing-power-bi"></a>A Power BI bemutatása

A Power BI egy üzleti elemzési szolgáltatás elemzéseket kínálnak, amelyek lehetővé teszik a gyors és megalapozott üzleti döntésekhez. A 2015-ben kiadása óta gyorsan vált egy népszerű szolgáltatás, amely a legkisebb szervezetek megoldásokat nyújtsanak a legnagyobb vállalatok.

Teszi elérhetővé két módon: Felhőalapú szolgáltatás, és a egy helyszíni jelentéskészítő megoldás nevű **Power BI jelentéskészítő kiszolgáló**. \[[1](#endnote-01)\]

Power bi-ban, mert egy felhőszolgáltatás-as-szoftverszolgáltatások (SaaS) \[ [2](#endnote-02)\]. Azt jelöli, szolgáltatások és alkalmazások, amelyek lehetővé teszik a szervezetek számára, hogy fejlesztése, üzembe helyezése, kezelése, oszthat meg megoldásokat üzleti figyelése.

Már nem ez a tanulmány a Power BI szolgáltatás átfogó leírást adhat a szándéka. Ehelyett arra összpontosít, a Power BI Premium tárgya témákról. A Power BI kapcsolatos általános információkért tekintse meg a teljes körű [a Power BI dokumentációja](service-admin-premium-multi-geo.md). A Power BI szolgáltatásban és a hangsúly ezúttal informatikusainak jól teljesítő vállalati üzemelő példánya részletes leírását, tekintse meg a teljes körű [egy Power BI Enterprise üzembehelyezési tervezés](https://aka.ms/pbienterprisedeploy) tanulmány.

Tulajdonos. Ez a tanulmány összefüggésében ez a szakasz bemutatja, és ismerteti a kapacitások, a Power BI tartalomtípusokat, modell tárolási módok és licencelés. Ezek a témakörök megértése alapvető fontosságú sikeres üzembe helyezése és kezelése a Power BI Premium.

### <a name="capacities"></a>Kapacitások

**Kapacitások** vannak a Power BI alapfogalom több erőforrást (storage, a processzor és memória) üzemeltetésére, és más Power bi-ban használt jelölő tartalom. Kapacitások vagy megosztott vagy dedikált. A **megosztott kapacitás** van osztva más Microsoft-ügyfelekkel, miközben egy **dedikált kapacitás** elkötelezett egyetlen ügyfél számára. Dedikált kapacitást a jelennek meg a [prémium szintű kapacitások](#premium-capacities) témakör.

Egy megosztott kapacitásban a számítási feladatok a más ügyfelekkel megosztott számítási erőforrásokon futnak. A kapacitás erőforrásokat kell osztani, annak biztosítása érdekében a "tisztességes play", például a modell maximális mérete (1 GB) és a maximális napi frissítési gyakoriságot nyolc alkalommal száma (naponta) korlátozásokat vezetnek be.

### <a name="workspaces"></a>Munkaterületek

Kapacitások található Power BI-munkaterületeket, és biztonsági, az együttműködés és a központi telepítési tárolók jelölnek. Minden Power BI-felhasználó rendelkezik személyes munkaterületek néven **saját munkaterület**. További munkaterületek és a központi telepítési hozható létre, és ezek **alkalmazás-munkaterületek**. Alapértelmezés szerint – beleértve a személyes munkaterületeket - munkaterületek a megosztott kapacitásban jönnek létre.

### <a name="power-bi-content-types"></a>A Power BI-tartalom típusa

A Power BI Premium témakörök bevezetni, fontos, az alapvető tartalomtípusok többek között a Power BI-architektúra alapos vita indítása.

Minden Power BI-tartalmak tárolja és kezeli a munkaterületeken, amelyek olyan tárolók, a Power BI-tartalmakat. Minden Power BI-felhasználó saját munkaterületét rendelkezik, de az általánosan bevált gyakorlat szerint az alkalmazás-munkaterületek létrehozásához. Alkalmazás-munkaterületek művelésének tartalom és a tartalom közös használata lehetővé teszi lehetővé. Akkor is lehetővé teszi a előkészítéséhez és az alkalmazások széles tartalmak terjesztése.

A következő Power BI-tartalmak a munkaterületeken tárolja:

- Adatfolyamok
- Adathalmazok
- Munkafüzetek
- Jelentések
- Irányítópultok

#### <a name="dataflows"></a>Adatfolyamok

A Power BI-adatfolyamok segítségével a szervezetek egyesítheti a különböző forrásokból származó adatokat. Lehessen venni azokat adatként, előkészített és előkészített használható modellek, de azok nem használható közvetlen forrásként a jelentéskészítéshez. A Microsoft adatösszekötők engedélyezése az adatfeldolgozást az adatok helyszíni és felhőbeli adatforrások rengeteg képesek kihasználni.

Adatfolyamok csak is létrehozhatók és kezelhetők az alkalmazás-munkaterületek, és az a közös adatok modell (CDM) az Azure Data Lake Storage Gen2 entitásokként vannak tárolva. Általában ütemezett naprakész adatokat tárolni rendszeres frissítéséhez.

További információkért tekintse meg a [önkiszolgáló adat-előkészítési a Power bi-ban (előzetes verzió)](service-dataflows-overview.md) dokumentumot.

#### <a name="datasets"></a>Adathalmazok

A Power BI-adatkészletek az adatforrást készen áll a jelentéskészítő és vizualizációs képviseli. Az adatkészletek, által létrehozott számos típusa van:

- Csatlakozás egy meglévő data modell, amelyet egy Power BI-kapacitás nem üzemeltet
- Egy modellt tartalmazó Power BI Desktop-fájl feltöltése
- Egy Excel-munkafüzet (amely tartalmaz egy vagy több Excel-táblák és/vagy egy munkafüzet adatmodell) fel- vagy egy Comma-Separated érték (CSV) fájl feltöltése
- A Power BI szolgáltatás használatával leküldéses, streaming vagy hibrid streamelési adatkészlet létrehozása

Kivéve a streamelési adatkészletek \[ [3](#endnote-03)\], az adatkészlet jelöli, amely kihasználja az érett modellezési technológiák az Analysis Services adatmodellt.

Vegye figyelembe, hogy a dokumentáció, néha a terminológiát adatkészleteket és a modellek felcserélhetők. Általában a Power BI szolgáltatás szempontjából, a neve egy **adatkészlet** , és azt nevezzük fejlesztési szemszögből egy **modell**. Ez a tanulmány összefüggésében, sokkal ugyanazt jelenti.

##### <a name="externally-hosted-models"></a>Externally-Hosted Models

Telepítését is magában foglalja egy külsőleg üzemeltetett modellhez csatlakozik a [On-Premises Data Gateway](service-gateway-onprem.md) szeretne csatlakozni az SQL Server Analysis Services, hogy a helyszíni vagy Virtuálisgép-ban üzemeltetett infrastruktúra--szolgáltatásként (IaaS). Az Azure Analysis Services nem szükséges az átjáró. Ebben a forgatókönyvben gyakran értelme Ha bármit modell létezik, általában az a vállalati adatok adattárház (EDW) részét képező. Lehetővé teszi a Power BI végrehajtásához egy **élő kapcsolat** (LC) Analysis Services és a rendszer úgy valósítja meg a Power BI-jelentés felhasználó identitásának használatával adatokhoz jogosultságok kényszerítésével. Az SQL Server Analysis Services többdimenziós modellek (kockák) és a táblázatos modellek támogatottak. Ahogy az az alábbi képen is látható, az élő kapcsolatos adatkészlet lekérdezések külsőleg üzemeltetett modellek továbbítja.

![Egy élő kapcsolat adatkészletet továbbítja a lekérdezések külsőleg üzemeltetett modellek](media/whitepaper-premium-deployment/live-connection-dataset.png)

##### <a name="power-bi-desktop-developed-models"></a>A Power BI Desktop fejlett modellek

A Power BI Desktop - egy Power bi-ban fejlesztési ügyfélalkalmazás - olyan modell, amely lényegében egy Analysis Services táblázatos modell használható. Modellek fejleszthetők adatok adatfolyamok, amely majd integrálható legyen más adatforrásokkal történő importálásával. Bár a részletekről a hogyan modellezési érhető el ebben a tanulmányban hatókörén kívül fontos megérteni, hogy nincsenek-e három különböző típusú - vagy módok - modellek, amelyek a Power BI Desktop használatával fejleszthetők. Módokban határozza meg, hogy az adatok importálása a modellbe, vagy hogy marad az adatforrás. A három mód a következők: Importálás, a DirectQuery és az összetett. Minden mód teljes hatásának a megbeszélését típushelyzetben az [modell tárolási módok](#model-storage-modes) témakör.

Külsőleg üzemeltetett modellek és a Power BI desktop fejlett modellek kényszerítheti a sorszintű biztonság (RLS), amely egy bizonyos felhasználó lekérhető adatok körét. Az értékesítők alkalmazásbiztonsági csoporthoz rendelt felhasználók például csak tekintheti meg a jelentés adatai, amelyhez hozzá van rendelve az értékesítési régió(k) esetében. RLS-szerepkörök lehet dinamikus vagy statikus. **Dinamikus szerepkörök** szűrő a jelentés felhasználó közben **statikus szerepkörök** a alkalmazni a szerepkörhöz rendelt minden felhasználó számára ugyanazokat a szűrőket.

##### <a name="excel-workbook-models"></a>Az Excel-munkafüzet modellek

Excel-munkafüzetek vagy CSV-alapú adatkészletek létrehozása fájlokat eredményez a modell létrehozásához. Importálandó Excel-táblák és a CSV-adatokat adatmodell-táblák létrehozása közben egy Excel-munkafüzet adatmodelljébe fog felcserélődhet, hozhat létre egy Power BI-modellben. Minden esetben a fájlokban tárolt adatokhoz importálni egy modellt.

Díjszabásban, ezt követően végezhető Power BI-adatkészleteket, amelyek modellek:

- A Power BI szolgáltatásban vagy üzemeltetett, vagy külsőleg üzemeltetett az Analysis Services
- Importált adatok tárolhatják, vagy azok is továbbító lekérdezés küldött kérések kiadására alapul szolgáló adatforrások vagy mindkét vegyes

A következő fontos alapvető tudnivalók a Power BI-adatkészleteket, amelyek modellek összefoglalása:

- Az SQL Server Analysis Services üzemeltetett modellek lekérdezésekben LC végrehajtásához átjáró szükséges.
- A Power BI-ban üzemeltetett modellek, amelyek az adatok importálása
  - Teljes mértékben a memóriába betöltött kell lennie, hogy lekérdezhetők legyenek
  - Frissítsen az adatok naprakészen igényelnek, és az átjárók kell magában foglalja, ha a forrásadatok nem érhető el közvetlenül az interneten keresztül
- A Power BI-ban üzemeltetett modellek, amelyek (DQ) a DirectQuery tárolási mód a forrásadatokhoz való kapcsolatot igényelnek. A modell kérdeznek le, amikor a Power BI lekérdezések problémák az aktuális adatok lekéréséhez a forrásadatokat. Ebben a módban magában kell foglalnia átjárók, ha a forrásadatok nem érhető el közvetlenül az interneten keresztül.
- Modellek léptethet RLS-szabályokat, a szűrők megadásával korlátozhatja az egyes felhasználók adatelérési kényszerítése

Sikeres telepítéséhez és a Power BI Premium kezelése, fontos modellek üzemeltető, azok tárolási módot, az átjárókat, az importált adatok mérete függőségek megértéséhez, és frissítse a típusát és gyakoriságát. Ezek az összes jelentős hatással lehet a Power BI Premium-erőforrásokon. Emellett a modell felépítésének maga többek között az adatok előkészítési lekérdezései és számításokat is hozzáadhat kapcsolatos szempontok keveréke.

Is fontos tudni, hogy a Power BI-ban üzemeltetett importálás modellek frissítési ütemezés szerint, vagy lehet aktivált igény szerint a felhasználó a Power BI szolgáltatásban.

Optimalizált modellek kialakítása a következő cikkben később a műszaki tanulmány a a [optimalizálása modellek](#optimizing-models) témakör.

#### <a name="workbooks"></a>Munkafüzetek

A Power BI munkafüzetek a Power BI-tartalom típusát \[ [4](#endnote-04)\]. Azok az Excel-munkafüzeteket, amely fel lett töltve a Power BI szolgáltatásba, és nem lehet a feltöltött Excel-munkafüzetek (modellek)-adatkészletek létrehozása. A munkafüzet tartalomtípus jelöli, amely vagy tölthető fel a Power BI szolgáltatásban, vagy maradjon a felhőalapú tárolás, a OneDrive vagy SharePoint online-hoz egy munkafüzettel létesített kapcsolatot.

Fontos megérteni, hogy a tartalom típusa nem érhető el a Power BI-adatmegjelenítéseket adatforrásként. Ehelyett azt segítségével lehet megnyitni a munkafüzetet a Power BI szolgáltatásban, az Excel online-ban. A tartalomtípus fő szándéka az, hogy lehetővé tegyék a régi Excel munkafüzet jelentéseket a Power BI szolgáltatásban érhető el, és lehetővé teszi az adatvizualizációk a Power BI-irányítópultok rögzíthetők.

További információkért tekintse meg a [adatok lekérése Excel-munkafüzetből](service-excel-workbook-files.md) dokumentumot.

#### <a name="reports"></a>Jelentések

A jelentések két típusa van: Power BI-jelentések és tördelt jelentések.

**Power BI-jelentések** adjon meg egy interaktív adatábrázolás élményt, amely csak egyetlen adatkészlet csatlakozik. Jelentések gyakran tervezték, hogy ösztönző felhasználói való részvétel lehetővé teheti, hogy szolgáltatásokat rendkívüli tömbjét interakcióba szűréshez, tovább szeletelve, beleértve a tartományok közötti, szűrés és kiemelés, Felhatolás, részletezéseket, részletes elemzések kibontásáról keresztül, a Q & A természetes nyelvi kihallgatásában, összpontosító, lapok közötti navigálásról, spotlighting, megtekinti a könyvjelzők és egyéb.

Ez a tanulmány összefüggésében fontos tudni, hogy a Power BI-architektúra, Power BI-jelentés tervezési és a felhasználói műveletet az összes hatással lehet a Power BI szolgáltatás-erőforrások:

- Betölteni és importált modelleken alapuló jelentések kezelése, a modell teljes betöltése a memóriába (akár a Power BI szolgáltatásban üzemeltetett vagy külsőleg üzemeltetett) kell lennie
- Minden egyes jelentésvizualizáció kiad egy lekérdezést, a modell lekérdezésével adatok lekéréséhez
- Szűrő és a szeletelő interakciók általában magában foglalja a modell lekérdezése. Például egy szeletelő-kijelölés módosítása – alapértelmezés szerint - szükséges újbóli betöltéséből minden vizualizációt az oldalon \[ [5](#endnote-05)\]
- Power BI-jelentések megjelenítése az aktuális adatok nem garantálják, és előfordulhat, hogy a felhasználónak betölti a jelentésoldalt és a benne lévő vizualizációkat a jelentés frissítéséhez
- Felhasználók is érhet el a Q & a tegyen fel kérdéseket, a Power BI jelentéskészítő Tervező biztosít a természetes nyelvi szolgáltatás lehetővé teszi, és a az adatkészlet jelöli az modell egy Power BI-ban üzemeltetett adatok importálása vagy LC adatkészletet úgy konfigurálva, hogy a Q & A engedélyezése

**Oldalakra osztott jelentések** lehetővé teszi a kiadványt, és az SQL Server Reporting Services (SSRS) jelentések megjelenítése (\*.rdl formátumban). Ahogy a nevük is sugallja, többoldalas jelentések gyakran használják, ha igények miatt rögzített oldalméret nyomtatás szüksége, vagy ha a változó listák, amelyek teljes körűen kell kibontani. Például egy többoldalas renderelési (nem pedig a vizualizáción belül görgetés) készült számla és a nyomtatási.

A két támogatott jelentéstípusok választási lehetőséget biztosítson a jelentéskészítők, lehetővé téve számukra az válassza ki a követelmények alapján, és használatra szánt. A Power BI-jelentések általában interaktív élmény a felhasználók vizsgálata, és Fedezze fel a elemezheti az adatait, miközben oldalakra osztott jelentések alkalmasabbak paraméterekkel lapelrendezés ideális.

Jelentéstípus, függetlenül válaszol-e a jelentés betöltése és az adatok frissítések elérése (Ha a szűrők vagy paraméterek módosítva) elengedhetetlen, megbízható és jól teljesítő felhasználói élmény.

#### <a name="dashboards"></a>Irányítópultok

A Power BI-irányítópultok célja, hogy a monitorozási élményeket nyújthat és adatbázistáblákhoz jelentősen különbözik a Power BI-jelentéseket. Az irányítópultok értékeket és adatokat Vizualizációk a csempék Express tekinthesse egyetlen ablaktábla megjelenítése tervezték. Általában a irányítópultokat kínál néhány irányítópult-tervek várt nincs szükség beavatkozásra, mint a Power BI-jelentések kevesebb interakció környezeteket. Ha például egy felügyelet nélküli irányítópult kiszolgáló szoba beavatkozást nem igénylő képernyőn jelenik meg. Egy másik jelentős különbség az, hogy a irányítópultok csempék, amelyek több adatkészlet, miközben a Power BI a forrásadatok jelentés minden eddiginél csak egyetlen adatkészlet alapján is jelenthet.

Fontos megérteni, hogy egy irányítópult az célja, hogy gyorsan betölteni és Express a legfrissebb adatok (vagyis a Power BI szolgáltatásba) minden alkalommal. Csempe lekérdezési eredmények gyorsítótárazásával éri ezt, és az egyes irányítópultok teszi ezt. Tulajdonképpen azt kell megtennie minden olyan felhasználóhoz, egy irányítópultot, amely azon alapul, amelyeket a dinamikus RLS modellek hozzáféréssel rendelkezik.

A Power BI szolgáltatás automatikusan frissíti irányítópult lekérdezési gyorsítótárak, importálása a Power BI-ban üzemeltetett modellek frissítése után azonnal. LC és DQ modellek esetén az adatkészlet tulajdonosa szabályozhatja, hogy milyen gyakran a a Power BI szolgáltatásban frissíti a gyorsítótár, amely akár 15 perces gyakoriságra gyakran vagy ritkán egyszeri konfigurálható egy bizonyos fokú. Vegye figyelembe, hogy LC lekérdezés gyorsítótár-frissítések először lekérdezési modellje a metaadatok a határozza meg, hogy a modell frissítése megtörtént az utolsó gyorsítótár-frissítés óta, és nem folytatódik a gyorsítótár frissítése, amikor a frissítés óta nem történt. Ez az ellenőrzés nem lehetséges DQ modellekhez, és így gyorsítótárazása történik az adatok módosultak-e vagy sem.

Irányítópult-gyorsítótár lekérdezés alapján DQ frissíti, és LC modellek jelentős hatással lehet a Power BI szolgáltatás-erőforrások és a külső adatforrásokhoz. Fontolja meg egy irányítópultot, és a 20 csempék, mind az Azure Analysis Services-modell, amely előírja, hogy dinamikus rls-t, amely óránként frissülnek, és 100 felhasználóval megosztott irányítópult alapján. Ha az adatkészlet frissítéséhez óránként van beállítva, ez azt eredményezi, legalább a 2000 (20 x 100) lekérdezésekben LC. Ez egy hatalmas mennyiségű betöltési tudta elhelyezni a Power BI szolgáltatásban és a külső adatforrásokhoz, és azt is túllépheti a rendelkezésre álló erőforrások vonatkozó korlátozások. Kapacitás erőforrásokat és korlátokat ismertetik a [kapacitás-csomópontokat](#capacity-nodes) témakör.

Felhasználók egy irányítópultot a Power BI szolgáltatás erőforrásainak igénylő többféle módon léphetnek interakcióba. Pontosabban ezek a következők:

- Aktiválhatja az irányítópult-csempék, amely egy igény szerinti frissítést az összes kapcsolódó adatok a Power BI-ban üzemeltetett importált modelleken eredményezhet
- Kapcsolatba léphet a tehet fel és (amely az irányítópult-tervező lehetővé teszi, hogy és az adatkészlet a Power BI-ban üzemeltetett adatmodell importálás vagy LC adatkészletet úgy konfigurálva, hogy engedélyezze a Q & A) a Q & A természetes nyelvi szolgáltatás
- A gyors elemzések a funkciót, a Power BI használata felderítése is használható elemzéseket készítsenek egy alapul szolgáló adatkészlet, és vizualizációkat, amelyek ismertetik azokat (amely az, hogy a csempe alapul-e egy adatkészletet, amely a Power BI-ban üzemeltetett importálás adatmodell) és válaszol.
- Riasztások beállítása az irányítópult-csempék a Power BI szolgáltatásban annak értékek – valószínűleg gyakorisággal óránkénti - csempét, és a felhasználók értesítése, ha a küszöbérték túllépése küszöbértékek összehasonlítása (biztosítása, hogy a csempe egyetlen numerikus érték, és alapul egy a Power BI-ban üzemeltetett importálás adatmodell adatkészlet)

### <a name="model-storage-modes"></a>Modell tárolási módok

Ne felejtse el, hogy a Power BI Desktop lehetővé teszi, hogy három módok egyikében modell fejlesztéséhez. Fontos tudni, hogy az egyes data model tárolási mód és a Power BI szolgáltatás-erőforrások lehetséges hatások logikáját. Ez a szakasz az összes három mód mutatja be. Ezeket később az ebben a tanulmányban a modell optimalizálása témakörben részletesen tárgyalja.

#### <a name="import-mode"></a>Importálási mód

Importálási mód érték a leggyakoribb módja modellek fejlesztése miatt a rendkívül gyors teljesítmény társított memóriabeli kérdez le, a Tervező rugalmasságnak modelers, és támogatja a megadott Power BI szolgáltatás képességeit (Q & A használatára, gyors elemzések stb.). Egy új Power BI Desktop-megoldás létrehozása esetén az alapértelmezett módban.

Fontos tudni, hogy importált adatok mindig tárolja a lemezre, és teljes betöltése a memóriába lekérdezni vagy frissíteni kell lennie. A memóriában, egyszer importált modelleken processzoroknak kibővítése a lekérdezési eredmények eléréséhez. Is fontos tudni, hogy nincs-e egy modell importálása folyamatban részben a memóriába betöltött fogalma nem.

Frissítés, az adatokat tömörített és optimalizált és tárolja a lemez tárolási VertiPaq motor által. A memóriába betöltött lemezről, esetén megállapíthatja, hogy 10 szörös tömörítés, és ezért indokolt várható, hogy 10 GB-os forrásadatok tömörítheti, körülbelül 1 GB méretű. Tárméret lemezen érheti el a 20 %-os felül. \[[6](#endnote-06)\]

Tervezhetőség háromféleképpen lehet elérni. Adatmodellezők a következőket teheti:

- Több adatforrás - adatforrás típusa és a formátum függetlenül származó adatok gyorsítótárazásával adatok integrálása
- Adatok előkészítése lekérdezések létrehozásakor használja ki a Power Query-a képlet nyelven (más néven M) funkciók teljes készletét
- A Data Analysis Expressions (DAX) funkciók teljes készletét használata esetén a modell az üzleti logikát, számított oszlopok, a számított táblázatok és mértékek elért továbbfejlesztésének épülő

Ahogy az az alábbi képen is látható, az importálás modell integrálja a támogatott adatforrástípusok tetszőleges számú származó adatok.

![Egy modell importálása integrálhatja adatait tetszőleges számú támogatott adatforrástípusok](media/whitepaper-premium-deployment/import-model.png)

Áll importált modelleken társított meggyőző előnyeit, amelyek előfordulhatnak azonban olyan hátrányait túl:

- A teljes modellt kell betöltve a memória, mielőtt a Power BI lekérdezhesse a modell, amely helyezheti nyomás a rendelkezésre álló erőforrások számát és méretét, a modellek növekedésével
- Modell adatok csak az aktuális, a legújabb frissítés, és így importált modelleken frissíteni kell, lehetőleg ütemezés alapján
- Teljes frissítés fog eltávolít minden adatot az összes táblából, és töltse be újra az adatforrásból. Ez nagyon drága időt és erőforrásokat a Power BI szolgáltatásban és a adatforrás(ok) tekintetében is lehet. A Power BI rendelkezik a növekményes frissítés, amely elkerülheti a teljes tábla csonkolása és átrakodás támogatása, és ez tárgyalja a [Optimizing Power BI-Hosted modellek](#optimizing-power-bi-hosted-models) témakör.

A Power BI szolgáltatás erőforrás szempontjából importált modelleken van szükség:

- Elegendő memória a modell betöltése során kérdezhető le, vagy frissíteni
- Feldolgozási erőforrásokat és a további memória-erőforrások adatainak frissítése

#### <a name="directquery-mode"></a>DirectQuery módban

Fejlett (DQ) a DirectQuery módban lévő modellek ne importálja az adatokat. Ehelyett csak a metaadatok állnak, hogy amikor az alapul szolgáló adatforrás problémák natív lekérdezés kérdezhető le.

![A DirectQuery modellben az alapul szolgáló adatforrás problémák az natív lekérdezések](media/whitepaper-premium-deployment/direct-query-model.png)

Nincsenek két fő oka a DQ modellt érdemes lehet. Az első ilyen OK akkor, ha az adatkötetek túl nagy méretű – akkor is, ha a csökkentési metody dat érvényesek - modellbe betöltése vagy gyakorlatilag frissítése. A második ok akkor, ha a jelentések és irányítópultok kell "közel valós idejű" adatokat, megjelenítésen túlmutató módokon lehet (48 naponta alkalommal egy dedikált kapacitás). az ütemezett frissítés korlátokon belül.

Nincsenek társított DQ modellek több előnye is van:

- Importálás modell mérete korlátozások nem érvényesek
- Modellek nem igényelnek frissítést
- Jelentésfelhasználók a legfrissebb adatok jelenik meg a jelentés szűrőket és szeletelőket, való interakció során, és frissítheti a teljes jelentés az aktuális adatainak letöltése
- Irányítópult-csempék, DQ modellek, alapján automatikusan frissítheti akár 15 percenként

Vannak azonban számos hátrányait és társított DQ modellek korlátai:

- A modell alapján kell egy támogatott adatforráshoz, és ezért semmilyen Adatintegráció már kell elérni az adatforrásban. Támogatott adatforrások relációs és elemző rendszerek támogatásával, számos népszerű adattár \[ [7](#endnote-07)\].
- Lehet, hogy a teljesítmény lassú, potenciálisan negatív hatással lenne a a Power BI szolgáltatásban (nagyon nagy processzorigényű lekérdezések lehet), és az adatforrás (ami előfordulhat, hogy nem lesz optimalizálva a elemzési lekérdezések)
- A Power Query lekérdezéseket nem lehet túl összetett, és legfeljebb M kifejezések és függvények, amelyek az adatforrás által ismert a natív lekérdezéseket is lehet felcserélődhet
- A DAX-függvények korlátozva, amelyek az is lehet helyett a natív lekérdezéseket az adatforrás által ismert, és nem támogatott a számított táblázatokat vagy időintelligencia beépített képességei
- Alapértelmezés szerint sikertelen lesz, több mint egy millió sort lekérési igénylő lekérdezések modell
- Jelentések és irányítópultok több vizualizációt jelöl is inkonzisztens eredményeket megjeleníteni, különösen akkor, ha az adatforrás ideiglenes
- A Q & A és a gyors elemzések nem támogatottak.

A Power BI szolgáltatás erőforrás szempontjából DQ modellek van szükség:

- Minimális memória betölteni a modellt (csak metaadatai) Ha vannak lekérdezve
- Egyes esetekben jelentős processzor-erőforrások létrehozásához és az adatforrás felé küldött lekérdezések feldolgozása

További információkért tekintse meg a [közvetlen lekérdezés a Power BI Desktopban](desktop-use-directquery.md) dokumentumot.

#### <a name="composite-mode"></a>Összetett mód

Összetett módban fejlett modellek lehetővé teszik az egyes adatmodell-táblák tárolását módjának konfigurálása. Ezért importálása és DQ táblázatok támogatja. A számított táblázatok (a DAX definiált) és a DQ több adatforráshoz is támogatja.

Tábla tárolási mód importálás, DirectQuery vagy kettős konfigurálható. A tábla konfigurált kettős tárolási mód importálás és a DirectQuery, és ez lehetővé teszi, hogy a Power BI szolgáltatásban a leghatékonyabb mód használata egy lekérdezést a lekérdezési alapon meghatározni.

![Egy összetett modell az importálás és DQ tárolási mód esetén tábla szintjén konfigurált kombinációja](media/whitepaper-premium-deployment/composite-model.png)

Összetett modellek arra törekszik, hogy az importálási és DirectQuery módok legjavát. Ha megfelelően konfigurálta, a lekérdezési teljesítmény memórián belüli modellek lehetővé teszi az beolvasni a közel valós idejű adatokat adatforrásokból származó kombinálhatók.

Összetett modellek fejlesztő adatmodellezők valószínűleg dimenziótípusnak táblázatok konfigurálása az importálás vagy kettős tárolási mód és a tény-típusú táblázatok DirectQuery módban. Például vegyünk egy termék dimenziótípusnak tábla modell a kettős üzemmódú és a egy értékesítési tény-típusú táblázat DirectQuery módban. A Product tábla sikerült gyorsan és hatékonyan kérdezhető le a memóriában való jelentésszeletelőben jelennek meg. A DirectQuery módban a termék táblát csatlakozik majd lehet lekérdezni a Sales táblában. Az utóbbi lekérdezés sikerült engedélyezni a termék- és Sales táblák és a szeletelő értékei alapján történő szűrést csatlakozni egyetlen hatékony natív lekérdezés generációja.

Általánosságban véve előnyeit és hátrányait, minden egyes modell mód társított tekinthető tábla tárolási mód összetett modellek a alkalmazni.

További információkért tekintse meg a [összetett modellek használata a Power BI Desktopban](desktop-composite-models.md) dokumentumot.

### <a name="licensing"></a>Licencelés

A Power BI három licenccel rendelkezik:

- Power BI Free
- Power BI Pro
- Power BI Premium

A **Power BI ingyenes** licenc lehetővé teszi, hogy jelentkezzen be a Power BI szolgáltatásban és a modellek és a jelentéseket tegye közzé saját munkaterületét belül működik a munkatársak számára. Fontos megérteni, hogy már nem a Power BI-tartalmak megosztása a jelen licenc használatával. Ezt a licencet, mert a neve is sugallja, díjmentes.

A **Power BI Pro** licenc lehetővé teszi, hogy hozzon létre és együttműködés belüli alkalmazás-munkaterületek és a megosztás és a Power BI egyéni tartalom. Ezenkívül konfigurálhatják a automatikusan adatokat naprakészen tartása, beleértve a helyszíni adatforrásokból származó adatkészletek frissítése. Emellett azok naplózása, és szabályozhatja a adatok elérhető és használható. A licencre szükség a megosztott tartalom fogadására mások, kivéve, ha a felhasználó egy Power BI Premium dedikált kapacitás társítva.

A **a Power BI Premium** licenc bérlői szintű licencre, és azt a következő cikkben a [bemutatása a Power BI Premium](#introducing-power-bi-premium) szakaszban.

A Power BI licenceléssel kapcsolatos további információkért tekintse meg a [Power BI díjszabásának oldalán](https://powerbi.microsoft.com/pricing/) lapot.

## <a name="introducing-power-bi-premium"></a>A Power BI Premium bemutatása

A Power BI Premium egy egységes önkiszolgáló és az enterprise BI platform méretezési, megbízható teljesítmény és kiszámítható költségeket biztosít. Ez elsősorban éri ezt azáltal, hogy futtassa a Power BI szolgáltatásban a szervezet számára dedikált erőforrásokkal.

Emellett a Power BI Premium számos vállalati szolgáltatást kínál:

- Költséghatékony tartalomterjesztést, a Power BI-tartalmak korlátlan számú Power BI Free felhasználó, beleértve a külső felhasználók számára való megosztásának engedélyezése
- Támogatása a nagyobb adatkészletek mérete \[ [8](#endnote-08)\]
- Magasabb frissítési érvényes adatfolyamok és adatkészletek (akár 48 alkalommal / nap)
- Növekményes frissítési adatfolyamok és adatkészletek
- Adatfolyam társított entitásokat, és a párhuzamos végrehajtás átalakítások
- Oldalakra osztott jelentések
- A Power BI jelentéskészítő kiszolgáló helyszíni reporting
- Lehetővé teszi a tartalom beágyazása alkalmazásokba nevében. alkalmazás felhasználóinak (PaaS)

Ezek közül számos is javítható, hatékony és méretezhető vállalati megoldásokat, és szerepelnek a [optimalizálása prémium szintű kapacitások](#optimizing-premium-capacities) szakaszban.

### <a name="subscriptions-and-licensing"></a>Előfizetések és licencek

A Power BI Premium egy bérlői szintű Office 365-előfizetéssel elérhető két (készletkezelési egység) Termékváltozat-családokra:

- **EM** termékváltozatok (EM1-EM3) számára végez beágyazást, egy éves kötelezettségvállalást igénylő után számlázunk havonta
- **P** termékváltozatok (P1-P3) beágyazása és nagyvállalati funkciókat, havi vagy éves kötelezettségvállalás, hogy havonta számlázzuk, és tartalmaz licencet helyszíni Power BI jelentéskészítő kiszolgáló telepítése

Egy alternatív módszer is megvásárolható az Azure Power BI Embedded előfizetéssel rendelkező egyetlen Termékváltozat-család: **A** termékváltozatok (A1-A6) beágyazáshoz és a kapacitás csak tesztelési célokra.

A termékváltozatokat nyújthat magok a kapacitások létrehozása \[ [9](#endnote-09)\], azonban a EM termékváltozatok a következők korlátozott kisebb méretezési beágyazásához. A lépéseknek az ismertetése, ez a tanulmány ugyan a P SKU-k a Mi a következő cikkben számos fontos is is, a termékváltozatok.

A Premium szintű előfizetéssel szakembereket SKU-k, az Azure termékváltozatokat szükséges idő kötelezettségvállalás nélkül, és óradíjat kell fizetni. Azok teljes rugalmasságát, felfelé méretezés engedélyezése kézbesítéséhez, vertikális leskálázás, szüneteltetése, folytatása és törlése.

Az Azure Power BI Embedded nagyrészt az ebben a tanulmányban hatókörén kívül, de a tesztelési módszer témakör gyakorlati és gazdasági lehetőségként teszteléséhez, és mérheti a számítási feladatok tárgyalja.

Az Azure termékváltozatokat kapcsolatos további információkért tekintse meg a [Azure Power BI Embedded dokumentációja](/azure/power-bi-embedded/).

A Power BI Premium-előfizetések rendszergazdái a Microsoft 365 felügyeleti központban vásárolhatók meg. Csak az Office 365 globális rendszergazdák vagy a rendszergazdák számlázási pontosabban vásárolhat az SKU-k.

Miután megvásárolta, a bérlő kap a kapacitás - hozzárendelése virtuális magok megfelelő számú ez más néven **magok készletezésével**. Például egy P3 SKU megvásárlása nyújt a bérlő 32 virtuális magot.

További információkért tekintse meg a [hogyan tudja megvásárolni a Power BI Premium](service-admin-premium-purchase.md) dokumentumot.

### <a name="premium-capacities"></a>Premium Capacities

Egy megosztott kapacitásban, amelyben a számítási feladatok más ügyfelekkel megosztott számítási erőforrásokon futnak szakembereket egy **dedikált kapacitás** kizárólagos használatra a szervezet által. Elkülönített és dedikált számítási erőforrást, amely megbízható és következetes teljesítményt szolgáltatott tartalom.

Az ebben a tanulmányban célja **prémium szintű kapacitás** , ami azt jelenti, hogy társítva, az EM vagy a P termékváltozatokat.

#### <a name="capacity-nodes"></a>A kapacitás csomópontok

Az előfizetésekről és a licencelésről a témakörben ismertetett, mint a következők két Power BI Premium SKU-család: EM és. o. Minden Power BI Premium-termékváltozatokat a processzor, memória és tárolási erőforrások időkereten jelölő kapacitás-csomópontként érhető el. Erőforrások mellett minden Termékváltozat esetében működési korlátozások száma másodpercenként (DQ) a DirectQuery és élő kapcsolat (LC) kapcsolatok számától függ, és a párhuzamos modell száma frissíti.

Feldolgozási számú mag, háttér és előtérbeli között egyenlően osztja használatával érhető el.

**Háttérbeli virtuális magok** felelősek a Power BI alapvető funkciókat, beleértve a lekérdezések feldolgozásához, a gyorsítótár kezeléséhez, R services, a modellfrissítéshez, természetes nyelvi feldolgozást (Q & A) és a jelentések és képek kiszolgálóoldali megjelenítés futtatásához. Háttérbeli virtuális magok hozzá vannak rendelve egy rögzített méretű memória, amely elsődleges használt gazdagép modellekhez, amely aktív adatkészlet is nevezzük.

**Előtérbeli virtuális magok** felelős a webes szolgáltatás, az irányítópult és jelentés dokumentumkezeléshez, access, ütemezés, API-k, feltölti és tölti le, és általában minden vonatkozó a felhasználói élmény.

Tárolási kapacitás csomópontonként 100 TB-ra van beállítva.

Az erőforrások és a korlátok minden prémium szintű termékváltozat (és év méretezni A Termékváltozat) a következő táblázat ismerteti.

| A kapacitás csomópontok | Összes virtuális mag | Háttérrendszeri virtuális magok | MEMÓRIA (GB) | Előtérrendszeri virtuális magok | DQ/LC (/ mp) | Modell frissítése párhuzamos végrehajtás |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 2.5 | 0,5 | 3.75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7.5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| | | | | | | |

#### <a name="capacity-workloads"></a>A kapacitás számítási feladatokhoz

A kapacitás számítási feladatokat a felhasználók számára elérhetővé tett szolgáltatások. Alapértelmezés szerint az Azure és a prémium szintű kapacitások támogatja a csak egy adatkészlet munkaterhelés nem tiltható le, amely a Power BI-lekérdezések futtatása társított.

További számítási feladatok oldalakra osztott jelentések, adatfolyamok és mesterséges Intelligencia esetén is engedélyezhető. Minden további számítási feladat beállítását igényli a maximális memóriát (a teljes szabad memória százalékaként), a munkaterhelés szerint használható.

#### <a name="how-capacities-function"></a>Hogyan működik a kapacitások

Az összes időpontokban a Power BI szolgáltatás nagy hangsúlyt fektet a, hogy a kapacitás-erőforrások ajánlott használatát, amíg nem haladja meg a korlátok a kapacitás kivetett.

A kapacitás műveletek besorolt vagy interaktív vagy a háttérben. Interaktív műveletek közé tartozik a kérelmek megjelenítése, és válaszol a felhasználói tevékenységeket (szűrés, a Q & A lekérdezése, stb.). Általában a importálás modell lekérdezésére, a memória erőforrás-igényes, viszont LC/DQ modellek lekérdezésekor a CPU-igényes. Háttérbeli műveletek közé tartozik az adatfolyamot, és importálja a modell frissül, és az irányítópult lekérdezés gyorsítótárazása.

Fontos tudni, hogy interaktív műveletekhez mindig szándék a lehető legjobb felhasználói élmény biztosítása érdekében a háttérbeli műveletek. Ha rendelkezésre áll elegendő erőforrás, a háttérbeli műveletek feldolgozással, ha az erőforrások felszabadítása várólistába lesz hozzáadva. Adatkészlet frissítések és a mesterséges Intelligencia funkciók, például a háttérbeli műveletek a Power BI szolgáltatás által leállítva közepes folyamat lehet, és hozzáadja egy üzenetsorba.

Importált modelleken teljes mértékben a memóriába betöltött kell lennie, hogy a lekérdezett vagy frissíteni. A Power BI szolgáltatás kezeli a memória kihasználtsága használatával kifinomult algoritmusok maximálisan kihasználható a rendelkezésre álló memória biztosítása érdekében, és a szükségesnél nagyobb kapacitás érhető el: Bár lehetséges, hogy a kapacitás számos importálás tárolja a modellek (akár 100 TB prémium szintű kapacitás kiszolgálónként), amikor azok összesített lemezterület meghaladja a támogatott memória (és további memóriára szükség, lekérdezéséhez és frissítés), majd azokat az összes betöltése nem sikerült a memóriába egy időben.

Ezért be - és távolítva - memória kihasználtsága alapján importált modelleken. Az importálás modell be van töltve, amikor éppen lekérdezett (interaktív művelet) és még nincs a memóriában, vagy ha frissíteni kell (háttér-művelet).

Az Eltávolítás a memóriából a modell más néven **kiürítési** , és egy műveletet, amely a Power bi-ban gyorsan hajthat végre a modellek méretétől függően. Ha a kapacitás minden rendelkezésre álló memória mennyisége nem tapasztalja, modellek egyszerűen a memóriába betöltött és helyükön maradnak. \[[10](#endnote-10) \] azonban, ha nincs elég memória a modell betöltése érhető el, a Power BI szolgáltatásban először szabadítson fel memóriát. Azt szabadít fel memória azzal, amelyet nem használtak az elmúlt három percben modellek inaktívvá vált modellek észlelésével \[ [11](#endnote-11)\], és ezután kizárásának őket. Ha nem inaktív modellek fürtből, a Power BI szolgáltatásban arra törekszik, hogy kizárandó modelleket, a háttérbeli műveletek betöltése. Ebbe beletartozik a kiürítési, a háttérben futó számítási feladatokhoz – például a mesterséges Intelligencia munkaterhelés. Végső megoldásként, a sikertelen kísérletek 30 másodperc múlva \[ [11](#endnote-11)\], hogy az interaktív művelet sikertelen. Ebben az esetben a jelentés felhasználó szabályosan értesítést kap, próbálkozzon újra hamarosan javaslatot hiba.

Fontos, hogy hangsúlyozzák az, hogy az adatkészlet kiürítési egy normál és az elvárt működés. Arra törekszik, betöltés és a modellek, amelyek összesített mérete meghaladhatja a rendelkezésre álló memória memóriából memóriafelhasználása maximalizálása érdekében. Ez a Tervező, és teljes mértékben átlátható jelentésfelhasználók. Magas kiürítési díjait nem jelenti a kapacitást nem megfelelően van forrásokat. Is, azonban válnak a veszélye, ha a lekérdezés vagy a frissítés válaszkészségének érte miatt magas kiürítési díjait.

Frissíti az importálás modellek mindig memóriaigényes modellek kell betölti a memóriába, és további memóriára szükség a feldolgozás céljából. Teljes frissítés körülbelül double a modell által igényelt memória mennyisége használhatja. Ez biztosítja, hogy a modell lekérdezhetők, akkor is, ha a feldolgozás alatt (küldi a lekérdezéseket a meglévő modellt, amíg a frissítés befejeződött, és az új modell adatainak érhető el). Vegye figyelembe, növekményes frissítési kevesebb memória van szükség, és gyorsabban sikerült végrehajtani, és így jelentősen csökkentheti nyomás kapacitás erőforrásokon. Frissítések is lehet a CPU-igényes modellekhez, különösen az összetett Power Query-átalakítások vagy számított táblákat/oszlopokat, amelyek összetett, vagy nagy táblák alapulnak.

Frissítések – például a lekérdezések - van szükség, hogy a modell a memóriába. Ha nincs elég memória, a Power BI szolgáltatás megkísérli kizárandó inaktív modelleket, és ha ez nem lehetséges (is minden modell nem aktív), a frissítési feladat várólistára van-e állítva. Frissítések általában nagyon nagy Processzorteljesítményt, még akkor is inkább, lekérdezéseket. Ebből kifolyólag nincsenek egyidejű frissítések, állítsa be a háttér virtuális magokkal kerekítve száma x 1.5-ös számú kapacitásának korlátjáig. Ha túl sok egyidejű frissítések, egy ütemezett frissítés várólistára kerül. Ezekben a helyzetekben fordulhat elő, ha hosszabb ideig tart a frissítés befejezéséhez. Vegye figyelembe, hogy a igény szerinti frissítések (egy felhasználói kérelem vagy API-hívás által aktivált) három alkalommal próbálkozik \[ [11](#endnote-11)\], és akkor sikertelen, ha még nem áll elég erőforrás.

## <a name="managing-power-bi-premium"></a>A Power BI Premium kezelése

Előfizetések vásárlása és létrehozását, kezelését és figyelését a prémium szintű kapacitások kezelése a Power BI Premium foglalja magában.

### <a name="creating-and-managing-capacities"></a>Létrehozása és kezelése a kapacitások

A **Kapacitásbeállítások** lapján a **Power BI felügyeleti** portál megjeleníti a vásárolt virtuális magok száma és a rendelkezésre álló (pl. még, hozzá kell rendelni egy kapacitáshoz) és a prémium szintű kapacitások sorolja fel. A lap lehetővé teszi, hogy az Office 365 globális rendszergazdák vagy a Power BI szolgáltatás-rendszergazdák elérhető virtuális magok a prémium szintű kapacitások létrehozása vagy meglévő prémium szintű kapacitást módosítani.

Amikor hoz létre egy prémium szintű kapacitás, a rendszergazda meghatározásához szükséges:

- Kapacitás neve (a bérlőn belül egyedi)
- A kapacitás admin(s)
- Kapacitás mérete
- Az adatok fizikai tárolási helye régió \[ [12](#endnote-12)\]

Legalább egy kapacitás-rendszergazda kell hozzárendelni. A kapacitás-rendszergazdák hozzárendelt felhasználók:

- Munkaterületek hozzárendelése kapacitáshoz
- További kapacitás-rendszergazdák vagy (ahhoz, hogy munkaterületeket rendeljen a kapacitás) hozzárendelési engedélyekkel rendelkező felhasználók hozzáadása a felhasználói engedélyek kezelése
- Többoldalas jelentések és adatfolyamok számítási feladatok maximális memóriahasználat konfigurálása a számítási feladatok kezelése
- Indítsa újra a kapacitás, alaphelyzetbe állítása minden művelet esetén a rendszer túlterhelési \[ [13](#endnote-13)\]

Kapacitás-rendszergazdák nem férhetnek hozzá a munkaterület tartalomhoz (kivéve, ha explicit módon hozzárendelt munkaterület-engedélyek), és nem hozzáféréssel rendelkeznek minden Power BI rendszergazdai felületéhez (kivéve, ha explicit módon hozzárendelt) például a használati metrikákat, a naplókhoz és a bérlői beállításokat. Ami fontosabb a kapacitás-rendszergazdák nincs engedélye új kapacitások létrehozása vagy meglévő kapacitások skálázhatja. Emellett hozzá vannak rendelve a egy kapacitás-alapon történik, csak is biztosítva megtekintése és kezelése a kapacitást, amelyhez hozzá van rendelve.

Kapacitás mérete listából egy rendelkezésre álló SKU beállítások korlátozza a készlet elérhető magok száma alapján kell jelölni. Lehetséges, hozzon létre több kapacitás a készlet, amely egy sikerült beolvasva, vagy további megvásárolható SKU-k. Ha például egy P3 SKU (32 mag) hozzon létre három kapacitások használható: egy P2 (16 mag), és két P1 (2 x 8 mag). Továbbfejlesztett teljesítmény és méret elérhető kisebb méretű kapacitások létrehozásával, és ez a témakör a következő cikkben a [optimalizálása prémium szintű kapacitások](#optimizing-premium-capacities) szakaszban. Az alábbi képen egy példa a telepítő a fiktív Contoso szervezet öt prémium szintű kapacitások álló (P1, és 2 x 3 x P3) minden egyes tartalmazó alkalmazás-munkaterületek, és számos munkaterületek megosztott kapacitáshoz tartoznak.

![Egy példa a telepítő a fiktív Contoso szervezet számára](media/whitepaper-premium-deployment/contoso-organization-example.png)

Prémium szintű kapacitáshoz melyik adatközpontra (meghatározott földrajzi régiókban) keresztül Power BI-tartalom található rendszergazdai felügyelet biztosít a Power BI-bérlő otthoni régiója régióban is hozzárendelhető. \[[12](#endnote-12)\]

A Power BI szolgáltatás-rendszergazdák és az Office 365 globális rendszergazdái módosíthatják a prémium szintű kapacitások. Pontosabban ezek a következők:

- Vertikális felskálázás vagy leskálázás erőforrások a kapacitás méretének módosítása. Azonban nincs lehetőség alacsonyabbra a P SKU-EM termékváltozatra cserélni, vagy a verziófrissítésre ez fordítva is igaz.
- Adja hozzá, vagy távolítsa el a kapacitás-rendszergazdák
- A hozzárendelési engedéllyel rendelkező felhasználók hozzáadása vagy eltávolítása
- Adja hozzá, vagy távolítsa el a további munkaterhelések
- Régió módosítása

A hozzárendelési engedéllyel kell rendelnie a munkaterületet egy adott prémium szintű kapacitáshoz. Az engedélyek az egész vállalattal, adott felhasználókra vagy csoportokra is megadható.

Alapértelmezés szerint prémium szintű kapacitások támogatja a Power BI-lekérdezések futtatásával kapcsolatos számítási feladatokhoz. Három további számítási feladatokat is támogatja: **Oldalakra osztott jelentések**, **adatfolyamok**, és **AI**. Minden számítási feladathoz szükséges konfigurálása a maximális memóriát (a teljes szabad memória százalékaként), a munkaterhelés szerint használható. Fontos megérteni, hogy növelje a maximális memórialefoglalások befolyásolhatja a üzemeltethető aktív modellek számát és az átviteli sebességet a frissítések.

A memória adatfolyamokhoz dinamikusan, lapszámozott jelentésekhez viszont statikusan van lefoglalva. A maximális memóriafoglalás statikusan oka, hogy oldalakra osztott jelentések futtathatók a kapacitás biztonságos tartalmazott szóközzel. Ha a beállítás többoldalas jelentések memória, mivel csökkenti a rendelkezésre álló memória a modell betöltése gondot kell fordítani.

|                     | EM3                      | P1                       | P2                      | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|
| Oldalakra osztott jelentések | N.A. | Alapértelmezés szerint 20%; minimum 10% | Alapértelmezés szerint 20%; minimum 5% | Alapértelmezés szerint 20%; minimum 2,5% |
| Adatfolyamok | Alapértelmezés szerint 20%; minimum 8%  | Alapértelmezés szerint 20%; minimum 4%  | Alapértelmezés szerint 20%; minimum 2% | Alapértelmezés szerint 20%; minimum 1%  |
| AI | N.A. | 20 %-os alapértelmezett; 20 %-os minimális  | Alapértelmezés szerint 20%; minimum 10% | Alapértelmezés szerint 20%; minimum 5%  |
| | | | | |

Prémium-kapacitás törlése lehetséges, és nem eredményez a munkaterületekről és a tartalom törlését. Ehelyett azt át minden egyes munkaállomásokra koncentrálják megosztott kapacitásra. A prémium szintű kapacitás egy másik régióban lett létrehozva, amikor a munkaterület megosztott kapacitás az otthoni régió kerül.

### <a name="assigning-workspaces-to-capacities"></a>Munkaterületek hozzárendelése kapacitások

Munkaterületek hozzárendelheti egy prémium szintű kapacitást a **Power BI felügyeleti** **portál** vagy - alkalmazás-munkaterület – az a **munkaterület** ablaktáblán.

Kapacitás-rendszergazdák, valamint az Office 365 globális rendszergazdák vagy a Power BI szolgáltatás-rendszergazdák, tömegesen rendelhet hozzá munkaterületeket, a **Power BI felügyeleti** **portál**. Hozzárendelt tömeges alkalmazhatók:

- **Munkaterületek felhasználók szerint** : Minden munkaterület tulajdonosa a felhasználókat, beleértve a személyes munkaterületeket, a prémium szintű kapacitás vannak hozzárendelve. Ide tartoznak a ismételt hozzárendelése után a munkaterületeket, amikor már hozzá van rendelve egy másik prémium szintű kapacitáshoz. Emellett a felhasználók is hozzárendelt munkaterület-hozzárendelési engedélyt.

- **Adott munkaterületek**
- **A teljes cég munkaterületei** : Minden munkaterület, beleértve a személyes munkaterületeket a prémium szintű kapacitás vannak hozzárendelve. Emellett az összes jelenlegi és jövőbeli felhasználónak hozzárendelt munkaterület-hozzárendelési engedélyt. \[[14](#endnote-14)\]

Egy prémium szintű kapacitáshoz is hozzáadhatók a munkaterület használatával a **munkaterület** ablaktáblán, lehetővé téve a felhasználó mindkét munkaterület-rendszergazda, és a hozzárendelési engedéllyel rendelkezik.

![A munkaterület ablak használó rendelnie a munkaterületet egy prémium szintű kapacitáshoz](media/whitepaper-premium-deployment/assign-workspace-capacity.png)

Munkaterületek rendszergazdái eltávolíthatják a munkaterületet egy kapacitáshoz (a megosztott kapacitás) anélkül, hogy a hozzárendelési engedéllyel. A munkaterület eltávolítása a munkaterület dedikált kapacitás hatékonyan helyez át a megosztott kapacitásra. Vegye figyelembe, hogy egy munkaterületet egy prémium szintű kapacitáshoz eltávolítása negatív következményekkel eredményez, például a megosztott tartalom a Power BI ingyenes elérhetetlenné lehetnek licenccel rendelkező felhasználók vagy az ütemezett frissítés felfüggesztését a támogatott keretek túllépésekor megosztott kapacitás.

A Power BI szolgáltatásban a gyémánt ikon jelzi, hogy a munkaterület neve adorns egy munkaterületet egy prémium szintű kapacitáshoz rendelve könnyedén azonosíthatók.

![Egy munkaterületet egy prémium szintű kapacitáshoz rendelve azonosítása](media/whitepaper-premium-deployment/premium-diamond-icon.png)

### <a name="monitoring-capacities"></a>Figyelési kapacitások

Prémium szintű kapacitások figyelés segítségével a rendszergazdák hogyan hajtja végre a kapacitások megismerése. Kapacitások használatával figyelhető a [Power BI Premium kapacitás-metrikák alkalmazás](service-admin-premium-monitor-capacity.md) vagy a [Power BI felügyeleti portáljához](service-admin-premium-monitor-portal.md).

#### <a name="interpreting-metrics"></a>Metrikák értelmezése

Metrikák ellenőrizni kell létesíteni egy erőforrás-használat és a számítási feladatok tevékenység alapvető ismeretekkel. Ha a kapacitás lassú, fontos tudni, hogy milyen metrikákat kíván monitorozni, és teheti következtetéseket.

Ideális esetben lekérdezések szolgáltatásszintről egy második rugalmas élményeket nyújthat a felhasználóknak a jelentés és a magasabb szintű lekérdezési teljesítmény engedélyezéséhez. Ez általában a kisebb aggodalomra ad okot amikor – beleértve a frissítések – háttérfolyamatok végrehajtásához hosszabb időt is igénybe.

Lassú jelentések általában arra utalhat, hogy egy túlzott fűtésrendszerek kapacitást is lehet. Nem sikerült betölteni a jelentéseket, ha ez az arra utalhat, hogy egy túlterhelt fűtött kapacitást. Mindkét esetben a fő ok lehet tulajdonítható sok tényező befolyásolja, többek között:

- **Sikertelen lekérdezések** természetesen jelzi a rendelkezésre álló memória mennyisége, és hogy a modell nem tölthető be a memóriába. A Power BI szolgáltatás megkísérli betölteni a modell 30 másodpercig, mielőtt hibát jelentene.

- **Túl sok lekérdezés várakozási idők** számos oka lehet:
  - A Power BI szolgáltatásban, először szükség a modellek fürtből, és töltsön be a to-be lekérdezett modell (visszaírási, hogy magasabb adatkészlet kiürítési önálló összeg nem arra utalhat, hogy kapacitás stress, kivéve, ha hosszú lekérdezési várakozási időt memóriaakadozás jelző fűzni)
  - Modell betöltése időpontokban (különösen a nagy modell betöltése a memóriába várakozás)
  - Hosszú ideig futó lekérdezések
  - Túl sok LC\DQ kapcsolat (kapacitáskorlátait meghaladó)
  - CPU színtelítettség
  - A jelentés összetett tervek a Vizualizáció túl sok (visszaírási, hogy minden egyes vizuális elem lekérdezés) lapon
- **Hosszú lekérdezés időtartamának összegénél** azt jelzi, hogy modell tervek nem vannak optimalizálva, különösen akkor, ha több adatkészlet kapacitásban aktív, és csak egy adatkészlet van előállító hosszú lekérdezés időtartamának összegénél. Ez azt sugallja, hogy a kapacitás elég ellátva erőforrással, és hogy az kérdés adatkészlet az optimálisnál rosszabb vagy csak lassú. Hosszú ideig futó lekérdezések problémás lehet, mert akkor képes blokkolni a hozzáférést, más folyamatok által igényelt erőforrások.
- **Frissítése hosszú várakozási idők vagy AI hívás várakozási idők** memóriát sok az aktív modellek miatt nincs elég memória, de akár (meghaladó párhuzamos frissítés korlátok), hogy problémás frissítést blokkolja a többi frissíti.

A mérőszámok használatát bemutató részletesebb magyarázatáért foglalkozik mellett a [optimalizálása prémium szintű kapacitások](#optimizing-premium-capacities) szakaszban.

## <a name="optimizing-premium-capacities"></a>Prémium szintű kapacitások optimalizálása

Ha prémium szintű kapacitás teljesítménybeli problémák merülnek fel, a közös először megközelítést az optimalizálásában vagy finomhangolása a már telepített megoldások elfogadható válaszidők visszaállításához. A legfontosabb közösségértékek, hogy kerülje a további prémium szintű kapacitás vásárlásával, kivéve, ha igazolható.

Ha további prémium szintű kapacitáshoz szükség, két lehetőség van, amely ebben a szakaszban később tárgyalja:

- Vertikális felskálázás a prémium szintű kapacitás
- Adjon hozzá egy új prémium szintű kapacitás

Végül tesztelési módszer és a prémium szintű kapacitás méretezése bétaszolgáltatás ebben a szakaszban.

### <a name="general-best-practices"></a>Általános – gyakorlati tanácsok

Mindent megtesz érhet el a legjobban kihasználtságát és a teljesítményt van néhány ajánlott eljárást, amely is veszik a általános ajánlásként. Ezek a következők:

- Alkalmazás-munkaterületek helyett személyes munkaterületek használatával
- Üzletileg kritikus és önkiszolgáló bi-ban (összetett) elkülönítésére, különböző kapacitások

  ![Kritikus fontosságú üzleti és az önkiszolgáló BI szétválasztása eltérő kapacitások be](media/whitepaper-premium-deployment/separate-capacities.png)

- Ha a tartalom megosztása csak a Power BI Pro-felhasználók, előfordulhat, nem kell tárolnia a tartalmat a dedikált kapacitás
- Dedikált kapacitás használja, ha egy adott frissítés idejének eléréséhez, illetve a funkciók szükség, például nagyméretű adatkészletek vagy többoldalas jelentés

### <a name="addressing-common-questions"></a>Addressing Common Questions

A Power BI Premium üzemelő példányok optimalizálásához munkaterhelési követelményeinek, a rendelkezésre álló erőforrások és azok hatékony felhasználása megismerése érintő összetett témakör.

Ez a témakör hét gyakori kérdésekre, leíró lehetséges problémák és magyarázatok és hogyan azonosíthatja és megoldhatja őket, a címeket.

#### <a name="why-is-the-capacity-slow-and-what-can-i-do"></a>Miért van a lassú kapacitást, és mi a teendő?

Nincsenek számos oka lehet, amely hozzájárulhat a lassú prémium-kapacitás. Ez a kérdés további információra van szüksége, megismerheti, mit kell érteni lassú. Azok a jelentések betöltődni? Vagy azok sikertelen betöltéséhez? Lassúak a jelentésvizualizációk betölteni vagy frissíteni, ha a felhasználók használják a jelentést? Frissítések tart hosszabb, mint a várt, vagy a korábban észlelt?

Kellene szerzett megértéséhez okát, majd elkezdheti vizsgálatára. Az alábbi hat kérdésekre adott válaszok segítségével történő több konkrét problémák.

#### <a name="what-content-is-using-up-my-capacity"></a>Milyen tartalmat használ fel saját kapacitása?

Használhatja a **Power BI Premium kapacitás-metrikák** alkalmazás szűrés a kapacitást, és tekintse át a munkaterület-tartalom a teljesítmény-mérőszámon. Tekintse át a teljesítmény-mérőszámok és erőforrás-használatra óránként egy prémium szintű kapacitáson belül tárolt összes tartalom az elmúlt hét nap, lehetőség. Ez gyakran az az első lépés, ha a prémium szintű kapacitás teljesítményével kapcsolatos általános gondja hibaelhárítás.

Alapvető metrikák figyelése a következők:

- Átlagos CPU és a magas kihasználtság száma
- Átlagos memória és a magas kihasználtság száma és a memóriahasználat, adott adatkészletek, adatfolyamok és oldalakra osztott jelentések
- A memóriában aktív adatkészlet
- Átlagos és maximális lekérdezési időtartamok
- A lekérdezés átlagos várakozási idő
- Átlagos adatkészletet és adatfolyam alkalommal frissítése
- Átlagos mesterséges Intelligencia alkalommal hívja, és a várakozási idő

Ezenkívül a Power BI alkalmazásban prémium szintű kapacitás metrikák, aktív memória jeleníti meg egy jelentést, amely nem zárható ki, mert az elmúlt három percben használja kiosztott memória teljes mennyisége. Egy nagy és/vagy aktív adatkészlet frissítési várakozási idő kiugróan magas sikerült megfeleltetendő.

A "Top 5 által átlagos időtartam" diagram emeli ki, az az öt legaktívabb adatkészletek, többoldalas jelentések, adatfolyamok és AI-hívások kapacitás erőforrásokat. Az első öt listák tartalom deduplikációra vizsgálat és a lehetséges optimalizálás.

#### <a name="why-are-reports-slow"></a>Miért olyan jelentések lassú?

Az alábbi táblázat ismerteti a lehetséges problémákat, és hogy hogyan azonosíthatja és kezelni őket.

##### <a name="insufficient-capacity-resources"></a>Nincs elegendő kapacitás erőforrások

| Lehetséges magyarázata | Azonosítása | Megoldását |
| --- | --- | --- |
| Összes aktív magas memóriahasználat (modell nem zárható ki, mert használja az elmúlt három perc)<br><br> Lekérdezés több magas kiugrások várakozási idő<br><br> Frissítés várakozási időt több magas kiugrások | Figyelheti a mérőszámokat memória \[ [18](#endnote-18)\], és a kizárási \[ [19](#endnote-19)\] | Csökkentse a modell mérete, vagy a DirectQuery mód átalakítása – lásd a [optimalizálása modellek](#optimizing-models) ebben a szakaszban a témakör<br><br> Vertikális felskálázás a kapacitás<br><br> Rendelje hozzá a tartalmat egy másik kapacitás |

##### <a name="inefficient-report-designs"></a>A jelentés nem elég hatékony tervek

| Lehetséges magyarázata | Azonosítása | Megoldását |
| --- | --- | --- |
| Jelentésoldalak (interaktív szűrés is indíthat vizualizációnként legalább egy lekérdezést) számos olyan vizualizációkat tartalmaznak<br><br> Vizualizációk a szükségesnél több adat lekérése | Tekintse át a jelentés tervek<br><br> Interjú jelentés felhasználóknak megérteni, hogyan kommunikáljanak a jelentések<br><br> Adatkészlet lekérdezés metrikák figyelése \[ [20](#endnote-20)\] | Egy-egy lapon kevesebb vizualizációt tartalmazó újratervezése jelentések |

##### <a name="dataset-slow-especially-when-reports-have-previously-performed-well"></a>Adatkészlet lassú (különösen ha jelentéseket korábban végrehajtása után is)

| Lehetséges magyarázata | Azonosítása | Megoldását |
| --- | --- | --- |
| Egyre inkább nagy mennyiségű adatok importálása<br><br> Összetett vagy nem elég hatékony számítási logikát, beleértve az RLS-szerepkörök<br><br> A modell nem teljes mértékben optimalizálva<br><br> (DQ/LC) Átjáró késés<br><br> Lassú DQ adatforrás lekérdezési válaszidők | Tekintse át a modell tervek<br><br> Átjáró-teljesítményszámlálók figyelése | Tekintse meg a [optimalizálása modellek](#optimizing-models) ebben a szakaszban a témakör |

##### <a name="high-concurrent-report-usage"></a>Egyidejű jelentés magas kihasználtsága

| Lehetséges magyarázata | Azonosítása | Megoldását |
| --- | --- | --- |
| A lekérdezési várakozási időt<br><br> CPU színtelítettség<br><br> Túllépte a DQ/LC kapcsolat korlátai | Monitorozhatja a processzorkihasználtságot \[ [21](#endnote-21)\], lekérdezés várakozási idő és a DQ/LC kihasználtság \[ [22-es](#endnote-22) \] metrikák + lekérdezés időtartamának összegénél – Ha ingadozik is egyidejűségi problémák jelzi | Vertikális felskálázás a kapacitást, vagy rendelje hozzá a tartalmat egy másik kapacitás<br><br> Egy-egy lapon kevesebb vizualizációt tartalmazó újratervezése jelentések |

#### <a name="why-are-reports-not-loading"></a>Miért van a jelentések nem töltődik be?

Ha jelentéseket feltöltheti azokat, a legrosszabb, valamint arról, hogy a kapacitás nem rendelkezik elég memóriával és túlterhelt fűtött bejelentkezési. Ez akkor fordulhat elő, amikor az összes betöltött modellek vannak aktívan kérdeznek le, és ezért nem dobható, és frissítési műveleteket már fel van függesztve vagy késleltetett. A Power BI szolgáltatás megkísérli az adatkészlet betöltése 30 másodpercet, és a felhasználó szabályosan értesítést kap, próbálkozzon újra hamarosan javaslatot a hiba.

Jelenleg nincs nincs a mérőszám a jelentés betöltési hibák figyelése. A probléma lehetséges monitorozási rendszer memóriájában, kifejezetten legmagasabb kihasználtsággal és idővel a legnagyobb kihasználtságú alapján azonosíthatja. Magas adatkészlet adatbázislap és hosszú az adatkészlet frissítési átlagos várakozási idő sikerült javasoljuk, hogy a probléma jelentkezett.

Ez néha csak nagyon történik, ha ez nem tekinthetők a prioritás a probléma. A jelentés felhasználók üzenetet kapnak, hogy a szolgáltatás foglalt, és, hogy azok kell próbálkoznia rövid idő múlva. Ha túl gyakran történik, a probléma a prémium szintű kapacitás vertikális felskálázásával, vagy a tartalom hozzárendelése egy másik kapacitás lehet orvosolni.

A kapacitás rendszergazdák (és a Power BI szolgáltatás-rendszergazdák) figyelheti a **sikertelen lekérdezések** metrika meghatározni, ha ez történik. Akkor is újraindíthatja a kapacitás, minden művelet esetén a rendszer túlterhelési alaphelyzetbe állítása.

#### <a name="why-are-refreshes-not-starting-on-schedule"></a>Miért vannak frissítések nem indul el ütemezés szerint?

Az ütemezett frissítés kezdési idejének nem garantált. Ne felejtse el, hogy a Power BI szolgáltatás mindig rangsorolja interaktív műveletekhez háttérműveletekhez keresztül. Frissítés a háttérben futó művelet, amely akkor fordulhat elő, amikor két feltétel teljesül:

- Nincs elegendő memória
- A prémium szintű kapacitás esetén támogatott egyidejű frissítések száma nem lett túllépve

Ha a feltételek nem teljesülnek, a frissítés várólistára van állítva, addig, amíg kedvező feltételek.

A teljes frissítés, amely az aktuális adatkészlet memória méretének legalább duplán visszaírási szükség. Ha nem áll rendelkezésre elegendő memória áll rendelkezésre, majd a frissítés nem kezdhetik meg modell kiürítési szabadít fel memória – Ez azt jelenti, hogy késések mindaddig, amíg egy vagy több adatkészletet inaktívvá válik, és képes eltávolítani kívánt.

Ne felejtse el, hogy a támogatott maximális egyidejű frissítések számát értéke 1,5-szerese a háttérbeli virtuális magokkal lesz kerekítve.

Egy ütemezett frissítés meghiúsul, ha azt nem akkor kezdődik, a következő ütemezett frissítés határideje megkezdése előtt. Egy igény szerinti frissítést, a felhasználói felületen manuálisan aktivált megpróbálja legfeljebb három alkalommal futtatása korábban sikertelen.

A kapacitás rendszergazdák (és a Power BI szolgáltatás-rendszergazdák) figyelheti a **átlagos frissítése várakozási idő (perc)** metrika meghatározni a megadott időpont és a művelet kezdete közötti átlagos késés.

Amíg egy rendszergazda prioritás, kereskedelmi adatok általában nem frissül, győződjön meg arról, hogy elegendő memória áll rendelkezésre. Ez magában foglalhatja adatkészleteket, ismert elegendő erőforrással rendelkező kapacitások elkülönítése. Lehetőség arra is, hogy a rendszergazdák sikerült egyeztessen a az adatkészlet tulajdonosa szinkronizálások eltolása vagy ütemezett adatok frissítési idejének ütközések minimálisra csökkentése érdekében. Vegye figyelembe, hogy már nem a rendszergazda a frissítési várólista megtekintéséhez, vagy az adatkészlet lekéréséhez ütemezi.

#### <a name="why-are-refreshes-slow"></a>Miért vannak lassú frissítések?

Frissítések lassú - vagy észlelhető (mint az előző gyakori kérdés címek) lassú lehet.

Ha a frissítés tulajdonképpen lassú, számos oka lehet:

- Nem elegendő Processzor (a frissítés nagyon CPU-igényes lehet)
- Nincs elég memória, a frissítés (amely a kezdenie, ha feltételek esetén a mellőzésére kedvező újrabetöltést igényel) felfüggesztése eredményez
- Nem-kapacitási okokból, beleértve az adatok forrása rendszer válaszideje, hálózati késés, érvénytelen engedélyek vagy átjáró teljesítménye
- Adatmennyiség - csak jó okkal konfigurálása növekményes frissítése, ahogy az alábbiakban tárgyalt

Kapacitás rendszergazdák (és a Power BI szolgáltatás-rendszergazdák) figyelheti a **frissítése átlagos időtartam (perc)** összehasonlítás a teljesítményteszt meghatározni az idő múlásával metrika és a **átlagos frissítése várakozási idő (perc)** mérőszámok megállapításához közötti átlagos késés átlagos az ütemezett idő és a művelet megkezdése között.

Növekményes frissítési adatok frissítés időtartama, különösen a nagy méretű adatmodell-táblák jelentősen csökkentheti. Nincsenek a növekményes frissítés négy előnye:

- **Frissítések gyorsabbak** : Egy tábla csak egy részhalmazát kell betöltése során, és csökkenti a Processzor- és használati és párhuzamosság magasabb lehet, ha több partíció frissítése
- **Frissítés történik, csak szükség esetén** : Növekményes frissítési szabályzatok beállíthatók úgy, hogy csak amikor adatok változtak betöltése
- **Frissítések megbízhatóbb** : Ideiglenes adatforrásként szolgáló rendszerekben futó rövidebb kapcsolatok kevésbé érzékenyek, adott válaszának
- **Modellek maradnak vágás** : Növekményes frissítési szabályzatok beállíthatók úgy, hogy automatikusan eltávolítja az előzmények túl egy csúszóablakban idő

További információkért tekintse meg a [növekményes frissítés a Power BI Premium](service-premium-incremental-refresh.md) dokumentumot.

#### <a name="why-are-data-refreshes-not-completing"></a>Miért van az adatok frissítése feladatom befejezése meghiúsul?

Amikor az Adatfrissítés megkezdése, de nem lehetett végrehajtani, számos oka lehet:

- Nincs elég memória, akkor is, ha csak egy modell található a prémium szintű kapacitás, azaz a modell mérete nagyon nagy
- Nem-kapacitási okokból, beleértve a data source rendszer leválasztásának, érvénytelen engedélyek vagy átjáró hiba

A kapacitás rendszergazdák (és a Power BI szolgáltatás-rendszergazdák) figyelheti a **frissítése hibák miatt nincs elegendő szabad memória** metrika.

#### <a name="why-are-ai-calls-failing"></a>Miért vannak az AI-hívások sikertelenek?

AI-hívás több okból meghiúsulhat. A minimális memória elindításához a mesterséges Intelligencia munkaterhelés 5 GB-os, de ez nem minden esetben az egyes bemeneti adatkészlet szükséges. Például automatikus machine learning-modell betanítása szükséges legalább kétszer, és néha többször is feldolgozza a bemeneti adatkészlet méretét. Egy AI-hívás megszakadt is, ha több mint két órát vesz igénybe. Az automatizált machine learning-modell betanítási hívás, amely nem végezte el két órán belül, a legjobb modellt ezen két órán belül található adja vissza.  AI-hívások is interaktív kérelmek, amelyek elsőbbséget szerint lehet megszakítani.

A rendszergazdák célszerű figyelemmel kísérni más kérelmek figyelembe vételével jeleit AI várakozási időt. A rendszergazdák is biztosíthatja, hogy elegendő memória áll rendelkezésre, a mesterséges Intelligencia terheléshez bemeneti adatméretek útként. Ez magába foglaló AI számítási feladatok ismert, hogy elegendő erőforrással kapacitások elkülönítése. Lehetőség arra is, hogy a rendszergazdák sikerült egyeztessen a adatfolyamot tulajdonosok szinkronizálások eltolása, vagy csökkentse az adatfolyamot frissítési idejének ütközések minimalizálása érdekében. Vegye figyelembe, hogy már nem rendszergazdai a mesterséges Intelligencia hívás várólista megtekintéséhez.

### <a name="optimizing-models"></a>Modellek optimalizálása

Optimális modell felépítésének elengedhetetlen egy hatékony és méretezhető megoldások kidolgozását. Azonban ebben a tanulmányban hatókörén kívül esik, adja meg a teljes leírása. Ehelyett ez a szakasz biztosít legfontosabb szempont modellek optimalizálása.

#### <a name="optimizing-power-bi-hosted-models"></a>A Power BI-ban üzemeltetett modellek optimalizálása

Az adatok (ok) hoz és a modell rétegeken prémium kapacitásban lévő üzemeltetett optimalizálása modellek érhető el.

Vegye figyelembe az importálás modell optimalizálási lehetőségeit:

![Az importálás modell optimalizálási lehetőségekkel](media/whitepaper-premium-deployment/import-model-optimizations.png)

Az adatok forrása rétegben:

- Relációs adatforrások előre integráló adatokat, alkalmazza a megfelelő indexeket, olyan táblapartíciók meghatározása a növekményes frissítés időszakokra és számítások materializálása segítségével optimalizálható a leggyorsabb lehetséges frissítési biztosításához (helyén kiszámítása táblák és oszlopok modell) vagy a számítási logika hozzáadása a nézetekhez
- Nem relációs adatforrások előre integrálható relációs adattárak
- Győződjön meg arról, hogy átjárók lehetőleg gépeken dedikált, elegendő hálózati sávszélesség és adatforrások hálózatbővítési elegendő erőforrással rendelkezik

A modell rétegben:

- A Power Query lekérdezést tervek is minimálisra csökkentése vagy összetett átalakítások, és különösen azokkal, amelyek a különböző adatforrások (data warehouse-adattárházak ennek érdekében a kinyerési, átalakítási-betöltési szakaszában) egyesítése. Is biztosítva, hogy a megfelelő az adatforrások adatvédelmi szintjeit vannak beállítva, így elkerülhető igénylő lekérdezések között egy összesített eredményt teljes eredmények betöltése a Power bi-ban.
- A modell szerkezetét meghatározza, hogy az adatok betöltése, és a modell mérete közvetlen hatással van. Azt is úgy, hogy elkerülje a felesleges adatokat (különösen előzményadatok) sorok eltávolítását, szükségtelen oszlopok eltávolításával vagy összegzett adatokat jelez (rovására részletes adatok betöltése) betöltése. Drámai méretének csökkentése nagy számosságú oszlopokat (különösen a szöveges oszlopok), amely tárolja és nem nagyon hatékonyan tömörítése eltávolításával érhető el.
- Egyetlen irányra kapcsolatok konfigurálásával, kivéve, ha van egy jelentős indok arra, hogy engedélyezze a kétirányú szűrés modell lekérdezési teljesítmény javítása érdekében. Fontolja meg továbbá a CROSSFILTER függvény kétirányú szűrés helyett.
- A táblákban összesítési kibővítése a lekérdezési válaszok betöltésével előre összegzett adatok, érhető el, azonban ez a modell és az eredmény mérete megnő a frissítés hosszabb időt. Általában a táblákban összesítési számára lefoglalt nagyon nagy méretű modellek vagy összetett modell műveletekhez.
- Számított táblázatokat, oszlopokat modell méretének növeléséhez és a frissítés hosszabb időt eredményez. Általában egy kisebb tárméret és gyorsabb frissítés érhető el, a tényleges táblán alapuló vagy az adatforrás alapján számítjuk ki. Ha ez nem lehetséges, egyéni oszlopokat a Power Query használatával elérhetővé teheti még több tárterület-tömörítést.
- Előfordulhat, hogy lehetőség a DAX-kifejezésekben a mértékek és RLS-szabályokat, például újraírását logikát, elkerülheti a költséges képletek finomhangolása
- A növekményes frissítés frissítési idő csökkentése érdekében jelentősen, és takarítson meg a memória és CPU. A növekményes frissítés eltávolítása modellméretet vágás tartja előzményadatok is konfigurálható.
- Ha másik, ütköző lekérdezési minták modell sikerült újratervezve két modell szerint. Például bizonyos összes előzmények, valamint is jelen magas szintű összesítések 24 órányi késéssel ugyan jelentéseket. Más jelentések mai adatokat tartalmazó aggódik, és az egyes tranzakciók részletes hozzáférésre van szükségük. Ahelyett, hogy tervezzen egy adott modellt felel meg az összes jelentés az egyes követelményekhez optimalizált két modell létrehozása.

Fontolja meg a DirectQuery modellben optimalizálási lehetőségeit. Ahogy a modellben a lekérdezésekre vonatkozó kérelmek az alapul szolgáló adatforrás problémák, data source optimalizálási fontos rugalmas adatbázismodell lekérdezések továbbítása.

 ![Egy DirectQuery-modell optimalizálási lehetőségek](media/whitepaper-premium-deployment/direct-query-model-optimizations.png)

Az adatok forrása rétegben:

- Az adatforrás is lehet optimalizálni annak érdekében, hogy a leggyorsabb lehetséges lekérdezése előre integrálja az adatokat (ez nem lehetséges a modell rétegben), alkalmazza a megfelelő indexeket, táblapartíciók materializálása meghatározása összegzett adatok (az indexelt nézetek), és számítási végfelhasználónak. A legjobb élményt érhető el, ha a csatlakoztatott lekérdezések csak szűrése, és hajtsa végre a belső illesztések indexelt táblák vagy nézetek között van szükség.
- Győződjön meg arról, hogy átjárók lehetőleg gépeken dedikált, elegendő hálózati sávszélesség és az adatforrás hálózatbővítési elegendő erőforrással rendelkezik

A modell rétegben:

- Power Query lekérdezéssel formátumukban kell lehetőleg átalakítások nem – ellenkező esetben megkísérlik kívül tartani átalakításokat is az abszolút minimális
- Egyetlen irányra kapcsolatok konfigurálásával, kivéve, ha van egy jelentős indok arra, hogy engedélyezze a kétirányú szűrés modell lekérdezési teljesítmény javítása érdekében. Ezenkívül modell, kapcsolatokat konfigurálni kell, hogy feltételezik, hogy hivatkozási integritás (Ha ez a helyzet) és hatékonyabb belső illesztések használata (nem a külső illesztések) adatforrás-lekérdezéseket eredményez.
- Ne hozzon létre a Power Query lekérdezést egyéni oszlopot és a modell számított oszlop – a tényleges táblává alakíthatóak ezeket az adatforrás, amikor lehetséges
- Előfordulhat, hogy lehetőség a DAX-kifejezésekben a mértékek és RLS-szabályokat, például újraírását logikát, elkerülheti a költséges képletek finomhangolása

Fontolja meg egy összetett modell az optimalizálási lehetőségekkel. Ne felejtse el, hogy egy összetett modell lehetővé teszi, hogy importálási és DirectQuery táblákat.

![Egy összetett modell optimalizálási lehetőségek](media/whitepaper-premium-deployment/composite-model-optimizations.png)

- Az importálási és DirectQuery-modellek az optimalizálási témakörök általában ezek tárolási módot használó összetett adatmodell-táblák vonatkoznak.
- Általában arra törekszik, hogy egy elosztott terhelésű kialakítás megvalósítása dimenziótípusnak táblák (üzleti entitásokat képviselő) konfigurálásával táblákként kettős tárolási mód és a tény-type (gyakran nagy táblák, operatív tények képviselő), DirectQuery tárolási mód. Kettős tárolási mód azt jelenti, hogy a is importálhatja, és a DirectQuery tárolási mód, és ez lehetővé teszi, hogy a Power BI szolgáltatás meghatározni a csatlakoztatott egy natív lekérdezés generálása során használandó leghatékonyabb tárolási módját.
- Győződjön meg arról, hogy átjárók lehetőleg gépeken dedikált, elegendő hálózati sávszélesség és adatforrások hálózatbővítési elegendő erőforrással rendelkezik
- Tárolási mód importálás biztosíthat DirectQuery tárolási mód (tény) típusú táblák összegzéséhez drámai lekérdezési teljesítményt érintő továbbfejlesztés összesítések táblák konfigurálva. Ebben az esetben összesítési táblák a modell méretének növekedését és növelheti a frissítés idejét, és gyakran ez a lekérdezések egy elfogadható kompromisszum.

#### <a name="optimizing-externally-hosted-models"></a>Optimizing Externally-Hosted Models

Számos optimalizálási lehetőségekkel tárgyalt a [Optimizing Power BI-Hosted modellek](#optimizing-power-bi-hosted-models) a témakör a modellek az Azure Analysis Services és az SQL Server Analysis Services fejlesztett is vonatkozik. Egyértelmű kivétel bizonyos funkciók, amely jelenleg nem támogatottak, többek között összetett modelleket és összesítési táblák.

Egy további szempont, külsőleg üzemeltetett adatkészletek esetében, az adatbázis-üzemeltetési viszonyítva a Power BI szolgáltatásban. Az Azure Analysis Services esetén ez azt jelenti, hogy az Azure-erőforrás létrehozása a Power BI-bérlő (otthoni régiója) ugyanabban a régióban. Az SQL Server Analysis Services esetén az IaaS Ez azt jelenti, hogy ugyanabban a régióban a virtuális Gépet üzemeltető, és a helyszínen, az azt jelenti, hogy egy hatékony átjáró telepítőjének biztosítása.

Egy feltöltési, érdemes lehet, fontos megjegyezni, hogy az Azure Analysis Services-adatbázisokat és SQL Server Analysis Services táblázatos adatbázisok megkövetelése, hogy a modellek a memóriába teljes-lekérdezése támogatásához, hogy azok továbbra is van minden alkalommal. A Power BI szolgáltatásban, például szükség van elegendő memória a frissítés, ha a modell online kell maradnia a frissítés során. Ellentétben a Power BI szolgáltatásban, és nincs modellek automatikusan elavult adataikkal memória kihasználtsága alapján. A Power BI Premium, ezért maximalizálhatja a modell lekérdezés alacsonyabb memóriahasználat a hatékonyabb megközelítést kínál.

### <a name="capacity-planning"></a>Kapacitástervezés

Prémium-kapacitás mérete határozza meg, a rendelkezésre álló memória és a processzor-erőforrások és a kapacitás vonatkozó korlátozások. A prémium szintű kapacitások számát is fontos szempont, mint létrehozása több prémium szintű kapacitások segíthet egymástól számítási feladatok elkülönítésére. Vegye figyelembe, hogy storage 100 TB-os kapacitás csomópontonként, és ez valószínűleg több mint elegendő, ha bármilyen számítási feladatot.

Amely meghatározza, hogy a méretét és a prémium szintű kapacitások kihívást jelenthet, kifejezetten rendszergazdák számára a kezdeti kapacitások hoz létre. Az első lépés, ha kapacitásméretezést munkaterhelés átlagos jelölő várt mindennapos használatának megértéséhez. Fontos tudni, hogy nem minden munkaterhelésről sem egyenlő. Például: a álló kínálat - egyik végén 100 egyidejű felhasználó fér hozzá egyetlen vizualizációt tartalmazó egyetlen jelentésoldalon könnyen elérhető. Még - - spektrum másik végén 100 egyidejű felhasználó fér hozzá a különböző jelentések 100, egyenként 100 Vizualizációk a jelentés oldalon lévő hozom létre kapacitás-erőforrások különböző igényeknek.

Kapacitás-rendszergazdák ezért figyelembe kell vennie a sok tényező befolyásolja a környezet, a tartalom és a várható használat. Maximalizálhatja a tárolókapacitás kihasználtságát konzisztens gyorsaság elfogadható várakozási időt és kiürítési díjak adatbáziscsoportok legfontosabb célja. Tényezőket veszi figyelembe a következők lehetnek:

- **Modell mérete és az adatok jellemzői** : Importált modelleken teljes betöltése a memóriába, hogy a lekérdezés vagy frissíteni kell. LC/DQ adatkészletek jelentős processzoridő- és valószínűleg jelentős összetett mértékeket és az RLS-szabályok kiértékelése lehet szükség. Memória és a feldolgozó mérete és a LC/DQ lekérdezések átviteli sebességére is korlátozza a kapacitás méretét.
- **Egyidejű aktív modellek** : Különböző importált modelleken egyidejű lekérdezését fog nyújtani ajánlott válaszidejét és teljesítmény, ha azokat a memóriában marad. Gazdagép összes erősen lekérdezett modelleket, hogy a frissítéshez további memória elegendő memóriával kell lennie.
- **Importálás a modellfrissítéshez** : Az alkalmazásfrissítési típus (teljes vagy növekményes), az időtartam és a Power Query lekérdezéseket, és a számított tábla vagy oszlop logikai összetettsége befolyásolhatja a memória és a processzor terhelését is különösen. Egyidejű frissítések csak korlátozottan működik, a kapacitás méretét (1,5 x backend mag, kerekítve) szerint.
- **Egyidejű lekérdezések** : Számos egyidejű lekérdezéseket eredményezhet a nem válaszoló jelentések mikor processzor- és LC/DQ kapcsolatok meghaladja a kapacitási korlátot. Ez különösen a helyzet sok vizualizációt tartalmazó jelentésoldalak.
- **Adatfolyamok, többoldalas jelentések és a mesterséges Intelligencia funkciók** : A kapacitás a adatfolyamok, a többoldalas jelentések és a mesterséges Intelligencia funkciók, a kapacitás memóriával konfigurálható maximális százalékos igénylő konfigurálható. Adatfolyamot dinamikusan lefoglalja a memóriát, de ennek statikusan a többoldalas jelentések és a mesterséges Intelligencia számítási feladatok számára.

Ezek a tényezők mellett a kapacitás-rendszergazdák is érdemes lehet létrehozni több kapacitások. Több kapacitás lehetővé teszik a számítási feladatok elkülönítése és beállítható úgy, hogy prioritást számítási feladatok rendelkezik garantált erőforrások biztosítása. Ha például két kapacitások üzleti szempontból kritikus fontosságú számítási feladatok elkülönítése önkiszolgáló BI összetett számítási feladatok is létrehozható. Az üzleti szempontból kritikus fontosságú kapacitása nagy vállalati modellek, így azokat a garantált erőforrásokkal rendelkező authoring hozzáférés csak az informatikai részleg számára biztosított elkülönítéséhez használható. Az összetett kapacitás, kisebb modelleket egyre nagyobb számban üzemeltetéséhez az üzleti elemzők számára biztosított hozzáférés használható. Az összetett kapacitás esetenként tapasztalhat, amelyek tolerálható lekérdezés vagy a frissítés vár.

Az idő múlásával a kapacitás-rendszergazdák tudja osztani a munkaterületek kapacitások között munkaterületek, vagy a munkaterületek között kapacitások közötti áthelyezése a tartalmat, és a kapacitások kiterjesztése vagy szűkítése. Általában nagyobb üzemeltetni, vertikális felskálázás és a magasabb szintű egyidejűség érdekében, modellek horizontális felskálázás.

Ne felejtse el, hogy a bérlő virtuális magok licencet vásárol biztosít. Vásárlása egy **P3** előfizetés segítségével hozzon létre egyet, vagy akár négy prémium szintű kapacitás, azaz P3 vagy a x P2 2 vagy 4 x 1 x P1. Emellett egy P2 szintű kapacitás, P3 kapacitásokhoz Továbbfejlesztő, mielőtt is mérlegelni történő felosztásának eredménye a virtuális magok két P1 szintű kapacitások létrehozása.

### <a name="testing-approaches"></a>Tesztelési módszer

A kapacitás méretét dönthető el, ha tesztelési végezhető létrehozása az ellenőrzött környezetben. A gyakorlati és gazdaságos lehetőség, hogy hozzon létre egy Azure (termékváltozatok) kapacitást, megjegyezni, hogy a P1 kapacitás, az A4 kapacitás, a P2 az azonos méretű és P3 kapacitások akkora, mint a A5 és az a6-os kapacitások jelölik. Azure kapacitások gyorsan létrehozhatók és óradíjat számítjuk fel. Tehát tesztelés befejezése után a egyszerűen törölje őket keletkezhetnek költségek leállítása.

A vizsgálati tartalom is hozzáadhatók a munkaterületek létrehozása az Azure kapacitás, és egyéni felhasználóként is jelentések futtatásával hozzon létre egy valósághű és reprezentatív munkaterhelés-lekérdezések. Ha importált modelleken, is minden modell frissítésének kell végrehajtani. Monitorozási eszközökkel, majd segítségével minden metrika erőforrás-használat megértéséhez tekintse át.

Fontos, hogy a vizsgálatok megismételhető: Tesztek többször kell futtatni, és továbbítsa körülbelül ugyanazt az eredményt, azok minden alkalommal, amikor. Ezekkel az eredményekkel átlagosan extrapolálja, és megbecsülheti a számítási feladatok valódi éles körülmények között is használható.

Szeretne létrehozni egy terhelési teszt, érdemes a terhelésteszt valósághű számítási feladatok szimulálásához alkalmazás lehet. Hogyan érhető ez tulajdonságairól ebben a tanulmányban hatókörén kívül vannak. További információk egy kódmintát, tekintse meg a [terhelési tesztelés a Power BI-alkalmazások a Visual Studio terhelési teszt](https://blogs.msdn.microsoft.com/charles_sterling/2018/04/04/webinar-load-testing-power-bi-applications-with-visual-studio-load-test/) webináriumra.

## <a name="exploring-real-world-scenarios"></a>Valós Életből vett felfedezése

Ebben a szakaszban számos való életből vett forgatókönyv jelenik meg a gyakori problémák vagy kihívásokat, hogyan azonosíthatja azokat, és hogyan oldhatja meg őket:

- [Az adatkészletek naprakészen tartása](#keeping-datasets-up-to-date)
- [Az adatkészletek lassan válaszol azonosítása](#identifying-slow-responding-datasets)
- [Okainak azonosítása vonatkozó szórványosan lassú-adatkészletek](#identifying-causes-for-sporadically-slow-responding-datasets)
- [Meghatározása, hogy van-e elegendő memória](#determining-whether-there-is-enough-memory)
- [Amely meghatározza, hogy van-e elegendő Processzor](#determining-whether-there-is-enough-cpu)

A lépéseket, valamint különböző példákkal diagram és táblázat származnak az **Power BI Premium-kapacitás metrikák alkalmazás** (alkalmazás), hogy a Power BI-rendszergazda hozzáférést kap.

### <a name="keeping-datasets-up-to-date"></a>Az adatkészletek fel tartja a mai napig

Ebben a forgatókönyvben vizsgálat lett elindítva, amikor a felhasználók kifogásolt, hogy a jelentés adatokat néha tűnt, régi vagy "elavult".

Az alkalmazásban a rendszergazda kommunikál a **frissíti** vizualizációt, a rendezés adatkészletek a **maximális várakozási idő** statisztika csökkenő sorrendben. Ez segít azokat az adatkészleteket, amelyek rendelkeznek a leghosszabb idő, a munkaterület neve szerint csoportosítva várjon felfedéséhez.

![Adatkészlet frissítések maximális várakozási idő, munkaterület szerint csoportosítva csökkenő sorrendben rendezve](media/whitepaper-premium-deployment/dataset-refreshes.png)

Ezenkívül a **óránkénti átlagos frissítése várakozási idők** vizualizációval, figyelje meg, hogy a frissítés várakozási időt kiugró következetesen körülbelül 4 du minden nap.

![Frissítés vár csúcs rendszeres időközönként du. 4:](media/whitepaper-premium-deployment/peak-refresh-waits.png)

Nincs magyarázatairól több ezeket az eredményeket:

- Túl sok frissítési kísérlet sikerült kell zajló egyszerre, meghaladja a határoz meg a kapacitás-csomópontot (hat egyidejű frissíti az alapértelmezett memória mennyiségét a P1 szintű)

- Lehet, hogy frissíteni kell az adatkészletek túl nagy rendelkezésre álló memória (legalább 2 x teljes memóriaigényének lesz szükség)
- Nem elég hatékony Power Query-logika előfordulhat, hogy lehet eredményez memória kihasználtsága ugrásszerű adatkészlet frissítése során. A foglalt kapacitás a fizikai korlátot, a frissítés sikertelen, és potenciálisan érintő műveletek más jelentés megtekintése a kapacitás esetenként ezt is elérheti.
- Gyakran lekérdezett adatkészleteket szeretne maradni a memóriában befolyásolhatja az egyéb adatkészletek frissítéséhez, mert korlátozott rendelkezésre álló memória

A Power BI rendszergazdája ez vizsgálatáról be is keressen:

- Az adatok frissítése, ha rendelkezésre álló memória kevesebb, mint a frissítendő adatkészlet mérete x 2 időpontjában alacsony memória
- Adatkészletek, amely is nem frissülnek, és a memória, a frissítés előtt nem voltak, de amely interaktív forgalom megjelenítése során (nagy erőforrásigényű) frissítési idejének megkezdődött. Megtekintheti, mely adatkészleteket is a memóriába betöltött egy adott időpontban egy Power BI rendszergazdai tekintse meg az adatkészletek területén **adatkészletek** egy adott idő alatt, kattintson a sávok az alkalmazást, és több szűrő lapján a **óránként Adatkészlet Counts betöltött**. (Az alábbi képen látható) helyi ugrásszerű azt jelzi, hogy egy órát, amikor több adatkészlet is betölti a memóriába, amely késhet tárhelyének kezdete
- Nagyobb adatkészletet adatbázislap véve helyezze el, amikor ütemezett adatfrissítéseket indul el, jelezve a magas rendelkezésre álló memória mennyisége túl sok különböző interaktív jelentéseket frissítés időpontja előtt szolgáltató által okozott hiba történt. A **óránkénti adatkészlet adatbázislap és memóriát** visual adatbázislap kiugrások egyértelműen utalhat.

Az alábbi képen látható helyi ugrásszerű betöltött adatkészletekben, ami arra utal, interaktív lekérdezés késleltetett frissítések kezdete. Egy adott időszakban az kiválasztása a **óránkénti betöltött adatkészlet Counts** Vizualizáció keresztszűrő a **adatkészlet méretű** visual.

![A betöltött adatkészletek helyi ugrásszerű javasol frissíti az interaktív lekérdezési Késleltetett indítás](media/whitepaper-premium-deployment/hourly-loaded-dataset-counts.png)

A Power BI rendszergazdája is megkísérelheti a probléma megoldásához, győződjön meg arról, hogy elegendő memória áll rendelkezésre, az adatok frissülni fognak, első lépésként lépések végrehajtásával:

- Kapcsolatfelvétel az adatkészlet tulajdonosai és a rendszer arra szinkronizálások eltolása és a lemezterület-adatai frissítése ütemezések
- Adatkészlet csökkenti a szükségtelen irányítópultok vagy az irányítópult eltávolításával lekérdezési terhelése csempéket, különösen azokkal, amelyek a sorszintű biztonság kényszerítése
- Modell adatfrissítéseket felgyorsítva a Power Query logikai optimalizálással, számított oszlopok vagy táblázatok, csökkenti az adatkészletek mérete, vagy annak konfigurálását a nagyobb adatkészletből a végrehajtásához a növekményes adatok frissítése

### <a name="identifying-slow-responding-datasets"></a>Az adatkészletek lassan válaszol azonosítása

Ebben a forgatókönyvben a vizsgálat lett elindítva, amikor a felhasználók kifogásolt, hogy bizonyos jelentések megnyitásához hosszú időbe telt-e, és esetenként lenne lefagy.

Az alkalmazás a Power BI-rendszergazda használhat a **lekérdezés időtartamának összegénél** vizualizációt a legrosszabbul teljesítő adatkészletek meghatározása szerint csökkenő sorrendben rendezi a adatkészletek **átlagos időtartam**. Ez a Vizualizáció is látható adatkészlet lekérdezések száma, így láthatja, hogy milyen gyakran az adatkészletek a rendszer megkérdezi.

![Hogy felfedné legrosszabbul teljesítő adatkészletek](media/whitepaper-premium-deployment/worst-performing-datasets.png)

A Power BI rendszergazdája olvassa el a **lekérdezés időtartamok eloszlása** visual, amely bemutatja egy általános elosztásának bucketed lekérdezési teljesítmény (< 30ms, = 0 – 100 MS, stb.) a szűrt időszakra. Általában a lekérdezéseket, hogy hajtsa végre a megfelelő egy másodperc vagy kevesebb által figyelembe veendő válaszol-e a felhasználók többsége; Hozzon létre egy rossz teljesítmény érzete általában lekérdezéseket, amelyek hosszabb időt vesz igénybe.

A **óránkénti lekérdezés időtartamok eloszlása** Vizualizáció lehetővé teszi, hogy a Power BI rendszergazdáját, hogy ha a kapacitás teljesítmény sikerült rendelkezik lett által tapasztalt óránként időszakainak, gyenge. Minél nagyobb a sáv szegmensek, amelyek lekérdezési időtartamok több mint egy másodperc, a nagyobb a kockázat, hogy a felhasználók lássák fog gyenge teljesítményt eredményez.

A Vizualizáció interaktív, és ha a sáv szegmens választja, a megfelelő **lekérdezés időtartamának összegénél** visual a jelentés oldalon lévő táblázat keresztszűrhető jelöli, az adatkészletek megjelenítése. A keresztszűrés lehetővé teszi, hogy a Power BI rendszergazdáját, hogy könnyen azonosíthassa, amely adatkészletek lassan válaszol.

Az alábbi képen látható Vizualizáció szűrve **óránkénti lekérdezés időtartama Disztribúciók**, fókuszáló óránként gyűjtők a legrosszabbul teljesítő adatkészleteken. 

![Szűrt óránkénti lekérdezés időtartama Disztribúciók visual látható a még rosszabb adatkészletek végrehajtása](media/whitepaper-premium-deployment/hourly-query-duration-distributions.png)

A gyenge teljesítő adatkészlet egy adott 1 órás időtartam azonosítja, miután a Power BI rendszergazdája segítségével megvizsgálhatja, hogy gyenge teljesítményt egy túlterhelt kapacitást okozza, vagy egy rosszul miatt tervezett adatkészlet vagy jelentés. Ennek érdekében is hivatkozhatnak a **várjon gyorsaság** Vizualizáció, és a lekérdezések átlagos várakozási idő csökkenő rendezés adatkészletek. Lekérdezések álló várnak, ha az adatkészlet egy nagy kereslet okozza valószínűleg a sok lekérdezést vár. Ha az átlagos lekérdezési idő jelentősen kell (> 100 ms), akkor érdemes lehet megfontolni áttekintése az adatkészlet és jelentés megtekintéséhez, ha optimalizálást lehet végrehajtani. Például esetleg kevesebb vizualizációt megadott jelentésoldalak vagy a DAX-kifejezés optimalizálása.

![A lekérdezés várakozási idők Vizualizáció segít a gyengén teljesítő adatkészlet feltárása](media/whitepaper-premium-deployment/query-wait-times.png)

Nincsenek lekérdezési várakozási idő Összeállíthatunk adatkészletei több lehetséges oka:

- Ez az optimálisnál rosszabb modell kialakítást, a mértékkifejezéseik vagy még jelentéstervező – minden körülmények között, amelyek hozzájárulhatnak a hosszú ideig futó lekérdezéseket, amelyek nagy mértékű CPU felhasználását. Ez kényszeríti, várja meg, amíg a szálak CPU elérhetővé válnak, és hozhat létre üzleti csúcsidőben fordul elő egy convoy hatás (csávából gondolkodási forgalmat), új lekérdezéseket. A **lekérdezési várakozások** fog a lap a fő erőforrást annak megállapításához, hogy adatkészletek rendelkeznek-e a lekérdezések magas átlagos várakozási időt.
- Nagyszámú egyidejű kapacitás felhasználók (több és több ezer) ugyanaz a jelentés vagy adatkészlet felhasználása. Akkor is a jól megtervezett adatkészletek egy egyidejűségi küszöbérték rosszul hajthat végre. Ez jelentősen nagyobb értéket megjelenítő, a lekérdezés számolja, mint a többi adatkészletek megjelenítése egyetlen adatkészlet általában jelzi (azaz 300K képest egy adatkészlet lekérdezései < 30K lekérdezések minden adathalmaz esetében). A lekérdezési várakozások ehhez az adatkészlethez ütemtervét elindul, és ez lesz látható a bármikor a **lekérdezés időtartamának összegénél** visual.
- Számos különböző adatkészletek egyidejűleg lekérdezett memóriaakadozás okoz, a memória adataikkal gyakran ciklus adatkészletek. Ennek eredményeképpen a felhasználók teljesítménycsökkenést tapasztal, ha az adatkészlet betölti a memóriába. Ennek ellenőrzéséhez a Power BI-rendszergazdák az itt található a **óránkénti adatkészlet adatbázislap és memóriát** visual, ez arra utalhat, hogy nagy számú adatkészletek a memóriába betöltött vannak ismételten a kiürítés alatt.

### <a name="identifying-causes-for-sporadically-slow-responding-datasets"></a>Okainak azonosítása vonatkozó szórványosan lassú-adatkészletek

Ebben a forgatókönyvben a vizsgálat volt aktiválódik, ha a felhasználók ismerteti, hogy a jelentés-Vizualizációk néha korábban úgy tűnt lassan válaszol, vagy válaszképtelenné válik, de máskor voltak intézkedéseket válaszol-e.

Az alkalmazáson belüli a **lekérdezés időtartamának összegénél** szakaszban használt keresse meg a hibát okozó adatkészlet a következő módon:

- Az a **lekérdezés időtartamának összegénél** vizuális a rendszergazda adatkészlet adatkészletet (a felső adatkészletek lekérdezett-gyel kezdődik) szerint szűrt és megvizsgálta a keresztszűrés szűrt sávok a **óránkénti lekérdezés Disztribúciók** visual.
- Ha egy egyetlen óránként sáv bemutatta az összes lekérdezés időtartama csoportokat és más óránként sávok az adott adatkészlethez aránya jelentős változásokat (azaz a arányok a színek között változik jelentősen), azt jelenti, hogy ez az adatkészlet bemutatott szórványos módosítása teljesítmény.
- A bemutató egy gyengén teljesítő lekérdezések szabálytalan része egy órás sávok jelzett timespan, ahol az adatkészlet egy zajos szomszédok hatást, egyéb adatkészletekhez tevékenységek által okozott hatással volt.

Egy adatkészlet teljesítmény jelentős setback történt, ahol a "(3,10s]"végrehajtási időtartamgyűjtő mérete által jelzett a január 30-án egy órán keresztül az alábbi kép. Adott egy órás sávon kattintással tárja fel az összes adathalmaz ideje alatt a memóriába betöltött így felszínre hozza a jelölt sokkal adatkészletek zajos szomszédok hatása okozza.

![Sáv megjelenítése a legrosszabb teljesítmény nagy által](media/whitepaper-premium-deployment/worst-performing-queries.png)

Miután problémás lehet timespan van (azaz során azonosított január 30 a fenti képen) a Power BI rendszergazdája adatkészlet összes szűrő eltávolítása, majd csak az adott időtartam meghatározni, melyik adatkészleteket aktívan kérdeztek ebben az időszakban szűrése. A felső lekérdezett adatkészlet vagy egy a leghosszabb átlagos lekérdezési idő általában a zajos szomszédok hatása sokkal adatkészlete.

Egy megoldás erre a problémára lehet terjeszteni a különböző munkaterületekhez különböző prémium szintű kapacitások vagy a megosztott kapacitás, ha az adatkészlet méretét, a felhasználási követelményeket és az adatok frissítése minták keresztül adatkészletek támogatottak nem sokkal.

Fordítva is igaz lehet. A Power BI rendszergazdája sikerült alkalommal, amikor egy adatkészlet lekérdezés jelentősen javítja a teljesítményt, azonosítása, majd keresse meg mi eltűnt. Adott időpontban hiányzik a bizonyos adatokat, majd, amely segíthet a okozó probléma mutasson.

### <a name="determining-whether-there-is-enough-memory"></a>Meghatározó e nincs elég memória

Annak megállapításához, hogy van-e elegendő memória a kapacitás a számítási feladatok végrehajtásához, a Power BI-rendszergazdák az itt található a **felhasznált memória százalékos** Vizualizáció a a **adatkészletek** az alkalmazás lapján. **Az összes** memória (összesen) a betölti a memóriába, függetlenül attól, hogy aktívan kérdezhető le, vagy azok feldolgozott adatkészletek által felhasznált memóriát jelenti. **Aktív** memória a aktívan feldolgozott adatkészletek által felhasznált memóriát jelenti.

A megfelelő minőségben a Vizualizáció fog kinézni a, megjelenítése egy minden (összesen) közötti résnek és aktív memória:

![Egy megfelelő kapacitást jelennek meg minden (összesen) közötti eseményáramlási kimaradást és aktív memória](media/whitepaper-premium-deployment/memory-healthy-capacity.png)

Tapasztal memóriaterhelés minőségben ugyanabban a vizualizációban egyértelműen jelennek meg a aktív memória és a teljes memória beépül, ami azt jelenti, hogy nem lehet további adatkészletek betölti a memóriába abban az időpontban. Ebben az esetben a Power BI rendszergazdája kattintva **indítsa újra a kapacitás** (a **speciális beállítások** a kapacitás beállításai terület a felügyeleti portál). Újraindítás a kapacitás eredmények összes adatkészletek folyamatban van a memóriából a kiürített, és lehetővé teheti, hogy újra betölti a memóriába (lekérdezések vagy az adatok frissítése) igényeinek megfelelően.

![** Aktív ** memória beépül a ** minden ** memória](media/whitepaper-premium-deployment/memory-unhealthy-capacity.png)

### <a name="determining-whether-there-is-enough-cpu"></a>Meghatározó e nincs elegendő CPU

Általában egy kapacitáshoz átlagos CPU-kihasználtsága 80 % alatt kell maradnia. Ez az érték meghaladja a kapacitás mérete hamarosan eléri a Processzor színtelítettség jelenti.

CPU színtelítettség hatásait ki, a műveletek, a kapacitás sok CPU-környezet kapcsolók végez, akkor próbálja meg minden művelet feldolgozása miatt kell tovább tart a vártnál. Nagy számú lekérdezést a lekérdezési Ez jelzi a prémium szintű kapacitást várakozási idők. A lekérdezési várakozási időt következménye a szokásosnál lassabban válaszképességét. A Power BI rendszergazdai amikor megtekinti a Processzor megtelt könnyen azonosítható a **óránkénti lekérdezés várakozási idő Disztribúciók** visual. Lekérdezés rendszeres csúcsok várakozási számát jelzi a lehetséges CPU színtelítettség idő.

![Lekérdezés rendszeres csúcsok várakozási számát jelzi a lehetséges CPU színtelítettség idő](media/whitepaper-premium-deployment/peak-query-wait-times.png)

Hasonló mintát néha is észlelhető a háttérbeli műveletek, ha azok hozzájárulnak CPU színtelítettség. A Power BI-rendszergazdák is keresni rendszeres ugrásszerű CPU színtelítettség (valószínűleg miatt más folyamatban lévő adatkészlet frissíti és/vagy interaktív lekérdezések) időben jelezheti egy adott adatkészlet frissítési időpont. Ebben a példányban hivatkozó a **rendszer** megtekintése az alkalmazásban esetleg nem feltétlenül mutatja, hogy van-e a CPU 100 %-os. A **rendszer** a nézet jeleníti meg az óradíjas átlagok, de a Processzor is legyen telített (nagy erőforrásigényű) művelet több percig ami megjelenik-e csúcsok, várakozási időt.

Nincsenek egyéb CPU színtelítettség hatásának további részleteiről. Fontos, hogy várjon lekérdezések száma, amíg lekérdezés várakozási idő mindig akkor történik meg bizonyos mértékig lekérdezésteljesítmény teljesítményromlást okozó nélkül. Bizonyos adatkészletek (a hosszabb átlagos lekérdezési idő, jelezve összetettségére vagy nagy méretére) jobban ki CPU színtelítettség hatásait a többinél. Könnyedén azonosíthatja ezeket az adatkészleteket, a Power BI rendszergazdája is keresse meg a szín összeállításban gyűjteménye a módosításokat a **óránkénti várakozási idő terjesztési** visual. Után gyorsabban egy rendkívüli sáv, akkor keresse meg az adatkészleteket, akinek lekérdezést vár ebben az időszakban és is tekintse meg a lekérdezés átlagos várakozási idő átlagos lekérdezési idő képest. Ha két metrikák ugyanolyan nagyságrendű, és a lekérdezési számítási feladatok az adatkészlet nem triviális, valószínű, hogy az adatkészlet nem elegendő Processzor hatással van.

Ennek a hatásnak nyilvánvaló, különösen akkor lehet, ha rövid adatlöketekkel nagyon gyakori lekérdezések (azaz a betanítási munkamenet), a több felhasználó által CPU színtelítettség során minden egyes burst eredményez az adatkészlet használja fel. Ebben az esetben az adatkészlethez jelentős várakozási időt is észlelt és az egyéb adatkészletekhez a kapacitást (zajos szomszédok hatás), mely negatív hatással.

Bizonyos esetekben a Power BI-rendszergazdák kérheti, hogy az adatkészlet tulajdonosa hozzon létre egy kisebb felejtő lekérdezési számítási feladatok létrehoz egy irányítópultot (melyik lekérdezések rendszeres időközönként minden olyan adatkészletben a gyorsítótárban lévő csempék frissítése) helyett egy jelentést. Ez megakadályozhatja ugrásszerűen az irányítópult betöltésekor. Ez a megoldás nem mindig lehetséges a megadott üzleti követelményeknek, ugyanakkor anélkül, hogy módosítja az adatkészletet CPU telítettséget elkerülése érdekében hatékony módja lehet.

## <a name="conclusion"></a>Összegzés

A Power BI Premium stabilabb teljesítményt, a nagyméretű kötetek támogatása és a egy egységes önkiszolgáló és az enterprise BI platform rugalmasságát biztosítja a szervezet minden tagja számára. A szint 300 műszaki tanulmány kifejezetten a Power BI-rendszergazdák, és a tartalom szerzők és közzétevők került. Segíthet eligazodni a Power BI Premium lehetséges, és azt ismertetik, hogyan megtervezésére, üzembe helyezése, figyelése és hibaelhárítása a méretezhető megoldások célja.

Telepíti és kezeli a Power BI Premium kapacitásaihoz, hogy a rendszergazdák és fejlesztők modell nagyon jó ismerete kell kapacitások funkciót, akkor is lehet felügyelt és figyelésének a menete és hogyan modellek is lehet optimalizálni, annak érdekében, hogy megfelelően válaszolnak teljesítménybeli problémák és a szűk keresztmetszeteket esetleg felmerülő.

## <a name="end-notes"></a>Záró megjegyzések

<a name="endnote-01"></a>\[1\] a műszaki tanulmány a Power BI Premiumot, amely csak a Power BI felhőalapú szolgáltatás által támogatott érintett, és így a Power BI jelentéskészítő kiszolgáló cím nem része az hatókör, kivéve a licenc telepítéséhez szükséges állapotba a Power BI jelentéskészítő kiszolgáló részét képezi néhány A Power BI Premium SKU-k.

<a name="endnote-02"></a>\[2\] power BI egy felhőalapú szolgáltatás, application felhasználók nevében-tartalmak beágyazásához használatakor a Platform--szolgáltatásként (PaaS). Ilyen típusú beágyazással a másik két termék, amelyek egyike a Power BI Premium érhető el.

<a name="endnote-03"></a>\[3\] leküldéses streamelési és a hibrid adatkészletek nem kerülnek be a prémium szintű kapacitások, ezért nem veszi figyelembe telepítése, kezelése és figyelése a prémium szintű kapacitások során.

<a name="endnote-04"></a>\[4\] Excel-munkafüzetek a Power BI-tartalom típusát, nem kerülnek be a prémium szintű kapacitások, és ezért nem üzembe helyezésekor, kezelése és figyelése a prémium szintű kapacitások veszi figyelembe.

<a name="endnote-05"></a>\[5\] Vizualizációk figyelmen kívül hagyja a szeletelők kezelése konfigurálható. További információkért tekintse meg a [Vizualizációk interakciói a Power BI-jelentés](service-reports-visual-interactions.md) dokumentumot.

<a name="endnote-06"></a>\[6\] mérete közötti különbség a Power BI Desktop-fájl mérete az Feladatkezelő memória használata a fájl összehasonlításával lehet meghatározni.

<a name="endnote-07"></a>\[7\] Microsoft-adatforrások támogatása az SQL Server, az Azure Data tégla, az Azure HDInsight Spark (bétaverzió), Azure SQL Database és Azure SQL Data Warehouse tartalmazza. További források kapcsolatos információkért tekintse meg a [Direct Query, a Power BI által támogatott adatforrások](desktop-directquery-data-sources.md) dokumentumot.

<a name="endnote-08"></a>\[8\] a power BI Premium támogatja a legfeljebb egy 10 GB méretű Power BI Desktop (.pbix) fájlt feltölteni. Feltöltése után egy adatkészlet növelhető legfeljebb 12 GB méretű frissítés miatt. SKU maximális feltöltési méretének eltérő. További információkért tekintse meg a [nagy adatkészletek támogatása a Power BI Premium](service-premium-large-datasets.md) dokumentumot.

<a name="endnote-09"></a>\[9\] Termékváltozatait kisebb, mint négy magot nem futtathatók a dedikált infrastruktúra. Ez magában foglalja a EM1, EM2, A1 és a2-es termékváltozatokat.

<a name="endnote-10"></a>\[10\] bár ritka, modellek memóriából szolgáltatási műveletek miatt lehet.

<a name="endnote-11"></a>\[11\] ezek időzítésüket, bármikor módosulhatnak.

<a name="endnote-12"></a>\[12\] ezt nevezik multi-földrajzi, jelenleg előzetes verzióban érhető el. A közösségértékek multi-földrajzi központi telepítés általában van a vállalati vagy kormányzati megfelelőségi, hanem teljesítmény és méretezhetőség. Jelentés és irányítópult betöltésekor továbbra is magában foglalja a kérelmeket a metaadatokat az otthoni régiója. További információkért tekintse meg a [Multi-földrajzi támogatása a Power BI Premium (előzetes verzió)](service-admin-premium-multi-geo.md) dokumentumot.

<a name="endnote-13"></a>\[13\] lehetséges, hogy felhasználók a Power BI szolgáltatásban a feladatok terhelve, túl összetett lekérdezések írásának módját, stb. a körkörös hivatkozások létrehozása teljesítmény problémákat okozhat.

<a name="endnote-14"></a>\[14\] a teljes szervezet munkaterületeinek hozzárendeléséhez a beállítást nem ajánlott, és a egy további, jobban célzott módszer használata ajánlott. Általában a nem éles tartalom személyes munkaterületek használata ajánlott.

<a name="endnote-15"></a>\[15\] lehetséges termékváltozatok figyelheti az alkalmazást vagy az Azure Portalon, de nem található a Power BI felügyeleti Portáljához. Termékváltozatok figyeléséhez, a jelentés meghiúsul, ha az alkalmazás még nem lett hozzáadva az erőforrás az Olvasó szerepkörhöz. További információkért tekintse meg a [figyelő Power BI Premium és a Power BI Embedded-kapacitások](service-admin-premium-monitor-capacity.md) dokumentumot.

<a name="endnote-16"></a>\[16\] frissítések várhat, ha nem, akkor elegendő CPU és memória elindításához.

<a name="endnote-17"></a>\[17\] az adatkészlet méretét, a memória a lemezen, akár 20 %-kal nagyobb lehet.

<a name="endnote-18"></a>\[18\] átlagos memóriahasználat (GB) és a legmagasabb memóriát (GB)

<a name="endnote-19"></a>\[19\] adatkészlet adatbázislap

<a name="endnote-20"></a>\[20\] adatkészlet lekérdezések, az adatkészlet átlagos lekérdezési idő (ms), a adatkészlet várjon száma és az adatkészlet átlagos várakozási idő (ms)

<a name="endnote-21"></a>\[21\] magas CPU-kihasználtság száma és a CPU-idő a legnagyobb kihasználtságú (elmúlt hét napban)

<a name="endnote-22"></a>\[22-es\] DQ/LC magas kihasználtság száma és DQ/LC ideje legnagyobb kihasználtságú (elmúlt hét napban)