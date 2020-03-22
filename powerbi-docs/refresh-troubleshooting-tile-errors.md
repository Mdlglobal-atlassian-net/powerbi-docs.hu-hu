---
title: Csempékkel kapcsolatos hibák elhárítása
description: A csempék Power BI-beli frissítésének megkísérlésekor előforduló gyakori hibák
author: maggiesMSFT
ms.reviewer: kayu
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 12/06/2018
ms.author: maggies
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 79f18faf56fba8afa85afd808f6faa1bd16811d8
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/14/2020
ms.locfileid: "79381146"
---
# <a name="troubleshooting-tile-errors"></a>Csempékkel kapcsolatos hibák elhárítása
Az alábbiakban a csempékkel kapcsolatban felmerülő gyakori hibákat és azok magyarázatát soroltuk fel.

> [!NOTE]
> Ha egy itt fel nem sorolt hiba okozza a problémát, a [közösségi webhelyen](https://community.powerbi.com/) kérhet további segítséget, vagy létrehozhat egy [támogatási jegyet](https://powerbi.microsoft.com/support/).
> 
> 

## <a name="errors"></a>Hibák
**Hibát észlelt a Power BI a modell betöltése közben. Próbálkozzon újra később.**
vagy **Nem sikerült beolvasni az adatmodellt. Forduljon az irányítópult tulajdonosához, és győződjön meg róla, hogy az adatforrások és az adatmodell léteznek és elérhetők.**

Nem sikerült hozzáférni az adataihoz, mert az adatforrás nem volt elérhető. Ez akkor fordulhat elő, ha az adatforrást eltávolították, átnevezték, áthelyezték, offline állapotban volt, vagy megváltoztak az engedélyek. Győződjön meg róla, hogy a forrás még a mutatott helyen található, és továbbra is van engedélye az eléréséhez. Ha nem ez a probléma, lehetséges, hogy a forrás lassú. Próbálkozzon újra egy későbbi időpontban, amikor a forrás terhelése kisebb. Ha ez egy helyszíni adatforrás, az adatforrás tulajdonosa esetleg további információkkal tud szolgálni.

**Nem rendelkezik engedéllyel a csempe megtekintéséhez és a munkafüzet megnyitásához.**

Forduljon az irányítópult tulajdonosához, és győződjön meg róla, hogy az adatforrások és az adatmodell léteznek és elérhetők az Ön fiókjával.

**A rendszergazda letiltotta a Power BI-vizualizációkat.**

A Power BI-rendszergazda letiltotta a Power BI-vizualizációkat a szervezete vagy a biztonsági csoportja számára.
Emiatt nem használhat Power BI-vizualizációkat a [Microsoft Marketplace-ről](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals), és nem importálhat privát vizualizációkat fájlból. Csak az előcsomagolt vizualizációkat használhatja.


**Minden adathierarchizálásban legalább egy olyan csoportnak vagy számításnak kell szerepelnie, amely adatokat generál. Forduljon az irányítópult tulajdonosához.**

Jelenleg nem jeleníthetők meg adatok, mert a lekérdezés üres. Próbálja meg egyes mezőket a mezőlistáról hozzáadni a vizualizációhoz, és újra rögzíteni azt.

**Nem sikerült megjeleníteni az adatokat, mert a Power BI nem tudta meghatározni, hogy milyen kapcsolat van két vagy több mező között.**

Két vagy több, nem kapcsolódó táblázatokból származó mezőt próbál használni. Távolítsa el a nem kapcsolódó mezőket a vizualizációból, majd hozzon létre kapcsolatot a táblák között. Miután ezt elvégezte a módosítást, újból hozzáadhatja a mezőket a vizualizációhoz. Ezt a Power BI Desktopban vagy az Excel programhoz készült PowerPivot bővítményben teheti meg. [További információ](desktop-create-and-manage-relationships.md)

**Az elsődleges és a másodlagos tengelyen lévő csoportok között átfedés van. Az elsődleges tengelyen lévő csoportok kulcsai nem egyezhetnek meg a másodlagos tengelyen lévőkével.**

Ez általában átmeneti jellegű probléma. Általában olyankor lép fel, ha sorokból oszlopokba helyez át csoportokat. Ebben az esetben a csoportok áthelyezésének befejezésekor el kell, hogy tűnjön a hiba. Ha továbbra is megjelenik az üzenet, próbálkozzon mezőváltással a sorok és oszlopok, vagy a tengely jelmagyarázata között, vagy eltávolítani mezőket a vizualizációból.  

**A megjelenítés túllépte az elérhető erőforráskorlátokat. Szűréssel csökkentheti a megjelenített adatmennyiséget.**

A vizualizáció túl sok adatot próbált lekérdezni ahhoz, hogy a rendelkezésre álló erőforrásokkal biztosítani tudjuk a teljes eredményt. Próbálkozzon a vizualizáció szűrésével az eredményben szereplő adatmennyiség csökkentése érdekében.

**Nem lehet azonosítani a következő mezőket: {0}. Frissítse a látványelemet az adathalmazban meglévő mezőkkel.**

A mezőt valószínűleg törölték vagy átnevezték. Távolítsa el a hibás mezőt a vizualizációból, adjon hozzá egy másik mezőt, és rögzítse ismét.

**Nem sikerült betölteni a látványelem adatait. Próbálkozzon újra később.**

Ez általában átmeneti jellegű probléma. Ha később ismét próbálkozik, és továbbra is megjelenik ez az üzenet, forduljon a támogatási szolgálathoz.

**A csempék továbbra is a nem szűrt adatokat jelenítik meg az egyszeri bejelentkezés (SSO) engedélyezése után.**

Ez akkor fordulhat elő, ha az alapul szolgáló adatkészlet DirectQuery mód használatára van konfigurálva, vagy egy helyszíni adatátjárón keresztül élő kapcsolatot használ az Analysis Serviceshez. Ebben az esetben a csempék továbbra is a nem szűrt adatokat jelenítik meg, miután engedélyezte az egyszeri bejelentkezést az adatforráshoz, egészen a következő csempefrissítésig. A következő csempefrissítéskor a Power BI az SSO-t már konfiguráltként használja, és a csempék a felhasználói identitásnak megfelelően szűrve jelenítik meg az adatokat. 

Ha azonnal szűrt adatokat szeretne megjeleníteni, a csempefrissítést kényszerítheti is az irányítópult jobb felső sarkában található **További lehetőségek** (…) elemet, majd **Az irányítópult csempéinek frissítése** lehetőséget választva.

Adatkészlet tulajdonosaként a csempefrissítés gyakoriságát is módosíthatja, és a csempe frissítésének felgyorsításához 15 percre is beállíthatja azt. Válassza a Power BI szolgáltatás jobb felső sarkában található fogaskerék ikont, majd a **Beállítások** lehetőséget. A **Beállítások** lapon válassza az **Adatkészletek** lehetőséget. Bontsa ki az **Ütemezett gyorsítótár-frissítés** elemet, és módosítsa az **Ütemezés gyakoriságát**. Fontos, hogy alaphelyzetbe állítsa a konfigurációt az eredeti frissítési gyakoriságra, miután a Power BI végrehajtaná a következő csempefrissítést.

> [!NOTE]
> Az **Ütemezett gyorsítótár-frissítés** szakasz csak a DirectQuery/Élő kapcsolat módú adatkészletekhez érhető el. Az Importálás módú adatkészletekhez nem szükséges külön csempefrissítés, mert a csempék automatikusan frissülnek a következő beütemezett adatfrissítésnél.

## <a name="contact-support"></a>Kapcsolatfelvétel az ügyfélszolgálattal
Ha a probléma továbbra is fennáll, [kérjen támogatást](https://support.powerbi.com) a további vizsgálat érdekében.

## <a name="next-steps"></a>Következő lépések
[A Helyszíni adatátjáróval kapcsolatos hibák elhárítása](service-gateway-onprem-tshoot.md)  
[A Power BI Personal Gateway hibáinak elhárítása](service-admin-troubleshooting-power-bi-personal-gateway.md)  
További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

