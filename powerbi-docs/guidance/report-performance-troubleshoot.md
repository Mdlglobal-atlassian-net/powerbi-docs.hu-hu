---
title: Jelentésteljesítménnyel kapcsolatos problémák elhárítása a Power BI-ban
description: Hibaelhárítási útmutató a lassú jelentések teljesítményének diagnosztizálásához Power BI-ban.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/15/2020
ms.author: v-pemyer
ms.openlocfilehash: a5230a39706ce5d6941c00386160fe10114442e1
ms.sourcegitcommit: 5ece366fceee9832724dae40eacf8755e1d85b04
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81527991"
---
# <a name="troubleshoot-report-performance-in-power-bi"></a>Jelentésteljesítménnyel kapcsolatos problémák elhárítása a Power BI-ban

Az ebben a cikkben olvasható útmutatás alapján a fejlesztők és a rendszergazdák hibaelhárítást végezhetnek a lassú teljesítményű jelentéseken. Az információ a Power BI-jelentésekre és a többoldalas Power BI-jelentésekre vonatkozik.

Lassú jelentések esetén a jelentést készítő felhasználók azt tapasztalják, hogy a jelentés lassan töltődik be vagy lassan frissül, amikor szeletelőket vagy más funkciókat használnak. Ha a jelentések a prémium szintű kapacitáson futnak, a lassú jelentések a [Power BI Premium metrikaalkalmazás](../service-admin-premium-monitor-capacity.md) figyelésével is azonosíthatók. Ez az alkalmazás segít a Power BI Premium-előfizetés állapotának és kapacitásának figyelésében.

## <a name="follow-flowchart-steps"></a>A folyamatábra lépéseinek követése

A következő folyamatábra segítségével megismerheti a lassú teljesítmény okát, és meghatározhatja, hogy milyen műveletet kell végrehajtania.

:::image type="content" source="media/report-performance-troubleshoot/flowchart.png" alt-text="A képen a folyamatábra látható, amely teljes mértékben le van írva a cikk szövegében." border="true":::

A folyamatábrán hat lezáró jel található, amelyek mindegyike egy elvégzendő műveletet jelöl:

|Lezáró jel|Művelet(ek)|
|---------|---------|
|![Folyamatábra 1. lezárója](media/common/icon-01-red-30x30.png)|Kapacitás kezelése<br />Kapacitás méretezése |
|![Folyamatábra 2. lezárója](media/common/icon-02-red-30x30.png)|A kapacitás tevékenységének vizsgálata a jelentések szokásos használata során|
|![Folyamatábra 3. lezárója](media/common/icon-03-red-30x30.png)|Architektúra változása<br />Az Azure Analysis Services használatának lehetősége<br />A helyszíni átjáró ellenőrzése|
|![Folyamatábra 4. lezárója](media/common/icon-04-red-30x30.png)|Az Azure Analysis Services használatának lehetősége<br />A Power BI Premium használatának lehetősége|
|![Folyamatábra 5. lezárója](media/common/icon-05-red-30x30.png)|A Power BI Desktop Teljesítményelemzőjének használata<br />A jelentés, a modell vagy a DAX optimalizálása|
|![Folyamatábra 6. lezárója](media/common/icon-06-red-30x30.png)|Támogatási jegy létrehozása|

## <a name="take-action"></a>Művelet végrehajtása

Először is fontos megtudni, hogy a lassú jelentés prémium kapacitáson van-e üzemeltetve.

### <a name="premium-capacity"></a>Prémium-kapacitás

Ha a jelentés egy prémium szintű kapacitáson fut, akkor a **Power BI Premium metrikaalkalmazásának** használatával állapítsa meg, hogy a jelentéskészítő kapacitása gyakran meghaladja-e a kapacitás erőforrásait. Ha gyakran meghaladja a 80%-ot, akkor a CPU-val kapcsolatos a jelenség. A memória akkor érintett, ha az [aktív memória metrikája](../service-premium-metrics-app.md#the-active-memory-metric) meghaladja a 50-et. Az erőforrásokra nehezedő terhelés esetén érdemes lehet a [kapacitást kezelni vagy skálázni](../service-admin-premium-manage.md) (folyamatábra 1. lezárója). Ha elegendő erőforrás áll rendelkezésre, vizsgálja meg a kapacitás tevékenységeit a jelentés szokásos használata során (folyamatábra 2. lezárója).

### <a name="shared-capacity"></a>Megosztott kapacitás

Ha a jelentés megosztott kapacitáson fut, akkor nem lehetséges a kapacitás állapotát figyelni. Ilyenkor másféle vizsgálati megközelítést kell alkalmazni.

Először ellenőrizze, hogy a lassú teljesítmény a nap vagy a hónap adott időpontjában jelentkezik-e. Ha igen – és sok felhasználó nyitja meg a jelentést ezekben az időpontokban – két lehetőség közül választhat:

- A lekérdezés átviteli sebességének növeléséhez migrálhatja az adatkészletet az [Azure Analysis Servicesbe](/azure/analysis-services/analysis-services-overview) vagy egy prémium szintű kapacitásba (folyamatábra 4. lezárója).
- A Power BI Desktop [Teljesítményelemző](../desktop-performance-analyzer.md) funkciójával kiderítheti, hogy milyen teljesítményt nyújtanak az egyes jelentéselemek, köztük a vizualizációk és a DAX-képletek. Különösen hasznos annak megállapításához, hogy a lekérdezés vagy a vizualizáció renderelése okoz-e teljesítményproblémákat (folyamatábra 5. lezárója).

Ha azt állapítja meg, hogy nincs időminta, a következő lépés annak a megállapítása, hogy a lassú teljesítmény egy adott földrajzi helyhez vagy régióhoz kötődik-e. Ha igen, valószínű, hogy az adatforrás távoli, és lassú a hálózati kommunikáció. Ebben az esetben érdemes lehet a következőkkel próbálkozni:

- Az architektúra módosítása az [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) használatával (folyamatábra 3. lezárója).
- A [helyszíni adatátjáró teljesítményének](/data-integration/gateway/service-gateway-performance) optimalizálása (folyamatábra 3. lezárója).

Végül, ha azt állapítja meg, hogy nincs időminta _és_ lassú teljesítmény mutatkozik minden régióban, vizsgálja meg, hogy a lassú teljesítmény bizonyos eszközökön, ügyfeleken vagy webböngészőkön történik-e. Ha nem, használja a Power BI Desktop [Teljesítményelemzőjét](../desktop-performance-analyzer.md) a korábban leírtak szerint a jelentés vagy a modell optimalizálásához (folyamatábra 5. lezárója).

Ha azt látja, hogy a lassú teljesítmény meghatározott eszközöket, ügyfeleket vagy webböngészőket érint, javasoljuk, hogy hozzon létre egy támogatási jegyet a [Power BI támogatási oldalán](https://powerbi.microsoft.com/support/) (folyamatábra 6. lezárója).

## <a name="next-steps"></a>Következő lépések

Erről a cikkről a következő forrásanyagokban talál további információt:

- [A Power BI útmutatója](index.yml)
- [Jelentések teljesítményének figyelése](monitor-report-performance.md)
- [Teljesítményelemző](../desktop-performance-analyzer.md)
- Tanulmány: [A Power BI Enterprise üzembehelyezési előkészületei](https://go.microsoft.com/fwlink/?linkid=2057861)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
- Javaslatai vannak? [A Power BI javítására vonatkozó ötletek beküldése](https://ideas.powerbi.com/)
