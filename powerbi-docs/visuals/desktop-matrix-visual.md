---
title: Mátrixvizualizáció használata a Power BI-ban
description: Útmutató lépcsőzetes elrendezések és részletes kiemelés mátrixvizualizációval történő megvalósításához a Power BI-ban.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: fa097489fcf81ec1bb1df2162465e6413bd116c0
ms.sourcegitcommit: 0ae9328e7b35799d5d9613a6d79d2f86f53d9ab0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76040427"
---
# <a name="create-matrix-visualizations-in-power-bi"></a>Mátrixvizualizációk létrehozása a Power BI-ban

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

A Mátrix vizualizáció egy táblázathoz hasonlít.  A táblázatok kétdimenziósak, és az adatok simák, vagyis az ismétlődő értékek is megjelennek, és nincsenek összesítve. Egy mátrixszal könnyebben megjeleníthetők a fontos adatok több dimenzióban, ez ugyanis lépcsőzetes elrendezést is támogat. A mátrix automatikusan összesíti az adatokat és elérhetővé teszi a részletezést. 

Mátrixvizualizációkat a **Power BI Desktop** jelentéseiben hozhat létre, és a mátrix elemeire keresztkiemelést alkalmazhat a jelentésoldalon lévő más vizualizációkkal. Kiválaszthat például sorokat, oszlopokat vagy egyetlen cellát is, és keresztkiemeléssel láthatja el őket. Egy vagy több kijelölt cellát ki is másolhat és beilleszthet más alkalmazásokba. 

![mátrix és fánkdiagram keresztkiemeléssel](media/desktop-matrix-visual/matrix-visual_2a.png)

A mátrix számos funkcióval rendelkezik, amelyeket a cikk következő szakaszaiban be is mutatunk.


## <a name="understanding-how-power-bi-calculates-totals"></a>Hogyan számítja ki a Power BI az összegeket?

A mátrixvizualizáció használatának ismertetése előtt fontos tisztázni, hogy a Power BI hogyan számítja ki a táblázatok és mátrixok összegeit és részösszegeit. Az összegeket és részösszegeket tartalmazó sorok esetén a Power BI a mögöttes adatok összes sorának mértékét határozza meg, nem egyszerűen összeadja a látható vagy megjelenített sorok értékeit. Ez azt jelenti, hogy az összeget tartalmazó sorban a várttól eltérő értékek szerepelhetnek.

Tekintse meg az alábbi mátrixvizualizációkat. 

![táblázat és mátrix összehasonlítása](media/desktop-matrix-visual/matrix-visual_3.png)

Ebben a példában a jobb szélső Mátrix vizualizáció minden sora az egyes értékesítő/dátum kombinációkhoz tartozó *összeget* mutatja. Azonban mivel egy értékesítő több dátummal együtt is szerepel, a számok többször is előfordulhatnak. A mögöttes adatok pontos formája, valamint a látható adatok egyszerű összeadása így nem felel meg egymásnak. Ez egy gyakori trend akkor, ha az összegzett érték egy egy-a-többhöz kapcsolat egyéni oldalán áll.

Amikor összegeket vagy részösszegeket lát, ne feledkezzen meg arról, hogy ezek az értékek a mögöttes adatokon alapulnak. Nem egyszerűen a megjelenített értékekből vannak kiszámítva.

<!-- use Nov blog post video

## Expanding and collapsing row headers
There are two ways you can expand row headers. The first is through the right-click menu. You’ll see options to expand the specific row header you clicked on, the entire level or everything down to the very last level of the hierarchy. You have similar options for collapsing row headers as well.

![](media/desktop-matrix-visual/power-bi-expand1.png)

You can also add +/- buttons to the row headers through the formatting pane under the row headers card. By default, the icons will match the formatting of the row header, but you can customize the icons’ color and size separately if you want. 
Once the icons are turned on, they work similarly to the icons from PivotTables in Excel.

