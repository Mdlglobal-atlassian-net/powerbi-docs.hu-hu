---
title: A Microsoft Power BI Premium-kapacitás kezelése
description: A Power BI Premium-kapacitásait felügyeleti feladatait ismerteti.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: e4bb907e12d3c0b07408f069d9b238599756e8e0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565251"
---
# <a name="managing-premium-capacities"></a>Prémium szintű kapacitások kezelése

A Power BI Premium kezelése létrehozása, kezelése és figyelése a prémium szintű kapacitások foglalja magában.

## <a name="creating-and-managing-capacities"></a>Létrehozása és kezelése a kapacitások

A **Kapacitásbeállítások** a Power BI felügyeleti portál vásárolt virtuális magok és a prémium szintű kapacitások elérhető számát jeleníti meg. A lap lehetővé teszi, hogy az Office 365 globális rendszergazdák vagy a Power BI szolgáltatás-rendszergazdák a prémium szintű kapacitások létrehozása az elérhető virtuális magok, vagy módosíthatja a meglévő prémium szintű kapacitások.

Amikor hoz létre egy prémium szintű kapacitás, a rendszergazdák meghatározásához van szükség:

- Kapacitás neve (a bérlőn belül egyedi).
- A kapacitás admin(s).
- Kapacitás mérete.
- Adattárolás helye régióban.

Legalább egy kapacitás-rendszergazda kell hozzárendelni. A kapacitás-rendszergazdák hozzárendelt felhasználók:

- Munkaterületek hozzárendelése a kapacitást.
- További kapacitás-rendszergazdák vagy (ahhoz, hogy munkaterületeket rendeljen a kapacitás) hozzárendelési engedélyekkel rendelkező felhasználók hozzáadása a felhasználói engedélyek kezelése.
- Többoldalas jelentések és adatfolyamok számítási feladatok maximális memóriahasználat konfigurálása a számítási feladatok kezelése.
- Indítsa újra a kapacitás, alaphelyzetbe állítása minden művelet egy rendszer túlterhelés miatt.

Kapacitás-rendszergazdák munkaterület-tartalom nem érhető el, ha explicit módon a munkaterület-engedélyek rendelve. Még nem hozzáféréssel rendelkeznek minden Power BI rendszergazdai felületéhez (kivéve, ha explicit módon hozzárendelt) például a használati metrikákat, a naplókhoz és a bérlői beállítások. Ami fontosabb a kapacitás-rendszergazdák nincs engedélye új kapacitások létrehozása vagy meglévő kapacitások skálázhatja. Rendszergazdák száma kapacitás alapon hozzárendelt, annak biztosítása, hogy akkor is csak tekintheti meg és kezelheti a kapacitást, amelyhez hozzá van rendelve.

Kapacitás mérete ki van jelölve egy rendelkezésre álló SKU beállítások listájának, amelyek korlátozzák a készlet rendelkezésre álló magok számát. Lehetséges több kapacitások létrehozása a készletből, amely egy sikerült beolvasva, vagy további termékváltozatok vásárolt. Ha például egy P3 SKU (32 mag) hozzon létre három kapacitások használható: egy P2 (16 mag), és két P1 (2 x 8 mag). Továbbfejlesztett teljesítmény és méret elérhető kisebb méretű kapacitások létrehozásával leírtak szerint a [optimalizálása prémium szintű kapacitások](service-premium-capacity-optimize.md) cikk. Az alábbi képen egy példa a telepítő a fiktív Contoso szervezet öt prémium szintű kapacitások álló (P1, és 2 x 3 x P3) minden egyes tartalmazó alkalmazás-munkaterületek, és számos munkaterületek megosztott kapacitáshoz tartoznak.

![Egy példa a telepítő a fiktív Contoso szervezet számára](media/service-premium-capacity-manage/contoso-organization-example.png)

Prémium szintű kapacitáshoz multi-földrajzi néven ismert Power BI-bérlő otthoni régiója régióban is hozzárendelhető. Multi-földrajzi biztosít a rendszergazda szabályozhatja a Power BI-tartalom található, meghatározott földrajzi régiókban mely adatközpontra. A közösségértékek multi-földrajzi központi telepítés általában van a vállalati vagy kormányzati megfelelőségi, hanem teljesítmény és méretezhetőség. Jelentés és irányítópult betöltésekor továbbra is magában foglalja a kérelmeket a metaadatokat az otthoni régiója. További tudnivalókért lásd: [Multi-földrajzi támogatása a Power BI Premium](service-admin-premium-multi-geo.md).

