---
title: Helyszíni adatátjáró
description: Ez a cikk egy áttekintés a Power BI-hoz készült helyszíni adatátjáróhoz. Ezt az átjárót használhatja DirectQuery-adatforrásokon történő munkához. Helyszíni adatokkal rendelkező felhőbeli adatkészletek frissítésére is használhatja ezt az átjárót.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Gateways
ms.date: 07/15/2019
ms.openlocfilehash: 883d5c83019df293628d096f5834c9b5c6d425b6
ms.sourcegitcommit: 73228d0a9038b8369369c059ad06168d2c5ff062
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/02/2019
ms.locfileid: "68730276"
---
# <a name="what-is-an-on-premises-data-gateway"></a>Mi az a helyszíni adatátjáró?

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

A helyszíni adatátjáró hídként biztosítja a helyszíni (nem felhőbeli) adatok és számos Microsoft-felhőszolgáltatás közötti gyors és biztonságos adatátvitelt. Ezen szolgáltatások közé tartozik a Power BI, a PowerApps, a Microsoft Flow, az Azure Analysis Services, és az Azure Logic Apps. Az átjáró használata lehetővé teszi, hogy a cégek az adatbázisaikat és más adatforrásaikat a helyszíni hálózaton belül tartsák, de ezzel együtt biztonságosan használhassák ezeket a felhőszolgáltatásokban is.

## <a name="how-the-gateway-works"></a>Az átjáró működése

![Az átjáró áttekintése](media/service-gateway-onprem/on-premises-data-gateway.png)

Az átjáró működéséről további információ talál [A helyszíni adatátjáró architektúrája](/data-integration/gateway/service-gateway-onprem-indepth) című témakörben.

## <a name="types-of-gateways"></a>Átjárótípusok

Kétféle átjárótípus van, mindkettő más-más helyzethez:

* A **helyszíni adatátjáró** több felhasználó számára teszi lehetővé, hogy több helyszíni adatforráshoz csatlakozzanak. A helyszíni adatátjárót egyetlen átjárótelepítéssel minden támogatott szolgáltatáshoz használhatja. Ez az átjáró összetett helyzetekhez optimális, ahol többen is hozzá akarnak férni több adatforráshoz.

* A **helyszíni adatátjáró (személyes mód)** egyetlen felhasználónak teszi lehetővé, hogy kapcsolódjon a forrásokhoz, és nem osztható meg másokkal. A helyszíni adatátjáró (személyes mód) csak a Power BI-jal használható. Ez az átjáró kiválóan alkalmazható olyan helyzetekhez, ahol egyedül Ön készít jelentéseket, és nem szükséges megosztania adatforrásokat másokkal.

## <a name="use-a-gateway"></a>Átjáró használata

Átjáró használatához négy fő lépés szükséges.

1. [Az átjáró letöltése és telepítése](/data-integration/gateway/service-gateway-install) helyi számítógépre.
2. Az átjáró [konfigurálása](/data-integration/gateway/service-gateway-app) a tűzfal és más hálózati követelmények alapján.
3. [Átjáró-rendszergazdák hozzáadása](/data-integration/gateway/service-gateway-manage), akik más hálózati követelményeket is kezelhetnek.
4. Az átjáró [hibaelhárítása](service-gateway-onprem-tshoot.md) hibák esetén.

## <a name="next-steps"></a>Következő lépések

* [A helyszíni adatátjáró telepítése](/data-integration/gateway/service-gateway-install)


További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
