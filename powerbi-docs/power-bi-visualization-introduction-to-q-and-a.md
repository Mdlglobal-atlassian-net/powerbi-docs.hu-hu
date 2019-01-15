---
title: Első lépések a Power BI Q&A-ben
description: Első lépések a Q&A kiskereskedelmi elemzési mintákon való használatában a Power BI szolgáltatásban
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/21/2018
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 87783b928fdec1cadf5318ae184858c37daa4acc
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54279251"
---
# <a name="get-started-with-power-bi-qa"></a>Első lépések a Power BI Q&A-ben

Ha válaszokat keres az adatokban, néha az a leggyorsabb megoldás, ha természetes nyelven kérdez.  Ebben az útmutatóban két különböző módszert is megtekintünk ugyanannak a vizualizációnak a létrehozására: először felépítjük egy jelentésben, majd kérdést teszünk fel a Q&A-vel. Noha a Power BI szolgáltatást fogjuk használni, a folyamat csaknem teljesen azonosan néz ki a Power BI Desktop használatával is.

A bemutatott megoldások elvégzéséhez rendelkeznie kell egy Ön által szerkeszthető jelentéssel, ezért a Power BI-ban elérhető egyik mintát fogjuk használni.

## <a name="create-a-visual-in-the-report-editor"></a>Vizualizáció létrehozása a jelentésszerkesztőben

1. Válassza a Power BI munkaterületén az **Adatok beolvasása** \> **Minták** \> **Kiskereskedelmi elemzési minta** > **Csatlakozás** menüpontot.
   
2. Az irányítópult tartalmaz egy területdiagram-csempét „Last Year Sales and This Year Sales.” (Elmúlt évi értékesítések és idei értékesítések) címmel.  Jelölje ki ezt a csempét. Ha ezt a csempét a Q&A-val hozták létre, a csempe kijelölésekor megnyílik a Q&A. Ezt a csempét azonban egy jelentésben hozták létre, ezért a jelentés megnyílik a vizualizációt tartalmazó oldalon.

    ![A Kiskereskedelmi elemzési minta irányítópultja](media/power-bi-visualization-introduction-to-q-and-a/power-bi-dashboard.png)

1. Nyissa meg a jelentést szerkesztési nézetben a **Jelentés szerkesztése** lehetőséget választva.  Ha nem tulajdonosa a jelentésnek, akkor nem nyithatja meg Szerkesztő nézetben.
   
    ![Jelentés szerkesztése gomb](media/power-bi-visualization-introduction-to-q-and-a/power-bi-edit-report.png)
4. Jelölje ki a területdiagramot, és tekintse át a beállításokat a **Mezők** ablaktáblán.  A jelentés létrehozója ennek a három értéknek a kiválasztásával építette fel a jelentést: (**Idő > FiscalMonth**, **Értékesítések > This Year Sales (Idei értékesítések)**, **Értékesítések > Last Year Sales (Múlt évi értékesítések) > Érték**), és ezeket a **Tengely** és az **Értékek** mezőterületen rendezte el.
   
    ![Vizualizációk panel](media/power-bi-visualization-introduction-to-q-and-a/gnatutorial_3-new.png)

## <a name="create-the-same-visual-with-qa"></a>Ugyanazon vizualizáció létrehozása a Q&A segítségével

Hogyan lehet létrehozni ugyanezt a vonaldiagramot a Q&A-val?

![Kérdés feltevése mező](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna.png)

1. Térjen vissza a Kiskereskedelmi elemzési minta irányítópulthoz.
2. A természetes nyelvet használva írjon be valami ehhez a kérdéshez hasonlót a kérdezési mezőbe:
   
   **hogyan alakult az idei és a múlt évi értékesítés havi bontásban, területdiagramon ábrázolva**
   
   A kérdés beírása közben a Q&A kiválasztja a legjobb vizualizációt a válasz megjelenítéséhez; a kérdés módosítása közben a vizualizáció dinamikusan változik. A Q&A segít a kérdés megfogalmazásában is javaslatokkal, automatikus kiegészítéssel és helyesírási javításokkal.
   
   Amikor befejezi a kérdés beírását, az eredmény pontosan ugyanaz a diagram lesz, amelyet a jelentésben láttunk.  De így sokkal gyorsabban létre lehet hozni!
   
   ![Példakérdés](media/power-bi-visualization-introduction-to-q-and-a/powerbi-qna-areachart.png)
3. A jelentésekkel való munkavégzéshez hasonlóan a Q&A-ben hozzáférhet a Vizualizációk, a Szűrők és a Mezők panelekhez.  Nyissa meg ezeket az ablaktáblákat a vizualizáció további felfedezéséhez és módosításához.
4. A diagram irányítópultra való kitűzéséhez válassza a gombostű ikont ![Gombostű ikon](media/power-bi-visualization-introduction-to-q-and-a/pinnooutline.png).

## <a name="next-steps"></a>Következő lépések
[Q&A a Power BI-ban](consumer/end-user-q-and-a.md)

[Megfelelő adatműködés biztosítása a Q&A és a Power BI használatánál](service-prepare-data-for-q-and-a.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

