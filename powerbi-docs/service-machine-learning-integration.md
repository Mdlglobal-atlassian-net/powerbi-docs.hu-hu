---
title: Az Azure Machine Learning integrálása a Power BI-jal (Előzetes verzió)
description: Tudnivalók az Azure Machine Learning a Power BI szolgáltatással történő használatáról
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/31/2019
ms.author: davidi
LocalizationGroup: conceptual
ms.openlocfilehash: 86fab3a760eb8bb12ed1955fd5bf357790090e0e
ms.sourcegitcommit: c539726c9c180e899a8a34443e3fda2b9848beb2
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66448335"
---
# <a name="azure-machine-learning-integration-in-power-bi-preview"></a>Az Azure Machine Learning integrálása a Power BI-jal (Előzetes verzió)

Számos szervezet használja a **Machine Learning** modelljeit hatékonyabb üzleti elemzések és előrejelzések készítéséhez. A modellekből kinyerhető információk (valamint ezek megjelenítése) a jelentésekben, irányítópultokban és egyéb elemzésekben segít az üzleti felhasználóknak értelmezni ezeket az adatokat.  A Power BI mostantól egérrel végezhető műveletekkel egyszerűen beépíthetővé teszi az Azure Machine Learning Service modelljeinek elemzéseit.

A funkció használatához egy adattudós egyszerűen hozzáférést biztosíthat az Azure ML-modellhez egy BI-elemzőnek az Azure Portalon.  Innentől kezdve a Power Query minden munkamenet elején felismeri azokat az Azure ML-modelleket, amelyekhez a felhasználó hozzáfér, és dinamikus Power Query-függvényként jeleníti meg őket.  A felhasználó ezután meghívhatja ezeket a függvényeket a Power Query-szerkesztő menüszalagjáról vagy közvetlenül az M függvénnyel. A Power BI a jobb teljesítmény érdekében automatikusan kötegeli a hozzáférési kéréseket, amikor meghívja az Azure ML-modellt egy sorkészlethez.

Ez a funkció jelenleg csak Power BI-adatfolyamokban, valamint a Power Query online, a Power BI-ban történő használatához támogatott.

További információ az adatfolyamokról: [Önkiszolgáló adat-előkészítés a Power BI-ban](service-dataflows-overview.md).

További információ az Azure Machine Learning szolgáltatásról:

