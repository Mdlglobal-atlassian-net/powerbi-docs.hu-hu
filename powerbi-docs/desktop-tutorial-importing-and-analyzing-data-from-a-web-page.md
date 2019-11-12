---
title: 'Oktatóanyag: Weboldalról származó adatok importálása és elemzése'
description: 'Oktatóanyag: Weboldalakról származó adatok importálása és elemzése a Power BI Desktop használatával'
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: e4a805db851e63a725a866065a774ef8ecc23c24
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73879595"
---
# <a name="tutorial-analyze-web-page-data-using-power-bi-desktop"></a>Oktatóanyag: Weboldalakról származó adatok elemzése a Power BI Desktop használatával

Igazi futballrajongóként szeretne jelentést készíteni az UEFA labdarúgó-Európa-bajnokság (Eb) eddigi győzteseiről. A Power BI Desktop használatával az adatokat egy weboldalról egy jelentésbe importálhatja, majd vizualizációs elemek létrehozásával megjelenítheti azokat. Ebben az oktatóanyagban bemutatjuk, hogyan végezheti el a következő feladatokat a Power BI Desktop alkalmazással:

- Kapcsolódás egy webes adatforráshoz és navigálás az elérhető táblák között;
- Adatok formázása és átalakítása a **Power Query-szerkesztőben**;
- Lekérdezés elnevezése és importálása egy Power BI Desktop-jelentésbe; valamint 
- Térképes és tortadiagramos vizualizáció létrehozása és testreszabása.

## <a name="connect-to-a-web-data-source"></a>Kapcsolódás egy webes adatforráshoz

Az Eb-győztesekre vonatkozó adatokat a labdarúgó-Európa-bajnokság Wikipédia-oldalán található Eredmények nevű táblából töltheti le az alábbi linken: https://en.wikipedia.org/wiki/UEFA_European_Football_Championship. 

![Eredmények tábla a Wikipédia-oldalon](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage1.png)

Vegye figyelembe, hogy a csatlakozó a webes kapcsolatok létrehozásához csak alapszintű hitelesítést használ. Előfordulhat, hogy az egyéb hitelesítést igénylő webhelyek nem fognak megfelelően működni a Web-összekötő használatakor.

Az adatok importálásához a következőket kell tennie:

1. A Power BI Desktop alkalmazásban a **Kezdőlap** szalagfülön kattintson a **Lekérdezés** melletti listanyílra, majd válassza ki a **Web** lehetőséget.
   
   ![Adatok lekérése a szalagfülön keresztül](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web3.png) 
   
   >[!NOTE]
   >A **Lekérdezés** elemet kijelölheti közvetlenül, vagy kiválaszthatja a Power BI **Első lépések** párbeszédéből is, majd a **Lekérdezés** párbeszédpanelen kattintson a **Web** elemre az **Összes** vagy **Egyéb** szakaszon belül, végül pedig kattintson a **Kapcsolódás** elemre.
   
2. A **Webes tartalomból** párbeszédpanelen illessze be az URL-címet `https://en.wikipedia.org/wiki/UEFA_European_Football_Championship` az **URL** szövegmezőbe, majd kattintson az **OK** gombra.
   
    ![Adatok lekérése az párbeszédpanelen](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web2.png)
   
   A Wikipédia-oldalhoz történő kapcsolódást követően a Power BI **Kezelő** párbeszédpanelje az oldalon elérhető táblák listáját tartalmazza. Az adatok előnézetének megtekintéséhez válassza ki bármelyik tábla nevét. Az **Eredmények[szerkesztés]** tábla tartalmazza azokat az adatokat, amelyekre szüksége van, azonban nem olyan formában, amelyben használni szeretné őket. Az adatokat újra kell formáznia és meg kell tisztítania, mielőtt betöltené őket a jelentésbe. 
   
   ![Kezelő párbeszédpanel](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/tutorialimanaly_navigator.png)
   
   >[!NOTE]
   >Az **Előnézet** ablaktábla a legutoljára kiválasztott táblát mutatja, de az összes kiválasztott tábla betöltődik a **Power Query-szerkesztőbe**, amikor rákattint a **Szerkesztés** vagy **Betöltés** lehetőségre. 
   
