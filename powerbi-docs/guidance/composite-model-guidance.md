---
title: Útmutató a Power BI Desktopbeli Összetett modellekhez
description: Útmutató Összetett modellek kialakításához.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/24/2019
ms.author: v-pemyer
ms.openlocfilehash: fa9ecd66d30839e169252065f7f736189b71b6ce
ms.sourcegitcommit: 8b300151b5c59bc66bfef1ca2ad08593d4d05d6a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/30/2020
ms.locfileid: "76889480"
---
# <a name="composite-model-guidance-in-power-bi-desktop"></a>Útmutató a Power BI Desktopbeli Összetett modellekhez

Ez a cikk azoknak az adatmodellezőknek szól, akik Összetett Power BI-modelleket fejlesztenek. Bemutatja az Összetett modellek használati eseteit, és útmutatást nyújt a tervezésükhöz. Az útmutató segít eldönteni, hogy egy Összetett modell megfelelő-e egy adott megoldáshoz. Ha az, akkor a cikk egy optimális modell megtervezéséhez is segítséget nyújt.

> [!NOTE]
> A cikknek nem tárgya az Összetett modellek bemutatása. Ha nem ismeri jól az Összetett modelleket, ajánlott előbb az [Összetett modellek használata a Power BI Desktopban](../desktop-composite-models.md) című cikket elolvasnia.
>
> Mivel az Összetett modellek legalább egy DirectQuery-forrást is tartalmaznak, fontos alaposan megismernie a [modellek közötti kapcsolatokat](../desktop-relationships-understand.md), a [DirectQuery-modelleket](../desktop-directquery-about.md) és a [DirectQuery-modellek tervezéséhez elérhető útmutatást](directquery-model-guidance.md).

## <a name="composite-model-use-cases"></a>Összetett modellek használati esetei

Ha csak lehetséges, a modelleket legjobb Importálás módban fejleszteni. Ez a mód kínálja a legnagyobb fejlesztési rugalmasságot és a legjobb teljesítményt.

A nagy adattömegekkel vagy a közel valós idejű jelentéskészítéssel kapcsolatos nehézségek azonban nem küzdhetők le Importálás módú modellekkel. Ezekben az esetekben megfontolható egy DirectQuery módú modell használata, feltéve, hogy az adatok egyetlen, [a DirectQuery mód által támogatott](../power-bi-data-sources.md) adatforrásban találhatók.

Ezen kívül az alábbi helyzetekben mérlegelheti egy Összetett modell kifejlesztését is.

- Lehet, hogy a modellje DirectQuery módú, de szeretné fokozni annak teljesítményét. Összetett modellekben a teljesítmény az egyes tábláknak megfelelő tárolók konfigurálásával javítható. Felvehet [összesítéseket](../desktop-aggregations.md) is. Mindkét optimalizálásról szó lesz a cikk későbbi részében.
- Olyan további adatokkal szeretne kombinálni egy DirectQuery modellt, amelyeket a modellbe kell importálni. Az importált adatok betölthetők más adatforrásból vagy számított táblákból.
- Kettő vagy több DirectQuery-adatforrást szeretne egyetlen modellben kombinálni.

