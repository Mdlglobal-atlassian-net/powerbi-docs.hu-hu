---
title: Vizualizációk személyre szabásának engedélyezése a felhasználók számára jelentésekben
description: Lehetővé teheti a felhasználóknak, hogy saját jelentésnézetet hozzanak létre szerkesztés nélkül.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/09/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: abc936c6ea4b61e4837e05fbde110e5159296815
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/06/2020
ms.locfileid: "82867116"
---
# <a name="let-users-personalize-visuals-in-a-report"></a>Vizualizációk személyre szabásának engedélyezése a felhasználók számára jelentésekben

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Amikor széles közönséggel oszt meg egy jelentést, előfordulhat, hogy néhány felhasználó más nézetben szeretne megtekinteni egyes vizualizációkat. Például lecserélnék a tengelyek tartalmát, módosítanák a vizualizációtípust vagy bővítenék az elemleírást. Nehéz olyan vizualizációt készíteni, amely mindenkinek megfelel. Ezzel az új funkcióval lehetővé teheti a felhasználóknak, hogy személyre szabják a vizualizációkat a jelentés olvasó nézetében. Igény szerint módosíthatják a vizualizációt, majd elmenthetik könyvjelzőként. Nem kell szerkesztési jogosultsággal rendelkezniük a jelentéshez, és nem kell megkérniük a jelentéskészítőt, hogy helyettük végezze el a módosításokat.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-visual.png" alt-text="Vizualizáció személyre szabása":::
 
## <a name="what-report-consumers-can-change"></a>A jelentésfelhasználók által módosítható elemek

Ezzel a funkcióval a felhasználók további elemzéseket készíthetnek a Power BI-jelentések vizualizációinak ad-hoc szintű feltárásával. A funkció ideális azon jelentéskészítőknek, akik alapszintű feltárási forgatókönyveket szeretnének lehetővé tenni az olvasók számára. A jelentésolvasók az alábbi módosításokat végezhetik el:

- Vizualizáció típusának módosítása
- Mérték vagy dimenzió cseréje
- Jelmagyarázat hozzáadása vagy eltávolítása
- Kettő vagy több mérték összehasonlítása
- Összesítések és hasonlók módosítása

A funkcióval nemcsak új feltárási lehetőségek válnak elérhetővé, hanem lehetővé teszi a módosítások rögzítését és megosztását is:

- Módosítások rögzítése
- Módosítások megosztása
- Egy jelentés összes módosításának visszaállítása
- Egy vizualizáció összes módosításának visszaállítása
- A legutóbbi módosítások törlése

## <a name="turn-on-the-preview-feature"></a>Az előzetes verziójú funkció engedélyezése

Mivel ez a funkció előzetes verzióban érhető el, először be kell kapcsolnia. Nyissa meg a **Fájl** > **Lehetőségek és beállítások** > **Beállítások** menüpontot. A **Globális** beállítások > **Előzetes verziójú funkciók** területen győződjön meg róla, hogy ki van választva a **Vizualizációk személyre szabása** lehetőség.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-preview-personalize-visual.png" alt-text="A Vizualizációk személyre szabása beállítás bekapcsolása":::

Előfordulhat, hogy újra kell indítania Power BI Desktopot, hogy ez megjelenjen a beállítások között.

## <a name="enable-personalization-in-a-report"></a>Személyre szabás engedélyezése a jelentésekben

Az előzetes verziós kapcsoló bekapcsolása után engedélyeznie kell a funkciót azokban a jelentésekben, amelyekben lehetővé szeretné tenni a vizualizációk személyre szabását.

Ez a funkció bekapcsolható a Power BI Desktopban és a Power BI szolgáltatásban.

### <a name="in-power-bi-desktop"></a>A Power BI Desktopban

Ha engedélyezni szeretné a Power BI Desktopban, lépjen a **Fájl** > **Lehetőségek és beállítások** > **Lehetőségek** > **Aktuális fájl** > **Jelentésbeállítások** területre. Győződjön meg arról, hogy a **Vizualizációk személyre szabása (előzetes verzió)** beállítás be van kapcsolva.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-settings-personalize-visual.png" alt-text="Személyre szabás engedélyezése a jelentésekben":::

### <a name="in-the-power-bi-service"></a>A Power BI szolgáltatásban

Ha inkább a Power BI szolgáltatásban szeretné engedélyezni a funkciót, lépjen a jelentése **Beállítások** területére.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-service-settings-personalize-visual.png" alt-text="Jelentésbeállítások a Power BI szolgáltatásban":::

Válassza a **Vizualizációk személyre szabása (előzetes verzió)**  > **Mentés** lehetőséget.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-service-personalize-visual.png" alt-text="A Vizualizációk személyre szabása beállítás bekapcsolása a szolgáltatásban":::

## <a name="select-visuals-that-can-be-personalized"></a>Személyre szabható vizualizációk kiválasztása

Ha egy adott jelentéshez engedélyezi ezt a beállítást, alapértelmezés szerint a jelentésben szereplő összes vizualizáció személyre szabható. Ha nem szeretné, hogy minden vizualizáció személyre szabható legyen, vizualizációnként ki- vagy bekapcsolhatja a beállítást.

Válassza ki a vizualizációt, majd a **Vizualizációk** panel **Formázás** lehetőségét, végül bontsa ki a **Vizualizáció fejléce** területet.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-header-personalize.png" alt-text="Vizualizáció-fejléc kibontása":::
 
Kapcsolja **be** vagy **ki** **A vizualizáció testreszabása** >   lehetőséget.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-personalize-on-off.png" alt-text="A vizualizáció testreszabása csúszka be- vagy kikapcsolása":::

