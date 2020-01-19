---
title: 'Oktatóanyag: Számított oszlopok létrehozása a Power BI Desktopban'
description: 'Oktatóanyag: Számított oszlopok létrehozása a Power BI Desktopban'
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 11/26/2019
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: cdd4f4f5058b57cbf59a3a0b35286243bd8c8f37
ms.sourcegitcommit: b68a47b1854588a319a5a2d5d6a79bba2da3a4e6
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/08/2020
ms.locfileid: "75731719"
---
# <a name="tutorial-create-calculated-columns-in-power-bi-desktop"></a>Oktatóanyag: Számított oszlopok létrehozása a Power BI Desktopban

Időnként az elemzett adatok nem tartalmazzák a kívánt eredményhez szükséges mezőt. Ekkor nyernek jelentőséget a *számított oszlopok*. A számított oszlopok az oszlopok értékeinek meghatározásához Data Analysis Expressions- (DAX-) képleteket használnak, amelyek bármik lehetnek, a több különböző oszlopból származó szöveges értékek összeillesztésétől a numerikus értékek más értékekből történő kiszámításáig. Tegyük fel például, hogy az adatokban vannak **Város** és **Állam** oszlopok, de Ön egyetlen **Hely** mezőt szeretne, amelyben mindkettő szerepel, mint például „Miami, FL”. Pontosan erre szolgálnak a számított oszlopok.

A számított oszlopok hasonlóak a [mértékekhez](desktop-tutorial-create-measures.md), mert mindkettő DAX-képleteken alapul, de a használatuk módja különböző. A mértékek gyakran használhatók a vizualizációk **Értékek** területén, a más mezőkön alapuló eredmények kiszámításához. A számított oszlopok új **Mezők** formájában használhatók a vizualizációk sor, tengely, jelmagyarázat és csoport területein.

Ez az oktatóanyag bemutatja néhány számított oszlop létrehozását és jelentésvizualizációkban való felhasználását a Power BI Desktopban.

## <a name="prerequisites"></a>Előfeltételek

- Az oktatóanyag olyan Power BI-felhasználóknak szól, akik már jól ismerik a speciálisabb modellek létrehozásának eljárásait a szolgáltatásban. Ehhez már tudnia kell, hogyan használhatja az Adatok lekérése és a Power Query-szerkesztő funkciót adatok lekérésére, több kapcsolódó táblával való munkára és mezőknek a jelentésvászonhoz történő hozzáadására. Ha még csak most ismerkedik a Power BI Desktoppal, mindenképp tekintse át a [Power BI Desktop használatának első lépéseit](desktop-getting-started.md) ismertető témakört.
  
