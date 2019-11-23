---
title: Felbontásfa
description: 'Oktatóanyag: Felbontásfa-vizualizáció létrehozása a Power BI-ban'
author: mihart
manager: kvivek
ms.reviewer: juluczni
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 11/13/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: d653bb0193351e2ecb38c09e6b34d02eea5cce67
ms.sourcegitcommit: f7b28ecbad3e51f410eff7ee4051de3652e360e8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/13/2019
ms.locfileid: "74060614"
---
# <a name="use-the-decomposition-tree-visual-in-power-bi-preview"></a>A felbontásfa-vizualizáció használata a Power BI-ban (előzetes verzió)
[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

A felbontásfa-vizualizáció sokdimenziós adatok képi megjelenítését teszi lehetővé a Power BI-ban. Automatikusan összesíti az adatokat, és lehetővé teszi a lefúrást a dimenziók tetszőleges sorrendjében. Ugyanakkor mesterséges intelligenciával (AI-val) rendelkező vizualizáció, tehát meg lehet kérni a következő dimenzió megkeresésére, amelybe egy adott feltétel alapján le kell fúrni. Ez az alkalmi felderítés és az alapvető okok elemzése értékes eszközévé teszi.

![Felbontásfa](media/power-bi-visualization-decomposition-tree/tree-full.png)

Ez az oktatóanyag két példát használ:

- Egy ellátási lánc esetét, amely a vállalatnál a megrendelések alapján hiányzó termékek százalékos arányát elemzi.  
- Egy értékesítési esetet, amely videojátékok értékesítését bontja le számos tényező, például a játék műfaja és kiadója alapján.


## <a name="get-started"></a>Első lépések
Válassza a felbontásfa ikonját a Vizualizációk panelen.
![Felbontásfa vízjel](media/power-bi-visualization-decomposition-tree/tree-watermark.png)

A vizualizáció kétféle bemenő információt igényel.

**Elemzés** – az elemezni kívánt metrika. Ennek metrikának vagy összesítésnek kell lennie.  
**Magyarázat ez alapján:** – egy vagy több dimenzió, amelyekbe le szeretne fúrni.

Amikor a mértéket a mezőgyűjtőbe húzza, a vizualizáció frissül, és megmutatja az összesített mértéket. Az alábbi példa a hiánylistán szereplő termékek átlagos százalékos arányát (5,07%) jeleníti meg. ![Felbontásfa gyökércsomópontja](media/power-bi-visualization-decomposition-tree/tree-root.png)

A következő lépés annak az egy vagy több dimenziónak a megadása, amelyekbe le szeretne fúrni. Ezeket a mezőket vegye a **Magyarázat ez alapján:** gyűjtőbe. Figyelje meg a gyökércsomópont mellett megjelenő pluszjelet. A + választásával megadhatja, hogy melyik mezőbe szeretne lefúrni (a mezőkbe tetszőleges sorrendben fúrhat le).
![Felbontásfa menüje](media/power-bi-visualization-decomposition-tree/tree-menu.png)

Az **Előrejelzés eltérése** elem kiválasztásakor a fa kibomlik, és az oszlopban lévő értékek alapján bontja le a mértéket. Ez az eljárás megismételhető egy másik csomópont választásával a lefúráshoz.
![Felbontásfa kibontása](media/power-bi-visualization-decomposition-tree/tree-expansion.png)

Az utolsó szint egy csomópontjának kijelölése keresztszűrést végez az adatokon. Egy korábbi szint csomópontjának kiválasztása megváltoztatja az útvonalat.

![Felbontásfa menüje](media/power-bi-visualization-decomposition-tree/tree-interaction.gif)

Más vizualizációk kezelésével a felbontásfán keresztszűrés végezhető. Ennek eredményeként megváltozhat a csomópontok szinteken belüli sorrendje.
Az alábbi példában a Ubisoft alapján végeztünk keresztszűrést a fán. Az útvonal módosul, az Xbox-értékesítések az elsőről a másodikra kerülnek, a PlayStation mögé. 

Ha ekkor a Nintendo alapján végzünk keresztszűrést a fán, az Xbox-értékesítések üresek, ugyanis nincsenek Xboxra fejlesztett Nintendo-játékok. Az Xbox és az az alatti ágak ki lesznek szűrve a nézetből.

Az útvonal elrejtése ellenére a meglévő szintek (ebben az esetben a Játék műfaja) rögzítve maradnak a fán. A Nintendo csomópont kijelölése ezért automatikusan kibontja a fát a Játék műfaja szintig.

![Felbontásfa menüje](media/power-bi-visualization-decomposition-tree/tree-interaction-2.gif)


## <a name="ai-splits"></a>AI-vágás

Az „AI-vágás” segítségével megállapíthatja, hol érdemes folytatni az adatok vizsgálatát. Ezek a vágások a lista tetején jelennek meg, villanykörtével jelölve. A vágások az magas és alacsony értékek automatikus megkeresésével segítenek.

Az elemzés az Ön választása szerint két módon működhet. Az alapértelmezett viselkedése a következő:

**Magas érték**: Megvizsgálja az összes rendelkezésre álló mezőt, és megállapítja, hogy melyikbe lefúrva érhető el az elemzett mérték legmagasabb értéke.  
**Alacsony érték**: Megvizsgálja az összes rendelkezésre álló mezőt, és megállapítja, hogy melyikbe lefúrva érhető el az elemzett mérték legalacsonyabb értéke.  

Ha a hiánylista példáján a **Magas érték** lehetőséget választja, az eredmény az alábbi lesz: ![Felbontásfa AI-vágása](media/power-bi-visualization-decomposition-tree/tree-ai-split.png)

A **Terméktípus** mellett villanykörte jelenik meg, jelezve, hogy ez egy „AI-vágás” eredménye. A fa egy pontvonallal a **Betegfigyelés** csomópontot is megjelöli, mivel az eredményezi a legmagasabb hiányarányt (9,2%). 

A villanykörtére vitt egérmutató alatt elemleírás jelenik meg. Ebben a példában a leírás szövege a következő: „A hiány százalékos aránya akkor a legmagasabb, ha a terméktípus a Betegfigyelés”.

A vizualizáció úgy is konfigurálható, hogy **Abszolút** AI-vágás helyett **Relatívat** alkalmazzon. 

A relatív mód a kiugróan magas értékeket keresi meg (az oszlop adataihoz viszonyítva). Ezt a következő példa szemlélteti: ![Felbontásfa abszolút vágása](media/power-bi-visualization-decomposition-tree/tree-ai-absolute.png)

A fenti képernyőképen az észak-amerikai videójáték-értékesítések láthatók. A fa először a **Kiadó neve** szerint lett vágva, majd lefúrást végeztek a Nintendo csomópontba. A **Magas érték** választásának eredménye a **Nintendo platform** kibontása. Mivel a Nintendo (kiadó) csak Nintendo konzolra fejleszt, itt csak egyetlen érték van, tehát nem meglepő, hogy ez a legmagasabb érték.

Ennél érdekesebb vágást végezhet, ha azt vizsgálja meg, hogy melyik érték emelkedik ki a vele egy oszlopban lévő többi érték közül. Az **Abszolút** helyett a **Relatív** elemzési típust választva a következő eredmény áll elő a Nintendóhoz: ![Felbontásfa relatív vágása](media/power-bi-visualization-decomposition-tree/tree-ai-relative.png)

A javasolt érték ezúttal a **Platform a Játék műfaján belül**.  A Platform nem ad a Nintendóénál magasabb értéket (19 950 000 USD < 46 950 000 USD). Az értéke mégis kiemelkedő.

Még pontosabban fogalmazva, mivel a Játék műfajához 10 érték tartozik, a Platformhoz várható érték 4,6 millió USD lenne, ha ezek egyeneletesen oszlanának meg. Mivel a Platform értéke közel 20 millió USD, érdekes eredménynek számít, hiszen négyszerese a várt eredménynek.

A számítás menete a következő:

A Platformhoz tartozó észak-amerikai értékesítések / ABS(AVG(A Játék műfajához tartozó észak-amerikai értékesítések))  
a következőhöz képest:  
A Nintendóhoz tartozó észak-amerikai értékesítések / ABS(AVG(A Platformhoz tartozó észak-amerikai értékesítések))  

Behelyettesítve:

19 550 000 / ((19 550 000 + 11 140 000 + ... + 470 000 + 60 000) / 10) = 4,164  
a következőhöz képest:  
46 950 000 / (46 950 000 / 1) = 1  

Ha nem szeretne AI-vágásokat alkalmazni a fában, ezeket ki is kapcsolhatja az **Elemzési formázás** beállításaiban:  

![Felbontásfa AI-vágásának letiltása](media/power-bi-visualization-decomposition-tree/tree-ai-disable.png)

## <a name="tree-interactions-with-ai-splits"></a>Fa kezelése AI-vágásokkal

Több AI-szint is épülhet egymásra. Különböző (Magas érték, Alacsony érték majd újra Magas érték) AI-szintek is használhatók: ![Felbontásfa három AI-útvonallal](media/power-bi-visualization-decomposition-tree/tree-multi-ai-path.png)

Ha a fa egy másik csomópontját választja ki, az AI-vágás elölről végzi az újraszámítást. Az alábbi példában másik csomópont lett kiválasztva az **Előrejelzés eltérése** szinten. Az ez alatti szintek úgy módosulnak, hogy a megfelelő Magas és Alacsony értékeket adják. ![Felbontásfa kezelése mesterséges intelligenciával](media/power-bi-visualization-decomposition-tree/tree-ai-interactions.png)

Az AI-szintek akkor is újra lesznek számítva, ha egy másik vizualizációval keresztszűrést végez a felbontásfán. Az alábbi példán az látható, hogy a százalékos hiány a #0477-es üzemnél a legmagasabb.

![Felbontásfa keresztszűrése](media/power-bi-visualization-decomposition-tree/tree-ai-crossfilter1.png)

Ha azonban kiválasztja a sávdiagram **Április** elemét, a legmagasabb érték a **Speciális sebészeti terméktípusra** módosul. Ebben az esetben nem csak a csomópontok sorrendje változott meg, hanem egy másik oszlop lett kiválasztva. 

![Felbontásfa keresztszűrése](media/power-bi-visualization-decomposition-tree/tree-ai-crossfilter2.png)

Ha azt szeretné, hogy egy AI-szint AI nélküli szintként viselkedjen, a villanykörtét választva állíthatja vissza az alapértelmezett viselkedést. 

Bár több AI-szint egymás után fűzhető, AI-szintet nem követhet AI nélküli szint. Ha egy AI-vágást követően manuális vágást hajt végre, az AI-szintet jelző villanykörte eltűnik, és a szint normál szintté alakul át. 

## <a name="locking"></a>Zárolás

A tartalom készítője zárolhatja a szinteket a jelentés felhasználói számára. A zárolt szintek nem távolíthatók el és nem módosíthatók. A felhasználók bejárhatja a zárolt szinten belüli különböző útvonalakat, de magát a szintet nem változtathatja meg. A készítő a meglévő szint fölé vitt egérmutatóval jelenítheti meg a zárolás ikont. Tetszőleges számú szint zárolható, de zárolatlan szintek nem előzhetnek meg zároltakat.

Az alábbi példában az első két szint van zárolva. Ez azt jelenti, hogy a jelentés felhasználói módosíthatják a 3. és a 4. szintet, és akár új szinteket is beszúrhatnak ezek után. Az első két szintet azonban nem módosíthatják:

![Felbontásfa zárolása](media/power-bi-visualization-decomposition-tree/tree-locking.png)

## <a name="known-limitations"></a>Ismert korlátozások

A felbontásfa nem támogatott az alábbiaknál:  
-   Helyszíni Analysis Services

Az AI-vágás nem támogatott az alábbiaknál:  
-   Azure Analysis Services
-   Közvetlen lekérdezés
-   Power BI jelentéskészítő kiszolgáló
-   Webes közzététel
-   Összetett mértékek és az „Elemzésen” belüli bővítménysémákból származó mértékek

Az előzetes verzió egyéb korlátozásai:
- Power BI Mobile  
- Rögzítés irányítópulton
- Adatmegjelenítési funkcó
- Támogatás a Q&A-ban

## <a name="next-steps"></a>Következő lépések

[Power BI-perecdiagram](power-bi-visualization-doughnut-charts.md)

[Power BI-vizualizációk](power-bi-report-visualizations.md)

