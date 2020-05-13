---
title: 'Oktatóanyag: Excelből és OData-csatornáról származó adatok összevonása a Power BI Desktopban'
description: 'Oktatóanyag: Excelből és OData-csatornáról származó adatok összevonása'
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 01/17/2020
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: bf4a4ba9c816aaca19e04d0061df7316ffcc7a2b
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83287303"
---
# <a name="tutorial-analyze-sales-data-from-excel-and-an-odata-feed"></a>Oktatóanyag: Excelből és OData-csatornáról származó értékesítési adatok elemzése

Gyakori, hogy adatok több adatforrásban találhatók. Előfordulhat például, hogy két adatbázissal rendelkezik: egy a termékinformációkhoz, egy pedig az értékesítési adatokhoz. A *Power BI Desktoppal* összevonhatja a különböző forrásokból származó adatokat, így érdekes, meggyőző elemzéseket és vizualizációkat hozhat létre.

Ebben az oktatóanyagban kombinálhatja két adatforrás adatait:

* Egy termékinformációkat tartalmazó Excel-munkafüzet
* Egy rendelési adatokat tartalmazó OData-csatorna

Az adatkészletek importálása után átalakítási és összesítési műveleteket végezhet. Ezután a két forrás adataival értékesítéselemzési jelentést készíthet, amely interaktív vizualizációkat tartalmaz. Ezek a technikák később SQL Server-lekérdezésekhez, CSV-fájlokhoz és a Power BI Desktopban használt egyéb adatforrásokhoz is használhatók.

>[!NOTE]
>A Power BI Desktopban gyakori, hogy egy adott feladatot többféleképpen is el lehet végezni. Például a menüszalag további elemeit megjelenítheti jobb gombbal történő kattintással, vagy az egyik oszlopon vagy cellán található **További lehetőségek** menü választásával is. Az alábbi lépések számos választható módszert leírnak.

## <a name="import-excel-product-data"></a>Excel-termékadatok importálása

Először is importálja a *Products.xlsx* Excel-munkafüzetben lévő termékadatokat a Power BI Desktopba.

