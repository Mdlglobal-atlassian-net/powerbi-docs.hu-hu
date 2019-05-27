---
title: A Power BI Desktop beszerzése
description: A Power BI Desktop letöltése és telepítése
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: 5e5d143c21ad726e7cdb8a4bc99903238916bb64
ms.sourcegitcommit: 2116af72f435cd30f1401bb9c7afdcbc76b1c3ce
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65454532"
---
# <a name="get-power-bi-desktop"></a>A Power BI Desktop beszerzése
A **Power BI Desktop** segítségével az adatok megjelenítésére szolgáló speciális lekérdezések, modellek és jelentések állíthatók össze. A **Power BI Desktop** használatával adatmodelleket állíthat össze, jelentéseket hozhat létre és megoszthatja a munkáját a Power BI szolgáltatásba való közzététellel.  A **Power BI Desktop** ingyenesen letölthető.

A **Power BI Desktopot** kétféleképpen szerezheti be. Ezen módszerek leírását megtalálja a következő szakaszokban:

* Közvetlen **letöltés** (egy MSI-csomag letöltésével és telepítésével a számítógépen)
* Telepítés alkalmazásként a **Microsoft Store-ból**

Mindkét módszerrel a **Power BI Desktop** legfrissebb verzióját szerzi be, de néhány különbséget érdemes kiemelni. Ezeket a különbségeket a következő szakaszok ismertetik.

## <a name="download-power-bi-desktop"></a>A Power BI Desktop letöltése
A **Power BI Desktop** legfrissebb verziójának letöltését elvégezheti úgy, hogy kiválasztja a Power BI szolgáltatás jobb felső sarkában lévő letöltés ikont, majd a **Power BI Desktop** lehetőséget.

![](media/desktop-get-the-desktop/getpbid_downloads.png)

Vagy a következő letöltési oldalról is letöltheti a Power BI Desktop legfrissebb verzióját:

