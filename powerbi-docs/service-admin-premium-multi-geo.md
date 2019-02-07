---
title: Multi-Geo támogatás a Power BI Premiumhoz (előzetes verzió)
description: Útmutató tartalom üzembe helyezéséhez a Power BI-bérlő saját régióján kívüli régiókban lévő adatközpontokban.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/05/2019
LocalizationGroup: Premium
ms.openlocfilehash: bdbcb949ffe29efc4170391774da0863568e97e8
ms.sourcegitcommit: 54d44deb6e03e518ad6378656c769b06f2a0b6dc
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/07/2019
ms.locfileid: "55794660"
---
# <a name="multi-geo-support-for-power-bi-premium-preview"></a>Multi-Geo támogatás a Power BI Premiumhoz (előzetes verzió)

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

A Multi-Geo nem elérhető a Power BI Germany, a 21Vianet által üzemeltetett Power BI China és az USA kormányzati szervei számára készült Power BI esetében.

A Multi-Geo már a Power BI Embeddedben is elérhető. További információ: [Multi-Geo-támogatás a Power BI Embedded (előzetes verzió) számára](developer/embedded-multi-geo.md).

## <a name="using-multi-geo"></a>A Multi-Geo használata

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
- Az [adatfolyamok](service-dataflows-overview.md) funkció (előzetes verzió) jelenleg nem támogatott Multi-GEO használatával.

## <a name="next-steps"></a>Következő lépések

- [Power BI Premium: Mi ez?](service-premium.md)
- [Multi-Geo a Power BI Embedded-kapacitásokhoz](developer/embedded-multi-geo.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
