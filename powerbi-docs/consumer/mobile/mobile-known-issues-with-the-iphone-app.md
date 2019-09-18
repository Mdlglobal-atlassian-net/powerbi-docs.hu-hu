---
title: A „kommunikációs hibák” javítása az iOS-mobilalkalmazásokban – Power BI
description: Ez a cikk segíthet, ha a „Kommunikációs hibák történtek. A hibákat a Wi-Fi-kapcsolat proxybeállításai okozhatják.” üzenet jelenik meg.
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 05/21/2018
ms.author: mshenhav
ms.openlocfilehash: 9e487f4305b663028714cbe45ab76abaaa4a6db9
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/16/2019
ms.locfileid: "61135704"
---
# <a name="fixing-communication-failures-in-ios-mobile-apps---power-bi"></a>A „kommunikációs hibák” javítása az iOS-mobilalkalmazásokban – Power BI

| ![iPhone](./media/mobile-known-issues-with-the-iphone-app/iphone-logo-50-px.png) | ![iPad](./media/mobile-known-issues-with-the-iphone-app/ipad-logo-50-px.png) |
|:--- |:--- |
| iPhone-ok |iPadek |

## <a name="we-encountered-communication-failures"></a>„Kommunikációs hibák történtek”
„Kommunikációs hibák történtek. A hibákat a Wi-Fi-kapcsolat proxybeállításai okozhatják. Ha átvált egy másik Wi-Fi-kapcsolatra, azzal megoldhatja a problémát.”

Ez az üzenet akkor jelenik meg, ha az iPhone vagy iPad internetkapcsolatához kötelező, explicit HTTP-proxyt kell beállítani (manuális vagy automatikus). Ebben az esetben a Power BI alkalmazás nem fog működni az iOS-eszközön.

### <a name="workaround"></a>Áthidaló megoldás
Váltsa át az iPhone vagy iPad kapcsolatát egy másikra, amely nem igényel explicit HTTP-proxybeállítást (azaz egy olyan beállítást, ahol a HTTP-proxy ki van kapcsolva).

## <a name="other-issues"></a>Más problémái vannak?
Forduljon a [Power BI közösségéhez](http://community.powerbi.com/).

