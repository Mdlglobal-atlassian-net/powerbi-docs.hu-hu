---
title: Szűrők és kiemelés a Power BI-jelentésekben
description: Szűrők és kiemelés a Power BI-jelentésekben
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/23/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: f1722690ff974a9d4fac6e94243e1024bfbfc12e
ms.sourcegitcommit: 7e845812874b3347bcf87ca642c66bed298b244a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79207068"
---
# <a name="filters-and-highlighting-in-power-bi-reports"></a>Szűrők és kiemelés a Power BI-jelentésekben
 Ez a cikk bevezetést nyújt a Power BI szűrő és kiemelő funkcióiba. A funkciók szinte ugyanúgy működnek, mint a Power BI Desktop szolgáltatásban. A *szűrők* használatával minden olyan adatot eltávolíthat, amelyek az Ön szempontjából lényegtelenek. A *Kiemelés* nem szűrés. Nem távolítja el az adatokat, hanem kiemeli a látható adatok egy részét, miközben a ki nem emelt adatok halványan láthatóak maradnak.

A Power BI-ban sokféleképpen szűrheti és kiemelheti a jelentések adatait. Ha az összes információt egyetlen cikkbe sűrítenénk, az nehezen lenne áttekinthető, ezért a tudnivalókat a következő szakaszokra bontottuk fel:

* Bevezetés a szűrők és a kiemelés használatába (a cikk, amelyet most olvas).
* [Szűrők létrehozása és használata szerkesztési nézetben](power-bi-report-add-filter.md) a Power BI Desktop és a Power BI szolgáltatás jelentéseiben. Ha szerkesztési engedélye van egy jelentéshez, akkor létrehozhatja, módosíthatja és törölheti a szűrőket a jelentésekben.
* Így működik a [szűrés és a kiemelés az Önnel megosztott jelentésekben,](consumer/end-user-interactions.md) a jelentés Olvasó nézetében, valamint a Power BI szolgáltatásban. A cselekvés korlátozott, de még így is számos lehetőség marad a szűrésre és a kiemelésre.  
* Részletes bemutató a [Szerkesztés nézetben elérhető szűrési és kiemelési lehetőségekről](power-bi-report-add-filter.md) a Power BI Desktopban és a Power BI szolgáltatásban. A cikk részletesen bemutatja a szűrők (például dátum és idő, numerikus és szöveges) típusait. Ezenfelül az alapvető és a speciális beállítások közötti különbségeket is ismerteti.
* Ha már megismerte a szűrők és a kiemelés alapértelmezés szerinti működését, nézze meg, [miképpen módosíthatja azt, ahogy az oldal vizualizációi egymást szűrik és kiemelik](service-reports-visual-interactions.md)

**Tudta?** A Power BI új szűrési felülettel rendelkezik. Bővebben is tájékozódhat [a Power BI-jelentésekben elérhető új szűrési felületről](power-bi-report-filter.md).

![Új szűrőfunkciók](media/power-bi-reports-filters-and-highlighting/power-bi-filter-reading.png)


## <a name="intro-to-the-filters-pane"></a>A Szűrők panel ismertetése

A szűrőket alkalmazhatja a **Szűrők** panelen, vagy úgy, hogy [szeletelőkön választ](visuals/power-bi-visualization-slicers.md) közvetlenül a jelentésben. A Szűrők ablaktáblán láthatók a jelentésben használt táblák és mezők és az alkalmazott szűrők, ha vannak. 

![A Szűrők panel](media/power-bi-reports-filters-and-highlighting/power-bi-add-filter-reading-view.png)

A szűrőknek négy különböző típusa létezik.

- **Oldalszűrő:** A jelentésoldal összes vizualizációjára vonatkozik.     
- **Vizualizációszűrő:** Egy adott vizualizációra vonatkozik a jelentésoldalon. Vizuális szintű szűrőket csak akkor láthat, ha kiválasztott egy vizualizációt a jelentés vásznán.    
- **Jelentésszűrő:** A jelentés összes oldalára vonatkozik.    
- **Részletezési szűrő:** A jelentés egyetlen entitására vonatkozik.    

A kívánt értékre oldal-, vizualizáció-, és jelentésszűrőkben, valamint Olvasó vagy Szerkesztő nézetben kereshet, majd kiválaszthatja azt. 

![Keresés szűrőben](media/power-bi-reports-filters-and-highlighting/power-bi-search-filter.png)

Ha a szűrő mellett jelen van a **Mind** szó, akkor a szűrőbe a mező összes értéke beletartozik.  A fenti képernyőfelvételen például a **Lánc (Mind)** beállítás azt jelzi, hogy a jelentésoldal minden áruházlánc adatait tartalmazza.  A **FiscalYear is 2013 or 2014** (A pénzügyi év 2013 vagy 2014) jelentésszintű szűrő azonban azt jelzi, hogy a jelentés csak a 2013-as és 2014-es pénzügyi évek adatait tartalmazza.