- Az oktatóprogram a [Power BI Desktop Contoso értékesítési mintát](https://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20Sample%20for%20Power%20BI%20Desktop.zip) használja, ami azonos a [Saját mértékek létrehozása a Power BI Desktopban](desktop-tutorial-create-measures.md) című oktatóanyagban használt mintával. Ezek a fiktív Contoso, Inc. vállalattól származó értékesítési adatok egy adatbázisból lettek importálva, így Ön nem tud majd az adatforráshoz kapcsolódni, illetve nem tudja azt megtekinteni a Power Query-szerkesztőben. Töltse le és bontsa ki a fájlt saját számítógépére, majd nyissa meg a fájlt a Power BI Desktopban.

## <a name="create-a-calculated-column-with-values-from-related-tables"></a>Hozzon létre számított oszlopot, kapcsolódó táblákból származó értékekkel

Értékesítési jelentésében Ön termékkategóriákat és alkategóriákat egyetlen értékként kíván megjeleníteni, mint például „Mobiltelefonok – Kellékek”, „Mobiltelefonok – Okostelefonok és PDA-k” és így tovább. A **Mezők** listában nincs ilyen adatokat kínáló mező, van viszont egy **ProductCategory** (termékkategória) és egy **ProductSubcategory** (termék-alkategória) mező, mindegyik a saját táblájában. Ön létrehozhat egy számított oszlopot, amely egyesíti e két oszlop értékeit. A DAX-képletek kihasználhatják a már meglévő modell minden képességét, beleértve a már meglévő táblák közötti kapcsolatokat.

 ![Oszlopok a Mező listában](media/desktop-tutorial-create-calculated-columns/create1.png)

1. Ha új oszlopot szeretne létrehozni a **ProductSubcategory** táblában, kattintson a jobb gombbal, vagy válassza a három pontot **...** a **ProductSubcategory** elem mellett **Mezők** panelen, majd válassza az **Új oszlop** lehetőséget a menüből.

   ![Új oszlop](media/desktop-tutorial-create-calculated-columns/create2.png)

   Az **Új oszlop** lehetőség kiválasztásakor, jelentésvászon tetején megjelenik a **szerkesztőléc**, amelyen elnevezheti az oszlopot, és beírhatja a DAX-képletet.

   ![Szerkesztőléc](media/desktop-tutorial-create-calculated-columns/create3.png)

2. Alapértelmezés szerint az új számított oszlop neve **Oszlop** lesz. Ha nem nevezi át, akkor a további új oszlopok neve **Oszlop 2**, **Oszlop 3** lesz, és így tovább. Az oszlopnak célszerű informatívabb nevet adni, ezért mivel az **Oszlop** neve már ki van jelölve a szerkesztőlécen, a **ProductFullCategory** név beírásával nevezze át, majd írjon be egy egyenlőségjelet ( **=** ).

3. Az a cél, hogy az új oszlopban lévő értékek a **ProductCategory** mezőben található névvel kezdődjenek. Mivel ez az oszlop egy másik, de kapcsolódó táblában található, a lekéréséhez a [RELATED](https://msdn.microsoft.com/library/ee634202.aspx) függvény használható.

   Az egyenlőségjel után írja be: **r**. Egy legördülő javaslati lista megjeleníti az összes R betűvel kezdődő DAX-függvényt. Az egyes függvényeket kijelölve megjelenik a függvény hatásának leírása. A függvénynév beírása közben a javaslatok listája a keresett függvényhez közeli lehetőségekre szűkül. Jelölje ki a **RELATED** függvényt, majd nyomja meg az **Enter** billentyűt.

   ![Válassza a RELATED függvényt](media/desktop-tutorial-create-calculated-columns/create4.png)

   Egy nyitó zárójel jelenik meg a RELATED függvénynek átadható, kapcsolódó oszlopok javaslati listájával, és a megadandó paraméterek leírásaival és részleteivel.

   ![Válassza a ProductCategory elemet](media/desktop-tutorial-create-calculated-columns/create5.png)

4. A **ProductCategory** táblában lévő **ProductCategory** oszlopra van szükség. Válassza a **ProductCategory[ProductCategory]** elemet, nyomja meg az **Enter** billentyűt, majd írjon be egy záró zárójelet.

    > [!TIP]
    > A szintaktikai hibákat leggyakrabban a hiányzó vagy máshová írt záró zárójelek okozzák, bár egyes esetekben a Power BI Desktop automatikusan hozzáadja.

5. Az új értékekben kötőjelekkel és szóközökkel kellene elválasztani a **ProductCategories** és a **ProductSubcategories** elemeket, ezért az első kifejezés záró zárójele után írja be a következőket: szóköz, „és”-jel ( **&** ), idézőjel ( **"** ), szóköz, kötőjel ( **-** ), szóköz, idézőjel, „és”-jel. A képletnek most így kell kinéznie:

    `ProductFullCategory = RELATED(ProductCategory[ProductCategory]) & " - " &`

    > [!TIP]
    > Ha több helyre van szüksége, válassza a lefelé mutató sávnyilat a szerkesztőléc jobb oldalán a képletszerkesztő kibontásához. A szerkesztőben nyomja le az **Alt + Enter** billentyűkombinációt, hogy lejjebb menjen egy sorral, és a **Tab** billentyűt az elmozgatáshoz.

6. Írjon be egy nyitó szögletes zárójelet ( **[** ), majd válassza a **[ProductSubcategory]** oszlopot a képlet befejezéséhez. 

    ![Válassza a ProductSubcategory elemet](media/desktop-tutorial-create-calculated-columns/create6.png)

    A második kifejezésben nem kell újabb RELATED függvényt használnia a **ProductSubcategory** tábla hívásához, mert a számított oszlopot ebben a táblában hozza létre. A **[ProductSubcategory]** oszlopot a táblanév előtaggal (teljes) vagy anélkül is (nem teljes) beírhatja.

7. A képlet befejezéséhez nyomja le az **Enter** billentyűt, vagy válassza a szerkesztőlécen lévő pipa jelet. Megtörténik a képlet ellenőrzése, majd a **ProductFullCategory** oszlop neve megjelenik a **ProductSubcategory** táblában a **Mezők** panelen.

   ![A ProductFullCategory oszlop elkészült](media/desktop-tutorial-create-calculated-columns/create7.png)

    >[!NOTE]
    >A Power BI Desktopban a számított oszlopok különleges ikont kapnak a **Mezők** panelen, jelezve, hogy képleteket tartalmaznak. A Power BI szolgáltatásban (az Ön Power BI-webhelyén) nem lehet módosítani a képleteket, ezért a számított oszlopoknak nincs ikonja.

## <a name="use-your-new-column-in-a-report"></a>Az új oszlop felhasználható a jelentésekben

Mostantól az új **ProductFullCategory** oszlop használatával a **SalesAmount** **ProductFullCategory** szerint tekinthető meg.

1. Az összes **ProductFullCategory** nevet megjelenítő tábla létrehozásához válassza ki a **ProductFullCategory** oszlopot a **ProductSubcategory** táblából, vagy húzza onnan a jelentésvászonra.

   ![ProductFullCategory tábla](media/desktop-tutorial-create-calculated-columns/vis1.png)

2. Az egyes **ProductFullCategory** elemekhez tartozó **SalesAmount** értékesítési összeg megjelenítéséhez válassza ki vagy húzza a táblába a **SalesAmount** mezőt a **Sales** táblából.

   ![SalesAmount (Értékesítés összege) a ProductFullCategory elemek alapján](media/desktop-tutorial-create-calculated-columns/vis2.png)

## <a name="create-a-calculated-column-that-uses-an-if-function"></a>Hozzon létre egy számított oszlopot, amely IF függvényt alkalmaz

A Contoso értékesítési minta aktív és inaktív üzletekre vonatkozó értékesítési adatokat is tartalmaz. Egy **Active StoreName** (aktív üzlet név) mező létrehozásával biztosíthatja, hogy a jelentésében az aktív üzletek értékesítései egyértelműen elkülönüljenek az inaktív üzletek értékesítéseitől. Az új **Active StoreName** számított oszlopban mindegyik aktív üzlet megjelenik az üzlet teljes nevével, míg az inaktív üzletek értékesítéseit egyetlen „**Inaktív**” sorelem alatt csoportosítja a rendszer.

Szerencsére a **Stores** (Üzletek) táblának van egy **Status** (Állapot) nevű oszlopa, amelyben az aktív üzleteket „Be”, az inaktív üzleteket „Ki” érték jelzi, amelyek használatával értékek hozhatók létre az új **Active StoreName** oszlop számára. A DAX-képlet a logikai [IF](https://msdn.microsoft.com/library/ee634824.aspx) függvényt fogja használni az egyes üzletek **Status** értékének ellenőrzése, és az eredménytől függően fog egy bizonyos értéket kiadni. Ha egy üzlet **Status** értéke „On” („Be”), akkor a képlet kiadja az üzlet nevét. Ha az észlelt érték „Off” („Ki”), akkor a képlet „Inactive”(„Inaktív”) **Active StoreName** értéket fog hozzárendelni.

1. A **Stores** táblában hozzon létre egy új számított oszlopot, és a szerkesztőlécen adja neki az **Active StoreName** nevet.

2. Az **=** jel után kezdje beírni az **IF** szót. A javaslati listában megjelennek a választható lehetőségek. Válassza ki az **IF** függvényt.

    ![Válassza ki az IF függvényt](media/desktop-tutorial-create-calculated-columns/if1.png)

3. Az **IF** függvény első argumentuma annak logikai ellenőrzése, hogy az adott üzlet **Status** értéke „On”-e. Írjon be egy nyitó szögletes zárójelet **[** , am oszlopokat listáz a **Stores** táblából, majd válassza a **[Status]** elemet.

    ![Válassza a Status elemet](media/desktop-tutorial-create-calculated-columns/if2.png)

4. Közvetlenül a **[Status]** után írja be a következőt: **= "On"** , majd írjon be egy vesszőt ( **,** ) az argumentum befejezéséhez. Az eszköztipp azt javasolja, hogy most adja meg a kiadandó értéket arra az esetre, ha az eredmény TRUE (igaz).

    ![TRUE érték hozzáadása](media/desktop-tutorial-create-calculated-columns/if3.png)

5. Ha az üzlet Állapot értéke „On”, akkor meg kell jeleníteni az üzlet nevét. Írjon be egy nyitó szögletes zárójelet **[** , és válassza ki a **[StoreName]** oszlopot, majd írjon be egy újabb vesszőt. Az eszköztipp most azt jelzi, hogy adja meg a kiadandó értéket arra az esetre, ha az eredmény FALSE (hamis).

    ![HAMIS érték hozzáadása](media/desktop-tutorial-create-calculated-columns/if4.png)

6. Az értéknek Inactive-nek kell lennie, ezért a szerkesztőlécen írja be az **"Inactive"** kifejezést, majd fejezze be a képletet az **Enter** billentyű lenyomásával vagy a szerkesztőlécen a pipa jel választásával. Megtörténik a képlet ellenőrzése, majd az új oszlop neve megjelenik a **Stores** táblában a **Mezők** panelen.

    ![Active StoreName oszlop](media/desktop-tutorial-create-calculated-columns/if5.png)

7. Az új **Active StoreName** oszlop bármely más mezőhöz hasonlóan használható a vizualizációkban. A **SalesAmounts** értékek **Active StoreName** szerint történő megjelenítéséhez jelölje ki az **Active StoreName** mezőt, vagy húzza azt a vászonra, majd jelölje ki a **SalesAmount** mezőt, vagy húzza azt a táblába. Ebben a táblában az aktív üzletek önállóan, név szerint jelennek meg, de az inaktív üzleteket a rendszer a tábla végére, **Inactive** címmel csoportosítja.

    ![A SalesAmount értékeket Active StoreName szerint megjelenítő tábla](media/desktop-tutorial-create-calculated-columns/if6.png)

## <a name="what-youve-learned"></a>Az oktatóanyag összefoglalása

A számított oszlopok tovább gazdagíthatják az adatokat, és megkönnyíthetik azok elemzését. Bemutattuk, hogyan történik a számított oszlopok létrehozása a **Mezők** panelen és a szerkesztőlécen, hogyan használhatók a javaslati listák és az eszköztippek a képletek összeállításához, hogyan kell megfelelő argumentumokkal meghívni például a RELATED és az IF DAX-függvényeket, és hogyan lehet felhasználni a számított oszlopokat a jelentésvizualizációkban.

## <a name="next-steps"></a>Következő lépések

Ha szeretné a DAX-képleteket részletesebben megismerni, és összetettebb képletekkel szeretne létrehozni számított oszlopokat, olvassa el a cikket, amely [a DAX alapszintű használatát ismerteti a Power BI Desktopban](desktop-quickstart-learn-dax-basics.md). Ez a cikk a DAX alapvető fogalmaira, a szintaxisra, a függvényekre és a környezet alaposabb megértésére összpontosít.

Mindenképp vegye fel a [Data Analysis Expressions (DAX) referenciát](https://msdn.microsoft.com/library/gg413422.aspx) a kedvencei közé. Ebben találja részletesen leírva a DAX-szintaxist, az operátorokat, valamint a több mint 200 DAX-függvényt.
