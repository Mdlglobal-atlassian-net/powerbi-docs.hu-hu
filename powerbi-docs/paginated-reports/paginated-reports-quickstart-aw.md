---
title: 'Oktatóanyag: Lapszámozott jelentés létrehozása és feltöltése a Power BI szolgáltatásba'
description: Ebben az oktatóanyagban egy Azure SQL-mintaadatbázishoz csatlakozik. Ezután a Jelentéskészítő varázslójával létrehoz egy lapszámozott jelentést. Ezt követően feltölti a lapszámozott jelentést a Power BI szolgáltatás Prémium szintű kapacitásának egyik munkaterületére.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: tutorial
ms.date: 11/06/2018
ms.openlocfilehash: 17742c48d9ac5cb49b6d04fe6fe4674e7f6c7ac9
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "80404882"
---
# <a name="tutorial-create-a-paginated-report-and-upload-it-to-the-power-bi-service"></a>Oktatóanyag: Lapszámozott jelentés létrehozása és feltöltése a Power BI szolgáltatásba

Ebben az oktatóanyagban egy Azure SQL-mintaadatbázishoz csatlakozik. Ezután a Power BI Jelentéskészítő varázslójával létrehoz egy lapszámozott jelentést egy több oldalon átívelő táblázattal. Ezt követően feltölti a lapszámozott jelentést a Power BI szolgáltatás Prémium szintű kapacitásának egyik munkaterületére.

![Lapszámozott jelentés a Power BI szolgáltatásban](media/paginated-reports-quickstart-aw/power-bi-paginated-report-service.png)

A jelen oktatóanyagban az alábbi lépéseket fogja végrehajtani:

> [!div class="checklist"]
> * Azure-mintaadatbázis létrehozása.
> * Mátrix létrehozása a Power BI Jelentéskészítőben egy varázslóval.
> * A jelentés formázása címmel, oldalszámokkal és oszlopfejlécekkel minden oldalon.
> * A pénznem formázása.
> * Jelentés feltöltése a Power BI szolgáltatásba.

