---
title: Kitöltött (koropletikus) tematikus térképek a Power BI-ban
description: Dokumentáció – kitöltött (koropletikus) tematikus térképek létrehozásához a Power BI-ban
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: ef03a562351b8f4487e4822ef28b89009ee5cbb4
ms.sourcegitcommit: 80961ace38ff9dac6699f81fcee0f7d88a51edf4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/13/2019
ms.locfileid: "56223490"
---
# <a name="filled-maps-choropleths-in-power-bi"></a>Kitöltött (koropletikus) tematikus térképek a Power BI-ban
A tematikus térképek árnyalással, színezéssel vagy mintázattal jelenítik meg egy értéknek egy földrajzi területen vagy régión belüli viszonylagos eltéréseit.  A viszonylagos eltérések gyorsan megjeleníthetők a világostól (ritkább/kevesebb) a sötétig (gyakrabb/több) terjedő árnyalással.    

![USA-térkép](media/power-bi-visualization-filled-maps-choropleths/large_map.png)

## <a name="what-is-sent-to-bing"></a>Mit küld el a rendszer a Bingnek
A Power BI a Binggel integrálva adja meg az alapértelmezett térkép-koordinátákat (a geokódolás nevű eljárással). Amikor térképi vizualizációt hoz létre a Power BI szolgáltatásban vagy a Power BI Desktopban, akkor a **Hely**, **Szélesség** és **Hosszúság** gyűjtőben lévő (a vizualizáció létrehozásához használt) adatok továbbítódnak a Bingnek.

Lehetséges, hogy Önnek vagy a cégnek frissítenie kell a tűzfalat, hogy engedélyezze a hozzáférést azokhoz az URL-címekhez, amelyeket a Bing a geokódoláshoz használ.  Ezek az alábbiak:
- https://dev.virtualearth.net/REST/V1/Locations    
- https://platform.bing.com/geo/spatial/v1/public/Geodata    
- https://www.bing.com/api/maps/mapcontrol

A Bingnek küldött adatokról további információt, a geokódolás sikerességének növeléséhez pedig tippeket kaphat a [Tippek és trükkök térképi vizualizációkhoz](power-bi-map-tips-and-tricks.md) című cikkben.

## <a name="when-to-use-a-filled-map"></a>Mikor érdemes tematikus térképet használni
A tematikus térkép kitűnően alkalmas:

* mennyiségi információk térképi megjelenítésére.
* térbeli mintázatok és összefüggések kimutatására.
* szabványosított adatok esetén.
* társadalmi-gazdasági adatokkal végzett munkához.
* kiemelten fontos régiók esetén.
* a földrajzi helyek közötti eloszlás áttekintéséhez.

### <a name="prerequisites"></a>Előfeltételek
- Power BI szolgáltatás vagy Power BI Desktop
- Értékesítési és marketing minta

Az oktatóanyag lépéseinek elvégzéséhez ne a Power BI Desktopot, hanem a Power BI szolgáltatást használja.

## <a name="create-a-basic-filled-map"></a>Egyszerű tematikus térkép létrehozása
Ezen a videón Kim egy egyszerű térképet hoz létre és alakít át kitöltött tematikus térképpé.

<iframe width="560" height="315" src="https://www.youtube.com/embed/ajTPGNpthcg" frameborder="0" allowfullscreen></iframe>

### <a name="get-data-and-add-a-new-blank-page-to-the-report"></a>Adatok lekérése, illetve új üres lap hozzáadása a jelentéshez
1. Saját tematikus térkép létrehozásához jelentkezzen be a Power BI-ba, majd az **Adatok beolvasása \> Minták \> Értékesítés és Marketing \> Csatlakozás** lehetőség választásával [töltse le az Értékesítés és Marketing mintát](../sample-datasets.md).
2. A sikert jelző üzenet megjelenése után zárja be az üzenetet, és kattintson a **Jelentések** lapra. A jelentés megnyitásához válassza az **Értékesítési és marketingminta** lehetőséget.

   ![Jelentés tartalomjegyzéke](media/power-bi-visualization-filled-maps-choropleths/power-bi-content-reports2.png)
