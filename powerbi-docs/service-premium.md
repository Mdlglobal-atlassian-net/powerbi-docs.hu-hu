---
title: Mi az a Microsoft Power BI Premium?
description: A Power BI Premium dedikált kapacitást biztosít cége vagy csapata számára, így felhasználónkénti licencek vásárlása nélkül is megbízható teljesítményre számíthat nagyobb mennyiségű adat estén is.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/12/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: f327cb95c10756f079778d20e62cba4871b95c02
ms.sourcegitcommit: ac63b08a4085de35e1968fa90f2f49ea001b50c5
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/18/2019
ms.locfileid: "57964939"
---
# <a name="what-is-microsoft-power-bi-premium"></a>Mi az a Microsoft Power BI Premium?

> [!NOTE]
> Ezt a cikket jelenleg frissítjük új funkciók leírásával, valamint további részletekkel, és javítjuk az olvashatóságot. A legfrissebb információk: [Power BI Premium-kapacitások üzembe helyezése és kezelése](whitepaper-powerbi-premium-deployment.md).

A Power BI Premium dedikált erőforrásokat biztosít vállalata számára a Power BI szolgáltatás futtatásához. Megbízhatóbb teljesítményt biztosít és nagyobb mennyiségű adat kezelését teszi lehetővé. A Premium széles körű tartalommegosztást is lehetővé tesz anélkül, hogy a tartalomfogyasztók számára felhasználónkénti Pro-licenceket kellene beszereznie.  

## <a name="premium-capacity-and-shared-capacity"></a>Prémium szintű kapacitás és megosztott kapacitás

A Power BI Premium előnyeit úgy használhatja ki, hogy a munkaterületeket *prémium szintű kapacitáshoz* rendeli. A Prémium szintű kapacitás egy dedikált erőforrás a szervezet számára. Azok a munkaterületek, melyek nincsenek prémium szintű kapacitáshoz rendelve, egy *megosztott kapacitásban* fognak szerepelni. Megosztott kapacitással munkafolyamatai más ügyfelekkel megosztott számítási erőforrásokon futnak.

Az alábbi képen a prémium szintű kapacitás és a megosztott kapacitás közötti kapcsolat látható, és a Contoso szervezet szerepel példaként.

![Illusztráció a Power BI Premiumról](media/service-premium/premium-chart.png)

| Terület | Leírás |
| --- | --- |
| **(1)** A prémium szintű kapacitás elemei | <ul><li>Az alkalmazás-munkaterületek tagként vagy rendszergazdaként való eléréséhez és az alkalmazások közzétételéhez Power BI Pro-licenc szükséges.<li>Az alkalmazások megosztásához Pro-licenc szükséges, az alkalmazás felhasználásához azonban nem.<li>Az irányítópultok minden címzettje beállíthat adatriasztásokat, a hozzájuk rendelt licenc típusától függetlenül.<li>A beágyazáshoz a REST API-k Pro-licences szolgáltatásfiókot használnak, nem felhasználói fiókot.</ul> |
| **(2)** Saját munkaterület megosztott kapacitás esetén | <ul><li>Az alkalmazások megosztásához és felhasználásához is Pro-licenc szükséges.</ul> |
| **(3)** Alkalmazás-munkaterületek megosztott kapacitás esetén | <ul><li>Bármely alkalmazás használatához Pro-licenc szükséges.</ul>|
| | |

A kapacitás megosztásakor a Power BI több korlátot érvényesít az egyes felhasználókon annak érdekében, hogy mindenki számára minőségi felhasználói élményt biztosíthasson. Alapértelmezés szerint a munkaterületek is megosztott kapacitáson vannak, beleértve a személyes *Saját munkaterületet* és az alkalmazás-munkaterületeket is.

Az alábbi táblázat a megosztott és a prémium szintű kapacitás közötti különbségeket foglalja össze:

|  | Megosztott kapacitás | Power BI Prémium-kapacitás |
| --- | --- | --- |
| **Frissítési időköz** |8/nap |48/nap |
| Dedikált hardverrel elkülönítve |![Nem érhető el](media/service-premium/not-available.png) |![](media/service-premium/available.png) |
| *Minden felhasználó* számára elérhető vállalati terjesztés | | |
| Alkalmazások és megosztás |![Nem érhető el](media/service-premium/not-available.png) |![](media/service-premium/available.png) |
| Beágyazott API-k és vezérlők |![Nem érhető el](media/service-premium/not-available.png) |![](media/service-premium/available.png)<sup>[1](#fnt1)</sup> |
| Power BI-jelentések helyszíni közzététele |![Nem érhető el](media/service-premium/not-available.png) |![](media/service-premium/available.png) |
| | | |

<a name="fnt1">1</a> A Power BI Premium további fejlesztései várhatók.



### <a name="premium-capacity-nodes"></a>Prémium szintű kapacitást használó csomópontok

A Power BI Premium csomópont-konfigurációkban különböző virtuálismag-kapacitások érhetők el. A konkrét termékváltozat-ajánlatokról és a költségekről a [Power BI díjszabásáról](https://powerbi.microsoft.com/pricing/) szóló témakörben tájékozódhat. Itt egy [költségkalkulátor](https://powerbi.microsoft.com/calculator/) is elérhető. Ha további információra van szüksége a beágyazott elemzési kapacitások tervezésével kapcsolatban, tekintse át a [Planning a Power BI Enterprise Deployment](https://aka.ms/pbienterprisedeploy) (A Power BI vállalati bevezetésének a megtervezése) című tanulmányt. Összegezve:

* A P csomópontok beágyazott, illetve szolgáltatási környezetben is használhatók.

* Az EM csomópontok csak beágyazott környezetekben használhatók. Az EM csomópontok nem férhetnek hozzá prémium képességekhez, például alkalmazások Power BI Pro-licenccel nem rendelkező felhasználókkal való megosztásához.

| Kapacitáscsomópont | Összes virtuális mag<br/>*(Háttérrendszer + előtérrendszer)*  | Háttérrendszeri virtuális magok <sup>[1](#fn1)</sup> | Előtérrendszeri virtuális magok <sup>[2](#fn2)</sup> | DirectQuery-/élő kapcsolat korlátai | Egyidejű frissítések maximális száma |
| --- | --- | --- | --- | --- | --- |
| EM1 (havonta megújuló) |1 virtuális mag |0,5 virtuális mag, 2,5 GB RAM |0,5 virtuális mag |Másodpercenként 3,75 |  1 |
| EM2 (havonta megújuló) |2 virtuális mag |1 virtuális mag, 5 GB RAM |1 virtuális mag |Másodpercenként 7.5 |  2 |
| EM3 (havonta megújuló) |4 virtuális mag |2 virtuális mag, 10 GB RAM |2 virtuális mag | 15 | 3 |
| P1 |8 virtuális mag |4 virtuális mag, 25 GB RAM |4 virtuális mag |Másodpercenként 30 | 6 |
| P2 |16 virtuális mag |8 virtuális mag, 50 GB RAM |8 virtuális mag |Másodpercenként 60 | 12 |
| P3 |32 virtuális mag |16 virtuális mag, 100 GB RAM |16 virtuális mag |Másodpercenként 120 | 24 |
| | | | | | |

<a name="fn1">1</a>: A webszolgáltatásokhoz az előtérrendszeri virtuális magok használatosak. Például az irányítópultokhoz, a jelentés- és dokumentumkezeléshez, a hozzáférések kezeléséhez, az ütemezéshez, az API-khoz, a feltöltésekhez, és letöltésekhez és többnyire mindenhez, ami a felhasználói élmény részét képzi. 

<a name="fn2">2</a>: A háttérrendszeri virtuális magokat a nagyobb erőforrásigényű feladatokhoz, például a lekérdezések feldolgozásához, a gyorsítótár kezeléséhez, R szerverek futtatásához, adatfrissítéshez, természetes nyelvi feldolgozásához, valós idejű adatcsatornákhoz és a jelentések és képek megjelenítéséhez használja. A háttérrendszeri virtuális magokkal bizonyos mennyiségű memóriát is fenntart. A megfelelő mennyiségű memória nagy adatmodellek esetén vagy akkor válik különösen fontossá, amikor nagy számú aktív adatkészlet kezelésére van szükség.

## <a name="workloads-in-premium-capacity"></a>Számítási feladatok prémium szintű kapacitásban

A Power BI Premium és a Power BI Embedded kapacitásai alapértelmezés szerint csak a Power BI-lekérdezések felhőbeli futtatásával társított számítási feladatot támogatják. A Premium emellett **AI**, **adatfolyamok**, és **lapszámozott jelentések** számára is támogatja a további számítási feladatokat. Ahhoz, hogy a számítási feladatok használni tudják a kapacitás erőforrásait, engedélyezni kell őket a Power BI felügyeleti portálján vagy a Power REST API használatával. Minden számítási feladat rendelkezik alapértelmezett beállításokkal arra, hogy az egyes számítási feladatok milyen maximális memóriamennyiséget használhatnak. Beállíthat azonban másféle memóriafogyasztást is, így meghatározhatja, hogy a számítási feladatok milyen kapcsolatban álljanak egymással, és hogy hogyan használják a kapacitás erőforrásait. További információ: [Számítási feladatok konfigurálása](service-admin-premium-workloads.md).

## <a name="power-bi-report-server"></a>Power BI jelentéskészítő kiszolgáló

A Power BI Premium azt is lehetővé teszi, hogy a cég a helyszínen futtassa a Power BI jelentéskészítő kiszolgálót. További információkat az [Első lépések a Power BI jelentéskészítő kiszolgálóval](report-server/get-started.md) című cikkben talál.

## <a name="next-steps"></a>Következő lépések

[Power BI Premium-kapacitások üzembe helyezése és kezelése](whitepaper-powerbi-premium-deployment.md)   
[A Power BI Premium megvásárlása](service-admin-premium-purchase.md)   
[Power BI Premium – gyakori kérdések](service-premium-faq.md)   



További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
