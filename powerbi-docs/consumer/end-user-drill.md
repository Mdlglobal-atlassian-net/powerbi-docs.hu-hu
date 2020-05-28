---
title: Lehatolás és felhatolás a vizualizációkban
description: Ez a cikk bemutatja, hogyan lehet részletezni a vizualizációk mélyebb szintjeit a Microsoft Power BI szolgáltatásban.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 02/18/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 9b1cd7e7bfd808edc89dc4490e252a89ac5acb3e
ms.sourcegitcommit: 2cb249fc855e369eed1518924fbf026d5ee07eb1
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83813738"
---
# <a name="drill-mode-in-a-visual-in-power-bi"></a>Részletezés mód vizualizációkban a Power BI-ban

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Ez a cikk bemutatja, hogyan lehet részletezni a vizualizációk mélyebb szintjeit a Microsoft Power BI szolgáltatásban. Az adatpontok részletezésével és felhatolásával mélyreható betekintést nyerhet az adatokba. 

## <a name="drill-requires-a-hierarchy"></a>A részletezéshez hierarchiára van szükség

Ha a vizualizáció mögött hierarchikus adatstruktúra található, a részletesebb adatszintek kibonthatók. Tegyük fel például, hogy egy vizualizáció az olimpiai érmek számát jeleníti meg, sportonkénti, szakágankénti és versenyszámonkénti adathierarchia alapján. Alapértelmezés szerint a vizualizáció az érmek számát sportok szerinti bontásban (pl. gimnasztika, síelés, vízi sportok stb.) jeleníti meg. Ugyanakkor mivel a vizualizáció hierarchikus, egy-egy vizuális elem (például egy oszlop, egy sáv vagy egy kör) kiválasztásakor egyre részletesebb ábra jeleníthető meg. Ha a **vízi sportok** elemre kattint, megjelennek az úszásra, a műugrásra és a vízilabdára vonatkozó adatok.  Ha a **műugrás** elemre kattint, a műugró, toronyugró és szinkronugró versenyszámra vonatkozó információkat fogja látni.

Sajátos hierarchiatípust képviselnek a dátumok.  A jelentéstervezők gyakran vesznek fel hierarchiákat a vizualizációkba. A dátumhierarchiákban gyakran szerepel az év, a negyedév, a hónap és a nap. 

## <a name="figure-out-which-visuals-can-be-drilled"></a>A részletezhető vizualizációk azonosítása
Nem tudja, hogy mely Power BI-vizualizációk tartalmaznak hierarchiát? Vigye az egérmutatót egy vizualizáció fölé. Ha a tetején a képen látható részletezési vezérlők kombinációja látható, az azt jelzi, hogy a vizualizáció tartalmaz hierarchiát.

![A részletezési ikonok képernyőképe](./media/end-user-drill/power-bi-drill-icons.png)  


## <a name="learn-how-to-drill-down-and-up"></a>A lehatolás és a felhatolás ismertetése

Ebben a példában egy fatérképet használunk, amelyhez egy területből, településből, irányítószámból és áruháznévből álló hierarchia tartozik. A fatérkép a részletezés előtt megvizsgálja, hogy összesen hány egységet adtak el ebben az évben területeként. 

![A fatérkép és a hozzá tartozó szűrők képernyőképe](./media/end-user-drill/power-bi-treemaps.png)  


### <a name="two-ways-to-access-the-drill-features"></a>A részletezési funkciók elérésének két módja

A lehatolási, a felhatolási és a kibontási funkciót kétféleképpen is elérheti a hierarchiával rendelkező vizualizációkhoz. Próbálja ki őket, és használja azt, amelyik Önnek tetszik.

- Első módszer: az ikonok megjelenítéséhez és használatához mutasson egy vizualizációra.  

    ![Képernyőkép a rámutatásról.](./media/end-user-drill/power-bi-hover.png)

- Második módszer: a menü megjelenítéséhez és használatához kattintson a jobb gombbal egy vizualizációra.

    ![Képernyőkép a jobb gombbal való kattintásról.](./media/end-user-drill/power-bi-drill-menu.png)



