---
title: A Power BI-vizualizáció működési elve
description: A cikk azt ismerteti, hogyan integrálódik a vizualizáció a Power BI-jal
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 36742917829013a6efca9d74f88b01bc686437a8
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/02/2019
ms.locfileid: "74700846"
---
# <a name="power-bi-visual-concept"></a>A Power BI-vizualizáció működési elve

Ez a cikk elmagyarázza, hogy a felhasználó és a vizualizáció hogyan kommunikál a Power BI-jal, és hogyan kommunikál a felhasználó a Power BI-vizualizációval. A diagramon láthatja, hogy mely műveletek befolyásolják közvetlenül a vizualizációt vagy érvényesülnek a Power BI-on keresztül (például a felhasználó könyvjelzőket választ).

![Power BI-vizualizáció](./media/visual-concept.svg)

## <a name="the-visual-gets-update-from-power-bi"></a>A vizualizáció a Power BI-ról frissül

A vizualizáció `update` metódussal rendelkezik, és ez a metódus általában tartalmazza a vizualizáció fő logikáját, és felelős a diagram vagy az adat megjelenítéséért.

Az `update` metódus hívásában több frissítés is szerepet játszik.

### <a name="user-interacts-with-visual-through-power-bi"></a>A felhasználó a vizualizáción keresztül kommunikál Power BI-jal

* A felhasználó megnyitja a vizualizáció tulajdonságainak paneljét.

    A Power BI beolvassa a támogatott objektumokat és tulajdonságokat a vizualizáció `capabilities.json` fájljából, és a tulajdonságok tényleges értékeinek fogadásához a Power BI hívja a vizualizáció `enumerateObjectInstances` metódusát.

    A vizualizációnak a tulajdonságok tényleges értékeit kell visszaadnia.

    További információért [olvasson a vizuális képességekről](capabilities.md).

* [A felhasználó módosítja a vizualizáció tulajdonságát](../../visuals/power-bi-visualization-customize-title-background-and-legend.md) a formátum panelen.

    Egy tulajdonság értékének módosítása után a Power BI meghívja a vizualizáció `update` metódusát, és a frissítési metódusba továbbítja az új `options` tulajdonságot az objektumok új értékeivel.

    További információért [olvasson a vizualizáció objektumairól és tulajdonságairól](objects-properties.md).

* A felhasználó átméretezi a vizualizációt.

    Amikor a felhasználó megváltoztatja a vizualizáció méretét, a Power BI meghívja az `update` metódust az új `option` objektummal. A beállítások beágyazott `viewport` objektummal rendelkeznek a vizualizáció új szélességével és magasságával.

* A felhasználó jelentést, oldalt vagy vizualizációs szintű szűrőt alkalmaz.

    A Power BI a szűrési feltételek alapján szűri az adatokat, és meghívja a vizualizáció `update` metódusát, hogy új adatokat adjon át a vizualizációnak.

    A vizualizáció megkapja az `options` új frissítését az egyik beágyazott objektumban lévő új adattal. Ez a vizualizáció adatnézet-leképezési konfigurációjától függ.

    További információért [olvasson az adatnézet-leképezésekről](dataview-mappings.md).

* A felhasználó a jelentés egy másik vizualizációjában kiválasztja az adatpontot.

    A Power BI kiszűri vagy kiemeli a kijelölt adatpontokat, és meghívja a vizualizáció `update` metódusát.

    A vizualizáció megkapja az új szűrt adatokat vagy ugyanazokat az adatokat a kiemelések tömbjével.

    További információért [olvassa el, hogy lehet kiemelni az adatokat a vizualizációkban](highlight.md).

* A felhasználó kiválasztja a könyvjelzőt a jelentés könyvjelzők paneljén.

    Ekkor kétféle művelet végrehajtása történhet:

    1. A Power BI meghívja a `registerOnSelectionCallback` metódussal a regisztráción átesett függvényt, és a visszahívási függvény megkapja a kijelölések tömbjeit a megfelelő könyvjelzőhöz.

    2. A Power BI meghívja az `update` metódust a megfelelő szűrőobjektummal az `options` tulajdonságban.

    A vizualizációnak mindkét esetben módosítania kell a vizualizáció állapotát a kapott kijelöléseknek vagy szűrőobjektumoknak megfelelően.

    A könyvjelzőkről további részletekért [olvassa el, hogyan kezelheti a könyvjelzőket](filter-api.md).

    A szűrőkről további információért [olvassa el, hogyan tudják szűrni a Power BI-vizualizációk a más vizualizációkban található adatokat](filter-api.md).

