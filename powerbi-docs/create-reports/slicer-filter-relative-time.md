---
title: Relatívidő-szeletelő vagy -szűrő használata a Power BI-ban
description: Útmutató a relatív időtartományok szeletelővel vagy szűrővel végzett korlátozásához a Power BI-ban.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/22/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 4f0bfdbf3eb3856f872c872fbe0880ad39839e07
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/06/2020
ms.locfileid: "82867599"
---
# <a name="use-a-relative-time-slicer-and-filter-in-power-bi"></a>Relatívidő-szeletelő és -szűrő használata a Power BI-ban

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Gyors frissítési forgatókönyvek esetén hasznos lehet egy kisebb időtartam szűrése. A relatív időszeletelővel vagy relatív időszűrővel időalapú szűrőket alkalmazhat az adatmodellek bármely dátum- vagy időoszlopára. A relatívidő-szeletelővel például megjelenítheti csak az elmúlt perc vagy óra videómegtekintéseit. 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time.gif" alt-text="Példa a relatív időre":::

A funkciót nem kell az [automatikus oldalfrissítéssel](../desktop-automatic-page-refresh.md) együtt használnia. Azonban számos, relatív időt tartalmazó forgatókönyv jól működik együtt az automatikus oldalfrissítés funkcióval is.  

