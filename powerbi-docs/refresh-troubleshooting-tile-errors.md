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
ms.openlocfilehash: bfb6178908a9d6a4bcfe81f8d3d9771ac5b12b9d
ms.sourcegitcommit: 88ac51106ec7d0ead8c2a1550a11afae0d502bb9
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/12/2019
ms.locfileid: "56086632"
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

**A rendszergazda letiltotta az egyéni vizualizációkat.**

A Power BI-rendszergazda letiltotta az egyéni vizualizációkat a szervezete vagy a biztonsági csoportja számára. Emiatt nem használhat egyéni vizualizációkat a [Microsoft Marketplace-ről](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=power-bi-visuals), és nem importálhat privát vizualizációkat fájlból. Csak az előcsomagolt vizualizációkat használhatja.


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

## <a name="contact-support"></a>Kapcsolatfelvétel az ügyfélszolgálattal
Ha a probléma továbbra is fennáll, [kérjen támogatást](https://support.powerbi.com) a további vizsgálat érdekében.

## <a name="next-steps"></a>Következő lépések
[A Helyszíni adatátjáróval kapcsolatos hibák elhárítása](service-gateway-onprem-tshoot.md)  
[A Power BI Personal Gateway hibáinak elhárítása](service-admin-troubleshooting-power-bi-personal-gateway.md)  
További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