![](media/desktop-matrix-visual/power-bi-expand2.png)

The expansion state of the matrix will save with your report. It can be pinned to dashboards as well, but consumers will need to open up the report to change the state. Conditional formatting will only apply to the inner most visible level of the hierarchy. Note that this expand/collapse experience is not currently supported when connecting to AS servers older than 2016 or MD servers.

![](media/desktop-matrix-visual/power-bi-expand3.png)

Watch the following video to learn more about expand/collapse in the matrix:

-->
## <a name="using-drill-down-with-the-matrix-visual"></a>Részletes elemzés használata a Mátrix vizualizációval
Mátrixvizualizációval számos érdekes, korábban nem elérhető részletes elemzési tevékenység hajtható végre. Például a részletes elemzés sorok, oszlopok vagy külön szakaszok és cellák használatával. Vessünk egy pillantást ezek működésére.

### <a name="drill-down-on-row-headers"></a>Sorazonosítókon végzett részletes elemzés

Amikor a Vizualizációk panelen több mezőt ad hozzá a **Mezők** terület **Sorok** szakaszához, engedélyezi a mátrixvizualizáció sorain végzett részletes elemzést. Ez hasonlít egy hierarchia létrehozásához, amely utána lehetővé teszi a hierarchia részletezését (majd a felhatolást), és az adatok elemzését minden szinten.

Az alábbi képen a **Sorok** szakasz tartalmazza az *Értékesítési fázis* és a *Lehetőség mérete* elemeket, létrehozva egy csoportosítást (vagy hierarchiát) a részletezhető sorokban.

![A kiválasztott sorokat mutató szűrőkártya](media/desktop-matrix-visual/power-bi-rows-matrix.png)

Ha a vizualizáció a **Sorok** szakaszban csoportosítást tartalmaz, a vizualizáció megjeleníti a *részletezés* és *kibontás* ikont a vizualizáció bal felső sarkában.

![mátrix a részletezésvezérlők kiemelésével](media/desktop-matrix-visual/power-bi-matrix-drilldown.png)

Az egyéb vizualizációk részletezési és kibontási viselkedéséhez hasonlóan, ha ezekre a gombokra kattint, akkor lehetőség nyílik a részletezésre (vagy felhatolásra) a hierarchián keresztül. Ebben az esetben lehatolhatunk az *Értékesítési fázistól* a *Lehetőség méretéig*, ahogy az alábbi képen is látható, ahol a „lehatolás egy szinttel” ikon (a lefelé mutató villa) lett kiválasztva.

![mátrix a lefelé mutató villa kiemelésével](media/desktop-matrix-visual/power-bi-matrix-drill3.png)

Az ikonok használatán kívül bármelyik sorazonosító kiválasztásával is részletes elemzést végezhet, ha kiválasztja ezt a lehetőséget a megjelenő menüből.

![mátrix soraihoz tartozó menüpontok](media/desktop-matrix-visual/power-bi-matrix-menu.png)

Figyelje meg, hogy van néhány lehetőség a megjelenő menüben, amely különböző eredményekhez vezet:

A **Részletezés** kiválasztása kibontja az *ahhoz* a sorszinthez tartozó mátrixot, *kivéve* az egyéb összes sorfejlécet, annak a sorazonosítónak a kivételével, amelyet kiválasztott. Az alábbi ábrán az **Ajánlattétel** > **Részletezés** lett kiválasztva. Figyelje meg, hogy egyéb legfelső szintű sorok már nem jelennek meg a mátrixban. Ez a fajta részletezés olyan hasznos funkció, amely a keresztkiemelés szakaszában válik igazán hasznossá.

![mátrix egy szintre részletesen lebontva](media/desktop-matrix-visual/power-bi-drill-down-matrix.png)

