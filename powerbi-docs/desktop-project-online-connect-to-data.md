---
title: 'Project Online: kapcsolódás az adatokhoz a Power BI Desktopon keresztül'
description: 'Project Online: kapcsolódás adatokhoz a Power BI Desktoppal'
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/01/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 0f01a6da3bb0d829d396861814f71d33ba69f22f
ms.sourcegitcommit: 6e56d038280efab86521602cbc089b3989dddbd0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/02/2020
ms.locfileid: "80550921"
---
# <a name="connect-to-project-online-data-through-power-bi-desktop"></a>Kapcsolódás Project Online-adatokhoz a Power BI Desktopon keresztül
A Project Online-adatokhoz kapcsolódhat a Power BI Desktopon keresztül.

## <a name="step-1-download-power-bi-desktop"></a>1\. lépés: A Power BI Desktop letöltése
1. [Töltse le a Power BI Desktopot](https://go.microsoft.com/fwlink/?LinkID=521662), majd futtassa a telepítőt, és telepítse a **Power BI Desktopot** a számítógépre.

## <a name="step-2-connect-to-project-online-with-odata"></a>2\. lépés: Kapcsolódás a Project Online-hoz az OData használatával
1. Nyissa meg a **Power BI Desktopot**.
2. Az *üdvözlőképernyőn* válassza az **Adatok lekérése** lehetőséget.
3. Válassza az **OData-csatorna**, majd a **Csatlakozás** lehetőséget.
4. Adja meg az OData-csatorna címét az URL mezőben, majd kattintson az OK gombra.
   
   Ha a Project Web App-hely címe a *https://\<bérlő_neve\>.sharepoint.com/sites/pwa* címhez hasonló, az OData-csatorna számára a *https://\<bérlő_neve\>.sharepoint.com/sites/pwa/\_api/Projectdata* címet adja meg.
   
   Ebben a példában a következőket használjuk:

    `https://contoso.sharepoint.com/sites/pwa/default.aspx`

5. A Power BI Desktop megkéri, hogy jelentkezzen be az Office 365-fiókjával. Válassza a Szervezeti fiók elemet, és adja meg a hitelesítő adatait.
   
   ![](media/desktop-project-online-connect-to-data/image.png)

Az OData-csatornához való csatlakozásra használt fióknak legalább Portfóliómegtekintő hozzáféréssel kell rendelkeznie a Project Web App-webhelyhez. 

Ezután kiválaszthatja, hogy melyik táblákhoz szeretne csatlakozni, és létrehozhat egy lekérdezést.  Szeretne képet kapni az első lépésekről?  A következő blogbejegyzés leírja, hogyan készíthet egy burndown chartot a Project Online-adataiból.  A blogbejegyzésben a Power Query használatával csatlakoznak a Project Online-hoz, de ugyanez alkalmazható a Power BI Desktopra is.

[Projektek burndown chartjainak létrehozása a Power Pivot és a Power Query használatával](https://blogs.office.com/2014/03/24/creating-burndown-charts-for-project-using-power-pivot-and-power-query/)

