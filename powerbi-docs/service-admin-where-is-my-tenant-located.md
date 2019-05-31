---
title: Hol található a Power BI-bérlőm?
description: Tudja meg, hogy hol található a Power BI-bérlője, és hogy miként történt ennek a helynek a kiválasztása. Ez fontos, hogy ismerje meg, mert hatással lehet a szolgáltatással kapcsolatos interakciókra.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 05/03/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 06b7ba4bfc68358887af28bd2595b442df90d334
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65710509"
---
# <a name="where-is-my-power-bi-tenant-located"></a>Hol található a Power BI-bérlőm?

<iframe width="560" height="315" src="https://www.youtube.com/embed/0fOxaHJPvdM?showinfo=0" frameborder="0" allowfullscreen></iframe>

Tudja meg, hogy hol található a Power BI-bérlője, és hogy miként történt ennek a helynek a kiválasztása. A hely fontos, mert hatással lehet az interakciókat tanulási rendelkezik a szolgáltatással.

## <a name="how-to-determine-where-your-power-bi-tenant-is-located"></a>A Power BI-bérlő helyének meghatározása

A bérlő a régiójának megkereséséhez kövesse az alábbi lépéseket.

1. A Power BI szolgáltatásban a felső menüből válassza ki a Súgó ( **?** ), majd **A Power BI bemutatása** lehetőséget.

1. Nézze meg **Az adatok a következő helyeken vannak tárolva** melletti szöveget. A bérlő a régió. Az érték akkor is a régió, ahol az adatok tárolása, kivéve, ha használ különböző régiókban található dedikált kapacitást a munkaterület.

    ![Adatterület](media/service-admin-where-is-my-tenant-located/power-bi-data-region.png)

## <a name="how-the-data-region-is-selected"></a>Az adatrégió kiválasztásának módja

Az adatrégiót a bérlő létrehozásakor kiválasztott ország határozza meg. A kijelölt érvényes mindkét Office 365-höz és a Power BI-regisztrációhoz, mert ez az információ. Ha új bérlőről van szó, regisztrációkor válassza ki a megfelelő országot a listából.

![Ország kiválasztása](media/service-admin-where-is-my-tenant-located/sign-up-country-selection.png)

A Power BI szerzi országhoz legközelebbi a kiválasztáshoz, amely megadja, hogy a bérlőhöz tartozó adatok tárolására.

> [!IMPORTANT]
> A beállítás nem módosítható, a bérlő létrehozása után.

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

