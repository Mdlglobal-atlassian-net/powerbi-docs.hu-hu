---
title: Mi az a Microsoft Power BI Premium?
description: A Power BI Premium dedikált kapacitást a szervezete számára biztosít, így megbízhatóbb teljesítményt biztosítva nagyobb mennyiségű adat, anélkül, hogy felhasználónkénti licencek megvásárlását.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/22/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: e5ffa624bf69cf470aade076c80ac37028a55456
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565256"
---
# <a name="what-is-power-bi-premium"></a>Mi az a Power BI Premium?

A Power BI Premium dedikált és továbbfejlesztett forrásanyagokat biztosít az futtassa a Power BI szolgáltatásban a szervezet számára. Például:

- Nagyobb méretezés és teljesítmény
- Rugalmas kapacitás licenc
- Használja őket egységes előtérrendszerként önkiszolgáló és a vállalati bi-ban
- A Power BI jelentéskészítő kiszolgáló helyszíni BI kiterjesztése
- Adattárolás helye (több, földrajzilag) régiónként támogatása
- Felhasználói licenc megvásárlása nélkül bárkivel megoszthatják adataikat

Ez a cikk nem csupán azt, hogy valójában adja meg a Power BI Premium – minden funkcióját részletes adatait, csak a felszín éri el. Szükség esetén további információt a további cikkek hivatkozásainak állnak rendelkezésre.

## <a name="subscriptions-and-licensing"></a>Előfizetések és licencek

A Power BI Premium egy bérlői szintű Office 365-előfizetéssel elérhető két (készletkezelési egység) Termékváltozat-családokra:

- **EM** termékváltozatok (EM1-EM3) számára végez beágyazást, egy éves kötelezettségvállalást igénylő után számlázunk havonta.
- **P** termékváltozatok (P1-P3) beágyazása és nagyvállalati funkciókat, a havi vagy éves kötelezettségvállalást igénylő, havi elszámolásban, és a helyszíni Power BI jelentéskészítő kiszolgáló telepítése egy licencet tartalmaz.

Egy alternatív módszer is meg kell vásárolnia egy **Azure Power BI Embedded** előfizetés, amely rendelkezik egy **A** csak (A1-A6) Termékváltozat-család beágyazáshoz és kapacitás tesztelési célra használja. A termékváltozatokat nyújthat magok a kapacitások létrehozása, de a EM termékváltozatok a következők korlátozott kisebb méretezési beágyazásához. EM1, EM2, A1 és A2 Termékváltozatait legalább négy magot nem futtathatók a dedikált infrastruktúra.

Bár a lépéseknek az ismertetése, ez a cikk a P SKU-k, szinte leírtakhoz egyben a termékváltozatok a. A Premium szintű előfizetéssel szakembereket SKU-k, az Azure termékváltozatokat szükséges idő kötelezettségvállalás nélkül, és óradíjat kell fizetni. Azok teljes rugalmasságát, felfelé méretezés engedélyezése kézbesítéséhez, vertikális leskálázás, szüneteltetése, folytatása és törlése. 

