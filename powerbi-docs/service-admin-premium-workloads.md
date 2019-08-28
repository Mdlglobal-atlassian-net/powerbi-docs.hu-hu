---
title: Számítási feladatok konfigurálása a Power BI Premiumban
description: Megtudhatja, hogyan konfigurálhat számítási feladatokat a Power BI Premiumban.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 08/21/2019
LocalizationGroup: Premium
ms.openlocfilehash: 2d2eb51c5aad44572f1b427248fd85ef19a6306f
ms.sourcegitcommit: e62889690073626d92cc73ff5ae26c71011e012e
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/23/2019
ms.locfileid: "69985696"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Számítási feladatok konfigurálása egy Premium-kapacitásban

Ez a cikk azt ismerteti, hogy hogyan engedélyezhet és konfigurálhat számítási feladatokat Power BI Premium-kapacitásokban. A kapacitások alapértelmezés szerint csak a Power BI-lekérdezésekkel társított számítási feladatot támogatják. További számítási feladatokat engedélyezhet és konfigurálhat **[mesterséges intelligenciához (Cognitive Services)](service-cognitive-services.md)** , **[adatfolyamokhoz](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)** és **[lapszámozott jelentésekhez](paginated-reports-save-to-power-bi-service.md)** .

## <a name="default-memory-settings"></a>Alapértelmezett memóriabeállítások

A lekérdezési számítási feladatok a Premium-kapacitás SKU-ja által meghatározott erőforrásokhoz vannak optimalizálva, valamint ez szabja meg azok korlátait. A Premium-kapacitások emellett kapacitás-erőforrások használatára képes, további számítási feladatokat is támogatnak. A számítási feladatok alapértelmezett memóriaértékei az SKU-ban elérhető kapacitás-csomópontokon alapulnak. A maximum memóriabeállítások nem halmozottak. A megadott maximum értékig terjedő memória mesterséges intelligenciához és adatfolyamokhoz dinamikusan, lapszámozott jelentésekhez viszont statikusan van lefoglalva.

### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>Microsoft Office SKU-k szoftverszolgáltatásokhoz (SaaS)

|                     | EM2                      | EM3                       | P1                      | P2                       | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|--------------------------|
| Mesterséges intelligencia | N.A. | N.A. | Alapértelmezés szerint 20%; minimum 20% | Alapértelmezés szerint 20%; minimum 10% | Alapértelmezés szerint 20%; minimum 5% |
| Adatfolyamok | N.A. |Alapértelmezés szerint 20%; minimum 12%  | Alapértelmezés szerint 20%; minimum 5%  | Alapértelmezés szerint 20%; minimum 3% | Alapértelmezés szerint 20%; minimum 2%  |
| Oldalakra osztott jelentések | N.A. |N.A. | Alapértelmezés szerint 20%; minimum 10% | Alapértelmezés szerint 20%; minimum 5% | Alapértelmezés szerint 20%; minimum 2,5% |
| | | | | | |

### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>Microsoft Office SKU-k platformszolgáltatásokhoz (PaaS)

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| Mesterséges intelligencia | N.A.                      | Alapértelmezés szerint 20%; minimum 100%                     | Alapértelmezés szerint 20%; minimum 50%                     | Alapértelmezés szerint 20%; minimum 20% | Alapértelmezés szerint 20%; minimum 10% | Alapértelmezés szerint 20%; minimum 5% |
| Adatfolyamok         | Alapértelmezés szerint 40%; minimum 40% | Alapértelmezés szerint 24%; minimum 24% | Alapértelmezés szerint 20%; minimum 12% | Alapértelmezés szerint 20%; minimum 5%  | Alapértelmezés szerint 20%; minimum 3% | Alapértelmezés szerint 20%; minimum 2%   |
| Oldalakra osztott jelentések | N.A.                      | N.A.                      | N.A.                     | Alapértelmezés szerint 20%; minimum 10% | Alapértelmezés szerint 20%; minimum 5% | Alapértelmezés szerint 20%; minimum 2,5% |
| | | | | | |

## <a name="workload-settings"></a>Számítási feladat beállításai

### <a name="ai-preview"></a>AI (előzetes verzió)

Az AI számítási feladataival kognitív szolgáltatásokat és automatizált gépi tanulást vehet igénybe a Power BI-ban. A számítási feladatok viselkedésének vezérléséhez használja a következő beállításokat.

| Beállítás neve | Leírás |
|---------------------------------|----------------------------------------|
| **Maximális memória (%)** | Az AI által a kapacitásban felhasználható, rendelkezésre álló memória maximális százalékos aránya. |
| **Power BI Desktopból történő használat engedélyezése** | Ez a beállítás jövőbeli használatra van fenntartva, és nem jelenik meg minden bérlőben. |
| **Gépi tanulási modellek fejlesztésének engedélyezése** | Meghatározza, hogy az üzleti elemzők betaníthatnak, érvényesíthetnek, és meghívhatnak-e gépi tanulási modelleket közvetlenül a Power BI-ban. További információ: [Automatizált gépi tanulás a Power BI-ban (előzetes verzió)](service-machine-learning-automated.md). |
| **AI-kérelmek párhuzamosságának engedélyezése** | Meghatározza, hogy az AI-kérelmek párhuzamosan futtathatók-e. |
|  |  |

