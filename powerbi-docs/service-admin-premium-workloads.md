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
ms.openlocfilehash: c84bebef5589ec391e3640ff3be674b1fb5a0ebd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65564881"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Számítási feladatok konfigurálása egy Premium-kapacitásban

Ez a cikk azt ismerteti, hogy hogyan engedélyezhet és konfigurálhat számítási feladatokat Power BI Premium-kapacitásokban. A kapacitások alapértelmezés szerint csak a Power BI-lekérdezésekkel társított számítási feladatot támogatják. További számítási feladatokat engedélyezhet és konfigurálhat **[mesterséges intelligenciához (Cognitive Services)](service-cognitive-services.md)** , **[adatfolyamokhoz](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)** és **[lapszámozott jelentésekhez](paginated-reports-save-to-power-bi-service.md)** .

## <a name="default-memory-settings"></a>Alapértelmezett memóriabeállítások

A lekérdezési számítási feladatok a Premium-kapacitás SKU-ja által meghatározott erőforrásokhoz vannak optimalizálva, valamint ez szabja meg azok korlátait. A Premium-kapacitások emellett kapacitás-erőforrások használatára képes, további számítási feladatokat is támogatnak. A számítási feladatok alapértelmezett memóriaértékei az SKU-ban elérhető kapacitás-csomópontokon alapulnak. A maximum memóriabeállítások nem halmozottak. A megadott maximum értékig terjedő memória mesterséges intelligenciához és adatfolyamokhoz dinamikusan, lapszámozott jelentésekhez viszont statikusan van lefoglalva. 

### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>Microsoft Office SKU-k szoftverszolgáltatásokhoz (SaaS)

|                     | EM2                      | EM3                       | P1                      | P2                       | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|--------------------------|
| AI | N.A. | N.A. | 20 %-os alapértelmezett; 20 %-os minimális | Alapértelmezés szerint 20%; minimum 10% | Alapértelmezés szerint 20%; minimum 5% |
| Adatfolyamok | N.A. |Alapértelmezés szerint 20%; minimum 12%  | Alapértelmezés szerint 20%; minimum 5%  | Alapértelmezés szerint 20%; minimum 3% | Alapértelmezés szerint 20%; minimum 2%  |
| Oldalakra osztott jelentések | N.A. |N.A. | Alapértelmezés szerint 20%; minimum 10% | Alapértelmezés szerint 20%; minimum 5% | Alapértelmezés szerint 20%; minimum 2,5% |
| | | | | | |

### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>Microsoft Office SKU-k platformszolgáltatásokhoz (PaaS)

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| AI | N.A.                      | 20 %-os alapértelmezett; 100 %-os minimális                     | 20 %-os alapértelmezett; 50 %-os minimális                     | 20 %-os alapértelmezett; 20 %-os minimális | Alapértelmezés szerint 20%; minimum 10% | Alapértelmezés szerint 20%; minimum 5% |
| Adatfolyamok         | Alapértelmezés szerint 40%; minimum 40% | Alapértelmezés szerint 24%; minimum 24% | Alapértelmezés szerint 20%; minimum 12% | Alapértelmezés szerint 20%; minimum 5%  | Alapértelmezés szerint 20%; minimum 3% | Alapértelmezés szerint 20%; minimum 2%   |
| Oldalakra osztott jelentések | N.A.                      | N.A.                      | N.A.                     | Alapértelmezés szerint 20%; minimum 10% | Alapértelmezés szerint 20%; minimum 5% | Alapértelmezés szerint 20%; minimum 2,5% |
| | | | | | |

## <a name="workload-settings"></a>Számítási beállítások

### <a name="ai-preview"></a>AI (előzetes verzió)

Mellett a **maximális memória** beállítást, a mesterséges Intelligencia számítási feladathoz tartozik egy további beállítás **használatának engedélyezése a Power BI Desktopból**. Az alapértelmezett érték **ki**. Ez a beállítás későbbi használatra fenntartva, és előfordulhat, hogy nem jelennek meg az összes bérlőre vonatkozóan.

### <a name="datasets-preview"></a>Adatkészletek (előzetes verzió)

Az adatkészletek számítási feladatok alapértelmezés szerint engedélyezve van, és nem tiltható le. Ezt a munkafolyamatot tartalmaz egy további beállítás **XMLA-végpontja**. Az alapértelmezett érték **1**, azaz engedélyezve van. Ezzel a beállítással ügyfélalkalmazásokról érkező kapcsolatokat, tartsa tiszteletben a biztonsági csoport tagsága állítsa be a munkaterület és alkalmazás szinten. További tudnivalókért lásd: [csatlakozhat az eszközök és az ügyfélalkalmazások adatkészletek](service-premium-connect-tools.md).

### <a name="dataflows"></a>Adatfolyamok

Mellett a **maximális memória** beállításnál az adatfolyamok számítási feladathoz tartozik egy további beállítás **tárolóméret**. Ez a beállítás lehetővé teszi adatfolyamot számítási feladatok teljesítményoptimalizálása összetettebb, a számítási műveltekből adatfolyamok feldolgozására.

