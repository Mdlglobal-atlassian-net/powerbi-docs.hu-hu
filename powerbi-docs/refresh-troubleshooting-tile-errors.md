---
title: Csempékkel kapcsolatos hibák elhárítása
description: A csempék Power BI-beli frissítésének megkísérlésekor előforduló gyakori hibák
author: mgblythe
manager: kfile
ms.reviewer: kayu
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: c1df7e6293db703922f37c3f28546bb296d1a46a
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66050997"
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

**Csempék továbbra is nem szűrt adatok megjelenítése az egyszeri bejelentkezés (SSO) engedélyezése után.**

Ez akkor fordulhat elő, ha az alapul szolgáló adatkészlet egy helyszíni adatátjárón keresztül a DirectQuery módban, vagy az Analysis Services élő kapcsolat használatára van konfigurálva. Ebben az esetben a csempék továbbra is a nem szűrt adatok után SSO engedélyezése az adatforrás, amíg a következő csempefrissítés határideje. A következő csempék frissítését, a Power BI az egyszeri bejelentkezés konfigurálva, és a csempék megjelenítése a felhasználói identitás alapján szűri az adatokat. 

Ha szeretné azonnal meg is tekintheti a szűrt adatokat, egy csempefrissítés kényszerítheti a egy irányítópultot, a jobb felső sarokban a három pontra (...) kiválasztásával **az irányítópult csempéinek frissítése**.

Egy adatkészlet tulajdonosa is módosíthatja a csempe frissítési gyakoriságot és beállíthatja azt a 15 perc és gyorsítsa fel a csempe frissítése. Kattintson a fogaskerék ikonra a Power BI szolgáltatás jobb felső sarokban, majd válassza ki **beállítások**. Az a **beállítások** lapon válassza ki a **adatkészletek** fülre. Bontsa ki a **ütemezett gyorsítótár-frissítés** , és módosítsa **frissítési gyakoriság**. Ellenőrizze, hogy konfigurációjának visszaállítása az eredeti frissítési gyakoriságot, miután a Power BI a következő csempék frissítését hajtja végre.

> [!NOTE]
> A **ütemezett gyorsítótár-frissítés** szakaszban csak adatkészleteket a DirectQuery/LiveConnection módban érhető el. Adatkészleteket az importálási mód nem igényel külön csempék frissítését, mert a csempék automatikusan frissülnek a következő ütemezett frissítés során.

## <a name="contact-support"></a>Kapcsolatfelvétel az ügyfélszolgálattal
Ha a probléma továbbra is fennáll, [kérjen támogatást](https://support.powerbi.com) a további vizsgálat érdekében.

## <a name="next-steps"></a>Következő lépések
[A Helyszíni adatátjáróval kapcsolatos hibák elhárítása](service-gateway-onprem-tshoot.md)  
[A Power BI Personal Gateway hibáinak elhárítása](service-admin-troubleshooting-power-bi-personal-gateway.md)  
További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

