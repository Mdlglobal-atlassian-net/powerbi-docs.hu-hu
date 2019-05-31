---
title: 'Oktatóanyag: Excelből és OData-csatornáról származó adatok összevonása a Power BI Desktopban'
description: 'Oktatóanyag: Excelből és OData-csatornáról származó adatok összevonása'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 05/21/2018
ms.author: v-thepet
LocalizationGroup: Learn more
ms.openlocfilehash: 94e40681d065591db008f8a9062d851e0bd83f61
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61368560"
---
# <a name="tutorial-combine-sales-data-from-excel-and-an-odata-feed"></a>Oktatóanyag: Excelből és OData-csatornáról származó értékesítési adatok összevonása

Igen gyakori, hogy az adatok több különböző adatforrásban találhatók, például a termékinformációk egy adatbázisban, az értékesítési adatok egy másikban. A **Power BI Desktoppal** összevonhatja a különböző forrásokból származó adatokat, így érdekes, meggyőző elemzéseket és vizualizációkat hozhat létre. 

Ebben az oktatóanyagban két adatforrás esetén sajátíthatja el a belőlük származó adatok összevonását: az egyik a termékinformációkat tartalmazó Excel-munkafüzet, a másik a megrendeléseket tartalmazó OData-csatorna. Az adatkészletek importálása, majd az átalakítás és összesítés lépései után mindkét forrás adatait felhasználhatja egy interaktív vizualizációkkal kiegészített eladáselemzési jelentéshez. Ezek a technikák SQL Server-lekérdezésekhez, CSV-fájlokhoz és a Power BI Desktopban használt egyéb adatforrásokhoz is használhatók.

>[!NOTE]
>A Power BI Desktopban gyakori, hogy egy adott feladatot többféleképpen is el lehet végezni. Például a menüszalag elemeit ki lehet jelölni jobb gombbal történő kattintással, vagy az egyik oszlopon vagy cellán található **További lehetőségek** menü választásával is. Az alábbi lépések számos választható módszert leírnak. 

## <a name="import-the-product-data-from-excel"></a>Termékadatok importálása az Excelből

Először is importálja az Excel Products.xlsx munkafüzetben lévő termékadatokat a Power BI Desktopba.

1. [Töltse le a Products.xlsx Excel-munkafüzetet](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx), és mentse **Products.xlsx** néven.
   
2. Kattintson a Power BI Desktop **Kezdőlap** szalagfülén az **Adatok lekérése** elem mellett lenyitó nyílra, majd a **Leggyakoribb** legördülő listán kattintson az **Excel** elemre. 
   
   ![Adatok lekérése](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_1.png)
   
   >[!NOTE]
   >Az **Adatok lekérése** elemet kijelölheti közvetlenül, vagy kiválaszthatja a Power BI **Első lépések** párbeszédéből is, majd az **Adatok lekérése** párbeszédpanelben kattintson az **Excel** vagy a **Fájl** > **Excel** elemre, és végül a **Kapcsolódás** elemre.
   
3. A **Megnyitás** párbeszédpanelben keresse meg és jelölje ki a **Products.xlsx** fájlt, majd kattintson a **Megnyitás** elemre.
   
4. A **Kezelő** ablaktáblán válassza a **Termékek** táblát, majd a **Szerkesztés** lehetőséget.
   
   ![Az Excel kezelőpanelje](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_2.png)
   
A **Power Query-szerkesztőben** megnyílik a tábla előnézeti képe, amelyben átalakításokat hajthat végre az adattisztításhoz. 
   
![Power Query-szerkesztő](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_3.png)
   
>[!NOTE]
>A **Power Query-szerkesztőt** a Power BI Desktop **Kezdőlap** szalagfül **Lekérdezések szerkesztése** > **Lekérdezések szerkesztése** elemére kattintva nyithatja meg, vagy úgy, ha a jobb gombbal kijelöli a **Jelentés nézet** mellett lévő **További lehetőségeket**, és ott rákattint a **Lekérdezések szerkesztése** elemre.

## <a name="clean-up-the-products-columns"></a>A termékeket tartalmazó oszlopok tisztítása

