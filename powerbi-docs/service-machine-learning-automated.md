---
title: Automatizált Machine Learning a Power BI-ban (előzetes verzió)
description: Machine Learning automatikus (AutoML) használata a Power bi-ban
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
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61236450"
---
# <a name="automated-machine-learning-in-power-bi-preview"></a>Automatizált Machine Learning a Power BI-ban (előzetes verzió)

Automatizált a machine learning (AutoML) adatfolyamok esetében lehetővé teszi, hogy az üzleti elemzők betanításához, érvényesíteni, és meghívja a Machine Learning-modellek közvetlenül a Power bi-ban. Ez magában foglalja egy egyszerű felület, ahol elemzők az adatfolyamok megadásához használhatja a bemeneti adatokat a modell betanításához új gépi Tanulási modell létrehozásához. A szolgáltatás automatikusan kinyeri a leginkább releváns szolgáltatások, megfelelő algoritmus kiválasztása és hangolja és érvényesíti a gépi Tanulási modell. A modell tanítása, miután a Power BI automatikusan létrehozza egy jelentést, amely tartalmazza az eredményeket, amely ismerteti a teljesítmény érvényesítési és az eredményeket, hogy az elemzők. A modell majd minden új vagy frissített adatokon belül az adatfolyamot lehet meghívni.

![Machine learning képernyő](media/service-machine-learning-automated/automated-machine-learning-power-bi-01.png)

Automatizált machine learning szolgáltatás csak a Power BI Premium és a beágyazott kapacitások lévő adatfolyamok érhető el. Ebben az előzetes verzióban AutoML lehetővé teszi a bináris előrejelzési besorolási és regressziós modellek gépi tanulási modelleket taníthat be.

## <a name="working-with-automl"></a>AutoML használata

[A Power BI-adatfolyamok](service-dataflows-overview.md) önkiszolgáló adatelőkészítéshez big Data-ajánlat. AutoML lehetővé teszi lehetővé az adatok előkészítési erőfeszítés létrehozásához a machine learning-modellek, közvetlenül a Power BI-ban.

AutoML a Power BI lehetővé teszi az adatelemzők adatfolyamok használatával hozhat létre a machine learning-modellek egyszerűsített felhasználói élmény, csak a Power BI készségeit. A legtöbb mögött az ML-modellek létrehozása a data science guardrails, ügyeljen arra, hogy a modell előállított jó minőségű, és látható-e, így a folyamat a gépi Tanulási modellek létrehozásához használt teljes körű betekintést nyújt a a Power BI, automatizált.

AutoML támogatja a **bináris előrejelzési**, **besorolási**, és **regressziós** adatfolyamok modelleket. Ezek olyan felügyelt machine learning-modellek, ami azt jelenti, hogy tanuljon előre jelezni az eredményekkel más megfigyelések múltbeli megfigyelések ismert eredményeit. A bemeneti adatkészlet egy AutoML modell betanításához egy olyan bejegyzéseket, amelyek **feliratú** az ismert eredményekkel együtt.