### <a name="user-interacts-with-visual-directly"></a>A felhasználó közvetlenül lép interakcióba a vizualizációval

* A felhasználó az egérmutatót az adatelemre viszi

    A vizualizáció további információt jeleníthet meg az adatpontról a Power BI Elemleírások API-jával.
    A felhasználó a vizuális elemre viszi az egérmutatót, a vizualizáció képes kezelni az eseményt, és megjeleníti az adatokat az elemleírásban.

    A vizualizáció képes megjeleníteni a standard elemleírást vagy a jelentési oldal elemleírását.

    További információért olvassa el a [elemleírások hozzáadásának módjáról](add-tooltips.md) az útmutatót.

* A felhasználó módosítja a vizualizáció tulajdonságait (például a felhasználó kibontja a fát, és a vizualizáció menti az állapotot a tulajdonságokban)

    A vizualizáció mentheti a tulajdonságok értékeit a Power BI API-n keresztül. Például, amikor a felhasználó kommunikál a vizualizációval. A vizualizációnak mentenie vagy frissítenie kell a tulajdonságok értékeit. Ehhez a vizualizáció meghívhatja a `presistProperties` metódust.

* A felhasználó rákattint egy URL-hivatkozásra.

    Alapértelmezés szerint a vizualizáció megnyithatja az URL-címet. Az URL új lapon történő megnyitásához a vizualizációnak a `launchURL` metódust kell hívnia, és paraméterként kell átadnia az URL-címet.

    További információ az [URL indítása API-ról](launch-url.md).

* A felhasználó szűrőt alkalmaz a vizualizáción keresztül

    A vizualizáció az `applyJSONFilter` metódust hívja, és átadja a szűrési feltételeket a szűrőnek más vizualizációkban történő szűréshez.

    A vizualizáció többféle szűrési típust is használhat, például alapszintű szűrőt, speciális szűrőt rekordszűrőt.

    A szűrőkről további információért [olvassa el, hogyan tudják szűrni a Power BI-vizualizációk a más vizualizációkban található adatokat](filter-api.md).

* A felhasználó rákattint az elemekre a vizualizáción, illetve kijelöli azokat.

    A kijelölésekről további információért [olvassa el, hogyan kommunikálnak a vizualizációk](selection-api.md).

### <a name="the-visual-interacts-with-power-bi"></a>A vizualizáció a Power BI-jal kommunikál

* A vizualizáció további adatokat kér a Power BI-tól.

    A vizualizáció képes feldolgozni az adatok soron következő részeit. A FetchMoreData API-metódus az adathalmaz következő részét kéri.

    A `fetchMoreData` metódusról további információért [olvassa el, hogyan kérhet le további adatokat a Power BI-ból](fetch-more-data.md)

* Eseményszolgáltatás

    A Power BI exportálhatja a jelentéseket PDF-fájlba, vagy elküldheti e-mailben (csak a tanúsítvánnyal rendelkező vizualizációk támogatottak). A vizualizáció az Események renderelése API hívásával értesíti a Power BI-t a megjelenítésre való előkészítés befejeződéséről, és arról, hogy készen áll a PDF-fájl/e-mail rögzítésére.

    További információért [olvasson a jelentések Power BI-ból PDF-fájlba történő exportálásáról](../../consumer/end-user-pdf.md)

    További [információ az eseményszolgáltatásról](event-service.md)

## <a name="next-steps"></a>Következő lépések

Ön olyan webfejlesztő, aki szeretne saját vizualizációkat létrehozni, és hozzáadni azokat az AppSource-hoz? A [Power BI-vizualizáció fejlesztése](./custom-visual-develop-tutorial.md) című cikkből megtudhatja, hogyan [tehet közzé Power BI-vizualizációkat az AppSource-on](../office-store.md).
