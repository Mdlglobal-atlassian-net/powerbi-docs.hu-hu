---
title: Oldalakra osztott jelentések előfizetése a Power BI szolgáltatásban
description: Ebből a cikkből megtudhatja, hogy mire érdemes figyelnie, ha többoldalas jelentésekre iratkozik fel a Power BI szolgáltatásban.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 05/24/2019
ms.openlocfilehash: 472606fcb3b823cdcb722c9d8d6421d0ec652d24
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/12/2019
ms.locfileid: "66839553"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Feliratkozás és mások feliratkoztatása többoldalas jelentésre a Power BI szolgáltatásban 

Most már beállíthat e-mailes előfizetéseket saját maga és mások számára többoldalas jelentésekre a Power BI szolgáltatásban. A folyamat általánosságban ugyanaz, mint [a Power BI szolgáltatás jelentéseire és irányítópultjaira való feliratkozás](service-report-subscribe.md) esetében. Ez a cikk az eltéréseket és a megfontolandó szempontokat ismerteti. 

Feliratkozás beállításakor kiválaszthatja, hogy milyen gyakorisággal szeretné fogadni az e-maileket: naponta, hetente vagy óránként. Napi vagy heti gyakoriság esetén megadhatja a feliratkozás futásának időpontját. Egy napra legfeljebb 24 különböző feliratkozást állíthat be az összes jelentéshez. 

## <a name="considerations-for-paginated-report-subscriptions"></a>Szempontok többoldalas jelentésekre való feliratkozás esetén 

- Az irányítópultokra és Power BI-jelentésekre való feliratkozásokkal ellentétben ez a feliratkozás a teljes jelentés kimenetét tartalmazza mellékletként.  A következő melléklettípusok vannak támogatva: PDF, PowerPoint-bemutató (PPTX), Excel-munkafüzet (XLSX), Word-dokumentum (DOCX), CSV-fájl és XML.

- Az e-mail szövegtörzsében nem található előnézeti kép a jelentésről.  Azt tervezzük, hogy a jelentés első oldalának képe választható elem legyen. 

- A jelentés maximális mellékletméretének értéke 25 MB. 

- Bármely másik felhasználót felírathat bármely jelenleg támogatott adatforráshoz – így például Azure Analysis Services- vagy Power BI-adatkészletekhez – csatlakozó oldalakra osztott jelentésekre. Ne feledje, hogy a jelentésmelléklet az engedélyein alapuló adatokat tükrözi, csakúgy mint az SQL Server Reporting Services jelenleg. 

- A jelentésoldalakra való feliratkozás a jelentés nevéhez kapcsolódik.  

- Az e-mailes feliratkozások a jelentés paramétereinek alapértelmezett értékeit alkalmazva lesznek elküldve. 

- A többoldalas jelentések esetében nincs **Adatfrissítés után** gyakorisági beállítás. Mindig az alapul szolgáló adatforrásból származó legújabb értékeket fogja kapni. 

## <a name="next-steps"></a>Következő lépések

[Feliratkozás és mások feliratkoztatása jelentésekre és irányítópultokra a Power BI szolgáltatásban](service-report-subscribe.md)

[Mik a lapszámozott jelentések a Power BI Premiumban?](paginated-reports-report-builder-power-bi.md)
