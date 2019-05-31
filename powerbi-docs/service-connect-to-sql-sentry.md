---
title: Csatlakozás az SQL Sentryhez a Power BI használatával
description: A Power BI-hoz készült SQL Sentry
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 1fc8decc70ade009a7c4236686cfe9cf72adb54d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61161707"
---
# <a name="connect-to-sql-sentry-with-power-bi"></a>Csatlakozás az SQL Sentryhez a Power BI használatával
Az SQL Sentry által gyűjtött teljesítményadatok egyszerűen elemezhetők a Power BI-jal. A Power BI begyűjti az adatait, majd összeállít egy alapértelmezett irányítópultot és az adatokon alapuló jelentéseket.

Kapcsolódjon a Power BI-hoz készült [SQL Sentry tartalomcsomaghoz](https://app.powerbi.com/groups/me/getdata/services/sql-sentry).

>[!NOTE]
>A kapcsolódáshoz szüksége lesz egy SQL Sentry-fiókra, amellyel a http://cloud.sqlsentry.com oldalhoz csatlakozik, valamint egy adatbázis-azonosítóra, amelyet monitorozni fog.  Az adatbázis-azonosító helyével kapcsolatos útmutatást alább találja.

## <a name="how-to-connect"></a>Csatlakozás
1. A bal oldali navigációs ablaktábla alján kattintson az **Adatok lekérése** elemre.
   
   ![](media/service-connect-to-sql-sentry/pbi_getdata.png)
2. A **Szolgáltatások** mezőben kattintson a **Lekérés** elemre.
   
   ![](media/service-connect-to-sql-sentry/pbi_getservices.png) 
3. Válassza az **SQL Sentry \> Lekérés** lehetőséget.
   
   ![](media/service-connect-to-sql-sentry/sqlsentry.png)
4. Adja meg a Power BI-ban monitorozni kívánt adatbázis **adatbázis-azonosítóját**. [Ennek a helyével](#FindingParams) kapcsolatban lásd alább.
   
   ![](media/service-connect-to-sql-sentry/img2400.png)
5. A Hitelesítési módszernél válassza az **oAuth2 \> Bejelentkezés** lehetőséget.
   
   Mikor a rendszer arra kéri, adja meg a cloud.sqlsentry.com oldalon használt hitelesítő adatait, és kövesse az SQL Sentry hitelesítési folyamatát.
   
   ![](media/service-connect-to-sql-sentry/img6400.png)
   
   Az első csatlakozás alkalmával a Power BI megkéri, hogy adjon olvasási hozzáférést a fiókjához. Kattintson az Engedélyezés gombra az importálási folyamat indításához.  Az importálás a fiókban lévő adatok mennyiségétől függően pár percig is eltarthat.
   
   ![](media/service-connect-to-sql-sentry/img7400.png)
6. Miután a Power BI importálta az adatokat, egy új irányítópult, jelentés és adatkészlet jelenik meg a bal oldali navigációs panelen. Az új elemeket egy sárga csillag \* jelöli:
   
   ![](media/service-connect-to-sql-sentry/img8200.png)
7. Válassza az SQL Sentry irányítópultot.
   
   Ez a Power BI által az adatok megjelenítéséhez létrehozott alapértelmezett irányítópult. Az irányítópultot igény szerint módosíthatja, hogy az adatok a kívánt módon jelenjenek meg.
   
   ![](media/service-connect-to-sql-sentry/img9dashboard800.png)

**Mi a következő lépés?**

* [Kérdéseket tehet fel a Q&A mezőben](consumer/end-user-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](consumer/end-user-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

## <a name="whats-included"></a>Tartalom
A következő, az SQL Sentryből származó adatok állnak rendelkezésre a Power BI-ban:

| Tábla neve | Leírás |
| --- | --- |
| Kapcsolat |A tábla az SQL Sentry definiált kapcsolataival kapcsolatos információkat tartalmaz. |
| Dátum<br /> |A tábla a mai naptól visszamenőleg az első olyan napig tartalmazza a dátumokat, amelyre vonatkozóan a rendszer teljesítményadatokat gyűjtött és őrzött meg. |
| Állásidő<br /> |A tábla a környezetben lévő monitorozott kiszolgálók állásidejével és üzemidejével kapcsolatos adatokat tartalmaz. |
| Memóriahasználat<br /> |A tábla az egyes kiszolgálók elérhető vagy szabad memóriakapacitásával kapcsolatos adatokat tartalmaz.<br /> |
| Kiszolgáló<br /> |A tábla a környezetben lévő kiszolgálók rekordjait tartalmazza. |
| Kiszolgáló állapota<br /> |A tábla a környezet egyéni feltételei által kiváltott események adatait tartalmazza a súlyossági értékekkel és darabszámokkal együtt. |

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Paraméterek helye
Az **Adatbázis-azonosító** megállapításához jelentkezzen be a <https://cloud.sqlsentry.com> oldalra egy új böngészőablakban.  Az **Adatbázis-azonosító** a fő áttekintő oldalon található meg:

    ![](media/service-connect-to-sql-sentry/database2.png)

Az **Adatbázis-azonosító** az adatbázis részleteit megjelenítő képernyőn is megtekinthető:

    ![](media/service-connect-to-sql-sentry/database.png)


## <a name="troubleshooting"></a>Hibaelhárítás
Ha egyes alkalmazások adatai nem jelennek meg a Power BI-ban, ellenőrizze, hogy a megfelelő adatbázis-azonosítót használja-e, és van-e jogosultsága megtekinteni az adatokat. 

Ha nem Ön a <https://cloud.sqlsentry.com> oldallal szinkronizált SQL Sentry-adatbázis tulajdonosa, forduljon a rendszergazdához, és bizonyosodjon meg róla, hogy jogosult megtekinteni a gyűjtött adatokat.

## <a name="next-steps"></a>Következő lépések
[Mi az a Power BI?](power-bi-overview.md)

[Power BI – Adatok lekérése](service-get-data.md)