Ha még nincs Azure-előfizetése, kezdés előtt hozzon létre egy [ingyenes fiókot](https://azure.microsoft.com/free/?WT.mc_id=A261C142F).
 
## <a name="prerequisites"></a>Előfeltételek  

Lapszámozott jelentések létrehozásának előfeltételei:

- [A Power BI Jelentéskészítő telepítése a Microsoft letöltőközpontból](https://go.microsoft.com/fwlink/?linkid=2086513). 

- Kövese az [Azure SQL-mintaadatbázis létrehozása az Azure Portalon](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal) című rövid útmutató lépéseit. Másolja ki és mentse az **Áttekintés** lap **Kiszolgálónév** mezőjének értékét. Jegyezze meg az Azure-ban létrehozott felhasználónevet és jelszót.

A lapszámozott jelentés a Power BI szolgáltatásba való feltöltésének előfeltételei:

- [Power BI Pro-licencre](../service-admin-power-bi-pro-in-your-organization.md) lesz szüksége.
- Egy [Power BI Premium-kapacitásban](../service-premium-what-is.md) található munkaterületre van szüksége a szolgáltatásban. A munkaterület neve mellett egy gyémánt ikon látható ![prémium gyémánt ikon](media/paginated-reports-quickstart-aw/premium-diamond.png).

## <a name="create-the-matrix-with-a-wizard"></a>A mátrix létrehozása a varázslóval
  
1.  Indítsa el a Power BI Jelentéskészítőt a számítógépen.  
  
     Ekkor megjelenik az **Első lépések** párbeszédpanel.  
  
     ![Jelentéskészítő – Első lépések](media/paginated-reports-create-embedded-dataset/power-bi-paginated-get-started.png)
  
1.  A bal oldali panelen ellenőrizze, hogy az **Új jelentés** elem van-e kijelölve, a jobb oldali panelen pedig válassza a **Táblázat vagy mátrix varázsló** lehetőséget.  
  
4.  Az **Adatkészlet kiválasztása** lapon válassza az **Adatkészlet létrehozása** > **Tovább** lehetőséget.  

    ![Adathalmaz létrehozása](media/paginated-reports-quickstart-aw/power-bi-paginated-create-dataset.png)
  
5.  Az **Adatforrás felé irányuló kapcsolat kiválasztása** lapon válassza az **Új** lehetőséget. 

    ![Új adatforrás](media/paginated-reports-quickstart-aw/power-bi-paginated-new-data-source-connection.png)
  
     Ekkor megnyílik az **Adatforrás tulajdonságai** párbeszédpanel.  
  
6.  Az adatforrásnak tetszőleges nevet adhat, amelyekben karaktereket és aláhúzásjeleket használhat. Ebben az oktatóanyagban a **Név** mezőbe a **MyAzureDataSource** kifejezést írja be.  
  
7.  A **Kapcsolattípus kiválasztása** mezőben válassza a **Microsoft Azure SQL Database** elemet.  
  
8.  A **Kapcsolati sztring** mező mellett válassza a **Build** lehetőséget. 

    ![Adatforrás tulajdonságai – Build](media/paginated-reports-quickstart-aw/power-bi-paginated-data-source-properties-build.png)

9. **Az Azure-ban:** Lépjen az Azure Portalra, majd válassza az **SQL-adatbázisok** elemet.

1. Válassza ki a cikk **Előfeltételek** szakaszában található „Azure SQL-mintaadatbázis létrehozása az Azure Portalon” című útmutatóban létrehozott Azure SQL-adatbázist.

1. Másolja ki és mentse az **Áttekintés** lap **Kiszolgálónév** mezőjének értékét.

2. **A Jelentéskészítőben**: A **Kapcsolat tulajdonságai** párbeszédpanel **Kiszolgálónév** területén illessze be a másolt kiszolgálónevet. 

1. A **Bejelentkezés a kiszolgálóra** esetén győződjön meg arról, hogy az **SQL Server-hitelesítés használata** lehetőség van kiválasztva, majd adja meg az Azure-ban létrehozott felhasználónevet és jelszót a mintaadatbázisban.

1. A **Kapcsolódás adatbázishoz** területen kattintson a legördülő nyílra, majd válassza ki az Azure-ban létrehozott adatbázist.
 
    ![Adatforrás kapcsolati tulajdonságai](media/paginated-reports-quickstart-aw/power-bi-paginated-connection-properties.png)

1. Válassza a **Kapcsolat tesztelése** lehetőséget. Ekkor megjelenik a **teszteredmények** üzenet, amely a **tesztkapcsolat sikerességét** jelzi.

1. Válassza az **OK** > **OK** gombot. 

   A Jelentéskészítő a **Kapcsolati sztring** mezőben megjeleníti a létrehozott kapcsolati sztringet. 

    ![Adatforrás kapcsolati sztringje](media/paginated-reports-quickstart-aw/power-bi-paginated-data-source-properties-connection-string.png)

1. Válassza az **OK** lehetőséget.
  
9. Az **Adatforrás felé irányuló kapcsolat kiválasztása** lapon az „(ebben a jelentésben)” kifejezést láthatja a létrehozott adatforrás-kapcsolat alatt. Válassza ki az adatforrást, majd kattintson a **Tovább** gombra.  

    ![Saját Azure-adatforrás](media/paginated-reports-quickstart-aw/power-bi-paginated-my-azure-data-source.png)

10. Írja a mezőbe ugyanazt a felhasználónevet és jelszót. 
  
10. A **Lekérdezés tervezése** lapon bontsa ki a SalesLT, majd a Táblázatok elemet, és jelölje ki a következő táblázatokat:

    - Cím
    - Ügyfél
    - Termék
    - ProductCategory
    - SalesOrderDetail
    - SalesOrderHeader

     Mivel a **Kapcsolatok** > **Automatikus észlelés** beállítás van kiválasztva, a Jelentéskészítő észleli a táblázatok közötti kapcsolatot. 
    
    ![Lekérdezés tervezése](media/paginated-reports-quickstart-aw/power-bi-paginated-design-query.png)
 
1.  Válassza a **Lekérdezés futtatása** lehetőséget. A Jelentéskészítő megjeleníti a **lekérdezés eredményeit**. 
 
     ![Lekérdezés eredményei](media/paginated-reports-quickstart-aw/power-bi-paginated-query-results.png)

18. Válassza a **Tovább** lehetőséget. 

19. Az **Adatkészlet kiválasztása** lapon válassza ki az imént létrehozott adatkészletet, majd kattintson a **Tovább** gombra.

    ![Adatkészlet kiválasztása](media/paginated-reports-quickstart-aw/power-bi-paginated-choose-dataset.png)

1. A **Mezők elrendezése** lapon húzza a következő mezőket a **Használható mezők** mezőből a **Sorcsoportok** mezőbe:

    - CompanyName
    - SalesOrderNumber
    - Product_Name

1. Húzza a következő mezőket a **Használható mezők** mezőből az **Értékek** mezőbe:

    - OrderQty
    - EgységÁr
    - LineTotal

    A Jelentéskészítő automatikusan összeggé alakította az **Értékek** mező mezőit.

    ![Mezők elrendezése](media/paginated-reports-quickstart-aw/power-bi-paginated-drag-fields.png)

24. Az **Elrendezés kiválasztása** lapon hagyja meg az alapértelmezett beállításokat, de törölje a jelet **Csoportok kibontása/összecsukása** jelölőnégyzetből. A Csoportok kibontása/összecsukása funkció a legtöbb esetben hasznos, jelenleg azonban azt szeretnénk, hogy a táblázat több oldalon átíveljen.

1. Válassza a **Tovább** > **Befejezés** lehetőséget. A táblázat a tervezési felületen jelenik meg.
 
## <a name="what-youve-created"></a>Az eredmény

Tekintsük át a varázsló eredményét.

![A Mátrix varázsló eredménye](media/paginated-reports-quickstart-aw/power-bi-paginated-wizard-results.png)

1. A Jelentés adatai panelen láthatja a létrehozott beágyazott Azure-adatforrást és az azon alapuló beágyazott adatkészletet. 

2. A tervezési felület körülbelül 6 hüvelyk széles. A tervezési felületen megjelenik a mátrix, amelyben láthatók az oszlopfejlécek és a helyőrzők. A mátrix hat oszlopot tartalmaz, és úgy tűnik, hogy csak öt sor magas. 

3. Az Order Qty, Unit Price és Line Total értékek mind összegek, és mindegyik sorcsoport egy részösszeget tartalmaz. 

    A tényleges adatértékek továbbra sem látszanak. Ehhez futtatnia kell a jelentést.

4. A Tulajdonságok panelen a kiválasztott mátrix neve Tablix1. A Jelentéskészítőben a *táblix* egy olyan adatterület, amely sorokban és oszlopokban jelenít meg adatokat. Ez táblázat vagy mátrix is lehet.

5. A Csoportosítás panelen három sorcsoport jelenik meg, amelyet létrehozott a varázslóban: 

    - CompanyName
    - Értékesítési megrendelés
    - Terméknév

    Ez a mátrix nem tartalmaz oszlopcsoportokat.

### <a name="run-the-report"></a>A jelentés futtatása

A tényleges értékek megtekintéséhez futtatnia kell a jelentést.

1. Válassza a **Futtatás** lehetőséget a**kezdőlapon**.

   Ekkor megjelennek az értékek. A mátrix jóval több sorral rendelkezik, mint amit Tervezés nézetben láthatott. Láthatja, hogy a Jelentéskészítő szerint az **1.** oldalon tartózkodik a **2?** oldalból. A Jelentéskészítő a lehető leggyorsabban betölti a jelentést, így egyszerre csak néhány oldalnyi adatot tud lekérni. A kérdőjel azt jelenti, hogy a Jelentéskészítő még nem töltötte be az összes adatot.

   ![A jelentés futtatása](media/paginated-reports-quickstart-aw/power-bi-paginated-run-report.png)

2. Válassza a **Nyomtatási elrendezés** lehetőséget. A jelentés ebben a formátumban jelenik meg a nyomtatáskor. A Jelentéskészítő mostanra felmérte, hogy a jelentés 33 oldalas, és automatikusan hozzáadott egy dátum- és időbélyeget az élőlábhoz.

## <a name="format-the-report"></a>A jelentés formázása

Most már van egy mátrixos, 33 oldalas jelentése. Adjunk hozzá néhány funkciót, amellyel feldobhatjuk a megjelenését. A jelentést minden lépés után futtathatja, így megtekintheti a részeredményeket.

- A menüszalag **Futtatás** lapján válassza a **Tervezés** lehetőséget, amely további szerkesztést tesz lehetővé.  

### <a name="set-page-width"></a>Oldalszélesség beállítása

A lapszámozott jelentések általában nyomtatáshoz vannak formázva, az átlagos oldalméret pedig 8,5x11 hüvelyk nagyságú. 

1. A vonalzó húzásával módosítsa a felületet 7 hüvelyk szélességűre. Az alapértelmezett margóméret 1 hüvelyk mindkét oldalon – ezeket kisebbre kell vennünk.

1. Kattintson a tervezőfelület körüli szürke területre a **jelentés** tulajdonságainak megjelenítéséhez.

    Ha nem látja a Tulajdonságok panelt, kattintson a **Nézet** fül **Tulajdonságok** elemére.

2. Bontsa ki a **Margók** szakaszt, és módosítsa a **bal** és **jobb** margókat 0,75 hüvelykre. 

    ![Margók beállítása](media/paginated-reports-quickstart-aw/power-bi-paginated-set-margins.png)
  
### <a name="add-a-report-title"></a>Jelentéscím hozzáadása  

1. Válassza a **Kattintson ide cím megadásához** lehetőséget az oldal tetején, majd írja be az **Értékesítés cég szerint** kifejezést.  

2. Válassza ki a címszöveget, majd a Tulajdonságok panel **Betűtípus** területén módosítsa a **színt** **kékre**.
  
### <a name="add-a-page-number"></a>Oldalszám hozzáadása

Megfigyelhette, hogy egy dátum- és időbélyeg található a jelentés élőlábában. Ehhez oldalszámot is hozzáadhat.

1. A tervezési felület alján, az élőláb jobb oldalán az [&ExecutionTime] kifejezést láthatja. 

2. A Jelentés adatai panelen bontsa ki a Beépített mezők mappát. Húzza az **Oldalszám** elemet az élőláb bal oldalára, az [&ExecutionTime] elemmel megegyező magasságba.

3. A [&PageNumber] mező jobb oldalának húzásával formázza azt négyzet alakúra.

4. A **Beszúrás** lapon válassza a **Szövegmező** lehetőséget.

5. Kattintson a [& PageNumber] jobb oldalára, írja be az „of” kifejezést, majd formázza négyzet alakúra a szövegmezőt.

6. A **Teljes oldalszám összesen** elemet húzza az élőlábra, az „of” kifejezés jobb oldalára, majd a jobb oldal húzásával formázzon ebből is négyzetet.

    ![Oldalszámok húzása](media/paginated-reports-quickstart-aw/power-bi-paginated-add-page-numbers.png)

### <a name="make-the-table-wider"></a>A táblázat kiszélesítése  

Most már kiszélesítheti a mátrixot annyira, hogy az széltében kitöltse a teljes oldalt, a szöveges oszlopok kiszélesítésével pedig elkerülheti a nevek megkurtítását. 
 
1. Jelölje ki a mátrixot, majd a Cég neve oszlopot.

3. Helyezze a kurzort a mátrix tetején található szürke területre, a Cég neve oszlop jobb széléhez. Húzza jobbra addig, amíg az oszlop el nem éri az 1 és 3/8 hüvelyket. 

    ![Az oszlop jobb szélének húzása](media/paginated-reports-quickstart-aw/power-bi-paginated-drag-column.png)

4. A Terméknév jobb szélét húzza addig, amíg az oszlop el nem éri a 3 és 3/4 hüvelyket.   

A mátrix így már majdnem olyan széles, mint a nyomtatási terület.

### <a name="format-the-currency"></a>A pénznem formázása

A jelentés futtatásakor megfigyelhette, hogy a dollárban megadott mennyiségek még nincsenek pénznemként formázva.

1. Jelölje ki a bal felső, [Sum(OrderQty)] cellát, tartsa lenyomva a Shift billentyűt, és jelölje ki a jobb alsó, [Sum(LineTotal)] cellát.

    ![Pénznemértékkel rendelkező cellák kijelölése](media/paginated-reports-quickstart-aw/power-bi-paginated-select-money-cells.png)

2. A **kezdőlapon** válassza a dollárjel ( **$** ) pénznemszimbólumot, majd válassza a **Helyőrzőstílusok** > **Mintaértékek** elem melletti nyilat.
 
    ![Mintaértékek megjelenítése](media/paginated-reports-quickstart-aw/power-bi-paginated-format-currency.png)

    Most már pénznemként formázva láthatja az értékeket.

    ![Pénznem mintaértékei](media/paginated-reports-quickstart-aw/power-bi-paginated-display-sample-values.png)

### <a name="add-column-headers-on-each-page"></a>Oszlopfejlécek hozzáadása minden oldalhoz

Mielőtt közzétenné a jelentést a Power BI szolgáltatásban, még egy formázást elvégezhet: az oszlopfejléceket a jelentés minden oldalán megjelenítheti.

1. A Csoportosítás panel felső sávjának jobb szélén válassza a legördülő nyilat, majd a **Speciális mód** lehetőséget.

    ![Speciális mód bekapcsolása](media/paginated-reports-quickstart-aw/power-bi-paginated-advanced-mode.png)

2. A **Sorcsoportok** területen válassza ki a felső **statikus** sávot. Láthatja, hogy a mátrix Cég neve cellája ki van jelölve.

   ![Statikus csoport kiválasztása](media/paginated-reports-quickstart-aw/power-bi-paginated-static-group.png)

3. A **Tulajdonságok** panelen keresse meg a **Táblix tagja** tulajdonságait. A**KeepWithGroup** beállítást állítsa **Utána** értékre, a **RepeatOnNewPage** beállítást pedig **igazra**.

    ![RepeatOnNewPage beállítása](media/paginated-reports-quickstart-aw/power-bi-paginated-repeat-on-new-page.png)

    Ideje futtatni a jelentést, hogy lássa, jelenleg hogy mutat.

5. A **kezdőlapon** válassza a **Futtatás** lehetőséget.

6. Válassza a **Nyomtatási elrendezés** lehetőséget, ha ezt még nem tette meg. A jelentés már 29 oldalból áll. Görgessen át néhány oldalon. Láthatja, hogy a pénznem formázva van, az oszlopok minden oldalon rendelkeznek fejléccel, a jelentés minden oldala pedig tartalmaz egy élőlábat oldalszámokkal és dátum- és időbélyeggel.
 
    ![Kész oldal](media/paginated-reports-quickstart-aw/power-bi-paginated-finished-page.png)

7. Mentse a jelentést a számítógépre.
 
##  <a name="upload-the-report-to-the-service"></a>Jelentés feltöltése a szolgáltatásba

Most, hogy létrehozta a lapszámozott jelentést, ideje feltölteni a Power BI szolgáltatásba.

1. A Power BI szolgáltatás (`https://app.powerbi.com`) navigációs paneljén válassza a **Munkaterületek** > **Munkaterület létrehozása** lehetőséget.

2. A munkaterületet nevezze el **Azure AW-nek** vagy adjon neki egy egyedi nevet. Egyelőre Ön az egyetlen tag. 

3. Kattintson a **Speciális** elem melletti nyílra, és kapcsolja be a **dedikált kapacitást**. 

    ![Munkaterület létrehozása Prémium szintű kapacitásban](media/paginated-reports-quickstart-aw/power-bi-paginated-create-workspace-premium-capacity.png)

    Ha nem tudja bekapcsolni a dedikált kapacitást, engedélyt kell kérnie a Power BI-rendszergazdájától a munkaterület a dedikált Prémium szintű kapacitáshoz való hozzáadásához.

4. Válasszon egy **elérhető dedikált kapacitást a munkaterület számára**, majd igény szerint **mentse**.
    
    ![Gyémánt Prémium ikon](media/paginated-reports-quickstart-aw/power-bi-paginated-diamond-icon.png)

    Ha a munkaterület nem egy Prémium szintű kapacitás része, a jelentés feltöltésekor a következő üzenet jelenik meg: „Nem sikerült feltölteni a lapszámozott jelentést.” Lépjen kapcsolatba a Power BI- rendszergazdával a munkaterület áthelyezéséhez.

1. Az új munkaterületen válassza az **Adatok lekérése** lehetőséget.

2. A **Fájlok** mezőben válassza a **Beolvasás** lehetőséget.

3. Válassza a **Helyi fájl** elemet, keresse meg a mentett fájl helyét, majd válassza a **Megnyitás** lehetőséget.

   A Power BI importálja a fájlt, amely megjelenik az alkalmazáslista oldal **Jelentések** területén.

    ![Jelentés az alkalmazáslistában](media/paginated-reports-quickstart-aw/power-bi-paginated-app-list.png)

4. A megtekintéshez válassza ki a jelentést.

5. Ha hibaüzenetet kap, előfordulhat, hogy újra meg kell adnia a hitelesítő adatokat. Válassza a **Kezelés** ikont.

    ![A jelentés kezelése](media/paginated-reports-quickstart-aw/power-bi-paginated-manage-report.png)

6. Válassza a **Hitelesítő adatok szerkesztése** lehetőséget és adja meg az Azure-adatbázis létrehozásakor használt, Azure-beli hitelesítő adatokat.

    ![Jelentés hitelesítő adatainak szerkesztése](media/paginated-reports-quickstart-aw/power-bi-paginated-edit-credentials.png)

7. A lapszámozott jelentést mostantól megtekintheti a Power BI szolgáltatásban.

    ![Lapszámozott jelentés a Power BI szolgáltatásban](media/paginated-reports-quickstart-aw/power-bi-paginated-report-service.png)

## <a name="next-steps"></a>Következő lépések

[Mik a lapszámozott jelentések a Power BI Premiumban?](paginated-reports-report-builder-power-bi.md)

