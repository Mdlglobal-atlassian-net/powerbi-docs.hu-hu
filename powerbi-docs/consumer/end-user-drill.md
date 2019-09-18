---
title: Lehatolás és felhatolás egy vizualizációban
description: Ez a dokumentum bemutatja, hogyan lehet részletezni a vizualizációk mélyebb szintjeit a Microsoft Power BI szolgáltatásban és a Power BI Desktopban.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: MNAaHw4PxzE
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 6/17/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 29823a2f1ca7f1448df54282e0ce081310974eb3
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/16/2019
ms.locfileid: "67265268"
---
# <a name="drill-mode-in-a-visualization-in-power-bi"></a>Részletezési mód vizualizációkban a Power BI-ban

Ez a cikk bemutatja, hogyan lehet részletezni a vizualizációk mélyebb szintjeit a Microsoft Power BI szolgáltatásban és a Power BI Desktopban. A Power BI-jelentések több adathierarchiát tartalmazhatnak, amelyek részletes betekintést engednek az adatokba. Az adatpontok részletezésével és felhatolásával mélyreható betekintést nyerhet az adatokba. Ezt még a mobileszközökön is kihasználhatja.

## <a name="drill-requires-a-hierarchy"></a>A részletezéshez hierarchiára van szükség

Ha a vizualizáció mögött hierarchikus adatstruktúra található, a részletesebb adatszintek kibonthatók. Tegyük fel például, hogy egy vizualizáció az olimpiai érmek számát jeleníti meg, sportonkénti, szakágankénti és versenyszámonkénti adathierarchia alapján. Alapértelmezés szerint a vizualizáció az érmek számát sportok szerinti bontásban (pl. gimnasztika, síelés, vízi sportok.) jeleníti meg. Ugyanakkor mivel rendelkezik hierarchiával, egy-egy vizualizációs elem (például egy oszlop, egy sáv vagy egy kör) kiválasztásakor egyre részletesebb ábra jeleníthető meg. Ha a **vízi sportok** elemre kattint, megjeleníthetők az úszásra, műugrásra és vízilabdára vonatkozó adatok.  Ezután ha a **műugrásra** kattint, megtekintheti a műugró, toronyugró és szinkronugró versenyszámokra vonatkozó információkat.

Hierarchiát csak saját jelentéseihez adhat, mások által Önnel megosztottakhoz nem.
Nem tudja, mely Power BI-vizualizációk tartalmaznak hierarchiát? Helyezze a kurzort egy vizualizáció fölé. Ha az alábbi részletezésvezérlők megjelennek a felső sarkokban, a vizualizáció rendelkezik hierarchiával.

![Képernyőkép az első szintű lehatolás ikonjáról.](./media/end-user-drill/power-bi-drill-icon4.png)  ![Képernyőkép a lehatolás be- és kikapcsoló ikonjáról.](./media/end-user-drill/power-bi-drill-icon2.png)  ![Képernyőkép az összes mezőre vonatkozó egyidejű lehatolás ikonjáról](./media/end-user-drill/power-bi-drill-icon3.png)
![felhatolás ikon](./media/end-user-drill/power-bi-drill-icon5.png) ![Képernyőkép a kibontás lefelé ikonról.](./media/end-user-drill/power-bi-drill-icon6.png)  

Sajátos hierarchiatípust képviselnek a dátumok. Amikor dátummezőt ad egy vizualizációhoz, a Power BI automatikusan felvesz egy évekből, negyedévekből, hónapokból és napokból álló időhierarchiát. Ha ezzel kapcsolatban további információra van szüksége, tekintse át a [vizualizációs hierarchiákat és a lehatolás működését](../guided-learning/visualizations.yml?tutorial-step=18) áttekintő cikket, vagy az alábbi videót.

<iframe width="560" height="315" src="https://www.youtube.com/embed/MNAaHw4PxzE?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> Ha meg szeretné tanulni, hogyan hozhatók létre hierarchiák a Power BI Desktopot használva, tekintse meg a [How to create and add hierarchies](https://youtu.be/q8WDUAiTGeU) (Hierarchiák létrehozása és hozzáadása) című videót.

## <a name="prerequisites"></a>Előfeltételek

1. A Power BI szolgáltatásban és a Power BI Desktopban a részletezéshez hierarchiával rendelkező vizualizációra van szükség.

