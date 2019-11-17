---
title: A diagramok rendezésének módosítása egy jelentésben
description: A diagramok rendezésének módosítása egy Power BI-jelentésben
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/28/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: e325d13dd8001e8da41dc5602bf3f7dbba2f371f
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73852372"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>A diagramok rendezésének módosítása egy Power BI-jelentésben

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

A Power BI szolgáltatásban módosíthatja egy vizualizáció kinézetét, ha különböző adatmezők szerint rendezi. A vizualizáció rendezésének módosításával kiemelheti a közvetíteni kívánt információt, és biztosíthatja, hogy a vizualizáció tükrözze ezt a trendet (vagy hangsúlyt).

Akár numerikus adatokat használ (például értékesítési adatokat), akár szöveges adatokat (például államneveket), tetszése szerint rendezheti a vizualizációkat és az adatok megjelenését. A Power BI nagyon rugalmas rendezhetőséget és egyszerűen használható menüket biztosít. Bármely vizualizáción válassza a **További műveletek** (...) lehetőséget, majd válassza ki a mezőt, amely alapján rendezni szeretne.

![sávdiagram ábécé szerint rendezett X-tengellyel](media/end-user-change-sort/power-bi-more-actions.png)

Az irányítópultokon szereplő vizualizációkat nem lehet rendezni, a Power BI-jelentésekben viszont a legtöbb vizualizációt rendezheti a kategóriáinak neve alapján betűrendben vagy az egyes kategóriák számértéke szerint. Ez a diagram például a **store name** (üzlet neve) kategória szerint van ábécésorrendbe rendezve.

![sávdiagram ábécé szerint rendezett X-tengellyel](media/end-user-change-sort/pbi-chartsortcategory.png)

A rendezés könnyedén módosítható egy kategóriáról (store name – üzlet neve) egy értékre (sales per square feet – értékesítés négyzetlábanként).

1. Válassza a **További műveletek** (...), majd a **Rendezési szempont > Sales Per Sq Ft** (Eladások négyzetméterenként) lehetőséget.
2. Ha szükséges, válassza újból a **További műveletek** (...), majd a **Csökkenő rendezés** lehetőséget. A rendezéshez használt mező félkövérrel szedve és egy sárga sávval jelenik meg.

   ![videó emelkedő, majd csökkenő sorrendű rendezés kiválasztásáról](media/end-user-change-sort/sort.gif)

> [!NOTE]
> Nem minden vizualizáció rendezhető. A következő vizualizációkat például nem lehet rendezni: fatérkép, térkép, kartogram, pontdiagram, mérőműszer, kártya, vízesés.

## <a name="saving-changes-you-make-to-sort-order"></a>A rendezési sorrend módosításainak mentése
A Power BI-jelentések megőrzik a szűrőket, a szeletelőket, a rendezést és az adatnézetek egyéb módosításait. Így ha kilép egy jelentésből, majd később visszatér, a módosítások mentve lesznek.  Ha szeretné visszaállítani a módosításokat a jelentés tervezőjének beállításaira, válassza a **Visszaállítás alapértelmezettre** lehetőséget a felső menüsávon. 

![megőrzött rendezés](media/end-user-change-sort/power-bi-reset.png)

Ha azonban a **Visszaállítás alapértelmezettre** gomb szürke színnel jelenik meg, az azt jelenti, hogy a jelentés tervezője letiltotta a módosítások mentésének (megőrzésének) lehetőségét.

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>Rendezés más feltételek alapján
Néha más (a vizualizációban nem szereplő) mező vagy más feltételek használatával szükséges rendezni a vizualizációt.  Rendezhet például hónapok (és nem betűrend) alapján, vagy a teljes számok és nem az egyes számjegyek alapján is (például, 0, 1, 9, 20, nem pedig 0, 1, 20, 9).  A jelentéstervező frissítheti az adathalmazt az ilyen típusú rendezés engedélyezéséhez. A tervező kapcsolattartási adatai a fejléc sávban a jelentés nevét választva találhatók meg.

![A kapcsolattartási adatokat megjelenítő legördülő lista](media/end-user-change-sort/power-bi-contact.png)

## <a name="next-steps"></a>Következő lépések
További információk [a Power BI-jelentésekben lévő vizualizációkról](end-user-visualizations.md).

[Power BI – Alapfogalmak](end-user-basic-concepts.md)
