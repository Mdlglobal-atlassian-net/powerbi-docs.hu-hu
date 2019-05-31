---
title: Elemleírások testreszabása a Power BI Desktopban
description: Egyéni elemleírások létrehozása a vizualizációkhoz az összetevők húzásával
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: d5259ba22287a8a2ade3107e4320c39713dcb45e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65239739"
---
# <a name="customizing-tooltips-in-power-bi-desktop"></a>Elemleírások testreszabása a Power BI Desktopban
Az elemleírások használatával elegáns módon lehet kiegészítő környezeti információkat és részleteket megjeleníteni a vizualizációkban lévő adatpontokról. Az alábbi képen egy diagramhoz hozzáadott elemleírás látható a Power BI Desktopban.

![Alapértelmezett elemleírás](media/desktop-custom-tooltips/custom-tooltips-1.png)

A képi megjelenítés létrehozásakor az alapértelmezett elemleírás az adatpont értékét és kategóriáját jeleníti meg. Nincsenek számos hasznos az elemleírásban megjelenő információk testreszabása, és valószínűleg tartalmaz olyan további kontextus és információk biztosíthatók a vizualizációt megtekintő felhasználóknak. Az egyéni elemleírásokkal további adatpontokat adhat meg, amelyek az elemleírás részeként jelennek meg.

## <a name="how-to-customize-tooltips"></a>Az elemleírások testreszabása
Hozhat létre egy egyéni elemleírás a **mezők** , valamint a **Vizualizációk** ablaktáblán húzzon egy mezőt a **elemleírások** gyűjtőbe, akkor az alábbi képen látható. Az alábbi ábrán két mező van az **Elemleírások** gyűjtőbe húzva.

![Elemleírás-mezők hozzáadása](media/desktop-custom-tooltips/custom-tooltips-2.png)

Miután hozzáadta az Elemleírásokat a Mezők területen, a kurzort a képi megjelenítés adatpontjai fölé mozgatva az adott mezők értékei megjelennek az elemleírásban.

![Egyéni elemleírás](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-calcs"></a>Elemleírások testreszabása összesítésekkel és gyors számításokkal
Lehetősége van az eszközelemek további testreszabására aggregátumfüggvények vagy *gyors számítások* kiválasztásával. Ehhez kattintson az **Elemleírás** gyűjtő melletti nyílra, majd válasszon az elérhető lehetőségek közül.

![Elemleírás Gyorsszámítással](media/desktop-custom-tooltips/custom-tooltips-4.png)

Számos módon szabhatja testre **elemleírások**, közvetíteni gyors információk és az irányítópultokat és jelentéseket megtekintő felhasználók számára elérhető, az adatkészlet bármely mező használatával.

