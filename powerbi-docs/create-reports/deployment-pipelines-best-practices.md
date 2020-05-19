---
title: Ajánlott eljárások az üzembehelyezési folyamatokhoz
description: Az üzembehelyezési folyamatok ajánlott eljárásai a Power BI-ban
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 05/06/2020
ms.openlocfilehash: e76d820e804a19db148e0db4c2702e002ee2c017
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83275915"
---
# <a name="deployment-pipelines-best-practices-preview"></a>Ajánlott eljárások az üzembehelyezési folyamatokhoz (előzetes verzió)

Ez a cikk azoknak a BI-alkotóknak nyújt útmutatást, akik a teljes életciklusa során kezelik a tartalmukat. Az üzembehelyezési folyamatok a BI-tartalom életciklus-felügyeleti eszközeként való használatára összpontosít.

A cikk négy szakaszból áll:

* **Tartalom előkészítése** – Készítse elő a tartalmat az életciklus-felügyeletre.

* **Fejlesztés** – Ismerje meg a tartalom létrehozásának legjobb módjait az üzembehelyezési folyamatok fejlesztési szakaszában.

* **Tesztelés** – Tudja meg, hogyan tesztelheti a környezetet az üzembehelyezési folyamatok tesztelési szakaszában.

* **Éles környezet** – Vegye használatba az üzembehelyezési folyamatok éles szakaszát a tartalom elérhetővé tételekor.

## <a name="content-preparation"></a>A tartalom előkészítése

Készítse elő a tartalmát a teljes életciklusát végigkísérő folyamatos felügyeletre. Az alábbi műveletek elvégzése előtt mindenképp tekintse át a jelen szakaszban található információkat:

* A tartalom éles környezetben való közzététele

* Az üzembehelyezési folyamat használatának megkezdése egy adott munkaterületen

* A munka közzététele

### <a name="treat-each-workspace-as-a-complete-package-of-analytics"></a>Az egyes munkaterületek teljes elemzési csomagként való kezelése

Ideális esetben a munkaterületnek teljes képet kell adnia a szervezet egyik aspektusáról (például: részleg, üzleti egység, projekt vagy vertikális). Így egyszerűbben kezelheti a különböző felhasználók engedélyeit, és a tervezett ütemezésnek megfelelően szabályozhatja a tartalom teljes munkaterület számára való közzétételét.  

Ha szervezeti szintű [központosított adathalmazokat](../connect-data/service-datasets-across-workspaces.md) használ, azt javasoljuk, hogy hozzon létre kétféle munkaterületet:

* **Modellezési és adat-munkaterületek** – Ezek a munkaterületek az összes központosított adathalmazt tartalmazzák

* **Jelentéskészítési munkaterületek** – Ezek a munkaterületek az összes kapcsolódó jelentést és irányítópultot tartalmazzák

### <a name="plan-your-permission-model"></a>Az engedélymodell megtervezése

