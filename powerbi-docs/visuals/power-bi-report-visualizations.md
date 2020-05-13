---
title: A Power BI szolgáltatás és a Power BI Desktop jelentésvizualizációinak áttekintése
description: A Microsoft Power BI jelentésvizualizációinak áttekintése.
author: mihart
ms.author: mihart
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/05/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: 65a6ab132cccc56d96f5ac22fef5d80f59f96ca9
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83277548"
---
# <a name="visualizations-in-power-bi-reports"></a>Vizualizációk Power BI-jelentésekben

[!INCLUDE[consumer-appliesto-yyyn](../includes/consumer-appliesto-yyyn.md)]    

A vizualizációk az adatokból nyert megállapításokat jelenítik meg. Egy Power BI-jelentés állhat egyetlen oldalból, amelyen csak egy vizualizáció szerepel, de előfordulhatnak olyan jelentések is, amelyek számos vizualizációt tartalmazó oldalakból állnak. A Power BI szolgáltatásban a vizualizációkat a [jelentésekből irányítópultokra lehet rögzíteni](../create-reports/service-dashboard-pin-tile-from-report.md).

Fontos különbséget tenni a *jelentéstervezők* és a *jelentésfelhasználók* között.  Ha Ön az a személy, akik a jelentést létrehozza vagy módosítja, akkor Ön tervező.  A tervezőknek szerkesztési jogosultságuk van a jelentéshez és az alapul szolgáló adathalmazhoz. A Power BI Desktopban ez azt jelenti, hogy megnyithatja az adatkészletet Adatnézetben, és vizualizációkat hozhat létre Jelentés nézetben. A Power BI szolgáltatásban ez azt jelenti, hogy megnyithatja az adathalmazt vagy a jelentést a jelentésszerkesztőben [Szerkesztési nézetben](../consumer/end-user-reading-view.md). Ha a jelentést vagy az irányítópultot [megosztották Önnel](../consumer/end-user-shared-with-me.md), akkor Ön a jelentés *felhasználója*. A jelentést és a rajta szereplő vizualizációkat megtekintheti és használhatja, de nem végezhet annyi módosítást, amennyit egy *tervező*.

A Power BI Vizualizációk paneljén számos különféle típusú vizualizáció érhető el.

![az egyes vizualizációs típusok ikonjait tartalmazó ablaktábla](media/power-bi-report-visualizations/power-bi-icons.png)

Még nagyobb választékot talál a [Microsoft AppSource közösség webhelyén](https://appsource.microsoft.com), ahol a Microsoft és a közösség által kínált [Power BI-vizualizációkat](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) kereshet meg és [tölthet le](../developer/visuals/custom-visual-develop-tutorial.md).

Ha még nem használta a Power BI-t, vagy fel szeretné frissíteni a tudását, az alábbi hivatkozásokat követve megismerkedhet a Power BI-vizualizációk használatának alapfogalmaival.  A (cikk bal oldalán látható) Tartalomjegyzék alapján további hasznos információkhoz juthat.

## <a name="add-a-visualization-in-power-bi"></a>Vizualizáció hozzáadása a Power BI-ban

A jelentések oldalain különböző [vizualizációkat hozhat létre](power-bi-report-add-visualizations-i.md). Böngésszen [az elérhető vizualizációk és a rájuk vonatkozó oktatóanyagok](power-bi-visualization-types-for-reports-and-q-and-a.md) között. 

## <a name="upload-a-custom-visualization-and-use-it-in-power-bi"></a>Egyéni vizualizáció feltöltése és használata a Power BI-ban

Önállóan létrehozott vagy a [Microsoft AppSource közösségi webhelyéről](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals) letöltött egyéni vizualizációkat is használhat. Kreatív kedvében van? Merüljön el a forráskódban, és használja [fejlesztői eszközeinket](../developer/visuals/custom-visual-develop-tutorial.md) egy új típusú vizualizáció létrehozásához, amelyet aztán [a közösség többi tagjával is megoszthat](../developer/visuals/office-store.md). Az egyéni vizualizációk fejlesztéséről az [Egyéni Power BI-vizualizáció fejlesztése](../developer/visuals/custom-visual-develop-tutorial.md) című cikkben található további információ.

## <a name="personalize-your-visualization-pane-preview"></a>A vizualizációs ablaktábla személyre szabása (előzetes verzió)

Ha azt veszi észre, hogy ugyanazt az egyéni vizualizációt használja számos jelentésben, az egyéni vizualizációt rögzítheti a vizualizációs ablaktáblán. Az ablaktáblára való rögzítéséhez kattintson a jobb gombbal a vizualizációra.

![Rögzítés a vizualizációs ablaktáblára](media/power-bi-report-visualizations/power-bi-pin-custom-visual-option.png)

A rögzítését követően a vizualizáció többi beépített vizualizációval együtt aktív lesz. A vizualizációt a rendszer a bejelentkezéshez használt fiókjához kötötte, így minden új, Ön által létrehozott jelentés automatikusan magában fogja foglalni ezt a vizualizációt, feltéve, hogy bejelentkezett. Így nagyon egyszerűen általános használatúvá tehető egy adott vizualizáció, anélkül, hogy minden egyes jelentéshez külön hozzá kellene adni.

![Személyre szabott vizualizációs ablaktábla](media/power-bi-report-visualizations/power-bi-personalized-visualization-pane.png)

Amíg ez a funkció előzetes verzióban érhető el, a rögzített vizualizációk csak a Power BI Desktopban láthatók. A funkció használatához emellett be kell jelentkeznie.

## <a name="change-the-visualization-type"></a>Vizualizáció típusának módosítása

Próbálkozhat [a vizualizáció típusának módosításával](power-bi-report-change-visualization-type.md), hogy megtalálja azt, amelyik a legjobban illik az adataihoz.

## <a name="pin-the-visualization"></a>A vizualizáció rögzítése

Ha a vizualizáció pont úgy néz ki, ahogy szeretné, a Power BI szolgáltatásban csempeként [rögzítheti az irányítópultra](../create-reports/service-dashboard-pin-tile-from-report.md). Ha rögzítés után megváltoztatja a jelentésben használt vizualizációt, az irányítópulton lévő csempe nem változik. Ha például vonaldiagram volt, akkor az is marad, noha a jelentésben fánkdiagrammá alakította át.

## <a name="limitations-and-considerations"></a>Korlátozások és megfontolandó szempontok
- Az adatforrástól és a mezők számától függően (mérőszámok vagy oszlopok) előfordulhat, hogy a vizualizációk lassan töltenek be.  Javasoljuk, hogy a vizualizációkat korlátozza összesen 10–20 mezőre a jobb olvashatóság és teljesítmény érdekében. 

- A vizualizációkra érvényes felső korlát 100 mező (mérőszámok és oszlopok). Ha a vizualizáció betöltése sikertelen, csökkentse a mezők számát.   

## <a name="next-steps"></a>További lépések

* [Vizualizációk típusai a Power BI-ban](power-bi-visualization-types-for-reports-and-q-and-a.md)
* [Power BI-vizualizációk](../developer/visuals/power-bi-custom-visuals.md)
