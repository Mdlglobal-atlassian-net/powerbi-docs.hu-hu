---
title: Optimalizálási útmutató a Power BI-hoz
description: Optimalizálási útmutató a Power BI-hoz.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: 0f29b70a42375be945d206672116219b7d5a3b48
ms.sourcegitcommit: 032a77f2367ca937f45e7e751997d7b7d0e89ee2
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609995"
---
# <a name="optimization-guide-for-power-bi"></a>Optimalizálási útmutató a Power BI-hoz

Az ebben a cikkben olvasható útmutatás alapján optimalizált Power BI-megoldásokat készíthetnek és üzemeltethetnek a fejlesztők és a rendszergazdák. Különböző architekturális rétegek szintjén optimalizálhatók a megoldások. A rétegek az alábbiakat foglalják magukban:

- Az adatforrás(ok)
- Az adatmodell
- Vizualizációk, köztük irányítópultok, Power BI-jelentések és többoldalas Power BI-jelentések
- A környezet, beleértve a funkciókat, az adatátjárókat és a hálózatot

## <a name="optimizing-the-data-model"></a>Az adatmodell optimalizálása

Az adatmodellre épül a teljes vizualizációs környezet. Az adatmodellek külső vagy belső üzemeltetésűek lehetnek, és a Power BI-ban _adatkészleteknek_ hívjuk őket. Fontos, hogy megértse a lehetőségeket, és hogy a saját megoldásához illő adatkészlettípust válassza. Három adatkészletmódot különböztetünk meg: Importálás, DirectQuery és Összetett. További információt az [Adatkészletek a Power BI szolgáltatásban](../service-datasets-understand.md) és az [Adatkészletmódok a Power BI szolgáltatásban](../service-dataset-modes-understand.md) című témakörben talál.

Az egyes adatkészletmódokhoz itt talál útmutatást:

- [Adatmennyiség-csökkentési technikák importálási modellek készítéséhez](import-modeling-data-reduction.md)
- [Útmutató a Power BI Desktopbeli DirectQuery-modellekhez](directquery-model-guidance.md)
- [Útmutató a Power BI Desktopbeli Összetett modellekhez](composite-model-guidance.md)

## <a name="optimizing-visualizations"></a>Vizualizációk optimalizálása

A Power BI vizualizációi lehetnek irányítópultok, Power BI-jelentések vagy többoldalas Power BI-jelentések. Mindegyiknek más és más az architektúrája, ezért mindegyikhez külön útmutatót készítettünk. 

### <a name="dashboards"></a>Irányítópultok