Mivel az összevont jelentés a munkafüzetből csak a **ProductID** (Termékazonosító), a **ProductName** (Terméknév), a **QuantityPerUnit** (Mennyiség egységek szerint) és a **UnitsInStock** (Egységek száma a készletben) oszlopokat fogja használni, a többi oszlopot eltávolíthatja. 

1. A **Power Query-szerkesztőben** jelölje ki a **ProductID**, a **ProductName**, a **QuantityPerUnit**, és a **UnitsInStock** oszlopokat (a **Ctrl**+**Kattintás** kombinációval több oszlopot is kiválaszthat, a **Shift**+**Kattintás** kombinációval egymás melletti oszlopokat jelölhet ki).
   
2. Kattintson a jobb gombbal a kijelölt fejlécek bármelyikére, majd a legördülő listában kattintson a **További oszlopok eltávolítása** elemre, így a táblázat összes oszlopát eltávolíthatja a kijelölteken kívül. 
   Azt is megteheti, hogy a **Kezdőlap** szalagfül **Oszlopok kezelése** csoportjában kattint rá az **Oszlopok eltávolítása** > **További oszlopok eltávolítása** elemre. 
   
   ![További oszlopok eltávolítása](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_removeothercolumns.png)

## <a name="import-the-order-data-from-an-odata-feed"></a>Megrendelési adatok importálása egy OData-csatornáról

A következő lépésben importálja a megrendelési adatokat a Northwind értékesítési rendszer mintaanyagából az OData-csatornán keresztül. 

1. A **Power Query-szerkesztőben** kattintson az **Új forrás** elemre, majd a **Leggyakoribbak** legördülő listából válassza ki az **OData-csatorna** lehetőséget. 
   
   ![OData beolvasása](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata.png)
   
2. Az **OData-csatorna** párbeszédpanelbe másolja be a Northwind OData-csatorna URL-címét, `http://services.odata.org/V3/Northwind/Northwind.svc/`, majd kattintson az **OK** elemre.
   
   ![OData-csatorna párbeszédpanel](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata2.png)
   
3. Az adatokat úgy töltheti be a **Power Query-szerkesztőbe**, hogy a **Kezelő** panelen a **Megrendelések** táblázatra, majd az **OK** elemre kattint.
   
   ![OData Kezelő panel](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_odatafeed.png)
   
   >[!NOTE]
   >Ha a **Kezelőben** rákattint egy táblázat nevére, de nem jelöli be a jelölőnégyzetet, megtekintheti a táblázat előnézetét.

## <a name="expand-the-order-data"></a>A megrendelési adatok kibontása

Ha több táblázatot tartalmazó adatforrásokhoz csatlakozik, mint például a relációs adatbázisok, vagy a Northwind OData-csatorna, a lekérdezések létrehozásához hivatkozásokat használhat a táblázatok között. A **Megrendelések** táblázat hivatkozásokat tartalmaz több kapcsolódó táblázathoz. A **Kibontás** művelettel a kapcsolódó **Order_Details** (Megrendelés részletei) táblázatból hozzáadhatja a **ProductID**, a **UnitPrice**, és a **Quantity** oszlopokat a (**Megrendelések**) táblázathoz. 

1. Görgessen jobbra a **Megrendelések** táblázatban, amíg el nem jut az **Order_Details** oszlopig. Vegye figyelembe, hogy itt nem adatokat, hanem más táblázatokra mutató hivatkozásokat talál.
   
   ![Order_Details oszlop](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/7.png)
   
2. Kattintson a **Kibontás** ikonra (![Kibontás ikon](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expand.png)) az **Order_Details** oszlop fejlécén. 
   
3. A **Kibontás** legördülő menüben:
   
   1. Válassza **(Az összes oszlop kijelölése)** lehetőséget az összes oszlop törléséhez.
      
   2. Jelölje ki a **ProductID**, a **UnitPrice**, és a **Quantity** oszlopokat, majd kattintson az **OK** elemre.
      
      ![Kibontás párbeszédpanel](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/8.png)