3. Válassza ki az **Eredmények [szerkesztés]** táblát a **Kezelő** listájából, majd kattintson a **Szerkesztése** lehetőségre. 
   
   A **Power Query-szerkesztőben** megnyílik a tábla előnézeti képe, amelyben átalakításokat hajthat végre az adattisztításhoz. 
   
   ![Power Query-szerkesztő](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage3.png)
   
## <a name="shape-data-in-power-query-editor"></a>Adatok formázása a Power Query-szerkesztőben

Ha kizárólag az évszámokat és a győztes országokat jeleníti meg, azzal megkönnyítheti az adatok beolvasását. Az adatokat a **Power Query-szerkesztő** használatával tudja formázni és megtisztítani.

Először távolítson el minden oszlopot a táblából az **Év** és a **Döntő győztesei** oszlopok kivételével.

1. A **Power Query-szerkesztő** által létrehozott táblában válassza ki az **Év** és a **Döntő győztesei** oszlopokat (több elem kiválasztásához tartsa lenyomva a **CTRL** billentyűt).
   
2. Kattintson a jobb gombbal, és válassza ki a **További oszlopok eltávolítása** lehetőséget a legördülő menüből, vagy válassza az **Oszlopok eltávolítása** > **További oszlopok eltávolítása** lehetőséget az  **Oszlopok kezelése** csoportban a **Kezdőlap** szalagfülön, hogy minden további oszlopot eltávolítson a táblából. 
   
   ![További oszlopok eltávolítása a legördülő menün keresztül](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web6.png) vagy ![További oszlopok eltávolítása a szalagfülön keresztül](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage4.png)

Ezután távolítsa el a felesleges **Részletek** szót az **Év** oszlop celláiból.

1. Jelölje ki az **Év** oszlopot.
   
2. Kattintson a jobb gombbal, és válassza ki az **Értékek lecserélése** lehetőséget a legördülő menüből, vagy válassza az **Értékek lecserélése** lehetőséget az **Átalakítás** csoportban a **Kezdőlap** szalagfülön (amely a **Bármely oszlop** csoportban is megtalálható az **Átalakítás** fülön). 
   
   ![Értékek lecserélése a legördülő menün keresztül](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web7.png) vagy ![Értékek lecserélése a szalagfülön keresztül](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web8a.png)
   
3. Az **Értékek lecserélése** párbeszédpanelen írja be a **Részletek** szöveget a **Keresendő érték** szövegmezőbe, hagyja üresen a **Csere a következőre** szövegmezőt, majd kattintson az **OK** gombra, törölve ezáltal a „Részletek” szót az **Év** oszlopban található bejegyezésekből.
   
   ![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage6.png)

Néhány **Év** cella csak az „Év” szót tartalmazza az évszámok helyett. Az **Év** oszlop értékeire tud úgy szűrni, hogy csak azok a sorok jelenjenek meg, amelyek nem tartalmazzák az „Év” szót. 

1. Kattintson a szűrő listanyílra az **Év** oszlopban.
   
2. Görgessen le a legördülő menüben, és törölje a jelölést az **Év** lehetőség melletti jelölőnégyzetből, majd kattintson az **OK**, gombra, eltávolítva ezáltal azokat a sorokat, amelyek kizárólag az „Év” szót tartalmazzál az **Év** oszlopban. 

   ![Adatok szűrése](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage7.png)

Most, hogy sikerült megtisztítania az **Év** oszlop adatait, rátérhet a **Döntő győztesei** oszlopra. Mivel jelenleg csakis a döntő győzteseinek adatait látja, átnevezheti az oszlopot „**Ország**”-ra. Az oszlopot a következőképpen nevezheti át:

1. Kattintson duplán vagy koppintson és tartsa lenyomva a **Döntő győztesei** oszlop fejlécét, vagy 
   - Kattintson a jobb gombbal a **Döntő győztesei** oszlop fejlécére, és válassza ki az **Átnevezés** lehetőséget a legördülő menüből, vagy 
   - Válassza ki a **Döntő győztesei** oszlopot, majd kattintson az **Átnevezés** lehetőségre a **Bármely oszlop** csoportban a menüszalag **Átalakítás** fülén. 
   
   ![Átnevezés a legördülő menün keresztül](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage7a.png) vagy ![Átnevezés a menüszalagon keresztül](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web8.png)
   
