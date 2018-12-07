---
title: A Power BI és az ExpressRoute
description: A Power BI és az ExpressRoute
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 12/03/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 62289c974e25207f3a991e7f17a0ee965c729b8a
ms.sourcegitcommit: b03912343a5a214c6bb972aaa6aa051c2a5f4332
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2018
ms.locfileid: "52900129"
---
# <a name="power-bi-and-expressroute"></a>A Power BI és az ExpressRoute

Az **ExpressRoute** egy olyan Azure-szolgáltatás, amely magánkapcsolatok létrehozását teszi lehetővé az Azure-adatközpontok (ahol a Power BI is található) és a saját helyszíni infrastruktúrája vagy bérelt kiszolgálói környezete között.

A **Power BI** és az **ExpressRoute** közös használatával létrehozhat egy hálózati magánkapcsolatot a vállalata és a Power BI között (vagy egy internetszolgáltatótól bérelhető kiszolgálói létesítmény között), így megkerülheti az Internetet, és jobb védelmet biztosíthat érzékeny Power BI-adatai és -kapcsolatai számára.

További információkat az [ExpressRoute áttekintésében](/azure/expressroute/expressroute-introduction) találhat. A Power BI használható az ExpressRoute-tal, azonban van néhány olyan kivétel, amikor a Power BI a nyilvános interneten keresztül fogad vagy küld adatokat. A Power BI által használt URL-ek listáját megtekintheti a [Power BI URL-címei](power-bi-whitelist-urls.md) című témakörben.

![ExpressRoute-diagram](media/service-admin-power-bi-expressroute/pbi_expressroute_1.png)