Miután kibontotta az **Order_Details** táblázatot, az **Order_Details** oszlop helyére a beágyazott táblázat három új oszlopa kerül, és minden új megrendelésnél új sorok jelennek meg a hozzáadott adatok részére. 

![Kibontott oszlopok](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/9.png)

## <a name="create-a-custom-calculated-column"></a>Egyéni számított oszlop létrehozása

A Power Query-szerkesztővel számításokat és egyéni mezőket vehet fel az adatok bővítéséhez. Hozzon létre egy egyéni oszlopot, amely az egységár és a tételmennyiség szorzatával kiszámítja egy megrendelés minden sortételének teljes árát.

1. A Power Query-szerkesztő **Oszlop hozzáadása** szalagfülén válassza ki az **Egyéni oszlop** lehetőséget.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/10.png)
   
2. Az **Egyéni oszlop** párbeszédpanelen írja be a **LineTotal** (Sorösszeg) kifejezést az **Új oszlop neve** mezőbe.

3. Az **Egyéni oszlop képlete** mezőben a **=** jel után adja meg az **[Order_Details.UnitPrice]** \* **[Order_Details.Quantity]** adatokat. (A mezőneveket a **Megjeleníthető oszlopok** görgetőgombon is kijelölheti, és a begépelés helyett kattinthat a **<< Beillesztés** elemre.) 
3. Kattintson az **OK** gombra.
   
   ![Egyéni oszlop párbeszédpanel](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/11.png)

Az új **LineTotal** (Sorösszeg) mező a **Megrendelések** táblázat utolsó oszlopaként jelenik meg.

## <a name="set-the-data-type-for-the-new-field"></a>Adattípus beállítása az új mezőhöz

Amikor a Power Query-szerkesztő csatlakozik az adatokhoz, minden mezőhöz meghatározza a legmegfelelőbb adattípust, és az adatokat ez alapján jeleníti meg. A mezőkhöz rendelt adattípusokat a fejlécekben lévő ikonok mutatják, vagy megtekinthetők a **Kezdőlap** szalagfülön, az **Átalakítás** csoport **Adattípusok** eleme alatt. 

Az új **LineTotal** (Sorösszeg) oszlop tartalmaz egy **Bármely** adattípust is, de a benne foglalt értékek pénznemek. Adattípus hozzárendeléséhez kattintson a jobb gombbal a **LineTotal** oszlop fejlécére, válassza ki a legördülő menüből az **Adattípus módosítása** lehetőséget, és kattintson a **Fixpontos decimális szám** elemre. 

![Adattípus módosítása](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/12.png)

>[!NOTE]
>Azt is megteheti, hogy kiválasztja a **LineTotal** oszlopot, rákattint a lenyíló nyílra a **Kezdőlap** szalagfül **Átalakítás** területének **Adattípusok** eleme mellett, és itt jelöli ki a **Fixpontos decimális szám** elemet.

## <a name="clean-up-the-orders-columns"></a>A megrendelések oszlop tisztítása

Annak érdekében, hogy a modell a jelentéseken belül könnyebben kezelhető legyen, egyes oszlopokat törölhet, átnevezhet és átrendezhet.

A jelentés csak az **OrderDate** (Megrendelés dátuma), **ShipCity** (Megrendelés városa), **ShipCountry** (Megrendelés országa), **Order_Details.ProductID** (Megrendelés adatai, termékazonosító), **Order_Details.UnitPrice** (Megrendelés adatai, egységár), és az **Order_Details.Quantity** (Megrendelés adatai, mennyiség) oszlopokat használja fel. Ezen oszlopok kijelölése mellett ugyanúgy használhatja a **További oszlopok eltávolítása** lehetőséget, mint korábban az Excel-adatok esetén, vagy kijelölheti a listázottakon kívül az összes oszlopot, jobb gombbal rákattinthat az egyik kijelölt oszlopra, és az **Oszlopok eltávolítása** elemre kattintva távolíthatja mindegyiket el. 

Ha eltávolítja az *Order_Details.* előtagot az oszlopnevekből, könnyebben azonosíthatók lesznek az **Order_Details.ProductID**, az **Order_Details.UnitPrice** és az **Order_Details.Quantity** oszlopok. Az oszlopokat a következőképpen nevezheti át a **ProductID**, a **UnitPrice** és a **Quantity** névre:

1. Kattintson duplán, koppintson nyomvatartással, vagy kattintson a jobb gombbal az egyes oszlopfejlécekre, és a legördülő menüből válassza az **Átnevezés** lehetőséget. 
2. Törölje az *Order_Details.* előtagot minden egyes névből, majd nyomja le az **Entert**.

Végezetül pedig húzza balra a **LineTotal** oszlopot, közvetlenül a **ShipCountry** oszlop jobb oldalára, hogy könnyebben hozzáférhető legyen.

![A tisztított táblázat](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/14.png)

## <a name="review-the-query-steps"></a>A lekérdezési lépések áttekintése

Amikor a Power Query-szerkesztőben formázta és átalakította az adatokat, a rendszer minden lépést rögzített a Power Query-szerkesztő jobb oldalán lévő **Lekérdezés beállításai** ablaktábla **Alkalmazott lépések** területén. Az Alkalmazott lépések területen visszaléphet, és áttekintheti a végrehajtott módosításokat, sőt szükség szerint szerkesztheti, törölheti és át is rendezheti őket (bár ez kockázatos lehet, mert a korábbi lépések módosítása a későbbi lépések hibájához vezethet). 

A Power Query-szerkesztő bal oldalán látható **Lekérdezések** listán válassza ki a lekérdezéseit, és tekintse meg az **Alkalmazott lépéseket** a **Lekérdezés beállításai** ablaktáblán. Az eddigi adatátalakítások után a két lekérdezés az Alkalmazott lépések területen az alábbihoz hasonlóan jelenik meg:

![Termékek lekérdezése az Alkalmazott lépésekben](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/15.png) &nbsp;&nbsp; ![Megrendelések lekérdezése az Alkalmazott lépésekben](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/17.png)

>[!TIP]
>Az Alkalmazott lépések alapjául olyan képletek szolgálnak, amelyek **Power Query-nyelven** (más néven **M**) íródtak. A Kezdőlap szalagfül **Lekérdezés** csoportjában lévő **Speciális szerkesztő** kiválasztásával megtekintheti és szerkesztheti a képleteket. 

## <a name="import-the-transformed-queries"></a>Az átalakított lekérdezések importálása

Ha elégedett az átalakított adatokkal, kattintson a **Kezdőlap** szalagfül **Bezárás** csoportjának **Bezárás és Alkalmazás** > **Bezárás és alkalmazás** elemére, és ezzel importálja az adatokat a Power BI Desktop Jelentés nézetébe. 

![Bezárás és alkalmazás](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_4.png)

Az adatok betöltése után a lekérdezések megjelennek a Power BI Desktop Jelentés nézetének **Mezőlistáján**.

![Lekérdezések a Mezőlistán](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/18.png)

## <a name="manage-the-relationship-between-the-datasets"></a>Az adatkészletek kapcsolatainak kezelése

A Power BI Desktopban nem szükséges kombinálni a lekérdezéseket ahhoz, hogy jelentéseket készíthessen belőlük. De az adatkészletek közti kapcsolatokat a közös mezők alapján felhasználhatja a jelentések kiterjesztéséhez és gazdagításához. A kapcsolatokat a Power BI Desktop automatikusan is észlelheti, de Ön is létrehozhatja őket a Power BI Desktop **Kapcsolatok kezelése** párbeszédpaneljén. További információk a kapcsolatokról a Power BI Desktopban: [Kapcsolatok létrehozása és kezelése](desktop-create-and-manage-relationships.md).

Mivel az Orders (Megrendelések) és a Products (Termékek) adatkészletek ebben az oktatóanyagban közös *ProductID* (Termékazonosító) mezőhöz tartoznak, az adott oszlop létrehoz köztük egy kapcsolatot. 

1. A Power BI Jelentés nézetben a **Kezdőlap** szalagfülön kattintson a **Kapcsolatok** terület **Kapcsolatok kezelése** elemére.
   
   ![Kapcsolatok kezelése menüszalag](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_5.png)
   
