---
title: A Power BI Q&A-vizualizáció használata
description: A Power BI Q&A-vizualizáció beállítása
author: mihart
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/19/2019
ms.author: mohaali
ms.openlocfilehash: 9805b98df7f606e61412ca9dee7dc0467a1649a3
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/06/2020
ms.locfileid: "74791816"
---
# <a name="introduction-to-power-bi-qa-visual"></a>Bevezetés a Power BI Q&A-vizualizáció használatába

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

## <a name="what-is-the-qa-visual"></a>Mi a Q&A-vizualizáció?

A Q&A-vizualizáció lehetővé teszi a felhasználók számára, hogy természetes nyelven feltett kérdéseikre vizualizáció formájában kapják meg a választ. 

![A Q&A-vizualizáció bemutatása](../natural-language/media/qna-visual-walkthrough.gif)

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

A Q&A-vizualizációt egyaránt igénybe vehetik a *felhasználók*, ha gyors választ kívánnak kapni a megadott adataikra, és a *tervezők*, akik két kattintással hozhatnak létre vizualizációkat bárhol a jelentésben, és természetes nyelven kezdhetik a használatot. A Q&A-vizualizáció, más vizualizációkhoz hasonlóan biztosítja a keresztszűrés és a keresztkijelölés lehetőségét, és támogatja a könyvjelzőket. A Q&A-vizualizáció támogatja a témákat és a Power BI-ban elérhető egyéb alapértelmezett formázási lehetőségeket.

A Q&A vizualizáció négy alapvető elemből áll;

- Kérdésmező. A felhasználó ide írja be a kérdést, és itt kap javaslatokat a kérdés kiegészítéséhez.
- A javasolt kérdések előre feltöltött listája.
- A Q&A vizualizációt hagyományos vizualizációra váltó ikon. 
- Ez az ikon megnyitja a Q&A-eszközök ablaktáblát, ahol a tervezők konfigurálhatják a mögöttes természetes nyelvi motort.

## <a name="prerequisites"></a>Előfeltételek

