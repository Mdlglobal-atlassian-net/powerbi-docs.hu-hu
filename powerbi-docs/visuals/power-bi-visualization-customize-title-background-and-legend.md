---
title: A Power BI-vizualizációk formázásának első lépései
description: A vizualizáció címének, hátterének és jelmagyarázatának testreszabása
author: mihart
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/04/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 252e83a543640ec47fbadd00012bf1a4d8074f84
ms.sourcegitcommit: e492895259aa39960063f9b337a144a60c20125a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74831449"
---
# <a name="customize-visualization-titles-legends-and-backgrounds"></a>A vizualizáció címeinek, jelmagyarázatainak és háttereinek testreszabása

Ezen oktatóanyag segítségével elsajátíthatja a vizualizációk testre szabására szolgáló különböző módszereket. A vizualizációk testreszabására számtalan lehetőség áll rendelkezésre. Ezek megismerésére a legjobb módszer a **Formázás** panel felfedezése (válassza a festőhenger ikont). Az első lépésekhez megtételéhez ez a cikk bemutatja, hogyan szabhatja testre a vizualizáció címét, jelmagyarázatát és hátterét, valamint hogyan adhat hozzá témát.

Nem minden vizualizáció szabható testre. A részleteket a vizualizációk [teljes listájában](#visualization-types-that-you-can-customize) találja meg.


## <a name="prerequisites"></a>Előfeltételek

- A Power BI szolgáltatás vagy a Power BI Desktop

- A Kiskereskedelmi elemzési minta jelentés

## <a name="customize-visualization-titles-in-reports"></a>Vizualizáció címének testreszabása jelentésekben

Hogy követni tudja a lépéseket, jelentkezzen be a Power BI Desktop szolgáltatásba, és nyissa meg a [Kiskereskedelmi elemzési minta](../sample-datasets.md) jelentést.

> [!NOTE]
> Ha rögzít egy vizualizációt az irányítópulton, az irányítópult-csempévé válik. Maguk a csempék is testre szabhatók [új címekkel és alcímekkel és hiperhivatkozásokkal, és átméretezhetők](../service-dashboard-edit-tile.md).

1. Nyissa meg a **Kiskereskedelmi elemzési minta** **Új üzletek** oldalát.

1. Válassza a **Nyitva lévő üzletek száma nyitási hónap és üzletlánc szerint** fürtözött oszlopdiagramot.

1. A **Vizualizációk** panelen válassza a festőhenger ikont, hogy láthatóvá váljanak a formázási lehetőségek.

1. A **Cím** lehetőség kiválasztásával bontsa ki az adott szakaszt.

   ![A Formázás panel képernyőképe a festőhenger ikon kiemelésével és a Cím legördülő menüre mutató nyíllal.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-format-menu.png)

1. Állítsa át a **Cím** kapcsolót a **Be** állásba.

1. A cím módosításához írja be az *Üzletek száma nyitási hónap szerint* szöveget a **Címszöveg** mezőbe.

    ![Képernyőkép a Formázás panelről, kiemelt Cím szöveggel.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-title.png)

1. Módosítsa a **Betűszínt** fehérre, és a **Háttérszínt** kékre.    

    a. Válassza a legördülő listát, és válasszon egy színt a **Téma színei**, **Legutóbbi színek** vagy **Egyéni szín** közül.

        ![Screenshot of the Font color and Background color options.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-color.png)

    b. A színablak bezárásához válassza a legördülő menüt.


1. Növelje a betűméretet a **16 pt** értékre.

1. A diagram címének utolsó testre szabásaként igazítsa azt a vizualizáció közepére.

    ![Az Igazítás vezérlők képernyőképe a Középre beállítás kijelölésével.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-align.png)

    Az oktatóanyag ezen pontján a fürtözött oszlopdiagram címe az alábbihoz hasonló:

    ![Képernyőkép az újonnan konfigurált fürtözött oszlopdiagramról.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-table.png)

Mentse a végrehajtott módosításokat és haladjon tovább a következő részre.

Az összes módosítás visszavonásához válassza a **Visszaállítás alapértelmezettre** lehetőséget a **Cím** testreszabási panel alján.

![A Visszaállítás alapértelmezettre lehetőség képernyőképe.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-revert.png)

## <a name="customize-visualization-backgrounds"></a>Vizualizáció hátterek testreszabása

Ugyanazt a fürtözött oszlopdiagramot kiválasztva bontsa ki a **Háttér** beállításokat.

1. Állítsa **Be** értékre a **Háttér** kapcsolót.

1. Válassza a legördülő listát, és válasszon egy szürke árnyalatot.

1. Módosítsa az **Átlátszóságot** **74%** -ra.

Az oktatóanyag ezen pontján a fürtözött oszlopdiagram háttere az alábbihoz hasonló:

![A módosított háttérszínű fürtözött oszlopdiagram képernyőképe.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-background.png)

Mentse a végrehajtott módosításokat és haladjon tovább a következő részre.

Az összes módosítás visszavonásához válassza a **Visszaállítás alapértelmezettre** lehetőséget a **Háttér** testreszabási panel alján.

## <a name="customize-visualization-legends"></a>Vizualizáció jelmagyarázatának testreszabása

1. Nyissa meg az **Overview** (Áttekintés) jelentésoldalt, és válassza ki a **Total Sales Variance by FiscalMonth and District Manager** (Teljes értékesítési szórásnégyzet pénzügyi hónap és kerületi menedzser szerint) diagramot.

1. A **Vizualizáció** lapon a festőhenger ikonra kattintva nyissa meg a Formátum panelt.

1. Bontsa ki a **Jelmagyarázat** beállításait:

    ![A Jelmagyarázat kártya képernyőképe.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-legends.png)

1. Állítsa a **Jelmagyarázat** kapcsolót **Be** helyzetbe.

1. Helyezze át a jelmagyarázatot a vizualizáció bal oldalára.

1. Adjon címet a jelmagyarázathoz a **Cím** lehetőség **Bekapcsolásával**.

1. A **Jelmagyarázat neve** mezőbe írja be a *Vezető* nevet.

1. Módosítsa a **színt** feketére.

Mentse a végrehajtott módosításokat és haladjon tovább a következő részre.

Az összes módosítás visszavonásához válassza a **Visszaállítás alapértelmezettre** lehetőséget a **Jelmagyarázat** testreszabási panel alján.

## <a name="customize-colors-using-a-theme"></a>Színek testreszabása téma használatával

A jelentéstémák használatával olyan tervezési módosításokat hajthat végre az egész jelentésen, mint a vállalati színek, a változó ikonkészletek, vagy egy új alapértelmezett vizualizációs formázás. Jelentéstéma alkalmazásakor a jelentésben szereplő összes vizualizáció a kiválasztott téma színeit és formázását fogja használni.

Ha alkalmazni szeretne egy témát egy jelentésre, válassza a menüsáv **Témaváltás** lehetőségét. Válasszon témát.  Az alábbi jelentés a **Solar** témát használja.

 
![Jelentés a sárga, narancssárga és vörös színeket tartalmazó Solar témával](media/power-bi-visualization-customize-title-background-and-legend/power-bi-theme.png)

## <a name="visualization-types-that-you-can-customize"></a>Testre szabható vizualizációtípusok

Az alábbi lista a vizualizációkat és az azokhoz elérhető testreszabási lehetőségeket foglalja össze:

| Vizualizáció | Cím | Háttér | Jelmagyarázat |
|:--- |:--- |:--- |:--- |
| Terület | igen | igen |igen |
| Sáv | igen | igen |igen |
| Kártya | igen | igen |n.a. |
| Többsoros kártya | igen | igen | n.a. |
| Oszlop | igen | igen | igen |
| Kombinált | igen | igen | igen |
| Gyűrű | igen | igen | igen |
| Kartogram | igen | igen | igen |
| Tölcsér | igen | igen | n.a. |
| Kijelző | igen | igen | n.a. |
| Főbb befolyásoló | igen | igen | n.a. |
| KPI | igen | igen | n.a. |
| Vonal | igen | igen | igen |
| Térkép | igen | igen | igen |
| Mátrix | igen | igen | n.a. |
| Torta | igen | igen | igen |
| Q&A | igen | igen | n.a. |
| Pont | igen | igen | igen |
| Alakzat | igen | igen | igen |
| Szeletelő | igen | igen | n.a. |
| Táblázat | igen | igen | n.a. |
| Szövegmező | nem | igen | n.a. |
| Fatérkép | igen | igen | igen |
| Vízesés | igen | igen | igen |

## <a name="next-steps"></a>Következő lépések

- [X és Y tengely tulajdonságainak testreszabása](power-bi-visualization-customize-x-axis-and-y-axis.md)

- [Bevezetés a színformázás és tengelytulajdonságok használatába](service-getting-started-with-color-formatting-and-axis-properties.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
