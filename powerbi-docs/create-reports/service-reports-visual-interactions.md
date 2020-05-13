---
title: Vizuális elemek jelentésen belüli működésének módosítása
description: Dokumentáció a vizualizációk a Microsoft Power BI szolgáltatás jelentéseiben és a Power BI Desktop-jelentésekben előforduló interakcióiról.
author: mihart
ms.reviewer: ''
featuredvideoid: N_xYsCbyHPw
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/04/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: f50b7fb9cc63322ea488ab6f2adddfd29f763d14
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83321044"
---
# <a name="change-how-visuals-interact-in-a-power-bi-report"></a>Vizualizációk Power BI-jelentésen belüli működésének módosítása
Ha rendelkezik szerkesztési engedéllyel a jelentéshez, akkor a **Vizualizáció-interakciókkal** határozhatja meg, hogy a jelentésoldal vizualizációi milyen hatással legyenek egymásra. 

## <a name="introduction-to-visual-interactions"></a>A vizualizációk működésének bemutatása
Alapértelmezés szerint egy jelentésoldal vizualizációi az oldal további vizualizációinak keresztszűréséhez és keresztkijelöléséhez használhatók.
Például egy állam kijelölése egy térkép vizualizációján kiemeli az oszlopdiagramot, és úgy szűri a vonaldiagramot, hogy az csak az adott államra vonatkozó adatokat jelenítse meg.
Lásd: [Szűrés és kiemelés](power-bi-reports-filters-and-highlighting.md). Ha pedig olyan vizualizációkkal is rendelkezik, amelyek támogatják a [részletes vizsgálatot](../consumer/end-user-drill.md), akkor alapbeállítás szerint egy adott vizualizáció részletező elemzése nem lesz hatással a jelentésoldal többi vizualizációjára. Mindkét alapértelmezett viselkedés módosítható azonban, és az interakciók az egyes vizualizációkra vonatkozóan beállíthatóak.

Ez a cikk azt mutatja be, hogyan használhatók a **vizualizáció-interakciók** a Power BI Desktopban. Az eljárás ugyanez a Power BI szolgáltatás [Szerkesztő nézetében](service-interact-with-a-report-in-editing-view.md). Ha csak Olvasási hozzáféréssel rendelkezik, vagy egy jelentés meg van osztva Önnel, a vizualizációk interakcióinak beállítását nem módosíthatja.

A *keresztszűrés* és *keresztkijelölés* kifejezésekkel az itt ismertetett viselkedéseket a **Szűrők** ablaktábla *szűrés* és *kiemelés* funkciójától különböztetjük meg.  

> [!NOTE]
> Ez a videó a Power BI Desktop és a Power BI szolgáltatás régi verzióit használja. 
>
>

<iframe width="560" height="315" src="https://www.youtube.com/embed/N_xYsCbyHPw?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>


## <a name="enable-the-visual-interaction-controls"></a>A vizualizáció-interakciók vezérlőinek engedélyezése
Ha szerkesztési engedélyekkel rendelkezik egy jelentéshez, bekapcsolhatja a vizualizáció-interakciók vezérlőit, majd testreszabhatja, hogy hogyan szűrik és emelik ki egymást a jelentésoldal vizualizációi. 

1. Aktiváljon egy vizualizációt annak kijelölésével.  
2. Jelenítse meg a **Vizualizáció-interakciók** beállításait.
    

    - A Desktopban válassza a **Formázás > Interakciók** lehetőséget.

        ![Formátum, majd interakciók kiválasztása](media/service-reports-visual-interactions/power-bi-interaction.png)

    - A Power BI szolgáltatásban nyissa meg a jelentést Szerkesztő nézetben, majd válassza a jelentés menüsávjának legördülő listáját.

        ![Vizualizáció-interakciók legördülő lista](media/service-reports-visual-interactions/power-bi-service.png)

3. Ha meg szeretné jeleníteni a vizualizáció-interakciók vezérlőit, válassza az **Interakciók szerkesztése** lehetőséget. A Power BI a jelentésoldal összes többi vizualizációjához szűrési és kiemelési ikonokat ad hozzá. Láthatjuk, hogy a faszerkezetes térkép keresztszűrést végez a diagramra és a térképre, és keresztkiemelést végez az oszlopdiagramra. Most már módosíthatja, hogyan hasson kölcsön a kijelölt vizualizáció a jelentésoldal többi vizualizációjával.
   
    ![jelentés a bekapcsolt Vizualizációk interakcióival](media/service-reports-visual-interactions/power-bi-turn-on.png)


