---
title: Mik a lapszámozott jelentések a Power BI Premiumban? (Előzetes verzió)
description: A lapszámozott jelentések nyomtathatók és megoszthatók. Elrendezésük pontosan vezérelhető. Minden adatot egy táblázatban jelenítenek meg, akkor is, ha az több oldalon keresztül fut.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: report-builder
ms.topic: overview
ms.date: 11/08/2018
ms.author: maggies
ms.openlocfilehash: 15ec21a0b86977173c16071980d7527f27db74ef
ms.sourcegitcommit: 5eb0f37f59b5fec15c0caecbbd1f8d688c7f0013
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2018
ms.locfileid: "51297044"
---
# <a name="what-are-paginated-reports-in-power-bi-premium-preview"></a>Mik a lapszámozott jelentések a Power BI Premiumban? (Előzetes verzió)
A lapszámozott jelentések, melyek az SQL Server Reporting Services szabványos jelentéstípusát képviselik már régóta, mostantól elérhetők a Power BI szolgáltatásban. A lapszámozott jelentések nyomtatáshoz és megosztáshoz lettek kialakítva. Nevük arra utal, hogy oldalakra osztáshoz lettek formázva, és minden adatot egy táblázatban jelenítenek meg, akkor is, ha az több oldalon keresztül fut. Az oldalak elrendezése pontosan vezérelhető egészen az utolsó pixelig. A lapszámozott jelentések az SQL Server Reporting Services RDL-jelentéseinek technológiáján alapulnak. A Jelentéskészítő a lapszámozott jelentések létrehozásának különálló eszköze. 

A lapszámozott jelentések számos oldalból állhatnak. Az alábbi példában a jelentés 563 oldalból áll, amelyek mindegyike pontosan egy számlát tartalmaz, valamint ismétlődő fejlécekből és élőlábakból áll.

![Lapszámozott jelentés a Power BI szolgáltatásban](media/paginated-reports-report-builder-power-bi/power-bi-paginated-wwi-report-page.png)

