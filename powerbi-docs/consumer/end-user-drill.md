---
title: Lehatolás és felhatolás egy vizualizációban
description: Ez a dokumentum bemutatja, hogyan lehet lehatolni a vizualizációk mélyebb szintjeire a Microsoft Power BI szolgáltatásban és a Power BI Desktopban.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: MNAaHw4PxzE
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: d935b044e5cbe1a2c84ce5749c3a0b58c528bab0
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54282356"
---
# <a name="drill-mode-in-a-visualization-in-power-bi"></a>Részletezési mód vizualizációkban a Power BI-ban

## <a name="drill-requires-a-hierarchy"></a>A részletezéshez hierarchiára van szükség
Ha a vizualizáció mögött hierarchikus adatstruktúra található, a részletesebb adatszintek kibonthatók. Tegyük fel például, hogy egy vizualizáció az olimpiai érmek számát jeleníti meg, sportonkénti, szakágankénti és versenyszámonkénti adathierarchia alapján. Alapértelmezés szerint a vizualizáció az érmek számát sportok szerinti bontásban (pl. gimnasztika, síelés, vízi sportok.) jeleníti meg. Ugyanakkor mivel rendelkezik hierarchiával, egy-egy vizuális elem (például egy oszlop, egy sáv vagy egy kör) kiválasztásakor egyre részletesebb ábra jeleníthető meg. Ha a **vízi sportok** elemre kattint, megjeleníthetők az úszásra, műugrásra és vízilabdára vonatkozó adatok.  Ezután ha a **műugrásra** kattint, megtekintheti a műugró, toronyugró és szinkronugró versenyszámokra vonatkozó információkat.

Hierarchiát csak saját jelentéseihez adhat, mások által Önnel megosztottakhoz nem.
Nem tudja, mely Power BI-vizualizációk tartalmaznak hierarchiát?  Húzza a kurzort az egyik vizualizáció fölé. Ha az alábbi részletezésvezérlők megjelennek a felső sarkokban, a vizualizáció rendelkezik hierarchiával.

![Lehatolás egy szinttel](./media/end-user-drill/power-bi-drill-icon4.png)  ![lehatolás ki- és bekapcsolása](./media/end-user-drill/power-bi-drill-icon2.png)  ![összes mezőre lehatolás egyszerre ikon](./media/end-user-drill/power-bi-drill-icon3.png)
![felhatolás ikon](./media/end-user-drill/power-bi-drill-icon5.png) ![kibontás lefelé ikon](./media/end-user-drill/power-bi-drill-icon6.png)  

Sajátos hierarchiatípust képviselnek a dátumok. Amikor dátummezőt ad egy vizualizációhoz, a Power BI automatikusan felvesz egy évekből, negyedévekből, hónapokból és napokból álló időhierarchiát. Ha ezzel kapcsolatban további információra van szüksége, tekintse át a [vizualizációs hierarchiákat és a lehatolás működését](../guided-learning/visualizations.yml?tutorial-step=18) áttekintő cikket.


  <iframe width="560" height="315" src="https://www.youtube.com/embed/MNAaHw4PxzE?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> Ha meg szeretné tanulni, hogyan hozhatók létre hierarchiák a Power BI Desktopot használva, tekintse meg a [How to create and add hierarchies](https://youtu.be/q8WDUAiTGeU) (Hierarchiák létrehozása és hozzáadása) című videót
> 

## <a name="prerequisites"></a>Előfeltételek

1. A Power BI szolgáltatásban és a Power BI Desktopban a részletezéshez hierarchiával rendelkező vizualizációra van szükség. 
   
2. A gyakorlat elvégzéséhez [nyissa meg a Kiskereskedelmi elemzési mintát](../sample-datasets.md), és hozzon létre egy fatérképet, amely az alábbiakat tartalmazza: **Összes egység a folyó évre** (Értékek) **Terület**, **Város**, **Irányítószám** és **Név** (Csoport) alapján.  A fatérkép területből (Territory), városból (City), irányítószámból (Postal Code) és városnévből (Name) felépülő hierarchiával rendelkezik. Minden területhez egy vagy több város, minden városhoz egy vagy több irányítószám tartozik, és így tovább. Alapértelmezés szerint a vizualizáció csak a területi adatokat jeleníti meg, mert a lista első eleme a *Territory* (Terület).
   
   ![Válassza a „Territory” lehetőséget](media/end-user-drill/power-bi-hierarcy-list.png)

