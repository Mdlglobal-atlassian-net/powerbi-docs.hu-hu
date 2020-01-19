---
title: Többoldalas jelentés létrehozása megosztott Power BI-adathalmazzal – Power BI-jelentéskészítő
description: Többoldalas jelentés létrehozása a Power BI-jelentéskészítőben egy megosztott Power BI-adathalmaz alapján.
ms.date: 01/03/2020
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 335b93720718bb72027c29c6093aad952cc4cdb2
ms.sourcegitcommit: b09de56e971b8844a3771413d1f56d49b31baaaf
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/07/2020
ms.locfileid: "75691469"
---
# <a name="create-a-paginated-report-based-on-a-power-bi-shared-dataset"></a>Többoldalas jelentés létrehozása megosztott Power BI-adathalmaz alapján

Egy Power BI Desktopban létrehozott adathalmazt adatforrásként használhat a Power BI jelentéskészítővel készített többoldalas jelentésekhez. Képzelje el a következő helyzetet: Létrehozott egy Power BI-jelentést a Power BI Desktopban. Sok időt áldozott az adatmodell megtervezésére, majd létrehozott egy sok csodás vizualizációt tartalmazó, szépséges Power BI-jelentést. A jelentése tartalmaz egy soksoros mátrixot, amelyet görgetni kell, hogy mindet megtekinthesse. A jelentés olvasói olyan nyomtatható jelentést szeretnének, amelyen ennek a mátrixnak minden sora látható. A többoldalas Power BI-jelentés alkalmas erre: egy kinyomtatható táblázat vagy mátrix több oldalra kiterjedhet, fej- és láblécekkel ellátva, az Ön által tervezett tökéletes elrendezésben. Teljessé tenné a Power BI Desktop-jelentést. Ha azt szeretné, hogy a kettő pontosan, eltérések nélkül ugyanazokra az adatokra épüljön, akkor ugyanazt az adathalmazt kell használnia.

![A Power BI Desktop és a Jelentéskészítő többoldalas jelentése](media/report-builder-shared-datasets/power-bi-desktop-report-builder-arrow-26-pgs.png)

Az adathalmaznak nem kell Prémium szintű kapacitásban lévő munkaterületen lennie, és Önnek sem kell a munkaterület tagjának lennie. Elég [Összeállítási engedéllyel](service-datasets-build-permissions.md) rendelkeznie az adathalmazra. Többoldalas jelentése közzétételéhez viszont Power BI Pro-licencre lesz szüksége. Ezen kívül legalább Közreműködői szerepkörrel kell rendelkeznie egy Prémium szintű kapacitásbeli munkaterületen.

## <a name="what-you-need"></a>Amire szükség lesz

Az alábbi lista felsorolja mindazt, ami megosztott adathalmaz Power BI Jelentéskészítőben való felhasználásához szükséges, és ami nem szükséges.