1. A leírás követéséhez nyissa meg a [Kiskereskedelmi elemzési mintát](../sample-datasets.md). Hozzon létre egy **Fatérkép** vizualizációt a következőkkel:

    | Panel | Mező |
    | ---- | ----- |
    | Érték |Értékesítés<br>\|\_ Folyó évi összes egység |
    | Csoportosítás | Store<br>\|\_ Terület<br>\|\_ Város<br>\|\_ Irányítószám<br>\|\_ Név

    A fatérkép területből (Territory), városból (City), irányítószámból (Postal Code) és városnévből (Name) felépülő hierarchiával rendelkezik. Minden területhez egy vagy több város, minden városhoz egy vagy több irányítószám tartozik, és így tovább. Alapértelmezés szerint a vizualizáció csak a területi adatokat jeleníti meg, mert a lista első eleme a *Territory* (Terület).

    ![Képernyőkép a Vizualizációk panelről, kiemelt Territory mezővel.](media/end-user-drill/power-bi-hierarcy-list.png)

1. A különböző részletezési ikonok működésének elsajátítása kihívást jelenthet. Szűrjük a fatérképet úgy, hogy csak a két kisebb területet jelenítse meg: **KY** és **TN**. Válassza ki a fatérképet, majd a **Vizualizáció szintű szűrők** alatt bontsa ki a **Terület** részt, és válassza ki a **KY** és a **TN** elemeket.

    ![Képernyőkép a Vizualizációk panelről, KY és TN szűrőjével.](./media/end-user-drill/power-bi-filter.png)

    Most már csak két terület jelenik meg a fatérképen.

    ![Képernyőkép a vizualizációról, kiemelt KY és TN elemmel.](./media/end-user-drill/power-bi-territories.png)

## <a name="three-ways-to-use-the-drill-features"></a>A részletezési funkciók használatának három módja

A lehatolási, felhatolási és kibontási funkciókat több különféle módon is elérheti a hierarchiával rendelkező vizualizációknál. Ebben a cikkben alább az első módszer használatát mutatjuk be. A lehatolás és a kibontás alapjainak elsajátítása után mindhárom módot használhatja. Ezek ugyanis ugyanazt az eredményt szolgálják. Próbálja ki őket, és válassza ki azt, amelyik a legszimpatikusabb.

- Az ikonok használatához mutasson egy vizualizációra.  

    ![Képernyőkép a rámutatásról.](./media/end-user-drill/power-bi-hover.png)

- A menü megjelenítéséhez kattintson jobb gombbal egy vizualizációra.

    ![Képernyőkép a jobb gombbal való kattintásról.](./media/end-user-drill/power-bi-drill-menu.png)

- A Power BI menüsávjában válassza a **Böngészés** gombot.

   ![Képernyőkép a Böngészés kiválasztásáról, amelynek hatására részletezési ikonok és választható lehetőségek jelennek meg.](media/end-user-drill/power-bi-explore.png)

## <a name="drill-pathways"></a>A lehatolás útvonala

### <a name="drill-down"></a>Lehatolás

A vizualizációban való lehatoláshoz több módszert is használhat. A **Lehatolás** a hierarchia következő szintjére vezet. Ha a **Terület** szinten van, lehatolhat a város szintjére, majd az irányítószám, és végül a név szintjére is. Az útvonal minden lépésén új információhoz juthat.

![A részletezés útvonalát ismertető diagram](./media/end-user-drill/power-bi-drill-path.png)

### <a name="expand"></a>Kibontás

A **Kibontás** a jelenlegi nézethez egy új hierarchiaszintet ad hozzá. Így ha a **Terület** szinten van, kibonthatja, azt és hozzáadhat a fatérképhez várost, irányítószámot és nevet. Az útvonal minden lépése ugyanazt az információt jeleníti meg, és egy új szintet ad hozzá új információkkal.

![A kibontás útvonalát ismertető diagram](./media/end-user-drill/power-bi-expand-path.png)

Egyesével is lehatolhat és kibonthatja a szintet, de lehetőség van arra is, hogy egyszerre az összes mezőre végezze el a műveletet.

## <a name="drill-down-all-fields-at-once"></a>Lehatolás minden mezőre egyszerre

