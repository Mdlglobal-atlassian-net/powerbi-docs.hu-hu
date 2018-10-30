---
title: A Power BI Premium-kapacitás memóriahasználata és optimalizálása
description: Ismerkedjen meg a Power BI Premium-kapacitás memóriakezelésével és annak optimalizálásával.
ms.date: 10/18/2018
ms.topic: conceptual
ms.service: powerbi
ms.component: powerbi-admin
ms.author: mblythe
ms.reviewer: mblythe
author: mgblythe
manager: kfile
ms.openlocfilehash: 99c84aff932c7ce56a4aaa81d71e4583bce3e4c2
ms.sourcegitcommit: a764e4b9d06b50d9b6173d0fbb7555e3babe6351
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/22/2018
ms.locfileid: "49641741"
---
# <a name="microsoft-power-bi-premium-capacity-resource-management-and-optimization"></a>Microsoft Power BI Premium-kapacitások erőforrás-kezelése és optimalizálása

Ez a cikk bemutatja, hogyan kezeli a Power BI Premium az erőforrásokat, valamint példákat és hibaelhárítási javaslatokat is tartalmaz. Az áttekintésért lásd [Mi a Power BI Premium?](service-premium.md)

## <a name="premium-capacity-memory-management"></a>A prémium szintű kapacitás memóriakezelése

 A prémium szintű kapacitás memóriafelhasználása:

* Memóriába betöltött adathalmazok
* Adathalmaz frissítése (ütemezett és igény szerinti)
* Jelentéslekérdezések

Amikor a kapacitáson belül egy közzétett adatkészletre vonatkozó kérelem érkezik, az adott adatkészletet a rendszer az állandó tárolóból tölti be a memóriába (ezt a folyamatot lemezkép betöltésének is nevezzük). Ha az adatkészlet betöltve marad a memóriában, az adatkészletre vonatkozó későbbi lekérdezések esetén rövidebb lesz a válaszidő. Az adathalmazok memóriában való tárolásához szükséges memórián kívül a jelentéslekérdezések és az adathalmaz-frissítések is memóriahasználattal járnak.

### <a name="dataset-memory-estimation"></a>Az adatkészlet becsült memóriafelhasználása

Amikor megkísérli betölteni az adathalmazt a memóriába, a Power BI megbecsüli, hogy mennyi memóriára lesz szüksége az adathalmaznak a kért parancs végrehajtásához. A memóriában tárolt adathalmazok általában nagyobb méretűek a lemezre mentett adathalmazoknál. Az adathalmaz-frissítés során a Power BI-nak legalább kétszer annyi memóriára van szüksége, mint az adathalmaz tétlen állapotában.

### <a name="overcommitting-capacity-eviction-and-reloading-of-datasets"></a>Kapacitás túlterhelése, kizárás és adatkészletek újbóli betöltése

A Power BI Premium lehetővé teszi a kapacitás *túlterhelését*. Közzétehet például több adathalmazt, mint amennyit a kapacitás tárolni tud. Ha a közzétett adathalmazoknak több memóriára van szükségük, mint amennyi a kapacitásban elérhető, egyes adathalmazokat külön, állandó tárolóban tárol a rendszer. Az állandó tároló az egyes kapacitásokhoz tartozó 100 TB-os tárterület részét képezi.

Tehát melyik adathalmazok maradnak a memóriában, és mi történik a többi adathalmazzal? Ahogyan korábban már leírtuk, amikor kérelem érkezik egy adott adatkészletre vonatkozóan, az adatkészlet betöltődik a memóriába (lemezkép betöltése). A kérelem lehet jelentéslekérdezés vagy frissítési műveletet. Mivel megengedett a kapacitástúlterhelés, a kapacitás esetében is előfordulhat memóriatúlterhelés. Ez esetben a csomópont egy vagy több adathalmazt *kizár* a memóriából. Először az inaktív adathalmazok (nincs végrehajtás alatt álló lekérdezési/frissítési művelet) lesznek kizárva. Ezután a „legrégebben használt” (LRU) paraméter értéke határozza meg a kizárási sorrendet. Ha új parancsot ad ki egy kizárt adathalmazra, a szolgáltatás megkísérli újból betölteni az adathalmazt a memóriába, szükség esetén más adathalmazok kizárásával. Ez a működési mód nagyobb kihasználtságot és hatékonyságot biztosít, mivel a kapacitás így sokkal több adatkészletet tud kiszolgálni, mint amennyi a memóriájában elfér.