1. [Töltse le a Products.xlsx Excel-munkafüzetet](https://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx), és mentse *Products.xlsx* néven.

1. Kattintson a Power BI Desktop **Kezdőlap** szalagfülén az **Adatok beolvasása** elem melletti lenyitó nyílra, majd a **Leggyakoribb** menüben kattintson az **Excel** elemre.

   ![Adatok lekérése](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_1.png)

   >[!NOTE]
   >Az **Adatok beolvasása** elemet kijelölheti közvetlenül, vagy kiválaszthatja a Power BI **Első lépések** párbeszédpanelén is, majd az **Adatok beolvasása** párbeszédpanelen kattintson az **Excel** vagy a **Fájl** > **Excel** elemre, és végül a **Kapcsolódás** elemre.

1. A **Megnyitás** párbeszédpanelben keresse meg és jelölje ki a **Products.xlsx** fájlt, majd kattintson a **Megnyitás** elemre.

1. A **Kezelőben** válassza a **Termékek** táblát, majd az **Adatok átalakítása** lehetőséget.

   ![Az Excel kezelőpanelje](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_2.png)

A Power Query-szerkesztőben megnyílik a tábla előnézeti képe, amelyben átalakításokat hajthat végre az adattisztításhoz.

![Power Query-szerkesztő](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_3.png)

>[!NOTE]
>A Power Query-szerkesztőt a Power BI Desktop **Kezdőlap** szalagfül **Lekérdezések szerkesztése** > **Lekérdezések szerkesztése** elemére kattintva nyithatja meg, vagy úgy, ha a jobb gombbal kijelöli a **Jelentés** nézet mellett lévő **További lehetőségeket**, és ott rákattint a **Lekérdezések szerkesztése** elemre.

## <a name="clean-up-the-products-columns"></a>A termékeket tartalmazó oszlopok tisztítása

Az összevont jelentés az Excel-munkafüzet **ProductID** (Termékazonosító), a **ProductName** (Terméknév), a **QuantityPerUnit** (Mennyiség egységek szerint) és a **UnitsInStock** (Egységek száma a készletben) oszlopokat fogja használni. A többi oszlopot eltávolíthatja.

1. A Power Query-szerkesztőben válassza ki a **ProductID**, a **ProductName**, a **QuantityPerUnit** és a **UnitsInStock** oszlopokat. A Ctrl billentyű használatával egyszerre több oszlopot jelölhet ki, a Shift lenyomva tartásával pedig az egymás melletti oszlopokat.

1. Kattintson a jobb gombbal a kijelölt fejlécek egyikére. Válassza a **További oszlopok eltávolítása** elemet a legördülő menüben.
   Azt is megteheti, hogy a **Kezdőlap** szalagfül **Oszlopok kezelése** csoportjában kattint rá az **Oszlopok eltávolítása** > **További oszlopok eltávolítása** elemre.

   ![További oszlopok eltávolítása](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_removeothercolumns.png)

## <a name="import-the-odata-feeds-order-data"></a>Az OData-csatorna megrendelési adatainak importálása

A következő lépésben importálja a megrendelési adatokat a Northwind értékesítési rendszer mintaanyagából az OData-csatornán keresztül.

1. A Power Query-szerkesztőben kattintson az **Új forrás** elemre, majd válassza a **Leggyakoribbak** legördülő menü **OData-adatcsatorna** elemét.

   ![OData beolvasása](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata.png)

1. Az **OData-csatorna** párbeszédablakban illessze be a Northwind OData-csatorna URL-címét (`https://services.odata.org/V3/Northwind/Northwind.svc/`). Válassza az **OK** lehetőséget.

   ![OData-csatorna párbeszédpanel](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata2.png)

1. Az adatokat úgy töltheti be a Power Query-szerkesztőbe, hogy a **Kezelőben** a **Megrendelések** táblázatra, majd az **Adatok átalakítása** elemre kattint.

   ![OData Kezelő](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_odatafeed.png)

   >[!NOTE]
   >Ha a **Kezelőben** rákattint egy táblázat nevére, de nem jelöli be a jelölőnégyzetet, megtekintheti a táblázat előnézetét.

## <a name="expand-the-order-data"></a>A megrendelési adatok kibontása

Ha több táblázatot tartalmazó adatforrásokhoz csatlakozik, mint például a relációs adatbázisok, vagy a Northwind OData-csatorna, a lekérdezések létrehozásához hivatkozásokat használhat a táblázatok között. A **Megrendelések** táblázat hivatkozásokat tartalmaz több kapcsolódó táblázathoz. A Kibontás művelettel a kapcsolódó **Order_Details** (Megrendelés részletei) táblázatból hozzáadhatja a **ProductID**, a **UnitPrice**, és a **Quantity** oszlopokat a (**Orders**) táblázathoz.

1. Görgessen jobbra a **Megrendelések** táblázatban, amíg el nem jut az **Order_Details** oszlopig. Itt nem adatokat, hanem más táblázatokra mutató hivatkozásokat talál.

   ![Order_Details oszlop](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/order-details-column.png)

1. Kattintson a **Kibontás** ikonra (![Kibontás ikon](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expand.png)) az **Order_Details** oszlop fejlécén.

1. A legördülő menüben:

   1. Válassza **(Az összes oszlop kijelölése)** lehetőséget az összes oszlop törléséhez.

   1. Jelölje ki a **ProductID**, a **UnitPrice**, és a **Quantity** oszlopokat, majd kattintson az **OK** elemre.

      ![Legördülő menü kibontása](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expand-drop-down-menu.png)

Az **Order_Details** tábla kibontása után három új beágyazott táblázat lép az **Order_Details** oszlop helyébe. Minden megrendelés hozzáadott adatai egy-egy új sort jelentenek a táblázatban.

![Kibontott oszlopok](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expanded-columns.png)

## <a name="create-a-custom-calculated-column"></a>Egyéni számított oszlop létrehozása

A Power Query-szerkesztővel számításokat és egyéni mezőket vehet fel az adatok bővítéséhez. Hozzon létre egy egyéni oszlopot, amely az egységár és a tételmennyiség szorzatával kiszámítja egy megrendelés minden sortételének teljes árát.

1. A Power Query-szerkesztő **Oszlop hozzáadása** szalagfülén válassza az **Egyéni oszlop** lehetőséget.

   ![Egyéni oszlop hozzáadása](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/adding-a-custom-column.png)

1. Az **Egyéni oszlop** párbeszédpanelen írja be a **LineTotal** (Sorösszeg) kifejezést az **Új oszlop neve** mezőbe.

1. Az **Egyéni oszlop képlete** mezőben a **=** jel után adja meg az **[Order_Details.UnitPrice]** \* **[Order_Details.Quantity]** adatokat. A mezőneveket a **Megjeleníthető oszlopok** görgetőgombon is kijelölheti, és a begépelés helyett kattinthat a **<< Beillesztés** elemre.

1. Válassza az **OK** lehetőséget.

   ![Egyéni oszlop párbeszédpanel](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/custom-column-dialog-box.png)

   Az új **LineTotal** (Sorösszeg) mező a **Megrendelések** táblázat utolsó oszlopaként jelenik meg.

## <a name="set-the-new-fields-data-type"></a>Adattípus beállítása az új mezőhöz

Amikor a Power Query-szerkesztő csatlakozik az adatokhoz, minden mezőhöz feltételezi a legmegfelelőbb adattípust, és az adatokat ez alapján jeleníti meg. Egy fejlécikon jelzi az egyes mezőkhöz társított adattípust. Igény szerint megtekintheti a **Kezdőlap** menüszalag **Átalakítás** csoportjának **Adattípus** területét is.

Az új **LineTotal** (Sorösszeg) oszlop tartalmaz egy **Bármely** adattípust is, de a benne foglalt értékek pénznemek. Adattípus hozzárendeléséhez kattintson a jobb gombbal a **LineTotal** oszlop fejlécére, válassza ki a legördülő menüből a **Típus módosítása** lehetőséget, és kattintson a **Fixpontos decimális szám** elemre.

![Adattípus fixpontos decimális számmá változtatása](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/change-data-type-to-fixed-decimal.png)

>[!NOTE]
>Azt is megteheti, hogy kiválasztja a **LineTotal** oszlopot, rákattint a lenyitó nyílra a **Kezdőlap** szalagfül **Átalakítás** területének **Adattípusok** eleme mellett, és itt jelöli ki a **Fixpontos decimális szám** elemet.

## <a name="clean-up-the-orders-columns"></a>A megrendelések oszlop tisztítása

Annak érdekében, hogy a modell a jelentéseken belül könnyebben kezelhető legyen, egyes oszlopokat törölhet, átnevezhet és átrendezhet.

A jelentés a következő oszlopokat fogja használni:

* **OrderDate**
* **ShipCity**
* **ShipCountry**
* **Order_Details.ProductID**
* **Order_Details.UnitPrice**
* **Order_Details.Quantity**
* **LineTotal**

Válassza ki ezeket az oszlopokat, majd használja a **További oszlopok eltávolítása** lehetőséget az Excel-adatokhoz hasonlóan. Másik megoldásként kiválaszthatja a listában nem szereplő oszlopokat, jobb gombbal rájuk kattinthat, majd az **Oszlopok eltávolítása** lehetőséget használhatja.

Az „**Order_Details.** ” előtaggal rendelkező oszlopokat átnevezheti a könnyebb olvashatóság érdekében:

1. Kattintson duplán, koppintson hosszan, vagy kattintson a jobb gombbal az egyes oszlopfejlécekre, és a legördülő menüből válassza az **Átnevezés** lehetőséget.

1. Törölje az **Order_Details.** előtagot a nevekből.

Végezetül pedig húzza balra a **LineTotal** oszlopot, közvetlenül a **ShipCountry** oszlop jobb oldalára, hogy könnyebben hozzáférhető legyen.

![A tisztított táblázat](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/cleaned-up-table.png)

## <a name="review-the-query-steps"></a>A lekérdezési lépések áttekintése

Az adatok formázására és átalakítására vonatkozó, Power Query-szerkesztőbeli műveletek rögzítve vannak. A műveletek a **Lekérdezés beállításai** panel **Alkalmazott lépések** területének jobb oldalán jelennek meg. Az **Alkalmazott lépések** területen részletesen áttekinthet, valamint igény szerint törölheti és átrendezheti a lépéseket. A korábbi lépések módosítása azonban kockázatos lehet, mivel ez használhatatlanná tehet későbbi lépéseket.

A Power Query-szerkesztő bal oldalán látható **Lekérdezések** listán válassza ki a lekérdezéseit, és tekintse meg az **Alkalmazott lépéseket** a **Lekérdezés beállításai** ablaktáblán. Az eddigi adatátalakítások után a két lekérdezés az **Alkalmazott lépések** területen az alábbihoz hasonlóan jelenik meg:

![Termékek lekérdezése az Alkalmazott lépésekben](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/products-query-applied-steps.png) &nbsp;&nbsp; ![Megrendelések lekérdezése az Alkalmazott lépésekben](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/orders-query-applied-steps.png)

>[!TIP]
>Az Alkalmazott lépések alapjául a *Power Query nyelvén*, az [M nyelven](https://docs.microsoft.com/powerquery-m/power-query-m-reference) írt képletek szolgálnak. A **Kezdőlap** szalagfül **Lekérdezés** csoportjában lévő **Speciális szerkesztő** kiválasztásával megtekintheti és szerkesztheti a képleteket.

## <a name="import-the-transformed-queries"></a>Az átalakított lekérdezések importálása

Ha elégedett az átalakított adatokkal, kattintson a **Kezdőlap** szalagfül **Bezárás** csoportjának **Bezárás és Alkalmazás** > **Bezárás és alkalmazás** elemére, és ezzel importálja az adatokat a Power BI Desktop **Jelentés** nézetébe.

![Bezárás és alkalmazás](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_4.png)

Az adatok betöltése után a lekérdezések megjelennek a Power BI Desktop **Jelentés** nézetének **Mezők** listáján.

![Lekérdezések a Mezőlistán](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/queries-in-fields-list.png)

## <a name="manage-the-relationship-between-the-datasets"></a>Az adatkészletek kapcsolatainak kezelése

A Power BI Desktopban nem szükséges kombinálni a lekérdezéseket ahhoz, hogy jelentéseket készíthessen belőlük. De az adatkészletek közti kapcsolatokat a közös mezők alapján felhasználhatja a jelentések kiterjesztéséhez és gazdagításához. A kapcsolatokat a Power BI Desktop automatikusan is észlelheti, de Ön is létrehozhatja őket a Power BI Desktop **Kapcsolatok kezelése** párbeszédpanelén. További információ: [Kapcsolatok létrehozása és kezelése a Power BI Desktopban](../transform-model/desktop-create-and-manage-relationships.md).

A megosztott `ProductID` mező létrehoz egy kapcsolatot az oktatóanyag `Orders` és `Products` adathalmaza között.

1. A Power BI Desktop **Jelentés** nézetében a **Kezdőlap** szalagfülön válassza a **Kapcsolatok** terület **Kapcsolatok kezelése** elemét.

   ![Kapcsolatok kezelése menüszalag](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_5.png)

1. A **Kapcsolatok kezelése** párbeszédpanelen látható, hogy a Power BI Desktop már észlelt és felvett a listára egy aktív kapcsolatot a **Termékek** és a **Megrendelések** tábla között. A kapcsolat megtekintéséhez kattintson a **Szerkesztés** elemre.

   ![Kapcsolatok kezelése párbeszédpanel](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_6.png)

   Megnyílik a **Kapcsolat szerkesztése** párbeszédpanel, és láthatóvá válnak a kapcsolat részletei.  

   ![Kapcsolat szerkesztése párbeszédpanel](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_7.png)

1. A Power BI Desktop pontosan észlelte a kapcsolatot, így Ön a **Mégse**, majd a **Bezárás** elemre kattinthat.

A Power BI Desktop bal oldalán válassza a **Modell** lehetőséget a lekérdezési kapcsolatok megtekintéséhez és kezeléséhez. Kattintson duplán a két lekérdezést összekötő vonalon látható nyílra, és ezzel nyissa meg a **Kapcsolat szerkesztése** párbeszédpanelt a kapcsolat megtekintéséhez vagy módosításához.

![Kapcsolat nézet](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_8.png)

A **Modell** nézetből a **Jelentés** ikonra kattintva léphet vissza a **Jelentés** nézethez.

![Jelentés nézet ikonja](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_9.png)

## <a name="create-visualizations-using-your-data"></a>Vizualizációk létrehozása az adatok alapján

A Power BI Desktop Áttekintés nézetében különböző vizualizációkat hozhat létre, amelyekkel elemzéseket készíthet. Többoldalas jelentéseket is készíthet, amelyeknek akár mindegyik oldalán több vizualizáció szerepelhet. A vizualizációkat munkatársaival együtt kezelheti az adatok elemzéséhez és megértéséhez. További információ: [Jelentés használata Szerkesztő nézetben a Power BI szolgáltatásban](../create-reports/service-interact-with-a-report-in-editing-view.md).

Az értékesítési adatok vizualizálásához és elemzéséhez mindkét adatkészletet és a köztük lévő kapcsolatokat is felhasználhatja.

Először is hozzon létre egy mindkét lekérdezés mezőit használó halmozott oszlopdiagramot, amely a megrendelt termékek mennyiségét mutatja.

1. A jobb oldalon lévő **Mezők** tábla **Megrendelések** területén kattintson a **Mennyiség** mezőre, vagy húzza át azt a vászon egyik üres részére. Ez a lépés egy halmozott oszlopdiagramot hoz létre, amelyen az összes megrendelt termék mennyisége látható.

1. Az egyes megrendelt termékek mennyiségének megtekintéséhez kattintson a **ProductName** elemre a **Mezők** tábla **Termékek** területén.

1. A termékek megrendelésszám szerint csökkenő rangsorolásához válassza a vizualizáció jobb felső sarkában lévő **További lehetőségeket** jelző három pontot ( **...** ), majd válassza a **Rendezés mennyiség szerint** elemet.

1. Több terméknév megjelenítéséhez a sarkokban lévő fogópontokkal nagyíthatja fel a diagramot.

   ![Mennyiség terméknév szerint sávdiagram](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/quantity-by-productname-bar-chart.png)

Most hozzon létre egy olyan grafikont, amely a megrendelések dátuma szerinti (**OrderDate**), dollárban kifejezett összegeket (**LineTotal**) tünteti fel.

1. Kijelölés nélküli vászon mellett kattintson a **Mezők** panelen a **Megrendelések** terület **LineTotal** (Sorösszeg) elemére, vagy húzza át azt a vászon egyik üres részére. A halmozott oszlopdiagram az összes megrendelés teljes értékét mutatja dollárban.

1. Jelölje ki a halmozott grafikont, majd válassza az **OrderDate** (Megrendelés dátuma) elemet az **Orders** területről, vagy húzza át azt a grafikonra. A grafikon most az egyes megrendelési dátumokon mutatja a sorösszegeket.

1. Több adat megtekintéséhez a sarkok kihúzásával méretezheti át a vizualizációt.

   ![Grafikon: Sorösszegek a megrendelés dátuma szerint](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/linetotals-by-orderdate-line-chart.png)

   >[!TIP]
   >Ha csak az **Év** értéket és csak három adatpontot lát a grafikonon, válassza a **Vizualizációk** panelen, a **Tengely** mezőben az **OrderDate** elem mellett látható nyilat, és a **Date Hierarchy** helyett kattintson az **OrderDate** elemre.

Végül pedig hozzon létre egy térképi megjelenítést az egyes országokból érkező rendelések ábrázolásához.

1. Kijelölés nélküli vászon mellett kattintson a **Mezők** panelen a **Megrendelések** terület **ShipCountry** (Megrendelés országa) elemére, vagy húzza át azt a vászon egyik üres részére. A Power BI Desktop észleli, hogy az adatok országnevek. Ezért automatikusan létrehoz egy térképi megjelenítést, amelyen adatpont jelöl minden országot, ahonnan megrendelés érkezett.

1. Ha az adatpontok méretét az országok megrendelési mennyiségeinek szeretné megfeleltetni, húzza a **LineTotal** mezőt a térképre. Másik megoldásként a **Vizualizációk** panel **Méret** területének **Ide húzhatja az adatmezőket** szakaszába is húzhatja. A térképen lévő körök területe most az egyes országokból érkező megrendelések dollárban kifejezett összegét tükrözi.

   ![Térképi megjelenítés: Sorösszegek a megrendelés országa alapján](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/linetotals-by-shipcountry-map-visualization.png)

## <a name="interact-with-your-report-visuals-to-analyze-further"></a>A jelentés vizualizációinak kezelése az adatok részletesebb elemzéséhez

A Power BI Desktopban a vizualizációk egymás közötti keresztkiemelések és szűrések segítségével további trendeket képesek mutatni. További információ: [Szűrők és kiemelés a Power BI-jelentésekben](../create-reports/power-bi-reports-filters-and-highlighting.md).

Mivel a lekérdezések kapcsolatban állnak egymással, az egyik vizualizáció kezelése az oldal összes többi vizualizációját is befolyásolja.

Kattintson a térképi megjelenítésen a **Kanadát** jelölő körre. A másik két vizualizáció is csak Kanadánál emeli ki a sorösszegeket és a megrendelési mennyiségeket.

![Kanadára szűnt eladási adatok](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/sales-data-filtered-for-canada.png)

Válasszon egy terméket a **Mennyiség terméknév szerint** diagramon a térkép megtekintéséhez, majd a dátumdiagram szűrőt az adott termék adatainak megjelenítéséhez. Válasszon egy dátumot a **Sorösszeg megrendelési dátum szerint** diagramon a térkép megtekintéséhez, majd a termékdiagram szűrőt az adott dátum adatainak megjelenítéséhez.

>[!TIP]
>Kijelölés visszavonásához ismételje meg a kijelölést, vagy jelöljön ki egy másik vizualizációt.

## <a name="complete-the-sales-analysis-report"></a>Az eladáselemzési jelentés befejezése

Az elkészült jelentés a *Products.xlsx* Excel-fájl és a Northwind OData-csatorna adatait összegzi a vizualizációkban, amelyek a különböző országok megrendelési adatait, időtartamait és termékeit elemzik. Az elkészült jelentést [feltöltheti a Power BI szolgáltatásba](../create-reports/desktop-upload-desktop-files.md), és megoszthatja más Power BI-felhasználókkal is.

## <a name="next-steps"></a>Következő lépések

* [Olvassa el a többi Power BI Desktop-oktatóanyagot](/power-bi/guided-learning/)
* [Tekintse meg a Power BI Desktop videóit](/power-bi/desktop-videos)
* [Látogasson el a Power BI fórumára](https://go.microsoft.com/fwlink/?LinkID=519326)
* [Látogasson el a Power BI blogra](https://go.microsoft.com/fwlink/?LinkID=519327)
