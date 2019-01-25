---
title: Adatok exportálása egy Power BI-vizualizációból
description: Adatok exportálása jelentésvizualizációból és irányítópult-vizualizációból, és azok megtekintése Excelben.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: jtlLGRKBvXY
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/26/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 83ca49a3307a12e8a92c01de4175fcb117e3163d
ms.sourcegitcommit: 54907bb59a5c31b25d368d83a0c4faa5e2f0db66
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54838439"
---
# <a name="export-data-from-visualizations"></a>Adatok exportálása vizualizációkból
Ha szeretné megtekinteni a vizualizáció létrehozásához használt adatokat, [megjelenítheti az adatokat a Power BI-ban](service-reports-show-data.md) vagy exportálhatja őket az Excelbe .xlsx- vagy .csv-fájlként. Az adatexportálási lehetőség használatához Pro- vagy Premium-licenc szükséges, valamint engedélyek az adathalmazhoz és a jelentésekhez. 

Tekintse meg, ahogy Will exportálja az adatokat az egyik jelentésében található vizualizációkból, menti őket .xlsx-fájlként, és megnyitja a fájlt az Excelben. Ezután a videó alatt látható részletes utasításokat követve próbálkozzon meg a feladat elvégzésével.

<iframe width="560" height="315" src="https://www.youtube.com/embed/KjheMTGjDXw" frameborder="0" allowfullscreen></iframe>

## <a name="from-a-visualization-on-a-power-bi-dashboard"></a>Power BI-irányítópulton található vizualizációból
1. Kattintson a vizualizáció jobb felső sarkában található három pontra.

    ![](media/power-bi-visualization-export-data/pbi-export-tile3.png)
2. Kattintson az **Adatok exportálása** ikonra.

    ![](media/power-bi-visualization-export-data/pbi_export_dash.png)
3. Az adatok exportálva lettek egy .csv-fájlba. Ha a vizualizáció szűrve van, akkor a letöltött adatok is szűrve lesznek.    
4. A böngésző megkéri, hogy mentse a fájlt.  A mentés után nyissa meg a .csv-fájlt az Excelben.

    ![](media/power-bi-visualization-export-data/pbi-export-to-excel.png)

## <a name="from-a-visualization-in-a-report"></a>Jelentésben található vizualizációból
Annak érdekében, hogy követni tudja a lépéseket, nyissa meg a [Beszerzéselemzési mintajelentést](../sample-procurement.md) Szerkesztési nézetben. Adjon hozzá egy új üres jelentésoldalt. Ezután kövesse az alábbi lépéseket, és adjon hozzá egy összesítést és egy vizualizáció-szintű szűrőt.

1. Hozzon létre egy új oszlopdiagramot.  A Mezők ablaktáblán válassza a **Hely > Város** és a **Számla > Kedvezmény százaléka** lehetőséget.  Előfordulhat, hogy a **Kedvezmény százalékát** át kell helyeznie az Érték mezőbe. 

    ![](media/power-bi-visualization-export-data/power-bi-export-data3.png)
2. Módosítsa a **Kedvezmény százaléka** összesítését **Darabszám** értékről **Átlag** értékre. Az Érték mezőben kattintson a **Kedvezmény százalékától** (előfordulhat, hogy **Kedvezmény mennyisége százalékban** néven találja) jobbra található nyílra, és válassza az **Átlag** lehetőséget.

    ![](media/power-bi-visualization-export-data/power-bi-export-data6.png)
3. Adjon hozzá egy szűrőt a **Városhoz** **Atlanta** eltávolításához.

   ![](media/power-bi-visualization-export-data/power-bi-export-data4.png)

   Most már készen állunk mindkét adatexportálási lehetőség kipróbálására. 

4. Kattintson a vizualizáció jobb felső sarkában található három pontra. Kattintson az **Adatok exportálása** elemre.

   ![](media/power-bi-visualization-export-data/power-bi-export-data2.png)
5. A Power BI online szolgáltatásban ha a vizualizáció összesítést tartalmaz (például ha módosította a **Szám** értéket *átlag*, *összeg* vagy *minimum* értékre), két lehetőség közül választhat: **Összegzett adatok** vagy **Mögöttes adatok**. A Power BI Desktopban csak **Összegzett adatokat** választhat. Az összesítésekkel kapcsolatos magyarázatokért tekintse meg [a Power BI összesítéseit](../service-aggregates.md) ismertető szakaszt.
    ![](media/power-bi-visualization-export-data/power-bi-export-data5.png)
