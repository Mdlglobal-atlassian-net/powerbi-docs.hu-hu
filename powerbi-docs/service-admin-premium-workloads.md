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
ms.date: 02/26/2019
LocalizationGroup: Premium
ms.openlocfilehash: 5b9bec67fef672d219b11bf3b3750959e72410b6
ms.sourcegitcommit: 364ffa1178cdfb0a20acffc0fd79922ebc892d72
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/02/2019
ms.locfileid: "57226066"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Számítási feladatok konfigurálása egy Premium-kapacitásban

Ez a cikk azt ismerteti, hogy hogyan engedélyezhet és konfigurálhat számítási feladatokat Power BI Premium-kapacitásokban. A kapacitások alapértelmezés szerint csak a Power BI-lekérdezésekkel társított számítási feladatot támogatják. A lekérdezési számítási feladatok a Premium-kapacitás SKU-ja által meghatározott erőforrásokhoz vannak optimalizálva, valamint ez szabja meg azok korlátait. A Premium-kapacitások emellett kapacitás-erőforrások használatára képes, további számítási feladatokat is támogatnak.

## <a name="configure-workloads"></a>Számítási feladatok konfigurálása

További számítási feladatokat engedélyezhet és konfigurálhat [adatfolyamokhoz](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium) és [lapszámozott](paginated-reports-save-to-power-bi-service.md) jelentésekhez. A számítási feladatok alapértelmezett memóriaértékei az SKU-ban elérhető kapacitás-csomópontokon alapulnak. A maximum memóriabeállítások nem halmozottak. A megadott maximum értékig terjedő memória adatfolyamokhoz dinamikusan, lapszámozott jelentésekhez viszont statikusan van lefoglalva. 

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


## <a name="next-steps"></a>Következő lépések

[A Power BI Premium-kapacitás erőforrás-kezelése és optimalizálása](service-premium-understand-how-it-works.md)   
[Önkiszolgáló adat-előkészítés a Power BI-ban adatfolyamokkal](service-dataflows-overview.md)   
[Mik a lapszámozott jelentések a Power BI Premiumban?](paginated-reports-report-builder-power-bi.md)   

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)