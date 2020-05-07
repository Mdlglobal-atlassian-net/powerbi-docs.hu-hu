---
title: Dátumtáblázatok beállítása és használata a Power BI Desktopban
description: Megtudhatja, hogyan állíthat be táblázatot dátumtáblázatként, és hogy ez mit jelent a Power BI Desktopban
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: b2a7f4434ac82a125352eaefdd2417d9039b710f
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "73868605"
---
# <a name="set-and-use-date-tables-in-power-bi-desktop"></a>Dátumtáblázatok beállítása és használata a Power BI Desktopban

A **Power BI Desktop** a háttérben automatikusan azonosítja a dátumokra vonatkozó oszlopokat, majd dátumhierarchiákat és más metaadatokat hoz létre a modellez. Az így elkészült beépített hierarchiákat a jelentések különféle funkcióinál használhatja, például ha vizualizációkat, táblázatokat, gyorsmérőket, szeletelőket vagy más elemeket hoz létre. A Power BI Desktop ezt rejtett táblázatok létrehozásával végzi el, amelyeket később a jelentésekhez és DAX-kifejezésekhez használhat fel.

További információt erről az automatikus viselkedésről az [automatikus dátum/idő a Power BI Desktopban történő használatát](desktop-auto-date-time.md) ismertető cikkben talál.

Vannak adatelemzők, akik inkább saját maguk szeretik létrehozni a táblákat, és ennek sincs akadálya. A **Power BI Desktop** lehetővé teszi, hogy Ön hozza létre a táblát, amelyet a modell **dátumtáblázatként** használ majd fel, és ezt követően ennek a táblának az adatait használva hozhat létre dátummal kapcsolatos vizualizációkat, táblázatokat, gyorsmérőket vagy más elemeket. Ha saját dátumtáblázatot hoz létre, Ön határozhatja meg a dátumhierarchiákat a modell számára, és ezeket használhatja a **gyorsmérőkhöz** és más olyan műveletekhez, amelyek a modell dátumtáblázatát használják. 

![](media/desktop-date-tables/date-tables_01.png)

## <a name="setting-your-own-date-table"></a>Saját dátumtáblázat beállítása

**Dátumtáblázat** beállításához a **Mezők** panelen válassza ki a dátumtáblázatként használni kívánt táblázatot, majd kattintson jobb gombbal a táblára, és a megjelenő menüben válassza a **Megjelölés dátumtáblázatként > Megjelölés dátumtáblázatként** lehetőséget, ahogy az alábbi képen látható.

![](media/desktop-date-tables/date-tables_02.png)

Másik lehetőségként kiválaszthatja a táblázatot, majd a **Modellezés** menüszalagon válassza a **Megjelölés dátumtáblázatként** lehetőséget, ahogy alább látható.

![](media/desktop-date-tables/date-tables_02b.png)

Ha saját **dátumtáblázatot** hoz létre, a Power BI Desktop ellenőrzi az oszlopokat és adatokat, biztosítva, hogy az adatok:

* egyedi értékeket tartalmaznak
* nem tartalmaznak null értékeket
* összefüggő dátumértékeket (az elejétől a végéig) tartalmaznak
* ha **dátum/idő** típusról van szó, minden érték ugyanazzal az időbélyeggel rendelkezik

Saját dátumtáblázat létrehozása leginkább az alábbi két esetben valószínűsíthető, és mindkét esetben ez a célszerű megoldás:

* Egyrészt amikor hagyományos vagy alapszintű dátumtáblázatot és hierarchiát használ. Ez olyan táblázat az adatok között, amely megfelel a dátumtáblázatok fenti kritériumainak. 

* Másrészt használhat egy olyan táblázatot például az Analysis Servicesből, amely tartalmaz egy *dátumdimenzió* (DimDate) mezőt, amelyet dátumtáblázatként szeretne használni. 

Miután meghatározta a dátumtáblázatot, kiválaszthatja, hogy a táblázatban melyik oszlop tartalmazza a dátumot. A használandó oszlop meghatározásához a **Mezők** panelen válassza ki a táblázatot, majd jobb gombbal kattintson a táblázatra, és válassza a **Megjelölés dátumtáblázatként > Dátumtáblázat beállításai** lehetőséget. Ekkor az alább látható ablak jelenik meg, amelyen a legördülő listából kiválaszthatja a dátumtáblázatként használni kívánt oszlopot.

![](media/desktop-date-tables/date-tables_03.png)

Fontos megjegyezni, hogy ha saját maga hozza létre a dátumtáblázatot, a **Power BI Desktop** nem hozza létre automatikusan a hierarchiákat, ellentétben más esetekkel, amikor azokat automatikusan beépítené a modellbe. Ha később megszünteti a dátumtáblázat kiválasztását (azaz ha már nincs manuálisan beállított dátumtáblája), akkor a Power BI Desktop a táblázatban szereplő dátumoszlopokat használva automatikusan újra létrehozza a beépített dátumtáblázatokat.

Azt is vegye figyelembe, hogy ha dátumtáblázatként jelöl meg egy táblázatot, a Power BI Desktop által automatikusan létrehozott beépített dátumtáblázat törölve lesz, és az ezt használó, korábban létrehozott vizualizációk és DAX-kifejezések nem fognak megfelelően működni. 

## <a name="marking-your-date-table-as-the-appropriate-data-type"></a>Dátumtáblázatok adattípusának helyes beállítása

Ha saját maga hozza létre a **dátumtáblázatot**, fontos, hogy megfelelően beállítsa az adattípusát. Az **Adattípus** beállítást **Dátum/idő** vagy **Dátum** értékre kell állítani. A beállítást az alábbi módon végezheti el:

1. A **Mezők** panelen válassza ki a **dátumtáblázatot** (ha szükséges, ehhez bontsa ki a panelt), majd válassza ki a dátumként használni kívánt oszlopot.
   
    ![](media/desktop-date-tables/date-tables_04.png) 

2. A **Modellezés** fülön válassza a **Dátumtípus:** elemet, majd kattintson a lefelé mutató nyílra az elérhető lehetőségek megjelenítéséhez.

    ![](media/desktop-date-tables/date-tables_05.png)

3. Adja meg az oszlop adattípusát. 


## <a name="next-steps"></a>További lépések

Az alábbi cikkeket is érdekesnek találhatja:

* [Automatikus dátum/idő a Power BI Desktopban](desktop-auto-date-time.md)
* [Adattípusok a Power BI Desktopban](desktop-data-types.md)
