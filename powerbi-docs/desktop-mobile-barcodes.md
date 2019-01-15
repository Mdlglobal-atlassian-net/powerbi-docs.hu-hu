---
title: Vonalkód mező címkézése mobilalkalmazásokhoz a Power BI Desktopban
description: Ha felcímkéz egy vonalkódmezőt a modellben a Power BI Desktopban, automatikusan szűrheti az adatokat vonalkód szerint az iPhone-ja Power BI alkalmazásában.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/16/2018
ms.author: maggies
LocalizationGroup: Model your data
ms.openlocfilehash: 584947dcd92078ea025468f5a38fc7fed3e2616a
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54289900"
---
# <a name="tag-barcodes-in-power-bi-desktop-for-the-mobile-apps"></a>Vonalkódok címkézése mobilalkalmazásokhoz a Power BI Desktopban
A Power BI Desktopban [kategorizálhatja](desktop-data-categorization.md) egy oszlop adatait, így a Power BI Desktop tudja, hogyan kezelje az értékeket egy jelentésben a vizualizációkban. Kategorizálhat egy oszlopot is **Vonalkódként**. Ha akár Ön, akár a kollégái [beolvassák egy termék vonalkódját a Power BI alkalmazással](consumer/mobile/mobile-apps-scan-barcode-iphone.md) egy iPhone-on, megjelenik az összes, az adott vonalkódot tartalmazó jelentés. Amikor megnyitja a jelentést a mobilalkalmazásban, a Power BI automatikusan szűri a jelentést az adott vonalkódhoz kapcsolódó adatokra.

1. A Power BI Desktopban váltson Adatnézetre.
2. Válasszon egy vonalkódadatokat tartalmazó oszlopot. A [támogatott vonalkódformátumok](#supported-barcode-formats) megtalálhatók alább.
3. A **Modellezés** lapon válassza az **Adatkategória** > **Vonalkód** lehetőséget.
   
    ![Adatkategória lista](media/desktop-mobile-barcodes/power-bi-desktop-barcode.png)
4. A Jelentés nézetben adja hozzá ezt a mezőt a vonalkód szerint szűrni kívánt vizualizációkhoz.
5. Mentse a jelentést, és tegye közzé a Power BI szolgáltatásban.

Most már, ha megnyitja a beolvasót az [iPhone-ra készült Power BI alkalmazásban](consumer/mobile/mobile-iphone-app-get-started.md), és beolvas egy vonalkódot, megjelenik ez a jelentés a jelentések listájában. Amikor megnyitja a jelentést, a benne lévő vizualizációkat az alkalmazás a beolvasott termékvonalkód alapján szűri.

## <a name="supported-barcode-formats"></a>Támogatott vonalkódformátumok
A Power BI a következő vonalkódokat ismeri fel, ha felcímkézi őket a Power BI-jelentésben: 

* UPCECode 
* Code39Code  
* A39Mod43Code 
* EAN13Code 
* EAN8Code  
* 93Code  
* 128Code 
* PDF417Code 
* Interleaved2of5Code 
* ITF14Code 

## <a name="next-steps"></a>További lépések
* [Vonalkód beolvasása az iPhone-ján lévő Power BI alkalmazásból](consumer/mobile/mobile-apps-scan-barcode-iphone.md)
* [Problémák az iPhone-on történő vonalkód-leolvasás során](consumer/mobile/mobile-apps-scan-barcode-iphone.md#issues-with-scanning-a-barcode)
* [Adatok kategorizálása a Power BI Desktopban](desktop-data-categorization.md)  
* Kérdése van? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