Az üzembehelyezési folyamat egy saját [engedélyekkel](deployment-pipelines-process.md#permissions) rendelkező Power BI-objektum. A folyamat emellett saját engedélyekkel rendelkező munkaterületeket is tartalmaz.

A munkafolyamat biztonságos és egyszerű implementálásához tervezze meg, hogy ki kaphat hozzáférést a folyamat egyes részeihez. Néhány megfontolandó szempont:

* Kinek legyen hozzáférése a folyamathoz?

* Milyen műveleteket végezhetnek a folyamathoz hozzáférő felhasználók az egyes szakaszokban?

* Ki tekinti át a tartalmat a tesztelési szakaszban?

* Hozzáférést kell biztosítani a folyamathoz a tesztelési szakasz felülvizsgálói számára?

* Ki fogja felügyelni az üzembe helyezést az éles szakaszban?

* Melyik munkaterületet rendeli hozzá?

* Melyik szakaszban rendeli hozzá a munkaterületet?

* Módosítania kell a hozzárendelt munkaterület engedélyeit?

### <a name="connect-different-stages-to-different-databases"></a>Szakaszok összekapcsolása különböző adatbázisokkal

Az éles adatbázisoknak mindig stabilnak és elérhetőnek kell lenniük. Nem javasolt túlterhelni őket a BI-alkotók fejlesztési vagy tesztelési adathalmazokhoz létrehozott lekérdezéseivel. Hozzon létre külön adatbázisokat a fejlesztéshez és a teszteléshez. Ez a lépés elősegíti az éles adatok védelmét, és nem terheli túl a fejlesztési adatbázist az összes éles adattal (ami lassulást okozhatna).

>[!NOTE]
>Ha a cége [megosztott központosított adathalmazokat](../connect-data/service-datasets-share.md) használ, nyugodtan kihagyhatja ezt a javaslatot.

### <a name="use-parameters-in-your-model"></a>Paraméterek használata a modellben

A Power BI szolgáltatásban nem szerkesztheti az adathalmazok adatforrásait, ezért azt javasoljuk, hogy a statikus kapcsolati sztring helyett használjon [paramétereket](https://docs.microsoft.com/power-query/power-query-query-parameters) a kapcsolat olyan adatainak tárolásához, mint a példányok és az adatbázisok neve. Így a Power BI szolgáltatás webes portálján, vagy egy későbbi szakaszban [API-k használatával](https://docs.microsoft.com/rest/api/power-bi/datasets/updateparametersingroup) is kezelheti a kapcsolatokat.

Az üzembehelyezési folyamatokban úgy konfigurálhatja a paraméterszabályokat, hogy adott értékeket állítsanak be a fejlesztési, tesztelési és éles szakaszokhoz.

Ha nem használ paramétereket a kapcsolati sztringhez, úgy is meghatározhatja az adatforrás szabályait, hogy megadjanak egy kapcsolati sztringet az adott adathalmaz számára. Az üzembehelyezési folyamatokban azonban ez nem minden adatforrás esetében támogatott. Ha ellenőrizni szeretné, hogy konfigurálhat-e szabályokat az adatforráshoz, tekintse meg az [adathalmazszabályokra vonatkozó korlátozásokat](deployment-pipelines-get-started.md#dataset-rule-limitations).

A paramétereket egyéb módokon is fel lehet használni, például módosítani lehet velük a lekérdezéseket, a szűrőket és a jelentésben megjelenő szöveget.

## <a name="development"></a>Fejlesztés

Ez a szakasz az üzembehelyezési folyamatok fejlesztési szakaszának használatához nyújt útmutatást.

### <a name="use-power-bi-desktop-to-edit-your-reports-and-datasets"></a>Power BI Desktop használata a jelentések és adathalmazok szerkesztésére

Tekintsen úgy a Power BI Desktopra, mint egy helyi fejlesztési környezetre. A Power BI Desktoppal kipróbálhatja, felfedezheti és áttekintheti a jelentések és adathalmazok frissítéseit. A munka befejeztével feltöltheti az új verziót a fejlesztési szakaszba. Az alábbi okok miatt azt javasoljuk, hogy a Desktopban szerkessze a .pbix-fájlokat (a Power BI szolgáltatás helyett):

* Egyszerűbb az együttműködés a .pbix-fájlt használó többi alkotóval, ha minden módosítást ugyanazon az eszközön végeznek.

 * Az online módosítások elvégzése, valamint a .pbix-fájl letöltése és újbóli feltöltése a jelentések és adathalmazok duplikálását eredményezi.

* Naprakészen tarthatja a .pbix-fájlokat a verziókövetés segítségével.

### <a name="version-control-for-pbix-files"></a>Verziókövetés a .pbix-fájlokhoz

Ha kezelni szeretné a jelentések és adathalmazok verzióelőzményeit, használja a [Power BI OneDrive-val történő automatikus szinkronizálását](../connect-data/service-connect-to-files-in-app-workspace-onedrive-for-business.md). A fájlok így folyamatosan frissülni fognak a legújabb verzióval. Ez azt is lehetővé teszi, hogy szükség esetén lekérje a régebbi verziókat.

>[!NOTE]
>A OneDrive-val (vagy bármely más adattárral) történő automatikus szinkronizálást csak az üzembehelyezési folyamatok fejlesztési szakaszában lévő .pbix-fájlokhoz használja. Ne szinkronizálja a .pbix-fájlokat az üzembehelyezési folyamatok tesztelési és éles szakaszába. Ez problémákat fog okozni a tartalmak teljes folyamaton belüli üzembe helyezésekor.

### <a name="separate-modeling-development-from-report-and-dashboard-development"></a>A modellezés fejlesztésének elkülönítése a jelentés és az irányítópult fejlesztésétől

A vállalati szintű üzembe helyezések esetén javasolt elkülöníteni az adathalmaz-fejlesztést a jelentések és irányítópultok fejlesztésétől. Ha a módosításokat csak egy adott jelentésbe vagy adathalmazba szeretné előléptetni, használja az üzembehelyezési folyamatok szelektív üzembehelyezési lehetőségét.  

A megközelítés kiindulópontja a Power BI Desktop, ahol létre kell hoznia egy külön .pbix-fájlt az adathalmazok és jelentések számára. Például létrehozhat egy adathalmaz .pbix-fájlt, és feltöltheti azt a fejlesztési szakaszba. A jelentés szerzői később létrehozhatnak egy új .pbix-fájlt a jelentés számára, és egy élő kapcsolattal [csatlakoztathatják a közzétett adathalmazhoz](../connect-data/service-datasets-discover-across-workspaces.md). Ez a technika lehetővé teszi, hogy az alkotók külön dolgozzanak a modellezésen és a vizualizációkon, és egymástól függetlenül helyezzék üzembe azokat az éles környezetben.

A [megosztott adathalmazokkal](../connect-data/service-datasets-share.md) ezt a módszert egyszerre több munkaterületre is alkalmazhatja.

### <a name="manage-your-models-using-xmla-readwrite-capabilities"></a>Modellek kezelése XMLA írási és olvasási képességekkel

A modellezés fejlesztésének a jelentés és az irányítópult fejlesztésétől történő elkülönítése lehetővé teszi az olyan fejlett képességek használatát, mint a verziókövetés, a különböző módosítások egyesítése és az automatizált folyamatok. Ezeket a módosításokat a fejlesztési szakaszban kell elvégezni, hogy a végleges tartalmat üzembe lehessen helyezni a tesztelési és az éles szakaszban. A módosítások így az éles szakaszban való üzembe helyezés előtt egy egységes folyamaton mennek keresztül, más függő elemekkel együtt.

A [megosztott adathalmaz](../connect-data/service-datasets-share.md) külső munkaterületen, XMLA írási és olvasási képességekkel történő kezelésével elkülönítheti egymástól a modellezés fejlesztését és a vizualizációkat. A megosztott adathalmaz a több folyamatban kezelt különböző munkaterületek több jelentéséhez is csatlakozhat.

## <a name="test"></a>Tesztelés

Ez a szakasz az üzembehelyezési folyamatok tesztelési szakaszának használatához nyújt útmutatást.

### <a name="simulate-your-production-environment"></a>Az éles környezet szimulálása

Az új jelentések és irányítópultok megjelenésének ellenőrzése mellett azt is fontos megvizsgálni, hogy miként teljesítenek ezek a végfelhasználók szemszögéből. Az üzembehelyezési folyamatok tesztelési szakaszában lehetősége van arra, hogy tesztelési célokra szimuláljon egy valódi éles környezetet.

Győződjön meg róla, hogy a tesztelési környezet figyelembe veszi a következő három tényezőt:

* Adatmennyiség

* Használt mennyiség

* Az éles környezetben találhatóhoz hasonló kapacitás

A tesztelés során használhatja ugyanazt a kapacitást, mint az éles szakaszban. A terheléses tesztelés során azonban ez instabillá teheti az éles környezetet. Az instabil éles környezet elkerülése érdekében a teszteléshez használjon egy másik, az éles kapacitáséhoz hasonló erőforrásokkal rendelkező kapacitást. Az extra költségek elkerüléséhez [Azure A-kapacitásokat](../developer/embedded/azure-pbie-create-capacity.md) is használhat, hogy csak a tesztelési időért kelljen fizetnie.

![az üzembehelyezési folyamatok ajánlott eljárásainak ábrája](media/deployment-pipelines-best-practices/deployment-pipelines-best-practices-diagram.png)

### <a name="use-dataset-rules-with-a-real-life-data-source"></a>Adathalmazszabályok használata valós adatforrással

Ha a tesztelési szakaszt a valós adathasználat szimulálására használja, javasolt elkülöníteni egymástól a fejlesztési és tesztelési adatforrásokat. A fejlesztési adatbázisnak viszonylag kis méretűnek kell lennie, a tesztelési adatbázisnak pedig a lehető legjobban kell hasonlítania az éles adatbázishoz. A tesztelési szakaszban használjon [adatforrásszabályokat](deployment-pipelines-get-started.md#step-4---create-dataset-rules) az adatforrások megcseréléséhez.

Az adatforrásból importált adatok mennyiségének szabályozása akkor hasznos, ha éles adatforrást használ a tesztelési szakaszban. Ehhez adjon hozzá egy paramétert az adatforrás lekérdezéséhez a Power BI Desktopban. Az importált adatok mennyiségének szabályozásához és a paraméter értékének szerkesztéséhez használjon paraméterszabályokat.
Ezt a megközelítést akkor is használhatja, ha nem szeretné túlterhelni a kapacitását.

### <a name="measure-performance"></a>Teljesítménymérés

Az éles szakasz szimulálásakor [ellenőrizze a jelentés terhelését és az interakciókat](../guidance/monitor-report-performance.md), és derítse ki, hogy hatással vannak-e rájuk a módosítások.

A [kapacitás terhelését is monitoroznia kell](../admin/service-admin-premium-monitor-capacity.md), hogy kiszűrhesse a szélsőséges terheléseket, mielőtt azok bekerülnének az éles környezetbe.  

>[!NOTE]
>A kapacitásterheléseket azután is ajánlott monitorozni, hogy üzembe helyezte a frissítéseket az éles szakaszban.

### <a name="check-related-items"></a>Kapcsolódó elemek ellenőrzése

Az adathalmazok és a jelentések módosítása a kapcsolódó elemekre is hatással lehet. A tesztelés során győződjön meg arról, hogy a módosítások nem befolyásolják vagy szakítják meg a frissített elemektől függő meglévő elemek teljesítményét.

A kapcsolódó elemeket egyszerűen megkeresheti a munkaterület [leszármaztatási nézetével](../collaborate-share/service-data-lineage.md).

### <a name="test-your-app"></a>Az alkalmazás tesztelése

Ha egy alkalmazáson keresztül osztja meg a tartalmat a végfelhasználókkal, ellenőrizze az alkalmazás új verzióját, mielőtt átvinné azt az éles környezetbe. Minden üzembehelyezési folyamat saját munkaterülettel rendelkezik, ezért egyszerűen közzéteheti és frissítheti az alkalmazásokat a fejlesztési és tesztelési szakaszok számára. Ez lehetővé teszi az alkalmazás végfelhasználó szemszögéből való tesztelését.

>[!IMPORTANT]
>Az üzembehelyezési folyamat nem foglalja magában az alkalmazás tartalmának és beállításainak frissítését. A módosítások tartalomra vagy beállításokra való alkalmazásához manuálisan kell frissítenie az alkalmazást a folyamat megfelelő szakaszában.

## <a name="production"></a>Éles környezet

Ez a szakasz az üzembehelyezési folyamatok éles szakaszához nyújt útmutatást.

### <a name="manage-who-can-deploy-to-production"></a>Az éles környezetben való üzembe helyezést végző személyek kezelése

Az éles környezetben való üzembe helyezést óvatosan kell kezelni, ezért célszerű csak bizonyos személyek számára engedélyezni ezt a különösen kényes műveletet. Ön azonban valószínűleg azt szeretné, hogy az adott munkaterület összes BI-alkotója hozzáférjen folyamathoz. Ezt az éles [munkaterület engedélyeivel](deployment-pipelines-process.md#permissions) szabályozhatja.  

A tartalom szakaszok közötti üzembe helyezéséhez a felhasználóknak tagi vagy rendszergazdai engedéllyel kell rendelkezniük mindkét szakaszhoz. Ügyeljen arra, hogy csak azok személyek rendelkezzenek engedéllyel az éles munkaterülethez, akiknek engedélyezni szeretné az üzembe helyezést az éles környezetben. A többi felhasználóhoz beállíthatja az éles munkaterület közreműködői vagy megtekintői szerepkörét. Ezek a személyek látni fogják a folyamat tartalmát, de nem rendelkeznek engedéllyel az üzembe helyezéshez.

Emellett a folyamathoz való hozzáférést is korlátoznia kell. Ezt úgy teheti meg, hogy csak a tartalomlétrehozási folyamatban részt vevő felhasználók számára engedélyezi a folyamatengedélyeket.

### <a name="set-rules-to-ensure-production-stage-availability"></a>Az éles szakasz rendelkezésre állását biztosító szabályok beállítása

Az [adathalmazszabályokkal](deployment-pipelines-get-started.md#step-4---create-dataset-rules) hatékony módon biztosíthatja, hogy a felhasználók bármikor el tudják érni az éles környezet adatait. Az adathalmazszabályok alkalmazása után a környezetek futása során biztos lehet benne, hogy a végfelhasználók fennakadások nélkül érik el a fontos információkat.

Ne felejtse el beállítani az éles adathalmaz adatforrásokra és az adathalmazban meghatározott paraméterekre vonatkozó szabályait.

### <a name="update-the-production-app"></a>Az éles alkalmazás frissítése

A folyamaton belüli üzembe helyezés frissíti a munkaterület tartalmát, viszont nem frissíti automatikusan a társított alkalmazást. Ha alkalmazást használ a tartalom terjesztésére, az éles környezetben való üzembe helyezés után ne felejtse el frissíteni az alkalmazást, hogy a végfelhasználók azonnal használatba vehessék a legújabb verziót.  

### <a name="quick-fixes-to-content"></a>A tartalom gyorsjavításai

Ha gyorsjavítást igénylő hibák lépnek fel, ne töltsön fel egy új .pbix-verziót közvetlenül az éles szakaszba, és ne végezzen online módosítást a Power BI szolgáltatásban. Ha a tesztelési és a fejlesztési szakaszban már van tartalom, nem lehet visszamenőleges üzembe helyezést végezni. A javítás tesztelés nélküli üzembe helyezése továbbá helytelen gyakorlatnak számít. A probléma kezelésének helyes módja tehát az, ha a javítást a fejlesztési szakaszban implementálja, majd leküldi az üzembehelyezési folyamat többi szakaszába. Így még az éles környezetben való üzembe helyezés előtt ellenőrizheti, hogy működik-e javítás. A teljes folyamatban való üzembe helyezés csak pár percet vesz igénybe.

## <a name="next-steps"></a>Következő lépések

>[!div class="nextstepaction"]
>[Az üzembehelyezési folyamatok bemutatása](deployment-pipelines-overview.md)

>[!div class="nextstepaction"]
>[Az üzembehelyezési folyamatok használatának első lépései](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[Az üzembehelyezési folyamatok feldolgozásának ismertetése](deployment-pipelines-process.md)

>[!div class="nextstepaction"]
>[Az üzembehelyezési folyamatok hibaelhárítása](deployment-pipelines-troubleshooting.md)
