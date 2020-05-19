---
title: Üzembehelyezési folyamatok
description: A Power BI üzembehelyezési folyamatainak megismerése
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 05/06/2020
ms.openlocfilehash: c4a823b0b41def6c10cd8f932bb97e91eb977ecb
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83148596"
---
# <a name="understand-the-deployment-process-preview"></a>Az üzembehelyezési folyamat megismerése (előzetes verzió)

Az üzembehelyezési folyamat lehetővé teszi, hogy tartalmat klónozzon a folyamat egyik szakaszából a másikba, általában fejlesztési környezetből tesztkörnyezetbe, vagy tesztkörnyezetből éles környezetbe.

Az üzembe helyezés során a Power BI az aktuális szakaszból a célszakaszba másolja a tartalmat. A másolási folyamat során a rendszer megőrzi a másolt elemek közötti kapcsolatokat. A Power BI továbbá alkalmazza a konfigurált adathalmazszabályokat a célszakasz frissített tartalmára. Az üzembe helyezett elemek számától függően az üzembe helyezés eltarthat egy ideig. Ez alatt az idő alatt megtekintheti a Power BI portál más oldalait, de nem használhatja a tartalmat a célszakaszban.

## <a name="deploying-content-to-an-empty-stage"></a>Tartalom üres szakaszban történő üzembe helyezése

Tartalom üres szakaszban történő üzembe helyezésekor a rendszer az üzembe helyezés céljaként szolgáló szakaszba másolja az üzembe helyezés forrásaként szolgáló munkaterület jelentéseinek, irányítópultjainak és adathalmazainak metaadatait. Az üzembe helyezés céljaként szolgáló szakaszhoz létrejön egy új munkaterület egy prémium szintű kapacitáson.

