---
title: Jelentések elkülönítése a modellektől a Power BI Desktopban
description: Útmutató a jelentések modellektől történő elkülönítéséhez a Power BI Desktopban.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/11/2020
ms.author: v-pemyer
ms.openlocfilehash: dad451da460abed65a69990394522f268d7f21cd
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "81525259"
---
# <a name="separate-reports-from-models-in-power-bi-desktop"></a>Jelentések elkülönítése a modellektől a Power BI Desktopban

Új Power BI Desktop-megoldás létrehozásakor az egyik első feladat az adatok lekérése. Az adat beolvasása két különböző kimenetet eredményezhet. Lehet a következő:

- Hozzon létre egy [élő kapcsolatot](../desktop-report-lifecycle-datasets.md) egy már közzétett modellhez, amely lehet egy Power BI-adatkészlet vagy egy távoli üzemeltetésű Analysis Services-modell.
- Megkezdheti egy új modell fejlesztését, amely lehet importálási, DirectQuery- vagy összetett modell.

Ez a cikk a második esettel foglalkozik. Ahhoz nyújt útmutatást, hogy egy jelentést és egy modellt érdemes-e egyetlen Power BI Desktop-fájlban egyesíteni.

## <a name="single-file-solution"></a>Egyfájlos megoldás

Az _egyfájlos megoldás_ akkor működik jól, ha biztosan csak egyetlen olyan jelentés van, amelyik a modellen alapul. Ebben az esetben valószínű, hogy mind a modellt, mind a jelentést ugyanaz a személy hozta létre. Ezt _személyes BI-megoldásnak_ nevezzük, noha a jelentés másokkal is megosztható. Ez a megoldás szerepkör hatókörű jelentéseknél vagy egy üzleti probléma egyszeri értékelésénél fordul elő, és ez sokszor _ad-hoc_ típusú vagy alkalmi jelentésnek is hívjuk.

:::image type="content" source="media/report-separate-from-model/single-file-solution.png" alt-text="Ez az egyetlen fájl egy modellt és egy jelentést tartalmaz, melyeket ugyanaz a személy készített el." border="true":::

## <a name="separate-report-files"></a>Különálló jelentésfájlok

A modell és a jelentés külön Power BI Desktop-fájlokban való elhelyezése a következő esetekben jó megoldás:

- Az adatmodellező és a jelentés szerzője más-más személy.
- A modell várhatóan több jelentés alapja lesz akár most, akár később.

:::image type="content" source="media/report-separate-from-model/separate-report-files.png" alt-text="Három PBIX-fájl fog szerepelni. Az első csak egy modellt tartalmaz. A másik kettő csak jelentéseket tartalmaz, amelyek élő kapcsolattal csatlakoznak a Power BI szolgáltatásban üzemeltetett modellhez. A jelentéseket különböző személyek hozták létre." border="true":::

Az adatmodellezők ekkor is használhatják a Power BI Desktop jelentéskészítési folyamatát a modell kialakításának teszteléséhez és ellenőrzéséhez. Miután azonban közzéteszik a fájlt a Power BI szolgáltatásban, a jelentést el kell távolítaniuk a munkaterületről. Arra is ügyelniük kell, hogy a jelentést minden egyes alkalommal újra el kell távolítaniuk, amikor újra közzéteszik és felülírják az adatkészletet.

### <a name="preserve-the-model-interface"></a>A modell interfészének megőrzése

Időnként a modell változásai elkerülhetetlenek. Ezért az adatmodellezőnek ügyelnie kell arra, hogy a modellinterfész ne sérüljön. Ha az sérül, azzal együtt a jelentések vizualizációi és az irányítópult csempéi is sérülhetnek. A sérült vizualizációk hibaként jelennek meg, és mind a jelentés szerzője, mind a fogyasztók számára rendkívül zavaróak lehetnek. És ami még rosszabb: oda vezethetnek, hogy csökken a bizalom az adatok iránt.

Ezért a változásokat nagyon körültekintően kell kezelni. Ha lehetséges, kerülje az alábbi módosításokat:

- Táblák, oszlopok, hierarchiák, hierarchiaszintek vagy mértékek átnevezése.
- Oszlopok adattípusainak módosítása.
- A mértékkifejezések olyan módosítása, melyek miatt azok más adattípust adnak vissza.
- Mértékek áthelyezése egy másik kezdőlapra. A mértékek áthelyezése ugyanis használhatatlanná teheti a jelentés hatókörű mértékeket, amelyek a kezdőlap táblájában szereplő nevekkel gondoskodnak a mértékek teljes megfelelőségéről. Nem javasoljuk, hogy DAX-kifejezéseket teljes mértékben minősített mértéknevekkel írjon meg. További információt a [DAX: Oszlopok és mértékek hivatkozásai](dax-column-measure-references.md) című témakörben talál.

Táblák, oszlopok, hierarchiák, hierarchiaszintek vagy mértékek hozzáadása biztonságosan végezhető, egy kivétellel: Lehetséges, hogy az új mértéknév ütközik majd egy jelentés hatókörű mértéknévvel. Az ütközés elkerülése érdekében javasoljuk a jelentés szerzőinek, hogy a jelentésekben szereplő mértékek definiálásához dolgozzanak ki egy elnevezési konvenciót. A jelentés hatókörű mértékek nevében használhatnak például előtagként aláhúzást vagy másféle karaktereket is.

Ha mindenképp el kell végeznie egy változást, amely a modell sérüléséhez vezet, az alábbiakat javasoljuk:

- [Tekintse meg a kapcsolódó tartalmakat az adatkészlethez](../consumer/end-user-related.md#view-related-content-for-a-dataset) a Power BI szolgáltatásban.
- Ismerkedjen meg az [Adatéletút](../collaborate-share/service-data-lineage.md) nézettel a Power BI szolgáltatásban.

Mindkét lehetőség lehetővé teszi a kapcsolódó jelentések és irányítópultok gyors azonosítását. Az adatéletút nézet valószínűleg jobb választás, mert azzal egyszerűbben megtalálható az egyes kapcsolódó munkadarabok kapcsolattartója. Ez egy olyan hiperhivatkozás lesz, amely egy e-mailt nyit majd meg a kapcsolattartót címzettként megjelölve.

Javasoljuk, hogy vegye fel a kapcsolatot az egyes kapcsolódó összetevők tulajdonosával, és értesítse őket a sérülést okozó tervezett változásokról. Így felkészülhetnek erre, és könnyebbe tudják majd a jelentéseiket kijavítani és újra közzétenni, amivel a leállási idő is csökken, és kevesebb bosszúsággal jár.

## <a name="next-steps"></a>Következő lépések

Ezzel a cikkel kapcsolatosan a következő forrásanyagokban talál további információt:

- [Kapcsolódás a Power BI szolgáltatásban lévő adathalmazokhoz a Power BI Desktopból](../desktop-report-lifecycle-datasets.md)
- [Kapcsolódó tartalom megtekintése a Power BI szolgáltatásban](../consumer/end-user-related.md)
- [Adatéletút](../collaborate-share/service-data-lineage.md)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
- Javaslatai vannak? [A Power BI javítására vonatkozó ötletek beküldése](https://ideas.powerbi.com/)
