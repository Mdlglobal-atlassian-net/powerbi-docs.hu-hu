---
title: A Power BI szolgáltatás és a Power BI Desktop jelentésvizualizációinak áttekintése
description: A Microsoft Power BI jelentésvizualizációinak áttekintése.
author: mihart
ms.author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: SYk_gWrtKvM
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/28/2019
LocalizationGroup: Visualizations
ms.openlocfilehash: d470a262bd8a5e6590746fb07889b1230f5cfc25
ms.sourcegitcommit: 8bf2419b7cb4bf95fc975d07a329b78db5b19f81
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66375669"
---
# <a name="visualizations-in-power-bi-reports"></a>Vizualizációk Power BI-jelentésekben

A vizualizációk az adatokból nyert információkat jelenítik meg. Egy Power BI-jelentés állhat egyetlen oldalból, amelyen csak egy vizualizáció szerepel, de előfordulhatnak olyan jelentések is, amelyek számos vizualizációt tartalmazó oldalakból állnak. A Power BI szolgáltatásban a vizualizációkat [jelentésekből irányítópultokra lehet rögzíteni](../service-dashboard-pin-tile-from-report.md).

Fontos, hogy a jelentés közötti különbséget tenni *tervezők* és a jelentés *fogyasztók* Ön hozza létre, és módosítja a jelentést, akkor egy konfigurációtervezővel áll.  Tervezők szerkesztési engedélye a jelentés és az alapul szolgáló adatkészlethez. A Power BI Desktopban ez azt jelenti, hogy megnyithatja az adatkészletet Adatnézetben, és vizualizációkat hozhat létre Jelentés nézetben. A Power BI szolgáltatásban, ez azt jelenti, hogy az adatkészlet vagy jelentés megnyithatja a Power bi [szerkesztési nézetben](../consumer/end-user-reading-view.md). Ha a jelentést vagy az irányítópultot [megosztották Önnel](../consumer/end-user-shared-with-me.md), akkor Ön a jelentés **felhasználója**. Is elérheti a használatával megtekinthetik és használhatják a jelentést, és a benne lévő vizualizációkat, de nem tudja menteni a fontosabb változását foglalja össze.

A Power BI VIZUALIZÁCIÓK paneljén számos különféle típusú vizualizáció érhető el.

![](media/power-bi-report-visualizations/power-bi-templates.png)

A [Microsoft AppSource közösségi oldalon](https://appsource.microsoft.com) azonban még nagyobb választékban talál [letölthető](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) [egyéni vizualizációkat](../developer/custom-visual-develop-tutorial.md), amelyeket a Microsoft és a közösség tett elérhetővé.

<iframe width="560" height="315" src="https://www.youtube.com/embed/SYk_gWrtKvM?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>


  Ha még nem használta a Power BI-t, vagy fel szeretné frissíteni a tudását, az alábbi hivatkozásokat követve megismerkedhet a Power BI-vizualizációk használatának alapfogalmaival.  A (cikk bal oldalán látható) Tartalomjegyzék alapján további hasznos információkhoz juthat.

## <a name="add-a-visualization-in-power-bi"></a>Vizualizáció hozzáadása a Power BI-ban

A jelentések oldalain különböző [vizualizációkat hozhat létre](power-bi-report-add-visualizations-i.md). Böngésszen [az elérhető vizualizációk és a rájuk vonatkozó oktatóanyagok](power-bi-visualization-types-for-reports-and-q-and-a.md) között. 

## <a name="upload-a-custom-visualization-and-use-it-in-power-bi"></a>Egyéni vizualizáció feltöltése és használata a Power BI-ban

Önállóan létrehozott vagy a [Microsoft AppSource közösségi webhelyéről](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals) letöltött egyéni vizualizációkat is használhat. Kreatív kedvében van? Merüljön el a forráskódban, és használja [fejlesztői eszközeinket](../developer/custom-visual-develop-tutorial.md) egy új típusú vizualizáció létrehozásához, amelyet aztán [a közösség többi tagjával is megoszthat](../developer/office-store.md). Az egyéni vizualizációk fejlesztéséről az [Egyéni Power BI-vizualizáció fejlesztése](../developer/custom-visual-develop-tutorial.md) című cikkben található további információ.

## <a name="change-the-visualization-type"></a>Vizualizáció típusának módosítása

Próbálkozhat [a vizualizáció típusának módosításával](power-bi-report-change-visualization-type.md), hogy megtalálja azt, amelyik a legjobban illik az adataihoz.

## <a name="pin-the-visualization"></a>A vizualizáció rögzítése

Ha a vizualizáció pont úgy néz ki, ahogy szeretné, a Power BI szolgáltatásban csempeként [rögzítheti az irányítópultra](../service-dashboard-pin-tile-from-report.md). Ha rögzítés után megváltoztatja a jelentésben használt vizualizációt, az irányítópulton lévő csempe nem változik. Ha például vonaldiagram volt, akkor az is marad, noha a jelentésben fánkdiagrammá alakította át.

## <a name="limitations-and-considerations"></a>Korlátozások és szempontok
- Az adatforrás és a mezők (mértékeket és oszlopokat) száma, attól függően egy vizualizációt az lassan előfordulhat, hogy betölteni.  Azt javasoljuk, hogy korlátozza a Vizualizációk 10 – 20 összesített mezőkhöz, mind az olvashatóság érdekében és teljesítmény érdekében. 

- A Vizualizációk felső korlátjának 100 mezők (mértékeket és oszlopokat). Ha nem sikerül betölteni a Vizualizáció, csökkentheti a mezők számát.   

## <a name="next-steps"></a>Következő lépések

* [Vizualizációtípusok a Power BI-ban](power-bi-visualization-types-for-reports-and-q-and-a.md)
* [Egyéni vizualizációk](../power-bi-custom-visuals.md)