---
title: Az egyéni Power BI-vizualizációk fejlesztésekor jelentkező hibák elhárítása
description: Ez cikk bemutat néhány olyan gyakori problémát, amely egyéni Power BI-vizualizációk fejlesztése és létrehozása közben jelentkezhet.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 11/06/2018
ms.openlocfilehash: 252b980b3a10bbafc29c36ad249b23166fb514f1
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54286565"
---
# <a name="troubleshoot-power-bi-custom-visuals"></a>Az egyéni Power BI-vizualizációk hibáinak elhárítása

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

Ha bármilyen kérdése, megjegyzése vagy problémája van, vegye fel a kapcsolatot az egyéni vizualizációk csapatával a  *pbicvsupport@microsoft.com*  címen.

## <a name="next-steps"></a>Következő lépések

További információt [az egyéni Power BI-vizualizációkkal kapcsolatos gyakori kérdések](power-bi-custom-visuals-faq.md#organizational-custom-visuals) között talál.
