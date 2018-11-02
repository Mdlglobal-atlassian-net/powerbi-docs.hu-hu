---
title: A Power BI Premium kapacitásának figyelése a cégnél
description: A Power BI felügyeleti portál és a Power BI Premium kapacitás-metrikák alkalmazás használata
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 10/09/2018
LocalizationGroup: Premium
ms.openlocfilehash: b2627950ea51239acb19972fde3244f3bd158255
ms.sourcegitcommit: 52ac456bf2ac025b22ea634c28482f22e1cc19ac
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/10/2018
ms.locfileid: "48909222"
---
# <a name="monitor-power-bi-premium-and-power-bi-embedded-capacities"></a>A Power BI Premium- és a Power BI Embedded-kapacitások monitorozása

A cikk azt tekinti át, hogyan monitorozhatóak a Power BI Premium kapacitásmetrikái. A kapacitás felhasználásának figyelemmel kísérése segít abban, hogy megalapozott döntéseket hozhasson a kapacitáskezelést illetően.

A kapacitás monitorozható a Power BI Premium Metrics alkalmazással vagy a felügyeleti portálon is. Az alkalmazás használatát javasoljuk, mert az jelentősen több információt nyújt, de a jelen cikkben mindkét monitorozási lehetőséget megvizsgáljuk.

<iframe width="560" height="315" src="https://www.youtube.com/embed/UgsjMbhi_Bk?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="install-the-premium-capacity-metrics-app"></a>A Premium Capacity Metrics alkalmazás telepítése

