---
title: Dinamikus sorszintű biztonság Analysis Services-beli táblázatos modellel a Power BI-ban
description: Dinamikus sorszintű biztonság Analysis Services-beli táblázatos modellel
author: selvarms
manager: amitaro
ms.reviewer: davidi
editor: davidi
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 10/21/2017
ms.author: selvar
LocalizationGroup: Connect to data
ms.openlocfilehash: 546ae48aac10ae6c72a062665c7d8f448432a194
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54292637"
---
# <a name="dynamic-row-level-security-with-analysis-services-tabular-model"></a>Dinamikus sorszintű biztonság Analysis Services-beli táblázatos modellel
Ez az oktatóanyag bemutatja a **sorszintű biztonság** megvalósításához szükséges lépéseket az **Analysis Services-beli táblázatos modellben**, és a Power BI-jelentésben való használatának módját. A jelen oktatóanyagban szereplő lépések célja, hogy végigvezessék és megismertessék a minta adatkészlet teljesítéséhez szükséges lépésekkel.

Az oktatóanyag során a következő lépésekről részletes leírás található, amelyek segítségével megtudhatja, mit kell tennie egy dinamikus sorszintű biztonság beállításához az Analysis Services-beli táblázatos modellel:

* Új táblázat létrehozása az **AdventureworksDW2012** adatbázisban
* A táblázatos modell felépítése a szükséges tény- és dimenziótáblákkal
* A felhasználók szerepköreinek és engedélyeinek meghatározása
* A modell üzembe helyezése egy **Analysis Services-beli táblázatos** példányon
* A jelentést elérő felhasználó megfelelő adatait megjelenítő jelentés létrehozása a Power BI Desktop segítségével
* A modell üzembe helyezése a **Power BI szolgáltatáson**
* A jelentés alapján egy új irányítópult létrehozása, és végül
* Az irányítópult megosztása munkatársaival

A jelen oktatóanyagban szereplő lépések követéséhez szükség van az **AdventureworksDW2012** adatbázisra, amelyet az **[adattárból](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)** tölthet le.

## <a name="task-1-create-the-user-security-table-and-define-data-relationship"></a>1. feladat: A felhasználói biztonság tábla létrehozása és az adatkapcsolat meghatározása
Számos közzétett cikkben található leírás arról, hogy hogyan állítható be a sorszintű dinamikus biztonság az **SQL Server Analysis Services-beli (SSAS) táblázatos** modellel. Ehhez a mintához a [Dinamikus biztonság implementálása sorszűrőkkel](https://msdn.microsoft.com/library/hh479759.aspx) cikk utasításait követjük. A következő lépések végigvezetik az oktatóanyag első feladatán:

1. Ebben a mintában az **AdventureworksDW2012** relációs adatbázist használjuk. Hozza létre a **DimUserSecurity** táblát az adatbázisban az alábbi képen látható módon. Ebben a példában az SQL Server Management Studio (SSMS) használatával hozzuk létre a táblát.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable.png)
2. A tábla létrehozása és mentése után létre kell hozni a kapcsolatot a **DimUserSecurity** tábla **SalesTerritoryID** oszlopa és a **DimSalesTerritory** tábla **SalesTerritoryKey** oszlopa között az alábbi képen látható módon. Ez elvégezhető az **SSMS-ből** úgy, hogy jobb gombbal a **DimUserSecurity** táblára kattint, és a **Tervezés** lehetőséget választja. Ezután válassza a **Táblatervező -> Kapcsolatok...** lehetőséget a menüből.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_keys.png)
3. Mentse a táblát, majd adjon meg néhány sornyi felhasználói információt a táblában úgy, hogy ismét a **DimUserSecurity** táblára kattint jobb gombbal, és a **Felső 200 sor szerkesztése** lehetőséget választja. Miután hozzáadta a felhasználókat, a **DimUserSecurity** tábla sorai az alábbi képen látható módon fognak kinézni:
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_users.png)
   
   A későbbi feladatokban visszatérünk ezekhez a felhasználókhoz.
