---
title: Számítási feladatok konfigurálása a Power BI Premiumban
description: Megtudhatja, hogyan konfigurálhat számítási feladatokat a Power BI Premiumban.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/01/2019
LocalizationGroup: Premium
ms.openlocfilehash: fbff4b744cf4a35f2fe1d0ae46f4676cd5f1db77
ms.sourcegitcommit: 8525b6365f3e224176730f4b8e5dae83f540a4ff
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/01/2019
ms.locfileid: "58795245"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Számítási feladatok konfigurálása egy Premium-kapacitásban

Ez a cikk azt ismerteti, hogy hogyan engedélyezhet és konfigurálhat számítási feladatokat Power BI Premium-kapacitásokban. A kapacitások alapértelmezés szerint csak a Power BI-lekérdezésekkel társított számítási feladatot támogatják. További számítási feladatokat engedélyezhet és konfigurálhat **[mesterséges intelligenciához (Cognitive Services)](service-cognitive-services.md)**, **[adatfolyamokhoz](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)** és **[lapszámozott jelentésekhez](paginated-reports-save-to-power-bi-service.md)**.

## <a name="default-memory-settings"></a>Alapértelmezett memóriabeállítások

A lekérdezési számítási feladatok a Premium-kapacitás SKU-ja által meghatározott erőforrásokhoz vannak optimalizálva, valamint ez szabja meg azok korlátait. A Premium-kapacitások emellett kapacitás-erőforrások használatára képes, további számítási feladatokat is támogatnak. A számítási feladatok alapértelmezett memóriaértékei az SKU-ban elérhető kapacitás-csomópontokon alapulnak. A maximum memóriabeállítások nem halmozottak. A megadott maximum értékig terjedő memória mesterséges intelligenciához és adatfolyamokhoz dinamikusan, lapszámozott jelentésekhez viszont statikusan van lefoglalva. 

### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>Microsoft Office SKU-k szoftverszolgáltatásokhoz (SaaS)

|                     | EM2                      | EM3                       | P1                      | P2                       | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|--------------------------|
| AI (Cognitive Services) | Alapértelmezés szerint 20%, minimum TBD| Alapértelmezés szerint 20%, minimum TBD | Alapértelmezés szerint 20%, minimum TBD | Alapértelmezés szerint 20%, minimum TBD | Alapértelmezés szerint 20%, minimum TBD |
| Adatfolyamok | N.A. |Alapértelmezés szerint 20%; minimum 12%  | Alapértelmezés szerint 20%; minimum 5%  | Alapértelmezés szerint 20%; minimum 3% | Alapértelmezés szerint 20%; minimum 2%  |
| Oldalakra osztott jelentések | N.A. |N.A. | Alapértelmezés szerint 20%; minimum 10% | Alapértelmezés szerint 20%; minimum 5% | Alapértelmezés szerint 20%; minimum 2,5% |
| | | | | | |

### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>Microsoft Office SKU-k platformszolgáltatásokhoz (PaaS)

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| AI (Cognitive Services) | N.A.                      | Alapértelmezés szerint 20%, minimum TBD                      | Alapértelmezés szerint 20%, minimum TBD                     | Alapértelmezés szerint 20%, minimum TBD | Alapértelmezés szerint 20%, minimum TBD | Alapértelmezés szerint 20%, minimum TBD |
| Adatfolyamok         | Alapértelmezés szerint 40%; minimum 40% | Alapértelmezés szerint 24%; minimum 24% | Alapértelmezés szerint 20%; minimum 12% | Alapértelmezés szerint 20%; minimum 5%  | Alapértelmezés szerint 20%; minimum 3% | Alapértelmezés szerint 20%; minimum 2%   |
| Oldalakra osztott jelentések | N.A.                      | N.A.                      | N.A.                     | Alapértelmezés szerint 20%; minimum 10% | Alapértelmezés szerint 20%; minimum 5% | Alapértelmezés szerint 20%; minimum 2,5% |
| | | | | | |

## <a name="configure-workloads"></a>Számítási feladatok konfigurálása

Maximalizálhatja a kapacitás elérhető erőforrásait, ha a számítási feladatokat csak akkor engedélyezi, amikor használni szükséges őket. A memóriabeállításokat csak akkor módosítsa, ha úgy értékelte, hogy az alapértelmezett beállítások nem felelnek meg az Ön erőforrásai kapacitásigényeinek.  

### <a name="to-configure-workloads-in-the-power-bi-admin-portal"></a>Számítási feladatok konfigurálása a Power BI felügyeleti portálján

1. A **Kapacitásbeállítások** > **PREMIUM-KAPACITÁSOK** területen válasszon kapacitást.

1. A **TOVÁBBI LEHETŐSÉGEK** alatt bontsa ki a **Számítási feladatok** elemet.

1. Engedélyezzen egy vagy több számítási feladatot, és állítsa be a **Maximális memória** értékét.   

    
    ![Számítási feladatok engedélyezése](media/service-admin-premium-workloads/admin-portal-workloads.png)

1. Kattintson az **Alkalmaz** gombra.

> [!NOTE]
> Ha engedélyezi a lapszámozott jelentések számítási feladatot, ügyeljen rá, a lapszámozott jelentésekkel a jelentés renderelése során saját kódot futtathat (például dinamikusan változtathatja a szövegszínt a tartalom alapján). A lapszámozott jelentéseket a Power BI Premium a kapacitás egy korlátozott területén belül futtatja. Ehhez a területhez az Ön által megadott maximális memóriát használja, akár aktív a számítási feladat, akár nem. Ha egy kapacitásban több Power BI-jelentést vagy -adatfolyamot használ, ügyeljen rá, hogy a lapszámozott jelentésekhez kellően alacsony memóriakorlátot adjon meg, hogy azok ne befolyásolhassák hátrányosan a többi számítási feladatot. Ritkán előfordulhat, hogy a „lapszámozott jelentések” számítási feladat elérhetetlenné válik. Ilyen esetben a számítási feladat hibás állapotot jelez a felügyeleti portálon, a felhasználók pedig időtúllépést tapasztalnak a jelentés renderelése során. A probléma megoldásához tiltsa le, majd engedélyezze újra a számítási feladatot.

### <a name="rest-api"></a>REST API

Számítási feladatokat a [Kapacitások](https://docs.microsoft.com/rest/api/power-bi/capacities) REST API-kkal engedélyezheti és rendelheti hozzá kapacitásokhoz.

## <a name="monitoring-workloads"></a>Számítási feladatok monitorozása

A [Power BI Premium-kapacitásmetrikák alkalmazás](service-admin-premium-monitor-capacity.md) metrikákat tesz elérhetővé az adatkészletről, az adatfolyamokról és a lapszámozott jelentésekről, amelyekkel monitorozhatja a kapacitásokhoz engedélyezett számítási feladatokat. 

## <a name="next-steps"></a>Következő lépések

[A Power BI Premium-kapacitás erőforrás-kezelése és optimalizálása](service-premium-understand-how-it-works.md)   
[Önkiszolgáló adat-előkészítés a Power BI-ban adatfolyamokkal](service-dataflows-overview.md)   
[Mik a lapszámozott jelentések a Power BI Premiumban?](paginated-reports-report-builder-power-bi.md)   

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)