2. Írja be az **Ország** szót a fejlécbe, majd nyomja le az **ENTER** billentyűt az oszlop átnevezéséhez.

Ezenkívül az olyan sorokat is érdemes kiszűrnie, mint a „2020”-as értékkel rendelkező sor, amelyek az **Ország** oszlopban null értéket tartalmaznak. Ehhez használhatja a szűrő menüt, ahogyan azt az **Év** oszlop értékeivel is tette, vagy ugyanezt megteheti a következő módon:

1. A **2020**-as értékkel rendelkező sorban kattintson a jobb gombbal az **Ország** oszlop cellájára, amely *null* értéket tartalmaz. 
2. Válassza ki a **Szövegszűrők** > **Nem egyenlő** lehetőséget a helyi menüből, hogy eltávolítson minden olyan sort, amelyek tartalmazzák ennek a cellának az értékét.
   
   ![Szövegszűrő](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web11.png)
   
## <a name="import-the-query-into-report-view"></a>A lekérdezés importálása Jelentés nézetbe

Most, hogy az adatokat az igényeinek megfelelően megformázta, nevezze el a lekérdezését (például „Európa-kupa győztesei”) és importálja azt a jelentésébe.

1. A **Lekérdezési beállítások** ablaktábla **Név** szövegmezőjébe írja be az **Európa-kupa győztesei** szöveget, majd nyomja le az **ENTER** billentyűt.
   
   ![Lekérdezés elnevezése](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage8.png)

2. Válassza ki a **Bezárás és alkalmazás** > **Bezárás és alkalmazás** lehetőséget a menüszalag **Kezdőlap** fülén.
   
   ![Bezárás és alkalmazás](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage9.png)
   
Miután a lekérdezés betöltődött, a Power BI Desktop **Jelentés nézet** oldalán, a **Mezők** ablaktáblán láthatja azt. 
   
   ![Mezők ablaktábla](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage11.png)
>[!TIP]
>Mindig visszatérhet a **Power Query-szerkesztőbe**, ha szerkeszteni vagy finomítani szeretné lekérdezését, amit a következőképpen tehet meg:
>- Válassza a **További beállítások** opciót jelző három pont ( **...** ) lehetőséget az **Európa-kupa győztesei** mező mellett a **Mezők** ablaktáblán, majd válassza ki a **Lekérdezés szerkesztése** lehetőséget a legördülő menüből, vagy
>- Jelentés nézetben válassza ki a **Lekérdezések szerkesztése** > **Lekérdezés szerkesztése** lehetőséget a **Külső adatok** csoportban a **Kezdőlap** szalagfülön. 

## <a name="create-a-visualization"></a>Vizualizáció létrehozása

Vizualizáció létrehozása az adatok alapján: 

1. Válassza ki az **Ország** mezőt a **Mezők** ablaktáblán, vagy húzza azt a jelentésvászonra. A Power BI Desktop felismeri, hogy az adatok országnevek, és automatikusan létrehoz egy **Térkép** vizualizációt. 
   
   ![Térkép vizualizáció](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web14.png)
   
2. Húzza a fogópontokat a képernyő sarkai felé, hogy felnagyítsa a térképet és lássa az összes győztes ország nevét.  

   ![Térkép nagyítása](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage14.png)
   
3. A térkép azonos adatpontokat mutat minden olyan ország esetén, amelyek valaha Európa-bajnokságot nyertek. Ha szeretné, hogy az egyes adatpontok méreteiből kiderüljön, hogy egy adott ország hányszor győzött, húzza az **Év** mezőt az **Ide húzhatja az adatmezőket** feliratra a **Méret** lehetőség alatt, a **Vizualizációs elemek** ablaktábla alsó részén. A mező automatikusan **Évek száma** mezőre változik, a térképen pedig azok az országok, amelyek több bajnokságot is megnyertek, nagyobb adatponttal rendelkeznek majd. 
   
   ![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage15.png)
   

## <a name="customize-the-visualization"></a>Vizualizáció testreszabása

Ahogyan láthatta, rendkívül egyszerűen tud létrehozni vizualizációs elemeket adatai alapján. Vizualizációs elemeit ugyanilyen könnyedén testre is szabhatja, hogy az adatok úgy jelenjenek meg, ahogy az a leginkább megfelel az Ön számára. 

