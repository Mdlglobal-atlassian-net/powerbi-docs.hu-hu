---
title: Webes közzététel a Power BI-ból
description: A Power BI Webes közzététel lehetőségével egyszerűen ágyazhat be interaktív Power BI-vizualizációkat online, például blogbejegyzésekbe, weboldalakba, e-mailen vagy közösségi médián keresztül, bármilyen eszközön.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/16/2019
LocalizationGroup: Share your work
ms.openlocfilehash: 1b5dfc0b05595e96c9a297a5be3700e71cdbe229
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051563"
---
# <a name="publish-to-web-from-power-bi"></a>Webes közzététel a Power BI-ból

A Power BI **webes közzététel** lehetőség, hogy lehetőségével egyszerűen ágyazhat be interaktív Power BI-vizualizációkat online, például blog blogbejegyzésekbe, weboldalakba, e-mailek vagy közösségi médián keresztül, bármilyen eszközről. A közzétett vizualizációkat egyszerűen szerkesztheti, frissítheti, vagy akár vissza is vonhatja a megosztásukat.

> [!WARNING]
> Ha használ **webes közzététel**, bárki hozzáférhet az interneten a közzétett jelentést vagy vizualizációt megtekintheti. Ez nem igényel hitelesítést, és többek között a megtekintésére részletességiszint-adatokat az összesítő jelentések. Egy jelentés közzététele előtt ellenőrizze, hogy az adatok és Vizualizációk nyilvános megosztás rendben. Bizalmas vagy szellemi tulajdont képező információt ne tegyen közzé. Ha bizonytalan, akkor a közzététel előtt ellenőrizze a cég szabályzatait.

>[!Note]
>Ha biztonságosan be szeretné ágyazni a tartalmat egy belső portálon vagy webhelyen, használja a [Beágyazás](service-embed-secure.md) vagy a [Beágyazás a SharePoint online-ban](service-embed-report-spo.md) lehetőséget. Ez biztosítja, hogy minden engedély és adatbiztonság kényszerítve legyen, amikor a felhasználók megtekintik a belső adatokat.

## <a name="how-to-use-publish-to-web"></a>A Webes közzététel használata

