---
title: 'Oktatóanyag: Egy gépi tanulási modellt a Power bi-ban (előzetes verzió)'
description: Ebben az oktatóanyagban létrehozhat egy Machine Learning-modellhez, a Power bi-ban.
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
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61406743"
---
# <a name="tutorial-build-a-machine-learning-model-in-power-bi-preview"></a>Oktatóanyag: Egy gépi tanulási modellt a Power bi-ban (előzetes verzió)

Ez az oktatóanyag a cikk használhatja **automatikus Machine Learning** hozhat létre és alkalmazhat egy bináris előrejelzési modell, a Power bi-ban. Az oktatóanyag egy Power BI-adatfolyam létrehozására vonatkozó útmutatást tartalmaz, és tanítása és ellenőrzése egy gépi tanulási modellt közvetlenül a Power bi-ban az adatfolyamban meghatározott az entitások használatával. Ezt követően segítségével, hogy a modell pontozó előrejelzések készítése.

Először egy bináris előrejelzési gépi tanulási modellt, a vásárlás célt hatalmas online azok online munkamenet attribútumok alapján előre jelezni fog létrehozni. Teljesítményteszt machine learning adatkészlet ebben a gyakorlatban használható. A modell tanítása, miután a Power BI automatikusan létrehoz egy folyamatérvényesítési jelentés elmagyarázza a modell eredményei. Ezután tekintse át az ellenőrzési jelentésből, és alkalmazza a modell adatait a pontozási.

Ez az oktatóanyag a következő lépéseket tartalmazza:

> [!div class="checklist"]
> * Hozzon létre egy adatfolyam a bemeneti adatok
> * Hozzon létre, és a egy gépi tanulási modell betanítása
> * Tekintse át a modell folyamatérvényesítési jelentés
> * A modell vonatkozik egy adatfolyam-entitás
> * A modell a pontozott kimenetének használata a Power BI-jelentésekben

## <a name="create-a-dataflow-with-the-input-data"></a>Hozzon létre egy adatfolyam a bemeneti adatok

Ez az oktatóanyag első részét, ha egy adatfolyam bemeneti adatokkal. A folyamat néhány lépést tart, verziótól kezdődően az adatok beolvasása az alábbiakban látható módon.

### <a name="get-data"></a>Adatok lekérése

Az első lépés egy adatfolyam létrehozásával, készen áll az adatforrások hogy. Ebben az esetben egy gépi tanulási adatkészlet közül, online foglalkozások, amelyek során az vásárlás használjuk. Az adatkészlet tulajdonságai, ezek a munkamenetek, amelyek fogjuk használni a modell tanítása tartalmazza.

Az adatkészlet letöltheti a UC Irvine webhelyről.  Van elérhető, a jelen oktatóanyag a következő hivatkozás: [online_shoppers_intention.csv](https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv).

### <a name="create-the-entities"></a>Az entitások létrehozása

Ahhoz, hogy létre tudja hozni az adatfolyamban az entitásokat, be kell jelentkeznie a Power BI szolgáltatásba. Lépjen egy olyan munkaterületre a dedikált kapacitásán belül, amelyben engedélyezve van az AI előzetes verzió.

Ha még nem rendelkezik egy munkaterületet, létrehozhat egy kiválasztásával **munkaterületek** a Power BI szolgáltatásban, és válassza a bal oldali navigációs menüjében **alkalmazás munkaterületének létrehozása** a panel alján, akkor jelenik meg. Ekkor megnyílik egy panel, a jobb oldalon adja meg a munkaterület részletei. Adjon meg egy nevet, és válassza ki **speciális**. Győződjön meg arról, hogy a munkaterület dedikált kapacitás a választógomb használja-e, és hogy hozzá van rendelve egy dedikált kapacitás-példányt, amely rendelkezik-e kapcsolva, az AI előzetes verziója. Kattintson a **Mentés** gombra.

![Munkaterület létrehozása](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-01.png)

A munkaterület létrehozása után kiválaszthatja **kihagyása** alján jobb üdvözlőképernyő, az alábbi képen látható módon.

![Folytassa, ha egy munkaterületet](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-02.png)

