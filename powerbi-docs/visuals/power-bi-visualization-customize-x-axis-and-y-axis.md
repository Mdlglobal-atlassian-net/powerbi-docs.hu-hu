---
title: X és Y tengely tulajdonságainak testreszabása
description: X és Y tengely tulajdonságainak testreszabása
author: mihart
ms.reviewer: ''
featuredvideoid: 9DeAKM4SNJM
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/3/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 830fbe945405f8ad7aadd7ceac9fb1967daad22b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "75758106"
---
# <a name="customize-x-axis-and-y-axis-properties"></a>X és Y tengely tulajdonságainak testreszabása

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Az oktatóanyag segítségével elsajátíthatja a vizualizációk X és Y tengelyének testreszabását lehetővé tevő módok végrehajtását. Nem minden vizualizációnak vannak tengelyei. A tortadiagramoknak például nincs tengelyük. A testreszabási lehetőségek pedig vizualizációnként változnak. Több beállítási lehetőség van annál, amennyit egyetlen cikkben ismertetni lehetne, így csak a leggyakrabban használt testreszabási lehetőségeket fogjuk átvenni, hogy Ön elsajátíthassa a vizualizációk **Formázás** paneljének használatát a Power BI-jelentések vásznán.  

Figyelje meg, ahogy Amanda testre szabja az X és Y tengelyt. Különböző módszereket mutat be az összefűzés szabályozására a részletesség növelése és csökkentése során.

> [!NOTE]
> A videó készítése során a Power BI egy régebbi verzióját használták.

<iframe width="560" height="315" src="https://www.youtube.com/embed/9DeAKM4SNJM" frameborder="0" allowfullscreen></iframe>

## <a name="prerequisites"></a>Előfeltételek

- Power BI Desktop

- [Kiskereskedelmi elemzési minta ](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)


## <a name="add-a-new-visualization"></a>Új vizualizáció hozzáadása

A vizualizációt először létre kell hoznia, hogy testre szabhassa.

1. A Power BI Desktopban nyissa meg a Kiskereskedelmi elemzési mintát.  

2. Kattintson alul a sárga plusz ikonra egy új oldal hozzáadásához. 

    ![sárga pluszjel](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-new-page-icon.png)

1. A **Vizualizációk** panelen válassza a halmozott oszlopdiagram ikont. Ezzel megjelenik egy üres sablon a jelentés vásznán.

    ![A Vizualizációk panel és egy üres halmozott oszlopdiagram képernyőképe](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-column-chart.png)

1. Az X tengely értékeinek beállításához válassza a **Mezők** panel **Idő** > **FiscalMonth** elemét.

1. Az Y tengely értékeinek beállításához a **Mezők** panelről válassza az **Értékesítések** > **múlt évi értékesítések** és az **Értékesítések** > **idei értékesítések** > **Érték** elemet.

    ![Az adatokkal feltöltött halmozott oszlopdiagram képernyőképe.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-build-visual.png)

    Most már testre szabhatja az X tengelyt. A Power BI szinte korlátlan lehetőségeket biztosít a vizualizációk formázásához. 

## <a name="customize-the-x-axis"></a>Az X tengely testreszabása
Az X tengely számos jellemzője testre szabható. Hozzáadhat és módosíthat adatcímkéket és az X tengely címét. A kategóriáknál módosítható a sávok, oszlopok, vonalak és területek szélessége, mérete és kitöltése, az értékeknél pedig módosíthatók a megjelenítési egységek, a tizedesjegyek és a rácsvonalak. Az alábbi példa egy oszlopdiagram testreszabását mutatja be. Hozzáadunk néhány testreszabási elemet, hogy megismerkedhessen pár lehetőséggel, a többit pedig önállóan fedezhesse fel.

### <a name="customize-the-x-axis-labels"></a>Az X tengely címkéinek testreszabása
Az X tengely címkéi a diagramban az oszlopok alatt jelennek meg. Jelenleg halványszürkék, kicsik és nehezen olvashatók. Ezt fogjuk most módosítani.

1. A **Vizualizációk** panelen válassza a **Formázás** (festőhenger ikon ![A festőhenger ikon képernyőképe.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-paintroller-icon.png) ) lehetőséget a testreszabási beállítások megjelenítéséhez.

2. Bontsa ki az X tengely beállításait.

   ![Az X tengely beállításainak képernyőképe.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-axis-x.png)

3. Állítsa az **X tengely** csúszkáját **Be** helyzetbe.

    ![A Be állású csúszka képernyőképe.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-slider-on.png)

    Az X tengelyt akkor lehet érdemes **Ki** helyzetbe kapcsolni, ha a vizualizáció címkék nélkül is magától értetődő, vagy ha a jelentésoldal zsúfolt, és helyet szeretne rajta felszabadítani, hogy több adatot lehessen megjeleníteni.