Egy adatfolyam frissítésekor az adatfolyamot számítási feladatot indít egy tárolót az egyes entitásokhoz az adatfolyamban. A tárolók a memória, akár a kötet a tároló mérete beállításban megadott is eltarthat. A termékváltozatokat az alapértelmezett **700 MB**. Előfordulhat, hogy szeretné módosítani ezt a beállítást, ha:

- Adatfolyamok frissítése túl sokáig tart, vagy időtúllépés adatfolyamot frissítése sikertelen.
- Adatfolyam-entitások számítási lépéseket, például egy illesztési tartalmazza.  

Azt javasoljuk, használja a a [Power BI Premium kapacitás-metrikák](service-admin-premium-monitor-capacity.md) alkalmazásnak elemezni az adatfolyamot számítási feladatok teljesítményére. 

Bizonyos esetekben méretének növelése nem javíthatja a teljesítményt. Például, ha az adatfolyamban az adatok beolvasása csak forrásból jelentős számítások végrehajtása nélkül, valószínűleg a tároló méretének módosítása nem sokat segít. Ha ez az adatfolyam számítási feladatok több memóriát lefoglalni az entitás frissítési műveletek lehetővé segíthetnek a tároló méretének növelését. Lefoglalt memória problémába, erősen számított entitások frissítéséhez szükséges idő, csökkentheti. 

A tárolóméret érték nem lehet hosszabb a maximális memóriát az adatfolyamok számítási feladatokhoz. Például a P1 kapacitás, 25GB-nyi memóriát. Ha az adatfolyam-számítási feladatok maximális memória (%) értéke 20 %-tároló mérete (MB) nem lehet hosszabb 5000-es. Minden esetben a tároló mérete nem haladhatja meg a maximális memóriát, még akkor is, ha magasabb értéket állít be. 

### <a name="paginated-reports-preview"></a>Többoldalas jelentések (előzetes verzió)

Többoldalas jelentések futtathatók, amikor egy jelentés megjelenítése egyéni kód lehetővé. Például szövegszínét tartalom alapján dinamikusan változnak, amely is igénybe vehet további memória. A lapszámozott jelentéseket a Power BI Premium a kapacitás egy korlátozott területén belül futtatja. Maximális memória megadott használt *e* aktív azonban a számítási feladatok. Ha a maximális memória beállítás módosítása az alapértelmezett, mindenképpen állítsa be azt alacsony ahhoz, hogy az informatikai negatívan más számítási feladatok nem érinti.

Bizonyos esetekben a többoldalas jelentések számítási feladatot is elérhetetlenné válik. Ebben az esetben a számítási feladat hibás állapotú bemutatja a felügyeleti portálon, és a felhasználók láthatják a jelentésmegjelenítés időtúllépések. A probléma megoldásához tiltsa le a számítási feladatok, és majd engedélyezze újra.

## <a name="configure-workloads"></a>Számítási feladatok konfigurálása

Maximalizálhatja a kapacitás elérhető erőforrásait, ha a számítási feladatokat csak akkor engedélyezi, amikor használni szükséges őket. A memóriabeállításokat csak akkor módosítsa, ha úgy értékelte, hogy az alapértelmezett beállítások nem felelnek meg az Ön erőforrásai kapacitásigényeinek.  

### <a name="to-configure-workloads-in-the-power-bi-admin-portal"></a>Számítási feladatok konfigurálása a Power BI felügyeleti portálján

1. A **Kapacitásbeállítások** > **PREMIUM-KAPACITÁSOK** területen válasszon kapacitást.

1. A **TOVÁBBI LEHETŐSÉGEK** alatt bontsa ki a **Számítási feladatok** elemet.

1. Engedélyezzen egy vagy több számítási feladatot, és állítsa be a **Maximális memória** értékét.   

    
    ![Számítási feladatok engedélyezése](media/service-admin-premium-workloads/admin-portal-workloads.png)

1. Kattintson az **Alkalmaz** gombra.

### <a name="rest-api"></a>REST API

Számítási feladatokat a [Kapacitások](https://docs.microsoft.com/rest/api/power-bi/capacities) REST API-kkal engedélyezheti és rendelheti hozzá kapacitásokhoz.

## <a name="monitoring-workloads"></a>Számítási feladatok monitorozása

A [Power BI Premium-kapacitásmetrikák alkalmazás](service-admin-premium-monitor-capacity.md) metrikákat tesz elérhetővé az adatkészletről, az adatfolyamokról és a lapszámozott jelentésekről, amelyekkel monitorozhatja a kapacitásokhoz engedélyezett számítási feladatokat. 

## <a name="next-steps"></a>Következő lépések

[A Power BI Premium-kapacitásait optimalizálása](service-premium-capacity-optimize.md)     
[Önkiszolgáló adat-előkészítés a Power BI-ban adatfolyamokkal](service-dataflows-overview.md)   
[Mik a lapszámozott jelentések a Power BI Premiumban?](paginated-reports-report-builder-power-bi.md)   

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)