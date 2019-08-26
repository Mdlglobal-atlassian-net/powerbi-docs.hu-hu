---
title: Mik a lapszámozott jelentések a Power BI Premiumban?
description: A lapszámozott jelentések, melyek az SQL Server Reporting Services szabványos jelentéstípusát képviselik már régóta, mostantól elérhetők a Power BI szolgáltatásban. Ezek a jelentések kinyomtathatók vagy megoszthatók. Elrendezésük pontosan vezérelhető. Minden adatot egy táblázatban jelenítenek meg, akkor is, ha az több oldalon keresztül fut.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: overview
ms.date: 06/06/2019
ms.openlocfilehash: 9e4d5285b48739e9f16fbe503736c20cb5524e5d
ms.sourcegitcommit: e62889690073626d92cc73ff5ae26c71011e012e
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/23/2019
ms.locfileid: "69985730"
---
# <a name="what-are-paginated-reports-in-power-bi-premium"></a>Mik a lapszámozott jelentések a Power BI Premiumban?

A lapszámozott jelentések, melyek az SQL Server Reporting Services szabványos jelentéstípusát képviselik már régóta, mostantól elérhetők a Power BI szolgáltatásban. Ezek a jelentések kinyomtathatók vagy megoszthatók. Lapszámozottnak hívjuk őket, mert egy oldalon jól megjeleníthetők. Minden adatot egy táblázatban jelenítenek meg, akkor is, ha az több oldalon keresztül fut. Az oldalak elrendezése pontosan vezérelhető egészen az utolsó pixelig. A lapszámozott jelentések az SQL Server Reporting Services RDL-jelentéseinek technológiáján alapulnak. A Jelentéskészítő a lapszámozott jelentések létrehozásának különálló eszköze. 

A lapszámozott jelentések számos oldalból állhatnak. Ez a jelentés például 563 oldalas. Mindegyik oldal pontosan egy számlát tartalmaz, valamint ismétlődő fejlécekből és élőlábakból áll.

![Lapszámozott](media/paginated-reports-report-builder-power-bi/power-bi-paginated-wwi-report-page.png)

![Lapszámozott jelentés a Power BI szolgáltatásban](media/report-builder-power-bi/report-builder-get-started-paginated-report.png)