A **Felhatolás** ikonra kattintva visszatérhet az előző felső szintű nézethez. Ha ezután az **Ajánlattétel** > **Következő szint megjelenítése** lehetőséget választja, megjelenik a következő szinten (ebben az esetben a *Lehetőség mérete* mezőben) lévő elemek növekvően rendezett listája, a magasabb szintű hierarchiakategorizálás nélkül.

![mátrix a következő szint megjelenítésével](media/desktop-matrix-visual/power-bi-next-level-matrix.png)

Válassza a bal felső sarokban lévő **Felhatolás** ikont, hogy a mátrix összes felső szintű kategóriája megjelenjen, majd válassza az **Ajánlattétel** > **Kibontás a következő szintig** lehetőséget, hogy a hierarchia mindkét szintjéhez (*Értékesítési fázis* és *Lehetőség mérete*) tartozó értékek megjelenjenek.

![mátrix a következő szint kibontásával](media/desktop-matrix-visual/power-bi-matrix-expand-next.png)

A megjelenítés tovább szabályozható a **Kibontás** menüponttal.  Válassza például az **Ajánlattétel** > **Kibontás** > **Kijelölés** lehetőséget. A Power BI minden *Értékesítési fázishoz* egy összegsort jelenít meg, az *Ajánlattétel* esetében viszont a *Lehetőség* mérete mező összes lehetőségét.

![Mátrix az Ajánlattételre alkalmazott Kibontás után](media/desktop-matrix-visual/power-bi-matrix-expand.png)

### <a name="drill-down-on-column-headers"></a>Oszlopfejléceken végzett részletes elemzés
A sorokon végzett részletes elemzéshez hasonlóan az oszlopokon is végezhet részletes elemzést. Az alábbi képen két mező található az **Oszlopok** mező területén, egy ahhoz hasonló hierarchiát létrehozva, amilyet a sorokhoz használtunk a cikk korábbi szakaszában. Az **Oszlopok** mező területén a *Régió* és a *Szegmens* található. Amikor a második mező fel lett véve az **Oszlopok** területre, új legördülő menü jelent meg a vizualizáción, amely jelenleg a **Sorok** lehetőséget mutatja.

![Mátrix egy második oszlopérték hozzáadása után](media/desktop-matrix-visual/power-bi-matrix-row.png)

Az oszlopok szerinti részletezéshez válassza az **Oszlopok** lehetőséget a mátrix bal felső sarkában található *Részletezés helye* menüből. Jelölje ki a *Keleti* régiót, majd válassza a **Részletezés** lehetőséget.

![menü az oszlopok szerinti részletezéshez](media/desktop-matrix-visual/power-bi-matrix-column.png)

A **Részletezés** kiválasztásakor megjelenik a *Régió > Keleti* oszlophierarchiájának következő szintje, ami ebben az esetben a *Lehetőségek száma*. A másik régió rejtett.

![mátrix egy szint oszlop szerinti részletezésével](media/desktop-matrix-visual/power-bi-matrix-column-drill.png)

A többi menüelem ugyanúgy működik az oszlopok, ahogy a sorok esetében (lásd az előző, a **sorazonosítókon végzett részletes elemzést** ismertető szakaszt). Oszlopok szerint ugyanúgy **megjelenítheti a következő szintet** és **kibonthat a következő szintig**, mint a sorok esetében.

> [!NOTE]
> A részletes elemzés és felhatolás ikonjai a mátrixvizualizáció bal felső sarkában csak a sorokra vonatkoznak. Ha oszlopokon szeretne részletes elemzést végezni, a helyi menüt kell használnia (a jobb gombbal kattintva).

## <a name="stepped-layout-with-matrix-visuals"></a>Lépcsőzetes elrendezés mátrixvizualizációkkal

A Mátrix vizualizáció automatikusan behúzza egy hierarchia alkategóriáit minden szülő alatt; ezt Lépcsőzetes elrendezésnek hívjuk.

A mátrixvizualizáció eredeti verziójában az alkategóriák egy teljesen külön oszlopban jelentek meg, több helyet foglalva a vizualizációban. Az alábbi képen az eredeti Mátrix vizualizáció egy táblája látható. Figyelje meg, hogy az alkategóriák külön oszlopban vannak.

