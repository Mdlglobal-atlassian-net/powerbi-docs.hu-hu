---
title: Multi-Geo-támogatás a Power BI Premiumhoz
description: Útmutató tartalom üzembe helyezéséhez a Power BI-bérlő saját régióján kívüli régiókban lévő adatközpontokban.
author: mgblythe
ms.author: mblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/05/2019
LocalizationGroup: Premium
ms.openlocfilehash: 129cef8a923b27582bd6424c8d025b93ecbe5532
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73873438"
---
# <a name="configure-multi-geo-support-for-power-bi-premium"></a>Multi-Geo-támogatás konfigurálása a Power BI Premiumhoz

A Multi-Geo a Power BI Premium funkciója, amely segít a nemzetközi ügyfeleknek a regionális, üzletág-specifikus vagy vállalati adatok tárolási helyére vonatkozó előírások betartásában. Power BI Premium-ügyfélként a Power BI-bérlője saját régióján kívüli régiókban lévő adatközpontokban is helyezhet üzembe tartalmat. Egy geo (földrajzi értelemben) egynél több régiót is tartalmazhat. Az Egyesült Államok például egy geo, az USA nyugati középső régiója és az USA déli középső régiója pedig az Egyesült Államokon belüli régió. A tartalom üzembe helyezéséhez az alábbi helyek bármelyikét választhatja:

- Egyesült Államok
- Kanada
- Egyesült Királyság
- Brazília
- Európa
- Japán
- India
- Kelet-Ázsia
- Ausztrália
- Africa

A Multi-Geo nem elérhető a Power BI Germany, a 21Vianet által üzemeltetett Power BI China és az USA kormányzati szervei számára készült Power BI esetében.

A Multi-Geo már a Power BI Embeddedben is elérhető. További információ: [Multi-Geo-támogatás a Power BI Embedded számára](developer/embedded-multi-geo.md).

## <a name="enable-and-configure"></a>Engedélyezés és konfigurálás

Új kapacitásokat érhet el, ha a legördülő listából az alapértelmezettől eltérő régiót választva engedélyezi a Multi-Geo használatát.  Minden elérhető kapacitásnál megjelenik a régió, ahol jelenleg elhelyezkedik, például az **USA nyugati középső régiója**.

![Kapacitás mérete: régió kiválasztása. Power BI Multi-Geo](media/service-admin-premium-multi-geo/power-bi-multi-geo-capacity-size.png)

A kapacitás létrehozása után ebben a régióban marad, és az összes létrehozott munkaterület tartalma ebben a régióban lesz tárolva. Munkaterület egy régióból egy másikba a munkaterület beállításainak képernyőjén lévő legördülő listával migrálható.

![Munkaterület szerkesztése: Rendelkezésre álló kapacitás kiválasztása. Power BI Multi-Geo](media/service-admin-premium-multi-geo/power-bi-multi-geo-edit-workspace.png)

Megjelenik a következő üzenet, amely a módosítás megerősítését kéri.

![Hozzárendelt munkaterület módosításának megerősítése](media/service-admin-premium-multi-geo/power-bi-multi-geo-change-assigned-workspace-capacity.png)

Az átjáró hitelesítő adatait a migrálás során ekkor nem kell újra beállítani.  Miután tárolva lesznek a Prémium szintű kapacitás régiójában, újra be kell állítania őket a migráláskor.

A migrálás során bizonyos műveletek, amilyen az új adatkészletek közzététele vagy az ütemezett adatfrissítés, sikertelenek lehetnek.  

A Multi-Geo engedélyezése esetén a következő elemek lesznek a Prémium-régióban tárolva:

- Modellek (.ABF-fájlok) importáláshoz és DirectQuery-adathalmazok
- Lekérdezési gyorsítótár
- R-lemezképek

A következő elemek a bérlő saját régiójában maradnak:

- Leküldéses adathalmazok
- Excel-munkafüzetek
- Irányítópultok és jelentések metaadatai: például csempenevek, csempelekérdezések
- Átjárólekérdezések vagy ütemezett frissítési feladatok szolgáltatásbuszai
- Engedélyek
- Adathalmaz hitelesítő adatai

## <a name="view-capacity-regions"></a>Kapacitások és régiók megtekintése

A felügyeleti portálom megtekinthető a Power BI-bérlő összes kapacitása, és a régiók, ahol azok jelenleg elhelyezkednek.

![Prémium szintű kapacitások megtekintése](media/service-admin-premium-multi-geo/power-bi-multi-geo-premium-capacities.png) 

## <a name="change-the-region-for-existing-content"></a>Meglévő tartalom régiójának módosítása

Ha módosítania kell egy meglévő tartalom régióját, két módszer közül választhat.

- Létrehozhat egy másik kapacitást, majd áthelyezheti a munkaterületeket. Az ingyenes felhasználók nem tapasztalnak állásidőt, ha a bérlő rendelkezik tartalék virtuális magokkal.
- Ha második kapacitás létrehozása nem járható út, akkor ideiglenesen visszahelyezheti a tartalmat a Prémium szintűből a megosztott kapacitásba. További virtuális magokra nincs szükség, az ingyenes felhasználók viszont valamennyi állásidőt tapasztalnak majd.

## <a name="move-content-out-of-multi-geo"></a>Tartalom visszavétele a Multi-Geo alól  

A munkaterületek kétféle módon vonhatók ki a Multi-Geo-kapacitásból:

- Törölheti a meglévő kapacitást, ahol a munkaterület elhelyezkedik.  A munkaterület ezáltal vissza lesz helyezve a saját régi megosztott kapacitásába.
- A munkaterületeket egyenként visszamigrálhatja a saját bérlőbeli Prémium szintű kapacitásba.

## <a name="limitations-and-considerations"></a>Korlátozások és szempontok

- Mielőtt kezdeményezné az adatátvitelt, győződjön meg arról, hogy a régiók közötti összes forgalom megfelel minden vállalati és kormányzati megfelelőségi követelménynek.
- A távoli régiókban tárolt gyorsítótárazott lekérdezések inaktív állapotban abban a régióban maradnak. Más átvitt adatok azonban oda-vissza mozoghatnak több földrajzi hely között.
- Ha Multi-Geo-környezetben adatot mozgat egy régióból egy másikba, a forrásadatok akár 30 napon át is megmaradhatnak abban a régióban, ahonnan mozgatta őket. Ebben az időszakban a végfelhasználók nem férnek hozzájuk. A 30 napos időszak után az adatok el lesznek távolítva ebből a régióból, és meg lesznek semmisítve.
- A Multi-Geo általában nem eredményez jobb teljesítményt. A jelentések és irányítópultok betöltéséhez továbbra is szükségesek a saját régióból lekért metaadatok.
- Az [adatfolyamok](service-dataflows-overview.md) funkció jelenleg nem támogatott Multi-GEO használatával.

## <a name="next-steps"></a>Következő lépések

- [Mi a Power BI Premium?](service-premium-what-is.md)
- [Multi-Geo a Power BI Embedded-kapacitásokhoz](developer/embedded-multi-geo.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
