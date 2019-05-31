---
title: 'Informatikaköltség-elemzési minta a Power BI-hoz: Bemutató megtekintése'
description: 'Informatikaköltség-elemzési minta a Power BI-hoz: Bemutató megtekintése'
author: maggiesMSFT
manager: kfile
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/23/2018
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 0a71a0e0fe7af3c074c94ab26083839ff114f815
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61232788"
---
# <a name="it-spend-analysis-sample-for-power-bi-take-a-tour"></a>Informatikaköltség-elemzési minta a Power BI-hoz: Bemutató megtekintése

## <a name="overview-of-the-it-spend-analysis-sample"></a>Informatikaköltség-elemzési minta: áttekintés
Az Informatikaköltség-elemzés [tartalomcsomag](service-organizational-content-pack-introduction.md) (irányítópult, jelentés és adatkészlet) egy informatikai osztály költségeinek terv- és tényadatait elemzi. Az összevetés segít megérteni, hogy milyen pontosan tervezte a cég az idei évet, és feltárhatóvá teszi a tervtől jelentősen eltérő területeket. A példában szereplő cég egy éves tervezési cikluson halad végig, és minden negyedévben friss becslést készít (Latest Estimate - LE) a pénzügyi év informatikai költségeiben bekövetkezett változások elemzéséhez.

![](media/sample-it-spend/it1.png)

