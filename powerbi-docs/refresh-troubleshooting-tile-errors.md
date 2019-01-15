---
title: Csempékkel kapcsolatos hibák elhárítása
description: A csempék Power BI-beli frissítésének megkísérlésekor előforduló gyakori hibák
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: bc53bdf6c0fd013d446c6d74cf2a422a84302f6a
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54289785"
---
# <a name="troubleshooting-tile-errors"></a>Csempékkel kapcsolatos hibák elhárítása
Az alábbiakban a csempékkel kapcsolatban felmerülő gyakori hibákat és azok magyarázatát soroltuk fel.

> [!NOTE]
> Ha egy itt fel nem sorolt hiba okozza a problémát, a [közösségi webhelyen](http://community.powerbi.com/) kérhet további segítséget, vagy létrehozhat egy [támogatási jegyet](https://powerbi.microsoft.com/support/).
> 
> 

## <a name="errors"></a>Hibák
**Hibát észlelt a Power BI a modell betöltése közben. Próbálkozzon újra később.**
vagy **Nem sikerült beolvasni az adatmodellt. Forduljon az irányítópult tulajdonosához, és győződjön meg róla, hogy az adatforrások és az adatmodell léteznek és elérhetők.**

Nem sikerült hozzáférni az adataihoz, mert az adatforrás nem volt elérhető. Ez akkor fordulhat elő, ha az adatforrást eltávolították, átnevezték, áthelyezték, offline állapotban volt, vagy megváltoztak az engedélyek. Győződjön meg róla, hogy a forrás még a mutatott helyen található, és továbbra is van engedélye az eléréséhez. Ha nem ez a probléma, lehetséges, hogy a forrás lassú. Próbálkozzon újra egy későbbi időpontban, amikor a forrás terhelése kisebb. Ha ez egy helyszíni adatforrás, az adatforrás tulajdonosa esetleg további információkkal tud szolgálni.

**Nem rendelkezik engedéllyel a csempe megtekintéséhez és a munkafüzet megnyitásához.**

Forduljon az irányítópult tulajdonosához, és győződjön meg róla, hogy az adatforrások és az adatmodell léteznek és elérhetők az Ön fiókjával.

**Minden adathierarchizálásban legalább egy olyan csoportnak vagy számításnak kell szerepelnie, amely adatokat generál. Forduljon az irányítópult tulajdonosához.**

Jelenleg nem jeleníthetők meg adatok, mert a lekérdezés üres. Próbálja meg egyes mezőket a mezőlistáról hozzáadni a vizualizációhoz, és újra rögzíteni azt.

**Nem sikerült megjeleníteni az adatokat, mert a Power BI nem tudta meghatározni, hogy milyen kapcsolat van két vagy több mező között.**

Két vagy több, nem kapcsolódó táblázatokból származó mezőt próbál használni. Távolítsa el a nem kapcsolódó mezőket a vizualizációból, majd hozzon létre kapcsolatot a táblák között. Miután ezt elvégezte, újból hozzáadhatja a mezőket a vizualizációhoz. Ezt a Power BI Desktopban vagy az Excel programhoz készült PowerPivot bővítményben teheti meg. [További információ](desktop-create-and-manage-relationships.md)

**Az elsődleges és a másodlagos tengelyen lévő csoportok között átfedés van. Az elsődleges tengelyen lévő csoportok kulcsai nem egyezhetnek meg a másodlagos tengelyen lévőkével.**

Ez általában átmeneti jellegű probléma. Általában olyankor lép fel, ha sorokból oszlopokba helyez át csoportokat. Ebben az esetben a csoportok áthelyezésének befejezésekor el kell, hogy tűnjön a hiba. Ha továbbra is megjelenik az üzenet, próbálkozzon mezőváltással a sorok és oszlopok, vagy a tengely jelmagyarázata között, vagy eltávolítani mezőket a vizualizációból.  

**A megjelenítés túllépte az elérhető erőforráskorlátokat. Szűréssel csökkentheti a megjelenített adatmennyiséget.**

A vizualizáció túl sok adatot próbált lekérdezni ahhoz, hogy a rendelkezésre álló erőforrásokkal biztosítani tudjuk a teljes eredményt. Próbálkozzon a vizualizáció szűrésével az eredményben szereplő adatmennyiség csökkentése érdekében.

**Nem lehet azonosítani a következő mezőket: {0}. Frissítse a látványelemet az adathalmazban meglévő mezőkkel.**

A mezőt valószínűleg törölték vagy átnevezték. Távolítsa el a hibás mezőt a vizualizációból, adjon hozzá egy másik mezőt, és rögzítse ismét.

**Nem sikerült betölteni a látványelem adatait. Próbálkozzon újra később.**

Ez általában átmeneti jellegű probléma. Ha később ismét próbálkozik, és továbbra is megjelenik ez az üzenet, forduljon a támogatási szolgálathoz.

## <a name="contact-support"></a>Kapcsolatfelvétel a támogatási szolgálattal
Ha a probléma továbbra is fennáll, [kérjen támogatást](https://support.powerbi.com) a további vizsgálat érdekében.

## <a name="next-steps"></a>Következő lépések
[A Helyszíni adatátjáróval kapcsolatos hibák elhárítása](service-gateway-onprem-tshoot.md)  
[A Power BI Personal Gateway hibáinak elhárítása](service-admin-troubleshooting-power-bi-personal-gateway.md)  
További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

