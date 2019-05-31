---
title: Power BI-vizualizációk létrehozása a Python használatával
description: Power BI-vizualizációk létrehozása a Python használatával
author: otarb
manager: rajatt
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/18/2018
ms.author: otarb
LocalizationGroup: Create reports
ms.openlocfilehash: 7390f029144e5cb37830921071ad5c2c678b2d4d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61285580"
---
# <a name="create-power-bi-visuals-using-python"></a>Power BI-vizualizációk létrehozása a Python használatával
A **Power BI Desktopban** a **Python** használatával vizualizálhatja az adatokat.

## <a name="install-python"></a>A Python telepítése
A **Power BI Desktop** nem tartalmazza, helyezi üzembe vagy telepíti a **Python**-motort. A Python-szkriptek **Power BI Desktopban** való futtatásához külön kell telepítenie a **Pythont** a helyi számítógépen. A **Pythont** számos helyről ingyen letöltheti és telepítheti, például a [Python hivatalos letöltési oldaláról](https://www.python.org/) vagy az [Anacondáról](https://anaconda.org/anaconda/python/). A Power BI Desktopban használható Python-szkriptek jelenlegi kiadása támogatja a Unicode karaktereket és a szóközöket (üres karaktereket) a telepítési útvonalban.

## <a name="enable-python-visuals"></a>Python-vizualizációk engedélyezése
A Python-vizualizációk engedélyezéséhez válassza ki a **Fájl > Lehetőségek és beállítások > Beállítások** lehetőséget, majd a megjelenő **Beállítások** lapon gondoskodjon arról, hogy a **Beállítások** ablak **Python-szkriptelés** szakaszában meg legyen adva a Python helyi telepítési útvonala, ahogy az a következő képen látható. A következő képen a Python helyi telepítési útvonala **C:\Python27**, és ez az elérési út van megadva a szövegdobozban. Gondoskodjon arról, hogy a megjelenő elérési út megegyezzen annak a helyi Python-telepítésnek a helyével, amelyet a **Power BI Desktoppal** használni kíván.
   
   ![](media/desktop-python-visuals/python-visuals-1.png)

Miután megadta a Python telepítési helyét, készen áll a Python-vizualizációk létrehozására.

## <a name="create-python-visuals-in-power-bi-desktop"></a>Python-vizualizációk létrehozása a Power BI Desktopban
1. Egy Python-vizualizáció hozzáadásához kattintson a **Python-vizualizáció** ikonra a **Vizualizáció** panelen, ahogy az a következő képen látható.
   
   ![](media/desktop-python-visuals/python-visuals-2.png)

   Ha hozzáadunk egy jelentéshez egy Python-vizualizációt, a **Power BI Desktop** a következőket teszi:
   
   - Megjelenik a jelentésvásznon egy helyőrző Python-vizualizációs kép.
   
   - A középső panel aljánál megjelenik a **Python-szkriptszerkesztő**.
   
   ![](media/desktop-python-visuals/python-visuals-3.png)

2. Ezután adja meg a **Mezők** területen az **Értékek** szakaszban, hogy a Python-szkript mely mezőket használja fel, ahogy azt a **Power BI Desktop** bármely más vizualizációja esetében is tenné. 
    
    A Python-szkript számára csak a **Mezők** területhez hozzáadott mezők érhetők el. A **Power BI Desktop Python-szkriptszerkesztőjében** a Python-szkripten dolgozva új mezőket adhat hozzá, vagy eltávolíthatja a szükségtelen mezőket a **Mezők** területről. A **Power BI Desktop** automatikusan észleli, hogy mely mezők lettek hozzáadva vagy eltávolítva.
   
   > [!NOTE]
   > A Python-vizualizációk összesítésének alapértelmezett típusa a *nincs összegzés*.
   > 
   > 
   
3. Ezután a kiválasztott adatok alapján létrehozhat egy rajzot. 

    A mezők kiválasztásakor a **Python-szkriptszerkesztő** létrehozza a támogató Python-szkriptkötő kódot az alapján, hogy a szerkesztőpanel tetején, a szürke részen mely mezők lettek kiválasztva. Ahogy további mezőket adunk hozzá vagy távolítunk el, a Python-szkriptszerkesztő automatikusan létrehozza vagy eltávolítja a hozzájuk tartozó támogató kódot.
   
   A következő képen látható példában három mezőt választottunk ki: hp, gear és drat. Ennek eredményeképp a Python-szkriptszerkesztő a következő kötési kódot hozta létre:
   
   * Létrejött egy **dataset** nevű adathalmaz
     * Az adathalmaz a felhasználó által kiválasztott különböző mezőkből áll
   * Az alapértelmezett összesítés a *Nincs összegzés*
   * A táblavizualizációkhoz hasonlóan a rendszer csoportosítja a mezőket, és a duplikált sorok csak egyszer jelennek meg
   
   ![](media/desktop-python-visuals/python-visuals-4.png)
   
   > [!TIP]
   > Bizonyos esetekben szükség lehet arra, hogy a rendszer ne végezzen automatikus csoportosítást, vagy minden sort megjelenítsen, a duplikáltakat is beleértve. Ebben az esetben hozzáadhat egy indexmezőt az adatkészlethez, amelynek hatására a rendszer minden sort egyedinek tekint, így megakadályozza a csoportosítást.
   > 
   > 
   
   A létrejött adathalmaz neve **dataset**, a kiválasztott oszlopok pedig a saját neveik alapján érhetők el. Például a gear mező úgy érhető el, ha a Python-szkriptbe beírja a *dataset["gear"]* kifejezést.

4. Mivel az adathalmaz automatikusan létrejön a kiválasztott mezők alapján, most már írhat olyan Python-szkripteket, amelyek a Python alapértelmezett eszközére küldik az ábrázolást. Ha a szkript elkészült, kattintson a **Futtatás** lehetőségre a **Python-szkriptszerkesztőben** (**Futtatás** lehetőség a címsor jobb oldalán).
   
    A **Futtatás** lehetőség kiválasztásakor a **Power BI Desktop** azonosítja az ábrázolást, és megjeleníti azt a vásznon. Mivel a folyamat végrehajtása a helyi Python-telepítésen történik, győződjön meg arról, hogy a szükséges csomagok telepítve vannak-e.
   
   A **Power BI Desktop** újrarajzolja a vizualizációt, ha a következő események bármelyike előfordul:
   
   * Ha a **Futtatás** lehetőséget választja a **Python-szkriptszerkesztő** címsorán
   * Ha az adatok frissítés, szűrés vagy kiemelés miatt változnak

    A következő képen egy példa látható a korrelációrajzolási kódra, amely a különböző típusú gépkocsik tulajdonságai közötti korrelációkat ábrázolja.

    ![](media/desktop-python-visuals/python-visuals-5.png)

5. A vizualizációk nagyobb méretű megtekintése érdekében a **Python-szkriptszerkesztő** kis méretűre állítható. Természetesen a **Power BI Desktop** egyéb vizualizációihoz hasonlóan a korrelációs ábrázoláson keresztszűrést is alkalmazhat úgy, ha csak a sportkocsikat választja ki a gyűrűdiagramon (a fenti példaképen a jobb oldali kerek vizualizáció).

    ![](media/desktop-python-visuals/python-visuals-6.png)

6. Emellett módosíthatja a Python-szkriptet a vizualizáció testreszabásához, és a Python képességeit kihasználva paramétereket adhat az ábrázolási parancshoz.

    Az eredeti ábrázolási parancs a következő volt:

    plt.matshow(dataset.corr('pearson'))

    A Python-szkript néhány módosításával a parancs most a következő:

    plt.matshow(dataset.corr('kendall'))

    Ennek eredményeként a Python-vizualizáció a Kendall Tau korrelációs együtthatóval végzi az ábrázolást, ahogyan az a következő képen látható.

    ![](media/desktop-python-visuals/python-visuals-7.png)

    Ha egy Python-szkript futtatása hibát eredményez, a rendszer nem ábrázolja a Python-vizualizációt, hanem egy hibaüzenetet jelenít meg a vásznon. A hiba részleteinek megtekintéséhez kattintson a **Részletek megtekintése** lehetőségre a vásznon megjelenő Python-vizualizációs hibaüzenetben.

    ![](media/desktop-python-visuals/python-visuals-8.png)

    > **Python-szkriptek biztonsága:** A Python-vizualizációk alapjait a Python-szkriptek jelentik, amelyek biztonsági vagy adatvédelmi kockázatot jelentő kódot tartalmazhatnak. Egy Python-vizualizáció első alkalommal való megtekintésekor vagy használatakor egy biztonsági figyelmeztető üzenet jelenik meg. Csak akkor engedélyezze a Python-vizualizációkat, ha megbízik a szerzőben és a forrásban, vagy ha már áttekintette és értelmezte a Python-szkriptet.
    > 
    > 

## <a name="known-limitations"></a>Ismert korlátozások
A **Power BI Desktopban** a Python-vizualizációkra vonatkozik néhány korlátozás:

* Adatmennyiség korlátozásai – a Python-vizualizációk által az ábrázoláshoz felhasznált adatmennyiség 150 000 sorban van korlátozva. 150 000-nél több sor kiválasztásakor a rendszer csak az első 150 000 sort használja fel, és megjelenít egy üzenetet a képen.
* Számítási idő korlátozása – ha egy Python-vizualizáció számítási ideje meghaladja az öt percet, végrehajtási időtúllépés történik, ami egy hibát eredményez.
* Kapcsolatok – a Power BI Desktop többi vizualizációjához hasonlóan, ha több adatmezőt választ ki különböző táblákból, amelyek közt nincs meghatározott kapcsolat, akkor a rendszer hibát jelez.
* A Python-vizualizációk az adatok frissítésekor, szűrésekor és kiemelésekor frissülnek. Ugyanakkor a kép maga nem interaktív és nem szolgálhat keresztszűrés forrásaként.
* A Python-vizualizációk reagálnak más vizualizációk kiemeléseire, de nem lehet az elemeikre kattintva keresztszűrni más elemeket.
* A vásznon csak az alapértelmezett Python megjelenítőeszközön ábrázolt ábrázolások jelennek meg helyesen. Kerülje az eltérő Python megjelenítőeszközök használatát.

## <a name="next-steps"></a>Következő lépések
Tekintse meg az alábbi, a Python programozási nyelv Power BI-ban történő használatára vonatkozó további információkat.

* [Python-szkriptek futtatása a Power BI Desktopban](desktop-python-scripts.md)
* [Külső Python IDE használata a Power BI-jal](desktop-python-ide.md)