Az adatkészletek memóriába történő betöltése viszonylag erőforrás-igényes művelet. A folyamat időtartama az adathalmaz méretétől függően változik: kis adathalmazok esetén néhány másodpercig, míg nagy, például 10 GB-os nagyságrendű adathalmazok esetén több tíz másodpercig, vagy akár percekig is tarthat. Prémium szintű kapacitás esetén a rendszer a legrégebben használt adatkészleteket igyekszik minél tovább a memóriában tárolni, hogy a kapacitást minél kevesebbszer kelljen újratölteni. Ha további memóriára van szükség, ki kell zárni egy vagy több adatkészletet, a rendszer pedig megpróbálja kiválasztani azokat, amelyek kizárása a legkevésbé befolyásolja majd a felhasználói élményt. Ha további memóriára van szükség, ki kell zárni egy vagy több adatkészletet, a rendszer pedig megpróbálja kiválasztani azokat, amelyek kizárása a legkevésbé befolyásolja majd a felhasználói élményt. A rendszer például kerülni fogja a legutóbbi néhány percben használt adathalmazok kizárását. Valószínű, hogy ezeket az adathalmazokat rövidesen újra le fogják kérdezni.

Maga a kizárási folyamat egy gyors művelet. Ha kizáráskor az adatkészlet épp nincsen használatban, a felhasználó nem fog sokat észlelni a kizárásból. Ha azonban egyszerre túl sok adathalmaz van használatban, és nincs elegendő memória az összes tárolásához, több kizárás is történhet. Ha túl sok aktív adathalmazt használ, az „akadozáshoz” vezethet, mivel ekkor a rendszer folyamatosan zárja ki, majd tölti be újra az adathalmazokat, a felhasználók pedig a válaszidő növekedését és a teljesítmény jelentős lecsökkenését tapasztalhatják.

### <a name="dataset-refresh-memory-requirement-competing-with-an-active-dataset-memory-requirement"></a>Az adatkészletek frissítéséhez, valamint a használatban lévő adatkészletekhez szükséges memóriaszükségletek közti versengés

Az adatkészleteket a felhasználók ütemezett módon vagy igény szerint is frissíthetik. Mint korábban említettük, a teljes frissítéshez legalább kétszer annyi memóriára van szükség, mint a betöltött, tétlen adathalmazok esetében. A frissítés megkezdése előtt a rendszer felbecsüli a folyamat memóriaszükségletét. Ha a teljes memóriaszükséglet meghaladja a kapacitáson belül rendelkezésre álló memóriát, a rendszer kizár egy vagy több adatkészletet. A kizárási sorrendet ez esetben is az LRU határozza meg.

Ha a kizárás ellenére sem áll rendelkezésre elegendő memória, a rendszer újbóli végrehajtás céljából sorba állítja a frissítési folyamatot. A szolgáltatás egészen addig próbálja újra és újra végrehajtani a folyamatot, amíg sikerrel nem jár, vagy amíg el nem indul egy másik frissítési folyamat.

Ha interaktív lekérdezés érkezik bármelyik adatkészlethez kapcsolódóan a kapacitáson belül, egy folyamatban lévő frissítés miatt azonban nem áll rendelkezésre elegendő memória, az említett kérelem sikertelen lesz, és a felhasználónak újból végre kell azt hajtania.

## <a name="cpu-resource-management-in-premium-capacity"></a>A CPU erőforrás-kezelése prémium szintű kapacitás esetén

A CPU erőforrásait elsősorban az alábbi két folyamat használja:

* Jelentéslekérdezések
* Frissítés (feldolgozás)

### <a name="queries-from-reports"></a>Jelentéslekérdezések

A jelentéslekérdezések a kapacitásban található processzor-erőforrásokat használják. A kevésbé hatékony jelentéslekérdezések és a sok egyidejű felhasználó nagy processzorhasználatot eredményezhetnek. Előfordulhat, hogy a meglévő kapacitás már nem lesz elegendő a terhelés kezeléséhez.

### <a name="refresh-parallelization-policy"></a>A párhuzamos frissítésekre vonatkozó irányelv

Nem a memória az egyetlen olyan erőforrás, amely korlátozhatja az adathalmazok frissíthetőségét. Az adott kiszolgáló virtuális magjainak száma szintén befolyásolhatja a folyamatokat. Mivel minden egyes frissítési művelethez meghatározott számú virtuális magra van szükség, a párhuzamosan futtatható frissítések száma korlátozott. Az alábbi táblázat az egyes termékváltozatokra vonatkozó felső határértéket mutatja. Ha a frissítések száma túllépi ezt az értéket, akkor a további műveletek várólistára kerülnek.

 | Termékváltozat | Háttérrendszeri virtuális magok | Párhuzamos frissítések modellezése |
 | --- | --- | --- |
 | A1  | 0,5  | 1  |
 | A2  | 1  | 2  |
 | A3  | 2  | 3  |
 | A4  | 4  | 6  |
 | A5  | 8  | 12  |
 | A6  | 16  | 24  |
 | EM1  | 0,5  | 1  |
 | EM2  | 1  | 2  |
 | EM3  | 2  | 3  |
 | P1  | 4  | 6  |
 | P2  | 8  | 12  |
 | P3  | 16  | 24  |
 | P4  | 32  | 48  |
 | P5  | 64  | 96  |

 > [!TIP]
