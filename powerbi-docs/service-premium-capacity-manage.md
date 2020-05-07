---
title: Microsoft Power BI Premium-kapacitások kezelése
description: A Power BI Premium-kapacitások felügyeleti feladatait ismerteti.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 2e32a61891cee2fb5e2a80167d5283962dc164bb
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "74697474"
---
# <a name="managing-premium-capacities"></a>Prémium szintű kapacitások kezelése

A Power BI Premium kezeléséhez tartozik a Premium-kapacitások létrehozása, kezelése és figyelése. Ez a cikk áttekintést nyújt a kapacitásokról. A lépésenkénti útmutatáshoz tekintse meg a [Kapacitások konfigurálása és kezelése](service-admin-premium-manage.md) című cikket.

## <a name="creating-and-managing-capacities"></a>Kapacitások létrehozása és kezelése

A Power BI Felügyeleti portál **Kapacitásbeállítások** lapján megtekintheti a megvásárolt virtuális magok számát és a rendelkezésre álló Premium-kapacitásokat. Ezen a lapon az Office 365 globális rendszergazdák és a Power BI-szolgáltatásgazdák Premium-kapacitásokat hozhatnak létre a rendelkezésre álló virtuális magokból, vagy módosíthatják a meglévő Premium-kapacitásokat.

Premium-kapacitás létrehozásakor a rendszergazdáknak a következőket kell meghatározniuk:

- Kapacitás neve (a bérlőn belül egyedi).
- Kapacitás-rendszergazdák.
- Kapacitás mérete.
- Adattárolási régió.

Legalább egy kapacitás-rendszergazdát hozzá kell rendelni. A kapacitás-rendszergazdaként hozzárendelt felhasználók a következőket tehetik:

- Munkaterületek hozzárendelése a kapacitáshoz.
- Felhasználói engedélyek kezelése további kapacitás-rendszergazdák vagy hozzárendelési engedélyekkel rendelkező felhasználók hozzáadásához (a munkaterületek kapacitáshoz való hozzárendelésének engedélyezéséhez).
- Munkaterhelések kezelése, a lapszámozott jelentések és az adatfolyamok számítási feladatainak maximális memóriahasználatának konfigurálása.
- A kapacitás újraindítása és az összes művelet visszaállítása rendszertúlterhelés esetén.

A kapacitás-rendszergazdák nem férhetnek hozzá a munkaterületek tartalmához, kivéve, ha erre külön jogosultságot kapnak a munkaterületek engedélyei között. Emellett nincs hozzáférésük a Power BI összes rendszergazdai felületéhez, például a használati metrikákhoz, az auditnaplókhoz és a bérlői beállításokhoz, hacsak nem kapnak erre külön engedélyt. Fontos megjegyezni, hogy a kapacitás-rendszergazdák nem hozhatnak létre új kapacitásokat, és nem méretezhetnek meglévő kapacitásokat. A rendszergazdák hozzárendelése a kapacitások alapján történik, így csak azokat a kapacitásokat tekinthetik meg és kezelhetik, amelyekhez hozzárendelték őket.

A kapacitásméret az SKU-beállítások listájából választható ki, amelyet a készletben elérhető virtuális magok száma korlátoz. A készletből több kapacitás is létrehozható, amely származhat egy vagy több megvásárolt SKU-ból. Egy 32 virtuális maggal rendelkező P3 SKU-val például három kapacitás hozható létre: egy P2 (16 virtuális maggal), és két P1 (egyenként 8 virtuális maggal). Jobb teljesítményt és méretezést érhet el, ha kisebb méretű kapacitásokat hoz létre. Ezt a [Premium-kapacitások optimalizálása](service-premium-capacity-optimize.md) című cikk ismerteti. Az alábbi képen egy mintabeállítás látható a nem létező Contoso nevű céghez, amely öt Premium- (három P1 és kettő P3 szintű) kapacitást tartalmaz, amelyek mindegyikéhez tartoznak munkaterületek, illetve több megosztott kapacitású munkaterület is.

![A nem létező Contoso cég mintabeállítása](media/service-premium-capacity-manage/contoso-organization-example.png)

Premium-kapacitás nem csak a Power BI-bérlő saját régiójához rendelhető hozzá. Ezt Multi-geo konfigurációnak nevezzük. A Multi-geo konfiguráció felügyeleti vezérlést nyújt afelett, hogy a meghatározott földrajzi helyek mely adatközpontjaiban tárolja a Power BI-tartalmat. A Multi-geo üzembe helyezés vállati vagy kormányzati megfelelőség esetén lehet célszerű, és kevésbé szolgálja nagyobb teljesítményt és méretezést. A jelentések és irányítópultok betöltéséhez továbbra is szükségesek a saját régióból lekért metaadatok. További információk: [Multi-Geo-támogatás a Power BI Premiumhoz](service-admin-premium-multi-geo.md).

