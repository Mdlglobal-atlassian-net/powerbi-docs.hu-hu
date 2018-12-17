---
title: Mi az a Microsoft Power BI Premium?
description: A Power BI Premium dedikált kapacitást biztosít cége vagy csapata számára, így felhasználónkénti licencek vásárlása nélkül is megbízható teljesítményre számíthat nagyobb mennyiségű adat estén is.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 10/21/2018
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: cbfee8034639a65517f9adc57cc95dd1271e6044
ms.sourcegitcommit: 72c9d9ec26e17e94fccb9c5a24301028cebcdeb5
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/07/2018
ms.locfileid: "53025442"
---
# <a name="what-is-microsoft-power-bi-premium"></a>Mi az a Microsoft Power BI Premium?

A Microsoft Power BI Premium a Power BI futtatásához dedikált erőforrásokat biztosít a cége számára. Megbízhatóbb teljesítményt biztosít és nagyobb mennyiségű adat kezelését teszi lehetővé. A Premium széles körű tartalommegosztást is lehetővé tesz anélkül, hogy a tartalomfogyasztók számára felhasználónkénti Pro-licenceket kellene beszereznie. A vásárlással kapcsolatban további tudnivalókért lásd [a Power BI Premium megvásárlását](service-admin-premium-purchase.md) ismertető szakaszt.

<iframe width="560" height="315" src="https://www.youtube.com/embed/lNQDkN0GXzU?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

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

Az alábbi táblázat a megosztott és a prémium szintű kapacitás közötti különbségeket foglalja össze.

|  | Megosztott kapacitás | Power BI Prémium-kapacitás |
| --- | --- | --- |
| **Frissítési időköz** |8/nap |48/nap |
| **Dedikált hardverrel elkülönítve** |![Nem érhető el](media/service-premium/not-available.png) |![Elérhető](media/service-premium/available.png) |
| _**Minden felhasználó**_ **számára elérhető vállalati terjesztés** | | |
| Alkalmazások és megosztás |![Nem érhető el](media/service-premium/not-available.png) |![Elérhető](media/service-premium/available.png) |
| Beágyazott API-k és vezérlők |![Nem érhető el](media/service-premium/not-available.png) |![Elérhető](media/service-premium/available.png)<sup>2</sup> |
| **Power BI-jelentések helyszíni közzététele** |![Nem érhető el](media/service-premium/not-available.png) |![Elérhető](media/service-premium/available.png) |
| | | |

*<sup>1</sup> További információkért lásd: [Funkciók a licenc típusa alapján](service-features-license-type.md).*  
*<sup>2</sup> A Power BI Premium további fejlesztései várhatók.*

Munkaterületek prémium szintű kapacitáshoz rendeléséről [A Power BI Premium felügyelete](service-admin-premium-manage.md) című cikkből tájékozódhat.

<a name="premiumskus"/>

### <a name="premium-capacity-nodes"></a>Prémium szintű kapacitást használó csomópontok