**Webes közzététel** érhető el a személyes vagy csoport-munkaterületein szerkesztheti a jelentéseket.  Nem érhető el a jelentéseket osztottak meg Önnel, vagy újakat hagyatkoznia a sorszintű biztonság adatok védelmét. Tekintse meg a [ **korlátozások** ](#limitations) esetek teljes listáját az alábbi szakasz ahol **webes közzététel** nem támogatott. Tekintse át a **figyelmeztetés** használata előtt a cikk elején **webes közzététel**.

A következő *rövid videó* Ez a funkció működését mutatja. Ezt követően próbálja ki az alábbi lépéseket.

<iframe width="560" height="315" src="https://www.youtube.com/embed/UF9QtqE7s4Y" frameborder="0" allowfullscreen></iframe>

A következő útmutató a **Webes közzététel** használatát ismerteti.

1. Nyisson meg egy jelentést, amely szerkesztheti, és válassza ki a munkaterület **fájl > Webes közzététel**.

   ![PtW1](media/service-publish-to-web/publish_to_web1.png)

2. Tekintse át a tartalmat, és válassza a párbeszédpanel **beágyazási kód létrehozása**.

   ![PtW2](media/service-publish-to-web/publish_to_web2_ga.png)

3. Itt látható módon, tekintse át a figyelmeztetést, és győződjön meg arról, hogy az adatok szabadon beágyazhatók-e a nyilvános webhelyeken. Ha igen, válassza ki a **közzététel**.

   ![PtW3](media/service-publish-to-web/publish_to_web3_ga.png)

4. Egy párbeszédpanel jelenik meg a hivatkozást. Ez a hivatkozás küldése e-mailben, beágyazhatja a kódban, például egy IFRAME elembe, vagy illessze be közvetlenül egy weboldalba vagy blogba.

   ![PtW4](media/service-publish-to-web/publish_to_web4.png)

5. Ha korábban létrehozott egy beágyazási kódot a jelentést, és kiválasztja **webes közzététel**, nem jelenik meg a 2 – 4. lépéseket a párbeszédpanelek útmutatásait. Ehelyett a **beágyazási kód** párbeszédpanel jelenik meg:

   ![PtW5](media/service-publish-to-web/publish_to_web5.png)

   Jelentésenként csak egy beágyazási kód hozható létre.


## <a name="tips-and-tricks-for-view-modes"></a>Tippek és trükkök a megtekintési módokhoz

Tartalom egy blogbejegyzésbe ágyaz be, amikor általában egy adott képernyőméret elférnie kell.  A magasságot és a szélességet az iFrame-címkében, igény szerint módosíthatja. Azonban szüksége annak érdekében, hogy a jelentés elférjen a megadott iFrame területet, így a jelentés szerkesztésekor be egy megfelelő megtekintési módot is kell.

A következő táblázat a Megtekintési módokat és azok beágyazott megjelenését ismerteti.

| Megtekintési mód | Beágyazott megjelenés |
| --- | --- |
| ![PtW6b](media/service-publish-to-web/publish_to_web6b.png) |**Laphoz igazítás** a jelentés oldal magasságát és szélességét veszi figyelembe. Ha az oldal, például 16:9 vagy 4:3 "Dinamikus" arányok a tartalom lesz skálázva illeszkedjen a keretbe. Beágyazott IFRAME használatával **laphoz igazítás** eredményezhet **illeszkedést**, ahol szürke hátterű látható iFrame területeken után a tartalom az átméreteződik, hogy illeszkedjen a keretbe. Sávok eltüntetéséhez állítsa be az IFRAME-keret magasságának és szélességének megfelelően. |
| ![PtW6d](media/service-publish-to-web/publish_to_web6d.png) |**Tényleges méret** biztosítja, hogy a jelentés mérete megőrzi a jelentés oldalon lévő készletként. Emiatt jelennek meg az IFrame-keretben görgetősávok jelenhetnek meg. Állítsa be az IFRAME-keret magasságának és szélességének beállításával kerülni a görgetősávok. |
| ![PtW6c](media/service-publish-to-web/publish_to_web6c.png) |**Szélességhez igazítás** biztosítja, hogy a tartalom elférjen az IFRAME elem vízszintes területen. Szegély továbbra is látható, de a tartalom-ig méretezhető használja a vízszintes rendelkezésre álló területre. |

## <a name="tips-and-tricks-for-iframe-height-and-width"></a>Tippek és trükkök az iFrame magasság- és szélesség-beállításaihoz

A **webes közzététel** beágyazási kódot úgy tűnik, az alábbihoz hasonló:

![PtW7](media/service-publish-to-web/publish_to_web7.png)
 
Szerkesztheti a szélességét és magasságát manuálisan kell, hogy pontosan hogyan szeretné, hogy illeszkedjen az oldalon, amelybe beágyazza.

Elérése illeszkedés érdekében megpróbálhat 56 képpontot az IFRAME-keret magasságának megfelelően az alsó sáv a jelenlegi méretét. Ha a jelentésoldala dinamikus méretezést használ, akkor az alábbi táblázatban talál néhány üres sávok nélküli illeszkedést biztosító méretet.

| Képarány | Nagyság | Méret (szélesség × magasság) |
| --- | --- | --- |
| 16:9 |Kicsi |640 × 416 képpont |
| 16:9 |Közepes |800 × 506 képpont |
| 16:9 |Nagy |960 × 596 képpont |
| 4:3 |Kicsi |640 × 536 képpont |
| 4:3 |Közepes |800 × 656 képpont |
| 4:3 |Nagy |960 × 776 képpont |

## <a name="manage-embed-codes"></a>Beágyazási kódok kezelése

Miután létrehozott egy **webes közzététel** beágyazási kódot, kezelheti a kódot a **beállítások** menü a Power bi-ban. Beágyazási kódok kezeléséhez tartozik a Vizualizáció vagy jelentés (a a beágyazási kód Ez használhatatlanná) kódot, eltávolítása vagy a beágyazási kód beolvasása.

1. A **Webes közzétételi** beágyazási kódok kezeléséhez nyissa meg a **Beállítások** fogaskerék-ikont, és válassza a **Beágyazási kódok kezelése** lehetőséget.

   ![PtW8](media/service-publish-to-web/publish_to_web8.png)

2. A beágyazási kódok jelennek meg.

   ![PtW9](media/service-publish-to-web/publish_to_web9.png)

3. Kérje le, vagy egy beágyazási kód törlése. A jelentés vagy Vizualizáció mutató hivatkozásokat törlését is letiltja.

   ![PtW10](media/service-publish-to-web/publish_to_web10.png)

4. Ha **törlése**, a művelet megerősítését kéri.

   ![PtW11](media/service-publish-to-web/publish_to_web11.png)

## <a name="updates-to-reports-and-data-refresh"></a>Jelentések és adatok frissítése

Miután létrehozta a **webes közzététel** beágyazási kódot, és a módosítások frissül az Ez a jelentés megosztása, győződjön meg arról, és a hivatkozás azonnal aktív, és bárki, aki megnyitja is megtekinthetik az alkalmazást. A kezdeti művelet után azonban jelentések vagy Vizualizációk frissítései is igénybe vehet, mielőtt a felhasználók számára láthatóvá váljon körülbelül egy óra. Ha a frissítéseknek azonnal elérhetőknek kell lenniük, akkor törölheti a beágyazási kódot, és létrehozhat egy újat. További tudnivalókért tekintse meg a [ **működését** ](#howitworks) Ez a cikk későbbi szakaszában talál. 

## <a name="data-refresh"></a>Adatfrissítés

Az adatfrissítések automatikusan megjelennek a beágyazott jelentésben vagy vizualizációban. A frissített adatok körülbelül egy óra elteltével lesznek láthatók a beágyazási kódokon keresztül. Automatikus frissítés letiltani, választhat **nem frissülnek** az ütemezés szerint, az adatkészlet a jelentés használja.  

## <a name="custom-visuals"></a>Egyéni vizualizációk

A **Webes közzététel** az egyéni vizualizációkat is támogatja. Ha használ **webes közzététel**, felhasználók, akikkel megosztja a közzétett vizualizációt nem kell egyéni Vizualizációk a jelentés megtekintéséhez.

## <a name="limitations"></a>Korlátozások

**Webes közzététel** támogatják a túlnyomó többsége adatforrásainak, és a Power BI szolgáltatás jelentéseinek azonban a következők **jelenleg nem támogatottak és elérhető** a **webes közzététel** :

- Sorszintű biztonságot használó jelentések.
- Az élő kapcsolatos adatforrásokat (például a helyszíni Analysis Services táblázatost, az Analysis Service Multidimensionalt és az Azure Analysis Servicest) használó jelentések.
- Közvetlenül Önnel vagy céges tartalomcsomagon keresztül megosztott jelentések.
- Olyan csoporthoz tartozó jelentések, amelynek ön nem szerkesztési joggal bíró tagja.
- Az "R" Vizualizációk jelenleg nem támogatottak a **webes közzététel** jelentéseket.
- Adatok exportálása a jelentésekben a vizualizációkban, amely közzé lett téve a weben.
- ArcGIS Maps for Power BI-vizualizációkat.
- A DAX-mértékek jelentésszintű tartalmazó jelentések.
- Egyszeri bejelentkezési adatok modelljeinek lekérdezéséhez.
- [Bizalmas vagy szellemi tulajdont képező információk biztonságos](#publish-to-web-from-power-bi).
- A **Beágyazás** lehetőség automatikus hitelesítés funkciója nem működik a Power BI JavaScript API-jával. A Power BI JavaScript API-hoz a [felhasználó az adatok tulajdonosa](developer/embed-sample-for-your-organization.md) módszert kell használnia. További információ a [felhasználó az adatok tulajdonosa](developer/embed-sample-for-your-organization.md) megközelítésről.

## <a name="tenant-setting"></a>Bérlőbeállítások

A Power BI-rendszergazdák engedélyezheti vagy letilthatja a **webes közzététel** funkció. Akkor is hozzáférést korlátozhatja adott csoportok, amelyek negatív hatással lehet a képességére létrehozzon egy beágyazási kódot.

|Funkció |A teljes cég számára engedélyezve |A teljes cég számára letiltva |Speciális biztonsági csoportok   |
|---------|---------|---------|---------|
|**Webes közzététel** parancs egy jelentés **fájl** menü|Mindenki számára engedélyezve|Nem mindenki számára látható|Csak az arra jogosult felhasználók vagy csoportok láthatják.|
|A **Beágyazási kódok kezelése** funkció a **Beállítások** közt|Mindenki számára engedélyezve|Mindenki számára engedélyezve|Mindenki számára engedélyezve van.<br><br>* A **Törlés** parancsot csak az arra jogosult felhasználók vagy csoportok érik el.<br>* A **Kód lekérése** mindenki számára engedélyezve van.|
|**Beágyazási kódok** a felügyeleti portálon|Az állapot a következő értékeket jelenítheti meg:<br>* Aktív<br>* Nem támogatott<br>* Blokkolva|Az állapot **Letiltva** lesz|Az állapot a következő értékeket jelenítheti meg:<br>* Aktív<br>* Nem támogatott<br>* Blokkolva<br><br>Ha egy felhasználónak nincs megfelelő jogosultsága a bérlői beállítások alapján, akkor az állapot **Megsértve** lesz.|
|Meglévő közzétett jelentések|Minden engedélyezve|Minden letiltva|A jelentések továbbra is megjelennek mindenki számára.|

## <a name="understanding-the-embed-code-status-column"></a>A beágyazási kód állapota oszlop ismertetése

A **beágyazási kódok kezelése** oldalon egy állapot oszlop is tartalmaz. Alapértelmezés szerint a beágyazási kódok vannak **aktív**, de az alábbi állapotok valamelyikét is lehet.

| Állapot | Leírás |
| --- | --- |
| **Aktív** |A jelentés elérhető, megtekinthető és használható a felhasználók számára az Interneten. |
| **Blokkolva** |A jelentés tartalma sérti a [Power BI használati feltételeit](https://powerbi.microsoft.com/terms-of-service). A Microsoft blokkolta azt. Ha úgy véli, hogy a tartalom blokkolása indokolatlan, akkor lépjen kapcsolatba a támogatási szolgálattal. |
| **Nem támogatott** |A jelentés adatkészlete sorszintű biztonságot vagy más nem támogatott konfigurációt használ. Tekintse meg a [ **korlátozások** ](#limitations) teljes listáját a következő szakaszban. |
| **Megsértve** |A beágyazási kód a bérlői házirend hatókörén kívül esik. Ez általában akkor fordul elő, amikor egy beágyazási kód létrehozása, majd a **webes közzététel** bérlői beállítás módosítva lett, a felhasználó a beágyazási kódot a tulajdonos kizárása. Ha a bérlői beállítás le van tiltva, vagy a felhasználó már nem hozhatnak létre beágyazási kódok, a meglévő beágyazási kódok show- **megsértve** állapotát. |

## <a name="how-to-report-a-concern-with-publish-to-web-content"></a>Webes közzététel tartalmával kapcsolatos észrevétel jelentése

A jelentés egy adott problémakörrel kapcsolatos **webes közzététel** egy weboldalba vagy blogba beágyazott tartalommal, használja a **jelző** ikonra az alsó sáv, az alábbi képen látható módon. Rendszer e-mailt küldeni a Microsoftnak, hogy elmagyarázza a potenciálisan veszélyes. A Microsoft értékeli a tartalmat a Power BI szolgáltatási feltételei alapján, és a megfelelő lépéseket.

Kapcsolatos észrevétel jelentése, válassza ki a **jelző** alsó sávján lévő ikonra a **webes közzététel** lát jelentést.

![PtW12](media/service-publish-to-web/publish_to_web12_ga.png)

## <a name="licensing-and-pricing"></a>Licencelés és Díjszabás

A **Webes közzétételt** csak Microsoft Power BI-felhasználók használhatják. A jelentés megtekintői nem kell Power BI-felhasználóknak lenniük.

<a name="howitworks"></a>
## <a name="how-it-works-technical-details"></a>Hogyan működik? (technikai részletek)

Amikor hoz létre egy beágyazási kódot a **webes közzététel**, a jelentés láthatóvá válik a internetes felhasználók. Érhető el nyilvánosan, így megjelenítők egyszerűen oszthat meg a jelentést a közösségi média a későbbiekben várható. Amikor a felhasználók a közvetlen nyilvános URL-cím megnyitásával vagy egy weboldalba vagy blogba beágyazottan megtekintik a jelentést, akkor a Power BI gyorsítótárazza a jelentés definícióját és a jelentés megtekintéséhez szükséges lekérdezések eredményeit. Ez biztosítja, hogy az egyidejű felhasználók ezreit teljesítmény befolyásolása nélkül is megtekintheti a jelentést.

A gyorsítótár hosszú élettartamú, nem, így ha módosítja a jelentés definícióját (például, ha megváltoztatja a megtekintési módját), vagy frissítse a jelentés adatait, körülbelül egy óra elteltével a módosítások megjelennek a jelentésben megtekintheti a felhasználók verziója is igénybe vehet. Éppen ezért ajánlott előre elkészíteni a munkáját, és a **Webes közzétételi** beágyazási kódot csak akkor létrehozni, amikor már elégedett a beállításokkal.

## <a name="next-steps"></a>Következő lépések

- [SharePoint Online jelentéskijelző](service-embed-report-spo.md) 

- [Jelentés beágyazása egy biztonságos portálon vagy webhelyen](service-embed-secure.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