4. A következő lépés egy *belső illesztés* létrehozása a **DimSalesTerritory** táblával, amely a felhasználóhoz társított régió részleteit mutatja. Az alábbi kód elvégzi a *belső illesztést*, és az utána következő kép bemutatja, hogyan fog kinézni a tábla a sikeres *belső illesztés* után.
   
       select b.SalesTerritoryCountry, b.SalesTerritoryRegion, a.EmployeeID, a.FirstName, a.LastName, a.UserName from [dbo].[DimUserSecurity] as a join  [dbo].[DimSalesTerritory] as b on a.[SalesTerritoryID] = b.[SalesTerritoryKey]
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_join_users.png)
5. Figyelje meg, hogy a fenti képen például olyan információk láthatók, hogy melyik felhasználó melyik értékesítési régióért felelős. Ez az adat a **2. lépésben** létrehozott kapcsolat miatt jelenik meg. Azt is figyelje meg, hogy **Jon Doe felhasználó az ausztrál értékesítési régióba tartozik**. A későbbi lépésekben és feladatokban visszatérünk Jon Doe-hoz.

## <a name="task-2-create-the-tabular-model-with-facts-and-dimension-tables"></a>2. feladat: A táblázatos modell létrehozása a tény- és dimenziótáblákkal
1. Miután a relációs adattárház elérhető, ideje meghatározni a táblázatos modellt. A modell létrehozható az **SQL Server Data Tools (SSDT)** használatával. A táblázatos modell meghatározásáról bővebben az [Új táblázatos modellprojekt létrehozása](https://msdn.microsoft.com/library/hh231689.aspx) című cikkben olvashat.
2. Importáljon minden szükséges táblát a modellbe a lent látható módon.
   
    ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/ssdt_model.png)
3. A szükséges táblák importálása után meg kell határoznia egy **Olvasás** engedéllyel rendelkező **SalesTerritoryUsers** szerepkört. Ez úgy érhető el, hogy az SQL Server Data Tools **Modell** menüjére kattint, majd kiválasztja a **Szerepkörök** lehetőséget. A **Szerepkörkezelő** párbeszédpanelen kattintson az **Új** gombra.
4. A **Szerepkörkezelő** **Tagok** lapján adja hozzá az **1. feladat 3. lépésében** a **DimUserSecurity** táblában meghatározott felhasználókat.
   
    ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager.png)
5. Ezután adja hozzá a megfelelő függvényeket a **DimSalesTerritory** és **DimUserSecurity** táblákhoz a **Sorszűrők** lap alatt a képen látható módon.
   
    ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager_complete.png)
