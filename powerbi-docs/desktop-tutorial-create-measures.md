---
title: 'Oktatóanyag: Saját mértékek létrehozása a Power BI Desktopban'
description: 'Oktatóanyag: Saját mértékek létrehozása a Power BI Desktopban'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 59567b62c44a386b3890f68de49b9f7aed76aa45
ms.sourcegitcommit: 2aa83bd53faad6fb02eb059188ae623e26503b2a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/29/2019
ms.locfileid: "73019347"
---
# <a name="tutorial-create-your-own-measures-in-power-bi-desktop"></a>Oktatóanyag: Saját mértékek létrehozása a Power BI Desktopban
A Power BI Desktop leghatékonyabb adatelemzési megoldásait a mértékek segítségével alakíthatja ki. A mértékek segítségével számításokat hajthat végre az adatokon a jelentések használata közben. Ez az oktatóanyag ismerteti a mértékekről, és bemutatja, hogy miképpen hozhatja létre a saját alapvető mértékeit a Power BI Desktopban.

### <a name="prerequisites"></a>Előfeltételek
- Az oktatóanyag olyan Power BI-felhasználóknak szól, akik már jól ismerik a speciálisabb modellek létrehozásának eljárásait a szolgáltatásban. Ehhez ismernie kell, hogyan importálhat adatokat az Adatok lekérése és a Lekérdezésszerkesztő segítségével, hogyan dolgozhat több kapcsolódó táblával, és hogyan adhat mezőket a jelentésvászonhoz. Ha még csak most ismerkedik a Power BI Desktoppal, mindenképp tekintse át a [Power BI Desktop használatának első lépéseit](desktop-getting-started.md) ismertető témakört.
  
