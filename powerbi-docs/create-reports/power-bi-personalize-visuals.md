---
title: Vizualizációk személyre szabásának engedélyezése a felhasználók számára jelentésekben
description: Lehetővé teheti a felhasználóknak, hogy saját jelentésnézetet hozzanak létre szerkesztés nélkül.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/09/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: ab232d4e5b6d17e7f20ed8a41875ca47693eb285
ms.sourcegitcommit: 21b06e49056c2f69a363d3a19337374baa84c83f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/15/2020
ms.locfileid: "83407593"
---
# <a name="let-users-personalize-visuals-in-a-report"></a>Vizualizációk személyre szabásának engedélyezése a felhasználók számára jelentésekben

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Amikor széles közönséggel oszt meg egy jelentést, előfordulhat, hogy néhány felhasználó más nézetben szeretne megtekinteni egyes vizualizációkat. Például lecserélnék a tengelyek tartalmát, módosítanák a vizualizációtípust vagy bővítenék az elemleírást. Nehéz olyan vizualizációt készíteni, amely mindenkinek megfelel. Ezzel az új funkcióval lehetővé teheti a felhasználóknak, hogy személyre szabják a vizualizációkat a jelentés olvasó nézetében. Igény szerint módosíthatják a vizualizációt, majd elmenthetik könyvjelzőként. Nem kell szerkesztési jogosultsággal rendelkezniük a jelentéshez, és nem kell megkérniük a jelentéskészítőt, hogy helyettük végezze el a módosításokat.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-visual.png" alt-text="Vizualizáció személyre szabása":::
 
## <a name="what-report-consumers-can-change"></a>A jelentésfelhasználók által módosítható elemek

Ezzel a funkcióval a felhasználók további elemzéseket készíthetnek a Power BI-jelentések vizualizációinak ad-hoc szintű feltárásával. Ennek a funkciónak a használatát a [Vizualizációk személyre szabása a jelentésekben](../consumer/end-user-personalize-visuals.md) című témakörben ismerheti meg. A funkció ideális azon jelentéskészítőknek, akik alapszintű feltárási forgatókönyveket szeretnének lehetővé tenni az olvasók számára. A jelentésolvasók az alábbi módosításokat végezhetik el:

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

[Vizualizációk személyre szabása a jelentésekben](../consumer/end-user-personalize-visuals.md).     

Próbálja ki a vizualizációk új személyre szabási funkcióját. Küldjön visszajelzést erről a funkcióról, és arról, hogy hogyan tehetnénk még jobbá ezt a felületet a [Power BI Ideas webhelyen](https://ideas.powerbi.com/forums/265200-power-bi). 

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