> Ha a frissítések késnek, ellenőrizze a kapacitás által támogatott párhuzamos frissítések számát.

## <a name="example-scenarios"></a>Esetpéldák

Az alábbiakban néhány gyakori alkalmazási helyzet, valamint a szolgáltatás által végrehajtott műveletek láthatók:

**Húsz ütemezett frissítés egyidejű elküldése**. A Power BI megkísérli egyszerre elindítani az első *x* frissítést. Az *x* értékét az adott termékváltozat párhuzamos frissítésekre vonatozó irányelve határozza meg. Ha a Power BI nem tud elég memóriát felszabadítani az inaktív (régebben használt) adatkészletek kizárásával, nem fog az *összes* frissítés egy időben elindulni. Az aktuálisan nem indítható frissítéseket a rendszer átmenetileg várólistára helyezi.

**Két frissítés fut egyszerre, de csak az egyik befejezéséhez van elegendő memória**. Az a frissítés, amelyik le tud futni, elindul. A másikat a rendszer megpróbálja később újból végrehajtani.

**Sok adathalmaz lekérdezése több adathalmaz frissítése közben**. Ha nincs elég memória, a Power BI megkísérli leállítani a folyamatban lévő frissítéseket, prioritást adva az interaktív lekérdezéseknek. Emiatt a frissítési teljesítmény csökken.

**Az adathalmaz frissítéséhez túl sok memóriára van szükség a kapacitás aktuális méretéhez viszonyítva**. A frissítés meghiúsul. A rendszer nem kísérli meg további memória felszabadítását az adatkészletek kizárásával.

**Egyetlen, kiugróan magas memóriahasználattal járó adathalmaz-frissítés**. Ha a csúcsidei memóriaszükséglet túllépi az inaktív adathalmazok kizárásával felszabadítható memória mennyiségét, a rendszer később újból megkísérli végrehajtani a frissítést, egészen addig, amíg a szükségletnek megfelelő mennyiségű memória rendelkezésre nem áll.

**Olyan adathalmaz lekérdezése, amely esetében a rendszer nem képes elegendő memóriát felszabadítani az inaktív adathalmazok és a frissítési műveletek kizárásával**. Ezek a lekérdezések meghiúsulnak. Az ilyen típusú munkaterhelési követelmények esetén nagyobb kapacitást kell megvásárolnia.

## <a name="troubleshooting-and-testing"></a>Hibaelhárítás és tesztelés

Ha a jelentések lassúak vagy nem válaszolnak, teszteljen egy jelentést először egyetlen egy felhasználó esetén. Ezután kezdje el megemelni az egyidejű felhasználók számát, hogy kiderítse, hány felett lassul le a rendszer. Sok esetben a DAX-lekérdezések finomhangolása jelentősen módosíthatja a jelentéskészítési teljesítményt. A lekérdezések finomhangolásával továbbá megnövelhető a kapacitás által támogatott párhuzamos felhasználók száma. [A kapacitás monitorozásával](service-admin-premium-monitor-capacity.md) azonosíthatók a lehetséges teljesítményproblémák.

Használjon Power BI Embedded-kapacitást az Azure-ban, hogy a különféle termékváltozatok tesztelését követően eldönthesse, melyik a legmegfelelőbb Premium termékváltozat az Ön számára feltételezett munkaterhelése alapján. A Power BI Embedded A4 termékváltozata a P1-gyel, az A5 a P2-vel, az A6 pedig a P3-mal egyezik meg. Az Azure Portal felületén egyszerűen váltogathat a kisebb vagy nagyobb kapacitású termékváltozatok között. Miután megtalálta a munkaterheléséhez legmegfelelőbb termékváltozatot, és befejezte a tesztelést, törölheti is a termékváltozatot.

Bizonyos esetekben sokat megtudhat az adott problémáról, ha megnyitja számítógépén a modell Power BI Desktop- (PBIX-) fájlját, illetve ellenőrzi a memória- és a CPU-használatot. Kisebb modellek esetén próbálkozzon azzal, hogy megnyitja a modellt a számítógépéről, frissíti, majd lekérdezéseket küld rá. Nagyon nagy modellek esetén azonban ez nem fog működni. A modell megnyitásakor ellenőrizze a modell méretét, valamint a memória- és a CPU-felhasználást. Próbáljon meg frissíteni és lekérdezéseket indítani. A feladatkezelővel ellenőrizheti a helyi fájl processzor- és memóriafelhasználását. Néha magának a számítógépnek a metrikáiból is kiderül, hogy egy alacsonyabb (pl. P1/P2) prémium szintű kapacitás nem feltétlen elegendő az Ön számára.

## <a name="next-steps"></a>Következő lépések

[Kapacitáskezelés a Power BI Premiumban és a Power BI Embeddedben](service-admin-premium-manage.md)