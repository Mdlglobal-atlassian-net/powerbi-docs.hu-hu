---
title: A Power BI Desktop Modell nézete
description: A Power BI Desktop Modell nézete
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/17/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: ea568c061142e66e79351de8a6c0f0603a46f775
ms.sourcegitcommit: 08f65ea314b547b41b51afef6876e56182190266
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/25/2020
ms.locfileid: "76753225"
---
# <a name="work-with-model-view-in-power-bi-desktop"></a>A Power BI Desktop Modell nézetének használata

A *Modell nézet* megjeleníti a modellben szereplő összes táblát, oszlopot és kapcsolatot. Ez a nézet különösen hasznos lehet, ha a modellben összetett kapcsolatrendszer áll fenn sok tábla között.

A meglévő modell nézetének megtekintéséhez válassza az ablak széle közelében található **Modell** ikont. Vigye a kurzort egy kapcsolat vonala fölé a használt oszlopok megjelenítéséhez.

![Modell nézet, Power BI Desktop](media/desktop-relationship-view/model-view-full-screen.png)

Az ábrán a *Stores* táblában van egy *StoreKey* oszlop, amely kapcsolódik a *Sales* táblához, amely szintén tartalmaz egy *StoreKey* oszlopot. A két tábla között *több az egyhez* (\*:1) kapcsolat áll fenn. A vonal közepén látható nyíl mutatja a szűrőkörnyezet folyamatának irányát. A kettős nyíl azt jelenti, hogy a keresztszűrés irányának beállítása *Kétirányú*.

Egy kapcsolatra duplán kattintva megnyithatja azt a **Kapcsolat szerkesztése** párbeszédpanelen. További információk a kapcsolatokról: [Kapcsolatok létrehozása és kezelése a Power BI Desktopban](desktop-create-and-manage-relationships.md).
