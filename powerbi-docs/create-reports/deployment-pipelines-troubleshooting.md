---
title: Az üzembehelyezési folyamatok hibaelhárítása
description: Az üzembehelyezési folyamatok hibaelhárítása a Power BI-ban
author: KesemSharabi
ms.author: kesharab
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 05/06/2020
ms.openlocfilehash: fda846a19b5c6081c59f08f2bf9f94eddbc9852c
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83148548"
---
# <a name="deployment-pipelines-troubleshooting-preview"></a>Az üzembehelyezési folyamatok hibaelhárítása (előzetes verzió)

Ebből a cikkből megismerheti, hogyan háríthatók el az üzembehelyezési folyamatok hibái.

## <a name="general"></a>Általános

### <a name="whats-deployment-pipelines-in-power-bi"></a>Mik azok az üzembehelyezési folyamatok a Power BI-ban?

Ha meg szeretné tudni, hogy mik azok az üzembehelyezési folyamatok a Power BI-ban, tekintse meg az [üzembehelyezési folyamatok áttekintését](deployment-pipelines-overview.md).

### <a name="how-do-i-get-started-with-deployment-pipelines"></a>Melyek az első lépések az üzembehelyezési folyamatok használatának megkezdésekor?

Az üzembehelyezési folyamatok használatával az [első lépéseket bemutató utasítások](deployment-pipelines-get-started.md) segítségével ismerkedhet meg.

### <a name="why-cant-i-see-the-deployment-pipelines-button"></a>Miért nem látom az üzembehelyezési folyamatok gombot?

Ha a következő feltételek nem teljesülnek, nem fogja látni az üzembehelyezési folyamatok gombot.

* Ön Power BI [Pro-felhasználó](../admin/service-admin-purchasing-power-bi-pro.md)

* Prémium szintű kapacitással rendelkező szervezethez tartozik

* Munkaterület csak egy folyamathoz rendelhető hozzá

* Ön egy új munkaterület rendszergazdája

## <a name="licensing"></a>Licencelés

### <a name="what-licenses-are-needed-to-work-with-deployment-pipelines"></a>Milyen licencekre van szükség az üzembehelyezési folyamatok használatához?