* [**A Power BI Desktop letöltése** (32 és 64 bites verzió)](https://powerbi.microsoft.com/desktop).
  
  [![](media/service-admin-power-bi-security/PBI_Security_01.png)](https://powerbi.microsoft.com/desktop)

A választott letöltési módszertől függetlenül a **Power BI Desktop** letöltése után a rendszer a telepítőfájl futtatását kéri:

![](media/desktop-get-the-desktop/getpbid_3.png)

A **Power BI Desktop** alkalmazásként lesz telepítve, amely a számítógépe asztalán fut.

![](media/desktop-get-the-desktop/designer_gsg_install.png)

> [!NOTE]
> Nem támogatott a **Power BI Desktop** letöltött (MSI-) verziójának és **Microsoft Store-ból** elérhető verziójának telepítése ugyanarra a számítógépre (ez más néven a *párhuzamos* telepítés).
> 
> 

## <a name="install-as-an-app-from-the-microsoft-store"></a>Telepítés alkalmazásként a Microsoft Store-ból
A **Power BI Desktopot** a Microsoft Store-ból is beszerezheti a következő hivatkozásra kattintva:

* [A **Power BI Desktop** telepítése a **Microsoft Store-ból**](http://aka.ms/pbidesktopstore)

![](media/desktop-get-the-desktop/getpbid_04.png)

A következő előnyökkel jár, ha a Microsoft Store-ból szerzi be a **Power BI Desktopot**:

* **Automatikus frissítések** – A Windows automatikusan letölti a legfrissebb verziót a háttérben, amint elérhetővé válik, így a verziója mindig naprakész marad.
* **Kisebb letöltések** – A **Microsoft Store** csak azokat az összetevőket tölti le a gépre, amelyek az egyes frissítések során megváltoztak, így frissítéskor kisebb méretű fájlokat kell letölteni.
* **Nincs szükség rendszergazdai jogosultságokra** – ha közvetlenül tölti le és telepíti az MSI-fájlt, a telepítés sikeres elvégzéséhez rendszergazdának kell lennie. Ha a Microsoft Store-ból szerzi be a **Power BI Desktopot**, *nincs* szükség rendszergazdai jogosultságra.
* **Engedélyezett az informatikai bevezetés** – a **Microsoft Store-ból** elérhető verzió könnyebben telepíthető vagy *vezethető be* a cég összes felhasználója számára, és a **Power BI Desktop** elérhetővé tehető a **Microsoft Store Vállalatoknak** segítségével.
* **Nyelv észlelése** – a **Microsoft Store-ból** elérhető verzió tartalmazza az összes támogatott nyelvet, és minden indításkor ellenőrzi, hogy mely nyelveket használják a számítógépen. Ez a **Power BI Desktopban** létrehozott modellek honosítására is hatással van: a beépített dátumhierarchiák például megfelelnek a **Power BI Desktop** által a .pbix fájl létrehozásakor használt nyelvnek.

A **Power BI Desktop** Microsoft Store-ból való telepítésével kapcsolatban megfontolandó szempontok és korlátozások többek között a következők:

* Ha az SAP-összekötőt használja, lehet, hogy a *Windows\System32* mappába kell helyeznie az SAP-illesztő fájljait.
* A **Power BI Desktop** Microsoft Store-ból való telepítésével nem történik meg az MSI-verzióból származó felhasználói beállítások másolása. Elképzelhető, hogy újra kell csatlakoztatni a legutóbbi adatforrásokat, és ismét meg kell adni az adatforrások hitelesítő adatait. 

> [!NOTE]
> Nem támogatott a **Power BI Desktop** letöltött (MSI-) verziójának és **Microsoft Store-ból** elérhető verziójának telepítése ugyanarra a számítógépre (ez más néven a *párhuzamos* telepítés). A **Power BI Desktop** manuális eltávolítására van szükség a **Microsoft Store-ból** való letöltés előtt
> 
> [!NOTE]
> A **Power BI Desktop** Power BI jelentéskészítő kiszolgáló verziója az ebben a cikkben tárgyalt verzióktól eltérő, önálló telepítés. A **Power BI Desktop** jelentéskészítő kiszolgáló verziójáról információt a [Power BI-jelentés létrehozása a Power BI jelentéskészítő kiszolgálóhoz](report-server/quickstart-create-powerbi-report.md) című cikkben talál.
> 
> 

## <a name="using-power-bi-desktop"></a>A Power BI Desktop használata
A **Power BI Desktop** elindításakor megjelenik egy *Üdvözlőképernyő*.

![](media/desktop-get-the-desktop/getpbid_05.png)

Ha most először használja a **Power BI Desktopot** (ha a telepítés nem frissítés), a rendszer a folytatás előtt arra kéri, hogy töltsön ki egy űrlapot, és válaszoljon néhány kérdésre, vagy jelentkezzen be a **Power BI szolgáltatásba**.

Innen megkezdheti adatmodellek vagy jelentések létrehozását, majd megoszthatja azokat másokkal a Power BI szolgáltatásban. A cikk végén lévő **További információ** hivatkozásokra kattintva a **Power BI Desktop** használatának megkezdésében segítséget nyújtó útmutatókat tekinthet meg.

## <a name="minimum-requirements"></a>Minimális követelmények
A következő lista a **Power BI Desktop** futtatásához szükséges minimális követelményeket tartalmazza:

* Windows 7 / Windows Server 2008 R2 vagy újabb
* .NET 4.5
* Internet Explorer 9-es vagy újabb verzió
* **Memória (RAM):** Legalább 1 GB, 1,5 GB vagy több javasolt.
* **Kijelző:** Legalább 1440×900 vagy 1600×900 (16:9) felbontás javasolt. Az alacsonyabb felbontás, például 1024x768 vagy 1280x800 nem javasolt, mert bizonyos vezérlők (például a kezdőképernyő bezárása) csak nagyobb felbontáson jelennek meg.
* **A Windows megjelenítési beállításai:** Ha a megjelenítési beállítások több mint 100%-ra módosítják a szövegek, alkalmazások és más elemek méretét, lehet, hogy nem jelennek meg bizonyos párbeszédpanelek, amelyeket be kell zárni, vagy amelyeken valamilyen műveletet kell végezni a **Power BI Desktop** használatának folytatásához. Ha ezzel a problémával találkozik, ellenőrizze a **megjelenítési beállításokat**. Ehhez lépjen Windows rendszeren a **Gépház > Rendszer > Kijelző** területre, és a csúszkával állítsa vissza a megjelenítési beállításokat 100%-ra.
* **CPU:** 1 GHz-es vagy gyorsabb x86-os vagy x64-es processzor ajánlott.

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások

Mindig igyekszünk a lehető legjobb élményt biztosítani a Power BI Desktop felhasználóinak. Előfordulhat, hogy a Power BI Desktop használata során problémák merülnek fel, ezért ez a szakasz megoldásokat és javaslatokat kínál a különböző esetekre. 

### <a name="issues-when-using-previous-releases-of-power-bi-desktop"></a>Problémák a Power BI Desktop előző kiadásainak használata során

Egyes felhasználók a következő példához hasonló hibával szembesülhetnek, ha a **Power BI Desktop** elavult verzióját használják: 

    "We weren't able to restore the saved database to the model" 

A Power BI Desktop aktuális verziójára történő frissítés általában megoldja ezt a problémát.

### <a name="disabling-notifications"></a>Értesítések letiltása
Azt javasoljuk, hogy frissítsen a Power BI Desktop legújabb verziójára, mert így a legújabb fejlesztéseket élvezheti többek között a funkciók, a teljesítmény és a stabilitás terén. Egyes cégek nem kívánják, hogy a munkatársaik minden új verzióra frissítsenek. Az értesítéseket a beállításjegyzék módosításával kapcsolhatja ki a következő lépésekben:

1. A beállításjegyzék-szerkesztővel nyissa meg a *HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Power BI Desktop* helyet.
2. Hozzon létre új bejegyzést a következő beállításokkal: *REG_DWORD : DisableUpdateNotification*
3. Állítsa az új bejegyzés értékét **1**-re.

A módosítás érvénybe lépéséhez újra kell indítania a számítógépet.

### <a name="power-bi-desktop-loads-with-a-partial-screen"></a>A Power BI Desktop részképernyővel töltődik be

Bizonyos körülmények között, például bizonyos képernyőfelbontási konfigurációk esetén, egyes felhasználók a Power BI Desktop tartalmai mellett nagy, fekete területeket láthatnak. Az elemek megjelenítésére általában inkább a közelmúltban történt operációsrendszer-frissítések hatnak, és nem az, ahogy maga a Power BI Desktop mutatja be őket. Ettől még a nagy, fekete területek nem mutatnak olyan jól, mint a vizualizációk, ezért a probléma megoldásához a következő lépéseket javasoljuk:

1. Nyomja le a Start billentyűt, és a megjelenő keresőmezőbe írja be a *blurry* (homályos) szót.
2. A megjelenő párbeszédablakban válassza az alábbi lehetőséget: *A Windows javítsa ki a homályos alkalmazásokat.*
3. Indítsa újra a Power BI Desktopot.

A további Windows-frissítések megjelenésekor megoldódhat a probléma. 
 

## <a name="next-steps"></a>Következő lépések
A **Power BI Desktop** telepítése után a következő tartalmak segíthetnek a használatának gyors megkezdésében:

* [Mi az a Power BI Desktop?](desktop-what-is-desktop.md)
* [Lekérdezések áttekintése a Power BI Desktopban](desktop-query-overview.md)
* [Adatforrások a Power BI Desktopban](desktop-data-sources.md)
* [Csatlakozás adatokhoz a Power BI Desktopban](desktop-connect-to-data.md)
* [Adatok formázása és kombinálása a Power BI Desktoppal](desktop-shape-and-combine-data.md)
* [Gyakori lekérdezési feladatok a Power BI Desktopban](desktop-common-query-tasks.md)   

