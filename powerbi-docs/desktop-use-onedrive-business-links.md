---
title: OneDrive Vállalati verzióra mutató hivatkozások használata a Power BI Desktopban
description: OneDrive Vállalati verzióra mutató hivatkozások használata a Power BI Desktopban
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 8597904e2753f198b3f99cdcad6062d756b734a0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65513763"
---
# <a name="use-onedrive-for-business-links-in-power-bi-desktop"></a>OneDrive Vállalati verzióra mutató hivatkozások használata a Power BI Desktopban
Sokan tárolnak olyan Excel-munkafüzeteket a OneDrive Vállalati verzió meghajtóján, amelyeket kiválóan tudnának a Power BI Desktopban használni. A **Power BI Desktopban** használhat a **OneDrive Vállalati verziójában** tárolt **Excel**-fájlokra mutató online hivatkozásokat jelentések és vizualizációk létrehozásához. Ehhez használhat **OneDrive Vállalati verzió**-csoportfiókot, vagy a saját **OneDrive Vállalati verzió**-fiókját.

Egy **OneDrive Vállalati verzióra** mutató online hivatkozás beállításához szükség van néhány konkrét lépésre. Az alábbi szakaszok ismertetik ezeket a lépéseket, amelyek segítségével megoszthatja a fájlhivatkozást különböző csoportokkal, gépekkel és munkatársakkal.

## <a name="get-a-link-from-excel-starting-in-the-browser"></a>Hivatkozás lekérése Excelből, a böngészőből kiindulva
1. Lépjen egy böngésző segítségével a OneDrive Vállalati verzió helyére. Kattintson a jobb gombbal a használni kívánt fájlra, majd válassza a **Megnyitás Excelben** lehetőséget.
   
   > [!NOTE]
   > Előfordulhat, hogy a böngészője felülete nem egyezik teljes mértékben az alábbi ábrával. A **OneDrive vállalati verzió** böngészőfelületén található fájlokhoz több módon is kiválaszthatja a **Megnyitás Excelben** lehetőséget. Bármelyik lehetőség megfelel, amellyel meg tudja nyitni a fájlt Excelben.
   > 
   > 
   
   ![](media/desktop-use-onedrive-business-links/odb-links_02.png)
2. Az **Excelben** válassza a **Fájl > Információ** lehetőséget, és jelölje ki a **Füzetvédelem** gomb fölött található hivatkozást. Válassza a **Hivatkozás másolása a vágólapra** lehetőséget (egyes verzióknál **Útvonal másolása a vágólapra** szöveg szerepel).
   
   ![](media/desktop-use-onedrive-business-links/odb-links_03.png)

## <a name="use-the-link-in-power-bi-desktop"></a>A hivatkozás használata a Power BI Desktopban
A Power BI Desktopban használhatja az imént a vágólapra másolt hivatkozást. Hajtsa végre a következő lépéseket:

1. A Power BI Desktopban válassza a **Lekérdezés > Web** lehetőséget.
   
   ![](media/desktop-use-onedrive-business-links/odb-links_04.png)
2. Illessze a hivatkozást a **Webes tartalomból** párbeszédpanelre (még **ne** válassza ki az OK gombot).
   
    ![](media/desktop-use-onedrive-business-links/odb-links_05.png)
3. Keresse meg a hivatkozás végén a *?web=1* karaktersort. A *webes URL-sztring ezen részét el kell távolítania*, **mielőtt** az **OK** gombot kiválasztaná, hogy a **Power BI Desktop** meg tudja találni a fájlt.
4. Ha a **Power BI Desktop** hitelesítő adatokat kér, válassza a **Windows** (helyszíni SharePoint-helyeknél) vagy a **Szervezeti fiók**(Office 365- vagy OneDrive Vállalati verzióhoz tartozó helyeknél) lehetőséget.
   
   ![](media/desktop-use-onedrive-business-links/odb-links_06.png)

Megjelenik egy **Kezelő** ablak, ahol választhat az Excelben talált táblák, lapok és tartományok listájáról. Ezután úgy használhatja a OneDrive vállalati verzióbeli fájlt, mint bármely más Excel-fájlt, és ugyanúgy hozhat létre jelentéseket és használhatja adatkészletekben, mint bármely más adatforrás esetében.

> [!NOTE]
> Ha egy **OneDrive vállalati verzióbeli** fájlt úgy szeretne adatforrásnak használni a Power BI szolgáltatásban, hogy a **Szolgáltatásfrissítés** be van kapcsolva, ügyeljen arra, hogy az **OAuth2** **hitelesítési módszert** válassza a frissítési beállítások konfigurálásakor. Ha nem az van kiválasztva, hiba (például egy *Az adatforrás hitelesítő adatainak frissítése sikertelen volt* üzenet) jelentkezhet a csatlakozás vagy a frissítés során. Ha hitelesítési módszernek az **OAuth2** módszert használja, megszűnik a hitelesítési hiba.
> 
> 

