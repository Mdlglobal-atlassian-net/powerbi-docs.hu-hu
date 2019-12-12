---
title: Tippek és trükkök a színformázáshoz a jelentésekben
description: Tippek és trükkök a színformázáshoz a Power BI-jelentésekben
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/04/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 006288cd380a56ba57697ed285b04b38985b69db
ms.sourcegitcommit: e492895259aa39960063f9b337a144a60c20125a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74831647"
---
# <a name="tips-and-tricks-for-color-formatting-in-power-bi"></a>Tippek és trükkök a színformázáshoz a Power BI-ban
A Power BI sokféle lehetőséget kínál, amelyekkel egyedivé tehetők az irányítópultok és a jelentések. Ez a cikk néhány olyan ötletet fejt ki részletesen, amelyek segítségével meggyőzőbb, érdekesebb és az Ön igényeinek jobban megfelelő Power BI-vizualizációkat készíthet.

A következő tippeket kínáljuk Önnek. Van egy másik remek ötlete? Nagyszerű! Küldje el nekünk, és talán hozzáadjuk ehhez a listához.

* Téma alkalmazása a teljes jelentésre
* Egy adatpont színének módosítása
* Diagram színeinek meghatározása egy numerikus érték alapján
* Adatpontok színének meghatározása egy mező értéke alapján
* A színskála összeállításának testre szabása
* Széttartó színskálák használata
* Művelet visszavonása a Power BI-ban

Módosítások elvégzéséhez szerkesztenie kell a jelentést. Nyissa meg a jelentést, majd válassza a **Jelentés szerkesztése** lehetőséget a menüsávon, a következő képhez hasonlóan.

![a Szerkesztés menü helye](media/service-tips-and-tricks-for-color-formatting/power-bi-edit-report.png)

Amikor a jelentésvászon jobb oldalán megjelenik a **Szűrők** és **Vizualizációk** panel, megkezdheti a testre szabást. Ha a panelek nem láthatók, a jobb felső sarokban található nyíllal nyithatók meg.

![jelentésvászon szerkesztési nézetben](media/service-tips-and-tricks-for-color-formatting/power-bi-edit.png)

## <a name="apply-a-theme"></a>Téma alkalmazása
A jelentéstémák használatával olyan tervezési módosításokat hajthat végre az egész jelentésen, mint a vállalati színek, a változó ikonkészletek, vagy egy új alapértelmezett vizualizációs formázás. Jelentéstéma alkalmazásakor a jelentésben szereplő összes vizualizáció a kiválasztott téma színeit és formázását fogja használni. További információért olvassa el a [Jelentéstémák használata](../desktop-report-themes.md) szakaszt

![Téma ikon módosítása a menüsávon](media/service-tips-and-tricks-for-color-formatting/power-bi-theme.png)

Itt az **Innováció** témát alkalmaztuk az értékesítési és marketingjelentésre.

![Az Innováció téma alkalmazva](media/service-tips-and-tricks-for-color-formatting/power-bi-theme-innovate.png)

## <a name="change-the-color-of-a-single-data-point"></a>Egy adatpont színének módosítása
Előfordul, hogy egy adott adatpontot szeretne kiemelni. Ez lehet egy újonnan bevezetett termék eladott mennyisége, vagy egy javuló minőségi mutató egy új program elindítása után. A Power BI-ban kiemelhet egy választott adatpontot a színe módosításával.

Az alábbi vizualizáció egységeket rangsorol a termékszegmens szerint. 

![Az adatszínek módosítása szürkére](media/service-tips-and-tricks-for-color-formatting/power-bi-data.png)

Tegyük fel, hogy a **Kényelem** szegmens színes kiemelésével meg szeretné mutatni, hogy milyen jól teljesít az új szegmens. A lépések a következők:

Bontsa ki az **Adatszínek** szakaszt, és kapcsolja be a csúszkát **Az összes megjelenítése** lehetőséghez. Így a vizualizáció összes adatelemének színe megjelenik. Módosítsa bármelyik adatpontot.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-show.png)

Állítsa a **Kényelem** színét narancssárgára. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-one-color.png)

Miután választott, a **Kényelem** adatpont szép narancssárga, és kétségtelenül szembeszökő színt vesz fel.

A Power BI akkor is megjegyzi a választását és narancssárgán jeleníti meg a **Kényelmet**, ha Ön megváltoztatja, majd visszaváltoztatja a vizualizáció típusát.

Egynél több, sőt akár az összes adatelem adatpontjának színe is megváltoztatható. A vizualizáció például a sárga, zöld és kék vállalati színeket is tükrözheti. 

![sávdiagram zöld, sárga és kék színű sávokkal](media/service-tips-and-tricks-for-color-formatting/power-bi-corporate.png)

A színekkel sok mindent megtehet. A következő bekezdések a színátmenetekkel foglalkoznak.

## <a name="conditional-formatting-for-visualizations"></a>Vizualizációk feltételes formázása
A vizualizációknak gyakran előnyére válik a színek dinamikus meghatározása egy mező numerikus értéke alapján. Ezen a módon az oszlopok magasságát megadó érték mellett egy másikat is megjeleníthet, így két értéket szemléltethet egy diagramon. Használhatja a lehetőséget egy bizonyos érték feletti (vagy alatti) adatpontok kiemelésére – például alacsony jövedelmezőségű területek kimutatására.

