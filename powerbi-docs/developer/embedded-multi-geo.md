---
title: Multi-Geo-támogatás a Power BI Embedded (előzetes verzió) számára
description: Útmutató tartalom üzembe helyezéséhez a Power BI Embedded saját régióján kívüli régiókban lévő adatközpontokban.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: nishalit
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/05/2019
ms.openlocfilehash: 25627709af2faa78fd30b28cffba21d1442e0d3f
ms.sourcegitcommit: 0abcbc7898463adfa6e50b348747256c4b94e360
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/06/2019
ms.locfileid: "55762421"
---
# <a name="multi-geo-support-for-power-bi-embedded-preview"></a>Multi-Geo-támogatás a Power BI Embedded (előzetes verzió) számára

**Multi-Geo-támogatás a Power BI Embedded (előzetes verzió) számára** Ez azt jelenti, hogy az alkalmazásokat létrehozó független szoftverszolgáltatók és szervezetek, amelyek a Power BI Embeddedel ágyazzák be az elemzéseket az alkalmazásokba, már üzembe helyezhetik adataikat a világ különböző régióiban.

A **Power BI Embedded** szolgáltatást használó ügyfelek már beállíthatnak egy **A kapacitást** a **Multi-Geo** beállítási lehetőségeinek használatával, ugyanazon funkciók és korlátozások alapján, amelyeket a [Power BI Premium is támogat a Multi-Geo funkció használatakor](../service-admin-premium-Multi-Geo.md).

## <a name="creating-new-power-bi-embedded-capacity-resource-with-multi-geo"></a>Új Power BI Embedded-beli kapacitás-erőforrás létrehozása Multi-Geoval

Az **Erőforrás létrehozása** képernyőn ki kell választania a kapacitás helyét. Eddig ez a Power BI-bérlő helyére volt korlátozva, tehát csak egyetlen helyen volt elérhető. A Multi-Geoval több régió közül választhat a kapacitás üzembe helyezésekor.

![A Power BI Embedded Multi-Geo beállítása](media/embedded-multi-geo/pbie-multi-geo-setup.png)

Vegye észre, hogy a Hely legördülő menü megnyitásakor alapértelmezetten a saját bérlője van kiválasztva.
  
![A Power BI Embedded Multi-Geo alapértelmezett helye](media/embedded-multi-geo/pbie-multi-geo-default-location.png)

Ha egy másik helyet választ, egy üzenet jelenik, amely felhívja a figyelmét erre a választásra.

![Hely módosítása](media/embedded-multi-geo/pbie-multi-geo-location-change.png)

## <a name="view-capacity-location"></a>Kapacitás helyének megtekintése

Ha megnyitja a Power BI Embedded felügyeleti főoldalát az Azure Portalon, akkor egyszerűen megtekintheti a kapacitások helyét.

![Különböző helyeken lévő kapacitások](media/embedded-multi-geo/pbie-multi-geo-location-different.png)

Ez a Powerbi.com Felügyeleti portálján is elérhető. A Felügyeleti portálon válassza a „Kapacitásbeállítások” lehetőséget, majd váltson a „Power BI Embedded” lapra.

![Megtekintés a Felügyeleti portálon](media/embedded-multi-geo/pbie-multi-geo-admin-portal.png)

[További információ a Power BI Embedded-kapacitások létrehozásáról.](azure-pbie-create-capacity.md)

## <a name="manage-existing-capacities-location"></a>Meglévő kapacitások helyének kezelése

A Power BI Embedded-erőforrás helye nem módosítható, miután létrehozott egy új kapacitást.

A Power BI-tartalmaknak egy másik régióba való áthelyezéséhez kövesse az alábbi lépéseket:

1. [Hozzon létre egy új kapacitást](azure-pbie-create-capacity.md) egy másik régióban.

2. Rendeljen hozzá minden munkaterület a meglévő kapacitásból az új kapacitásba.

3. Törölje vagy szüneteltesse a régi kapacitást.

Fontos megjegyezni, hogy ha úgy dönt, hogy töröl egy kapacitást a tartalmának az újrakiosztása nélkül, akkor a kapacitás minden tartalma egy megosztott kapacitásba kerül, amely az otthoni régiójában található.

## <a name="api-support-for-multi-geo"></a>A Multi-Geo API-támogatása

Annak érdekében, hogy a rendszer támogassa a Multi-Geoval rendelkező kapacitások API-n keresztüli kezelését, néhány módosítást végeztünk a meglévő API-kon:

1. **[Get Capacities (Kapacitások lekérése)](https://docs.microsoft.com/rest/api/power-bi/capacities/getcapacities)** – Az API a felhasználó számára elérhető kapacitások listáját adja vissza. A válasz már egy „region” nevű új tulajdonságot is tartalmaz, amely a kapacitás helyét határozza meg.

2. **[Assign To Capacity (Hozzárendelés kapacitáshoz)](https://docs.microsoft.com/rest/api/power-bi/capacities)** – Az API lehetővé teszi egy adott munkaterület hozzárendelését egy kapacitáshoz. Ez a művelet nem teszi lehetővé munkaterületek kapacitáshoz való hozzárendelését az otthoni régión kívül, sem a munkaterületek különböző régiókban lévő kapacitások közötti áthelyezését. A művelet végrehajtásához a felhasználónak vagy a [szolgáltatásnévnek](embed-service-principal.md) rendszergazdai engedélyre van szüksége a munkaterületen és rendszergazdai vagy hozzárendelési engedélyre a célkapacitásban.

3. **[Azure Resource Manager API](https://docs.microsoft.com/rest/api/power-bi-embedded/capacities)** – Az Azure Resource Manager API összes művelete, többek között a *Létrehozás* és a *Törlés* is támogatja a Multi-Geo funkciót.

## <a name="limitations-and-considerations"></a>Korlátozások és szempontok

* Mielőtt kezdeményezné az adatátvitelt, győződjön meg arról, hogy a régiók közötti összes forgalom megfelel minden vállalati és kormányzati megfelelőségi követelménynek.

* A távoli régiókban tárolt gyorsítótárazott lekérdezések inaktív állapotban abban a régióban maradnak. Más átvitt adatok azonban oda-vissza mozoghatnak különböző földrajzi hely között.

* Ha Multi-Geo-környezetben adatot mozgat egy régióból egy másikba, a forrásadatok akár 30 napon át is megmaradhatnak abban a régióban, ahonnan mozgatta őket. Ebben az időszakban a felhasználók nem férnek hozzájuk. A 30 napos időszak után az adatok el lesznek távolítva ebből a régióból, és meg lesznek semmisítve.

* A Multi-Geo általában nem eredményez jobb teljesítményt. A jelentések és irányítópultok betöltéséhez továbbra is szükségesek a saját régióból lekért metaadatok.

## <a name="next-steps"></a>Következő lépések

További információ a Power BI Embedded-kapacitásokról és a Multi-Geo beállításairól minden kapacitásnál az alábbi hivatkozásokon érhető el.

* [Mi az a Power BI Embedded?](azure-pbie-what-is-power-bi-embedded.md)

* [Power BI Embedded-kapacitás létrehozása](azure-pbie-create-capacity.md)

* [Multi-Geo a Power BI Premium kapacitásaiban](../service-admin-premium-multi-geo.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)