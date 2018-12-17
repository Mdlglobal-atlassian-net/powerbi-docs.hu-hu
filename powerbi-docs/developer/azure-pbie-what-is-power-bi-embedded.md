---
title: Az Azure Power BI Embedded és a beágyazott analitika ismertetése | Microsoft Docs
description: A Power BI Embedded beágyazott analitika eszköznek készült, mellyel a független szoftverszállítók lenyűgöző vizualizációkat, jelentéseket és irányítópultokat adhatnak gyorsan alkalmazásaikhoz, így leegyszerűsíthetik a Power BI funkcióit. Útmutató beágyazott analitikai szoftver, beágyazott analitikai eszközök, vagy beágyazott üzleti intelligencia eszközök alkalmazásához a Power BI Embedded használatával.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: power-bi-embedded
ms.component: ''
ms.devlang: csharp, javascript
ms.topic: overview
ms.custom: seodec18
ms.date: 12/10/2018
ms.openlocfilehash: 70cb8f72e5749f7eed70d4476f3af87e272813f4
ms.sourcegitcommit: f25464d5cae46691130eb7b02c33f42404011357
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/10/2018
ms.locfileid: "53180691"
---
# <a name="what-is-power-bi-embedded-in-azure"></a>A Power BI Embedded az Azure-ban ismertetése

A Power BI Embedded a beágyazott analitikákkal a Power BI-funkciók használatát teszi egyszerűbbé független szoftverszolgáltatók és fejlesztők számára. A Power BI Embeddeddel lenyűgöző vizualizációkat, jelentéseket és irányítópultokat adhat gyorsan alkalmazásaihoz, így leegyszerűsítheti a Power BI funkcióit. A Microsoft Azure-on fejlesztett alkalmazásokhoz hasonlóan Machine Learning és IoT szolgáltatásokat is használ. A könnyen navigálható, alkalmazáson belüli adatfeltárás engedélyezésével a független szoftverszállítók ügyfelei gyors és tájékozott döntéseket hozhatnak.

> [!VIDEO https://www.youtube.com/embed/iEHfUuoZseo]

2017. májusában bejelentettük a Power BI és a Power BI Embedded szolgáltatások átszervezését. Az átszervezés egyetlen API-felületet, egységes funkciókínálatot és a legújabb funkciókhoz való hozzáférést eredményezett mindkét szolgáltatásban. Emellett bevezettünk egy kapacitásalapú díjszabási modellt, amellyel egyszerűbbé tettük a Power BI számlázását.

A Power BI Embeddeddel a független szoftverszállítók és a fejlesztők rugalmasabban ágyazhatnak be intelligenciát az alkalmazásaikba a Power BI API-k segítségével. A független szoftverszállítók és a fejlesztők minimális fejlesztési erőfeszítéssel érhetnek el gyorsabb piacra dobási időt, és megkülönböztethetik alkalmazásaikat a Microsoft világszínvonalú elemzőmotorjával. A fejlesztők hasonlóképp a megoldásukra fókuszálhatnak, hogy megfeleljenek az ügyfelek igényeinek, ahelyett, hogy vizuális elemzési funkciókat fejlesztenének. A Power BI Embeddeddel ezen kívül jól ismert fejlesztési környezetekben dolgozhat – a Visual Studióban és az Azure-ban.

Már van beágyazott Power BI-tartalommal rendelkező alkalmazása, amely Power BI Premiumot használ? Ha Ön alkalmazásokat kínáló független szoftverszállító vagy fejlesztő, vagy egy ezeket felhasználó szervezet képviselője, nincs további teendője. Ezeket az alkalmazásokat megszakítás nélkül használhatja az ügyfeleivel együtt. Ha már van egy Power BI-beli munkaterület-csoportban fejlesztett alkalmazása, és ki szeretné használni az átszervezett API-felületet, valamint az új, kapacitásalapú Azure SKU-kat, migrálási segítséget a dokumentációban találhat.

## <a name="comparing-power-bi-embedded-with-power-bi-premium"></a>A Power BI Embedded és a Power BI Premium összehasonlítása

A **Power BI Embedded** független szoftvergyártóknak (ISV-knek) és fejlesztőknek szól, akik az ügyfelek számára fejlesztenek alkalmazásokat. Használható külső üzletiintelligencia-szolgáltatásként, amellyel megjelenítheti az alkalmazásadatokat a szolgáltatás saját kezű fejlesztése helyett. A Power BI Embedded egy elemzői szolgáltatásként nyújtott platform (PaaS), amellyel a fejlesztők jelentéseket és irányítópultokat ágyazhatnak be az ügyfeleik alkalmazásaiba. A **Power BI Premium** egy olyan elemzési szolgáltatottszoftver-megoldás (SaaS), amely vállalatok számára teszi lehetővé a legfontosabb üzleti adataik egyszerű megtekintését. 

A [Power BI Embedded](https://azure.microsoft.com/pricing/details/power-bi-embedded/) egy használatalapú fizetéses szolgáltatás, míg a [Power BI Premium](https://powerbi.microsoft.com/calculator/) havi díjas szolgáltatás. További összehasonlítást ebben a [videóban](https://www.youtube.com/watch?v=0y2oJikC6Xc&t=0s&list=PLv2BtOtLblH1dQPV49Ni12olDcUoW-GEl&index=3) találhat.

## <a name="easy-to-use-tools"></a>Egyszerűen használható eszközök

A Power BI Embeddeddel arra összpontosíthat, amihez igazán ért: a nagyszerű alkalmazások fejlesztésére. A Power BI Embeddeddel olyan eszközökkel és képességekkel dolgozhat, amelyeket már jól ismer.

* [**Az Azure Portal**](https://portal.azure.com/): Egy webalapú alkalmazás az Azure-szolgáltatások kezeléséhez
* [**Visual Studio Code**](https://code.visualstudio.com/docs): Egy ingyenes, letölthető, nyílt forráskódú kódszerkesztő Windows, macOS és Linux rendszerhez, amely bővítményeket is támogat
* [**Power BI Desktop**](https://powerbi.microsoft.com/desktop/): Egy ingyenes, letölthető eszköz, amellyel részletgazdag, vizuális elemzésekkel ellátott interaktív jelentéseket készíthet

A REST API-nak köszönhetően a Power BI Embeddedben bármilyen nyelven fejleszthet.

## <a name="engage-with-the-power-bi-engineering-team"></a>Lépjen kapcsolatba a Power BI mérnöki csapatával

* [Közösségek](https://community.powerbi.com/): Kérdéseket tehet fel a Power BI-ról
* [Power BI-ötletek](https://ideas.powerbi.com): Funkciók kérése és szavazás ezekről
* [Reddit](https://www.reddit.com/r/PowerBI/): A Power BI megvitatása

## <a name="next-steps"></a>Következő lépések

A kapacitáscsomópontokról további információt a [díjszabást ismertető lapon](https://azure.microsoft.com/pricing/details/power-bi-embedded/) találhat.

A Power BI Embedded-kapacitások létrehozásához tekintse meg a [Power BI Embedded-kapacitás az Azure Portalon való létrehozásával](azure-pbie-create-capacity.md) kapcsolatos cikket

Power BI-tartalmak beágyazásának megkezdése előtt tekintse át a [Power BI-irányítópultok, -jelentések és -csempék beágyazása](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/) című témakört.
