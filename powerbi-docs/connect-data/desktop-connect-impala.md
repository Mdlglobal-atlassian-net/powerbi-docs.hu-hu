---
title: Csatlakozás Impala-adatbázishoz a Power BI Desktopban
description: Könnyedén csatlakozhat Impala-adatbázisokhoz, és használhatja a bennük tárolt adatokat a Power BI Desktopban
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: bc27f08e476b90b720368609e75099e4af325fe0
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83347746"
---
# <a name="connect-to-an-impala-database-in-power-bi-desktop"></a>Csatlakozás Impala-adatbázishoz a Power BI Desktopban
A Power BI Desktopban csatlakozhat egy **Impala**-adatbázishoz, és úgy használhatja az alapul szolgáló adatokat, mint a Power BI Desktop bármely más adatforrását.

## <a name="connect-to-an-impala-database"></a>Kapcsolódás Impala-adatbázishoz
**Impala**-adatbázishoz való csatlakozáshoz végezze el a következő lépéseket: 

1. A Power BI Desktop **Kezdőlap** szalagján válassza az **Adatok lekérése** lehetőséget. 

2. A bal oldali kategóriák közül válassza az **Adatbázis** lehetőséget. Ekkor megjelenik az **Impala**.

    ![Adatok lekérése](media/desktop-connect-impala/connect_impala_2.png)

3. A megjelenő **Impala** ablakban írja vagy illessze be az Impala-kiszolgáló nevét a mezőbe. Ezután válassza az **OK** gombot. Az adatokat közvetlenül is **importálhatja** a Power BI-ba, vagy használhatja a **DirectQueryt**. További információ a [DirectQuery használatáról](desktop-use-directquery.md).

    ![Az Impala ablaka](media/desktop-connect-impala/connect_impala_3a.png)

4. Amikor a rendszer kéri, adja meg a hitelesítő adatait, vagy válassza a névtelen csatlakozást. Az Impala-összekötő a névtelen, az alapszintű (felhasználónév + jelszó) és a Windows-hitelesítési típusokat támogatja.

    ![Impala-összekötő](media/desktop-connect-impala/connect_impala_4.png)

    > [!NOTE]
    > Ha egy adott **Impala**-kiszolgálóhoz megadta a felhasználónévét és a jelszavát, a Power BI Desktop ugyanazon hitelesítő adatokat fogja használni a későbbi csatlakozási kísérletekhez is. A hitelesítő adatokat a **Fájl > Lehetőségek és beállítások > Adatforrás-beállítások** szakaszában módosíthatja.


5. A csatlakozás után egy **kezelő** ablak jelenik meg, és megjeleníti a kiszolgálón elérhető adatokat. Válassza ki az importálandó és a **Power BI Desktopban** használni kívánt elemeket az adatokból.

    ![Navigátor ablak](media/desktop-connect-impala/connect_impala_5.png)

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások
Az **Impala**-összekötő használatára vonatkozik néhány korlátozást és egyéb szempont:

* Az Impala-összekötőt támogatják a helyszíni adatátjárók, bármelyik hitelesítési módot is válassza a három támogatott közül.

## <a name="next-steps"></a>További lépések
A Power BI Desktop használatával számos adatforráshoz csatlakozhat. Az adatforrásokkal kapcsolatos információkért lásd az alábbi forrásanyagokat:

* [Mi az a Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Adatforrások a Power BI Desktopban](desktop-data-sources.md)
* [Adatok formázása és kombinálása a Power BI Desktoppal](desktop-shape-and-combine-data.md)
* [Kapcsolódás az Excelhez a Power BI Desktopban](desktop-connect-excel.md)   
* [Adatok közvetlen bevitele a Power BI Desktopba](desktop-enter-data-directly-into-desktop.md)   
