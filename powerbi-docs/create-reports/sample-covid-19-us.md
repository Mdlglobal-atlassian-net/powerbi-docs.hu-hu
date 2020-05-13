---
title: COVID-19-nyomonkövetési minta az USA tagállami és helyi szintű közigazgatási szervei részére
description: Letöltheti a mintajelentést, és módosíthatja azt az USA tagállami és helyi szintű közigazgatási szerveinek COVID-19-járványra vonatkozó adataival.
author: LukaszPawlowski-MS
ms.reviewer: maggies
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/28/2020
ms.author: lukaszp
LocalizationGroup: Samples
ms.openlocfilehash: aca7fc70bc70de553eee070ce5e1522b96c94880
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83277893"
---
# <a name="covid-19-tracking-sample-for-us-state-and-local-governments"></a>COVID-19-nyomonkövetési minta az USA tagállami és helyi szintű közigazgatási szervei részére

A Power BI csapata létrehozott egy COVID-19-nyomonkövetési mintát, amellyel az USA tagállami és helyi szintű közigazgatási szervei közzétehetnek és testre szabhatnak egy interaktív jelentést a COVID-19-ről. A Power BI Desktop használatával elemezhetik és megjeleníthetik a COVID-19-járvánnyal kapcsolatos adatokat belső használatra megyei, tagállami és országos szinten. Ezt követően a Power BI Webes közzététel funkciójával nyilvánosan megoszthatják a jelentést a polgárok tájékoztatása céljából. Ez a cikk különböző lehetőségeket mutat be az interaktív Power BI-vizualizációk nyilvános híradásokhoz, blogon vagy webhelyen történő felhasználására.

:::image type="content" source="media/sample-covid-19-us/covid-19-us-tracking-sample.png" alt-text="COVID-19-minta USA-beli adatokkal":::

Ez a cikk a következőket ismerteti:

- Beágyazási kód másolása és elhelyezése saját webhelyen. 
- Testreszabás, például adott tagállam formázása.
- Közzététel a Power BI szolgáltatásban.
- Webes közzététel. 
- Adategyesítés más forrásból származó adatokkal. 

## <a name="prerequisites"></a>Előfeltételek

A Power BI saját célra történő használatához az alábbi előfeltételeket kell teljesítenie:

- Az ingyenes [Power BI Desktop](https://powerbi.microsoft.com/desktop/) alkalmazás letöltése.
- Regisztráció a [Power BI szolgáltatásra](https://powerbi.microsoft.com/get-started/).

## <a name="option-1-pre-built-embed-code"></a>1\. lehetőség Előregyártott beágyazási kód

A Microsoft közzétette a mintajelentést, és készített hozzá egy webes beágyazási kódot. A beágyazási kóddal beágyazhatja a saját webhelyén a teljes mintát, beleértve az országos nézetet, illetve a tagállami és megyei szintű részletezést. Mielőtt közzétenné az adatokat, javasoljuk a cikkben olvasható [felelősséget kizáró nyilatkozatok](#disclaimers) áttekintését.

Ha szeretné felvenni az interaktív grafikát a webhelyén, másolja és illessze be az alábbi beágyazási kódot arra a helyre, ahol meg kívánja jeleníteni azt a weblapján.  

```
<iframe width="1600" height="900" src="https://app.powerbi.com/view?r=eyJrIjoiMmI2ZjExMzItZTcwNy00YmUwLWFlMTAtYTUxYzVjODZmYjA5IiwidCI6ImMxMzZlZWMwLWZlOTItNDVlMC1iZWFlLTQ2OTg0OTczZTIzMiIsImMiOjF9" frameborder="0" allowFullScreen="true"></iframe>
```

A beágyazási kód egy HTML iFrame-elem, amelyet bármely HTML-oldalra beilleszthet. Állítsa be a biztosított iFrame hosszát és szélességét a webhelynek megfelelően. A mintajelentés 16:9-es aránnyal készült, ezért válasszon olyan méretet, amely megőrzi ezt az arányt. Helyes megvalósítás esetén a grafika kiegészítő szürke szegély nélkül jelenik meg. A módosítások végrehajtásakor érdemes lehet [áttekinteni az iFrame méretezésével kapcsolatos tippeket és trükköket](../collaborate-share/service-publish-to-web.md#tips-for-iframe-height-and-width).

## <a name="option-2-customize-the-sample-power-bi-file"></a>2\. lehetőség A Power BI-mintafájl testreszabása

A Power BI-fájl Power BI Desktopban szerkeszthető .pbix formátumban tartalmazza az adatokat és az interaktív grafikát.  

Tipikus testreszabás lehet a jelentés adott tagállamra szűrése, majd egy saját beágyazási kód létrehozása a testreszabott jelentés webes közzétételéhez.

Az USAFacts a Creative Commons licenc keretében, forrásmegjelölés feltételével bocsátja rendelkezésre az adatokat. Az adatok közzététele előtt tekintse át a [felelősséget kizáró nyilatkozatokat](#disclaimers).

Első lépésként [töltse le (innen) a .pbix fájlt](https://go.microsoft.com/fwlink/?linkid=2125058).

### <a name="update-your-report"></a>A jelentés frissítése 

1. Ha még nem tette meg, töltse le a [Power BI Desktop](https://powerbi.microsoft.com/desktop/) ingyenes alkalmazás legújabb verzióját. 

2. Ha még nem tette meg, töltse le a [.pbix fájlt](https://go.microsoft.com/fwlink/?linkid=2125058), és nyissa meg a Power BI Desktopban.

3. A jelentés adott tagállamra szűréséhez a nyílra kattintva bontsa ki a Szűrők panelt.

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filters-pane.png" alt-text="A Szűrők panel kibontása":::

4. Válassza ki az Önt érdeklő tagállamot. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filter-selection.png" alt-text="Tagállam kiválasztása":::

5. A fájl mentéséhez válassza a **File** > **Save** (Fájl > Mentés) lehetőséget. 

### <a name="refresh-your-report"></a>A jelentés frissítése 

1. Kattintson a **Frissítés** gombra.

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-refresh-button.png" alt-text="Frissítés gomb":::

2. Válassza a **Névtelen** > **Csatlakozás** lehetőséget. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-azure-blob.png" alt-text="Névtelen kiválasztása":::

 
3. Válassza az **Adatvédelmi szintek figyelmen kívül hagyása** lehetőséget, és ha ez megjelenik, > **Mentés**. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-privacy-levels.png" alt-text="Adatvédelmi szintek beállítása":::

### <a name="publish-your-report-to-the-power-bi-service"></a>Jelentés közzététele a Power BI szolgáltatásban

Miután igényei szerint testre szabta a jelentést, [az alábbi lépések végrehajtásával teheti közzé a jelentést](../create-reports/desktop-upload-desktop-files.md) a Power BI szolgáltatásban.

### <a name="configure-scheduled-refresh"></a>Ütemezett frissítés beállítása

A jelentés adatainak naprakészen tartásához a jelentés közzététele után [beállíthatja az ütemezett frissítést](../connect-data/refresh-scheduled-refresh.md).

A lépések végrehajtásakor válassza az alábbi beállításokat:

1. Adatforrás azonosító adatainak hitelesítési módszere: Névtelen
2. Az adatforrás adatvédelmi szintjének beállítása: Nyilvános

A frissítési beállítás ellenőrzéséhez kattintson az adathalmazelemből elérhető [Azonnali frissítés](../connect-data/refresh-data.md#data-refresh) lehetőségre.

A frissített adatok az ütemezés minden futtatásakor betöltődnek. Az alapadatokat az USAFacts bocsátja rendelkezésre, és előfordulhat, hogy nem frissülnek olyan gyakran, mint a frissítési ütemezése. Az [USAFacts webhelyén](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/) megtekintheti a jelentésben használt adatok legutóbbi frissülésének idejét. 

Ha szeretné a saját webhelyén közzétenni a testreszabott jelentést, érdemes úgy beállítani az ütemezett frissítést, hogy legalább olyan gyakorisággal fusson, mint az USAFacts adatainak frissítése. Mivel az USAFacts minden nap eltérő időpontokban frissítheti az adatait, érdemes naponta több frissítést ütemezni. 

### <a name="create-a-publish-to-web-embed-code"></a>Beágyazási kód létrehozása webes közzétételhez 

A testreszabott jelentés saját webhelyen való közzétételéhez kövesse a [Saját beágyazási kód létrehozása webes közzétételhez](../collaborate-share/service-publish-to-web.md#create-embed-codes-with-publish-to-web) című cikk utasításait.

A beágyazási kód közzétételét követően a megerősítő párbeszédpanelen elérhető iFrame használatával végezhet beágyazást a webhelyen.

Ha a Power BI Desktopban módosítja a jelentést, közzéteheti és módosíthatja a meglévő jelentést a Power BI szolgáltatásban. A beágyazási kód nem változik. Körülbelül egy órába telik, amíg a jelentés módosításai vagy a frissített adatok megjelennek a webhelyén. 

## <a name="option-3-mash-up-data-from-another-source"></a>3\. lehetőség: Adategyesítés más forrásból származó adatokkal 

A jelentés adatait más forrásból származó adatokkal is egyesítheti. Az alábbi példa a [Johns Hopkins Egyetem](https://github.com/CSSEGISandData/COVID-19) adatait veszi alapul. Mielőtt közzétenné az adatokat, javasoljuk a cikkben olvasható [felelősséget kizáró nyilatkozatok](#disclaimers) áttekintését.

1. Válassza az **Adatok beolvasása** > **Web** lehetőséget.

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-get-data.png" alt-text="Adatok beolvasása gomb":::

2. Adja meg a következő URL-címet:

    ```
    https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_confirmed_global.csv
    ```

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-from-web.png" alt-text="Webes adatok kiválasztása":::

3. Válassza az **OK** lehetőséget. 

    > [!NOTE]
    > A Johns Hopkins Egyetem által közzétett hivatkozás módosulhat. A legújabb információkat a [Johns Hopkins GitHub-oldalán](https://github.com/CSSEGISandData/COVID-19) találja.

4. A **Betöltés** elemre kattintva töltse be a világszerte igazolt összes esetre vonatkozó adathalmazt.  

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-load-data.png" alt-text="Adatok betöltése a webről":::

    A [Csatlakozás weblapokhoz a Power BI Desktopból](../connect-data/desktop-connect-to-web.md) című cikkben találhat további információt a webről való adatbetöltésről.
    
Ezt követően megjelenítheti az adatokat a Power BI Desktopban. Végül hajtsa végre a **2. lehetőség** lépéseit: A jelentés közzétételéhez és az egyéni beágyazási kód létrehozásához kövesse a [Jelentés közzététele a Power BI szolgáltatásban](#publish-your-report-to-the-power-bi-service) című cikk utasításait. 

## <a name="option-4-use-the-covid-19-us-tracking-template-app"></a>4\. lehetőség: A COVID-19 USA-beli nyomon követésére szolgáló sablonalkalmazás használata

Egy további lehetőségként a Power BI csapata létrehozta a COVID-19-nyomkövetési *sablonalkalmazást* az azonnali induláshoz. A sablonalkalmazások egy adott adatforráshoz készült jelentésekből, irányítópultokból és adathalmazokból álló csomagok. Az AppSource-ról letölthetők, használhatók, igény szerint módosíthatók és terjeszthetők a munkatársak körében. 

A COVID-19 nyomkövetési sablonalkalmazás tartalmaz egy előre elkészített jelentést a COVID-19 metrikákról, amely használható változtatás nélkül, testre szabható közvetlenül a Power BI szolgáltatásban, vagy igény esetén letölthető, hogy más adatforrásokhoz is hozzáadhassa. Tájékozódjon [A COVID-19 USA-beli nyomon követésére szolgáló sablonalkalmazás](../connect-data/service-connect-to-covid-19-tracking.md) telepítéséről és az azonnal megtehető első lépésekről.

## <a name="about-the-data-source-for-this-report"></a>A jelentés adatforrásáról
Az interaktív jelentés az USA járványügyi és betegségmegelőzési központjától (CDC), valamint a tagállami és helyi szintű közegészségügyi intézményektől származó adatokat gyűjti. A megyei szintű adatokat az állami és helyi intézmények közvetlenül erősítik meg (hivatkozás).

Az adatokat az USAFacts bocsátja rendelkezésre. A gyakori adatfrissítések miatt az adatok nem feltétlenül azonosak a kormányzati szervek és a hírügynökségek által közölt pontos számokkal. További információkért, vagy az adatok letöltéséhez keresse fel az [USAFacts webhelyét](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/). 

## <a name="disclaimers"></a>Felelősséget kizáró nyilatkozatok

A jelentést és az adatokat „adott állapotukban”, „hibalehetőségekkel” és minden garancia nélkül tesszük közzé. A Microsoft nem nyújt kifejezett garanciát, és kifejezetten kizár minden vélelmezett garanciát, beleértve az eladhatóságra, az adott célú felhasználásra, valamint a nem jogsértésre vonatkozó szavatosságot.

Az USAFacts adatai Creative Commons licenc keretében érhetők el. A használat feltétele az USAFacts feltüntetése adatszolgáltatóként, és az USAFacts webhelyére mutató hivatkozás megadása. A hivatkozás pontos lépéseihez lásd az USAFacts webhelyének **#MadewithUSAFacts** oldalát: [Koronavírus az Egyesült Államokban: A COVID-19 terjedésének tagállamokra és megyékre bontott ábrázolása](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/).

A Johns Hopkins Egyetem adatait szerzői jog védi. Copyright 2020 Johns Hopkins University, Minden jog fenntartva. A nyilvános megjelenést kizárólag oktatási és tudományos kutatási célokra biztosítjuk. Itt találhatók meg az adategyesítési példában szereplő adatok teljes [Használati feltételei](https://github.com/CSSEGISandData/COVID-19/blob/master/README.md). További információkért keresse fel [a Johns Hopkins Egyetem webhelyét](https://coronavirus.jhu.edu/map-faq.html).

## <a name="next-steps"></a>Következő lépések

[Power BI-minták beszerzése](../create-reports/sample-datasets.md)




