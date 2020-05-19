---
title: Kapcsolódás Oracle-adatbázishoz
description: Az Oracle Power BI Desktophoz csatlakoztatásának lépései és az ahhoz szükséges letöltések
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/05/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f43981121211c900b3cb4506b830ce09da3b5e20
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83295491"
---
# <a name="connect-to-an-oracle-database"></a>Kapcsolódás Oracle-adatbázishoz
Ha egy Oracle-adatbázist a Power BI Desktophoz szeretne csatlakoztatni, előbb telepítenie kell a megfelelő Oracle ügyfélszoftvert a Power BI Desktopot futtató számítógépre. Az Oracle ügyfélszoftver szükséges verziója attól függ, hogy a Power BI Desktop melyik verzióját telepítette: 32 bites vagy 64 bites.

Támogatott Oracle-verziók: 
- Oracle 9-es és újabb verziók
- 8\.1.7-es vagy újabb Oracle-ügyfélszoftver

> [!NOTE]
> Ha a Power BI Desktophoz, a helyszíni adatátjáróhoz vagy a Power BI jelentéskészítő kiszolgálóhoz konfigurál Oracle-adatbázist, vegye figyelembe az [Oracle-kapcsolattípus](https://docs.microsoft.com/sql/reporting-services/report-data/oracle-connection-type-ssrs?view=sql-server-ver15) című cikkben foglaltakat. 


## <a name="determining-which-version-of-power-bi-desktop-is-installed"></a>A telepített Power BI Desktop-verzió meghatározása
A telepített Power BI Desktop verziójának meghatározásához válassza a **Fájl** > **Súgó** > **Névjegy** elemet, majd tekintse meg a **Verzió** sort. A következő képen a Power BI Desktop 64 bites verziója van telepítve:

![A Power BI Desktop verziója](media/desktop-connect-oracle-database/connect-oracle-database_1.png)

## <a name="installing-the-oracle-client"></a>Az Oracle ügyfél telepítése
- A Power BI Desktop 32 bites verzióihoz [töltse le és telepítse a 32 bites Oracle ügyfelet](https://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html).

- A Power BI Desktop 64 bites verzióihoz [töltse le és telepítse a 64 bites Oracle ügyfelet](https://www.oracle.com/database/technologies/odac-downloads.html).

> [!NOTE]
> Az Oracle-ügyfél telepítése során győződjön meg arról, hogy a telepítővarázslóban engedélyezi *Az ODP.NET és/vagy Oracle-szolgáltatók konfigurálása a számítógép szintjén az ASP.NET-hez* beállítást a megfelelő jelölőnégyzettel. Az Oracle-ügyfél varázslójának egyes verzióiban alapértelmezés szerint be van jelölve ez a jelölőnégyzet, más verziókban azonban nem. Ügyeljen arra, hogy be legyen jelölve a jelölőnégyzet, mert a Power BI így tud csatlakozni az Oracle-adatbázishoz.

## <a name="connect-to-an-oracle-database"></a>Kapcsolódás Oracle-adatbázishoz
A megfelelő Oracle ügyfélillesztő telepítése után csatlakozhat Oracle-adatbázisokhoz. A kapcsolat létrehozásához az alábbi lépéseket szükséges elvégezni:

1. A **Kezdőlapon** válassza az **Adatok betöltése** elemet. 

2. A megjelenő **Adatok betöltése** ablakban válassza a **Továbbiak** lehetőséget (ha szükséges), válassza az **Adatbázis** > **Oracle-adatbázis** elemet, majd a **Csatlakozás** lehetőséget.
   
   ![Csatlakozás Oracle-adatbázishoz](media/desktop-connect-oracle-database/connect-oracle-database_2.png)
2. A megjelenő **Oracle-adatbázis** párbeszédpanelen adja meg a **Kiszolgáló** nevét, és válassza az **OK** lehetőséget. Ha biztonsági azonosítóra (SID) van szükség, azt a következő formátumban adhatja meg: *Kiszolgálónév/biztonsági azonosító*, ahol a *biztonsági azonosító* az adatbázis egyedi neve. Ha a *Kiszolgálónév/biztonsági azonosító* formátum nem működik, használja a *Kiszolgálónév/szolgáltatásnév* formátumot, ahol a *szolgáltatásnév* a csatlakozáskor használt alias.


   ![Oracle-kiszolgáló nevének megadása](media/desktop-connect-oracle-database/connect-oracle-database_3.png)

   > [!TIP]
   > Ha ebben a lépésben akadályba ütközik a kapcsolódás, próbálja meg az alábbi formátumot használni a **Kiszolgáló** mezőben: *(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=host_name)(PORT=port_num))(CONNECT_DATA=(SERVICE_NAME=service_name)))*
   
3. Ha natív adatbázis-lekérdezéssel szeretne adatokat importálni, helyezze el a lekérdezést az **SQL-utasítás** mezőben, amely az **Oracle-adatbázis** párbeszédpanel **Speciális beállítások** területének kibontásakor jelenik meg.
   
   ![Speciális beállítások kibontása](media/desktop-connect-oracle-database/connect-oracle-database_4.png)
4. Miután az Oracle-adatbázis információit megadta az **Oracle-adatbázis** párbeszédpanelen (a nem kötelező információkkal, például a biztonsági azonosítóval vagy a natív adatbázis-lekérdezéssel együtt), válassza az **OK** lehetőséget a csatlakoztatáshoz.
5. Ha az Oracle-adatbázis az adatbázis felhasználói hitelesítő adatait igényli, adja meg ezeket a hitelesítő adatokat a párbeszédpanelen, amikor a rendszer kéri.


## <a name="troubleshooting"></a>Hibaelhárítás

Ha a Power BI Desktopot a Microsoft Store-ból töltötte le, előfordulhat, hogy egy Oracle-meghajtóval kapcsolatos hiba miatt nem tud csatlakozni Oracle-adatbázisokhoz. Ha ezzel a problémával találkozik, a visszaadott hibaüzenet a következő lesz: *„Objektumhivatkozás nincs beállítva” (Object reference not set)* . A hiba elhárításához hajtsa végre az alábbi lépések valamelyikét:

* A Microsoft Store helyett a [Letöltőközpontból](https://www.microsoft.com/download/details.aspx?id=58494) töltse le a Power BI Desktopot.

* Ha a Microsoft Store-ban elérhető verziót szeretné használni: a helyi számítógépén másolja az oraons.dll fájlt a _12.X.X\client_X_ helyről a _12.X.X\client_X\bin_ helyre, ahol _X_ verzió- és könyvtárszámokat jelent.

Ha az Oracle-adatbázishoz való csatlakozáskor a Power BI Gatewayben az *Objektumhivatkozás nincs beállítva* hibaüzenet látható, a problémát az [Adatforrás kezelése – Oracle](service-gateway-onprem-manage-oracle.md) című cikkben található útmutatót követve háríthatja el.

A Power BI jelentéskészítő kiszolgáló használatához az [Oracle-kapcsolattípus](https://docs.microsoft.com/sql/reporting-services/report-data/oracle-connection-type-ssrs?view=sql-server-ver15) című cikk nyújt útmutatást.