- Töltse le a [Power BI Desktophoz készült Contoso Sales](http://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20Sample%20for%20Power%20BI%20Desktop.zip) mintafájlt, amely a fiktív Contoso, Inc. vállalat online értékesítési adatait tartalmazza. Az adatok egy adatbázisból lettek importálva, ezért nem tud kapcsolódni az adatforráshoz, és a Lekérdezésszerkesztőben sem tudja megtekinteni azt. Töltse le a fájlt a számítógépére, majd nyissa meg a Power BI Desktopban.

## <a name="understand-measures"></a>A mértékek ismertetése

A mértékek általában automatikusan jönnek létre. A Contoso Sales mintafájlban kattintson a Fields (Mezők) területen lévő **Sales** (Értékesítés) tábla melletti **SalesAmount** (ÉrtékesítésÖsszeg) mezőre, vagy húzza át a **SalesAmount** mezőt a jelentés vászonra. Ekkor egy új oszlopdiagram jelenik meg, amely a Sales tábla SalesAmount oszlopában található összes érték összegét mutatja.

![SalesAmount diagram](media/desktop-tutorial-create-measures/meastut_salesamountchart.png)

A Fields (Mezők) területen megjelenő, szigma ikonnal ![szigma ikon](media/desktop-tutorial-create-measures/meastut_sigma.png) jelölt mezők numerikusak, és az értékeik összesíthetők. A Power Desktop nem tüntette fel egyetlen táblában a SalesAmount értékeinek sokaságát, ehelyett egy numerikus adattípust észlelt, és automatikusan létrehozott és kiszámolt egy mértéket az adatok összesítéséhez. A numerikus adattípusok alapértelmezett összesítése az összeg, de könnyedén alkalmazhat más összesítéseket is, mint például az átlag vagy a darabszám. A mértékek megértéséhez elengedhetetlen az összesítések megértése, mert minden mérték valamilyen típusú összesítést hajt végre. 

A diagram összesítéstípusának átlagra módosításához a Vizualizációk panel **Value** (Érték) területén kattintson a lefelé mutató nyílra a **SalesAmount** mellett, és válassza az **Average** (Átlag) lehetőséget. A vizualizáció módosul, és a SalesAmount mező értékesítési értékeinek átlagát mutatja.

![SalesAmount átlagot megjelenítő diagram](media/desktop-tutorial-create-measures/meastut_salesamountaveragechart.png)

Az összesítés típusa a kívánt eredménytől függően módosítható, de nem minden összesítéstípus alkalmazható minden numerikus adattípusra. Például a SalesAmount mező esetében az Összeg és az Átlag típusnak van értelme. A Minimum és a Maximum is alkalmazható. A Darabszám viszont nem igazán értelmezhető, mert bár a SalesAmount mező numerikus értékeket tartalmaz, azok valójában pénznemben kifejezett összegek.

A mértékekből számított értékek a jelentésben végrehajtott beállításoktól függően változnak. Ha például áthúzza a **RegionCountryName** (RégióOrszágNév) mezőt a**Geography** (Földrajzi hely) tábláról a diagramra, a jelentés országokra bontva átlagolja és jeleníti meg az értékesítési összeget.

![SalesAmount országonként](media/desktop-tutorial-create-measures/meastut_salesamountavchartbyrcn.png)

Amikor egy mérték eredménye a jelentés használata közben módosul, a módosulás a mérték *környezetében* megy végbe. Valahányszor módosítja a jelentés vizualizációit, megváltoztatja azt a környezetet, amelyben a mérték kiszámítja és megjeleníti az eredményeket.

## <a name="create-and-use-your-own-measures"></a>Saját mértékek létrehozása és használata

A legtöbb esetben a Power BI a választott mező- és összesítéstípusok alapján automatikusan kiszámítja és visszaadja az értékeket, de összetettebb egyéni számítások végrehajtásához érdemes saját mértékeket létrehoznia. A Power BI Desktopban a Data Analysis Expressions (Adatelemzési kifejezések, DAX) képletnyelv használatával hozhatja létre a saját mértékeket. 

A DAX-képletek számos olyan függvényt, műveletet és szintaxist használnak, amelyek megegyeznek az Excel-képletekével. A DAX-függvények azonban relációs adatbázisokhoz lettek kialakítva, és a jelentések használata során dinamikusabb számításokat hajtanak végre. Összesen több mint 200 DAX-függvény létezik az olyan egyszerű összesítő függvényektől, mint az összeg és az átlag, az összetettebb statisztikai és szűrőfüggvényekig. A DAX használatáról számos forrásból tájékozódhat. Miután elolvasta ezt az oktatóanyagot, mindenképp tekintse meg a következő forrást: [A DAX alapszintű használata a Power BI Desktopban](desktop-quickstart-learn-dax-basics.md).

A létrehozott saját mérték hozzáadódik a választott tábla Fields (Mezők) listájához, és a *modell* nevet kapja. A modell mértékek előnyei közé tartozik, hogy a könnyebb azonosítás érdekében tetszés szerint elnevezhetők, argumentumként használhatók más DAX-kifejezésekben, és igen gyorsan végezhetők velük összetett számítások.

>[!TIP]
>A Power BI Desktop 2018. februári kiadásától kezdődően **gyorsmérők** néven számos gyakran használt számítás érthető el, amelyek a kívánt DAX-képleteket azon értékek alapján állítják össze, amelyeket Ön egy párbeszédablakban adott meg. Ezek a hatékony gyorsszámítások kiválóan alkalmasak a DAX használatának gyakorlására és az egyéni mértékek feltöltésére is. A gyorsmérők létrehozásához vagy vizsgálatához kattintson az **New quick measure** (Új gyorsmérő) elemre a tábla **További beállítások** listáján, vagy a **Számítások** elemre a menüszalag Kezdőlap lapján. A gyorsmérők létrehozásáról és használatáról lásd még [A gyorsmérők használata](desktop-quick-measures.md) című témakört.

### <a name="create-a-measure"></a>Mérték létrehozása

A nettó értékesítések értékét szeretné kiszámítani azzal a módszerrel, hogy a teljes értékesítési összegből kivonja a kedvezményeket és a visszatérítéseket. Bármilyen környezet jelenik meg a vizualizációban, mindenképp szüksége lesz egy olyan mértékre, amely a SalesAmount (ÉrtékesítésÖsszeg) értékből kivonja a DiscountAmount (KedvezményÖsszeg) és a ReturnAmount (VisszatérítésÖsszeg) értékét. Bár a Mezők listában nincsen Net Sales (Nettó értékesítések) mező, rendelkezésre állnak azok az építőelemek, amelyekből létrehozhatja a nettó értékesítést kiszámító saját mértéket. 

1.  Kattintson jobb gombbal a Mezők területen látható **Sales** táblára, vagy vigye a kurzort a tábla fölé, válassza a **További beállítások** (...) elemet, majd válassza az **Új mérték** menüpontot. Ez menti az új mértéket a Sales táblába, ahol később könnyebben megtalálhatja.
    
    ![Új mérték](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure.png)
    
    Az új mértéket úgy is létrehozhatja, hogy a Power BI Desktop menüszalagjának Kezdőlap lapján a **New Measure** elemre kattint.
    
    ![Új mérték a menüszalagról](media/desktop-tutorial-create-measures/meastut_netsales_newmeasureribbon.png)
    
    >[!TIP]
    >A menüszalagról bármely táblában létrehozható az új mérték, de könnyebb lesz megtalálni, ha ott hozza létre, ahol használni szeretné. Ebben az esetben először a Sales táblát válassza ki, és csak ezután kattintson a **New Measure** elemre. 
    
    A jelentésvászon tetején megjelenő szerkesztőlécen átnevezheti a mértéket, és beírhatja a DAX-képletet.
    
    ![Szerkesztőléc](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formulabar.png)
    
2.  Alapértelmezés szerint az új mérték neve egyszerűen Measure (mérték). Ha nem nevezi át, a további új mértékek a Measure 2, Measure 3, stb. nevet kapják. Mivel könnyen azonosítható mértékre van szüksége, emelje ki a **Measure** szót a szerkesztőlécen, majd írja be a helyére a **Net Sales** (Nettó értékesítések) kifejezést.
    
3.  Most elkezdheti az új képlet beírását. Az egyenlőségjel után kezdje begépelni a **Sum** (Összeg) szót. A gépelés során legördülő menüben megjelenik az adott betűkkel kezdődő DAX-függvények listája. Szükség esetén görgessen le a **SUM** lehetőség kiválasztásához, majd nyomja le az Enter billentyűt.
    
    ![SUM kiválasztása](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_s.png)
    
    Ekkor egy nyitó zárójel jelenik meg egy újabb legördülő javaslatlistával, amely a SUM függvénynek továbbadható összes elérhető oszlopot tartalmazza.
    
    ![Oszlop kiválasztása](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_sum.png)
    
    A kifejezések mindig zárójelek között jelennek meg. Ebben a példában a kifejezés csak egy olyan argumentumot tartalmaz, amely továbbadható a SUM függvénynek, és ez a SalesAmount oszlop. Kezdje el a „SalesAmount” kifejezés gépelését, amíg a listán csak egyetlen érték marad: Sales(SalesAmount). A táblanévhez csatolt oszlopnév az oszlop *teljesen minősített* neve. A teljesen minősített oszlopnevek olvashatóbbá teszik a képleteket. 
    
    ![SalesAmount oszlop kiválasztása](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_salesam.png)
    
4. Válassza a **Sales[SalesAmount]** elemet, majd írjon be egy záró zárójelet.
    
    > [!TIP]
    > A szintaxishibákat leggyakrabban a hiányzó vagy rossz helyre beírt záró zárójelek okozzák,
    
    
    
5.  A másik két oszlop kivonásához:
    1. Miután bezárta az első kifejezés zárójelét, írjon be egy szóközt, egy mínusz operátort ( **-** ), majd egy újabb szóközt. 
    2. Adjon meg egy másik SUM függvényt, és kezdje el a „DiscountAmount” kifejezés beírását, amíg ki tudja választani argumentumként a **Sales[DiscountAmount]** oszlopot. Írja be a záró zárójelet. 
    3. Írjon be egy szóközt, még egy mínusz operátort, még egy SUM függvényt a **Sales[ReturnAmount]** argumentummal, és egy záró zárójelet.
    
    ![A képlet befejezése](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_discamount.png)
    
6.  A képlet befejezéséhez és érvényesítéséhez nyomja le az Enter billentyűt, vagy kattintson a szerkesztőlécen lévő pipa jelre. Az érvényesített mérték mostantól használható a Sales tábla mezőlistáján. 
    
    ![A mérték a mezőlistán](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_complete.png)
    
Ha a képlet beírásánál elfogy a hely, vagy szeretné több sorba rendezni a képletet, nyisson meg több helyet a szerkesztőléc jobb oldalán lévő sávnyílra kattintva.

![Sávnyíl a képlet mellett](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_chevron.png)

Ha az **Alt-Enter** billentyűre kattint, különböző sorokba rendezheti a képlet részeit, a **Tab** használatával pedig áthelyezheti az elemeket.

![Kibontott képlet](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_expanded.png)

### <a name="use-your-measure-in-the-report"></a>A mérték használata a jelentésben
Mostantól felveheti a Net Sales (Nettó értékesítés) értéket a jelentésvásznon, és kiszámíthatja a jelentéshez hozzáadott bármely mező nettó értékesítési értékét. Nettó értékesítés megtekintése országonként:

1. Kattintson a **Sales** tábla **Net Sales** mértékére, vagy húzza át a jelentésvászonra.
    
2. Kattintson a **Geography** (Földrajzi hely) tábla **RegionCountryName** (RégióOrszágNév) mezőjére, vagy húzza át a diagramra.
    
    ![Nettó értékesítés országonként](media/desktop-tutorial-create-measures/meastut_netsales_byrcn.png)
    
Ha a **SalesAmount** mezőre kattint, vagy áthúzza a diagramra, megtekintheti a nettó és az összes értékesítés közti különbséget országonként. 

![Értékesítések összege és Nettó értékesítés országonként](media/desktop-tutorial-create-measures/meastut_netsales_byrcnandsalesamount.png)

Az ábra most két mértéket használ: Az automatikusan összeadott SalesAmount értéket, és az imént létrehozott saját Net Sales értéket. Mindkét mértéket egy másik mező, a RegionCountryName (RégióOrszágNév) környezetében számolta ki a rendszer.
    
### <a name="use-your-measure-with-a-slicer"></a>Saját mérték használata szeletelővel

Szeletelő hozzáadásával tovább szűrheti a nettó értékesítés és az összes értékesítés értékeit a naptári év alapján.
    
1.  Kattintson egy üres területre a diagram mellett, majd kattintson a **Vizualizációk** menüben található **Tábla** vizualizációra. Ezzel létrehoz egy üres táblavizualizációt a jelentésvásznon.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_blanktable.png)
    
