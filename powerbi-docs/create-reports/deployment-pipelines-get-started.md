---
title: Az üzembehelyezési folyamatok használatának első lépései
description: A Power BI-beli üzembehelyezési folyamatok használatának megismerése
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 05/06/2020
ms.openlocfilehash: 8dc0dc97e2b4bca7154ea0f13273ee2dbaee1b61
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83272833"
---
# <a name="get-started-with-deployment-pipelines-preview"></a>Bevezetés az üzembehelyezési folyamatok használatába (előzetes verzió)

Ez a cikk végigvezeti Önt az üzembehelyezési folyamatok használatához szükséges alapbeállítások megadásának lépésein.

## <a name="accessing-deployment-pipelines"></a>Hozzáférés az üzembehelyezési folyamatokhoz

Akkor férhet hozzá az üzembehelyezési folyamatok funkcióhoz, ha a következő feltételek teljesülnek:

* Ön Power BI [Pro-felhasználó](../admin/service-admin-purchasing-power-bi-pro.md)

* Prémium szintű kapacitással rendelkező szervezethez tartozik

* Ön egy [új munkaterületi felület](../collaborate-share/service-create-the-new-workspaces.md) rendszergazdája

>[!NOTE]
> Akkor is láthatja az üzembehelyezési folyamatok gombját, ha korábban létrehozott egy folyamatot, vagy ha egy folyamatot megosztottak Önnel.

![üzembehelyezési folyamatok kezdőlapja](media/deployment-pipelines-get-started/creating-pipeline.png)

## <a name="step-1---create-a-deployment-pipeline"></a>1\. lépés – Üzembehelyezési folyamat létrehozása

Üzembehelyezési folyamat létrehozásához tegye a következőket:

1. A Power BI szolgáltatás navigációs panelén válassza az **Üzembehelyezési folyamatok** lehetőséget, majd kattintson a **Folyamat létrehozása** parancsra.

2. Az *Üzembehelyezési folyamat létrehozása* párbeszédpanelen adja meg a folyamat nevét és leírását, majd kattintson a **Létrehozás** parancsra.

