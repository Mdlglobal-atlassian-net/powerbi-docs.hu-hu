---
title: A Power BI jelentéskészítő kiszolgálóhoz optimalizált Power BI Desktop telepítése
description: Tudnivalók a Power BI jelentéskészítő kiszolgálóhoz optimalizált Power BI Desktop telepítéséről
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 09/19/2018
ms.author: maggies
ms.openlocfilehash: 943e81c8c49a4a0707ed41b593093fc27a85a01e
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54295881"
---
# <a name="install-power-bi-desktop-optimized-for-power-bi-report-server"></a>A Power BI jelentéskészítő kiszolgálóhoz optimalizált Power BI Desktop telepítése
Tudnivalók a Power BI jelentéskészítő kiszolgálóhoz optimalizált Power BI Desktop telepítéséről.

Ha a Power BI jelentéskészítő kiszolgálóhoz szeretne Power BI-jelentéseket létrehozni, akkor le kell tölteni és telepíteni a Power BI jelentéskészítő kiszolgálóhoz optimalizált Power BI Desktopot. Ez különbözik a Power BI szolgáltatáshoz használt Power BI Desktop-kiadástól. A Power BI szolgáltatáshoz készült Power BI Desktopban például olyan előzetes funkciók is megtalálhatók, amelyek a kiadásukig nem érhetők el a Power BI jelentéskészítő kiszolgálóban. Ha ezt a verziót használja, akkor a jelentéskészítő kiszolgáló a jelentések és a modell ismert verzióját használhatja. 

A Power BI Desktop és a Power BI jelentéskészítő kiszolgálóhoz optimalizált Power BI Desktop azonban egymás mellett is telepíthető ugyanazon a számítógépen.

## <a name="download-and-install-power-bi-desktop"></a>A Power BI Desktop letöltése és telepítése

Ha ellenőrizné, hogy a Power BI jelentéskészítő kiszolgálóhoz optimalizált Power BI Desktop legújabb verzióját használja-e, akkor a jelentéskészítő kiszolgáló webportáljáról induljon.

