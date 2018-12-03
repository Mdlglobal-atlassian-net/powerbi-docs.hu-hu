---
title: Elemleírások testreszabása a Power BI Desktopban
description: Egyéni elemleírások létrehozása a vizualizációkhoz az összetevők húzásával
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: faabacabbd20930f90187f4c21fe539d61b3d678
ms.sourcegitcommit: 05303d3e0454f5627eccaa25721b2e0bad2cc781
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52578819"
---
# <a name="customizing-tooltips-in-power-bi-desktop"></a>Elemleírások testreszabása a Power BI Desktopban
Az elemleírások használatával elegáns módon lehet kiegészítő környezeti információkat és részleteket megjeleníteni a vizualizációkban lévő adatpontokról. Az alábbi képen egy diagramhoz hozzáadott elemleírás látható a Power BI Desktopban.

![Alapértelmezett elemleírás](media/desktop-custom-tooltips/custom-tooltips-1.png)

A képi megjelenítés létrehozásakor az alapértelmezett elemleírás az adatpont értékét és kategóriáját jeleníti meg. Számos esetben bizonyulhat hasznosnak az elemleírásban megjelenő információk testreszabása, mivel így további kontextus és információk biztosíthatók a vizualizációt megtekintő felhasználóknak. Az egyéni elemleírásokkal további adatpontokat adhat meg, amelyek az elemleírás részeként jelennek meg.

## <a name="how-to-customize-tooltips"></a>Az elemleírások testreszabása
Az elemleírások testreszabásához a **Képi megjelenítések** ablaktábla **Mezők** területén egyszerűen húzzon át egy mezőt az **Elemleírások** gyűjtőbe az alábbi ábrán látható módon. Az alábbi ábrán két mező van az **Elemleírások** gyűjtőbe húzva.

![Elemleírás-mezők hozzáadása](media/desktop-custom-tooltips/custom-tooltips-2.png)

Miután hozzáadta az Elemleírásokat a Mezők területen, a kurzort a képi megjelenítés adatpontjai fölé mozgatva az adott mezők értékei megjelennek az elemleírásban.

![Egyéni elemleírás](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-calcs"></a>Elemleírások testreszabása összesítésekkel és gyors számításokkal
Lehetősége van az eszközelemek további testreszabására aggregátumfüggvények vagy *gyors számítások* kiválasztásával. Ehhez kattintson az **Elemleírás** gyűjtő melletti nyílra, majd válasszon az elérhető lehetőségek közül.

![Elemleírás Gyorsszámítással](media/desktop-custom-tooltips/custom-tooltips-4.png)

Az **Elemleírások** számos módon testreszabhatók az adatkészlet bármely elérhető mezőjének használatával, így gyors információk és betekintések biztosíthatók az irányítópultokat és a jelentéseket megtekintő felhasználók számára.

