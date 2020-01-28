---
title: A Power BI-vizualizációkkal kapcsolatos fogalmak
description: A cikk azt ismerteti, hogyan integrálhatók a vizualizációk a Power BI-jal, és hogy hogyan használhatja a felhasználó a vizualizációkat a Power BI-ban.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: bb0834527ba23c6cfcc155cc65cd0318b296ba84
ms.sourcegitcommit: 052df769e6ace7b9848493cde9f618d6a2ae7df9
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/14/2020
ms.locfileid: "75925593"
---
# <a name="visuals-in-power-bi"></a>Vizualizációk a Power BI-ban

A cikk azt ismerteti, hogyan integrálhatók a vizualizációk a Power BI-jal, és hogy hogyan használhatja a felhasználó a vizualizációkat a Power BI-ban. 

Az alábbi ábra azt mutatja, hogyan vannak feldolgozva a Power BI-ban a felhasználók által a leggyakrabban végzett vizualizációkkal kapcsolatos műveletek.

![Power BI-vizualizációk műveleteinek diagramja](./media/visual-concept.svg)

## <a name="visuals-get-updates-from-power-bi"></a>A vizualizációk frissítéseket kapnak a Power BI-ból

A vizualizáció egy `update` metódust hív meg a frissítések Power BI-ból való lekéréséhez. Az `update` metódus általában tartalmazza a vizualizáció fő logikáját, és felelős a diagram vagy az adat megjelenítéséért.

A frissítések akkor aktiválódnak, amikor a vizualizáció meghívja az `update` metódust.

## <a name="action-and-update-patterns"></a>Műveleti és frissítési minták

Power BI-vizualizációkban a műveletek és a további frissítések az alábbi három minta valamelyikében történnek:

* A felhasználó a vizualizáción keresztül kommunikál Power BI-jal.
* A felhasználó közvetlenül lép interakcióba a vizualizációval.
* A vizualizáció a Power BI-jal kommunikál.

### <a name="user-interacts-with-a-visual-through-power-bi"></a>A felhasználó a vizualizáción keresztül kommunikál Power BI-jal

* A felhasználó megnyitja a vizualizáció tulajdonságainak paneljét.

    Amikor a felhasználó megnyitja a vizualizáció tulajdonságainak paneljét, a Power BI beolvassa a támogatott objektumokat és a tulajdonságokat a vizualizáció *properties.json* fájljából. A tulajdonságok tényleges értékeinek beolvasásához a Power BI meghívja a vizualizáció `enumerateObjectInstances` metódusát. A vizualizáció a tulajdonságok tényleges értékeit adja vissza.

    További információ: [A Power BI-vizualizációk képességei és tulajdonságai](capabilities.md).

* A felhasználó [módosítja a vizualizáció tulajdonságát](../../visuals/power-bi-visualization-customize-title-background-and-legend.md) a formátum panelen.

    Amikor a felhasználó módosítja egy tulajdonság értékét a formátum panelen, a Power BI meghívja a vizualizáció `update` metódusát. A Power BI átadja az új `options` objektumot az `update` metódusnak. Az objektumok tartalmazzák az új értékeket.

    További információ: [A Power BI-vizualizációk objektumai és tulajdonságai](objects-properties.md).

* A felhasználó átméretezi a vizualizációt.

    Amikor a felhasználó megváltoztatja a vizualizáció méretét, a Power BI meghívja az `update` metódust az új `options` objektummal. Az `options` objektumok beágyazott `viewport` objektumokkal rendelkeznek, amelyek tartalmazzák a vizualizáció új szélességét és magasságát.

* A felhasználó szűrőt alkalmaz a jelentés, az oldal vagy a vizualizáció szintjén.

    A Power BI a szűrési feltételek alapján szűri az adatokat. A Power BI meghívja a vizualizáció `update` metódusát, hogy frissítse a vizualizációt az új adatokkal.

    A vizualizáció megkapja az `options` objektumok új frissítéseit, ha új adatok érhetőek el valamely beágyazott objektumban. Hogy a frissítés hogyan történik, az a vizualizáció adatnézet-leképezési konfigurációjától függ.

    További információ: [A Power BI-vizualizációkban végzett adatnézet-leképezések ismertetése](dataview-mappings.md).

* A felhasználó a jelentés egy másik vizualizációjában kiválaszt egy adatpontot.

    Ha a felhasználó a jelentés egy másik vizualizációjában kiválaszt egy adatpontot, a Power BI kiemeli a kiválasztott adatpontokat, és meghívja a vizualizáció `update` metódusát. A vizualizáció megkapja az új szűrt adatokat vagy ugyanazokat az adatokat a kiemelések tömbjével.

    További információ: [Adatpontok kiemelése Power BI-vizualizációkban](highlight.md).