3. A Power BI megnyitja a jelentést. Válassza a **Jelentés szerkesztése** elemet a jelentés [szerkesztési nézetben](../service-interact-with-a-report-in-editing-view.md) való megnyitásához.

4. A vászon aljánál lévő sárga plusz ikonra kattintva adjon hozzá egy új oldalt.

    ![Jelentéslapok](media/power-bi-visualization-filled-maps-choropleths/power-bi-new-page.png)

### <a name="create-a-filled-map"></a>Kitöltött térkép létrehozása
1. A Mezők panelen válassza a **Geo** \> **Állam** mezőt.    

   ![Állapot melletti sárga pipa](media/power-bi-visualization-filled-maps-choropleths/power-bi-state.png)
5. [Alakítsa át a diagramot](power-bi-report-change-visualization-type.md) tematikus térképpé. Figyelje meg, hogy az **Állam** a **Hely** alatt jelenik meg. A Bing Térképek a **Hely** alatti mezőt használja a térkép létrehozásához.  A hely többféle létező földrajzi hely lehet: országok, államok, megyék, városok, irányítószámok vagy más postai kódok, stb. A Bing Térképek világszerte sok helyhez biztosít kitöltött térképformákat. A Hely alatt bevitt érvényes érték nélkül a Power BI nem tudja létrehozni a tematikus térképet.  

   ![sablonok kiemelt kartogramikonnal](media/power-bi-visualization-filled-maps-choropleths/img003.png)
6. Szűrje a térképet úgy, hogy csak az Egyesült Államok szárazföldi területeit mutassa.

   a.  Keresse meg a **Szűrők** területet a Megjelenítések panel alján.

   b.  Vigye a kurzort az **Állam** fölé, és kattintson a kibontó sávnyílra.  
   ![Vizualizációszint szűrői az Állam (mind) elemmel](media/power-bi-visualization-filled-maps-choropleths/img004.png)

   c.  Tegyen pipát a **Mind** lehetőség mellé, és távolítsa el a pipát az **AK** elem mellől.

   ![Államok legördülő menüje kijelöletlen Minden és AK elemmel](media/power-bi-visualization-filled-maps-choropleths/img005.png)
7. A **SalesFact** \> **Vélemény** választásával adja azt hozzá a **Színtelítettség** alatt. A **Színtelítettség** alatti mezők szabják meg a térkép árnyalását.  
   ![Vélemény a Színtelítettség mezőben](media/power-bi-visualization-filled-maps-choropleths/power-bi-filled-map.png)
8. A kitöltött térkép zöld és piros árnyalattal jelenik meg, ahol a piros az alacsonyabb véleménypontszámot, a zöld pedig a magasabb, pozitívabb véleménypontszámot jelöli.  Ezen a képen Wyoming-állam (WY) van kijelölve, és látható, hogy az elégedettség nagyon magas, értéke 74.  
   ![fekete párbeszédpanel az Állam és a Vélemény elemekkel](media/power-bi-visualization-filled-maps-choropleths/power-bi-wy.png)
9. [Mentse a jelentést](../service-report-save.md).
##    <a name="adjust-the-color-formatting"></a>A színformázás módosítása
A Power BI-ban számos lehetőség van a kitöltött térkép megjelenésének szabályozására.
1. A Formátum ablaktábla megnyitásához válassza a festőhenger ikont.

    ![Formázás ablaktábla](media/power-bi-visualization-filled-maps-choropleths/power-bi-data-colors.png)

2. Adatszínek beállításainak megjelentéséhez kattintson az **Adatszínek** elemre.
3. A minimális és a maximális érték legyen a sárga és a kék. A minimális és maximális értékeket pedig adja hozzá az adatok alapján. A vezérlők használatával elérheti a kívánt külalakot. 

    ![nem széttartó színek használata](media/power-bi-visualization-filled-maps-choropleths/power-bi-color.png)

