---
title: A Power BI és az ExpressRoute
description: A Power BI és az ExpressRoute
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 12/03/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 0c4618150094a4eabb0dc9745e9ac93e4f342ff1
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54291096"
---
# <a name="power-bi-and-expressroute"></a>A Power BI és az ExpressRoute

Az **ExpressRoute** egy olyan Azure-szolgáltatás, amely magánkapcsolatok létrehozását teszi lehetővé az Azure-adatközpontok (ahol a Power BI is található) és a saját helyszíni infrastruktúrája vagy bérelt kiszolgálói környezete között.

A **Power BI** és az **ExpressRoute** közös használatával létrehozhat egy hálózati magánkapcsolatot a vállalata és a Power BI között (vagy egy internetszolgáltatótól bérelhető kiszolgálói létesítmény között), így megkerülheti az Internetet, és jobb védelmet biztosíthat érzékeny Power BI-adatai és -kapcsolatai számára.

További információkat az [ExpressRoute áttekintésében](/azure/expressroute/expressroute-introduction) találhat. A Power BI használható az ExpressRoute-tal, azonban van néhány olyan kivétel, amikor a Power BI a nyilvános interneten keresztül fogad vagy küld adatokat. A Power BI által használt URL-ek listáját megtekintheti a [Power BI URL-címei](power-bi-whitelist-urls.md) című témakörben.

![ExpressRoute-diagram](media/service-admin-power-bi-expressroute/pbi_expressroute_1.png)