---
title: 'Oktatóanyag: Machine Learning-modell létrehozása a Power BI-ban (előzetes verzió)'
description: Ebben az oktatóanyagban egy Machine Learning-modellt fog létrehozni a Power BI-ban.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 03/29/2019
ms.author: davidi
LocalizationGroup: Connect to services
ms.openlocfilehash: 611d6f6c923e6cb68af94840c4266a0b6dee7651
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61406743"
---
# <a name="tutorial-build-a-machine-learning-model-in-power-bi-preview"></a>Oktatóanyag: Machine Learning-modell létrehozása a Power BI-ban (előzetes verzió)

Ebben az oktatóanyagban egy bináris előrejelzési modellt fog létrehozni és alkalmazni a Power BI-ban az **automatizált gépi tanulás** használatával. Az oktatóanyag alapján létrehozhat egy Power BI-adatfolyamot, és az adatfolyamban megadott entitások felhasználásával közvetlenül a Power BI-ban taníthat be és ellenőrizhet egy gépi tanulási modellt. Ezután a modellt előrejelzések pontozására és létrehozására használjuk.

Először létre kell hoznia egy bináris előrejelzési gépi tanulási modellt, amely az online vásárlók vásárlási szokásait jelzi előre az online munkamenet-attribútumaik alapján. A gyakorlathoz teljesítményteszt-alapú gépi tanulási adatkészletet használunk. A modell betanítása után a Power BI automatikusan létrehoz egy ellenőrzési jelentést, amely ismerteti a modell eredményeit. Tekintse át az ellenőrzési jelentést, és ezután felhasználhatja a modellt a saját adatainak pontozására.

Az oktatóanyag a következő lépésekből áll:

> [!div class="checklist"]
> * Adatfolyam létrehozása a bemeneti adatokkal
> * Gépi tanulási modell létrehozása és betanítása
> * A modell ellenőrzési jelentésének áttekintése
> * A modell alkalmazása egy adatfolyam-entitásra
> * A modell pontozott kimenetének felhasználása egy Power BI-jelentésben

## <a name="create-a-dataflow-with-the-input-data"></a>Adatfolyam létrehozása a bemeneti adatokkal

Az oktatóanyag első része a bemeneti adatokat tartalmazó adatfolyam létrehozását ismerteti. Az alábbi szakaszban bemutatott folyamat több lépésből áll, amelyek közül az első az adatok lekérése.

### <a name="get-data"></a>Adatok lekérése

Az adatfolyam létrehozásának első lépése az adatok előkészítése. Példánkban egy olyan online munkamenet-sorozatból nyertük ki a gépi tanulás adatkészletét, amelynek egy része vásárlással végződött. Az adatkészletben a munkamenetek attribútumai találhatók, amelyeket a modell betanítására használunk.

Az adatkészlet letölthető az UC Irvine webhelyről.  Az adatkészlet a jelen oktatóanyag céljaira elérhető a következő hivatkozáson is: [online_shoppers_intention.csv](https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv).

### <a name="create-the-entities"></a>Az entitások létrehozása

Ahhoz, hogy létre tudja hozni az adatfolyamban az entitásokat, be kell jelentkeznie a Power BI szolgáltatásba. Lépjen egy olyan munkaterületre a dedikált kapacitásán belül, amelyben engedélyezve van az AI előzetes verzió.

Ha még nincs munkaterülete, létrehozhat egyet. Ehhez válassza a **Munkaterületek** elemet a Power BI szolgáltatás bal oldali navigációs menüjében, majd a megjelenő panel alján válassza az **Alkalmazás-munkaterület létrehozása** lehetőséget. Ez megnyit egy panelt a jobb oldalon, ahol megadhatja a munkaterület adatait. Írja be a munkaterület nevét, majd válassza a **Speciális** lehetőséget. A választógombbal győződjön meg róla, hogy a munkaterület dedikált kapacitást használ, és olyan dedikáltkapacitás-példányhoz van rendelve, amelyhez be van kapcsolva az AI előzetes verziója. Kattintson a **Mentés** gombra.

![Munkaterület létrehozása](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-01.png)