* A felhasználó kiválaszt egy könyvjelzőt a jelentés könyvjelzők paneljén.

    Ha a felhasználó kiválaszt egy könyvjelzőt a jelentés könyvjelzők paneljén, a következő két művelet egyike történhet:

    * A Power BI meghívja a `registerOnSelectionCallback` metódus által átadott és regisztrált függvényt. A visszahívási függvény a megfelelő könyvjelző kiválasztásának tömbjét kapja meg.

    * A Power BI meghívja az `update` metódust egy megfelelő `filter` objektummal az `options` objektumon belül.

    A vizualizációnak mindkét esetben meg kell változtatnia az állapotát a kapott kiválasztások vagy a `filter` objektum alapján.

    További információ a könyvjelzők és szűrők használatáról: [Vizualizációszűrő API a Power BI-vizualizációkban](filter-api.md).

### <a name="user-interacts-with-the-visual-directly"></a>A felhasználó közvetlenül lép interakcióba a vizualizációval

* A felhasználó az egérmutatót egy adatelem fölé viszi.

    A vizualizáció további információt jeleníthet meg az adatpontról a Power BI Elemleírások API-jával. Ha a felhasználó a vizuális elemre viszi az egérmutatót, a vizualizáció képes kezelni az eseményt, és megjeleníti a kapcsolódó elemleírás információit. A vizualizáció képes megjeleníteni akár a standard elemleírást, akár a jelentési oldal elemleírását.

    További információért lásd: [Elemleírások a Power BI-vizualizációkban](add-tooltips.md).

* A felhasználó megváltoztatja a vizualizáció tulajdonságait. (Például a felhasználó kibontja a fát, és a vizualizáció menti a vizualizáció állapotát a tulajdonságokban.)

    A vizualizáció mentheti a tulajdonságok értékeit a Power BI API-n keresztül. Ha például egy felhasználó kommunikál a vizualizációval, és a vizualizációnak mentenie vagy frissítenie kell a tulajdonságok értékeit, a vizualizáció meghívhatja a `presistProperties` metódust.

* A felhasználó kiválaszt egy URL-címet.

    Alapértelmezés szerint a vizualizáció közvetlenül nem tud megnyitni URL-címet. Ha az URL-címet új lapon kell megnyitni, a vizualizáció meghívja a `launchUrl` metódust, és paraméterként adja át neki az URL-címet.

    További információkért lásd: [Indítási URL-cím létrehozása](launch-url.md).

* A felhasználó szűrőt alkalmaz a vizualizáción keresztül.

    A vizualizáció meghívhatja az `applyJsonFilter` metódust, és átadhatja az egyéb vizualizációkban tárolt adatok szűrési feltételeit. A szűrők különféle típusai érhetőek el, többek között az alapszintű, a speciális és a rekordos szűrők.

    További információ: [Vizualizációszűrő API a Power BI-vizualizációkban](filter-api.md).

* A felhasználó elemeket jelöl ki a vizualizáción.

    A Power BI-vizualizációkon belüli kijelöléssel kapcsolatosan az [Interaktivitás hozzáadása kijelöléssel a Power BI-vizualizációkban](selection-api.md) című cikkben talál információt.

### <a name="visual-interacts-with-power-bi"></a>A vizualizáció a Power BI-jal kommunikál

* A vizualizáció további adatokat kér a Power BI-tól.

    A vizualizáció részenként feldolgozza az adatokat. A `fetchMoreData` API-metódus az adathalmaz következő részét lekéri.

    További információ: [További adatok beolvasása a Power BI-ból](fetch-more-data.md).

* Az eseményszolgáltatás aktiválódik.

    A Power BI exportálni tudja a jelentéseket PDF-fájlba, vagy elküldheti e-mailben (csak a tanúsítvánnyal rendelkező vizualizációknál). A vizualizáció az Események renderelése API hívásával értesíti a Power BI-t a megjelenítésre való előkészítés befejeződéséről és arról, hogy készen áll a PDF-fájl vagy az e-mail rögzítésére.

    További információért olvassa el a [Jelentések exportálása a Power BI-ból PDF-fájlba](../../consumer/end-user-pdf.md) című cikket.

    Az eseményszolgáltatással kapcsolatos további tudnivalókért lásd: [Renderelési események a Power BI-vizualizációkban](event-service.md).

## <a name="next-steps"></a>Következő lépések

Szeretne saját képi megjelenítéseket létrehozni, és hozzáadni azokat a Microsoft AppSource-hoz? Olvassa el a következő cikkeket:

* [Power BI-vizualizáció fejlesztése](./custom-visual-develop-tutorial.md)
* [Power BI-vizualizációk közzététele a Partnerközpontban](../office-store.md)
