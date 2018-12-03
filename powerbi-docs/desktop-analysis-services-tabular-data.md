---
title: Az Analysis Services táblázatos adatainak használata a Power BI Desktopban
description: Az Analysis Services táblázatos adatai a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 102198c4524903098ad0c6b0b9fd7e231c3f1fdc
ms.sourcegitcommit: 05303d3e0454f5627eccaa25721b2e0bad2cc781
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52578290"
---
# <a name="using-analysis-services-tabular-data-in-power-bi-desktop"></a>Az Analysis Services táblázatos adatainak használata a Power BI Desktopban
A Power BI Desktopban kétféleképpen érheti el és kérheti le az adatokat az SQL Server Analysis Services táblázatos modelljeiből: élő kapcsolaton keresztüli feltárással vagy az elemek kiválasztásával és a Power BI Desktopba történő importálásával.

Lássuk mindezt közelebbről.

**Feltárás élő kapcsolaton keresztül** – Élő kapcsolat használata esetén a táblázatos modellben vagy perspektívában lévő elemek, például a táblák, oszlopok és mértékek a Power BI Desktop Mezők listájában jelennek meg. A Power BI Desktop fejlett vizualizáció és jelentéskészítő eszközeivel új, interaktív módokon tárhatja fel a táblázatos modellek részleteit.

Élő kapcsolat esetén a táblázatos modell adatait a rendszer nem importálja a Power BI Desktopba. Minden alkalommal, amikor használ egy vizualizációt, a Power BI Desktop lekérdezi a táblázatos modellt, és kiszámítja a megjelenített eredményeket. Mindig a táblázatos modellben elérhető legfrissebb adatokat látja az utolsó feldolgozási időpontból vagy a táblázatos modellben elérhető közvetlen lekérdezési táblákból. 

Vegye figyelembe, hogy a táblázatos modellek rendkívül biztonságosak. A Power BI Desktopban megjelenő elemek a csatlakoztatott táblázatos modellre vonatkozó engedélyektől függnek.

A Power BI Desktopban létrehozott dinamikus jelentéseket másokkal is megoszthatja, ha közzéteszi őket a Power BI-webhelyén. Ha egy olyan Power BI Desktop-fájlt tesz közzé a Power BI-webhelyén, amelyet élő kapcsolat köt egy táblázatos modellhez, a rendszergazdának egy helyszíni adatátjárót kell telepítenie és konfigurálnia. További tudnivalókért lásd a [helyszíni adatátjárókkal](service-gateway-onprem.md) foglalkozó témakört.

**Elemek kiválasztása és importálása a Power BI Desktopba** – Ha ezzel a lehetőséggel kapcsolódik, kiválaszthatja a táblázatos modell vagy perspektíva különféle elemeit, például táblákat, oszlopokat vagy mértékeket, és betöltheti azokat a Power BI Desktop-modellekbe. A Power BI Desktop fejlett lekérdezésszerkesztőjével tovább finomíthatja a lekérdezéseket, a Power BI Desktop modellezési funkcióival pedig tovább modellezheti az adatokat. A Power BI Desktop és a táblázatos modell közt nincs folyamatos élő kapcsolat. Offline is megvizsgálhatja a Power BI Desktop-modell részleteit, de közzé is teheti a modellt a Power BI-webhelyén.

## <a name="to-connect-to-a-tabular-model"></a>Csatlakozás a táblázatos modellekhez
1. A Power BI Desktopban kattintson a **Kezdőlapon** az **Adatok lekérése** gombra.
   
   ![](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata.png)
2. Kattintson az **SQL Server Analysis Services-adatbázis**, majd a **Csatlakozás** elemre.
   
   ![](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as.png)
3. Adja meg a kiszolgáló nevét, és válassza ki a kapcsolati módot. 
   
   ![](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_server.png)
4. Ez a lépés a kiválasztott kapcsolati módtól függ:

* Ha élő módban kapcsolódik, a Kezelőben válasszon ki egy táblázatos modellt vagy perspektívát.
  
  ![](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_live.png)
* Ha az elemek kiválasztását és az adatok lekérését választotta, a Kezelőben válasszon ki egy táblázatos modellt vagy perspektívát. Ezután már csak egyes táblákat és oszlopokat választhat ki a betöltéshez. Az adatok betöltést megelőző további formázásához a Szerkesztés gombra kattintva nyissa meg a Lekérdezésszerkesztőt. Miután végzett, a Betöltés gombra kattintva importálja az adatokat a Power BI Desktopba.

  ![](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_select.png)

## <a name="frequently-asked-questions"></a>Gyakran feltett kérdések
**Kérdés:** Van szükségem helyszíni adatátjáróra?

