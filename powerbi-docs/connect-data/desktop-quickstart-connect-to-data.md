---
title: 'Gyorsútmutató: Csatlakozás adatokhoz a Power BI Desktopban'
description: Csatlakozás a Power BI Desktopban elérhető adatforrásokhoz
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: quickstart
ms.date: 01/10/2020
ms.author: davidi
LocalizationGroup: quickstart
ms.openlocfilehash: d689258b4e4da5349d57b41f72d4266eb759029b
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83348597"
---
# <a name="quickstart-connect-to-data-in-power-bi-desktop"></a>Gyorsútmutató: Csatlakozás adatokhoz a Power BI Desktopban

Ebben az útmutatóban a Power BI Desktop használatával csatlakozhat adatokhoz, ami az adatmodellek és jelentések létrehozásának első lépése.

![Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_01.png)

Ha még nem regisztrált a Power BI-ra, a kezdés előtt [hozzon létre egy ingyenes próbaverziós fiókot](https://app.powerbi.com/signupredirect?pbi_source=web).

## <a name="prerequisites"></a>Előfeltételek

Az cikkben ismertetett lépések elvégzéséhez az alábbi erőforrásokra lesz szüksége:

* A Power BI Desktop letöltésére és telepítésére, amely egy ingyenesen letölthető és a helyi számítógépén futtatható alkalmazás. Közvetlenül is [letöltheti a Power BI Desktopot](https://powerbi.microsoft.com/desktop), vagy beszerezheti azt a [Microsoft Store-ból](https://aka.ms/pbidesktopstore).
* [Töltse le ezt az Excel-munkafüzet mintát](https://go.microsoft.com/fwlink/?LinkID=521962), és hozzon létre egy mappát *C:\PBID-qs* néven, ahol az Excel-fájlt tárolja majd. Az útmutató további lépéseinél feltételezzük, hogy a letöltött Excel-munkafüzet ebben a mappában található.
* A Power BI Desktop számos olyan adatösszekötőt tartalmaz, amelyek hitelesítéséhez az Internet Explorer 10 vagy újabb verziója szükséges.

## <a name="launch-power-bi-desktop"></a>A Power BI Desktop elindítása

Telepítés után indítsa el a Power BI Desktopot a helyi számítógépén. Egy Power BI-oktatóanyag jelenik meg. Követheti az oktatóanyagot, vagy bezárhatja a párbeszédpanelt, hogy üres vászonból indulhasson ki. A vásznon hozhat létre vizualizációkat és jelentéseket az adatokból.

![A Power BI Desktop üres vászonnal](media/desktop-quickstart-connect-to-data/qs-connect-data_01.png)

## <a name="connect-to-data"></a>Kapcsolódás adatokhoz

A Power BI Desktoppal számos különböző adattípushoz csatlakozhat. A források közé tartoznak az olyan egyszerű adatforrások is, mint egy Microsoft Excel-fájl. Csatlakozhat olyan online szolgáltatásokhoz is, amelyek sokféle adattípust tartalmaznak, például a Salesforce-hoz, a Microsoft Dynamicshez, az Azure Blob Storage-hoz és sok más forráshoz.

Adatokhoz való csatlakozáshoz a **Kezdőlap** menüszalagon válassza az **Adatok lekérése** lehetőséget.

![Az Adatok betöltése lehetőség a Kezdőlap menüszalagon](media/desktop-quickstart-connect-to-data/qs-connect-data_02.png)

Megjelenik az **Adatok betöltése** ablak. Választhat a különféle adatforrások közül, amelyekhez a Power BI Desktop csatlakozni képes. Ebben a gyorsútmutatóban az [Előfeltételek](#prerequisites) szakaszban letöltött Excel-munkafüzetet használjuk.

![Adatok betöltése, összes forrás](media/desktop-quickstart-connect-to-data/qs-connect-data_03.png)

Mivel ez az adatforrás egy Excel-fájl, ezért az **Adatok betöltése** ablakban az **Excel** lehetőséget választjuk, majd a **Csatlakozás** gombra kattintunk.

A Power BI kéri annak az Excel-fájlnak a helyét, amelyhez csatlakozni szeretnénk. A letöltött fájl neve *Pénzügyi minta*. Jelölje ki ezt a fájlt, majd válassza a **Megnyitás** lehetőséget.

![Adatok betöltése a Pénzügyi minta fájlból](media/desktop-quickstart-connect-to-data/qs-connect-data_04.png)

A Power BI Desktop ezt követően betölti a munkafüzetet, és beolvassa annak tartalmát, majd megmutatja az elérhető adatokat is a **Navigátor** ablakban. Ebben az ablakban kiválaszthatja, mely adatokat szeretné betölteni a Power BI Desktopba. Az importálni kívánt táblákat a táblák melletti jelölőnégyzetek bejelölésével választhatja ki. Importálja mindkét elérhető táblát.

![Adatok kijelölése a Navigátor ablakban](media/desktop-quickstart-connect-to-data/qs-connect-data_05.png)

Ha kiválasztotta az összes importálni kívánt táblát, válassza a **Betöltés** lehetőséget, ezzel importálja az adatokat a Power BI Desktopba.

## <a name="view-data-in-the-fields-pane"></a>Adatok megtekintése a Mezők panelen

A táblák betöltése után a **Mezők** táblán jelennek meg az adatok. A táblákat úgy bonthatja ki, ha a név melletti nyílra kattint. Az alábbi képen a *financials* tábla van kibontva, amelynek így az összes mezője láthatóvá válik.

![Adatok lekérése](media/desktop-quickstart-connect-to-data/qs-connect-data_06.png)

Ezzel készen is van! Csatlakozott az adatokhoz a Power BI Desktoppal, betöltötte az adatokat, és most már láthatja a táblákban elérhető mezőket is.

## <a name="next-steps"></a>További lépések

Az adatokhoz való csatlakozás után sokféle feladatot végezhet el a Power BI Desktoppal. Létrehozhat vizualizációkat és jelentéseket. Az első lépésekhez tekintse meg az alábbi forrást:

* [Első lépések a Power BI Desktoppal](../fundamentals/desktop-getting-started.md)
