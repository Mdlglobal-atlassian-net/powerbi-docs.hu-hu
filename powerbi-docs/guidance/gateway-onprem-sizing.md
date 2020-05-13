---
title: Helyszíni adatátjáró méretezése
description: Útmutató a helyszíni adatátjáró működőképes méretezéséhez.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/30/2019
ms.author: v-pemyer
ms.openlocfilehash: de84dd7e9021abf1198f2dc4f910afb8bd078ac6
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83279526"
---
# <a name="on-premises-data-gateway-sizing"></a>Helyszíni adatátjáró méretezése

Ez a cikk azoknak a Power BI-rendszergazdáknak szól, akiknek [helyszíni adatátjárót](../connect-data/service-gateway-onprem.md) kell telepíteniük és felügyelniük.

Az átjáróra akkor van szükség, ha a Power BI-nak az interneten közvetlenül nem elérhető adatokhoz kell hozzáférnie. Telepíthető helyszíni kiszolgálóra, vagy virtuális gépen üzemeltetett szolgáltatott infrastruktúrára (IaaS).

## <a name="gateway-workloads"></a>Az átjáró feladatai

A helyszíni adatátjáró két munkafolyamatot végez. Mielőtt rátérnénk az átjáró méretezésére és a javaslatokra, fontos tisztában lenni ezekkel a folyamatokkal.

### <a name="cached-data-workload"></a>Gyorsítótárazott adatok kezelése

A _gyorsítótárazott adatokhoz_ kapcsolódó munkafolyamat olvassa be és alakítja át a Power BI-adathalmazokba betöltendő forrásadatokat. Ezt három lépésben végzi el:

1. **Kapcsolódás**: Az átjáró kapcsolódik a forrásadatokhoz
1. **Adatbeolvasás és átalakítás**: A lekért adatok szükség esetén át lesznek alakítva. Amikor csak lehetséges, a Power Query adategyesítési motor leküldi az átalakítási lépéseket az adatforrásba – ez az úgynevezett _[lekérdezésdelegálás](power-query-folding.md)_ . Ha ez nem lehetséges, akkor az átalakításokat az átjárónak kell elvégeznie. Ebben az esetben az átjáró több CPU- és memória-erőforrást használ.
1. **Átvitel**: A rendszer átviszi az adatokat a Power BI szolgáltatásba – fontos a megbízható és gyors internetkapcsolat, főleg nagy adatmennyiségek esetén

![Egy ábra mutatja be a helyszíni adatátjárót, amely helyszíni forrásokhoz: relációs adatbázishoz, Excel-munkafüzethez és CSV-fájlokhoz csatlakozik. Az átjáró beolvassa és átalakítja az adatokat.](media/gateway-onprem-sizing/gateway-onprem-workload-cached-data.png)

### <a name="live-connection-and-directquery-workloads"></a>Élő kapcsolatú és DirectQuery-munkafolyamatok

Az _élő kapcsolatot és DirectQuery-t_ használó munkafolyamat többnyire átmenő módban működik. A Power BI szolgáltatás lekérdezéseket küld, az átjáró pedig a lekérdezési eredményekkel válaszol. A lekérdezési eredmények mérete általában kicsi.