6. Válassza az **Összegzett adatok** > **Exportálás** lehetőséget, és válassza az .xlsx vagy .csv formátumot. A Power BI exportálja az adatokat.  Ha szűrőket alkalmazott a vizualizációhoz, az exportált adatok szűrve lesznek exportálva. Ha az **Exportálás** lehetőséget választja, a böngésző megkéri, hogy mentse a fájlt. A mentés után nyissa meg a fájlt az Excelben.

   **Összegzett adatok**: Válassza ezt a lehetőséget, ha exportálni szeretné a vizualizációban látható adatokat.  Az ilyen típusú export csak azokat az adatokat (oszlopokat és méréseket) jeleníti meg, amelyekkel létrehozta a vizualizációt.  Ha a vizualizáció összesítést tartalmaz, exportálja az összesített adatokat. Például ha egy 4 sávot megjelenítő sávdiagrammal rendelkezik, 4 sornyi adatot fog kapni. Az összegzett adatok .xlsx- és .csv-fájlként érhetők el.

   Ebben a példában az Excel-exportálás egy teljes értéket jelenít meg minden városhoz. Mivel Atlantát kiszűrtük, nem szerepel az eredmények között.  A táblázat első sorában azok a szűrők láthatók, amelyeket az adatok Power BI-ból való kinyerésére használtunk.

   ![](media/power-bi-visualization-export-data/power-bi-export-data7.png)
7. Most válassza ki a **Mögöttes adatok** > **Exportálás** lehetőséget, és válassza az .xlsx formátumot. A Power BI exportálja az adatokat. Ha szűrőket alkalmazott a vizualizációhoz, az exportált adatok szűrve lesznek exportálva. Ha az **Exportálás** lehetőséget választja, a böngésző megkéri, hogy mentse a fájlt. A mentés után nyissa meg a fájlt az Excelben.

   >[!WARNING]
   >A mögöttes adatok exportálása lehetővé teszi a felhasználók számára, hogy az összes részletes adatot (az adatokban szereplő minden sort) megtekintsék. A Power BI szolgáltatás rendszergazdái ezt kikapcsolhatják a cégük számára. Ha Ön egy adatkészlet tulajdonosa, a jogvédett oszlopokat „rejtett” állapotúra állíthatja, így azok nem jelennek meg a Mezők listájában a Desktopban vagy a Power BI szolgáltatásban.


   **Mögöttes adatok**: Válassza ezt a lehetőséget, ha a vizualizáció adatait ***és*** a modell további adatait szeretné megtekinteni (részletekért tekintse meg a lenti diagramot).  ha a vizualizáció összesítést tartalmaz, a *Mögöttes adatok* kiválasztása eltávolítja az összesítést. Ha az **Exportálás** lehetőséget választja, az adatokat egy .xlsx-fájlba exportálja a rendszer, és a böngésző megkéri, hogy mentse a fájlt. A mentés után nyissa meg a fájlt az Excelben.

   Ebben a példában az Excel-exportálás az adatkészletben található minden Város sorhoz egy sort jelenít meg, és az egyetlen bejegyzéshez tartozó kedvezmény százalékát mutatja. Más szóval az adatok nem összesítve, hanem egybesimítva lettek. A táblázat első sorában azok a szűrők láthatók, amelyeket az adatok Power BI-ból való kinyerésére használtunk.  

   ![](media/power-bi-visualization-export-data/power-bi-export-data8.png)

## <a name="export-underlying-data-details"></a>Mögöttes adatok részleteinek exportálása
A **Mögöttes adatok** lehetőség kiválasztásakor több dolog történhet. Az adatok megértéséhez előfordulhat, hogy rendszergazdai vagy informatikusi segítségre lesz szüksége. A Power BI Desktop vagy a szolgáltatás jelentéskészítési nézetében megjelenik egy *mérték* a Mezők listában egy számológép ikonnal ![megjelenő ikon](media/power-bi-visualization-export-data/power-bi-calculator-icon.png). A mértékek a Power BI Desktopban jönnek létre, a Power BI szolgáltatásban nem.


| A vizualizáció tartalma |                                                                              Az exportáláskor megjelenő elemek                                                                              |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   Összesítések    |                                                 az *első* összesítés és az összesítés teljes táblájának nem rejtett adatai                                                  |
|   Összesítések    | kapcsolódó adatok – ha a vizualizáció más, az összesítést tartalmazó adattáblához *kapcsolódó* adattáblák adatait használja (mindaddig, amíg a kapcsolat \*:1 vagy 1:1 mértékű) |
|    Mértékek     |                                      A vizualizáció összes mértéke *és* minden mérték azon adattáblákból, amelyek a vizualizációban használt mértékeket tartalmaznak                                      |
|    Mértékek     |                                       Minden nem rejtett adat az adott értéket tartalmazó adattáblákból (mindaddig, amíg a kapcsolat \*:1 vagy 1:1 mértékű)                                       |
|    Mértékek     |                                      Minden adat minden olyan táblából, amely a mértékeket \*:1/1:1 arányban tartalmazó táblákhoz kapcsolódik                                      |
|  Csak mértékek  |                                                   Minden nem rejtett oszlop minden kapcsolódó táblából (a mérték kiterjesztése érdekében)                                                   |
|  Csak mértékek  |                                                             A modellmértékek másolt sorainak összegzett adatai.                                                              |