## <a name="filters-in-reading-or-editing-view"></a>Szűrők Olvasás vagy Szerkesztés nézetben
A jelentések kétféle módban használhatók: [Olvasás nézetben](consumer/end-user-reading-view.md) vagy Szerkesztés nézetben. Az elérhető szűrési képességek az éppen használatban lévő módtól függenek.

* Szerkesztés nézetben jelentés-, oldal-, részletező és vizualizációszűrőket vehet fel. A jelentés mentésekor a szűrőket is menti, akkor is, ha a jelentést mobilalkalmazásban nyitja meg. Aki Olvasás nézetben tekinti meg a jelentést, használhatja a hozzáadott szűrőket, de nem vehet fel újat.
* Olvasás nézetben használhatja a jelentés meglévő szűrőit, és mentheti az elvégzett kijelöléseket. Új szűrőket nem vehet fel.

### <a name="filters-in-reading-view"></a>Szűrők Olvasás nézetben
Ha csak Olvasás nézetben van hozzáférése a jelentéshez, a Szűrők ablaktábla ehhez hasonló:

![Szűrők Olvasás nézetben](media/power-bi-reports-filters-and-highlighting/power-bi-filter-reading-view.png)

A jelentésoldalnak tehát hat oldalszintű és egy jelentésszintű szűrője van.

Minden vizualizáció tartalmaz szűrőket a saját összes mezőjéhez, és a jelentés szerzője továbbiakat is felvehet. Az alábbi képen szereplő buborék diagram hat szűrőt tartalmaz.

![Vizualizációszintű szűrő](media/power-bi-reports-filters-and-highlighting/power-bi-filter-visual-level.png)

Olvasás nézetben a meglévő szűrők módosításával tárhatja fel az adatokat. A módosításokat menti a rendszer a jelentéssel együtt, még akkor is, ha mobilalkalmazásban nyitja meg a jelentést. Ennek a módját [a Szűrők panel bemutatójában](consumer/end-user-report-filter.md) ismerheti meg.

Amikor kilép a jelentésből, a szűrők mentve lesznek. Ha visszavonná a szűrést, és visszatérne a jelentés készítője által beállított alapértelmezett szűrő-, szeletelő-, részletezési és rendezési készlethez, válassza a **Visszaállítás alapértelmezettre** lehetőséget a felső menüsoron.

![Visszaállítás alapértelmezettre ikon](media/power-bi-reports-filters-and-highlighting/power-bi-reset-to-default.png)

### <a name="filters-in-editing-view"></a>Szűrők Szerkesztés nézetben
Ha tulajdonosi engedélye van a jelentéshez, és Szerkesztés nézetben nyitja meg azt, akkor látni fogja, hogy a **Szűrők** panel csak az egyike a rendelkezésre álló szerkesztési ablaktábláknak.

![Szűrők ablaktábla a Szerkesztés nézetben](media/power-bi-reports-filters-and-highlighting/power-bi-add-filter-editing-view.png)

Hasonlóan az Olvasás nézethez, a jelentésoldalnak itt is hat oldalszintű és egy jelentésszintű szűrője van. A buborék diagram kijelölésekor látható, hogy arra hat vizuális szintű szűrőt alkalmaztak.

Szerkesztés nézetben több lehetőség van a szűrők és a kiemelés használatára. A legfontosabb, hogy új szűrőket lehet felvenni. [Szűrők hozzáadása a jelentésekhez](power-bi-report-add-filter.md) és más tudnivalók.

## <a name="ad-hoc-highlighting"></a>Eseti kiemelés
Az oldal többi vizualizációjának kiemeléséhez jelöljön ki egy értéket vagy tengelyfeliratot a jelentésvásznon. A kiemelés eltávolításához jelölje ki ismét az értéket, vagy válasszon ki egy üres helyet a vizualizációban. A kiemeléssel gyorsan feltárhatja az adatok hatásait. Az ilyen típusú keresztkiemelés finombeállításához lásd: [Vizualizációk interakciói](service-reports-visual-interactions.md).

![Keresztkijelölés](media/power-bi-reports-filters-and-highlighting/power-bi-adhoc-filter.gif)


## <a name="next-steps"></a>Következő lépések

[A Power BI-jelentésekben elérhető új szűrési felület](power-bi-report-filter.md)

[Szűrő hozzáadása jelentéshez (Szerkesztés nézetben)](power-bi-report-add-filter.md)

[Ismerkedés a jelentésszűrőkkel](consumer/end-user-report-filter.md)

[A jelentésvizualizációk keresztszűrési és keresztkiemelési viselkedésének módosítása](consumer/end-user-interactions.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