**Válasz:** Attól függ. Ha a Power BI Desktoppall élő kapcsolaton keresztül kapcsolódik egy táblázatos modellhez, de nem szándékozik tartalmakat közzétenni a Power BI-webhelyén, nincs szüksége átjáróra. Ha azonban közzé szeretne valamit tenni a Power BI-webhelyén, szükség van az adatátjáróra, hogy biztonságos kommunikációt lehessen kialakítani a Power BI szolgáltatás és a helyszíni Analysis Services-kiszolgáló között. Mindenképpen egyeztessen az Analysis Services-kiszolgáló rendszergazdájával, mielőtt telepítené az adatátjárót.

Ha az elemek kiválasztását és az adatok lekérését választja, a táblázatos modell adatait közvetlenül a Power BI Desktop-fájlba importálja, így nincs szükség átjáróra.

**Kérdés:** Mi a különbség aközött, ha a Power BI szolgáltatásból vagy ha a Power BI Desktopból kapcsolódunk élő kapcsolattal a táblázatos modellhez?

**Válasz:** Ha élő kapcsolattal kapcsolódik a Power BI szolgáltatásban lévő webhelyről a cége vagy szervezete helyszíni Analysis Services-adatbázisában egy táblázatos modellhez, a kettő közötti biztonságos kommunikáció kiépítéséhez egy helyszíni adatátjáróra van szükség. Ha a Power BI Desktopból létesít élő kapcsolatot a táblázatos modellel, nincs szükség átjáróra, mivel a Power BI Desktop és a csatlakoztatott Analysis Services-kiszolgáló egyaránt a helyszínen fut a cégen vagy szervezeten belül. Azonban ha közzéteszi a Power BI Desktop-fájlt a Power BI-webhelyén, szükség lesz átjáróra.

**Kérdés:** Ha létrehoztam egy élő kapcsolatot, kapcsolódhatok más adatforrásokhoz ugyanabban a Power BI Desktop-fájlban?

**Válasz:** Nem. Az élő adatok vizsgálata és a más típusú adatforrásokhoz való csatlakozás nem lehetséges ugyanabban a fájlban. Ha már importált adatokat vagy csatlakozott egy eltérő adatforráshoz valamelyik Power BI Desktop-fájlban, az élő vizsgálathoz egy új fájlt kell létrehoznia.

**Kérdés:** Ha létrehoztam egy élő kapcsolatot, szerkeszthetem a modellt vagy a lekérdezést a Power BI Desktopban?

**Válasz:** Jelentésszintű mértékeket létrehozhat a Power BI Desktopban, az összes többi lekérdezési és modellezési funkció azonban le van tiltva az élő adatok vizsgálata esetén.

**Kérdés:** Ha élő kapcsolatot építek ki, az biztonságos lesz?

**Válasz:** Igen. Az Analysis Services-kiszolgálóhoz meglévő Windows-felhasználói hitelesítő adataival csatlakozhat. Élő vizsgálat esetén sem a Power BI szolgáltatásban, sem a Power BI Desktopban nem használhat alapszintű vagy tárolt hitelesítő adatokat.

**Kérdés:** A Kezelőben egy modellt és egy perspektívát is látok. Mi közöttük a különbség?

**Válasz:** A perspektíva a táblázatos modell egy adott nézete. Az egyedi adatelemzési igényektől függően előfordulhat, hogy csak egyes táblákat, oszlopokat vagy mértékeket tartalmaz. A táblázatos modellek minden esetben rendelkeznek legalább egy perspektívával, amely akár a teljes modellt is tartalmazhatja. Ha nem biztos benne, hogy melyiket válassza, forduljon a rendszergazdához.

## <a name="to-change-the-server-name-after-initial-connection"></a>A kiszolgáló nevének módosítása a kezdeti kapcsolódást követően
Miután létrehozott egy élő vizsgálati kapcsolattal rendelkező Power BI Desktop-fájlt, egyes esetekben előfordulhat, hogy a kapcsolatot át szeretné állítani egy másik kiszolgálóra. Ilyen eset lehet, ha a Power BI Desktop-fájl létrehozásakor a fejlesztési kiszolgálóra csatlakozott, a Power BI szolgáltatásban való közzététel előtt azonban át szeretné a kapcsolatot állítani az üzemi kiszolgálóra.

1. Válassza a **Lekérdezések szerkesztése** lehetőséget a menüszalagon.
   
   ![](media/desktop-analysis-services-tabular-data/pbid_sqlas_chname_editquery.png)
2. Adja meg az új kiszolgáló nevét.
   
   ![](media/desktop-analysis-services-tabular-data/pbid_sqlas_chname_dialog.png)
   
   
## <a name="troubleshooting"></a>Hibaelhárítás 
A következő lista tartalmazza az SQL Server Analysis Services (SSAS) vagy Azure Analysis Services szolgáltatáshoz való kapcsolódáskor előforduló összes ismert problémát. 

* **Hiba: A modellséma nem tölthető be** – Ez a hiba általában akkor fordul elő, ha az Analysis Serviceshez csatlakozó felhasználó nem rendelkezik hozzáféréssel az adatbázishoz/modellhez.