## <a name="personalize-visuals-in-the-power-bi-service"></a>Vizualizációk testreszabása a Power BI szolgáltatásban

Vizualizációk testreszabásával a felhasználók számos módon feltárhatják az adatokat anélkül, hogy kilépnének az olvasó nézetből. Az alábbi példák a különböző módosítási lehetőségeket mutatják be. 

1. A Power BI szolgáltatásban nyisson meg egy jelentést olvasó nézetben.

2. A vizualizáció jobb felső sarkában válassza **A vizualizáció testreszabása** ![A vizualizáció testreszabása ikon](media/power-bi-personalize-visuals/power-bi-personalize-visual-icon.png) lehetőséget. 

### <a name="change-the-visualization-type"></a>Vizualizáció típusának módosítása

A vizualizációt más megjelenítésre válthatja a **vizualizáció típusának** módosításával.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-visual-type.png" alt-text="Vizualizációtípus módosítása":::
 
### <a name="swap-out-a-measure-or-dimension"></a>Mérték vagy dimenzió cseréje
Az X tengely mértékeinek vagy dimenzióinak cseréjéhez jelölje ki a lecserélni kívánt mezőt, majd egy másik mértéket vagy dimenziót.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-axis.png" alt-text="Tengely módosítása":::
 
### <a name="add-or-remove-a-legend"></a>Jelmagyarázat hozzáadása vagy eltávolítása
Jelmagyarázat hozzáadásával színkóddal láthat el egy vizualizációt a kategóriák szerint,. A kategorikus színkódolást a **Személyre szabás** panel **Jelmagyarázat** mezőjének törlésével szüntetheti meg. 

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-legend.png" alt-text="Jelmagyarázat hozzáadása vagy eltávolítása":::

### <a name="compare-two-or-more-different-measures"></a>Kettő vagy több eltérő mérték összehasonlítása
A + ikonnal több mértéket adhat hozzá egy vizualizációhoz, így összehasonlíthatja azok értékeit.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-compare-measures.png" alt-text="Mértékek összehasonlítása":::

### <a name="change-aggregations"></a>Összesítések módosítása
A mérték kiszámításának módját módosíthatja, ha a **Személyre szabás** panelben módosítja az összesítést.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-aggregation.png" alt-text="Összesítések módosítása":::

### <a name="capture-changes"></a>Változások rögzítése 
Személyes könyvjelzőkkel rögzítheti a változtatásokat, így visszatérhet a személyre szabott nézethez. 

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-bookmark.png" alt-text="Könyvjelző létrehozása":::
 
A könyvjelzőt beállíthatja alapértelmezett nézetként.

### <a name="share-changes"></a>Módosítások megosztása 
Ha olvasási és újramegosztási engedéllyel is rendelkezik, a jelentés megosztásakor dönthet úgy, hogy belefoglalja a módosításokat.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-share-changes.png" alt-text="Módosítások megosztása":::
 
### <a name="reset-all-your-changes-to-a-report"></a>Egy jelentés összes módosításának visszaállítása

Válassza az **Alaphelyzetbe állítás** lehetőséget, így a jelentésen végzett összes módosítást eltávolíthatja, és visszaállíthatja a szerző által legutóbb mentett nézetre.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-reset-all.png" alt-text="Az összes módosítás visszaállítása":::
 
### <a name="reset-all-your-changes-to-a-visual"></a>Egy vizualizáció összes módosításának visszaállítása

Válassza az **Vizualizáció alaphelyzetbe állítása** lehetőséget, így a vizualizáción végzett összes módosítást eltávolíthatja, és visszaállíthatja a szerző által legutóbb mentett nézetre.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-reset-visual.png" alt-text="Az összes vizualizáció módosításainak visszaállítása":::
 
### <a name="clear-recent-changes"></a>Legutóbbi módosítások törlése

A radír ikonnal minden módosítást törölhet, amelyet a **Személyre szabás** panel megnyitása óta végzett.  

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-revert-changes.png" alt-text="Legutóbbi módosítások visszaállítása":::

## <a name="limitations-and-known-issues"></a>Korlátozások és ismert problémák

A funkció jelenleg néhány korlátozást von magával.

- A funkció nem támogatott beágyazási forgatókönyvekben, így a webes közzététel során sem.
- A felhasználói felfedezések nem maradnak meg automatikusan. A módosítások rögzítéséhez személyes könyvjelzőként kell menteni a nézetet.
- A vizualizációk nem módosíthatók a Power BI-mobilalkalmazásokban. A Power BI személyes könyvjelzőiben mentett vizualizációmódosítások azonban megmaradnak a mobilalkalmazásokban is.

Emellett tisztában vagyunk néhány problémával, amelyeknek már dolgozunk a megoldásán:

- A hierarchia hozzáadása nem támogatott; a gyermekelemeket egyesével kell hozzáadni.
- A dátumhierarchia nem módosítható dátumra, vagy fordítva. 
- A személyes könyvjelzők esetében előfordulhat, hogy eltérő eredményt kap a kiválasztott szekvenciától függően. Az eltérések azért lehetségesek, mert nem rögzítjük a jelentés teljes állapotát, csak az elvégzett módosításokat. Megkerülő megoldásként használja az **Alaphelyzetbe állítás** lehetőséget, majd válassza ki a megtekinteni kívánt könyvjelzőt. 

## <a name="next-steps"></a>Következő lépések

Próbálja ki a vizualizációk új személyre szabási funkcióját. Küldjön visszajelzést erről a funkcióról, és arról, hogy hogyan tehetnénk még jobbá ezt a felületet a [Power BI Ideas webhelyen](https://ideas.powerbi.com/forums/265200-power-bi). 

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