Válassza ki a **adatfolyamok (előzetes verzió)** fülre. Válassza ki a **létrehozás** gombbal a megfelelő, a munkaterület, és adja meg **adatfolyamot**.

![Adatfolyam létrehozása](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-03.png)

Válassza az **Új entitások hozzáadása** lehetőséget. Ezzel elindítja a **Power Query** szerkesztő a böngészőben.

![Új entitás hozzáadása](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-04.png)

Válassza ki **Text/CSV-fájl** adatforrásként, az alábbi képen látható.

![A kijelölt szöveg/CSF fájl](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-05.png)

Az a **adatforráshoz csatlakozhat** , amely megjelenik a következő, illessze be a következő hivatkozásra kattintva a *online_shoppers_intention.csv* be a **fájl elérési útja vagy URL-cím** mezőbe, és válassza ki a  **Tovább**.

`https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv`

![Fájl elérési útja](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-06.png)

A Power Query-szerkesztő a CSV-fájlból az adatok előnézetét jeleníti meg. Válassza ki **tábla átalakítása** a parancs menüszalagon, majd válassza ki a **első sor használata fejlécként** lehetőséget a megjelenő menüből. Ez hozzáadja a _előléptetett fejlécek_ lekérdezés lépést, a **alkalmazott lépései** szakasz a képernyő jobb. Átnevezheti a lekérdezés arculata névre értékét módosítsa úgy a **neve** mezőbe a jobb oldali ablaktáblában található. Ha például sikerült módosítani a lekérdezés nevét _Online látogató_.

![Váltson egy rövid nevet](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-07.png)

Ez az adatkészlet az attribútum az adattípusok közül néhány _numerikus_ vagy _logikai_, bár ezek a karakterláncok értelmezhetők **Power Query**. Az egyes oszlopfejlécekre, lásd a lenti listát a következő típusú oszlopok sorrendjének megváltoztatásához tetején attribútum ikon kiválasztása:

* **Tizedes tört szám:** Administrative_Duration; Informational_Duration; ProductRelated_Duration; BounceRates; ExitRates; PageValues; SpecialDay
* **True/False:** Hétvégi; Bevétel

![Adattípus módosítása](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-08.png)

A **bináris előrejelzési** azt fogja train model azonosítása a múltbeli megfigyelések a kimenetek címkeként logikai típusú mező szükséges. Ez az adatkészlet a _bevétel_ attribútum azt jelöli, vásárlás, és ez az attribútum egy logikai érték érhető el. Így nem szükséges a címke számított oszlop hozzáadása. Egyéb adatkészletekhez akkor előfordulhat, hogy alakítsa át meglévő címke attribútumok egy logikai oszlopot.

Válassza ki a **kész** gombra kattintva zárja be a Power Query-szerkesztő. Ez az entitások listáját jeleníti meg a _Online látogatók_ hozzáadtunk adatokat. Válassza ki **mentése** jobb felső sarokban adjon meg egy nevet az adatfolyamot, és válassza **mentése** párbeszédpanelen, a következő képen látható módon.

![Az adatfolyam mentése](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-09.png)

### <a name="refresh-the-dataflow"></a>Az adatfolyam frissítése

Egy értesítés jelenik meg az adatfolyam eredmények mentése, hogy megtörtént-e az adatfolyamot feltüntetve. Válassza ki **azonnali frissítés** az adatokat a forrás-, az adatfolyamot, hogy.

![Azonnali frissítés](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-10.png)

A jobb felső sarokban válassza a **Bezárás** lehetőséget, és várja meg, amíg az adatfolyam frissítése befejeződik.

Az adatfolyam használatával is frissítheti a **műveletek** parancsokat. Az adatfolyam időbélyegzője a frissítés befejeződött.

![Frissítés időbélyege](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-11.png)

## <a name="create-and-train-a-machine-learning-model"></a>Hozzon létre, és a egy gépi tanulási modell betanítása

