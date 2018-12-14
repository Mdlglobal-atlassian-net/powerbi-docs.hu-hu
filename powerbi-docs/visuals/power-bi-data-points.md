---
title: Nagy adathalmazok, adatpontkorlátok és adatstratégiák
description: Vizualizációkra vonatkozó adatkorlátozások és adatcsökkentési stratégiák
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/02/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 125787bab3892f2e9616866a9d5487837131d0ed
ms.sourcegitcommit: 4f46d71ff6026c1c158f007425aefdcb501f48ee
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/06/2018
ms.locfileid: "52981491"
---
# <a name="data-point-limits-and-strategies-by-visual-type"></a>Adatpontkorlátok és -stratégiák vizualizációtípus szerint

Amikor a Power BI-ban vizualizációt renderel, a vizualizációnak gyorsan és pontosan kell megjelennie. Ez minden vizualizációtípushoz külön konfigurált háttérbeli algoritmusokat igényel. A Power BI-beli vizualizációknak elég rugalmasnak kell lenniük a különböző méretű adathalmazok kezeléséhez. Egyes adathalmazok csupán néhány adatpontból állnak, mások viszont több petabájtnyiból. Ez a cikk a Power BI által a vizualizációk rendereléséhez használt stratégiákat ismerteti.

## <a name="data-reduction-strategies"></a>Adatcsökkentési stratégiák
Minden vizualizáció magában foglal egy vagy több *adatcsökkentési stratégiát*, így nagyobb adatmennyiségek is kezelhetők. Még az egyszerű táblák is alkalmaznak olyan stratégiát, amellyel elkerülhető a teljes adathalmaz betöltése az ügyfélen.  A használt csökkentési stratégia vizualizációtípusonként különböző. Minden vizualizáció a támogatott *adatcsökkentési stratégiák* közül választ a kiszolgálónak küldött adatkérés generálásának részeként. 

Minden vizualizáció az adatok teljes mennyiségét befolyásoló módon szabályozza ezeknek a stratégiáknak a paramétereit.   

## <a name="strategies"></a>Stratégiák
Minden stratégiának megvannak a megjelenített adatok formáján és típusán alapuló alapértelmezései. Az alapértelmezések azonban a felhasználók számára megfelelő megjelenítés érdekében felülírhatók a Power BI Formázás paneljén. 

* **Adatablakok** (szegmentálás): A felhasználók úgy görgethetik az adatokat a vizualizációban, hogy egymás után töltik be a teljes adathalmaz részleteit.
* **Első N**: Csak az első N elem megjelenítése
* **Egyszerű minta**: Az első, az utolsó, és a köztük egyenlő közökkel elhelyezkedő N elem megjelenítése.
* **Utolsó N**: Csak az utolsó N elem megjelenítése.  Gyakran frissített adatok figyelésére hasznos.
* **Sűrű mintavételezés** – Továbbfejlesztett mintavételezési algoritmus, amely jobban figyelembe veszi a kiugró értékeket, és/vagy egy görbe alakját.
    * **Dobozolt sor-mintavételezés** – Dobozokba sorolt kiugró értékeken alapuló mintaadatpontok egy tengely mentén
    * **Átfedéses pont-mintavételezés** – Mintaadatpontok átfedő értékek alapján, a kiugró értékek megőrzésére

## <a name="statistics"></a>Statisztika
Egyes modellek statisztikát tudnak adni az egyes oszlopokban előforduló értékek számáról. Ha rendelkezésre áll ilyen információ, akkor ezt kihasználva több hierarchia is jobban kiegyensúlyozható, hacsak a vizualizáció kifejezetten felül nem írja az értékek számát egy stratégiában.

