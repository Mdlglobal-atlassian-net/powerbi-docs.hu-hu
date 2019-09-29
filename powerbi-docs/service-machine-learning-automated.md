---
title: Automatizált Machine Learning a Power BI-ban (előzetes verzió)
description: 'Útmutató: Automatizált Machine Learning (AutoML) funkció használata a Power BI-ban'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/02/2019
ms.author: davidi
LocalizationGroup: conceptual
ms.openlocfilehash: 894e92687a6283ce71b253bd4dc635aca0c4673f
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61236450"
---
# <a name="automated-machine-learning-in-power-bi-preview"></a>Automatizált Machine Learning a Power BI-ban (előzetes verzió)

Az adatfolyamokhoz készült Automatizált Machine Learning (AutoML) funkció közvetlenül a Power BI-ban teszi lehetővé az üzleti elemzők számára a Machine Learning-modellek betanítását, ellenőrzését és meghívását. Tartalmazza egy új ML-modell egyszerű létrehozását, amelyben az elemzők saját adatfolyamaik használatával határozhatják meg a modell betanításához szükséges bemeneti adatokat. A szolgáltatás automatikusan kinyeri a legfontosabb jellemzőket, kiválaszt egy megfelelő algoritmust, majd finomhangolja és ellenőrzi az ML-modellt. A modell betanítása után a Power BI automatikusan létrehoz egy jelentést az ellenőrzött eredményekről, amely elmagyarázza az elemzőknek a teljesítményt és az eredményeket. Ezt követően a modell az adatfolyamon belül bármely új vagy frissített adattal meghívható.

![Machine Learning-képernyő](media/service-machine-learning-automated/automated-machine-learning-power-bi-01.png)

Az automatizált gépi tanulás funkció csak a Power BI Premium és Embedded kapacitásokon üzemeltetett adatfolyamok számára érhető el. Ebben az előzetes verzióban bináris előrejelzési, besorolási és regressziós modellekhez taníthatja be a gépi tanulási modelleket az AutoML segítségével.

## <a name="working-with-automl"></a>Az AutoML használata

A [Power BI adatfolyamok](service-dataflows-overview.md) lehetővé teszik a big data típusú adatok önkiszolgáló adat-előkészítését. Az AutoML közvetlenül a Power BI-ban segíti a hatékonyabb adat-előkészítési munkát a gépi tanulási modellek létrehozásához.

A Power BI-ban működő AutoML és az adatfolyamok használatával az adatelemzők egyszerűbben, és csupán a Power BI képességei révén építhetnek gépi tanulási modelleket. Az ML-modellek létrehozását támogató adatelemzés legnagyobb részét a Power BI automatizálja olyan biztonsági korlátokkal, amelyek szavatolják a létrehozott modell jó minőségét és átláthatóságát, így teljes betekintést nyújtanak az ML-modell létrehozását szolgáló folyamatokba.

Az AutoML az adatfolyamok **bináris előrejelzési**, **besorolási** és **regressziós** modelljeit támogatja. Ezek a felügyelt gépi tanulási modellek típusai, ami azt jelenti, hogy a korábbi megfigyelések eredményeinek betanulása révén jelzik előre más megfigyelések eredményeit. Az AutoML-modell betanítására szolgáló bemeneti adatkészlet az ismert eredményekkel **címkézett** rekordhalmaz.