Fontos tudni, hogy a Power BI gyorsítótárazza az irányítópult-csempéket, kivéve az élő jelentéscsempéket és a streamelési csempéket. További információt az Adatfrissítés a Power BI-ban című témakör [Csempék frissítése](../refresh-data.md#tile-refresh) című szakasza tartalmaz. Ha dinamikus [sorszintű biztonságot (RLS)](../service-admin-rls.md) követel meg az adatkészlet, mindenképpen tisztában kell lennie a teljesítményre gyakorolt hatásokkal, mert a csempék gyorsítótárazása felhasználónként fog történni.

Amikor élő jelentéscsempéket tűz ki valamelyik irányítópultra, akkor nem a lekérdezési gyorsítótárból történik a kiszolgálásuk. Ehelyett jelentésekként viselkednek, és menet közben küldenek lekérdezéseket a háttérbeli magoknak.

Ahogy azt a neve alapján sejtheti, az adatok gyorsítótárból történő beolvasása jobb és egységesebb teljesítményt nyújt, mintha közvetlenül az adatforrásra támaszkodna. E funkcionalitás kihasználásának egyik módja, ha az irányítópultokat kezdőlapként állítja be a felhasználók számára. A gyakran használt és sokak által igényelt vizualizációkat rögzítse az irányítópultokra. Ily módon az irányítópultok értékes „első védelmi vonalként” működnek, amely egységes teljesítményt biztosít, kevésbé csökkentve a kapacitást. A részletek elemzése céljából a felhasználók továbbra is átkattinthatnak bármely jelentésre.

A DirectQuery módú és az élő kapcsolatot használó adatkészletek esetén a gyorsítótár rendszeres időközönként frissül az adatforrás lekérdezésével. A frissítés alapértelmezés szerint óránként történik, de ettől eltérő gyakoriságot is beállíthat az adatkészlet-beállítások között. A gyorsítótár minden egyes frissítése lekérdezéseket küld az alapul szolgáló adatforrásnak, hogy az frissítse a gyorsítótárt. A generált lekérdezések számát az határozza meg, hogy hány olyan vizualizáció van az irányítópultokon rögzítve, amely az adott adatforrásra támaszkodik. Tartsa szem előtt, hogy ha engedélyezve van a sorszintű biztonság, a rendszer minden egyes biztonsági környezethez külön lekérdezéseket generál. Tegyük fel például, hogy két különböző szerepkör kategorizálja a felhasználókat, és két különböző nézetben jelenítik meg az adatokat. A Power BI két lekérdezéskészletet hoz létre a lekérdezési gyorsítótár frissítése közben.

### <a name="power-bi-reports"></a>Power BI-jelentések

Több javaslat is született a Power BI-jelentéstervek optimalizálására.

> [!NOTE]
> Ha DirectQuery típusú adatkészleten alapulnak a jelentések, akkor az Útmutató a DirectQuery-modellhez a Power BI Desktopban című témakör [Jelentéstervek optimalizálása](directquery-model-guidance.md#optimize-report-designs) című szakaszában talál további jelentésterv-optimalizálási tudnivalókat.

#### <a name="apply-the-most-restrictive-filters"></a>A legszigorúbb szűrők alkalmazása

Minél több adatot jelenítenek meg a vizualizációk, annál lassabban töltődnek be. Még ha ez nyilvánvalónak is tűnik, könnyű megfeledkezni róla. Tegyük fel például, hogy nagy méretű adatkészleten dolgozik, amelynek alapján készít egy táblát tartalmazó jelentést. A végfelhasználók szeletelőkkel szűrnek rá a kívánt sorokra a lapon, és jellemzően csak néhány tucatnyi sor érdekli őket.

Gyakori hiba ilyen esetben, hogy a tábla alapértelmezett nézete szűretlen marad, vagyis az összes (akár több mint százmillió) sort tartalmazza. A rendszer ezeknek a soroknak az adatait minden egyes frissítéskor betölti a memóriába, majd kitömöríti. Ez a feldolgozási folyamat óriási memóriahasználattal jár. A megoldás az, hogy a Top N szűrőt használva csökkenteni kell a táblában maximálisan megjeleníthető elemek számát. A maximális elemszám lehet a felhasználók által jellemzően igényelt sorszámnál magasabb is, például 10 000. Ennek eredményeként a végfelhasználói élmény nem változik, a memóriahasználat azonban jelentősen csökken. A legfontosabb pedig az, hogy javul a teljesítmény.

A jelentésben található összes vizualizációhoz ajánlott az előzőekhez hasonló tervezési megközelítést használni. Mindig tegye fel a kérdést: Minden adatra szükség van ebből a vizualizációból? Szűrhető a megjelenített adatmennyiség úgy, hogy az csak minimálisan befolyásolja a végfelhasználói élményt? Ne feledje, hogy a táblák különösen teljesítményigényesek lehetnek.

#### <a name="limit-visuals-on-report-pages"></a>A jelentéslapokon megjelenő vizualizációk számának korlátozása

A fenti elv a jelentéslapokon elhelyezett vizualizációk számára nézve is ugyanúgy igaz. Kifejezetten javasolt, hogy az egyes jelentéslapokon csak annyi vizualizációt jelenítsen meg, amennyi valóban szükséges. A [részletező lapok](report-drillthrough.md) és a [jelentéslapok elemleírásai](report-page-tooltips.md) nagyszerű megoldást kínálnak arra, hogy további részleteket jeleníthessen meg anélkül, hogy még több vizualizációt zsúfolna a lapra.

#### <a name="evaluate-custom-visual-performance"></a>Egyéni vizualizációk teljesítményének kiértékelése

Tesztelje az összes egyéni vizualizációt annak megállapításához, hogy biztosan megfelelő teljesítményt nyújtanak-e. A rosszul optimalizált egyéni vizualizációk a teljes jelentés teljesítményére negatív hatással lehetnek.

### <a name="power-bi-paginated-reports"></a>Többoldalas Power BI-jelentések

A többoldalas Power BI-jelentések terveinek optimalizálásához felhasználhatja az ajánlott eljárások szerint készült tervet a jelentés adatlekérési fázisához. További információt az [Adatlekérési útmutató többoldalas jelentésekhez](report-paginated-data-retrieval.md) című témakörben talál.

Győződjön meg arról is, hogy elegendő memóriát foglalt le a [többoldalas jelentések számítási feladataihoz](../service-admin-premium-workloads.md#paginated-reports).

## <a name="optimizing-the-environment"></a>A környezet optimalizálása

A kapacitásbeállítások konfigurálásával, az adatátjárók méretezésével és a hálózati késés csökkentésével optimalizálhatja a Power BI-környezetet.

### <a name="capacity-settings"></a>Kapacitásbeállítások

Ha dedikált kapacitásokat használ (a Power BI Premium szolgáltatás P jelű termékváltozataival vagy a Power BI Embedded szolgáltatás A jelű (A4–A6) termékváltozataival), kezelheti a kapacitásbeállításokat. További információ: [Prémium szintű kapacitások kezelése](../service-premium-capacity-manage.md). A kapacitás optimalizálásához a [Prémiumszintű kapacitások optimalizálása](../service-premium-capacity-optimize.md) című témakörben talál útmutatást.

### <a name="gateway-sizing"></a>Átjárók méretezése

Átjáróra akkor van szükség, amikor az interneten közvetlenül nem elérhető adatokhoz kell hozzáférnie a Power BI-nak. A [helyszíni adatátjárót](../service-gateway-onprem.md) helyszíni kiszolgálón és virtuális gépen üzemelő IaaS-környezetekben egyaránt telepítheti.

Ha tisztában szeretne lenni az átjárók számítási feladataival és a méretezési javaslatokkal, olvassa el a [Helyszíni adatátjáró méretezése](gateway-onprem-sizing.md) című témakört.

### <a name="network-latency"></a>Hálózati késés

A hálózati késés hatással van a jelentések teljesítményére, hiszen megnöveli azt az időt, amely a kérések Power BI szolgáltatásba való eljuttatásához, illetve a válaszok kézbesítéséhez szükséges. A Power BI-bérlők konkrét régióhoz vannak társítva.

> [!TIP]
> A [Hol található a Power BI-bérlőm?](../service-admin-where-is-my-tenant-located.md) című témakörből megtudhatja, hogy hol üzemel a bérlője.

Amikor egy bérlő felhasználói hozzáférnek a Power BI szolgáltatáshoz, a kéréseiket a rendszer mindig ehhez a régióhoz irányítja. A kérések Power BI szolgáltatásba érkezésekor a szolgáltatás további kéréseket küldhet (például az alapul szolgáló adatforrásnak vagy egy adatátjárónak), amelyekre szintén érvényes a hálózati késés.

Bizonyos eszközök, például az [Azure Speed Test](https://azurespeedtest.azurewebsites.net/), segíthetnek megállapítani, hogy mekkora a hálózati késés az ügyfél és az Azure-régió között. A hálózati késés hatásának minimalizálásához általánosságban igyekezzen minél közelebb tartani egymáshoz az adatforrásokat, az átjárókat és a Power BI-fürtöt. Lehetőség szerint legyenek ugyanabban a régióban. Ha problémát okoz a hálózati késés, próbálja meg közelebb helyezni a Power BI-fürthöz az átjárókat és az adatforrásokat azzal, hogy felhőbeli virtuális gépeken helyezi el őket.

## <a name="monitoring-performance"></a>Teljesítményfigyelés

A teljesítmény figyelésével azonosíthatja a szűk keresztmetszeteket. A folytatólagos optimalizálás során kiemelt figyelmet igényelnek a lassú lekérdezések (vagy a jelentésekben szereplő vizualizációk). A figyelés történhet a Power BI Desktopban tervezéskor, vagy a Power BI Premium kapacitásaiban végzett éles számítási feladatok közben. További információt a [Jelentések teljesítményének figyelése a Power BI-ban](monitor-report-performance.md) című témakör tartalmaz.

## <a name="next-steps"></a>Következő lépések

Erről a cikkről a következő forrásanyagokban talál további információt:

- [A Power BI útmutatója](index.yml)
- [Jelentések teljesítményének figyelése](monitor-report-performance.md)
- Tanulmány: [A Power BI Enterprise üzembehelyezési előkészületei](https://go.microsoft.com/fwlink/?linkid=2057861)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
- Javaslatai vannak? [A Power BI javítására vonatkozó ötletek beküldése](https://ideas.powerbi.com/)
