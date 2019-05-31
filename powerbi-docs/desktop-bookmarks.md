---
title: Könyvjelzők használata a Power BI-ban
description: A Power BI Desktop könyvjelzői segítségével elmentheti a jelentések nézeteit és beállításait, valamint történetszerű bemutatókat hozhat létre
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/22/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 59d5ccd6a7179ca4c44210854fb66abb5371ac6c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61325934"
---
# <a name="use-bookmarks-to-share-insights-and-build-stories-in-power-bi"></a>Elemzések megosztása és történetek felépítése a Power BI könyvjelzőivel 
A Power BI-ban a **könyvjelzők** használatával rögzítheti az egyes jelentésoldalak aktuális nézetkonfigurációját, beleértve a szűréseket és a vizualizációk állapotát, hogy később egyszerűen a mentett könyvjelzőre kattintva visszaállíthassa az adott állapotot. 

Egy tetszőleges sorrendbe rendezett teljes könyvjelzőgyűjteményt is létrehozhat, majd ezeket sorban megnyitva egy olyan bemutatót állíthat össze, amelyben lényegi összefüggések sorozatát mutathatja be, vagy előadhatja azt a történetet, amelyet a vizualizációkkal és a jelentésekkel be szeretne mutatni. 

![A Power BI könyvjelzői](media/desktop-bookmarks/bookmarks_01.png)

A könyvjelzőknek rengeteg felhasználási módja létezik. A segítségükkel nyomon követheti, hogy hol tart épp a jelentések készítésében (a könyvjelzők hozzáadása, törlése és átnevezése nem bonyolult dolog), illetve létrehozhat belőlük egy PowerPoint-szerű bemutatót is, amely a könyvjelzőkön végigléptetve bemutat egy történetet a jelentésen keresztül. Természetesen más alkalmazási területek is elképzelhetőek aszerint, hogy Ön mire szeretné leginkább használni a könyvjelzőket.