2. A **Kapcsolatok kezelése** párbeszédpanelen figyelje meg, hogy a Power BI Desktop már észlelt és felvett a listára egy aktív kapcsolatot a Termékek és a Megrendelések táblázat között. A kapcsolat megtekintéséhez kattintson a **Szerkesztés** elemre. 
   
   ![Kapcsolatok kezelése párbeszédpanel](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_6.png)
   
   Ekkor megnyílik a **Kapcsolat szerkesztése** párbeszédpanel, és láthatóvá válnak a kapcsolat részletei.  
   
   ![Kapcsolat szerkesztése párbeszédpanel](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_7.png)
   
3. A Power BI Desktop pontosan észlelte a kapcsolatot, ezért a **Mégse**, majd a **Bezárás** elemre kattintva kiléphet a párbeszédpanelből.

A lekérdezések közti kapcsolatokat úgy is megtekintheti és kezelheti, ha a Power BI Desktop ablak bal oldalán lévő **Kapcsolat** nézetre kattint. Kattintson duplán a két lekérdezést összekötő vonalon látható nyílra, és ezzel nyissa meg a **Kapcsolatok szerkesztése** párbeszédpanelt a kapcsolat megtekintéséhez vagy módosításához. 

![Kapcsolat nézet](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_8.png)

A Kapcsolatok nézetből a **Jelentés nézet** ikonra kattintva léphet vissza a Jelentés nézethez. 

![Jelentés nézet ikonja](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_9.png)

## <a name="create-visualizations-using-your-data"></a>Vizualizációk létrehozása az adatok alapján

A Power BI Desktop Jelentés nézetében különféle vizualizációkat hozhat létre az adatok elemzéséhez. Többoldalas jelentéseket is készíthet, amelyeknek akár mindegyik oldalán több vizualizáció szerepelhet. A vizualizációkat munkatársaival együtt kezelheti az adatok elemzéséhez és megértéséhez. A jelentések saját, Power BI szolgáltatásbeli oldalon történő megtekintéséhez és szerkesztéséhez lásd: [Jelentés szerkesztése](service-interact-with-a-report-in-editing-view.md).

Az értékesítési adatok vizualizálásához és elemzéséhez mindkét adatkészletet és a köztük lévő kapcsolatokat is felhasználhatja. 

Először is hozzon létre egy mindkét lekérdezés mezőit használó halmozott oszlopdiagramot, amely a megrendelt termékek mennyiségét mutatja. 

1. A jobb oldalon lévő **Mezők** tábla **Megrendelések** területén kattintson a **Mennyiség** mezőre, vagy húzza át azt a vászon egyik üres részére. Ez a lépés egy halmozott oszlopdiagramot hoz létre, amelyen az összes megrendelt termék mennyisége látható. 
   
2. Az egyes megrendelt termékek mennyiségének megtekintéséhez kattintson a **ProductName** (Terméknév) elemre a **Mezők** tábla **Termékek** területén. 
   
3. A termékek megrendelésszám szerint csökkenő rangsorolásához kattintson a vizualizáció jobb felső sarkában lévő **További lehetőségek** három pontra ( **...** ), majd kattintson a **Sort By Quantity** (Rendezés mennyiség szerint) elemre.
   
4. Több terméknév megjelenítéséhez a sarkokban lévő fogópontokkal nagyíthatja fel a diagramot. 
   
   ![Mennyiség terméknév szerint sávdiagram](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/19.png)

Most hozzon létre egy olyan grafikont, amely a megrendelések dátuma szerinti (**OrderDate**), dollárban kifejezett összegeket (**LineTotal**) tünteti fel. 

1. Kijelölés nélküli vászon mellett kattintson a **Mezők** panelen a **Megrendelések** terület **LineTotal** (Sorösszeg) elemére, vagy húzza át azt a vászon egyik üres részére. A halmozott oszlopdiagram az összes megrendelés teljes értékét mutatja dollárban. 
   
2. A grafikon kijelölése mellett kattintson az **OrderDate** (Megrendelés dátuma) elemre az **Orders** (Megrendelések) területről, vagy húzza át azt a grafikonra. A grafikon most az egyes megrendelési dátumokon mutatja a sorösszegeket. 
   