A Power BI-beli AutoML az [Azure Machine Learning szolgáltatásból](https://docs.microsoft.com/azure/machine-learning/service/overview-what-is-azure-ml) integrálja az [automatizált gépi tanulást](https://docs.microsoft.com/azure/machine-learning/service/concept-automated-ml) az ML-modellek létrehozásához. Ennek ellenére az AutoML Power BI-beli használatához nincs szükség Azure-előfizetésre. Az ML-modellek betanításának és üzemeltetésének teljes folyamatát a Power BI szolgáltatás kezeli.

Egy ML-modell betanítása után az AutoML automatikusan létrehoz egy Power BI-jelentést, amely ismerteti az ML-modell valószínű teljesítményét. Az AutoML az áttekinthetőség érdekében kiemelten tünteti fel a bemeneti adatok között a modell előrejelzéseire legnagyobb hatást gyakorló tényezőket. A jelentés az ML-modell típusától függően a modellhez tartozó fő mérőszámokat is tartalmazza.

A létrehozott jelentés más lapjain a modell statisztikai összegzése és a betanítási adatok láthatók. A statisztikai összegzés azon felhasználók számára fontos, akik látni szeretnék a modell teljesítményének szabványos adatelemzési mértékeit. A betanítási adatok összegzik a modell létrehozásához futtatott összes iterációt a kapcsolódó modellezési paraméterekkel együtt. Azt is leírja, hogy az ML-modell hogy használta fel az egyes bemeneteket.

Ezután alkalmazhatja az ML-modellt az adatok pontozásához. Az adatfolyamat frissítésekor a rendszer automatikusan alkalmazza az adatokra az ML-modell előrejelzéseit. A Power BI külön ismertetést nyújt az ML-modell által előállított minden egyes előrejelzési pontszámhoz.

## <a name="creating-a-machine-learning-model"></a>Gépi tanulási modell létrehozása

Ez a szakasz az AutoML tanulási modell létrehozását ismerteti. 

### <a name="data-prep-for-creating-an-ml-model"></a>Adat-előkészítés az ML-modell létrehozásához

Ha gépi tanulási modellt kíván létrehozni a Power BI-ban, először egy adatfolyamot kell létrehoznia az előzményalapú eredményekre vonatkozó információkból az ML-modell betanításához. Az adatfolyam konfigurálásához lásd: [Önkiszolgáló adat-előkészítés a Power BI-ban](service-dataflows-overview.md).

A Power BI jelenlegi kiadása csak egyetlen entitás adatait használja az ML-modell betanításához. Ezért ha az előzményalapú adatok több entitásból állnak, manuálisan kell összekötnie az adatokat, hogy egyetlen adatfolyam-entitást kapjon. Ezenkívül számított oszlopokat is fel kell vennie minden olyan üzleti metrikához, amely az előrejelezni kívánt eredmény erős előrejelzője lehet.

Az AutoML konkrét adatkövetelményeket ad meg a gépi tanulási modell betanításához. Ezeket a követelményeket az alábbi szakaszok ismertetik az egyes modellek szerint.

### <a name="configuring-the-ml-model-inputs"></a>Az ML-modellek bemeneteinek konfigurálása

AutoML-modell létrehozásához válassza az előzményadatokat tartalmazó adatfolyam-entitás **Műveletek** oszlopában található ML ikont, majd válassza a **Machine Learning-modell**hozzáadása lehetőséget.

![Gépi tanulási modell felvétele](media/service-machine-learning-automated/automated-machine-learning-power-bi-02.png)

Ekkor elindul az ML-modell létrehozásának egyszerű folyamata, amelyen egy varázsló vezeti végig. A varázsló a következő egyszerű lépéseket tartalmazza.

1. Az előzményalapú eredményadat-entitás és az előrejelezni kívánt mező kiválasztása
2. A modell kiválasztása az előrejelzés típusa alapján
3. Azon bemenetek kiválasztása, amelyeket a modell előrejelzési jelként használhat
4. A modell elnevezése és a konfiguráció mentése

Az előzményalapú eredmények mezője azonosítja az ML-modell betanításának címkeattribútumát az alábbi kép szerint.

![Előzményalapú eredményadatok kiválasztása](media/service-machine-learning-automated/automated-machine-learning-power-bi-03.png)

Az előzményalapú eredmények mezőjének megadásakor az AutoML elemzi a címke adatait az adatokhoz betanítható ML-modellek meghatározásához, és javaslatot tesz a legvalószínűbben betanítható ML-modellre. 

> [!NOTE]
> Előfordulhat, hogy egyes modellek nem támogatottak a kiválasztott adatokhoz.

Az AutoML elemzi a kiválasztott entitás minden egyes mezőjét, hogy javaslatot tehessen az ML-modell betanításához használható bemenetekre. Ez egy statisztikai elemzéseken alapuló hozzávetőleges folyamat, ezért tekintse át a felhasznált bemeneteket. Az előzményalapú eredmény (vagy címke) mezőjétől függő bemenetek nem használhatók az ML-modell betanítására, mert hatással lennének a teljesítményére.

![Beviteli mezők testreszabása](media/service-machine-learning-automated/automated-machine-learning-power-bi-04.png)

Az utolsó lépésben nevet adhat a modellnek, és mentheti a beállításait.

Ekkor a rendszer felszólítja az adatfolyam frissítésére, és ezzel kezdetét veszi az ML-modell betanítása.

### <a name="ml-model-training"></a>Az ML-modell betanítása

Az ML-modellek betanítása az adatfolyamok frissítésének része. Az első lépésben az AutoML előkészíti az adatokat a betanításra.

Az AutoML az előzményadatokat betanítási és tesztelési adathalmazra osztja. A tesztelési adathalmaz egy validációs adatkészlet, amellyel a betanítás után ellenőrizhető a modell teljesítménye. Az adathalmazok **Betanítási és Tesztelési** entitásként szerepelnek az adatfolyamban. Az AutoML keresztvalidálást alkalmaz a modell ellenőrzéséhez.

Ezután a rendszer minden beviteli mezőt ellenőriz, és imputálás révén minden hiányzó értéket egy helyettesített értékkel vált fel. Az AutoML több különböző imputálási stratégiát használ. Ezt követően a modell alkalmazza az adatokra az összes szükséges mintavételezést és normalizálást.

Az AutoML számos átalakítást használ, amelyek az adattípus beviteli mezője és statisztikai tulajdonságai alapján lettek kiválasztva. Az AutoML ezeket az átalakításokat az ML-modell betanítása során igénybe vehető funkciók kinyeréséhez használja fel.

Az AutoML-modellek betanítási folyamata a legjobb teljesítményű modell létrehozása érdekében akár 50 iterációt is tartalmazhat különböző modellezési algoritmusokkal és hiperparaméter-beállításokkal. Az egyes modellek teljesítményét a validációs tesztadatkészlettel történő értékelés ellenőrzi. Ebben a betanítási lépésben az AutoML számos folyamatot hoz létre az iterációk betanításához és ellenőrzéséhez. A modellek teljesítményének értékelése hosszabb időt vehet igénybe, amely néhány perctől több óráig terjedhet az adatkészlet méretétől és az elérhető dedikált kapacitási erőforrásoktól függően.

Bizonyos esetekben az előállított végső modell az együttes tanulás módszerét is felhasználhatja, amely több modellt vesz igénybe a jobb előrejelzési teljesítményhez.

### <a name="automl-model-explainability"></a>Az AutoML-modell áttekinthetősége

A modell betanítása után az AutoML elemzi a kapcsolatot a bemeneti funkciók és a modell kimenete között. Felméri a modell kimenetében bekövetkezett változás nagyságát és irányát minden bemeneti funkció validációs tesztadatkészletére. Ez a *funkció fontossága*.

![A funkció fontossága](media/service-machine-learning-automated/automated-machine-learning-power-bi-05.png)

### <a name="automl-model-report"></a>AutoML modell-jelentés

Az AutoML létrehoz egy Power BI-jelentést, amely összegzi a modell validáció során nyújtott teljesítményét, valamit a globális funkciófontosságot. A jelentés összefoglalja az ML-modell validációs tesztadatokra alkalmazásának eredményeit és összeveti az előrejelzéseket az ismert kimeneti értékekkel.

A modellhez tartozó jelentés áttekintésével megértheti annak teljesítményét. Azt is ellenőrizheti, hogy a modell fő befolyásolói megfelelnek-e az ismert eredményekre vonatkozó üzleti információknak.

A jelentésben a modell teljesítményének leírásához használt diagramok és mértékek a modell típusától függenek. A teljesítménydiagramokat és -mértékeket a következő szakaszok mutatják be.

A jelentés egyéb oldalai adatelemzési szempontból írhatnak le statisztikai mértékeket a modellről. A **bináris előrejelzéshez** tartozó jelentés például tartalmaz egy nyereségi diagramot és a modell ROC-görbéjét.

A jelentésekhez egy **Betanítási adatok** oldal is tartozik, amely leírja a modell betanításának módját, és grafikonon ábrázolja a modell teljesítményét minden egyes iteráció futtatásakor.

![Tanulás részletei](media/service-machine-learning-automated/automated-machine-learning-power-bi-06.png)

Az oldal egy másik szakasza a bemeneti értékek hiányzó értékeinek pótlására szolgáló imputálási módszert írja le, valamint azt, hogy miképpen történt az egyes bemeneti mezők átalakítása a modellben használt jellemzők kinyeréséhez. Tartalmazza a végső modell által használt paramétereket is.

![További információk a modellhez](media/service-machine-learning-automated/automated-machine-learning-power-bi-07.png)

Ha a modell az együttes tanulás módszerét használta, akkor a **Betanítási adatok** oldal egy szakasza leírja az együttest alkotó minden egyes modell súlyozását és paramétereit.

![Súlyozás az együttesen belül](media/service-machine-learning-automated/automated-machine-learning-power-bi-08.png)

## <a name="applying-the-automl-model"></a>Az AutoML-modell alkalmazása

Ha elégedett a létrehozott ML-modell teljesítményével, akkor az adatfolyam minden frissülésekor alkalmazhatja új vagy frissített adatokra. Ezt a modellhez tartozó jelentésből is kezdeményezheti, ha a jobb felső sarokban lévő **Alkalmaz** gombra kattint.

Az ML-modell alkalmazásához meg kell adnia annak az entitásnak a nevét, amelyre alkalmazni kívánja azt, és egy előtagot az entitáshoz hozzáadandó, a modell kimenetét jelző oszlopokhoz. Az oszlopnevek alapértelmezett előtagja a modell neve. Az *Alkalmazás* funkció a modell típusára jellemző további paramétereket is tartalmazhat.

Az ML-modell alkalmazása egy új adatfolyam-entitást hoz létre az **enriched <model_name>** utótaggal. Ha például a _PurchaseIntent_ modellt alkalmazza az _OnlineShoppers_ entitásra, a kimenet az **OnlineShoppers enriched PurchaseIntent** entitást hozza létre.

Jelenleg a kimeneti entitás nem használható az ML-modell eredményeinek Power Query-szerkesztőben való megtekintéséhez. A kimeneti oszlopok eredménye mindig null. Az eredmények megtekintéséhez a modell alkalmazásakor egy második kimeneti entitás is létrejön **enriched <model_name> Preview** utótaggal.

Frissítse az adatfolyamot, hogy az eredményeket megtekinthesse a Lekérdezésszerkesztőben.

![Lekérdezésszerkesztő](media/service-machine-learning-automated/automated-machine-learning-power-bi-09.png)

A modell alkalmazásakor az AutoML mindig naprakészen tartja az előrejelzéseket, ha az adatfolyam frissül.

Az AutoML külön magyarázatot tartalmaz minden sorra, amelyet a kimeneti entitásban pontoz.

Ha Power BI-jelentésben szeretné felhasználni az ML-modell elemzéseit és előrejelzéseit, akkor a Power BI Desktopból kapcsolódhat a kimeneti entitáshoz az **adatfolyamok**-összekötő használatával.

## <a name="binary-prediction-models"></a>Bináris előrejelzési modellek

A bináris előrejelzési modellek, vagy hivatalos nevükön a **bináris besorolási modellek** egy adathalmaz két csoportba sorolására szolgálnak. Olyan eseményeket jeleznek előre, amelyeknek kétféle kimenetelük lehet, például hogy konvertálódik-e egy értékesítési lehetőség, megszűnik-e egy felhasználói fiók, időben befizetnek-e egy számlát, megtévesztő-e egy tranzakció stb.

Mivel bináris az eredmény, a Power BI logikai címkét vár el a bináris előrejelzési modelltől, az érték tehát vagy **igaz**, vagy **hamis** lehet. Egy értékesítési konverziós modellben például a sikeresen megvalósult lehetőségek igaz címkét, a meghiúsult lehetőségek hamis címkét, a nyitott lehetőségek null címkét kapnak.

A bináris előrejelzési modell kimenete egy valószínűségi pontszám, amely annak a valószínűségét jelzi, hogy megvalósul-e a címke igaz értékének megfelelő eredmény.

### <a name="training-a-binary-prediction-model"></a>A bináris előrejelzési modell betanítása

Bináris előrejelzési modell létrehozásához a betanítási adatokat tartalmazó bemeneti entitásnak tartalmaznia kell egy logikai mezőt, amely az előzményalapú eredmények mezője, és a korábbi ismert eredményeket határozza meg.

Előfeltételek:

* Az előzményalapú eredmény mezőjeként logikai mezőt kell használni
* Minden eredményosztályhoz legalább 50 sor előzményalapú adatra van szükség

Általában ha a korábbi eredményeket egy másik adattípus mezői határozzák meg, felvehet egy számított oszlopot, amely a Power Query használatával logikai értékké alakítja őket.

A bináris előrejelzési modell létrehozási folyamata ugyanazokat a lépéseket követi, mint a többi AutoML-modellé, ahogy azt **Az ML-modellek bemeneteinek konfigurálása** című, fentebb olvasható szakasz ismerteti.

### <a name="binary-prediction-model-report"></a>A bináris előrejelzési modellhez tartozó jelentés

A bináris előrejelzési modell kimenete annak a valószínűsége, hogy a rekord megvalósítja-e a logikai címke által meghatározott Igaz értéket. A jelentéshez tartozik egy szeletelő a valószínűségi küszöbérték meghatározásához, amely hatással van a küszöb feletti és alatti pontszámok értékelésére.

A jelentés az *Igaz pozitív*, *Hamis pozitív*, *Igaz negatív* és *Hamis negatív* kifejezésekkel mutatja be a modell teljesítményét. Az Igaz pozitív és az Igaz negatív értékek a két osztály pontosan előrejelzett eredményeit jelölik az eredményadatokban. A Hamis pozitív értékek olyan eredmények, amelyek az előrejelzés szerint Igazak voltak, de végül mégis a Hamis logikai címkét kapták. A Hamis negatív értékeknél az ellenkezője történt: az előrejelzés Hamis volt, de az eredmény tényleges logikai címkéje Igaz.

A mértékek, például a Pontosság és a Visszahívás, a valószínűségi küszöb előrejelzett eredményekre gyakorolt hatását írják le. A valószínűségi szeletelő használatával olyan küszöböt választhat, amely kiegyensúlyozott kompromisszumot jelent a Pontosság és a Visszahívás között.

![Pontossági előnézet](media/service-machine-learning-automated/automated-machine-learning-power-bi-10.png)

A modellhez tartozó jelentés **Pontossági jelentés** oldala tartalmaz egy *Összesített nyereségek* diagramot és a modell ROC-görbéjét. Ezek a modell teljesítményének statisztikai mértékei. A jelentésekben megtalálható a feltüntetett diagramok leírása.

![A pontossági előnézet képernyője](media/service-machine-learning-automated/automated-machine-learning-power-bi-11.png)

### <a name="applying-a-binary-prediction-model"></a>A bináris előrejelzési modell alkalmazása

A bináris előrejelzési modell használatához meg kell adnia azt az entitást, amelynek adataira alkalmazni szeretné az ML-modell előrejelzéseit. További paraméter például a kimeneti oszlop nevének előtagja és az előrejelzett eredmény besorolásához használt valószínűségi küszöb.

![Előrejelzési bemenetek](media/service-machine-learning-automated/automated-machine-learning-power-bi-12.png)

A bináris előrejelzési modell alkalmazásakor a modell három kimeneti oszlopot ad hozzá a kiegészített kimeneti entitáshoz. Ezek a következők: **PredictionScore**, **PredictionOutcome** és **PredictionExplanation**. Az entitásban szereplő oszlopnevek előtagja a modell alkalmazásakor jön létre.

A **PredictionOutcome** oszlop tartalmazza az előrejelzett eredmény címkéjét. A küszöb feletti valószínűségű rekordok valószínűleg elérik a várt eredményt, a küszöb alatti rekordok valószínűleg nem érik el azt.

A **PredictionExplanation** oszlop annak a magyarázatát tartalmazza, hogy a bemeneti funkciók milyen konkrét hatást gyakoroltak a **PredictionScore** oszlopra. Ez az előrejelzéshez felhasznált súlyozások és bemeneti funkciók JSON-formázású gyűjteménye.

## <a name="classification-models"></a>Besorolási modellek

A besorolási modellek egy adatkészlet több csoportba vagy osztályba sorolására szolgálnak.  Olyan események előrejelzésére használhatók, ahol több lehetőség közül egy eredmény valósulhat meg, például egy vásárló élettartam-értéke nagyon magas, magas, közepes, vagy alacsony lehet; az alapértelmezett kockázat magas, mérsékelt, alacsony, vagy nagyon alacsony lehet, stb.

A besorolási modell kimenete egy valószínűségi pontszám, amely annak a valószínűségét határozza meg, hogy egy rekord megvalósítja-e egy adott osztály feltételeit.

### <a name="training-a-classification-model"></a>A besorolási modell betanítása

A besorolási modell betanítási adatait tartalmazó bemeneti entitásnak tartalmaznia kell egy karakterláncot vagy egy numerikus mezőt, amely az előzményalapú eredmények mezője, és a korábbi ismert eredményeket határozza meg.

Előfeltételek:

* Minden eredményosztályhoz legalább 50 sor előzményalapú adatra van szükség

A besorolási modell létrehozási folyamata ugyanazokat a lépéseket követi, mint a többi AutoML-modellé, ahogy **Az ML-modellek bemenetének konfigurálása** című, fentebb olvasható szakasz ismerteti.

### <a name="classification-model-report"></a>A besorolási modellhez tartozó jelentés

A besorolási modellhez tartozó jelentés létrehozásához a rendszer a validációs tesztadatokra alkalmazza az ML-modellt, és összehasonlítja a rekord előrejelzett osztályát a ténylegesen megismert osztállyal.

A jelentés egy diagramot tartalmaz minden egyes ismert osztály pontosan és pontatlanul besorolt rekordjairól.

![A modellhez tartozó jelentés](media/service-machine-learning-automated/automated-machine-learning-power-bi-13.png)

Egy további osztályspecifikus részletezés lehetővé teszi annak elemzését, hogy egy ismert osztály előrejelzései miképpen oszlanak meg. Ebbe azok az osztályok is beletartoznak, ahol az ismert osztály rekordjainak besorolása valószínűleg helytelen.

![Elemzési jelentés](media/service-machine-learning-automated/automated-machine-learning-power-bi-14.png)

A jelentésben szereplő modell magyarázata az osztályok legfontosabb előrejelzőit is tartalmazza.

A besorolási modellhez tartozó jelentésben a többi modelltípushoz hasonlóan szerepel egy Betanítási adatok oldal, amelyet a feljebb olvasható **Az AutoML-modellhez tartozó jelentés** szakasz ismertet.

### <a name="applying-a-classification-model"></a>A besorolási modell alkalmazása

A besorolási ML-modell alkalmazásához meg kell adnia a bemeneti adatokat tartalmazó entitást és a kimeneti oszlop nevének előtagját.

A besorolási modell alkalmazásakor a modell három kimeneti oszlopot ad hozzá a kiegészített kimeneti entitáshoz. Ezek a következőek: **PredictionScore**, **PredictionClass** és **PredictionExplanation**. Az entitásban szereplő oszlopnevek előtagja a modell alkalmazásakor jön létre.

A **PredictionClass** oszlop a rekord legvalószínűbb előrejelzett osztályát tartalmazza. A **PredictionScore** oszlop a rekord valószínűségi pontszámainak listáját tartalmazza minden lehetséges osztályhoz.

A **PredictionExplanation** oszlop annak a magyarázatát tartalmazza, hogy a bemeneti funkciók milyen konkrét hatást gyakoroltak a **PredictionScore** oszlop értékeire. Ez az előrejelzéshez felhasznált súlyozások és bemeneti funkciók JSON-formázású gyűjteménye.

## <a name="regression-models"></a>Regressziós modellek

A regressziós modellek olyan értékek előrejelzésére szolgálnak, mint például egy értékesítési ügylet várható bevétele, egy előfizetői fiók élettartama, egy várhatóan beérkező kintlevőség értéke, egy számla lehetséges befizetésének dátuma stb.

A regressziós modell kimenete az előrejelzett érték.

### <a name="training-a-regression-model"></a>A regressziós modell betanítása

A regressziós modell betanítási adatait tartalmazó bemeneti entitásnak tartalmaznia kell egy numerikus mezőt, amely az előzményalapú eredmények mezője, és a korábbi ismert eredményeket határozza meg.

Előfeltételek:

* Regressziós modellhez legalább 100 sor előzményalapú adatra van szükség

A regressziós modell létrehozási folyamata ugyanazokat a lépéseket követi, mint a többi AutoML-modellé, ahogy az **ML-modellek bemenetének konfigurálása** című, fentebb olvasható szakasz ismerteti.

### <a name="regression-model-report"></a>A regressziós modellhez tartozó jelentés

Hasonlóan a többi AutoML-jelentéshez, a regressziós jelentés is a modell validációs tesztadatokra alkalmazásának eredményein alapul.

A modellhez tartozó jelentés egy grafikonon veti össze az előrejelzett értékeket a tényleges értékekkel. A grafikonon az átlós vonaltól való távolság jelzi az előrejelzés hibáit.

A maradványhiba-diagram a különböző értékek átlagos hibaeloszlását mutatja be százalékosan a validációs tesztadatkészletben. A vízszintes tengely a tényleges érték középértékét jelzi a csoportban, a buborékok mérete az értékek gyakoriságát vagy számát mutatja az adott tartományban. A függőleges tengely az átlagos maradványhiba.

![Maradványhiba-grafikon](media/service-machine-learning-automated/automated-machine-learning-power-bi-15.png)

A regressziós modellhez tartozó jelentésben a többi modelltípushoz hasonlóan szerepel egy Betanítási adatok oldal, ahogy **Az AutoML-modellhez tartozó jelentés** című szakasz ismerteti.

### <a name="applying-a-regression-model"></a>Regressziós modell alkalmazása

A regressziós ML-modell alkalmazásához meg kell adnia a bemeneti adatokat tartalmazó entitást és a kimeneti oszlop nevének előtagját.

![Regresszió alkalmazása](media/service-machine-learning-automated/automated-machine-learning-power-bi-16.png)

A regressziós modell alkalmazásakor a modell két kimeneti oszlopot ad hozzá a kiegészített kimeneti entitáshoz. Ezek a **PredictionValue** és a **PredictionExplanation** oszlopok. Az entitásban szereplő oszlopnevek előtagja a modell alkalmazásakor jön létre.

A **PredictionValue** oszlop a rekord előrejelzett értékét tartalmazza a bemeneti mezők alapján. A **PredictionExplanation** oszlop annak a magyarázatát tartalmazza, hogy a bemeneti funkciók milyen konkrét hatást gyakoroltak a **PredictionValue** oszlop értékeire. Ez a súlyozások és bemeneti funkciók JSON-formázású gyűjteménye.

## <a name="next-steps"></a>Következő lépések

Ez a cikk áttekintést nyújtott az adatfolyamokhoz készült Automatizált Machine Learning funkcióról a Power BI szolgáltatásban. A következő cikkek szintén hasznosak lehetnek.

* [Oktatóanyag: Machine Learning-modell létrehozása a Power BI-ban (előzetes verzió)](service-tutorial-build-machine-learning-model.md)
* [Oktatóanyag: A Cognitive Services használata a Power BI-ban](service-tutorial-use-cognitive-services.md)
* [Oktatóanyag: Machine Learning Studio-modell meghívása a Power BI-ban (előzetes verzió)](service-tutorial-invoke-machine-learning-model.md)
* [A Cognitive Services a Power BI-ban (Előzetes verzió)](service-cognitive-services.md)
* [Az Azure Machine Learning integrálása a Power BI-jal (Előzetes verzió)](service-machine-learning-integration.md)

Az adatfolyamokkal kapcsolatban az alábbi cikkeket érdemes elolvasni:
* [Adatfolyamok létrehozása és használata a Power BI-ban](service-dataflows-create-use.md)
* [Számított entitások használata a Power BI Premiumban](service-dataflows-computed-entities-premium.md)
* [Adatfolyamok használata helyszíni adatforrásokkal](service-dataflows-on-premises-gateways.md)
* [Fejlesztői erőforrások Power BI-adatfolyamokhoz](service-dataflows-developer-resources.md)
* [Adatfolyamok és az Azure Data Lake integrációja (előzetes verzió)](service-dataflows-azure-data-lake-integration.md)


