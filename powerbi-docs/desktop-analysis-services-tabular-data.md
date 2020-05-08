---
title: Csatlakozás az Analysis Services táblázatos adataihoz a Power BI Desktopban
description: 'A Power BI Desktopban kétféleképpen érheti el és kérheti le az adatokat az SQL Server Analysis Services táblázatos modelljeiből: élő kapcsolaton keresztül vagy az elemek kiválasztásával és a Power BI Desktopba történő importálásával.'
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/28/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: ac15a732f3d388fd5dafa61d33eec1d82022da54
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "77464253"
---
# <a name="connect-to-analysis-services-tabular-data-in-power-bi-desktop"></a>Csatlakozás az Analysis Services táblázatos adataihoz a Power BI Desktopban
A Power BI Desktopban kétféleképpen érheti el és kérheti le az adatokat az SQL Server Analysis Services táblázatos modelljeiből: Élő kapcsolaton keresztüli feltárással vagy az elemek kiválasztásával és a Power BI Desktopba történő importálásával.

Lássuk mindezt közelebbről.

**Feltárás élő kapcsolat használatával**: Élő kapcsolat használata esetén a táblázatos modellben vagy perspektívában lévő elemek, például a táblák, oszlopok és mértékek a Power BI Desktop **Mezők** listájában jelennek meg. A Power BI Desktop fejlett vizualizáció és jelentéskészítő eszközeivel új, interaktív módokon tárhatja fel a táblázatos modellek részleteit.

Élő kapcsolat esetén a táblázatos modell adatait a rendszer nem importálja a Power BI Desktopba. Minden alkalommal, amikor használ egy vizualizációt, a Power BI Desktop lekérdezi a táblázatos modellt, és kiszámítja a megjelenített eredményeket. Mindig a táblázatos modellben elérhető legfrissebb adatokat látja az utolsó feldolgozási időpontból vagy a táblázatos modellben elérhető DirectQuery-táblákból. 

Vegye figyelembe, hogy a táblázatos modellek rendkívül biztonságosak. A Power BI Desktopban megjelenő elemek a csatlakoztatott táblázatos modellre vonatkozó engedélyektől függnek.

A Power BI Desktopban létrehozott dinamikus jelentéseket másokkal is megoszthatja, ha közzéteszi őket a Power BI-webhelyén. Ha egy olyan Power BI Desktop-fájlt tesz közzé a Power BI-webhelyén, amelyet élő kapcsolat köt egy táblázatos modellhez, a rendszergazdának egy helyszíni adatátjárót kell telepítenie és konfigurálnia. További tudnivalókért lásd a [helyszíni adatátjárókkal](service-gateway-onprem.md) foglalkozó témakört.

**Elemek kiválasztása és importálása a Power BI Desktopba**: Ha ezzel a lehetőséggel kapcsolódik, kiválaszthatja a táblázatos modell vagy perspektíva különféle elemeit, például táblákat, oszlopokat vagy mértékeket, és betöltheti azokat a Power BI Desktop-modellekbe. A Power BI Desktop Power Query Editorával alakíthatja tovább, amire szüksége van és a modellezési funkcióit az adatok további modellezéséhez. Mivel nincs élő kapcsolat a Power BI Desktop és a táblázatos modell között, megvizsgálhatja a Power BI Desktop-modell részleteit offline, vagy közzéteheti a Power BI-webhelyén.

## <a name="to-connect-to-a-tabular-model"></a>Csatlakozás táblázatos modellekhez
1. A Power BI Desktop **Kezdőlap** lapján válassza az **Adatok lekérése** > **Továbbiak** > **Adatbázis** lehetőséget.
   
1. Válassza az **SQL Server Analysis Services-adatbázis**, majd a **Csatlakozás** lehetőséget.
   
   ![SQL Server Analysis Services-adatbázis kiválasztása](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as.png)
3. Az **SQL Server Analysis Services-adatbázisban** adja meg a **Kiszolgáló** nevét, válasszon csatlakozási módot, majd kattintson az **OK** gombra.
   
   ![SQL Server Analysis Services-adatbázis ablak](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_server.png)