A Power BI-szolgáltatásgazdák és az Office 365 globális rendszergazdái módosíthatják a Premium-kapacitásokat. Ők a következő műveleteket végezhetik el:

- A kapacitásméret módosítása az erőforrások vertikális fel- és leskálázásához.
- Kapacitás-rendszergazdák hozzáadása és eltávolítása.
- Hozzárendelési engedélyekkel rendelkező felhasználók hozzáadása és eltávolítása.
- További munkaterhelések hozzáadása és eltávolítása.
- Régiók módosítása.

Egy munkaterület egy adott Premium-kapacitáshoz való hozzárendeléséhez hozzárendelési engedélyre van szükség. Ez megadható a teljes vállalatnak, csak adott felhasználóknak, vagy egyes csoportoknak.

A Premium-kapacitások alapértelmezés szerint a Power BI-lekérdezésekkel társított számítási feladatokat támogatják. A Premium-kapacitások emellett további számítási feladatokat is támogatnak: **AI (Cognitive Services)** , **lapszámozott jelentések** és **adatfolyamok**. Minden számítási feladathoz a számítási feladat által felhasználható maximális memória konfigurálása szükséges (a teljes rendelkezésre álló memória arányában). Fontos észben tartani, hogy a maximális memórialefoglalások növelése hatással lehet az üzemeltethető aktív modellek számára, valamint a frissítések átviteli sebességére. 

