---
title: Az R használata a Power Query szerkesztőben
description: Az R használata a Power BI Lekérdezésszerkesztőjében speciális elemzésekhez
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/06/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: d2ba33e18701ad147cb38072461804b4528101ea
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73877923"
---
# <a name="use-r-in-query-editor"></a>Az R használata a lekérdezésszerkesztőben

Az [**R**](https://mran.microsoft.com/documents/what-is-r) hatékony programnyelv, amelyet sok statisztikus, adatszakértő és adatelemző használ. Az **R** nyelvet a következőre használhatja a Power BI Desktop **Lekérdezésszerkesztőjében**:

* Adatmodellek előkészítése

* Jelentések létrehozása

* Végezhet adattisztítást, speciális adatátalakítást és adathalmaz-elemzést, amely magában foglalja a hiányzó adatok kiegészítését, az előrejelzéseket, a fürtözést és még sok mást.  

## <a name="install-r"></a>Az R telepítése

Az **R** ingyenesen letölthető a [Revolution Open letöltési oldaláról](https://mran.revolutionanalytics.com/download/) és a [CRAN adattárból](https://cran.r-project.org/bin/windows/base/).

### <a name="install-mice"></a>A mice telepítése

A [**mice** kódtárnak](https://www.rdocumentation.org/packages/mice/versions/3.5.0/topics/mice) telepítve kell lennie az R-környezetben. A **mice** nélkül a mintaszkript kódja nem működik megfelelően. A **mice** csomag értelmez egy metódust, amely a hiányzó adatokat kezeli.

A **mice** telepítése:

1. Indítsa el az R.exe programot (például C:\Program Files\Microsoft\R Open\R-3.5.3\bin\R.exe)  

2. Futtassa a telepítési parancsot:

   ``` 
   >  install.packages('mice') 
   ```

## <a name="use-r-in-query-editor"></a>Az R használata a lekérdezésszerkesztőben

Az **R** használatát a **Lekérdezésszerkesztőben** egy tőzsdei példa-adathalmazzal mutatjuk be, amelyet egy .csv-fájl tartalmaz, és a következő lépésekkel használható:

1. [Töltse le az **EuStockMarkets_NA.csv** fájlt](https://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/EuStockMarkets_NA.csv). Jegyezze meg, hogy hová menti.

1. Töltse be a fájlt a **Power BI Desktopba**: A **Kezdőlap** menüszalagon válassza az **Adatok lekérése > Szöveg/CSV** menüpontot.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_1.png)

1. Jelölje ki a fájlt, majd válassza a **Megnyitás** lehetőséget. A CSV adatai megjelennek a **Szöveges/CSV-fájl** párbeszédpanelen.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_2.png)

1. Az adatok a betöltésük után megjelennek a **Mezők** panelen.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_3.png)

1. A **Lekérdezésszerkesztő** megnyitásához válassza a **Kezdőlap** menüszalag **Lekérdezések szerkesztése** elemét.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_4.png)

1. Az **Átalakítás** menüszalagon válassza az **R-szkript futtatása** lehetőséget. Megnyílik az **R-szkript futtatása** szerkesztő.  

   A 15. és a 20. sorban adatok hiányoznak, ahogyan a képen nem látható további sorokban is. Az alábbi lépések bemutatják, hogyan egészíti ki az R nyelv ezeket a sorokat.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_5d.png)

1. Ehhez a példához írja be az alábbi szkriptkódot. A „&lt;Your File Path&gt;” helyére írja be az **EuStockMarkets_NA.csv** fájl helyi fájlrendszerben érvényes elérési útját, például C:/Users/Kiss Anna/Documents/Microsoft/EuStockMarkets_NA.csv

    ```r
       dataset <- read.csv(file="<Your File Path>/EuStockMarkets_NA.csv", header=TRUE, sep=",")
       library(mice)
       tempData <- mice(dataset,m=1,maxit=50,meth='pmm',seed=100)
       completedData <- complete(tempData,1)
       output <- dataset
       output$completedValues <- completedData$"SMI missing values"
    ```

    > [!NOTE]
    > Lehetséges, hogy felül kell írnia egy *output* nevű változót ahhoz, hogy az új adathalmaz megfelelően jöjjön létre a szűrők alkalmazásával.

