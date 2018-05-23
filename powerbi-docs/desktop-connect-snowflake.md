---
title: Kapcsolódás Snowflake Computing-adattárházakhoz a Power BI Desktopban
description: Könnyedén csatlakozhat Snowflake Computing-adattárházakhoz, és használhatja a bennük tárolt adatokat a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 7d89ea7453a74470a73786bb8001c35db9252158
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/17/2018
---
# <a name="connect-to-snowflake-in-power-bi-desktop"></a>Kapcsolódás a Snowflake-hez a Power BI Desktopban
A Power BI Desktopban csatlakozhat egy **Snowflake** Computing-adattárházhoz, és úgy használhatja az alapul szolgáló adatokat, mint a Power BI Desktop bármely más adatforrását. 

> [!NOTE]
> Ezenkívül a **Snowflake ODBC-illesztőt** is telepítenie *kell* a **Snowflake**-összekötőt használó gépekre a **Power BI Desktop**-telepítésnek megfelelő architektúrával (32 vagy 64 bites). Kövesse az alábbi hivatkozást, és [töltse le a megfelelő Snowflake ODBC-illesztőt](http://go.microsoft.com/fwlink/?LinkID=823762).
> 
> 

## <a name="connect-to-a-snowflake-computing-warehouse"></a>Kapcsolódás egy Snowflake Computing-adattárházhoz
Ha csatlakozni kíván egy **Snowflake** Computing-adattárházhoz, válassza a Power BI Desktop **Kezdőlap** menüszalagján az **Adatok lekérése** lehetőséget. A bal oldali kategóriák közül válassza az **Adatbázis** lehetőséget, ekkor megjelenik a **Snowflake**.

![](media/desktop-connect-snowflake/connect_snowflake_2b.png)

A megjelenő **Snowflake** ablakban írja vagy illessze be a Snowflake Computing-adattárház nevét a mezőbe, és válassza az **OK** gombot. Vegye figyelembe, hogy az adatokat közvetlenül is **importálhatja** a Power BI-ba, vagy használhatja a **DirectQueryt**. További információ a DirectQueryről: [A DirectQuery használata](desktop-use-directquery.md).

![](media/desktop-connect-snowflake/connect_snowflake_3.png)

Ha a rendszer kéri, adja meg a felhasználónevét és a jelszavát.

![](media/desktop-connect-snowflake/connect_snowflake_4.png)

> [!NOTE]
> Ha egy adott **Snowflake**-kiszolgálóhoz megadta a felhasználónévét és a jelszavát, a Power BI Desktop ugyanazon hitelesítő adatokat fogja használni a későbbi csatlakozási kísérletekhez is. A hitelesítő adatokat a **Fájl > Lehetőségek és beállítások > Adatforrás-beállítások** szakaszában módosíthatja.
> 
> 

Ha sikeresen csatlakozott, megjelenik a **Kezelő** ablaka, és megjeleníti a kiszolgálón elérhető adatokat. Ezek közül kiválaszthat egy vagy több importálni kívánt elemet, és használhatja őket a **Power BI Desktopban**.

![](media/desktop-connect-snowflake/connect_snowflake_5.png)

A kiválasztott táblát **betöltheti**, amellyel az egész tábla bekerül a **Power BI Desktopba**, vagy **szerkesztheti** is a lekérdezést. Ekkor megnyílik a **Lekérdezésszerkesztő**, amellyel szűrheti vagy finomíthatja a használni kívánt adatokat, majd a finomított adatkészletet betöltheti a **Power BI Desktopba**.

## <a name="next-steps"></a>Következő lépések
A Power BI Desktop használatával számos adatforráshoz csatlakozhat. Az adatforrásokkal kapcsolatos információkért lásd az alábbi forrásanyagokat:

* [Első lépések a Power BI Desktopban](desktop-getting-started.md)
* [Adatforrások a Power BI Desktopban](desktop-data-sources.md)
* [Adatok formázása és kombinálása a Power BI Desktoppal](desktop-shape-and-combine-data.md)
* [Kapcsolódás az Excelhez a Power BI Desktopban](desktop-connect-excel.md)   
* [Adatok közvetlen bevitele a Power BI Desktopba](desktop-enter-data-directly-into-desktop.md)   

