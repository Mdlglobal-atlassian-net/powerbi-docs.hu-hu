---
title: A Power BI-vizualizáció tesztelése a küldés előtt
description: Ez a cikk azokat a teszteseteket ismerteti, amelyeken a vizualizációnak meg kell felelnie az AppSource-on való közzétételhez. Léteznek továbbá választható tesztesetek is.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 04/15/2020
ms.openlocfilehash: 65e00fa5311ea12c9fe0011c6aa7c3e779f33dc5
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83131119"
---
# <a name="submission-testing-of-a-power-bi-visual"></a>A Power BI-vizualizáció tesztelése a küldés előtt

A vizualizációnak meg kell felelnie ezeken a teszteseteken mielőtt közzéteszi az [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals)-on. Az elküldés előtt tesztelje a vizualizációt. Ha a vizualizáció nem felel meg a szükséges teszteseteken, vissza lesz utasítva.

További tudnivalókat a közzétételi folyamatról [a Power BI-vizualizációk Partnerközpontban való közzétételével](./office-store.md) kapcsolatos cikkben talál.

## <a name="general-test-cases"></a>Általános tesztesetek

| Teszteset | Várt eredmények
| --------- | ----------------
| Hozzon létre egy **kategóriával** és **értékkel** rendelkező **halmozott oszlopdiagramot**. Alakítsa át vizualizációvá, majd vissza oszlopdiagrammá. | Az átalakítások elvégzése után nem jelentkezik hiba. |
| Hozzon létre egy három mértéket tartalmazó **kijelzőt**. Alakítsa át vizualizációvá, majd vissza **kijelzővé**. | Az átalakítások elvégzése után nem jelentkezik hiba. |
| Válasszon ki elemeket a vizualizációban. | Más vizualizációk tükrözni fogják a kiválasztásokat. |
| Válasszon ki elemeket más vizualizációkban. | A vizualizáció a szűrt adatokat a többi vizualizációban végzett kiválasztásoknak megfelelően jeleníti meg. |
| Ellenőrizze a minimális/maximális **dataViewMapping** feltételt. | A mezőgyűjtők több mezőt vagy egyetlen mezőt fogadnak el, vagy más gyűjtők határozzák meg őket. A minimális/maximális **dataViewMapping** feltételt megfelelően be kell állítani a vizualizáció képességein belül. |
| Különböző sorrendben távolítson el minden mezőt. | A vizualizáció megfelelően kiürül, a mezők tetszőleges sorrendben történő eltávolítása hatására. Nincsenek hibák a konzolon vagy a böngészőben. |
| Nyissa meg a **Formátum** panelt minden lehetséges gyűjtőkonfigurációval. | Ez a teszt nem aktiválja a null értékű hivatkozáskivételeket. |
| Az adatszűréshez használja a vizualizáció-, lap- és jelentésszinten található **Szűrés** panelt. | Az elemleírások a szűrők alkalmazása után megfelelőek. Az elemleírások a szűrt értéket jelenítik meg. |
| Adatok szűrése **szeletelővel**. | Az elemleírások a szűrők alkalmazása után megfelelőek. Az elemleírások a szűrt értéket jelenítik meg. |
| Szűrje az adatokat egy közzétett vizualizációval. Például válasszon ki egy kördiagramszeletet vagy egy oszlopot. | Az elemleírások a szűrők alkalmazása után megfelelőek. Az elemleírások a szűrt értéket jelenítik meg. |
| Ha a keresztszűrés támogatott, ellenőrizze, hogy a szűrők megfelelően működnek-e. | Az alkalmazott kiválasztás szűri a jelentés ezen lapján lévő további vizualizációkat. |
| A Ctrl, Alt és Shift billentyűk lenyomásával választhat ki elemeket. | Nincs váratlan működés. |
| A **Megjelenítési mód** beállítást módosítsa **Tényleges méret**, **Laphoz igazítás** és **Szélességhez igazítás** értékre. | Az egér koordinátái pontosak. |
| Méretezze át a vizualizációt. | A vizualizáció megfelelően reagál az átméretezésre. |
| Állítsa a jelentés méretét a minimálisra. | Nincsenek megjelenítési hibák. |
| Ellenőrizze, hogy a görgetősávok megfelelően működnek-e. | A görgetősávoknak meg kell jelenniük, ha szükség van rájuk. Ellenőrizze a görgetősávok méretét. A görgetősávok nem lehetnek túl szélesek vagy túl magasak. A görgetősávok pozíciójának és méretének igazodnia kell a vizualizáció további elemeihez. Győződjön meg arról, hogy a vizualizáció különböző méreteihez görgetősávok szükségesek. |
| Rögzítse a vizualizációt az **irányítópulton**. | A vizualizációnak megfelelően kell megjelennie. |
| Adja hozzá a vizualizáció több verzióját egy adott jelentésoldalhoz. | A vizualizáció összes verziójának megfelelően kell megjelennie és működnie. |
| Adja hozzá a vizualizáció több verzióját több jelentésoldalhoz. | A vizualizáció összes verziójának megfelelően kell megjelennie és működnie. |
| Váltson a jelentésoldalak között. | A vizualizáció megfelelően jelenik meg. |
| Tesztelje a vizualizáció Olvasó nézetét és Szerkesztő nézetét. | Minden funkció megfelelően működik. |
| Ha a vizualizáció animációkat használ, adja hozzá, módosítsa és törölje a vizualizáció elemeit. | A vizualizáció elemeinek animálása megfelelően működik. |
| Nyissa meg a **Tulajdonság** panelt. Kapcsolja be és ki a tulajdonságokat, írjon be egyéni szöveget, próbálja ki az elérhető lehetőségeket, és adjon meg helytelen adatokat. | A vizualizáció megfelelően reagál. |
| Mentse a jelentést, majd nyissa meg újra. | Az összes tulajdonságbeállítás megmaradt. |
| Lépjen másik oldalra a jelentésben, majd lépjen vissza. | Az összes tulajdonságbeállítás megmaradt. |
| Tesztelje a vizualizáció összes funkcióját, beleértve a vizualizáció által biztosított különböző lehetőségeket. | Valamennyi megjelenítés és funkció megfelelően működik. |
| Tesztelje az összes numerikus, dátum és karakter adattípust a következő tesztekhez hasonlóan. | Minden adat megfelelően van formázva. |
| Tekintse át az elemleírás-értékek, a tengelyfeliratok, az adatfeliratok és más formázott vizuális elemek formázását. | Minden elem megfelelően van formázva. |
| Győződjön meg arról, hogy az adatfeliratok a formázási sztringet használják. | Minden adatfelirat megfelelően van formázva. |
| Kapcsolja be, majd ki a numerikus értékek automatikus formázását az elemleírásokban. | Az elemleírások megfelelően jelenítik meg az értékeket. |
| Tesztelje az adatbejegyzéseket különböző típusú adatokkal, például numerikus, szöveges, dátum- és időértékekkel, valamint a modell különböző formátumú sztringjeivel. Teszteljen különféle adatmennyiségeket, például több ezer sort, egy sort és két sort. | Valamennyi megjelenítés és funkció megfelelően működik. |
| Adjon meg helytelen adattípust a vizualizációban, például null, végtelen és negatív értékeket, valamint nem megfelelő értéktípusokat. | Valamennyi megjelenítés és funkció megfelelően működik. |