![Képernyőkép az alkategóriákat külön oszlopban megjelenítő régi mátrixvizualizációról.](media/desktop-matrix-visual/matrix-visual_14.png)

Az alábbi képen a Mátrix vizualizáció látható Lépcsőzetes elrendezéssel. Figyelje meg, hogy a *Számítógépek* kategória saját, kis mértékben behúzott alkategóriákkal rendelkezik (Számítógép-kiegészítők, Asztali számítógépek, Laptopok, Monitorok stb.), ezzel átláthatóbb és tömörebb vizualizációt biztosít.

![ahogyan a jelenlegi mátrix formázza az adatokat](media/desktop-matrix-visual/matrix-visual_13.png)

A lépcsőzetes elrendezés beállításait egyszerűen módosíthatja. Ha a Mátrix vizualizáció van kiválasztva, a **Vizualizációk** panel **Formátum** szakaszában (festőhenger ikon) bontsa ki a Sorazonosítók szakaszt. Két lehetőség érhető el: a Lépcsőzetes elrendezés váltógomb (amely ki- vagy bekapcsolja ezt az elrendezést) és a Lépcsőzetes elrendezés behúzása (a behúzás mértékét adja meg képpontokban).

![Sorazonosítók kártya a Lépcsőzetes elrendezés vezérlővel](media/desktop-matrix-visual/power-bi-stepped-matrix.png)

Ha kikapcsolja a Lépcsőzetes elrendezést, a Power BI egy külön oszlopban jeleníti meg az alkategóriákat, nem pedig a szülőkategória alatt behúzva.

## <a name="subtotals-with-matrix-visuals"></a>Részösszegek a mátrixvizualizációkkal

A részösszegeket a soroknál és oszlopoknál is ki- vagy bekapcsolhatja a mátrixvizualizációkban. Az alábbi képen látható, hogy a sorok részösszegei **Be** vannak kapcsolva.

![mátrix összegekkel és részösszegekkel](media/desktop-matrix-visual/matrix-visual_20.png)

A Vizualizációk ablaktábla Formátum szakaszában bontsa ki a **Részösszegek** kártyát, és állítsa a Sorok részösszegei csúszkát a **Ki** beállításra. Ebben az esetben a részösszegek nem jelennek meg.

![mátrix a részösszegek kikapcsolásával](media/desktop-matrix-visual/matrix-visual_21.png)

Ugyanez a folyamat vonatkozik az oszlopok részösszegeire.

## <a name="cross-highlighting-with-matrix-visuals"></a>Keresztkijelölés a mátrixvizualizációkkal

A Mátrix vizualizációval a mátrix bármely eleme kiválasztható a keresztkijelölés alapjaként. Ha kijelöli egy mátrix egy oszlopát, a Power BI kiemeli ezt az oszlopot, ahogyan a jelentéslapon lévő többi vizualizáció is. Ez a keresztkijelölési mód az egyéb vizualizációk és az adatpont-kiválasztások közös funkciója volt, de ugyanez a funkció már a Mátrix vizualizációnál is elérhető.

Továbbá a Ctrl+kattintás is használható a keresztkijelöléshez. Például az alábbi képen alkategóriák egy gyűjteménye lett kiválasztva a Mátrix vizualizációból. Figyelje meg, hogy a vizualizációból ki nem választott elemek kiszürkítve jelennek meg, és az oldalon található egyéb vizualizációk a Mátrix vizualizációban végzett kijelöléseket tükrözik.

![A keresztkijelölés CTRL+kattintásos funkcióját egy mátrix- és két másik vizualizáción bemutató képernyőkép.](media/desktop-matrix-visual/matrix-visual_16.png)

## <a name="copying-values-from-power-bi-for-use-in-other-applications"></a>A Power BI értékeinek másolása és felhasználása más alkalmazásokban

