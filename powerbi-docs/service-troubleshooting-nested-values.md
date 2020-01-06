---
title: Szövegként visszaadott beágyazott értékek hibaelhárítása a Power BI szolgáltatásban
description: Megtudhatja, hogyan háríthatja el a sztringgé konvertált beágyazott értékek hibáját helytelen adatforrás-védelmi beállítások használatakor
author: cpopell
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 6/4/2019
ms.author: gepopell
LocalizationGroup: Reports
ms.openlocfilehash: ab40ca9c415dacf52f4d82eb2c157d57aef92f93
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/06/2020
ms.locfileid: "73871289"
---
# <a name="troubleshooting-nested-values-returned-as-text-in-power-bi-service"></a>Szövegként visszaadott beágyazott értékek hibaelhárítása a Power BI szolgáltatásban

## <a name="cause"></a>Ok

Korábban előfordultak esetek, amelyekben a Power BI-jelentés megfelelően frissült a Desktopban, azonban ehhez hasonló hibát észlelt a Power BI szolgáltatásban: „A [Tábla] érték nem konvertálható a következő típusra: Tábla.” A hiba egyik oka, hogy amikor az Adatvédelmi tűzfal egy adatforrást pufferel, a beágyazott, nem skaláris értékek (például a táblák, rekordok, listák és függvények) automatikusan szöveges értékekké alakulnak (például [Tábla] vagy [Rekord]).

Most, hogy a Power BI szolgáltatás már támogatja az adatvédelmi szintek beállítását (vagy a tűzfal teljes kikapcsolását), az ilyen hibák elkerülhetők az [adatforrás adatvédelmi beállításainak nem privátként történő konfigurálásával](https://powerbi.microsoft.com/blog/privacy-levels-for-cloud-data-sources/) a Power BI szolgáltatásban.

A Power BI júniusi frissítésétől kezdődően amikor a tűzfal egy beágyazott táblát/rekordot/listát/egyéb elemet pufferel, az értékek csendes szöveggé alakítása helyett a következő hibaüzenet jelenik meg: 

`We cannot return a value of type Table in this context`

## <a name="effect-on-loadrefresh"></a>Hatás a betöltésre és a frissítésre

Bár a módosítás a tűzfal pufferelésére vonatkozik, annak hatása a betöltésre és a frissítésre is kiterjed. A tűzfal pufferelési eljárásának módosításához meg kellett változtatnunk a beágyazott táblák, rekordok és egyéb elemek a Power BI-modellbe és az Excel-adatmodellbe való betöltését az Excel PQ-ban. Korábban a beágyazott táblák, rekordok és egyéb elemek szöveges értékként töltődtek be (például [Tábla] vagy [Rekord]). Ezek mostantól hibának számítanak, és nullértéket eredményeznek a betöltött táblában, valamint hibaszám-növekedést a betöltési eredményekben.

Mivel ezek a hibák csak a betöltés és frissítés közben merülnek fel, a Power Query-szerkesztőben nem jelennek meg.

### <a name="before"></a>Előtte

- Betöltés és frissítés hiba nélkül
- A betöltött tábla a következőket tartalmazza: [Tábla], [Rekord], és hasonlók
 

### <a name="after"></a>Utána

- Betöltés és frissítés hibával
- A betöltött tábla nullértékeket tartalmaz (a [Tábla], [Rekord], és hasonlók helyett)
 

## <a name="resolution"></a>Megoldás

Nem skaláris értékeket (táblákat, listákat, rekordokat és hasonlókat) tartalmazó oszlopot szeretne betölteni?
Ha igen, az oszlop eltávolításával megszüntetheti a hibát.
Ha nem tudja eltávolítani az oszlopot, replikálhatja a régi viselkedést egy egyéni oszlop hozzáadásával, és a következő mintához hasonló logikával:

`if [MyColumn] is table then "[Table]" else if [MyColumn] is record then "[Record]" else if [MyColumn] is list then "[List]" else if [MyColumn] is function then "[Function]" else [MyColumn]`

A hiba a Power BI Desktopban is megjelenik, ha minden adatforrás-védelmi beállítást privátra állít?
Ha igen, megoldhatja a problémát, ha a Power BI szolgáltatásban nem privátként [konfigurálja az adatforrás-védelmi beállításokat](https://powerbi.microsoft.com/blog/privacy-levels-for-cloud-data-sources/).