> [!TIP]
> A Power BI szolgáltatásbeli személyes könyvjelzők használatáról a személyes könyvjelzők funkciót bejelentő [blogbejegyzésben](https://powerbi.microsoft.com/blog/announcing-personal-bookmarks-in-the-power-bi-service/) olvashat. 

### <a name="enable-the-bookmarks-preview-versions-prior-to-march-2018"></a>A könyvjelzők előzetes verziójának engedélyezése (a 2018. márciusinál korábbi verziók esetében)
A Power BI Desktop 2018. márciusi verziójától kezdve a könyvjelzőkezelési funkció általánosan elérhető. 

Mindig ajánlott a legújabb kiadásra frissíteni. Ha mégis a Power BI Desktop korábbi verzióját használja, a **könyvjelzőkezelési** funkció a **2017. októberi** kiadással vált elérhetővé a **Power BI Desktopban**, valamint a könyvjelző-kompatibilis jelentésekben a **Power BI szolgáltatásban**. Az előzetes verziójú funkció engedélyezéséhez válassza a **Fájl > Lehetőségek és beállítások > Beállítások > Előzetes verziójú funkciók** lehetőséget, majd jelölje be a **Könyvjelzők** elem melletti jelölőnégyzetet. 

![A könyvjelzők engedélyezése a Beállítások ablakban](media/desktop-bookmarks/bookmarks_02.png)

A könyvjelzőkezelési funkció előzetes verziójának engedélyezése után újra kell indítania a **Power BI Desktopot**.

## <a name="using-bookmarks"></a>A könyvjelzők használata
A könyvjelzők használatához lépjen a **Nézet** menüszalagra, majd jelölje be a **Könyvjelzők panel** jelölőnégyzetét. 

![A Könyvjelzők panel megjelenítésének bekapcsolása a Nézet menüszalagon.](media/desktop-bookmarks/bookmarks_03.png)

A létrehozott könyvjelzőkhöz a rendszer a következő elemeket menti:

* Az aktuális oldal
* Szűrők
* Szeletelők, szeletelőtípusok (például legördülő menü vagy lista), valamint szeletelőállapot
* A vizualizáció kiválasztásának állapota (például szűrők keresztikemelése)
* A rendezés iránya
* A részletezés helye
* Láthatóság (az egyes objektumoké, a **Kiválasztás** panel használatával)
* A látható objektumok fókusz vagy **Reflektorfény** módja

Állítson be egy jelentésoldalt úgy, amilyen állapotban a könyvjelzővel menteni szeretné. Miután a jelentésoldalt és a vizualizációkat a kívánt módon elrendezte, a könyvjelző hozzáadásához válassza a **Könyvjelzők** panel **Hozzáadás** gombját. 

![Könyvjelző hozzáadása](media/desktop-bookmarks/bookmarks_04.png)

A **Power BI Desktop** létrehoz egy könyvjelzőt, amelynek egy általános nevet ad. A könyvjelzőket könnyen *átnevezheti*, *törölheti* vagy *frissítheti*, ha a könyvjelző neve melletti három pontra kattint, majd kiválasztja a megfelelő műveletet a megjelenő menüből.

![Könyvjelző almenüjének kiválasztása a három pontra kattintva](media/desktop-bookmarks/bookmarks_05.png)

Miután létrehozott egy könyvjelzőt, a megjelenítéséhez egyszerűen kattintson rá a **Könyvjelzők** panelen. 

Azt is megadhatja, hogy az egyes könyvjelzők alkalmazzák-e az *adattulajdonságokat*, például a szűrőket és a szeletelőket, valamint a *megjelenítési* tulajdonságokat, például a reflektorfényt és annak láthatóságát, illetve a könyvjelző hozzáadásakor látható oldalt bemutató oldalmódosításokat. Ezek a funkciók akkor lehetnek hasznosak, ha könyvjelzőkkel vált a jelentésnézetek és a kiválasztott vizualizációk között – ekkor ugyanis célszerű kikapcsolni az adattulajdonságokat, így a szűrők nem állnak alaphelyzetbe, ha a felhasználók nézetet váltanak egy könyvjelző kiválasztásával. 

A módosítások elvégzéséhez kattintson a könyvjelző neve melletti három pontra (ahogyan azt az előző képen láthatja), majd jelölje be vagy törölje a jelölést az *Adatok*, *Megjelenítés*, és egyéb vezérlők jelölőnégyzeteiből. 

## <a name="arranging-bookmarks"></a>A könyvjelzők rendezése
Előfordulhat, hogy a könyvjelzőket nem olyan sorrendben hozza létre, amilyenben aztán be szeretné őket mutatni. Ez nem jelent problémát, mivel a könyvjelzőket könnyedén átrendezheti.

A **Könyvjelzők** panelen egyszerűen húzza át a könyvjelzőket a megfelelő sorrendbe, amint az alábbi képen is látható. A könyvjelzők közötti sárga vonal jelzi a helyet, ahová az elhúzott könyvjelző kerülni fog.

![Könyvjelzők sorrendjének módosítása áthúzással](media/desktop-bookmarks/bookmarks_06.png)

A könyvjelzők sorrendje a könyvjelzők **Nézet** funkciójának használatakor nyer jelentőséget, amint arra a következő szakasz kitér.

## <a name="bookmarks-as-a-slide-show"></a>Diavetítés a könyvjelzőkkel
Ha van több könyvjelzője, amelyeket sorrendben be szeretne mutatni, a **Könyvjelzők** panel **Nézet** gombjának kiválasztásával indíthatja el a diavetítést.

A **Nézet** módban érdemes odafigyelni a következőkre:

1. A könyvjelző neve a könyvjelző címsorában látható a vászon alján.
2. A könyvjelző címsorában lévő nyilakkal léptethet előre és hátra a könyvjelzők között.
3. A **Nézet** módból a **Könyvjelzők** panel **Kilépés** gombjával, vagy a könyvjelzők címsorán található **X** gombbal léphet ki. 

![Könyvjelző címsorának elemei](media/desktop-bookmarks/bookmarks_07.png)

A **Nézet** módban bezárhatja a **Könyvjelzők** panelt (a panel X gombjára kattintva), így több hely marad a bemutatónak. A **Nézet** módban az összes vizualizáció interaktívan kezelhető, és keresztkiemelést is lehet alkalmazni, ahogy a normál használat során is. 

## <a name="visibility---using-the-selection-pane"></a>Láthatóság – a Kiválasztás panel használatával
A könyvjelzőkkel együtt az új **Kiválasztás** panel is bevezetésre kerül. A **Kiválasztás** panel az aktuális oldalon lévő összes objektum listáját jeleníti meg, és lehetővé teszi az egyes objektumok kiválasztását és láthatóságának beállítását. 

![A Kiválasztás panel engedélyezése](media/desktop-bookmarks/bookmarks_08.png)

A **Kiválasztás** panelen kiválaszthatja az egyes objektumokat. Az egyes vizualizációk jobb oldalán lévő szem ikonra kattintva azt is ki- és bekapcsolhatja, hogy az adott objektum látható legyen-e. 

![Kiválasztás panel](media/desktop-bookmarks/bookmarks_09.png)

A könyvjelzők hozzáadásakor a rendszer az egyes objektumok láthatósági állapotát is menti a **Kiválasztás** panelen megadott beállítások szerint. 

Érdemes megjegyezni, hogy a **szeletelők** a láthatósági állapotuktól függetlenül szűrik a jelentésoldalt. Így számos különböző könyvjelzőt hozhat létre különböző szeletelőbeállításokkal, és az adott jelentésoldal sokféleképpen jelenhet meg (és különböző lényegi összefüggésekre mutathat rá) a különböző könyvjelzőkön.

## <a name="bookmarks-for-shapes-and-images"></a>Alakzatok és képek könyvjelzői
Alakzatokat és képeket is hozzárendelhet a könyvjelzőkhöz. Ezzel a funkcióval, ha egy objektumra kattint, megjelenik az adott objektumhoz rendelt könyvjelző. Ez különösen hasznos lehet akkor, ha gombokkal dolgozik. Erről további információt a [Gombok használata a Power BI-ban](desktop-buttons.md) című cikkben találhat. 

Egy könyvjelző objektumhoz rendeléséhez jelölje ki az objektumot, majd bontsa ki a **Művelet** szakaszt az **Alakzat formázása** panelen, amint az alábbi képen is látható.

![Könyvjelző-hivatkozás hozzárendelése egy objektumhoz](media/desktop-bookmarks/bookmarks_10.png)

Miután **Be** állásba kapcsolta a **Művelet** kapcsolót, kiválaszthatja, hogy az objektum egy vissza gomb, egy könyvjelző vagy egy Q&A-parancs legyen-e. Ha a könyvjelzőt választja, megadhatja, hogy a meglévő könyvjelzők közül melyikhez legyen az objektum rendelve.

Az objektumokhoz rendelt könyvjelzőknek számos felhasználási módja van. Létrehozhat egy látványos tartalomjegyzéket a jelentésoldalon, vagy egyszerűen az egyes objektumokra kattintva különböző nézeteket (például különféle vizualizációtípusokat) mutathat be ugyanazokról az adatokról.

A szerkesztési módban Ctrl+kattintással nyithatja meg a hivatkozásokat, a szerkesztési módon kívül pedig elég rákattintani az objektumra. 

## <a name="bookmark-groups"></a>Könyvjelzőcsoportok

A **Power BI Desktop** 2018. augusztusi kiadásától kezdve könyvjelzőcsoportokat is létrehozhat és használhat. A könyvjelzőcsoport az Ön által létrehozott könyvjelzők gyűjteménye, amelyeket csoportokba gyűjtve jeleníthet meg. 

Könyvjelzőcsoport létrehozásához a CTRL billentyű lenyomva tartása mellett válassza ki a csoportba foglalandó könyvjelzőket, majd kattintson valamelyik kijelölt könyvjelző mellett a három pontra, és a megjelenő menüben válassza a **Csoportosítás** lehetőséget.

![Könyvjelzőcsoport létrehozása](media/desktop-bookmarks/bookmarks_15.png)

A **Power BI Desktop** a csoportnak automatikusan a *Csoport 1* nevet adja. Az átnevezéshez egyszerűen kattintson a névre, és adja meg a használni kívánt új nevet.

![Könyvjelzőcsoport átnevezése](media/desktop-bookmarks/bookmarks_16.png)

Ha a könyvjelzőcsoport nevére kattint, akkor a könyvjelzőcsoportot kibonthatja vagy összecsukhatja, a név nem jelöl konkrét könyvjelzőket. 

A könyvjelzők **Megjelenítés** funkciójának használatakor az alábbiak érvényesek:

* Ha a kiválasztott könyvjelző egy könyvjelzőcsoport tagja, a **Megjelenítés** választásakor csak *az adott csoport* könyvjelzői jelennek meg. 

* Ha a kiválasztott könyvjelző nem csoport, vagy ha a csoport legfelső szintjén található (például a könyvjelzőcsoport nevéről van szó), akkor a jelentés összes könyvjelzője megjelenik, azok is, amelyek valamelyik csoporthoz tartoznak. 

A könyvjelzők csoportosításának megszüntetéséhez válassza ki a csoport bármelyik könyvjelzőjét, kattintson a három pontra, majd a megjelenő menüben válassza a **Csoportosítás megszüntetése** lehetőséget. 

![Könyvjelzőcsoport csoportosításának megszüntetése](media/desktop-bookmarks/bookmarks_17.png)

Vegye figyelembe, hogy ha egy csoport bármely könyvjelzőjénél a **Csoportosítás megszüntetése** funkciót használja, azzal minden könyvjelzőt eltávolít a csoportból. (A művelet törli a csoportot, de nem törli magukat a könyvjelzőket.) Ha csupán egyetlen könyvjelzőt szeretne eltávolítani a csoportból, akkor válassza a **Csoportosítás megszüntetése** lehetőséget az adott csoport bármely könyvjelzőjénél, amely megszünteti a csoportot. Ezt követően válassza ki az új csoportba felvenni kívánt könyvjelzőket (CTRL + az egyes könyvjelzőkre való kattintással), majd válassza újra a **Csoportosítás** lehetőséget. 


## <a name="using-spotlight"></a>A Reflektorfény használata
A könyvjelzőkkel egy időben bevezetett másik funkció a **Reflektorfény**. A **Reflektorfénnyel** felhívhatja például a figyelmet egy adott diagramra, amikor a könyvjelzőket **Nézet** módban mutatja be.

Lássuk, miben különbözik a **Reflektorfény** a **fókusz** módtól.

1. **Fókusz** módban egyetlen vizualizáció tölti ki a teljes vásznat, ha a **fókusz mód** ikonra kattint.
2. A **Reflektorfény** használatával viszont az eredeti méretében emelheti ki a vizualizációt azáltal, hogy az oldalon lévő összes többi vizualizációt majdnem teljesen elhalványítja. 

![A fókusz mód és a reflektorfény összehasonlítása](media/desktop-bookmarks/bookmarks_11.png)

Ha az előző képen látható vizualizáció **fókusz** ikonjára kattintunk, az oldal így fog kinézni:

![fókusz mód](media/desktop-bookmarks/bookmarks_12.png)

Ezzel szemben, ha a vizualizáció menüjében (...) a **Reflektorfény** elemre kattint, az oldal így néz majd ki:

![reflektorfény mód](media/desktop-bookmarks/bookmarks_13.png)

Ha egy könyvjelző hozzáadásakor bármelyik mód (fókusz vagy reflektorfény) be van kapcsolva, a könyvjelző megőrzi a beállítást.

## <a name="bookmarks-in-the-power-bi-service"></a>A könyvjelzők a Power BI szolgáltatásban
Ha egy, a **Power BI szolgáltatásban** közzétett jelentés tartalmaz könyvjelzőket, azokat a **Power BI szolgáltatásban** is megtekintheti és használhatja. Ha a jelentés tartalmaz könyvjelzőket, a vonatkozó paneleket a **Nézet > Kiválasztás panel** vagy a **Nézet > Könyvjelzők panel** kiválasztásával jelenítheti meg.

![A Könyvjelzők és a Kiválasztás panel megjelenítése a Power BI szolgáltatásban](media/desktop-bookmarks/bookmarks_14.png)

A **Könyvjelzők panel** ugyanúgy működik a **Power BI szolgáltatásban**, mint a **Power BI Desktopban**. Itt is le tudja játszani a könyvjelzőket diavetítésként a **Nézet** kiválasztásával.

Ügyeljen arra, hogy a könyvjelzők között a könyvjelző szürke címsorán léptethet, és nem a fekete nyilakkal, ez utóbbiak ugyanis a jelentésoldalak, és nem a könyvjelzők közötti váltásra szolgálnak.

## <a name="limitations-and-considerations"></a>Korlátozások és szempontok
A **könyvjelzők** aktuális kiadásának használatára vonatkozik néhány korlátozás és egyéb szempont.

* A legtöbb egyéni vizualizáció zökkenőmentesen működik a könyvjelzőkkel. Ha hibát tapasztal egy könyvjelző és egy egyéni vizualizáció használatakor, lépjen kapcsolatba az egyéni vizualizáció létrehozójával, és kérje meg, hogy szolgáltasson támogatást a könyvjelzőkhöz. 
* Ha egy vizualizációt a könyvjelző létrehozását követően ad hozzá a jelentésoldalhoz, a vizualizáció az alapértelmezett állapotában jelenik meg. Ez azt is jelenti, hogy ha egy olyan oldalra vesz fel szeletelőt, ahol már hozott létre könyvjelzőket, a szeletelő az alapértelmezett állapotának megfelelően viselkedik majd.
* Ha a vizualizációkat a könyvjelzők létrehozását követően áthelyezi, a változást a könyvjelzők lekövetik. 


## <a name="next-steps"></a>Következő lépések
A könyvjelzőkhöz hasonló vagy azokkal együtt használható funkciókkal kapcsolatos részletesebb információkat az alábbi cikkekben talál:

* [Részletezés használata a Power BI Desktopban](desktop-drillthrough.md)
* [Irányítópult-csempe vagy jelentésvizualizáció megjelenítése Fókusz módban](consumer/end-user-focus.md)

