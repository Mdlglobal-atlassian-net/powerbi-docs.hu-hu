---
title: Hol található a Power BI-bérlőm?
description: Tudja meg, hogy hol található a Power BI-bérlője, és hogy miként történt ennek a helynek a kiválasztása. Ennek a megértése fontos, mert hatással lehet a szolgáltatással kapcsolatos interakciókra.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 10/31/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: b396b55304e468143fe28fb5ed46ed290bfb3812
ms.sourcegitcommit: 0611860a896e636ceeb6e30ce85243bfd8e7b61d
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/01/2018
ms.locfileid: "50909525"
---
# <a name="where-is-my-power-bi-tenant-located"></a>Hol található a Power BI-bérlőm?

<iframe width="560" height="315" src="https://www.youtube.com/embed/0fOxaHJPvdM?showinfo=0" frameborder="0" allowfullscreen></iframe>

Tudja meg, hogy hol található a Power BI-bérlője, és hogy miként történt ennek a helynek a kiválasztása. Fontos a hely ismerete, mert az befolyásolhatja a szolgáltatással való kommunikációt.

## <a name="how-to-determine-where-your-power-bi-tenant-is-located"></a>A Power BI-bérlő helyének meghatározása

A bérlő a régiójának megkereséséhez kövesse az alábbi lépéseket.

1. A Power BI szolgáltatásban a felső menüből válassza ki a Súgó (**?**), majd **A Power BI bemutatása** lehetőséget.

1. Nézze meg **Az adatok a következő helyeken vannak tárolva** melletti szöveget. A bérlője ezen a területen található.

    ![Adatterület](media/service-admin-where-is-my-tenant-located/power-bi-data-region.png)

## <a name="how-the-data-region-is-selected"></a>Az adatrégió kiválasztásának módja

Az adatrégiót a bérlő létrehozásakor kiválasztott ország határozza meg. Ez a Power BI mellett az Office 365-re való regisztrációra is vonatkozik, mivel ez egy megosztott információ. Ha új bérlőről van szó, regisztrációkor válassza ki a megfelelő országot a listából.

![Ország kiválasztása](media/service-admin-where-is-my-tenant-located/sign-up-country-selection.png)

A Power BI a megjelölt országhoz legközelebbi adatterületet választja ki, amely meghatározza, hogy hol tárolódnak a bérlővel kapcsolatos adatok.

> [!IMPORTANT]
> Ez a beállítás a bérlő létrehozása után már nem módosítható.

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