A [Premium Capacity Metrics alkalmazást](https://app.powerbi.com/groups/me/getapps/services/capacitymetrics) közvetlenül is megnyithatja, de ha szeretné, ugyanúgy telepítheti is, mint bármely más alkalmazást a Power BI-ban.

1. A Power BI-ban kattintson az **Alkalmazások** elemre.

    ![Ugrás az alkalmazásokra](media/service-admin-premium-monitor-capacity/apps.png)

2. A jobb oldalon kattintson az **Alkalmazások beszerzése** lehetőségre.

3. Az **Alkalmazások** kategóriában keresse meg a **Power BI Premium Capacity Metrics alkalmazást**.

4. Az alkalmazás telepítéséhez regisztrálnia kell.

Az alkalmazás telepítése után már megtekintheti a cég kapacitásainak információit. Most vizsgáljuk meg a legfontosabb elérhető metrikákat.

## <a name="use-the-metrics-app"></a>A metrika alkalmazás használata

Az alkalmazás a megnyitás után egy irányítópultot jelenít meg, amelyen egy összefoglaló áttekintés látható minden olyan kapacitásról, amelyhez Önnek adminisztrátori jogosultsága van.

![A Metrics alkalmazás irányítópultja](media/service-admin-premium-monitor-capacity/app-dashboard.png)

A jelentés három lapot tartalmaz, amelyeknek részletesebb leírását az alábbi szakaszokban találja.

* **Összes oldalra alkalmazott szűrők**: lehetővé teszi egy adott kapacitás szűrését a jelentés többi oldalán.
* **Adatkészletek**: részletes mérőszámokat biztosít a kapacitások adathalmazainak állapotáról.
* **Rendszer**: általános kapacitási mérőszámokat biztosít, például a memória és a processzor magas kihasználtságával kapcsolatban. 

### <a name="filters-applied-to-all-pages-tab"></a>Összes oldalra alkalmazott szűrők lap

Az **Összes oldalra alkalmazott szűrők** lap lehetővé teszi, hogy kiválasszon egy kapacitást, egy adathalmazt és egy dátumtartományt az elmúlt hét napból. A szűrők ezután alkalmazva lesznek a jelentés vonatkozó oldalaira és csempéire. Ha nincsenek kiválasztva szűrők, a jelentés alapértelmezés szerint a kapacitások múlt heti mérőszámait jeleníti meg.

![Szűrők lap](media/service-admin-premium-monitor-capacity/filters-tab.png)

### <a name="datasets-tab"></a>Adatkészletek lap

Az **Adatkészletek** lap biztosítja a legtöbb mérőszámot az alkalmazásban. Használja a lap tetején található négy gombot a különböző területek közötti váltáshoz: **Összefoglalás**, **Frissítések**, **Lekérdezések** és **Adatkészletek**.

![Adatkészletek lap](media/service-admin-premium-monitor-capacity/datasets-tab.png)

#### <a name="summary-area"></a>Összefoglalás terület

![Összefoglalás gomb](media/service-admin-premium-monitor-capacity/summary-button.png)

Az **Összefoglalás** terület entitások, rendszererőforrások és adathalmazhoz tartozó számítási feladatok alapján jeleníti meg a kapacitásokat.

| | **Metrikák** |
| --- | --- |
| **Entitások** | * Az Önhöz tartozó kapacitások száma<br> * A kapacitásában meglévő különálló adatkészletek száma<br> * A kapacitásában meglévő különálló munkaterületek száma |
| **Rendszer** | * Az átlagos memóriahasználat GB-ban az elmúlt hét napban<br> * A legmagasabb memóriahasználat GB-ban az elmúlt hét napban, az események helyi idejével<br> * Az a szám, ahányszor a CPU-használat meghaladta a küszöbérték 80%-át a legutóbbi hét napban, három perces gyűjtőkbe csoportosítva<br> * A legtöbb eset, amikor a CPU-használat meghaladta a 80%-ot a legutóbbi hét napban, egyórás gyűjtőkbe elosztva, és az esemény helyi idejével<br> * Az a szám, ahányszor a Közvetlen lekérdezés/Élő kapcsolat értéke meghaladta a küszöbérték 80%-át a legutóbbi hét napban, három perces gyűjtőkbe csoportosítva<br> * A legtöbb eset, amikor a Közvetlen lekérdezés/Élő kapcsolat értéke meghaladta a 80%-ot a legutóbbi hét napban, egyórás gyűjtőkbe elosztva, és az esemény helyi idejével |
| **Adatkészlethez tartozó számítási feladatok** | * A frissítések teljes száma a legutóbbi hét napban<br> * A sikeres frissítések teljes száma a legutóbbi hét napban<br> * A sikertelen frissítések teljes száma a legutóbbi hét napban<br> * A nem elegendő mennyiségű memória miatt sikertelen frissítések teljes száma<br> * A frissítések átlagos időtartama percekben kifejezve és a művelethez szükséges teljes idő<br> * Az átlagos frissítési idő percekben kifejezve, valamint a beütemezett időpont és a művelet kezdete közötti átlagos késés<br> * A lekérdezések teljes száma a legutóbbi hét napban<br> * A sikeres lekérdezések teljes száma a legutóbbi hét napban<br> * A sikertelen lekérdezések teljes száma a legutóbbi hét napban<br> * A lekérdezések átlagos időtartama percekben kifejezve és a művelethez szükséges teljes idő<br> * A memóriaterhelés miatt kizárt modellek teljes száma |
|  |  |

#### <a name="refreshes-area"></a>Frissítések terület

![Frissítések gomb](media/service-admin-premium-monitor-capacity/refreshes-button.png)

A **Frissítések** terület adathalmazokra lebontva megjeleníti a frissítéseket, a sikeres műveleteket, a frissítések átlagos/maximális várakozási idejét és a frissítések átlagos/maximális időtartamát, az elmúlt hét napra vonatkozóan. Az utolsó két diagram a frissítéseket és a GB-ban kifejezett memóriafogyasztást hasonlítja össze, valamint az átlagos várakozási időt egyórás gyűjtőkbe csoportosítva, helyi időben kifejezve. A felső sávdiagramok az első öt adathalmazt mutatják aszerint, hogy mennyi időt vett igénybe az adathalmaz frissítése (a frissítés időtartama), és mennyi volt a frissítések átlagos várakozási ideje. Ha több magas frissítési várakozási érték is van, az azt jelzi, hogy a kapacitáshasználat a csúcsértékhez közelít.

#### <a name="queries-area"></a>Lekérdezések terület

![Lekérdezések gomb](media/service-admin-premium-monitor-capacity/queries-button.png)

A **Lekérdezések** terület adathalmazokra, munkaterületekre és egyórás gyűjtőkre lebontva megjeleníti a lekérdezések teljes számát, a lekérdezésre való várakozások számát az élő/közvetlen lekérdezéseknél, az átlagos/maximális időtartamot és az ezredmásodpercben kifejezett átlagos/maximális jelentett várakozási időt, az elmúlt hét napra vonatkozóan. Az alsó diagramok a lekérdezések számát, az átlagos időtartamot (ezredmásodpercben) és az átlagos várakozási időt (ezredmásodpercben) hasonlítják össze a GB-ban kifejezett memóriafogyasztással, egyórás gyűjtőkre bontva, helyi időben kifejezve. A két felső diagram az első öt adathalmazt mutatja aszerint, hogy mennyi volt a lekérdezések átlagos időtartama, és mennyi várakozási időre volt szükség a lekérdezések végrehajtásához. A hosszú lekérdezési időtartamok és a hosszú várakozási idők azt jelzik, hogy a kapacitáshasználat a csúcsértékhez közelít. Azt is jelenthetik, hogy az egyik adathalmaz problémákat okoz, és további vizsgálat szükséges.

#### <a name="datasets-area"></a>Adatkészletek terület

![Adatkészletek gomb](media/service-admin-premium-monitor-capacity/datasets-button.png)

Az **Adatkészletek** terület a memóriaterhelés miatt kizárt adathalmazok teljes számát mutatja, óránkénti lebontásban.

### <a name="system-tab"></a>Rendszer lap

A **Rendszer** lap megjeleníti, hogy mikor volt magas a processzorhasználat (hányszor haladta meg a 80%-os kihasználtságot), a közvetlen lekérdezés/élő kapcsolat kihasználtsága és a memóriahasználat.

![Premium szint rendszerjelentése](media/service-admin-premium-monitor-capacity/system-tab.png)

## <a name="monitor-power-bi-embedded-capacity"></a>A Power BI Embedded-kapacitás monitorozása

A Power BI Premium Capacity Metrics alkalmazással *A SKU*-kapacitásokat is monitorozhat a Power BI Embedded szolgáltatásban. Ha Ön az adott kapacitás adminisztrátora, akkor a kapacitás megjelenik a jelentésben is. A jelentést azonban csak akkor lehet frissíteni, ha a Power BI-nak megad bizonyos engedélyeket az A SKU-kra vonatkozóan:

1. Nyissa meg a kapacitást az Azure Portalon.
1. Kattintson a **Hozzáférés-vezérlés (IAM)** lehetőségre, és adja hozzá a „Power BI Premium” alkalmazást az Olvasó szerepkörhöz. Ha az alkalmazást nem találja név szerint, az ügyfél-azonosító használatával is hozzáadhatja azt: cb4dc29f-0bf4-402a-8b30-7511498ed654.

    ![Engedélyek a Power BI Embeddedhez](media/service-admin-premium-monitor-capacity/embedded-permissions.png)

> [!NOTE]
> Power BI Embedded kapacitás használatát monitorozhatja az alkalmazással vagy az Azure Portalon, a Power BI felügyeleti portálján azonban nincs erre lehetőség.

## <a name="basic-monitoring-in-the-admin-portal"></a>Alapszintű monitorozás a felügyeleti portálon

A felügyeleti portál **Kapacitásbeállítások** területén négy kijelző van, amelyeken a kapacitás által felhasznált terhelés és erőforrás-fogyasztás látható a legutóbbi hét napra vonatkozóan. A négy csempe egyórás időszakokkal működik, és megmutatja, hány óráig volt a vonatkozó metrika a legutóbbi hét nap során 80% fölötti értéken. Ez a metrika azt jelzi, hogy a végfelhasználói élmény minősége csökkenhet.

![7 napot használat](media/service-admin-premium-monitor-capacity/usage-in-days.png)

| **Metrika** | **Leírás** |
| --- | --- |
| Processzor |Ahányszor a processzorhasználat túllépte a 80%-ot. |
| Memóriaakadozás |A háttérrendszerbeli magok memóriaterhelését mutatja. Ez egészen pontosan azt jelzi, hogy az adathalmazok hányszor lettek kiürítve a memóriából a több adathalmaz használata miatti memóriaterhelés következtében. |
| Memóriahasználat |Átlagos memóriahasználat, gigabájtban (GB) kifejezve. |
| DQ/másodperc | Ahányszor a Direct Query-kapcsolatok és élő kapcsolatok száma meghaladta a korlát 80%-át. <br> * A DirectQuery és élő kapcsolatos lekérdezések másodpercenkénti maximális száma korlátozott.* A korlátok a következők: 30/s P1-nél, 60/s P2-nél és 120/s P3 esetén. * A Direct Query és az élő kapcsolatos lekérdezések száma összeadódik. Ha például 15 DirectQueryvel és 15 élő kapcsolattal rendelkezik egy adott másodpercben, elérte a korlátot<br>* Ez mind a helyszíni, mind a felhőkapcsolatokra vonatkozik. |
|  |  |

A metrikák az elmúlt hét használati adatait tükrözik.  Ha szeretne részletesebb nézetet látni a metrikákról, kattintson az összesítő csempék egyikére.  Ez megnyitja a prémium szintű kapacitása metrikáinak részletes diagramjait tartalmazó lapot. Az alábbi ábrán a CPU-metrika részletei láthatóak.

![Részletes használati diagram – Processzor](media/service-admin-premium-monitor-capacity/premium-usage-detailed-chart-cpu.png)

Ezeket a diagramokat a rendszer óránként összegzi az elmúlt hétre vonatkozóan, és segítenek megállapítani, hogy mikor történhetett teljesítménnyel kapcsolatos esemény a prémium szintű kapacitásában.

Exportálhatja bármelyik metrika mögöttes adatait egy CSV-fájlba.  Ezzel a művelettel részletes adatokat kaphat három perces időközökkel az elmúlt hét minden egyes napjára vonatkozóan.

## <a name="next-steps"></a>Következő lépések

Most, hogy megismerkedett a Power BI Premium kapacitásainak monitorozásával, tudjon meg többet a kapacitás optimalizálásáról is.

> [!div class="nextstepaction"]
> [A Power BI Premium-kapacitás erőforrás-kezelése és optimalizálása](service-premium-understand-how-it-works.md)