### <a name="format-the-map"></a>A térkép formázása
Ha szeretné megváltoztatni egy vizualizációs elem megjelenését, válassza ki az elemet, majd kattintson a **Formázás** (festőhenger) ikonra a **Vizualizációs elemek** ablaktáblán. A „Németország” adatpont(ok) például megtévesztőek lehetnek a térkép vizualizáción, ugyanis Nyugat-Németország két bajnokságot is megnyert, Németország viszont csak egyet, a térkép azonban egymásra helyezi a két pontot ahelyett, hogy különválasztaná vagy egyesítené azokat. Ha szeretné felhívni erre a figyelmet, adjon meg különböző színeket ehhez a két ponthoz. A térképnek még inkább leíró jellegű, vonzó címet is adhat. 

1. A vizualizáció kijelölése után kattintson a **Formázás** ikonra, és válassza ki az **Adatszínek** lehetőséget a lehetséges adatszíneket tartalmazó mező kibontásához. 
   
   ![Adatszínek formázása](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web15.png)
   
2. Az **Összes megjelenítése** lehetőségnél válassza a **Be** opciót, majd kattintson a legördülő menüre **Nyugat-Németország** mellett és válassza ki az egyik sárga színt. 
   
   ![Szín módosítása](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web16.png)
   
3. Kattintson a **Cím** lehetőségre a címbeállítások kibontásához, és a **Címszöveg** mezőbe az aktuális cím helyett írja be az **Európa-kupa győztesei** szöveget. 
4. A **Betűszínt** állítsa át pirosra, a **Szövegméretet** állítsa **12**-esre, a **Betűcsaládot** pedig módosítsa a **Segoe (Bold)** lehetőségre. 
   
   ![Adatszínek formázása](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web17.png)
   

Az Ön térkép vizualizációja jelenleg így néz ki:

![Formázott térkép vizualizáció](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web18.png)
   
### <a name="change-the-visualization-type"></a>Vizualizáció típusának módosítása
Egy vizualizáció típusának módosításához válassza ki az adott vizualizációt, majd kattintson egy másik ikonra a **Vizualizáció** ablaktábla tetején. Térkép vizualizációja például nem tartalmazza a Szovjetunióra és Csehszlovákiára vonatkozó adatokat, ezek az országok ugyanis már nem szerepelnek a világtérképen. Más típusú vizualizációk, például egy fatérkép vagy egy tortadiagram pontosabb képet adhatnak, mivel ezek minden értéket megjelenítenek. 

Ha a térképet tortadiagramra szeretné cserélni, jelölje ki a térképet, majd kattintson a **Tortadiagram** ikonra a **Vizualizáció** ablaktáblán. 
   
![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web19.png)

>[!TIP]
>- Az **Adatszínek** formázási lehetőséggel „Németország” és „Nyugat-Németország” esetén megadhatja ugyanazt a színt. 
>- Ha szeretné csoportosítani a tortadiagramon a legtöbb győzelmet aratott országokat, válassza a három pont ( **...** ) lehetőséget a vizualizáció jobb felső sarkában, majd válassza ki a **Rendezés az Évek száma szerint** lehetőséget a legördülő menüből. 

A Power BI Desktop teljes körű szolgáltatást nyújt, lehetővé téve az adatok számos különféle adatforrásból való beszerzését, az elemzési igényeknek megfelelő átalakítását, valamint látványos és interaktív módon történő megjelenítését. Miután elkészült a jelentés, [felöltheti azt a Power BI-ba](desktop-upload-desktop-files.md), és létrehozhat azon alapuló irányítópultokat, amelyeket más Power BI-felhasználókkal meg is oszthat.

## <a name="see-also"></a>Lásd még:
* [Olvassa el a többi Power BI Desktop-oktatóanyagot](https://go.microsoft.com/fwlink/?LinkID=521937)
* [Tekintse meg a Power BI Desktop videóit](https://go.microsoft.com/fwlink/?LinkID=519322)
* [Látogasson el a Power BI fórumára](https://go.microsoft.com/fwlink/?LinkID=519326)
* [Látogasson el a Power BI blogra](https://go.microsoft.com/fwlink/?LinkID=519327)

