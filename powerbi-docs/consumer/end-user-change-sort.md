---
title: A diagramok rendezésének módosítása egy Power BI-jelentésben
description: A diagramok rendezésének módosítása egy Power BI-jelentésben
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: Conceptual
ms.date: 09/20/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: f4ca6633eb401e7df8041ea385284210c14995ad
ms.sourcegitcommit: 4f46d71ff6026c1c158f007425aefdcb501f48ee
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/06/2018
ms.locfileid: "52979337"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>A diagramok rendezésének módosítása egy Power BI-jelentésben
A Power BI-jelentésekben a legtöbb vizualizációt rendezheti a kategóriáinak neve alapján betűrendben vagy az egyes kategóriák számértéke szerint. Ez a diagram például az **üzlet neve** kategória szerint van rendezve.

![](media/end-user-change-sort/pbi_chartsortcategory.png)

A rendezés könnyedén módosítható egy kategóriáról (store name – üzlet neve) egy értékre (sales per square feet – értékesítés négyzetlábanként).

1. Kattintson a három pontra (...), és majd a **Rendezés szempontja: Eladások négyzetméterenként** lehetőségre.
2. Ha szükséges, kattintson újra a három pontra, majd a **Rendezés csökkenő sorrendben** lehetőségre.

   ![](media/end-user-change-sort/sort.gif)

   **MEGJEGYZÉS**: Nem minden vizualizáció rendezhető.  A következő vizualizációkat például nem lehet rendezni: Fatérkép, térkép, kartogram, pontdiagram, mérőműszer, kártya, többsoros kártya, vízesés.

## <a name="saving-changes-you-make-to-sort-order"></a>A rendezési sorrend módosításainak mentése
A Power BI-jelentések megőrzik a szűrőket, a szeletelőket, a rendezést és az adatnézetek egyéb módosításait. Így ha kilép egy jelentésből, majd később visszatér, a módosítások mentve lesznek.  Ha szeretné visszaállítani a módosításokat a jelentés létrehozójának beállításaira, válassza a **Visszaállítás alapértelmezettre** lehetőséget a felső menüsorban. 

![megőrzött rendezés](media/end-user-change-sort/power-bi-reset-to-default.png)

Ha azonban a **Visszaállítás alapértelmezettre** gomb szürke színnel jelenik meg, az azt jelenti, hogy a jelentés létrehozója letiltotta a módosítások mentésének (megőrzésének) lehetőségét.

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>Rendezés más feltételek alapján
Néha más mező vagy feltétel használatával szükséges rendezni a vizualizációt.  Rendezhet például hónapok (és nem betűrend) alapján, vagy a teljes számok és nem az egyes számjegyek alapján is (például, 0, 1, 9, 20, nem pedig 0, 1, 20, 9).  

Bizonyos esetekben lehetséges a vizualizációk kívánt feltétel, például hónap szerinti rendezése.  Ha ez nem lehetséges, szükséges lehet a jelentés alapjául szolgáló adatkészlet módosítása. Kérje meg a jelentés létrehozóját az adathalmaz frissítésére.

## <a name="next-steps"></a>Következő lépések
További információk [a Power BI-jelentésekben lévő vizualizációkról](end-user-visualizations.md).

[Power BI – Alapfogalmak](end-user-basic-concepts.md)