- Áttekintés:  [Az Azure Machine Learning Service ismertetése](https://docs.microsoft.com/azure/machine-learning/service/overview-what-is-azure-ml)
- Rövid útmutatók és oktatóanyagok az Azure Machine Learning szolgáltatáshoz:  [Azure Machine Learning-dokumentáció](https://docs.microsoft.com/azure/machine-learning/)

## <a name="granting-access-to-the-azure-ml-model-to-a-power-bi-user"></a>Az Azure ML-modellhez való hozzáférés biztosítása egy Power BI-felhasználónak

Egy Azure ML-modell a Power BI-ból való eléréséhez a felhasználónak **olvasási** hozzáféréssel kell rendelkeznie az Azure-előfizetésben.  Továbbá:

- Machine Learning Studio-modellek esetén **olvasási** hozzáférés a Machine Learning Studio webszolgáltatáshoz
- Machine Learning Service-modellek esetén **olvasási** hozzáférés a Machine Learning Service-munkaterülethez

A cikk lépései ismertetik, hogyan adhat hozzáférést egy Power BI-felhasználónak egy Azure Machine Learning Service-modellhez, hogy azt Power Query-függvényként használhassa.  További részletekért tekintse meg a [Hozzáférés-kezelés az RBAC és az Azure Portal segítségével](https://docs.microsoft.com/azure/role-based-access-control/role-assignments-portal) című témakört.

1. Jelentkezzen be az [Azure Portalra](https://portal.azure.com).

2. Lépjen az **Előfizetések** oldalra. Az **Előfizetések** oldalt az Azure Portal bal oldali navigációs menüjének **Minden szolgáltatás** listájában találhatja.

    ![Azure-előfizetések lap](media/service-machine-learning-integration/machine-learning-integration_01.png)

3. Válassza ki az előfizetését.

    ![Az előfizetés kiválasztása](media/service-machine-learning-integration/machine-learning-integration_02.png)

4. Válassza a **Hozzáférés-vezérlés (IAM)**, majd a **Hozzáadás** lehetőséget.

    ![Hozzáférés-vezérlés AIM](media/service-machine-learning-integration/machine-learning-integration_03.png)

5. Szerepkörként válassza az **Olvasó** lehetőséget. Válassza ki azt a Power BI-felhasználót, akinek hozzáférést szeretne adni az Azure ML-modellhez.

    ![Olvasó kiválasztása](media/service-machine-learning-integration/machine-learning-integration_04.png)

6. Kattintson a **Mentés** gombra.

7. Ismételje meg a 3–6. lépést, így **Olvasó** hozzáférést adhat a felhasználónak az adott Machine Learning Studio webszolgáltatáshoz *vagy* a modellt tartalmazó Machine Learning Service-munkaterülethez.


## <a name="schema-discovery-for-machine-learning-service-models"></a>Machine Learning Service-modellek sémafeltárása

Az adattudósok elsősorban Pythont használnak a Machine Learning Service gépi tanulási modelljeinek fejlesztéséhez és üzembe helyezéséhez.  A Machine Learning Studióval ellentétben (amely automatizálja a modell sémafájljainak létrehozását) a Machine Learning Service esetén az adattudósnak explicit módon létre kell hoznia a sémafájlt a Pythonnal.

Ezt a sémafájlt bele kell foglalni a Machine Learning szolgáltatáshoz üzembe helyezett webszolgáltatásba. Ahhoz, hogy a séma automatikusan generálva legyen a webszolgáltatásban, meg kell adnia a bemenet/kimenet mintáját az üzembe helyezett modell belépési szkriptjében. Olvassa el a Modellek üzembe helyezése az Azure Machine Learning szolgáltatással című dokumentáció (Választható) Automatikus Swagger-séma generálása című fejezetét. A hivatkozás egy példát is tartalmaz a belépési szkriptre a sémageneráló utasításokkal. 

A belépési szkript *@input_schema* és *@output_schema* függvénye az *input_sample* és az *output_sample* változóban hivatkozik a bemeneti és kimeneti mintaformátumokra, és ezeket a mintákat használja a webszolgáltatás egy OpenAPI- (Swagger-) specifikációjának generálására az üzembe helyezés során.

A belépési szkript módosításakor ezeket a sémagenerálási utasításokat kell alkalmazni az Azure Machine Learning SDK-val végzett automatizált gépi tanulási kísérletek használatával létrehozott modellekre is.

> [!NOTE]
> Az Azure Machine Learning szolgáltatás vizuális interfészének (előzetes verzió) használatával létrehozott modellek jelenleg nem támogatják a sémagenerálást, de a későbbi kiadásokban már fogják. 

## <a name="invoking-the-azure-ml-model-in-power-bi"></a>Az Azure ML-modell meghívása a Power BI-ban

A Power Query-szerkesztőben közvetlenül meghívhat minden olyan Azure ML-modellt, amelyhez hozzáféréssel rendelkezik. Az Azure ML-modellek eléréséhez válassza a **Szerkesztés** gombot azon entitáshoz, amelyet az Azure ML-modell elemzéseivel szeretne bővíteni.

![Power BI szolgáltatás – az entitás szerkesztése](media/service-machine-learning-integration/machine-learning-integration_05.png)

A **Szerkesztés** gombbal megnyithatja a Power Query-szerkesztőt az adatfolyam entitásaihoz.

![Power Query-szerkesztő](media/service-machine-learning-integration/machine-learning-integration_06.png)

Válassza a menüszalag **AI-elemzések** gombját, majd a bal oldali navigációs menü _Azure Machine Learning-modellek_ elemét. Itt Power Query-függvényként láthat minden olyan Azure ML-modellt, amelyhez hozzáférhet. Az Azure ML-modell bemeneti paraméterei automatikusan le vannak képezve a megfelelő Power Query-függvény paramétereiként.

Az Azure ML-modell meghívásához bemenetként a kijelölt entitás bármelyik oszlopát megadhatja. Emellett megadhat egy állandó értéket is, amelyet bemenetként használhat. Ehhez a bemeneti párbeszédpanelen be kell kapcsolnia az oszlop ikont.

![oszlop kiválasztása](media/service-machine-learning-integration/machine-learning-integration_07.png)

A **Meghívás** lehetőséggel megtekintheti az Azure ML-modell kimenetét új oszlopként az entitástáblában. Láthatja, hogy a modell meghívása a lekérdezés lépéseként is megjelenik.

![Meghívás](media/service-machine-learning-integration/machine-learning-integration_08.png)

Ha a modell több kimeneti paramétert eredményez, azok egy rekordként lesznek csoportosítva a kimeneti oszlopban. Az oszlop kibontásával több egyéni kimeneti paramétert kaphat különálló oszlopokban.

![oszlop kibontása](media/service-machine-learning-integration/machine-learning-integration_09.png)

Az adatfolyam mentése után a rendszer az entitástábla minden új vagy frissített sora esetén automatikusan meghívja a modellt, amikor az adatfolyam frissül.

## <a name="next-steps"></a>Következő lépések

Ez a cikk áttekintést nyújtott a Machine Learning a Power BI szolgáltatásba való integrálásáról. Az alábbi cikkeket is érdekesnek találhatja. 

* [Oktatóanyag: Machine Learning Studio-modell meghívása a Power BI-ban (előzetes verzió)](service-tutorial-invoke-machine-learning-model.md)
* [Oktatóanyag: A Cognitive Services használata a Power BI-ban](service-tutorial-use-cognitive-services.md)
* [A Cognitive Services a Power BI-ban (Előzetes verzió)](service-cognitive-services.md)

Az adatfolyamokkal szolgáltatással kapcsolatban az alábbi cikkeket érdemes elolvasni:
* [Adatfolyamok létrehozása és használata a Power BI-ban](service-dataflows-create-use.md)
* [Számított entitások használata a Power BI Premiumban](service-dataflows-computed-entities-premium.md)
* [Adatfolyamok használata helyszíni adatforrásokkal](service-dataflows-on-premises-gateways.md)
* [Fejlesztői erőforrások Power BI-adatfolyamokhoz](service-dataflows-developer-resources.md)
* [Adatfolyamok és az Azure Data Lake integrációja (előzetes verzió)](service-dataflows-azure-data-lake-integration.md)