Egy mátrix vagy táblázat tartalmazhat olyan adatokat, amelyeket szeretne más alkalmazásokban használni: Dynamics CRM-ben, Excelben és más Power BI-jelentésekben. Ha a Power BI-ban a jobb gombbal kattint egy vagy több kijelölt cellára, kimásolhatja azokat a vágólapra. Ez után beillesztheti őket egy másik alkalmazásba.


* Ha egyetlen cella értékét szeretné másolni, jelölje ki a cellát, kattintson a jobb gombbal, és válassza az **Érték másolása** lehetőséget. A cella formázatlan értéke felkerül a vágólapra, ahonnan beillesztheti egy másik alkalmazásba.

    ![A Mátrix vizualizáció képernyőképe az egyik értékre mutató nyíllal, a kibontott helyi menüvel, valamint az Érték másolása és a Kijelölés másolása lehetőség kiemelésével.](media/desktop-matrix-visual/power-bi-cell-copy.png)



* Ha több cellát szeretne másolni, jelölje ki a cellatartományt, vagy a CTRL billentyűt nyomva tartva jelöljön ki egy vagy több cellát. 

    ![A Mátrix vizualizáció képernyőképe három kiemelt értékről a kibontott helyi menüre mutató nyíllal, valamint az Érték másolása és a Kijelölés másolása lehetőség kiemelésével.](media/desktop-matrix-visual/power-bi-copy.png)

* A másolat tartalmazni fogja az oszlopok és a sorok fejléceit.

    ![Excel sorok és oszlopok képernyőképe a beillesztett értékekkel.](media/desktop-matrix-visual/power-bi-copy-selection.png)

* Ha magáról a vizualizációról szeretne olyan másolatot készíteni, amely csak a kijelölt cellákat tartalmazza, akkor jelöljön ki egy vagy több cellát a CTRL+jobb-klikk módszerrel, majd válassza a **Vizualizáció másolása** lehetőséget.

    ![A vizualizáció másolása lehetőséget bemutató képernyőkép](media/desktop-matrix-visual/power-bi-copy-visual.png)

* A másolat egy újabb mátrixvizualizáció lesz, de csak a kimásolt adatokat fogja tartalmazni.

    ![A vizualizációmásolási példát bemutató képernyőkép](media/desktop-matrix-visual/power-bi-copy-visual-example.png)

## <a name="shading-and-font-colors-with-matrix-visuals"></a>Árnyékolás és betűtípus mátrixvizualizációkkal
A Mátrix vizualizációval Feltételes formázást (színek, árnyékolás és adatsávok) alkalmazhat a mátrixban található cellák hátterére, valamint magára a szövegre és az értékekre is.

Feltételes formázáshoz jelölje ki a mátrixvizualizációt, és nyissa meg a **Formázás** panelt. Bontsa ki a **Feltételes formázás** kártyát, és kapcsolja **Be** a **Háttérszín**, **Betűszín** vagy **Adatsávok** lehetőséget. Egy ilyen beállítás bekapcsolása után megjelenik a *Speciális vezérlők* hivatkozása, amely lehetővé teszi a színek és a színformátum értékeinek testreszabását.
  
  ![Formázás panel az Adatsávok vezérlővel](media/desktop-matrix-visual/power-bi-matrix-data-bars.png)

Válassza a *Speciális vezérlők* hivatkozást, így megjelenik egy párbeszédpanel, amelyen végrehajthatja a beállításokat. Ez a példa az **Adatsávok** párbeszédpanelt mutatja be.

![Adatsávok panel](media/desktop-matrix-visual/power-bi-data-bars.png)

## <a name="next-steps"></a>Következő lépések

[A Power BI-hoz készült Power Apps-vizualizációk](power-bi-visualization-powerapp.md)

[Vizualizációtípusok a Power BI-ban](power-bi-visualization-types-for-reports-and-q-and-a.md)