A Power BI Premium csomópont-konfigurációkban különböző virtuálismag-kapacitások érhetők el. A konkrét termékváltozat-ajánlatokról és a költségekről a [Power BI díjszabásáról](https://powerbi.microsoft.com/pricing/) szóló témakörben tájékozódhat. Itt egy [költségkalkulátor](https://powerbi.microsoft.com/calculator/) is elérhető. Ha további információra van szüksége a beágyazott elemzési kapacitások tervezésével kapcsolatban, tekintse át a [Planning a Power BI Enterprise Deployment](https://aka.ms/pbienterprisedeploy) (A Power BI vállalati bevezetésének a megtervezése) című tanulmányt. Összegezve:

* A P csomópontok beágyazott, illetve szolgáltatási környezetben is használhatók.

* Az EM csomópontok csak beágyazott környezetekben használhatók. Az EM csomópontok nem férhetnek hozzá prémium képességekhez, például alkalmazások Power BI Pro-licenccel nem rendelkező felhasználókkal való megosztásához.

>[!NOTE]
>A táblázatban található hivatkozások csak azoknak a felhasználóknak működnek megfelelően, akik az Office 365 globális rendszergazdai szerepkörével rendelkeznek. A többi felhasználó 404-es hibaüzenetet kap.

| Kapacitáscsomópont | Összes virtuális mag<br/>*(Háttérrendszer + előtérrendszer)* | Háttérrendszeri virtuális magok | Előtérrendszeri virtuális magok | DirectQuery-/élő kapcsolat korlátai | Maximális oldalmegjelenítések óránként csúcsidőszakban | Elérhetőség |
| --- | --- | --- | --- | --- | --- | --- |
| [EM1 (havonta megújuló)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |1 virtuális mag |0,5 virtuális mag, 2,5 GB RAM |0,5 virtuális mag |Másodpercenként 3,75 |150-300 |Elérhető |
| [EM2 (havonta megújuló)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |2 virtuális mag |1 virtuális mag, 5 GB RAM |1 virtuális mag |Másodpercenként 7.5 |301-600 |Elérhető |
| [EM3 (havonta megújuló)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |4 virtuális mag |2 virtuális mag, 10 GB RAM |2 virtuális mag | |601-1200 |Elérhető |
| [P1](https://portal.office.com/SubscriptionDetails?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1&adminportal=1) |8 virtuális mag |4 virtuális mag, 25 GB RAM |4 virtuális mag |Másodpercenként 30 |1201-2400 |Elérhető ([havonta megújulóként](https://portal.office.com/SubscriptionDetails?OfferId=E4C8EDD3-74A1-4D42-A738-C647972FBE81&adminportal=1) is elérhető) |
| [P2](https://portal.office.com/SubscriptionDetails?OfferId=062F2AA7-B4BC-4B0E-980F-2072102D8605&adminportal=1) |16 virtuális mag |8 virtuális mag, 50 GB RAM |8 virtuális mag |Másodpercenként 60 |2401-4800 |Elérhető |
| [P3](https://portal.office.com/SubscriptionDetails?OfferId=40c7d673-375c-42a1-84ca-f993a524fed0&adminportal=1) |32 virtuális mag |16 virtuális mag, 100 GB RAM |16 virtuális mag |Másodpercenként 120 |4801-9600 |Elérhető |
| | | | | | | |

* Az előtérrendszeri virtuális magokat használja a rendszer webes szolgáltatásokhoz, az irányítópultokhoz, a jelentés- és dokumentumkezeléshez, a hozzáférések kezeléséhez, az ütemezéshez, az API-khoz, a feltöltésekhez, és letöltésekhez és többnyire mindenhez, ami a felhasználói élmény részét képzi.

* A háttérrendszeri virtuális magokat a nagyobb erőforrásigényű feladatokhoz, például a lekérdezések feldolgozásához, a gyorsítótár kezeléséhez, R szerverek futtatásához, adatfrissítéshez, természetes nyelvi feldolgozásához, valós idejű adatcsatornákhoz és a jelentések és képek megjelenítéséhez használja. A háttérrendszeri virtuális magokkal bizonyos mennyiségű memóriát is fenntart. A megfelelő mennyiségű memória nagy adatmodellek esetén vagy akkor válik különösen fontossá, amikor nagy számú aktív adatkészlet kezelésére van szükség.

## <a name="workloads-in-premium-capacity"></a>Számítási feladatok prémium szintű kapacitásban

Egy Power BI-beli számítási feladat felfogható a felhasználók számára felkínálható számos szolgáltatás egyikeként. A **Power BI Premium** és a **Power BI Embedded** kapacitásai alapértelmezés szerint csak a Power BI-lekérdezések felhőbeli futtatásával társított számítási feladatot támogatják.

Most két további számítási feladathoz kínálunk előzetes verziójú támogatást: a **lapszámozott jelentésekhez** és az **adatfolyamokhoz**. Ezek a számítási feladatok a Power BI felügyeleti portálján, vagy a Power BI REST API-n keresztül engedélyezhetők. Beállíthatja az egyes számítási feladatok által felhasználható memória maximumát is, hogy szabályozni tudja a különböző számítási feladatok egymásra gyakorolt hatását. További információ: [Számítási feladatok konfigurálása](service-admin-premium-manage.md#configure-workloads).

### <a name="default-memory-settings"></a>Alapértelmezett memóriabeállítások

Az alábbi táblázatok a különböző elérhető [kapacitás-csomópontokon](#premium-capacity-nodes) alapuló alapértelmezett és minimális memóriaértékeket ismertetik. A memória adatfolyamokhoz dinamikusan, lapszámozott jelentésekhez viszont statikusan van lefoglalva. További információt a következő, [Szempontok lapszámozott jelentések esetén](#considerations-for-paginated-reports) című szakaszban talál.

#### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>Microsoft Office SKU-k szoftverszolgáltatásokhoz (SaaS)

|                     | EM3                      | P1                       | P2                      | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|
| Oldalakra osztott jelentések | N.A. | Alapértelmezés szerint 20%; minimum 10% | Alapértelmezés szerint 20%; minimum 5% | Alapértelmezés szerint 20%; minimum 2,5% |
| Adatfolyamok | Alapértelmezés szerint 20%; minimum 8%  | Alapértelmezés szerint 20%; minimum 4%  | Alapértelmezés szerint 20%; minimum 2% | Alapértelmezés szerint 20%; minimum 1%  |
| | | | | |

#### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>Microsoft Office SKU-k platformszolgáltatásokhoz (PaaS)

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| Oldalakra osztott jelentések | N.A.                      | N.A.                      | N.A.                     | Alapértelmezés szerint 20%; minimum 10% | Alapértelmezés szerint 20%; minimum 5% | Alapértelmezés szerint 20%; minimum 2,5% |
| Adatfolyamok         | Alapértelmezés szerint 27%; minimum 27% | Alapértelmezés szerint 20%; minimum 16% | Alapértelmezés szerint 20%; minimum 8% | Alapértelmezés szerint 20%; minimum 4%  | Alapértelmezés szerint 20%; minimum 2% | Alapértelmezés szerint 20%; minimum 1%   |

### <a name="considerations-for-paginated-reports"></a>Szempontok lapszámozott jelentések esetén

A „lapszámozott jelentések” számítási feladat használata során a következőket tartsa szem előtt.

* **Memóriafoglalás lapszámozott jelentésekben**: A lapszámozott jelentések lehetővé teszik, hogy a jelentés renderelése során saját kódot futtasson (például dinamikusan változtassa a szövegszínt a tartalom alapján). Ezt figyelembe véve, a Power BI Premium-kapacitás védelme érdekében a lapszámozott jelentéseket a kapacitás egy korlátozott területén belül futtatjuk. Ehhez a területhez az Ön által megadott maximális memóriát foglaljuk le, akár aktív a számítási feladat, akár nem. Ha egy kapacitásban több Power BI-jelentést vagy -adatfolyamot használ, ügyeljen rá, hogy a lapszámozott jelentésekhez kellően alacsony memóriakorlátot adjon meg, hogy azok ne befolyásolhassák hátrányosan a többi számítási feladatot.

* **A lapszámozott jelentések nem elérhetők**: Ritkán előfordulhat, hogy a „lapszámozott jelentések” számítási feladat elérhetetlenné válik. Ilyen esetben a számítási feladat hibás állapotot jelez a felügyeleti portálon, a felhasználók pedig időtúllépést tapasztalnak a jelentés renderelése során. A probléma megoldásához tiltsa le, majd engedélyezze újra a számítási feladatot.

## <a name="power-bi-report-server"></a>Power BI jelentéskészítő kiszolgálón

A Power BI Premium azt is lehetővé teszi, hogy a cég a helyszínen futtassa a Power BI jelentéskészítő kiszolgálót. További információkat az [Első lépések a Power BI jelentéskészítő kiszolgálóval](report-server/get-started.md) című cikkben talál.

## <a name="next-steps"></a>Következő lépések

[Power BI Premium – gyakori kérdések](service-premium-faq.md)
[A Power BI Premium megvásárlása](service-admin-premium-purchase.md)
[A Power BI Premium kezelése](service-admin-premium-manage.md)
[Microsoft Power BI Premium-tanulmány](https://aka.ms/pbipremiumwhitepaper)
[A Power BI Enterprise üzembehelyezési előkészületeit bemutató tanulmány](https://aka.ms/pbienterprisedeploy)
[A Power BI céges felügyelete](service-admin-administering-power-bi-in-your-organization.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
