---
title: Nyomtatás a Power BI szolgáltatásból
description: Irányítópult, csempe vagy jelentésoldal nyomtatása a Power BI szolgáltatásból.
author: mihart
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 03/12/2020
ms.author: mihart
LocalizationGroup: Common tasks
ms.openlocfilehash: 8c91e2a07143a6355b7049e80cbdc3e4ba906013
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83145388"
---
# <a name="printing-from-the-power-bi-service"></a>Nyomtatás a Power BI szolgáltatásból

[!INCLUDE[consumer-appliesto-yynn](../includes/consumer-appliesto-yynn.md)]
## <a name="what-can-be-printed"></a>Mit lehet nyomtatni
[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Útmutató teljes irányítópultok, irányítópult-csempék, jelentésoldalak, jelentés-vizualizációk Power BI-ból történő nyomtatásához. Ha a jelentésnek több oldala is van, minden oldalt külön-külön kell kinyomtatnia. 

## <a name="printing-considerations"></a>Nyomtatási megfontolások

A Power BI-ban az irányítópultok és a jelentések többségét a jelentések *tervezői* hozzák létre, amelyeket online lehet használni, és számos eszközön kiváló minőségben jelennek meg. Amikor kinyomtat egy jelentést, a böngészőtől függ, hogy a tartalom hogyan jelenik majd meg a papíron. 

A böngésző beállításai segítségével módosíthatja a nyomtatási megjelenést, de még akkor is előfordulhat, hogy nem tudja elérni a kívánt eredményt. Érdemes lehet a tartalmat először [PDF-be](end-user-pdf.md) exportálni, és a PDF-fájlt kinyomtatni inkább. 

## <a name="adjust-your-browser-print-settings"></a>A böngésző nyomtatási beállításainak módosítása
Amikor Power BI-ból nyomtat, a böngésző megnyit egy nyomtatási ablakot. Minden böngésző nyomtatási ablaka különbözik a többitől. Mindegyikben megtalálhatóak azonban bizonyos beállítások, amelyek segítségével szabályozhatja a nyomtatás megjelenését. 

Íme néhány gyors tipp, amellyel formázhatja a nyomtatást.

   > 
1. Ha az irányítópult, a jelentés vagy a vizualizáció szélesebb, mint amilyen a magassága, érdemes lehet a **Fekvő** elrendezést használni. 

   ![A Fekvő elrendezést mutató nyomtatási párbeszédpanel](./media/end-user-print/power-bi-landscape-layout.png)

2. Ha több tartalmat szeretne egy oldalon, módosítsa például a margókat és a méretezést. 

    ![A További beállításokat megjelenítő nyomtatási párbeszédpanel](./media/end-user-print/power-bi-margins.png)

Kísérletezzen a böngésző beállításaival addig, amíg meg nem találja a kívánt megjelenítést. Egyes böngészőkben arra is lehetőség van, hogy a háttérbeli grafikákat is kinyomtassa. 

## <a name="print-a-dashboard"></a>Irányítópult nyomtatása
1. Nyissa meg azt az irányítópultot, amelyet ki szeretne nyomtatni.
2. A bal felső sarokban válassza az Exportálás elemet, majd az **Oldal nyomtatása** lehetőséget.
   
    ![Irányítópult nyomtatása lehetőség](./media/end-user-print/power-bi-dashboard-print.png)

3. Ekkor megjelenik a böngésző Nyomtatás ablaka. Válassza ki a beállításokat. Ha például az irányítópult szélesebb, mint amilyen hosszú, érdemes lehet az elrendezést **Fekvő tájolásra** állítani. Válassza a **Nyomtatás** lehetőséget.
   
    ![nyomtatási párbeszédpanel](./media/end-user-print/power-bi-print-dash.png)

## <a name="print-a-dashboard-tile"></a>Irányítópult-csempe nyomtatása
1. A felső menüsáv teljes képernyő ikonjára ![teljes képernyő ikon](./media/end-user-print/power-bi-full-screen.png) kattintva nyissa meg az irányítópultot [teljes képernyős módban](end-user-focus.md).

3. [Nyissa meg a csempét fókusz módban](end-user-focus.md). Ehhez vigye fölé az egérmutatót, hogy megjelenjen a **További lehetőségek** (...) elem, majd válassza a **Megnyitás fókusz módban** lehetőséget vagy a fókusz ikont ![Fókusz ikon](./media/end-user-print/power-bi-focus-icon.png).
   
    ![három pont menü](./media/end-user-print/power-bi-menu-options.png)

4. A kurzort a csempe fölé húzva jelenítheti meg a válaszható lehetőségek menüjét.
   
    ![teljes képernyős beállítások menü](./media/end-user-print/menu-options-new.png)

4. A nyomtatás ikon kiválasztása ![nyomtatás ikon](./media/end-user-print/print-icon.png).     

5. Ekkor megjelenik a böngésző Nyomtatás ablaka. Válassza ki a beállításokat. Ha például a csempe nem fér el az oldalon, akkor érdemes lehet a méretezést 75%-ra módosítani. Válassza a **Nyomtatás** lehetőséget.

    ![nyomtatási ablak](./media/end-user-print/power-bi-scale.png) 

> [!TIP]
> Ha követte ezeket a lépéseket, és a csempe továbbra sem a kívánt módon jelenik meg, próbálja meg a következőket.
> 1. Nyissa meg a nyomtatási ablakot, és végezze el a módosításokat úgy, hogy a nyomtatási beállítások a legjobb nyomtatási megjelenést eredményezzék. Módosíthatja például az elrendezést, a margókat és a méretezést. 
> 2. A nyomtatás helyett azonban válassza a **Mégse** lehetőséget. 
> 3. Végezze el újra az 1–5 lépéseket. A csempe a nyomtatási ablak új beállításaira lesz módosítva, és készen áll a nyomtatásra.

## <a name="print-a-report-page"></a>Jelentésoldal nyomtatása
A jelentésekből egyszerre egy oldal nyomtatható ki.

1. Az aktuális oldal nyomtatásához nyissa meg a jelentést, és válassza az **Exportálás** > **Nyomtatás** lehetőséget.
   
    ![Power BI Fájl menü](./media/end-user-print/power-bi-report-print.png)
2. Ekkor megjelenik a böngésző Nyomtatás ablaka.

3. Kövesse a fenti **Irányítópult nyomtatása** szakasz nyomtatási lépéseit.
   


## <a name="print-a-report-visual"></a>Jelentés-vizualizáció nyomtatása
1. A kurzort a csempe fölé húzva, majd jobb felső sarokban látható Fókusz ikonra ![Fókusz ikon](./media/end-user-print/power-bi-focus-icon.png) kattintva [nyissa meg a vizualizációt fókusz módban](end-user-focus.md).

2. A vizualizáció nyomtatásához a bal felső sarokban válassza az **Exportálás** > **Nyomtatás** lehetőséget.

    ![Power BI Fájl menü](./media/end-user-print/power-bi-report-print.png)


3. Kövesse a fenti **Irányítópult nyomtatása** szakasz nyomtatási lépéseit.

## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás

* KÉRDÉS: Nem nyomtatható ki a jelentés minden lapja egyszerre.    
* VÁLASZ: Ez nem hiba. A jelentésekből egyszerre csak egy oldal nyomtatható ki.
* KÉRDÉS: Nem lehet PDF-fájlba nyomtatni.    
* VÁLASZ: Ez a lehetőség csak akkor jelenik meg, ha böngészőjéhez már beállított egy PDF-illesztőprogramot.    
* KÉRDÉS: A **Nyomtatásra** kattintás után nem az itt bemutatott képernyő jelenik meg.    
* VÁLASZ: A Nyomtatási képernyők böngészőnként és szoftververziónként változnak.
* KÉRDÉS: A nyomtatásra kerülő anyag nincs megfelelően méretezve.  Az irányítópult nem fér el az oldalon. Méretezéssel és tájolással kapcsolatos egyéb problémák.    
* VÁLASZ: Nem tudjuk garantálni, hogy a nyomtatott példány pontosan meg fog egyezni azzal, ami a Power BI szolgáltatásban látható. A kicsinyítést és nagyítást, a margókat, a megjelenítési részleteket, a tájolást és a méretet nem a Power BI szolgáltatás vezérli. Próbálja meg módosítani a böngésző nyomtatási beállításait. A fentiekben szereplő néhány javaslat az oldal tájolása (álló vagy fekvő), a margó mérete és a méretezés. Ha ezekkel nem jár sikerrel, a böngésző súgójában találhat további információt.      
* KÉRDÉS: A teljes képernyős módból való nyomtatáskor nem jelenik meg a Nyomtatás lehetőség, amikor a vizualizáció fölé viszem a kurzort.   
* VÁLASZ: Térjen vissza az irányítópultra vagy jelentésre az alapértelmezett nézetben, majd nyissa meg újra a vizualizációt fókusz módban, majd a teljes képernyős módban. 

## <a name="next-steps"></a>Következő lépések
[Irányítópultok és jelentések megosztása munkatársakkal és más személyekkel](../collaborate-share/service-share-dashboards.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