AutoML a Power BI integrálható [ML automatikus](https://docs.microsoft.com/azure/machine-learning/service/concept-automated-ml) származó a [Azure Machine Learning szolgáltatás](https://docs.microsoft.com/azure/machine-learning/service/overview-what-is-azure-ml) a gépi Tanulási modellek létrehozásának eljárásait. Azonban nem kell Azure-előfizetés AutoML használata a Power bi-ban. A képzés és a gépi Tanulási modelleket üzemeltető folyamat teljes egészében a Power BI szolgáltatás kezeli.

Egy gépi Tanulási modellek tanítása, miután a AutoML automatikusan létrehozza a Power BI-jelentés, amely ismerteti a gépi Tanulási modell valószínűleg teljesítményét. AutoML explainability, kiemelve a fontos Véleményformálók többek között a bemeneteket az előrejelzés a modell által visszaadott befolyásoló által emeli ki. A jelentés alapvető metrikákat, a gépi Tanulási modell típusától függően a modell része.

A létrehozott jelentés egyéb oldalain statisztikai összegzését a modell és a képzési részletek megjelenítése. A statisztikai összegzés van, a felhasználók számára azt, hogy a modell teljesítményét, a standard szintű adatelemző mértékek meg lényeges. A képzési részleteit a modell létrehozásához a társított modellezési paraméterekkel futtató összes ismétlésének foglalják össze. Azt is ismerteti, hogyan minden egyes bemenet a gépi Tanulási modellek létrehozásához használt.

A gépi Tanulási modell adatait a kiértékelés ezután alkalmazhat. Az adatfolyam frissítésekor a rendszer automatikusan alkalmazza a gépi Tanulási modellek által létrehozott javaslatok az adatokhoz. Power bi-ban minden egyes adott előrejelzési pontszám, amely a gépi Tanulási modell rajongóknak magyarázattal is tartalmaz.

## <a name="creating-a-machine-learning-model"></a>A gépi tanulási modell létrehozása

Ez a szakasz ismerteti, hogyan hozhat létre egy AutoML tanulási modell. 

### <a name="data-prep-for-creating-an-ml-model"></a>Adat-előkészítési egy gépi Tanulási modellek létrehozásához

Hozzon létre egy gépi tanulási modellt a Power bi-ban, először hozzon létre az adatok egy adatfolyam az előzményadatok serkenti az eredményt információkkal szolgál a gépi Tanulási modell betanításához. Az adatfolyam konfigurálásával kapcsolatos részletekért lásd: [önkiszolgáló adat-előkészítési a Power bi-ban](service-dataflows-overview.md).

A jelenlegi kiadásban a Power bi-ban csak egyetlen entitáshoz adatait használja a gépi Tanulási modell betanításához. Ezért ha több entitás tartalmaz előzményadatait, manuálisan csatlakoztatnia kell az adatok egy egyetlen adatfolyam entitásba. Számított oszlopok bármely üzleti metrikákat, lehet, hogy az előre jelezni kívánt eredményhez erős előrejelzőket is hozzá kell adnia.

AutoML a machine learning-modell betanításához meghatározott követelményekkel rendelkezik. Ezeket a követelményeket ismerteti, az alábbi szakaszok a megfelelő modellt típusok alapján.

### <a name="configuring-the-ml-model-inputs"></a>A gépi Tanulási modell bemeneti adatok konfigurálása

Egy AutoML modell létrehozásához, válassza ki a gépi tanulás ikonra a **műveletek** korábbi adatok alapján, majd válassza az adatfolyamot entitás oszlop **adjon hozzá egy gépi tanulási modellt**.

![Adjon hozzá egy gépi tanulási modell](media/service-machine-learning-automated/automated-machine-learning-power-bi-02.png)

Egyszerű élmény indításakor álló egy varázslót, amely végigvezeti Önt a gépi Tanulási modellek létrehozásának folyamatán. A varázslóban az alábbi egyszerű lépéseket.

1. Válassza ki az entitást a korábbi serkenti az eredményt és a mező, amelyek esetében szeretne előrejelzése
2. Válassza ki a modell típusa alapján az előrejelzéses szeretné látni
3. Válassza ki a bemeneti adatok a modellt, prediktív jelek használata
4. Nevezze el a modellt, és mentse a konfigurációt

A korábbi serkenti az eredményt mező azonosítja a címke attribútum a következő képen látható, a gépi Tanulási modell betanításához.

![Korábbi serkenti az eredményt adatok kiválasztása](media/service-machine-learning-automated/automated-machine-learning-power-bi-03.png)

A korábbi serkenti az eredményt a mező megadása esetén a AutoML elemzi a címke az adatokat használva azonosítja a gépi Tanulási modelleket, amelyek is vélik, hogy az adatok típusait, és a legnagyobb valószínűséggel gépi Tanulási modell típusa, amely képes tartani a következőkről javasol. 

> [!NOTE]
> Néhány modell típusa nem támogatott a kiválasztott adatok.

AutoML is használható a gépi Tanulási modell betanításához bemenetei javasolja a kiválasztott entitás mezőinek elemzi. Ez a folyamat hozzávetőleges és statisztikai elemzésekhez alapul, ezért tekintse át a bemeneti adatok használt. A korábbi serkenti az eredményt mező (vagy a címke mező) függő bemenetet a gépi Tanulási modell betanításához hatással lesz a teljesítményét, mivel nem használható.

![Beviteli mezők testreszabása](media/service-machine-learning-automated/automated-machine-learning-power-bi-04.png)

Az utolsó lépésben a modell neve, és mentse a beállításokat.

Ezen a ponton kéri az adatfolyamot, amely megkezdi a gépi Tanulási modell a betanítási folyamat frissítése.

### <a name="ml-model-training"></a>Gépi Tanulási modell betanítása

Képzési AutoML modellek az adatfolyamot frissítés része. AutoML először képzési előkészíti az adatokat.

AutoML oszt fel egy tanítási és tesztelési adnia előzményi adatokat. A tesztelési adatkészletnél olyan visszatartási képzési után a modellek teljesítményének ellenőrzése szolgálja ki. Ezek is felismerte **betanítására és tesztelésére** entitások az adatfolyamban. A modell érvényesítése kereszt-ellenőrzési AutoML használ.

Ezután minden beviteli mező elemzett és imputálási van érvényben, amelyek hiányzó értéket lecseréli a helyettesített érték. Több különböző imputálási stratégiák AutoML használja. Ezután minden szükséges mintavételi és normalizálási tüntetjük fel az adatokat.

AutoML vonatkozik több átalakításokra a kijelölt beviteli mező jeho datovému typu és a statisztikai tulajdonságai alapján. AutoML bontsa ki a gépi Tanulási modell tanítása használt funkciók átalakításokat használ.

A betanítási folyamat AutoML modellek különböző modellezési algoritmusokkal és a hiperparaméter beállítások keresése a modell a legjobb teljesítmény érdekében legfeljebb 50 ismétlések áll. Ezek a modellek teljesítményét a visszatartási tesztadatkészlet érvényesítést által adatokon. A képzési lépés során AutoML hoz létre több folyamatokat, és ezeket az ismétlések érvényesítése. A folyamat a modellek teljesítményének értékeléséhez bárhol néhány óra múlva, az adatkészlet és a dedikált kapacitás elérhető erőforrások méretétől függően néhány perctől időt vehet igénybe.

Bizonyos esetekben a kész modell generált tanulás, ahol több modell segítségével jobban prediktív teljesítmény ensemble használhatja.

### <a name="automl-model-explainability"></a>AutoML modell explainability

Miután a modell rendelkezik betanítva, AutoML elemzi a bemeneti funkciói és a modell kimeneti közötti kapcsolat. Azt értékeli a magnitude és irányának módosítása a modell kimeneti visszatartási teszt adatkészlet az egyes bemeneti szolgáltatásokhoz. Ez más néven a *fontosság funkció*.

![A szolgáltatás fontosság](media/service-machine-learning-automated/automated-machine-learning-power-bi-05.png)

### <a name="automl-model-report"></a>AutoML modell jelentés

AutoML hoz létre a Power BI-jelentés, amely összefoglalja a modell teljesítményét, és a globális szolgáltatás fontosság érvényesítése során. A jelentés összesíti az eredményeket a gépi Tanulási modellt alkalmaz a visszatartási Tesztadatok és összehasonlítja az előrejelzés eredményét ismert értékekkel.

A modell jelentést, a teljesítményét annak tekintheti meg. Emellett ellenőrizheti, hogy a modell fontos Véleményformálók összhangba kerüljenek az üzleti elemzések az ismert eredményekkel kapcsolatban.

A diagramok és a mértékeket a modell teljesítményét, a jelentés leírására szolgáló modell-típustól függnek. A következő szakaszok ezeket teljesítménydiagramok és mértékek ismerteti.

A jelentés további oldalainak előfordulhat, hogy adja meg a data science szempontjából a modell statisztikai mértékeket. Például a **bináris előrejelzési** jelentés nyereség diagramot és a ROC-görbe a modell tartalmazza.

A jelentések is tartalmazzák a **képzési részletek** hogyan a modell betanított volt, és tartalmazza az egyes ismétlésének a modellek teljesítményének leíró diagram leírását tartalmazó lapon futtatja.

![Tanulás részletei](media/service-machine-learning-automated/automated-machine-learning-power-bi-06.png)

Ezen az oldalon egy másik szakasz ismerteti, hogy a imputálási metódus hiányzó értékeit az adatbeviteli mezők kitöltéséhez is, hogy hogyan minden beviteli mező a modellben használt a szolgáltatások kibontásához lettek átalakítva. A kész modell által használt paraméterek is tartalmaz.

![További információ a modell](media/service-machine-learning-automated/automated-machine-learning-power-bi-07.png)

Ha a létrehozott modellt használ ensemble tanulás, akkor a **képzési részletek** oldal is egy a ensemble, valamint paramétereket lévő minden egyes alkotó modell súlyát leíró szakaszt.

![A ensemble súly](media/service-machine-learning-automated/automated-machine-learning-power-bi-08.png)

## <a name="applying-the-automl-model"></a>A AutoML modell alkalmazása

Ha elégedett a létrehozott gépi Tanulási modell teljesítményét, alkalmazhat, új vagy frissített adatok az adatfolyam frissítésekor. Ezt megteheti is a modell jelentésből kiválasztásával a **alkalmaz** gombra a jobb felső sarokban.

A alkalmazni, a gépi Tanulási modellt az entitást, amelyhez azt kell alkalmazni, és a egy előtagot az oszlopok, amely belekerül a modell kimeneti az entitás nevét kell megadnia. Az alapértelmezett előtag, az oszlopneveket számára, a modell neve. A *alkalmaz* függvény előfordulhat, hogy tartalmazza a modelltípus vonatkozó további paraméterek.

Egy új adatfolyamot entitás alkalmazása a gépi Tanulási modellt hoz létre az utótag **< modell_neve > bővített**. Például ha alkalmaz a _PurchaseIntent_ a modell a _OnlineShoppers_ entitáshoz, a kimenetet fog létrehozni a **OnlineShoppers bővített PurchaseIntent**.

A kimeneti entitás jelenleg nem használható a Power Query-szerkesztőben a gépi Tanulási modell eredményeinek megtekintése. A kimeneti oszlopok mindig jeleníti meg null eredményezi. Tekintse meg az eredményeket, egy második kimeneti utótagjával rendelkező entitás **< modell_neve > Előnézet bővített** jön létre a modell alkalmazása esetén.

Frissítenie kell az adatfolyamot, a Lekérdezésszerkesztő az eredmények előnézetének megtekintése.

![Lekérdezésszerkesztő](media/service-machine-learning-automated/automated-machine-learning-power-bi-09.png)

Amikor alkalmazza a modellt, AutoML mindig megőrzi az előrejelzések naprakész az adatfolyamot frissítésekor.

AutoML minden egyes sorára, amely azt pontszámmodell rajongóknak magyarázattal is tartalmaz a kimeneti entitásban.

Az elemzések és előrejelzések a gépi Tanulási modell alapján a Power BI-jelentésekben használatához csatlakozhat a kimeneti entitáshoz a Power BI Desktop használatával a **adatfolyamok** összekötő.

## <a name="binary-prediction-models"></a>Bináris prediktív modellek

Bináris prediktív modellek, több korábbi néven **bináris osztályozási modell**, adatkészlet besorolása a két csoportra szolgálnak. Események, amelyeken egy bináris eredménye, hogy egy értékesítési lehetőséggel konvertálja, például egy fiókot fog churn, hogy e számla alapján kell fordítani a Time; előre jelezni kell a tranzakció-e rosszindulatú, és így tovább.

Mivel az eredmény bináris, a Power bi-ban a címkét egy bináris előrejelzési modell egy logikai értéket, a "folyamatban" feliratú ismert eredményeket kell vár **igaz** vagy **hamis**. Például egy értékesítési lehetőséghez átalakítás modellben megnyert értékesítési lehetőségeket vannak ellátva true, false (hamis), amelyek elvesztek vannak ellátva és a nyitott értékesítési lehetőségeket vannak ellátva null értékű.

Egy bináris előrejelzési modell kimenete egy valószínűségi pontszámának létrehozásához, amely azonosítja annak a valószínűségét, hogy a felirat érték a true megfelelő eredménye érik el.

### <a name="training-a-binary-prediction-model"></a>Egy bináris előrejelzési modell betanítása

Egy bináris előrejelzési modell létrehozásához, a bemeneti entitás a tanítási adatokat tartalmazó azonosításához az utolsó ismert eredményekkel korábbi serkenti az eredményt mezőként kell rendelkeznie egy logikai típusú mező.

Előfeltételek:

* Egy logikai típusú mezőt kell használni, mint a korábbi serkenti az eredményt mező
* Az előzményadatok 50 sor legalább szükség az egyes eredmények

Általában egy más típusú mezők azonosítja az elmúlt eredményekkel, ha hozzáadhat egy számított oszlopot, ezeket egy logikai Power Queryvel történő átalakítására.

A létrehozási folyamat számára egy bináris előrejelzési modell a következő azonos lépések egyéb AutoML modelleket, a szakaszban leírt **konfigurálása a gépi tanulás modellbemenetek** felett.

### <a name="binary-prediction-model-report"></a>Bináris előrejelzési modell jelentés

A bináris előrejelzési modell kimenetként hoz létre, hogy egy rekord éri el az eredménye IGAZ, logikai címke értéke által meghatározott valószínűség. A jelentés tartalmazza a valószínűségi küszöbértéke, amely befolyásolja, hogyan legyenek értelmezve a valószínűségi küszöbértéke kisebb és nagyobb pontszámokat szeletelőt.

A jelentés azt ismerteti, hogy a modell teljesítményét *valódi pozitívok*, *Vakriasztások*, *igaz negatív* és *téves negatív*. Valódi pozitívok és valódi negatív a két osztály az eredmény adatok helyesen előre jelzett eredményekkel. Vakriasztások eredmények, a hamis értéket, a tényleges logikai címke volt, de TRUE előrejelzett is. Ezzel szemben téves negatív olyan eredményeket, ahol a tényleges logikai címke értéke igaz volt, de voltak előre meghatározott hamis értéket.

Mértékek, például a pontosság és a már ismert, az előre jelzett eredményekkel a valószínűségi küszöbértéke hatását ismertetik. A valószínűségi küszöbértéke szeletelő segítségével válassza ki a küszöbértéket, amellyel éri el a pontosság és a visszaírási kiegyensúlyozott kompromisszumot.

![Pontosság előzetes verzió](media/service-machine-learning-automated/automated-machine-learning-power-bi-10.png)

A **pontossága jelentés** a modell jelentés tartalmazza a *halmozott nyereség* diagram és a ROC-görbe a modellhez. Ezek a modellek teljesítményének statisztikai intézkedéseket. A jelentések a diagramokon látható leírását tartalmazzák.

![Pontosság Jelentéskezelő képernyőn](media/service-machine-learning-automated/automated-machine-learning-power-bi-11.png)

### <a name="applying-a-binary-prediction-model"></a>Egy bináris előrejelzési modell alkalmazása

A alkalmazni egy bináris előrejelzési modell, meg kell adnia az entitás, amelyre az előrejelzés a gépi Tanulási modellt a alkalmazni szeretné az adatokat. Más paramétereket tartalmazzák a kimeneti oszlopnév-előtag és a valószínűségi küszöbértéke az Írisz az előre jelzett serkenti az eredményt.

![Előrejelzési bemenetek](media/service-machine-learning-automated/automated-machine-learning-power-bi-12.png)

Ha egy bináris előrejelzési modell alkalmazza, három kimeneti oszlopok hozzáadása a jelentéstétellel kimeneti entitás. Ezek a **PredictionScore**, **PredictionOutcome** és **PredictionExplanation**. Az oszlopok neveit az entitásban meg, ha a modell alkalmazandó előtagot kell.

A **PredictionOutcome** oszlop tartalmazza az előre jelzett serkenti az eredményt címkét. A küszöbérték átlépését valószínűségek rekordokat vannak előre jelzett, valószínűleg az eredmény elérése érdekében, és azok alá vannak, nem valószínű, hogy az eredmény elérése érdekében előre meghatározott.

A **PredictionExplanation** oszlop tartalmazza az adott hatást a bemeneti funkciói volt magyarázata a **PredictionScore**. Ez a bemeneti funkciói az előrejelzés súlyozását JSON formátumú gyűjteménye.

## <a name="classification-models"></a>Képbesorolási modellek

Képbesorolási modellek segítségével több csoport vagy osztály az adatkészlet besorolása.  Eseményeket, amelyek több lehetséges kimenetek, például az ügyfél valószínűleg egy nagyon magas, magas, közepes vagy alacsony a Csoportélettartam értékének; e egyike előre jelezni kell -e alapértelmezett kockázatát a magas, közepes, alacsony vagy nagyon alacsony; és így tovább.

A valószínűségi pontszámának létrehozásához, amely azonosítja annak a valószínűségét, hogy egy rekordot a feltételeknek, egy adott osztály elérése érdekében. a besorolási modell kimenete.

### <a name="training-a-classification-model"></a>A besorolási modell tanítása

A bemeneti entitást tartalmazó osztályozási modell a betanítási adatok, a korábbi serkenti az eredményt mező, amely azonosítja az utolsó ismert eredményekkel rendelkeznie kell egy karakterlánc- vagy numerikus mező.

Előfeltételek:

* Az előzményadatok 50 sor legalább szükség az egyes eredmények

A létrehozási folyamat esetében ugyanaz a besorolási modell a következő lépések egyéb AutoML modelleket, a szakaszban leírt **konfigurálása a gépi tanulás modellbemenetek** felett.

### <a name="classification-model-report"></a>Osztályozási modell jelentés

A besorolási modell jelentés előállítása a gépi Tanulási modellt alkalmaz a visszatartási adatok, és összehasonlítja az előrejelzett osztály egy rekord a tényleges ismert osztállyal teszteléséhez.

A modell jelentés egy diagramot, amely tartalmazza a megfelelő és nem megfelelően osztályozott rekordokat az egyes ismert áttekintését tartalmazza.

![Modell-jelentés](media/service-machine-learning-automated/automated-machine-learning-power-bi-13.png)

Egy további osztály-specifikus drilldown lehetővé teszi, hogy hogyan oszlanak meg az adatokat egy ismert osztály elemzése. Ez magában foglalja a más osztályok, amelyben az adott osztály ismert rekordok várhatóan misclassified lehet.

![Elemzése – jelentés](media/service-machine-learning-automated/automated-machine-learning-power-bi-14.png)

A modell magyarázata a jelentésben szereplő minden egyes osztály a felső előrejelzőket is tartalmaz.

A besorolási modell jelentést is tartalmaz, minden olyan modell esetében a lapok hasonló képzési részletei lap, a szakaszban leírt módon **AutoML modell jelentés** a cikk elején.

### <a name="applying-a-classification-model"></a>A besorolási modell alkalmazása

A alkalmazni egy besorolási gépi Tanulási modellt, meg kell adnia az entitás a bemeneti adatokat és a kimeneti oszlopnév-előtag.

A besorolási modell alkalmazásakor hozzáadja három kimeneti oszlopok a jelentéstétellel kimeneti entitáshoz. Ezek a **PredictionScore**, **PredictionClass** és **PredictionExplanation**. Az oszlopok neveit az entitásban meg, ha a modell alkalmazandó előtagot kell.

A **PredictionClass** oszlop tartalmazza a rekord a nagy valószínűséggel előrejelzett osztály. A **PredictionScore** oszlop tartalmazza a valószínűség pontszámok a rekord minden lehetséges osztályhoz.

A **PredictionExplanation** oszlop tartalmazza az adott hatást a bemeneti funkciói volt magyarázata a **PredictionScore**. Ez a bemeneti funkciói az előrejelzés súlyozását JSON formátumú gyűjteménye.

## <a name="regression-models"></a>Regressziós modellek

Regressziós modellek segítségével előre jelezni az értéket, például a bevétel nagy valószínűséggel abban az esetben az értékesítési üzlet, a csoportélettartam értékének egy olyan fiók, a Kinnlevőségek számlát, amely nagy eséllyel kell fizetni, a dátum, amelyen számla alapján fizetendő összeg , és így tovább.

Egy regressziós modell kimenete az előre jelzett érték.

### <a name="training-a-regression-model"></a>Egy regressziós modell tanítása

Egy regressziós modell a betanítási adatok tartalmazó bemeneti entitásnak rendelkeznie kell egy számmező mint a korábbi serkenti az eredményt mező, amely azonosítja az utolsó ismert serkenti az eredményt értékeket.

Előfeltételek:

* Az előzményadatok 100 sor legalább egy regressziós modell megadása kötelező

A létrehozási folyamat esetében ugyanaz a regressziós modell a következő lépések egyéb AutoML modelleket, a szakaszban leírt **konfigurálása a gépi tanulás modellbemenetek** felett.

### <a name="regression-model-report"></a>Regressziós modell jelentés

Az egyéb AutoML modell jelentések, például a regressziós jelentést a modellt alkalmaz a visszatartási Tesztadatok eredményeinek alapul.

A modell jelentés egy diagramot, amely összehasonlítja a tényleges érték előre jelzett értékek tartalmazza. Ebben a diagramban a átlós közötti távolságot azt jelzi, hogy a hiba az előrejelzéshez.

A fennmaradó hiba diagram visszatartási teszt adatkészlet különböző értékek átlagos hiba százalékos elosztását mutatja. A vízszintes tengely megjelenítése a gyakoriságát, vagy az értékek száma a tartományon a buborék méretét az a csoport a tényleges érték átlagát jelöli. A függőleges tengely az átlagos maradék hiba.

![Maradék hiba diagram](media/service-machine-learning-automated/automated-machine-learning-power-bi-15.png)

A regressziós modell jelentést is tartalmaz minden olyan modell esetében a jelentések például képzési Részletek lap, a szakaszban leírt módon **AutoML modell jelentés** felett.

### <a name="applying-a-regression-model"></a>Egy regressziós modell alkalmazása

Egy regressziós gépi Tanulási modellt alkalmaz, meg kell adnia az entitás a bemeneti adatokat és a kimeneti oszlopnév-előtag.

![A alkalmazni regresszió](media/service-machine-learning-automated/automated-machine-learning-power-bi-16.png)

Egy regressziós modellt alkalmazzák, amikor két kimeneti oszlopok hozzáadása a jelentéstétellel kimeneti entitás. Ezek a **PredictionValue**, és **PredictionExplanation**. Az oszlopok neveit az entitásban meg, ha a modell alkalmazandó előtagot kell.

A **PredictionValue** oszlop tartalmazza az előre jelzett érték a rekord az adatbeviteli mezők alapján. A **PredictionExplanation** oszlop tartalmazza az adott hatást a bemeneti funkciói volt magyarázata a **PredictionValue**. Ez a bemeneti funkciói súlyozását JSON formátumú gyűjteménye.

## <a name="next-steps"></a>Következő lépések

Ez a cikk a Power BI szolgáltatásban automatikus Machine Learning áttekintése megadott adatfolyamot. Az alábbi cikkeket is hasznos lehet.

* [Oktatóanyag: Egy gépi tanulási modellt a Power bi-ban (előzetes verzió)](service-tutorial-build-machine-learning-model.md)
* [Oktatóanyag: A Cognitive Services használata a Power BI-ban](service-tutorial-use-cognitive-services.md)
* [Oktatóanyag: Machine Learning Studio-modell meghívása a Power BI-ban (előzetes verzió)](service-tutorial-invoke-machine-learning-model.md)
* [A Cognitive Services a Power BI-ban (Előzetes verzió)](service-cognitive-services.md)
* [Az Azure Machine Learning integrálása a Power BI-jal (Előzetes verzió)](service-machine-learning-integration.md)

Az adatfolyamokkal kapcsolatban az alábbi cikkeket érdemes elolvasni:
* [Adatfolyamok létrehozása és használata a Power BI-ban](service-dataflows-create-use.md)
* [A Power BI Premium számított entitások használatával](service-dataflows-computed-entities-premium.md)
* [Adatfolyamok használata a helyszíni adatforrások](service-dataflows-on-premises-gateways.md)
* [Fejlesztői erőforrások a Power BI-adatfolyamok](service-dataflows-developer-resources.md)
* [Adatfolyamok és az Azure Data Lake integrációja (előzetes verzió)](service-dataflows-azure-data-lake-integration.md)


