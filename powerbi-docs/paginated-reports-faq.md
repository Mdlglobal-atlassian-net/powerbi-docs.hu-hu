---
title: 'Többoldalas jelentések a Power BI-ban: GYIK (előzetes verzió)'
description: Ez a cikk a lapszámozott jelentésekkel kapcsolatos gyakori kérdésekre ad választ. Ezek a jelentések magas szinten formázott, tökéletesen pontos jelentések, amelyek nyomtatáshoz vagy PDF-készítéshez vannak optimalizálva.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: overview
ms.date: 11/05/2018
ms.author: maggies
ms.openlocfilehash: d86f52b45dfac4252dfd2e7de29de64c16a566ca
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54294107"
---
# <a name="paginated-reports-in-power-bi-faq-preview"></a>Többoldalas jelentések a Power BI-ban: GYIK (előzetes verzió)

Ez a cikk a lapszámozott jelentésekkel kapcsolatos gyakori kérdésekre ad választ. Ezek a jelentések magas szinten formázott, tökéletesen pontos jelentések, amelyek nyomtatáshoz vagy PDF-készítéshez vannak optimalizálva. Lapszámozottnak hívjuk őket, mert több oldalon megjeleníthetők. A lapszámozott jelentések az SQL Server Reporting Services RDL-jelentéseinek technológiáján alapulnak. 

Ez a cikk számos, a Power BI Premium lapszámozott jelentéseivel, valamint a Jelentéskészítővel (a lapszámozott jelentések készítéséhez használt különálló eszközzel) kapcsolatos gyakori kérdést megválaszol. A szolgáltatásban csak Power BI Pro-licenccel tehet közzé jelentéseket. Lapszámozott jelentéseket a Saját munkaterületen vagy az alkalmazások munkaterületein tehet közzé, ha az adott munkaterület egy Power BI Premium-kapacitáshoz tartozik. 

## <a name="administration"></a>Felügyelet

### <a name="what-size-premium-capacity-do-i-need-for-paginated-reports"></a>Milyen méretű Prémium szintű kapacitás szükséges a lapszámozott jelentésekhez?

A lapszámozott jelentések számítási feladatai a P1–P3 termékváltozatokon érhetők el nyilvános előzetes verzióban.  Azonban test/dev forgatókönyvekben az A4–A6 termékváltozatokban is használhatók.

### <a name="what-is-the-maximum-memory-threshold-i-can-put-for-paginated-reports-in-my-capacity"></a>Mi a kapacitásom lapszámozott jelentéseihez megadható maximális memóriaküszöb?

Jelenleg csak a memória 50%-át tarthatja fenn ezekhez a számítási feladatokhoz. 

### <a name="how-does-user-access-work-for-paginated-reports"></a>Hogyan működik a felhasználói hozzáférés lapszámozott jelentések esetén?

A lapszámozott jelentések felhasználói hozzáférése megegyezik a Power BI szolgáltatás minden egyéb tartalmának felhasználói hozzáférésével 

### <a name="how-do-i-turn-onoff-my-paginated-reports-workload"></a>Hogyan kapcsolhatom be és ki a lapszámozott jelentések számítási feladatát?

A kapacitás-rendszergazda engedélyezheti vagy letilthatja a lapszámozott jelentések számítási feladatait a kapacitás-rendszergazdai portálon.  

### <a name="how-can-i-monitor-usage-of-paginated-reports-in-my-tenant"></a>Hogyan tudom monitorozni a bérlőm lapszámozott jelentéseinek használatát?

Az Office 365-naplók a részletesen vezetik eme jelentéstípus használatát a következő eseményekben: 

- Power BI-jelentés megtekintése
- Power BI-jelentés törlése
- Power BI-jelentés létrehozása
- Letöltött Power BI-jelentés

A ReportType mező „PaginatedReport” értéke megkülönbözteti a lapszámozott jelentéseket a Power BI-jelentésektől.

A naplók továbbá a következő eseményeket teszik elérhetővé a lapszámozott jelentésekhez:

- Power BI-adatkészlet kötése egy átjáróhoz
- Power BI-adatforrás feltárása
- TakeOverDatasource (Adatforrás átvétele)

### <a name="can-i-monitor-this-workload-through-the-premium-capacity-monitoring-app"></a>Figyelhetem a számítási feladatot a Prémium szintű kapacitás Monitoring Appjával?

Igen, a monitoring új lapként elérhető ugyanazokkal a releváns információkkal, amelyek az Power BI-adatkészleteknél is elérhetőek.

