---
title: Elemzések megosztása és történetek felépítése a Power BI Desktop könyvjelzőivel
description: A Power BI Desktop könyvjelzői segítségével elmentheti a jelentések nézeteit és beállításait, valamint történetszerű bemutatókat hozhat létre
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/18/2019
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: b986b86642e5ac3e6a8394010bf27922daaf5ea7
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "81439917"
---
# <a name="create-bookmarks-in-power-bi-desktop-to-share-insights-and-build-stories"></a>Könyvjelzők létrehozása a Power BI Desktopban elemzések megosztásához és történetek felépítéséhez
A Power BI-ban a *könyvjelzők* használatával rögzítheti az egyes jelentésoldalak aktuális nézetkonfigurációját, beleértve a szűréseket és a vizualizációk állapotát. A mentett könyvjelző kiválasztásával később visszatérhet az állapothoz. 

Egy tetszőleges sorrendbe rendezett teljes könyvjelzőgyűjteményt is létrehozhat, majd ezeket sorban megnyitva egy olyan bemutatót állíthat össze, amelyben lényegi összefüggések sorozatát mutathatja be, vagy előadhatja azt a történetet, amelyet a vizualizációkkal és a jelentésekkel be szeretne mutatni. 

![A Power BI könyvjelzői](media/desktop-bookmarks/bookmarks_01.png)

A könyvjelzőknek rengeteg felhasználási módja létezik. A könyvjelzők segítségével például nyomon követheti, hogy hol tart épp a jelentések készítésében (a könyvjelzők hozzáadása, törlése és átnevezése nem bonyolult dolog), illetve létrehozhat belőlük egy PowerPoint-szerű bemutatót is, amely a könyvjelzőkön végigléptetve bemutat egy történetet a jelentésen keresztül. 

