---
title: Vizualizációk jelentésen belüli működésének módosítása
description: Dokumentáció a vizualizációk a Microsoft Power BI szolgáltatás jelentéseiben és a Power BI Desktop-jelentésekben előforduló interakcióiról.
author: mihart
manager: kfile
ms.reviewer: ''
featuredvideoid: N_xYsCbyHPw
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 09/24/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: c3671ae626496bf80ac4b212a755bb13f82ec66b
ms.sourcegitcommit: ce8332a71d4d205a1f005b703da4a390d79c98b6
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/27/2018
ms.locfileid: "47418438"
---
# <a name="visualization-interactions-in-a-power-bi-report"></a>Vizualizációk interakciói a Power BI-jelentésekben
Ha rendelkezik szerkesztési engedéllyel a jelentéshez, akkor a **Vizualizáció-interakciókkal** határozhatja meg, hogy a jelentésoldal vizualizációi milyen hatással legyenek egymásra. 

Alapértelmezés szerint egy jelentésoldal vizualizációi az oldal további vizualizációinak keresztszűréséhez és keresztkijelöléséhez használhatók.
Például egy állam kijelölése egy térkép vizualizációján kiemeli az oszlopdiagramot, és úgy szűri a vonaldiagramot, hogy az csak az adott államra vonatkozó adatokat jelenítse meg.
Lásd: [Szűrés és kiemelés](power-bi-reports-filters-and-highlighting.md). Ha pedig olyan vizualizációkkal is rendelkezik, amelyek támogatják a [részletes vizsgálatot](consumer/end-user-drill.md), akkor alapbeállítás szerint egy adott vizualizáció részletező elemzése nem lesz hatással a jelentésoldal többi vizualizációjára. Mindkét alapértelmezett viselkedés módosítható azonban, és az interakciók az egyes vizualizációkra vonatkozóan beállíthatóak.

Ez a cikk azt mutatja be, hogyan használhatók a **vizualizáció-interakciók** a Power BI szolgáltatásban [Szerkesztési módban](service-interact-with-a-report-in-editing-view.md), valamint a Power BI Desktopban. Ha egy jelentés meg van osztva Önnel, a vizualizációk interakcióinak beállítását nem módosíthatja.

> [!NOTE]
> A *keresztszűrés* és *keresztkijelölés* kifejezésekkel az itt ismertetett viselkedéseket a **Szűrők** ablaktábla szűrés és kiemelés funkciójától különböztetjük meg.  
> 
> 

<iframe width="560" height="315" src="https://www.youtube.com/embed/N_xYsCbyHPw?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

1. Aktiváljon egy vizualizációt annak kijelölésével.  
2. Jelenítse meg a **Vizualizáció-interakciók** beállításait.
    - A Power BI szolgáltatásban válassza a jelentés menüsorából a legördülő listát.

       ![Vizualizáció-interakciók legördülő lista](media/service-reports-visual-interactions/power-bi-visual-interaction.png)

    - A Desktopban válassza a **Formázás > Interakciók** lehetőséget.

        ![Formátum, majd interakciók kiválasztása](media/service-reports-visual-interactions/pbi-visual-interaction-desktop.png)

3. Ha be szeretné kapcsolni a vizualizáció-interakciók vezérlőit, válassza az **Interakciók szerkesztése** lehetőséget. A Power BI a jelentésoldal összes többi vizualizációjához keresztszűrési és keresztkiemelési ikonokat ad hozzá.
   
    ![jelentés a bekapcsolt Vizualizációk interakcióival](media/service-reports-visual-interactions/power-bi-icons-on.png)
3. Adja meg, hogy a kijelölt vizualizáció milyen hatással legyen a többire.  Ha szeretné, ezt megismételheti a jelentés oldalának minden vizualizációjával.
   
   * Ha keresztszűrést szeretne megadni, kattintson a **szűrő** ikonra ![szűrő ikon](media/service-reports-visual-interactions/pbi-filter-icon-outlined.png).
   * Ha keresztkiemelést szeretne megadni, kattintson a **kiemelés** ikonra ![kiemelés ikon](media/service-reports-visual-interactions/pbi-highlight-icon-outlined.png).
   * Ha nem szeretne hatást megadni, kattintson a **nincs hatás** ikonra ![nincs hatás ikon](media/service-reports-visual-interactions/pbi-noimpact-icon-outlined.png).

4. A részletező elemzés vezérlőinek bekapcsolásához válassza a **Más vizualizációk részletező szűrése** lehetőséget.  Ha most egy vizualizációt részletesen elemez, akkor a jelentésoldal többi vizualizációja is változik majd, és tükrözi az aktuális elemzési kiválasztást. 

   ![vizsgálat vezérlők bekapcsolását bemutató videó](media/service-reports-visual-interactions/drill2.gif)