### <a name="do-i-need-a-pro-license-to-create-and-publish-paginated-reports"></a>Pro-licencre van szükségem lapszámozott jelentések létrehozásához és közzétételéhez?

Igen. Nem tölthet fel jelentéseket a munkaterületre Pro-licenc nélkül. Pro-licenc nélkül is letöltheti és kipróbálhatja a Jelentéskészítőt, azonban nem teheti közzé a létrehozott lapszámozott jelentéseket. 

### <a name="what-if-i-have-a-paginated-report-in-a-workspace-and-the-paginated-report-workload-is-turned-off"></a>Mi történik, ha van egy lapszámozott jelentésem egy munkaterületen, és a lapszámozott jelentés számítási feladata ki van kapcsolva?

Hibaüzenetet kap, a jelentést pedig nem tekintheti meg, amíg be nem kapcsolja a számítási feladatot. A jelentés továbbra is törölhető a munkaterületről.

### <a name="what-is-the-default-memory-for-each-of-the-premium-skus-supported-for-paginated-reports"></a>Mennyi a lapszámozott jelentéseket támogató Prémium termékváltozatok alapértelmezett memóriája?

A lapszámozott jelentéseket támogató Prémium termékváltozatok alapértelmezett memóriája:

- **P1/A4**: Alapértelmezés szerint 20%; minimum 10%
- **P2/A5**: Alapértelmezés szerint 20%; minimum 5%
- **P3/A6**: Alapértelmezés szerint 20%; minimum 2,5%

## <a name="general"></a>Általános

### <a name="when-should-i-use-a-paginated-report-vs-a-power-bi-report"></a>Mikor érdemes lapszámozott, illetve Power BI-jelentést használnom?

A lapszámozott jelentések olyan forgatókönyvekhez ideálisak, amelyek magas szinten formázott, tökéletesen pontos jelentéseket igényelnek, amelyek nyomtatáshoz vagy PDF-készítéshez vannak optimalizálva.  Erre jó példa lehet egy havi eredménybeszámoló.  

A Power BI-jelentések áttekintéshez és interaktivitáshoz tökéletesek.  Például egy Power BI-jelentés a legmegfelelőbb választás egy olyan értékesítési jelentés esetében, amelyben különböző értékesítők saját régiójuk/iparáguk/ügyfeleik szerint szeretnék szeletelni ugyanazon jelentés adatait, és megtekinteni, hogyan változnak a számok.

### <a name="the-documentation-says-report-builder-is-the-preferred-authoring-tool-can-i-create-paginated-reports-in-sql-server-data-tools-for-power-bi"></a>A dokumentáció szerint a Jelentéskészítő az előnyben részesített jelentéskészítő eszköz. Létrehozhatok lapszámozott jelentéseket az SQL Server Data Tools for Power BI szolgáltatással is?