> [!NOTE]
> Ha egy relatívidő-szűrőt vagy -szeletelőt alkalmaz az oldal vagy a jelentés szintjén, az oldal vagy a jelentés minden vizualizációját pontosan ugyanarra az időtartományra szűr egy megosztott *rögzített kezdőidő* használatával. Mivel a vizualizációk némileg eltérő végrehajtási idővel rendelkezhetnek, a megosztott rögzített kezdőidő gondoskodik a vizualizációk szinkronizálásáról az oldalon vagy a jelentésben. Ebben a cikkben további információt talál a [rögzített kezdőidőről](#understanding-anchor-time).

## <a name="turn-on-relative-time-preview"></a>A relatív idő előzetes verziójának bekapcsolása

A relatívidő-szűrő előzetes verzióban érhető el, ezért engedélyeznie kell a funkciót. Nyissa meg a **Fájl** > **Lehetőségek és beállítások** > **Beállítások** menüpontot. A **Globális beállítások** > **Előzetes verziójú funkciók** területen győződjön meg róla, hogy ki van választva a **Relatívidő-szűrő** lehetőség.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set-preview.png" alt-text="A relatív idő előzetes verziójának beállítása":::

## <a name="create-a-relative-time-slicer-or-filter"></a>Relatívidő-szeletelő vagy -szűrő létrehozása

A funkció engedélyezése után húzással elhelyezheti a dátum- vagy időmezőt a szeletelő mezőterületén, vagy a Szűrők panelen. 

### <a name="create-a-slicer"></a>Szeletelő létrehozása

1. Húzzon egy dátum- vagy időmezőt a vászonra.

2. Válassza ki a **Szeletelő** vizualizációtípust.

    :::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-create-slicer.png" alt-text="Időszeletelő létrehozása":::

### <a name="create-a-filter"></a>Szűrő létrehozása
 
- Húzzon egy dátum- vagy időmezőt a Szűrők panelre **ehhez a vizualizációhoz**, **ehhez az oldalhoz** vagy **minden oldalhoz**.

### <a name="set-relative-time"></a>Relatív idő beállítása 

Ezután módosítsa a szűrő típusát **Relatív időre**.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set.png" alt-text="Módosítás relatív időre":::
 
Ennek a következőképpen kell kinéznie egy szeletelőben:

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-slicer.png" alt-text="Relatív idő egy szeletelőben":::

A következőképpen kell kinéznie egy szűrőkártyán: 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-filter.png" alt-text="Relatív idő egy szűrőben":::
 
Az új szűrőtípussal **Utolsó**, **Következő** vagy **Ezen időszak** alapján szűrhet: 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-last-next.png" alt-text="Utolsó, Következő vagy Ezen időszak kiválasztása":::
 
Az időtartamot egy egész számmal és egy időegységgel adhatja meg: **Perc** vagy **Óra**.
 
:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-minutes-hours.png" alt-text="Perc vagy óra kiválasztása":::

Ha területet szeretne megtakarítani a vásznon, szűrőkártyaként is létrehozhatja a relatívidő-szűrőt a Szűrők panelen.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set-filter.png" alt-text="Relatív idő beállítása egy szűrőben":::
 
## <a name="understanding-anchor-time"></a>A rögzített kezdőidő

Ha az oldalra vagy a jelentés szintjére alkalmaz egy szűrőt, az oldal vagy jelentés minden vizualizációját ugyanarra az időtartományra szinkronizálja. Ezeket a lekérdezéseket a rendszer a *rögzített kezdőidőnek* nevezett időponthoz viszonyítva végzi el. A rögzített kezdőidő automatikusan frissül az alábbi esetekben:

- Az oldal kezdeti betöltése.
- Manuális frissítés.
- Automatikus vagy változásészleléses oldalfrissítés.
- A modell változása.

### <a name="anchor-time-exceptions"></a>A rögzített kezdőidő kivételei

- A Q&A vizualizáció relatívidő-szűrése nem a rögzített kezdőidőhöz van viszonyítva mindaddig, amíg Ön szabványos vizualizációvá nem alakítja a Q&A vizualizációt. A többi AI-vizualizáció (például a főbb befolyásolók és a felbontásfa) azonban a rögzített kezdőidővel van szinkronizálva. 
- A relatívdátum-szűrők és -szeletelők emellett nem a rögzített kezdőidőhöz képest relatívak, kivéve, ha relatívidő-szűrőkkel egy környezetben vannak. Ha egy relatívdátum- és egy relatívidő-szűrő ugyanazon az oldalon található, a relatívdátum-szűrő a rögzített kezdőidőhöz igazodik.

## <a name="limitations-and-considerations"></a>Korlátozások és szempontok

A relatívidő-szeletelők és -szűrők használatára jelenleg a következő korlátozások és szempontok vonatkoznak.

- **Időzónával kapcsolatos megfontolások**: A Power BI adatmodelljei nem tartalmaznak időzóna-információkat. A modellek tudják tárolni az időadatokat, de nem jelölik az időzónákat. A szeletelők és a szűrők minden esetben az UTC-időn alapulnak. Így ha beállít egy szűrőt egy jelentésben, majd elküldi azt egy másik időzónában tartózkodó munkatársának, mindketten ugyanazokat az adatokat fogják látni. Hacsak nem a UTC időzónában vannak, Önnek és a munkatársának figyelembe kell vennie az időeltolódást. A helyi időzónában rögzített adatok a Lekérdezésszerkesztővel alakíthatók át UTC-idővé.
- Az új szűrőtípust a Power BI Desktop, a Power BI szolgáltatás, a Power BI Embedded és a Power BI-mobilalkalmazások támogatják. Azonban néhány ismert támogatási korlátozással is rendelkezik:

    - Az Embed API nem támogatja.
    - A webes közzétételhez nem használható.

- **Lekérdezések gyorsítótárazása**: Ehhez az ügyfél gyorsítótárát használjuk. Tegyük fel, hogy „az utolsó 1 perc”, majd „az utolsó 5 perc”, végül ismét „az utolsó 1 perc” beállítást adja meg. Ekkor ugyanazok az eredmények jelennek meg, mint az első futtatásakor, hacsak nem frissíti az oldalt, vagy az nem frissül automatikusan.

## <a name="next-steps"></a>Következő lépések

- [Relatívdátum-szeletelő és -szűrő használata a Power BI-ban](../visuals/desktop-slicer-filter-date-range.md)
- [Szeletelők a Power BI-ban](../visuals/power-bi-visualization-slicers.md)

