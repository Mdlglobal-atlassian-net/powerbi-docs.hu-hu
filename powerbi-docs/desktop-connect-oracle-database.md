---
title: Kapcsolódás Oracle-adatbázishoz
description: Az Oracle Power BI Desktophoz csatlakoztatásának lépései és az ahhoz szükséges letöltések
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 826338a5e5524bb54c2ebb2207a3d438a8d428b1
ms.sourcegitcommit: 3c8196be5626a0f037599abb6ccbd294fb1249df
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54899227"
---
# <a name="connect-to-an-oracle-database"></a>Kapcsolódás Oracle-adatbázishoz
Ha egy Oracle-adatbázist a **Power BI Desktophoz** szeretne csatlakoztatni, előbb telepítenie kell a megfelelő Oracle ügyfélszoftvert a Power BI Desktopot futtató számítógépre. Az Oracle ügyfélszoftver szükséges verziója attól függ, hogy a Power BI Desktop melyik verzióját telepítette – a **32 bites** verziót vagy a **64 bites** verziót.

**Támogatott verziók**: Oracle 9 és újabb, Oracle ügyfélszoftver 8.1.7-es és újabb.

## <a name="determining-which-version-of-power-bi-desktop-is-installed"></a>A telepített Power BI Desktop-verzió meghatározása
A telepített Power BI Desktop verziójának meghatározásához válassza a **Fájl > Súgó > Névjegy** elemet, majd tekintse meg a **Verzió:** sort. A következő képen a Power BI Desktop 64 bites verziója van telepítve:

![](media/desktop-connect-oracle-database/connect-oracle-database_1.png)

## <a name="installing-the-oracle-client"></a>Az Oracle ügyfél telepítése
A Power BI Desktop **32 bites** verzióihoz a következő hivatkozással töltse le és telepítse a **32 bites** Oracle ügyfelet:

* [32 bites Oracle Data Access Components (ODAC) az Oracle Developer Tools for Visual Studio (12.1.0.2.4) verzióval](http://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html)

A Power BI Desktop **64 bites** verzióihoz a következő hivatkozással töltse le és telepítse a **64 bites** Oracle ügyfelet:

* [64 bites ODAC 12c 4-es kiadás (12.1.0.2.4) Windows x64 rendszerhez](http://www.oracle.com/technetwork/database/windows/downloads/index-090165.html)

## <a name="connect-to-an-oracle-database"></a>Kapcsolódás Oracle-adatbázishoz
A megfelelő Oracle ügyfélillesztő telepítése után csatlakozhat az Oracle-adatbázisokhoz. A kapcsolat létrehozásához az alábbi lépéseket szükséges elvégezni:

1. Az Adatok lekérése ablakban válassza az **Adatbázis > Oracle-adatbázis** lehetőséget
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_2.png)
2. A megjelenő **Oracle-adatbázis** párbeszédpanelen adja meg a kiszolgáló nevét, és válassza a **Csatlakozás** lehetőséget. Ha biztonsági azonosítóra van szükség, azt a következő formátumban adhatja meg: *Kiszolgálónév/biztonsági azonosító*, ahol az azonosító az adatbázis egyedi neve. Ha a *Kiszolgálónév/biztonsági azonosító* formátum nem működik, használja a *Kiszolgálónév/szolgáltatásnév* formátumot, ahol a szolgáltatásnév a csatlakozáskor használt alias.
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_3.png)
3. Ha natív adatbázis-lekérdezéssel szeretné importálni az adatokat, a lekérdezést az **SQL-utasítás** mezőben adhatja meg. Ez az **Oracle-adatbázis** párbeszédpanel **Speciális beállítások** szakaszának kibontásával érhető el.
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_4.png)
4. Miután az Oracle-adatbázis információit megadta az Oracle-adatbázis párbeszédpanelen (a nem kötelező információkkal, például a biztonsági azonosítóval vagy a natív adatbázis-lekérdezéssel együtt), válassza az **OK** lehetőséget a csatlakoztatáshoz.
5. Ha az Oracle-adatbázis az adatbázis felhasználói hitelesítő adatait igényli, adja meg ezeket a hitelesítő adatokat a párbeszédpanelen, amikor a rendszer kéri.


## <a name="troubleshooting"></a>Hibaelhárítás

Ha a Power BI Desktopot a Microsoft Store-ból töltötte le, előfordulhat, hogy egy Oracle-meghajtóval kapcsolatos hiba miatt nem tud csatlakozni Oracle-adatbázisokhoz. Ha ezzel a problémával találkozik, a visszaadott hibaüzenet „Objektumhivatkozás nincs beállítva” (Object reference not set) lesz. A hiba elhárításához végezze el az alábbi műveletek valamelyikét:

* A Power BI Desktopot inkább a https://powerbi.microsoft.com/desktop helyről töltse le.

* Ha a Microsoft Store-ban elérhető verziót szeretné használni: a helyi számítógépén másolja az oraons.dll fájlt a _12.X.X\client_X_ helyről a _12.X.X\client_X\bin_ helyre. Az X a verzió és a könyvtár száma helyett áll.
