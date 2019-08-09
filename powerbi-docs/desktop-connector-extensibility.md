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
ms.openlocfilehash: 7d5d743dda31d05df0beb528648c5a43ffc6b335
ms.sourcegitcommit: 32a44dd17a44ccfd4a2d86a0d235251c2fda1c5c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68702113"
---
# <a name="connector-extensibility-in-power-bi"></a>Összekötők bővíthetősége a Power BI-ban

A Power BI felhasználói és fejlesztői számos módon kiterjeszthetik az adatforrásokat, amelyekhez csatlakozhatnak. Meglévő összekötőket és általános adatforrásokat (például ODBC, OData, Oledb, Web, CSV, XML, JSON) használhatnak. A fejlesztők emellett adatkiterjesztéseket hozhatnak létre (más néven **egyéni összekötőket**), ezekből pedig **hitelesített összekötőket** készíthetnek.

Az **egyéni összekötők** jelenleg egy olyan menüben engedélyezhetők, amelyekkel biztonságosan vezérelhetők a rendszerben futtatni kívánt egyéni kódok. Az **Adatok lekérése** párbeszédpanelen kiválaszthatja az összes összekötőt vagy csak a Microsoft-összekötőket.

## <a name="custom-connectors"></a>Egyéni összekötők

Az **egyéni összekötők** számos lehetőséget hordoznak magukban a kis méretű, üzleti szempontból kritikus API-któl kezdve a nagyszabású, iparágra jellemző szolgáltatásokig, amelyekhez a Microsoft nem adott ki összekötőt. Számos összekötőt szállítók szolgáltatnak. Így ha Önnek egy adott adatösszekötőre van szüksége, célszerű a szállítóval felvennie a kapcsolatot.

**Egyéni összekötők** használatához helyezze őket a *\[Dokumentumok]\\Power BI Desktop\\Egyéni összekötők* mappába, majd a következő szakaszban ismertetettek szerint módosítsa a biztonsági beállításokat.

A **hitelesített összekötők** használatához nem kell módosítania a biztonsági beállításokat.

## <a name="data-extension-security"></a>Adatkiterjesztés biztonsága

Az adatkiterjesztések beállításainak módosításához a **Power BI Desktopban** válassza a **Fájl > Lehetőségek és beállítások > Lehetőségek > Biztonság** elemet.

![Annak szabályozása, hogy betölthet-e adatkiterjesztési biztonsági beállításokkal rendelkező egyéni összekötőket](media/desktop-connector-extensibility/data-extension-security-1.png)

Az **Adatkiterjesztések** területen két biztonsági szint közül választhat:

* (Ajánlott) Csak a tanúsítvánnyal rendelkező bővítmények betöltésének engedélyezése
* (Nem ajánlott) Bármilyen bővítmény betöltésének engedélyezése figyelmeztetés nélkül

Ha **egyéni összekötőket** vagy olyan összekötőket szeretne használni, amelyeket Ön vagy egy külső fél fejlesztett, válassza a **„(Nem ajánlott) Bármilyen bővítmény betöltésének engedélyezése figyelmeztetés nélkül”** lehetőséget. Nem javasoljuk ezt a biztonsági beállítást, hacsak nem bízik meg teljes mértékben az egyéni összekötőkben. Ez azért van, mert az itteni kód képes kezelni a hitelesítő adatokat – beleértve azok HTTP-n keresztüli küldését is –, és figyelmen kívül hagyni az adatvédelmi szinteket.

Az **„(Ajánlott)”** biztonsági beállításban, ha egyéni összekötőket használ a rendszer, a „The following connector has not been certified, and we are unable to verify that is secure to use” (A következő összekötő nincs hitelesítve, ezért nem biztonságos a használata) hibaüzenet jelenik meg, amelyet a biztonságosan betölthető összekötők listája követ.

![Egy párbeszédpanel ismerteti azokat az egyéni összekötőket, amelyek biztonsági okokból nem tölthetők be, ebben az esetben a TripPint](media/desktop-connector-extensibility/data-extension-security-2.png)

A probléma a biztonság módosítása nélküli megoldásához távolítsa el a nem aláírt összekötőket az „Egyéni összekötők” mappából.

A hiba elhárításához és az összekötők használatához módosítsa a biztonsági beállításokat a **„(Nem ajánlott) Bármilyen bővítmény betöltésének engedélyezése figyelmeztetés nélkül”** beállításra a korábban ismertetett módon. Ezután indítsa újra a **Power BI Desktopot**.

## <a name="certified-connectors"></a>Hitelesített összekötők

Az adatkiterjesztések egy korlátozott részhalmazát **hitelesítettnek** tekintjük. A hitelesített összekötőket az **Adatok lekérése** párbeszédpanelen érheti el. Az összekötő fenntartásáért és támogatásáért azonban a külső fejlesztő felelős, aki létrehozta azt. Bár a Microsoft kínál ilyen összekötőket, nem vállalunk felelősséget a teljesítményükért és a folyamatos működésükért.

Ha hitelesíteni szeretne egy egyéni összekötőt, kérje meg a szállítót, hogy lépjen kapcsolatba a dataconnectors@microsoft.com képviselőivel.
