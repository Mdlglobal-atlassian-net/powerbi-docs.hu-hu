---
title: Az SAP BW Connector használata a Power BI Desktopban
description: Az SAP BW Connector használata a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 10/15/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 73be85644fd320bd44372a0df6c844705c3cf602
ms.sourcegitcommit: b8461c1876bfe47bf71c87c7820266993f82c0d3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/15/2018
ms.locfileid: "49336921"
---
# <a name="use-the-sap-bw-connector-in-power-bi-desktop"></a>Az SAP BW Connector használata a Power BI Desktopban
A Power BI Desktopban hozzáférhet az **SAP Business Warehouse (BW)** adataihoz.

Ha szeretné megismerni, milyen előnyökkel jár, ha az ügyfelek a Power BI-t a meglévő SAP Business Warehouse (BW) rendszerükhöz csatlakoztatják, olvassa el a [Power BI-t és az SAP BW-t bemutató tanulmányt](https://aka.ms/powerbiandsapbw). A DirectQuery az SAP BW-vel való használatáról további tudnivalókat a [DirectQuery és SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md) szolgáltatást ismertető cikkben találhat.

A **Power BI Desktop** 2018. júniusi kiadása óta (és a 2018. októberi kiadástól általánosan) a SAP BW-összekötőt olyan implementációval használhatja, amelynek teljesítménye és képességei jelentős mértékben javultak. Az SAP BW-összekötő felújított változatát a Microsoft fejlesztette, a neve **2.0-s Implementáció**. Ezentúl választhat az 1. verzió (v1) **SAP BW-összekötője** és az **SAP-összekötő 2.0-ás implementációja** között. A következő szakaszok az egyes verziók telepítését mutatják be egymás után. Amikor a Power BI Desktopból az SAP BW-hez kapcsolódik, kiválaszthatja, hogy a kettő közül melyik összekötőt kívánja használni.

Javasoljuk, hogy amikor csak lehetséges az **SAP-összekötő 2.0-s Implementáció** lehetőséget válassza.

## <a name="installation-of-version-1-of-the-sap-bw-connector"></a>Az SAP BW-összekötő 1. verziójának telepítése
Javasoljuk, hogy amikor csak lehetséges, az SAP-összekötő 2.0-s Implementációját használja (a használathoz útmutatást a következő szakaszban talál). Ez a szakasz az **SAP BW-összekötő** 1. verziójának telepítését mutatja be, amelynek folyamata a következő telepítési lépésekből áll:

1. Telepítse az **SAP NetWeaver** kódtárat a helyi számítógépen. Az **SAP Netweaver** kódtárat az SAP-rendszergazdától vagy közvetlenül az [SAP Software Download Center letöltőközpontból](https://support.sap.com/swdc) szerezheti be. Mivel az **SAP Software Download Center** szerkezete gyakran változik, a helyet nem tudjuk pontosabban meghatározni. Az **SAP NetWeaver** kódtárat általában az SAP Client Tools telepítése is tartalmazza.
   
   A legfrissebb verzió letöltései helyének megtalálásához érdemes rákeresnie a *SAP Note #1025361* jegyzetre. Bizonyosodjon meg róla, hogy az **SAP NetWeaver** kódtár architektúrája (32 vagy 64 bites) megegyezik a **Power BI Desktop** telepítésével, majd telepítse az **SAP NetWeaver RFC SDK-t** az SAP-jegyzetnek megfelelően.
2. Az **Adatok lekérése** párbeszédpanelen az **Adatbázis** kategóriában megjelenik egy **SAP Business Warehouse-alkalmazáskiszolgáló** és egy **SAP Business Warehouse üzenetkezelési kiszolgáló** bejegyzés.
   
   ![Adatbeolvasási lehetőségek az SAP-hoz](media/desktop-sap-bw-connector/sap_bw_2a.png)

## <a name="installation-of-implementation-20-sap-connector"></a>Az SAP-összekötő 2.0-s Implementációjának telepítése

Az SAP-összekötő **2.0-s Implementációjához** szükség van az SAP .NET-összekötő 3.0-s verziójára. A következő hivatkozás használatával [letöltheti az SAP .NET-összekötő 3.0-s verzióját](https://support.sap.com/en/product/connectors/msnet.html) az SAP weboldaláról:

* [SAP .NET-összekötő 3.0](https://support.sap.com/en/product/connectors/msnet.html)

A letöltéshez való hozzáféréshez érvényes S-felhasználói fiókra van szükség. Javasoljuk, hogy az SAP .NET-összekötő 3.0-s verziójának beszerzéséhez ügyfeleink lépjenek kapcsolatba SAP Basis-csapatukkal. 

Az összekötő elérhető 32-bites és 64-bites verzióban is, és ezek közül a felhasználóknak azt a verziót *kell* kiválasztaniuk, amelyik a Power BI Desktop telepített verziójához igazodik. A cikk írásának időpontjában két verzió érhető el a weboldalon (a .NET-keretrendszer 4.0-s verziójához):

* SAP-összekötő Microsoft .NET-hez 3.0.20.0-s verzió Windows 32-bites (x86) rendszerhez zip-fájlként (6.896 KB), 2018 Január 16
* SAP-összekötő Microsoft .NET-hez 3.0.20.0-s verzió Windows 64-bites (x64) rendszerhez zip-fájlként (7.180 KB), 2018 Január 16

Telepítéskor ügyeljen rá, hogy a **Választható telepítési lépések** (Optional setup steps) ablakban a *Szerelvények telepítése a globális szerelvény-gyorsítótárba* (Install assemblies to GAC) lehetőség ki legyen választva, ahogy az a következő ábrán is látható:

![Választható telepítési lépések az SAP-hoz](media/desktop-sap-bw-connector/sap_bw_2b.png)

> [!NOTE]
> Az SAP BW-implementáció 1. verziójának esetében szükség van a Netweaver DLL-fájlok telepítésére is, azonban ha az SAP-összekötő 2.0-ás implementációját használja, és nem az 1. verziót, akkor a Netweaver DLL-fájlokra nincsen szükség.


## <a name="version-1-sap-bw-connector-features"></a>Az SAP BW-összekötő 1. verziójának funkciói
A Power BI Desktopban található **SAP BW-összekötő** 1. verziójának használatával adatokat importálhat az **SAP Business Warehouse-kiszolgáló** típusú kockákból, de DirectQuery használatát is lehetővé teszi. 

Az **SAP BW Connectorról** és annak a DirectQueryvel való használatáról [A DirectQuery és az SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md) című cikkből tájékozódhat.

A kapcsolat kiépítéséhez kapcsolódáskor ki kell töltenie a *Kiszolgáló*, a *Rendszer száma* és az *Ügyfélazonosító* mezőt.

![SAP-kiszolgáló kapcsolatbeállításai](media/desktop-sap-bw-connector/sap_bw_3a.png)

Két további **Speciális beállítást** is megadhat: a nyelvkódot, valamint a megadott kiszolgálón futtatható egyéni MDX-utasítást.

![kapcsolat további adatai](media/desktop-sap-bw-connector/sap_bw_4a.png)

Ha nincs MDX-utasítás megadva, a **Kezelő** ablak jelenik meg, amely a kiszolgálón elérhető kockák listáját mutatja, valamint az elérhető kockák részletes elemzését és elemeit, köztük a dimenziók és mértékek kiválasztását lehetővé tevő beállításokat. A Power BI-ban elérhetőek a [BW Open Analysis Interface OLAP BAPI-kban](https://help.sap.com/saphelp_nw70/helpdata/en/d9/ed8c3c59021315e10000000a114084/content.htm) elérhető lekérdezések és kockák.

Amikor kijelöl egy vagy több elemet a kiszolgálón, a rendszer a kijelölés alapján létrehozza a kimeneti tábla előnézetét.

![SAP-táblázat előnézete](media/desktop-sap-bw-connector/sap_bw_5.png)

A **Kezelő** ablakban néhány **megjelenítési beállítás** is elérhető, amelyekkel a következőket állíthatja be:

* **Megjelenítés – *Csak a kijelölt elemek* vagy *Összes elem* (alapértelmezett nézet):** Ezzel a beállítással ellenőrizheti a kiválasztott elemek végleges halmazát. Ezt az *Előnézet* területen az *Oszlopnevek* kiválasztásával is megtekintheti.
* **Adatok előnézetének engedélyezése (alapértelmezett viselkedés):** Szabályozhatja azt is, hogy a párbeszédablakban megjelenjenek-e az adatelőnézetek. Az adatelőnézetek letiltása csökkenti a kiszolgálói hívások mennyiségét, mivel a rendszer nem kér le adatokat az előnézetekhez.
* **Technikai nevek:** Az SAP BW támogatja a kockákban lévő objektumokra vonatkozó *technikai nevek* koncepciót. A technikai nevek segítségével a kocka tulajdonosa *felhasználóbarát* nevekkel jelenítheti meg a kockában lévő objektumokat, nem csupán azok *fizikai neveivel*.

![a Kezelőablak](media/desktop-sap-bw-connector/sap_bw_6.png)

Miután kijelölte az összes szükséges objektumot a **Kezelőben** a **Kezelő** ablak alján lévő alábbi gombokkal meghatározhatja a következő lépéseket:

* A **Betöltés** gombbal a rendszer betölti a kimeneti tábla teljes sorkészletét a Power BI Desktop-adatmodellbe, majd átvált a **Jelentés** nézetbe, ahol elkezdheti összeállítani az adatok vizualizációját, és további módosításokat végezhet az **Adatok** és **Kapcsolatok** nézetek használatával.
* A **Szerkesztés** gomb megnyitja a **Lekérdezésszerkesztőt**, ahol további adatátalakítási és -szűrési lépéseket hajthat végre, mielőtt a rendszer a teljes sorkészletet behúzza a Power BI Desktop-adatmodellbe.

Ne feledje, hogy az **SAP BW**-kockákból importálható adatok mellett adatforrások széles választékából importálhat még adatokat a Power BI Desktopba, és ezeket egyetlen jelentésbe kombinálhatja. Ez számos különféle izgalmas jelentéskészítési és elemzési forgatókönyvet tesz lehetővé az **SAP BW**-adatokra épülően.

## <a name="using-implementation-20-sap-bw-connector"></a>Az SAP BW-összekötő 2.0-s Implementációjának használata

Az SAP BW-összekötő 2.0-s Implementációjának használatához egy új kapcsolatot kell létrehozni. A következő lépések elvégzésével hozhat létre új kapcsolatot:

1. Az **Adatok lekérése** ablakban válassza ki az **SAP Business Warehouse-alkalmazáskiszolgáló** vagy az **SAP Business Warehouse üzenetkezelési kiszolgáló** lehetőségek egyikét.

2. Megjelenik az új kapcsolat párbeszédpanelje, ahol kiválasztható a használni kívánt implementáció. A **2.0-s Implementáció** kiválasztása – mint azt a következő ábra is bemutatja – elérhetővé teszi a Végrehajtási mód, a Köteg mérete, és a Jellemző struktúrák engedélyezése beállítási lehetőségeket.

    ![SAP-kapcsolat párbeszédpanel](media/desktop-sap-bw-connector/sap_bw_7.png)

3. Az **OK** lehetőség kiválasztása után a **Kezelő** használata már megegyezik a szakasz korábbi részében tárgyalt SAP BW-összekötő (1. verzió) esetén leírtakkal. 

### <a name="new-options-for-implementation-20"></a>A 2.0-s Implementáció új beállítási lehetőségei 

A 2.0-s Implementáció a következő beállítási lehetőségeket támogatja:

1. **ExecutionMode** (Végrehajtási mód) – meghatározza a kiszolgálón lekérdezések végrehajtására használt MDX-felületet. A következő érvényes lehetőségek közül választhat:

        a. SapBusinessWarehouseExecutionMode.BasXml
        b. SapBusinessWarehouseExecutionMode.BasXmlGzip
        c. SapBusinessWarehouseExecutionMode.DataStream

    A beállítás alapértelmezett értéke a SapBusinessWarehouseExecutionMode.BasXmlGzip.

    A *SapBusinessWarehouseExecutionMode.BasXmlGzip.* beállítás használata javíthatja a teljesítményt nagy méretű adatkészletek nagy késésű kapcsolattal történő használata esetén.

2. **BatchSize** (Köteg mérete) – Meghatározza az MDX-utasítások végrehajtásakor letöltött sorok maximális számát. Kevesebb sor esetén a nagyobb adatkészletek beolvasásához több hívásra lesz szükség a kiszolgáló felé. Nagy számú sor használata javíthat a teljesítményen, de memóriával kapcsolatos problémákat okozhat a SAP BW-kiszolgálón. Az alapértelmezett érték 50000 sor.

3. **EnableStructures** (Struktúrák engedélyezése) – Logikai érték, amely a jellemző struktúrák felismerésének engedélyezését jelzi. A beállítás alapértelmezett értéke false (hamis). Hatással van a kiválasztható objektumok listájára. Natív lekérdezési módban nem támogatott.

A **ScaleMeasures** (Mértékek skálázása) beállítás elavulttá vált ebben az implementációban. A rendszer viselkedése megegyezik a korábbi *ScaleMeasures = false* (Mértékek skálázása = hamis) beállítással, amely mindig méretezés nélkül jelenítette meg az értékeket.

### <a name="additional-improvements-for-implementation-20"></a>További fejlesztések a 2.0-s Implementációban 

A következő felsorolás bemutatja az új implementáció néhány további fejlesztett funkcióját:

* Jobb teljesítmény
* Akár több millió sornyi adat beolvasása és finomhangolhatóság a kötegméret paraméter használatával.
* Kiválasztható végrehajtási mód.
* Tömörített mód támogatása. Különösen hasznos nagy késleltetésű kapcsolatok vagy nagy adatkészletek esetében.
* A Dátum változók továbbfejlesztett észlelése.
* [Kísérleti funkció] A dátum (DATS ABAP-típusú) és idő (TIMS ABAP-típusú) dimenziók dátummá és idővé alakítása szöveges értékek helyett.
* Jobb kivételkezelés. A BAPI-hívásokban esetleg felmerülő hibák megjelennek a felületen.
* Oszlopok összecsukása BasXml és BasXmlGzip módoknál. Ha például a generált MDX-lekérdezés 40 oszlopot kér le, de az aktuális kijelöléshez csak 10 oszlopra van szükség, akkor ez a kérelem továbbításra kerül a kiszolgáló felé, hogy kisebb adatkészlet kerüljön letöltésre.


### <a name="changing-existing-reports-to-use-implementation-20"></a>Meglévő jelentések átállítása a 2.0-s Implementáció használatára 

A meglévő jelentések átállítása **2.0-s Implementáció használatára** csak Importálás módban lehetséges, és a következő kézileg elvégzendő lépésekből áll:

1. Nyisson meg egy meglévő jelentést, válassza ki a **Lekérdezések szerkesztése** lehetőséget a menüszalagból, ezután pedig válassza ki azt az SAP Business Warehouse-lekérdezést, amelyet frissíteni szeretne.

2. Kattintson jobb gombbal a lekérdezésre, és válassza a **Speciális szerkesztő** lehetőséget.

3. A **Speciális szerkesztő** felületén következőképpen módosítsa az SapBusinessWarehouse.Cubes-hívást: 

    a. Határozza meg, hogy tartalmaz-e már a lekérdezés ahhoz hasonló beállítás-rekordot, mint amilyen a következő példában látható:

    ![lekérdezés-részlet](media/desktop-sap-bw-connector/sap_bw_9.png)

    b. Ha igen, a következő példában látható módon vegye fel az Implementation 2.0 (2.0-s Implementáció) beállítást, és távolítsa el a ScaleMeasures beállítást, ha van ilyen:

    ![lekérdezés-részlet](media/desktop-sap-bw-connector/sap_bw_10.png)

    c. Ha a lekérdezés még nem tartalmaz beállítás-rekordot, egyszerűen vegyen fel egyet. Ha például a következők találhatók a lekérdezésben:

    ![lekérdezés-részlet](media/desktop-sap-bw-connector/sap_bw_11.png)

    d. Egyszerűen módosítsa a következőre:

    ![lekérdezés-részlet](media/desktop-sap-bw-connector/sap_bw_12.png)

4. Az SAP BW-összekötő 2.0-s Implementációjának fejlesztése során mindent megtettünk azért, hogy az kompatibilis maradjon az SAP BW-összekötő 1. verziójával. Ennek ellenére előfordulhat néhány különbség, amelyek az eltérő SAP BW MDX végrehajtási módok használatából fakadnak. Az egyezési hibák elhárítása érdekében érdemes lehet a különböző végrehajtási módok között váltani.

## <a name="troubleshooting"></a>Hibaelhárítás
Ez a szakasz hibaelhárítási forgatókönyveket (és megoldásokat) mutat be az **SAP BW**-összekötő használatához.

1. Az **SAP BW** numerikus adataiban az ezreselválasztó vessző helyett pont szerepel. Például az 1,000,000 helyett 1.000.000 áll.
   
   Az **SAP BW** a tizedes értékeket *,* (vessző) vagy *.* (pont) karakterrel tördelve jeleníti meg. Annak meghatározásához, hogy a kettő közül melyiket használja az **SAP BW** tizedesjelként, a **Power BI Desktop** által használt illesztő meghívja a *BAPI_USER_GET_DETAIL* függvényt. Ez a hívás a **DEFAULTS** (Alapértékek) szerkezetet adja vissza, amelynek a *DCPFM* mezője tárolja a *tizedes formátum jelölését*. A következő három érték egyikét veheti fel:
   
       ‘ ‘ (space) = Decimal point is comma: N.NNN,NN
       'X' = Decimal point is period: N,NNN.NN
       'Y' = Decimal point is N NNN NNN,NN
   
   A hibát jelző ügyfelek azt tapasztalták, hogy a *BAPI_USER_GET_DETAIL* meghívásának hibája esetén az adott felhasználó (akinél az adatok nem megfelelően jelennek meg) a következőhöz hasonló hibaüzenetet kap:
   
       You are not authorized to display users in group TI:
           <item>
               <TYPE>E</TYPE>
               <ID>01</ID>
               <NUMBER>512</NUMBER>
               <MESSAGE>You are not authorized to display users in group TI</MESSAGE>
               <LOG_NO/>
               <LOG_MSG_NO>000000</LOG_MSG_NO>
               <MESSAGE_V1>TI</MESSAGE_V1>
               <MESSAGE_V2/>
               <MESSAGE_V3/>
               <MESSAGE_V4/>
               <PARAMETER/>
               <ROW>0</ROW>
               <FIELD>BNAME</FIELD>
               <SYSTEM>CLNTPW1400</SYSTEM>
           </item>
   
   A hiba megoldásához a felhasználónak meg kell kérnie az SAP-rendszergazdát, hogy engedélyezze a Power BI-ban használt SAPBW felhasználó számára a *BAPI_USER_GET_DETAIL* végrehajtását. Azt is érdemes ellenőrizni, hogy a felhasználónál a megfelelő *DCPFM* érték van-e beállítva a jelen hibaelhárítási forgatókönyvben korábban leírtaknak megfelelően.
2. **Az SAP BEx lekérdezések kapcsolódási beállításai**
   
   A **BEx** lekérdezések végrehajtásához a Power BI Desktopban engedélyezni kell egy adott tulajdonságot, amint az a következő képen látható:
   
   ![](media/desktop-sap-bw-connector/sap_bw_8.png)

## <a name="next-steps"></a>Következő lépések
Az SAP-val és a DirectQueryvel kapcsolatos további információkért tekintse meg az alábbi forrásanyagokat:

* [DirectQuery és SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery és SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md)
* [A DirectQuery használata a Power BI-ban](desktop-directquery-about.md)
* [A DirectQuery által támogatott adatforrások](desktop-directquery-data-sources.md)
* [Power BI és SAP BW - tanulmány](https://aka.ms/powerbiandsapbw)