Válassza ki az adatfolyamot, a frissítés befejezése után. Egy gépi tanulási modellt hozzáadásához válassza a **alkalmazása gépi Tanulási modellek** gombra a **műveletek** listában az alap entitás, amely tartalmazza a betanítási adatok és a címke adatait, és válassza ki **hozzáadása egy gépi tanulási modell**.

![Gépi tanulási modell hozzáadása](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-12.png)

A gépi tanulási modell létrehozásához az első lépés, hogy a korábbi adatok, többek között a felirat a mező, amely előre jelezni kívánt azonosításához. A modell az adatokból learning fogja létrehozni.

Az adatkészletet használunk, esetén ez az a **bevétel** mező. Válassza ki **bevétel** , a "korábbi serkenti az eredményt mező" értéket, majd **tovább**.

![Válassza ki a korábbi adatok alapján](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-13.png)

Ezután azt kell választania a gépi tanulási modellt létrehozni típusát. A Power BI elemzi a korábbi serkenti az eredményt mezőben, hogy megismerte az értékeket, és a machine learning-modellek előre jelezni, hogy a mező hozható létre a típusú javasol.

Ebben az esetben, mivel azt még előrejelzésére egy bináris eredménye, hogy egy felhasználó e e vásárolni valamit, vagy nem, válassza **bináris előrejelzési** a modell típusa, és majd kattintson a Tovább gombra.

![Bináris előrejelzési kiválasztva](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-14.png)

Ezután a Power BI előzetes keresését, az adatok nem, és javasolja, amely a modell bemenetei. Lehetősége van az adatbeviteli mezők használt modell testreszabása. Az összeválogatott adatkészlethez jelölje be az összes mezőt, válassza az entitás neve melletti jelölőnégyzetet. Válassza ki **tovább** a bemeneti adatok fogadására.

![Jelölje be a következő](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-15.png)

Az utolsó lépésben elnevezi a modellt, valamint a valódi címkéket az eredményeket az automatikusan létrehozott jelentést, amely tartalmazza a modell érvényesítése eredményeit használandó kell biztosítunk. Ezután kell, hogy a modell neve _beszerzési szándékot előrejelzési_, és a true és FALSE (hamis) címkéket, ahogy _beszerzési_ és _nem vásárlási_. Kattintson a **Mentés** gombra.

![A modell mentése](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-16.png)

A gépi tanulási modell most már készen áll a képzést. Válassza ki **frissítés most** elindításához a modell betanításához.

![Azonnali frissítés](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-17.png)

A betanítási folyamat megkezdődik, mintavétel és normalizálása előzményadatait, és az adatkészlet felosztása két új entitások az *beszerzési szándékot előrejelzési betanítási adatok* és *beszerzési szándékot előrejelzési tesztelése Adatok*.

Az adatkészlet méretétől függően a betanítási folyamat is eltarthat pár percet vagy való néhány óra múlva. A modell látható ezen a ponton a **gépi tanulási modelljeit** az adatfolyamot lapján. A _készen_ az állapot azt jelzi, hogy a modell képzéshez várólistára került, illetve képzési alatt.

![Készen áll a képzés](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-18.png)

Míg a modellnél képzés, akkor tudni megtekinteni vagy szerkeszteni az adatfolyamban. Ellenőrizheti, hogy a modell folyamatban van tanítva, és igazolt felhasználói a adatfolyamot állapotát. Ez jelenik meg a folyamatban lévő adatok frissítése a **adatfolyamok** a munkaterület fülre.

![Folyamatban](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-19.png)

Ha a modell betanítása befejeződött, az adatfolyam egy frissített frissítés idejét jeleníti meg. Ellenőrizheti, hogy a modell tanítása-e, lépjen a **gépi tanulási modelljeit** fülre az adatfolyamban. A létrehozott modell állapotúnak kell lennie mint **Trained** és a **utolsó betanított** idő most kell frissíteni.

![Utolsó tanított](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-20.png)

## <a name="review-the-model-validation-report"></a>Tekintse át a modell folyamatérvényesítési jelentés

A modell folyamatérvényesítési jelentés megtekintendő a **Machine learning-modellek, s** használatba vétele a **teljesítményjelentés megtekintése és a alkalmazni a modell** gombra a **műveletek** oszlopot a modellhez . Ez a jelentés azt ismerteti, hogyan a gépi tanulási modell valószínű végrehajtásához.