A Power BI szolgáltatás-rendszergazdák és az Office 365 globális rendszergazdái módosíthatják a prémium szintű kapacitások. Pontosabban ezek a következők:

- Módosítsa a kapacitás méretét a vertikális felskálázás vagy skálázási erőforrásokat.
- Adja hozzá, vagy távolítsa el a kapacitás-rendszergazdákat.
- Adja hozzá, vagy távolítsa el a hozzárendelési engedéllyel rendelkező felhasználók.
- Adja hozzá, vagy távolítsa el a további munkaterhelések.
- Régió módosítása

A hozzárendelési engedéllyel kell rendelnie a munkaterületet egy adott prémium szintű kapacitáshoz. Az engedélyek a teljes szervezet számára, bizonyos felhasználók vagy csoportok adható meg.

Alapértelmezés szerint prémium szintű kapacitások támogatja a Power BI-lekérdezések futtatásával kapcsolatos számítási feladatokhoz. Prémium szintű kapacitások további számítási feladatokat is támogatja: **Mesterséges Intelligencia (Cognitive Services)** , **oldalakra osztott jelentések**, és **adatfolyamok**. Minden számítási feladathoz szükséges konfigurálása a maximális memóriát (a teljes szabad memória százalékaként), a munkaterhelés szerint használható. Fontos megérteni, hogy növelje a maximális memórialefoglalások befolyásolhatja a üzemeltethető aktív modellek számát és az átviteli sebességet a frissítések. 