Igen, azonban a Power BI szolgáltatással egyszerre csak egy elem tölthető fel, így számos SQL Server Data Tools- (SSDT-) forgatókönyve még nem támogatott. A [nem támogatott funkciók teljes listáját](#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi) a gyakori kérdések későbbi egy szakaszában tekintheti meg.  

### <a name="what-versions-of-report-builder-do-you-support"></a>A Jelentéskészítő mely verziói támogatottak?

A jelentések a Power BI szolgáltatásban való létrehozásához és közzétételéhez az SQL Server 2016 Jelentéskészítőjének legújabb verzióját használja. Telepítse a [Jelentéskészítőt a Microsoft letöltőközpontból](https://www.microsoft.com/download/details.aspx?id=53613).

### <a name="how-do-i-move-existing-reports-i-have-saved-in-sql-server-reporting-services-to-power-bi"></a>Hogyan helyezhetek át meglévő mentett jelentéseket az SQL Server Reporting Servicesből a Power BI-ba?

Le kell töltenie a jelentést a kiszolgálóról, majd feltöltenie a Power BI-ra a portálról.  Jelenleg nincs elérhető migrálási eszköz, de már tervezzük egy készítését, amint véget ért a nyilvános előzetes verzió időszaka, és elértük a termékek megfelelő funkcióparitását.

### <a name="can-i-open-reports-and-publish-directly-to-the-service"></a>Megnyithatok jelentéseket, majd közzétehetem őket közvetlenül a szolgáltatásban?

Jelenleg nem. A jövőben valószínűleg támogatni fogjuk ezt a funkciót a Jelentéskészítőben, ahogyan már elvégezhető a Power BI Desktopban is.

### <a name="what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi"></a>Az SSRS mely lapszámozott jelentéssekkel kapcsolatos funkciói nem támogatottak még a Power BI-ban?

A lapszámozott jelentések jelenleg a következő elemeket nem támogatják:

- Megosztott adatforrások
- Megosztott adathalmazok
- Segédjelentések
- Átkattintásos és részletezési műveletek
- Csatolt jelentések
- Könyvjelzők
- Bing-térképrétegek
- Egyéni betűtípusok

Ha egy nem támogatott funkcióval rendelkező fájlt próbál meg feltölteni a Power BI szolgáltatásba, hibaüzenetet kap egy átváltás/rendezés elem helyett.

### <a name="what-data-sources-do-you-support-currently-for-paginated-reports"></a>Milyen adatforrásokat támogatnak jelenleg a lapszámozott jelentések?

Az Azure SQL Database, SQL Server és mind az SQL Server Analysis Services (SSAS) táblázatos (DAX) és többdimenziós (MDX) helyszíni átjárót használó modelljeit támogatjuk.

Az SSAS az átjárón keresztül történő megnyitásakor a tárolt hitelesítő adatokhoz tartozó felhasználónak emelt szintű engedélyre lesz szüksége az SSAS-ben az átjárón történő munkához.

### <a name="what-authentication-methods-do-you-support"></a>Milyen hitelesítési módszerek támogatottak?

Jelenleg felhasználónevet és jelszót kell tárolnia az adatforráshoz a portálon vagy az átjárón.  További hitelesítési módszereket, például a sorszintű biztonságot, az előzetes verzió későbbi szakaszaiban teszünk elérhetővé.

### <a name="can-i-use-a-power-bi-dataset-as-a-data-source-for-my-paginated-report"></a>Használhatok Power BI-adatkészletet a lapszámozott jelentés adatforrásaként?

Még nem, de hamarosan erre is lehetőség nyílik.

### <a name="can-i-use-stored-procedures-through-the-gateway"></a>Használhatok tárolt eljárásokat az átjárón keresztül?

Használhat tárolt eljárást az átjárón keresztül, de bizonyos esetekben problémák jelentkezhetnek, ha a tárolt eljárás paraméterekkel rendelkezik.

### <a name="what-export-formats-are-available-for-my-report-in-the-power-bi-service"></a>Milyen exportálási formátumokat használhatok a jelentéshez a Power BI szolgáltatásban?

Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF, .CSV, XML, és MHTML formátumokban exportálhat.

### <a name="can-i-print-paginated-reports"></a>Nyomtathatok lapszámozott jelentéseket?

Igen, nyomtatás is lehetséges a lapszámozott jelentéseknél, és egy új, továbbfejlesztett előnézet is használható. 

### <a name="are-e-mail-subscriptions-available-yet-for-paginated-reports"></a>Léteznek már e-mail-előfizetések a lapszámozott jelentésekhez?

Nem, de hamarosan elérhető lesz az e-mailes előfizetés.

### <a name="what-features-from-ssrs-will-you-be-supporting-in-the-power-bi-service"></a>Milyen SSRS-funkciókat fog támogatni a jövőben a Power BI szolgáltatás?

Tervezzük, hogy a legtöbb forgatókönyvhöz bevezetjük a funkcióparitást, de egyes dolgokat nem érdemes megváltoztatni az SSRS-nél és a Power BI-nál ahhoz, hogy illeszkedjenek a meglévő SSRS-mintákhoz.  Például a Power BI különféle engedélyezési modelljeit nem lehet vissza leképezni az SSRS-re.  Ezeket a döntéseket az ügyfeleink és a partnereink visszajelzései alapján fogjuk meghozni.

### <a name="can-i-run-custom-code-in-my-report"></a>Futtathatok egyéni kódot a jelentésben?

Igen, az SSRS-hez hasonlóan itt is támogatjuk kódok futtatását.

### <a name="does-this-mean-ssrs-is-going-away"></a>Ez azt jelenti, hogy az SSRS megszűnik?

Egyáltalán nem.  Az új ajánlat egy felhőalapú megoldást kínál az ügyfeleknek lapszámozott jelentésekhez.  

### <a name="can-i-use-power-bi-embedded-to-embed-my-paginated-reports-into-an-app-im-hosting"></a>Használhatom a Power BI Embedded szolgáltatást lapszámozott jelentések egy általam üzemeltetett alkalmazásba történő beágyazásához?

Szeretnénk támogatni ezt a forgatókönyvet a meglévő Power BI API-kkal, azonban egyelőre nincs időkeret ennek elérhetőségére.

### <a name="can-i-drill-through-from-a-power-bi-report-to-a-paginated-report"></a>Végezhetek részletezést egy Power BI-jelentésből egy lapszámozott jelentésbe?

Még nem, de a jövőben ezt mindenképp lehetővé tesszük.

### <a name="can-i-share-my-paginated-report-content-through-a-power-bi-app"></a>Megoszthatom a lapszámozott jelentésem tartalmát egy Power BI-alkalmazáson keresztül?

Jelenleg csak a portál Megosztás funkciójával vagy az eszköztár használatával oszthat meg önálló lapszámozott jelentéseket más felhasználókkal. Az alkalmazáson belüli megosztás még nem támogatott, de hamarosan elérhetővé válik. 

### <a name="will-other-report-specific-features-in-power-bi-like-pinning-to-report-tiles-to-dashboards-work-with-paginated-reports"></a>A Power BI más jelentésspecifikus funkciói – például az irányítópultok jelentéscsempéin való rögzítés – is működnek a lapszámozott jelentésekkel?

Terveink szerint a jelentések ugyanazokat a főbb szolgáltatásbeli forgatókönyveket fogják támogatni.  Ideális esetben – ügyfélszempontból – ezeknek ugyanolyan jelentésként kell majd megjelenniük a portálon, még ha a szerkesztésükre szolgáló eszköz más is. Számukra nem fontos, hogyan jött létre a jelentés, amíg a feladatát ellátja.  Ezen funkcióparitás jó példája a megjegyzések támogatásának terve. Bár a funkció kissé eltérő módon működik minden jelentéstípus esetén, mindkettőhöz hozzáfűzhet megjegyzéseket.

### <a name="are-you-planning-to-create-a-new-authoring-tool-for-paginated-reports-in-the-power-bi-service--we-cant-do-everything-we-need-to-with-report-builder-today"></a>Tervben van egy új szerkesztőeszköz lapszámozott jelentések a Power BI szolgáltatáson belüli létrehozásához?  A Jelentéskészítő jelenleg nem képes minden funkciót ellátni.

Jelenleg is dolgozunk különféle lehetőségeken, amelyekkel a legjobb eszközhasználat lesz elérhető a Power BI lapszámozott jelentéseihez. 

### <a name="is-a-migration-tool-planned-so-ssrs-customers-can-move-their-existing-reports-and-assets-to-power-bi"></a>Tervben van egy migrálási eszköz létrehozása, amellyel az SSRS-ügyfelek áthelyezhetik a meglévő jelentéseiket és eszközeiket a Power BI-ba?

Jelenleg vizsgáljuk azokat a lehetőségeket, amelyekkel automatikusan lehet tartalmat áthelyezni a Power BI-ba, de ez csak az általános elérhetőség után esedékes.

### <a name="will-i-ever-be-able-to-create-both-paginated-reports-and-power-bi-reports-in-a-single-authoring-tool"></a>Létrehozhatok a jövőben lapszámozott jelentéseket és Power BI-jelentéseket is egyetlen szerkesztőeszközben?

Valószínűleg.  Jelenleg vizsgáljuk a lehetőségeit egy ilyen megoldásnak, de szeretnénk együtt, BI-csomagként elérhetővé tenni a szerkesztőeszközöket különálló letöltések és márkák helyett.

### <a name="is-there-a-report-viewer-control-for-paginated-reports-in-the-power-bi-service"></a>Létezik jelentésmegjelenítő vezérlőelem a Power BI szolgáltatásban a lapszámozott jelentésekhez?

Nem, jelentésmegjelenítő vezérlőelem jelenleg nem érhető el.

### <a name="can-you-search-for-paginated-reports-from-the-new-home-experience-in-the-power-bi-service"></a>Kereshetek lapszámozott jelentéseket a Power BI szolgáltatás új kezdőlapján?

Nem, a kezdőlapról jelenleg nem kereshet lapszámozott jelentésekre.  Az új kezdőlap egyéb területein azonban láthatja őket.

## <a name="next-steps"></a>Következő lépések

- [A Jelentéskészítő telepítése a Microsoft letöltőközpontból](https://www.microsoft.com/download/details.aspx?id=53613)
- [Oktatóanyag: Lapszámozott jelentés létrehozása](paginated-reports-quickstart-aw.md)
