---
title: R-szkriptek futtatása a Power BI Desktopban
description: R-szkriptek futtatása a Power BI Desktopban
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 358a61c13418bd29a9e83ed7029e8b90f9a5988e
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "76161533"
---
# <a name="run-r-scripts-in-power-bi-desktop"></a>R-szkriptek futtatása a Power BI Desktopban

R-szkripteket kapott a Power BI Desktopban futtathat, majd importálhatja az eredményül szolgáló adatkészleteket egy Power BI Desktop-adatmodellbe.

## <a name="install-r"></a>Az R telepítése

Az R-szkriptek a Power BI Desktopban való futtatásához telepítenie kell az R-t a helyi gépen. Az R-t számos helyről ingyen letöltheti és telepítheti, például a [Microsoft R Application Networkről](https://mran.revolutionanalytics.com/download/) vagy a [CRAN-adattárból](https://cran.r-project.org/bin/windows/base/). Az aktuális kiadás a Unicode karakterek és szóközök (üres karakterek) használatát is támogatja a telepítési útvonalban.

## <a name="run-r-scripts"></a>R-szkriptek futtatása

Már néhány lépésben futtathat R-szkripteket és létrehozhat egy adatmodellt a Power BI Desktopban. Az adatmodellel jelentéseket hozhat létre, és megoszthatja azokat a Power BI szolgáltatásban. A Power BI Desktopban használható R-szkriptek már támogatják a tizedespontokat (.) és vesszőket (,) tartalmazó számformátumokat is.

### <a name="prepare-an-r-script"></a>R-szkriptek összeállítása

Ha egy R-szkriptet szeretne futtatni a Power BI Desktopban, hozza létre a szkriptet a helyi R-fejlesztői környezetben, és ellenőrizze, hogy sikeresen futtatható-e.

A szkript a Power BI Desktopban való futtatásához mindenképp ellenőrizze, hogy sikeresen lefut-e egy új és módosítatlan munkaterületen. Ez azt jelenti, hogy minden csomagot és függőséget kifejezetten be kell tölteni és le kell futtatni. A függő szkriptek futtatásához használhatja a `source()` parancsot.

Az R-szkriptek előkészítésére és a Power BI Desktopban való futtatására vonatkozik néhány korlátozás:

* Mivel csak az adatkeretek lesznek importálva, ezért a Power BI-ba importálni kívánt adatokat mindenképp meg kell jeleníteni egy adatkeretben.
* A Complex és Vector típusú oszlopok nem lesznek importálva, a helyükön a létrejött táblában hibaértékek szerepelnek.
* Az `N/A` értékek a Power BI Desktopban `NULL` értékekké lesznek átalakítva.
* A 30 percnél hosszabb ideig futó R-szkriptek időtúllépési hibát adnak vissza.
* Ha az R-szkriptben interaktív hívás van megadva (például felhasználói válaszra vár), az megszakítja a szkript futását.
* Az R-szkriptekben a munkakönyvtárak megadásánál teljes és nem relatív elérési utat *kell* megadni.

### <a name="run-your-r-script-and-import-data"></a>R-szkriptek futtatása és az adatok importálása

Most már futtathatja az R-szkriptet, és adatokat importálhat a Power BI Desktopba:

1. A Power BI Desktopban válassza az **Adatok lekérése**, majd az **Egyéb** > **R-szkript** lehetőséget, végül pedig a **Csatlakozás** elemet:

    ![Kapcsolódás R-szkripthez, Egyéb kategória, Adatok lekérése párbeszédpanel, Power BI Desktop](media/desktop-r-scripts/r-scripts-1.png)

2. Ha az R telepítve van a helyi gépen, csak másolja a szkriptet a szkript ablakába, és válassza az **OK**lehetőséget. A legújabb telepített verzió az R-motorként jelenik meg.

    ![R-szkript párbeszédpanel, Power BI Desktop](media/desktop-r-scripts/r-scripts-2.png)

3. Kattintson az **OK** gombra az R-szkript futtatásához. Miután a szkript sikeresen lefutott, kiválaszthatja az eredményül kapott adatkereteket, és a Power BI-modellhez adhatja azokat.

Megadhatja, hogy a rendszer melyik R-telepítést használja a szkript futtatásához. Az R telepítési beállításainak megadásához válassza a **Fájl** > **Lehetőségek és beállítások** > **Beállítások** **R-szkriptek használata** lehetőséget. Az **szkript** terület **Észlelt R-kezdőkönyvtárak** legördülő listájában megtekintheti az aktuális R-telepítési lehetőségeket. Ha a kívánt R-telepítés nem szerepel a listán, válassza az **Egyéb** lehetőséget, majd keresse meg vagy adja meg a kívánt R-telepítési könyvtárat **Az R-kezdőkönyvtár beállítása** szakaszban.

![R-szkript beállításai, Beállítások párbeszédpanel, Power BI Desktop](media/desktop-r-scripts/r-scripts-4.png)

### <a name="refresh"></a>Előnézet

Az R-szkripteket frissítheti a Power BI Desktopban. Az R-szkriptek frissítésekor a Power BI Desktop újra lefuttatja az R-szkriptet a Power BI Desktop környezetében.

## <a name="next-steps"></a>További lépések

Tekintse meg az alábbi, az R programozási nyelv Power BI-ban történő használatára vonatkozó további információkat.

* [Power BI-vizualizációk létrehozása az R használatával](desktop-r-visuals.md)
* [Külső R IDE környezet használata a Power BI-jal](desktop-r-ide.md)
