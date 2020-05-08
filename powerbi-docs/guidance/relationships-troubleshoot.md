---
title: Kapcsolatok hibaelhárítási útmutatója
description: Útmutató a modellkapcsolati problémák elhárításához.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/02/2020
ms.author: v-pemyer
ms.openlocfilehash: e2854d82d858bb1963b691d32d561c7b3bbfc11a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "78263645"
---
# <a name="relationship-troubleshooting-guidance"></a>Kapcsolatok hibaelhárítási útmutatója

Ez a cikk a Power BI Desktopot használó adatmodellezőknek szól. Útmutatást nyújt a modellek és jelentések fejlesztése során esetlegesen felmerülő problémák elhárításához.

[!INCLUDE [relationships-prerequisite-reading](includes/relationships-prerequisite-reading.md)]

## <a name="troubleshooting-checklist"></a>Hibaelhárítási ellenőrzőlista

Ha egy jelentésvizualizáció két (vagy több) tábla mezőinek használatára van konfigurálva, és nem a megfelelő eredményt mutatja (vagy egyáltalán nem mutat eredményt), lehetséges, hogy a probléma a modellkapcsolatokban van.

Ebben az esetben kövesse a következő általános hibaelhárítási ellenőrzőlistát. A problémák azonosítása érdekében fokozatosan haladjon végig az ellenőrzőlistán.

1. Váltsa a vizualizációt egy táblára vagy mátrixra, vagy nyissa meg az „Adatok megjelenítése” panelt – a hibaelhárítás könnyebb, ha látja a lekérdezés eredményét
1. Ha üres lekérdezési eredményt lát, váltson adatnézetre, és ellenőrizze, hogy a táblák fel vannak-e töltve adatsorokkal
1. Váltson modellnézetre – könnyen láthatja a kapcsolatokat, és gyorsan meghatározhatja azok tulajdonságait
1. Ellenőrizze, hogy léteznek-e kapcsolatok a táblák között
1. Ellenőrizze, hogy a számossági tulajdonságok megfelelően vannak-e konfigurálva – ha egy „több” oldali oszlop jelenleg egyedi értékeket tartalmaz, és helytelenül „egy” oldaliként lett konfigurálva, ezek a tulajdonságok hibásak lehetnek
1. Ellenőrizze, hogy a kapcsolatok aktívak-e (folytonos vonal)
1. Ellenőrizze, hogy a szűrési irányok támogatják-e a propagálást (a nyílhegyek értelmezésével)
1. Ellenőrizze, hogy a megfelelő oszlopok vannak-e összekapcsolva – ehhez válassza ki a kapcsolatot, vagy vigye fölé a kurzort a kapcsolódó oszlopok megjelenítéséhez
1. Ellenőrizze, hogy a kapcsolódó oszlopok adattípusai azonosak, vagy legalábbis kompatibilisek – szöveges oszlop is összekapcsolható egész számokat tartalmazó oszloppal, a szűrők azonban így nem találnak propagálható egyezéseket
1. Váltson adatnézetre, és ellenőrizze, hogy vannak-e egyező értékek a kapcsolódó oszlopokban

## <a name="troubleshooting-guide"></a>Hibaelhárítási útmutató

Íme egy lista a hibákról és a lehetséges megoldásokról.

|Probléma|Lehetséges ok(ok)|
|---------|---------|
|A vizualizáció nem jelenít meg eredményt|– A modellbe nincsenek betöltve adatok<br />– A szűrő kontextusában nem találhatók adatok<br />– Kényszerítve van a sorszintű biztonság<br />– A kapcsolatok nem propagálnak a táblák között – _kövesse a fenti ellenőrzőlistát_<br />– Kényszerítve van a sorszintű biztonság, azonban nincs engedélyezve a kétirányú kapcsolat propagálása – lásd: [Sorszintű biztonság (RLS) a Power BI Desktoppal](../desktop-rls.md)|
|A vizualizáció ugyanazt az értéket jeleníti meg minden csoportosításhoz |– A kapcsolatok nem léteznek<br />– A kapcsolatok nem propagálnak a táblák között – _kövesse a fenti ellenőrzőlistát_|
|A vizualizáció megjelenít eredményeket, ezek azonban helytelenek|– A vizualizáció helytelenül van konfigurálva<br />– A mérték logikája helytelen<br />– Frissíteni kell a modelladatokat<br />– A forrásadatok helytelenek<br />– A kapcsolati oszlopok helytelenül kapcsolódnak egymáshoz (például a **ProductID** a **CustomerID** oszlopra van leképezve)<br />– Két DirectQuery-tábla közti kapcsolat esetén a kapcsolat „egy” oldali oszlopa ismétlődő értékeket tartalmaz|
|ÜRES csoportosítások vagy szeletelő-/szűrőelemek jelennek meg, a forrásoszlopok pedig nem tartalmaznak ÜRES értéket|– Erős kapcsolat, ahol a „több” oldali oszlop olyan értékeket tartalmaz, amelyek nem az „egy” oldali oszlopban vannak tárolva – lásd: [Modellbeli kapcsolatok a Power BI Desktopban (erős kapcsolatok)](../desktop-relationships-understand.md#strong-relationships)<br />– Erős egy az egyhez típusú kapcsolat, ahol a kapcsolódó oszlopok ÜRES értékeket tartalmaznak – lásd: [Modellbeli kapcsolatok a Power BI Desktopban (erős kapcsolatok)](../desktop-relationships-understand.md#strong-relationships)<br />– Egy inaktiválási kapcsolat „több” oldali oszlopa ÜRES értékeket tárol, vagy olyan értékeket tartalmaz, amelyek nincsenek az „egy” oldalon tárolva|
|A vizualizációból adatok hiányoznak|– Helytelen/nem várt szűrők vannak alkalmazva<br />– Kényszerítve van a sorszintű biztonság<br />– Gyenge kapcsolat, ahol ÜRES értékek találhatók a kapcsolódó oszlopokban, vagy adatintegritási hibák lépnek fel – lásd: [Modellbeli kapcsolatok a Power BI Desktopban (gyenge kapcsolatok)](../desktop-relationships-understand.md#weak-relationships)<br />– Két DirectQuery-tábla közötti kapcsolat, amely [hivatkozási integritás feltételezéséhez](../desktop-relationships-understand.md#assume-referential-integrity) van konfigurálva, azonban adatintegritásbeli problémák adódtak (nem egyező értékek a kapcsolódó oszlopokban)|
|A sorszintű biztonság nincs megfelelően kényszerítve|– A kapcsolatok nem propagálnak a táblák között – _kövesse a fenti ellenőrzőlistát_<br />– Kényszerítve van a sorszintű biztonság, azonban nincs engedélyezve a kétirányú kapcsolat propagálása – lásd: [Sorszintű biztonság (RLS) a Power BI Desktoppal](../desktop-rls.md)|
|||

## <a name="next-steps"></a>További lépések

Ezzel a cikkel kapcsolatosan a következő forrásanyagokban talál további információt:

- [Modellbeli kapcsolatok a Power BI Desktopban](../desktop-relationships-understand.md)
- Kérdései vannak? [Kérdezze meg a Power BI-közösséget](https://community.powerbi.com/)
- Javaslatai vannak? [A Power BI javítására vonatkozó ötletek beküldése](https://ideas.powerbi.com/)