A memória adatfolyamokhoz dinamikusan, lapszámozott jelentésekhez viszont statikusan van lefoglalva. A maximális memória statikus lefoglalásának oka az, hogy a lapszámozott jelentések a kapacitás egy biztonságosan elzárt területén futnak. Óvatosan állítsa be a lapszámozott jelentések memóriáját, mivel ez csökkenti a modellek betöltéséhez használható memóriát. További információ: [Alapértelmezett memóriabeállítások](service-admin-premium-workloads.md#default-memory-settings).

A Premium-kapacitások törölhetők, és ezzel nem törlődnek azok munkaterületei és tartalma. A hozzárendelt munkaterületek ilyen esetekben a megosztott kapacitásba kerülnek. Amikor a Premium-kapacitást egy másik régióban hozza létre, a munkaterület a saját régió megosztott kapacitásába kerül.

### <a name="assigning-workspaces-to-capacities"></a>Munkaterületek hozzárendelése kapacitásokhoz

Munkaterületeket a Power BI Felügyeleti portálján, vagy munkaterületek esetén a **Munkaterület** panelen rendelhet hozzá egy Premium-kapacitáshoz.

A kapacitás-rendszergazdák, az Office 365 globális rendszergazdái és a Power BI-szolgáltatásgazdái tömegesen rendelhetnek hozzá munkaterületeket a Power BI Felügyeleti portálján. A tömeges hozzárendelés a következőkre vonatkozhat:

- **Munkaterületek felhasználók szerint** – A felhasználói tulajdonban álló munkaterületek, így a személyes munkaterületek is, a Premium-kapacitáshoz vannak rendelve. Ez azt is jeleneti, hogy a munkaterületek ismét hozzá lesznek rendelve, ha már egy másik Premium-kapacitáshoz tartoznak. Emellett a felhasználók is kapnak munkaterület-hozzárendelési engedélyt.

- **Adott munkaterületek**
- **A teljes cég munkaterületei** – Minden munkaterület, így a személyes munkaterületek is, a Premium-kapacitáshoz vannak rendelve. Minden jelenlegi és jövőbeli felhasználó kap munkaterület-hozzárendelési engedélyt. Ezt a módszert nem javasoljuk. Célszerű egy célzottabb megközelítést alkalmazni.

A Premium-kapacitáshoz a **Munkaterület** panelen adható hozzá munkaterület, feltéve, hogy a felhasználó a munkaterület rendszergazdája, és rendelkezik hozzárendelési engedéllyel.

![Munkaterület hozzárendelése a Premium-kapacitáshoz a Munkaterület panelen](media/service-premium-capacity-manage/assign-workspace-capacity.png)

A munkaterületek rendszergazdái eltávolíthatnak munkaterületeket a kapacitásból (és áthelyezhetik azokat a megosztott kapacitásba) anélkül, hogy ehhez hozzárendelési engedéllyel kelljen rendelkezniük. Ha eltávolít egy munkaterületet egy dedikált kapacitásból, azzal tulajdonképpen áthelyezi a munkaterületet egy megosztott kapacitásba. A munkaterületek egy Premium-kapacitásból való eltávolítása negatív következményekkel járhat, a tartalom például elérhetetlenné válhat a Power BI ingyenes licencével rendelkező felhasználói számára, vagy leállhat az ütemezett frissítés, ha az meghaladja a támogatott kapacitások által támogatott keretet.

A Power BI szolgáltatásban egy Premium-kapacitáshoz rendelt munkaterület könnyen felismerhető a munkaterület neve melletti gyémánt ikonról.

![Premium-kapacitáshoz rendelt munkaterület azonosítása](media/service-premium-capacity-manage/premium-diamond-icon.png)

## <a name="monitoring-capacities"></a>Kapacitások figyelése

A Premium-kapacitások figyelésével a rendszergazdák képet kaphatnak a kapacitások teljesítményéről. Kapacitások a Power BI Felügyeleti portál és a **Power BI Premium kapacitásmetrikák** (Power BI) alkalmazás használatával figyelhetők.

### <a name="power-bi-admin-portal"></a>Power BI felügyeleti portál

A Felügyeleti portál **Állapot** lapján megtekintheti az egyes kapacitások és az engedélyezett számítási feladatok összesített metrikáit. A metrikák az elmúlt hét nap átlagát jelenítik meg.  

A kapacitásszinten a metrikák az összes engedélyezett számítási feladat összesítését jelenítik meg. A következő metrikák érhetők el:

- **CPU-KIHASZNÁLTSÁG** – A kapacitásban rendelkezésre álló processzorhasználat átlagos CPU-kihasználtsága (százalékban).  
- **MEMÓRIAHASZNÁLAT** – A kapacitásban elérhető összes memória átlagos memóriahasználata (GB-ban). 

A CPU-kihasználtság és a memóriahasználat minden engedélyezett számítási feladathoz megtekinthető a számítási feladatokra vonatkozó specifikus metrikák mellett. Az Adatfolyam számítási feladat esetén például az **Összesített szám** az egyes adatfolyamok összes frissítését jeleníti meg, míg az **Átlagos időtartam** az adatfolyam frissítéseinek átlagos időtartamát.

![A Kapacitásállapot lap a portálon](media/service-premium-capacity-manage/admin-portal-health-dataflows.png)

További információ a számítási feladatokhoz elérhető metrikákról: [Kapacitások monitorozása a felügyeleti portálon](service-admin-premium-monitor-portal.md).

A Power BI Felügyeleti portál figyelési funkcióival gyors összefoglalót kaphat a legfontosabb kapacitásmetrikákról. Részletesebb figyeléshez célszerű a **Power BI Premium-kapacitásmetrikák** alkalmazást használni.

### <a name="power-bi-premium-capacity-metrics-app"></a>A Power BI Premium-kapacitásmetrikák alkalmazás

A [Power BI Premium-kapacitásmetrikák alkalmazás](https://appsource.microsoft.com/product/power-bi/pbi_pcmm.pbi-premiumcapacitymonitoring?tab=Overview) egy kapacitás-rendszergazdák számára elérhető alkalmazás, amely a többi Power BI-alkalmazáshoz hasonlóan telepíthető. Egy irányítópultot és egy jelentést tartalmaz.

![A Power BI Premium-kapacitásmetrikák alkalmazás](media/service-premium-capacity-manage/capacity-metrics-app.png)

Az alkalmazás megnyitásakor a rendszer betölti az irányítópultot, és számos olyan csempét jelenít meg, amelyek a kapacitás-rendszergazdai felhasználó kapacitásainak összesített nézetét mutatják be. Az irányítópult elrendezése öt fő szakaszt tartalmaz:

- **Áttekintés** – Alkalmazásverzió, valamint a kapacitások és munkaterületek száma
- **Rendszerösszegzés** – Memória- és CPU-metrikák
- **Adatkészlet összegzése** – Adatkészletek, valamint DQ/LC-, frissítési és lekérdezési metrikák száma
- **Adatfolyam összegzése** – Adatfolyamok és adatkészlet-metrikák száma
- **Lapszámozott jelentés összegzése** – Metrikák frissítése és megtekintése

A mögöttes jelentés, amely a rögzített irányítópult-csempék alapja, az irányítópult-csempékre való kattintással érhető el. Részletesebb áttekintést nyújt az irányítópultok egyes részeiről, és támogatja az interaktív szűrést. 

A szűréshez be kell állítania a szeletelőket dátumtartomány, kapacitás, munkaterület és számítási feladat (jelentés, adatkészlet, adatfolyam) szerint, valamint ki kell választania a jelentésvizualizációk elemeit, amelyekkel keresztszűrést végez a jelentésoldalon. A keresztszűrés egy hatékonya technika, amellyel a keresést adott időszakokra, kapacitásokra, munkaterületekre, adatkészletekre és hasonló elemekre korlátozhatja, valamint segít az alapvető okok elemzésében.

További információ az alkalmazásban elérhető irányítópult- és jelentésmetrikákról: [Premium-kapacitások monitorozása az alkalmazással.](service-admin-premium-monitor-capacity.md)

### <a name="interpreting-metrics"></a>A metrikák értelmezése

A metrikák figyelésével megismerheti az erőforrás-használat mértékét és a számítási feladatok tevékenységeit. Ha a kapacitás lelassul, fontos tudnia, hogy mely metrikákat érdemes figyelni, illetve milyen következtetéseket tud levonni belőlük.

Ideális esetben a lekérdezéseknek egy másodpercen belül le kell futniuk, és rugalmasan ki kell tudniuk szolgálni a felhasználókat, így nagyobb átviteli sebességet lehetővé téve. Általában kevésbé jelent problémát, ha a háttérbeli folyamatok (például a frissítések) hosszabb ideig tartanak.

A lassú jelentések általában egy túlhevülő kapacitásra utalnak. Ha a jelentések nem töltődnek be, az egy túlhevült kapacitás jele lehet. Mindkét esetben számos oka lehet a kiváltó oknak, például:

- **Sikertelen lekérdezések**, amelyek memóriaterhelésre utalnak, illetve arra, hogy egy modellt nem sikerült betölteni a memóriába. A Power BI szolgáltatás a hiba előtt 30 másodpercig kísérli meg betölteni a modellt.

- **A lekérdezésekre való túlzott időtartamú várakozásoknak** több oka lehet:
  - A Power BI szolgáltatásnak előbb ki kell zárnia a modelleket, majd be kell töltenie a lekérdezendő modellt (a magas adatkészlet-kizárási arányok önmagukban nem feltétlenül jelentenek magas kapacitásterhelést, hacsak nem társul melléjük hosszú várakozási idő is, amely memóriaakadozásra utalhat).
  - A modellek betöltési ideje (különösen egy nagy méretű modell memóriába való betöltésére való várakozás).
  - Hosszú ideig futó lekérdezések.
  - Túl sok LC\DQ-kapcsolat (amelyek meghaladják a kapacitási korlátokat).
  - CPU-telítettség.
  - Összetett jelentéstervek, amelyek túl sok vizualizációt tartalmaznak egy oldalon (minden vizualizáció egy lekérdezés).

- A **hosszú lekérdezés-időtartamok** azt jelezhetik, hogy a modelltervek nincsenek optimalizálva, különösképp akkor, ha több adatkészlet aktív egy kapacitásban, és nem csak egy adatkészlet eredményez hosszú lekérdezési időket. Ez arra utal, hogy a kapacitás megfelelő erőforrásokkal rendelkezik, és a kérdéses adatkészlet minősége nem optimális, vagy lassú. A hosszú ideig futó lekérdezések problémát okozhatnak, mivel letilthatják a más folyamatok által igényelt erőforrásokhoz való hozzáférést.
- **A hosszú frissítési várakozási idők** azt jelzik, hogy nincs elegendő memória a számos aktív modell miatt, amelyek felhasználják a memóriát, vagy azt, hogy egy hibás frissítés meggátolja a többit (átlépve a párhuzamos frissítési korlátokat).

A metrikák használatáról részletesebb leírást a [Premium-kapacitások optimalizálása](service-premium-capacity-optimize.md) című cikkben találhat.

## <a name="acknowledgements"></a>Nyugták

A cikket Peter Myers, a [Bitwise Solutions](https://www.bitwisesolutions.com.au/) Data Platform MVP-je és független BI-szakértője szerezte.

## <a name="next-steps"></a>Következő lépések

> [!div class="nextstepaction"]
> [Premium-kapacitások optimalizálása](service-premium-capacity-optimize.md)   
> [!div class="nextstepaction"]
> [Számítási feladatok konfigurálása egy Premium-kapacitásban](service-admin-premium-workloads.md)   

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

