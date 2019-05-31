---
title: Összekötők bővíthetősége a Power BI-ban
description: Az összekötők bővíthetősége, funkciói, biztonsági beállításai és a hitelesített összekötők
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/22/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: 16b96d91a9dd37fa8a502bbcca772438c703cb63
ms.sourcegitcommit: d88cc6a87d4ba82ad2c4d496a3634f927e4ac529
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/30/2019
ms.locfileid: "66412970"
---
# <a name="connector-extensibility-in-power-bi"></a>Összekötők bővíthetősége a Power BI-ban

A Power BI-ügyfelek és a fejlesztők kiterjesztheti az adatforrásokat, számos módon csatlakoznak. Általános adatforrások (például ODBC, OData, Oledb, Web, CSV, XML vagy JSON) és a meglévő összekötők használata. Vagy a fejlesztők, hozzon létre adatkiterjesztések néven **egyéni összekötők**, és azokat **hitelesített összekötők**.

Jelenleg engedélyezi **egyéni összekötők** egyéni kód lehetővé teheti a rendszerben szintjének használatával egy menüt, amelyben biztonságosan szabályozhatja. Kiválaszthatja az összes egyéni összekötők vagy csak a hitelesített, és a Microsoft által terjesztett összekötők a **adatok lekérése** párbeszéd.

## <a name="custom-connectors"></a>Egyéni összekötők

**Egyéni összekötők** lehetnek lehetőségek széles skáláját, és a kis méretű API-k kritikus fontosságú üzleti nagy iparág-specifikus szolgáltatások, a Microsoft nyilvánosan nem összekötő. Számos összekötő a szállító által oszlanak meg. Ha egy adott adatösszekötő szüksége van, lépjen kapcsolatba szállító.

Használata egy **egyéni összekötő**, helyezni, a  *\[dokumentumok]\\Power BI Desktop\\egyéni összekötők* mappát, és módosítsa úgy a biztonsági beállításokat a leírtak szerint a következő szakaszt.

A **hitelesített összekötők** használatához nem kell módosítania a biztonsági beállításokat.

## <a name="data-extension-security"></a>Adatkiterjesztés biztonsága

Az adatok kiterjesztése biztonsági beállítások módosításához **Power BI Desktop** kiválasztása **fájl > lehetőségek és beállítások > Beállítások > biztonsági**.

![Szabályozhatja, hogy szeretné-e az egyéni összekötők az adatok kiterjesztése biztonsági beállítások betöltése](media/desktop-connector-extensibility/data-extension-security-1.png)

Az **Adatkiterjesztések** területen két biztonsági szint közül választhat:

* (Ajánlott) Csak a tanúsítvánnyal rendelkező bővítmények betöltésének engedélyezése
* (Nem ajánlott) Bármilyen bővítmény betöltésének engedélyezése figyelmeztetés nélkül

Ha azt tervezi, hogy használatával **egyéni összekötők** vagy jelöljön kidolgoztunk, vagy egy harmadik féltől származó összekötők **"(Not Recommended) minden figyelmeztetés nélkül betölteni a bővítmény engedélyezése"** . Ez a beállítás nem ajánlott, kivéve, ha az egyéni összekötőkhöz teljesen megbízható. Mivel a kódot az itt lévő hitelesítő adatait, beleértve a HTTP-n keresztül elküldi azokat kezelni és adatvédelmi szintek figyelmen kívül.

Jelenleg a **"(ajánlott)"** biztonsági beállítást, ha a rendszer az egyéni összekötők, hibaüzenet jelenik meg, amely leírja az összekötőket, amelyek biztonsági miatt nem tölthető be.

![Egy párbeszédpanel, írja le egyéni összekötőkhöz, mely biztonsági beállításai, a ez megkülönbözteti a kis TripPin miatt nem tölthető be](media/desktop-connector-extensibility/data-extension-security-2.png)

Hárítsa el a hibát, és ezeket az összekötőket használ, módosítsa a biztonsági beállításokat a **"(Not Recommended) minden figyelmeztetés nélkül betölteni a bővítmény engedélyezése"** beállítása a korábban leírtaknak megfelelően. Ezután indítsa újra **Power BI Desktop**.

## <a name="certified-connectors"></a>Hitelesített összekötők

Adatkiterjesztések korlátozott részhalmaza számít **Certified**. A hitelesített összekötők eléréséhez a **adatok lekérése** párbeszéd. De a külső fejlesztő, aki létrehozta az összekötő feladata a karbantartási és támogatási. Bár a Microsoft elosztja az összekötők, akkor sem felelős a teljesítmény vagy a folyamatos függvény.

Ha hitelesíteni szeretne egy egyéni összekötőt, kérje meg a szállítót, hogy lépjen kapcsolatba a dataconnectors@microsoft.com képviselőivel.
