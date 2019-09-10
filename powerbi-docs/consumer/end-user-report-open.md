---
title: Jelentés megtekintése
description: Ez a témakör azt mutatja be a Power BI-felhasználóknak és -végfelhasználóknak, hogyan nyithatnak meg és tekinthetnek meg Power BI-jelentéseket.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 08/28/2018
ms.author: mihart
ms.openlocfilehash: e02d7bfa295b3bd18b0b6b9c64c688ed668c8389
ms.sourcegitcommit: c799941c8169cd5b6b6d63f609db66ab2af93891
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/06/2019
ms.locfileid: "70391753"
---
# <a name="view-a-report-in-the-power-bi-service-for-consumers"></a>A *felhasználóknak* készült Power BI szolgáltatásban jelentéseket tekinthet meg
A jelentések egy vagy több oldalnyi vizualizációból állnak. A jelentéseket a Power BI *tervezői* hozzák létre, és [megosztják őket a *felhasználókkal* közvetlenül](end-user-shared-with-me.md) vagy egy [alkalmazás](end-user-apps.md) részeként. 

A jelentések megnyitásának számos különböző módja van, amelyek közül most kettőt mutatunk be: a kezdőlapról, és az irányítópultról történő megnyitást. 

<!-- add art-->


## <a name="open-a-report-from-power-bi-home"></a>Jelentés megnyitása a Power BI kezdőlapjáról
Nyissunk meg egy Önnel közvetlenül megosztott jelentést, majd egy olyat, amely egy alkalmazás részeként lett megosztva Önnel.

   ![Kezdőlap](./media/end-user-report-open/power-bi-home-canvas.png)

### <a name="open-a-report-that-has-been-shared-with-you"></a>Önnel megosztott jelentés megnyitása
A Power BI-*tervezők* megoszthatnak egy adott jelentést közvetlenül Önnel e-mailes hivatkozással vagy a Power BI kezdőlapjához való hozzáadással. Az ezúton megosztott tartalmak a bal oldali navigációs sávon található **Velem megosztva** tárolóban, valamint a kezdőlap **Velem megosztva** szakaszában jelennek meg.

1. Nyissa meg a Power BI szolgáltatást (app.powerbi.com).

2. A kezdőlap vászon megjelenítéséhez a navigációs sávon válassza a **Kezdőlap** lehetőséget.  

   ![Kezdőlap vászon](./media/end-user-report-open/power-bi-select-home-new.png)
   
3. Görgessen le a **Velem megosztva** szakaszig. Keresse meg a jelentés ikont ![jelentés ikon](./media/end-user-report-open/power-bi-report-icon.png). Ezen a képernyőfelvételen egy *Sales and Marketing sample* (Értékesítési és marketing minta) nevű irányítópult és egy jelentés található. 
   
   ![a kezdőlap Velem megosztva része](./media/end-user-report-open/power-bi-shared-new.png)

4. A jelentés megnyitásához egyszerűen válassza ki az egyik *jelentéskártyát*.

   ![jelentés oldala](./media/end-user-report-open/power-bi-open.png)

5. Figyelje meg a bal oldalon található lapokat.  Minden fül egy *jelentésoldalt* jelöl. Jelenleg a *Growth Opportunity* (Növekedési lehetőség) lap van megnyitva. A jelentésoldal megnyitásához válassza ki az *Idei bevétel kategóriát*. 

   ![jelentésoldal fülei](./media/end-user-report-open/power-bi-ytd.png)

6. Most a jelentés teljes oldalát látjuk. Az oldal megjelenítésének módosításához (kinagyításához) válassza a Nézet legördülő elemet a jobb felső sarokban, majd válassza a **Tényleges méret** lehetőséget.

   ![nagyítás módosítása](./media/end-user-report-open/power-bi-fit-new.png)

   ![laphoz igazítás](./media/end-user-report-open/power-bi-actual.png)

### <a name="open-a-report-that-is-part-of-an-app"></a>Alkalmazás részét képező jelentés megnyitása
A munkatársaitól kapott vagy az AppSource-ból szerzett alkalmazásokat a kezdőlapon és a bal oldali navigációs sáv **Alkalmazások** tárolóján érheti el. Az irányítópultok és jelentések együttesét [alkalmazásnak](end-user-apps.md) nevezzük.

1. Lépjen vissza a kezdőlapra a navigációs sáv **Kezdőlap** elemének kiválasztásával.

7. Görgessen le a **Saját alkalmazások** szakaszig.

   ![Kezdőlap](./media/end-user-report-open/power-bi-my-apps.png)

8. A megnyitáshoz kattintson az egyik alkalmazásra. Az alkalmazás *tervezője* által megadott beállításoktól függően az alkalmazás egy irányítópultot vagy egy jelentést nyit meg. Ha az alkalmazásra kattintva:
    - megnyílik a jelentés, készen is van.
    - egy irányítópult nyílik meg, tekintse meg a következő szakaszt: ***Jelentés megnyitása irányítópultról***.


## <a name="open-a-report-from-a-dashboard"></a>Jelentés megnyitása irányítópultról
A jelentések irányítópultokról is megnyithatók. Az irányítópult legtöbb [csempéje](end-user-tiles.md) jelentésekből van *rögzítve*. Egy adott csempére kattintva megnyílik a csempe létrehozásához használt jelentés. 

1. Az irányítópulton kattintson egy csempére. Ebben a példában a „Total Units YTD...” (Összes egység az év elejétől...) oszlopdiagram címét választottuk.

    ![irányítópult egy kijelölt csempével](./media/end-user-report-open/power-bi-dashboard.png)

2.  Ekkor megnyílik a hozzá tartozó jelentés. Figyelje meg, hogy most a „YTD Category” oldalon vagyunk. Ez a jelentésoldal tartalmazza azt az oszlopdiagramot, amelyet az irányítópulton választottunk ki.

    ![megnyitott jelentés az Olvasó nézetben](./media/end-user-report-open/power-bi-report-tabs.png)

> [!NOTE]
> Nem minden csempe mutat jelentésekre. Ha olyan csempét nyit meg, amelyet a [Q&A használatával hoztak létre](end-user-q-and-a.md), akkor a Q&A képernyő is megnyílik. Ha olyan csempét nyit meg, amelyet az [irányítópult **Csempe felvétele** vezérlője használatával hoztak létre](../service-dashboard-add-widget.md), számos különböző dolog történhet: lejátszódhat egy videó, megnyílhat egy webhely és így tovább.  


##  <a name="still-more-ways-to-open-a-report"></a>További lehetőségek a jelentés megnyitására
Ha már otthonosabban mozog a Power BI szolgáltatásban, minden bizonnyal tudni fogja, mely munkafolyamatok a legkényelmesebbek az Ön számára. Íme még néhány további lehetőség a jelentések megnyitásához:
- A navigációs panelen a **Kedvencek**, majd a **Legutóbbi** lehetőséget választva    
- A [Kapcsolódó megtekintése](end-user-related.md) használata    
- E-mailben, ha valaki [megosztja Önnel](../service-share-reports.md) vagy Ön [riasztást állít be](end-user-alerts.md);    
- Az [Értesítési központból](end-user-notification-center.md)    
- és még néhány további lehetőség

## <a name="next-steps"></a>Következő lépések
[Jelentés megnyitása és megtekintése](end-user-dashboard-open.md)