További információt [Az Analysis Services újdonságai](https://docs.microsoft.com/en-us/sql/analysis-services/what-s-new-in-analysis-services?view=sql-server-2017) című cikkben talál

## <a name="dynamic-limits"></a>Dinamikus korlátok
A fenti stratégiákon kívül a csoportosítóoszlopok két hierarchiájával rendelkező vizualizációk (tengely és felirat, vagy kategória és adatsor) egy további, *dinamikus korlátok* nevű stratégiát is használnak.  A dinamikus korlátok az adatpontok jobb kiegyensúlyozására vannak kialakítva. 

A dinamikus korlátok alkalmasabbak a ritka adatpontok kiválasztására, mint a statikus korlátok. Egy vizualizáció konfigurálható például úgy, hogy 100 kategóriát és 10 adatsort válaszon ki, összesen 1000 ponttal. A tényleges adatok azonban 50 kategóriába és 20 adatsorba tartoznak.  A lekérdezés futásakor a dinamikus korlátok mind a 20 adatsort kiválasztják a kért 1000 pont betöltéséhez.

A dinamikus korlátok stratégiája automatikusan alkalmazva lesz megfelelő kiszolgáló esetén, az alábbiak szerint:

* Helyszíni SSAS 2016 vagy újabb verzióval rendelkező Power BI Desktopban [a kiszolgáló SuperDax-képességeit kihasználva](https://blogs.msdn.microsoft.com/analysisservices/2015/09/02/whats-new-in-microsoft-sql-server-analysis-services-tabular-models-in-sql-server-2016-ctp-2-3/)

* A Desktopban és a Power BI szolgáltatásban importált modell, Direct Query, a szolgáltatással való élő kapcsolat, vagy élő AS PaaS-kapcsolat használatakor. 

* A Power BI szolgáltatásban, helyszíni SSAS-hez helyszíni átjárón keresztül kapcsolódva nem használhatók dinamikus korlátok. A helyszíni átjáró nem támogatja teljes körűen a dinamikus korlátok stratégiáját, amely más struktúrájú eredményeket ad vissza a helyszíni SSAS-től.  

## <a name="strategies-and-data-point-limits-by-visual-type"></a>Stratégiákra és adatpontokra vonatkozó korlátozások vizualizációtípus szerint

### <a name="area-chart"></a>Területdiagram
Lásd: [A vonalas mintavételezés működése](../desktop-high-density-sampling.md#how-the-new-line-sampling-algorithm-works)

### <a name="barcolumn-chart"></a>Sáv- és oszlopdiagram
- Kategorikus módban
    - Kategóriák: Virtualizálás egyszerre 500 sort tartalmazó ablakokkal
    - Adatsorozatok: Első 60
    - Skaláris módban (használhat dinamikus korlátokat)
        - Pontok maximális száma: 10 000
        - Kategóriák: 500 értékből álló minta
        - Adatsorozatok: Az első 20 érték

### <a name="card-multirow"></a>Kártya (többsoros) 
- Értékek: Virtualizálás egyszerre 200 sort tartalmazó ablakokkal

### <a name="combo-chart"></a>Kombinált diagram
 Ugyanazokat a stratégiákat használja, mint az oszlopdiagram. Lényeges, hogy a **kombinált diagramban** lévő vonal nem azt a sűrű algoritmust használja, amelyet a **vonaldiagram**.

### <a name="custom-visuals"></a>Egyéni vizualizációk
Akár 30 000 is lehet, de a vizualizáció készítői döntik el, hogy mely stratégiák legyenek használva

### <a name="doughnut"></a>Perec
- Pontok maximális száma: 3,500
- Csoport: Első 500
- Részletek: Első 20

### <a name="filled-map-choropleth"></a>Felületkartogram 
A kartogram használhat statisztikákat vagy dinamikus korlátokat. A Power BI a következő sorrendben kísérli meg a csökkentést: dinamikus korlátok, statisztikák, végül konfiguráció. 
- Pontok maximális száma: 10 000
- Kategóriák: Első 500
- Adatsorok (ha X és Y is létezik): Első 20

### <a name="funnel"></a>Tölcsér
- Pontok maximális száma: 3,500
- Kategóriák: Első 3500

### <a name="kpi"></a>KPI
- Trendtengely
- Utolsó 3500

### <a name="line-chart"></a>Vonaldiagram
Lásd: [A vonalas mintavételezés működése](../desktop-high-density-sampling.md#how-the-new-line-sampling-algorithm-works)

### <a name="line-chart-high-density"></a>Vonaldiagram, nagy sűrűségű
Lásd: [Sűrű mintavételezés](../desktop-high-density-sampling.md)

### <a name="map"></a>Térkép 
- Pontok maximális száma: 3,500

A konfigurációtól függően a térképen a következők szerepelhetnek:
- Hely: Első 3500
- Hely, méret: Első 3500
- Hely, összesített hosszúsági és szélességi adatok (+/-méret): Első 3500
- Szélesség, hosszúság – lásd: [nagy sűrűségű pontdiagram](desktop-high-density-scatter-charts.md)
- Szélesség, hosszúság, méret: Első 3500
- Jelmagyarázat, szélesség, hosszúság – lásd: [nagy sűrűségű pontdiagram](desktop-high-density-scatter-charts.md)
- Jelmagyarázat, szélesség, hosszúság, méret: Első 233 jelmagyarázat, első 15 szélesség és hosszúság (használhat statisztikákat vagy dinamikus korlátokat)
- Hely, jelmagyarázat, szélesség és hosszúság összesítve (+/-méret): Első 233 hely, első 15 jelmagyarázat (használhat statisztikákat vagy dinamikus korlátokat)

### <a name="matrix"></a>Mátrix
- Sorok: Virtualizálás egyszerre 500 sort tartalmazó ablakokkal
- Oszlopok: Első 100 csoportosítási oszlop 
- Értékek: a többszörös értékek nem számítanak az adatcsökkentésnél

### <a name="radial-gauge"></a>Tárcsa
Nincs adatcsökkentési stratégia

### <a name="slicer"></a>Szeletelő
- Értékek: Virtualizálás egyszerre 200 sort tartalmazó ablakokkal

### <a name="scatter-chart-high-density"></a>Pontdiagram (nagy sűrűségű)
Lásd: [Nagy sűrűségű pontdiagramok](https://docs.microsoft.com/en-us/power-bi/visuals/desktop-high-density-scatter-charts)

### <a name="pie"></a>Torta
- Pontok maximális száma: 3,500
- Csoport: Első 500
- Részletek: Első 20

### <a name="r--python-visuals"></a>R- és Python-vizualizációk
150 000 sorra korlátozva. Több, mint 150 000 sor kiválasztása esetén csak az első 150 000 sor lesz használva

### <a name="ribbon-chart"></a>Szalagdiagram
- Kategorikus módban
    - Kategóriák: Virtualizálás (adatablakok) egyszerre 500 sort tartalmazó ablakokkal
    - Adatsorozatok: Első 60
    - Skaláris módban (használhat dinamikus korlátokat)
        - Pontok maximális száma: 10 000
        - Kategóriák: 500 értékből álló minta
        - Adatsorozatok: Az első 20 érték

### <a name="shape-map"></a>Alakzat leképezése
A kartogram használhat statisztikákat vagy dinamikus korlátokat. 
- Pontok maximális száma: 10 000
- Kategóriák: Első 500
- Adatsorok (ha X és Y is létezik): Első 20

### <a name="table"></a>Tábla
- Értékek: Virtualizálás (adatablakok) egyszerre 500 sort tartalmazó ablakokkal

### <a name="tree-map-this-could-use-statistics-or-dynamic-limits"></a>Fatérkép (használhat statisztikákat vagy dinamikus korlátokat)
- Pontok maximális száma: 3,500
- Csoport: Első 500
- Részletek: Első 20

### <a name="waterfall-chart"></a>Vízesésdiagram
- Ha csak a kategóriagyűjtő adott
    - Pontok maximális száma: 3,500
    - Csak kategória – első 3500
- Ha a kategória és a lebontása is szerepel
    - Kategória: Virtualizálás (adatablakok) egyszerre 30 sort tartalmazó ablakokkal
    - Lebontás – Az első 200 érték


## <a name="next-steps"></a>Következő lépések
[Vizualizációtípusok](power-bi-report-visualizations.md)
