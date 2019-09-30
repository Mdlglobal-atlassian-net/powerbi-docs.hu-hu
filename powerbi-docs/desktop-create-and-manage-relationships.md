---
title: Kapcsolatok létrehozása és kezelése a Power BI Desktopban
description: Kapcsolatok létrehozása és kezelése a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/19/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: f2102ad654a056832f7890dc506acc99eb5ef26f
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61312496"
---
# <a name="create-and-manage-relationships-in-power-bi-desktop"></a>Kapcsolatok létrehozása és kezelése a Power BI Desktopban
Amikor több táblázatot importál, valószínűleg az összes táblázatból származó adattal fog elemzést végezni. A táblázatok közötti kapcsolatok szükségesek az eredmények pontos kiszámításához és a jelentésekben a helyes információk megjelenítéséhez. A Power BI Desktop megkönnyíti ezen kapcsolatok létrehozását. Valójában a legtöbb esetben semmit sem kell tennie, az Automatikus észlelés funkció elvégezheti Ön helyett. Bizonyos esetekben azonban szükség lehet a kapcsolatok saját kezű létrehozására, vagy egy kapcsolat módosításaira. Mindkét esetben fontos megérteni a Power BI Desktopban lévő kapcsolatokat és azok létrehozásának és szerkesztésének módját.

## <a name="autodetect-during-load"></a>Automatikus észlelés a betöltés során
Ha egyszerre két vagy több táblázatot kérdez le, az adatok betöltésekor a Power BI Desktop megkísérli megkeresni és létrehozni a kapcsolatokat Ön helyett. A Számosság, a Szűrő irányának keresztezése és az Aktív tulajdonságok automatikusan be vannak állítva. A Power BI Desktop a lekérdezett táblázatokban szereplő oszlopneveket tekinti meg annak meghatározásához, hogy vannak-e lehetséges kapcsolatok. Ha vannak, a kapcsolatok automatikusan létrejönnek. Ha a Power BI Desktop nem tud magabiztosan meghatározni egyezést, nem hozza létre automatikusan a kapcsolatot. A Kapcsolatok kezelése párbeszédpanelen továbbra is létrehozhatja vagy szerkesztheti a kapcsolatokat.

## <a name="create-a-relationship-by-using-autodetect"></a>Kapcsolatok létrehozása az Automatikus észleléssel
A **Kezdőlap** lapon kattintson a **Kapcsolatok kezelése** \> **Automatikus észlelés** elemre.

![](media/desktop-create-and-manage-relationships/automaticrelationship.gif)

## <a name="create-a-relationship-manually"></a>Kapcsolatok létrehozása manuálisan
1. A **Kezdőlap** lapon kattintson a **Kapcsolatok kezelése** \> **Új** elemre.
2. A **Kapcsolat létrehozása** párbeszédpanelen az első táblázat legördülő listájában válasszon egy táblázatot, majd válassza ki a kapcsolatban használni kívánt oszlopot.
3. A második táblázat legördülő listájában válassza ki a kapcsolatba foglalni kívánt második táblázatot, és válassza ki a használni kívánt másik oszlopot, majd kattintson az **OK** gombra.

![](media/desktop-create-and-manage-relationships/manualrelationship2.gif)

Alapértelmezés szerint a Power BI Desktop automatikusan konfigurálja az új kapcsolat Számosság (irány), Szűrő irányának keresztezése és Aktív tulajdonságait, de szükség esetén módosíthatja ezeket. További tudnivalókat a jelen cikk későbbi, „További beállítások ismertetése” című szakaszában talál.

Ha a kapcsolat létrehozásához kiválasztott táblák egyike sem tartalmaz egyedi értékeket, akkor *Az oszlopok egyikének egyedi értékeket kell tartalmaznia* hibaüzenet fog megjelenni. Egy kapcsolatban legalább az egyik táblának tartalmaznia *kell* kulcs-értékek megkülönböztethető, egyedi listáját, amely egy általános követelmény a relációs adatbázis-technológiák esetében. 

Ha ezt a hibát észleli, a következő módokon javíthatja a problémát:

* Használja az „Ismétlődő sorok eltávolítása” funkciót egy egyedi értékeket tartalmazó oszlop létrehozásához. Ennek a megközelítésnek az a hátránya, hogy az ismétlődő sorok eltávolítása adatvesztéssel jár, és egy kulcs (sor) legtöbb esetben okkal van megkettőzve.
* Vegyen fel egy köztes táblát a modellben használt egyedi kulcs-értékekkel, amely csatlakoztatva lesz a kapcsolat mindkét eredeti oszlopához.