Memória adatfolyamok számára dinamikusan történik, de a többoldalas jelentések statikusan hozzá van rendelve. A maximális memóriafoglalás statikusan oka, hogy oldalakra osztott jelentések futtathatók a kapacitás biztonságos tartalmazott szóközzel. Ha a beállítás többoldalas jelentések memória, mivel csökkenti a rendelkezésre álló memória a modell betöltése gondot kell fordítani. További tudnivalókért tekintse meg a [memória beállításainak alapértelmezett](service-admin-premium-workloads.md#default-memory-settings).

Egy prémium szintű kapacitás törlése lehetséges, és nem a munkaterületekről és a tartalom törlését eredményezi. Ehelyett áthelyezi azt minden hozzárendelt munkaterületek megosztott kapacitáshoz. A prémium szintű kapacitás egy másik régióban lett létrehozva, amikor a munkaterület megosztott kapacitás az otthoni régió került.

### <a name="assigning-workspaces-to-capacities"></a>Munkaterületek hozzárendelése kapacitások

Munkaterületek lehet hozzárendelni egy prémium szintű kapacitáshoz a Power BI felügyeleti portálon, vagy egy alkalmazás-munkaterületen, a a **munkaterület** ablaktáblán.

Kapacitás-rendszergazdák, valamint az Office 365 globális rendszergazdák vagy a Power BI szolgáltatás-rendszergazdák, tömegesen rendelhet hozzá munkaterületeket a Power BI felügyeleti portálon. Hozzárendelt tömeges alkalmazhatók:

- **Munkaterületek felhasználók szerint** -felhasználókat, beleértve a személyes munkaterületeket, által birtokolt összes munkaterületet a prémium szintű kapacitáshoz rendelt. Ide tartoznak a munkaterületek újbóli hozzárendelése során már hozzá van rendelve egy másik prémium szintű kapacitáshoz. Emellett a felhasználók is hozzárendelt munkaterület-hozzárendelési engedélyt.

- **Adott munkaterületek**
- **A teljes cég munkaterületei** – összes munkaterületet, beleértve a személyes munkaterületeket a prémium szintű kapacitáshoz rendelt. Az összes jelenlegi és jövőbeli felhasználónak vannak hozzárendelve a munkaterület-hozzárendelési engedélyt. Ez a módszer nem ajánlott. Egy további, jobban célzott módszer használata ajánlott.

Egy prémium szintű kapacitáshoz is hozzáadhatók a munkaterület használatával a **munkaterület** ablaktáblán, lehetővé téve a felhasználó mindkét munkaterület-rendszergazda, és a hozzárendelési engedéllyel rendelkezik.

![A munkaterület ablak használó rendelnie a munkaterületet egy prémium szintű kapacitáshoz](media/service-premium-capacity-manage/assign-workspace-capacity.png)

Munkaterületek rendszergazdái eltávolíthatják a munkaterületet egy kapacitáshoz (a megosztott kapacitás) anélkül, hogy a hozzárendelési engedéllyel. A munkaterület eltávolítása a munkaterület dedikált kapacitás hatékonyan helyez át a megosztott kapacitásra. Vegye figyelembe, hogy egy munkaterületet egy prémium szintű kapacitáshoz eltávolítása negatív következményekkel eredményez, például a megosztott tartalom a Power BI ingyenes elérhetetlenné lehetnek licenccel rendelkező felhasználók vagy az ütemezett frissítés felfüggesztését a támogatott keretek túllépésekor megosztott kapacitás.

A Power BI szolgáltatásban a gyémánt ikon jelzi, hogy a munkaterület neve adorns egy munkaterületet egy prémium szintű kapacitáshoz rendelve könnyedén azonosíthatók.

![Egy munkaterületet egy prémium szintű kapacitáshoz rendelve azonosítása](media/service-premium-capacity-manage/premium-diamond-icon.png)

## <a name="monitoring-capacities"></a>Figyelési kapacitások

Prémium szintű kapacitások figyelés segítségével a rendszergazdák hogyan hajtja végre a kapacitások megismerése. Kapacitások figyelhető a Power BI felügyeleti portál használatával vagy a **Power BI Premium kapacitás-metrikák** (Power BI-) alkalmazást.

### <a name="power-bi-admin-portal"></a>Power BI felügyeleti portál

A felügyeleti portálon, minden kapacitáshoz a **egészségügyi** lapot összefoglaló metrikákat nyújt a kapacitás és minden engedélyezett számítási feladathoz. Metrikák megjelenítése az átlagos az elmúlt hét napban.  

A kapacitás szintjén metrikák összeadódnak az összes engedélyezett munkaterhelés. a következő metrikákat:

- **CPU-KIHASZNÁLTSÁG** -átlagos CPU-kihasználtság százalékos arányában teljes rendelkezésre álló Processzorkapacitást nyújt a kapacitáshoz.  
- **MEMÓRIAHASZNÁLAT** – átlag biztosít memória használata (GB), a kapacitás rendelkezésre álló memória összesen. 

Minden engedélyezett számítási CPU-kihasználtság és a memóriahasználat érhetők el, valamint egy adott mérőszámok számítási feladatok száma. Az adatfolyam-számítási feladatok, például, ha **összesített száma** látható minden egyes adatfolyamot, a frissítések teljes és **átlagos időtartama** jeleníti meg az adatfolyamot a frissítés az átlagos időtartama.

![A kapacitás állapot lapon a portálon](media/service-premium-capacity-manage/admin-portal-health-dataflows.png)

Az egyes munkaterhelésekhez tartozó összes rendelkezésre álló metrikák kapcsolatos további információkért lásd: [figyelheti a felügyeleti portál kapacitások](service-admin-premium-monitor-portal.md).

A megfigyelési lehetőségek a Power BI felügyeleti portálon adja meg a kulcs kapacitási összefoglalóját lettek kialakítva. Részletes figyelését, javasoljuk, használja a **Power BI Premium kapacitás-metrikák** alkalmazást.

### <a name="power-bi-premium-capacity-metrics-app"></a>Power BI Premium kapacitás metrikák alkalmazás

A [Power BI Premium kapacitás-metrikák alkalmazás](https://appsource.microsoft.com/product/power-bi/pbi_pcmm.pbi-premiumcapacitymonitoring?tab=Overview) a kapacitás-rendszergazdák rendelkezésére áll egy Power BI-alkalmazást, és telepítve van, mint bármely más Power BI alkalmazást. Tartalmaz egy irányítópultot és jelentést.

![Power BI Premium kapacitás metrikák alkalmazás](media/service-premium-capacity-manage/capacity-metrics-app.png)

Az alkalmazás megnyitásakor nyújtjuk egy összesített nézet kifejezésének keresztül, amelynek a felhasználó egy kapacitás-rendszergzdát. nem minden kapacitás számos olyan csempéket az irányítópult betöltése Az irányítópult elrendezése öt fő részből áll:

- **Áttekintés** -verziója, a kapacitások és munkaterületek száma
- **Rendszer összegzése** – memória és CPU-metrikák
- **Adatkészlet összefoglaló** - szám, adatkészletek, DQ/LC, frissítési és lekérdezési metrikák
- **Adatfolyam-összegzés** - szám adatfolyamok, és az adatkészlet-metrikák
- **Többoldalas jelentés összefoglaló** – frissítés, és metrikák megtekintése

Az alapul szolgáló jelentés, amelyből az irányítópult-csempék lett rögzítve az irányítópulton, az irányítópult csempékre kattintva elérhető lesz. Az irányítópult egyes részletesebb szempontjából, és interaktív szűrés támogat. 

Szűrés elérhető szeletelők által dátumtartomány, a kapacitás, a munkaterület és a számítási feladatok (jelentés, adatkészlet, adatfolyam) beállításával, és a jelentésben az elemek kiválasztásával a Vizualizációk közötti jelentésoldalak szűrése. Keresztszűrés egy hatékony módszer az adott időszakra, kapacitások, munkaterületeket, adatkészleteket, stb. szűkítéséhez, és nagyon hasznos lehet, amikor a kiváltó okok elemzésével.

Az alkalmazás-irányítópult és jelentés metrikák kapcsolatos részletes információkért lásd: [figyelő prémium szintű kapacitások az alkalmazással](service-admin-premium-monitor-capacity.md).

### <a name="interpreting-metrics"></a>Metrikák értelmezése

Metrikák ellenőrizni kell létesíteni egy erőforrás-használat és a számítási feladatok tevékenység alapvető ismeretekkel. Ha a kapacitás lassú, fontos tudni, hogy milyen metrikákat kíván monitorozni, és teheti következtetéseket.

Ideális esetben lekérdezések szolgáltatásszintről egy második rugalmas élményeket nyújthat a felhasználóknak a jelentés és a magasabb szintű lekérdezési teljesítmény engedélyezéséhez. Ez általában a kisebb aggodalomra ad okot amikor – beleértve a frissítések – háttérfolyamatok végrehajtásához hosszabb időt is igénybe.

Lassú jelentések általában arra utalhat, hogy egy túlzott fűtésrendszerek kapacitást is lehet. Nem sikerült betölteni a jelentéseket, ha ez az arra utalhat, hogy egy túlterhelt fűtött kapacitást. Mindkét esetben a fő ok lehet tulajdonítható sok tényező befolyásolja, többek között:

- **Sikertelen lekérdezések** természetesen jelzi a rendelkezésre álló memória mennyisége, és hogy a modell nem tölthető be a memóriába. A Power BI szolgáltatás megkísérli betölteni a modell 30 másodpercig, mielőtt hibát jelentene.

- **Túl sok lekérdezés várakozási idők** számos oka lehet:
  - A Power BI szolgáltatásban, először szükség a modellek fürtből, és töltsön be a to-be lekérdezett modell (visszaírási, hogy magasabb adatkészlet kiürítési önálló összeg nem arra utalhat, hogy kapacitás stress, kivéve, ha hosszú lekérdezési várakozási időt memóriaakadozás jelző fűzni).
  - Modell-terhelés időpontokban (különösen a nagy modell betöltése a memóriába várakozás).
  - A hosszabb ideig futó lekérdezéseket.
  - Túl sok LC\DQ kapcsolat (kapacitáskorlátait meghaladó).
  - CPU színtelítettség.
  - A jelentés összetett tervek a Vizualizáció túl sok (visszaírási, hogy minden egyes vizuális elem lekérdezés) lapon.

- **Hosszú lekérdezés időtartamának összegénél** azt jelzi, hogy modell tervek nem vannak optimalizálva, különösen akkor, ha több adatkészlet kapacitásban aktív, és csak egy adatkészlet van előállító hosszú lekérdezés időtartamának összegénél. Ez azt sugallja, hogy a kapacitás elég ellátva erőforrással, és hogy az kérdés adatkészlet az optimálisnál rosszabb vagy csak lassú. Hosszú ideig futó lekérdezések problémás lehet, mert akkor képes blokkolni a hozzáférést, más folyamatok által igényelt erőforrások.
- **Mennyi ideig frissítse a várakozási időt** memóriát sok az aktív modellek miatt nincs elég memória, de akár (meghaladó párhuzamos frissítés korlátok), hogy problémás frissítést blokkolja a többi frissíti.

A mérőszámok használatát bemutató részletesebb magyarázatáért tárgyalja a [optimalizálása prémium szintű kapacitások](service-premium-capacity-optimize.md) cikk.

## <a name="acknowledgements"></a>Nyugtázás

Ez a cikk írásának Peter Myers, a Data Platform MVP és a független, a BI-Szakértővé [bitenként megoldások](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Következő lépések

> [!div class="nextstepaction"]
> [Prémium szintű kapacitások optimalizálása](service-premium-capacity-optimize.md)   
> [!div class="nextstepaction"]
> [Prémium-kapacitás a számítási feladatok konfigurálása](service-admin-premium-workloads.md)   

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

||||||