2.  Húzza a **Year** (Év) mezőt a **Calendar** (Naptár) táblából erre az üres táblavizualizációra. Mivel az Év numerikus mező, a Power BI Desktop összeadja a benne található értékeket, de ennek összegzésként nincs sok értelme. 
    
    ![Év összegzése](media/desktop-tutorial-create-measures/meastut_netsales_yearaggtable.png)
    
3.  A Vizualizációk táblán lévő **Values** (Értékek) területen kattintson a **Year** (Év) elem mellett található lefelé mutató nyílra, majd kattintson a **Don't summarize** (Nincs összegzés) lehetőségre. A tábla most már az egyes éveket mutatja.
    
    ![Nincs összegzés](media/desktop-tutorial-create-measures/meastut_netsales_year_donotsummarize.png)
    
4.  Ha a Vizualizációk ablaktáblán kiválasztja a **Szeletelő** ikont, szeletelővé alakítja a táblát.

    ![Átalakítás szeletelővé](media/desktop-tutorial-create-measures/meastut_netsales_year_changetoslicer.png)
    
5.  Válasszon ki egy tetszőleges értéket a **Year** (Év) szeletelőben a **Nettó értékesítés és értékesítési összeg országonként** diagram megfelelő szűréséhez. A Power BI újraszámolja a Net Sales és a SalesAmount értékeit, majd a kiválasztott Év mező környezetében jeleníti meg az eredményt. 
    
    ![Év szerint szeletelt diagram](media/desktop-tutorial-create-measures/meastut_netsales_chartslicedbyyear.png)