### <a name="datasets"></a>Adathalmazok

Az adathalmazok számítási feladat alapértelmezés szerint engedélyezve van, és nem tiltható le. A számítási feladatok viselkedésének vezérléséhez használja a következő beállításokat.

| Beállítás neve | Leírás |
|---------------------------------|----------------------------------------|
| **Maximális memória (%)** | Az adatkészletek által a kapacitásban felhasználható, rendelkezésre álló memória maximális százalékos aránya. |
| **XMLA-végpont** | Megadja, hogy a csatlakozó ügyfélalkalmazások figyelembe vegyék a munkaterület és az alkalmazás szintjén meghatározott biztonságicsoport-tagságot. További információ: [Csatlakozás adathalmazokhoz ügyfélalkalmazásokkal és -eszközökkel](service-premium-connect-tools.md). |
| **Köztes sorok maximális száma** | A DirectQuery által visszaadott köztes sorok maximális száma. Az alapértelmezett érték 1 000 000, a megengedett tartomány pedig 100 000-től 2 147 483 647-ig terjed. A beállítással szabályozhatja az erőforrás-igényes vagy rosszul megtervezett jelentések hatásait. |
| **Offline adathalmaz maximális mérete (GB)** | A memóriában lévő offline adathalmaz maximális mérete. Ez a tömörített méret a lemezen. Az alapértelmezett értéket a termékváltozat szabja meg, a megengedett tartomány pedig 0,1 GB-tól 10 GB-ig terjed. A beállítással megakadályozhatja, hogy a jelentéskészítők a kapacitást hátrányosan érintő, nagyméretű adathalmazt tegyenek közzé. |
| **Eredménysorok maximális száma** | A DAX-lekérdezés által visszaadott sorok maximális száma. Az alapértelmezett érték -1 (nincs korlát), a megengedett tartomány pedig 100 000-től 2 147 483 647-ig terjed. A beállítással szabályozhatja az erőforrás-igényes vagy rosszul megtervezett jelentések hatásait. |
| **Lekérdezés memóriakorlátja (%)** | Egy lekérdezésben vagy DAX-mértékben ideiglenes eredményekhez a kapacitásban felhasználható, rendelkezésre álló memória maximális százalékos aránya. A beállítással szabályozhatja az erőforrás-igényes vagy rosszul megtervezett jelentések hatásait. |
| **Lekérdezés időkorlátja (másodpercben)** | A lekérdezés időtúllépéséig eltelt idő maximuma. Az alapértelmezett érték 3600 másodperc (1 óra). A 0 érték azt jelenti, hogy a lekérdezések lépik túl az időt. A beállítással jobban szabályozhatja a hosszan futó lekérdezéseket. |
|  |  |  |

### <a name="dataflows"></a>Adatfolyamok

Az adatfolyamok számítási feladattal az adatfolyamok önkiszolgáló adat-előkészítési funkciójával tölthet be, alakíthat át, integrálhat és bővíthet adatokat. A számítási feladatok viselkedésének vezérléséhez használja a következő beállításokat.