## <a name="highlighting-and-cross-filtering"></a>Kiemelés és keresztszűrés
További információ a Szűrök ablaktábla használatáról: [Szűrők hozzáadása jelentésekhez](../power-bi-report-add-filter.md).

A kitöltött térképek egyes helyeinek kiemelésével a rendszer keresztszűri a jelentésoldalon lévő többi vizualizációt, és fordítva.

1. Ahhoz, hogy követni tudja a lépéseket, először a **Fájl > Mentés** gombra kattintva mentenie kell a jelentést. 

2. Másolja ki a kitöltött térképet a CTRL-C billentyűkombinációval.

3. A jelentésvászon alsó részén válassza a **Vélemény** lapot, a Vélemény jelentéslap megnyitásához.

    ![A Vélemény lap kijelölve](media/power-bi-visualization-filled-maps-choropleths/power-bi-sentiment-tab.png)

4. A vizualizációk áthelyezésével és méretezésével csináljon helyet az oldalon, majd a CTRL-V billentyűkombinációval illessze be az előző jelentésből származó kitöltött térképet.

   ![A Vélemény laphoz hozzáadott kitöltött térkép](media/power-bi-visualization-filled-maps-choropleths/power-bi-map.png)

5. Jelöljön ki egy államot a tematikus térképen.  Ezzel az oldalon lévő többi vizualizációt is kijelöli. Például, ha kijelöli **Texas** államot, a rendszer azt mutatja, hogy a Vélemény értéke 74, Texas pedig a Central District (Középső körzet) \#23. eleméhez tartozik.   
   ![Texas kijelölve](media/power-bi-visualization-filled-maps-choropleths/power-bi-texas.png)
2. Jelöljön ki egy adatpontot a VanArsdel – Sentiment by Month (Vélemény hónap szerint) vonaldiagramon. Ekkor a rendszer szűrést alkalmaz a kitöltött térképen, így csak a VanArsdel véleményadatai jelennek meg, a konkurenciáé pedig nem.  
   ![új árnyalat](media/power-bi-visualization-filled-maps-choropleths/power-bi-yes.png)

## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás
A térképadatok nem feltétlenül egyértelműek.  Van például egy Paris nevű város (Párizs) Franciaországban, de van egy Paris Texasban is. A földrajzi adatok feltehetően külön oszlopokban tárolódnak – Egy oszlopban a városok nevei, egy oszlopban az államoké vagy tartományoké, stb. – így a Bing nem mindig tudja eldönteni, hogy melyik Paris nevű városról van szó. Ha az adatkészlet földrajzi szélesség- és hosszúság-adatokat is tartalmaz, akkor a Power BI speciális mezőkkel támogatja a térképadatok egyértelművé tételét. Ehhez elég a szélesség értékét tartalmazó mezőt a Megjelenítések \> Szélesség területre húzni.  Tegye ugyanezt a hosszúsági adatokkal.    

![A Vizualizációk és a Mezők panel](media/power-bi-visualization-filled-maps-choropleths/pbi_latitude.png)

Ha rendelkezik az adatkészlet Power BI Desktopban történő szerkesztéséhez szükséges jogosultsággal, akkor tekintse meg ezt a térképek kétértelműségének feloldásában segítő videót.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Co2z9b-s_yM" frameborder="0" allowfullscreen></iframe>

Ha nem fér hozzá a szélességi és hosszúsági adatokhoz, akkor [kövesse ezt az útmutatást az adatkészlet frissítéséhez](https://support.office.com/article/Maps-in-Power-View-8A9B2AF3-A055-4131-A327-85CC835271F7).

A térképi vizualizációkhoz további segítséget nyújt a [Tippek és trükkök térképi vizualizációkhoz](../power-bi-map-tips-and-tricks.md) című cikk.

## <a name="next-steps"></a>Következő lépések

[Alakzat leképezése](desktop-shape-map.md)

[Vizualizációtípusok a Power BI-ban](power-bi-visualization-types-for-reports-and-q-and-a.md)