3. Több adat megtekintéséhez a sarkok kihúzásával méretezheti át a vizualizációt. 
   
   ![Grafikon: Sorösszegek a megrendelés dátuma szerint](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/20.png)
   
   >[!TIP]
   >Ha csak az Éveket (három adatpont) látja a grafikonon, gördítse le a **Vizualizációk** panelen, a **Tengely** mezőben az **OrderDate** elem mellett látható nyilat, és a **Date Hierarchy** helyett kattintson az **OrderDate** elemre. 

Végül pedig hozzon létre egy térképi megjelenítést az egyes országokból érkező rendelések ábrázolásához. 

1. Kijelölés nélküli vászon mellett kattintson a **Mezők** panelen a **Megrendelések** terület **ShipCountry** (Megrendelés országa) elemére, vagy húzza át azt a vászon egyik üres részére. A Power BI Desktop észleli, hogy az adatok országnevek, ezért automatikusan létrehoz egy térképi megjelenítést, amelyen adatpont jelöl minden országot, ahonnan megrendelés érkezett. 
   
2. Ahhoz, hogy az adatpontok az országokhoz tartozó megrendelések nagyságát is érzékeltessék, húzza át a **LineTotal** mezőt a térképre (vagy húzza át a **Vizualizációk** ablaktábla alsó részén lévő **Méret** szakasz **Húzza ide az adatmezőket** területére). A térképen lévő körök területe most az egyes országokból érkező megrendelések dollárban kifejezett összegét tükrözi. 
   
   ![Térképi megjelenítés: Sorösszegek a megrendelés országa alapján](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/21.png)

## <a name="interact-with-your-report-visuals-to-analyze-further"></a>A jelentés vizualizációinak kezelése az adatok részletesebb elemzéséhez

A Power BI Desktopban a vizualizációk egymás közötti keresztkiemeléseinek és szűréseinek kezelésével további trendeket is kimutathat. További információkért lásd: [Szűrés és kiemelés a jelentésekben](power-bi-reports-filters-and-highlighting.md). 

Mivel a lekérdezések kapcsolatban állnak egymással, az egyik vizualizáció kezelése az oldal összes többi vizualizációját is befolyásolja. 

Kattintson a térképi megjelenítésen a **Kanadát** jelölő körre. Figyelje meg, hogy most a másik két vizualizáció is csak Kanadánál emeli ki a sorösszegeket és a megrendelési mennyiségeket.

![Kanadára szűnt eladási adatok](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/22.png)

Ha kijelöl egy terméket a **Quantity by ProductName** (Mennyiség terméknév alapján) grafikonon, a térkép és az adatdiagram az adott termékre vonatkozó adatokra szűr, ha dátumot jelöl ki a **LineTotal by OrderDate** (Sorösszeg megrendelési dátum alapján) grafikonon, a térkép és az adatdiagram az adott dátumra szűr. 
>[!TIP]
>Kijelölés visszavonásához ismételje meg a kijelölést, vagy jelöljön ki egy másik vizualizációt. 

## <a name="complete-the-sales-analysis-report"></a>Az eladáselemzési jelentés befejezése

Az elkészült jelentés a Products.xlsx Excel-fájl és a Northwind OData-csatorna adatait összegzi a vizualizációkban, amelyek a különböző országokra, időtartamokra és termékekre vonatkozó megrendelési adatok elemzését segítik. Az elkészült jelentést [feltöltheti a Power BI szolgáltatásba](desktop-upload-desktop-files.md), és megoszthatja más Power BI-felhasználókkal is.

## <a name="next-steps"></a>Következő lépések
* [Olvassa el a többi Power BI Desktop-oktatóanyagot](http://go.microsoft.com/fwlink/?LinkID=521937)
* [Tekintse meg a Power BI Desktop videóit](http://go.microsoft.com/fwlink/?LinkID=519322)
* [Látogasson el a Power BI fórumára](http://go.microsoft.com/fwlink/?LinkID=519326)
* [Látogasson el a Power BI blogra](http://go.microsoft.com/fwlink/?LinkID=519327)