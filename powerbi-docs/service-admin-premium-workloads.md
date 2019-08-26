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
ms.date: 04/15/2019
LocalizationGroup: Premium
ms.openlocfilehash: 49a1f02e5aa327c2704b6c2d789934a43b760ad0
ms.sourcegitcommit: 0e50ebfa8762e19286566432870ef16d242ac78f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/13/2019
ms.locfileid: "68962015"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Számítási feladatok konfigurálása egy Premium-kapacitásban

Ez a cikk azt ismerteti, hogy hogyan engedélyezhet és konfigurálhat számítási feladatokat Power BI Premium-kapacitásokban. A kapacitások alapértelmezés szerint csak a Power BI-lekérdezésekkel társított számítási feladatot támogatják. További számítási feladatokat engedélyezhet és konfigurálhat **[mesterséges intelligenciához (Cognitive Services)](service-cognitive-services.md)**, **[adatfolyamokhoz](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)** és **[lapszámozott jelentésekhez](paginated-reports-save-to-power-bi-service.md)**.

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

A **Maximális memória** beállítás mellett az AI számítási feladat egy további beállítása a **Power BI Desktopból történő használat engedélyezése**. Ennek alapértelmezett beállítása **Kikapcsolva**. Ez a beállítás jövőbeli használatra van fenntartva, és nem feltétlenül jelenik meg minden bérlőben.

### <a name="datasets-preview"></a>Adathalmazok (előzetes verzió)

Az Adathalmazok számítási feladat alapértelmezés szerint engedélyezve van, és nem tiltható le. Ez a számítási feladat tartalmaz egy további beállítást az _XMLA-végponthoz_, valamint egy teljesítménnyel kapcsolatos beállításcsoportot. Ez az **XMLA-végpont** beállítás adja meg, hogy a csatlakozó ügyfélalkalmazások figyelembe vegyék a munkaterület és az alkalmazás szintjén meghatározott biztonságicsoport-tagságot. További információ: [Csatlakozás adathalmazokhoz ügyfélalkalmazásokkal és -eszközökkel](service-premium-connect-tools.md).

A teljesítménnyel kapcsolatos beállításokat az alábbi táblázat foglalja össze.

| Beállítás neve | Leírás | Használat |
|---------------------------------|----------------------------------------|----------------------------------------|
| **Köztes sorok maximális száma** | A DirectQuery által visszaadott köztes sorok maximális száma. Az alapértelmezett érték 1 000 000, a megengedett tartomány pedig 100 000-től 2 147 483 647-ig terjed. | Az erőforrás-igényes vagy rosszul megtervezett jelentések hatásainak szabályozása. |
| **Offline adathalmaz maximális mérete (GB)** | A memóriában lévő offline adathalmaz maximális mérete. Ez a tömörített méret a lemezen. Az alapértelmezett értéket a termékváltozat szabja meg, a megengedett tartomány pedig 0,1 GB-tól 10 GB-ig terjed. | Megakadályozza, hogy a jelentéskészítők a kapacitást hátrányosan érintő, nagyméretű adathalmaz tegyenek közzé. |
| **Eredménysorok maximális száma** | Megadja a DAX-lekérdezés által visszaadott sorok maximális számát. Az alapértelmezett érték -1 (nincs korlátozás), a megengedett tartomány pedig 100 000-től 2 147 483 647-ig terjed. | Az erőforrás-igényes vagy rosszul megtervezett jelentések hatásainak szabályozása. |
| **Lekérdezés memóriakorlátja (%)** | Csak DAX-mértékekre és -lekérdezésekre vonatkozik. Százalékban van megadva, és korlátozza a lekérdezés során az ideiglenes eredmények által felhasználható memória mennyiségét. | Az erőforrás-igényes vagy rosszul megtervezett jelentések hatásainak szabályozása. |
| **Lekérdezés időkorlátja (másodpercben)** | Egész szám, amely másodpercekben adja meg a lekérdezések időkorlátját. Alapértelmezett értéke 3 600 másodperc (60 perc). A nulla (0) érték azt jelenti, hogy a lekérdezésekre nincs időkorlát. | A hosszan futó lekérdezések jobb szabályozása. |
|  |  |  |

### <a name="dataflows"></a>Adatfolyamok

A **Maximális memória** beállítás mellett az Adatfolyamok számítási feladat egy további beállítása a **Tárolóméret**. Ez a beállítás teszi lehetővé az Adatfolyam számítási feladatok teljesítményének optimalizálását az összetettebb, számításigényes adatfolyamokhoz.

Adatfolyam frissítésekor az Adatfolyam számítási feladat az adatfolyam minden entitásához létrehoz egy tárolót. Minden tároló legfeljebb a Tárolóméret beállításban megadott mennyiségű memóriát foglalhat el. Az alapértelmezett érték minden termékváltozathoz **700 MB**. Ezt a beállítást a következő esetekben lehet érdemes módosítani:

- Az adatfolyamok frissítése túl sokáig tart, vagy időtúllépés miatt meghiúsul.
- Az adatfolyam-entitások között számítási lépések, például összekapcsolás is szerepel.  

Az Adatfolyam számítási feladat teljesítményének elemzéséhez javasolt a [Power BI Premium-kapacitásmetrikák](service-admin-premium-monitor-capacity.md) alkalmazás használata. 

Bizonyos esetekben a tárolóméret növelése nem feltétlenül javítja a teljesítményt. Ha az adatfolyam például csak egy jelentős számításokat végző forrásból nyer adatokat, a tárolóméret módosítása valószínűleg nem használ. A tárolóméret növelése akkor lehet előnyös, ha lehetővé teszi, hogy az Adatfolyam számítási feladat több memóriát foglaljon le az entitásfrissítési műveletekhez. Több memória lefoglalásával csökkenthető a sok számítást igénylő entitások frissítésének ideje.

A Tárolóméret érték nem haladhatja meg az Adatfolyam számítási feladat maximális memóriáját. Egy P1 kapacitás például 25 GB memóriával rendelkezik. Ha az Adatfolyam számítási feladat Maximális memória (%) beállítása 20%, a Tárolóméret (MB) nem haladhatja meg az 5000 értéket. A Tárolóméret még ennél magasabb érték beállításakor sem haladhatja meg a maximális memóriát.

### <a name="paginated-reports-preview"></a>Többoldalas jelentések (előzetes verzió)

A többoldalas jelentések egyéni kód futtatását teszik lehetővé egy jelentés renderelésekor. Ilyen például a szövegszín dinamikus megváltoztatása a tartalom alapján, ez pedig további memóriát igényelhet. A lapszámozott jelentéseket a Power BI Premium a kapacitás egy korlátozott területén belül futtatja. Attól függetlenül, hogy a számítási feladat *aktív vagy nem*, a megadott Maximális memória lesz használva. Ha a Maximális memóriát az alapértelmezettől eltérő értékre állítja be, ügyeljen rá, hogy elég alacsonyra állítsa, hogy ne befolyásolja hátrányosan a többi számítási feladatot.

Bizonyos esetekben a Többoldalas jelentések számítási feladat elérhetetlenné válik. Ilyen esetben a számítási feladat hibás állapotot jelez a felügyeleti portálon, a felhasználók pedig időtúllépést tapasztalnak a jelentés renderelése során. A probléma megoldásához tiltsa le, majd engedélyezze újra a számítási feladatot.

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