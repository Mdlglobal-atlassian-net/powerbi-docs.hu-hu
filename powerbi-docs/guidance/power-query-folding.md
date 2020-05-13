---
title: Útmutató lekérdezésdelegáláshoz a Power BI Desktopban
description: Útmutató Power Query lekérdezések átadásának megvalósításához a Power BI Desktopban.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/09/2019
ms.author: v-pemyer
ms.openlocfilehash: 271ccd9abcba8fe75f0ad66a88cb970584855a35
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83149172"
---
# <a name="query-folding-guidance-in-power-bi-desktop"></a>Útmutató lekérdezésdelegáláshoz a Power BI Desktopban

Ez a cikk azoknak az adatmodellezőknek szól, akik modelleket fejlesztenek a Power BI Desktopban. Útmutatást nyújt arról, hogy mikor és hogyan valósítható meg a Power Query lekérdezések átadása.

A _lekérdezésátadás_ a Power Query-lekérdezéseknek az a képessége, hogy egyetlen lekérdezési utasítást generál a forrásadatok lekéréséhez és átalakításához. További információ: [Power Query lekérdezésdelegálás](/power-query/power-query-folding).

## <a name="guidance"></a>Útmutató

A lekérdezésdelegáláshoz nyújtott útmutatás a modell módjától függően különböző.

A Power Query-lekérdezésnek **DirectQuery** vagy **Kettős** tárolási módú táblák esetén meg kell valósítania a lekérdezésátadást.

**Importálás** módú tábla esetén lehetséges lehet a lekérdezésátadás. Relációs forráson alapuló lekérdezés esetén, vagy ha egyetlen SELECT utasítás írható, a _legjobb adatfrissítési teljesítmény_ a lekérdezésátadás megvalósulásának biztosításával érhető el. Ha az Power Query adategyesítő motorja továbbra is szükséges az átalakítások feldolgozásához, akkor az általa elvégzendő munka minimálisra csökkentése a cél, főleg nagy adathalmazok esetében.

Az alábbi felsorolás részletes útmutatást ad.

- **A lehető legtöbb feldolgozási feladat adatforráshoz delegálása**: Ha egy Power Query-lekérdezés összes lépése nem adható át, keresse meg a lekérdezésátadást megakadályozó lépést. Ha lehetséges, helyezze át az ezt követő lépéseket a sor korábbi szakaszába, hogy be lehessen foglalni a lekérdezésátadásba. Érdemes tudni, hogy a Power Query adategyesítési motorja elég intelligens lehet a lekérdezési lépések átrendezéséhez a forráslekérdezés létrehozásakor.

    Relációs adatforrás esetén, ha a lekérdezésátadást megakadályozó lépések megvalósíthatók egyetlen SELECT utasítással vagy egy tárolt eljárás belső logikájával, érdemes megfontolni az alábbiakban ismertetett natív SQL-lekérdezés használatát.

- **Natív SQL-lekérdezés használata**: Ha egy Power Query-lekérdezés relációs forrásból fogad adatokat, bizonyos források esetén natív SQL-lekérdezés is használható. A lekérdezés bármilyen érvényes utasítás, akár egy tárolt eljárás végrehajtása is lehet. Ha az utasítás több eredményhalmazt állít elő, csak az első lesz visszaadva. Paraméterek deklarálhatók az utasításon belül, emellett ajánlott a [Value.NativeQuery](/powerquery-m/value-nativequery) M-függvényt használni. Ez a függvény a paraméterértékek biztonságos és kényelmes átadására lett tervezve. Fontos tisztában lenni azzal, hogy a Power Query adategyesítő motorja nem tud későbbi lekérdezési lépéseket átadni, ezért érdemes az összes (vagy a lehető legtöbb) átalakítási logikát belefoglalni a natív lekérdezési utasításba.

    Natív SQL-lekérdezések használatakor két lényeges szempontot kell szem előtt tartania:

    - DirectQuery módú modelltábla esetén a lekérdezésnek egy SELECT utasításnak kell lennie, és nem használhat közös táblakifejezéseket (CTE-ket) vagy tárolt eljárásokat.
    - Növekményes frissítés nem használhat natív SQL-lekérdezést. Ilyen esetben a Power Query adategyesítő motornak kellene lekérnie a forrás összes sorát, majd szűrők alkalmazásával felismernie a növekményes módosításokat.

    > [!IMPORTANT]
    > Egy natív SQL-lekérdezéssel az adatok lekérésénél több is végrehajtható. Bármely érvényes utasítást (többször is) végrehajthat, akár olyanokat is, amelyek adatokat módosítanak vagy törölnek. Fontos a legalacsonyabb jogosultság elvének alkalmazásával biztosítani, hogy az adatbázis eléréséhez használt fiók csak olvasási engedéllyel rendelkezzen a szükséges adatokhoz.

- **Az adatok előkészítése és átalakítása a forrásban**: Ha azt állapítja meg, hogy egy Power Query-lekérdezés bizonyos lépései nem adhatók át, az átalakítások végrehajthatók lehetnek az adatforrásban. Az átalakítások megvalósíthatók lehetnek egy olyan adatbázisnézet megírásával, amely logikusan alakítja át a forrásadatokat. Egy másik megoldás lehet az adatok fizikai előkészítése és materializálása, mielőtt a Power Query lekérdezné azokat. Az általában vállalati adatok előre integrált forrásaiból álló relációs adattárházak kitűnő példái az előkészített adatoknak.

## <a name="next-steps"></a>Következő lépések

Erről a cikkről a következő forrásanyagokban talál további információt:

- Power Query [Lekérdezésdelegálás](/power-query/power-query-folding) elméleti cikk
- [Növekményes frissítés a Power BI Premium szolgáltatásban](../admin/service-premium-incremental-refresh.md)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