## <a name="optional-browser-testing"></a>Választható böngészőtesztelés

Az AppSource csapata a Google Chrome, a Microsoft Edge és a Mozilla Firefox böngészők legújabb Windows-verzióin ellenőrzi a vizualizációt.
Szükség esetén ellenőrizze a vizualizációt a következő böngészőkben.

| Teszteset | Várt eredmények
| --------- | ----------------
| **Windows** |
| Google Chrome (korábbi verzió) | Valamennyi megjelenítés és funkció megfelelően működik. |
| Mozilla Firefox (korábbi verzió) | Valamennyi megjelenítés és funkció megfelelően működik. |
| Microsoft Edge (korábbi verzió) | Valamennyi megjelenítés és funkció megfelelően működik. |
| Microsoft Internet Explorer 11 (választható) | Valamennyi megjelenítés és funkció megfelelően működik. |
| **macOS** |
| Chrome (korábbi verzió) | Valamennyi megjelenítés és funkció megfelelően működik. |
| Firefox (korábbi verzió) | Valamennyi megjelenítés és funkció megfelelően működik. |
| Safari (korábbi verzió) | Valamennyi megjelenítés és funkció megfelelően működik. |
| **Linux** |
| Firefox (legfrissebb és korábbi verziók) | Valamennyi megjelenítés és funkció megfelelően működik. |
| **Mobileszközök – iOS** |
| Apple Safari iPad (korábbi Safari-verzió) | Valamennyi megjelenítés és funkció megfelelően működik. |
| Chrome iPad (legfrissebb Safari-verzió) | Valamennyi megjelenítés és funkció megfelelően működik. |
| **Mobileszközök – Android** |
| Chrome (legfrissebb és korábbi verziók) | Valamennyi megjelenítés és funkció megfelelően működik. |

## <a name="desktop-testing"></a>Asztali tesztelés

Tesztelje a vizualizációt a [Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop/) aktuális verziójában.

| Teszteset | Várt eredmények
| --------- | ----------------
| Tesztelje a vizualizáció összes funkcióját. | Valamennyi megjelenítés és funkció megfelelően működik. |
| Importáljon, mentsen és nyisson meg egy fájlt, majd tegye közzé a Power BI webszolgáltatásban a Power BI Desktop **Közzététel** gombjával. | Valamennyi megjelenítés és funkció megfelelően működik. |
| Módosítsa a numerikus formátumú sztringet úgy, hogy a pontosság növelésével vagy csökkentésével nulla tizedesjegyet vagy három tizedesjegyet jelenítsen meg. | A vizualizáció megfelelően jelenik meg. |

## <a name="performance-testing"></a>Teljesítménytesztelés

A vizualizációnak elfogadható teljesítményt kell nyújtania. Fejlesztői eszközökkel ellenőrizze a teljesítményt. Ne támaszkodjon vizuális jelekre és a konzol időnaplóira.

| Teszteset | Várt eredmények
| --------- | ----------------
| Hozzon létre egy számos vizuális elemmel rendelkező vizualizációt. | A vizualizációnak megfelelő teljesítményűnek kell lennie, és nem fagyaszthatja le az alkalmazást. Nem lehetnek olyan elemekkel kapcsolatos teljesítményproblémák, mint az animáció sebessége, az átméretezés, a szűrés és a kiválasztás.

## <a name="next-steps"></a>Következő lépések

További tudnivalókat a közzétételi folyamatról [a Power BI-vizualizációk Partnerközpontban való közzétételével](./office-store.md) kapcsolatos cikkben talál.

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/).
