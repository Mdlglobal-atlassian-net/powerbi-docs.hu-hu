---
title: Irányítópult-csempe szerkesztése
description: 'Az oktatóanyag végigvezeti Önt a csempe létrehozásától az irányítópulton való rögzítéséig, miközben elsajátíthatja az irányítópultok csempéinek szerkesztési módszereit: az átméretezést, az áthelyezést, az átnevezést, a rögzítést, a törlést és a hivatkozások használatát.'
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: lJKgWnvl6bQ
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/02/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: bdd2ec136ae741e15e0cb60d141c651cd5fb6749
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "79207597"
---
# <a name="edit-or-remove-a-dashboard-tile"></a>Irányítópult-csempék szerkesztése és eltávolítása

## <a name="dashboard-owners-versus-dashboard-consumers"></a>Az irányítópult *tulajdonosai* és *felhasználói* közötti különbségek
Ha Ön az irányítópult létrehozója vagy tulajdonosa, számos lehetőség áll rendelkezésére az irányítópulton lévő csempék megjelenésének és alapértelmezett viselkedésének a módosítására. Az alábbi beállítások és eljárások használatával testre szabhatja az irányítópultot a *felhasználók* számára.  Meghatározhatja például, hogy ha kiválasztanak egy csempét, akkor az alapjául szolgáló jelentés, egy egyéni URL-cím vagy egy másik irányítópult nyíljon-e meg. Dönthet úgy, hogy [hozzáad egy olyan csempét, amely videót vagy streamelési adatot jelenít meg](service-dashboard-add-widget.md). Sőt, akár olyan csempét is [létrehozhat, amely interaktív szeletelőket tartalmaz](service-dashboard-pin-live-tile-from-report.md). *Létrehozóként* tehát nagyon sok lehetősége van. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/lJKgWnvl6bQ" frameborder="0" allowfullscreen></iframe>

Ez a cikk az alábbiakat ismerteti.

