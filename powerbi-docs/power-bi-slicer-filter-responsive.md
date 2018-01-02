---
title: "Átméretezhető rugalmas szeletelő létrehozása a Power BI-ban"
description: "Útmutató egy olyan szeletelő létrehozásához, mely átméretezhető a jelentésnek megfelelően"
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/08/2017
ms.author: maggies
ms.openlocfilehash: f95f126cc6a7c95fbe3227b712281a7d3f81e320
ms.sourcegitcommit: b780b7108fd9b52398b8377b52836f0e0fedc96e
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/09/2017
---
# <a name="create-a-responsive-slicer-you-can-resize-in-power-bi-preview"></a>Átméretezhető rugalmas szeletelő létrehozása a Power BI-ban (Előzetes verzió)

A rugalmas szeletelők a jelentés tetszőleges területének megfelelően átméretezhetők. Ha rugalmas szeletelőket használ, azokat különböző méretekre és vízszintes, négyzetes vagy függőleges alakzatokra méretezheti át, és a szeletelő értékei eközben automatikusan átrendeződnek. A Power BI Desktopban és a Power BI szolgáltatásban is rugalmassá tehet vízszintes szeletelőket és dátumtartomány-szeletelőket. A dátumtartomány-szeletelők emellett továbbfejlesztett érintéses területtel rendelkeznek, így könnyebben módosíthatók egyetlen érintéssel. A rugalmas szeletelők tetszőleges méretűre állíthatók; emellett a rendszer automatikusan átméretezi őket, hogy megfelelően illeszkedjenek a jelentésekbe a Power BI szolgáltatásban, illetve a Power BI-mobilalkalmazásokban is. 

![A rugalmas szeletelők számos különböző alakúak lehetnek](media/power-bi-slicer-filter-responsive/responsive-slicer-gif.gif)

## <a name="create-a-slicer"></a>Szeletelő létrehozása

A dinamikus szeletelők létrehozásának első lépése egy egyszerű szeletelő létrehozása. 

1. Válassza a **Szeletelő** ikont ![Szeletelő ikon](media/power-bi-slicer-filter-responsive/power-bi-slicer-icon.png) a **Megjelenítések** ablaktáblán.
2. Húzza a szűrni kívánt mezőt a **Mező** lehetőségre.

    ![Mező hozzáadása a szeletelőhöz](media/power-bi-slicer-filter-responsive/power-bi-slicer-field.png)

## <a name="convert-to-a-horizontal-slicer"></a>Átalakítás vízszintes szeletelővé

1. Válassza ki a szeletelőt, majd a **Megjelenítések** ablaktáblán válassza a **Formátum** lapot.
2. Bontsa ki az **Általános** szakaszt, majd a **Tájolás** beállításnál válassza a **Vízszintes** lehetőséget.

    ![A szeletelő vízszintesre állítása](media/power-bi-slicer-filter-responsive/power-bi-slicer-horizontal.png) 

1.  Érdemes szélesebbre állítania, hogy több érték jelenjen meg.

     ![A szeletelő szélesebbre állítása](media/power-bi-slicer-filter-responsive/power-bi-slicer-wide-horizontal.png)

## <a name="make-it-responsive-and-experiment-with-it"></a>Rugalmassá tétel és kísérletezés

Ez egy könnyű lépés. 

1. A **formátum** lap **Általános** szakaszában közvetlenül a **Tájolás** alatt állítsa a **Rugalmas (Előzetes verzió)** csúszkát a **Bekapcsolva** értékre.  

    ![A szeletelő mostantól rugalmas](media/power-bi-slicer-filter-responsive/power-bi-slicer-wide-responsive.png)

1. Most már kísérletezhet vele. A sarkok húzásával rövidre, hosszúra, szélesre vagy keskenyre állíthatja. Ha kellően kicsire állítja, akkor csupán egy szűrőikon lesz belőle.

    ![Egy olyan kicsi rugalmas szeletelő, amely már csak egy szűrőikon](media/power-bi-slicer-filter-responsive/power-bi-slicer-small-filter-icon.png)

## <a name="add-it-to-a-phone-report-layout"></a>Hozzáadás egy telefonos jelentéselrendezéséhez

A Power BI Desktopban egy jelentés minden egyes oldalához létrehozhat egy telefonos elrendezést. Ha egy oldal rendelkezik telefonos elrendezéssel, az álló nézetben jelenik meg mobiltelefonokon. Ellenkező esetben fekvő nézetben kell azt megtekinteni. 

1. A **Nézet** menüben válassza a **Telefonos elrendezés** lehetőséget.

     ![Telefonos elrendezés ikon, Nézet menü](media/power-bi-slicer-filter-responsive/power-bi-phone-layout-menu.png)
    
1. Húzzon minden, a telefonos jelentésben használni kívánt látványelemet a rácsra. A rugalmas szeletelő húzásakor állítsa azt tetszőleges méretűre – ebben az esetben olyanra, hogy csak egy szűrőikon legyen.

    ![A szeletelő hozzáadása a telefonos jelentéselrendezéshez](media/power-bi-slicer-filter-responsive/power-bi-slicer-phone-layout.png)

További információk [a Power BI-mobilalkalmazásokra optimalizált jelentések létrehozásáról](desktop-create-phone-report.md).

## <a name="make-a-time-or-range-slicer-responsive"></a>Idő- vagy tartományszeletelő rugalmassá tétele

Ugyanezekkel a lépésekkel tehet rugalmassá egy csempe- vagy tartományszeletelőt is. Miután a **Rugalmas** beállítást a **Bekapcsolva** értékre állította, észrevehet néhány dolgot:

- A látványelemek a vásznon engedélyezett mérettől függően optimalizálják a beviteli mezők sorrendjét. 
- A rendszer úgy optimalizálja az adatelemek megjelenítését, hogy a szeletelő a lehető legjobban használható legyen a vásznon engedélyezett mérete alapján. 
- A csúszkák érintéses műveletei új kerek fogantyúkkal vannak optimalizálva. 
- Amikor egy látványelem túl kicsi ahhoz, hogy használható legyen, a helyén megjelenő és a látványelem típusát jelölő ikonná alakul. Ennek használatához egyszerűen koppintson rá duplán a fókusz módban való megnyitásához. Ezzel értékes helyet takaríthat meg a jelentésoldalon funkciók elvesztése nélkül.

## <a name="next-steps"></a>Következő lépések

- [Útmutató: Szeletelők a Power BI szolgáltatásban](power-bi-visualization-slicers.md)
- További kérdései vannak? [Kérdezze meg a Power BI-közösséget](http://community.powerbi.com/)