Ha létrehozta a munkaterületet, választhatja az üdvözlő képernyő alján jobbra a **Kihagyás** lehetőséget, az alábbi kép szerint.

![Kihagyás, ha már van munkaterülete](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-02.png)

Kattintson az **Adatfolyamok (előzetes verzió)** fülre. Válassza a **Létrehozás** lehetőséget a munkaterület jobb felső sarkában, majd válassza az **Adatfolyam** elemet.

![Adatfolyam létrehozása](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-03.png)

Válassza az **Új entitások hozzáadása** lehetőséget. Ez elindítja a **Power Query** szerkesztőjét a böngészőben.

![Új entitás hozzáadása](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-04.png)

Adatforrásként válassza a **Text/CSV fájl** lehetőséget az alábbi kép szerint.

![Text/CSF file kiválasztása](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-05.png)

Az ekkor megjelenő **Csatlakozás adatforráshoz** lapon illessze az *online_shoppers_intention.csv* fájlra mutató hivatkozást a **Fájl elérési útja vagy URL** mezőbe, majd kattintson a **Tovább** elemre.

`https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv`

![Fájl elérési útja](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-06.png)

A Power Query-szerkesztő megjeleníti a CSV-fájl adatainak előnézetét. A parancssávon válassza a **Tábla átalakítása** elemet, majd a megjelenő menüből válassza az **Első sor használata fejlécként** lehetőséget. Ez hozzáadja az _Előléptetett fejlécek_ lekérdezési lépést a képernyő jobb oldalán látható **Alkalmazott lépések** szakaszhoz. A jobb oldali panelen látható **Név** mező értékének módosításával felhasználóbarát nevet adhat a lekérdezésnek. A Query (Lekérdezés) nevet például _Online Visitor_ (Online látogató) névre módosíthatja.

![Módosítás felhasználóbarát névre](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-07.png)

A példában szereplő adatkészlet egyes attribútum-adattípusai _numerikus_ vagy _logikai_ jellegűek, de a **Power Query** karakterláncként is azonosíthatja őket. Az oszlopfejlécekben az attribútumtípus ikonjára kattintva módosítsa az alábbi oszlopokat a következő típusokra:

* **Tizedes tört:** Administrative_Duration; Informational_Duration; ProductRelated_Duration; BounceRates; ExitRates; PageValues; SpecialDay
* **Igaz/Hamis:** Weekend (Hétvége); Revenue (Bevétel)

![Adattípus módosítása](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-08.png)

A betanítani kívánt **bináris előrejelzési** modellhez a korábbi megfigyelésekből származó eredményeket logikai címkével kell azonosítani. A példánkban szereplő adatkészletben a vásárlást a _Revenue_ (Bevétel) attribútum jelzi, amely már logikai érték formájában jelenik meg. Ezért nem kell számított oszlopot hozzáadnunk a címkéhez. Más adatkészletekben előfordulhat, hogy a meglévő címkeattribútumokat logikai oszloppá kell alakítani.

A Power Query-szerkesztő bezárásához válassza a **Kész** lehetőséget. Ez megjeleníti az entitások listáját a felvett _Online Visitor_ adatokkal. Válassza a **Mentés** lehetőséget a jobb felső sarokban, adjon nevet az adatfolyamnak, majd a párbeszédpanelen válassza a **Mentés** lehetőséget z alábbi kép szerint.

![Az adatfolyam mentése](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-09.png)

### <a name="refresh-the-dataflow"></a>Az adatfolyam frissítése

Az adatfolyam eredményeinek mentésekor értesítés jelenik meg, hogy az adatfolyam mentése megtörtént. Válassza a **Frissítés most** lehetőséget – ezzel betölti az adatokat a forrásból az adatfolyamba.

![Azonnali frissítés](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-10.png)

A jobb felső sarokban válassza a **Bezárás** lehetőséget, és várja meg, amíg az adatfolyam frissítése befejeződik.

Az adatfolyamot a **Műveletek** parancsok használatával is frissítheti. Az adatfolyam megjeleníti a frissítés befejeződésének időbélyegzőjét is.

![A frissítés időbélyege](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-11.png)

## <a name="create-and-train-a-machine-learning-model"></a>Gépi tanulási modell létrehozása és betanítása