> [!NOTE]
> Az Összetett modellekbe nem építhetők be Élő kapcsolatú források vagy DirectQuery módú analitikai adatbázis-források. Élő kapcsolatú források például a [külső üzemeltetésű modellek](../service-datasets-understand.md#external-hosted-models) és a Power BI-adathalmazok. DirectQuery analitikai adatbázis-forrás például az SAP Business Warehouse és az SAP HANA.

## <a name="optimize-model-design"></a>Modelltervek optimalizálása

Az Összetett modellek a táblák [tárolási módjának](../desktop-storage-mode.md) konfigurálásával és [összesítések](../desktop-aggregations.md) felvételével optimalizálhatók.

### <a name="table-storage-mode"></a>Táblaalapú tárolási mód

Összetett modellben (a számított táblák kivételével) minden tábla tárolási módja külön konfigurálható:

- **DirectQuery**: Ennek a módnak a beállítása olyan táblákhoz ajánlott, amelyek nagy mennyiségű adatot tartalmaznak, vagy közel valós idejű eredményeket kell szolgáltatniuk. Ezekbe a táblákba soha nem lesznek importálva az adatok. Ezek a táblák általában tény típusú – összegzéshez használt – táblák.
- **Importálás**: Ennek a módnak a beállítása dimenzió típusú – szűréshez és csoportosításhoz használt – táblákhoz ajánlott. Valójában ez az egyetlen lehetőség olyan táblák esetén, amelyek a DirectQuery által nem támogatott forrásokon alapulnak. A számított táblák mindig Importálás módúak.
- **Kettős**: Ez a mód dimenzió típusú táblákhoz ajánlott akkor, ha fennáll a lehetőség, hogy DirectQuery módú ténytáblákkal egyszerre lesznek lekérdezve ugyanabból a forrásból.

A Power BI többféle helyzetben kérdezhet le egy Összetett modellt:

- **Csak Importálás vagy Kettős táblá(ka)t kérdez le**: Minden adat a modell gyorsítótárából van beolvasva. Ez nyújtja a lehető leggyorsabb teljesítményt. Ez a helyzet gyakori a szűrők vagy szeletelő vizualizációk által lekérdezett dimenziótáblák esetén.
- **Kettős módú táblá(ka)t vagy DirectQuery módú táblá(ka)t kérdez le ugyanabból a forrásból**: Az összes adat egy vagy több, a DirectQuery-forráshoz küldött lekérdezéssel van beolvasva. Ezzel érhető el a leggyorsabb működés, különösen akkor, ha a forrástáblákban léteznek a megfelelő indexek. Ez a helyzet a Kettős módú dimenziótáblákat és DirectQuery módú ténytáblákat összekapcsoló lekérdezések esetén gyakori. Ezek úgynevezett _szigeten belüli_ lekérdezések, tehát minden egy az egyhez vagy egy a többhöz kapcsolat [erős kapcsolatként](../desktop-relationships-understand.md#strong-relationships) van kiértékelve.
- **Minden más lekérdezés**: Az ilyen lekérdezések szigetek közötti kapcsolatokat is használnak. Ennek vagy az az oka, hogy egy Importálás módú tábla kapcsolódik egy DirectQuery-táblához, vagy hogy egy Kettős módú tábla kapcsolódik egy másik forrásban lévő DirectQuery-táblához – ilyen esetben Importálás módú táblaként viselkedik. Minden kapcsolat [gyenge kapcsolatként](../desktop-relationships-understand.md#weak-relationships) van kiértékelve. Ez azzal is jár, hogy a nem DirectQuery módú táblákra alkalmazott csoportosításokat virtuális táblaként kell elküldeni a DirectQuery-forrásnak. Ilyen esetben a natív lekérdezés nem mindig hatékony, különösen nagy csoportosítási halmazok esetén. Az a lehetőség is fennáll, hogy bizalmas adatokat tesz elérhetővé a natív lekérdezésben.

Összefoglalva, a következőket javasoljuk:

- Gondolja át alaposan, hogy az Összetett modell-e a megfelelő megoldás – bár lehetővé teszi a különböző adatforrások modellszintű integrálását, olyan tervezési bonyodalmakkal is jár, amelyeknek súlyos következményei lehetnek
- Akkor állítson be **DirectQuery** tárolási módot, ha a tábla nagy mennyiségű adatot tartalmazó ténytábla, vagy ha közel valós idejű eredményeket kell szolgáltatnia
- **Kettős** tárolási módot dimenzió típusú táblához állítson be, ha az **DirectQuery** módú ténytáblákkal együtt lesz lekérdezve, amelyek ugyanazon a forráson alapulnak
- Konfigurálja a megfelelő frissítési gyakoriságot, hogy a modell Kettős módú táblákhoz (és minden azoktól függő számított táblához) tartozó gyorsítótárát szinkronban tartsa az egy vagy több forrás-adatbázissal
- Törekedjen az adatok integritásának biztosítására az összes adatforrásban (a modell gyorsítótárát is beleértve) – a gyenge kapcsolatok eltüntetik a sorokat, ha a kapcsolódó oszlopok értékei nem egyeznek
- A hatékony összekapcsolások, szűrés és csoportosítás érdekében optimalizálja a DirectQuery-adatforrásokat a megfelelő indexekkel
- Nem töltsön be bizalmas adatokat Importálás vagy Kettős módú táblákba, ha fennáll egy natív lekérdezés elfogásának kockázata. További információ: [Összetett modellek használata a Power BI Desktopban (Biztonsági vonatkozások)](../desktop-composite-models.md#security-implications)

### <a name="aggregations"></a>Összesítések

Az Összetett modellben összesítéseket vehet fel DirectQuery-táblákhoz. Az összesítések a modellben vannak gyorsítótárazva, ezért Importálás módú táblákként viselkednek (modelltáblaként azonban nem használhatók). A rendeltetésük a „kevésbé részletes” lekérdezések teljesítményének javítása. További információ: [Összesítések a Power BI Desktopban](../desktop-aggregations.md).

Ajánlott betartani egy, az összesítő táblákra vonatkozó alapszabályt: A sorok száma legyen egy 10-es nagyságrenddel kisebb, mint a mögöttes táblában. Ha a mögöttes tábla például 1 milliárd sort tárol, akkor az összesítő tábla ne legyen nagyobb 100 millió sornál. Ez a szabály biztosítja az összesítő tábla létrehozásának és fenntartásának költségéhez viszonyítva elfogadható teljesítménynövekedést.

## <a name="next-steps"></a>Következő lépések

Ezzel a cikkel kapcsolatosan a következő forrásanyagokban talál további információt:

- [Összetett modellek használata a Power BI Desktopban](../desktop-composite-models.md)
- [Modellbeli kapcsolatok a Power BI Desktopban](../desktop-relationships-understand.md)
- [DirectQuery-modellek a Power BI Desktopban](../desktop-directquery-about.md)
- [A DirectQuery használata a Power BI Desktopban](../desktop-use-directquery.md)
- [DirectQuery-modell hibaelhárítása a Power BI Desktopban](../desktop-directquery-troubleshoot.md)
- [Adatforrások a Power BI-hoz](../power-bi-data-sources.md)
- [Tárolási mód a Power BI Desktopban](../desktop-storage-mode.md)
- [Összesítések a Power BI Desktopban](../desktop-aggregations.md)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
- Javaslatai vannak? [A Power BI javítására vonatkozó ötletek beküldése](https://ideas.powerbi.com)
