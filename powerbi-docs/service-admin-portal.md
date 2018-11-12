---
title: Power BI felügyeleti portál
description: A felügyeleti portál a Power BI bérlői felügyeletét teszi lehetővé a munkahelyen. Olyan lehetőségeket kínál, mint például a használati metrikák, hozzáférés az Office 365 felügyeleti központjához, valamint a beállítások.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 10/30/2018
LocalizationGroup: Administration
ms.openlocfilehash: 3e125061766d6ade0daeaacb208d3070d8e9bd9b
ms.sourcegitcommit: d20f74d5300197a0930eeb7db586c6a90403aabc
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/03/2018
ms.locfileid: "50973258"
---
# <a name="power-bi-admin-portal"></a>Power BI felügyeleti portál

A felügyeleti portál segítségével kezelheti a szervezetéhez tartozó Power BI-*bérlőt*. A portál olyan lehetőségeket kínál, mint például a használati metrikák, hozzáférés az Office 365 felügyeleti központjához, valamint a beállítások.

Az Office 365 minden globális rendszergazdája hozzáférhet a teljes felügyeleti portálhoz, valamint olyan felhasználók is, akik Power BI-szolgáltatásadminisztrátori szerepkört kaptak. Ha még nem kapott ilyen szerepkörbe, csak a **kapacitásbeállításokat** láthatja a portálon. A Power BI szolgáltatás rendszergazdai szerepkörére vonatkozó további információkat [a Power BI rendszergazdai szerepkörét ismertető](service-admin-role.md) témakör tartalmaz.

## <a name="how-to-get-to-the-admin-portal"></a>A felügyeleti portál elérése

A Power BI felügyeleti portál eléréséhez az adott fiókot **globális rendszergazdaként** kell megjelölni az Office 365-ben vagy az Azure Active Directoryban, vagy Power BI-szolgáltatásadminisztrátori szerepkört kell hozzárendelni. További információ a Power BI-szolgáltatásadminisztrátori szerepkörről: [A Power BI rendszergazdai szerepkörének ismertetése](service-admin-role.md). A Power BI felügyeleti portál eléréséhez tegye az alábbiakat.

1. Válassza ki a Beállítások fogaskereket a Power BI szolgáltatás jobb felső sarkában.

1. Válassza a **Felügyeleti portál** lehetőséget.

    ![A felügyeleti portál beállításai](media/service-admin-portal/powerbi-admin-settings.png)

A portálon hét lap található. A cikk további részében ezen lapokról olvashat.

![Navigálás a felügyeleti portálon](media/service-admin-portal/powerbi-admin-landing-page.png)

