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
ms.date: 09/11/2018
LocalizationGroup: Premium
ms.openlocfilehash: 0723ddb57131fed499d4ac86666b3cd6d8bcbd2d
ms.sourcegitcommit: 833cf1252807721fb1b3000487bd032bfd6c8c98
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/04/2018
ms.locfileid: "48271808"
---
# <a name="what-is-microsoft-power-bi-premium"></a>Mi az a Microsoft Power BI Premium?

A Microsoft Power BI Premium a Power BI futtatásához dedikált erőforrásokat biztosít a cége vagy csapata számára. Megbízhatóbb teljesítményt biztosít és nagyobb mennyiségű adat kezelését teszi lehetővé. A Premium széles körű tartalommegosztást is lehetővé tesz anélkül, hogy a megtekintők számára felhasználónkénti Pro-licenceket kellene beszereznie.

A Power BI Premium előnyeit úgy használhatja ki, hogy a munkaterületeket *Prémium szintű kapacitáshoz* rendeli. A Prémium szintű kapacitás egy dedikált erőforrás a szervezet számára. Azok a munkaterületek, melyek nincsenek prémium szintű kapacitáshoz rendelve, egy *megosztott kapacitásban* fognak szerepelni. Megosztott kapacitással munkafolyamatai más ügyfelekkel megosztott számítási erőforrásokon futnak. 

A kapacitás megosztásakor a Power BI több korlátot érvényesít az egyes felhasználókon annak érdekében, hogy mindenki számára minőségi felhasználói élményt biztosíthasson. Alapértelmezés szerint a munkaterületek is megosztott kapacitáson vannak, beleértve a személyes *Saját munkaterületet* és az alkalmazás-munkaterületeket is.

[!INCLUDE [powerbi-premium-illustration](./includes/powerbi-premium-illustration.md)]

<iframe width="560" height="315" src="https://www.youtube.com/embed/lNQDkN0GXzU?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="capacity-tiers"></a>Kapacitásszintek

Az alábbiakban a megosztott és a prémium szintű kapacitások közötti különbségeket foglaljuk össze.

|  | Megosztott kapacitás | Power BI Prémium-kapacitás |
| --- | --- | --- |
| **Frissítési időköz** |8/nap |48/nap |
| **Dedikált hardverrel elkülönítve** |![](media/service-premium/not-available.png "Nem érhető el") |![](media/service-premium/available.png "Elérhető") |
| ***Minden felhasználó*** **számára elérhető vállalati terjesztés** | | |
| Alkalmazások és megosztás |![](media/service-premium/not-available.png "Nem érhető el") |![](media/service-premium/available.png "Elérhető")<sup>1</sup> |
| Beágyazott API-k és vezérlők |![](media/service-premium/not-available.png "Nem érhető el") |![](media/service-premium/available.png "Elérhető")<sup>2</sup> |
| **Power BI-jelentések helyszíni közzététele** |![](media/service-premium/not-available.png "Nem érhető el") |![](media/service-premium/available.png "Elérhető") |

*<sup>1</sup> További információkért lásd: [Funkciók a licenc típusa alapján](service-features-license-type.md).*  
*<sup>2</sup> A Power BI Premium további fejlesztései várhatók.*

Ha el szeretné kezdeni a Power BI prémium szintű kapacitásainak használatát, rendeljen egy munkaterületet a kapacitáshoz. Ha egy munkaterület hátterében prémium szintű kapacitás áll, az a következő előnyöket nyújtja:

* **Ütemezett frissítések**: A megosztott kapacitás használatával az importált modell-adatkészletek ütemezett frissítésének száma napi nyolc alkalomra van korlátozva. Prémium szintű munkaterületekhez akár napi 48 frissítés is ütemezhető. A DirectQuery-gyorsítótár prémium szintű kapacitás használatával is csak nyolcszor frissíthető naponta.

* **Elkülönítés dedikált hardverrel**: Megosztott kapacitás mellett a további számítási feladatok erőforrás-szükségletei hatással lehetnek a jelentések és az irányítópultok teljesítményére. Ezzel szemben a prémium szintű kapacitás gondoskodik a számítási feladatok megbízhatóbb teljesítményéről, mert elkülöníti azokat a nem kapcsolódó számítási feladatoktól.

Ha egy alkalmazás Premium-kapacitással van támogatva (azaz prémium szintű kapacitáshoz rendelt munkaterületről lett közzétéve), a közzétett alkalmazást a cég bármely felhasználója használhatja, függetlenül attól, hogy milyen licenccel rendelkeznek.

Munkaterületek prémium szintű kapacitáshoz rendeléséről [A Power BI Premium felügyelete](service-admin-premium-manage.md) című cikkből tájékozódhat.

<a name="premiumskus"/>

### <a name="premium-capacity-nodes"></a>Prémium szintű kapacitást használó csomópontok