A frissítés befejezése után válassza ki az adatfolyamot. Gépi tanulási modell felvételéhez válassza a **Műveletek** listában az **ML-modell alkalmazása** gombot a betanítási és címkeadatokat tartalmazó alapentitáshoz, majd kattintson a **Gépi tanulási modell hozzáadása** lehetőségre.

![Gépi tanulási modell hozzáadása](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-12.png)

A gépi tanulási modell létrehozásának első lépése az előzményalapú adatok azonosítása az előrejelezni kívánt címkemezőt is beleértve. A modell létrehozásához ezekből az adatokból tanul a rendszer.

A példánkban használt adatkészlet esetében ez a **Revenue** mező. Jelölje ki a **Revenue** mezőt az előzményalapú eredmények mezőjeként, majd kattintson a **Tovább** elemre.

![Előzményalapú adatok kiválasztása](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-13.png)

A továbbiakban ki kell választanunk a létrehozni kívánt gépi tanulási modellt. A Power BI elemzi az előzményalapú eredmények mezőjében megadott értékeket, és javaslatot tesz a mező előrejelzéséhez létrehozható gépi tanulási modelltípusokra.

Mivel példánkban bináris eredményt várunk arra a kérdésre, hogy a felhasználó vásárol-e vagy sem, jelölje ki a **Bináris előrejelzés** lehetőséget, majd kattintson a Tovább elemre.

![A bináris előrejelzés kiválasztása](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-14.png)

A következő lépésben a Power BI elvégzi az adatok előzetes vizsgálatát, és javaslatot tesz a modell által használható bemenetekre. A modell által használt bemeneti mezőket lehetősége van testre szabni. Az általunk kiválasztott adatkészletben jelölje ki az entitás neve melletti jelölőnégyzetet az összes mező kiválasztásához. A bemenetek jóváhagyásához kattintson a **Tovább** elemre.

![Tovább jelölőnégyzet kijelölése](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-15.png)

Az utolsó lépésben el kell nevezni a modellt és azokat a felhasználóbarát címkéket, amelyek hozzárendelődnek a modell értékelési eredményeit összefoglaló, automatikusan előállított jelentés eredményeihez. Legyen a modell neve _Vásárlási szándék előrejelzése_, az Igaz és Hamis címkék neve pedig legyen _Vásárlás_ és _Nem vásárlás_. Kattintson a **Mentés** gombra.

![A modell mentése](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-16.png)

A gépi tanulási modell ezzel készen áll a betanításra. A betanítás elkezdéséhez kattintson a **Frissítés most** elemre.

![Azonnali frissítés](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-17.png)

A betanítási folyamat kezdő lépései az előzményalapú adatok mintavételezése és normalizálása, valamint az adatkészlet felosztása *Vásárlási szándék előrejelzése betanítási adatok* és *Vásárlási szándék előrejelzése tesztadatok* csoportra.

A betanítási folyamat az adatkészlet méretétől függően néhány perctől akár több óráig is eltarthat. Ekkor a modell megjelenik az adatfolyam **Gépi tanulási modellek** lapján. A _Kész_ állapot azt jelzi, hogy a modell várólistára került, vagy már betanítás alatt áll.

![Betanításra kész](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-18.png)

A modell betanítása alatt az adatfolyam nem tekinthető meg és nem szerkeszthető. A modell betanításának és ellenőrzésének folyamatát az adatfolyam állapotából ellenőrizheti. Ez az információ a munkaterület **Adatfolyamok** lapján, folyamatban lévő adatfrissítésként jelenik meg.

![Folyamatban](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-19.png)

Ha a modell betanítása lezárult, az adatfolyam megjeleníti a legújabb frissítés időpontját. Az adatfolyam **Gépi tanulási modellek** lapjára lépve ellenőrizheti, hogy a modell betanítása lezárult-e. A létrehozott modellnek ilyenkor **Betanított** állapotban kell lennie, és a **Legutóbbi betanítás** időpontja már frissült.

![Legutóbb betanítva ekkor](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-20.png)

## <a name="review-the-model-validation-report"></a>A modell ellenőrzési jelentésének áttekintése