* [Használati metrikák](#usage-metrics)
* [Felhasználók](#users)
* [Auditnaplók](#audit-logs)
* [Bérlői beállítások](#tenant-settings)
* [Premium-beállítások](#premium-settings)
* [Beágyazási kódok](#embed-codes)
* [Szervezeti vizualizációk](#organization-visuals)

## <a name="usage-metrics"></a>Használati metrikák

A **Használati metrikák** segítségével nyomon követheti a szervezet Power BI-használatát. Ezenkívül azt is mutatja, hogy mely munkahelyi felhasználók és csoportok a legaktívabbak a Power BI-ban.

> [!NOTE]
> Az irányítópult első használatakor, vagy ha hosszú idő elteltével keresi fel újra az irányítópultot, egy betöltési képernyő jelenik meg az irányítópult betöltése során.

Miután az irányítópult betöltődött, két szakaszba sorolt csempék jelennek meg. Az első szakasz tartalmazza az egyes felhasználók használati adatait, míg a második szakaszban a munkahelyi csoportok hasonló információi láthatók.

Az alábbiakban az egyes csempéknél megjelenő részletes információkat ismertetjük:

* A felhasználói munkaterület összes irányítópultjának, jelentésének és adatkészletének eltérő darabszáma
  
    ![Az irányítópultok, jelentések és adatkészletek eltérő darabszáma](media/service-admin-portal/powerbi-admin-usage-metrics-number-tiles.png)

* A legtöbbet használt irányítópult az ahhoz hozzáférő felhasználók száma szerint. Például ha 3 felhasználóval oszt meg egy irányítópultot, és olyan tartalomcsomaghoz is hozzáadja azt, amelyhez két különböző felhasználó kapcsolódik, a számláló értéke 6 (1 + 3 + 2)
  
    ![Legtöbbet felhasznált irányítópultok](media/service-admin-portal/powerbi-admin-usage-metrics-top-dashboards.png)

* A legnépszerűbb tartalom, amelyhez a felhasználók kapcsolódtak. Ez bármi lehet, amelyhez a felhasználók hozzáférhetnek az adatbeolvasási folyamaton keresztül, például szolgáltatott szoftveres tartalomcsomagok, munkahelyi tartalomcsomagok, fájlok vagy adatbázisok.
  
    ![Legtöbbet felhasznált csomagok](media/service-admin-portal/powerbi-admin-usage-metrics-top-connections.png)

* A legaktívabb felhasználókat mutatja az irányítópultok száma alapján, beleértve a felhasználók által létrehozott és a velük megosztott irányítópultok számát.
  
    ![Legaktívabb felhasználók – irányítópultok](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-dashboards.png)

* A legaktívabb felhasználókat mutatja a jelentések száma alapján
  
    ![Legaktívabb felhasználók – jelentések](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-reports.png)

A második szakasz ugyanezeket az információkat tartalmazza – a csoportok alapján. Lehetővé teszi annak megtekintését, hogy a munkahely mely csoportjai a legaktívabbak, és milyen típusú tartalmakat használnak fel.

Ezek az információk valós betekintést nyújtanak abba, hogy a felhasználók miként használják a Power BI-t a munkahelyen, és mely munkahelyi felhasználók és csoportok számítanak különösen aktívnak.

## <a name="users"></a>Felhasználók

A Power BI-felhasználókat, -csoportokat és -rendszergazdákat az Office 365 felügyeleti központjában kezelheti. A **Felhasználók** lap tartalmaz egy hivatkozást a bérlő felügyeleti központjára.

![Ugrás az O365 felügyeleti központjára](media/service-admin-portal/powerbi-admin-manage-users.png)

## <a name="audit-logs"></a>Auditnaplók

A Power BI-naplókat az Office 365 Security & Compliance Centerben kezelheti. A **Auditnaplók** lap tartalmaz egy, a bérlőhöz tartozó Security & Compliance centerre mutató hivatkozást. [További információ](service-admin-auditing.md)

Az auditnaplók használatához engedélyezze a [**Vizsgálati naplók létrehozása belső tevékenységek és megfelelőség vizsgálatához**](#create-audit-logs-for-internal-activity-auditing-and-compliance) beállítást.

## <a name="tenant-settings"></a>Bérlői beállítások

A **Bérlői beállítások** lap lehetővé teszi a szervezet számára elérhetővé tett funkciók finomhangolt szabályozását. Ha aggályai vannak a bizalmas adatokkal kapcsolatban, a funkciók némelyike esetlegesen nem megfelelő a munkahely számára, vagy csak egy adott funkciót szeretne engedélyezni egy adott csoportnak.

Az alábbi képen a **Bérlői beállítások** lap első két szakasza látható.

![Bérlői beállítások](media/service-admin-portal/powerbi-admin-tenant-settings.png)

> [!NOTE]
> A beállítás módosításának érvénybe léptetése a bérlő összes felhasználója számára akár 10 percet is igénybe vehet.

A beállítások állapota háromféle lehet:

* **A szervezeten belül sehol nem engedélyezett**: A munkahelyen senki sem használhatja az adott funkciót.

    ![Az összes le van tiltva beállítás](media/service-admin-portal/powerbi-admin-tenant-settings-disabled.png)

* **A szervezeten belül mindenhol engedélyezett**: A munkahelyen mindenki használhatja az adott funkciót.

    ![Az összes engedélyezve van beállítás](media/service-admin-portal/powerbi-admin-tenant-settings-enabled.png)

* **A szervezet egy alegysége számára engedélyezett**: A szervezet felhasználóinak egy adott részhalmaza vagy csoportjai használhatják az adott funkciót.

    Engedélyezhet egy funkciót az egész munkahelyen a felhasználók egy adott csoportja kivételével.

    ![Engedélyezett részhalmaz beállítás](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except.png)

    Engedélyezhet egy funkciót a felhasználók egy adott csoportjában, és letilthatja azt a felhasználók egy másik csoportjában. Ezzel a módszerrel garantálható, hogy egyes felhasználók még akkor sem férhetnek hozzá az adott funkcióhoz, ha egyébként benne vannak az engedélyezett csoportban.

    ![Kivéve engedélyezése beállítás](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except2.png)

A következő néhány bekezdés a bérlői beállítások különböző típusainak áttekintését nyújtja.

## <a name="workspace-settings"></a>Munkaterület beállításai

### <a name="create-workspaces-preview"></a>Munkaterületek létrehozása (előzetes verzió)

A vállalat felhasználói alkalmazás-munkaterületeket hozhatnak létre az irányítópultok, jelentések és egyéb tartalmak közös használatához. [További információ](service-create-the-new-workspaces.md)

## <a name="export-and-sharing-settings"></a>Exportálási és megosztási beállítások

### <a name="share-content-to-external-users"></a>Tartalom megosztása külső felhasználókkal

A munkahelyi felhasználók külső felhasználókkal oszthatnak meg irányítópultokat. [További információ](service-share-dashboards.md#share-a-dashboard-or-report-with-people-outside-your-organization)

![Külső felhasználók beállítás](media/service-admin-portal/powerbi-admin-sharing-external-02.png)

Az alábbi képen azon üzenet látható, amely akkor jelenik meg, ha külső felhasználóval oszt meg tartalmat.

![Megosztás külső felhasználóval](media/service-admin-portal/powerbi-admin-sharing-external.png)

### <a name="publish-to-web"></a>Webes közzététel

A munkahelyi felhasználók a weben tehetnek közzé jelentéseket. [További információ](service-publish-to-web.md)

Az alábbi képen látható a **Fájl** menü egy jelentéshez, ha a **Webes közzététel** beállítás engedélyezve van.

![Webes közzététel beállítás](media/service-admin-portal/powerbi-admin-publish-to-web.png)

A **Webes közzététel** beállításától függően a felhasználók különféle lehetőségeket láthatnak a felhasználói felületen.

|Funkció |A teljes cég számára engedélyezve |A teljes cég számára letiltva |Speciális biztonsági csoportok   |
|---------|---------|---------|---------|
|A **Webes közzététel** parancs egy jelentés **Fájl** menüjében.|Mindenki számára engedélyezve|Nem mindenki számára látható|Csak az arra jogosult felhasználók vagy csoportok láthatják.|
|A **Beágyazási kódok kezelése** funkció a **Beállítások** közt|Mindenki számára engedélyezve|Mindenki számára engedélyezve|Mindenki számára engedélyezve<br><br>* A **Törlés** parancsot csak az arra jogosult felhasználók vagy csoportok érik el.<br>* A **Kód lekérése** mindenki számára engedélyezve van.|
|**Beágyazási kódok** a felügyeleti portálon|Az állapot a következő értékek egyikét jeleníti meg:<br>* Aktív<br>* Nem támogatott<br>* Blokkolva|Állapotként a **Letiltva** jelenik meg|Az állapot a következő értékek egyikét jeleníti meg:<br>* Aktív<br>* Nem támogatott<br>* Blokkolva<br><br>Ha egy felhasználónak nincs megfelelő jogosultsága a bérlői beállítások alapján, akkor a **Megsértve** állapot jelenik meg.|
|Meglévő közzétett jelentések|Minden engedélyezve|Minden letiltva|A jelentések továbbra is megjelennek mindenki számára.|

### <a name="export-data"></a>Adatok exportálása

A munkahelyi felhasználók adatokat exportálhatnak egy csempéről vagy vizualizációból. [További információ](visuals/power-bi-visualization-export-data.md)

Az alábbi képen az adatok exportálásának lehetősége látható egy csempén.

![Adatok exportálása egy csempéből](media/service-admin-portal/powerbi-admin-export-data.png)

> [!NOTE]
> Az **Adatok exportálása** lehetőség letiltásával azt is megakadályozhatja, hogy a felhasználók az **Elemzés az Excelben** funkciót vagy a Power BI szolgáltatás élő kapcsolatát használják.

### <a name="export-reports-as-powerpoint-presentations"></a>Jelentések exportálása PowerPoint-bemutatóként

A munkahelyi felhasználók PowerPoint-fájlként exportálhatják a Power BI-jelentéseket. [További információ](consumer/end-user-powerpoint.md)

Az alábbi képen látható a **Fájl** menü egy jelentéshez, ha a **Jelentések exportálása PowerPoint-bemutatóként** beállítás engedélyezve van.

![Jelentések exportálása PowerPoint-bemutatóként](media/service-admin-portal/powerbi-admin-powerpoint.png)

### <a name="print-dashboards-and-reports"></a>Irányítópultok és jelentések nyomtatása

A munkahelyi felhasználók irányítópultokat és jelentéseket nyomtathatnak. [További információ](consumer/end-user-print.md)

Az alábbi képen az irányítópult nyomtatásának lehetősége látható.

![Irányítópult nyomtatása](media/service-admin-portal/powerbi-admin-print-dashboard.png)

Az alábbi képen a jelentéshez tartozó **Fájl** menü látható, ha az **Irányítópultok és jelentések nyomtatása** beállítás engedélyezve van.

![Jelentés nyomtatása](media/service-admin-portal/powerbi-admin-print-report.png)

## <a name="content-pack-and-app-settings"></a>Tartalomcsomag és alkalmazás beállításai

### <a name="publish-content-packs-and-apps-to-the-entire-organization"></a>Tartalomcsomagok és alkalmazások közzététele a teljes szervezet számára

A munkahely felhasználói nem csupán egyes csoportok, hanem a teljes szervezet számára közzétehetik a tartalomcsomagokat és alkalmazásokat. [További információ](service-organizational-content-pack-manage-update-delete.md)

Az alábbi képen a **Teljes saját szervezet** lehetőség látható a tartalomcsomag létrehozásakor.

![Tartalomcsomag közzététele a szervezet számára](media/service-admin-portal/powerbi-admin-publish-entire-org.png)

### <a name="create-template-organizational-content-packs-and-apps"></a>Szervezeti tartalomcsomagok és alkalmazások sablonjainak létrehozása

A munkahelyi felhasználók tartalomcsomag-sablonokat készíthetnek, amelyek a Power BI Desktop adatkészleteit használják. [További információ](template-content-pack-authoring.md)

### <a name="push-apps-to-end-users"></a>Alkalmazások küldése a végfelhasználóknak

A felhasználók közvetlenül is megoszthatnak alkalmazásokat a végfelhasználókkal, anélkül, hogy telepíteni kéne azokat az AppSource-ból. [További információ](service-create-distribute-apps.md)

## <a name="integration-settings"></a>Integrálási beállítások

### <a name="ask-questions-about-data-using-cortana"></a>Adatokkal kapcsolatos kérdések feltevése Cortanával

A munkahelyi felhasználók Cortana használatával kérdéseket tehetnek fel az adataikról. [További információ](service-cortana-enable.md)

> [!NOTE]
> Ez a beállítás az egész munkahelyre vonatkozik, és nem lehet korlátozni meghatározott csoportokra.

### <a name="use-analyze-in-excel-with-on-premises-datasets"></a>Az Elemzés az Excelben helyszíni adatkészleteken való használata

A munkahelyi felhasználók az Excel használatával megtekinthetik és használhatják a helyszíni Power BI-adatkészleteket. [További információ](service-analyze-in-excel.md)

> [!NOTE]
> Az **Adatok exportálása** lehetőség letiltásával azt is megakadályozhatja, hogy a felhasználók az **Elemzés az Excelben** funkciót használják.

### <a name="use-arcgis-maps-for-power-bi"></a>Az ArcGIS Maps for Power BI használata

A vállalati felhasználók használhatják az Esri által biztosított ArcGIS Maps for Power BI vizualizációt. [További információ](power-bi-visualization-arcgis.md)

### <a name="use-global-search-for-power-bi-preview"></a>A globális keresés használata a Power BI-ban (előzetes verzió)

A vállalati felhasználók használhatják az Azure Searchre épülő külső keresési funkciókat. Például a felhasználók a Cortana használatával a lényeges információkat közvetlenül a Power BI-irányítópultokból és -jelentésekből nyerhetik ki. [További információ](service-cortana-intro.md)

## <a name="custom-visuals-settings"></a>Egyéni vizualizációk beállításai

### <a name="enable-custom-visuals-for-the-entire-organization"></a>Egyéni vizualizációk engedélyezése a teljes cég számára

A munkahelyi felhasználók egyéni vizualizációkat használhatnak és oszthatnak meg. [További információ](power-bi-custom-visuals.md)

> [!NOTE]
> Ez a beállítás az egész munkahelyre vonatkozik, és nem lehet korlátozni meghatározott csoportokra.

## <a name="r-visuals-settings"></a>R-vizualizációk beállításai

### <a name="interact-with-and-share-r-visuals"></a>R-vizualizációk kezelése és megosztása

A munkahelyi felhasználók R-szkriptekkel készült vizualizációkat használhatnak és oszthatnak meg. [További információ](visuals/service-r-visuals.md)

> [!NOTE]
> Ez a beállítás az egész munkahelyre vonatkozik, és nem lehet korlátozni meghatározott csoportokra.

## <a name="audit-and-usage-settings"></a>Naplózási és használati beállítások

### <a name="create-audit-logs-for-internal-activity-auditing-and-compliance"></a>Auditnaplók létrehozása a belső tevékenységek vizsgálatához és a megfelelőség biztosításához

A felhasználók a naplózással nyomon követhetik, hogy a munkahely más felhasználói milyen műveleteket hajtottak végre a Power BI-ban. [További információ](service-admin-auditing.md)

Az auditnapló bejegyzéseinek rögzítéséhez engedélyezni kell ezt a beállítást. Akár 48 órás késés is lehet a naplózás engedélyezése és a naplózási adatok megtekinthetővé válása között. Ha nem látja azonnal adatokat, ellenőrizze később az auditnaplókat. Hasonló késés lehet az auditnaplók megtekintési engedélyének megkapása és a naplók elérésének lehetővé válása között.

> [!NOTE]
> Ez a beállítás az egész munkahelyre vonatkozik, és nem lehet korlátozni meghatározott csoportokra.

### <a name="usage-metrics-for-content-creators"></a>Használati metrikák tartalomkészítők számára

A munkahelyi felhasználók láthatják az általuk létrehozott jelentések és irányítópultok használati metrikáit. [További információ](service-usage-metrics.md)

### <a name="per-user-data-in-usage-metrics-for-content-creators"></a>Felhasználónkénti adatok a használati metrikákban a tartalmak szerzői számára

A tartalmak szerzőinek használati metrikáiban szerepel a tartalmakhoz hozzáférő felhasználók megjelenítendő neve és e-mail-címe. [További információ](service-usage-metrics.md)

A felhasználónkénti adatok alapértelmezés szerint engedélyezve vannak a használati metrikákhoz, a tartalomkészítői fiókadatok pedig szerepelnek a metrikák jelentéseiben. Ha ezt az információt nem szeretné belefoglalni egyes felhasználók esetében, tiltsa le a funkciót megadott biztonsági csoportok, vagy a teljes szervezet számára. A fiókadatok ekkor *névtelenként* jelennek meg a jelentésben.

## <a name="dashboard-settings"></a>Irányítópult beállításai

### <a name="data-classification-for-dashboards"></a>Irányítópultok adatainak besorolása

A munkahelyi felhasználók a biztonsági szint besorolását jelző címkékkel láthatják el az irányítópultokat. [További információ](service-data-classification.md)

> [!NOTE]
> Ez a beállítás az egész munkahelyre vonatkozik, és nem lehet korlátozni meghatározott csoportokra.

## <a name="developer-settings"></a>Fejlesztői beállítások

### <a name="embed-content-in-apps"></a>Tartalom beágyazása alkalmazásokba

A munkahelyi felhasználók beágyazhatnak Power BI-irányítópultokat és -jelentéseket szolgáltatott szoftveres (SaaS-) alkalmazásokba. A beállítás kikapcsolásával megakadályozhatja, hogy a felhasználók a REST API-k használatával Power BI-tartalmakat ágyazzanak be saját alkalmazásukba. [További információ](developer/embedding.md)

## <a name="workspaces-and-import-settings"></a>Munkaterületek és importálási beállítások

### <a name="author-content-in-workspaces"></a>Szerzői tartalmak a munkaterületeken

A munkahelyi felhasználók hozzáférhetnek a munkaterületekhez, hogy csatlakozni tudjanak az adatokhoz és a szerzői tartalmakhoz. [További információ](service-create-the-new-workspaces.md)

### <a name="import-data-into-power-bi"></a>Adatok importálása a Power BI-ba

A munkahelyi felhasználók adatokat importálhatnak a szolgáltatásba, például jelentéseket tehetnek közzé a Power BI Desktopról, Power BI-jelentésfájlokat tölthetnek fel, és közvetlenül a szolgáltatásból csatlakozhatnak az adatokhoz. [További információ](desktop-upload-desktop-files.md)

## <a name="capacity-settings"></a>Kapacitásbeállítások

### <a name="power-bi-premium"></a>Power BI Premium

A **Power BI Premium** lapon a munkahely által megvásárolt bármely Power BI Premium-kapacitás (EM vagy P termékváltozat) felügyelhető. A munkahely minden felhasználója láthatja a **Power BI Premium** lapot, de annak tartalma csak akkor jelenik meg, ha az adott felhasználó *kapacitás-rendszergazda* vagy rendelkezik a szükséges engedélyekkel. Ha a felhasználó nem rendelkezik ilyen engedéllyel, az alábbi üzenet jelenik meg.

![Nincs hozzáférés a Premium-beállításokhoz](media/service-admin-portal/premium-settings-no-access.png)

További információ a Premium-beállítások kezeléséről: [A Power BI Premium kezelése](service-admin-premium-manage.md).

### <a name="power-bi-embedded"></a>Power BI Embedded

A **Power BI Embedded** lapon megtekintheti az ügyfél számára vásárolt Power BI Embedded (A termékváltozat) kapacitásait. Mivel az A termékváltozatot csak az Azure-tól szerezheti be, a [beágyazott kapacitások Azure-ban való kezelésére](developer/azure-pbie-create-capacity.md) **az Azure Portalt** kell használnia.

A Power BI Embedded (A termékváltozat) beállításainak kezeléséről további információért lásd a [Mi a Power BI Embedded](developer/azure-pbie-what-is-power-bi-embedded.md) szakaszt.

## <a name="embed-codes"></a>Beágyazási kódok

A rendszergazdák megnézhetik a bérlő számára generált beágyazási kódokat. A kódokat vissza is vonhatja, vagy törölheti. [További információ](service-publish-to-web.md)

![Beágyazási kódok a Power BI felügyeleti portálon](media/service-admin-portal/embed-codes.png)

## <a name="organization-visuals"></a>Szervezeti vizualizációk

A **Szervezeti vizualizációk** lapon egyéni vizualizációkat helyezhet üzembe és kezelhet a cégen belül. A szervezeti vizualizációk segítségével egyszerűen helyezhet üzembe szellemi tulajdont képező vizualizációkat, a szerzők pedig láthatják a jelentéseket és importálhatják a saját jelentéseikbe a Power BI Desktopból. [További információ](power-bi-custom-visuals-organization.md)

> [!WARNING]
> Az egyéni vizualizációk biztonsági vagy adatvédelmi kockázatot jelentő kódokat tartalmazhatnak, ezért az adattárban való üzembe helyezés előtt ellenőrizze, hogy megbízható-e a vizualizáció szerzője és forrása.

A következő képen látható az összes olyan egyéni vizualizáció, amely jelenleg megtalálható a szervezet adattárában.

![Szervezeti rendszergazdai visualizáció](media/service-admin-portal/power-bi-custom-visuals-organizational-admin-01.png)

### <a name="add-a-new-custom-visual"></a>Új egyéni vizualizáció hozzáadása

Új egyéni vizualizáció hozzáadásához kövesse az alábbi lépéseket. 

1. A jobb oldali ablaktáblán válassza ki az **Egyéni vizualizáció hozzáadása** lehetőséget.

    ![Egyéni vizualizáció űrlap](media/service-admin-portal/power-bi-custom-visuals-organizational-admin-02.png)

1. Töltse ki az **Egyéni vizualizáció hozzáadása** űrlapot:

    * **Válasszon egy .pbiviz-fájlt** (kötelező): Válasszon ki egy feltöltendő egyéni vizualizációs fájlt. Csak a verziószámmal ellátott API-s vizualizációk támogatottak (itt elolvashatja, ez mit jelent).

    Az egyéni vizualizációk feltöltése előtt át kell tekintenie a vizualizációt biztonsági és adatvédelmi szempontból, hogy biztosan megfeleljen a szervezet igényeinek.

    * **Nevezze el az egyéni vizualizációkat** (kötelező): Adjon egy rövid címet a vizualizációnak, hogy a Power BI Desktop felhasználói könnyen megértsék a rendeltetését.

    * **Ikon**: A Power BI Desktop felhasználói felületén megjelenő ikonfájl.

    * **Leírás**: A vizualizáció rövid leírása, amely több információt szolgáltat a felhasználónak

1. Kattintson a **Hozzáadás** lehetőségre a feltöltés kérelmezéséhez. Ha ez sikeres, az új elem megjelenik a listában. Ha nem, egy ennek megfelelő hibaüzenet jelenhet meg

### <a name="delete-a-custom-visual-from-the-list"></a>Egyéni látványelem törlése a listából

A vizualizáció végleges törléséhez kattintson az adattárban lévő vizualizációhoz tartozó kuka ikonra.

> [!IMPORTANT]
> A törlés nem vonható vissza. A törölt vizualizációk azonnal abbahagyják a renderelést a meglévő jelentésekben. A törölt változatot még ugyanazon vizualizáció ismételt feltöltése sem helyettesíti. A felhasználók azonban újraimportálhatják a vizualizációt, és pótolhatják azt a jelentéseikben.

### <a name="disable-a-custom-visual-in-the-list"></a>Egyéni látványelem letiltása a listában

A vizualizáció szervezeti áruházból való letiltásához válassza a fogaskerék ikont. A **Hozzáférés** szakaszban, tiltsa le az egyéni vizualizációt.

Miután letiltja a vizualizációt, az nem fog megjelenni a meglévő jelentésekben, és az alábbi hibaüzenet jelenik meg.

*Ez az egyéni vizualizáció már nem érhető el. További információért forduljon a rendszergazdához.*

Azonban a könyvjelzőzött vizualizációk továbbra is működnek.

Frissítés vagy rendszergazdai módosítás után a Power BI felhasználóinak újra kell indítaniuk az alkalmazást, vagy a Power BI szolgáltatás használata esetén frissíteniük kell a böngészőt a frissítések megjelenítéséhez.

### <a name="update-a-visual"></a>Vizualizáció frissítése

A vizualizáció munkahelyi áruházból való feltöltéséhez kattintson a fogaskerék ikonra. Keresse meg és töltse fel a vizualizáció új verzióját.

Győződjön meg róla, hogy a vizuális azonosító ugyanaz maradt. Az új fájl az előző fájlt helyére kerül a jelentésekben az egész vállalatnál. Ha azonban a vizualizáció új verziója megbontja az előző verziójának valamely használati vagy adatstruktúráját, akkor ne cserélje le az előző verziót. Ehelyett hozzon létre egy új listázást a vizualizáció új verziójához. Például adjon hozzá egy új verziószámot (X.X verzió) az új listázott vizualizáció címéhez. Ezáltal nyilvánvalóvá válik, hogy ez ugyanaz a vizualizáció, de frissített verziószámmal, így a meglévő jelentések működése nem hibásodik meg. Most is győződjön meg róla, hogy a vizuális azonosító ugyanaz maradt. Így amikor a felhasználók legközelebb belépnek a szervezeti adattárba a Power BI Desktopból, importálhatják az új verziót, amely kérni fogja őket, hogy cseréljék le a jelentésben található jelenlegi verziót.

## <a name="next-steps"></a>Következő lépések

[A Power BI felügyelete a szervezetnél](service-admin-administering-power-bi-in-your-organization.md) [A Power BI rendszergazdai szerepkörének ismertetése](service-admin-role.md)  
[A Power BI-naplózás használata a munkahelyen](service-admin-auditing.md)  
[A Power BI Premium kezelése](service-admin-premium-manage.md)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