- Power BI Jelentéskészítő. [Töltse le és telepítse a Power BI Jelentéskészítőt](https://go.microsoft.com/fwlink/?linkid=2086513).
- Power BI-adathalmazhoz akkor férhet hozzá, ha rendelkezik az adathalmazra vonatkozó Összeállítási engedéllyel. Tájékozódjon az [Összeállítási engedélyről](service-datasets-build-permissions.md).
- Többoldalas jelentést Power BI Pro-licenc nélkül is létrehozhat a Jelentéskészítőben. 
- A többoldalas jelentés közzétételéhez viszont Power BI Pro-licenc szükséges. Ezen kívül legalább Közreműködői szerepkörrel kell rendelkeznie egy Prémium szintű kapacitásbeli munkaterületen. 
- Választható: Ha követni szeretné a cikk tartalmát, töltse le a [Kiskereskedelmi elemzési minta .pbix](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) Power BI Desktop-fájlt, nyissa meg a Power BI Desktopban, és vegyen fel egy sok oszlopból álló táblázatot. A **Formátum** panelen kapcsolja ki az **Összegek** beállítást. Ez után tegye közzé egy munkaterületen a Power BI szolgáltatásban.

    ![Összegek kikapcsolása](media/report-builder-shared-datasets/power-bi-desktop-totals-off.png)

## <a name="connect-to-the-power-bi-dataset"></a>Csatlakozás a Power BI-adathalmazhoz

1. Nyissa meg a Power BI Jelentéskészítőt.
1. Válassza a **Bejelentkezés** lehetőséget a Jelentéskészítő jobb felső sarkában, és jelentkezzen be Power BI-fiókjába.
1. A Jelentésadatok panelen válassza az **Új** > **Power BI-adathalmaz kapcsolat** lehetőséget.

    ![Új adathalmaz a Jelentésadatok panelen](media/report-builder-shared-datasets/power-bi-report-builder-new-dataset.png)

    > [!NOTE]
    > Egy Power BI-adathalmaz adatforrását vagy adathalmazát nem hozhatja létre a Jelentéskészítő táblázat-, mátrix- vagy diagram-varázslója használatával. Ezek alapján a létrehozásuk után hozhat létre táblázatokat, mátrixokat vagy diagramokat a varázslók használatával.

1. Keresse meg vagy tallózza ki az adathalmazt vagy az azt tartalmazó munkaterületet > **Kiválasztás**.
    A Jelentéskészítő kitölti az adathalmaz nevét.

    ![Adathalmaz kiválasztása](media/report-builder-shared-datasets/power-bi-report-builder-select-dataset.png)
    
1. Az adathalmaz az Adatforrások listájában jelenik meg a Jelentésadatok panelen.

    ![Adathalmaz a Jelentésadatok panel Adatforrások területén](media/report-builder-shared-datasets/power-bi-report-builder-data-source.png)

    Lényeges, hogy egy többoldalas jelentésen belül több Power BI-adathalmazhoz vagy más adatforráshoz is csatlakozhat.


## <a name="get-the-query-for-the-dataset"></a>Az adathalmazhoz tartozó lekérdezés átvétele

Ha az a cél, hogy a Power BI-jelentés és a Jelentéskészítőbeli jelentés adatai megegyezzenek, akkor nem elég az adathalmazhoz csatlakozni. Ehhez az adathalmazra épülő lekérdezés is szükséges.

1. Nyissa meg a Power BI-jelentést (.pbix) a Power BI Desktopban.
1. Ellenőrizze, hogy a jelentés egyik táblázata a többoldalas jelentésben kívánt összes adatot tartalmazza-e.

1. A **Nézet** menüszalagon válassza a **Teljesítményelemző** elemet.

    ![A Teljesítményelemző megnyitása](media/report-builder-shared-datasets/power-bi-performance-analyzer.png)

1. A **Teljesítményelemző** panelen válassza a **Rögzítés indítása**, majd a **Vizualizációk frissítése** lehetőséget.

    ![Vizualizációk frissítése](media/report-builder-shared-datasets/power-bi-performance-analyzer-refresh-visuals.png)

1. Bontsa ki a táblázat neve melletti pluszjelet ( **+** ), majd válassza a **Lekérdezés másolása** lehetőséget. A lekérdezés az adathalmazhoz a Power BI Jelentéskészítőben szükséges DAX-képlet.

    ![A lekérdezés másolása](media/report-builder-shared-datasets/power-bi-performance-analyzer-copy-query.png)

## <a name="create-the-dataset-with-the-query"></a>Az adathalmaz létrehozása a lekérdezéssel

1. Lépjen vissza a Power BI Jelentéskészítőbe.
1. Kattintson a jobb gombbal az **Adatforrások** területen megjelenő adathalmazra, majd válassza az **Adathalmaz hozzáadása** lehetőséget.

    ![Adatkészlet hozzáadása](media/report-builder-shared-datasets/power-bi-report-builder-add-dataset.png)

1. Adjon neki nevet az Adathalmaz tulajdonságainál, majd válassza a **Lekérdezéstervezőt**.

4. Ügyeljen rá, hogy a **DAX** lehetőség legyen kijelölve, és szüntesse meg a **Tervezési mód** ikon kijelölését.

    ![A Jelentéskészítő lekérdezéstervezője](media/report-builder-shared-datasets/power-bi-report-builder-query-designer.png)

1. A felső mezőbe illessze be a Power BI Desktopból kimásolt lekérdezést.

1. A **Lekérdezés végrehajtása** (piros felkiáltójel, !) lehetőséggel ellenőrizze, hogy működik-e a lekérdezés. 

    ![A lekérdezés futtatása](media/report-builder-shared-datasets/power-bi-report-builder-run-query.png)

    A lekérdezés eredménye az alsó mezőben jelenik meg.

    ![Lekérdezés eredményei](media/report-builder-shared-datasets/power-bi-report-builder-query-results.png)

1. Válassza az **OK** lehetőséget.

    A lekérdezés az **Adathalmaz tulajdonságai** párbeszédpanel **Lekérdezés** ablakában látható.

    ![Adathalmaz tulajdonságai párbeszédpanel](media/report-builder-shared-datasets/power-bi-report-builder-dataset-properties.png)

1. Válassza az **OK** lehetőséget.

    Az új adathalmaz most már a mezői listájával együtt látható a Jelentésadatok panelen.

    ![Adathalmaz a Jelentésadatok panelen](media/report-builder-shared-datasets/power-bi-report-builder-dataset.png)

## <a name="create-a-table-in-the-report"></a>Táblázat létrehozása a jelentésben

Táblázat létrehozására gyors módszer a Táblázat varázsló használata.

1. Válassza a **Beszúrás** menüszalag **Táblázat** > **Táblázat varázsló** elemét.

    ![A Táblázat varázsló kiválasztása](media/report-builder-shared-datasets/power-bi-report-builder-table-wizard.png)

1. Jelölje ki a DAX-lekérdezéssel létrehozott adathalmazt > **Tovább**.

    ![Adathalmaz kiválasztása](media/report-builder-shared-datasets/power-bi-report-builder-choose-dataset.png)

1. Egyszerű táblázat létrehozásához jelölje ki a kívánt mezőket a **Használható mezők** között. Egyszerre több mezőt is kijelölhet úgy, hogy kijelöli az elsőt, majd a Shift billentyűt lenyomva tartva kijelöli az utolsót.

    ![Több mező kijelölése](media/report-builder-shared-datasets/power-bi-report-builder-select-fields.png)

1. Húzza az adatmezőket az **Értékek** mezőbe > **Tovább**.

    ![Táblázat varázsló](media/report-builder-shared-datasets/power-bi-report-builder-value-fields.png)

1. Válassza ki a kívánt elrendezési lehetőségeket > **Tovább**.

1. Válassza a **Befejezés** gombot.
    A táblázat Tervezési nézetben jelenik meg.

    ![Jelentéstervező nézet](media/report-builder-shared-datasets/power-bi-report-builder-design-view.png)

1. Válassza a **Kattintson ide cím megadásához.** lehetőséget, és adjon meg egy címet.

1. A jelentés előnézetéhez válassza a **Futtatás** lehetőséget.

    ![Jelentés előnézete](media/report-builder-shared-datasets/power-bi-report-builder-preview.png)

1. A **Nyomtatási elrendezés** lehetőséggel úgy tekintheti meg a jelentést, ahogyan nyomtatásban jelenik meg. 

    Ennek a jelentésnek az elrendezésén még dolgozni kell. 54 oldalból áll, mert az oszlopok és a margók miatt a táblázat szélessége két oldal.

    ![Jelentés nyomtatási elrendezése](media/report-builder-shared-datasets/power-bi-report-builder-print-layout-2-p1-p2.png)

## <a name="format-the-report"></a>A jelentés formázása

Többféle formázási lehetőséggel érhető el, hogy a táblázat elférjen egy oldalon. 

1. Az oldal margóit a Tulajdonságok panelen teheti keskenyebbé. Ha nem látja a Tulajdonságok panelt, jelölje be a **Nézet** menüszalagon a **Tulajdonságok** jelölőnégyzetet.

1. Ne a táblázatot vagy a címét, hanem a jelentést jelölje ki.
1. A **Jelentés tulajdonságai** panel **Oldal** területén bontsa ki a **Margók** elemet, és módosítsa mindegyiket a **2 cm** értékre.

    ![Margók beállítása](media/report-builder-shared-datasets/power-bi-report-builder-page-margins.png)

1. Az oszlopokat is karcsúbbá teheti. Jelölje ki az oszlophatárt, és húzza balra a jobb szélét.

    ![Oszlopszélesség beállítása](media/report-builder-shared-datasets/power-bi-report-builder-column-width.png)

1. Egy másik lehetőség a számértékek megfelelő formátumának ellenőrzése. Jelöljön ki egy számértéket tartalmazó cellát. 
    > [!TIP]
    > Egyszerre több cellát is formázhat, ha a többi cella kijelölése közben lenyomva tartja a Shift billentyűt.

    ![Több cella kijelölése](media/report-builder-shared-datasets/power-bi-report-builder-select-cells.png)

1. A **Kezdőlap** menüszalag **Szám** szakaszában módosítsa az **Alapértelmezett** formátumot egy numerikus, például **Pénznem** formátumra.

    ![Számformátum beállítása](media/report-builder-shared-datasets/power-bi-report-builder-number-format.png)

1. A **Helyőrző** stílust módosítsa **Mintaértékekre**, hogy a formázást a cellában láthassa. 

    ![Mintaérték megjelenítése](media/report-builder-shared-datasets/power-bi-report-builder-sample-values.png)

1. Ha megteheti, helytakarékosság céljából csökkentse a tizedesjegyek számát a **Szám** szakaszban.

### <a name="getting-rid-of-blank-pages"></a>Üres oldalak kiiktatása

Előfordulhat, hogy bár a margókat és a táblázat oszlopait is keskenyebbre állította, minden második oldal üres lesz. Miért? A matematika ad magyarázatot. 

A beállított margóknak és a *jelentéstörzs* szélességének összesen kisebbnek kell lennie a jelentésformátum szélességénél.

Tegyük fel például, hogy a jelentés 210 mm × 297 mm formátumú, az oldalmargókat pedig 20 mm-re állította be. A két margó összege 40 mm, ezért a törzs szélessége legfeljebb 170 mm lehet.

1. Jelölje ki a jelentéstervező felület jobb szélét, és húzza addig, amíg a kívánt értéknél kisebbhez ér a vonalzón. 

    > [!TIP]
    > A **Törzs** tulajdonságaiban ezt pontosabban is beállíthatja. Válassza a **Szélesség** tulajdonságot a **Méret** területen.

    ![Jelentéstörzs méreteinek beállítása](media/report-builder-shared-datasets/power-bi-report-builder-body-size.png)

1. Válassza a **Futtatás** lehetőséget a jelentés előnézetének megtekintéséhez, és ügyeljen rá, hogy eltüntesse az üres oldalakat. A jelentés már csak 26 oldalból áll az eredeti 54 helyett. Sikerült!

    ![Nyomtatás üres oldalak nélkül](media/report-builder-shared-datasets/power-bi-report-builder-print-26-pgs.png)

## <a name="limitations-and-considerations"></a>Korlátozások és szempontok 

- Élő Analysis Services-kapcsolatot használó adathalmazok esetén közvetlenül csatlakozhat, ha megosztott adathalmaz helyett a mögöttes Analysis Services-kapcsolatot használja.
- A Meghirdetett vagy Minősített támogatási szinttel rendelkező adathalmazok megjelennek a rendelkezésre álló adathalmazok listájában, de nincsenek megjelölve. 

## <a name="next-steps"></a>Következő lépések

- [Mik a lapszámozott jelentések a Power BI Premiumban?](paginated-reports-report-builder-power-bi.md)