Ez a minta abba a sorozatba tartozik, amely a Power BI üzleti jellegű adatokkal, jelentésekkel, és irányítópultokkal történő használatát mutatja be. Az adatok az obviEnce-től (<http://obvience.com/>) származó valós, de anonimizált adatok.

## <a name="prerequisites"></a>Előfeltételek

 Használat előtt a mintát [tartalomcsomagként](https://docs.microsoft.com/power-bi/sample-it-spend#get-the-content-pack-for-this-sample), [.pbix-fájlként](http://download.microsoft.com/download/E/9/8/E98CEB6D-CEBB-41CF-BA2B-1A1D61B27D87/IT%20Spend%20Analysis%20Sample%20PBIX.pbix) vagy [Excel-munkafüzetként](http://go.microsoft.com/fwlink/?LinkId=529783) le kell töltenie.

### <a name="get-the-content-pack-for-this-sample"></a>Tartalomcsomag letöltése ehhez a mintához

1. Nyissa meg a Power BI szolgáltatást (app.powerbi.com), és jelentkezzen be.
2. A bal alsó sarokban válassza az **Adatok lekérése** lehetőséget.
   
    ![](media/sample-datasets/power-bi-get-data.png)
3. Ekkor megjelenik az Adatok lekérése lap. Itt kattintson a **Minták** ikonra.
   
   ![](media/sample-datasets/power-bi-samples-icon.png)
4. Válassza a **Informatikaköltség-elemzési mintát**, majd a **Csatlakozás** lehetőséget.  
  
   ![Adatok beolvasása](media/sample-it-spend/it-connect.png)
   
5. A Power BI importálja a tartalomcsomagot, és egy új irányítópultot, jelentést és adatkészletet ad hozzá az aktuális munkaterülethez. Az új tartalmakat sárga csillag jelöli. 
   
   ![Csillag](media/sample-it-spend/it-asterisk.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>.pbix-fájl letöltése ehhez a mintához

Lehetőség van a mintát .pbix-fájlként is letölteni, amelyet a Power BI Desktoppal való használatra terveztek. 

 * [Informatikaköltség-elemzési minta](http://download.microsoft.com/download/E/9/8/E98CEB6D-CEBB-41CF-BA2B-1A1D61B27D87/IT%20Spend%20Analysis%20Sample%20PBIX.pbix)

### <a name="get-the-excel-workbook-for-this-sample"></a>Excel-munkafüzet letöltése ehhez a mintához
Letöltheti [kizárólag a minta adatkészletét (Excel-munkafüzetét) is](http://go.microsoft.com/fwlink/?LinkId=529783). A munkafüzet megtekinthető és módosítható Power View-lapokat tartalmaz. A nyers adatokat a **Power Pivot > Kezelés** lehetőségre kattintva nézheti meg.


## <a name="the-it-spend-analysis-sample-dashboard"></a>Az Informatikaköltség-elemzés minta irányítópultja
Az irányítópulton látható két számcsempe, a **Var Plan %** (Tervtől való százalékos eltérés) és a **Variance Latest Estimate % Quarter 3** (A 3. negyedévi friss becsléstől való százalékos eltérés) bemutatja a cég általános teljesítményét a tervhez és a friss negyedévi becsléshez képest (LE3 = 3. negyedévi friss becslés). A tervtől való átlagos eltérés körülbelül 6 %. Tárja fel az eltérés okát – mikor, hol, és mely kategóriában jelentkezik?

## <a name="ytd-it-spend-trend-analysis-page"></a>„Idei informatikaköltségek trendanalízise” oldal
Ha a **Var Plan % by Sales Region** (Tervtől való százalékos eltérés értékesítési régiók szerint) csempére kattint, megnyílik az Informatikaköltség-elemzés mintajelentés „informatikaköltségek trendanalízise ” oldala. Egy pillantással felmérheti, hogy az USA és Európa területén pozitív, Kanadában, Latin-Amerikában és Ausztráliában negatív az eltérés. Míg az USA területén körülbelül +6 % az eltérés a legfrissebb becsléshez képest, Ausztráliában ez az érték körülbelül -7 %.

![](media/sample-it-spend/it2.png)

De ha csupán ezt az egy diagramot vizsgálja, téves következtetésre juthat. A nagyobb összefüggések megértéséhez meg kell vizsgálnia a dollárban kifejezett tényleges összegeket is.

1. A „Tervtől való százalékos eltérés régiók szerint” diagramon jelölje ki **Ausztráliát és Új-Zélandot**, és tekintse meg a „Tervtől való eltérés informatikai terület szerint” diagramot.

   ![](media/sample-it-spend/it3.png)
2. Most válassza ki az **USA** elemet. Így már világosabb a kép – a teljes költség Ausztráliára eső része elenyésző az USA-hoz képest.

    Mi a teendő most, hogy leszűkítette az elemzést az USA területére? Vizsgálja meg, hogy az USA területén belül melyik kategória okozza az eltérést.

## <a name="ask-questions-of-the-data"></a>Kérdések az adatokról
1. A felső navigációs sávon, az **Informatikaköltség-elemzés minta** lehetőségre kattintva visszatérhet az irányítópultokhoz.
2. A kérdés mezőbe írja be a következőt: „show IT areas, var plan % and var le3 % bar chart” (mutassa az informatikai területeket, a tervtől való százalékos eltérést, és a le3 értéktől való százalékos eltérést).

   ![](media/sample-it-spend/it4.png)

   Az első informatikai területen (**Infrastruktúra**), igen jelentős a százalékos különbség az eredeti tervhez és a legfrissebb becsléshez képest mért eltérés között.

## <a name="ytd-spend-by-cost-elements-page"></a>„Idei költségelemek szerinti ráfordítás” oldal
Térjen vissza az irányítópulthoz, és tekintse meg a **Var Plan %, Var LE3%** (Tervtől való százalékos eltérés és a LE3 értéktől való százalékos eltérés) csempét.

![](media/sample-it-spend/it5.png)

Az infrastruktúra területe a tervtől való hatalmas pozitív eltéréssel tűnik ki.

1. Ha erre a csempére kattint, megnyílik az Informatikaköltség-elemzés minta jelentésének „Idei költségelemek szerinti ráfordítás” oldala.
2. Kattintson az **Infrastruktúra** sávra a bal alsó „Var Plan % and Var LE3 % by IT Area” (tervtől való százalékos eltérés, és a LE3 értéktől való százalékos eltérés informatikai területek szerint) diagramon, és tekintse meg a balra található „Var Plan % by Sales Region" (tervtől való százalékos eltérés értékesítési régiók szerint) diagramot.

    ![](media/sample-it-spend/it6.png)
3. A jelentősen eltérő költségelem megtalálásához kattintson a szeletelőben az egyes költségelemcsoportokra.
4. A legnagyobb eltérést mutató részterület megtalálásához az **Egyéb** elem kijelölése mellett kattintson az informatikai terület **Infrastruktúra** elemére, és kattintson az „Informatikai részterületek” szeletelő elemeire.  

   A **Hálózatkezelés** részterületen jelentős eltérés mutatkozik.

   Úgy látszik, a cég juttatásként telefonos szolgáltatásokat osztott ki az alkalmazottainak, de ez nem szerepelt a tervben.

## <a name="plan-variance-analysis-page"></a>„Tervtől való eltérés elemzése” oldal
Maradjon a jelentésben, és kattintson az alul látható „Plan Variance Analysis” (Tervtől való eltérés elemzése) lapra, amely megnyitja a jelentés 3.oldalát.

Ha a bal oldali „Var Plan, and Var Plan % by Business Area” (Tervtől való eltérés és Tervtől való százalékos eltérés üzleti területek szerint) összetett diagramon az Infrastruktúra oszlopra kattint, az oldal többi részén kiemelheti az infrastruktúra értékeit.

![](media/sample-it-spend/it7.png)

A „Var plan% by Month and Business Area” (Tervtől való százalékos eltérés hónapok és üzleti területek szerint) diagramon megfigyelheti, hogy az infrastruktúránál február körül pozitív eltérés jelent meg, amelynek mértéke azóta is növekszik. Szintén figyelje meg az infrastruktúra tervtől való eltérését országok szerint, és vesse ezt össze az összes üzleti területre vonatkozó értékkel. A jobb oldali „Informatikai terület” és „Informatikai részterület” szeletelők használatával kiemelés helyett szűrheti az oldal többi részén látható értékeket. Az adatok másféle elemzéséhez kattintson a jobb oldalon látható különböző informatikai területekre. Az informatikai részterületek kijelölésével a részterületek szintjén tekintheti meg az eltéréseket.

## <a name="edit-the-report"></a>A jelentés szerkesztése
Kattintson a **Jelentés szerkesztése** elemre a bal felső sarokban, és nyissa meg a Szerkesztési nézetet.

* Áttekintheti a lapok felépítését – a mezőket az egyes diagramokban és a szűrőket az oldalakon
* Lapokat és diagramokat vehet fel ugyanazon adatok alapján
* Módosíthatja az egyes diagramok vizualizációjának típusát
* Rögzítheti a diagramokat az irányítópulton

Ebben a környezetben nyugodtan kísérletezhet. Mindig hozhat olyan döntést, hogy nem menti a módosításokat. De ha mégis menteni szeretné őket, bármikor lekérheti a minta új másolatát az Adatok lekérése lehetőséggel.

## <a name="next-steps-connect-to-your-data"></a>Következő lépések: Csatlakozás az adatokhoz
Reméljük, hogy ez a bemutató segített megérteni, hogy miképpen elemezheti az informatikai költségek adatait a Power BI irányítópultok, a Q&A és a jelentések használatával. Most Önön a sor – kapcsolódjon a saját adataihoz. A Power BI használatával számos különböző adatforráshoz kapcsolódhat. További tudnivalók a [Power BI használatának első lépéseiről](service-get-started.md).