1. Ez az oktatóanyag az [Értékesítési és Marketing minta PBIX-fájlt](https://download.microsoft.com/download/9/7/6/9767913A-29DB-40CF-8944-9AC2BC940C53/Sales%20and%20Marketing%20Sample%20PBIX.pbix) használja. 

1. A Power BI Desktop menüsorának bal felső részén válassza a **Fájl** > **Megnyitás** lehetőséget
   
2. Keresse meg az **Értékesítési és Marketing minta PBIX-fájlt**.

1. Fájl megnyitása jelentés nézetben ![A jelentés nézet ikonjának képernyőképe.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Kiválasztás ![A sárga fül képernyőképe.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) új oldal hozzáadásához.


Ha hibát tapasztal a Q&A-vizualizáció létrehozása során, ellenőrizze a [korlátozások](../natural-language/q-and-a-limitations.md) szakaszban, hogy az adatforrás-konfiguráció támogatva van-e.

## <a name="create-a-qa-visual-using-a-suggested-question"></a>Q&A-vizualizáció létrehozása javasolt kérdés használatával
Ebben a gyakorlatban egy javasolt kérdést választunk ki a Q&A vizualizáció létrehozásához. 

1. Egy üres jelentésoldalról kiindulva válassza ki a Vizualizáció ablaktáblán a Q&A-vizualizáció ikont.

    ![Vizualizáció ablaktábla a kiemelt Q&A-vizualizáció ikonnal](media/power-bi-visualization-q-and-a/power-bi-icon.png)

2. Húzza át a szegélyt a vizualizáció újraméretezéséhez.

    ![Q&A-vizualizáció a jelentés vásznon](media/power-bi-visualization-q-and-a/power-bi-qna.png)

3. A vizualizáció létrehozásához válasszon a javasolt kérdések közül, vagy kezdjen beírni egy kérdést a kérdésmezőbe. Ebben a példában kiválasztottuk a **top geo states by sum of revenue** (vezető földrajzi államok jövedelemösszeg alapján) kérdést. A Power BI megpróbálja kiválasztani a felhasználható vizualizációtípust. Ebben az esetben ez egy térkép.

    ![Q&A-vizualizáció térkép](media/power-bi-visualization-q-and-a/power-bi-map.png)

    De a természetes nyelven megadott lekérdezésekhez hozzáadhatja annak meghatározását is, hogy a Power BI milyen típusú vizualizációt használjon. Vegye figyelembe, hogy nem minden vizualizációtípus fog működni vagy értelmezhető eredményt mutatni az adatokkal. Ezek az adatok például nem ábrázolhatók értelmezhetően egy pontdiagramon. A kartogram azonban jól használható.

    ![Q&A-vizualizáció, mint kartogram](media/power-bi-visualization-q-and-a/power-bi-specify-map.png)

## <a name="create-a-qa-visual-using-a-natural-language-query"></a>Q&A-vizualizáció létrehozása természetes nyelvi lekérdezéssel
Az előző példában kiválasztottunk egy javasolt kérdést a Q&A-vizualizáció létrehozásához.  Ebben a gyakorlatban a saját kérdésünket írjuk be. A kérdés beírását a Power BI automatikus kiegészítéssel, javaslatokkal és visszajelzéssel segíti.

Ha nem biztos a kérdéstípusban vagy a szóhasználatban, bontsa ki az **Összes javaslat megjelenítése** elemet, vagy tekintse át a Mezők ablaktáblát a vászon jobb oldalán. Itt megismerheti az Értékesítési és Marketing adatkészlet szóhasználatát és tartalmát.

![vászon az Összes javaslat megjelenítése és a Mezők ablaktábla kiemelésével](media/power-bi-visualization-q-and-a/power-bi-terminology.png)


1. Írjon be egy kérdést a Q&A-mezőbe. A Power BI pirossal húzza alá a fel nem ismert szavakat. A Power BI lehetőség szerint segít a fel nem ismert szavak meghatározásában.  Az alábbi első példában bármelyik javaslatot kiválaszthatja.  

    ![Kérdés beírása a Q&A-kérdésmezőbe](media/power-bi-visualization-q-and-a/power-bi-red-suggest.png)

2. Ahogy előrehalad a kérdés beírásával, a Power BI értesíti, ha nem érti a kérdést, és megpróbál segíteni. Az alábbi példában a Power BI felteszi a „Did you mean...” (Arra gondolt hogy...) kérdést, és javaslatot tesz egy másik szó használatára az adatkészletből. 

    ![A Q&A-vizualizáció javaslatainak megjelenítése](media/power-bi-visualization-q-and-a/power-bi-define.png)

5. A Power BI segítségével feltehettünk egy csak felismerhető kifejezésekből álló kérdést. A Power BI vonaldiagram formájában jeleníti meg az eredményeket. 

    ![Q&A-vizualizáció eredmények](media/power-bi-visualization-q-and-a/power-bi-type.png)


6. Módosítsuk a vizualizációt oszlopdiagramra. 

    ![Q&A-vizualizáció a kérdéshez hozzátett „as a column chart” (oszlopdiagramként) kifejezéssel](media/power-bi-visualization-q-and-a/power-bi-specify-visual.png)

7.  Adjon hozzá további vizualizációkat a jelentésoldalhoz, és tekintse meg, hogyan kommunikál a Q&A-vizualizáció a többi vizualizációval az oldalon. Ebben a példában a Q&A-vizualizáció keresztszűrést végzett a vonatdiagramon és a térképen, és keresztkiemelést a sávdiagramon.

    ![Q&A-vizualizáció egy kiválasztott sávval és ennek hatása a másik három vizualizációra a jelentésoldalon](media/power-bi-visualization-q-and-a/power-bi-filters.png)

## <a name="format-and-customize-the-qa-visual"></a>Q&A-vizualizáció formázása és testreszabása
A Q&A-vizualizációt a formázási ablaktábla segítségével és téma alkalmazásával formázhatja. 

### <a name="apply-a-theme"></a>Téma alkalmazása
Téma kiválasztása esetén a téma a teljes jelentésoldalra érvényes lesz. Számos téma közül választhat, ezért érdemes többet is kipróbálni, amíg megtalálja az igényeinek megfelelőt. 

1. A menüsáv **Kezdőlap** lapján kattintson a **Témaváltás** lehetőségre. 

    ![Asztal a kijelölt Témaváltás elemmel](media/power-bi-visualization-q-and-a/power-bi-themes.png)

    
    
2. Ebben a példában az **Egyéb témák**  > **Színvakok számára biztonságos** lehetőséget választottuk.

    ![Q&A-vizualizáció a színvakok számára biztonságos téma alkalmazásával](media/power-bi-visualization-q-and-a/power-bi-color-blind.png)

### <a name="format-the-qa-visual"></a>A Q&A-vizualizáció formázása
Formázhatja a Q&A-vizualizációt, a kérdésmezőt és a javaslatok megjelenítésének módját. Mindent módosíthat, a cím hátterétől kezdve a fel nem ismert szavak rámutatáskor megjelenő színéig. Ebben a példában szürke hátteret választottunk a kérdésmezőhöz, az aláhúzás színét pedig sárgára és zöldre módosítottuk. A cím középre igazított, a háttere sárga. 

![Q&A-vizualizáció a formázási eredmények megjelenítésével](media/power-bi-visualization-q-and-a/power-bi-q-and-a-format.png)

## <a name="convert-your-qa-visual-into-a-standard-visual"></a>Q&A-vizualizáció átváltása hagyományos vizualizációra
Cím és szegély hozzáadásával módosítottuk a színvakok számára biztonságos oszlopdiagramot. Most már készen állunk arra, hogy a jelentésben hagyományos vizualizációra váltsunk, majd rögzítsük azt egy irányítópulthoz.

Kattintson a ![fogaskerék ikonra](media/power-bi-visualization-q-and-a/power-bi-convert-icon.png), és **váltson a Q&A-eredményről hagyományos vizualizációra**.

![Q&A-vizualizáció a Hagyományos vizualizáció ikonra mutató nyíllal](media/power-bi-visualization-q-and-a/power-bi-visual-convert.png)

Ez már nem Q&A-vizualizáció, hanem hagyományos oszlopdiagram. Irányítópulthoz rögzíthető. A jelentésen belül ez a vizualizáció a többi hagyományos vizualizációhoz hasonlóan működik. Figyelje meg, hogy a Vizualizáció ablaktáblán a Q&A-vizualizáció ikon helyett egy Oszlopdiagram ikon van kiemelve.

A ***Power BI szolgáltatás*** használata esetén a rögzítés ikonra kattintva rögzítheti a vizualizációt egy irányítópulthoz. 


![Power BI szolgáltatás a kiemelt rögzítés ikonnal](media/power-bi-visualization-q-and-a/power-bi-pin.png)


## <a name="advanced-features-of-the-qa-visual"></a>A Q&A-vizualizáció speciális funkciói
A fogaskerék ikonra kattintva megnyithatja a Q&A vizualizáció Eszközök ablaktábláját. 

![Q&A-vizualizáció a kiemelt Eszközök ikonnal](media/power-bi-visualization-q-and-a/power-bi-q-and-a-tooling.png)

Az Eszközök ablaktábla használatával megtaníthatja a Q&A-vizualizációnak az ismeretlen kifejezéseket, a kifejezések használatát, valamint a használatban lévő adatkészlethez és jelentéshez javasolt kérdések kezelését. Az Eszközök ablaktáblán áttekintheti a Q&A-vizualizáció használata során feltett kérdéseket, és láthatja a felhasználók által megjelölt kérdéseket. További információkhoz lásd a [Bevezetés a Q&A-eszközök használatába](../natural-language/q-and-a-tooling-intro.md) című cikket.

![A Q&A Eszközök ablaktábla](media/power-bi-visualization-q-and-a/power-bi-q-and-a-tooling-pane.png)

## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás
A Q&A-vizualizáció integrálva van az Office és a Bing szolgáltatásokkal az adatkészlet mezőiben lévő fel nem ismert, általános használatú szavak azonosításának megkísérléséhez.  

## <a name="next-steps"></a>Következő lépések

A természetes nyelvet többféleképpen is integrálhatja. További információért tekintse át a következő cikkeket:

* [Q&A Eszközök](../natural-language/q-and-a-tooling-intro.md)
* [Q&A – ajánlott eljárások](../natural-language/q-and-a-best-practices.md)
