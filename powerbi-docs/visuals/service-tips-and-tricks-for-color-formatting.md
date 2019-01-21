---
title: Tippek és trükkök a színformázáshoz a Power BI-ban
description: Tippek és trükkök a színformázáshoz a Power BI-ban
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/09/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 71ed70344281dec3353b73c8698594d62ef32eae
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54285599"
---
# <a name="tips-and-tricks-for-color-formatting-in-power-bi"></a>Tippek és trükkök a színformázáshoz a Power BI-ban
A Power BI sokféle lehetőséget kínál, amelyekkel egyedivé tehetők az irányítópultok és a jelentések. Ez a cikk néhány olyan ötletet fejt ki részletesen, amelyek segítségével meggyőzőbb, érdekesebb és az Ön igényeinek jobban megfelelő Power BI-vizualizációkat készíthet.

A következő tippeket kínáljuk Önnek. Van egy másik remek ötlete? Nagyszerű! Küldje el nekünk, és talán hozzáadjuk ehhez a listához.

* Egy adatpont színének módosítása
* Diagram színeinek meghatározása egy numerikus érték alapján
* Adatpontok színének meghatározása egy mező értéke alapján
* A színskála összeállításának testre szabása
* Széttartó színskálák használata
* Művelet visszavonása a Power BI-ban

Módosítások elvégzéséhez szerkesztenie kell a jelentést. Nyissa meg a jelentést, majd válassza a **Jelentés szerkesztése** lehetőséget a felső menüben, a következő képhez hasonlóan.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-edit.png)

Amikor a **Jelentés** vászon jobb oldalán megjelenik a **Vizualizációk** panel, megkezdheti a testre szabást. Ha a panel nem látható, a jobb felső sarokban található nyíllal nyitható meg.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-formatting-pane.png)

## <a name="change-the-color-of-a-single-data-point"></a>Egy adatpont színének módosítása
Előfordul, hogy egy adott adatpontot szeretne kiemelni. Ez lehet egy újonnan bevezetett termék eladott mennyisége, vagy egy javuló minőségi mutató egy új program elindítása után. A Power BI-ban kiemelhet egy választott adatpontot a színe módosításával.

Az alábbi vizualizáció egységeket rangsorol a termékszegmens szerint. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-grey.png)

Tegyük fel, hogy a **Kényelem** szegmens színes kiemelésével meg szeretné mutatni, hogy milyen jól teljesít az új szegmens. A lépések a következők:

Bontsa ki az **Adatszínek** szakaszt, és kapcsolja be a csúszkát **Az összes megjelenítése** lehetőséghez. Így a vizualizáció összes adatelemének színe megjelenik. A kurzort az adatpontok fölé helyezve engedélyezett a görgetés, tehát az adatpontok bármelyikét módosíthatja.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-show-all.png)

Állítsa a **Kényelem** színét narancssárgára. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-orange.png)

Miután választott, a **Kényelem** adatpont szép narancssárga, és kétségtelenül szembeszökő színt vesz fel.

A Power BI akkor is megjegyzi a választását és narancssárgán jeleníti meg a **Kényelmet**, ha Ön megváltoztatja, majd visszaváltoztatja a vizualizáció típusát.

Egynél több, sőt akár az összes adatelem adatpontjának színe is megváltoztatható. A vizualizáció a vállalati színeket is tükrözheti. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-corporate.png)

A színekkel sok mindent megtehet. A következő bekezdések a színátmenetekkel foglalkoznak.

## <a name="base-the-colors-of-a-chart-on-a-numeric-value"></a>Diagram színeinek meghatározása egy numerikus érték alapján
Egy diagramnak gyakran előnyére válik a színek dinamikus meghatározása egy mező numerikus értéke alapján. Ezen a módon az oszlopok magasságát megadó érték mellett egy másikat is megjeleníthet, így két értéket szemléltethet egy diagramon. Használhatja a lehetőséget egy bizonyos érték feletti (vagy alatti) adatpontok kiemelésére – például alacsony jövedelmezőségű területek kimutatására.

A következő szakaszok különböző módszereket mutatnak be a színek numerikus érték alapján történő meghatározására.

## <a name="base-the-color-of-data-points-on-a-value"></a>Adatpontok színének meghatározása egy érték alapján
A szín érték alapján történő megadásához húzza a színezés alapjául szánt mezőt a **Mezők** panel **Színtelítettség** területére. A következő ábrán a **%Market Share SPLY YTDP** (Piaci részesedés a tavalyi év azonos időszakában, az év elejétől számítva (%))mező adja meg a **Színtelítettség** értékét. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-color-saturation.png)

A Formázás panel **Adatszínek** területén adja meg, hogy a **%Market Share SPLY YTDP** mező értéke hogyan befolyásolja az oszlopdiagram színárnyalatait. Ebben a példában az alacsonyabb százalékos érték világosabb kéket eredményez, a magasabb pedig sötétebbet.


