---
title: Hol található a Power BI-bérlőm?
description: Tudja meg, hogy hol található a Power BI-bérlője, és hogy miként történt ennek a helynek a kiválasztása. Ennek a megértése fontos, mert hatással lehet a szolgáltatással kapcsolatos interakciókra.
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 3f12e6f0b54f85ebd626b2bd35bf1a03d513c17a
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73873329"
---
# <a name="where-is-my-power-bi-tenant-located"></a>Hol található a Power BI-bérlőm?

<iframe width="560" height="315" src="https://www.youtube.com/embed/0fOxaHJPvdM?showinfo=0" frameborder="0" allowfullscreen></iframe>

Tudja meg, hogy hol található a Power BI-bérlője, és hogy miként történt ennek a helynek a kiválasztása. Fontos a hely ismerete, mert az befolyásolhatja a szolgáltatással való kommunikációt.

## <a name="how-to-determine-where-your-power-bi-tenant-is-located"></a>A Power BI-bérlő helyének meghatározása

A bérlő a régiójának megkereséséhez kövesse az alábbi lépéseket.

1. A Power BI szolgáltatásban a felső menüből válassza ki a Súgó ( **?** ), majd **A Power BI bemutatása** lehetőséget.

1. Nézze meg **Az adatok a következő helyeken vannak tárolva** melletti szöveget. A bérlője ezen a területen található. Ez az érték emellett az adatok tárolására szolgáló régió is, kivéve, ha a munkaterületeihez dedikált kapacitásokat használ más régiókban.

    ![Adatterület](media/service-admin-where-is-my-tenant-located/power-bi-data-region.png)

## <a name="how-the-data-region-is-selected"></a>Az adatrégió kiválasztásának módja

Az adatrégiót a bérlő létrehozásakor kiválasztott ország határozza meg. A kijelölés Power BI mellett az Office 365-re való regisztrációra is vonatkozik, mivel ez egy megosztott információ. Ha új bérlőről van szó, regisztrációkor válassza ki a megfelelő országot a listából.

![Ország kiválasztása](media/service-admin-where-is-my-tenant-located/sign-up-country-selection.png)

A Power BI a megjelölt országhoz legközelebbi adatterületet választja ki, amely meghatározza, hogy hol tárolódnak a bérlővel kapcsolatos adatok.

> [!IMPORTANT]
> Ez a beállítás a bérlő létrehozása után már nem módosítható.

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

