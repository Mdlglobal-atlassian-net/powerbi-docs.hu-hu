---
title: Az R használata a Power Query szerkesztőben
description: Az R használata a Power BI Lekérdezésszerkesztőjében speciális elemzésekhez
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 10431709fd77089fb98524b7060711ce6acc76fd
ms.sourcegitcommit: 72c9d9ec26e17e94fccb9c5a24301028cebcdeb5
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/07/2018
ms.locfileid: "53026120"
---
# <a name="using-r-in-query-editor"></a>Az R használata a Lekérdezésszerkesztőben
A Power BI Desktop **Lekérdezésszerkesztőjében** használhatja a statisztikusok, adatszakértők és adatelemzők által széles körben használt **R** programozási nyelvet. Az R integrációja a **Lekérdezésszerkesztőbe** lehetővé teszi adattisztítás elvégzését az R használatával, és összetett adatátalakítási és elemzési műveletek elvégzését adatkészletekben, beleértve többek között a hiányos adatok kiegészítését, az előrejelzéseket és a fürtözést. Az **R** egy sokoldalú nyelv, amely a **Lekérdezésszerkesztőben** is használható adatmodellek előkészítéséhez és jelentések létrehozásához.

## <a name="installing-r"></a>Az R telepítése
Ahhoz, hogy az **R**-t a Power BI Desktop **Lekérdezésszerkesztőjében** használhassa, telepítenie kell az **R** nyelvet a helyi számítógépre. Az **R**-t számos helyről ingyen letöltheti és telepítheti, például a [Revolution Open letöltőoldalról](https://mran.revolutionanalytics.com/download/) vagy a [CRAN tárból](https://cran.r-project.org/bin/windows/base/).

## <a name="using-r-in-query-editor"></a>Az R használata a lekérdezésszerkesztőben
Az **R** **Lekérdezésszerkesztőben** való használatának bemutatásához a tőzsdei adatkészletből használunk egy példát, amely egy .CSV-fájlon alapul, amelyet [innen tölthet le](http://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/EuStockMarkets_NA.csv). A példa lépései a következők:

1. Első lépésként töltse be az adatokat a **Power BI Desktopba**. Ebben a példában töltse be az *EuStockMarkets_NA.csv* fájlt, és a **Power BI Desktop** **Kezdőlap** menüszalagján válassza az **Adatok beolvasása > CSV** lehetőséget.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_1.png)
2. Válassza ki a fájlt, és kattintson a **Megnyitás** elemre, ekkor a CSV megjelenik a **CSV-fájl** párbeszédpanelen.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_2.png)
3. Miután az adatok betöltődtek, a Power BI Desktop **Mezők** ablaktábláján jelennek meg.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_3.png)
4. A **Power BI Desktop** **Kezdőlapján** válassza a **Lekérdezések szerkesztése** lehetőséget a **Lekérdezésszerkesztő** megnyitásához.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_4.png)
5. Az **Átalakítás** lapon válassza az **R-szkript futtatása** lehetőséget, ekkor megjelenik az **R-szkript futtatása** szerkesztő (a következő lépésben látható). Figyelje meg, hogy a 15. és a 20. sorból adatok hiányoznak, ahogy egyéb, az alábbi képen nem látható sorokból is. Az alábbi lépések bemutatják, hogyan egészítheti és (egészíti) ki az R nyelv ezeket a sorokat.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_5d.png)
6. Ebben a példában az alábbi szkriptkódot adjuk meg:

       library(mice)
       tempData <- mice(dataset,m=1,maxit=50,meth='pmm',seed=100)
       completedData <- complete(tempData,1)
       output <- dataset
       output$completedValues <- completedData$"SMI missing values"

   > [!NOTE]
   > A fenti szkriptkód megfelelő működéséhez rendelkeznie kell az R-környezetben telepített *mice* kódtárral. A mice telepítéséhez futtassa a következő parancsot az R-környezetben: |      > install.packages('mice')
   > 
   > 

   Az **R-szkript futtatása** párbeszédpanelre helyezve a kód az alábbi módon néz ki:

   ![](media/desktop-r-in-query-editor/r-in-query-editor_5b.png)
7. Ha az **OK** gombra kattintunk, a **Lekérdezésszerkesztő** egy, az adatvédelemről szóló figyelmeztetést jelenít meg.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_6.png)
8. Ahhoz, hogy az R-szkriptek megfelelően működjenek a Power BI szolgáltatásban, minden adatforrást *nyilvánosra* kell állítani. További tudnivalókat az adatvédelmi beállításokról és azok következményeiről az [adatvédelmi szinteket](desktop-privacy-levels.md) ismertető szakaszban találhat.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_7.png)

   Ekkor egy új, *completedValues* nevű oszlop jelenik meg a **Mezők** panelen. Figyelje meg, hogy van néhány hiányzó adatelem, például a 15. és 18. sorban. Azt, hogy ezeket az R hogyan kezeli, a következő szakaszban láthatjuk.