A modell ellenőrzési jelentésének áttekintéséhez a **Gépi tanulási modellek** lapon kattintson a **Teljesítményjelentés megtekintése és modell alkalmazása** gombra a modellhez tartozó **Műveletek** oszlopban. A jelentés a gépi tanulási modell valószínű teljesítményét ismerteti.

A modell legfontosabb előrejelzőinek megtekintéséhez a jelentés **Modell teljesítménye** oldalán kattintson a **Legfontosabb befolyásolók** elemre. Ha kijelöli valamelyik előrejelzőt, megtekintheti a hozzá tartozó kimenetek eloszlását.

![A modell teljesítménye](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-21.png)

A Modell teljesítménye oldalon lévő **Valószínűségi küszöb** szeletelő használatával megvizsgálhatja a Pontosságra és Visszahívásra gyakorolt hatást.

![Valószínűségi határérték](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-22.png)

A jelentés további oldalai a modell teljesítményének statisztikai mérőszámait ismertetik.

A jelentés egy Betanítási adatok lapot is tartalmaz, amely ismerteti a futtatott iterációkat, a funkciók bemenetekből kinyeréséhez használt módszereket és a felhasznált végső modell hiperparamétereit.

## <a name="apply-the-model-to-a-dataflow-entity"></a>A modell alkalmazása egy adatfolyam-entitásra

Kattintson a jelentés tetején látható **Modell alkalmazása** gombra a modell meghívásához az adatfolyam frissítésekor. Az **Alkalmaz** párbeszédpanelen megadhatja azt a célentitást, amelynek adataira a modellt alkalmazni kell.

![A modell alkalmazása](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-23.png)

Amikor a rendszer erre kéri, **frissítse** az adatfolyamot a modell eredményeinek megtekintéséhez.

A modell alkalmazása **enriched <model_name>** utótaggal egy új alkalmazást hoz létre, amely ahhoz az entitáshoz kapcsolódik, amelyre a modellt alkalmazta. A mi példánk a modellt az **OnlineShoppers** entitásra alkalmazta, így az **OnlineShoppers enriched Purchase Intent Prediction** entitás jött létre, benne a modell által előrejelzett kimenettel.

A bináris előrejelzési modell alkalmazása három oszlopot hoz létre, amelyek az előrejelzett eredményt, a valószínűségi pontszámot és a legfőbb rekordspecifikus befolyásolókat tartalmazzák, előtagjuk pedig a megadott oszlopnév.

![A három eredményoszlop](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-24.png)

Egy ismert probléma miatt a kiegészített entitás pontozott eredményoszlopai csak a Power BI Desktopból érhetők el. Ha működés közben szeretné látni őket, különleges előnézeti entitást kell használnia.

Miután az adatfolyam frissítése lezajlott, az eredményeket az **OnlineShoppers enriched Purchase Intent Prediction Preview** entitás kijelölésével tekintheti meg.

![Az eredmények megtekintése](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-25.png)

## <a name="using-the-scored-output-from-the-model-in-a-power-bi-report"></a>A modell pontozott kimenetének felhasználása Power BI-jelentésben

A gépi tanulási modellből származó pontozott kimenetek használatához a Adatfolyamok összekötő segítségével csatlakoztathatja az adatfolyamot a Power BI Desktopból. Az **OnlineShoppers enriched Purchase Intent Prediction** entitás segítségével mostantól beillesztheti a modellből származó előrejelzéseket a Power BI-jelentésekbe.

## <a name="next-steps"></a>Következő lépések

Ebben az oktatóanyagban bináris előrejelzési modellt hozott létre és alkalmazott a Power BI-ban az alábbi lépéseket követve:

* Adatfolyam létrehozása a bemeneti adatokkal
* Gépi tanulási modell létrehozása és betanítása
* A modell ellenőrzési jelentésének áttekintése
* A modell alkalmazása egy adatfolyam-entitásra
* A modell pontozott kimenetének felhasználása Power BI-jelentésben

A gépi tanulás Power BI-ban történő automatizálásához lásd még: [Automatizált gépi tanulás a Power BI-ban (előzetes verzió)](service-machine-learning-automated.md).