A Power BI Premium csomópont-konfigurációkban különböző virtuálismag-kapacitások érhetők el. A konkrét termékváltozat-ajánlatokról és a költségekről a [Power BI díjszabása](https://powerbi.microsoft.com/pricing/) témakörben tájékozódhat. Itt egy [költségkalkulátor](https://powerbi.microsoft.com/calculator/) is elérhető. Ha további információra van szüksége a beágyazott elemzési kapacitások tervezésével kapcsolatban, tekintse át a [Planning a Power BI Enterprise Deployment](https://aka.ms/pbienterprisedeploy) (A Power BI vállalati bevezetésének a megtervezése) című tanulmányt.

* A P csomópontok beágyazott, illetve szolgáltatási környezetben is használhatók.

* Az EM csomópontok csak beágyazott környezetekben használhatók. Az EM csomópontok nem férhetnek hozzá prémium képességekhez, például alkalmazások Power BI Pro-licenccel nem rendelkező felhasználókkal való megosztásához.

>[!NOTE]
>A táblázatban található hivatkozások csak azoknak a felhasználóknak működnek megfelelően, akik az Office 365 globális rendszergazdái. A többi felhasználó 404-es hibaüzenetet kap.

| Kapacitáscsomópont | Összes virtuális mag<br/>*(Háttérrendszer + előtérrendszer)* | Háttérrendszeri virtuális magok | Előtérrendszeri virtuális magok | DirectQuery-/élő kapcsolat korlátai | Maximális oldalmegjelenítések óránként csúcsidőszakban | Elérhetőség |
| --- | --- | --- | --- | --- | --- | --- |
| [EM1 (havonta megújuló)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |1 virtuális mag |0,5 virtuális mag, 2,5 GB RAM |0,5 virtuális mag |Másodpercenként 3,75 |150-300 |Elérhető |
| [EM2 (havonta megújuló)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |2 virtuális mag |1 virtuális mag, 5 GB RAM |1 virtuális mag |Másodpercenként 7.5 |301-600 |Elérhető |
| [EM3 (havonta megújuló)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |4 virtuális mag |2 virtuális mag, 10 GB RAM |2 virtuális mag | |601-1200 |Elérhető |
| [P1](https://portal.office.com/SubscriptionDetails?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1&adminportal=1) |8 virtuális mag |4 virtuális mag, 25 GB RAM |4 virtuális mag |Másodpercenként 30 |1201-2400 |Elérhető ([havonta megújulóként](https://portal.office.com/SubscriptionDetails?OfferId=E4C8EDD3-74A1-4D42-A738-C647972FBE81&adminportal=1) is elérhető) |
| [P2](https://portal.office.com/SubscriptionDetails?OfferId=062F2AA7-B4BC-4B0E-980F-2072102D8605&adminportal=1) |16 virtuális mag |8 virtuális mag, 50 GB RAM |8 virtuális mag |Másodpercenként 60 |2401-4800 |Elérhető |
| [P3](https://portal.office.com/SubscriptionDetails?OfferId=40c7d673-375c-42a1-84ca-f993a524fed0&adminportal=1) |32 virtuális mag |16 virtuális mag, 100 GB RAM |16 virtuális mag |Másodpercenként 120 |4801-9600 |Elérhető |

* Az előtérrendszeri virtuális magokat használja a rendszer webes szolgáltatásokhoz, az irányítópultokhoz, a jelentés- és dokumentumkezeléshez, a hozzáférések kezeléséhez, az ütemezéshez, az API-khoz, a feltöltésekhez, és letöltésekhez és többnyire mindenhez, ami a felhasználói élmény részét képzi.

* A háttérrendszeri virtuális magokat a nagyobb erőforrásigényű feladatokhoz, például a lekérdezések feldolgozásához, a gyorsítótár kezeléséhez, R szerverek futtatásához, adatfrissítéshez, természetes nyelvi feldolgozásához, valós idejű adatcsatornákhoz és a jelentések és képek megjelenítéséhez használja. A háttérrendszeri virtuális magokkal bizonyos mennyiségű memóriát is fenntart. A megfelelő mennyiségű memória nagy adatmodellek esetén vagy akkor válik különösen fontossá, amikor nagy számú aktív adatkészlet kezelésére van szükség.

## <a name="power-bi-report-server"></a>Power BI jelentéskészítő kiszolgáló
A Power BI Premium azt is lehetővé teszi, hogy a cég a helyszínen futtassa a Power BI jelentéskészítő kiszolgálót. További információkat az [Első lépések a Power BI jelentéskészítő kiszolgálóval](report-server/get-started.md) című cikkben talál.

## <a name="next-steps"></a>Következő lépések
[Power BI Premium – gyakori kérdések](service-premium-faq.md)  
[A Power BI Premium kiadásával kapcsolatos megjegyzések](service-premium-release-notes.md)  
[A Power BI Premium megvásárlása](service-admin-premium-purchase.md)  
[A Power BI prémium kezelése](service-admin-premium-manage.md)  
[Microsoft Power BI Premium-tanulmány](https://aka.ms/pbipremiumwhitepaper)  
[A Power BI vállalati bevezetésének megtervezése ‒ tanulmány](https://aka.ms/pbienterprisedeploy)  
[A Power BI felügyelete a cégnél](service-admin-administering-power-bi-in-your-organization.md)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