Mindössze öt sornyi R-szkript használatát követően a **Lekérdezésszerkesztő** egy prediktív modellel kitöltötte a hiányzó értékeket.

## <a name="creating-visuals-from-r-script-data"></a>Vizualizációk létrehozása az R-szkript adataiból
Most létrehozhatunk egy vizualizációt, amelyből látható, hogy az R-szkriptkód hogyan használja a *mice* kódtárat a hiányzó adatok kiegészítésére. Ezt az alábbi kép illusztrálja:

![](media/desktop-r-in-query-editor/r-in-query-editor_8a.png)

Miután a vizualizáció elkészült, bármely egyéb vizualizációval együtt amelyet a **Power BI Desktop** használatával szeretnénk létrehozni, mentheti a **Power BI Desktop-fájlt** (.pbix-fájlként), és utána a Power BI szolgáltatásban használhatja az adatmodellt, beleértve a részét képező R-szkripteket.

> [!NOTE]
> Szeretne egy teljes .pbix-fájlt látni úgy, hogy ezek a lépések már be vannak fejezve? Szerencséje van – [innen](http://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/Complete%20Values%20with%20R%20in%20PQ.pbix) letöltheti az ebben a példában használt, teljes **Power BI Desktop-fájlt**.

Miután feltöltötte a .pbix-fájlt a Power BI szolgáltatásba, néhány további lépés szükséges az adatfrissítés engedélyezéséhez (a szolgáltatásban) és annak engedélyezéséhez, hogy a vizualizációk frissíthetők legyenek a szolgáltatásban (az adatoknak hozzáféréssel kell rendelkezniük az R-hez, hogy a vizualizációk frissülhessenek). A további lépések a következők:

* **Adatkészlet ütemezett frissítésének engedélyezése** – az R-szkripttel rendelkező adatkészletet tartalmazó munkafüzet ütemezett frissítésének engedélyezéséhez tekintse meg az [ütemezett frissítés konfigurálását](refresh-scheduled-refresh.md) ismertető részt, amely a **Privát átjáróról** is tartalmaz információkat.
* **Privát átjáró telepítése** – szüksége van egy arra a számítógépre telepített **Privát átjáróra**, amelyen a fájl található és amelyre az R telepítve van. A Power BI szolgáltatásnak hozzáféréssel kell rendelkeznie ahhoz a munkafüzethez, és újra kell renderelnie a frissített vizualizációkat. További információt a [Privát átjáró telepítésével és konfigurálásával](service-gateway-personal-mode.md) foglalkozó témakörben talál.

## <a name="limitations"></a>Korlátozások
A **Lekérdezésszerkesztőben** létrehozott R-szkripteket tartalmazó lekérdezések némiképp korlátozottak:

* Minden R-adatforrás beállításait *Nyilvánosra* kell állítani, és a **Lekérdezésszerkesztőben** létrehozott lekérdezés egyéb lépéseinek is nyilvánosnak kell lenniük. Az adatforrás-beállítások eléréshez a **Power BI Desktopban** válassza a **Fájl > Lehetőségek és beállítások > Adatforrás-beállítások** elemet.

  ![](media/desktop-r-in-query-editor/r-in-query-editor_9.png)

  Az **Adatforrás-beállítások** párbeszédpanelen válassza ki az adatforrásokat, majd kattintson az **Engedélyek szerkesztése** elemre, és győződjön meg arról, hogy az **Adatvédelem szintje** *Nyilvános* beállítású.

  ![](media/desktop-r-in-query-editor/r-in-query-editor_10.png)    
* Az R-vizualizációk vagy adatkészletek ütemezett frissítésének engedélyezéséhez engedélyeznie kell az **Ütemezett frissítést**, és rendelkeznie kell a munkafüzetet és az R-környezetet tároló számítógépre telepített **Privát átjáróval**. Az ezekről szóló információkért tekintse meg a cikk korábbi szakaszait. A vonatkozó részekben található hivatkozásokkal további információhoz juthat.

Az R-rel és egyéni lekérdezésekkel sok mindent tehet, például felderítheti adatait és olyanná alakíthatja azokat, amilyen módon meg szeretné őket jeleníteni.

