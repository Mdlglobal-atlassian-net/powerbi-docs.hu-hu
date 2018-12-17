---
title: Az eltérő eloszlások helyének azonosítása elemzésekkel (előzetes verzió)
description: A Power BI Desktopban könnyen végezhet olyan elemzéseket, amelyekkel azonosíthatja a diagramok eltérő eloszlásainak helyét
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 1966c39fef818d6df84b9b47039b1d762374ce28
ms.sourcegitcommit: 72c9d9ec26e17e94fccb9c5a24301028cebcdeb5
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/07/2018
ms.locfileid: "53026787"
---
# <a name="use-insights-in-power-bi-desktop-to-find-where-a-distribution-is-different-preview"></a>Az eltérő eloszlások helyének azonosítása a Power BI Desktop elemzéseivel (előzetes verzió)

A vizualizációk adatpontjainál gyakran felmerül a kérdés, hogy az eloszlás vajon hasonló lenne-e különböző kategóriáknál. A **Power BI Desktop** **elemzéseivel** ezt néhány kattintással megtudhatja.

Vegyük például a következő vizualizációt, amely az *Összes értékesítést* jeleníti meg *Országok* szerint. Ahogy a diagramon látható, a legtöbb értékesítés az Egyesült Államokból érkezik, amely az összes értékesítés 57%-áért felelős, a többi ország pedig kisebb mértékben járul hozzá a 100%-hoz. Az ilyen esetekben érdekes lehet megvizsgálni, hogy azonos eloszlás jelenne-e meg eltérő alkategóriák esetén is. Vajon ugyanezt az eredményt látnánk minden év, minden értékesítési csatorna, és minden termékkategória esetében is?  Bár alkalmazhatna különböző szűrőket, és összehasonlíthatná a megjelenített eredményeket, ez időigényes, és több hibalehetőséget rejt magában. 

![Nagy eloszlású diagram](media/desktop-insights-find-where-different/find-where-different_01.png)

A **Power BI Desktop** alkalmazáson belül kérheti az eltérő eloszlások helyének azonosítását, valamint az adatok gyors, automatikus, részletes elemzését is. Egyszerűen a jobb egérgombbal kattintson egy adatpontra, és válassza az **Elemzés > Eltérő eloszlás helyének keresése** lehetőséget. A rendszer ezt követően az elemzést egy könnyen használható ablakban jeleníti meg.

![Az eloszlás eltéréseinek elemzése](media/desktop-insights-find-where-different/find-where-different_02.png)

Ebben a példában az automatizált elemzés gyorsan kimutatja, hogy a *túrakerékpárok* értékesítési aránya alacsonyabb az Egyesült Államokban és Kanadában, míg a többi országban magasabb.   

> [!NOTE]
> Ez a funkció egyelőre előzetes verzióként érhető el, ezért változhat. A **Power BI Desktop** 2017 szeptemberi és az annál újabb verzióiban az elemzés funkció alapértelmezés szerint engedélyezve van és működik (nem kell bejelölnie az előnézeti jelölőnégyzetet az engedélyezéshez).
> 
> 

## <a name="using-insights"></a>Elemzések használata
Ha elemzésekkel szeretné azonosítani a diagramok eloszlásában található eltérések helyét, kattintson a jobb egérgombbal bármelyik adatpontra (vagy a teljes vizualizációra), majd válassza az **Elemzés > Eltérő eloszlás helyének keresése** lehetőséget.

![Kattintás a jobb egérgombbal az elemzésekhez](media/desktop-insights-find-where-different/find-where-different_03.png)

A **Power BI Desktop** ezt követően futtatja az adatokon a gépi tanulási algoritmusokat, majd feltölti a legnagyobb eloszlásbeli eltérést okozó kategóriák (oszlopok), illetve az oszlopok értékeinek leírását és vizualizációját egy ablakba. Ahogy az a következő képen látható, az elemzéseket oszlopdiagram formájában adja meg a rendszer. 

![Oszlopdiagram](media/desktop-insights-find-where-different/find-where-different_04.png)

A választott szűrővel ellátott értékek a normál, alapértelmezett színnel jelennek meg. Az összesített értékek, ahogyan az eredeti kezdő vizualizáción láthatjuk, szürkén jelennek meg. Akár három különböző szűrőt alkalmazhat (ebben a példában ezek a *túrakerékpárok*, *a mountain bike-ok* és a *közúti kerékpárok*), a különböző szűrők pedig kattintással választhatók ki (vagy Ctrl + kattintással, ha egyszerre többet szeretne kijelölni).

