---
title: Gyakori kérdések – Power BI-beli egyéni vizualizációk
description: Az alábbiakban a Power BI egyéni vizualizációival kapcsolatos gyakori kérdések és válaszok listáját tekintheti át.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 10/29/2018
LocalizationGroup: Visualizations
ms.openlocfilehash: 064d32944f52f6e391d4a7ec4df41ecbf09b7e3f
ms.sourcegitcommit: 02f918a4f27625b6f4e47473193ebc8219db40e2
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/07/2018
ms.locfileid: "51223076"
---
# <a name="frequently-asked-questions-about-power-bi-custom-visuals"></a>Gyakori kérdések – Power BI-beli egyéni vizualizációk

## <a name="organizational-custom-visuals"></a>Egyéni szervezeti vizualizációk

**Hogyan felügyelheti a rendszergazda az egyéni szervezeti vizualizációkat?**

A felügyeleti portál „Egyéni szervezeti vizualizációk” lapján a rendszergazda megtekintheti és [felügyelheti a vállalat összes egyéni szervezeti vizualizációját](https://docs.microsoft.com/power-bi/service-admin-portal#organization-visuals): hozzáadhat, letilthat, engedélyezhet és törölhet.
Most már nem kell megosztani ezeket a vizualizációkat e-mailek vagy megosztott mappák segítségével. A szervezeti adattárban való üzembe helyezésük után a szervezet felhasználói könnyedén észrevehetik őket, és közvetlenül a Power BI Desktopból vagy szolgáltatásból importálhatják az egyéni szervezeti vizualizációkat a jelentéseikbe. Az egyéni szervezeti vizualizációk a beépített áruházból érhetők el (az asztali verzióban és a szolgáltatásban is), a „SAJÁT SZERVEZET” lapon. Miután a rendszergazda feltölti egy egyéni szervezeti vizualizáció új verzióját, a szervezet összes tagja megkapja ugyanazt a frissített verziót. A jelentések létrehozóinak nem kell törölniük a vizualizációt a jelentésükből a vizualizáció új verziójának beszerzéséhez, és a rendszer automatikusan frissíti az adott vizualizációt használó összes jelentést. A frissítési mechanizmus hasonló a piactéren beszerzett vizualizációkéhoz.

**Ha egy rendszergazda feltölt egy egyéni vizualizációt a nyilvános piactérről a szervezet áruházába, az automatikusan frissül, ha a készítője frissíti a nyilvános piactéren a vizualizációt?**

Nem, a nyilvános piactérről nem érkezik automatikusan a frissítés.
Az egyéni szervezeti vizualizációk verziójának frissítése – ha igény van rá – a rendszergazda feladata.

**Van lehetőség a szervezeti áruház letiltására?**

Nem, a felhasználók számára mindig megjelenik a „SAJÁT SZERVEZET” lap a Power BI Desktopban és a szolgáltatásban. A rendszergazda letilthatja vagy törölheti az összes egyéni szervezeti vizualizációt a felügyeleti portálról, így a szervezeti áruház üres lesz.
  
**Ha a rendszergazda letiltja az egyéni szervezeti vizualizációkat a felügyeleti portálon (Bérlői beállítások), a felhasználók attól még hozzáféréssel rendelkeznek az egyéni szervezeti vizualizációkhoz?**

Igen. Az, hogy a rendszergazda letiltja az egyéni vizualizációkat a felügyeleti portálon, nincs hatással a szervezeti áruházra. Bizonyos szervezetek letiltják az egyéni vizualizációkat, és csak olyan, válogatott vizualizációk használatát engedélyezik, amelyeket a Power BI-rendszergazda importált és töltött fel a szervezeti áruházba. Az egyéni vizualizáció a felügyeleti portálon történő letiltása nem lesz érvényesítve a Power BI Desktopban. Az asztali verzió felhasználói a jelentéseikben továbbra is hozzáadhatnak és használhatnak egyéni, a nyilvános piactérről származó vizualizációkat. Ezek a nyilvános egyéni vizualizációk azonban nem jelennek meg a Power BI szolgáltatásban való közzététel után, és kiváltják a megfelelő hibaüzenetet. A Power BI szolgáltatás használatakor nem importálhatók egyéni vizualizációk a nyilvános piactérről. Csak a szervezeti áruházból származó vizualizációk importálhatók, mert az egyéni vizualizációk a felügyeleti portálon megadott beállítása érvényesítve lesz a Power BI szolgáltatásban.

**Miért számít kiváló nagyvállalati megoldásnak a szervezeti áruház és az egyéni szervezeti vizualizációk használata?**

* Mindenki a vizualizáció azonos verzióját kapja, amely felett a Power BI-rendszergazda gyakorol irányítást. Ha a rendszergazda frissíti a vizualizáció verzióját a felügyeleti portálon, a szervezet összes felhasználója automatikusan megkapja a frissített verziót.

* Többé nem kell megosztani e-mailben vagy megosztott mappákban a vizualizációs fájlokat. Az összes bejelentkezett felhasználó látja ezt a központi helyet.

* Biztonságos, és számos támogatási lehetőséget biztosít. Az egyéni szervezeti vizualizációk új verziói automatikusan frissülnek minden jelentésben, akárcsak a piactérről beszerzett vizualizációk.

* A szervezet egyéni szervezeti vizualizációkat használó felhasználóinak be kell jelentkezniük, hogy lássák és használhassák a szervezet számára biztonsági tényezőnek számító egyéni szervezeti vizualizációkat.

* A rendszergazdák szabályozhatják, hogy mely egyéni vizualizációk legyenek elérhetők a szervezetben.

* A rendszergazdák a felügyeleti portálról engedélyezhetik/letilthatják a vizualizációkat tesztelési célból. A biztonsági szabályok jobban kikényszeríthetők, hiszen a vizualizációkhoz csak a szervezet tagjai férhetnek hozzá.

## <a name="certified-custom-visuals"></a>Minősített egyéni vizualizációk

**Mik azok a minősített egyéni vizualizációk?**

A minősített egyéni vizualizációk azok a [piactéren](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) lévő vizualizációk, amelyek megfelelnek [bizonyos](power-bi-custom-visuals-certified.md), a Power BI csapata által megadott kódolási és tesztelési előírásoknak.  A végrehajtott tesztek célja az, hogy ellenőrizzék, hogy a vizualizáció nem használ-e külső szolgáltatásokat vagy erőforrásokat. Azonban nem a Microsoft a készítője a külső felek egyéni vizualizációinak, és azt javasoljuk az ügyfeleinknek, hogy közvetlenül a készítővel kapcsolatba lépve ellenőrizzék az ilyen vizualizációk működését.

## <a name="next-steps"></a>Következő lépések

A hibaelhárítással kapcsolatban az [egyéni Power BI-vizualizációk hibáinak elhárítását](power-bi-custom-visuals-troubleshoot.md) ismertető cikkből tájékozódhat.
