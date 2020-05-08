---
title: A OneDrive Vállalati verzió hivatkozásainak használata a Power BI Desktopban
description: A OneDrive Vállalati verzió hivatkozásainak használata a Power BI Desktopban
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 706703985242284725fb4fc2d42bf46e54c605c7
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "76709703"
---
# <a name="use-onedrive-for-business-links-in-power-bi-desktop"></a>A OneDrive Vállalati verzió hivatkozásainak használata a Power BI Desktopban
Sokan tárolnak olyan Excel-munkafüzeteket a OneDrive Vállalati verziójában, amelyeket kiválóan tudnának a Power BI Desktopban használni. A Power BI Desktopban használhat a OneDrive Vállalati verziójában tárolt Excel-fájlokra mutató online hivatkozásokat jelentések és vizualizációk létrehozásához. Ehhez használhat OneDrive Vállalati verzió-csoportfiókot, vagy a saját OneDrive Vállalati verzió-fiókját.

Egy OneDrive Vállalati verzióra mutató online hivatkozás beállításához szükség van néhány konkrét lépésre. Az alábbi szakaszok ismertetik ezeket a lépéseket, amelyek segítségével megoszthatja a fájlhivatkozást különböző csoportokkal, gépekkel és munkatársakkal.

## <a name="get-a-link-from-excel"></a>Hivatkozás kiolvasása az Excelből
1. Lépjen egy böngésző segítségével a OneDrive Vállalati verzió helyére. Kattintson a jobb gombbal a használni kívánt fájlra, majd válassza a **Megnyitás Excelben** lehetőséget.
   
   > [!NOTE]
   > Előfordulhat, hogy a böngészője felülete nem egyezik teljes mértékben az alábbi ábrával. A OneDrive vállalati verzió böngészőfelületén található fájlokhoz több módon is kiválaszthatja a **Megnyitás Excelben** lehetőséget. Bármelyik lehetőség megfelel, amellyel meg tudja nyitni a fájlt Excelben.
   > 
   > 
   
   ![](media/desktop-use-onedrive-business-links/odb-links_02.png)
2. Az Excelben válassza a **Fájl** > **Információk** lehetőséget, majd a **Munkafüzet védelme** feletti **Elérési út másolása** lehetőséget.
   
   ![](media/desktop-use-onedrive-business-links/onedrive-copy-path.png)

## <a name="use-the-link-in-power-bi-desktop"></a>A hivatkozás használata a Power BI Desktopban
A Power BI Desktopban használhatja az imént a vágólapra másolt hivatkozást. Hajtsa végre a következő lépéseket:

1. A Power BI Desktopban válassza az **Adatok beolvasása** > **Web** lehetőséget.
   
   ![](media/desktop-use-onedrive-business-links/power-bi-web-link-onedrive.png)
2. Az **Alapszintű** beállítás kijelölésével illessze be a hivatkozást a **Webről** párbeszéablakba.
3. A hivatkozás végéről távolítsa el a *?web=1* sztringet, hogy a Power BI Desktop megfelelően állapíthassa meg a fájl helyét, majd válassza az **OK** lehetőséget.
   
    ![](media/desktop-use-onedrive-business-links/power-bi-web-link-confirmation.png) 
4. Ha a Power BI Desktop hitelesítő adatokat kér, válassza a **Windows** (helyszíni SharePoint-helyeknél) vagy a **Vállalati fiók**(Office 365- vagy OneDrive Vállalati verzióhoz tartozó helyeknél) lehetőséget.
   
   ![](media/desktop-use-onedrive-business-links/odb-links_06.png)

   Megjelenik egy **Kezelő** párbeszédpanel, ahol választhat az Excelben talált táblák, lapok és tartományok listájáról. Ettől kezdve ugyanúgy használhatja a OneDrive Vállalati verziójában tárolt fájlt, mint bármelyik Excel-fájlt. Létrehozhat jelentéseket, és ugyanúgy felhasználhatja adathalmazokban, mint bármely más adatforrást.

> [!NOTE]
> Ha egy OneDrive Vállalati verzióbeli fájlt úgy szeretne adatforrásnak használni a Power BI szolgáltatásban, hogy a **Szolgáltatásfrissítés** be van kapcsolva, ügyeljen arra, hogy az **OAuth2** **hitelesítési módszert** válassza a frissítési beállítások konfigurálásakor. Ellenkező esetben hiba (például egy *Az adatforrás hitelesítő adatainak frissítése sikertelen volt* üzenet) jelentkezhet a csatlakozás vagy a frissítés során. Ha hitelesítési módszernek az **OAuth2** módszert használja, megszűnik a hitelesítési hiba.
> 
> 