6. Ebben a lépésben a **LOOKUPVALUE** függvény használatával egy oszlop értékeit adjuk vissza, amelyben a Windows-felhasználónév megegyezik a **USERNAME** függvény által visszaadott felhasználónévvel. A lekérdezéseket ezután korlátozhatók arra, ahol a **LOOKUPVALUE** által visszaadott értékek megegyeznek az ugyanazon vagy a kapcsolódó táblában találhatókkal. A **DAX-szűrő** oszlopba írja be a következő képletet:
   
       =DimSalesTerritory[SalesTerritoryKey]=LOOKUPVALUE(DimUserSecurity[SalesTerritoryID], DimUserSecurity[UserName], USERNAME(), DimUserSecurity[SalesTerritoryID], DimSalesTerritory[SalesTerritoryKey])
    Ebben a képletben a **LOOKUPVALUE** függvény a **DimUserSecurity[SalesTerritoryID]** oszlop minden értékét visszaadja, ahol a **DimUserSecurity[UserName]** megegyezik az aktuálisan bejelentkezett Windows-felhasználónévvel, az **DimUserSecurity[SalesTerritoryID]** pedig ugyanaz, mint a **DimSalesTerritory[SalesTerritoryKey]**.
   
    > [!IMPORTANT]
    > Ügyeljen arra, hogy sorszintű biztonság használatakor a [USERELATIONSHIP](https://msdn.microsoft.com/query-bi/dax/userelationship-function-dax) DAX-függvény nem támogatott.

   A **LOOKUPVALUE** által visszaadott értékesítési SalesTerritoryKey készletét ezután a **DimSalesTerritory** sorainak korlátozására használja a rendszer. Csak azok a sorok jelennek meg, ahol a sorhoz tartozó **SalesTerritoryKey** megtalálható a **LOOKUPVALUE** függvény által visszaadott azonosítók készletében.
8. A **DimUserSecurity** tábla **DAX-szűrő** oszlopába írja be a következő képletet:
   
       =FALSE()

    Ez a képlet megadja, hogy minden oszlop feloldható a hamis logikai állapotra, ezért nem kérhető le oszlop a **DimUserSecurity** táblához.
1. Most fel kell dolgoznunk és üzembe kell helyeznünk a modellt. Olvassa el az [üzembe helyezésről szóló cikket](https://msdn.microsoft.com/library/hh231693.aspx), ha segítségre van szüksége a modell üzembe helyezésével kapcsolatban.

## <a name="task-3-adding-data-sources-within-your-on-premises-data-gateway"></a>3. feladat: Adatforrások hozzáadása a helyszíni átjáróban
1. Miután üzembe helyezte a táblázatos modellt, és az készen áll a használatára, egy adatforrás-kapcsolatot kell hozzáadnia a helyszíni Analysis Services-beli táblázatos kiszolgálóhoz a Power BI portálon belül.
2. Annak engedélyezéséhez, hogy a **Power BI szolgáltatás** hozzáférhessen a helyszíni elemzési szolgáltatáshoz, egy telepített és konfigurált **[Helyszíni adatátjáróval](service-gateway-onprem.md)** kell rendelkeznie a környezetben.
3. Az átjáró helyes konfigurálása után létre kell hoznia egy adatforrás-kapcsolatot az **Analysis Services-beli** táblázatos példányhoz. Ez a cikk segítséget nyújt az [adatforrások Power BI portálon való hozzáadásában](service-gateway-enterprise-manage-ssas.md).
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_gateway.png)
4. Ha az előző lépés kész, az átjáró konfigurálva van, és készen áll a helyszíni **Analysis Services**-adatforrással való kommunikációra.

## <a name="task-4-creating-report-based-on-analysis-services-tabular-model-using-power-bi-desktop"></a>4. feladat: Analysis Services-beli táblázatos modellen alapuló jelentés létrehozása a Power BI Desktop segítségével
1. Indítsa el a **Power BI Desktop** szolgáltatást, és válassza az **Adatok lekérése > Adatbázis** lehetőséget.
2. Az adatforrások listájából válassza ki az **SQL Server Analysis Services-adatbázist**, majd válassza a **Kapcsolódás** elemet.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata.png)
3. Adja meg az **Analysis Services-beli** táblázatos példány részleteit, és válassza az **Élő csatlakozás** lehetőséget. Kattintson az **OK** gombra. A **Power BI** szolgáltatással a dinamikus biztonság csak **Élő kapcsolattal** működik.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata_connectlive.png)
4. Látni fogja az **Analysis Services**-példányon üzembe helyezett modellt. Válassza ki a megfelelő modellt, és válassza az **OK** gombot.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata_connectlive.png)
5. A **Power BI Desktop** mostantól megjeleníti az összes elérhető mezőt, a **Mezők** ablaktáblán a vászon jobb oldalán.
6. A jobb oldali **Mezők** ablaktáblán válassza ki a **SalesAmount** mértéket a **FactInternetSales** táblából, és a **SalesTerritoryRegion** dimenziót a **SalesTerritory** táblából.
7. Ennél a jelentésnél az egyszerűségre törekszünk, ezért most nem adunk hozzá több oszlopot. Az adatok kifejezőbb megjelenítéséhez a vizualizációt **Fánkdiagramra** állítjuk be.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart.png)
8. Ha elkészült a jelentés, közvetlenül közzé teheti azt a Power BI portálon. A **Power BI Desktop** **Kezdőlap** szalagján válassza a **Közzététel** lehetőséget.

