---
title: A „kommunikációs hibák” javítása az iOS-mobilalkalmazásokban – Power BI
description: Ez a cikk segíthet, ha a „Kommunikációs hibák történtek. A hibákat a Wi-Fi-kapcsolat proxybeállításai okozhatják.” üzenet jelenik meg.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: painbar
ms.openlocfilehash: 0162d78fd4358f415ac52ea70bd3460d3c28b722
ms.sourcegitcommit: 480bba9c745cb9af2005637e693c5714b3c64a8a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/11/2020
ms.locfileid: "79114919"
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
Forduljon a [Power BI közösségéhez](https://community.powerbi.com/).

