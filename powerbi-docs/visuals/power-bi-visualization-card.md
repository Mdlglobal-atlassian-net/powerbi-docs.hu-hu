---
title: Kártyavizualizációk (nagy méretű numerikus csempék)
description: Kártyavizualizáció létrehozása a Power BI-ban
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/05/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: c898c31e87c4532b3e99c8d4ee88f34d18e2fa34
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/06/2020
ms.locfileid: "82865483"
---
# <a name="create-card-visualizations"></a>Kártyavizualizációk létrehozása

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Néha csupán egyetlen szám a legfontosabb, amit nyomon szeretne követni a Power BI-irányítópulton vagy -jelentésben, például az összesített értékesítés, az egy évre vetített piaci részesedés, vagy a lehetőségek száma összesen. Az ilyen típusú vizualizációkat *Kártyáknak* nevezzük. Csakúgy, mint szinte minden natív Power BI-vizualizáció, a Kártyák is a jelentésszerkesztővel vagy a Q&A-val hozhatók létre.

![kártyavizualizáció](media/power-bi-visualization-card/pbi-opptuntiescard.png)

> [!NOTE]
> A jelentés egy Power BI-munkatárssal való megosztásához mindkettőjüknek Power BI Pro-licenccel kell rendelkezniük, vagy a jelentésnek egy Premium kapacitásban kell lennie.

## <a name="prerequisite"></a>Előfeltétel

Ez az oktatóanyag a [Kiskereskedelmi elemzési minta PBIX-fájlt](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) használja

1. A menüsor bal felső részén válassza a **Fájl** \> **Megnyitás** lehetőséget
   
2. Keresse meg a **Kiskereskedelmi elemzési minta PBIX-fájlt**

1. Nyissa meg a **Kiskereskedelmi elemzési minta PBIX-fájlt** jelentésnézetben ![A jelentésnézet ikon képernyőképe.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Kiválasztás ![A sárga fül képernyőképe.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) új oldal hozzáadásához.

## <a name="option-1-create-a-card-using-the-report-editor"></a>1\. lehetőség Kártyák létrehozása a jelentésszerkesztővel

A kártya létrehozásának első módszere a jelentésszerkesztő használata a Power BI Desktopban.

1. Kezdjen egy üres jelentésoldalon, és válassza a **Store** \> **Open store count** (Üzlet > Nyitva lévő üzletek száma) mezőt.

    A Power BI létrehoz egy oszlopdiagramot ezzel az egy számmal.

   ![példa számcsempe-diagram](media/power-bi-visualization-card/pbi-overview-chart.png)

2. A Vizualizációk panelen válassza a kártya ikont.

   ![példa számcsempe-diagram](media/power-bi-visualization-card/power-bi-card-visualization.png)

Ezzel sikeresen létrehozott egy kártyát a jelentésszerkesztővel. A következőkben egy másik lehetőséget mutatunk be a kártya létrehozására a Q&A kérdésmezője használatával.

## <a name="option-2-create-a-card-from-the-qa-question-box"></a>2\. lehetőség Kártya létrehozása a Q&A kérdésmezőben
Másik lehetőségként a Q&A kérdésmezője is használható kártya létrehozására. A Q&A kérdésmező a Power BI Desktop jelentés nézetében érhető el.

1. Kezdje a műveletet egy üres jelentésoldalon

1. Az ablak felső részén válassza a **Kérdés feltevése** ikon. 

    A Power BI létrehoz egy kártyát és egy mezőt a kérdéshez. 

   ![a kérdés feltevése ikont helye](media/power-bi-visualization-card/power-bi-q-and-a-overview.png)

2. A kérdésmezőbe beírhatja például a „Tina összes értékesítése” szöveget.

    A kérdésmező javaslatokkal és újrafogalmazásokkal segíti, és végül megjeleníti az összesített számot.  

   ![példa a kérdésmezőben](media/power-bi-visualization-card/power-bi-q-and-a-box.png)

   ![példakártya a kérdésfeltevéses módszerrel](media/power-bi-visualization-card/power-bi-q-and-a-card.png)

Ezzel sikeresen létrehozott egy kártyát a Q&A kérdésmezőjével. A további lépések a kártya igény szerinti formázását ismertetik.

## <a name="format-a-card"></a>Kártya formázása
A címkék, szöveg, színét és egyebek módosításához több lehetőség áll rendelkezésre. A tanulás legjobb módja, ha létrehoz egy kártyát, és azután részletesebben is megismerkedik a Formázás ablaktábla lehetőségeivel. Bemutatunk néhányat az elérhető formázási lehetőségek közül. 

A Formázás panel a jelentések kártyáinak használatakor érhető el. 

1. Kezdő lépésként nyissa meg a Formázás ablaktáblát a festőhenger ikon kiválasztásával. 

    ![kártya, amelyen a festőhenger kiemelve látható](media/power-bi-visualization-card/power-bi-format-card-2.png)

2. A kártya kijelölése után bontsa ki az **Adatfelirat** elemet, majd módosítsa a színt, a méretet és a betűtípust. Ha több ezer üzlettel rendelkezik, akkor a **Megjelenítési egységek** használatával ezresével jelenítheti meg az üzleteket, és beállíthatja a tizedesjegyeket is. Például 125,8 e a 125 832,00 helyett.

    ![példakártya adatformázással](media/power-bi-visualization-card/power-bi-card-format-2.png)

3.  Bontsa ki a **Kategóriacímke** elemet, majd módosítsa a színt és a méretet.

    ![példakártya kategóriával](media/power-bi-visualization-card/power-bi-card-format-category.png)

4. Bontsa ki a **Háttér** elemet, és a csúszkát tolja „On” (Be) állásba.  Mostantól módosíthatja a háttérszínt és az átlátszóságot.

    ![csúszka ON (BE) állásban](media/power-bi-visualization-card/power-bi-format-color-2.png)

5. Folytassa is a formázási beállítások felfedezését, amíg a kártya pontosan olyan nem lesz, amilyennek kívánja. 

## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás
Ha a kereső mező nem látható, forduljon a rendszerszintű vagy a bérlői rendszergazdához.    

## <a name="next-steps"></a>Következő lépések
[Kombinált diagramok a Power BI-ban](power-bi-visualization-combo-chart.md)

[Vizualizációtípusok a Power BI-ban](power-bi-visualization-types-for-reports-and-q-and-a.md)