## <a name="task-5-creating-and-sharing-a-dashboard"></a>5. feladat: Irányítópult létrehozása és megosztása
1. Létrehozta a jelentést, és rákattintott a **Közzététel** elemre a **Power BI Desktopban**, így a jelentés közzé lett téve a **Power BI** szolgáltatásban. Most, hogy már elérhető a szolgáltatásban, a modellbiztonsági forgatókönyv bemutatható az előző lépésekben létrehozott példa használatával.
   
   **Értékesítési vezető – Sumit** szerepkörében láthatja a különböző értékesítési régiókból származó adatokat. Ezért létrehozza ezt a jelentést (az előző lépésekben létrehozott jelentést) és közzéteszi azt a Power BI szolgáltatásban.
   
   Miután közzétette a jelentést, létrehozza a jelentésen alapuló **TabularDynamicSec** nevű irányítópultot a Power BI szolgáltatásban. Figyelje meg a következő képen, hogy az Értékesítési vezető (Sumit) megtekintheti az összes értékesítési régiónak megfelelő adatot.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart_1.png)
2. Most Sumit megosztja az irányítópultot a munkatársával, Jon Doe-val, aki az ausztráliai régióban történő értékesítésért felelős.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/user_jon_doe.png)
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_dashboard.png)
3. Ha Jon Doe bejelentkezik a **Power BI** szolgáltatásba, és megtekinti a Sumit által létrehozott, megosztott irányítópultot, **csak** annak a régiónak az értékesítéseit fogja látni, amelyért felelős. Tehát Jon bejelentkezik, eléri az irányítópultot, amelyet Sumit osztott meg vele, és Jon Doe **csak** az ausztráliai régió értékesítéseit látja.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/dashboard_jon_doe.png)
4. Gratulálunk! A helyszíni **Analysis Servicesbeli** táblázatos modellben meghatározott dinamikus sorszintű biztonság sikeresen megjelent és megfigyelhető volt a **Power BI** szolgáltatásban. A Power BI az **effectiveusername** tulajdonságot használja az aktuális Power BI felhasználói hitelesítő adatok helyszíni adatforrásokhoz történő elküldésére, hogy azok futtassák a lekérdezéseket.

## <a name="task-6-understanding-what-happens-behind-the-scenes"></a>6. feladat: Ismerje meg, mi történik a színfalak mögött
1. A feladat azt feltételezi, hogy ismeri az SQL Profilert, mivel egy SQL Server Profiler nyomkövetést szeretne rögzíteni a helyszíni SSAS-beli táblázatos példányon.
2. A munkamenet inicializálva lesz, amint a felhasználó (ebben az esetben Jon Doe) eléri az irányítópultot a Power BI szolgáltatásban. Láthatja, hogy a **salesterritoryusers** szerepkör azonnal életbe lép a hatályos felhasználónévvel a következő formában: **<EffectiveUserName>jondoe@moonneo.com</EffectiveUserName>**
   
       <PropertyList><Catalog>DefinedSalesTabular</Catalog><Timeout>600</Timeout><Content>SchemaData</Content><Format>Tabular</Format><AxisFormat>TupleFormat</AxisFormat><BeginRange>-1</BeginRange><EndRange>-1</EndRange><ShowHiddenCubes>false</ShowHiddenCubes><VisualMode>0</VisualMode><DbpropMsmdFlattened2>true</DbpropMsmdFlattened2><SspropInitAppName>PowerBI</SspropInitAppName><SecuredCellValue>0</SecuredCellValue><ImpactAnalysis>false</ImpactAnalysis><SQLQueryMode>Calculated</SQLQueryMode><ClientProcessID>6408</ClientProcessID><Cube>Model</Cube><ReturnCellProperties>true</ReturnCellProperties><CommitTimeout>0</CommitTimeout><ForceCommitTimeout>0</ForceCommitTimeout><ExecutionMode>Execute</ExecutionMode><RealTimeOlap>false</RealTimeOlap><MdxMissingMemberMode>Default</MdxMissingMemberMode><DisablePrefetchFacts>false</DisablePrefetchFacts><UpdateIsolationLevel>2</UpdateIsolationLevel><DbpropMsmdOptimizeResponse>0</DbpropMsmdOptimizeResponse><ResponseEncoding>Default</ResponseEncoding><DirectQueryMode>Default</DirectQueryMode><DbpropMsmdActivityID>4ea2a372-dd2f-4edd-a8ca-1b909b4165b5</DbpropMsmdActivityID><DbpropMsmdRequestID>2313cf77-b881-015d-e6da-eda9846d42db</DbpropMsmdRequestID><LocaleIdentifier>1033</LocaleIdentifier><EffectiveUserName>jondoe@moonneo.com</EffectiveUserName></PropertyList>
