---
title: A Power BI jelentéskészítő kiszolgálóhoz optimalizált Power BI Desktop telepítése
description: Tudnivalók a Power BI jelentéskészítő kiszolgálóhoz optimalizált Power BI Desktop telepítéséről
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 02/13/2020
ms.openlocfilehash: 74e2c60bfe0d6d494fc1175fb001b4b4b7eb24fa
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/14/2020
ms.locfileid: "79381123"
---
# <a name="install-power-bi-desktop-optimized-for-power-bi-report-server"></a>A Power BI jelentéskészítő kiszolgálóhoz optimalizált Power BI Desktop telepítése

Ha a Power BI jelentéskészítő kiszolgálóhoz szeretne Power BI-jelentéseket létrehozni, akkor le kell tölteni és telepíteni a Power BI jelentéskészítő kiszolgálóhoz optimalizált Power BI Desktop-verziót. Ez különbözik a Power BI szolgáltatáshoz használt Power BI Desktop-kiadástól. A Power BI szolgáltatáshoz készült Power BI Desktopban például olyan előzetes funkciók is megtalálhatók, amelyek az általános elérhetőség előtt nem érhetők el a Power BI jelentéskészítő kiszolgálóban. Ha ezt a verziót használja, akkor a jelentéskészítő kiszolgáló a jelentések és a modell ismert verzióját használhatja. 

A Power BI Desktop és a Power BI jelentéskészítő kiszolgálóhoz optimalizált Power BI Desktop azonban egymás mellett is telepíthető ugyanazon a számítógépen.

## <a name="download-and-install-power-bi-desktop"></a>A Power BI Desktop letöltése és telepítése

Ha ellenőrizné, hogy a Power BI jelentéskészítő kiszolgálóhoz optimalizált Power BI Desktop legújabb verzióját használja-e, akkor a jelentéskészítő kiszolgáló webportáljáról induljon.

