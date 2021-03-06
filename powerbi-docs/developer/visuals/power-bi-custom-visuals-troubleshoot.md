---
title: A Power BI-vizualizációk fejlesztésekor jelentkező hibák elhárítása
description: Ez cikk bemutat néhány olyan gyakori problémát, amely egyéni Power BI-vizualizációk fejlesztése és létrehozása közben jelentkezhet.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 11/06/2018
ms.openlocfilehash: e066ea5128709a0e16873bba5f025e96938cac54
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "80113646"
---
# <a name="troubleshoot-power-bi-visuals"></a>Power BI-vizualizációk hibáinak elhárítása

## <a name="debug"></a>Hibakeresés

**A pbiviz parancs nem található (vagy ehhez hasonló hibaüzenetek)**

Ha a terminálon/parancssorból kiadja a `pbiviz` parancsot, akkor meg kell jelennie a súgóképernyőnek. Ha nem jelenik meg, akkor nincs jól telepítve az eszköz. Ellenőrizze, hogy telepítve van-e a NodeJS 4.0-s vagy újabb verziója.

**Nem látható a Vizualizációk lapon a vizualizációk hibáinak keresését indító ikon**

A **Megjelenítések** panelen egy olyan ikon jelzi a vizualizáció hibakeresését, amelyen egy parancssor grafikája látható.

![A vizualizáció kiválasztása](media/power-bi-custom-visuals-troubleshoot/powerbi-developer-visual-selection.png)

Ha ez nincs ott, akkor valószínűleg engedélyeznie kell a Power BI beállításai között.

> [!NOTE]
> A vizualizáció hibakeresése jelenleg csak a Power BI szolgáltatásban érhető el, a Power BI Desktopban és a mobilappan nem. A csomagolt vizualizáció ennek ellenére minden platformon működik.

**Nem lehet kapcsolatot létesíteni a vizualizáció kiszolgálójával**

Futtassa a vizualizáció kiszolgálóját. Ehhez adja ki a terminálon/parancsorból a `pbiviz start` parancsot a vizualizáció projektjének gyökérmappájából. Ha a kiszolgáló nem fut, akkor valószínűleg nincsenek helyesen telepítve az SSL-tanúsítványok.

Ha bármilyen kérdése, megjegyzése vagy problémája van, vegye fel a kapcsolatot a Power BI-vizualizációk csapatával a pbicvsupport@microsoft.com címen.

## <a name="next-steps"></a>További lépések

További információt [a Power BI-vizualizációkkal kapcsolatos gyakori kérdések](power-bi-custom-visuals-faq.md#organizational-power-bi-visuals) között talál.