4. Formázza a szöveg színét, méretét és betűtípusát:

    - **Szín**: Válassza a feketét

    - **Szövegméret**: Adja meg a *14* értéket

    - **Betűtípus**: Válassza az **Arial Black** típust

    - **Belső kitöltés**: Adjon meg *40%* -ot

        ![Képernyőkép döntött címkékkel](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-formatting-x.png)
    
5. Tegyük fel, hogy változtatni szeretne az X tengely feliratainak döntött megjelenítésén. Erre több lehetősége is van. 
    - Csökkentse a szöveg méretét 14-esnél kisebbre.
    - Növelje a vizualizáció méretét. 
    - Jelenítsen meg kevesebb oszlopot, és adjon hozzá egy görgetősávot a **Minimális kategóriaszélesség** növelésével. 
    
    Itt a második lehetőséget választottuk, és az egyik méretezési csúszka elhúzásával növeltük a vizualizáció szélességét. Most már elfér rajta a 14 pontos szöveg, amit így nem kell döntve vagy görgetősávval megjeleníteni. 

   ![Diagram és formázási panel vízszintes címkékkel](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-stretch.png)

### <a name="customize-the-x-axis-title"></a>Az X tengely címének testreszabása
Ha az X tengely címe **be** van kapcsolva, akkor a cím az X tengely címkéi alatt jelenik meg. 

1. Először is kapcsolja **be** az X tengely címkéjét.  

    ![Cím csúszkája](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-title-on.png)

    Rögtön észre fogja venni, hogy a vizualizáció X tengelyének mostantól van egy alapértelmezett címe.  Ez ebben az esetben **Pénzügyi hónap**.

   ![Diagram egy címmel az alján](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-x-title.png)

1. Formázza a cím szövegének színét, méretét és betűtípusát:

    - **Cím színe**: Válassza a narancssárgát

    - **Tengelycím**: Írja be a *Pénzügyi hónap* kifejezést (szóközzel)

    - **Cím szövegmérete**: Adja meg a *18*-at

    A testreszabás befejezése után a halmozott oszlopdiagram nagyjából így néz ki:

    ![A testreszabott halmozott oszlopdiagram képernyőképe.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-x-title-formatted.png)

1. Mentse a végrehajtott módosításokat és haladjon tovább a következő részre. Az összes módosítás visszavonásához válassza a **Visszaállítás alapértelmezettre** lehetőséget az **X tengely** testreszabási panel alján. Most az Y tengelyt szabhatja testre.

## <a name="customize-the-y-axis"></a>Az Y tengely testreszabása
Az Y tengely számos jellemzője testre szabható. Hozzáadhat és módosíthat adatcímkéket, az Y tengely címét és rácsvonalakat. Az értékeknél módosíthatók a megjelenítési egységek, a tizedesjegyek, a kezdő- és végpontok, a kategóriáknál pedig módosítható a sávok, oszlopok, vonalak és területek szélessége, mérete és kitöltése. 

Az alábbi példában folytatjuk az oszlopdiagram testreszabását. Végrehajtunk néhány módosítást, hogy megismerkedhessen pár lehetőséggel, a többit pedig önállóan fedezhesse fel.

### <a name="customize-the-y-axis-labels"></a>Az Y tengely címkéinek testreszabása
Alapértelmezés szerint az Y tengely címkéi a bal oldalon jelennek meg. Jelenleg halványszürkék, kicsik és nehezen olvashatók. Ezt fogjuk most módosítani.

1. Bontsa ki az Y tengely beállításait.

   ![Az Y tengely beállításainak képernyőképe.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-axis-y.png)

1. Állítsa az **Y tengely** csúszkát **Be** helyzetbe.  

    ![A Be állású csúszka képernyőképe.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-y-axis-on.png)

    Az Y tengely kikapcsolásának az egyik lehetséges oka az lehet, hogy ezzel helyet hagyjunk még több adatnak.

1. Formázza a szöveg színét, méretét és betűtípusát:

    - **Szín**: Válassza a feketét

    - **Szövegméret**: Adja meg a *10*-et

    - **Megjelenítési egységek**: Válassza a **Millió** lehetőséget

    ![A diagram az Y tengely formázása után](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-formatting-y.png)

### <a name="customize-the-y-axis-title"></a>Az Y tengely címének testreszabása
Ha az Y tengely címe **be** van kapcsolva, akkor a cím az Y tengely címkéi mellett jelenik meg. Ennél a vizualizációnál az Y tengely címe nem tesz hozzá a vizualizációhoz, így hagyja a **Cím** beállítást **kikapcsolva**. Az oktatóanyag későbbi részében majd Y-tengelycímeket is hozzá fogunk adni egy kéttengelyes vizualizációhoz. 

### <a name="customize-the-gridlines"></a>A rácsvonalak testreszabása
Emelje ki a rácsvonalat a szín módosításával és a vonalvastagság növelésével:

- **Szín**: Válassza a narancssárgát

- **Vonalvastagság**: Adja meg a *2* értéket

A testreszabás elvégzése után az oszlopdiagramnak a következőhöz hasonlóan kell kinéznie:

![A diagram képernyőképe a testreszabott Y tengellyel.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-gridline.png)

## <a name="customizing-visualizations-with-dual-y-axes"></a>Dupla Y tengellyel rendelkező vizualizációk testreszabása

Egyes vizualizációk esetében hasznos lehet, ha két Y tengely van. Ilyenek például a kombinált diagramok. Mielőtt formázhatnánk a dupla Y tengelyt, létrehozunk egy kombinált diagramot, amely az értékesítések és a bruttó árrések alakulását hasonlítja össze.  

### <a name="create-a-chart-with-two-y-axes"></a>Két Y tengellyel rendelkező diagram létrehozása

1. Jelölje ki az oszlopdiagramot, majd módosítsa a típusát *Vonal- és halmozott oszlopdiagramra*. Ez a típusú vizualizáció egyetlen vonaldiagram-értéket és több halmozható oszlopértéket támogat. 

    ![Képernyőkép a Vizualizációk panelről, a vonal- és halmozott oszlopdiagram ikon kiemelésével.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-combo.png)
   

2. Húzza át az **Értékesítés** > **tavalyi bruttó nyereség (%)** értékét a Mezők panelről a **Sorértékek** közé.

    ![A vonal- és halmozott oszlopdiagram képernyőképe, amelyen mindhárom érték jól látható.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-add-line.png)

    
3. Formázza újra a vizualizációt úgy, hogy eltávolítja az X tengely döntött címkéit. 

   ![Kombinált diagram és formázási panel, 12-esre csökkentett betűmérettel](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-font-size.png)

   A Power BI létrehoz két Y tengelyt, amelyek értékei külön-külön méretezhetők. A bal oldali tengely az értékesítést méri dollárban, a jobb oldali pedig a bruttó árrés százalékos arányát.

### <a name="format-the-second-y-axis"></a>A második Y tengely formázása
Mivel egy olyan vizualizáción kezdtünk dolgozni, amelynek az eredeti Y tengelye formázva volt, a Power BI a második Y tengely létrehozásakor is megőrizte a beállításokat. Ezeket azonban módosíthatjuk. 

1. A **Vizualizációk** ablaktáblán válassza a festőhenger ikont, a formázási lehetőségek megjelenítéséhez.

1. Bontsa ki az Y tengely beállításait.

1. Görgessen lefelé, amíg meg nem találja a **Másodlagos mutatása** beállítást. Ellenőrizze, hogy ez **Be** van-e kapcsolva. A másodlagos Y tengely a vonaldiagramot jelöli.

   ![A Másodlagos mutatása beállítás képernyőképe.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-show-secondary.png)

1. (Opcionális) Testre szabhatja a két tengely színét, méretét és megjelenítési egységeit. Ha átállítja akár az oszloptengely, akár a sortengely **Pozíció** beállítását, akkor a két tengely helyet cserél.

### <a name="add-titles-to-both-axes"></a>Címek hozzáadása a tengelyekhez

Az összetett vizualizációk esetében sokat segíthet, ha címeket adunk a tengelyeknek.  A címek segítségével a munkatársai jobban megérthetik a vizualizáció által elmondott történetet.

1. Állítsa a **Cím** lehetőséget **Be** állásba az **Y tengely (Oszlop)** és az **Y tengely (Sor)** esetén is.

1. A **Stílus** beállításnál mindkettőhöz válassza a **Csak a cím megjelenítése** lehetőséget.

   ![A Cím és Stílus beállítások képernyőképe.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-show-title.png)

1. A kombinált diagram ekkor a dupla tengelyt címekkel együtt jeleníti meg.

   ![A testreszabott dupla Y tengellyel rendelkező diagram képernyőképe.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-titles-on.png)

1. Formázza meg a címeket. Ebben a példában az egyik címet rövidítettük, és mindkettőnek csökkentettük a betűméretét. 
    - Betűméret: **9**
    - Lerövidítettük az első Y tengely (az oszlopdiagram) **tengelycímét**: Tavalyi és idei év értékesítései

    ![Képernyőkép a kombinált diagramról, amelyen a teljes címek megjelennek.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-dual.png)



További információkért lásd a [Tippek és trükkök a színformázáshoz a Power BI-ban](service-tips-and-tricks-for-color-formatting.md), illetve [A vizualizáció címeinek, jelmagyarázatainak és háttereinek testreszabása](power-bi-visualization-customize-title-background-and-legend.md) cikket. Hamarosan újabb frissítések is elérhetővé válnak a címek formázásához kapcsolódóan. 

## <a name="next-steps"></a>Következő lépések

- [Vizualizációk a Power BI-jelentésekben](power-bi-report-visualizations.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