Az a **modellek teljesítményének** a jelentés, jelölje be **kulcs Véleményvezérek** a felső előrejelzőket a modell megtekintéséhez. A megtekintéséhez, hogyan az eredmény terjesztési kapcsolódó adott előjelző előrejelzőket közül választhat.

![Modellek teljesítményének](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-21.png)

Használhatja a **valószínűségi küszöbértéke** szeletelő a modellek teljesítményének oldalon vizsgálja meg a pontosság és a visszaírási modell gyakorolt hatását.

![Valószínűségi határérték](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-22.png)

A jelentés egyéb oldalain ismertetik a modell statisztikai teljesítmény-mérőszámon.

A jelentés is tartalmaz, amely leírja, hogy, hogyan könyvtárban találhatók szolgáltatások a bemeneti adatok és a modell végső használt hiperparaméterek különböző ismétlésének képzési Részletek lap.

## <a name="apply-the-model-to-a-dataflow-entity"></a>A modell vonatkozik egy adatfolyam-entitás

Válassza ki a **alkalmaz modell** gombra, és ez a modell meghívni az adatfolyamot frissítésekor a jelentés felső részén. Az a **alkalmaz** párbeszédpanelen adhatja meg, amely rendelkezik a forrásadatokat, amelyekre a modell a alkalmazni szeretné a célentitás.

![A modell alkalmazása](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-23.png)

Amikor a rendszer kéri, hogy kell **frissítése** a modell az eredmények előnézetének megtekintése az adatfolyamot.

A modell alkalmazásával hoz létre egy új entitást az utótaggal **< modell_neve > bővített** az entitást, amelyhez a modell alkalmazva lesz hozzáfűzve. Ebben az esetben az alkalmazása a modellt a **OnlineShoppers** entitás hoz létre **OnlineShoppers bővített beszerzési szándékot előrejelzési**, amely tartalmazza a modell előre jelzett kimenete.

Az előre jelzett serkenti az eredményt, valószínűségi pontszámának létrehozásához és a felső rekord-specifikus véleményvezérek az előrejelzés három oszlop egy bináris előrejelzési modell alkalmazásával ad hozzá, minden egyes előtaggal van ellátva a megadott oszlopnévvel.

![Három oszlopot az eredmény](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-24.png)

Egy ismert probléma miatt a jelentéstétellel entitás pontozott kimeneti oszlopok csak érhetők el a Power BI Desktopból. Az előzetes verzióra, ezek a szolgáltatásban, egy speciális előzetes entitást kell használnia.

Az adatfolyam frissítés befejezése után kiválaszthatja a **OnlineShoppers bővített beszerzési szándékot előrejelzési előzetes** entitás az eredmények megtekintéséhez.

![Az eredmények megtekintése](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-25.png)

## <a name="using-the-scored-output-from-the-model-in-a-power-bi-report"></a>A modell a pontozott kimenetének használata a Power BI-jelentésekben

Pontozott kimenete a teljes gépi tanulási modell használatához csatlakozhat az adatfolyamot, a Power BI desktopban, az adatfolyamok-összekötővel. A **OnlineShoppers bővített beszerzési szándékot előrejelzési** entitás már használható a modellben a Power BI-jelentések által létrehozott javaslatok révén.

## <a name="next-steps"></a>Következő lépések

Ebben az oktatóanyagban létrehozott, és a alkalmazni egy bináris előrejelzési modell, a Power bi-ban az alábbi lépések végrehajtásával:

* Hozzon létre egy adatfolyam a bemeneti adatok
* Hozzon létre, és a egy gépi tanulási modell betanítása
* Tekintse át a modell folyamatérvényesítési jelentés
* A modell vonatkozik egy adatfolyam-entitás
* A modell a pontozott kimenetének használata a Power BI-jelentésekben

A Power bi-ban a Machine Learning automatizálásával kapcsolatos további információkért lásd: [automatikus Machine Learning a Power bi-ban (előzetes verzió)](service-machine-learning-automated.md).