- További információ az élő kapcsolatokról: [Adathalmazok a Power BI szolgáltatásban (külső üzemeltetésű modellek)](../connect-data/service-datasets-understand.md#external-hosted-models).
- További információ a DirectQuery-ről: [Adathalmaz-módok a Power BI szolgáltatásban (DirectQuery mód)](../connect-data/service-dataset-modes-understand.md#directquery-mode).

Ez a folyamat a lekérdezések és a lekérdezési eredmények forgalmának irányításához igényel CPU-erőforrásokat. A CPU-igénye általában kisebb, mint a gyorsítótárazott adatokat kezelő munkafolyamaté – különösen akkor, ha gyorsítótárazandó adatok átalakításához van rá szükség.

A megbízható, gyors és konzisztens kapcsolat elengedhetetlen annak biztosításához, hogy a felhasználói felület gyorsan reagáljon.

![Egy ábra mutatja be a helyszíni adatátjárót, amely helyszíni forrásokhoz csatlakozik: Táblázatos Analysis Services- és relációs adatbázishoz. Az átjáró többnyire átmenő módban működik.](media/gateway-onprem-sizing/gateway-onprem-workload-liveconnection-directquery.png)

## <a name="sizing-considerations"></a>Méretezési szempontok

Az átjáró-számítógép megfelelő méretének meghatározása az alábbi változóktól függhet:

- Gyorsítótáras munkafolyamatokhoz:
  - Az egyidejű adathalmaz-frissítések száma
  - Az adatforrások típusai (relációs adatbázis, analitikai adatbázis, adatcsatornák vagy fájlok)
  - Az adatforrásokból lekérendő adatok mennyisége
  - A Power Query adategyesítési motor által végrehajtandó átalakítások
  - A Power BI szolgáltatásnak továbbítandó adatok mennyisége
- Élő kapcsolatú és DirectQuery-munkafolyamatokhoz:
  - A jelentést egyidejűleg használó felhasználók száma
  - A jelentésoldalakon lévő vizualizációk száma (minden vizualizáció legalább egy lekérdezést küld)
  - A Power BI-irányítópult lekérdezési gyorsítótárának frissítési gyakorisága
  - Az [Automatikus oldalfrissítés](../create-reports/desktop-automatic-page-refresh.md) funkciót használó valós idejű jelentések száma
  - Alkalmaznak-e az adathalmazok [sorszintű biztonságot (RLS)](../create-reports/desktop-rls.md)

Az élő kapcsolatú és DirectQuery-munkafolyamatokhoz általában elegendő CPU-ra van szükség, a gyorsítótárazott adatokat kezelő munkafolyamatok viszont több CPU-t és memóriát igényelnek. Mindkét munkafolyamathoz jó minőségű kapcsolat szükséges a Power BI szolgáltatás és az adatforrások felé.

> [!NOTE]
> A Power BI-kapacitások korlátozzák a párhuzamosan végrehajtható modellfrissítéseket, valamint az élő kapcsolatok és a DirectQuery átviteli sebességét. Nincs értelme nagyobb teljesítményre méretezni az átjárót, mint amekkorát a Power BI szolgáltatás támogat. A különböző prémium szintű SKU-k (és méretben azokkal egyenértékű A SKU-k) korlátai eltérőek. További információ: [A Power BI Premium bemutatása (Kapacitás-csomópontok)](../admin/service-premium-what-is.md#capacity-nodes).

## <a name="recommendations"></a>Javaslatok

Az átjáró méretezésére vonatkozó javaslatok sok változó függvényei. Ebben a szakaszban megfontolásra érdemes, általános javaslatokat teszünk.

### <a name="initial-sizing"></a>Kezdeti méretezés

A megfelelő méretet olykor nehéz pontosan megbecsülni. Javasoljuk, hogy induljon ki egy legalább 8 CPU-maggal, 8 GB memóriával és gigabites hálózati adapterekkel rendelkező gépből. Ezzel már mérni tudja az átjáró jellemző terhelését a CPU- és a memóriarendszer számlálóinak naplózásával. További információ: [Helyszíni adatátjáró teljesítményének figyelése és optimalizálása](/data-integration/gateway/service-gateway-performance).

### <a name="connectivity"></a>Kapcsolatok

Tervezzen a lehető legjobb kapcsolattal a Power BI szolgáltatás és az átjáró, valamint az átjáró és az adatforrások között.

- Törekedjen a megbízhatóságra, a gyorsaságra és a következetesen alacsony késésre
- Iktassa ki – vagy csökkentse – az átjáró és az adatforrás közötti ugrásokat
- Szüntesse meg a tűzfal-proxy réteg által megvalósított sávszélesség-szabályozást. További információ a Power BI-végpontokról: [Engedélyezési listára helyezendő Power BI URL-címek](../admin/power-bi-whitelist-urls.md).
- Az [Azure ExpressRoute](/azure/expressroute/expressroute-introduction) konfigurálásával alakítson ki privát, felügyelt kapcsolatokat a Power BI-jal
- Azure-beli virtuális gépeken lévő adatforrások esetén gondoskodjon arról, hogy a virtuális gépek [a Power BI szolgáltatással közösen legyenek elhelyezve](../admin/service-admin-where-is-my-tenant-located.md)
- A dinamikus sorszintű biztonságot érvényesítő SQL Server Analysis Services (SSAS) forrással élő kapcsolatban dolgozó munkafolyamatok számára biztosítson jó minőségű kapcsolatot az átjáró-számítógép és a helyszíni Active Directory között

### <a name="clustering"></a>Fürtözés

Nagyméretű üzembe helyezésekhez átjárófürtöket telepíthet. A fürtök kiiktatják a rendszerkritikus meghibásodási pontokat, és terheléselosztást végezhetnek az átjárókon áthaladó forgalommal. A következőket teheti:

- Telepítsen egy vagy több átjárót egy fürtben
- A munkafolyamatokat különítse el önálló átjárókra, vagy átjárókiszolgáló-fürtökre

További információ: [Magas rendelkezésre állású helyszíni adatátjáró-fürtök és terheléselosztás kezelése](/data-integration/gateway/service-gateway-high-availability-clusters).

### <a name="dataset-design-and-settings"></a>Adathalmaz-tervezés és -beállítások

Az adathalmazok kialakítása és beállításai befolyásolhatják az átjárók terhelését. Az átjáró terhelésének csökkentése érdekében az alábbi teendőket érdemes mérlegelni.

Importálás módú adathalmazokhoz:

- Konfiguráljon kevésbé gyakori adatfrissítést
- Konfiguráljon [növekményes frissítést](../admin/service-premium-incremental-refresh.md), ezzel minimalizálva az átvitt adatok mennyiségét
- Amikor csak lehetséges, törekedjen a [lekérdezések delegálására](power-query-folding.md)
- Főleg nagy adatmennyiségek esetén, vagy ha kis késésű eredményekre van szükség, alakítsa át a tervet DirectQuery- vagy [Összetett](../connect-data/service-dataset-modes-understand.md#composite-mode) modellre

DirectQuery-adathalmazokhoz:

- Optimalizálja az adatforrások, a modell és a jelentések terveit – erről az [Útmutató a Power BI Desktop DirectQuery-modelljeihez](directquery-model-guidance.md) című cikkben talál további információt
- Hozzon létre [összesítéseket](../transform-model/desktop-aggregations.md), hogy a magasabb szintű eredmények gyorsítótárazásával csökkentse a DirectQuery-kérelmek számát
- Korlátozza az [automatikus oldalfrissítés](../create-reports/desktop-automatic-page-refresh.md) gyakoriságát a jelentések kivitelezésében és a kapacitásbeállításokban
- Korlátozza az irányítópult-gyorsítótár frissítési gyakoriságát, főleg akkor, ha dinamikus sorszintű biztonság van érvényben
- Elsősorban a kisebb adatmennyiségek vagy nem gyakran változó adatok esetében konvertálja a tervet Importálás vagy [Összetett](../connect-data/service-dataset-modes-understand.md#composite-mode) módú modellre

Élő kapcsolatú adathalmazokhoz:

- Korlátozza az irányítópult-gyorsítótár frissítési gyakoriságát, főleg akkor, ha dinamikus sorszintű biztonság van érvényben

## <a name="next-steps"></a>Következő lépések

Ezzel a cikkel kapcsolatosan a következő forrásanyagokban talál további információt:

- [Útmutató adatátjáró üzembe helyezéséhez a Power BI-hoz](../connect-data/service-gateway-deployment-guidance.md)
- [Helyszíni adatátjáró proxybeállításainak konfigurálása](/data-integration/gateway/service-gateway-proxy)
- [Helyszíni adatátjáró teljesítményének figyelése és optimalizálása](/data-integration/gateway/service-gateway-performance)
- [Átjárók hibaelhárítása – Power BI](../connect-data/service-gateway-onprem-tshoot.md)
- [A helyszíni adatátjáró hibaelhárítása](/data-integration/gateway/service-gateway-tshoot)
- [A lekérdezésdelegálás fontossága](power-query-folding.md)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
- Javaslatai vannak? [A Power BI javítására vonatkozó ötletek beküldése](https://ideas.powerbi.com)