| Beállítás neve | Leírás |
|---------------------------------|----------------------------------------|
| **Maximális memória (%)** | Az adatfolyamok által a kapacitásban felhasználható, rendelkezésre álló memória maximális százalékos aránya. |
| **Enhanced Dataflows Compute Engine (Előzetes verzió)** | Ezzel a beállítással akár 20-szor gyorsabban számíthat ki számított entitásokat nagy méretű adatmennyiségek használatakor. **Az új motor aktiválásához újra kell indítania a kapacitást.** További információ: [Enhanced Dataflows Compute Engine](#enhanced-dataflows-compute-engine). |
| **Tároló mérete** | Az adatfolyamok által az entitásokhoz használt tároló maximális mérete. Az alapértelmezett érték 700 MB. További információ: [Tároló mérete](#container-size). |
|  |  |

#### <a name="enhanced-dataflows-compute-engine"></a>Enhanced Dataflows Compute Engine

Az új számítási motor kihasználásához ossza külön adatfolyamokra az adatok betöltését, az átalakítási logikát pedig eltérő adatfolyamok számított entitásaiban helyezze el. Ezt azért célszerű megtennie, mert a számítási motor olyan adatfolyamokon működik, amelyek egy meglévő adatfolyamra hivatkoznak. Betöltési adatfolyamokon nem működik. Az útmutató követésével meggyőződhet arról, hogy az új számítási motor az optimális teljesítmény érdekében kezeli az átalakítási lépéseket, például az összekapcsolásokat és az egyesítéseket.

#### <a name="container-size"></a>Tároló mérete

Adatfolyam frissítésekor az Adatfolyam számítási feladat az adatfolyam minden entitásához létrehoz egy tárolót. Minden tároló legfeljebb a **Tárolóméret beállításban megadott mennyiségű memóriát foglalhat el. Az alapértelmezett érték minden termékváltozathoz 700 MB. Ezt a beállítást a következő esetekben lehet érdemes módosítani:

- Az adatfolyamok frissítése túl sokáig tart, vagy időtúllépés miatt meghiúsul.
- Az adatfolyam-entitások között számítási lépések, például összekapcsolás is szerepel.  

Az Adatfolyam számítási feladat teljesítményének elemzéséhez javasolt a [Power BI Premium-kapacitásmetrikák](service-admin-premium-monitor-capacity.md) alkalmazás használata.

Bizonyos esetekben a tárolóméret növelése nem feltétlenül javítja a teljesítményt. Ha az adatfolyam például csak egy jelentős számításokat végző forrásból nyer adatokat, a tárolóméret módosítása valószínűleg nem használ. A tárolóméret növelése akkor lehet előnyös, ha lehetővé teszi, hogy az Adatfolyam számítási feladat több memóriát foglaljon le az entitásfrissítési műveletekhez. Több memória lefoglalásával csökkenthető a sok számítást igénylő entitások frissítésének ideje.

A Tárolóméret érték nem haladhatja meg az Adatfolyam számítási feladat maximális memóriáját. Egy P1 kapacitás például 25 GB memóriával rendelkezik. Ha az Adatfolyam számítási feladat Maximális memória (%) beállítása 20%, a Tárolóméret (MB) nem haladhatja meg az 5000 értéket. A Tárolóméret még ennél magasabb érték beállításakor sem haladhatja meg a maximális memóriát.

### <a name="paginated-reports"></a>Oldalakra osztott jelentések

A lapszámozott jelentések számítási feladattal az SQL Server Reporting Services formátumán alapuló lapszámozott jelentéseket futtathat a Power BI szolgáltatásban. A számítási feladatok viselkedésének vezérléséhez használja a következő beállítást.

| Beállítás neve | Leírás |
|---------------------------------|----------------------------------------|
| **Maximális memória (%)** | A lapszámozott jelentések által a kapacitásban felhasználható, rendelkezésre álló memória maximális százalékos aránya. |
|  |  |

A többoldalas jelentések egyéni kód futtatását teszik lehetővé egy jelentés renderelésekor. Ilyen például a szövegszín dinamikus megváltoztatása a tartalom alapján, ez pedig további memóriát igényelhet. A lapszámozott jelentéseket a Power BI Premium a kapacitás egy korlátozott területén belül futtatja. Attól függetlenül, hogy a számítási feladat *aktív vagy nem*, a megadott Maximális memória lesz használva. Ha a Maximális memóriát az alapértelmezettől eltérő értékre állítja be, ügyeljen rá, hogy elég alacsonyra állítsa, hogy ne befolyásolja hátrányosan a többi számítási feladatot.

Bizonyos esetekben a lapszámozott jelentések számítási feladat elérhetetlenné válik. Ilyen esetben a számítási feladat hibás állapotot jelez a felügyeleti portálon, a felhasználók pedig időtúllépést tapasztalnak a jelentés renderelése során. A probléma megoldásához tiltsa le, majd engedélyezze újra a számítási feladatot.

## <a name="configure-workloads"></a>Számítási feladatok konfigurálása

Maximalizálhatja a kapacitás elérhető erőforrásait, ha a számítási feladatokat csak akkor engedélyezi, amikor használni szükséges őket. A memória- és más beállításokat csak akkor módosítsa, ha úgy értékelte, hogy az alapértelmezett beállítások nem felelnek meg az Ön erőforrásai kapacitásigényeinek.

### <a name="to-configure-workloads-in-the-power-bi-admin-portal"></a>Számítási feladatok konfigurálása a Power BI felügyeleti portálján

1. A **Kapacitásbeállítások** > **PREMIUM-KAPACITÁSOK** területen válasszon kapacitást.

1. A **TOVÁBBI LEHETŐSÉGEK** alatt bontsa ki a **Számítási feladatok** elemet.

1. Engedélyezzen egy vagy több számítási feladatot, és állítsa be a **Maximális memória** és a többi beállítás értékét.

1. Kattintson az **Alkalmaz** elemre.

### <a name="rest-api"></a>REST API

Számítási feladatokat a [Kapacitások](https://docs.microsoft.com/rest/api/power-bi/capacities) REST API-kkal engedélyezheti és rendelheti hozzá kapacitásokhoz.

## <a name="monitoring-workloads"></a>Számítási feladatok monitorozása

A [Power BI Premium-kapacitásmetrikák alkalmazás](service-admin-premium-monitor-capacity.md) metrikákat tesz elérhetővé az adatkészletről, az adatfolyamokról és a lapszámozott jelentésekről, amelyekkel monitorozhatja a kapacitásokhoz engedélyezett számítási feladatokat. 

## <a name="next-steps"></a>Következő lépések

[Power BI Premium-kapacitások optimalizálása](service-premium-capacity-optimize.md)     
[Önkiszolgáló adat-előkészítés a Power BI-ban adatfolyamokkal](service-dataflows-overview.md)   
[Mik a lapszámozott jelentések a Power BI Premiumban?](paginated-reports-report-builder-power-bi.md)   

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)