Az Azure Power BI Embedded nem nagymértékben Ez a cikk tárgyalja, de leírtak a [tesztelési módszer](service-premium-capacity-optimize.md#testing-approaches) optimalizálása prémium szintű kapacitások cikkének teszteléséhez, és mérheti a számítási feladatok gyakorlatban hasznosíthatóvá teszi és gazdasági beállításként. Az Azure termékváltozatokat kapcsolatos további információkért lásd: [Azure Power BI Embedded dokumentációja](https://azure.microsoft.com/services/power-bi-embedded/).

### <a name="purchasing"></a>Vásárlás

A Power BI Premium-előfizetések rendszergazdái a Microsoft 365 felügyeleti központban vásárolhatók meg. Pontosabban csak az Office 365 globális vagy számlázási rendszergazdái is vásárolhat SKU-k. Vásárolt, a bérlő kapja hozzárendelése a kapacitás, más néven virtuális magok megfelelő számú *magok készletezésével*. Például egy P3 SKU megvásárlása nyújt a bérlő 32 virtuális magot. További tudnivalókért lásd: [hogyan tudja megvásárolni a Power BI Premium](service-admin-premium-purchase.md).

## <a name="dedicated-capacities"></a>Dedikált kapacitás

A Power BI Premium beszerzése *dedikált kapacitás*. Szakembereket egy megosztott kapacitásban, amelyben a számítási feladatok más ügyfelekkel megosztott számítási erőforrásokon futnak a dedikált kapacitáshoz van egy szervezet kizárólagos használatára. Elkülönített és dedikált számítási erőforrást, amely megbízható és következetes teljesítményt szolgáltatott tartalom. 

Munkaterületek kapacitások belül találhatók. Minden Power BI-felhasználó rendelkezik személyes munkaterületek néven **saját munkaterület**. További munkaterületek és a központi telepítési hozható létre, és ezek **alkalmazás-munkaterületek**. Alapértelmezés szerint a munkaterületek, beleértve a személyes munkaterületeket, a megosztott kapacitásban jönnek létre. Ha prémium szintű kapacitások, saját munkaterületét és az alkalmazás-munkaterületek prémium szintű kapacitások is hozzárendelhető.

### <a name="capacity-nodes"></a>A kapacitás csomópontok

Leírtak szerint a [előfizetések és licencelés](#subscriptions-and-licensing) területen vannak a két Power BI Premium SKU-család: **EM** és **P**. Minden Power BI Premium-termékváltozatokat érhetők el, a kapacitás *csomópontok*, ahol a processzor, memória és tárolási erőforrások időkereten. Erőforrások mellett minden Termékváltozat működési korlátokkal rendelkeznek a DirectQuery és élő kapcsolat kapcsolatok másodpercenkénti száma, és a párhuzamos modell száma frissíti.

Feldolgozási számú mag, háttér és előtérbeli között egyenlően osztja használatával érhető el.

**Háttérbeli virtuális magok** felelősek a Power BI alapvető funkciókat, beleértve a lekérdezések feldolgozásához, a gyorsítótár kezeléséhez, R services, a modellfrissítéshez, természetes nyelvi feldolgozást (Q & A) és a jelentések és képek kiszolgálóoldali megjelenítés futtatásához. Háttérbeli virtuális magok hozzá vannak rendelve egy rögzített méretű memória, amely elsősorban a gazdagép modellek, más néven aktív adatkészlet.

**Előtérbeli virtuális magok** felelős a webes szolgáltatás, az irányítópult és jelentés dokumentumkezeléshez, access, ütemezés, API-k, feltölti és tölti le, és általában minden kapcsolódó a felhasználói élmény.

Tárolás beállítása **100 TB kapacitás csomópontonként**.

Az erőforrások és a korlátok minden prémium szintű termékváltozat (és év méretezni A Termékváltozat) a következő táblázat ismerteti:

| A kapacitás csomópontok | Összes virtuális mag | Háttérrendszeri virtuális magok | MEMÓRIA (GB) | Előtérrendszeri virtuális magok | A DirectQuery/élő kapcsolat (/ mp) | Modell frissítése párhuzamos végrehajtás |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 2.5 | 0,5 | 3.75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7.5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| | | | | | | |

### <a name="capacity-workloads"></a>A kapacitás számítási feladatokhoz

A kapacitás számítási feladatokat a felhasználók számára elérhetővé tett szolgáltatások. Alapértelmezés szerint prémium és a kapacitások Azure támogatja a csak egy adatkészlet számítási társított Power BI-lekérdezések futtatásához. Az adatkészlet számítási feladatok nem tiltható le. További számítási feladatok esetén is engedélyezhető [AI (Cognitive Services)](https://powerbi.microsoft.com/blog/easy-access-to-ai-in-power-bi-preview/), [adatfolyamok](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium), és [oldalakra osztott jelentések](paginated-reports-save-to-power-bi-service.md). Ezeket a feladatokat csak a prémium szintű előfizetés támogatottak. 

Minden további számítási feladat a maximális memóriát (a teljes szabad memória százalékaként), a munkaterhelés szerint használható konfigurálását teszi lehetővé. Maximális memória tartozó alapértelmezett értékeket határozza meg a Termékváltozat. A kapacitás rendelkezésre álló erőforrások maximalizálhatja a csak további számítási feladatok engedélyezésével, amikor használhatók. És módosíthatja a beállításokat csak akkor, ha meghatározta, alapértelmezett beállítások nem megfelelő a kapacitásigények erőforrás memória. Számítási feladatok is engedélyezni és konfigurálni egy kapacitás a kapacitás-rendszergazdák számára a **kapacitásbeállítások** a a [felügyeleti portál](service-admin-portal.md) vagy a [kapacitások REST API-k](https://docs.microsoft.com/rest/api/power-bi/capacities).  

![Számítási feladatok engedélyezése](media/service-admin-premium-workloads/admin-portal-workloads.png)

További tudnivalókért lásd: [Munkafeladatok konfigurálása prémium szintű kapacitásban](service-admin-premium-workloads.md). 

### <a name="how-capacities-function"></a>Hogyan kapacitások függvény

At minden alkalommal, a Power BI szolgáltatás lehetővé teszi a kapacitás-erőforrások ajánlott használatát nem haladhatja meg a kapacitás vonatkozó korlátozások.

A kapacitás műveletek besorolt vagy *interaktív* vagy *háttér*. Interaktív műveletek közé tartozik a kérelmek megjelenítése, és válaszol a felhasználói tevékenységeket (szűrés, a Q & A lekérdezése, stb.). Általában a importálás modell lekérdezése, a memória erőforrás-igényes, viszont a DirectQuery és élő kapcsolat modellek lekérdezésekor a CPU-igényes. Háttérbeli műveletek közé tartozik az adatfolyamot, és importálja a modell frissül, és az irányítópult lekérdezés gyorsítótárazása.

Fontos tudni, hogy interaktív műveletekhez mindig szándék a lehető legjobb felhasználói élmény biztosítása érdekében a háttérbeli műveletek. Ha rendelkezésre áll elegendő erőforrás, a háttérbeli műveletek feldolgozással, ha az erőforrások felszabadítása várólistába lesz hozzáadva. Háttérben futó műveletek, például adatkészlet frissítését, a Power BI szolgáltatás által leállítva közepes folyamat lehet, és hozzáadja egy üzenetsorba.

Importált modelleken teljes mértékben a memóriába betöltött kell lennie, ezért lekérdezni vagy frissíteni. A Power BI szolgáltatás kezeli a memória kihasználtsága használatával kifinomult algoritmusok maximálisan kihasználható a rendelkezésre álló memória biztosítása érdekében, és emiatt túlterhelt véglegesítése a kapacitás: Közben, a lehető kapacitás számos importálás tárolja a modellek (akár 100 TB prémium szintű kapacitás kiszolgálónként), amikor azok összesített lemezterület meghaladja a támogatott memória (és további memóriára szükség, lekérdezéséhez és frissítés), majd azokat az összes betöltése nem sikerült a memóriába egy időben.

Importált modelleken vannak ezért betölti és a memória kihasználtsága alapján. Az importálás modell be van töltve, amikor éppen lekérdezett (interaktív művelet) és még nincs a memóriában, vagy ha frissíteni kell (háttér-művelet).

Az Eltávolítás a memóriából a modell más néven *kiürítési*. Egy Power bi-ban gyorsan hajthat végre a modellek méretétől függően a művelet. Ha a kapacitás minden rendelkezésre álló memória mennyisége nem tapasztalja, modellek egyszerűen a memóriába betöltött és helyükön maradnak. Azonban ha nincs elég memória a modell betöltése érhető el, a Power BI szolgáltatásban először szabadítson fel memóriát. Memória, felszabadítja a modelleket, hogy azzal, amelyet nem használtak az elmúlt három percben modellek inaktív váltak észlelésével \[ [1](#endnote-1)\], és ezután kizárásának őket. Ha nem inaktív modellek fürtből, a Power BI szolgáltatásban arra törekszik, hogy kizárandó modelleket, a háttérbeli műveletek betöltése. Végső megoldásként, a sikertelen kísérletek 30 másodperc múlva \[ [1](#endnote-1)\], hogy az interaktív művelet sikertelen. Ebben az esetben a jelentés felhasználó értesítést kap, próbálkozzon újra hamarosan javaslatot a hiba. Bizonyos esetekben modellek lehet memóriából szolgáltatási műveletek miatt.

Fontos, hogy hangsúlyozzák az, hogy az adatkészlet kiürítési egy normál és az elvárt működés. Arra törekszik, betöltés és a modellek, amelyek összesített mérete meghaladhatja a rendelkezésre álló memória memóriából memóriafelhasználása maximalizálása érdekében. Ez a Tervező, és teljes mértékben átlátható jelentésfelhasználók. Magas kiürítési díjait nem jelenti a kapacitást nem megfelelően van forrásokat. Is, azonban válnak a veszélye, ha a lekérdezés vagy a frissítés válaszkészségének érte miatt magas kiürítési díjait.

Frissíti az importálás modellek áll a mindig memóriaigényes modellek kell betölti a memóriába. További memóriára szükség a feldolgozáshoz. Teljes frissítés körülbelül double a modell által igényelt memória mennyisége használhatja. Ez biztosítja, hogy a modell lekérdezhetők, akkor is, ha a feldolgozás alatt, mert a lekérdezések továbbítóknak a meglévő modellt, amíg a frissítés befejeződött, és az új modell adatainak érhető el. Növekményes frissítési kell kevesebb memóriával és gyorsabban sikerült végrehajtani, és így jelentősen csökkentheti nyomás kapacitás erőforrásokon. Frissítések is lehet a CPU-igényes modellekhez, különösen az összetett Power Query-átalakítások vagy számított táblákat/oszlopokat, amelyek összetett, vagy nagy táblák alapulnak.

A szükséges frissítések, például a lekérdezések a modell a memóriába. Ha nincs elég memória, a Power BI szolgáltatás megkísérli kizárandó inaktív modelleket, és ha ez nem lehetséges (is minden modell nem aktív), a frissítési feladat várólistára van-e állítva. Frissítések általában nagy Processzorteljesítményt, még akkor is inkább, lekérdezéseket. Ebből kifolyólag nincsenek egyidejű frissítések, állítsa be a háttér virtuális magokkal kerekítve száma x 1.5-ös számú kapacitásának korlátjáig. Ha túl sok egyidejű frissítések, egy ütemezett frissítés várólistára kerül. Ezekben a helyzetekben fordulhat elő, ha hosszabb ideig tart a frissítés befejezéséhez. Igény szerinti frissíti, például egy felhasználói kérelem által aktivált, vagy egy API-hívás három alkalommal próbálkozik újra \[ [1](#endnote-1)\]. Ha még nincs elegendő erőforrása, a frissítés majd sikertelen lesz.

A Megjegyzések szakaszban.   
<a name="endnote-1"></a>\[1\] változhat.

### <a name="regional-support"></a>Regionális támogatás

Amikor egy új kapacitást, az Office 365 globális rendszergazdák és a Power BI szolgáltatás-rendszergazdák létrehozásával megadhatja egy régióban, ahol munkaterületet a kapacitáshoz rendelve helyezkednek el. Ez az úgynevezett **Multi-földrajzi**. A Multi-földrajzi szervezetek megfelel adatok tárolási helyére vonatkozó előírásoknak által egy adott régióban lévő adatközpontokba tartalom központi telepítése akkor is, ha nem egyezik a régiót, amelyben a Office 365-előfizetésben található. További tudnivalókért lásd: [Multi-földrajzi támogatása a Power BI Premium](service-admin-premium-multi-geo.md).

### <a name="capacity-management"></a>Kapacitáskezelés

Prémium szintű kapacitások felügyelete magában foglalja a létrehozása vagy törlése a kapacitások, Rendszergazdák hozzárendelése, munkaterületek hozzárendelése, konfigurálása a számítási feladatok, figyelés és a kapacitás teljesítményének optimalizálásához szükséges módosításokat. 

Az Office 365 globális rendszergazdák és a Power BI szolgáltatás-rendszergazdák is elérhető virtuális magok a prémium szintű kapacitások létrehozása, vagy módosítsa a meglévő prémium szintű kapacitások. A kapacitás létrehozásakor a kapacitás méretét és a földrajzi régió van megadva, és legalább egy kapacitás-rendszergazda van hozzárendelve. 

Kapacitások létrehozásakor a legtöbb felügyeleti feladat végezhető el a [felügyeleti portál](service-admin-portal.md).

![Felügyeleti portál](media/service-premium-what-is/premium-admin-portal.png)

A kapacitás-rendszergazdák munkaterületeket rendeljen a kapacitás, felhasználói engedélyek kezelése, és rendelje hozzá a többi adminisztrátor. A kapacitás-rendszergazdák is konfigurálhatja a számítási feladatokhoz, módosításával memórialefoglalások, és szükség esetén indítsa újra a kapacitást, alaphelyzetbe állítása esetén a kapacitás túlterhelési műveletek.

![Felügyeleti portál](media/service-premium-what-is/premium-admin-portal-mgmt.png)

Kapacitás-rendszergazdákat is ügyeljen arra, hogy már simán fut egy kapacitáshoz. Kapacitás egészségügyi jobb a felügyeleti portálon vagy a prémium szintű kapacitás metrikák alkalmazással figyelésére.

További információk kapacitások létrehozásával, Rendszergazdák hozzárendelése és munkaterületek hozzárendelésének kapcsolatban lásd: [kezelése prémium szintű kapacitások](service-premium-capacity-manage.md). Szerepkörök kapcsolatos további információkért lásd: [rendszergazdai szerepköröket a Power bi-hoz kapcsolódó](service-admin-administering-power-bi-in-your-organization.md#administrator-roles-related-to-power-bi).

### <a name="monitoring"></a>Figyelés

Prémium szintű kapacitások figyelés segítségével a rendszergazdák hogyan működnek a kapacitások megismerése. Kapacitások figyelhető a felügyeleti portál használatával, és a [Power BI Premium kapacitás-metrikák alkalmazás](https://app.powerbi.com/groups/me/getapps/services/capacitymetrics).

Monitoring a portálon egy gyors nézetet biztosít magas szintű metrikák elhelyezett terhelések és a kapacitás átlagolva az elmúlt hét napban az egyes erőforrásokat jelző. 

![Felügyeleti portál](media/service-premium-what-is/premium-admin-portal-health.png)

A **Power BI Premium kapacitás-metrikák** alkalmazás be, hogyan hajtja végre a kapacitások a legtöbb részletesebb információkat biztosít. Az alkalmazás biztosít magas szintű irányítópult és jelentések részletes.

![A Metrics alkalmazás irányítópultja](media/service-admin-premium-monitor-capacity/app-dashboard.png)

Az alkalmazás irányítópulton kattintson egy metrika cella részletes jelentés megnyitásához. Jelentések nyújtanak részletes mérőszámokat és lehatolást a legfontosabb információt jelenítse meg a szűrési képességek meg kell őrizni a kapacitások működőkre.

![Lekérdezés rendszeres csúcsok várakozási számát jelzi a lehetséges CPU színtelítettség idő](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

Kapacitások figyelésével kapcsolatos további tudnivalókért lásd: [figyelése a Power BI felügyeleti portálon](service-admin-premium-monitor-portal.md) és [, a Power BI Premium kapacitás-metrikák alkalmazás figyelési](service-admin-premium-monitor-capacity.md).

### <a name="optimizing-capacities"></a>Kapacitás optimalizálása

A kapacitások optimális kihasználására, kritikus fontosságú a felhasználók get biztosítva a teljesítmény és a prémium szintű befektetések a legtöbb értéket kap. Alapvető metrikák figyelésével rendszergazdái meghatározhatják, hogy hogyan érdemes hibaelhárítása a szűk keresztmetszeteket, és a szükséges műveleteket. További tudnivalókért lásd: [optimalizálása prémium szintű kapacitások](service-premium-capacity-optimize.md) és [prémium szintű kapacitás forgatókönyvek](service-premium-capacity-scenarios.md).

### <a name="capacities-rest-apis"></a>Kapacitások REST API-k

A Power BI REST API-k gyűjteménye, például [kapacitások API-k](https://docs.microsoft.com/rest/api/power-bi/capacities). Az API-khoz a rendszergazdák programozott módon kezelheti a prémium szintű kapacitás, engedélyezése és letiltása a számítási feladatok, munkaterületek hozzárendelése egy kapacitáshoz, és többek között számos szempontból.

## <a name="large-datasets"></a>Nagyméretű adatkészletek

A Termékváltozat függően a Power BI Premium támogatja a fájlokat tölthet fel a Power BI Desktop (.pbix) modell legfeljebb **10 GB-os** mérete. Betöltött, a modell közzétehetők egy munkaterületet egy prémium szintű kapacitáshoz rendelve. Az adatkészlet majd frissíthet legfeljebb **12 GB** mérete.

### <a name="size-considerations"></a>Méretére vonatkozó szempontok

Nagy modellek erőforrás-igényes lehet. Rendelkeznie kell legalább a P1 Termékváltozatot alkalmazni minden 1 GB-nál nagyobb méretű modellek esetén. Bár a munkaterületek nagy modellek közzététele termékváltozatok legfeljebb A3 alapját sikerült munka, hozzájuk eredményez.

A következő táblázatban a különböző méretű .pbix-fájlokhoz ajánlott termékváltozatok vannak megadva:

   |Termékváltozat  |A .pbix-fájl mérete   |
   |---------|---------|
   |P1    | < 3 GB        |
   |P2    | < 6 GB        |
   |P3, P4, P5    | legfeljebb 10 GB   |

A Power BI Embedded A4 termékváltozata a P1 SKU-val, az A5 a P2-vel, az A6 pedig a P3-mal egyezik meg. Fontos tudni, hogy nagy modellek A és EM SKU-kba való közzététele olyan hibát eredményezhet, amely nem a megosztott kapacitásbeli modellméret-korlátozási hibával függ össze. Nagy modellek A és EM SKU-kban fellépő frissítési hibái feltehetően időtúllépésre utalnak. 

A .pbix-fájlok jelenítik meg az adatokat egy *tömörítve állapot*. Az adatok mérete valószínűleg többszörösére fog nőni a memóriába való betöltéskor, és ehhez képest is a többszörösére nőhet az adatok frissítése során.

A nagyméretű adathalmazok ütemezett frissítés is egy hosszú időt is igénybe és erőforrás-igényes lehet. Fontos, nem a túl sok egymással átfedő frissítést ütemezni. Ajánlott [növekményes frissítés](service-premium-incremental-refresh.md) van konfigurálva, mert gyorsabb és megbízhatóbb, és kevesebb erőforrást használ fel.

A jelentés kezdeti betöltése a nagyméretű adathalmazok hosszú időt vehet igénybe, ha az adatkészlet használták utoljára óta volt. A hosszabb ideig töltődő jelentések esetében egy betöltési folyamatjelző mutatja a betöltés előrehaladását.

A lekérdezés – memória és korlátozásai, amelyek közül sokkal nagyobb prémium szintű kapacitásban ajánlott a látványelemeket szűrőkkel és Szeletelőkkel korlátozni megjelenítéséhez, csak hogy mire szükség.

## <a name="incremental-refresh"></a>Növekményes frissítés

A növekményes frissítés biztosít kapcsolatban, és nagy méretű adatkészleteket a Power BI Premium karbantartása szerves része. Növekményes frissítés számos előnye van, például frissítések gyorsabb, mert csak az adatokat, amely rendelkezik a módosított kell frissíteni. Frissítések nincsenek megbízhatóbb, mert nem felejtő adatforrásokhoz tartós kapcsolatok fenntartásához szükséges. Erőforrás-használat csökken, mert kevesebb adatot frissítéséhez csökkenti a teljes fogyasztás memória és egyéb erőforrásokat. A növekményes frissítés házirendeket **Power BI Desktop**, és egy munkaterülethez prémium szintű kapacitásban közzétett érvényesek. 

![Frissítés részletei](media/service-premium-incremental-refresh/refresh-details.png)

További tudnivalókért lásd: [növekményes frissítés a Power BI Premium](service-premium-incremental-refresh.md).

## <a name="paginated-reports"></a>Oldalakra osztott jelentések

Többoldalas jelentések, a P1-P3 és A4_A6 SKU-k, támogatott jelentésdefiníciós nyelv (RDL) technológia az SQL Server Reporting Services alapulnak. Az RDL-technológián alapuló, amíg nincs ugyanaz, mint a Power BI jelentéskészítő kiszolgáló, amely egy letölthető jelentéskészítési platform, telepítheti a helyszínen, a Power BI Premium is tartalmazzák. Egy oldal, amely kinyomtatását, vagy megosztott illeszkedjenek a többoldalas jelentések formázása. Adatok táblázatként, jelenik meg akkor is, ha a tábla több oldalra is átnyúlik. Az ingyenes használatával [ **Power BI jelentéskészítő** ](https://go.microsoft.com/fwlink/?linkid=2086513) Windows asztali alkalmazások, felhasználók Szerző többoldalas jelentések és közzéteheti őket a szolgáltatásban.

A Power BI Premium Paginated-jelentések olyan számítási feladatok, amelyek engedélyezni kell a kapacitást a felügyeleti portál használatával. A kapacitás-rendszergazdák engedélyezheti, és adja meg a memória mennyiségét a teljes memória-erőforrások a kapacitás százalékában. Ellentétben más típusú számítási feladatokat prémium szintű futtatja az oldalakra osztott jelentések belül a kapacitás tartalmazott szóközzel. A maximális memóriát, ezt a helyet használja a rendszer a számítási feladatok aktív-e megadva. Az alapértelmezett érték 20 %-át. 

További tudnivalókért lásd: [oldalakra osztott jelentések a Power BI Premium](paginated-reports-report-builder-power-bi.md). A jelentések Paginated számítási feladatok engedélyezésével kapcsolatos további tudnivalókért lásd: [számítási feladatainak konfigurálásában](service-admin-premium-workloads.md).

## <a name="power-bi-report-server"></a>Power BI jelentéskészítő kiszolgáló
 
A Power BI jelentéskészítő kiszolgáló van a Power BI Premium mellékelt egy *helyszíni* jelentéskészítő kiszolgáló a webes portálon. A BI készíthet a helyszíni környezetben, és terjeszteni a jelentéseket a cég tűzfala mögött. Jelentéskészítő kiszolgáló hozzáférést biztosít a felhasználóknak gazdag, interaktív és az SQL Server Reporting Services a nagyvállalati jelentéskészítési funkciókat. A felhasználók ismerje meg a vizuális adatok és gyorsabb döntéseket hatékonyabban, minták gyorsan felderítése. Jelentéskészítő kiszolgáló cégirányítási biztosít a saját igényei szerint. Az idő csatlakozik a hálózathoz, ha a Power BI jelentéskészítő kiszolgáló egyszerűen migrálása a felhőbe, ahol a szervezet minden Power BI Premium-funkció, teljes mértékben kihasználhatják a.

További tudnivalókért lásd: [Power BI jelentéskészítő kiszolgáló](report-server/get-started.md).

## <a name="unlimited-content-sharing"></a>Korlátlan számú tartalommegosztás

Prémium szintű bárki, belül vagy kívül a szervezet akár megtekintheti a Power BI-tartalmakat, beleértve a többoldalas és interaktív jelentéseket az egyes licencek vásárlása nélkül. 

![Tartalom megosztása](media/service-premium-what-is/premium-sharing.png)

Prémium szintű lehetővé teszi, hogy a tartalom a Pro-felhasználók széles körű terjesztés anélkül, hogy Pro-licenceket a címzetteket, akik a tartalom megtekintésére. Pro-licencek tartalomkészítők számára szükségesek. Létrehozói csatlakozhat adatforrásokhoz, a modell adatait, és létrehozhat jelentéseket és irányítópultokat, amelyek a munkaterület-alkalmazásokként vannak csomagolva. 

További tudnivalókért lásd: [Power BI-licencelés](service-admin-licensing-organization.md).

## <a name="tool-connectivity-preview"></a>Eszköz kapcsolat (előzetes verzió)

Technikai részletek, a bevált Microsoft vállalati **Analysis Services Vertipaq motor** Power BI-adatkészleteket használja. Analysis Services kínálja programozhatóság, és ügyfél-alkalmazás és eszköz támogatja a klienskódtárak és API-k, amelyek támogatják az XMLA nyílt szabványú protokoll használatával. Jelenleg támogatja a Power BI prémium szintű adatkészleteiket *csak olvasható* műveleteket a Microsoft és külső ügyfél-alkalmazások és eszközök keresztül **XMLA végpontok**. 

A Microsoft eszközök, mint például az SQL Server Management Studio és az SQL Server Profiler és a külső alkalmazások, például a DAX Studio és a Vizualizáció alkalmazások, csatlakozhat és prémium szintű adatkészleteiket lekérdezése XMLA, a DAX, a MDX, a dinamikus felügyeleti nézetek és a nyomkövetési események használatával. 

![SSMS](media/service-premium-what-is/connect-tools-ssms-dax.png)

További tudnivalókért lásd: [csatlakozhat az eszközök és az ügyfélalkalmazások adatkészletek](service-premium-connect-tools.md).

## <a name="acknowledgements"></a>Nyugtázás

Peter Myers, a Data Platform MVP és a független, a BI-Szakértővé [bitenként megoldások](https://www.bitwisesolutions.com.au/), és a Microsoft Power BI ügyfél Ügyféltanácsadói csapat Kivitelezésén közreműködők erre a cikkre.

## <a name="next-steps"></a>Következő lépések

> [!div class="nextstepaction"]
> [Prémium szintű kapacitások kezelése](service-premium-capacity-manage.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

||||||