1. Kezdje a fatérkép legfelső szintjével, ahol a KY és a TN adatai láthatóak. Szélesítse ki a fatérképet: válassza ki az egyik fogópontot, és húzza a jobb oldalra.

    ![Képernyőkép a fatérképről a KY és a TN elemmel](./media/end-user-drill/power-bi-drill-down.png)

1. Ha az *összes szinten egyszerre* szeretne lehatolni, kattintson a vizualizáció bal felső sarkában látható, lefelé mutató dupla nyílra ![kétszeres lehatolás ikon](./media/end-user-drill/power-bi-drill-icon3.png). A fatérkép most Kentucky és Tennessee városadatait mutatja.

    ![Képernyőkép a fatérképről a városokra mutató lehatolással.](./media/end-user-drill/power-bi-drill-down1.png)

1. Hatoljon le még egyszer az irányítószám szintre a hierarchiában.

    ![Képernyőkép a fatérképről az irányítószámra mutató lehatolással.](./media/end-user-drill/power-bi-drill-down2.png)

1. Ha vissza szeretne lépni, válassza a vizualizáció bal felső sarkában látható felfelé mutató nyilat ![Képernyőkép az első szintű felhatolás ikonjáról.](./media/end-user-drill/power-bi-drill-icon5.png).

## <a name="drill-down-one-field-at-a-time"></a>Lehatolás mezőnként

Ez a módszer a vizualizációk felső sarkaiban megjelenő lehatolási ikonokat használja.

1. A lehatolási ikont kiválasztással kapcsolhatja be ![Képernyőkép a lehatolás be- és kikapcsoló ikonjáról bekapcsolt állapotban.](./media/end-user-drill/power-bi-drill-icon2.png).

    Most már lehetősége van arra, hogy **egyszerre egy mezőnyit hatoljon le**.

    ![Képernyőkép a vizualizációról, a lehatolás ki/be ikonra mutató nyíl bekapcsolt állapotáról.](media/end-user-drill/power-bi-drill-icon-new.png)

    Ha nem kapcsolja be a lehatolást, egy vizualizációs elem (például egy sáv, buborék vagy levél) kiválasztásakor nem történik lehatolás. Ehelyett a program keresztszűrést végez a jelentésoldal többi diagramján.

1. Válassza ki a **TN**-hez tartozó levélcsomópontot. A fatérkép ekkor megjeleníti az összes olyan várost Tennessee államban, amelyben van üzlet.

    ![Képernyőkép a fatérképről kizárólag TN adataival.](media/end-user-drill/power-bi-drill-down-one1.png)

1. Jelenleg a következőket végezheti el:

    1. További, Tennesseere vonatkozó lehatolás.

    1. Tennessee egy adott városára vonatkozó lehatolás.

    1. Kibontás (lásd: **Minden mező kibontása** alább).

    Most folytassuk azzal, hogy egyszerre egy-egy mezőben végzünk lehatolást.  Válassza ki a **Knoxville, TN** elemet. A fatérkép most a Knoxville-ben található üzlet postai irányítószámát mutatja.

    ![Képernyőkép a fatérképről a 37919-es irányítószámmal.](media/end-user-drill/power-bi-drill-down-one2.png)

    Nézze meg, hogyan változik a csempe, ahogy le- és felhatol a hierarchiában.

## <a name="expand-all-and-expand-one-field-at-a-time"></a>Az összes kibontása és egyszerre egy-egy mező kibontása

Egy olyan fatérkép, amely mindössze egy irányítószámot mutat, nem igazán hasznos.  Ezért bontsuk ki a hierarchiát egy szinttel lejjebb.  

1. Az aktív fatérképben válassza a *Kibontás lefelé* ikont ![Képernyőkép a kibontás lefelé ikonról](./media/end-user-drill/power-bi-drill-icon6.png). A fatérkép ekkor a hierarchia két szintjét mutatja: irányítószámot és üzletnevet.

    ![Képernyőkép a fatérképről az irányítószámmal és az üzletnévvel](./media/end-user-drill/power-bi-expand1.png)

1. Ha meg szeretné tekinteni a Tennessee-hez tartozó adatok mind a négy hierarchiaszintjét, válassza a felhatolás nyilat addig, amíg el nem éri a faszerkezetes térképen a második szintet, amely a **Total units this year by territory and city** (Összes egység ebben az évben terület és város szerint).

    ![Képernyőkép a fatérképről TN összes adatával.](media/end-user-drill/power-bi-drill-down-one1.png)

