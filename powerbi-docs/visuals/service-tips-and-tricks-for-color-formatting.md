---
title: Tippek és trükkök a színformázáshoz a Power BI-ban
description: Tippek és trükkök a színformázáshoz a Power BI-ban
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 12/19/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 09c505d114eaa951978f23061d9c79c1b6870fad
ms.sourcegitcommit: 5206651c12f2b91a368f509470b46f3f4c5641e6
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53983370"
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

A módosításhoz szerkesztenie kell a jelentést: jelölje ki saját **Jelentését** a **Saját munkaterület** panelen, majd válassza a **Jelentés szerkesztése** lehetőséget a felső menüben, ahogyan az alábbi ábrán látható. Ez a példa az **Emberi erőforrások mintát** használja.

![jelentésvászon a Jelentés szerkesztése elem kiemelésével](media/service-tips-and-tricks-for-color-formatting/power-bi-edit.png)

Amikor a **Jelentés** vászon jobb oldalán megjelenik a **Vizualizációk** panel, megkezdheti a testre szabást.

![jelentés a Formázás panellel](media/service-tips-and-tricks-for-color-formatting/power-bi-formatting-pane.png)

## <a name="change-the-color-of-a-single-data-point"></a>Egy adatpont színének módosítása
Előfordul, hogy egy adott adatpontot szeretne kiemelni. Ez lehet egy újonnan bevezetett termék eladott mennyisége, vagy egy javuló minőségi mutató egy új program elindítása után. A Power BI-ban és a vizualizációtípusok többségénél kiemelhet egy választott adatpontot a színe módosításával.

Az alábbi vizualizáció az értékesítési nyereségeket mutatja be alkalmazottanként az alapértelmezett színekkel. 

![területdiagram](media/service-tips-and-tricks-for-color-formatting/power-bi-area-chart.png)

Az Annelie-hez tartozó terület nem jól látható, ezért színezéssel fogjuk jobban kiemelni. A lépések a következők:

Bontsa ki az **Adatszínek** szakaszt. A következő jelenik meg.

![a Formázás alatti Adatszínek terület](media/service-tips-and-tricks-for-color-formatting/power-bi-data-colors.png)


Ebben az esetben válasszunk egy sötét de élénk színt, amely nem hasonló a Valery adataihoz használt színhez. Válassza ki az Annelie színmezőjében lévő lefelé mutató nyilat, válassza az **Egyéni szín** lehetőséget, és válasszon egy élénk kék színt.

![színválasztás](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_6.png)

A választás után Annelie területe sokkal jobban megkülönböztethető a többi alkalmazottétól. 

![területdiagram, Annalie területe már élénk kék](media/service-tips-and-tricks-for-color-formatting/power-bi-color.png)

A Power BI akkor is megjegyzi a választását és zölden jeleníti meg **Washingtont**, ha Ön megváltoztatja, majd visszaváltoztatja a vizualizáció típusát.

Egynél több adatpont színe is megváltoztatható. A következő ábrán **Arizona** piros, **Washington** továbbra is zöld színnel jelenik meg.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_8.png)

A színekkel sok mindent megtehet. A következő bekezdések a színátmenetekkel foglalkoznak.

## <a name="base-the-colors-of-a-chart-on-a-numeric-value"></a>Diagram színeinek meghatározása egy numerikus érték alapján
Egy diagramnak gyakran előnyére válik a színek dinamikus meghatározása egy mező numerikus értéke alapján. Ezen a módon az oszlopok magasságát megadó érték mellett egy másikat is megjeleníthet, így két értéket szemléltethet egy diagramon. Használhatja a lehetőséget egy bizonyos érték feletti (vagy alatti) adatpontok kiemelésére – például alacsony jövedelmezőségű területek kimutatására.

A következő szakaszok különböző módszereket mutatnak be a színek numerikus érték alapján történő meghatározására.

## <a name="base-the-color-of-data-points-on-a-value"></a>Adatpontok színének meghatározása egy érték alapján
A szín érték alapján történő megadásához húzza a színezés alapjául szánt mezőt a **Mező** panel **Színtelítettség** területére. A következő ábrán az **Adózatlan nyereség** mező adja meg a **Színtelítettség** értékét. Mint látható, bár a **Velo** **Bruttó értékesítés** mutatója nagyobb (az oszlopa magasabb), az **Amarilla** nagyobb **Adózatlan nyereséget** ért el (az oszlopának telítettebb a színe).

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_9.png)

## <a name="customize-the-colors-used-in-the-color-scale"></a>A színskála összeállításának testre szabása
A színskála összeállítását is testre szabhatja. Bontsa ki az **Adatszíneket** és megjelenik az adatai megjelenítéséhez használt színskála. Alapértelmezés szerint a legalacsonyabb értékű adathoz tartozik a legkevésbé telített szín, a legmagasabbhoz pedig a legtelítettebb.

A színskála sávján látható színtartomány az értékek **minimuma** és **maximuma** közötti átmeneteket mutatja. A sáv bal szélén a **legkisebb**, a jobb szélén a **legnagyobb** értékhez tartozó szín látható.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_10.png)

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

