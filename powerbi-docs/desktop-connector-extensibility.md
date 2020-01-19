---
title: Összekötők bővíthetősége a Power BI-ban
description: Az összekötők bővíthetősége, funkciói, biztonsági beállításai és a hitelesített összekötők
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/02/2020
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: b604ade56335e65b25501eb9fe3d3c2fd185a6f0
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761397"
---
# <a name="connector-extensibility-in-power-bi"></a>Összekötők bővíthetősége a Power BI-ban

A Power BI meglévő összekötők és általános adatforrások (például ODBC, OData, OLE DB, Web, CSV, XML, és JSON) segítségével csatlakozhat az adatokhoz. A fejlesztők emellett engedélyezhetnek egyéni adatkiterjesztésekkel rendelkező adatforrásokat – *ezeket egyéni összekötőknek nevezzük*. Egyes egyéni összekötőket a Microsoft *hitelesített összekötőkként* minősít és terjeszt.

Az Ön vagy külső fél által fejlesztett, nem hitelesített egyéni összekötők használatához a Power BI Desktop biztonsági beállításait úgy kell konfigurálni, hogy a bővítmények ellenőrzés vagy figyelmeztetés nélkül betölthetők legyenek. Ezt a biztonsági beállítást csak akkor javasoljuk, ha teljes mértékben megbízik az egyéni összekötőkben, mivel az itt szereplő kód kezelheti a hitelesítő adatokat (beleértve azok HTTP-n való küldését), és figyelmen kívül hagyhatja az adatbiztonsági szinteket.

Alternatív megoldásként a fejlesztő aláírhatja az összekötőt egy tanúsítvánnyal, majd megadhatja Önnek a biztonsági beállítások módosítása nélküli használathoz szükséges adatokat. További információ: [Megbízható harmadik féltől származó összekötők ismertetése](desktop-trusted-third-party-connectors.md).

## <a name="custom-connectors"></a>Egyéni összekötők

A nem hitelesített összekötők kis méretű, üzleti szempontból kritikus API-któl kezdve a nagyszabású, iparágspecifikus szolgáltatásokig terjednek, amelyekhez a Microsoft nem adott ki összekötőt. Számos összekötőt szállítók szolgáltatnak. Ha egy adott adatösszekötőre van szüksége, lépjen kapcsolatba a szállítóval. 

Ha nem hitelesített egyéni összekötőt szeretne használni, helyezze az összekötő *.pq*, *.pqx*, *.m*, vagy *.mez* fájlját a *\[Documents]\\Power BI Desktop\\Custom Connectors* mappába. Ha a könyvtár nem létezik, hozza létre.

Módosítsa az alábbiak szerint az adatkiterjesztési beállításokat:

A Power BI Desktopban válassza a **Fájl** > **Lehetőségek és beállítások** > **Beállítások** > **Biztonság** lehetőséget.

Az **Adatkiterjesztések** területen válassza a **(Nem ajánlott) Bármilyen bővítmény ellenőrzés vagy figyelmeztetés nélküli betöltésének engedélyezése** lehetőséget. Válassza az **OK** gombot, majd indítsa újra a Power BI Desktopot. 

![Nem minősített egyéni összekötők engedélyezése az adatkiterjesztés biztonsági beállításaiban](media/desktop-connector-extensibility/data-extension-security-1.png)

A Power BI Desktop alapértelmezett adatkiterjesztés-biztonsági beállítása az **(Ajánlott) Csak Microsoft-tanúsítvánnyal rendelkező és egyéb megbízható harmadik féltől származó bővítmények betöltésének engedélyezése**. Ezzel a beállítással, ha nem hitelesített egyéni összekötők találhatók a rendszerén, a **Nem hitelesített összekötők** párbeszédpanel jelenik meg a Power BI Desktop indításakor, amely felsorolja a biztonságos módon nem betölthető összekötőket.

![Nem hitelesített összekötők párbeszédpanel](media/desktop-connector-extensibility/data-extension-security-2.png)

A hiba elhárításához módosítsa az **Adatkiterjesztések** biztonsági beállítást, vagy távolítsa el a nem hitelesített összekötőket a *Custom Connectors* mappából.

## <a name="certified-connectors"></a>Hitelesített összekötők

Az adatkiterjesztések egy korlátozott részhalmazát *hitelesítettnek* tekintjük. Bár a Microsoft kínál ilyen összekötőket, nem vállalunk felelősséget a teljesítményükért és a folyamatos működésükért. Az összekötő fenntartásáért és támogatásáért a külső fejlesztő felelős, aki létrehozta azt. 

A Power BI Desktopban a hitelesített külső összekötők az **Adatok lekérése** párbeszédpanel listájában jelennek meg az általános és gyakori összekötőkkel együtt. A hitelesített összekötők használatához nem kell módosítania a biztonsági beállításokat.

Ha hitelesíteni szeretne egy egyéni összekötőt, kérje meg a szállítót, hogy vegye fel a kapcsolatot a dataconnectors@microsoft.com címmel.