![](media/service-tips-and-tricks-for-color-formatting/power-bi-data-colors2.png)


Mint látható, bár mind a **Productivity**, mind az **Extreme** egységei több eladást eredményeztek (amit a magasabb oszlop jelez), a **Moderation** nagyobb **%Market Share SPLY YTD** értékkel rendelkezik (amit az oszlop színtelítettségéből láthatunk).

![](media/service-tips-and-tricks-for-color-formatting/power-bi-saturation.png)

## <a name="customize-the-colors-used-in-the-color-scale"></a>A színskála összeállításának testre szabása
A színskála összeállítását is testre szabhatja. Alapértelmezés szerint a legalacsonyabb értékű adathoz tartozik a legkevésbé telített szín, a legmagasabbhoz pedig a legtelítettebb. A fenti ábrán kék színskálát használtuk. 

Bontsa ki az **Adatszíneket** és megjelenik az adatai megjelenítéséhez használt színskála. A színskála sávján látható színtartomány az értékek **minimuma** és **maximuma** közötti átmeneteket mutatja. A sáv bal szélén a **legkisebb**, a jobb szélén a **legnagyobb** értékhez tartozó szín látható.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-data-colors2.png)


Más színátmenet beállításához nyissa meg a legördülő ablakot a **Minimum** vagy a **Maximum** mellett, és válassza ki a színt. A következő ábrán a **legnagyobb** értékhez tartozó szín feketére van állítva, és a színskála a **legkisebb** és a **legnagyobb** értékek közötti átmenetet mutatja.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_11.png)

Az értékek és a színek egymáshoz rendelése is módosítható. A következő ábrán a **legkisebb** és a **legnagyobb** értékhez választott két szín a narancs, illetve a zöld.

Figyelje meg az első képen, hogy a diagram oszlopai a sávon ábrázolt színátmenetet tükrözik. A legmagasabb érték zöld, a legalacsonyabb narancsszínű, a közöttük lévők pedig a skála zöld és narancs közötti árnyalatait viselik.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_12.png)

Most próbáljon meg numerikus értéket adni a **legkisebb** és a **legnagyobb** értékhez tartozó színek alatti **Minimum** és **Maximum** mezőknek (ahogyan az alábbi képen látható). Állítsa a **Minimum** értékét 20 000 000-ra, a **Maximum** értékét pedig 20 000 001-re.

Ezekkel az értékekkel a színátmenet már nem alkalmazható a diagramnak a **Minimum** alatti vagy **Maximum** feletti értékeire. A **Maximum** értéknél magasabb oszlopok színe zöld, a **Minimum** alattiaké piros.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_13.png)

## <a name="use-diverging-color-scales"></a>Széttartó színskálák használata
Előfordul, hogy az adatok természetes módon széttartó jellegűek. Egy hőmérsékleti skálának például természetes középpontja a fagypont, egy jövedelmezőségi érték természetes középpontja a nulla.

Széttartó színskálák használatához állítsa a **Széttartó** csúszkát **Be** helyzetbe. A **Széttartó** beállítással újabb paletta és értékmező jelenik meg **Középérték** néven, ahogyan az alábbi képen látható.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_14.png)

Amíg a **Széttartó** beállítás be van kapcsolva, a **Minimumhoz**, a **Maximumhoz** és a **Középértékhez** tartozó szín külön módosítható. A következő képen **Középértékként** 1 van megadva, ezért az 1-nél nagyobb értékek a zöld, az egynél kisebbek a piros árnyalataiban jelennek meg.

## <a name="how-to-undo-in-power-bi"></a>Művelet visszavonása a Power BI-ban
Sok más Microsoft-szolgáltatáshoz és -szoftverhez hasonlóan a Power BI is egyszerű módot kínál az utolsó parancs visszavonására. Képzelje el például, hogy megváltoztatta egy adatpont vagy adatpont-sorozat színét és a vizualizáción megjelenő szín nem teszik Önnek. Majd pedig az eredeti színt szeretné visszaállítani, csakhogy már nem emlékszik rá!

Az utolsó művelet vagy műveletek **visszavonásához** csak egyvalamit kell tennie:

- Nyomja le a Ctrl+Z billentyűkombinációt

## <a name="feedback"></a>Visszajelzés
Van egy tippje, amelyet szívesen megosztana másokkal? Kérjük, küldje el nekünk, és megvizsgáljuk, hozzáadhatjuk-e ehhez a listához.

>[!NOTE]
>A **Formátum** ikon választásával elérhető szín, tengely és kapcsolódó testreszabások a Power BI Desktopban is elérhetők.

## <a name="next-steps"></a>További lépések
[Bevezetés a színformázás és tengelytulajdonságok használatába](service-getting-started-with-color-formatting-and-axis-properties.md)