3. A hatályos felhasználónév-kérés alapján az Analysis Services konvertálja a kérést a tényleges moonneo\jondoe hitelesítő adattá a helyi Active Directory lekérdezése után. Miután az **Analysis Services** megkapta a tényleges hitelesítő adatot az Active Directorytól, ezután azon engedélyek és hozzáférés alapján, amelyekkel a felhasználó rendelkezik az adatokon, az **Analysis Services** csak azt az adatot adja vissza, amelyhez a személy engedéllyel rendelkezik.
4. Ha további tevékenység észlelhető az irányítópulton, például Jon Doe az irányítópultról az alapul szolgáló jelentéshez lép, az SQL Profilerrel Ön egy, az Analysis Servicesbeli táblázatos modellhez DAX-lekérdezésként visszaérkező adott lekérdezést fog látni.
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/profiler1.png)
5. Alább a jelentés adatainak feltöltéséhez futtatott DAX-lekérdezést is megtekintheti.
   
   ```
   EVALUATE
     ROW(
       "SumEmployeeKey", CALCULATE(SUM(Employee[EmployeeKey]))
     )
   
   <PropertyList xmlns="urn:schemas-microsoft-com:xml-analysis">``
             <Catalog>DefinedSalesTabular</Catalog>
             <Cube>Model</Cube>
             <SspropInitAppName>PowerBI</SspropInitAppName>
             <EffectiveUserName>jondoe@moonneo.com</EffectiveUserName>
             <LocaleIdentifier>1033</LocaleIdentifier>
             <ClientProcessID>6408</ClientProcessID>
             <Format>Tabular</Format>
             <Content>SchemaData</Content>
             <Timeout>600</Timeout>
             <DbpropMsmdRequestID>8510d758-f07b-a025-8fb3-a0540189ff79</DbpropMsmdRequestID>
             <DbPropMsmdActivityID>f2dbe8a3-ef51-4d70-a879-5f02a502b2c3</DbPropMsmdActivityID>
             <ReturnCellProperties>true</ReturnCellProperties>
             <DbpropMsmdFlattened2>true</DbpropMsmdFlattened2>
             <DbpropMsmdActivityID>f2dbe8a3-ef51-4d70-a879-5f02a502b2c3</DbpropMsmdActivityID>
           </PropertyList>
   ```

## <a name="considerations"></a>Megfontolandó szempontok
Van néhány szempont, melyet figyelembe kell venni a sorszintű biztonsággal, SSAS-szel vagy Power BI szolgáltatással való munka során:

1. Helyszíni sorszintű biztonság a Power BI szolgáltatással csak élő kapcsolattal érhető el.
2. A modell feldolgozása után az adatok bármely módosítása azonnal elérhetővé válik a felhasználók számára (akik **Élő kapcsolaton** keresztül érik el a jelentést) a Power BI szolgáltatásból.