Egyszerű additív mértékek esetében (például az *Összes értékesítés*) az összehasonlítás a relatív, és nem az abszolút értékeken alapul. Mivel a túrakerékpárok értékesítése alacsonyabb, mint az összes kategória összesített értékesítése, a vizualizáció alapértelmezés szerint kettős tengelyen jeleníti meg a különböző országokban tapasztalható értékesítési arányok összehasonlítását a túrakerékpárok és a többi kerékpár-kategória között.  A vizualizáció alatti váltógombbal a két érték azonos tengelyen jeleníthető meg, az abszolút értékek így könnyen összehasonlíthatók (ahogyan az a következő képen látható).    

![elemzések használatakor megjelenő vizualizációk](media/desktop-insights-find-where-different/find-where-different_04.png)

A leíró szöveg a szűrők értékeihez kapcsolható fontossági szintről is tanúskodhat, a szűrőnek megfelelő rekordok száma alapján. Így ebben a példában láthatjuk, hogy míg a *túrakerékpárok* eloszlása jelentősen eltérő, csak a rekordok 16,6%-áért felelősek.

A lap tetején található *felfelé mutató hüvelykujj* és *lefelé mutató hüvelykujj* ikonokat használva visszajelzést adhat a vizualizációról és a funkcióról. Bár küldhet így visszajelzést, az algoritmus jelenleg nem tanul ezekből, így ez nem befolyásolja a funkció következő használatakor kapott eredményeket.

Továbbá a vizualizáció tetején található **+** gomb segítségével hozzáadhatja jelentéséhez a kiválasztott vizualizáció ugyanúgy, mintha manuálisan hozta volna létre. Ezt követően tetszőlegesen formázhatja vagy módosíthatja a hozzáadott vizualizációt bármely más, a jelentésében szereplő vizualizációhoz hasonlóan. Csak akkor adhat hozzá egy kiválasztott elemzési vizualizációt, ha a **Power BI Desktopban** szerkeszti a jelentést.

Az elemzéseket akkor használhatja, ha a jelentés olvasási vagy szerkesztési módban van, így azt mind az adatok elemzésére, mind pedig a jelentéshez könnyen hozzáadható vizualizációk létrehozásához is használhatja.

## <a name="details-of-the-returned-results"></a>A kapott eredmények részletei
Az algoritmus a modell összes többi oszlopát felhasználja, és ezek értékeit alkalmazza szűrőként az eredeti vizualizációban, majd megállapítja, hogy mely szűrőértékek adják az eredetitől *leginkább eltérő* eredményt.

Most biztos azon gondolkodik, mit is jelent az, hogy *eltérő*. Tegyük fel például, hogy az Egyesült Államok és Kanada értékesítései az alábbiak szerint oszlanak meg:

|Ország  |Értékesítés (millió USD)|
|---------|----------|
|USA      |15        |
|Kanada   |5         |

Egy adott termékkategória (*közúti kerékpár*) esetében a következő lehet az értékesítések eloszlása:

|Ország  |Értékesítés (millió USD)|
|---------|----------|
|USA      |3        |
|Kanada   |1         |

Bár a számok eltérnek mindegyik táblázatban, a relatív értékek az Egyesült Államok és Kanada között megegyeznek (75% és 25% összesen, valamint a közúti kerékpárok esetében is). Emiatt ezeket nem tekintjük eltérőnek. Ehhez hasonló egyszerű additív mértékek esetében az algoritmus tehát a *relatív* értékben keres eltérést.  

Most vegyünk egy olyan mértéket, mint az árrés, amelyet nyereség/költség egyenlettel számolunk, és tegyük fel, hogy az Egyesült Államok és Kanada összesített árrései a következők voltak:

|Ország  |Árrés (%)|
|---------|----------|
|USA      |15        |
|Kanada   |5         |

Egy adott termékkategória (*közúti kerékpár*) esetében a következő lehet az értékesítések eloszlása:

|Ország  |Árrés (%)|
|---------|----------|
|USA      |3        |
|Kanada   |1         |

A mértékek természete miatt ezeket érdekes módon *eltérőnek* tekintjük. A nem additív mértékek esetén, mint a fenti árréses példa, az algoritmus az abszolút értékben keresi az eltérést.

A megjelenített vizualizációk így érthetően megjelenítik az összesített eloszlás eltéréseit (ahogyan az eredeti vizualizációban láthatjuk), valamint a szűrővel ellátott értéket.  

Az additív mértékeknél, mint a fenti *értékesítési* példa, oszlop- és vonaldiagramot használtunk, így könnyen összehasonlíthatók a relatív értékek a kettős tengelynek és a megfelelő méretezésnek köszönhetően. Az oszlopok az alkalmazott szűrővel kapott értéket jelenítik meg, a vonal pedig az összesített értéket (az oszloptengely a bal oldalon, a vonaltengely pedig a jobb oldalon található). A vonal *lépcsőzetes* stílusban jelenik meg, egy szürkével kitöltött szaggatott vonalként. Az előző példához visszatérve, ha az oszloptengely maximális értéke 4, a vonaltengelyé pedig 20, akkor könnyen összehasonlíthatók az Egyesült Államok és Kanada relatív értékei a szűrt és az összesített értékek esetén is. 