A tartalom egyik szakaszból másikba történő üzembe helyezésének két módja van. Üzembe helyezheti az összes tartalmat, vagy [kiválaszthatja, mely tartalomelemeket szeretné üzembe helyezni](deployment-pipelines-get-started.md#selective-deployment).

A tartalmat visszafelé, az üzembehelyezési folyamat egy későbbi szakaszából egy korábbi szakaszra irányulóan is üzembe helyezheti.

Az üzembe helyezés befejezte után frissítse az adathalmazokat, hogy használhassa az újonnan másolt tartalmat. Az adathalmazok frissítésére azért van szükség, mert a rendszer nem másolja az adatokat az egyik szakaszból a másikba. Ha szeretné megtudni, hogy az üzembehelyezési folyamat során a rendszer mely elemtulajdonságokat másolja, és melyeket nem, tekintse át [az üzembe helyezés során másolt elemtulajdonságokkal](#item-properties-copied-during-deployment) foglalkozó szakaszt.

### <a name="creating-a-premium-capacity-workspace"></a>Prémium szintű kapacitáson futó munkaterület létrehozása

Az első üzembe helyezés során az üzembehelyezési folyamat ellenőrzi, hogy rendelkezik-e Prémium szintű kapacitásra vonatkozó engedélyekkel.  

Ha rendelkezik a kapacitásra vonatkozó engedélyekkel, a rendszer az üzembe helyezés céljaként szolgáló szakaszba másolja a munkaterület tartalmát, és létrehoz hozzá egy új munkaterületet a Prémium szintű kapacitáson.

Ha nem rendelkezik kapacitásra vonatkozó engedélyekkel, a rendszer létrehozza a munkaterületet, de nem másolja a tartalmat. Kérjen meg egy kapacitás-rendszergazdát, hogy adja hozzá a munkaterületet egy kapacitáshoz, vagy kérjen hozzárendelési engedélyeket a kapacitáshoz. Később, ha a munkaterület már hozzá van rendelve egy kapacitáshoz, üzembe helyezheti a tartalmat a munkaterületen.

### <a name="workspace-and-content-ownership"></a>Munkaterület és tartalom tulajdonjoga

Az üzembe helyezést végző felhasználó automatikusan a klónozott adathalmazok adathalmaz-tulajdonosává és az új munkaterület kizárólagos rendszergazdájává válik.

## <a name="deploy-content-to-an-existing-workspace"></a>Tartalom üzembe helyezése meglévő munkaterületen

A tartalom éles munkafolyamatban, meglévő munkaterülettel rendelkező szakaszban történő üzembe helyezése az alábbiakat foglalja magában:

* Új tartalom üzembe helyezése kiegészítésként egy tartalommal már rendelkező szakaszban.

* Új tartalom üzembe helyezése a régi tartalom lecserélése céljából egy aktuális munkaszakaszban.

### <a name="deployment-process"></a>Üzembehelyezési folyamat

A rendszer a célszakaszba másolja az aktuális szakasz tartalmát. A Power BI azonosítja a meglévő tartalmat a célszakaszban, és felülírja azt. Az üzembehelyezési folyamat a szülő elem és annak klónjai közötti kapcsolat használatával azonosítja a felülírandó tartalomelemeket. Új tartalom létrehozásakor a rendszer megőrzi ezt a kapcsolatot. A felülírási művelet csak az elem tartalmát írja felül. Az elem azonosítója, URL-címe és engedélyei változatlanok maradnak.

A célszakaszban [a nem másolt elemtulajdonságok](deployment-pipelines-process.md#item-properties-that-are-not-copied) az üzembe helyezés előtti állapotukban maradnak. A rendszer az aktuális szakaszból a célszakaszba másolja az új tartalmat és az új elemeket.

### <a name="refreshing-the-dataset"></a>Az adathalmaz frissítése

Ha lehetséges, a rendszer megőrzi az adatokat a céladathalmazban. Ha az adathalmaz nem módosult, az adatok az üzembe helyezés előtti állapotukban maradnak.

A Power BI kis módosításokkal (például egy táblázat vagy számított mértékek hozzáadásával) megőrzi az eredeti adatokat, és úgy optimalizálja a frissítést, hogy csak az frissüljön, aminek kell. Kompatibilitástörő sémaváltozások vagy adatforráskapcsolat-változások esetén teljes frissítésre van szükség.

### <a name="requirements-for-deploying-to-a-stage-with-an-existing-workspace"></a>A meglévő munkaterülettel rendelkező szakaszban történő üzembe helyezésre vonatkozó követelmények

Ha az üzembe helyezett tartalom egy [prémium szintű kapacitáson](../admin/service-premium-what-is.md) található, akkor az alábbi feltételeknek megfelelő felhasználók üzembe helyezhetik a tartalmat egy meglévő munkaterülettel rendelkező szakaszban:

* [Pro-felhasználó](../admin/service-admin-purchasing-power-bi-pro.md), aki az üzembe helyezés forrás- és célszakaszában található mindkét munkaterület tagja.

* Az üzembe helyezni kívánt célmunkaterület összes adathalmazának tulajdonosa.

További információért tekintse át az [engedélyekkel](#permissions) foglalkozó szakaszt.

## <a name="deployed-items"></a>Üzembe helyezett elemek

Amikor tartalmat helyez üzembe az egyik folyamatszakaszból a másikba, a másolt tartalom az alábbi Power BI-elemeket tartalmazza:

* Adathalmazok

* Jelentések

* Irányítópultok

### <a name="unsupported-items"></a>Nem támogatott elemek

Az üzembehelyezési folyamatok nem támogatják az alábbi elemeket:

* Nem .pbix-fájlból eredő adathalmazok

* Nem támogatott adathalmazokon alapuló jelentések

* A munkaterület nem használhat sablonalkalmazást

* Oldalakra osztott jelentések

* Adatfolyamok

* LEKÜLDÉSES adathalmazok

* Munkafüzetek

## <a name="item-properties-copied-during-deployment"></a>Üzembe helyezés során másolt elemtulajdonságok

Az üzembe helyezés során a rendszer az alábbi elemtulajdonságokat másolja, amelyek felülírják a célszakasz elemtulajdonságait:

* Adatforrások (az [adathalmazszabályok](deployment-pipelines-get-started.md#step-4---create-dataset-rules) támogatottak)

* Paraméterek (az [adathalmazszabályok](deployment-pipelines-get-started.md#step-4---create-dataset-rules) támogatottak)

* Jelentésvizualizációk

* Jelentésoldalak

* Irányítópult-csempék

* Modell metaadatai

* Elemkapcsolatok

### <a name="item-properties-that-are-not-copied"></a>Nem másolt elemtulajdonságok

Üzembe helyezés során a rendszer nem másolja az alábbi elemtulajdonságokat:

* Adatok – A rendszer csak a metaadatokat másolja, az adatokat nem

* URL-cím

* ID

* Engedélyek – Munkaterülethez vagy adott elemhez

* Munkaterület beállításai – Minden szakasz saját munkaterülettel rendelkezik

* Alkalmazás tartalma és beállításai – Az alkalmazások üzembe helyezéséhez tekintse meg[a Power BI-alkalmazások üzembe helyezésével](#deploying-power-bi-apps) foglalkozó szakaszt

Üzembe helyezés során a rendszer az alábbi adathalmaz-tulajdonságokat sem másolja:

* Szerepkör-kijelölés
    
* Frissítési ütemezés
    
* Adatforráshoz tartozó hitelesítő adatok
    
* Lekérdezés-gyorsítótárazási beállítások (öröklődhet a kapacitásból)
    
* Ellenőrzés beállításai

## <a name="deploying-power-bi-apps"></a>Power BI-alkalmazások üzembe helyezése

A tartalmak ingyenes szintű Power BI-felhasználókkal történő megosztásához a [Power BI-alkalmazások](../consumer/end-user-apps.md) javasoltak. Az üzembehelyezési folyamatok használatával felügyelheti az üzembehelyezési folyamatban található Power BI-alkalmazásokat, így nagyobb mértékű vezérléssel és rugalmassággal kezelheti az alkalmazás életciklusát.

Létrehozhat egy alkalmazást minden üzembehelyezési folyamatszakaszhoz, így tesztelheti az egyes alkalmazásfrissítéseket a végfelhasználó szemszögéből. Az üzembehelyezési folyamattal egyszerűen felügyelheti ezt az eljárást. A munkaterület kártyáján található közzététel vagy megtekintés gombra kattintva közzéteheti vagy megtekintheti az alkalmazást egy bizonyos folyamatszakaszban.

[![](media/deployment-pipelines-process/publish.png "Publish app")](media/deployment-pipelines-process/publish.png#lightbox)

Az éles szakaszban a bal alsó sarokban található fő műveletgomb megnyitja az alkalmazásfrissítési oldalt a Power BI-ban, így a tartalomfrissítések elérhetővé válnak az alkalmazás felhasználói számára.

[![](media/deployment-pipelines-process/update-app.png "Update app")](media/deployment-pipelines-process/update-app.png#lightbox)

>[!IMPORTANT]
>Az üzembehelyezési folyamat nem foglalja magában az alkalmazás tartalmának és beállításainak frissítését. A módosítások tartalomra vagy beállításokra való alkalmazásához manuálisan kell frissítenie az alkalmazást a folyamat megfelelő szakaszában.

## <a name="permissions"></a>Engedélyek

A folyamatra és a munkaterületre vonatkozó engedélyek megadása és kezelése egymástól függetlenül történik. Az a felhasználó például, aki olyan folyamat-hozzáféréssel rendelkezik, amelyhez nem járulnak munkaterület-engedélyek, megtekintheti a folyamatot, és meg is oszthatja másokkal. Ez a felhasználó azonban nem tekintheti meg munkaterület tartalmát a folyamatban vagy a munkaterület oldalán, és nem hajthat végre üzembe helyezéseket.

### <a name="user-with-pipeline-access"></a>Folyamat-hozzáféréssel rendelkező felhasználók

A folyamat-hozzáféréssel rendelkező felhasználók az alábbi engedélyekkel rendelkeznek:

* A folyamat megtekintése
    
* A folyamat megosztása másokkal
    
* A folyamat szerkesztése és törlése

>[!NOTE]
>A folyamat-hozzáféréssel nem jár engedély a munkaterület tartalmának megtekintésére és műveletek elvégzésére.

### <a name="workspace-viewer"></a>Munkaterület megtekintője

A munkaterület *folyamat-hozzáféréssel* rendelkező megtekintői az alábbiakat is elvégezhetik:

* Tartalom felhasználása

>[!NOTE]
>A munkaterület megtekintői nem férhetnek hozzá az adathalmazhoz, és nem szerkeszthetik a munkaterület tartalmát.

### <a name="workspace-contributor"></a>Munkaterület közreműködője

A munkaterület *folyamat-hozzáféréssel* rendelkező közreműködői az alábbiakat is elvégezhetik:

* Tartalom felhasználása

* Szakaszok összehasonlítása

* Adathalmazok megtekintése

### <a name="workspace-member"></a>Munkaterület tagja

A munkaterület *folyamat-hozzáféréssel* rendelkező tagjai az alábbiakat is elvégezhetik:

* Munkaterület tartalmának megtekintése
    
* Szakaszok összehasonlítása
    
* Jelentések és irányítópultok üzembe helyezése

* Munkaterületek eltávolítása

### <a name="workspace-admin"></a>Munkaterületi rendszergazda

A munkaterület *folyamat-hozzáféréssel* rendelkező rendszergazdái végrehajthatják *a munkaterület tagjai* számára elérhető műveleteket, továbbá az alábbiakat is elvégezhetik:

* Munkaterületek hozzárendelése

* Munkaterületek eltávolítása

### <a name="dataset-owner"></a>Adathalmaz tulajdonosa

Azok az adathalmaz-tulajdonosok, akik egy munkaterület tagjai vagy rendszergazdái, az alábbiakat is elvégezhetik:

* Adathalmazok frissítése
    
* Szabályok konfigurálása

>[!NOTE]
>Ez a szakasz az üzembehelyezési folyamatok felhasználói engedélyeit ismerteti. Előfordulhat, hogy a jelen szakaszban felsorolt engedélyek eltérő alkalmazási módokkal rendelkeznek a többi Power BI-funkcióban.

## <a name="limitations"></a>Korlátozások

Ez a szakasz ismerteti az üzembehelyezési folyamatokra vonatkozó legtöbb korlátozást.

* A munkaterületnek  [prémium szintű kapacitáson](../admin/service-premium-what-is.md) kell lennie.

* A Power BI-[bizalmassági címkével](../admin/service-security-data-protection-overview.md#sensitivity-labels-in-power-bi) rendelkező Power BI-elemek (például jelentések vagy irányítópultok) nem helyezhetők üzembe.

* A [növekményes frissítéssel](../admin/service-premium-incremental-refresh.md) konfigurált adathalmazok nem helyezhetők üzembe.

* A munkaterületekre vonatkozó korlátozások listájáért tekintse meg a [munkaterületekre vonatkozó korlátozásokkal](deployment-pipelines-get-started.md#workspace-assignment-limitations) foglalkozó szakaszt.

* Az adathalmazszabályokra vonatkozó korlátozások listájáért tekintse meg az [adathalmazszabályokra vonatkozó korlátozásokkal](deployment-pipelines-get-started.md#dataset-rule-limitations) foglalkozó szakaszt.

* A nem támogatott elemek listájáért tekintse meg a [nem támogatott elemekkel](#unsupported-items) foglalkozó szakaszt.

## <a name="next-steps"></a>Következő lépések

>[!div class="nextstepaction"]
>[Az üzembehelyezési folyamatok bemutatása](deployment-pipelines-overview.md)

>[!div class="nextstepaction"]
>[Ajánlott eljárások az üzembehelyezési folyamatokhoz](deployment-pipelines-best-practices.md)

>[!div class="nextstepaction"]
>[Az üzembehelyezési folyamatok használatának első lépései](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[Az üzembehelyezési folyamatok hibaelhárítása](deployment-pipelines-troubleshooting.md)