A következő szakaszok különböző módszereket mutatnak be a színek numerikus érték alapján történő meghatározására.

### <a name="base-the-color-of-data-points-on-a-value"></a>Adatpontok színének meghatározása egy érték alapján
Ha egy érték alapján szeretné módosítani a színt, válasszon egy vizualizációt az aktiváláshoz. Nyissa meg a Formátum panelt a festőhenger ikon kiválasztásával és az **Adatszínek** kártya kibontásával. Vigye az egérmutatót a kártyára, és válassza a megjelenő három pontot, majd a **Feltételes formázás** lehetőséget.  

![a feltételes formázás lehetőség választása a három pontra történő kattintással](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-formatting.gif)

Az **Alapértelmezett színek** panel legördülő menüjében adja meg a feltételesen formázni kívánt mezőket. Ebben a példában a **Sales fact** > **Total Units** mezőt választottuk, amelyhez a **legalacsonyabb értéknek** a világoskéket, **legmagasabb értéknek** pedig a sötétkéket adtuk meg. 

![az adatszínnel történő feltételes formázás beállításai](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-formatting2-new.png)

![alapértelmezett színekkel ellátott oszlopdiagram](media/service-tips-and-tricks-for-color-formatting/power-bi-default-colors.png)

A vizualizáció színét egy vizualizáción kívüli mezővel is formázhatja. A következő ábrán a **%Market Share SPLY YTDP** (Piaci részesedés a tavalyi év azonos időszakában, az év elejétől számítva (%)) mező szolgál erre. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-colors.png)


Mint látja, bár mind a **Productivity**, mind az **Extreme** egységei több eladást eredményeztek (amit a magasabb oszlop jelez), a **Moderation** nagyobb **%Market Share SPLY YTD** értékkel rendelkezik (amit az oszlop színtelítettségéből láthatunk).

### <a name="customize-the-colors-used-in-the-color-scale"></a>A színskála összeállításának testre szabása
Az értékek és a színek egymáshoz rendelése is módosítható. A következő ábrán a **legkisebb** és a **legnagyobb** értékhez választott két szín a narancs, illetve a zöld.

Figyelje meg az első képen, hogy a diagram oszlopai a sávon ábrázolt színátmenetet tükrözik. A legmagasabb érték zöld, a legalacsonyabb narancsszínű, a közöttük lévők pedig a skála zöld és narancs közötti árnyalatait viselik.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional4.png)

Most próbáljon meg numerikus értéket adni a **Minimum** és **Maximum** mezőknek. Válassza a **Szám** lehetőséget a legördülő menükből a **Minimum** és a **Maximum** értékeinek megadásához, és adja meg a **Minimum** értékeként, hogy 3500 a **Maximum** értékeként, hogy 6000.

![Feltételes formázás számok alapján](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-formatting-number.png)

Ezekkel az értékekkel a színátmenet már nem alkalmazható a diagramnak a **Minimum** alatti vagy **Maximum** feletti értékeire. A **Maximum** értéknél magasabb oszlopok színe zöld, a **Minimum** alattiaké piros.

![a feltételes formázás számok alapján művelet eredménye](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional3.png)

### <a name="use-diverging-color-scales"></a>Széttartó színskálák használata
Előfordul, hogy az adatok természetes módon széttartó jellegűek. Egy hőmérsékleti skálának például természetes középpontja a fagypont, egy jövedelmezőségi érték természetes középpontja a nulla.

Széttartó színskálák használatához jelölje be a **Széttartó** jelölőnégyzetet. A **Széttartó** beállítással újabb paletta jelenik meg **Középérték** néven, ahogyan az alábbi képen látható.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-diverging2.png)

Amíg a **Széttartó** beállítás be van kapcsolva, a **Minimumhoz**, a **Maximumhoz** és a **Középértékhez** tartozó szín külön módosítható. A következő képen a **% Market Share SPLY YTD** **Középértékeként** 0,2 van megadva, ezért a 0,2-nél nagyobb értékek a zöld, az egynél kisebbek a piros árnyalataiban jelennek meg.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-diverging.png)

## <a name="how-to-undo-in-power-bi"></a>Művelet visszavonása a Power BI-ban
Sok más Microsoft-szolgáltatáshoz és -szoftverhez hasonlóan a Power BI is egyszerű módot kínál az utolsó parancs visszavonására. Képzelje el például, hogy megváltoztatta egy adatpont vagy adatpont-sorozat színét és a vizualizáción megjelenő szín nem teszik Önnek. Majd pedig az eredeti színt szeretné visszaállítani, csakhogy már nem emlékszik rá!

A legutóbbi művelet vagy néhány nemrégiben végzett művelet **visszavonásához** csak a CTRL+Z billentyűkombinációt kell megnyomnia.

## <a name="feedback"></a>Visszajelzés
Van egy tippje, amelyet szívesen megosztana másokkal? Kérjük, küldje el nekünk, és megvizsgáljuk, hozzáadhatjuk-e ehhez a listához.

>[!NOTE]
>A **Formátum** ikon választásával elérhető szín, tengely és kapcsolódó testreszabások a Power BI Desktopban is elérhetők.

## <a name="next-steps"></a>További lépések
[Bevezetés a színformázás és tengelytulajdonságok használatába](service-getting-started-with-color-formatting-and-axis-properties.md)

