---
title: Átjáró alkalmazásteljesítmény-figyelés (nyilvános előzetes verzió)
description: Ez a cikk ismerteti, a helyszíni átjáró műveletek teljesítményének monitorozásához.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 05/08/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 8c5f4170383f31ea465ebb7035aebfb53f551982
ms.sourcegitcommit: af2b2238fe77eaa1b2392a19a143a0250b8665cf
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/11/2019
ms.locfileid: "65535367"
---
# <a name="gateway-performance-monitoring-public-preview"></a>Átjáró alkalmazásteljesítmény-figyelés (nyilvános előzetes verzió)

Teljesítmény figyelése, a átjáró rendszergazdái rendelkezik hagyományosan alárendelve, rendszerteljesítmény-számlálók a Windows Teljesítményfigyelő eszköz segítségével manuálisan figyelése. Most már biztosítunk további lekérdezések naplózása és a egy [átjáró teljesítménye PBI-sablonfájl](http://download.microsoft.com/download/D/A/1/DA1FDDB8-6DA8-4F50-B4D0-18019591E182/GatewayPerformanceMonitoring.pbit) jeleníthetik meg az eredményeket. Ez a funkció az átjáró használatának új elemzéseket biztosít, és lehetővé teszi, hogy a lassú lekérdezések.

> [!NOTE]
> Ez a funkció jelenleg csak a szabványos módban a helyszíni adatátjáró és nem a személyes módot.

## <a name="enable-performance-logging"></a>Teljesítménynaplózás engedélyezése

Ez a funkció engedélyezéséhez a következő módosításokat, a *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config* fájlt a "\Program Files\On – helyi adatátjáró" mappa:

1. Frissítés **QueryExecutionReportOn** való _igaz_ az átjáró használatával végrehajtott lekérdezések számára további naplózási beállítások engedélyezéséhez. Ez a beállítás engedélyezésével hoz létre, a lekérdezés-végrehajtási jelentés és a lekérdezés végrehajtási összesítési jelentésfájlt.

   ``` xml
   <setting name="QueryExecutionReportOn" serializeAs="String">
     <value>True</value>
   </setting>
   ```

1. Frissítés **SystemCounterReportOn** való _igaz_ memória és CPU-rendszerszámlálókat további naplózási beállítások engedélyezéséhez. Ezzel a beállítással a rendszer a számláló összesítési jelentésfájl hoz létre.

   ```xml
   <setting name="SystemCounterReportOn" serializeAs="String">
     <value>True</value>
   </setting>
   ```

1. Nincsenek más értékeket szükség szerint frissítheti a konfigurációs fájlban.

    - **ReportFilePath**: Meghatározza, hogy az elérési utat a három naplófájlok tárolására. Alapértelmezés szerint ez az elérési út a "\Users\PBIEgwService\AppData\Local\Microsoft\On-premises adatok gateway\Report" vagy "Windows\ServiceProfiles\PBIEgwService\AppData\Local\Microsoft\On helyszíni adatok gateway\Report", az operációs rendszer verziójától függően. Ha a szolgáltatás fiók használata az átjáró nem _PBIEgwService_, ezen részét cserélje le a szolgáltatás fiók nevét.
    - **ReportFileCount**: Naplófájlok megőrzése minden típusú számát határozza meg. Az alapértelmezett értéke 10.
    - **ReportFileSizeInBytes**: Határozza meg a fenntartani a fájl méretét. Az alapértelmezett érték: 104857600.
    - **QuerExecutionAggregationTimeInMinutes**: Meghatározza, hogy hány perc, amelynek a lekérdezés-végrehajtási információt összesített értéket jelenít meg. Az alapértelmezett érték 5.
    - **SystemCounterAggregationTimeInMinutes**: Meghatározza, hogy hány perc, amelyhez a rendszer számlálók összesített értéket jelenít meg. Az alapértelmezett érték 5.

1. Miután a konfigurációs fájlban végrehajtott módosítások, indítsa újra a e konfigurációs értékek érvénybe léptetéséhez az átjárót. Most kezdi, jelennek meg a megadott helyen létrehozott jelentésfájlt **ReportFilePath**.

    > [!NOTE]
    > Akár 10 percet is igénybe vehet, plusz a beállított idő **QuerExecutionAggregationTimeInMinutes** a fájlok elindítani jelennek meg a mappát a konfigurációs fájlban.

## <a name="understand-performance-logs"></a>Teljesítménynaplók ismertetése

Ha bekapcsolja ezt a szolgáltatást, hogy hozzon létre három új naplófájlokat:

- A lekérdezés-végrehajtási jelentés
- A lekérdezés végrehajtási összesítő jelentés
- A számláló összesítő jelentés

A lekérdezés végrehajtási jelentés részletes lekérdezés végrehajtási információkat tartalmaz. Hogy rögzítése a következő attribútumokat:

|Attribútum |Leírás |
| ---- | ---- |
|**GatewayObjectId** |Az átjáró egyedi azonosítója. |
|**RequestId** |Egy átjáró kérelem egyedi azonosítója. Több lekérdezés esetében azonos lehet. |
|**Adatforrás** |Az adatforrás típusa és az adatforrás tartalmaz. |
|**QueryTrackingId** |A lekérdezés egyedi azonosítója. |  
|**QueryExecutionEndTimeUTC** |Idő, amikor a lekérdezés végrehajtása befejeződött. |
|**QueryExecutionDuration**(ms) |A lekérdezés-végrehajtás időtartama. |
|**QueryType** |Írja be a lekérdezés - példányhoz, lehet, hogy az átadott lekérdezési egy frissítési/DirectQuery Power bi-ban vagy a PowerApps és Microsoft Flow-lekérdezéseket. |
|**DataProcessingEndTimeUTC** |Időpontot, amikor adatok feldolgozása a tevékenységeket, például a sorkezelés, adatok beolvasása, tömörítés, adatfeldolgozási, és így tovább befejeződött. |
|**DataProcessingDuration**(ms) |Időtartama adatfeldolgozási tevékenységeket, például a sorkezelés, adatok beolvasása, tömörítés, adatfeldolgozási és így tovább. |
|**Sikeres** |Azt jelzi, ha a lekérdezés sikeres vagy sikertelen volt. |
|**Hibaüzenet** |A lekérdezés sikertelen, a hibaüzenet jelzi. |
| | |

A lekérdezés végrehajtási összesítő jelentés adott idő alatt szerint összesítve lekérdezés információkat tartalmaz **GatewayObjectId**, **DataSource**, **sikeres**, és **QueryType**. Az alapértelmezett érték 5 perc, de az alább ismertetett módosíthatja. Hogy rögzítése a következő attribútumokat:

|Attribútum |Leírás |
| ---- | ---- |
|**GatewayObjectId** |Az átjáró egyedi azonosítója. |
|**AggregationStartTimeUTC** |Az, amelynek lekérdezés attribútumok lettek összesítve időablak kezdete. |
|**AggregationEndTimeUTC** |Az időtartomány, mely lekérdezés attribútumok lettek összesítve vége. |
|**Adatforrás** |Az adatforrás típusa és az adatforrás tartalmaz. |
|**Sikeres** |Azt jelzi, ha a lekérdezés sikeres vagy sikertelen volt. |
|**AverageQueryExecutionDuration**(ms) |Lekérdezések átlagos végrehajtási idő, az összesítés időtartomány. |
|**MaxQueryExecutionDuration**(ms) |Lekérdezés maximális végrehajtási ideje az összesítési időtartomány. |
|**MinQueryExecutionDuration**(ms) |Az összesítési időszakon minimális lekérdezés végrehajtási ideje. |
|**QueryType** |Írja be a lekérdezés - példányhoz, lehet, hogy az átadott lekérdezési egy frissítési/DirectQuery Power bi-ban vagy a PowerApps és Microsoft Flow-lekérdezéseket. |
|**AverageDataProcessingDuration**(ms) |Átlagos ideje az adatfeldolgozás tevékenységeket, például a sorkezelés, adatok beolvasása, tömörítés, adatfeldolgozási, és így tovább az összesítési időszakon. |
|**MaxDataProcessingDuration**(ms) |Az összesítési időszakon adatfeldolgozási tevékenységek, például a sorkezelés, adatok beolvasása, tömörítés, adatfeldolgozási és így tovább maximális ideje. |
|**MinDataProcessingDuration**(ms) |Az összesítési időszakon adatfeldolgozási tevékenységek, például a sorkezelés, adatok beolvasása, tömörítés, adatfeldolgozási és így tovább minimális ideje. |
|**Száma** |Lekérdezések száma. |
| | |

A számláló összesítő jelentés rendszer számlálók értékeit az adott idő alatt összesített tartalmazza. Az alapértelmezett érték 5 perc, de az alább ismertetett módosíthatja. Hogy rögzítése a következő attribútumokat:

|Attribútum |Leírás |
| ---- | ---- |
|**GatewayObjectId** |Az átjáró egyedi azonosítója. |
|**AggregationStartTimeUTC** |Az időtartomány, amelyhez a rendszer számlálói összesített kezdete. |
|**AggregationEndTimeUTC** |Az időtartomány, mely rendszer számlálók összesített vége. |
|**CounterName** |A rendszer számlálói, például a memória és CPU-használat úgy, hogy az átjáró, az adategyesítési, és összességében a gép által az átjárót üzemeltető. |
|**Max** |A rendszer a számláló az összesítési időtartomány maximális értéke. |
|**Min** |A rendszer a számláló az összesítési időtartomány minimális értéke. |
|**Átlag** |Az összesítési időtartomány a rendszer számláló átlagos értéke. |
| | |

## <a name="visualize-gateway-performance"></a>Jelenítheti meg az átjáró teljesítménye

Most jelenítheti meg az adatokat, amely a rendszernapló fájljaiban.

1. Töltse le a [átjáró teljesítménye PBI sablon](http://download.microsoft.com/download/D/A/1/DA1FDDB8-6DA8-4F50-B4D0-18019591E182/GatewayPerformanceMonitoring.pbit) , és nyissa meg a Power BI desktopban.

1. A megnyíló párbeszédpanelen ellenőrizze, hogy a mappa elérési útjának értéke megegyezik-e **ReportFilePath**.

    ![A mappa elérési útjaként előugró ablak](media/service-gateway-performance-monitoring/gateway-folder-path-pop-up.png)

1. Válassza ki **terhelés**, és a sablonfájlt megkezdi az adatok betöltése a naplófájlokban. Minden Vizualizáció Ezután töltse fel az adatok használata a jelentésekben.

1. Igény szerint mentse a fájlt egy pbix-fájlt, és tegye közzé a szolgáltatáshoz az automatikus frissítések esetén.

Emellett testre szabhatja a sablonfájlt az igényeinek. A Power BI-sablonokat a további információkért lásd: Ez [a Microsoft Power BI blogbejegyzés](https://powerbi.microsoft.com/en-us/blog/deep-dive-into-query-parameters-and-power-bi-templates/).