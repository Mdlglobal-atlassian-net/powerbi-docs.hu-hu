---
title: Kapcsolódás Snowflake Computing-adattárházakhoz a Power BI Desktopban
description: Könnyedén csatlakozhat Snowflake Computing-adattárházakhoz, és használhatja a bennük tárolt adatokat a Power BI Desktopban
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: a625e5cfb99703f939ae1050a75264cd7705797a
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83347608"
---
# <a name="connect-to-a-snowflake-computing-warehouse-in-power-bi-desktop"></a>Kapcsolódás Snowflake Computing-adattárházhoz a Power BI Desktopban
A Power BI Desktopban csatlakozhat egy **Snowflake** Computing-adattárházhoz, és úgy használhatja az alapul szolgáló adatokat, mint a Power BI Desktop bármely más adatforrását. 

## <a name="connect-to-a-snowflake-computing-warehouse"></a>Kapcsolódás egy Snowflake Computing-adattárházhoz
Ha csatlakozni kíván egy **Snowflake** Computing-adattárházhoz, válassza a Power BI Desktop **Kezdőlap** menüszalagján az **Adatok lekérése** lehetőséget. A bal oldali kategóriák közül válassza az **Adatbázis** lehetőséget, ekkor megjelenik a **Snowflake**.

![](media/desktop-connect-snowflake/connect-snowflake-2b.png)

A megjelenő **Snowflake** ablakban írja vagy illessze be a Snowflake Computing-adattárház nevét a mezőbe, és válassza az **OK** gombot. Vegye figyelembe, hogy az adatokat közvetlenül is **importálhatja** a Power BI-ba, vagy használhatja a **DirectQueryt**. További információ a DirectQueryről: [A DirectQuery használata](desktop-use-directquery.md). Vegye figyelembe, hogy az AAD-beli SSO csak a DirectQueryt támogatja.

![](media/desktop-connect-snowflake/connect-snowflake-3.png)

Ha a rendszer kéri, adja meg a felhasználónevét és a jelszavát.

![](media/desktop-connect-snowflake/connect-snowflake-4.png)

> [!NOTE]
> Ha egy adott **Snowflake**-kiszolgálóhoz megadta a felhasználónévét és a jelszavát, a Power BI Desktop ugyanazon hitelesítő adatokat fogja használni a későbbi csatlakozási kísérletekhez is. A hitelesítő adatokat a **Fájl > Lehetőségek és beállítások > Adatforrás-beállítások** szakaszában módosíthatja.
> 
> 

Ha a Microsoft-fiókot szeretné használni, a Snowflake AAD-integrációt a Snowflake oldalán kell konfigurálni. Ehhez olvassa el a [Snowflake erre a témakörre vonatkozó dokumentációjának](https://docs.snowflake.net/manuals/user-guide/oauth-powerbi.html#power-bi-sso-to-snowflake) Első lépések szakaszát.

![A Microsoft-fiók hitelesítési típusa a Snowflake-összekötőben.](media/desktop-connect-snowflake/connect-snowflake-6.png)


Ha sikeresen csatlakozott, megjelenik a **Kezelő** ablaka, és megjeleníti a kiszolgálón elérhető adatokat. Ezek közül kiválaszthat egy vagy több importálni kívánt elemet, és használhatja őket a **Power BI Desktopban**.

![Az ODBC 28000-es hiba miatt sikertelen volt a kapcsolódás.](media/desktop-connect-snowflake/connect-snowflake-5.png)

A kiválasztott táblát **betöltheti**, amellyel az egész tábla bekerül a **Power BI Desktopba**, vagy **szerkesztheti** is a lekérdezést. Ekkor megnyílik a **Lekérdezésszerkesztő**, amellyel szűrheti vagy finomíthatja a használni kívánt adatokat, majd a finomított adatkészletet betöltheti a **Power BI Desktopba**.

## <a name="next-steps"></a>Következő lépések
A Power BI Desktop használatával számos adatforráshoz csatlakozhat. Az adatforrásokkal kapcsolatos információkért lásd az alábbi forrásanyagokat:

* [Mi az a Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Adatforrások a Power BI Desktopban](desktop-data-sources.md)
* [Adatok formázása és kombinálása a Power BI Desktoppal](desktop-shape-and-combine-data.md)
* [Kapcsolódás az Excelhez a Power BI Desktopban](desktop-connect-excel.md)   
* [Adatok közvetlen bevitele a Power BI Desktopba](desktop-enter-data-directly-into-desktop.md)   