Az üzembehelyezési folyamatok használatához [Pro-felhasználói](../admin/service-admin-purchasing-power-bi-pro.md) szintre és [Prémium szintű kapacitásra](../admin/service-premium-what-is.md) van szükség. További információért tekintse meg az [üzembehelyezési folyamatokhoz való hozzáférést ismertető cikket](deployment-pipelines-get-started.md#accessing-deployment-pipelines).

### <a name="what-type-of-capacity-can-i-assign-to-a-workspace-in-a-pipeline"></a>Milyen típusú kapacitást rendelhetek hozzá egy folyamat munkaterületéhez?

Az üzembehelyezési folyamat minden munkaterületének egy dedikált kapacitásban kell lennie ahhoz, hogy a folyamat működjön. Azonban egy folyamat különböző munkaterületeihez használhat különböző kapacitásokat. Emellett ugyanazon folyamat különböző munkaterületeihez használhat különböző kapacitástípusokat is.

Fejlesztési és tesztelési célból használhat A vagy EM kapacitást is felhasználónként egy Pro Power BI-fiók mellett.

Az éles üzemű munkaterületekhez P kapacitásra van szükség. Ha Ön független szoftvergyártó, aki beágyazott alkalmazásokkal terjeszti a tartalmakat, éles környezethez is használhat A vagy EM kapacitást.

## <a name="technical"></a>Műszaki

### <a name="why-cant-i-see-all-my-workspaces-when-i-try-to-assign-a-workspace-to-a-pipeline"></a>Miért nem látom az összes munkaterületet, amikor munkaterületet próbálok hozzárendelni egy folyamathoz?

Ha munkaterületet szeretne hozzárendelni egy folyamathoz, a következő feltételeknek kell teljesülnie:

* A munkaterület egy [új munkaterületi felület](../collaborate-share/service-create-the-new-workspaces.md)

* Ön a munkaterület rendszergazdája

* A munkaterület nincs hozzárendelve egy másik folyamathoz

* A munkaterület [prémium szintű kapacitáson](../admin/service-premium-what-is.md) található

Azok a munkaterületek, amelyek nem felelnek meg ezeknek a feltételeknek, nem jelennek meg a választható munkaterületek listájában.

### <a name="how-can-i-assign-workspaces-to-all-the-stages-in-a-pipeline"></a>Hogyan rendelhetek hozzá munkaterületet egy folyamat minden szakaszához?

Folyamatonként egy munkaterületet rendelhet hozzá. Ha egy munkaterület hozzá lett rendelve egy folyamathoz, akkor a következő folyamatszakaszokban helyezheti üzembe. Az első üzembe helyezéskor a rendszer létrehoz egy új munkaterületet a forrásszakaszban található elemek másolataival. A másolt elemek közötti kapcsolatok nem vesznek el. További információért tekintse meg, hogyan [rendelhető hozzá munkaterület egy üzembehelyezési folyamathoz](deployment-pipelines-get-started.md#step-2---assign-a-workspace-to-a-deployment-pipeline).

### <a name="why-did-my-first-deployment-fail"></a>Miért hiúsult meg az első üzembe helyezés?

Az első üzembe helyezés több okból is meghiúsulhat. Néhány ilyen ok megtekinthető az alábbi táblázatban.

|Hiba  |Művelet  |
|---------|---------|
|Nem rendelkezik [prémium szintű kapacitásra vonatkozó engedélyekkel](deployment-pipelines-process.md#creating-a-premium-capacity-workspace).     |A prémium szintű kapacitási engedélyek beszerzéséhez kérjen meg egy kapacitás-rendszergazdát, hogy adja hozzá a munkaterületet egy kapacitáshoz, vagy kérjen hozzárendelési engedélyeket a kapacitáshoz. Miután a munkaterület bekerült a kapacitásba, végezze el újra az üzembe helyezést.        |
|Nem rendelkezik munkaterület-engedélyekkel.     |Az üzembe helyezéshez a munkaterület tagjának kell lennie. Kérje meg a munkaterület rendszergazdáját, hogy adja meg a megfelelő engedélyeket.         |
|A Power BI-rendszergazda letiltotta a munkaterületek létrehozását.     |Támogatásért lépjen kapcsolatba a Power BI-rendszergazdával.         |
|A munkaterület nem egy [új munkaterületi felület](../collaborate-share/service-create-the-new-workspaces.md).     |Az új munkaterületi felületen hozza létre a tartalmat. Ha klasszikus munkaterületen rendelkezik tartalommal, [frissítheti](../collaborate-share/service-upgrade-workspaces.md) a munkaterületet egy új munkaterületi felületre.         |
|[Szelektív üzembe helyezést](deployment-pipelines-get-started.md#selective-deployment) használ, és nem választotta ki a tartalom adathalmazát.     |Tegye a következők egyikét: </br></br>Szüntesse meg az adathalmazhoz csatlakoztatott tartalom kijelölését. A nem kijelölt tartalmakat (például jelentéseket vagy irányítópultokat) a rendszer nem másolja át a következő szakaszba. </br></br>Válassza ki a kiválasztott tartalomhoz csatlakoztatott adathalmazt. A rendszer átmásolja az adathalmazt a következő szakaszba.         |

### <a name="im-getting-a-warning-that-i-have-unsupported-artifacts-in-my-workspace-when-im-trying-to-deploy-how-can-i-know-which-artifacts-are-not-supported"></a>Az üzembe helyezéskor figyelmeztetés jelenik meg, amely szerint „nem támogatott összetevők” találhatók a munkaterületen. Hol tudhatom meg, hogy melyek a nem támogatott összetevők?

Az üzembehelyezési folyamatokban nem támogatott elemek és összetevők átfogó listájáért tekintse meg a következő részeket:

* [Nem támogatott elemek](deployment-pipelines-process.md#unsupported-items)

* [Nem másolt elemtulajdonságok](deployment-pipelines-process.md#item-properties-that-are-not-copied)

### <a name="why-did-my-deployment-fail-due-to-broken-rules"></a>Miért hiúsult meg az üzembe helyezés hibás szabályok miatt?

Ha problémája van az adathalmaz szabályainak konfigurálásakor, tekintse meg az [adathalmazszabályokat](deployment-pipelines-get-started.md#step-4---create-dataset-rules) és kövesse az [adathalmazszabályokra vonatkozó korlátozásokat](deployment-pipelines-get-started.md#dataset-rule-limitations).

Ha az üzembe helyezés korábban sikeres volt, de most hirtelen hibás szabályok miatt meghiúsul, ennek oka lehet, hogy az adathalmazt újból közzétették. A forrásadathalmaz következő módosításai miatt hiúsul meg az üzembe helyezés:

**Paraméterszabályok**

* Eltávolított paraméter

* Egy paraméter nevének megváltoztatása

**Adatforrásszabályok**

Az adathalmazszabályokból értékek hiányoznak. Ez akkor fordulhat elő, ha az adathalmaz módosult.

![hibás szabály](media/deployment-pipelines-troubleshooting/broken-rule.png)

Ha egy korábban sikeres üzembe helyezés hibás hivatkozások miatt meghiúsul, a rendszer figyelmeztetést jelenít meg. A **Szabályok konfigurálása** elemre kattintva az üzembehelyezési beállítások paneljére jut, ahol a meghiúsult adathalmaz meg van jelölve. Ha rákattint az adathalmazra, a hibás szabályokat megjelöli a rendszer.

A sikeres üzembe helyezéshez javítsa ki vagy távolítsa el a hibás szabályokat, majd végezze el újra az üzembe helyezést.

### <a name="how-can-i-change-the-data-source-in-the-pipeline-stages"></a>Hogyan módosíthatom az adatforrásokat a folyamat szakaszaiban?

A Power BI szolgáltatásban nem módosíthatja az adatforrás-kapcsolatot.

Ha módosítani szeretné az adatforrást a tesztelési vagy az éles szakaszban, ezt [adathalmazszabályok](deployment-pipelines-get-started.md#step-4---create-dataset-rules) vagy [API-k](https://docs.microsoft.com/rest/api/power-bi/datasets/updateparametersingroup) használatával teheti meg. Az adathalmazszabályok csak a következő üzembe helyezés után lépnek érvénybe.

### <a name="i-fixed-a-bug-in-production-but-now-i-cant-click-the-deploy-to-previous-stage-button-why-is-it-greyed-out"></a>Kijavítottam egy hibát az éles környezetben, de most nem tudok rákattintani az „üzembe helyezés az előző szakaszba” gombra. Miért szürkén jelenik meg ez a gomb?

Visszamenőleg csak üres szakaszba végezhető el az üzembe helyezés. Ha tartalom van a tesztelési szakaszban, az éles környezetből nem végezhető visszamenőleges üzembe helyezés.

A folyamat létrehozása után a fejlesztési szakasz segítségével fejleszthet tartalmakat, a tesztelési szakaszokkal pedig ellenőrizheti és tesztelheti azokat. Ezekben a szakaszokban kijavíthatja a hibákat, majd üzembe helyezheti a javított környezetet az éles szakaszban.

>[!NOTE]
>A visszamenőleges üzembe helyezés csak [teljes üzembe helyezés](deployment-pipelines-get-started.md#deploying-all-content) esetén támogatott. A [szelektív üzembe helyezés](deployment-pipelines-get-started.md#selective-deployment) nem támogatott.

### <a name="does-deployment-pipelines-support-multi-geo"></a>Az üzembehelyezési folyamatok támogatják a Multi-Geót?

A Multi-Geo támogatott. A tartalom üzembe helyezése különböző földrajzi helyeken található szakaszok között hosszabb időt vehet igénybe.

## <a name="permissions"></a>Engedélyek

### <a name="what-is-the-deployment-pipelines-permissions-model"></a>Mi az üzembehelyezési folyamatok engedélyezési modellje?

Az üzembe helyezési folyamatok engedélyezési modelljét az [engedélyek](deployment-pipelines-process.md#permissions) szakasz ismerteti.

### <a name="who-can-deploy-content-between-stages"></a>Kik helyezhetnek üzembe tartalmat a szakaszok között?

Tartalom egy üres szakaszba vagy egy tartalommal rendelkező szakaszba helyezhető üzembe. A tartalomnak [prémium szintű kapacitáson](../admin/service-premium-what-is.md) kell lennie.

* **Üzembe helyezés üres szakaszba** – Bármely [Pro-felhasználó](../admin/service-admin-purchasing-power-bi-pro.md), aki tag vagy rendszergazda a forrás munkaterületén.

* **Üzembe helyezés tartalommal rendelkező szakaszba** – Bármely [Pro-felhasználó](../admin/service-admin-purchasing-power-bi-pro.md), aki az üzembe helyezés forrás- és célszakaszában található mindkét munkaterület tagja vagy rendszergazdája.

* **Adathalmaz felülbírálása** – Az üzembe helyezés felülbírálja a célszakaszban található összes adathalmazt, még akkor is, ha az adathalmaz nem változott. A célszakasz az üzembe helyezésben megadott összes adathalmaza tulajdonosának a felhasználónak kell lennie.

### <a name="which-permissions-do-i-need-to-configure-dataset-rules"></a>Milyen engedélyek szükségesek az adathalmazszabályok konfigurálásához?

Az üzembehelyezési folyamatok adathalmazszabályainak konfigurálásához az adathalmaz tulajdonosának kell lennie.

### <a name="why-cant-i-see-workspaces-in-the-pipeline"></a>Miért nem látom a munkaterületeket a folyamatban?

A folyamat- és a munkaterület-engedélyeket külön kezeli a rendszer. Előfordulhat, hogy rendelkezik folyamatengedélyekkel, munkaterület-engedélyekkel azonban nem. További információért tekintse át az [engedélyekkel](deployment-pipelines-process.md#permissions) foglalkozó szakaszt.

## <a name="next-steps"></a>Következő lépések

>[!div class="nextstepaction"]
>[Az üzembehelyezési folyamatok bemutatása](deployment-pipelines-overview.md)

>[!div class="nextstepaction"]
>[Az üzembehelyezési folyamatok használatának első lépései](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[Az üzembehelyezési folyamatok feldolgozásának ismertetése](deployment-pipelines-process.md)

>[!div class="nextstepaction"]
>[Ajánlott eljárások az üzembehelyezési folyamatokhoz](deployment-pipelines-best-practices.md)