## <a name="change-the-interaction-behavior"></a>Az interakció viselkedésének módosítása
A vizualizációk közötti interakciók megismeréséhez egyesével kijelölheti a vizualizációkat a jelentésoldalon.  Jelöljön ki egy adatpontot, sávot vagy alakzatot, és figyelje meg ennek a többi vizualizációra gyakorolt hatását. Ha a megfigyelt viselkedés nem az, amit Ön szeretne, módosíthatja az interakciókat. Ezek a módosítások mentve lesznek a jelentéssel, így Ön és a jelentés felhasználói a vizualizációk azonos interakcióit tapasztalhatják.


Először aktiváljon egy vizualizációt annak kijelölésével.  Figyelje meg, hogy a lapon lévő összes többi vizualizáció most interakciós ikonokat jelenít meg. A félkövérrel szedett ikon van alkalmazva. Következő lépésként adja meg, hogy a **kijelölt vizualizáció** milyen hatással legyen a többire.  Ha szeretné, ezt megismételheti a jelentés oldalának minden vizualizációjával.

Hogy a kiválasztott vizualizációnak a következőket kell-e tennie:
   
   * az oldalon található egyéb vizualizációk egyikének szűréséhez válassza a vizualizáció jobb felső sarkában lévő **szűrő** ikont ![szűrő ikon](media/service-reports-visual-interactions/power-bi-filter-icon.png).
   * az oldalon található másik vizualizáció keresztkiemeléséhez válassza a **kiemelés** ikont ![kiemelés ikon](media/service-reports-visual-interactions/power-bi-highlight-icon.png).
   * ne legyen hatása az oldalon található vizualizációk egyikére, akkor válassza a **nincs hatás** ikont ![nincs hatás ikon](media/service-reports-visual-interactions/power-bi-no-impact.png).

## <a name="change-the-interactions-of-drillable-visualizations"></a>Lefúrásra alkalmas vizualizációk interakcióinak módosítása
[Bizonyos Power BI-vizualizációkon lefúrás végezhető](../consumer/end-user-drill.md). Egy vizualizáción végzett lefúrás alapértelmezés szerint nem befolyásolja a jelentésoldalon lévő többi vizualizációt. Ez a viselkedés azonban módosítható. 

> [!TIP]
> Próbálja ki Ön is az [Emberi erőforrások minta PBIX-fájl](https://download.microsoft.com/download/6/9/5/69503155-05A5-483E-829A-F7B5F3DD5D27/Human%20Resources%20Sample%20PBIX.pbix) használatával. Ebben van egy lefúrást tartalmazó oszlopdiagram az **Újonnan felvett alkalmazottak** lapon.
>

1. A lefúrásra alkalmas vizualizáció aktiválásához jelölje ki azt. 

2. A lehatolás bekapcsolásához válassza a lehatolás ikont.

    ![lehatolás bekapcsolása](media/service-reports-visual-interactions/power-bi-drill-down.png)

2. A menüsávon válassza a **Formázás** > **A lefúrás szűri a többi vizualizációt** menüpontot.  Ha most egy vizualizációt részletesen elemez, akkor a jelentésoldal többi vizualizációja is változik majd, és tükrözi az aktuális elemzési kiválasztást. 

    ![a lefúrás szűri a többi vizualizációt beállítás bekapcsolása](media/service-reports-visual-interactions/power-bi-drill.png)

3. Ha a megfigyelt viselkedés nem az, amit Ön szeretne, módosíthatja az interakciókat [a fent leírtak szerint](#change-the-interaction-behavior).

## <a name="considerations-and-troubleshooting"></a>Szempontok és hibaelhárítás
Ha különböző táblákból származó mezőkkel rendelkező mátrixot hoz létre, majd a hierarchiában több elem kiválasztásával megpróbál több elemet keresztkiemeléssel megjelölni, akkor a többi vizualizáción hiba jelentkezik. 

![Videó arról a hibáról, amely a hierarchia több szintjén történő szűrésnél jelentkezik](media/service-reports-visual-interactions/cross-highlight.gif)
    
## <a name="next-steps"></a>További lépések
[Szűrés és kiemelés Power BI-jelentésekben](power-bi-reports-filters-and-highlighting.md)