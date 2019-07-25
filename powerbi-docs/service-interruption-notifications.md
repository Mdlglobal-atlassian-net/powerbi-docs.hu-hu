---
title: Szolgáltatáskimaradásokkal kapcsolatos értesítések
description: Útmutató ahhoz, hogy hogyan kérhet e-mail-értesítéseket a Power BI szolgáltatást érintő szolgáltatáskiesésről vagy teljesítménycsökkenésről.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/19/2019
ms.author: mblythe
ms.openlocfilehash: 0bb78e29cc3e9b9792d5916050179703281aa01a
ms.sourcegitcommit: 850e7883e21190151684e32f4d957beecd08e959
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/20/2019
ms.locfileid: "68366749"
---
# <a name="service-interruption-notifications"></a>Szolgáltatáskimaradásokkal kapcsolatos értesítések

Rendkívül fontos, hogy információt kapjon az üzletmenet szempontjából kritikus üzleti alkalmazások rendelkezésre állásáról. A Power BI értesítéseket küld az incidensekről, így Ön e-mailt kap a szolgáltatáskimaradásról és a teljesítménycsökkenésről. Habár a Power BI 99,9%-os szolgáltatói szerződést (SLA) kínál, így ez rendkívül ritkán fordul elő, szeretnénk garantálni, hogy Ön minden ilyen esetről értesüljön. Az alábbi képernyőképen láthatja, hogy milyen típusú e-maileket fog kapni, ha engedélyezi az értesítéseket:

![Frissítéssel kapcsolatos értesítő e-mail](media/service-interruption-notifications/refresh-notification-email.png)

Jelenleg a következő _megbízhatósági eseményekről_küld e-mailt a rendszer:

- Jelentés megnyitási megbízhatósága
- Modell frissítési megbízhatósága
- Lekérdezés frissítési megbízhatósága

Ha az incidens megoldódott, arról is e-mailt küldünk.

> [!NOTE]
> Ez a funkció jelenleg csak a Power BI Premium dedikált kapacitásainak esetében érhető el. A megosztott kapacitások esetében nem érhető el.

## <a name="enable-notifications"></a>Értesítések engedélyezése

Az értesítéseket a Power BI bérlői rendszergazdája engedélyezheti a felügyeleti portálon:

1. Adjon meg vagy hozzon létre egy levelezési biztonsági csoportot, amelynek a rendszer elküldheti az értesítéseket.

1. A felügyeleti portálon válassza a **Bérlői beállítások** lehetőséget. A **Súgó és támogatás beállításai**területen bontsa ki az **E-mail-értesítések fogadása szolgáltatásbeli kimaradásokról vagy incidensekről** elemet.

1. Engedélyezze az értesítéseket, adjon meg egy biztonsági csoportot, majd válassza az **Alkalmazás** lehetőséget.

    ![Szolgáltatási értesítések engedélyezése](media/service-interruption-notifications/enable-notifications.png)

> [!NOTE]
> A Power BI a következő fiókból küldi ki az értesítéseket: no-reply-powerbi@microsoft.com. Ügyeljen rá, hogy ez a fiók felkerüljön az engedélyezési listára, mivel így elkerülheti, hogy az értesítések a levélszemét mappába kerüljenek.

## <a name="next-steps"></a>Következő lépések

[A Power BI Pro és a Power BI Premium támogatási lehetőségei](service-support-options.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)