> [!TIP]
> Tudnivalók a Power BI-beli személyes könyvjelzők használatáról: [Személyes könyvjelzők bejelentése a Power BI szolgáltatásban](https://powerbi.microsoft.com/blog/announcing-personal-bookmarks-in-the-power-bi-service/). 

## <a name="using-bookmarks"></a>A könyvjelzők használata
A könyvjelzők használatához válassza a Power BI Desktop menüszalagon a **Nézet** lapot, majd válassza a **Könyvjelzők panelt**. 

![A Könyvjelzők panel bekapcsolása](media/desktop-bookmarks/bookmarks_03.png)

A létrehozott könyvjelzőkhöz a rendszer a következő elemeket menti:

* Az aktuális oldal
* Szűrők
* Szeletelők, szeletelőtípusok (például legördülő menü vagy lista), valamint szeletelőállapot
* A vizualizáció kiválasztásának állapota (például szűrők keresztikemelése)
* A rendezés iránya
* A részletezés helye
* Objektumok láthatósága (a **Kiválasztás** panel használatával)
* A látható objektumok fókusz vagy **Reflektorfény** módja

Állítson be egy jelentésoldalt úgy, amilyen állapotban a könyvjelzővel menteni szeretné. Miután a jelentésoldalt és a vizualizációkat a kívánt módon elrendezte, a könyvjelző hozzáadásához kattintson a **Könyvjelzők** panel **Hozzáadás** gombjára. 

![Könyvjelző hozzáadása](media/desktop-bookmarks/bookmarks_04.png)

A Power BI Desktop létrehoz egy könyvjelzőt, amelynek egy általános nevet ad. A könyvjelzőket könnyen **átnevezheti**, **törölheti** vagy **frissítheti**, ha a könyvjelző neve melletti három pontra kattint, majd kiválasztja a megfelelő műveletet a megjelenő menüből.

![A három pont használatával válassza a könyvjelzők menüt](media/desktop-bookmarks/bookmarks_05.png)

Miután létrehozott egy könyvjelzőt, a megjelenítéséhez válassza ki a **Könyvjelzők** panelen. 

Azt is kiválaszthatja, hogy minden könyvjelző alkalmazzon **adattulajdonságokat**, például szűrőket és szeletelőket; **megjelenítési** tulajdonságokat, például reflektorfényt és annak láthatóságát; valamint az **aktuális oldal** módosításait, amelyek a könyvjelző hozzáadásakor látható oldalt jelenítik meg. Ezek a funkciók akkor hasznosak, ha könyvjelzőkkel vált a jelentésnézetek és a kiválasztott vizualizációk között, ekkor ugyanis célszerű kikapcsolni az adattulajdonságokat, hogy a szűrők ne álljanak alaphelyzetbe, ha a felhasználók egy könyvjelző kiválasztásával váltanak nézetet. 

Az ilyen módosítások elvégzéséhez válassza a könyvjelző neve melletti három pontot, majd jelölje be az **Adatok**, **Megjelenítés** és egyéb vezérlők melletti jelölőnégyzeteket, vagy törölje a jelölésüket. 

## <a name="arranging-bookmarks"></a>A könyvjelzők rendezése
Előfordulhat, hogy a könyvjelzőket más sorrendben hozza létre, mint amilyenben aztán be szeretné őket mutatni. Ez nem jelent problémát, mivel a könyvjelzőket könnyedén átrendezheti.

- A **Könyvjelzők** panelen áthúzással módosítsa a könyvjelzők sorrendjét. 

   A könyvjelzők közötti sárga vonal jelzi a helyet, ahová az elhúzott könyvjelző kerülni fog.

   ![Könyvjelzők sorrendjének módosítása áthúzással](media/desktop-bookmarks/bookmarks_06.png)

A könyvjelzők sorrendje a könyvjelzők **Nézet** funkciójának használatakor lehet fontos, amint arra a következő szakasz kitér.

## <a name="bookmarks-as-a-slide-show"></a>Diavetítés a könyvjelzőkkel
Ha van több könyvjelzője, amelyeket sorrendben be szeretne mutatni, a **Könyvjelzők** panel **Nézet** gombjának kiválasztásával indíthatja el a diavetítést.

A **Nézet** módban érdemes odafigyelni a néhány dologra.

   ![Könyvjelző címsorának elemei](media/desktop-bookmarks/bookmarks_07.png)

1. A könyvjelző neve a könyvjelző címsorában látható a vászon alján.

2. A könyvjelző címsorában lévő nyilakkal léptethet előre és hátra a könyvjelzők között.

3. A **Nézet** módból a **Könyvjelzők** panel **Kilépés** gombjával, vagy a könyvjelzők címsorán található **X** gombbal léphet ki. 

A **Nézet** módban bezárhatja a **Könyvjelzők** panelt a panel **X** gombjára kattintva, így több hely marad a bemutatónak. A **Nézet** módban az összes vizualizáció interaktívan kezelhető, és keresztkiemelést is lehet alkalmazni, ahogy közvetlen használat során is. 

## <a name="visibility-using-the-selection-pane"></a>Láthatóság: A Kiválasztás panel használata
A **Könyvjelzők** panelhez kapcsolódó **Kiválasztás** panel az aktuális oldalon lévő összes objektum listáját jeleníti meg, és lehetővé teszi az egyes objektumok kiválasztását és láthatóságának beállítását. 

![A Kiválasztás panel engedélyezése](media/desktop-bookmarks/bookmarks_08.png)

A **Kiválasztás** panelen kiválaszthat egy objektumot, és az objektum jobb oldalán lévő szem ikonra kattintva ki- és bekapcsolhatja az adott objektum láthatóságát. 

![Kiválasztás panel](media/desktop-bookmarks/bookmarks_09.png)

A könyvjelzők hozzáadásakor a rendszer az egyes objektumok láthatósági állapotát is menti a **Kiválasztás** panelen megadott beállítások szerint. 

Érdemes megjegyezni, hogy a szeletelők a láthatósági állapotuktól függetlenül szűrik a jelentésoldalt. Így számos különböző könyvjelzőt hozhat létre különböző szeletelőbeállításokkal, és az adott jelentésoldal sokféleképpen jelenhet meg (és különböző lényegi összefüggésekre mutathat rá) a különböző könyvjelzőkön.

## <a name="bookmarks-for-shapes-and-images"></a>Alakzatok és képek könyvjelzői
Alakzatokat és képeket is hozzárendelhet a könyvjelzőkhöz. Ezzel a funkcióval, ha kiválaszt egy objektumot, megjelenik az adott objektumhoz rendelt könyvjelző. Ez a funkció különösen hasznos lehet akkor, ha gombokat használ. További információt a [Gombok használata a Power BI-ban](desktop-buttons.md) című cikkben talál. 

Egy könyvjelző objektumhoz rendeléséhez: 

1. Jelölje ki az objektumot a jelentésvásznon. Ezután a megjelenő **Alakzat formázása** panelen kapcsolja **BE** állásba a **Művelet** kapcsolót.

2. Bontsa ki a **Művelet** szakaszt. A **Típus** területen válassza ki a **Könyvjelző** lehetőséget.

3. A **Könyvjelzők** területen válasszon ki egy könyvjelzőt.

   ![Könyvjelző-hivatkozás hozzárendelése egy objektumhoz](media/desktop-bookmarks/bookmarks_10.png)

Az objektumokhoz rendelt könyvjelzőknek számos felhasználási módja van. Létrehozhat egy látványos tartalomjegyzéket a jelentésoldalon, vagy különböző nézeteket (például különféle vizualizációtípusokat) mutathat be ugyanazokról az adatokról.

A szerkesztési módban nyomja le a **Ctrl** billentyűt, és jelölje ki a hivatkozást annak megnyitásához. A szerkesztési módon kívül elég rákattintani az objektumra a hivatkozás megnyitásához. 

## <a name="bookmark-groups"></a>Könyvjelzőcsoportok

A Power BI Desktop 2018. augusztusi kiadásától kezdve könyvjelzőcsoportokat is létrehozhat és használhat. A könyvjelzőcsoport az Ön által létrehozott könyvjelzők gyűjteménye, amelyeket csoportokba gyűjtve jeleníthet meg. 

Könyvjelzőcsoport létrehozásához: 
1. Nyomja le a **Ctrl** billentyűt, és válassza ki a csoportba felvenni kívánt könyvjelzőket. 

2. Válassza ki a kijelölt könyvjelzők melletti három pontot, majd a megjelenő menüben válassza a **Csoport** elemet.

   ![Könyvjelzőcsoport létrehozása](media/desktop-bookmarks/bookmarks_15.png)

A Power BI Desktop a csoportnak automatikusan a *Csoport 1* nevet adja. A név melletti három pontra kattintva kiválaszthatja az **Átnevezés** lehetőséget, és átnevezheti a csoportot, amire csak szeretné.

![Könyvjelzőcsoport átnevezése](media/desktop-bookmarks/bookmarks_16.png)

Mint minden könyvjelzőcsoport esetén, a könyvjelzőcsoport nevének kibontása csak a könyvjelzők csoportjának kibontására és összecsukására szolgál, és a név nem jelöl konkrét könyvjelzőket. 

A könyvjelzők **Megjelenítés** funkciójának használatakor az alábbi részletek érvényesek:

* Ha a kiválasztott könyvjelző egy könyvjelzőcsoport tagja, a **Megjelenítés** választásakor csak *az adott csoport* könyvjelzői jelennek meg. 

* Ha a kiválasztott könyvjelző nem csoport, vagy ha a csoport legfelső szintjén található (például a könyvjelzőcsoport nevéről van szó), akkor a jelentés összes könyvjelzője megjelenik, azok is, amelyek valamelyik csoporthoz tartoznak. 

Könyvjelzők csoportosításának megszüntetése: 
1. Válassza ki egy csoport bármelyik könyvjelzőjét, és kattintson az amellett lévő három pontra. 

2. A megjelenő helyi menüben válassza a **Csoportosítás megszüntetése** lehetőséget.

   ![Könyvjelzőcsoport csoportosításának megszüntetése](media/desktop-bookmarks/bookmarks_17.png)

   Ha egy csoport bármely könyvjelzőjénél a **Csoportosítás megszüntetése** funkciót használja, azzal minden könyvjelzőt eltávolít a csoportból; a művelet törli a csoportot, de nem törli magukat a könyvjelzőket. 

Ha csupán egyetlen könyvjelzőt szeretne eltávolítani a csoportból: 
1. Válassza a **Csoportosítás megszüntetése** lehetőséget az adott csoport bármely könyvjelzőjénél, amely megszünteti a csoportot. 

2. Válassza ki az új csoportba felvenni kívánt könyvjelzőket (**Ctrl** + az egyes könyvjelzőkre való kattintással), majd válassza újra a **Csoportosítás** lehetőséget. 


## <a name="using-spotlight"></a>A reflektorfény használata
A könyvjelzőkkel egy időben bevezetett másik funkció a *reflektorfény*. A reflektorfénnyel felhívhatja például a figyelmet egy adott diagramra, amikor a könyvjelzőket **Nézet** módban mutatja be.

Lássuk, miben különbözik a reflektorfény a fókusz módtól:

1. Fókusz módban kiválaszthatja a vizualizáció **Fókusz mód** ikonját, aminek eredményeként a vizualizáció kitölti a teljes vásznat.

2. A reflektorfény esettében kiválaszthatja a **Reflektorfény** elemet a vizualizációhoz tartozó három pontra kattintva, hogy az eredeti méretében emelhessen ki egy vizualizációt azáltal, hogy az oldalon lévő összes többi vizualizációt majdnem teljesen elhalványítja. 

![A reflektorfény összehasonlítása a fókusz móddal](media/desktop-bookmarks/bookmarks_11.png)

Ha kijelöli az előző képen látható vizualizáció **Fókusz mód** ikonját, az oldal a következőképpen jelenik meg:

![Fókusz mód](media/desktop-bookmarks/bookmarks_12.png)

Ezzel szemben, ha a vizualizáció menüjében (...) a **Reflektorfény** elemre kattint, az oldal így néz majd ki:

![Reflektorfény mód](media/desktop-bookmarks/bookmarks_13.png)

Ha egy könyvjelző hozzáadásakor a fókusz vagy a reflektorfény mód be van kapcsolva, a könyvjelző megőrzi a beállítást.

## <a name="bookmarks-in-the-power-bi-service"></a>A könyvjelzők a Power BI szolgáltatásban
Ha egy, a Power BI szolgáltatásban közzétett jelentés tartalmaz könyvjelzőket, azokat a Power BI szolgáltatásban is megtekintheti és használhatja. Ha a jelentés tartalmaz könyvjelzőket, akkor a **Kiválasztás** és a **Könyvjelzők** paneleket a **Nézet** > **Kiválasztás panel** vagy a **Nézet** > **Könyvjelzők panel** lehetőség kiválasztásával jelenítheti meg. 

![A Könyvjelzők és a Kiválasztás panel megjelenítése a Power BI szolgáltatásban](media/desktop-bookmarks/bookmarks_14.png)

A **Könyvjelzők** panel ugyanúgy működik a Power BI szolgáltatásban, mint a Power BI Desktopban. Itt is le tudja játszani a könyvjelzőket diavetítésként a **Nézet** kiválasztásával.

A könyvjelzők között a könyvjelzők szürke címsorán léptethet, és nem a fekete nyilakkal. (A fekete nyilak a jelentésoldalak, és nem a könyvjelzők közötti váltásra szolgálnak.)

## <a name="enable-the-bookmarks-preview-versions-prior-to-march-2018"></a>A könyvjelzők előzetes verziójának engedélyezése (a 2018. márciusinál korábbi verziók esetében)
A Power BI Desktop 2018. márciusi verziójától kezdve a könyvjelzőkezelési funkció általánosan elérhető. 

Mindig ajánlott a legújabb kiadásra frissíteni. Ha mégis a Power BI Desktop korábbi verzióját használja, a könyvjelzőkezelési funkció a 2017. októberi kiadással vált elérhetővé a Power BI Desktopban, valamint a könyvjelző-kompatibilis jelentésekben a Power BI szolgáltatásban. 

A könyvjelzők előzetes verziójának engedélyezése: 

1. Válassza ki a **Fájl** > **Lehetőségek és beállítások** > **Lehetőségek** > **Előzetes verziójú funkciók** lehetőséget, majd válassza a **Könyvjelzők** lehetőséget. 

   ![A könyvjelzők engedélyezése a Beállítások ablakban](media/desktop-bookmarks/bookmarks_02.png)

2. A könyvjelzők előzetes verziójának engedélyezése után indítsa újra a Power BI Desktopot.

## <a name="limitations-and-considerations"></a>Korlátozások és szempontok
A könyvjelzőkezelési funkciók aktuális kiadásának használatára vonatkozik néhány korlátozás és egyéb szempont.

* A legtöbb Power BI-vizualizáció zökkenőmentesen működik a könyvjelzőkkel. Ha hibát tapasztal egy könyvjelző és egy egyéni vizualizáció használatakor, lépjen kapcsolatba az egyéni vizualizáció létrehozójával, és kérje meg, hogy szolgáltasson támogatást a könyvjelzőkhöz. 
* Ha egy vizualizációt a könyvjelző létrehozását követően ad hozzá a jelentésoldalhoz, a vizualizáció az alapértelmezett állapotában jelenik meg. Ez azt jelenti, hogy ha egy olyan oldalra vesz fel szeletelőt, ahol már hozott létre könyvjelzőket, a szeletelő az alapértelmezett állapotának megfelelően viselkedik majd.
* Ha a vizualizációkat a könyvjelzők létrehozását követően áthelyezi, a változást a könyvjelzők automatikusan tükrözni fogják. 

## <a name="next-steps"></a>Következő lépések
A könyvjelzőkhöz hasonló vagy azokkal együtt használható funkciókkal kapcsolatos részletesebb információkat az alábbi cikkekben talál:

* [Részletezés használata a Power BI Desktopban](desktop-drillthrough.md)
* [Irányítópult-csempe vagy jelentésvizualizáció megjelenítése fókusz módban](consumer/end-user-focus.md)