Miután létrejött a folyamat, megoszthatja azt más felhasználókkal, vagy törölheti. Amikor megoszt egy folyamatot másokkal, a megosztásra kijelölt felhasználók [hozzáférést kapnak a folyamathoz](deployment-pipelines-process.md#user-with-pipeline-access). A folyamat-hozzáférés lehetővé teszi a felhasználók számára a folyamat megtekintését, megosztását, szerkesztését és törlését.

## <a name="step-2---assign-a-workspace-to-a-deployment-pipeline"></a>2\. lépés – Munkaterület hozzárendelése üzembehelyezési folyamathoz

Egy folyamat létrehozása után hozzá kell adnia a kezelni kívánt tartalmat. A folyamathoz a munkaterületek adott folyamatszakaszhoz való hozzárendelésével adhat hozzá tartalmakat. Bármelyik szakaszhoz rendelhet munkaterületet. 

Egy üzembehelyezési folyamathoz egy munkaterületet rendelhet hozzá. Az üzembehelyezési folyamatok a munkaterület tartalmának klónjait hozzák létre, amelyek felhasználhatók a folyamat különböző szakaszaiban.

Az üzembehelyezési folyamatokban az alábbi lépések végrehajtásával vehet fel munkaterületet:

1. Az újonnan létrehozott üzembehelyezési folyamatban kattintson a **Munkaterület hozzárendelése** parancsra.

2. A *Munkaterület kiválasztása* legördülő menüben válassza ki azt a munkaterületet, amelyet hozzá szeretne rendelni a folyamathoz.

3. Válassza ki azt a szakaszt, amelyhez hozzá szeretné rendelni a munkaterületet.

### <a name="workspace-assignment-limitations"></a>A munkaterületek hozzárendelésére vonatkozó korlátozások

* A munkaterületnek [új munkaterületi felületnek](../collaborate-share/service-create-the-new-workspaces.md) kell lennie.

* Önnek a munkaterület rendszergazdájának kell lennie.

* A munkaterület nincs hozzárendelve egy másik folyamathoz.

* A munkaterületnek  [prémium szintű kapacitáson](../admin/service-premium-what-is.md) kell lennie.

* A [Power BI-mintákkal](../create-reports/sample-datasets.md) rendelkező munkaterületek nem rendelhetők hozzá a munkaterület-szakaszokhoz.

>[!NOTE]
>Csak azok a munkaterületek jelennek meg a választható munkaterületek listájában, amelyek használhatók az üzembehelyezési folyamatokban.

## <a name="step-3---deploy-to-an-empty-stage"></a>3\. lépés – Üres szakaszban történő üzembe helyezés

Bármely [Pro-felhasználó](../admin/service-admin-purchasing-power-bi-pro.md), aki tag vagy rendszergazda a forrás munkaterületén, üzembe helyezhet tartalmakat egy üres szakaszban (olyan szakaszban, amelynek nincs tartalma). A munkaterületnek egy kapacitáson kell elhelyezkednie, hogy az üzembe helyezést végre lehessen hajtani.

Ha üres szakaszban helyezi üzembe a tartalmat, az elemek közötti kapcsolatok megmaradnak. A forrásszakaszban található adathalmazhoz kapcsolódó jelentés például az adathalmazával együtt klónozva lesz, és a klónok hasonlóképpen fognak egymáshoz kapcsolódni a célmunkaterületen.

Az üzembe helyezés befejezése után frissítse az adathalmazt. További információkért lásd a [tartalom üres szakaszban történő üzembe helyezését](deployment-pipelines-process.md#deploying-content-to-an-empty-stage) ismertető szakaszt.

### <a name="deploying-all-content"></a>Minden tartalom üzembe helyezése

Válassza ki az üzembe helyezés forrásszakaszát, majd kattintson az üzembe helyezés parancsra. Az üzembehelyezési folyamat a munkaterület másolatát hozza létre a célszakaszban. Ez a munkaterület tartalmazza az aktuális szakaszban található összes tartalmat.

[![](media/deployment-pipelines-get-started/deploy.png "Deploy all content")](media/deployment-pipelines-get-started/deploy.png#lightbox)

### <a name="selective-deployment"></a>Szelektív üzembe helyezés

Csak meghatározott elemek üzembe helyezéséhez kattintson a **Továbbiak megjelenítése** hivatkozásra, és válassza ki az üzembe helyezni kívánt elemeket. Az üzembe helyezés gombra kattintva a rendszer csak a kiválasztott elemeket helyezi üzembe a következő szakaszban.

Mivel az irányítópultok, jelentések és adathalmazok kapcsolatban állnak egymással, és függőségekkel rendelkeznek, a kapcsolódók kijelölésére szolgáló gomb használatával megtekintheti az adott elemtől függő összes elemet. Ha például egy jelentést szeretne üzembe helyezni a következő szakaszban, a kapcsolódók kijelölésére szolgáló gombra kattintva megadhatja azt az adathalmazt, amelyhez a jelentés kapcsolódik, így mindkettő egyszerre lesz üzembe helyezve, és a jelentés rendeltetésszerűen lesz használható.

[![](media/deployment-pipelines-get-started/selective-deploy.png "Selective deployment")](media/deployment-pipelines-get-started/selective-deploy.png#lightbox)

>[!NOTE]
> * Nem helyezhet üzembe jelentést vagy irányítópultot a következő szakaszban, ha az annak függőségei tárgyát képező elemek nem léteznek az üzembe helyezés célszakaszában.
> * Ha egy jelentést vagy irányítópultot az adathalmaza nélkül helyez üzembe, előfordulhat, hogy nem várt eredményt kap. Ez akkor fordulhat elő, ha a célszakaszban lévő adathalmaz módosult, és már nem azonos az üzembe helyezés forrásszakaszában szereplővel.

### <a name="backwards-deployment"></a>Visszamenőleges üzembe helyezés

Dönthet úgy is, hogy egy korábbi szakaszban helyez üzembe tartalmakat, például olyan esetben, amikor egy meglévő munkaterületet egy éles szakaszhoz rendel hozzá, majd visszamenőlegesen helyezi üzembe, először a tesztelési, majd a fejlesztési szakaszban.

Az előző szakaszban való üzembe helyezés csak akkor működik, ha az előző szakasz nem rendelkezik tartalommal. Az előző szakaszban való üzembe helyezéskor nem választhat ki adott elemeket. A szakasz összes tartalma üzembe lesz helyezve.

[![](media/deployment-pipelines-get-started/deploy-back.png "Backwards deployment")](media/deployment-pipelines-get-started/deploy-back.png#lightbox)

## <a name="step-4---create-dataset-rules"></a>4\. lépés – Adathalmazszabályok létrehozása

Az üzembehelyezési folyamatban végzett munka során a különböző szakaszok különbözőképpen konfigurálhatók. Például minden szakasz rendelkezhet különböző adatbázisokkal vagy különböző lekérdezési paraméterekkel. A fejlesztési szakasz mintaadatokat kérdezhet le az adatbázisból, míg a tesztelési és az éles szakasz a teljes adatbázist kérdezi le.

Amikor tartalmat helyez üzembe a folyamat szakaszai között, az adathalmazszabályok konfigurálása lehetővé teszi a tartalom módosításának engedélyezését, míg bizonyos beállítások módosítását megakadályozza.

Az adathalmazszabályok az adatforrásokra és a paraméterekre vonatkozóan vannak meghatározva az egyes adathalmazokban. Ezek határozzák meg az adatforrások vagy paraméterek értékeit az egyes adathalmazok esetében. Ha például azt szeretné, hogy egy éles szakasz adathalmaza egy termelési adatbázisra mutasson, megadhat egy erre vonatkozó szabályt. A szabályt az éles szakaszban kell meghatározni, a megfelelő adathalmaz alatt. A szabály meghatározása után a tesztszakaszból az éles szakaszba üzembe helyezett tartalmak öröklik az adatkészlet szabályaiban meghatározott értéket, és ez mindaddig érvényes marad, amíg a szabály változatlan és érvényes.

>[!NOTE]
> Az adathalmazszabályok csak akkor működnek, ha a forrás- és cél-adatforrás ugyanolyan típusú.

### <a name="create-a-dataset-rule"></a>Adathalmazszabály létrehozása

1. Kattintson az **Üzembehelyezési beállítások** gombra abban a folyamatszakaszban, amelyhez adathalmazszabályt kíván létrehozni.

    ![üzembehelyezési beállítások](media/deployment-pipelines-get-started/deployment-settings.png)

2. Az Üzembehelyezési beállítások panelen válassza ki azt az adathalmazt, amelyhez szabályt szeretne létrehozni.

    [![](media/deployment-pipelines-get-started/dataset-rules.png "Select a dataset")](media/deployment-pipelines-get-started/dataset-rules.png#lightbox)

3. Válassza ki a létrehozni kívánt szabály típusát, bontsa ki a listát, és kattintson a **Szabály hozzáadása** parancsra.

     [![](media/deployment-pipelines-get-started/add-rule.png "Add a rule")](media/deployment-pipelines-get-started/add-rule.png#lightbox)

### <a name="dataset-rule-types"></a>Adathalmazszabályok típusai

Kétféle szabályt hozhat létre:

* **Adatforrásszabályok** Az adatforráslista a forrás-folyamatszakasz adathalmazából lesz átvéve. Válasszon ki egy lecserélendő adatforrást az adatforrások listájából. A forrásszakasz egyik értékének lecserélés céljából történő kiválasztásához kövesse az alábbi módszerek egyikét:

    1. Válasszon a listáról.

    2. Kattintson az **Egyéb** elemre, és manuálisan adjon hozzá új adatforrást. Csak ugyanolyan típusú adatforrásra válthat.

* **Paraméterszabályok** Válasszon egy paramétert a listáról. Ekkor az aktuális érték jelenik meg. Az értéket szerkessze át arra az értékre, amelyet az egyes üzembe helyezések után életbe kíván léptetni.

### <a name="dataset-rule-limitations"></a>Adathalmazszabályokra vonatkozó korlátozások

* Adathalmazszabály létrehozásához az adathalmaz tulajdonosának kell lennie.

* A fejlesztési szakaszban nem hozhatók létre adathalmazszabályok.

* Egy elem eltávolításakor vagy törlésekor a hozzá tartozó szabályok is törlődnek. Ezek a szabályok nem állítható vissza.

* Ha az adatforrás vagy a szabályban meghatározott paraméterek módosulnak vagy törlődnek a forrásadathalmazból, akkor a szabály nem lesz érvényes, és az üzembe helyezés meghiúsul.

* Az adatforrásszabályok csak a következő adatforrásokhoz határozhatók meg:
    * Analysis Services
    * Azure SQL Server
    * Azure Analysis Services
    * OData-adatcsatorna
    * Oracle
    * SapHana
    * SharePoint
    * SQL Server
    * SQL Server Analysis Services (SSAS)
    * Teradata

    Más adatforrások esetében [az adatforrás paraméterek használatával történő konfigurálását](deployment-pipelines-best-practices.md#use-parameters-in-your-model) ajánljuk.

## <a name="step-5---deploy-content-from-one-stage-to-another"></a>5\. lépés – Tartalom az egyik szakaszból a másikba történő üzembe helyezése

Ha egy folyamatszakasz rendelkezik tartalommal, akkor üzembe helyezheti azt a következő szakaszban. A tartalmak egy másik szakaszban való üzembe helyezése általában a folyamatban történő egyes műveletek végrehajtása után történik. Ezek lehetnek például a fejlesztési módosítások végrehajtása a tartalmon a fejlesztési szakaszban, vagy a tartalom tesztelése a tesztelési szakaszban. A tartalom szakaszok közötti áthelyezésének jellemző munkafolyamata a fejlesztésiből a tesztelési szakaszba, majd a tesztelésiből az éles szakaszba történő áthelyezés. Erről az eljárásról a [tartalom egy meglévő munkaterületen történő üzembe helyezését](deployment-pipelines-process.md#deploy-content-to-an-existing-workspace) ismertető szakaszban tudhat meg többet.

A tartalom az üzembehelyezési folyamat következő szakaszában történő üzembe helyezéséhez kattintson az üzembe helyezés gombjára a szakasz alsó részén.

A tesztelési és az éles szakasz kártyáinak áttekintésekor a legutóbbi üzembehelyezési időt láthatja. Ez a tartalom az adott szakaszban történő legutóbbi üzembe helyezésének idejét mutatja.

Az üzembehelyezési idő akkor hasznos, ha egy szakasz utolsó frissítésének időpontját szeretné meghatározni. Akkor is hasznos lehet, ha nyomon szeretné követni a tesztelési és éles üzembe helyezések között eltelt időt.

## <a name="comparing-stages"></a>Szakaszok összehasonlítása

Ha két egymást követő szakasz tartalommal rendelkezik, a tartalmat a rendszer a tartalmi elemek metaadatai alapján hasonlítja össze. Ez az összehasonlítás nem tartalmazza a szakaszok közötti adatok és frissítési idő összehasonlítását.

 [![](media/deployment-pipelines-get-started/deployment-flow.png "Comparing stages")](media/deployment-pipelines-get-started/deployment-flow.png#lightbox)

Annak érdekében, hogy gyors vizuális betekintést nyerhessen a két egymást követő szakasz közötti különbségekbe, egy összehasonlítási jelzőikon jelenik meg közöttük. Az összehasonlítási jelző két állapottal rendelkezik:

* **Zöld jelző** – A két szakaszban lévő tartalmi elemek metaadatai azonosak.

* **Narancssárga jelző** – Akkor jelenik meg, ha az alábbi feltételek valamelyik teljesül:
    * A szakaszokban található egyes tartalmi elemek módosultak vagy frissültek (eltérő metaadatokkal rendelkeznek).
    * A szakaszok eltérő számú elemmel rendelkeznek.

Ha két egymást követő szakasz nem azonos, akkor egy **összehasonlítási** hivatkozás jelenik meg a narancssárga összehasonlítási ikon alatt. A hivatkozásra kattintva megnyithatja a tartalmi elemek listáját mindkét szakaszban, az Összehasonlítás nézetben. Az Összehasonlítás nézet segítségével követheti nyomon a változásokat vagy az elemek közötti különbségeket az egyes folyamatszakaszok között. A módosított elemek a következő címkék egyikét kapják:

* **Új** – Új elem a forrásszakaszban. Ez egy olyan elem, amely a célszakaszban nem szerepel. Az üzembe helyezés után ez az elem klónozva lesz a célszakaszba.

* **Különböző** – A forrás- és a célszakaszban egyaránt létező elem, amelynek valamelyik verziója módosult a legutóbbi üzembe helyezést követően. Az üzembe helyezést követően a forrásszakaszban lévő elem felülírja a célszakaszban lévő elemet, függetlenül attól, hogy hol történt a módosítás.

* **Hiányzó** – Ez a címke azt jelzi, hogy egy elem megtalálható a célszakaszban, de a forrásszakaszban nem.

    >[!NOTE]
    >Az üzembe helyezés nem érinti a *hiányzó* elemeket.

 [![](media/deployment-pipelines-get-started/compare.png "Compare view")](media/deployment-pipelines-get-started/compare.png#lightbox)

## <a name="overriding-content"></a>Tartalom felülírása

Ha a forrásszakaszban lévő tartalom módosítása után végez üzembe helyezést, a rendszer felülírja a célszakaszban módosított tartalmat. Az *üzembe helyezésre* való kattintás után egy figyelmeztetés jelenik meg a felülírandó elemek számával.

![lecserélt tartalommal kapcsolatos figyelmeztetés](media/deployment-pipelines-get-started/replaced-content.png)

[Az üzembehelyezési folyamat ismertetése](deployment-pipelines-process.md) című ismertetőből többet is megtudhat arról, [mely elemek lesznek átmásolva a következő szakaszba](deployment-pipelines-process.md#deployed-items), és mely elemek [nem lesznek átmásolva](deployment-pipelines-process.md#unsupported-items).

## <a name="next-steps"></a>Következő lépések

>[!div class="nextstepaction"]
>[Az üzembehelyezési folyamatok bemutatása](deployment-pipelines-overview.md)

>[!div class="nextstepaction"]
>[Az üzembehelyezési folyamatok feldolgozásának ismertetése](deployment-pipelines-process.md)

>[!div class="nextstepaction"]
>[Az üzembehelyezési folyamatok hibaelhárítása](deployment-pipelines-troubleshooting.md)

>[!div class="nextstepaction"]
>[Ajánlott eljárások az üzembehelyezési folyamatokhoz](deployment-pipelines-best-practices.md)