1. A jelentéskészítő kiszolgáló webportálján kattintson a **Letöltés** nyíl > **Power BI Desktop** lehetőségre.

    ![A Power BI Desktop letöltése a webportálról](media/install-powerbi-desktop/report-server-download-web-portal.png)

    Vagy másik lehetőségként a Microsoft letöltőközpontban válassza közvetlenül a Power BI jelentéskészítő kiszolgálóra (2018. augusztus) optimalizált [Microsoft Power BI Desktop](https://www.microsoft.com/download/details.aspx?id=57271) hivatkozást.

2. A letöltőközpontlapon kattintson a **Letöltés** gombra.

3. A számítógépétől függően válassza az alábbiak egyikét: 

    - **PBIDesktopRS.msi** (32 bites verzió) vagy

    - **PBIDesktopRS_x64.msi** (64 bites verzió).

1. A telepítő letöltése után indítsa el a Power BI Desktop (2018. augusztus) telepítővarázslóját.

2. A telepítés végén kattintson a **Power BI Desktop azonnali indítása** lehetőségre.
   
    A folyamat automatikusan elindul, és máris hozzákezdhet.

## <a name="verify-you-are-using-the-correct-version"></a>Annak ellenőrzése, hogy a megfelelő verziót használja-e
Ellenőrizheti, hogy a Power BI Desktop megfelelő verzióját használja-e a Power BI Desktop indítóképernyőjének vagy címsorának megtekintésével. A címsor a kiadás hónapját és évét jelzi.

![A Power BI jelentéskészítő kiszolgálóhoz optimalizált Power BI Desktop címsora](media/install-powerbi-desktop/power-bi-report-server-desktop-august-2018.png)

A Power BI szolgáltatás Power BI Desktop verziójának címsorában nem szerepel a hónap és az év.

## <a name="file-extension-association"></a>Fájlkiterjesztés társítása
Ha a Power BI Desktopot és a Power BI jelentéskészítő kiszolgálóhoz optimalizált Power BI Desktopot ugyanarra a gépre telepítette, a Power BI Desktop legutóbbi telepítése rendelkezik a .pbix fájltársítással. Ez azt jelenti, hogy amikor duplán kattint egy pbix-fájlra, az a legutóbb telepített Power BI Desktopot indítja el.

Ha először a Power BI Desktopot telepítette, majd a Power BI jelentéskészítő kiszolgálóhoz optimalizált Power BI Desktopot, az összes pbix-fájl alapértelmezés szerint a Power BI jelentéskészítő kiszolgálóhoz optimalizált Power BI Desktopban nyílik meg. Ha azt szeretné, hogy inkább a Power BI Desktop induljon el alapértelmezés szerint a pbix-fájlok megnyitásakor, telepítse újra a Power BI Desktopot a Power BI szolgáltatásból.

Azt is megteheti, hogy először megnyitja a Power BI Desktop használni kívánt verzióját, majd megnyitja a fájlt a Power BI Desktopból.

Ha egy Power BI-jelentést szerkeszt a Power BI jelentéskészítő kiszolgálóból vagy új Power BI-jelentést hoz létre a webes portálról, mindig a Power BI Desktop megfelelő verziója nyílik meg.

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások
A Power BI jelentéskészítő kiszolgálón, a Power BI szolgáltatásban (http://app.powerbi.com)) és a Power BI-mobilalkalmazásokban található jelentések működése szinte teljesen megegyezik, de bizonyos funkciók eltérnek egymástól.

### <a name="in-a-browser"></a>Böngészőben
A Power BI jelentéskészítő kiszolgálón tárolt jelentések minden vizualizációt támogatnak, köztük:

* Egyéni vizualizációk

A Power BI jelentéskészítő kiszolgálón tárolt jelentések nem támogatják az alábbiakat:

* R vizualizációk
* ArcGIS-térképek
* Útkövetési eszközök
* A Power BI Desktop előzetes verziójú funkciói

### <a name="in-the-power-bi-mobile-apps"></a>A Power BI-mobilalkalmazásokban
A Power BI jelentéskészítő kiszolgálón tárolt jelentések a [Power BI-mobilalkalmazások](../consumer/mobile/mobile-apps-for-mobile-devices.md) minden alapvető funkcióját támogatják, köztük:

* [A jelentés telefonos elrendezése](../desktop-create-phone-report.md): A jelentést optimalizálhatja a Power BI-mobilalkalmazásokra. Az optimalizált jelentéseknek különleges ikonjuk ![Jelentés telefonos elrendezésének ikonja](media/install-powerbi-desktop/power-bi-rs-mobile-optimized-icon.png) és elrendezésük van a mobiltelefonon.
  
    ![Mobiltelefonokra optimalizált jelentés](media/install-powerbi-desktop/power-bi-rs-mobile-optimized-report.png)

A Power BI jelentéskészítő kiszolgálón tárolt jelentések nem támogatják a Power BI-mobilalkalmazások alábbi funkcióit:

* R vizualizációk
* ArcGIS-térképek
* Egyéni vizualizációk
* Útkövetési eszközök
* Geofiltering vagy vonalkódok

## <a name="power-bi-desktop-for-earlier-versions-of-power-bi-report-server"></a>Power BI Desktop a Power BI jelentéskészítő kiszolgáló korábbi verzióihoz

Ha a jelentéskészítő kiszolgálója korábbi verziójú, akkor a Power BI Desktop vonatkozó verzióját kell használnia. A két korábbi verzió a következő:

- [A Power BI jelentéskészítő kiszolgálóra (2017. október) optimalizált Microsoft Power BI Desktop](https://www.microsoft.com/download/details.aspx?id=56136)
- [A Power BI jelentéskészítő kiszolgálóra (2017. június) optimalizált Microsoft Power BI Desktop](https://www.microsoft.com/download/details.aspx?id=55330)

## <a name="next-steps"></a>Következő lépések
Most, hogy telepítette a Power BI Desktopot, megkezdheti Power BI-jelentések létrehozását.

[Power BI-jelentés létrehozása a Power BI jelentéskészítő kiszolgálóhoz](quickstart-create-powerbi-report.md)  
[Mi a Power BI jelentéskészítő kiszolgáló?](get-started.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

