---
title: Megbízható külső összekötők a Power bi-ban
description: A leg egy aláírt külső összekötő a Power bi-ban
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/3/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: 30b7457c6149320c43f24b967a842382821b01b1
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65607792"
---
# <a name="trusting-third-party-connectors"></a>Meghatalmazó külső összekötők

## <a name="why-do-you-need-trusted-third-party-connectors"></a>Miért kell megbízható külső összekötők?

A Power bi-ban általában javasoljuk, hogy az "adatok bővítmény biztonsági" szintű tartja a magasabb szintű, amely megakadályozza, hogy a kód, nem Microsoft által hitelesített betöltését. Előfordulhat azonban, amelyben az egyedi összekötők – beírt azokat, vagy a nyertes vagy kívül a Microsoft tanúsítványláncba szállító által biztosított alkalmazáscsomagokat betölteni kívánt sok esetben.

Egy adott összekötőt a fejlesztői is írja alá a tanúsítványt, és az információkat kell biztonságosan be anélkül, hogy csökkenti a biztonsági beállítások.

Ha szeretne többet megtudni a biztonsági beállításokat, áttekintheti őket [Itt](https://docs.microsoft.com/power-bi/desktop-connector-extensibility).

## <a name="using-the-registry-to-trust-third-party-connectors"></a>A beállításjegyzék használatával pedig megbízzon a külső összekötők

A Power bi-ban külső összekötők megbízó megbízik, a megadott beállításjegyzékbeli érték a tanúsítvány ujjlenyomatának listázásával történik. Ha ezzel az ujjlenyomattal kívánja betölteni az összekötő a tanúsítvány ujjlenyomata megegyezik, lesz nyissa meg a Power bi-ban "Ajánlott" biztonsági szintjét. 

Beállításjegyzékbeli elérési út HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Power BI Desktopban. Győződjön meg arról, hogy az elérési út létezik, vagy hozza azt létre. Ezen a helyen, elsősorban vezérli informatikai szabályzatnak, valamint szerkesztését igénylő helyi gép adminisztrációs hozzáférés miatt választottuk. 

![Állítsa be a Power BI Desktop beállításjegyzék megbízható külső kulcsok nélkül](media/desktop-trusted-third-party-connectors/desktoptrustedthird1.png)

Adjon meg egy új értéket a fent megadott elérési úton. A típusúnak kell lennie a "Karakterláncsoros érték" (REG_MULTI_SZ), és azt kell meghívni "TrustedCertificateThumbprints" 

![A Power BI Desktop Registry és a egy megbízható külső összekötők, de nincsenek kulcsok bejegyzés](media/desktop-trusted-third-party-connectors/desktoptrustedthird2.png)

Adja hozzá azt szeretné, hogy bízzon meg a tanúsítványok ujjlenyomatai. Elválasztóként vagy a beállításjegyzék-szerkesztőben jobb kattintással -> "\0" használatával több tanúsítvány módosítása, és minden egyes ujjlenyomat helyezi egy új sort is hozzáadhat. Például ujjlenyomat átveszi a rendszer egy önaláírt tanúsítványt. 

 ![A Power BI Desktop Registry és a egy megbízható külső kulcs beállítása](media/desktop-trusted-third-party-connectors/desktoptrustedthird3.png)

Ha idáig követte a megfelelő utasításokat, és a fejlesztői a megfelelő ujjlenyomat kapott, most tudnia kell a biztonságos megbízhatósági összekötőket a társított tanúsítvánnyal aláírva.

## <a name="how-to-sign-connectors"></a>Csatlakozás a összekötők

Ha egy összekötőt, vagy egy fejlesztői kell bejelentkeznie, olvashat, a Power Query-dokumentumokhoz [Itt](https://docs.microsoft.com/power-query/handlingconnectorsigning).
