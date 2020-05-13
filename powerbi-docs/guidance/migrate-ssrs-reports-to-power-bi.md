---
title: SQL Server Reporting Services-jelentések migrálása a Power BI-ba
description: Útmutató az SQL Server Reporting Services- (SSRS-) jelentések a Power BI-ba való migrálásához.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/03/2020
ms.author: v-pemyer
ms.openlocfilehash: d9fd23a0cf5c3ed26c78e4c53ae600bf74daca91
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83348183"
---
# <a name="migrate-sql-server-reporting-services-reports-to-power-bi"></a>SQL Server Reporting Services-jelentések migrálása a Power BI-ba

Ez a cikk az SQL Server Reporting Services (SSRS) jelentéskészítőinek és Power BI-rendszergazdáknak szól. Útmutatást nyújt a [Report Definition Language- (RDL-)](/sql/reporting-services/reports/report-definition-language-ssrs) jelentések a Power BI-ba való migrálásához.

> [!NOTE]
> Csal RDL-jelentések migrálhatók. A Power BI-ban az RDL-jelentéseket _lapszámozott jelentéseknek_ nevezzük.

Az útmutató négy szakaszra oszlik. Javasoljuk, hogy a jelentések migrálása előtt a teljes cikket olvassa el.

1. [Előkészületek](#before-you-start)
1. [Migrálás előtti szakasz](#pre-migration-stage)
1. [Migrálási szakasz](#migration-stage)
1. [Migrálás utáni szakasz](#post-migration-stage)

A migrálást az SSRS-kiszolgálók leállása és a jelentésfelhasználók oldalán tapasztalt megszakítások nélkül elvégezheti. Fontos tudnia, hogy ehhez nem kell adatokat vagy jelentéseket eltávolítania. Az aktuális környezetét tehát megtarthatja mindaddig, amíg fel nem készült annak kivezetésére.

## <a name="before-you-start"></a>Előzetes teendők

A migrálás megkezdése előtt ellenőrizze, hogy a környezet megfelel-e bizonyos előfeltételeknek. Itt ismertetjük ezeket, és egy hasznos migrálási eszközt is bemutatunk.

### <a name="preparing-for-migration"></a>A migrálás előkészítése

A Power BI-ba való jelentésmigrálás előkészítésének első lépéseként ellenőrizze, hogy szervezete rendelkezik-e [Power BI Premium](../admin/service-premium-what-is.md) előfizetéssel. A Power BI lapszámozott jelentéseinek üzemeltetéséhez és futtatásához szükség van erre az előfizetésre.

### <a name="supported-versions"></a>Támogatott verziók

Helyszínen vagy felhőszolgáltatón (például az Azure-on) üzemeltetett virtuális gépeken futó SSRS-példányokat migrálhat.

Az alábbi lista a Power BI-ba való migráláshoz támogatott SQL Server-verziókat ismerteti:

> [!div class="checklist"]
> - SQL Server 2012
> - SQL Server 2014
> - SQL Server 2016
> - SQL Server 2017
> - SQL Server 2019

A Power BI jelentéskészítő kiszolgálóról is migrálhat.

### <a name="migration-tool"></a>Áttelepítési eszköz

A jelentések előkészítéséhez és migrálásához az [RDL Migration Tool](https://github.com/microsoft/RdlMigration) használatát javasoljuk. Ezt a Microsoft fejlesztette ki az RDL-jelentések az SSRS-kiszolgálókról a Power BI-ba való migrálásához. A GitHubon elérhető, és a migrálási forgatókönyv összes lépését bemutatja.

Az eszköz a következő feladatokat automatizálja:

* [Nem támogatott adatforrásokat](../paginated-reports/paginated-reports-data-sources.md) és [nem támogatott jelentésfunkciókat](../paginated-reports/paginated-reports-faq.md#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi) keres
* A _megosztott_ erőforrásokat _beágyazott_-erőforrássá alakítja:
  * A megosztott **adatforrások** beágyazott adatforrássá válnak
  * A megosztott **adatkészletek** beágyazott adatkészletté válnak
* Jelentéseket tesz közzé (amelyek megfelelnek az ellenőrzéseknek) lapszámozott jelentésként egy adott Power BI-munkaterületen (egy Prémium-kapacitáson)

Nem módosítja vagy nem távolítja el a meglévő jelentéseket. A művelet befejezésekor az eszköz összegzi az összes befejezett műveletet, azok sikerességétől függetlenül.

A Microsoft idővel fejlesztheti az eszközt. A közösséget is ösztönözzük, hogy járuljon hozzá és segítsen fejleszteni.

## <a name="pre-migration-stage"></a>Migrálás előtti szakasz

Ha meggyőződött arról, hogy a szervezete megfelel az előfeltételeknek, készen áll a _migrálás előtti_ szakasz megkezdésére. Ez a szakasz három fázist tartalmaz:

1. Felderítés
1. Kiértékelés
1. Előkészítés

### <a name="discover"></a>Felderítés

A _felderítési_ fázis célja a meglévő SSRS-példányok azonosítása. Ez a folyamat a szervezet összes SQL Server-példányát megvizsgálja és azonosítja.

Használhatja a [Microsoft felmérési és tervezési eszközkészletet](https://www.microsoft.com/download/details.aspx?id=7826). A MAP eszközkészlet feltárja és jelentést készít az SQL Server-példányokról, -verziókról és az ezen telepített funkciókról. Ez egy hatékony leltározási, felmérési és jelentéskészítési eszköz, amely leegyszerűsíti a migrálás megtervezésének folyamatát.

### <a name="assess"></a>Kiértékelés

Ha felderítette az SSRS-példányokat, a _kiértékelési_ fázisban megismerheti a nem migrálható SSRS-jelentéseket és kiszolgálóelemeket.

Az SSRS-kiszolgálókról csak RDL-jelentések migrálhatók a Power BI-ra. Minden migrált RDL-jelentés lapszámozott jelentés lesz a Power BI-ban.

A következő SSRS-elemtípusok azonban nem migrálhatók a Power BI-ba:

- Megosztott adatforrások <sup>1</sup>
- Megosztott adatkészletek <sup>1</sup>
- Erőforrások, például képfájlok
- KPI-k (SSRS 2016 vagy újabb – csak az Enterprise kiadásban)
- Mobiljelentések (SSRS 2016 vagy újabb – csak az Enterprise kiadásban)
- Jelentésmodellek (elavult)
- Jelentésrészek (elavult)

<sup>1</sup> A [RDL Migration Tool](https://github.com/microsoft/RdlMigration) automatikusan átalakítja a megosztott adatforrásokat és a megosztott adatkészleteket – amennyiben ezek támogatott adatforrásokat használnak.

Ha az RDL-jelentései olyan funkciókra alapulnak, amelyeket [még nem támogatnak a Power BI lapszámozott jelentései](../paginated-reports/paginated-reports-faq.md#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi), akkor ezeket [Power BI-jelentésekként](../consumer/end-user-reports.md) újrafejlesztheti. Még ha migrálhatók is az RDL-jelentései, javasoljuk, hogy Power BI-jelentésekként modernizálja ezeket olyan esetekben, ahol ez hatékony.

Ha az RDL-jelentésekben _helyszíni adatforrásokból_ kell lekérnie az adatokat, akkor nem használhat egyszeri bejelentkezést (SSO). Jelenleg az ezekből a forrásokból beolvasott adatok az _átjáró adatforrásának felhasználói fiókja_ biztonsági környezetében lesznek végrehajtva. SQL Server Analysis Services (SSAS) esetében nem lehetséges a sorszintű biztonság (RLS) felhasználónkénti kényszerítése.

A Power BI lapszámozott jelentései általában **nyomtatáshoz** vagy **PDF-létrehozáshoz** vannak optimalizálva. A Power BI-jelentések **áttekintéshez és interaktivitáshoz** ideálisak. További információ: [Többoldalas jelentések használata a Power BI-ban](report-paginated-or-power-bi.md).

### <a name="prepare"></a>Előkészítés

A _előkészítési_ fázis célja, hogy minden készen álljon. Ismerteti a Power BI-környezet beállítását, a jelentések biztonságossá tételének és közzétételének megtervezését, valamint a nem migrált SSRS-elemek újrafejlesztéséhez használható ötleteket.

1. Győződjön meg arról, hogy a [Lapszámozott jelentések számítási feladat](../admin/service-admin-premium-workloads.md#paginated-reports) engedélyezve van a Power BI Premium-kapacitáshoz, és hogy elegendő memóriával rendelkezik.
1. Ellenőrizze a jelentés [adatforrásainak](../paginated-reports/paginated-reports-data-sources.md) támogatását, és állítson be egy [Power BI-átjárót](../connect-data/service-gateway-onprem.md), amely lehetővé teszi a helyszíni adatforrásokhoz való kapcsolódást.
1. Ismerje meg a Power BI biztonsági funkcióit, és tervezze meg, [hogyan fogja reprodukálni az SSRS-mappákat és az engedélyeket](/sql/reporting-services/security/secure-folders) a [Power BI munkaterületeivel és munkaterület-szerepköreivel](../collaborate-share/service-new-workspaces.md).
1. Ismerje meg a Power BI megosztási funkcióit, és tervezze meg, hogyan fogja terjeszteni a tartalmat [Power BI-alkalmazások](../collaborate-share/service-create-distribute-apps.md) közzétételével.
1. Használjon [megosztott Power BI-adatkészleteket](../connect-data/service-datasets-build-permissions.md) az SSRS megosztott adatforrásai helyett.
1. A [Power BI Desktoppal](../fundamentals/desktop-what-is-desktop.md) fejlesszen mobilra optimalizált jelentéseket. Ehhez a [Power KPI egyéni vizualizációt](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083?tab=Overview) is használhatja az SSRS-mobiljelentések és KPI-k helyett.
1. A **UserID** (Felhasználóazonosító) beépített mező használatának újraértékelése a jelentésekben. Ha a jelentés adatainak védelmekor a **UserID** mezőre hagyatkozik, akkor vegye figyelembe, hogy ez az oldalakra osztott jelentések (ha a Power BI szolgáltatásban tárolják) esetében az egyszerű felhasználónevet (UPN) adja vissza. Tehát az NT-fióknév, például az _AW\mblythe_ visszaadása helyett a beépített mező az _m.blythe&commat;adventureworks.com_ értékhez hasonlót fog visszaadni. Át kell néznie az adathalmaz definícióit és lehet, hogy még a forrásadatokat is. Az áttekintést és közzétételt követően javasoljuk a jelentések alapos tesztelését, hogy az adatengedélyek a várt módon működjenek.
1. Az **ExecutionTime** (Végrehajtási idő) beépített mező használatának újraértékelése a jelentésekben. Az oldalakra osztott jelentések esetében (ha a Power BI szolgáltatásban tárolják), a beépített mező a dátum/idő értéket _egyezményes világidő (vagy UTC)_ értékként adja vissza. Ez hatással lehet a jelentésparaméterek alapértelmezett értékeire és a jelentés-végrehajtási időcímkékre (amelyeket általában a jelentés lábléceihez adnak hozzá).
1. Ha az adatforrás a (helyszíni) SQL Server, ellenőrizze, hogy a jelentések nem használnak-e térkép-vizualizációkat. A térkép-vizualizáció az SQL Server térbeli adattípusaitól függ, amelyeket az átjáró nem támogat. További információ: [Adatlekérési útmutató lapszámozott jelentésekhez (Az SQL Server összetett adattípusai)](report-paginated-data-retrieval.md#sql-server-complex-data-types).
1. Győződjön meg arról, hogy a jelentéskészítők rendelkeznek a [Power BI Jelentéskészítővel](../paginated-reports/report-builder-power-bi.md), és hogy a későbbi kiadások könnyen terjeszthetők a szervezeten belül.

## <a name="migration-stage"></a>Migrálási szakasz

Power BI-környezet és a jelentések előkészítése után készen áll a _migrálási_ szakaszra.

Két migrálási lehetőség közül választhat: _manuális_ és _automatizált_. A manuális migrálás kis számú jelentéshez vagy a migrálás előtt módosítást igénylő jelentésekhez ideális. Az automatizált áttelepítés nagy számú jelentés migrálásához illik.

### <a name="manual-migration"></a>Manuális migrálás

Minden, az SSRS-példányhoz és a Power BI-munkaterülethez hozzáféréssel rendelkező felhasználó migrálhat jelentéseket a Power BI-ba. A lépések a következők:

1. Nyissa meg az SSRS portálját, amely a migrálni kívánt jelentéseket tartalmazza.
1. Töltse le az összes jelentésdefiníciót, és mentse helyileg az .rdl-fájlokat.
1. Nyissa meg a _Power BI Jelentéskészítő_ legújabb verzióját, és kapcsolódjon a Power BI szolgáltatáshoz az Azure AD-beli hitelesítő adataival.
1. Nyissa meg a jelentéseket a Power BI Jelentéskészítőben, majd tegye a következőket:
   1. Győződjön meg arról, hogy az összes adatforrás és adatkészlet be van ágyazva a jelentésdefinícióba, és hogy ezek [támogatott adatforrások](../paginated-reports/paginated-reports-data-sources.md).
   1. Tekintse meg a jelentés előnézetét, és győződjön meg arról, hogy megfelelően jelenik meg.
   1. Válassza a _Mentés másként_ lehetőséget, majd a _Power BI szolgáltatás_ elemet.
   1. Válassza ki azt a munkaterületet, amely a jelentést fogja tartalmazni.
   1. Ellenőrizze, hogy a jelentés mentése megtörtént-e. Ha a jelentésterv bizonyos funkciói még nem támogatottak, a mentés nem fog sikerülni. A rendszer értesítést küld ennek okairól. Ezután módosítania kell a jelentés tervét, és újra meg kell próbálnia a mentést.

### <a name="automated-migration"></a>Automatikus migrálást

Az automatikus migráláshoz két lehetőség áll rendelkezésre. Az alábbi eszközöket használhatja:

- Az RDL Migration Tool
- Az SSRS és a Power BI nyilvánosan elérhető API-jai

A cikkben már ismertettük az [RDL Migration Toolt](#migration-tool).

A tartalom migrálásának automatizálásához emellett a nyilvánosan elérhető SSRS és Power BI API-kat is használhatja. Habár az RDL-áttelepítési eszköz már használja ezeket az API-kat, Ön kialakíthat egy egyéni eszközt, amely pontosan megfelel a követelményeknek.

Az API-król további információt itt talál:

- [A Power BI REST API-jainak leírása](../developer/automation/rest-api-reference.md)
- [Az SQL server Reporting Services REST API-jai](/sql/reporting-services/developer/rest-api)

## <a name="post-migration-stage"></a>Migrálás utáni szakasz

Miután sikeresen elvégezte a migrálást, készen áll a _migrálás utáni_ szakaszra. Ebben a fázisban több migrálást követő feladatot is el kell végeznie annak érdekében, hogy minden megfelelően és hatékonyan működjön.

### <a name="configure-data-sources"></a>Adatforrások konfigurálása

Miután migrálta a jelentéseket a Power BI-ba, gondoskodnia kell arról, hogy az adatforrásaik megfelelően legyenek beállítva. Ez magában foglalhatja az átjáró-adatforrások hozzárendelését, és [az adatforrások hitelesítő adatainak biztonságos tárolását](../paginated-reports/paginated-reports-data-sources.md#azure-sql-database-authentication). Ezeket a műveleteket nem az RDL Migration Tool végzi.

### <a name="review-report-performance"></a>A jelentésteljesítmény áttekintése

Javasoljuk, hogy a lehető legjobb felhasználói élmény érdekében végezze el az alábbi műveleteket:

1. Tesztelje a jelentéseket a [Power BI által támogatott összes böngészőben](../fundamentals/power-bi-browsers.md), így meggyőződhet arról, hogy azok megfelelően lesznek renderelve.
1. Futtasson teszteket, amelyekkel összehasonlítja az SSRS és a Power BI jelentésrenderelési idejeit. Ellenőrizze, hogy a Power BI-jelentések renderelésének ideje elfogadható-e.
1. Ha a Power BI-jelentések renderelése meghiúsul a nem elegendő memória miatt, foglaljon le [további erőforrásokat a Power BI Premium-kapacitásban](../admin/service-admin-premium-workloads.md#paginated-reports).
1. A hosszú renderelési idejű jelentések esetén célszerű lehet a Power BI által eljuttatni őket a felhasználóknak, [jelentésmellékleteket tartalmazó e-mail-feliratkozásként](../consumer/paginated-reports-subscriptions.md).
1. Power BI-adatkészleteken alapuló Power BI-jelentések esetén tekintse át a modellterveket, így meggyőződhet arról, hogy teljes mértékben optimalizálva vannak.

### <a name="reconcile-issues"></a>A problémák megoldása

A migrálás utáni fázis elengedhetetlen az esetleges hibák feloldásához, valamint az esetleges teljesítménnyel kapcsolatos problémák megoldásához. Ha hozzáadja a Lapszámozott jelentések számítási feladatot egy kapacitáshoz, azzal lelassíthatja a lapszámozott jelentések és a kapacitásban tárolt _egyéb tartalmak_ teljesítményét.

További információt ezekről a problémákról, beleértve ezek ismertetését és megoldását, a következő cikkekben találhat:

- [Premium-kapacitások optimalizálása](../admin/service-premium-capacity-optimize.md)
- [Premium-kapacitások monitorozása az alkalmazásban](../admin/service-admin-premium-monitor-capacity.md)

## <a name="next-steps"></a>Következő lépések

Erről a cikkről a következő forrásanyagokban talál további információt:

- [Mik a lapszámozott jelentések a Power BI Premiumban?](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [Adatlekérési útmutató lapszámozott jelentésekhez](report-paginated-data-retrieval.md)
- [Többoldalas jelentések használata a Power BI-ban](report-paginated-or-power-bi.md)
- [Lapszámozott jelentések a Power BI-ban: GYIK](../paginated-reports/paginated-reports-faq.md)
- [Online kurzus: Lapszámozott jelentések egy nap alatt](../paginated-reports/paginated-reports-online-course.md)
- [Power BI Premium – gyakori kérdések](../admin/service-premium-faq.md)
- [RDL Migration Tool](https://github.com/microsoft/RdlMigration)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
- Javaslatai vannak? [A Power BI javítására vonatkozó ötletek beküldése](https://ideas.powerbi.com)

A Power BI-partnerek segíthetnek a migrálási folyamatban. Power BI-partner bevonásához látogasson el a [Power BI partnerportálra](https://powerbi.microsoft.com/partners/).
