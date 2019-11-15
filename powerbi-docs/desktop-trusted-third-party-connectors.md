---
title: Megbízható harmadik féltől származó összekötők a Power BI-ban
description: Harmadik féltől származó aláírt összekötő beállítása megbízhatóként a Power BI-ban
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/3/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: ac3f795d6a80d5f143daf68436f41f5771b3c2bb
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73876162"
---
# <a name="trusting-third-party-connectors"></a>Harmadik féltől származó összekötők beállítása megbízhatóként

## <a name="why-do-you-need-trusted-third-party-connectors"></a>Miért van szükség megbízható harmadik féltől származó összekötőkre?

A Power BI esetében általában azt javasoljuk, hogy magasabb szinten tartsák az adatbővítmények biztonsági szintjét, ami megakadályozza a Microsoft által nem hitelesített kódok betöltését. Számos esetben azonban előfordulhat, hogy konkrét összekötőket szeretne betölteni, amelyeket Ön írt, vagy a Microsoft tanúsítványláncán kívüli tanácsadótól vagy gyártótól szerzett be.

A fejlesztők aláírhatják az összekötőket egy tanúsítvánnyal, és megadhatják a szükséges információkat, amelyekkel biztonsági beállításainak csökkentése nélkül, biztonságosan betöltheti az összekötőket.

Ha többet szeretne megtudni a biztonsági beállításokról, [itt](https://docs.microsoft.com/power-bi/desktop-connector-extensibility) olvashat róluk.

## <a name="using-the-registry-to-trust-third-party-connectors"></a>A beállításjegyzék használata a harmadik féltől származó összekötők megbízhatóként való beállításához

Ha a Power BI-ban megbízhatóként kíván beállítani egy külső féltől származó összekötőt, akkor foglalja bele az adott tanúsítvány ujjlenyomatát egy megadott beállításjegyzékbeli értékbe. Ha ez az ujjlenyomat megegyezik a betölteni kívánt összekötőn lévő tanúsítvány ujjlenyomatával, akkor betölthető a Power BI Ajánlott biztonsági szintjén. 

A beállításjegyzékbeli elérési út: HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Power BI Desktop. Győződjön meg arról, hogy az elérési út létezik, vagy hozza létre. Ezt a helyet azért választottuk, mert elsődlegesen az informatikai szabályzat vezérli, valamint a szerkesztéséhez rendszergazdai jogú hozzáférésre szükséges a helyi gépen. 

![Power BI Desktop – beállításjegyzék beállított harmadik féltől származó megbízható kulcsok nélkül](media/desktop-trusted-third-party-connectors/desktoptrustedthird1.png)

Adjon hozzá egy új értéket a fent megadott elérési úton. Válassza a többsztringes érték (REG_MULTI_SZ) típust, és adja neki a TrustedCertificateThumbprints nevet. 

![Power BI Desktop – beállításjegyzék beállított harmadik féltől származó megbízható csatlakozóval, de kulcsok nélkül](media/desktop-trusted-third-party-connectors/desktoptrustedthird2.png)

Adja meg azoknak a tanúsítványoknak az ujjlenyomatait, amelyeket megbízhatóként kíván beállítani. Több tanúsítvány hozzáadásához használja határolóként a 0 karaktert, vagy kattintson a jobb gombbal a beállításszerkesztőben > válassza a Módosítás elemet, és helyezze az összes ujjlenyomatot új sorba. A példán szereplő ujjlenyomat önaláírt tanúsítványból származik. 

 ![Power BI Desktop – beállításjegyzék beállított harmadik féltől származó megbízható kulccsal](media/desktop-trusted-third-party-connectors/desktoptrustedthird3.png)

Ha megfelelően követte az utasításokat, és megkapta a megfelelő ujjlenyomatot a fejlesztőjétől, most már biztonságosan beállíthatja megbízhatóként a társított tanúsítvánnyal aláírt összekötőket.

## <a name="how-to-sign-connectors"></a>Az összekötők aláírása

Ha olyan összekötője van, amelyet Önnek vagy egy fejlesztőnek alá kell írnia, erről [itt](https://docs.microsoft.com/power-query/handlingconnectorsigning) olvashat a Power Query dokumentációjában.
