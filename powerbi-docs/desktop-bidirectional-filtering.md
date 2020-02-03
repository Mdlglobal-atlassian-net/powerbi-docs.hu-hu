---
title: Kétirányú keresztszűrés a Power BI Desktopban
description: Keresztszűrés engedélyezése a DirectQuery használatával a Power BI Desktopban
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 141dabdce7816d21c49d8c7f98d1438c2fc20e8d
ms.sourcegitcommit: a1409030a1616027b138128695b80f6843258168
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/24/2020
ms.locfileid: "76709866"
---
# <a name="enable-bidirectional-cross-filtering-for-directquery-in-power-bi-desktop"></a>Kétirányú keresztszűrés engedélyezése a DirectQuery használatához a Power BI Desktopban

Ha táblák szűrésével szeretnék létrehozni az adatok megfelelő nézetét, a jelentéskészítők és adatmodellezők nem könnyen határozzák meg, hogy hogyan alkalmazzanak szűrőket egy jelentésre. Korábban a tábla szűrési környezete a kapcsolat egyik oldalára korlátozódott, a másikra nem terjedt ki. Ez a megoldás gyakran követelt összetett DAX-képleteket a kívánt eredmény előállításához.

Kétirányú keresztszűréssel a jelentéskészítők és adatmodellezők már jobban kézben tarthatják a szűrők alkalmazását a kapcsolódó táblákkal végzett munka során. A kétirányú keresztszűrés lehetővé teszi, hogy egy táblák közötti kapcsolat *mindkét* oldalára alkalmazzanak szűrőket. A szűrők úgy alkalmazhatók, hogy a szűrő kontextusát egy másik kapcsolódó táblára propagálják egy táblák közötti kapcsolat másik oldalán.

## <a name="enable-bidirectional-cross-filtering-for-directquery"></a>Kétirányú keresztszűrés engedélyezése DirectQueryhez

A keresztszűrés a **Kapcsolat szerkesztése** párbeszédpanelen engedélyezhető. Ha engedélyezni szeretné a keresztszűrést egy kapcsolathoz, az alábbi beállításokat kell konfigurálnia:

* A **Keresztszűrés iránya** beállítás legyen **Kétirányú**.
* Jelölje be a **Biztonsági szűrők alkalmazása mindkét irányba** beállítást.

  ![Konfigurálja a kétirányú szűrést a Power BI Desktopban.](media/desktop-bidirectional-filtering/bidirectional-filtering_2.png)

> [!NOTE]
> Ha keresztszűrő DAX-képleteket hoz létre a Power BI Desktopban, használja a *UserPrincipalName* értéket. Ez a mező többnyire a felhasználó bejelentkezési nevével (például <em>joe@contoso.com</em>) azonos, a *UserName* értéke helyett. Emiatt szükség lehet egy kapcsolódó táblára, amely a *UserName* vagy az *EmployeeID* mezőt képezi le a *UserPrincipalName* paraméterre.

A kétirányú keresztszűrés működéséről a [Power BI Desktopbeli kétirányú keresztszűrést ismertető tanulmány](https://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx) nyújt további információt és példákat.

