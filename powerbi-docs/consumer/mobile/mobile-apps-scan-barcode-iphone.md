---
title: Vonalkód beolvasása a Power BI mobilalkalmazásból
description: Beolvashatja a való világbeli vonalkódokat, hogy közvetlenül a szűrt BI-adatokhoz jusson a Power BI mobilalkalmazásban.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 12/02/2019
ms.author: painbar
ms.openlocfilehash: 043f27a2fb695811ac867689b4a63efdefded2e6
ms.sourcegitcommit: 9b806dfe62c2dee82d971bb4f89d983b97931b43
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/07/2020
ms.locfileid: "80802049"
---
# <a name="scan-a-barcode-with-your-device-from-the-power-bi-mobile-app"></a>Vonalkód beolvasása saját eszközzel a Power BI mobilalkalmazásból
Beolvashatja a való világbeli vonalkódokat, hogy közvetlenül a szűrt BI-adatokhoz jusson a Power BI mobilalkalmazásban.


A következőkre vonatkozik:

| ![iPhone](./media/mobile-apps-qr-code/ios-logo-40-px.png) | ![iPadek](./media/mobile-apps-qr-code/ios-logo-40-px.png) | ![Android rendszerű telefon](././media/mobile-apps-qr-code/android-logo-40-px.png) | ![Android rendszerű táblagép](././media/mobile-apps-qr-code/android-logo-40-px.png) |
|:--- |:--- |:--- |:--- |
|iPhone-ok |iPadek |Android rendszerű telefonok |Android rendszerű táblagépek |

Tegyük fel, hogy az egyik munkatársa [megcímkézett egy vonalkódmezőt egy jelentésben a Power BI Desktopban](../../desktop-mobile-barcodes.md), majd megosztotta ezt a jelentést Önnel. 

![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-scanner.png)

Amikor beolvassa egy termék vonalkódját a Power BI alkalmazás olvasójával az eszközén, megjelenik a vonalkódot tartalmazó jelentés (vagy a jelentések listája). Ezt a jelentést megnyithatja a vonalkód alapján szűrve.

## <a name="scan-a-barcode-with-the-power-bi-scanner"></a>Vonalkód beolvasása a Power BI-olvasóval
1. A navigációs sávon koppintson a **További beállítások** (...) lehetőségre, majd a **Vizsgálat** elemre.

    ![](media/mobile-apps-scan-barcode-iphone/power-bi-scanner.png)

2. Ha a kamera nincs engedélyezve, engedélyeznie kell, hogy a Power BI alkalmazás használhassa azt. Ezt csak egyszer kell megtennie. 
4. Irányítsa az olvasót egy termék vonalkódjára. Ekkor megjelenik a vonalkódhoz társított jelentések listája.
5. A jelentés nevére koppintva megnyithatja az adott jelentést az eszközén, a vonalkód alapján automatikusan szűrve.

## <a name="filter-by-other-barcodes-while-in-a-report"></a>A jelentés szűrése más vonalkódok alapján
Az eszközön megtekintett, vonalkód alapján szűrt jelentést más vonalkódok alapján is szűrheti.

* Ha a vonalkód ikonon szűrő ![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-filtered-icon-black.png) látható, akkor a szűrő aktív, és a jelentés már szűrve van egy vonalkód alapján. 
* Ha az ikon nem tartalmaz szűrőt ![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-unfiltered-icon.png), akkor a szűrő nem aktív, és a jelentés nincs vonalkód alapján szűrve. 

Bárhogy is van, koppintson az ikonra, és megnyílik egy kisméretű menü úszó olvasóval.

* Fókuszálja az olvasót az új elemre a jelentés szűrőjének egy másik vonalkódértékre való megváltoztatásához. 
* Válassza a **Vonalkódszűrő törlése** lehetőséget a nem szűrt jelentéshez való visszatéréshez.
* Koppintson a **Szűrés a legutóbbi vonalkódok alapján** pontra a jelentés szűrőjének a jelenlegi munkamenetben beolvasott egyik vonalkódra váltásához.

## <a name="issues-with-scanning-a-barcode"></a>Problémák a vonalkód beolvasásakor
Íme néhány üzenet, melyeket egy termék vonalkódjának beolvasásakor láthat.

### <a name="couldnt-filter-report"></a>„A jelentés szűrése nem sikerült...”
A jelentés, amelynek a szűrését választotta olyan adatmodellen alapul, amely ezt a vonalkódértéket nem tartalmazza. A „mineral water” (ásványvíz) termék például nem szerepel a jelentésben.  

### <a name="allsome-of-the-visuals-in-the-report-dont-contain-any-value"></a>A jelentés vizualizációi vagy azok egy része semmilyen értéket sem tartalmaz
A beolvasott vonalkódérték megtalálható a modellben, de a jelentés vizualizációi vagy azok egy része ezt az értéket nem tartalmazza, ezért a szűrés üres állapotot ad vissza. Próbáljon meg más jelentésoldalakon keresni, vagy szerkessze a jelentést a Power BI Desktopban, hogy tartalmazza ezt az értéket. 

### <a name="looks-like-you-dont-have-any-reports-that-can-be-filtered-by-barcodes"></a>„Úgy tűnik, hogy nem rendelkezik olyan jelentéssel, amelyet vonalkódok alapján lehetne szűrni.”
Ez azt jelenti, hogy nincs egyetlen jelentés sem, amelyben engedélyezett lenne a vonalkódok használata. A vonalkódolvasó csak azokat a jelentéseket tudja szűrni, amelyekben van **Barcode** (Vonalkód) megjelölésű oszlop.  

Győződjön meg róla, hogy Ön vagy a jelentés tulajdonosa **Barcode** (Vonalkód) címkével látott el egy oszlopot a Power BI Desktopban. További tudnivalók a [vonalkódmezők Power BI Desktopban való címkézéséről](../../desktop-mobile-barcodes.md)

### <a name="couldnt-filter-report---looks-like-this-barcode-doesnt-exist-in-the-report-data"></a>„A jelentés szűrése nem sikerült – Úgy tűnik, ez a vonalkód nem szerepel a jelentés adatai között.”
A jelentés, amelynek a szűrését választotta olyan adatmodellen alapul, amely ezt a vonalkódértéket nem tartalmazza. A „mineral water” (ásványvíz) termék például nem szerepel a jelentésben. Beolvashat egy másik terméket, választhat másik jelentést (ha több jelentés is rendelkezésre áll), vagy megtekintheti a jelentést szűrés nélkül. 

## <a name="next-steps"></a>Következő lépések
* [Vonalkódmező címkézése a Power BI Desktopban](../../desktop-mobile-barcodes.md)
* [A Power BI-irányítópultok csempéi](../end-user-tiles.md)
* [A Power BI-irányítópultok](../end-user-dashboards.md)

