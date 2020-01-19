---
title: Kapcsolat nézet a Power BI Desktop szolgáltatásban
description: Kapcsolat nézet a Power BI Desktop szolgáltatásban
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: cd9671b8c38cb2aa1502c3aa00a871d125f819b1
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/09/2020
ms.locfileid: "75760480"
---
# <a name="work-with-relationship-view-in-power-bi-desktop"></a>A Power BI Desktop Kapcsolat nézetének használata
A **Kapcsolat nézet** megjeleníti a modellben szereplő összes táblát, oszlopot és kapcsolatot. Ez különösen hasznos lehet, ha a modellben összetett kapcsolatrendszer áll fenn sok tábla között.

Vizsgáljuk ezt meg.

![](media/desktop-relationship-view/relationshipview_fullscreen.png)

**A.**  Kapcsolat nézet ikonra – rákattintva Kapcsolat nézetben jelenítheti meg a modellt

**B.** Kapcsolat – ha az egérmutatót egy kapcsolat fölé viszi, megjelennek a használt oszlopok. Egy kapcsolatra duplán kattintva megnyithatja azt a **Kapcsolat szerkesztése** párbeszédpanelen. 

A fenti ábrán láthatja, hogy a *Stores* táblán van egy *StoreKey* oszlop, amely kapcsolódik a *Sales* táblához, amelyen szintén van egy *StoreKey* oszlop. Láthatjuk, hogy ez egy *Több az egyhez* (\*:1) kapcsolat, és a vonal közepén található ikon azt jelöli, hogy a Keresztszűrés iránya *Mindkettő*. Az ikonon látható nyíl mutatja a szűrőkörnyezet folyamatának irányát.

További információk a kapcsolatokról: [Kapcsolatok létrehozása és kezelése a Power BI Desktopban](desktop-create-and-manage-relationships.md).