2. A különféle részletezési ikonok együttműködését nehéz lehet átlátni, ezért most szűrni fogjuk a fatérképet, hogy csak ezt a két kisebb területet mutassa: **KY** és **TN**. Válassza ki a fatérképet, majd a **Vizualizáció szintű szűrők** alatt bontsa ki a **Terület** részt, és válassza ki a **KY** és a **TN** elemeket.

    ![szűrés KY és TN területekre](./media/end-user-drill/power-bi-filter.png)    

   Most már csak két terület jelenik meg a fatérképen.

   ![kettős részletezési ikon](./media/end-user-drill/power-bi-territories.png)

## <a name="three-ways-to-access-the-drill-features"></a>A részletezési funkciók elérésének három módja
A lehatolási, felhatolási és kibontási funkciókat több különféle módon is elérheti a hierarchiával rendelkező vizualizációknál. Ebben a cikkben alább az első módszer használatát mutatjuk be. Ha már megismerkedett a lehatolás és a kibontás alapjaival, mindhárom módszerrel elérheti ugyanazt az eredményt. Próbálja ki mindegyiket, és használja azt, amelyik leginkább tetszik Önnek.

- Az ikonok használatához mutasson egy vizualizációra.  

    ![lehatolási útvonal](./media/end-user-drill/power-bi-hover.png)

- A menü megjelenítéséhez kattintson jobb gombbal egy vizualizációra.
    
    ![helyi menü](./media/end-user-drill/power-bi-drill-menu.png)

- A Power BI menüsávjában válassza a **Böngészés** gombot.

   ![A Böngészés kiválasztására részletezés (lehatolási) ikonok és választható lehetőséget jelennek meg](media/end-user-drill/power-bi-explore.png)

## <a name="drill-pathways"></a>A lehatolás útvonala
### <a name="drill-down"></a>Lehatolás
A vizualizációban való lehatoláshoz több módszert is használhat. A ***Lehatolás*** lehetőséggel a hierarchia következő szintjét érheti el, így ha a **Terület** szinten van, lehatolhat a város szintjére, majd az irányítószám, és végül a név szintjére is. Az útvonal minden lépésén új információhoz juthat.

![lehatolási útvonal](./media/end-user-drill/power-bi-drill-path.png)

### <a name="expand"></a>Kibontás

A ***Kibontás*** a jelenlegi nézethez egy új hierarchiaszintet ad hozzá. Így ha a **Terület** szinten van, kibonthatja, azt és hozzáadhat a fatérképhez várost, irányítószámot és nevet. Az útvonal minden lépése ugyanazt az információt jeleníti meg, és egy új szintet ad hozzá új információkkal.

![az útvonal kibontása](./media/end-user-drill/power-bi-expand-path.png)

Egyesével is lehatolhat és kibonthatja a szintet, de lehetőség van arra is, hogy egyszerre az összes mezőre végezze el a műveletet. 

## <a name="drill-down-all-fields-at-a-time"></a>Lehatolás minden mezőre egyszerre

1. Kezdje a fatérkép legfelső szintjével, ahol a KY és a TN adatai láthatóak. Szélesítse ki a fatérképet: válassza ki az egyik fogópontot, és húzza a jobb oldalra. 

    ![két államot mutató fatérkép](./media/end-user-drill/power-bi-drill-down.png) .

2. Ha az ***összes szinten egyszerre*** szeretne lehatolni, kattintson a vizualizáció bal felső sarkában látható, lefelé mutató dupla nyílra ![kétszeres lehatolás ikon](./media/end-user-drill/power-bi-drill-icon3.png). A fatérkép most Kentucky és Tennessee városadatait mutatja. 

    ![kettős részletezési ikon](./media/end-user-drill/power-bi-drill-down1.png)
   
5. Hatoljon le még egyszer az irányítószám szintre a hierarchiában.

    ![kettős részletezési ikon](./media/end-user-drill/power-bi-drill-down2.png)

3. Ha vissza szeretne lépni, válassza a vizualizáció bal felső sarkában látható felfelé mutató nyilat ![felhatolás egy szinttel ikon](./media/end-user-drill/power-bi-drill-icon5.png).


## <a name="drill-down-one-field-at-a-time"></a>Lehatolás mezőnként
Ez a módszer a vizualizációk felső sarkaiban megjelenő lehatolási ikonokat használja. 

1. A lehatolási ikont kiválasztással kapcsolhatja be ![bekapcsolt lehatolás](./media/end-user-drill/power-bi-drill-icon2.png). Most már lehetősége van arra, hogy ***egyszerre egy mezőnyit hatoljon le***. 
   
   ![a lehatolás ki/be ikonra mutató nyíl](media/end-user-drill/power-bi-drill-icon-new.png)

   Ha nem kapcsolja be a lehatolási módot, akkor a rendszer nem lehatolást végez, hanem a jelentésoldalon szereplő többi diagram tekintetében keresztszűrést alkalmaz, amikor rákattint valamelyik vizualizációs elemre (pl. az egyik oszlopra, egy körre vagy levélcsomópontra).

