---
title: 'Oktatóanyag: A Power BI Elemzés az Excelben funkciójának használata az Excelből'
description: Ebben az oktatóanyagban az Excelből kiindulva csatlakozhat a Power BI Adathalmazok lapjához, hogy adathalmazokat importáljon az Excelbe.
author: tejaskulkarni
ms.reviewer: davidiseminger
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 02/13/2020
ms.author: tekulka
LocalizationGroup: Connect to services
ms.openlocfilehash: 9a8dd1eb7aa6b239cc542884ab3fae3679997017
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83146393"
---
# <a name="tutorial-use-power-bi-analyze-in-excel-starting-in-excel"></a>Oktatóanyag: A Power BI Elemzés az Excelben funkciójának használata az Excelből

Az Ön szervezete a Power BI-t használja az adatokhoz való hozzáférés megosztására. A Power BI Elemzés az Excelben funkcióját az Excelből indítva kimutatásokat és kimutatásdiagramokat hozhat létre az Excelben. Ezek gazdagítják az elemzések környezetét, és csökkentik a lényeges adathalmazok megkereséséhez és importálásához szükséges időt.

A Power BI-adathalmazzal végzett munka megkezdéséhez válassza az Excelben az „Elemzés az Excelben” lehetőséget. A rendszer végigvezeti az adatokat használó kimutatás létrehozásán.  

A szervezet által megosztott további adatkészleteket az adathalmazok lapra való visszatéréssel találja meg.

Ha bármikor probléma merül fel, válassza a **Nem** lehetőséget az alábbi folyamat megfelelő lépésében, és adjon visszajelzést a hivatkozott űrlapon.  

Az oktatóanyag a következőket ismerteti:

> [!div class="checklist"]
> * Töltsön le egy ODC-fájlt a Power BI-adatkészletek lapról.
> * Engedélyezze az Excelből az adatkészlethez való hozzáférést.
> * Az adatkészlet használatának megkezdése kimutatások, diagramok és munkalapok létrehozásához

## <a name="prerequisites"></a>Előfeltételek

Az oktatóanyag elvégzéséhez a következőkre lesz szüksége:

* Power BI-fiók. Ha még nem regisztrált a Power BI-ra, a kezdés előtt [hozzon létre egy ingyenes próbaverziós fiókot](https://app.powerbi.com/signupredirect?pbi_source=web).

* Ellenőrizze, hogy az [Első lépések a Power BI szolgáltatásban](https://docs.microsoft.com/power-bi/service-get-started) oktatóanyagban felsorolt összes lépést el tudja-e végezni.

* Szüksége lesz egy Power BI Premium-adatkészletre és egy Power BI Pro-licencre. Olvassa el [Mi az a Power BI Premium?](https://docs.microsoft.com/power-bi/service-premium-what-is) cikkre, ahol további információt talál.

* Az előfeltételek teljes listája megtalálható az [Elemzés az Excelben](https://docs.microsoft.com/power-bi/service-analyze-in-excel#requirements) című átfogó dokumentumban.

* Aktív [Microsoft Office E5-előfizetés](https://www.microsoft.com/microsoft-365/business/office-365-enterprise-e5-business-software?activetab=pivot%3aoverviewtab)

## <a name="get-started"></a>Első lépések

Kezdje az Excelben. Válassza a megosztott Power BI-adatokat tartalmazó kimutatások létrehozása lehetőséget, és lépjen a Power BI-adatkészletek lapra.

![Adatkészletek lap](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-01.png)

Az Elemzés az Excelben munkafolyamat használata során több kérdés is megjelenik majd, amelyek végigvezetik Önt a folyamaton és jelzik, hogy befejeződtek-e már az egyes lépések. Ha bármely lépésnél problémába ütközik, válassza a **Nem** lehetőséget, és adjon visszajelzést a megfelelő űrlapon.

![A munkafolyamat utasításai](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-02.png)

## <a name="download-and-open-the-odc-file"></a>Az ODC-fájl letöltése és megnyitása

Válassza ki az adatkészletet a megfelelő listából és a társított munkaterületről, majd kattintson az Elemzés az Excelben lehetőségre. Power BI létrehoz egy ODC-fájlt, és letölti a böngészőből a számítógépre.

![Adathalmaz kiválasztása](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-03.png)

Ha a fájlt megnyitja az Excelben, megjelenik egy üres kimutatás és egy mezőlista, benne a Power BI adatkészletből származó táblákkal, mezőkkel és mértékekkel. Ugyanúgy hozhat létre kimutatásokat, diagramokat és elemezheti az adatkészletet, mintha egy helyi adatkészlettel dolgozna az Excelben.

## <a name="enable-data-connections"></a>Adatkapcsolatok engedélyezése

A Power BI-adatok Excelben történő elemzésénél a rendszer rákérdezhet, hogy megbízik-e a kapcsolatban. A rendszergazdák a Power BI felügyeleti portál használatával letilthatják az Elemzés az Excelben funkciót az Analysis Services-adatbázisokban tárolt helyszíni adatbázisok esetében.

![A kapcsolat engedélyezése](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-04.png)

## <a name="install-updates-and-authenticate"></a>Frissítések telepítése és hitelesítés

Az új ODC-fájl első megnyitásakor szükség lehet a Power BI-fiókkal való hitelesítésre is.  Ha problémák merülnek fel, olvassa el a teljes [Elemzés az Excelben](https://docs.microsoft.com/power-bi/service-analyze-in-excel#sign-in-to-power-bi ) dokumentumot további információért, vagy kattintson a Nem gombra a munkafolyamatban.

![A kapcsolat engedélyezése](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-05.png)

## <a name="analyze-away"></a>Elemzés

A többi helyi munkafüzethez hasonlóan az Elemzés az Excelben lehetővé teszi kimutatások, diagramok és adathozzáadások létrehozását, valamint különböző munkalapok létrehozását az adatok megjelenítésével. Az Elemzés az Excelben funkció minden részletszintű adatot elérhetővé tesz minden olyan felhasználó számára, akinek jogosultsága van az adatkészlethez hozzáférni. Ezt a munkafüzetet mentheti, de nem teheti közzé és nem importálhatja vissza a Power BI-ba, és nem oszthatja meg a szervezet más felhasználóival. További információt és más használati eseteket az [Elemzés az Excelben](https://docs.microsoft.com/power-bi/service-analyze-in-excel#analyze-away) webhelyen talál.

## <a name="clean-up-resources"></a>Erőforrások felszabadítása

A Power BI szolgáltatás és az Adatkészletek lap csak az ODC-fájl letöltésére és a munkafolyamaton keresztül történő kattintásra használandó. Ha a fenti lépések bármelyikénél problémát tapasztal, válassza a **Nem** lehetőséget a megfelelő lépésnél, és küldjön visszajelzést a csatolt űrlapon. Az űrlap tartalmaz egy hivatkozást is, amelyen további információt lehet adni a problémával kapcsolatban. Nyissa meg újra az Adatkészletek lapot és próbálja újra, vagy válasszon egy másik adatkészletet.

## <a name="next-steps"></a>Következő lépések

Az alábbi cikkeket is érdekesnek találhatja:

* [Jelentésközi részletezés a Power BI Desktopban](https://docs.microsoft.com/power-bi/desktop-cross-report-drill-through)

* [Szeletelők használata a Power BI Desktopban](https://docs.microsoft.com/power-bi/visuals/power-bi-visualization-slicers)
