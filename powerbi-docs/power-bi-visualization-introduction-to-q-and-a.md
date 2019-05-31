---
title: Hozzon létre egy vizualizációt a Power BI Q & A
description: Ismerje meg, hogyan hozzon létre egy vizualizációt a Q & A használata a kiskereskedelmi elemzési minta a Power BI szolgáltatásban
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/13/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 580b387f8c763b0457bd32a71bfbccd90d4040a3
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65625268"
---
# <a name="create-a-visual-with-power-bi-qa"></a>Hozzon létre egy vizualizációt a Power BI Q & A

Ha válaszokat keres az adatokban, néha az a leggyorsabb megoldás, ha természetes nyelven kérdez.  Ebben a cikkben áttekintjük, két különböző módon hozhatók létre ugyanannak a vizualizációnak: először kérdést feltenni a Q & A és a második, felépítjük egy jelentésben. A Power BI szolgáltatás használatával hozhat létre a vizualizációt a jelentésbe, de a folyamat majdnem teljesen megegyezik, a Power BI Desktop használatával.

![A Power BI kitöltött diagram](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-visual.png)

A bemutatott megoldások elvégzéséhez rendelkeznie kell egy Ön által szerkeszthető jelentéssel, ezért a Power BI-ban elérhető egyik mintát fogjuk használni.

## <a name="create-a-visual-with-qa"></a>Hozzon létre egy vizualizációt a Q & A

Hogyan szeretné meg is vagyunk létrehozása ezen a vonaldiagramon a Q & A használatára?

1. Válassza a Power BI munkaterületén az **Adatok beolvasása** \> **Minták** \> **Kiskereskedelmi elemzési minta** > **Csatlakozás** menüpontot.

1. Nyissa meg a kiskereskedelmi elemzési minta irányítópultját, és vigye a kurzort a Q & A mezőben, **tegyen fel kérdést az adataival kapcsolatban**.

    ![Vigye a kurzort a Q & A mezőben](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-cursor-in-qna-box.png)

2. A Q & A mezőben írja be ezt a kérdést például:
   
    **az év értékesítései és a múlt évi értékesítés területdiagramon ábrázolva hónap szerint**
   
    A kérdés beírása közben a Q&A kiválasztja a legjobb vizualizációt a válasz megjelenítéséhez; a kérdés módosítása közben a vizualizáció dinamikusan változik. A Q&A segít a kérdés megfogalmazásában is javaslatokkal, automatikus kiegészítéssel és helyesírási javításokkal. A Q & A kis lábjegyzetet változást javasolja: "az év értékesítései és a múlt év értékesítései szerint *idő hónap* területdiagramon ábrázolva".  

    ![A Q & A javított szöveg](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-corrected-create-filled-chart.png)

4. Válassza ki a mondat a javaslat elfogadásához. 
   
   Amikor befejezi a kérdés beírását, ez az irányítópulton látható ugyanabban a diagramban.
   
   ![A Q & A kitöltött területdiagram](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-filled-chart.png)

4. A diagram irányítópultra való kitűzéséhez válassza a gombostű ikont ![Gombostű ikon](media/power-bi-visualization-introduction-to-q-and-a/pinnooutline.png) a jobb felső sarokban.

## <a name="create-a-visual-in-the-report-editor"></a>Vizualizáció létrehozása a jelentésszerkesztőben

1. Térjen vissza a Kiskereskedelmi elemzési minta irányítópulthoz.
   
2. Az irányítópult tartalmaz az azonos területdiagram-csempét "Last Year Sales és folyó évi értékesítések."  Jelölje ki ezt a csempét. Ne válassza a csempe a Q & A. létrehozott Kiválasztva megnyílik a Q & a területen. Az eredeti területdiagram-csempét, jelentést, ezt a vizualizációt tartalmazó oldalon ekkor megnyílik a jelentés sikeresen létrehozva.

    ![A Kiskereskedelmi elemzési minta irányítópultja](media/power-bi-visualization-introduction-to-q-and-a/power-bi-dashboard.png)

1. Nyissa meg a jelentést szerkesztési nézetben a **Jelentés szerkesztése** lehetőséget választva.  Ha nem tulajdonosa a jelentésnek, akkor nem nyithatja meg Szerkesztő nézetben.
   
    ![Jelentés szerkesztése gomb](media/power-bi-visualization-introduction-to-q-and-a/power-bi-edit-report.png)
4. Jelölje ki a területdiagramot, és tekintse át a beállításokat a **Mezők** ablaktáblán.  A jelentés létrehozója ennek a diagramnak beépített válassza a három értékre (**Last Year Sales** és **This Year Sales > érték** származó a **értékesítési** táblát, és  **Pénzügyi hónap** származó a **idő** tábla) és a **tengely** és **értékek** mezőterületen.
   
    ![Vizualizációk panel](media/power-bi-visualization-introduction-to-q-and-a/gnatutorial_3-new.png)

    Láthatja, hogy azok befejeződött az ugyanabban a vizualizációban. Ezzel a módszerrel hozza létre nem túl bonyolult. De könnyebb hozza létre a Q & A volt!

## <a name="next-steps"></a>Következő lépések

- [A Q & A irányítópultokon és jelentésekben](power-bi-tutorial-q-and-a.md)  
- [A Q & A a fogyasztók számára](consumer/end-user-q-and-a.md)
- [Megfelelő adatműködés biztosítása a Q&A és a Power BI használatánál](service-prepare-data-for-q-and-a.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