2. Válassza ki a **TN**-hez tartozó *levélcsomópontot*. A fatérkép most megjeleníti az összes olyan várost Tennessee államban, amelyben van üzlet. 

    ![a csak Tennessee adatait mutatót fatérkép](media/end-user-drill/power-bi-drill-down-one1.png)

2. Most folytathatja a lehatolást Tennessee államra, vagy lehatolhat Tennessee egy adott városára is, de lehetőség van arra is, hogy kibontást végezzen (lásd a **Minden mező kibontása** témát alább). Most folytassuk azzal, hogy egyszerre egy-egy mezőben végzünk lehatolást.  Válassza ki a **Knoxville, TN** elemet. A fatérkép most a Knoxville-ben található üzlet postai irányítószámát mutatja. 

   ![a fatérkép 37919 értéket mutat](media/end-user-drill/power-bi-drill-down-one2.png)

    Nézze meg, hogyan változik a csempe, ahogy le- és felhatol a hierarchiában.  

## <a name="expand-all-and-expand-one-field-at-a-time"></a>Az összes kibontása és egyszerre egy-egy mező kibontása
Egy olyan fatérkép, amely mindössze egy irányítószámot mutat, nem igazán hasznos.  Ezért bontsuk ki a hierarchiát egy szinttel lejjebb.  

1. Az aktív fatérképben válassza a *Kibontás lefelé* ikont ![kibontás lefelé ikon](./media/end-user-drill/power-bi-drill-icon6.png). A fatérkép most a hierarchia két szintjét mutatja: irányítószámot és üzletnevet. 

    ![irányítószám és üzletnév mutatása](./media/end-user-drill/power-bi-expand1.png)

2. Ha meg akarja tekinteni a Tennesee-hez tartozó adatok mind a 4 hierarchiaszintjét, válassza a felhatolás nyilat addig, amíg el nem éri a fatérképen a második szintet, amely a **Total units this year by territory and city** (Összes egység ebben az évben terület és város szerint). 

    ![Tennessee összes adatát mutatót fatérkép](media/end-user-drill/power-bi-drill-down-one1.png)


3. Ügyeljen rá, hogy a lehatolás még be legyen kapcsolva ![lehatolás bekapcsolva](./media/end-user-drill/power-bi-drill-icon2.png), majd válassza a *kibontás lefelé* ikont ![kibontás lefelé ikon](./media/end-user-drill/power-bi-drill-icon6.png). A fatérkép most már további adatokat is megjelenít: a város és az állam mellett most már irányítószámot is mutat. 

    ![kettős részletezési ikon](./media/end-user-drill/power-bi-expand-one3.png)

4. Válassza a *kibontás lefelé* ikont még egyszer: ezzel megjeleníti a Tennesee-hez tartozó adatok mind a 4 hierarchiaszintjét a fatérképen. Ha még több részletet szeretne, mutasson rá egy levélcsomópontra.

   ![fatérkép Tennesee adataival](./media/end-user-drill/power-bi-expand-all.png)

## <a name="drilling-filters-other-visuals"></a>Más vizualizációk szűrése részletezéskor
A Részletezés mód használatakor el kell döntenie, hogy a lehatolás és a kibontás milyen hatással legyen az oldal többi vizualizációjára. 

Alapértelmezés szerint a lehatolás nem szűri a jelentés többi vizualizációját. Ez a funkció azonban bekapcsolható a Power BI Desktopban és a Power BI szolgáltatásban. 

1. A Desktopban válassza a **Formázás** lapfület, majd jelölje be a **Más vizualizációk részletező szűrése** lehetőség melletti jelölőnégyzetet.

    ![beállítás a Power BI Desktopban](./media/end-user-drill/power-bi-drill-filters-desktop.png)

2. Ha most lehatolást, felhatolást vagy kibontást végez egy hierarchiával rendelkező vizualizációnál, ez a művelet az oldal más vizualizációit is szűrni fogja. 

    ![beállítás a Desktopban](./media/end-user-drill/power-bi-drill-filters.png)

    ![beállítás a Desktopban](./media/end-user-drill/power-bi-drill-filters2.png)

> [!NOTE]
> A Power BI szolgáltatásban ezt úgy engedélyezheti, ha a felső menüsávban kiválasztja a **Vizuális interakciók > Más vizualizációk részletező szűrése** lehetőséget.
>
> ![beállítás a Power BI szolgáltatásban](./media/end-user-drill/power-bi-drill-filters-service.png)



