---
title: Access- és .XLS-importálási hibák elhárítása a Power BI Desktopban
description: Az Access-adatbázisok és .XLS-táblázatok importálási hibáinak elhárítása a Power BI Desktopban és a Power Queryben
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/21/2019
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 1816fb7926ed378cdb70ce2e0ade08893828ce4c
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "75761956"
---
# <a name="troubleshoot-importing-access-and-excel-xls-files-in-power-bi-desktop"></a>Access- és Excel .xls-fájlok importálási hibáinak elhárítása a Power BI Desktopban

A Power BI Desktopban az Access-adatbázisok és az Excel-munkafüzetek korai verziói (Excel 97–2003 típusú .XLS-fájlok) az *Access adatbázismotort* használják. Három gyakori helyzet van, amely meggátolhatja az Access adatbázismotor megfelelő működését.

## <a name="situation-1-no-access-database-engine-is-installed"></a>1\. helyzet: Nincs telepítve az Access adatbázismotor

Ha a Power BI Desktop hibaüzenete azt jelzi, hogy az Access adatbázismotor nincs telepítve, telepíteni kell a 32 vagy a 64 bites Access adatbázismotort, attól függően, hogy melyik felel meg a Power BI Desktop verziójának. Az Access adatbázismotort a [letöltési oldalról](https://www.microsoft.com/download/details.aspx?id=13255) telepítheti.

>[!NOTE]
>Ha a telepített Access adatbázismotor bitverziója különbözik a Microsoft Office bitverziójától, az Office-alkalmazások nem tudják használni az Access adatbázismotort.

## <a name="situation-2-the-access-database-engine-bit-version-32-bit-or-64-bit-is-different-from-your-power-bi-desktop-bit-version"></a>2\. helyzet: Az Access adatbázismotor bitverziója (32 vagy 64 bites) különbözik a Power BI Desktop bitverziójától

Ez a helyzet gyakran előfordul, ha a Microsoft Office 32 bites verziója van telepítve, de a Power BI Desktop telepített verziója 64 bites, Ennek az ellenkezője is bekövetkezhet, és a bitverziók eltérése mindkét esetben fennáll. Ha Office 365-előfizetést használ, a [3. helyzetben](#situation-3-trouble-using-access-or-xls-files-with-an-office-365-subscription) találhat információt egy másik problémáról és megoldásról. A következő megoldások közül bármelyik orvosolhatja ezt az eltérő bitverzióból eredő hibát:

### <a name="solution-1"></a>1\. megoldás

Módosítsa úgy a Power BI Desktop verzióját, hogy megfeleljen a telepített Microsoft Office bitverziójának. 

1. A Power BI Desktop bitverziójának módosításához távolítsa el a Power BI Desktopot, majd egy olyan verzióját, amely megfelel a telepített Office-nak. 

1. A Power BI Desktop verziójának kiválasztásához válassza a **Speciális letöltési beállítások** lehetőséget a Power BI Desktop letöltési oldalán.
   
   ![A Power BI Desktop letöltési oldalának speciális letöltési lehetőségei](media/desktop-access-database-errors/desktop-access-errors-1.png)
   
1. A megjelenő letöltési oldalon válassza ki a nyelvet, majd kattintson a **Letöltés** gombra. 
 
1. A megjelenő képernyőn jelölje be a PBIDesktop.msi fájl melletti jelölőnégyzetet a 32 bites vagy a PBIDesktop_x64.msi fájl melletti jelölőnégyzetet a 64 bites verzióhoz. 

   A lenti képernyőképen a 64 bites verzió van bejelölve.
   
   ![A Power BI Desktop-letöltés típusának kiválasztása](media/desktop-access-database-errors/desktop-access-errors-2.png)
   
   >[!NOTE]
   >Ha a Power BI Desktop 32 bites verzióját használja, a nagy méretű adatmodellek létrehozásakor kifogyhat a memóriából.

### <a name="solution-2"></a>2\. megoldás

Módosítsa úgy a Microsoft Office bitverzióját, hogy megfeleljen a telepített Power BI Desktop bitverziójának:

1. A Microsoft Office eltávolítása

2. Azt az Office-verziót telepítse, amely megfelel a telepített Power BI Desktopnak.

### <a name="solution-3"></a>3\. megoldás

Ha a hiba akkor fordul elő, amikor .XLS-fájlt (Excel 97–2003 munkafüzetet) próbál megnyitni, az Access adatbázismotor használatának elkerüléséhez nyissa meg az .XLS-fájlt az Excelben, és mentse XLSX-fájlként.

### <a name="solution-4"></a>4\. megoldás

Ha az előző három megoldás nem alkalmazható, telepítheti az Access adatbázismotor mindkét verzióját. Ez a megkerülő megoldás azonban nem javasolt. Bár mindkét verzió telepítésével megoldja az Excelhez készült Power Query és a Power BI Desktop hibáját, ez más hibákat és problémákat okoz azoknál az alkalmazásoknál, amelyek automatikusan (alapértelmezés szerint) az Access adatbázismotor először telepített bitverzióját használják. 

Az Access adatbázismotor mindkét bitverziójának telepítéséhez kövesse az alábbi lépéseket:

1. Telepítse az Access adatbázismotor mindkét bitverzióját a [letöltési oldalról](https://www.microsoft.com/download/details.aspx?id=13255). 

1. Futtassa az Access adatbázismotor minden verzióját a */passive* kapcsolóval. Például:
   
       c:\users\joe\downloads\AccessDatabaseEngine.exe /passive
   
       c:\users\joe\downloads\AccessDatabaseEngine_x64.exe /passive

## <a name="situation-3-trouble-using-access-or-xls-files-with-an-office-365-subscription"></a>3\. helyzet: Probléma az Access- vagy .XLS-fájlok Office 365-előfizetéssel való használatakor

Ha Office 365-előfizetést használ (legyen szó **Office 2013-ról** vagy **Office 2016-ról**), az Access adatbázismotor szolgáltatója olyan virtuális beállításjegyzékbeli helyen van regisztrálva, amely *csak* Microsoft Office-folyamatok számára elérhető. Emiatt az adategyesítési motor (amely a nem Office 365-beli Excel és a Power BI Desktop futtatásáért felelős, és nem Office-folyamat) nem tudja használni az Access adatbázismotor szolgáltatóját.

A helyzet orvoslása érdekében [töltse le és telepítse az Access adatbázismotor azon terjeszthető változatát](https://www.microsoft.com/download/details.aspx?id=13255), amely megfelel a telepített Power BI Desktop bitverziójának. A bitverziókról a cikk korábbi szakaszaiban talál több információt.

## <a name="other-situations-that-can-cause-import-issues"></a>Egyéb helyzetek, amelyek importálási problémákat okozhatnak

Igyekszünk az Access- vagy .XLS-fájlokkal kapcsolatban előforduló lehető legtöbb hibára kitérni. Ha a jelen cikkben nem szereplő hibával találkozik, küldjön el egy rá vonatkozó kérdést a [Power BI ügyfélszolgálatának](https://powerbi.microsoft.com/support/). Rendszeresen vizsgáljuk az olyan hibákat, amelyek több felhasználót is érintenek, és ezeket a cikkeinkben tárgyaljuk.

