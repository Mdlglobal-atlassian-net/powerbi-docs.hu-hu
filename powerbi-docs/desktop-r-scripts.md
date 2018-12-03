---
title: R-szkriptek futtatása a Power BI Desktopban
description: R-szkriptek futtatása a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 25fbcbeba8be2148269fa8eb6d2ac632eb8efb0f
ms.sourcegitcommit: 2ae660a7b70fce23eb58b159d049eca44a664f2c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/30/2018
ms.locfileid: "52670049"
---
# <a name="run-r-scripts-in-power-bi-desktop"></a>R-szkriptek futtatása a Power BI Desktopban
R-szkripteket futtathat közvetlenül a **Power BI Desktopban** is, és az így kapott adatkészleteket importálhatja Power BI Desktop-adatmodellekbe.

## <a name="install-r"></a>Az R telepítése
Az R-szkriptek a Power BI Desktopban való futtatásához telepítenie kell az **R**-t a helyi gépen. Az **R**-t számos helyről ingyen letöltheti és telepítheti, például a [Revolution Open letöltőoldalról](https://mran.revolutionanalytics.com/download/) vagy a [CRAN tárból](https://cran.r-project.org/bin/windows/base/). A Power BI Desktopban használható R-szkriptek jelenlegi kiadása támogatja a Unicode karaktereket és a szóközöket (üres karaktereket) a telepítési útvonalban.

## <a name="run-r-scripts"></a>R-szkriptek futtatása
A Power BI Desktopban mindössze néhány lépéssel R-szkriptek futtatásával létrehozhat egy adatmodellt, amelyből aztán jelentéseket hozhat létre, és megoszthatja azokat a Power BI szolgáltatásban. A Power BI Desktopban használható R-szkriptek már támogatják a tizedespontokat (.) és vesszőket (,) tartalmazó számformátumokat is.

### <a name="prepare-an-r-script"></a>R-szkriptek összeállítása
Ha egy R-szkriptet szeretne futtatni a Power BI Desktopban, hozza létre a szkriptet a helyi R-fejlesztői környezetben, és ellenőrizze, hogy sikeresen futtatható-e.

A szkript a Power BI Desktopban való futtatásához mindenképp ellenőrizze, hogy sikeresen lefut-e egy új és módosítatlan munkaterületen. Ez azt jelenti, hogy minden csomagot és függőséget kifejezetten be kell tölteni és le kell futtatni. A függő szkriptek futtatásához használhatja a *source()* parancsot.

Az R-szkriptek előkészítésére és a Power BI Desktopban való futtatására vonatkozik néhány korlátozás:

* Csak az adatkeretek lesznek importálva, ezért a Power BI-ba importálni kívánt adatokat mindenképp meg kell jeleníteni egy adatkeretben.
* A Complex és Vector típusú oszlopok nem lesznek importálva, a helyükön a létrejött táblában hibaértékek szerepelnek
* Az N/A értékek a Power BI Desktopban NULL értékekké lesznek átalakítva.
* A 30 percnél hosszabb ideig futó R-szkriptek időtúllépési hibát adnak vissza.
* Ha az R-szkriptben interaktív hívás van megadva (például felhasználói válaszra vár), az megszakítja a szkript futását.
* Az R-szkriptekben a munkakönyvtárak megadásánál teljes és nem relatív elérési utat *kell* megadni.

### <a name="run-your-r-script-and-import-data"></a>R-szkriptek futtatása és az adatok importálása
1. A Power BI Desktopban az R-szkriptek adatösszekötője az **Adatok lekérése** menüpontban található. Az R-szkript futtatásához válassza az **Adatok lekérése &gt; Továbbiak...**, majd az **Egyéb &gt; R-szkript** lehetőséget, amint az az alábbi ábrán is látható:
   
   ![](media/desktop-r-scripts/r-scripts-1.png)
2. Ha az R telepítve van a helyi gépen, a rendszer a legfrissebb telepített verziót választja R-motorként. Egyszerűen másolja a szkriptet a szkriptablakba, és kattintson az **OK** gombra.
   
   ![](media/desktop-r-scripts/r-scripts-2.png)
3. Ha az R nincs telepítve, nem azonosítható, vagy több példányban is telepítve van a helyi gépen, nyissa ki **Az R telepítési beállításai** területet a telepítési beállítások megjelenítéséhez, vagy válassza ki, melyik telepítéssel szeretné futtatni az R-szkriptet.
   
   ![](media/desktop-r-scripts/r-scripts-3.png)
   
   Ha az R telepítve van, de a rendszernek nem sikerült azonosítania, közvetlenül megadhatja a helyét **Az R telepítési beállításai** terület megnyitásakor megjelenő szövegmezőben. A fenti képen a *C:\Program Files\R\R-3.2.0* elérési út van megadva a szövegmezőben.
   
   Az R telepítési beállításai terület a Beállítások párbeszédablak R-szkriptek használata szakaszának közepén található. Az R telepítési beállításainak megadásához válassza a **Fájl > Lehetőségek és beállítások**, majd a **Beállítások > R-szkriptek használata** lehetőséget. Ha az R több telepítése is elérhető, egy legördülő menü jelenik meg, amelyből kiválaszthatja a használni kívánt telepítést.
   
   ![](media/desktop-r-scripts/r-scripts-4.png)
4. Kattintson az **OK** gombra az R-szkript futtatásához. Miután a szkript sikeresen lefutott, kiválaszthatja az eredményül kapott adatkereteket, és a Power BI-modellhez adhatja azokat.

### <a name="refresh"></a>Frissítés
Az R-szkripteket frissítheti a Power BI Desktopban. Az R-szkriptek frissítésekor a Power BI Desktop újra lefuttatja az R-szkriptet a Power BI Desktop környezetében.

## <a name="next-steps"></a>Következő lépések
Tekintse meg az alábbi, az R programozási nyelv Power BI-ban történő használatára vonatkozó további információkat.

* [R-vizualizációk létrehozása a Power BI Desktopban](desktop-r-visuals.md)
* [Külső R IDE környezet használata a Power BI-jal](desktop-r-ide.md)

