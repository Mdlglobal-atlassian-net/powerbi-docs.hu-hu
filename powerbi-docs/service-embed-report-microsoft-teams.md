---
title: Jelentés beágyazása a Microsoft Teams Power BI lapjával
description: A Microsoft Teams Power BI lapjával egyszerűen ágyazhat be interaktív jelentéseket csatornákba és csevegésekbe.
author: LukaszPawlowski-MS
ms.author: lukaszp
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 01/31/2020
ms.openlocfilehash: fb4846a777dda4787e1ed0be7de869367a616ea5
ms.sourcegitcommit: b22a9a43f61ed7fc0ced1924eec71b2534ac63f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/21/2020
ms.locfileid: "77530487"
---
# <a name="embed-report-with-the-power-bi-tab-for-microsoft-teams"></a>Jelentés beágyazása a Microsoft Teams Power BI lapjával

A Microsoft Teams frissített Power BI lapjával egyszerűen ágyazhat be interaktív jelentéseket Microsoft Teams-csatornákba és -csevegésekbe.

A Microsoft Teams Power BI lapjának használatával segíthet munkatársainak a csapat által használt adatok megkeresésében és az adatok megvitatásában a csapat csatornáin.

## <a name="requirements"></a>Követelmények

A **Microsoft Teams Power BI lapjának** működéséhez a következők szükségesek:

- Power BI Pro-licenc, vagy az, hogy a jelentést Power BI-licenccel rendelkező [Power BI Premium-kapacitás (EM vagy P SKU)](service-premium-what-is.md) tartalmazza.
- A Microsoft Teams Power BI lapja.
- A jelentés használatához a felhasználóknak be kell jelentkezniük a Power BI szolgáltatásba, hogy aktiválják a Power BI-licencüket.
- A felhasználóknak rendelkezniük kell a jelentés megtekintéséhez szükséges engedéllyel.

## <a name="embed-your-report"></a>A jelentés beágyazása
Jelentés az alábbi lépésekkel ágyazható be Microsoft Teams-csatornába vagy csevegésbe.

1. Nyissa meg a kívánt csatornát vagy csevegést a Microsoft Teamsben, és válassza a **+** ikont.

    ![Lap felvétele csatornára vagy csevegésbe](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-add.png)

2. Válassza a Power BI lapot.

    ![A Microsoft Teams-lapok listája a Power BI lappal](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab.png)

3. A felkínált lehetőségekkel válasszon ki egy jelentést a Munkaterületről, a Velem megosztva területről vagy egy Power BI-alkalmazásból

    ![A Microsoft Teams Power BI lapjának beállításai](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab-settings.png)

4. A lap neve automatikusan frissül a jelentés nevének megfelelően, de módosítható. 

5. Kattintson a **Mentés** gombra.

## <a name="supported-reports"></a>Támogatott jelentések

A lap az alábbi jelentések beágyazását teszi lehetővé:

- Interaktív és többoldalas jelentések
- Jelentések a Saját munkaterületen, az új munkaterületi felületen és klasszikus munkaterületeken
- Jelentések Power BI-alkalmazásokban


## <a name="grant-access-to-reports"></a>Hozzáférés biztosítása a jelentésekhez

Egy jelentés beágyazása a Microsoft Teamsbe még nem ad automatikusan engedélyt a felhasználóknak arra, hogy megtekinthessék a jelentést – [a megtekintést a Power BI-ban kell engedélyeznie](service-share-dashboards.md). Az egyszerűség kedvéért használhat Office 365-csoportot a csapat számára. 

> [!IMPORTANT]
> Tekintse át kik láthatják a jelentést a Power BI szolgáltatásban, és adjon hozzáférést azoknak, akik még nem szerepelnek a listában.

Azt, hogy a csapat hozzáférjen a beágyazott jelentésekhez úgy is biztosíthatja, hogy egyetlen munkaterületre helyezi azokat a Power BI-ban, majd a csapat Office 365-csoportjának hozzáférést ad a munkaterülethez.

## <a name="known-issues-and-limitations"></a>Ismert problémák és korlátozások

- A Power BI nem ugyanazokat a honosított nyelveket támogatja mint a Microsoft Teams. Emiatt előfordulhat, hogy a beágyazott jelentés nem megfelelően honosított nyelven jelenik meg.
- Power BI-irányítópultok nem ágyazhatók be a Microsoft Teams Power BI lapján.
- Power BI-licenccel vagy a jelentésre vonatkozó engedéllyel nem rendelkező felhasználók „A tartalom nem érhető el” üzenetet kapják.
- Ha Internet Explorer 10-es böngészőt használ, előfordulhat, hogy problémákba ütközik. <!--You can look at the [browsers support for Power BI](consumer/end-user-browsers.md) and for [Office 365](https://products.office.com/office-system-requirements#Browsers-section). -->
- A Microsoft Teams Power BI lapja nem támogatja az [URL-szűrőket](service-url-filters.md).
- Országos felhőkben a Power BI lap nem érhető el. Elérhető lehet egy régebbi verzió, amely nem támogatja az új felületű munkaterületeket vagy a Power BI-alkalmazásokban lévő jelentéseket. 
- A lap mentése után a lap neve már nem módosítható a lap beállításaiban. A módosításhoz használja az átnevezés lehetőséget.

## <a name="next-steps"></a>Következő lépések
- [Irányítópult megosztása munkatársakkal és másokkal](service-share-dashboards.md)  
- [Alkalmazások létrehozása és terjesztése a Power BI-ban](service-create-distribute-apps.md)  
- [Mi a Power BI Premium?](service-premium-what-is.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