A jelentés előnézetét megtekintheti a Jelentéskészítőben, majd közzéteheti a Power BI szolgáltatásban (http://app.powerbi.com ). A szolgáltatásban csak Power BI Pro-licenccel tehet közzé jelentéseket. Lapszámozott jelentéseket a Saját munkaterületen vagy az alkalmazások munkaterületein tehet közzé, ha az adott munkaterület egy Power BI Premium-kapacitáshoz tartozik. Emellett egy Power BI-rendszergazdának engedélyeznie kell a lapszámozott jelentéseket a Power BI felügyeleti portáljának [Premium-kapacitásokkal foglalkozó szakaszában](service-admin-premium-workloads.md#paginated-reports). 

## <a name="create-reports-in-power-bi-report-builder"></a>Jelentések létrehozása a Power BI Jelentéskészítőben

A lapszámozott jelentésekhez saját eszköz tartozik: a Power BI Jelentéskészítő. Ez egy új eszköz amely ugyanazon eszközök alapjaira épül, mint amelyekkel a Power BI jelentéskészítő kiszolgálóhoz vagy az SQL Server Reporting Serviceshez (SSRS) hozott létre lapszámozott jelentéseket. Sőt az SSRS 2016-os és 2017-es verziójában vagy a helyszíni Power BI jelentéskészítő kiszolgálóban létrehozott lapszámozott jelentések kompatibilisek a Power BI szolgáltatással. A Power BI szolgáltatás megtartja az előző verziókkal való kompatibilitást, így a jelentésekhez új verziót használhat, és frissítheti a korábbi lapszámozott jelentéseket is. Megjelenéskor nem minden jelentésfunkció érhető el. Részletekért tekintse meg a cikk [Korlátozások és szempontok](#limitations-and-considerations) című szakaszát.
     
## <a name="report-from-a-variety-of-data-sources"></a>Számos adatforrásból készített jelentés

Egy lapszámozott jelentés több különböző adatforrással is rendelkezhet. A Power BI-jelentésekkel ellentétben nem tartozik hozzá mögöttes adatmodell. A lapszámozott jelentések első Power BI-os megjelenésekor Ön beágyazott adatforrásokat és adathalmazokat hoz létre magában a jelentésben. Egyelőre nem használhat megosztott adatforrásokat vagy megosztott adatkészleteket. A jelentéseket a Jelentéskészítőben, a helyi számítógépen hozza létre. Ha egy jelentés helyszíni adatokhoz kapcsolódik, a jelentés a Power BI szolgáltatásba való feltöltése után létre kell hoznia egy átjárót, majd átirányítani az adatkapcsolatot. Jelenleg a következő adatforrásokhoz csatlakozhat:

- Azure SQL Database és Data Warehouse
- Azure Analysis Services (SSO-val)
- SQL Server egy átjárón keresztül
- SQL Server Analysis Services egy átjárón keresztül
- Power BI Premium-adatkészletek
- Oracle
- Teradata
- További adatforrások a hozzáadás után

## <a name="design-your-report"></a>A jelentés megtervezése  

### <a name="create-paginated-reports-with-matrix-chart-and-free-form-layouts"></a>Lapszámozott jelentések létrehozása mátrixszal, diagrammal és szabad formátumú elrendezéssel

A táblázatos jelentések jól alkalmazhatók oszlopalapú adatok esetén. Az olyan mátrixjelentések, mint a lapközi vagy PivotTable-jelentések összegzett adatokhoz alkalmasak. A diagram jellegű jelentések grafikus formában mutatják be az adatokat, a kötetlen formájú *lista* jelentések pedig szinte bármi más, például számlák bemutatására is használhatók. 
  
Az első lépést a Jelentéskészítő egyik varázslójában teheti meg. A táblázat, mátrix és diagram varázslói lépésenként bemutatják a beágyazott adatforrás-kapcsolat és adathalmaz létrehozását. Ezután mezők húzásával létrehozhat egy adathalmaz-lekérdezést, kiválaszthat egy elrendezést és stílust, valamint testreszabhatja a jelentést.  
  
A Térkép varázslóval olyan jelentéseket készíthet, amelyek összesített adatokat jelenítenek meg egy földrajzi vagy geometriai háttér előtt. A térképadatok lehetnek egy Transact-SQL-lekérdezés térbeli adatai vagy Shapefile formátumú Environmental Systems Research Institute, Inc. (ESRI-) adatok. Emellett egy Microsoft Bingből származó térképcsempét is beállíthat háttérnek.  

### <a name="add-more-to-your-report"></a>További elemek hozzáadása a jelentéshez

Az adatait módosíthatja az adatok szűrésével, csoportosításával vagy rendezésével, illetve képletek és kifejezések hozzáadásával. Az adatok vizuális összegzéséhez diagramokat, mérőműszereket, értékgörbéket és kijelzőket adhat hozzá.  Paraméterekkel és szűrőkkel egyéni nézetek szerint szűrheti az adatokat. Beágyazhat és hivatkozhat képeket és egyéb erőforrásokat, így külső tartalmat is.  

A lapszámozott jelentések minden eleme – a jelentéstől kezdve a szövegmezőn, a képen és a táblázaton át a diagramig – számos olyan tulajdonsággal rendelkezik, amellyel Ön testreszabhatja a jelentést.

## <a name="creating-a-report-definition"></a>Jelentésdefiníció létrehozása

Lapszámozott jelentés tervezésekor valójában egy *jelentésdefiníciót készít*. Ez nem tartalmazza az adatokat. Az adatok lekérésének helyét, a lekérendő adatokat és azok megjelenítési módját szabja meg. A jelentés futtatásakor a jelentésfeldolgozó a megadott jelentésdefiníció és a lekért adatok a jelentés elrendezésének egyesítésével létrehozza a jelentést. A jelentésdefiníciót Ön ezután feltölti a Power BI szolgáltatásba (http://app.powerbi.com ), vagy a Saját munkaterületre, vagy egy munkatársakkal megosztott munkaterületre. Ha a jelentés adatforrása helyszíni, a jelentés feltöltése után az adatforrás kapcsolatát átirányítja egy átjárón. 

## <a name="view-your-paginated-report"></a>A lapszámozott jelentés megtekintése
A lapszámozott jelentést a böngészős Power BI szolgáltatásban és a Power BI mobilalkalmazásokban is megtekintheti. A Power BI szolgáltatásból exportálhatja a jelentést több formátumban, így például HTML, MHTML, PDF, XML, CSV, TIFF, Word és Excel formátumokban. Emellett megoszthatja másokkal.  

## <a name="create-a-subscription-to-your-report"></a>Felratkozás létrehozása a jelentéshez

Most már beállíthat lapszámozott jelentésekre vonatkozó e-mailes feliratkozásokat saját maga és mások számára a Power BI szolgáltatásban. A folyamat általánosságban ugyanaz, mint a Power BI szolgáltatás jelentéseire és irányítópultjaira való feliratkozás esetében. Feliratkozás beállításakor kiválaszthatja, hogy milyen gyakorisággal szeretné fogadni az e-maileket: naponta, hetente vagy óránként. A feliratkozás tartalmaz egy, a teljes jelentés eredményeit összesítő PDF-et is.

További információ: [Feliratkozás és mások feliratkoztatása lapszámozott jelentésre a Power BI szolgáltatásban](paginated-reports-subscriptions.md). 

## <a name="limitations-and-considerations"></a>Korlátozások és szempontok

Íme néhány funkció, amely nem támogatott az első megjelenéskor:

- Jelentésoldalak és vizualizációk rögzítése a Power BI irányítópultjain. Továbbra is rögzíthet vizualizációkat Power BI-irányítópultokra helyszíni lapszámozott jelentésből egy Power BI, vagy Reporting Services jelentéskészítő kiszolgálón. További információ: [Reporting Services-elemek rögzítése Power BI-irányítópultokra](https://docs.microsoft.com/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards).
- Interaktív funkciók, például dokumentumtérképek és Megjelenítés/elrejtés gombok.
- Segédjelentések és részletezések.
- Megosztott adatforrások és a megosztott adathalmazok.
- Power BI-jelentések vizualizációi.
 
## <a name="next-steps"></a>Következő lépések

- [A Power BI Jelentéskészítő telepítése a Microsoft letöltőközpontból](https://go.microsoft.com/fwlink/?linkid=2086513)
- [Oktatóanyag: Lapszámozott jelentés létrehozása](paginated-reports-quickstart-aw.md)
- [Adatok megadása közvetlenül többoldalas jelentésben](paginated-reports-enter-data.md)

  