### <a name="set-the-export-options"></a>Exportálási beállítások megadása
A felhasználók számára elérhető adatexportálási beállítások típusait a Power BI jelentéstervezői adják meg. Az alábbiak közül választhat:
- Csak az összegzett adatok exportálásának engedélyezése (ez az alapértelmezett beállítás az új jelentések esetében); 
- Az összegtett és az alapul szolgáló adatok exportálásának engedélyezése (ez volt az alapértelmezett beállítás 2018 októbere előtt); 
- Minden adat exportálásának letiltása.  

    > [!IMPORTANT]
    > Azt javasoljuk, hogy a jelentéstervezők térjenek vissza a régi jelentésekhez, és manuálisan állítsák vissza az exportálási beállítást igény szerint.

1. A beállítások megadásához először nyissuk meg a Power BI Desktopot.

2. A bal felső sarokban kattintson a **Fájl** > **Lehetőségek és beállítások** > **Lehetőségek** menüpontra. 

3. Az **Aktuális fájl** területen válassza a **Jelentésbeállítások** szakaszt.

    ![a Desktop jelentésbeállításai](media/power-bi-visualization-export-data/desktop-report-settings.png)

4. Válassza ki a kívánt beállítást az **Adatexportálás** legördülő menüben.

Ezt a beállítást a Power BI szolgáltatásban is frissítheti.  

Fontos megjegyezni, hogy amennyiben a Power BI felügyeleti portál beállításai és az exportált adatok jelentésbeállításai között ütközés lép fel, a felügyeleti beállítások felülírják az adatexportálási beállításokat. 

## <a name="limitations-and-considerations"></a>Korlátozások és szempontok
* A **Power BI Desktopból** és a **Power BI szolgáltatásból** legfeljebb 30 000 sor exportálható egy .csv-fájlba.
* Az .xlsx-fájlba legfeljebb 150 000 sor exportálható.
* Az *Alapul szolgáló adatok* használatával történő exportálás sikertelen lesz, ha az adatok forrása élő Analysis Services-kapcsolat, a verzió 2016-nál korábbi, és a modellben található táblák nem rendelkeznek egyedi kulccsal.  
* Az *Alapul szolgáló adatok* használatával történő exportálás sikertelen lesz, ha az *Adatot nem tartalmazó elemek megjelenítése* beállítás be van kapcsolva az exportálandó vizualizációra vonatkozóan.
* DirectQuery használatával az adatok maximálisan exportálható mennyisége 16 MB. Ez a sorok maximális számánál kisebb exportálást eredményezhet, különösen ha sok oszlop van, az adatokat nehéz tömöríteni, vagy egyéb, a fájl méretét és az exportált sorok számát csökkentő tényezők állnak fenn.
* Ha a vizualizáció egynél több adattábla adatait használja, az adatmodellben pedig nincs kapcsolat ezen táblák között, a rendszer csak az első tábla adatait exportálja. 
* Az egyéni vizualizációk és az R-vizualizációk jelenleg nem támogatottak.
* Az adatok exportálása nem érhető el a cégen kívüli olyan felhasználók számára, akik velük megosztott irányítópultot használnak. 
* A Power BI-ban egy mező (oszlop) átnevezéséhez kattintson duplán a mezőre,majd írja be az új nevet.  Ez az új név az úgynevezett *alias*. Előfordulhat, hogy egy Power BI-jelentésben így ismétlődő mezőnevek fordulnak elő, de az Excel nem engedélyezi az ismétlődő elemek használatát.  Így az adatok Excelbe való exportálásakor a mezők aliasai visszaállnak az eredeti mező- (oszlop-) nevekre.  
* Ha a .csv-fájlban Unicode-karakter található, a szöveg az Excelben hibásan jelenhet meg. A Jegyzettömbben azonban probléma nélkül megnyitható. Unicode-karakterek lehetnek például a pénznemek szimbólumai és az idegen szavak. Megkerülő megoldásként importálhatja a .csv-fájlt az Excelbe, közvetlen megnyitás helyett. Ehhez tegye a következőket:

  1. Nyissa meg az Excelt.
  2. Az **Adatok** lapon kattintson a **Külső adatok beolvasása** > **Szövegből** elemre.
* A Power BI-rendszergazdák letilthatják az adatok exportálását.


További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