További információkért tekintse meg ezt a [blogbejegyzést](https://blogs.technet.microsoft.com/cansql/2016/12/19/relationships-in-power-bi-fixing-one-of-the-columns-must-have-unique-values-error-message/).


## <a name="edit-a-relationship"></a>Kapcsolat szerkesztése
1. A **Kezdőlap** lapon kattintson a **Kapcsolatok kezelése** elemre.
2. A **Kapcsolatok kezelése** párbeszédpanelen válassza ki a kapcsolatot, majd kattintson a **Szerkesztés** gombra.

## <a name="configure-additional-options"></a>További beállítások konfigurálása
A kapcsolatok létrehozásakor vagy szerkesztésekor további beállításokat is konfigurálhat. Alapértelmezés szerint a rendszer automatikusan, legjobb belátása szerint konfigurálja a további beállításokat, amelyek az oszlopokban található adatok alapján kapcsolatonként eltérőek lehetnek.

## <a name="cardinality"></a>Számosság
**Több az egyhez (\*:1)** – Ez a leggyakoribb, alapértelmezett típus. Azt jelenti, hogy az egyik táblázat oszlopában egy érték több példánya szerepelhet, és a másik kapcsolódó táblázatban, másnéven a keresési táblázatban az érték egy példánya szerepel.

**Egy az egyhez (1:1)** – Az egyik táblázat oszlopában egy adott érték egy példánya szerepelhet, és a másik kapcsolódó táblázatban az érték egy példánya szerepel.

**Több a többhöz kapcsolatok**: Összetett modellek esetén több a többhöz típusú kapcsolatokat hozhat létre a táblák között, ami megszünteti a táblák egyedi értékeire vonatkozó követelményeket. Korábbi áthidaló megoldásokat is szükségtelenné tesz, például új táblák bevezetését a kapcsolatok létrehozásához. Részletesebb információkért lásd: [Kapcsolatok sok a sokhoz számossággal](https://docs.microsoft.com/power-bi/desktop-many-to-many-relationships). 

A számosság módosításának idejéről további tudnivalókat a jelen cikk későbbi, „További beállítások ismertetése” című szakaszában talál.

## <a name="cross-filter-direction"></a>Szűrő irányának keresztezése
**Mindkettő** – A leggyakoribb, alapértelmezett irány. Azt jelenti, hogy szűrési célokból a rendszer mindkét táblázatot egy táblázatként kezeli. A **Mindkettő** beállítás jól működik, ha egy olyan táblázattal dolgozik, amelyet számos keresési táblázat vesz körül. Erre példa lehet egy Értékesítési táblázat, amelyben a részleghez egy keresési táblázat szerepel. Ezt gyakran csillagséma konfigurációnak nevezik (egy központi táblázat több keresési táblázattal.) Ha azonban két vagy több olyan táblázata van, amelyek keresési táblázatokkal rendelkeznek (amelyek közül néhány közös), akkor nem érdemes a Mindkettő beállítást használni. Az előző példa folytatása érdekében ebben az esetben olyan költségvetési értékesítési táblázattal is rendelkezik, amely az egyes részlegek cél költségvetését rögzíti. A részleg táblázata pedig az értékesítés és a költségvetés táblázathoz is csatlakozik. Az ilyen konfigurációtípusok esetén kerülje a Mindkettő beállítást.

**Egyirányú** – A csatlakoztatott táblázatokban lévő szűrési lehetőségek arra a táblázatra érvényesek, ahol az értékek összesítve vannak. Ha egy Power Pivot táblázatot Excel 2013 vagy korábbi adatmodellbe importál, minden kapcsolat egyetlen iránnyal rendelkezik. 

A Szűrő irányának keresztezése beállítás módosításának idejéről további tudnivalókat a jelen cikk későbbi, „További beállítások ismertetése” című szakaszában talál.

## <a name="make-this-relationship-active"></a>A kapcsolat aktívvá tétele
Amikor be van jelölve, azt jelenti, hogy ez a kapcsolat az aktív, alapértelmezett kapcsolat. Olyan esetekben, ahol több kapcsolat van két táblázat között, az aktív kapcsolattal a Power BI Desktop automatikusan hozhatja létre a mindkét táblázatot tartalmazó vizualizációkat.

Egy adott kapcsolat aktívvá tételének idejéről további tudnivalókat a jelen cikk későbbi, „További beállítások ismertetése” című szakaszában talál.

## <a name="understanding-relationships"></a>A kapcsolatok ismertetése
Miután egy kapcsolattal összekapcsolt két táblázatot, mindkét táblázat adatait úgy használhatja, mintha egyetlen táblázatot alkotnának, így nem kell aggódnia a kapcsolat részletei miatt, és nem kell egybesimítania a táblázatokat egyetlen táblázattá az importálásuk előtt. Sok esetben a Power BI Desktop automatikusan létre tudja hozni a kapcsolatokat, így elképzelhető, hogy nem is kell saját kezűleg létrehoznia ezeket a kapcsolatokat. Ha azonban a Power BI Desktop nem tudja nagy valószínűséggel meghatározni, hogy léteznie kell-e kapcsolatnak két táblázat között, nem hozza létre automatikusan a kapcsolatot. Ebben az esetben létre kell hoznia a kapcsolatot. 

Tekintsünk át egy rövid oktatóprogramot, hogy jobban bemutathassuk a kapcsolatok működését a Power BI Desktopban.

>[!TIP]
>Ezt a leckét önállóan elvégezheti. Másolja az alábbi ProjektÓrák táblázatot egy Excel munkalapra, jelölje ki az összes cellát, és kattintson a **Beszúrás** \> **Táblázat** lehetőségre. A **Táblázat létrehozása** párbeszédpanelen csak kattintson az **OK** gombra. Ezután a **Táblázat neve** területen írja be a **ProjektÓrák**  nevet. Végezze el ugyanezt a VállalatiProjekt táblázathoz. Ezután importálhatja az adatokat az **Adatok lekérése** paranccsal a Power BI Desktopban. Válassza ki a munkafüzetet és a táblázatokat adatforrásként.

Az első táblázat, a ProjektÓrák, azon munkajegyek rekordja, amelyek rögzítik az egy adott személy által egy adott projekttel töltött órák számát. 

**ProjektÓrák**

| **Jegy** | **Beküldő** | **Órák** | **Projekt** | **KüldésiDátum** |
| ---:|:--- | ---:|:--- | ---:|
| 1001 |Brewer, Alan |22 |Kék |1/1/2013 |
| 1002 |Brewer, Alan |26 |Vörös |2/1/2013 |
| 1003 |Ito, Shu |34 |Sárga |12/4/2012 |
| 1004 |Brewer, Alan |13 |Narancssárga |1/2/2012 |
| 1005 |Bowen, Eli |29 |Bíbor |10/1/2013 |
| 1006 |Bento, Nuno |35 |Zöld |2/1/2013 |
| 1007 |Hamilton, David |10 |Sárga |10/1/2013 |
| 1008 |Han, Mu |28 |Narancssárga |1/2/2012 |
| 1009 |Ito, Shu |22 |Bíbor |2/1/2013 |
| 1010 |Bowen, Eli |28 |Zöld |10/1/2013 |
| 1011 |Bowen, Eli |9 |Kék |10/15/2013 |

A második táblázat, a VállalatiProjekt, a hozzárendelt prioritásokkal (A, B vagy C) rendelkező projektek listája. 

**VállalatiProjekt**

| **ProjektNév** | **Prioritás** |
| --- | --- |
| Kék |A |
| Vörös |B |
| Zöld |C |
| Sárga |C |
| Bíbor |B |
| Narancssárga |C |

Figyelje meg, hogy mindegyik táblázatban található egy projekt oszlop. Nem ugyanaz a nevük, de úgy tűnik, hogy az értékek egyeznek. Ez fontos, és nemsokára visszatérünk rá.

Most, hogy két táblázat van a modellbe importálva, hozzunk létre egy jelentést. Először a projekt prioritásai alapján elküldött órák számát szeretnénk lekérni, ezért jelöljük be a Mezők területen a **Prioritás** és az **Órák** lehetőségeket.

 ![](media/desktop-create-and-manage-relationships/candmrel_reportfiltersnorel.png)

Ha a Jelentés vásznon a táblázatra tekint, láthatja, hogy mindegyik projekthez **256,00** az órák száma, és az összeg is ez. Egyértelmű, hogy ez helytelen. Miért? Ez azért van, mert nem lehet kiszámítani az értékek összegét egy olyan táblázatból (Órák a Projekt táblázatban), amelyet egy másik táblázatban lévő értékek szeletelnek (Prioritás a VállalatiProjekt táblázatban) anélkül, hogy kapcsolat lenne a két táblázat között.

Ezért hozzunk létre egy kapcsolatot a két táblázat között.

Emlékszik a két táblázatban a projektnévvel szereplő oszlopokra, amelyeknek hasonlónak tűnő értékeik voltak? Ezzel a két oszloppal kapcsolatot hozunk létre a táblázatok között.

Miért ezekkel az oszlopokkal? Ha a ProjektÓrák táblázatban lévő Projekt oszlopra tekintünk, olyan értékeket láthatunk, mint Kék, Vörös, Sárga, Narancssárga stb. Valójában több azonos értékű sort is láthatunk. Ez azt jelenti, hogy számos színértékünk vannak a Projekthez.

Ha a VállalatiProjekt táblázatban lévő ProjektNév oszlopra tekintünk, láthatjuk, hogy csak egy-egy színérték tartozik a projekthez. A táblázatban lévő mindegyik érték egyedi, és ez fontos, mert kapcsolatot tudunk létrehozni a két táblázat között. Ebben az esetben ez egy „több az egyhez” kapcsolat. A „több az egyhez” kapcsolatokban legalább az egyik táblázat egyik oszlopának egyedi értékeket kell tartalmaznia. Néhány kapcsolathoz léteznek további beállítások, amelyek áttekintése később következik, egyelőre most hozzunk létre egy kapcsolatot a két táblázat Projekt oszlopai között.

### <a name="to-create-the-new-relationship"></a>Új kapcsolat létrehozása
1. Kattintson a **Kapcsolatok kezelése** lehetőségre.
2. A **Kapcsolatok kezelése** területen kattintson az **Új** lehetőségre a **Kapcsolat létrehozása** párbeszédpanel megnyitásához, ahol kiválaszthatja a kapcsolathoz használni kívánt táblázatokat, oszlopokat és további beállításokat.
3. Az első táblázatban válassza a **ProjektÓrák**  lehetőséget, majd válassza a **Projekt** oszlopot. Ez a kapcsolat „több” oldala.
4. A második táblázatban válassza a **VállalatiProjekt** lehetőséget, majd válassza a **ProjektNév** oszlopot. Ez a kapcsolat „egy” oldala. 
5. Kattintson az **OK** gombra a **Kapcsolat létrehozása** párbeszédpanelen és a **Kapcsolatok kezelése** párbeszédpanelen is.

![](media/desktop-create-and-manage-relationships/candmrel_create_compproj.png)

Az igazság az, hogy ez volt a kapcsolat létrehozásának nehezebb módja. A Kapcsolatok kezelése párbeszédpanelen egyszerűen az Automatikus észlelés gombra is kattinthatott volna. Az Automatikus észlelés ugyanis megtette volna mindezt az adatok betöltésekor, ha mindkét oszlop neve ugyanaz volt. De mi ebben a kihívás?

Most tekintsük meg ismét a Jelentés vásznon lévő táblázatot.

 ![](media/desktop-create-and-manage-relationships/candmrel_reportfilterswithrel.png)

Máris sokkal jobban néz ki, nem igaz?

Amikor a prioritás alapján összegezzük az órákat, a Power BI Desktop megkeresi a VállalatiProjekt keresési táblázatban az egyedi színértékek összes példányát, és megkeresi ezen értékek minden példányát a VállalatiProjekt táblázatban, majd kiszámítja minden egyes egyedi érték összegét.

Viszonylag egyszerű művelet volt mindez, az Automatikus észleléssel azonban talán még ennyit sem kellett volna tennünk.

## <a name="understanding-additional-options"></a>További beállítások ismertetése
A kapcsolatok Automatikus észleléssel vagy manuálisan való létrehozásakor a Power BI Desktop automatikusan konfigurálja a további beállításokat a táblázatokban lévő adatok alapján. E további kapcsolattulajdonságokat a Kapcsolat létrehozása/szerkesztése párbeszédpanel legalsó szakaszában találhatja meg és konfigurálhatja.

 ![](media/desktop-create-and-manage-relationships/candmrel_advancedoptions2.png)

Ahogy említettük, ezek beállítása általában automatikusan történik, így nem kell velük foglalkoznia; de több olyan helyzet is előfordulhat, amikor érdemes saját kezűleg konfigurálni a további beállításokat.

## <a name="automatic-relationship-updates"></a>Automatikus kapcsolatfrissítések

Felügyelheti, hogy a Power BI hogyan kezeli és állítja be automatikusan a jelentések és modellek kapcsolatait. Ha meg szeretné szabni, hogy a Power BI hogyan kezelje a kapcsolati beállításokat, válassza a **Fájl > Beállítások > Beállítások** lehetőséget a Power BI Desktopban, majd a bal oldali panelen válassza az **Adatok betöltése** elemet. Ezután megtekintheti a **Kapcsolatok** beállításait.

 ![Kapcsolati beállítások](media/desktop-create-and-manage-relationships/relationships-options-01.png)

Három lehetőség közül választhat. 

Az első lehetőség a *Kapcsolatok importálása adatforrásokból*, amely alapértelmezés szerint ki van jelölve. Ezzel a beállítással a Power BI ellenőrzi az adatforrásban definiált kapcsolatokat, például az adattárház külső kulcsainak és elsődleges kulcsainak kapcsolatait. Ha léteznek ilyen kapcsolatok, azok az első adatbetöltésnél megjelennek a Power BI adatmodelljében. Ezzel a beállítással gyorsan használatba veheti a modellt, anélkül, hogy Önnek kellene megkeresnie és definiálnia a kapcsolatokat.

A második lehetőség a *Az adatok frissítésekor frissítsen vagy töröljön kapcsolatokat*, amely alapértelmezés szerint ki van kapcsolva. Ezzel a beállítással (amelyet a jelölőnégyzet bejelölésével engedélyezhet) a Power BI az adatkészlet frissítésekor ellenőrzi az adatforrás-kapcsolatok változásait. Ha ezek a kapcsolatok módosulnak vagy törlődnek, a Power BI tükrözi ezeket a változásokat saját adatmodelljében, és a megfelelő (törlési vagy frissítési) műveletet végzi el.

> [!WARNING]
> Ha a definiált kapcsolatokra épülő sorszintű biztonságot alkalmaz, nem ajánlott a második lehetőséget (*Az adatok frissítésekor frissítsen vagy töröljön kapcsolatokat*) használni. Ha eltávolít egy olyan kapcsolatot, amelyre RLS-beállítások épülnek, az veszélyezteti a modell biztonságát. 

A harmadik lehetőség az *Új kapcsolatok automatikus észlelése az adatok betöltése után*, amelyet a cikk korábbi, [Automatikus észlelés a betöltés során](#autodetect-during-load) című szakaszában ismertettünk. 


## <a name="future-updates-to-the-data-require-a-different-cardinality"></a>Az adatok jövőbeli frissítései más számosságot igényelnek.
A Power BI Desktop normál esetben automatikusan meg tudja határozni a legmegfelelőbb számosságot a kapcsolathoz. Ha felül kell írnia az automatikus beállítást, mert tudja, hogy az adatok a jövőben módosulni fognak, a Számosság vezérlőben választhatja ki azt. Nézzünk egy olyan példát, ahol más számosságot kell választania.

Az alábbi VállalatiProjektPrioritás táblázat az összes vállalati projektet és azok prioritásait tartalmazza. A ProjektKöltségvetés táblázat pedig azon projektek listája, amelyekhez jóvá lett hagyva a költségvetés.

**ProjektKöltségvetés**

| **Jóváhagyott projektek** | **LefoglaltKöltségvetés** | **LefoglalásDátuma** |
|:--- | ---:| ---:|
| Kék |40,000 |12/1/2012 |
| Vörös |100,000 |12/1/2012 |
| Zöld |50,000 |12/1/2012 |

**VállalatiProjektPrioritás**

| **Projekt** | **Prioritás** |
| --- | --- |
| Kék |A |
| Vörös |B |
| Zöld |C |
| Sárga |C |
| Bíbor |B |
| Narancssárga |C |

Ha létrehozunk egy kapcsolatot a VállalatiProjektPrioritás táblázatban lévő Projekt oszlop és a ProjektKöltségvetés táblázat Jóváhagyott projektek oszlopa között a következőképpen:

 ![](media/desktop-create-and-manage-relationships/candmrel_create_compproj_appproj2.png)

A számosság beállítása automatikusan egy-az-egyhez (1:1), a keresztszűrésé pedig mindkettő (ahogy az ábrán látható). Ez azért van, mert a Power BI Desktop számára a két táblázat legjobb kombinációja a következő:

| **Projekt** | **Prioritás** | **LefoglaltKöltségvetés** | **LefoglalásDátuma** |
|:--- | --- | ---:| ---:|
| Kék |A |40,000 |12/1/2012 |
| Vörös |B |100,000 |12/1/2012 |
| Zöld |C |50,000 |12/1/2012 |
| Sárga |C |<br /> |<br /> |
| Bíbor |B |<br /> |<br /> |
| Narancssárga |C |<br /> |<br /> |

Egy-az-egyhez kapcsolat áll fenn a két táblázat között, mert nincsenek ismétlődő értékek a kombinált táblázat Projekt oszlopában. A Projekt oszlop egyedi, mert minden érték csak egyszer fordul elő, ezért a két táblázat sorai közvetlenül, megkettőzés nélkül kombinálhatók.

De tegyük fel, hogy tudja, hogy a következő frissítéskor az adatok módosulni fognak. A ProjektKöltségvetés táblázat frissített verziója ekkor egy további Kék és Vörös sorral rendelkezik:

**ProjektKöltségvetés**

| **Jóváhagyott projektek** | **LefoglaltKöltségvetés** | **LefoglalásDátuma** |
| --- | ---:| ---:|
| Kék |40,000 |12/1/2012 |
| Vörös |100,000 |12/1/2012 |
| Zöld |50,000 |12/1/2012 |
| Kék |80,000 |6/1/2013 |
| Vörös |90,000 |6/1/2013 |

 Ez azt jelenti, hogy a két táblázat legjobb kombinációja ekkor a következő: 

| **Projekt** | **Prioritás** | **LefoglaltKöltségvetés** | **LefoglalásDátuma** |
| --- | --- | ---:| ---:|
| Kék |A |40,000 |12/1/2012 |
| Vörös |B |100,000 |12/1/2012 |
| Zöld |C |50,000 |12/1/2012 |
| Sárga |C |<br /> |<br /> |
| Bíbor |B |<br /> |<br /> |
| Narancssárga |C |<br /> |<br /> |
| Kék |A |80000 |6/1/2013 |
| Vörös |B |90000 |6/1/2013 |

Ebben az új, kombinált táblázatban a Projekt oszlop ismétlődő értékekkel rendelkezik. A két eredeti táblázatnak nem egy-az-egyhez kapcsolata lesz a táblázat frissítése után. Ebben az esetben, mivel tudjuk, hogy ezen jövőbeli frissítések miatt a Projekt oszlopban ismétlődések lesznek, a Számosságot Több-az-egyhez (\*:1) típusúra érdemes állítani, ahol a „több” a ProjektKöltségvetés oldalán, az „egy” pedig a VállalatiProjektPrioritás oldalán van.

## <a name="adjusting-cross-filter-direction-for-a-complex-set-of-tables-and-relationships"></a>Keresztszűrés irányának módosítása összetett táblázatoknál és kapcsolatoknál
A legtöbb kapcsolat esetében a szűrő irányának keresztezése „Mindkettő” értékre állítható. Egyes ritka esetekben azonban előfordulhat, hogy az alapértéket módosítania kell, például ha egy modellt importál a Power Pivot egy régebbi verziójából, ahol minden kapcsolat egyetlen irányra van állítva. 

A Mindkettő beállítás lehetővé teszi, hogy a Power BI Desktop úgy kezelje a csatlakoztatott táblázatok minden szempontját, mintha egyetlen táblázatot alkotnának. Esetenként azonban a Power BI Desktop nem tudja a kapcsolat keresztszűrési irányát „Mindkettő” értékre állítani, és emellett jelentéskészítési célokból az alapértékek egyértelmű készletét is megőrizni. Ha egy kapcsolat keresztszűrési iránya nem állítható Mindkettő értékre, annak oka általában az, hogy az félreértést okozna. Ha az alapértelmezett keresztszűrő nem működik, próbálja meg egy adott táblázatra vagy Mindkettő értékre állítani.

Az egyetlen irányú keresztszűrés számos esetben működik. Ha a Power Pivotból importált egy modellt az Excel 2013 vagy korábbi verziójába, minden kapcsolat egyetlen irányra lesz állítva. Az egyetlen irány azt jelenti, hogy a csatlakoztatott táblázatokban lévő szűrési lehetőségek arra a táblázatra érvényesek, ahol az összesítés történik. Előfordulhat, hogy a keresztszűrés nehezen érthető meg, ezért tekintsünk meg egy példát.

 ![](media/desktop-create-and-manage-relationships/candmrel_singledircrossfiltering.png)

Ha egyetlen irányú keresztszűréssel hozza létre a projektórákat összegző jelentést, a VállalatiProjekt, a Prioritás, a VállalatiAlkalmazott vagy a Város alapján összegezhet (vagy szűrhet). Ha azonban meg szeretné számolni a projektenkénti alkalmazottak számát (ez kevésbé gyakori igény), mindez nem működik. Az eredmény egy azonos értékeket tartalmazó oszlop lesz. Az alábbi példában mindkét kapcsolat keresztszűrési iránya egyetlen irányra van állítva – a ProjektÓrák táblázat felé:

 ![](media/desktop-create-and-manage-relationships/candmrel_repcrossfiltersingle.png)

A szűrőspecifikáció a VállalatiProjekt felől a VállalatiAlkalmazott felé halad (az alábbi képen látható módon), de nem éri el a VállalatiAlkalmazott oszlopot. Ha azonban Mindkettő értékre állítja a keresztszűrés irányát, az működik. A Mindkettő beállítás lehetővé teszi, hogy a szűrőspecifikáció elérje az Alkalmazott oszlopot.

 ![](media/desktop-create-and-manage-relationships/candmrel_bidircrossfiltering.png)

Ha a keresztszűrés irányának értéke Mindkettő, a jelentés megfelelően jelenik meg:

 ![](media/desktop-create-and-manage-relationships/candmrel_repcrossfilterbi.png)

A keresztszűrés mindkettő iránya jól működik a fentihez hasonló táblázatkapcsolatok esetén. A minta neve általában csillagséma:

 ![](media/desktop-create-and-manage-relationships/candmrel_crossfilterstarschema.png)

A szűrő irányának keresztezése nem működik jól az adatbázisokban gyakran megtalálható általánosabb mintákkal, például a következő ábrán láthatóval:

 ![](media/desktop-create-and-manage-relationships/candmrel_crossfilterwithloops.png)

Ha ilyen táblázatmintát hoz léte hurkokkal, akkor a keresztszűrés a kapcsolatok nem egyértelmű készletét hozhatja létre. Ha például összegzi a TableX egyik mezőjét, majd a TableY egyik mezője alapján szűr, akkor nem egyértelmű, hogy hogyan kell haladnia a szűrőnek, a felső táblázaton vagy az alsó táblázaton keresztül. Az ilyen mintatípusok egyik gyakori példája, ha a TableX egy Értékesítési táblázat tényleges adatokkal, a TableY pedig költségvetési adatok táblázata. Ekkor a középen lévő táblázatok a mindkét táblázat által használt keresési táblázatok, amelyek például a részleget vagy régiót tartalmazzák. 

Az aktív/inaktív kapcsolatokhoz hasonlóan a Power BI Desktop nem engedi, hogy egy kapcsolat Mindkettő értékű legyen, ha az többértelműséget okoz a jelentésekben. Ez többféle módon kezelhető, és a két leggyakoribb módszer:

* A kapcsolatok törlése vagy megjelölése inaktívként a többértelműség csökkentése érdekében. Ezután elképzelhető, hogy a kapcsolat keresztszűrése Mindkettő értékre állítható.
* A táblázat beolvasása kétszer (másodszorra más névvel) a hurkok elkerülése érdekében. Ez a csillagséma kapcsolatok mintáját hozza létre. A csillagsémával mindegyik kapcsolat beállítható Mindkettő értékre.

## <a name="wrong-active-relationship"></a>Helytelen aktív kapcsolat
Amikor a Power BI Desktop automatikusan hoz létre kapcsolatokat, néha két táblázat között egynél több kapcsolatot talál. Ebben az esetben csak az egyik kapcsolat állítható be aktívként. Az aktív kapcsolat az alapértelmezett kapcsolat, így amikor két különböző táblázatból választ mezőket, a Power BI Desktop automatikusan létrehozhat egy vizualizációt. Néhány esetben azonban az automatikusan létrehozott kapcsolat helytelen lehet. A Kapcsolatok kezelése párbeszédpanelen aktívként vagy inaktívként állíthatja be a kapcsolatot, vagy a Kapcsolat szerkesztése párbeszédpanelen beállíthatja az aktív kapcsolatot. 

Annak biztosítása érdekében, hogy legyen alapértelmezett kapcsolat, a Power BI Desktop egyszerre csak egyetlen aktív kapcsolatot engedélyez két táblázat között. Ezért először inaktívvá kell állítani az aktuális kapcsolatot, majd be kell állítani az aktívvá tenni kívánt kapcsolatot.

Lássunk erre egy példát. Ez az első táblázat a ProjektJegyek, és a következő táblázat az AlkalmazottSzerepköre.

**ProjektJegyek**

| **Jegy** | **Megnyitó** | **Beküldő** | **Órák** | **Projekt** | **KüldésiDátum** |
| ---:|:--- |:--- | ---:|:--- | ---:|
| 1001 |Perham, Tom |Brewer, Alan |22 |Kék |1/1/2013 |
| 1002 |Roman, Daniel |Brewer, Alan |26 |Vörös |2/1/2013 |
| 1003 |Roth, Daniel |Ito, Shu |34 |Sárga |12/4/2012 |
| 1004 |Perham, Tom |Brewer, Alan |13 |Narancssárga |1/2/2012 |
| 1005 |Roman, Daniel |Bowen, Eli |29 |Bíbor |10/1/2013 |
| 1006 |Roth, Daniel |Bento, Nuno |35 |Zöld |2/1/2013 |
| 1007 |Roth, Daniel |Hamilton, David |10 |Sárga |10/1/2013 |
| 1008 |Perham, Tom |Han, Mu |28 |Narancssárga |1/2/2012 |
| 1009 |Roman, Daniel |Ito, Shu |22 |Bíbor |2/1/2013 |
| 1010 |Roth, Daniel |Bowen, Eli |28 |Zöld |10/1/2013 |
| 1011 |Perham, Tom |Bowen, Eli |9 |Kék |10/15/2013 |

**AlkalmazottSzerepköre**

| **Alkalmazott** | **Szerepkör** |
| --- | --- |
| Bento, Nuno |Projektvezető |
| Bowen, Eli |Projektvezető |
| Brewer, Alan |Projektvezető |
| Hamilton, David |Projektvezető |
| Han, Mu |Projektvezető |
| Ito, Shu |Projektvezető |
| Perham, Tom |Projektszponzor |
| Roman, Daniel |Projektszponzor |
| Roth, Daniel |Projektszponzor |

Itt valójában két kapcsolat áll fenn. Egy a ProjektJegyek táblázat Beküldő és az AlkalmazottSzerepköre táblázat Alkalmazott mezője, a másik pedig a ProjektJegyek táblázat Megnyitó és az AlkalmazottSzerepköre táblázat Alkalmazott mezője között.

 ![](media/desktop-create-and-manage-relationships/candmrel_activerelview.png)

Ha mindkét kapcsolatot a modellhez adjuk (először a Megnyitó oszlopot), akkor a Kapcsolatok kezelése párbeszédpanel a Megnyitó mezőt jeleníti meg aktívként:

 ![](media/desktop-create-and-manage-relationships/candmrel_managerelactive.png)

Ha most létrehozunk egy jelentést, amely az AlkalmazottSzerepköre táblázat Szerepkör és Alkalmazott mezőit, valamint a ProjektJegyek táblázat Órák mezőjét használja a Jelentés vásznon a táblázatvizualizációban, csak a projektszponzorokat látjuk, mert csak ők nyitották meg a projektjegyeket.

 ![](media/desktop-create-and-manage-relationships/candmrel_repcrossfilteractive.png)

Módosíthatjuk az aktív kapcsolatot, és a Megnyitó helyett a Beküldő mező lehet aktív. A Kapcsolatok kezelése párbeszédpanelen töröljük a ProjektJegyek(Megnyitó) és az AlkalmazottSzerepköre(Alkalmazott) közötti kapcsolat jelölőnégyzetét, majd bejelöljük a ProjektJegyek(Beküldő) és AlkalmazottSzerepköre(Alkalmazott) közötti kapcsolat jelölőnégyzetet.

![](media/desktop-create-and-manage-relationships/candmrel_managerelactivesubmittedby.png)

## <a name="see-all-of-your-relationships-in-relationship-view"></a>Az összes kapcsolat megtekintése a Kapcsolat nézetben
Néha a modellben több táblázat is található, amelyek között összetett kapcsolatok állnak fenn. A Power BI Desktop Kapcsolat nézete egy könnyen érthető és testreszabható ábrán jeleníti meg a modellben lévő összes kapcsolatot, azok irányát és számosságát. További információ: [Kapcsolat nézet a Power BI Desktopban](desktop-relationship-view.md).