## <a name="drill-pathways"></a>A lehatolás útvonala

### <a name="drill-down-all-fields-at-once"></a>Lehatolás minden mezőre egyszerre
![A lehatolás ikonja](./media/end-user-drill/power-bi-drill-icon3.png)

A vizualizációban való lehatoláshoz több módszert is használhat. A lehatolás ikonját választva a hierarchia következő szintjére léphet. A Kentucky és Tennessee államhoz tartozó **Terület** szint esetében egyaránt lehatolhat a település, majd az irányítószám, végül pedig az üzletnév szintjére. Az útvonal minden lépésén új információhoz juthat.

![A részletezés útvonalát ismertető diagram](./media/end-user-drill/power-bi-drill-path.png)

Válassza a felhatolás ikonját ![A felhatolás ikonja](./media/end-user-drill/power-bi-drill-icon5.png) a folyó évi összes egység terület szerinti adataihoz való visszatéréshez.

### <a name="expand-all-fields-at-once"></a>Az összes mező kibontása egyszerre
![A kibontás ikonja](./media/end-user-drill/power-bi-drill-icon6.png)

A **Kibontás** a jelenlegi nézethez egy új hierarchiaszintet ad hozzá. Így ha a **Terület** szinten van, kibonthatja, azt és hozzáadhat a fatérképhez várost, irányítószámot és nevet. Az útvonal minden lépése ugyanazt az információt jeleníti meg, és egy új szintet ad hozzá új információkkal.

![A kibontás útvonalát ismertető diagram](./media/end-user-drill/power-bi-expand-path.png)

A mezőkön egyesével is végezhet lehatolást és kibontást.


### <a name="drill-down-one-field-at-a-time"></a>Lehatolás mezőnként


1. A lehatolás ikonjának választása a bekapcsoláshoz ![Képernyőkép a lehatolás be- és kikapcsoló ikonjáról bekapcsolt állapotban.](./media/end-user-drill/power-bi-drill-icon2.png).

    Most már lehetősége van arra, hogy egy vizuális elemet kijelölve **egyszerre egy mezőnyit** hatoljon le. Példák a vizualizációs elemekre: sáv, buborék és levél.

    ![Képernyőkép a vizualizációról, amelyen egy nyíl mutat a bekapcsolt állapotú lehatolás be-/kikapcsoló ikonjára](media/end-user-drill/power-bi-drill-icon-selected.png)

    Ha nem kapcsolja be a lehatolást, egy vizualizációs elem (például egy sáv, buborék vagy levél) kiválasztásakor nem történik lehatolás. Ehelyett a program keresztszűrést végez a jelentésoldal többi diagramján.

1. Válassza ki a **TN**-hez tartozó levélcsomópontot. A fatérkép ekkor megjeleníti az összes olyan várost és területet Tennessee államban, amelyben van üzlet.

    ![Képernyőkép a fatérképről kizárólag TN adataival.](media/end-user-drill/power-bi-drill-down-one.png)

1. Jelenleg a következőket végezheti el:

    1. További, Tennesseere vonatkozó lehatolás.

    1. Tennessee egy adott városára vonatkozó lehatolás.

    1. Kibontás.

    Most folytassuk azzal, hogy egyszerre egy-egy mezőben végzünk lehatolást.  Válassza ki a **Knoxville, TN** elemet. A fatérkép most a Knoxville-ben található üzlet postai irányítószámát mutatja.

    ![Képernyőkép a fatérképről a 37919-es irányítószámmal.](media/end-user-drill/power-bi-drill-two.png)

    Nézze meg, hogyan változik a csempe, ahogy le- és felhatol a hierarchiában.

### <a name="expand-all-and-expand-one-field-at-a-time"></a>Az összes kibontása és egyszerre egy-egy mező kibontása

Egy olyan fatérkép, amely mindössze egy irányítószámot mutat, nem igazán hasznos.  Most *bontson ki* lefelé egy szintet a hierarchiában.  