1. A jelentéskészítő kiszolgáló webportálján kattintson a **Letöltés** nyíl > **Power BI Desktop** lehetőségre.

    ![A Power BI Desktop letöltése a webportálról](media/install-powerbi-desktop/report-server-download-web-portal.png)

    Megnyithatja a [Power BI jelentéskészítő kiszolgáló](https://powerbi.microsoft.com/report-server/) kezdőlapját is, ahol kiválaszthatja a **Speciális letöltési beállítások** lehetőséget.

2. A letöltőközpontlapon válassza ki a nyelvet, majd válassza a **Letöltés** gombot.

3. A számítógépétől függően válassza az alábbiak egyikét: 

    - **PBIDesktopRS.msi** (32 bites verzió) vagy
    - **PBIDesktopRS_x64.msi** (64 bites verzió).

1. A telepítő letöltése után indítsa el a Power BI Desktop (2019. szeptember) telepítő varázslóját.

2. A telepítés végén válassza a **Power BI Desktop indítása** lehetőséget.

    A folyamat automatikusan elindul, és máris hozzákezdhet.

## <a name="verify-youre-using-the-correct-version"></a>Annak ellenőrzése, hogy a megfelelő verziót használja-e
Egyszerűen ellenőrizheti, hogy a megfelelő Power BI Desktopot használja-e: A Power BI Desktopban ellenőrizze az indítási képernyőt vagy a címsort. A címsorban látható **Power BI Desktop (2019. szeptember)** feliratból láthatja, hogy a megfelelő verziót töltötte le. Emellett a Power BI logószínei is fordítva jelennek meg: fekete háttéren sárga, és nem sárga háttéren fekete.

![Power BI Desktop 2019. szeptember](media/install-powerbi-desktop/power-bi-report-server-desktop-sept-2019.png)

A Power BI szolgáltatáshoz készült Power BI Desktop-verzió címsorában nem szerepel az év és a hónap.

## <a name="file-extension-association"></a>Fájlkiterjesztés társítása
Ha a Power BI Desktopot és a Power BI jelentéskészítő kiszolgálóhoz optimalizált Power BI Desktopot ugyanarra a gépre telepítette, a Power BI Desktop legutóbbi telepítése rendelkezik a .pbix fájltársítással. Így ha duplán kattint egy .pbix-fájlra, akkor elindul a nemrég telepített Power BI Desktop.

Ha először a Power BI Desktopot telepítette, majd a Power BI jelentéskészítő kiszolgálóhoz optimalizált Power BI Desktopot, az összes pbix-fájl alapértelmezés szerint a Power BI jelentéskészítő kiszolgálóhoz optimalizált Power BI Desktopban nyílik meg. Ha azt szeretné, hogy inkább a Power BI Desktop induljon el alapértelmezés szerint a pbix-fájlok megnyitásakor, telepítse újra a [Power BI Desktopot a Microsoft Store áruházból](https://aka.ms/pbidesktopstore).

Azt is megteheti, hogy először megnyitja a Power BI Desktop használni kívánt verzióját, majd megnyitja a fájlt a Power BI Desktopból.

Ha egy Power BI-jelentést szerkeszt a Power BI jelentéskészítő kiszolgálóból vagy új Power BI-jelentést hoz létre a webes portálról, mindig a Power BI Desktop megfelelő verziója nyílik meg.

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások

A Power BI jelentéskészítő kiszolgálón, a Power BI szolgáltatásban (https://app.powerbi.com) ) és a Power BI-mobilalkalmazásokban található jelentések működése szinte teljesen megegyezik, de bizonyos funkciók eltérnek egymástól.

### <a name="selecting-a-language"></a>Nyelv kiválasztása

A Power BI jelentéskészítő kiszolgálóra optimalizált Power BI Desktop esetében az alkalmazás telepítésekor ki kell választania a nyelvet. Ezt követően nem módosítható a nyelv, de más nyelven is telepíthet egy verziót.

### <a name="report-visuals-in-a-browser"></a>Jelentésvizualizációk böngészőben

A Power BI jelentéskészítő kiszolgálón tárolt jelentések szinte minden vizualizációt, köztük Power BI-vizualizációkat is támogatnak. A Power BI jelentéskészítő kiszolgálón tárolt jelentések nem támogatják az alábbiakat:

* R vizualizációk
* ArcGIS-térképek
* Útkövetési eszközök
* A Power BI Desktop előzetes verziójú funkciói

### <a name="reports-in-the-power-bi-mobile-apps"></a>Jelentések a Power BI-mobilalkalmazásokban

A Power BI jelentéskészítő kiszolgálón tárolt jelentések a [Power BI-mobilalkalmazások](../consumer/mobile/mobile-apps-for-mobile-devices.md) minden alapvető funkcióját támogatják, köztük:

* [A jelentés telefonos elrendezése](../desktop-create-phone-report.md): A jelentést optimalizálhatja a Power BI-mobilalkalmazásokra. Az optimalizált jelentéseknek különleges ikonjuk ![Jelentés telefonos elrendezésének ikonja](media/install-powerbi-desktop/power-bi-rs-mobile-optimized-icon.png) és elrendezésük van a mobiltelefonon.
  
    ![Mobiltelefonokra optimalizált jelentés](media/install-powerbi-desktop/power-bi-rs-mobile-optimized-report.png)

A Power BI jelentéskészítő kiszolgálón tárolt jelentések nem támogatják a Power BI-mobilalkalmazások alábbi funkcióit:

* R vizualizációk
* ArcGIS-térképek
* Power BI-vizualizációk
* Útkövetési eszközök
* Földrajzi hely szerinti szűrés vagy vonalkódok

### <a name="custom-security"></a>Egyéni biztonság

A Power BI Jelentéskészítő kiszolgálóhoz optimalizált Power BI Desktop nem támogatja az egyéni biztonságot. Ha a Power BI Jelentéskészítő kiszolgáló egyéni biztonsági bővítménnyel van konfigurálva, nem menthet Power BI-jelentést a (Power BI Jelentéskészítő kiszolgálóhoz optimalizált) Power BI Desktopból a Power BI Jelentéskészítő kiszolgáló-példányba. Ki kell mentenie a .pbix-jelentésfájlt a Power BI Desktopból, és fel kell töltenie azt a Power BI Jelentéskészítő kiszolgáló portál webhelyén.

## <a name="power-bi-desktop-for-earlier-versions-of-power-bi-report-server"></a>Power BI Desktop a Power BI jelentéskészítő kiszolgáló korábbi verzióihoz

Ha a jelentéskészítő kiszolgálója korábbi verziójú, akkor a Power BI Desktop vonatkozó verzióját kell használnia. Korábbi verziók az alábbi hivatkozással tölthetők le.

- Microsoft Power BI Desktop ([A Power BI jelentéskészítő kiszolgálóra (2019. szeptember) optimalizálva](https://go.microsoft.com/fwlink/?linkid=2103723))

## <a name="next-steps"></a>Következő lépések

Most, hogy telepítette a Power BI Desktopot, megkezdheti Power BI-jelentések létrehozását.

[Power BI-jelentés létrehozása a Power BI jelentéskészítő kiszolgálóhoz](quickstart-create-powerbi-report.md)  
[Mi a Power BI jelentéskészítő kiszolgáló?](get-started.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