1. Győződjön meg róla, hogy továbbra is be van kapcsolva a lehatolás, ![Képernyőkép a lehatolás be- és kikapcsoló ikonjáról bekapcsolt állapotban.](./media/end-user-drill/power-bi-drill-icon2.png) majd válassza a *Kibontás lefelé* ikont ![Képernyőkép a kibontás lefelé ikonról](./media/end-user-drill/power-bi-drill-icon6.png). A fatérképen ekkor további részletek jelennek meg. A város és az állam mellett most már irányítószámot is mutat.

    ![Képernyőkép a vizualizációról, amely várost, államot és irányítószámot is megjelenít.](./media/end-user-drill/power-bi-expand-one3.png)

1. Válassza a *kibontás lefelé* ikont még egyszer: ezzel megjeleníti a Tennesee-hez tartozó adatok mind a négy hierarchiaszintjét a fatérképen. Ha még több részletet szeretne, mutasson rá egy levélcsomópontra.

    ![Képernyőkép a fatérképről, amelyen levélcsomópont-specifikus eszköztár jelent meg.](./media/end-user-drill/power-bi-expand-all.png)

## <a name="drilling-filters-other-visuals"></a>Más vizualizációk szűrése részletezéskor

A Részletezés mód használatakor el kell döntenie, hogy a lehatolás és a kibontás milyen hatással legyen az oldal többi vizualizációjára.

Alapértelmezés szerint a lehatolás nem szűri a jelentés többi vizualizációját. Ez a funkció bekapcsolható a Power BI Desktopban és a Power BI szolgáltatásban.

1. A Desktopban válassza a **Formázás** lapfület, majd jelölje be a **Más vizualizációk részletező szűrése** lehetőség melletti jelölőnégyzetet.

    ![Képernyőkép a Power BI Desktop Más vizualizációk részletező szűrése beállításáról](./media/end-user-drill/power-bi-drill-filters-desktop.png)

1. Ha most lehatolást, felhatolást vagy kibontást végez egy hierarchiával rendelkező vizualizációnál, ez a művelet az oldal más vizualizációit is szűrni fogja.

    ![Képernyőkép az eredményről a Desktopban.](./media/end-user-drill/power-bi-drill-filters.png)

    ![Képernyőkép egy másik eredményről a Desktopban.](./media/end-user-drill/power-bi-drill-filters2.png)

> [!NOTE]
> A Power BI szolgáltatásban ezt úgy engedélyezheti, ha a felső menüsávban kiválasztja a **Vizualizációk interakciói** > **Más vizualizációk részletező szűrése** lehetőséget.
>
> ![Képernyőkép a Power BI szolgáltatás Más vizualizációk részletező szűrése beállításáról](./media/end-user-drill/power-bi-drill-filters-service.png)

## <a name="learn-about-the-hierarchy-axis-and-hierarchy-group"></a>A hierarchiatengely és hierarchiacsoport ismertetése

A hierarchiatengely és a hierarchiacsoport tulajdonképpen a megtekinteni kívánt adatok részletességét szabályozó eszközöket jelenti. A kategóriákba és alkategóriákba csoportosítható minden adat (így a dátum- és időadatok is) rendelkezik hierarchiával.

Ha egy Power BI-vizualizációt hierarchiával együtt szeretne létrehozni, jelöljön ki egy vagy több adatmezőt, amelyet a **Tengely**vagy a **Csoport** gyűjtőhöz ad. Ezután adja hozzá az adatmezőkként vizsgálni kívánt adatokat az **Értékek** gyűjtőhöz ad. Ha a *Részletezés mód* ikonjai a vizualizáció jobb és bal felső sarkában jelennek meg, akkor biztos lehet benne, hogy az adatok hierarchikusak.

Alapvetően kétféle hierarchikus adatokkal dolgozunk:

- Dátum- és időadatok – Ha egy Dátum/idő adattípussal rendelkező adatmezője van, akkor hierarchikus adatokkal dolgozik. A Power BI automatikusan létrehozza a hierarchiát az adatmezőkhöz. Az értékek [Dátum/idő](https://msdn.microsoft.com/library/system.datetime.aspx) struktúra szerint elemezhetők. A **Tengely** vagy a **Csoport** gyűjtőhöz csak egy Dátum/Idő mezőt kell adnia.

- Kategorikus adatok – Ha a Power BI algyűjteményeket tartalmazó gyűjteményekből származtatja az adatokat, vagy olyan adatsorokkal rendelkezik, amelyeknek közös értékeik vannak, akkor hierarchikus adatokkal dolgozik.

A Power BI segítségével egyesével vagy részhalmazonként kibonthatja ezeket. Lehatolhat a szintenkénti részhalmazokig, vagy minden részhalmazt egyszerre megtekinthet egy szinten. Például lehatolhat egy adott évig, vagy megtekintheti az egyes évek eredményeit a hierarchiában lefelé haladva.

Hasonlóképpen hatolhat felfelé is.

A következő szakaszok a legmagasabb, a középső és a legalsó nézetből való lehatolást ismertetik.

### <a name="hierarchical-data-and-time-data"></a>Hierarchikus és időadatok

Ehhez a példához:

1. Használja fel a [kiskereskedelmi elemzési mintát](../sample-datasets.md), és hozzon létre egy halmozott oszlopdiagram típusú vizualizációt a következő adatokkal:

    | Panel | Mező |
    | ---- | ----- |
    | Tengely | Idő<br>\|\_ Hónap |
    | Értékek | Értékesítés<br>\|\_ ÖsszesÉrtékesítés |

    Bár a Tengely adatmezője a **Hónap**, a **Tengely** gyűjtőben továbbra is létrehoz egy **Év** kategóriát is. Ennek az az oka, hogy a Power BI a teljes Dátum/Idő-struktúrát megadja az összes beolvasott értékhez. A hierarchia tetején az év adatai jelennek meg.

    ![Képernyőkép az adatok éves csoportosítását megjelenítő egyetlen sávról](media/end-user-drill/power-bi-hierarchical-axis-datetime-1.png)

1. A Részletezés módban kattintson a diagram sávjára, ha egy szinttel lejjebb szeretne lépni a hierarchiában. Itt három sávot láthat, amelyek az elérhető negyedéveknek felelnek meg.

1. A bal felső sarokban található ikonok közül válassza az **Expand all down one level of the hierarchy** (Az összes kibontása a hierarchia egy szintjével lejjebb) lehetőséget.

1. Ezt ismételje meg a hierarchia legalsó szintjével is, amely az egyes hónapok eredményeit jeleníti meg.

    ![Képernyőkép a sávdiagram havi bontású sávaival](media/end-user-drill/power-bi-hierarchical-axis-datetime-2.png)

A vizualizáción kívül az egyes jelentések adataiban is láthatjuk a hierarchiát. A jobb felső sarokban kattintson a három pontra, majd az **Adatok megjelenítése** lehetőségre. Az alábbi táblázat egy jelentés egyetlen hónapjában vagy minden hónapjában végzett lehatolásának eredményeit jeleníti meg:

|Kibontás módja|Év|Negyedév|Hónap|Nap|
| --- |:---:|:---:|:---:|---|
|Egyirányú|![egy év](./media/end-user-drill/power-bi-hierarchical-year.png)|![egy negyedév](media/end-user-drill/power-bi-hierarchical-quarter.png)|![egy hónap](./media/end-user-drill/power-bi-hierarchical-one-month.png)|![egy nap](media/end-user-drill/power-bi-hierarchical-one-day.png)|
|Az összes|![összes év](./media/end-user-drill/power-bi-hierarchical-year.png)|![összes negyedév](media/end-user-drill/power-bi-hierarchical-quarter.png)|![összes hónap](./media/end-user-drill/power-bi-hierarchical-all-month.png)|![összes nap](media/end-user-drill/power-bi-hierarchical-all-day.png)|

Az adatok megegyeznek a **negyedév** és az **év** jelentéseiben. Ha lehatol az **Értékek** részletességi szintjéig, az egyetlen hónapra vonatkozó jelentés konkrétabb adatokat jelenít meg, az összes hónapra vonatkozó jelentés pedig több adatot tartalmaz.

### <a name="hierarchical-category-data"></a>Hierarchikus kategóriaadatok

A gyűjteményekből és algyűjteményekből modellezett adatok hierarchikusak.

Jó példák erre a helyadatok. Vegyünk például egy táblázatot egy olyan adatforrásban, amely az Ország, Állam, Város és Irányítószám oszlopokkal rendelkezik. Azok az adatok, amelyek megegyező Ország, Állam és Város értékekkel bírnak, hierarchikusak.

Ehhez a példához:

1. Használja a [kiskereskedelmi elemzési mintát](../sample-datasets.md). Hozzon létre egy halmozott oszlopdiagramos vizualizációt a következő adatokkal:

    | Panel | Mező |
    | ---- | ----- |
    | Érték |Értékesítés<br>\|\_ Folyó évi összes egység |
    | Tengely | Store<br>\|\_ Terület<br>\|\_ Város – előfordulhat, hogy a Várost a **Jelmagyarázat** panelről a **Tengely** panelre kell húznia.<br>\|\_ Irányítószám<br>\|\_ Név |

    ![Képernyőkép a sávdiagramról a folyó évi összes egység terület szerinti adataival.](media/end-user-drill/power-bi-hierarchical-axis-category-1.png)

1. A Részletezés módban a bal felső sarokban található ikonok közül válassza az **Expand all down one level of the hierarchy** (Az összes kibontása a hierarchia egy szintjével lejjebb) lehetőséget háromszor.

    Ekkor a hierarchia legalsó szintjén kell lennie, amely a Terület, a Város és az Irányítószám szerint jeleníti meg az eredményeket.

    ![Képernyőkép a sávdiagram a hierarchia legalacsonyabb szintjével, a legnagyobb részletezéssel.](media/end-user-drill/power-bi-hierarchical-axis-category-2.png)

A vizualizáción kívül az egyes jelentések adataiban is láthatjuk a hierarchiát. A jobb felső sarokban kattintson a három pontra, majd az **Adatok megjelenítése** lehetőségre. Az alábbi táblázat egy jelentés egyetlen területén vagy minden területén végzett lehatolásának eredményeit jeleníti meg.

| Kibontás módja|Terület|Település|Irányítószám|Név|
| ---|:---:|:---:|:---:|---|
|Egyirányú|![egy terület](./media/end-user-drill/power-bi-hierarchical-territory.png)|![egy város](media/end-user-drill/power-bi-hierarchical-one-territory-city.png)|![egy irányítószám](./media/end-user-drill/power-bi-hierarchical-one-territory-city-postal.png)|![egy név](media/end-user-drill/power-bi-hierarchical-one-territory-city-postal-name.png)|
|Az összes|![összes terület](./media/end-user-drill/power-bi-hierarchical-territory.png)|![összes város](media/end-user-drill/power-bi-hierarchical-all-territory-city.png)|![összes irányítószám](./media/end-user-drill/power-bi-hierarchical-all-territory-city-postal.png)|![összes név](media/end-user-drill/power-bi-hierarchical-all-territory-city-postal-name.png)|

 A lehatolás során láthatja, hogy az **egyetlen** területre vonatkozó jelentés konkrétabb adatokat jelenít meg, az **összes** területre vonatkozó jelentés pedig több adatot tartalmaz.

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások

Ha dátum mező felvételekor a rendszer nem hoz létre automatikusan időhierarchiát, elképzelhető, hogy a „dátum” mező nem dátum mezőként lett elmentve. Ha Ön az adatkészlet tulajdonosa:

1. Nyissa meg a Power BI Desktopban *Adatnézetben*.

1. Válassza ki a dátumot tartalmazó oszlopot.

1. A **Modellezés** lapon módosítsa az **Adattípust** **Dátum** vagy **Dátum/Idő** beállításra.

![Képernyőkép az adatkijelölési nézetről, ahol a jobb felső sarokban az Adattípus látható.](media/end-user-drill/power-bi-change-data-type2.png)

Ha a jelentés meg lett osztva Önnel, kérje meg a tulajdonost a módosítások végrehajtására.

## <a name="next-steps"></a>További lépések

[Vizualizációk a Power BI-jelentésekben](../visuals/power-bi-report-visualizations.md)

[A Power BI-jelentések](end-user-reports.md)

[Power BI – Alapfogalmak](end-user-basic-concepts.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