1. Az aktív fatérképben válassza a *Kibontás lefelé* ikont ![Képernyőkép a kibontás lefelé ikonról](./media/end-user-drill/power-bi-drill-icon6.png). A fatérkép ekkor a hierarchia két szintjét mutatja: irányítószámot és üzletnevet.

    ![Képernyőkép a fatérképről az irányítószámmal és az üzletnévvel](./media/end-user-drill/power-bi-expand-one.png)

1. Ha meg szeretné tekinteni a Tennessee-hez tartozó adatok mind a négy hierarchiaszintjét, válassza a felhatolás nyilat addig, amíg el nem éri a faszerkezetes térképen a második szintet, amely a **Total units this year by territory and city** (Összes egység ebben az évben terület és város szerint).

    ![Képernyőkép a fatérképről TN összes adatával.](media/end-user-drill/power-bi-expand-two.png)

1. Győződjön meg róla, hogy továbbra is be van kapcsolva a lehatolás, ![Képernyőkép a lehatolás be- és kikapcsoló ikonjáról bekapcsolt állapotban.](./media/end-user-drill/power-bi-drill-icon2.png) majd válassza a *Kibontás lefelé* ikont ![Képernyőkép a kibontás lefelé ikonról](./media/end-user-drill/power-bi-drill-icon6.png). A fatérképen most ugyanannyi levél (doboz) látható, de az egyes levelekhez további részletek is megjelennek. A város és az állam mellett most már irányítószámot is mutat.

    ![Képernyőkép a vizualizációról, amely várost, államot és irányítószámot is megjelenít.](./media/end-user-drill/power-bi-expand-three.png)

1. Válassza a *kibontás lefelé* ikont még egyszer: ezzel megjeleníti a Tennesee-hez tartozó adatok mind a négy hierarchiaszintjét a fatérképen. Ha még több részletet szeretne, mutasson rá egy levélcsomópontra.

    ![Képernyőkép a fatérképről, amelyen levélcsomópont-specifikus eszköztár jelent meg.](./media/end-user-drill/power-bi-expand-all.png)

## <a name="show-the-data-as-you-drill"></a>Az adatok megjelenítése lehatoláskor
Az **Adatok megjelenítése** elemet választva megjelenítheti a részleteket. Minden egyes alkalommal, amikor részletezést vagy kibontást végez, az **Adatok megjelenítése** elemmel megjelenítheti a vizualizáció létrehozásához használt adatokat. Ez segíthet annak megértésében, hogy a hierarchiák, a részletezés és a kibontás hogyan működnek együtt a vizualizációk létrehozásában. 

A jobb felső sarokban válassza a **További beállítások** (...) lehetőséget, majd az **Adatok megjelenítése** elemet. 

![A három pont menüjének képernyőképe](./media/end-user-drill/power-bi-ellipses.png)

A következő táblázatban az látható, hogy milyen eredményt kapunk, ha az összes mező területről egyszerre hatolunk le az üzletnévre.  


![Képernyőkép a lehatolás mind a négy szintjének adatairól](./media/end-user-drill/power-bi-show-data.png)

Figyelje meg, hogy a végösszegek azonosak a **Település**, az **Irányítószám** és a **Név** esetében. Ez nem mindig van így.  Ezeknél az adatoknál azonban minden egyes irányítószámhoz és településhez csak egyetlen üzlet tartozik.  



## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások
- Alapértelmezés szerint a lehatolás nem szűri a jelentés többi vizualizációját. A jelentéstervező azonban megváltoztathatja ezt az alapértelmezett viselkedést. Részletezés közben ellenőrizze, hogy a lapon a többi vizualizációra jellemző-e keresztszűrés vagy keresztkiemelés.

- Az Önnel megosztott jelentések megtekintéséhez Power BI Pro- vagy prémium szintű licenc szükséges. [Milyen licenccel rendelkezem?](end-user-license.md)


## <a name="next-steps"></a>További lépések

[Vizualizációk a Power BI-jelentésekben](../visuals/power-bi-report-visualizations.md)

[A Power BI-jelentések](end-user-reports.md)

[Power BI – Alapfogalmak](end-user-basic-concepts.md)

Több kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