## <a name="understanding-the-hierarchy-axis-and-hierarchy-group"></a>A hierarchiatengely és hierarchiacsoport ismertetése
A hierarchiatengely és a hierarchiacsoport tulajdonképpen a megtekinteni kívánt adatok részletességét szabályozó eszközöket jelenti. A kategóriákba és alkategóriákba csoportosítható minden adat rendelkezik hierarchiával. Ez természetesen magában foglalja a dátumokat és az időt.

Ha egy Power BI-vizualizációt hierarchiával együtt szeretne létrehozni, jelöljön ki egy vagy több adatmezőt, amelyet a **Tengely**vagy a **Csoport** gyűjtőhöz ad, valamint az adatmezőkként vizsgálni kívánt adatokat, amelyeket az**Értékek** gyűjtőhöz ad. Ha a *Részletezés mód* ikonjai a vizualizáció jobb és bal felső sarkában jelennek meg, akkor biztos lehet benne, hogy az adatok hierarchikusak. 

Alapvetően kétféle hierarchikus adatokkal dolgozunk:
- Dátum- és időadatok – Ha egy Dátum/idő adattípussal rendelkező adatmezője van, akkor hierarchikus adatokkal dolgozik. A Power BI automatikusan létrehozza a hierarchiát azon adatmezőkhöz, amelyek értékei [Dátum/idő](https://msdn.microsoft.com/library/system.datetime.aspx) struktúra szerint elemezhetők. A **Tengely** vagy a **Csoport** gyűjtőhöz csak egy Dátum/Idő mezőt kell adnia.
- Kategorikus adatok – Ha az adatok algyűjteményeket tartalmazó gyűjteményekből származnak, vagy olyan adatsorokkal rendelkeznek, amelyeknek közös értékeik vannak, akkor hierarchikus adatokkal dolgozik.

A Power BI segítségével egyesével vagy részhalmazonként kibonthatja ezeket. Lehatolhat a szintenkénti részhalmazokig, vagy minden részhalmazt egyszerre megtekinthet egy szinten. Például lehatolhat egy adott évig, vagy megtekintheti az egyes évek eredményeit a hierarchiában lefelé haladva. Hasonlóképpen hatolhat felfelé is.

A következő szakaszok a legmagasabb, a középső és a legalsó nézetből való lehatolást ismertetik.

### <a name="hierarchical-data-and-time-data"></a>Hierarchikus és időadatok
Ehhez a példához használja fel a [kiskereskedelmi elemzési mintát](../sample-datasets.md), és hozzon létre egy halmozott oszlopdiagram típusú vizualizációt, amelynek tengelye a **Hónap**, az értékei pedig az **Összes eladás**.  

Bár a Tengely adatmezője a **Hónap**, a **Tengely** gyűjtőben továbbra is létrehoz egy **Év** kategóriát is. Ennek az az oka, hogy a Power BI a teljes Dátum/Idő-struktúrát megadja az összes beolvasott értékhez. A hierarchia tetején az év adatai jelennek meg.

![Egyetlen sáv az adatok éves csoportosításával](media/end-user-drill/power-bi-hierarchical-axis-datetime-1.png)

A Részletezés módban kattintson a diagram sávjára, ha egy szinttel lejjebb szeretne lépni a hierarchiában. Itt három sávot láthat, amelyek az elérhető negyedéveknek felelnek meg. A bal felső sarokban található ikonok közül válassza az **Expand all down one level of the hierarchy** (Az összes kibontása a hierarchia egy szintjével lejjebb) lehetőséget. Ezt ismételje meg a hierarchia legalsó szintjével is, amely az egyes hónapok eredményeit jeleníti meg.

![sávdiagram havi bontású sávokkal](media/end-user-drill/power-bi-hierarchical-axis-datetime-2.png)

A vizualizáción kívül az egyes jelentések adataiban is láthatjuk a hierarchiát. Az alábbi táblázat egy jelentés egyetlen hónapjában vagy minden hónapjában végzett lehatolásának az **Adatok megjelenítése** műveletével kapott eredményeit jeleníti meg. 

Megfigyelheti, hogy az adatok megegyeznek a negyedéves és az éves jelentésekben, azonban ha lehatol az **Értékek** részletességi szintjéig, az egyetlen hónapra vonatkozó jelentés konkrétabb adatokat jelenít meg, az összes hónapra vonatkozó jelentés pedig több adatot tartalmaz.


|Kibontás módja|Év|Negyedév|Hónap|Nap|
| ---|:---:|:---:|:---:|---|
|Egyirányú|![egy év](./media/end-user-drill/power-bi-hierarchical-year.png)|![egy negyedév](media/end-user-drill/power-bi-hierarchical-quarter.png)|![egy hónap](./media/end-user-drill/power-bi-hierarchical-one-month.png)|![egy nap](media/end-user-drill/power-bi-hierarchical-one-day.png)|
|Összes|![összes év](./media/end-user-drill/power-bi-hierarchical-year.png)|![összes negyedév](media/end-user-drill/power-bi-hierarchical-quarter.png)|![összes hónap](./media/end-user-drill/power-bi-hierarchical-all-month.png)|![összes nap](media/end-user-drill/power-bi-hierarchical-all-day.png)|


### <a name="hierarchical-category-data"></a>Hierarchikus kategóriaadatok
A gyűjteményekből és algyűjteményekből modellezett adatok hierarchikusak. Jó példák erre a helyadatok. Vegyünk például egy táblázatot egy olyan adatforrásban, amely az Ország, Állam, Város és Irányítószám oszlopokkal rendelkezik. Azok az adatok, amelyek megegyező Ország, Állam és Város értékekkel bírnak, hierarchikusak.

Ehhez a példához használja a [kiskereskedelmi elemzési mintát](../sample-datasets.md). Hozzon létre egy halmozott oszlopdiagram típusú vizualizációt, amely az **Egységek éves számát** (Értékek) jeleníti meg a **Terület**, a **Város**, az **Irányítószám** és a **Név** szerint (Csoport).  

![sávdiagram a folyó évi összes egység terület szerinti adataival](media/end-user-drill/power-bi-hierarchical-axis-category-1.png)

A Részletezés módban a bal felső sarokban található ikonok közül válassza az **Expand all down one level of the hierarchy** (Az összes kibontása a hierarchia egy szintjével lejjebb) lehetőséget háromszor.
Ekkor a hierarchia legalsó szintjén kell lennie, amely a Terület, a Város és az Irányítószám szerint jeleníti meg az eredményeket.

![sávdiagram a hierarchia legalacsonyabb szintjével, a legnagyobb részletezéssel](media/end-user-drill/power-bi-hierarchical-axis-category-2.png)

A vizualizáción kívül az egyes jelentések adataiban is láthatjuk a hierarchiát. Az alábbi táblázat egy jelentés egyetlen területén vagy minden területén végzett lehatolásának az **Adatok megjelenítése** műveletével kapott eredményeit jeleníti meg. A lehatolás során láthatja, hogy az egyetlen területre vonatkozó jelentés konkrétabb adatokat jelenít meg, az összes területre vonatkozó jelentés pedig több adatot tartalmaz.


| Kibontás módja|Terület|Település|Irányítószám|Név|
| ---|:---:|:---:|:---:|---|
|Egyirányú|![egy terület](./media/end-user-drill/power-bi-hierarchical-territory.png)|![egy város](media/end-user-drill/power-bi-hierarchical-one-territory-city.png)|![egy irányítószám](./media/end-user-drill/power-bi-hierarchical-one-territory-city-postal.png)|![egy név](media/end-user-drill/power-bi-hierarchical-one-territory-city-postal-name.png)|
|Összes|![összes terület](./media/end-user-drill/power-bi-hierarchical-territory.png)|![összes város](media/end-user-drill/power-bi-hierarchical-all-territory-city.png)|![összes irányítószám](./media/end-user-drill/power-bi-hierarchical-all-territory-city-postal.png)|![összes név](media/end-user-drill/power-bi-hierarchical-all-territory-city-postal-name.png)|


## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások
* Ha dátum mező felvételekor a rendszer nem hoz létre automatikusan időhierarchiát, elképzelhető, hogy a „dátum” mező nem dátum mezőként lett elmentve. Ha Ön az adatkészlet tulajdonosa, nyissa meg *Adatok* nézetben a Power BI Desktopban, válassza ki a dátumot tartalmazó oszlopot, és a Modellezés lapfülön módosítsa az **Adattípust** **Dátumra** vagy **Dátum és időre**. Ha a jelentés meg lett osztva Önnel, kérje meg a tulajdonost a módosítások végrehajtására.  
  
  ![válassza az adatnézetet, majd a jobb felső sarokban tekintse meg az Adattípust](media/end-user-drill/power-bi-change-data-type2.png)

## <a name="next-steps"></a>Következő lépések
[Vizualizációk a Power BI-jelentésekben](../visuals/power-bi-report-visualizations.md)

[A Power BI-jelentések](end-user-reports.md)

[Power BI – Alapfogalmak](end-user-basic-concepts.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

