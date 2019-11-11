---
title: A Power BI jelentéskészítő kiszolgáló kapacitástervezési útmutatója
description: Ez a dokumentum a Power BI jelentéskészítő kiszolgáló kapacitástervezési útmutatóját tartalmazza, és különböző számítási feladatok terhelési tesztjeinek végrehajtási eredményeit ismerteti.
author: parthsha
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 3/5/2018
ms.author: pashah
ms.openlocfilehash: c286e921c47b46c20cd73d4b32146093adc74d7f
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73860125"
---
# <a name="capacity-planning-guidance-for-power-bi-report-server"></a>A Power BI jelentéskészítő kiszolgáló kapacitástervezési útmutatója
A Power BI jelentéskészítő kiszolgáló olyan önkiszolgáló BI és céges jelentéskészítő megoldás, amelyet az ügyfelek helyben telepíthetnek a saját tűzfal mögé. A Power BI Desktop interaktív jelentéskészítő képességét kombinálja az SQL Server Reporting Services helyi kiszolgálói platformjával. Az elemzések és a jelentések gyakori és növekvő céges használatának köszönhetően a hardveres infrastruktúrák és a vállalati felhasználói bázis skálázásához szükséges szoftverlicencek költségbecslése kihívást jelenthet. A jelen dokumentum célja, hogy útmutatást nyújtson a Power BI jelentéskészítő kiszolgálójának kapacitástervezéséhez, és megossza a jelentéskészítő kiszolgáló különböző számítási feladataihoz tartozó terhelési tesztek végrehajtási eredményeit. Bár a cégek jelentései, lekérdezései és használati mintái eltérőek lehetnek, a jelen dokumentumban ismertetett eredmények – a ténylegesen használt tesztekkel és azok végrehajtásának részletes bemutatásával – hivatkozási pontként szolgálnak bárkinek, aki a Power BI jelentéskészítő kiszolgáló üzembe helyezésének korai tervezési szakaszában van.

## <a name="executive-summary"></a>Vezetői összefoglaló
Két különböző típusú számítási feladatot hajtottunk végre a Power BI jelentéskészítő kiszolgáló használatával; mindkét számítási feladat különböző típusú jelentések megjelenítéséből, valamint különböző webportálos műveletek végrehajtásából állt. 

* A „Power BI-jelentés (nagy erőforrásigényű)” számítási feladatban a leggyakrabban végrehajtott művelet (azaz az időszak 60%-ában végrehajtott művelet) a Power BI-jelentések megjelenítése volt.
* A „Többoldalas jelentés (nagy erőforrásigényű)” számítási feladatban a leggyakrabban végrehajtott művelet a többoldalas jelentések megjelenítése volt.

A Power BI jelentéskészítő kiszolgáló topológiáján alapulva, valamint azt feltételezve, hogy a felhasználók legfeljebb 5%-a fér hozzá egyszerre a jelentéskészítő kiszolgálóhoz, az alábbi táblázat azoknak a felhasználóknak a maximális számát tartalmazza, akiket a Power BI jelentéskészítő kiszolgáló legalább 99%-os megbízhatósággal kezelni tud. 

| Számítási feladat | 8 mag, 32 GB RAM | 16 mag, 64 GB RAM |
| --- | --- | --- |
| **Power BI-jelentés (nagy erőforrásigényű)** (>60%) |1000 felhasználó |3000 felhasználó |
| **Többoldalas jelentés (nagy erőforrásigényű)** (>60%) |2000 felhasználó |3200 felhasználó |

Mindegyik körben a leginkább kihasznált erőforrás a CPU volt. Ezért a Power BI jelentéskészítő kiszolgáló magjainak számának növelésével jobb eredmény érhető el a rendszer megbízhatóságát tekintve, legalábbis a memória vagy a merevlemez-terület növeléséhez képest. 

## <a name="test-methodology"></a>Tesztelési módszer
A használt tesztelési topológia a szállítóspecifikus fizikai hardver helyett a Microsoft Azure Virtual Machines használatán alapult. Minden gép üzemeltetése egyesült államokbeli régiókban történt. Ez a helyi és a nyilvános felhőbeli hardvervirtualizálások általános trendjét tükrözi. 

### <a name="power-bi-report-server-topology"></a>A Power BI jelentéskészítő kiszolgáló topológiája
A Power BI jelentéskészítő kiszolgáló üzemelő példánya az alábbi virtuális gépekből állt:

* Active Directory-tartományvezérlő: az SQL Server adatbázismotor, az SQL Server Analysis Services és a Power BI jelentéskészítő kiszolgáló igényelte ezt az összes kérés biztonságos hitelesítéséhez.
* SQL Server adatbázismotor és SQL Server Analysis Services: itt tároltuk a jelentések megjelenítésekor használt összes adatbázist.
* Power BI jelentéskészítő kiszolgáló
* A Power BI jelentéskészítő kiszolgáló adatbázisa. A jelentéskészítő kiszolgáló adatbázisa a Power BI jelentéskészítő kiszolgálótól eltérő gépen található, így annak nem kell osztoznia az SQL Server adatbázismotorral a memórián, a CPU-n, a hálózaton és a lemezerőforrásokon.

![](media/capacity-planning/report-server-topology.png)

A topológiában használt egyes virtuális gépek átfogó konfigurálásával kapcsolatban lásd: 1.1. függelék – A Power BI jelentéskészítő kiszolgáló topológiája és 1.2. függelék – A Power BI jelentéskészítő kiszolgáló virtuálisgép-konfigurációja.

### <a name="tests"></a>Tesztek
A terhelési műveletekben használt tesztek nyilvánosan elérhetők a [Reporting Services LoadTest](https://github.com/Microsoft/Reporting-Services-LoadTest) nevű GitHub-projektben. Ez az eszköz lehetővé teszi a felhasználóknak az SQL Server Reporting Services és a Power BI jelentéskészítő kiszolgáló teljesítményre, megbízhatóságra, skálázhatóságra és helyreállíthatósági jellemzőkre vonatkozó adatainak tanulmányozását. A projekt négy csoportba tartozó teszteseteket tartalmaz:

* Power BI-jelentések megjelenítését szimuláló tesztek.
* Mobiljelentések megjelenítését szimuláló tesztek.
* Kicsi és nagy, többoldalas jelentések megjelenítését szimuláló tesztek. 
* Különböző típusú webportálos műveletek végrehajtását szimuláló tesztek. 

Minden tesztet úgy írtak meg, hogy alkalmas legyen teljes körű műveletek végrehajtására (jelentések megjelenítése, új adatforrások létrehozása stb.). Mindez legalább egy webkérés jelentéskészítő kiszolgálónak való elküldésével valósul meg (API-kon keresztül). A valós életben a felhasználónak néhány köztes műveletet is el kellhet végeznie az ilyen teljes körű műveletek végrehajtásakor. Például egy jelentés megjelenítéséhez a felhasználónak meg kell nyitnia a webportált és a jelentést tartalmazó mappát, majd a jelentésre kattintva kell megjelenítenie azt. Bár a tesztek nem tartalmazzák a teljes körű feladatok végrehajtásához szükséges összes műveletet, jól szimulálják a Power BI jelentéskészítő kiszolgálót érő terhelés nagy részét. A GitHub-projekt tanulmányozásával megismerheti a felhasznált jelentések különböző típusait, valamint az elvégzett különböző műveleteket.

### <a name="workloads"></a>Számítási feladatok
A teszteléshez két számítási profil használható: Power BI-jelentés (nagy erőforrásigényű) és lapszámozott jelentés (nagy erőforrásigényű). Az alábbi táblázat a jelentéskészítő kiszolgálón végrehajtott kérések eloszlását ismerteti.

| Tevékenység | Power BI-jelentés (nagy erőforrásigényű), előfordulás gyakorisága | Többoldalas jelentés (nagy erőforrásigényű), előfordulás gyakorisága |
| --- | --- | --- |
| **Power BI-jelentések megjelenítése** |60% |10% |
| **Többoldalas jelentések megjelenítése** |30% |60% |
| **Mobiljelentések megjelenítése** |5% |20% |
| **Webportálos műveletek** |5% |10% |

### <a name="user-load"></a>Felhasználói terhelés
Minden egyes tesztfuttatás során a végrehajtott tesztek a két számítási feladatban meghatározott gyakoriságon alapultak. A tesztek 20 egyidejű felhasználó jelentéskészítő kiszolgálónak küldött kérésével indultak. A rendszer ezután fokozatosan emelte a felhasználói terhelést, amíg a megbízhatóság a 99%-os célérték alá nem csökkent.

## <a name="results"></a>Eredmények
### <a name="concurrent-user-capacity"></a>Egyidejű felhasználói kapacitás
Ahogyan korábban hangsúlyoztuk, a tesztek 20 egyidejű felhasználó jelentéskészítő kiszolgálónak küldött kérésével indultak. Az egyidejű felhasználók számát a rendszer ezután fokozatosan növelte az összes kérés 1%-ának sikertelen végrehajtásáig. Az alábbi táblázatban lévő eredmények az egyidejű felhasználói kérések azon mennyiségét mutatják, amelyet a kiszolgáló csúcsterhelés alatt legfeljebb 1%-os hibaaránnyal kezelni tud.

| Számítási feladat | 8 mag, 32 GB RAM | 16 mag, 64 GB RAM |
| --- | --- | --- |
| **Power BI-jelentés (nagy erőforrásigényű)** |50 egyidejű felhasználó |150 egyidejű felhasználó |
| **Többoldalas jelentés (nagy erőforrásigényű)** |100 egyidejű felhasználó |160 egyidejű felhasználó |

### <a name="total-user-capacity"></a>Teljes felhasználói kapacitás
A Microsoftnál több csoport használja éles környezetben a Power BI jelentéskészítő kiszolgálót. A környezet tényleges használatának elemzéseikor azt figyeltük meg, hogy az egy adott időpontban egyidejű felhasználók száma (akár a napi csúcsterhelés során is) általában nem haladja meg a teljes felhasználói bázis 5%-át. Az 5%-os egyidejűségi arányt alapként használva extrapoláltuk azt a teljes felhasználói bázist, amelyet a Power BI jelentéskészítő kiszolgáló 99%-os megbízhatósággal kezelni tud.

| Számítási feladat | 8 mag, 32 GB RAM | 16 mag, 64 GB RAM |
| --- | --- | --- |
| **Power BI-jelentés (nagy erőforrásigényű)** |1000 felhasználó |3000 felhasználó |
| **Többoldalas jelentés (nagy erőforrásigényű)** |2000 felhasználó |3200 felhasználó |

### <a name="view-results"></a>Az eredmények megtekintése
A jelentés kiválasztásával tekintheti meg a terhelési teszt eredményeit.

| Számítási feladat | 8 mag, 32 GB RAM | 16 mag, 64 GB RAM |
| --- | --- | --- |
| **Power BI-jelentés (nagy erőforrásigényű)** |[Megtekintés – 8 mag](https://msit.powerbi.com/view?r=eyJrIjoiMDhhNGY4NGQtNGRhYy00Yzk4LTk2MzAtYzFlNWI5NjBkMGFiIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9) |[Megtekintés – 16 mag](https://msit.powerbi.com/view?r=eyJrIjoiNDBiODk1OGUtYTAyOC00MzVhLThmZmYtNzVjNTFjNzMwYzkwIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9) |
| **Többoldalas jelentés (nagy erőforrásigényű)** |[Megtekintés – 8 mag](https://msit.powerbi.com/view?r=eyJrIjoiNDFiZWYzMTktZGIxNS00MzcwLThjODQtMmJkMGRiZWEzNjhlIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9) |[Megtekintés – 16 mag](https://msit.powerbi.com/view?r=eyJrIjoiOTU0YjJkYTgtNDg4Yy00NzlhLWIwMGYtMzg4YWI2MjNmOTZjIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9) |

<iframe width="640" height="360" src="https://msit.powerbi.com/view?r=eyJrIjoiMDhhNGY4NGQtNGRhYy00Yzk4LTk2MzAtYzFlNWI5NjBkMGFiIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9" frameborder="0" allowFullScreen="true"></iframe>

<iframe width="640" height="360" src="https://msit.powerbi.com/view?r=eyJrIjoiNDBiODk1OGUtYTAyOC00MzVhLThmZmYtNzVjNTFjNzMwYzkwIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9" frameborder="0" allowFullScreen="true"></iframe>

<iframe width="640" height="360" src="https://msit.powerbi.com/view?r=eyJrIjoiNDFiZWYzMTktZGIxNS00MzcwLThjODQtMmJkMGRiZWEzNjhlIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9" frameborder="0" allowFullScreen="true"></iframe>

<iframe width="640" height="360" src="https://msit.powerbi.com/view?r=eyJrIjoiOTU0YjJkYTgtNDg4Yy00NzlhLWIwMGYtMzg4YWI2MjNmOTZjIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9" frameborder="0" allowFullScreen="true"></iframe>

## <a name="summary"></a>Összegzés
A futtatott terheléstesztekben a CPU volt a leginkább kihasznált erőforrás a Power BI jelentéskészítő kiszolgálót üzemeltető gép csúcsterhelésekor. Ezért az erőforrások közül először a magok számát érdemes növelni. Alternatív megoldásként fontolóra vehető a szolgáltatás kiterjesztése további, Power BI jelentéskészítő kiszolgálót üzemeltető kiszolgálók topológiába való felvételével.

A jelen dokumentumban ismertetett eredmények adott adatkészletet használó adott jelentések adott módon ismételt végrehajtásából származnak. Hasznos hivatkozási pontként szolgálnak, de vegye figyelembe, hogy a használat függ a jelentésektől, a lekérdezésektől, a használati mintáktól és a Power BI jelentéskészítő kiszolgáló üzemelő példányától is.

## <a name="appendix"></a>Függelék
### <a name="1-topology"></a>1\. Topológia
**1.1. A Power BI jelentéskészítő kiszolgáló topológiája**

Annak céljából, hogy a különböző konfigurációkban kizárólag a Power BI jelentéskészítő kiszolgáló viselkedését tudjuk vizsgálni, az egyes típusú gépek VM-konfigurációja rögzített volt (kivéve a Power BI jelentéskészítő kiszolgálót üzemeltető gépet). Mindegyik gép üzembe helyezése a második generációs (v2), Premium Storage-lemezekkel felszerelt, D sorozatú gépeknek megfelelően történt. Az egyes virtuálisgép-méretekről részletes információkat találhat a https://azure.microsoft.com/pricing/details/virtual-machines/windows/ weblap általános célú felhasználást ismertető szakaszában.

| Virtuális gép típusa | Processzor | Memória | Azure-beli virtuális gép mérete |
| --- | --- | --- | --- |
| **Active Directory-tartományvezérlő** |2 mag |7 GB |Standard_DS2_v2 |
| **SQL Server adatbázismotor és Analysis Services** |16 mag |56 GB |Standard_DS5_v2 |
| **A jelentéskészítő kiszolgáló adatbázisa** |16 mag |56 GB |Standard_DS5_v2 |

**1.2. A Power BI jelentéskészítő kiszolgáló virtuálisgép-konfigurációja** 

Különböző konfigurációjú processzorokat és memóriát használtunk a Power BI jelentéskészítő kiszolgálót üzemeltető virtuális gépen. A többi virtuális géptől eltérően ennek a gépnek az üzembe helyezése a harmadik generációs (v3), Premium Storage-lemezekkel felszerelt, D sorozatú gépeknek megfelelően történt. Erről a virtuálisgép-méretről részletes információkat találhat a https://azure.microsoft.com/pricing/details/virtual-machines/windows/ weblap általános célú felhasználást ismertető szakaszában.

| Virtuális gép | Processzor | Memória | Azure-beli virtuális gép mérete |
| --- | --- | --- | --- |
| **Power BI jelentéskészítő kiszolgáló (kicsi)** |8 mag |32 GB |Standard_D8S_v3 |
| **Power BI jelentéskészítő kiszolgáló (nagy)** |16 mag |64 GB |vStandard_D16S_v3 |

### <a name="2-run-the-loadtest-tool"></a>2\. A LoadTest eszköz futtatása
Ha szeretné futtatni a Reporting Services LoadTest eszközt a saját vagy egy Microsoft Azure-beli Power BI jelentéskészítő kiszolgálón, kövesse az alábbi lépéseket.

1. Klónozza a Reporting Services LoadTest nevű projektet a GitHubon (https://github.com/Microsoft/Reporting-Services-LoadTest) ).
2. A projekt könyvtárában található egy RSLoadTests.sln nevű megoldásfájl. Nyissa meg ezt a fájlt a Visual Studio 2015-ös vagy újabb verziójában.
3. Döntse el, hogy az eszközt a Power BI jelentéskészítő kiszolgáló saját üzemelő példányán vagy egy Microsoft Azure-beli Power BI jelentéskészítő kiszolgálón kívánja-e futtatni. Ha saját üzemelő példányon szeretné futtatni, ugorjon az 5. lépésre.
4. Hozzon létre egy Power BI jelentéskészítő kiszolgálói környezetet az Azure-ban a https://github.com/Microsoft/Reporting-Services-LoadTest#create-a-sql-server-reporting-services-load-environment-in-azure lap utasításait követve.
5. Miután végzett a környezet üzembe helyezésével, kövesse a https://github.com/Microsoft/Reporting-Services-LoadTest#load-test-execution weblapon található utasításokat a tesztek futtatásához.

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)