7. Ha az **OK** gombra kattintunk, a **Lekérdezésszerkesztő** egy, az adatvédelemről szóló figyelmeztetést jelenít meg.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_6.png)
8. Ahhoz, hogy az R-szkriptek megfelelően működjenek a Power BI szolgáltatásban, minden adatforrást **nyilvánosra** kell állítania. További tudnivalókat az adatvédelmi beállításokról és azok következményeiről az [adatvédelmi szinteket](desktop-privacy-levels.md) ismertető szakaszban találhat.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_7.png)

   A **Mentés** lehetőség kiválasztása után lefut a szkript. Ekkor egy új, **completedValues** nevű oszlop jelenik meg a **Mezők** panelen. Figyelje meg, hogy van néhány hiányzó adatelem, például a 15. és 18. sorban. Azt, hogy ezeket az R hogyan kezeli, a következő szakaszban láthatjuk.

   Mindössze öt sornyi R-szkript használatát követően a **Lekérdezésszerkesztő** egy prediktív modellel kitöltötte a hiányzó értékeket.

## <a name="create-visuals-from-r-script-data"></a>Vizualizációk létrehozása az R-szkript adataiból

Most létrehozhatunk egy vizualizációt, amelyből látható, hogy az R-szkriptkód hogyan használja a **mice** kódtárat a hiányzó adatok kiegészítésére. Ezt az alábbi kép illusztrálja:

![](media/desktop-r-in-query-editor/r-in-query-editor_8a.png)

Az összes elkészült vizualizációt mentheti egy **Power BI Desktop** .pbix-fájlba, az adatmodellt és annak R-szkriptjeit pedig felhasználhatja a Power BI szolgáltatásban.

> [!NOTE]
> [Letölthet egy .pbix-fájlt](https://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/Complete%20Values%20with%20R%20in%20PQ.pbix), amelyen ezeket a lépéseket már végrehajtották.

Miután feltöltötte a .pbix-fájlt a Power BI szolgáltatásba, további lépésekkel kell engedélyeznie a szolgáltatásnak az adatok és a vizualizációk frissítését:  

* **Adathalmaz ütemezett frissítésének engedélyezése** – az R-szkripttel rendelkező adathalmazt tartalmazó munkafüzet ütemezett frissítésének engedélyezéséhez tekintse meg az [ütemezett frissítés konfigurálását](refresh-scheduled-refresh.md) ismertető részt, amely a **Privát átjáróról** is tartalmaz információkat.

* **A privát átjáró telepítése** – azon a gépen, amelyen a fájl és az **R** található, telepítve kell lennie egy **privát átjárónak**. A Power BI szolgáltatás hozzáfér ehhez a munkafüzethez, és újrarendereli a módosított vizualizációkat. További információ: [Privát átjáró telepítése és konfigurálása](service-gateway-personal-mode.md).

## <a name="limitations"></a>Korlátozások

A **Lekérdezésszerkesztőben** létrehozott R-szkripteket tartalmazó lekérdezések némiképp korlátozottak:

* Minden R-adatforrást **nyilvánosra** kell beállítani. A **Lekérdezésszerkesztőben** készült lekérdezés minden további lépésének is nyilvánosnak kell lennie. Az adatforrás-beállítások eléréshez a **Power BI Desktopban** válassza a **Fájl > Lehetőségek és beállítások > Adatforrás-beállítások** elemet.

  ![](media/desktop-r-in-query-editor/r-in-query-editor_9.png)

  Az **Adatforrás beállításai** párbeszédpanelen jelölje ki az adatforrás(oka)t, majd válassza az **Engedélyek szerkesztése...** lehetőséget.  Az **Adatvédelmi szintet** állítsa be **Nyilvánosra**.

  ![](media/desktop-r-in-query-editor/r-in-query-editor_10.png)    
* Az R-vizualizációk vagy adathalmazok ütemezett frissítésének engedélyezéséhez engedélyeznie kell az **Ütemezett frissítést**, és rendelkeznie kell a munkafüzetet és az **R-t** tartalmazó számítógépre telepített **Privát átjáróval**. Az ezekről szóló információkért tekintse meg a cikk korábbi szakaszait. A vonatkozó részekben található hivatkozásokkal további információhoz juthat.

Az R-rel és egyéni lekérdezésekkel sok mindent tehet, például felderítheti adatait és olyanná alakíthatja azokat, amilyen módon meg szeretné őket jeleníteni.

## <a name="next-steps"></a>Következő lépések

* [Az R bemutatása](https://mran.microsoft.com/documents/what-is-r) 

* [R-szkriptek futtatása a Power BI Desktopban](desktop-r-scripts.md) 

* [Külső R IDE környezet használata a Power BI-jal](desktop-r-ide.md) 

* [R-csomagok a Power BI szolgáltatásban](service-r-packages-support.md)