4. Ez a lépés a **Kezelő** ablakban a kiválasztott kapcsolati módtól függ:

   - Ha élő módban kapcsolódik, válasszon ki egy táblázatos modellt vagy perspektívát.
  
      ![A Kezelő táblázatos modell vagy perspektíva kiválasztása](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_live.png)
   - Ha az elemek kiválasztását és az adatok betöltését választja, válasszon egy táblázatos modellt és perspektívát, majd a betöltéshez egy adott táblát vagy oszlopot. Ha betöltés előtt szeretné formázni az adatokat, válassza a **Lekérdezések szerkesztése** lehetőséget a Power Query Editor megnyitásához. Miután végzett, a **Betöltés** gombra kattintva importálja az adatokat a Power BI Desktopba.

      ![Kezelő-tábla vagy -oszlop kiválasztása a betöltéshez](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_select.png)

## <a name="frequently-asked-questions"></a>Gyakori kérdések
**Kérdés:** Szükségem van helyszíni adatátjáróra?

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

**Válasz:** A perspektíva a táblázatos modell egy adott nézete. Az egyedi adatelemzési igényektől függően előfordulhat, hogy csak egyes táblákat, oszlopokat vagy mértékeket tartalmaz. A táblázatos modellek minden esetben rendelkeznek legalább egy perspektívával, amely akár a teljes modellt is tartalmazhatja. Ha nem biztos benne, hogy melyik perspektívát válassza, forduljon a rendszergazdához.

**Kérdés:** Vannak az Analysis Servicesnek a Power BI viselkedését befolyásoló funkciói?

**Válasz:** Igen. A Táblázatos modell által használt funkcióktól függően a Power BI Desktopbeli felület is megváltozhat. Néhány példa:
* A mértékek megjelenhetnek a modellben a **Mezők** lista elején csoportosítva, és nem a táblázatokban az oszlopok mellett. Ne aggódjon, továbbra is a szokott módon használhatja ezeket, de így könnyebben megtalálhatók.

* Ha a Táblázatos modellben Számítási csoportok vannak definiálva, akkor ezeket csak a modell mértékeivel használhatja, az olyan közvetett mértékekkel viszont nem, amelyeket a vizualizációkhoz felvett numerikus mezőkkel hozott létre. Az is lehetséges, hogy manuálisan lett beállítva a modell **DiscourageImplicitMeasures** jelölője, amelynek ugyanez a hatása. További tudnivalók: [Számítási csoportok az Analysis Servicesben](https://docs.microsoft.com/analysis-services/tabular-models/calculation-groups#benefits).

## <a name="to-change-the-server-name-after-initial-connection"></a>A kiszolgáló nevének módosítása a kezdeti kapcsolódást követően
Miután létrehozott egy élő vizsgálati kapcsolattal rendelkező Power BI Desktop-fájlt, egyes esetekben előfordulhat, hogy a kapcsolatot át szeretné állítani egy másik kiszolgálóra. Ilyen eset lehet, ha a Power BI Desktop-fájl létrehozásakor a fejlesztési kiszolgálóra csatlakozott, a Power BI szolgáltatásban való közzététel előtt azonban át szeretné a kapcsolatot állítani az üzemi kiszolgálóra.

A kiszolgálónév módosítása:

1. Válassza a **Lekérdezések szerkesztése** lehetőséget a **Kezdőlap** lapon.

2. Az **SQL Server Analysis Services-adatbázisban** adja meg az új **Kiszolgáló** nevét, majd kattintson az **OK** gombra.

   
## <a name="troubleshooting"></a>Hibaelhárítás 
A következő lista tartalmazza az SQL Server Analysis Services (SSAS) vagy Azure Analysis Services szolgáltatáshoz való kapcsolódáskor előforduló összes ismert problémát: 

* **Hiba: Nem sikerült betölteni a modellsémát**: Ez a hiba általában akkor fordul elő, ha az Analysis Serviceshez csatlakozó felhasználó nem rendelkezik hozzáféréssel az adatbázishoz/modellhez.

