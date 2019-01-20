---
title: 'Oktatóanyag: Facebook-elemzések a Power BI Desktop használatával'
description: 'Oktatóanyag: Facebook-elemzések a Power BI Desktop használatával'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: ae2d40d5a53a7a84c0f6070a7be1011968d7ed7b
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54276974"
---
# <a name="tutorial-facebook-analytics-using-power-bi-desktop"></a>Oktatóanyag: Facebook-elemzések a Power BI Desktop használatával

Ez az oktatóanyag az adatok Facebookról való importálását és azok Power BI Desktopban való használatát ismerteti. Ön adatokhoz fog kapcsolódni, importálni fogja az adatokat a Power BI Facebook-oldaláról, átalakításokat fog végezni az importált adatokon, valamint jelentésbeli vizualizációkban fogja használni az adatokat.

## <a name="connect-to-a-facebook-page"></a>Kapcsolódás egy Facebook-oldalhoz

Ez az oktatóanyag a [Microsoft Power BI Facebook-oldaláról](https://www.facebook.com/microsoftbi) (*https://www.facebook.com/microsoftbi*) származó adatokat használja. Nincs szükség semmilyen különleges hitelesítő adatra a kapcsolódáshoz, illetve az adatok oldalról való importálásához, kivéve személyes Facebook-fiók használatakor.

1. Nyissa meg a Power BI Desktopot, válassza az **Adatok lekérése** elemet az **Első lépések** párbeszédpanelen, vagy a **Kezdőlap** szalagfülön válassza az **Adatok lekérése**, majd a **Továbbiak...** elemet.
   
2. Az **Adatok lekérése** párbeszédpanelen válassza a **Facebook** elemet az **Online szolgáltatások** csoportban, majd válassza a **Kapcsolódás** parancsot.
   
   ![Adatok lekérése](media/desktop-tutorial-facebook-analytics/t_fb_getdataother.png)
   
   Egy párbeszédpanel jelenik meg, amely a külső szolgáltatások használatának kockázataira figyelmeztet.
   
   ![Külső szolgáltatásra vonatkozó figyelmeztetés](media/desktop-tutorial-facebook-analytics/t_fb_connectingtotps.png)
   
3. Válassza a **Folytatás** lehetőséget. Megjelenik a **Facebook**-párbeszédpanel.
   
4. Írja vagy illessze be az oldal nevét (**microsoftbi**) a **Felhasználónév** szövegmezőbe, válassza a **Bejegyzések** lehetőséget a **Kapcsolat** legördülő menüből, majd válassza az **OK** gombot.
   
   ![Kapcsolódás](media/desktop-tutorial-facebook-analytics/2.png)
   
5. Amikor a rendszer a hitelesítő adatokat kéri, jelentkezzen be a saját Facebook-fiókjába, és engedélyezze a Power BI-hozzáférést a fiókján keresztül.
   
   ![Hitelesítő adatok](media/desktop-tutorial-facebook-analytics/facebookcredentials.png)

   Miután csatlakozott a Power BI Facebook-oldalához, megjelenik az oldal **Bejegyzések** típusú adatainak előnézete. 
   
   ![Adatelőnézet](media/desktop-tutorial-facebook-analytics/t_fb_1-loadpreview.png)
   
## <a name="shape-and-transform-the-imported-data"></a>Az importált adatok formázása és átalakítása

Szeretné látni és megjeleníteni, hogy mely bejegyzések rendelkeznek a legtöbb hozzászólással adott időszakban, de észreveszi, hogy a **Bejegyzések** típusú adatok előnézetében a **created_time** adatai nehezen olvashatók és érthetők, és egyáltalán nincsenek hozzászólási adatok. El kell végezni az adatok formázását és tisztítását ahhoz, hogy a legtöbbet tudja kihozni az adatokból. A Power BI Desktop **Power Query-szerkesztőjével** a Power BI Desktopba való importálás előtt vagy után módosíthatja az adatokat. 

### <a name="split-the-datetime-column"></a>A dátum/idő oszlop felosztása

Először a **created_time** oszlopban található dátum- és időértékeket válassza szét a jobb olvashatóság érdekében. 

1. A Facebook adatelőnézeti területén válassza a **Szerkesztés** elemet. 
   
   ![Adatelőnézeti szerkesztés](media/desktop-tutorial-facebook-analytics/t_fb_1-editpreview.png)
   
   A Power BI Desktop **Power Query-szerkesztője** egy új ablakban nyílik meg, és megjeleníti a Power BI Facebook-oldaláról származó adatelőnézetet. 
   
   ![Power Query-szerkesztő](media/desktop-tutorial-facebook-analytics/t_fb_1-intoqueryeditor.png)
   
2. Válassza ki a **created_time** oszlopot. Vegye figyelembe, hogy az oszlop jelenleg szöveges adattípusnak minősül, amelyet a fejlécben az **ABC** ikon jelöl. Kattintson a jobb gombbal a fejlécre, majd válassza az **Oszlop felosztása > Elválasztó alapján** lehetőséget a legördülő menőben, vagy válassza az **Oszlop felosztása > Elválasztó alapján** lehetőséget a Kezdőlap szalagfül **Átalakítás** csoportjában.  
   
   ![Oszlop felosztása elválasztó alapján](media/desktop-tutorial-facebook-analytics/delimiter1.png)
   
3. Az **Oszlop felosztása elválasztó alapján** párbeszédpanelen válassza az **Egyéni** lehetőséget a legördülő menüből, és írja be a **T** karaktert a beviteli mezőbe (ez az a karakter, amely a created_time értékeinek időre vonatkozó részével kezdődik), majd válassza az **OK** gombot. 
   
   ![Oszlop felosztása elválasztó alapján párbeszédpanel](media/desktop-tutorial-facebook-analytics/delimiter2.png)
   
   A rendszer két olyan oszlopra osztja fel az eredeti oszlopot, amelyek a **T** elválasztó előtti és utáni sztringeket tartalmazzák (ezek nevei a következők: **created_time.1** és **created_time.2**). Vegye észre, hogy a Power BI automatikusan észleli és **Dátum** adattípusra módosítja az első oszlop adattípusát, míg **Idő** adattípusra a második oszlop adattípusát, és úgy formázza a dátum- és időértékeket, hogy azok jobban olvashatóbbak legyenek.
   
4. Az egyes oszlopfejlécekre duplán kattintva nevezze át az oszlopokat, vagy jelölje ki az egyes oszlopokat, és a menüszalag **Átalakítás** fülének **Minden oszlop** csoportjában válassza az **Átnevezés** parancsot, majd írja be az új oszlopfejléceket: **created_date** és **created_time**.
   
   ![Új dátum- és időoszlopok](media/desktop-tutorial-facebook-analytics/delimiter3.png)
   
### <a name="expand-the-nested-column"></a>A beágyazott oszlop kibontása

Most, hogy a dátum- és időadatok a kívánt módon jelennek meg, a beágyazott oszlop kibontásával jelenítheti meg a hozzászólások adatait. 

1. Válassza az **object_link** oszlopot, majd a ![kibontás ikon](media/desktop-tutorial-facebook-analytics/14.png) ikon kiválasztásával megnyithatja a **Kibontás/összesítés** párbeszédpanelt. Válassza a **kapcsolatok** elemet, majd válassza az **OK** gombot. 
   
   ![Az object_link kibontása](media/desktop-tutorial-facebook-analytics/expand1.png)
   
   Az oszlopfejléc a következőre változik: **object_link.connections**.
2. Újból válassza a ![kibontás ikon](media/desktop-tutorial-facebook-analytics/14.png) ikont az **object_link.connections** oszlop tetején, majd válassza a **hozzászólások** elemet és az **OK** gombot. Az oszlopfejléc a következőre változik: **object_link.connections.comments**.
   
3. Válassza a ![kibontás ikon](media/desktop-tutorial-facebook-analytics/14.png) ikont az **object_link.connections.comments** oszlop tetején, majd a Kibontás helyett ezúttal válassza az **Összesítés** elemet a párbeszédpanelen. Válassza az **Azonosító száma** lehetőséget, majd válassza az **OK** gombot. 
   
   ![Hozzászólások összesítése](media/desktop-tutorial-facebook-analytics/expand2.png)
   
   Az oszlop most már az egyes üzenetekhez tartozó hozzászólások számát mutatja. 
   
4. Nevezze át az **object_link.connections.comments.id száma** oszlopot a következőre: **Hozzászólások száma**.
   
5. Válassza ki a **Hozzászólások száma** fejléc melletti lefelé mutató nyilat, majd a **Csökkenő rendezés** kiválasztásával tekintheti meg a bejegyzéseket a hozzászólások csökkenő sorrendben való rendezésével. 
   
   ![Üzenetenkénti hozzászólások](media/desktop-tutorial-facebook-analytics/data-fixed.png)
   
### <a name="review-query-steps"></a>Lekérdezési lépések áttekintése

Miután a **Power Query-szerkesztő** használatával elvégzi az adatok formázását és átalakítását, a rendszer minden egyes lépést rögzít a Power Query-szerkesztői ablak jobb oldalán lévő **Lekérdezés beállításai** ablaktábla **Alkalmazott lépések** területén. Visszaléphet az Alkalmazott lépések használatával, és megtekintheti, hogy pontosan milyen módosításokat hajtott végre, valamint szerkesztheti, törölheti és átrendezheti az egyes lépéseket szükség szerint (bár ez kockázatos, mert a korábbi lépések módosítása a további lépések hibás rögzítéséhez vezethet). 

Az eddigi adatátalakítások alkalmazása után az Alkalmazott lépések terület a következőhöz hasonló:
   
   ![Alkalmazott lépések](media/desktop-tutorial-facebook-analytics/applied-steps.png)
   
   >[!TIP]
   >Az Alkalmazott lépések alapjául olyan képletek szolgálnak, amelyek **Power Query-nyelven** (más néven **M**) íródtak. A Kezdőlap szalagfül **Lekérdezés** csoportjában lévő **Speciális szerkesztő** kiválasztásával megtekintheti és szerkesztheti a képleteket. 

### <a name="import-the-transformed-data"></a>Az átalakított adatok importálása

Ha elégedett az adatokkal, a Kezdőlap szalagfül **Bezárás és alkalmazás** > **Bezárás és alkalmazás** elemének kiválasztásával importálhatja azokat a Power BI Desktop alkalmazásba. 
   
   ![Bezárás és alkalmazás](media/desktop-tutorial-facebook-analytics/t_fb_1-loadandclose.png)
   
   Egy párbeszédpanel jelenik meg, amelyen az adatok a Power BI Desktop adatmodellbe való betöltése követhető nyomon. 
   
   ![Adatok betöltése](media/desktop-tutorial-facebook-analytics/t_fb_1-loading.png)
   
   A betöltést követően az adatok a Jelentés nézetben jelennek meg a Mezők lista új lekérdezéseként.
   
   ![Új lekérdezés](media/desktop-tutorial-facebook-analytics/fb-newquery.png)
   
## <a name="use-the-data-in-report-visualizations"></a>Az adatok használata jelentésbeli vizualizációkban 

Most, miután betöltötte az adatokat a Facebook-oldalról, a vizualizációk használatával gyorsan és egyszerűen elemezheti azokat. A vizualizációk létrehozása egyszerű, egyszerűen válasszon ki egy mezőt, vagy húzza át azt a **Mezők** listából a jelentésvászonra.

### <a name="create-a-bar-chart"></a>Sávdiagram létrehozása

1. A Power BI Desktop jelentési nézetében válassza ki az **üzenet** elemet a mezőlistából, vagy húzza át azt a vászonra. Az összes bejegyzésüzenetet tartalmazó tábla megjelenik a vásznon. 
   
   ![Új lekérdezés](media/desktop-tutorial-facebook-analytics/table-viz.png)
   
2. A tábla kijelölése után válassza a **Hozzászólások száma** elemet a Mezők listában, vagy húzza át azt a táblába. 
   
3. Válassza a **Halmozott sávdiagram** ikont a Megjelenítések ablaktáblán. A tábla olyan sávdiagramra változik, amely a bejegyzésenkénti hozzászólások számát mutatja. 
   
   ![Sávdiagram](media/desktop-tutorial-facebook-analytics/barchart1.png)
   
4. Válassza a vizualizáció jobb felső sarkában a három pont (...) lehetőséget, majd a **Rendezés hozzászólások száma szerint** elem kiválasztásával csökkenő sorrendbe rendezheti a tábla adatait. 
   
   ![Rendezés hozzászólások száma szerint](media/desktop-tutorial-facebook-analytics/barchart2.png)
   
5. Vegye észre, hogy a rendszer a legtöbb hozzászólást **Üres** üzenettel társította (elképzelhető, hogy ezek a bejegyzések történetek, hivatkozások, videók vagy egyéb nem szöveges tartalmak lehetettek). Az Üres sor kiszűréshez válassza a Megjelenítések ablaktábla alján található **Szűrők** elem **üzenet (összes)** lehetőségét, válassza az **Összes kijelölése** lehetőséget, majd válassza az **Üres** lehetőséget a bejelölés eltávolításához. A Szűrők bejegyzés az **üzenet nem (Üres)** értékre változik, és az Üres sor eltűnik a diagramos vizualizációból. 
   
   ![Üres értékek kiszűrése](media/desktop-tutorial-facebook-analytics/barchart3.png)
   
### <a name="format-the-chart"></a>A diagram formázása

A vizualizáció kezd érdekes lenni, de nem túl sok bejegyzésszöveg látható a diagramon. További bejegyzésszöveg megjelenítése:

1. A diagramos vizualizáció fogópontjainak használatával méretezze át a diagramot úgy, hogy az a lehető legnagyobb legyen. 
   
2. A diagram kijelölése után válassza a **Formázás ikont** (festőhenger) a Megjelenítések ablaktáblán.
   
3. Válassza az **Y tengely** melletti lefelé mutató nyilat, majd húzza a **Maximális méret** felirat melletti csúszkát egészen jobbra (50%). 
4. Továbbá csökkentse a **szövegméretet** **10-es** értékre, hogy még több szöveg férjen el.
   
   ![Módosítások formázása](media/desktop-tutorial-facebook-analytics/barchart4.png)
   
   A diagramon most már több látszik a bejegyzés tartalmából. 
   
   ![További bejegyzések megjelenítése](media/desktop-tutorial-facebook-analytics/barchart5.png)
   
A diagram X tengelye (hozzászólások száma) nem pontos értékeket mutat, és zavarosnak tűnik a diagram alján. Ön inkább adatfeliratok használata mellett dönt. 

1. Válassza a Formázás ikont, majd az **X tengely** melletti csúszka használatával kapcsolja **ki** azt. 
   
2. Válassza az **Adatfeliratok** melletti csúszkát a feliratok **bekapcsolásához**. A diagramon most már megjelenik az egyes bejegyzésekhez tartozó hozzászólások pontos száma.
   
   ![Adatfeliratok alkalmazása](media/desktop-tutorial-facebook-analytics/barchart6.png)
   
### <a name="edit-the-data-type"></a>Az adattípus szerkesztése

Ez így már jobb, de az adatfeliratok mindegyike **.0** tizedesértékkel rendelkezik, amely zavaró és félrevezető, mivel a **bejegyzések számának** egész számnak kell lennie. Módosítani kell a **Bejegyzések száma** oszlop adattípusát egész számra.

1. Az adattípus szerkesztéséhez kattintson a jobb gombbal a **Lekérdezés1** elemre a Mezők listában, vagy mutasson rá az egérmutatóval, válassza a **További beállítások** három pontot (...), majd válassza a **Lekérdezés szerkesztése** lehetőséget. Használhatja a Kezdőlap szalagfül **Külső adatok** területének **Lekérdezések szerkesztése** parancsát is, ilyenkor válassza a **Lekérdezések szerkesztése** lehetőséget a legördülő menüből. A Power BI Desktopban található **Power Query-szerkesztő** külön ablakban nyílik meg.
   
   ![Lekérdezés szerkesztése a Mezők listából](media/desktop-tutorial-facebook-analytics/editquery1.png)     ![Lekérdezések szerkesztése a menüszalagról](media/desktop-tutorial-facebook-analytics/t_fb_editquery.png)
   
2. A Power Query-szerkesztőben válassza a **Hozzászólások száma** oszlopot, majd módosítsa az adattípust **egész számra** az alábbi módszerek egyikével: 
   - Válassza az **1.2** ikont a **Hozzászólások száma** oszlopfejléc mellett, majd válassza az **Egész szám** lehetőséget a legördülő menüből.
   - Kattintson a jobb gombbal az oszlopfejlécre, majd válassza a **Típus módosítása > Egész szám** lehetőséget.
   - Válassza az **Adattípus: Tizedes tört szám** lehetőséget a Kezdőlap szalagfül **Átalakítás** csoportjában, vagy az **Átalakítás** szalagfül **Minden oszlop** csoportjában válassza az **Egész szám** lehetőséget.
   
   Az oszlopfejléc ikonja **123** értékre változik, így jelölve az Egész szám adattípust.
   
   ![Adattípus módosítása](media/desktop-tutorial-facebook-analytics/change-datatype.png)
   
3. A **Bezárás és alkalmazás** vagy egyszerűen az **Alkalmazás** elemet kiválasztva alkalmazhatja a módosításokat, miközben a Power Query-szerkesztő ablaka továbbra is nyitva marad. A módosítások betöltését követően a diagram adatfeliratai egész számokra változnak. 
   
   ![Diagram egész számokkal](media/desktop-tutorial-facebook-analytics/vis-3.png)
   
### <a name="create-a-date-slicer"></a>Dátumszeletelő létrehozása

Szeretné vizualizálni a bejegyzések hozzászólásainak számát adott időszakban. Szeletelői vizualizáció létrehozásával szűrni lehet a diagram adatait a különböző időkereteknek megfelelően. 

1. Kattintson a vászon egy üres területére, majd válassza a **Szeletelő ikont** a Megjelenítések ablaktáblán. Megjelenik egy üres szeletelői vizualizáció. 
   
   ![Szeletelő ikon kiválasztása](media/desktop-tutorial-facebook-analytics/slicer1.png)
   
2. Válassza a **created_date** mezőt a Mezők listából, vagy húzza át az új szeletelőre. A szeletelő egy dátumtartomány típusú csúszkává változik a mező Dátum adattípusa alapján.
   
   ![Dátumtartomány típusú csúszka szeletelője](media/desktop-tutorial-facebook-analytics/slicer2.png)
   
3. A csúszka fogópontjainak mozgatásával különböző dátumtartományokat választhat ki, és észreveheti, hogy a diagram adatait a rendszer ennek megfelelően szűri. A dátummezőket is használhatja a szeletelőben, és konkrét dátumokat írhat be, vagy kiválaszthatja azokat a felbukkanó naptárból.
    
   ![Adatok szeletelése](media/desktop-tutorial-facebook-analytics/slicer3.png)
   
### <a name="format-the-visualizations"></a>A vizualizációk formázása

Úgy dönt, hogy egy még inkább leíró jellegű, vonzó címet ad a diagramnak. 

1. Miután kijelölte a diagramot, válassza a **Formázás** ikont, majd válassza a lefelé mutató nyilat a **Cím** kibontásához.
2. Módosítsa a **Címszöveget** a következőre: **Hozzászólások bejegyzésenként**. 
3. Válassza a **Betűszín** melletti lefelé mutató nyilat, majd válasszon zöld színt a vizualizáció zöld sávjaihoz való illeszkedés céljából.
4. Növelje a **szövegméretet** **10-es** értékre, és módosítsa a **betűcsaládot** **Segoe (félkövér)** lehetőségre.

![Diagramcím formázása](media/desktop-tutorial-facebook-analytics/formatting1.png)

Kísérletezzen a további formázási lehetőségekkel és beállításokkal a vizualizációk megjelenésének módosításához. 

![Vizualizációk](media/desktop-tutorial-facebook-analytics/vis-1.png)

## <a name="create-more-visualizations"></a>További vizualizációk létrehozása

Amint láthatja, a jelentésekben könnyen testre szabhatók a vizualizációk, így tetszőleges módon lehet bemutatni az adatokat. Például az importált Facebook-adatok használatával próbálja meg létrehozni ezt a vonaldiagramot, amely a hozzászólások számát mutatja adott időszakban.

![Vonaldiagram](media/desktop-tutorial-facebook-analytics/moreviz.png)

A Power BI Desktop teljes körű szolgáltatást nyújt, lehetővé téve az adatok számos különféle adatforrásból való beszerzését, az elemzési igényeknek megfelelő átalakítását, valamint látványos és interaktív módon történő megjelenítését. Miután elkészült a jelentés, [feltöltheti azt a Power BI szolgáltatásba](desktop-upload-desktop-files.md), és létrehozhat azon alapuló irányítópultokat, amelyeket más Power BI-felhasználókkal is megoszthat.

## <a name="next-steps"></a>Következő lépések
* [Olvassa el a többi Power BI Desktop-oktatóanyagot](http://go.microsoft.com/fwlink/?LinkID=521937)
* [Tekintse meg a Power BI Desktop videóit](http://go.microsoft.com/fwlink/?LinkID=519322)
* [Látogasson el a Power BI fórumára](http://go.microsoft.com/fwlink/?LinkID=519326)
* [Látogasson el a Power BI blogra](http://go.microsoft.com/fwlink/?LinkID=519327)