### <a name="use-your-measure-in-another-measure"></a>Saját érték használata egy másik értéken belül

Annak kimutatásához, hogy értékesített darabszámra vetítve melyik terméknél a legnagyobb a nettó értékesítési összeg, olyan mértékre van szükség, amely a nettó értékesítést elosztja az értékesített darabok számával. Létrehozhat egy új értéket, amely elosztja a saját készítésű Net Sales mérték eredményét a Sales[SalesQuantity] összegével.

1.  Hozzon létre egy **Net Sales per Unit** (Darabszámra vetített nettó értékesítés) nevű mértéket a Sales táblában.
    
2.  A szerkesztőlécen kezdje begépelni a **Net Sales** kifejezést. A javaslati listában megjelennek a választható lehetőségek. Válassza a **[Net Sales]** mértéket.
    
    ![Képlet a Net Sales használatával](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2a.png)
    
    A mértékekre úgy is hivatkozhat, ha csak egy nyitó szögletes zárójelet ( **[** ) ír be. A javaslati listában csak a képlethez hozzáadható mértékek jelennek meg.
    
    ![A szögletes zárójelben csak mértékek jelennek meg](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2b.png)
    
3.  Írjon be egy szóközt, egy osztási operátort ( **/** ), majd még egy szóközt, egy SUM függvényt, és gépelje be a **Quantity** (Mennyiség) kifejezést. A javaslati lista az összes olyan oszlopot tartalmazza, amelyeknek a nevében szerepel a Quantity (Mennyiség) kifejezés. Válassza a **Sales[SalesQuantity]** lehetőséget, zárja be a zárójelet, majd nyomja le az ENTER billentyűt, vagy kattintson a pipa jelre a képlet érvényesítéséhez. A képletnek ilyennek kell lennie:
    
    `Net Sales per Unit = [Net Sales] / SUM(Sales[SalesQuantity])`
    
4. Válassza ki a **Net Sales per Unit** (Darabszámra vetített nettó értékesítés) mértéket a Sales tábláról, vagy húzza át egy üres területre a jelentésvásznon. A diagram most az összes eladott termékre mutatja a darabszámonkénti nettó értékesítési összeget, ami nem túl hasznos információ. 
    
    ![Teljes nettó értékesítés darabszámonként](media/desktop-tutorial-create-measures/meastut_nspu_chart.png)
    
5. A megjelenítés megváltoztatásához módosítsa a diagramvizualizáció típusát **Faszerkezetes térképre**.
    
    ![Módosítás faszerkezetes térképre](media/desktop-tutorial-create-measures/meastut_nspu_changetotreemap.png)
    
6. Kattintson a **Product Category** (TermékKategória) mezőre, vagy húzza át a Vizualizáció panel faszerkezetes térképére vagy Csoport mezőjére. Ezek már fontos információk!
    
    ![Faszerkezetes térkép a Termékkategória alapján](media/desktop-tutorial-create-measures/meastut_nspu_byproductcat.png)
    
7. Próbálja ki, hogy eltávolítja a **ProductCategory** mezőt, és helyette a **ProductName** (TermékNév) mezőt húzza át a diagramra. 
    
    ![TermékNév faszerkezetes térképe](media/desktop-tutorial-create-measures/meastut_nspu_byproductname.png)
    
Rendben, ez itt most csak játszadozás, de azért elég menő, ezt be kell látnia! Kísérletezzen bátran a vizualizáció egyéb szűrési és formázási lehetőségeivel is.

## <a name="what-youve-learned"></a>Az oktatóanyag összefoglalása
A mértékek nagy segítséget nyújtanak az adatok tetszés szerinti elemzéséhez. Ez az oktatóanyag megmutatta, hogyan hozhat létre mértékeket a szerkesztőléc használatával, hogyan adhat nekik könnyen értelmezhető nevet, és hogyan találhatja meg, illetve választhatja ki a megfelelő képletelemeket a DAX javaslati listákkal. Tájékozódhatott a környezetekről is, hiszen a mértékekkel végzett számítások aszerint változnak, hogy milyen más mezők és kifejezések jelennek még meg a képletben.

## <a name="next-steps"></a>Következő lépések
- További információk a Power BI Desktop számos gyakori számítást nyújtó gyorsmérőiről: [A gyorsmérők használata általános és nagy igényű számítások egyszerű végrehajtásához](desktop-quick-measures.md).
  
- A DAX-képletek részletesebb megismeréséhez és speciálisabb mértékek létrehozásához lásd: [A DAX alapszintű használata a Power BI Desktopban](desktop-quickstart-learn-dax-basics.md). Ez a cikk a DAX alapvető fogalmaira, a szintaxisra, a függvényekre és a környezet alaposabb megértésére összpontosít.
  
- Mindenképp vegye fel a [Data Analysis Expressions (DAX) referenciát](https://msdn.microsoft.com/library/gg413422.aspx) a kedvencei közé. Ebben találja részletesen leírva a DAX-szintaxist, az operátorokat, valamint a több mint 200 DAX-függvényt.