* [Vizualizáció létrehozása és rögzítése az irányítópulton](#create)
* [Csempe áthelyezése](#move)
* [ Csempe átméretezése](#resize)
* [ Csempe átnevezése](#rename)
* [Hivatkozás hozzáadása egy csempéhez](#hyperlink)
* [Csempe rögzítése egy másik irányítópulton](#different)
* [Csempe törlése](#delete)
  
  > [!TIP]
  > Ha magán a csempén látható vizualizációt szeretné módosítani, törölje a csempét, és vegyen fel egy új [irányítópult-csempét](consumer/end-user-tiles.md).

  
## <a name="prerequisites"></a>Előfeltételek
A bemutatott lépések követéséhez nyissa meg a Power BI szolgáltatást (nem a Power BI Desktopot), és [töltse le az Informatikaköltség-elemzési mintát](sample-it-spend.md). Amikor megkapja az értesítést a sikeres műveletről, válassza az **Ugrás az irányítópultra** lehetőséget.

- - -
<a name="create"></a>

## <a name="create-a-new-visualization-and-pin-it-to-the-dashboard"></a>Új vizualizáció létrehozása és rögzítése az irányítópulton
1. Az Informatikaköltség-elemzési minta irányítópultján válassza az „Amount” (Mennyiség) csempét, ezzel megnyitja a jelentést.

    ![Mennyiség csempe](media/service-dashboard-edit-tile/power-bi-amount-tile.png)

2. Nyissa meg a jelentést szerkesztési nézetben a felső menüsávon a **Jelentés szerkesztése** lehetőséget választva.

3. A jelentés aljánál lévő plusz (+) jelet választva adhat hozzá egy új jelentésoldalt.

    ![plusz ikon](media/service-dashboard-edit-tile/power-bi-add-page.png)

4. A MEZŐK panelen válassza a **Fact > Amount** és a **Business Area > Business Area** lehetőséget.
 
5. Ahhoz, hogy a vizualizációt fánkdiagrammá alakítsa át, a VIZUALIZÁCIÓK panelen válassza ki a fánkdiagram ikont.

    ![Vizualizációk panel](media/service-dashboard-edit-tile/power-bi-donut-chart.png)

5. Válassza a rögzítés ikont, és rögzítse a fánkdiagramot az Informatikaköltség-elemzési minta irányítópultjára.

   ![vigye az egérmutatót egy csempe fölé](media/service-dashboard-edit-tile/power-bi-pin.png)

6. Amikor megkapja az értesítést a sikeres műveletről, válassza az **Ugrás az irányítópultra** lehetőséget. A rendszer felszólítja, hogy mentse a változásokat. Kattintson a **Mentés** gombra.

- - -
<a name="move"></a>

## <a name="move-the-tile"></a>A csempe áthelyezése
Keresse meg az új csempét az irányítópulton. A csempe kiválasztásával és lenyomva tartásával húzhatja azt át az új helyre az irányítópult vásznán.

- - -
<a name="resize"></a>

## <a name="resize-the-tile"></a>A csempe átméretezése
Különböző méretekre állíthatja a csempéket – az 1x1-es elrendezéstől akár az 5x5-ös elrendezésig. A fogópont (a jobb alsó sarokban) kiválasztásával és húzásával méretezheti át a csempét.

![videó](media/service-dashboard-edit-tile/pbigif_resizetile4.gif)

- - -
## <a name="more-options--menu"></a>**További lehetőségek** (...) menü

1. Válassza a csempe jobb felső sarkában található **További lehetőségek** (...) elemet. 
   
   ![csempe három pont](media/service-dashboard-edit-tile/power-bi-tile.png)

2. Mozgassa az egérmutatót az „Account” csempe fölé, és a három pontot kiválasztva jelenítse meg a beállításokat. Az elérhető lehetőségek a csempe típusától függően változhatnak.  Egy élő csempe esetén például másféle lehetőségek jelennek meg, mint egy hagyományos vizualizációs csempe esetén. Ezen kívül ha az irányítópultot megosztották Önnel (azaz nem Ön a tulajdonosa), akkor kevesebb lehetőség áll rendelkezésére.

   ![három pont beállítások menü](media/service-dashboard-edit-tile/power-bi-tile-menu-new.png)

3. A „Csempe részletei” ablak megnyitásához válassza a **Részletek szerkesztése** lehetőséget. 

    Változtassa meg a csempe címét és alapértelmezett viselkedését.  Például dönthet úgy, hogy amikor a *felhasználó* kiválasztja a csempét, akkor a csempe létrehozásához használt jelentés megnyitása helyett inkább egy új irányítópult jelenjen meg.  
   


<a name="rename"></a>

### <a name="rename-the-tile"></a>A csempe átnevezése
A „Csempe részletei” ablak felső részén változtassa meg a **Cím** (Title) mező értékét **Elköltött összeg** szövegre.

![Csempe részletei ablak](media/service-dashboard-edit-tile/power-bi-tile-title.png)


<a name="hyperlink"></a>

### <a name="change-the-default-hyperlink"></a>Az alapértelmezett hivatkozás módosítása
Alapértelmezés szerint egy csempe kiválasztásával megnyílik az jelentés, amelyet a csempe létrehozásához használtak, vagy a Q&A (ha a csempe a Q&A-ben lett létrehozva). Egy weblap, egy másik irányítópult vagy jelentés (ugyanazon a munkaterületen), egy SSRS-jelentés vagy egyéb online tartalom hivatkozásához vegyen fel egyéni hivatkozást.

1. A Funkció címsor alatt válassza az **Egyéni hivatkozás beállítása** lehetőséget.

2. Válassza **Az aktuális munkaterületen található irányítópultra vagy jelentésre mutató hivatkozás** lehetőséget, majd válasszon a legördülő listából.  Ebben a példában az Emberi erőforrások minta irányítópultot választottuk ki. Ha ez a minta még nem található meg az Ön munkaterületén, először adja hozzá, majd térjen vissza ehhez a lépéshez, vagy pedig választhat egy másik irányítópultot is. 

    ![Funkció párbeszédpanel](media/service-dashboard-edit-tile/power-bi-custom-link.png)

3. Kattintson az **Alkalmaz** gombra.

4. Az új cím megjelenik a csempén.  Amikor pedig kiválasztja a csempét, a Power BI megnyitja az Emberi erőforrások irányítópultot. 

    ![csempecím](media/service-dashboard-edit-tile/power-bi-title.png)

<a name="different"></a>

### <a name="pin-the-tile-to-a-different-dashboard"></a>Csempe rögzítése egy másik irányítópulton
1. A legördülő lista menüjében válassza a **Csempe rögzítése** ![gombostű ikon](media/service-dashboard-edit-tile/pinnooutline.png) elemet.
2. Döntse el, hogy egy meglévő vagy egy új irányítópulton rögzíti-e a csempe másolatát. 
   
   ![Rögzítés az irányítópulton párbeszédablak](media/service-dashboard-edit-tile/pbi_pintoanotherdash.png)
3. Kattintson a **Rögzítés** elemre.

<a name="delete"></a>

### <a name="delete-the-tile"></a>A csempe törlése
1. Ha az irányítópultról véglegesen el szeretné távolítani a csempét, a legördülő menüben válassza a **Csempe törlése** ![törlés ikon](media/service-dashboard-edit-tile/power-bi-delete-tile-icon.png) lehetőséget. 

2. A csempe törlésével nem törli az alapul szolgáló vizualizációt. Nyissa meg az alapul szolgáló jelentést az „Amount” csempe kiválasztásával. Nyissa meg a jelentés utolsó oldalát, és látni fogja, hogy az eredeti vizualizáció nem lett törölve a jelentésből. 

- - -
## <a name="next-steps"></a>További lépések
[Irányítópult-csempék a Power BI-ban](consumer/end-user-tiles.md)

[Irányítópultok a Power BI-ban](consumer/end-user-dashboards.md)

[A Power BI szolgáltatás alapfogalmai tervezők számára](service-basic-concepts.md)

Több kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