A jelentés előnézetét megtekintheti a Jelentéskészítőben, majd közzéteheti a Power BI szolgáltatásban (http://app.powerbi.com). A szolgáltatásban csak Power BI Pro-licenccel tehet közzé jelentéseket. Lapszámozott jelentéseket a Saját munkaterületen vagy az alkalmazások munkaterületein tehet közzé, ha az adott munkaterület egy Power BI Premium-kapacitáshoz tartozik. Emellett egy Power BI-rendszergazdának engedélyeznie kell a lapszámozott jelentéseket a Power BI felügyeleti portálján. További információ a [számítási feladatok konfigurálásáról](service-admin-premium-manage.md#configure-workloads). 

## <a name="create-reports-in-report-builder"></a>Jelentés létrehozása a Jelentéskészítőben

A lapszámozott jelentésekhez saját eszköz tartozik: a Jelentéskészítő. Ha a Power BI jelentéskészítő kiszolgálóhoz vagy az SQL Server Reporting Serviceshez (SSRS) hozott létre lapszámozott jelentéseket, ugyanazt az eszközt és eszközverziót használhatja. Sőt az SSRS 2016-os és 2017-es verziójában vagy a helyszíni Power BI jelentéskészítő kiszolgálóban létrehozott lapszámozott jelentések kompatibilisek a Power BI szolgáltatással. A Power BI szolgáltatás megtartja az előző verziókkal való kompatibilitást, így a jelentésekhez új verziót használhat, és frissítheti a korábbi lapszámozott jelentéseket is. A megjelenéskor nem minden jelentésfunkció lesz elérhető, részletekért tekintse meg a [Korlátozások és szempontok](#limitations-and-considerations) című témakört.
     
## <a name="report-from-a-variety-of-data-sources"></a>Számos adatforrásból készített jelentés

Egy lapszámozott jelentés több különböző adatforrással is rendelkezhet. A Power BI-jelentésekkel ellentétben nem tartozik hozzá mögöttes adatmodell. A lapszámozott jelentések első Power BI-os megjelenésekor beágyazott adatforrásokat és adathalmazokat hoz létre magában a jelentésben ahelyett, hogy megosztott adatforrásokhoz vagy adathalmazokhoz csatlakozna a kiszolgálón. A jelentéseket a Jelentéskészítőben, a helyi számítógépen hozza létre. Ha egy jelentés helyszíni adatokhoz kapcsolódik, a jelentés a Power BI szolgáltatásba való feltöltése után létre kell hoznia egy átjárót, majd átirányítani az adatkapcsolatot. Az első kiadásban a következő adatforrásokhoz csatlakozhat:

- Azure SQL Database és Data Warehouse
- SQL Server egy átjárón keresztül
- SQL Server Analysis Services egy átjárón keresztül
 
Az előzetes verziós időszakban további adatforrásokat adunk hozzá.

## <a name="design-your-report"></a>A jelentés megtervezése  

### <a name="create-paginated-reports-with-matrix-chart-and-free-form-layouts"></a>Lapszámozott jelentések létrehozása mátrixszal, diagrammal és szabad formátumú elrendezéssel

Létrehozhat táblázatos jelentéseket oszlopalapú adatokhoz, mátrixjelentéseket (például kereszttáblás jelentéseket vagy kimutatásokat) összesített adatokhoz, valamint szabad formátumú *listajelentéseket* minden máshoz, például számlákhoz. 
  
Az első lépést a Jelentéskészítő egyik varázslójában teheti meg. A táblázat, mátrix és diagram varázslói lépésenként bemutatják a beágyazott adatforrás-kapcsolat és adathalmaz létrehozását. Ezután mezők húzásával létrehozhat egy adathalmaz-lekérdezést, kiválaszthat egy elrendezést és stílust, valamint testreszabhatja a jelentést.  
  
A Térkép varázslóval olyan jelentéseket készíthet, amelyek összesített adatokat jelenítenek meg egy földrajzi vagy geometriai háttér előtt. A térképadatok lehetnek egy Transact-SQL-lekérdezés térbeli adatai vagy Shapefile formátumú Environmental Systems Research Institute, Inc. (ESRI-) adatok. Emellett egy Microsoft Bingből származó térképcsempét is beállíthat háttérnek.  

### <a name="add-more-to-your-report"></a>További elemek hozzáadása a jelentéshez

Az adatait módosíthatja az adatok szűrésével, csoportosításával vagy rendezésével, illetve képletek és kifejezések hozzáadásával. Az adatok vizuális összegzéséhez diagramokat, mérőműszereket, értékgörbéket és kijelzőket adhat hozzá.  Paraméterekkel és szűrőkkel egyéni nézetek szerint szűrheti az adatokat. Beágyazhat és hivatkozhat képeket és egyéb erőforrásokat, így külső tartalmat is.  

A lapszámozott jelentések minden eleme – a jelentéstől kezdve a szövegmezőn, a képen és a táblázaton át a diagramig – számos olyan tulajdonsággal rendelkezik, amellyel Ön testreszabhatja a jelentést.

## <a name="creating-a-report-definition"></a>Jelentésdefiníció létrehozása

Lapszámozott jelentés tervezésekor valójában egy *jelentésdefiníciót készít*. Ez nem tartalmazza az adatokat. Az adatok lekérésének helyét, a lekérendő adatokat és azok megjelenítési módját szabja meg. A jelentés futtatásakor a jelentésfeldolgozó a megadott jelentésdefiníció és a lekért adatok a jelentés elrendezésének egyesítésével létrehozza a jelentést. A jelentésdefiníciót Ön ezután feltölti a Power BI szolgáltatásba (http://app.powerbi.com), vagy a Saját munkaterületre, vagy egy munkatársakkal megosztott munkaterületre. Ha a jelentés adatforrása helyszíni, a jelentés feltöltése után az adatforrás kapcsolatát átirányítja egy átjárón. 

## <a name="view-your-paginated-report"></a>A lapszámozott jelentés megtekintése
A lapszámozott jelentést a böngészős Power BI szolgáltatásban és a Power BI mobilalkalmazásokban is megtekintheti. A Power BI szolgáltatásban exportálhatja a jelentést több webes, lapalapú és asztali alkalmazásformátumban, így például HTML, MHTML, PDF, XML, CSV, TIFF, Word és Excel formátumokban. Emellett megoszthatja másokkal.  
  
## <a name="limitations-and-considerations"></a>Korlátozások és szempontok

Íme néhány funkció, amely nem támogatott az első megjelenéskor:

- Jelentésoldalak és vizualizációk rögzítése a Power BI irányítópultjain.
- Interaktív funkciók, például dokumentumtérképek és Megjelenítés/elrejtés gombok.
- Segédjelentések és részletezések.
- Előfizetések.
- Megosztott adatforrások és a megosztott adathalmazok.
- Power BI-adathalmazok.
- Power BI-jelentések vizualizációi.
- Lapszámozott jelentések az alkalmazásokban. Az alkalmazás-munkaterületek lapszámozott jelentéseit megoszthatja, azonban nem foglalhatja bele az alkalmazásba annak munkaterületről történő közzétételekor.
 
## <a name="next-steps"></a>Következő lépések

- [A Jelentéskészítő telepítése a Microsoft letöltőközpontból](http://go.microsoft.com/fwlink/?LinkID=734968)

- [Oktatóanyag: Többoldalas jelentés készítése](paginated-reports-quickstart-aw.md)
  