Hasonlóképp, a nem additív mértékeknél – mint a fenti *árréses* példa – oszlop- és vonaldiagramot használtunk, így könnyen összehasonlíthatók az abszolút értékek az egyszerű tengelynek köszönhetően. Ez esetben is a szürke vonal mutatja az összesített értéket. Akár tényleges, akár relatív számokat hasonlít össze, az eloszlások eltérésének mértékét nem egyszerűen az értékek eltérésének kiszámításával állapíthatja meg. Például:

* Számít a népesség mértéke, mivel az eltérés statisztikailag kevésbé jelentős és kevésbé érdekes, ha a teljes népesség egy kis szeletére vonatkozik. Az értékesítések eloszlása országonként jelentősen eltérő lehet egyes termékek esetében, azonban ez nem érdekes, ha több ezer termékről van szó, és az aktuálisan vizsgált termék csak egy töredékét teszi ki az összesített értékesítésnek.

* Azon kategóriák eltérései, amelyek esetén az eredeti értékek nagyon magasak, vagy a nullához nagyon közeliek voltak, nagyobb súllyal bírnak. Ha például egy ország csak az összesített értékesítések 1%-áért felelős, azonban egy adott terméktípus esetén 6%-ért, az statisztikailag nagyobb jelentőséggel bír, így érdekesebb, mint egy olyan ország, amelynek hozzájárulása 50%-ról 55%-ra nőtt. 

* A legnagyobb jelentőséggel bíró eredmények kiválasztásában különböző heurisztikák vállalnak szerepet, például az adatok közötti egyéb kapcsolatok.
     
A különböző oszlopok, valamint az egyes oszlopok értékeinek megvizsgálása után a program kiválasztja a legnagyobb eltéréseket eredményező értékkészleteket. A könnyebb megértés érdekében ezeket oszloponként csoportosítja, az első helyre pedig az az oszlop kerül, amelynek értékei a legnagyobb eltérést mutatják. Oszloponként legfeljebb három érték jelenhet meg, ez azonban lehet kevesebb is, ha háromnál kevesebb érték bír nagy jelentőséggel, vagy ha egyes értékek nagyobb hatással voltak a végeredményre, mint mások. 

Előfordulhat, hogy a rendszer a rendelkezésre álló időn belül nem vizsgál meg minden oszlopot, így nem garantálható a legnagyobb jelentőséggel bíró oszlopok és értékek megjelenítése. A különböző heurisztikák azonban garantálják, hogy a program a legvalószínűbb oszlopokat vizsgálja meg elsőként. Tegyük fel például, hogy az összes oszlop megvizsgálása után a program a következő oszlopokról/értékekről állapítja meg, hogy az eloszlásra a legnagyobb hatással vannak (csökkenő sorrendben):

    Subcategory = Touring Bikes
    Channel = Direct
    Subcategory = Mountain Bikes
    Subcategory = Road Bikes
    Subcategory = Kids Bikes
    Channel = Store

Ezek a következő sorrendben jelennének meg oszlopokként:

    Subcategory: Touring Bikes, Mountain Bikes, Road Bikes (only three listed, with the text including “...amongst others” to indicate that more than three have a significant impact) 

    Channel = Direct (only Direct listed, if it’s level of impact was much greater than Store)

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások
A következő lista az **elemzések** jelenleg nem támogatott forgatókönyveit tartalmazza:

* Legjobb N szűrők
* Mérték szűrők
* Nem numerikus mértékek
* Az „Érték megjelenítési módja” funkció használata
* Szűrt mértékek – A szűrt mértékek olyan vizualizációszintű számítások, amelyekre egy adott szűrőt alkalmaz (például *Franciaország összes értékesítése*). Ezeket az elemzés funkció által létrehozott vizualizációkhoz használhatja

Továbbá az elemzések esetében jelenleg nem támogatottak a következő modelltípusok és adatforrások:

* DirectQuery
* Élő kapcsolat
* Helyszíni Reporting Services
* Beágyazás

## <a name="next-steps"></a>Következő lépések
Ha többet szeretne megtudni a **Power BI Desktopról**, illetve a szoftver használatának kezdeti lépéseiről, tekintse meg a következő cikkeket.

* [Mi az a Power BI Desktop?](desktop-what-is-desktop.md)
* [Lekérdezések áttekintése a Power BI Desktopban](desktop-query-overview.md)
* [Adatforrások a Power BI Desktopban](desktop-data-sources.md)
* [Csatlakozás adatokhoz a Power BI Desktopban](desktop-connect-to-data.md)
* [Adatok formázása és kombinálása a Power BI Desktoppal](desktop-shape-and-combine-data.md)
* [Gyakori lekérdezési feladatok a Power BI Desktopban](desktop-common-query-tasks.md)   

