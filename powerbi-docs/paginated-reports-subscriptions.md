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
ms.date: 07/15/2019
ms.openlocfilehash: 2d48892450bbf6ab09a4bc88cd2be9a58bbdc863
ms.sourcegitcommit: 9d13ef7a257b5006fca5f92acf5b611f5cd143a2
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/18/2019
ms.locfileid: "68307067"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Feliratkozás és mások feliratkoztatása többoldalas jelentésre a Power BI szolgáltatásban 

Most már beállíthat e-mailes előfizetéseket saját maga és mások számára többoldalas jelentésekre a Power BI szolgáltatásban. A folyamat általánosságban ugyanaz, mint [a Power BI szolgáltatás jelentéseire és irányítópultjaira való feliratkozás](service-report-subscribe.md) esetében. Ez a cikk az eltéréseket és a megfontolandó szempontokat ismerteti. 

Feliratkozás beállításakor kiválaszthatja, hogy milyen gyakorisággal szeretné fogadni az e-maileket: naponta, hetente vagy óránként. Napi vagy heti gyakoriság esetén megadhatja a feliratkozás futásának időpontját. Egy napra legfeljebb 24 különböző feliratkozást állíthat be az összes jelentéshez. 

## <a name="considerations-for-paginated-report-subscriptions"></a>Szempontok többoldalas jelentésekre való feliratkozás esetén 

- Az irányítópultokra és Power BI-jelentésekre való feliratkozásokkal ellentétben ez a feliratkozás a teljes jelentés kimenetét tartalmazza mellékletként.  A következő melléklettípusok vannak támogatva: PDF, PowerPoint-bemutató (PPTX), Excel-munkafüzet (XLSX), Word-dokumentum (DOCX), CSV-fájl és XML.

- Az e-mail szövegtörzsében előnézeti képet is elhelyezhet a jelentésről.  Ez nem kötelező, és az előnézet némileg eltérhet a csatolt jelentésdokumentum első oldalától, a kiválasztott mellékletformátumtól függően. 

- A jelentés maximális mellékletméretének értéke 25 MB. 

- Bármely másik felhasználót felírathat bármely jelenleg támogatott adatforráshoz – így például Azure Analysis Services- vagy Power BI-adatkészletekhez – csatlakozó oldalakra osztott jelentésekre. Ne feledje, hogy a jelentésmelléklet az engedélyein alapuló adatokat tükrözi, csakúgy mint az SQL Server Reporting Services jelenleg. 

- Az e-mailes feliratkozásokat az aktuálisan kiválasztott vagy a jelentéshez tartozó alapértelmezett paraméterekkel is elküldheti.  A jelentéshez létrehozott egyes feliratkozásokhoz különböző paraméterértékeket állíthat be. 

- Ha a jelentés szerzője kifejezésalapú paramétereket állított be (például az alapértelmezett érték mindig a mai dátum), a feliratkozás ezt fogja alapértelmezett értékként használni. Módosíthatja más paraméterek értékeit, és beállíthatja az aktuális értékek használatát, de – hacsak nem módosítja kifejezetten ezt az értéket is – a feliratkozás a kifejezésalapú paramétert fogja használni.

- A többoldalas jelentések esetében nincs **Adatfrissítés után** gyakorisági beállítás. Mindig az alapul szolgáló adatforrásból származó legújabb értékeket fogja kapni. 

## <a name="next-steps"></a>Következő lépések

[Feliratkozás és mások feliratkoztatása jelentésekre és irányítópultokra a Power BI szolgáltatásban](service-report-subscribe.md)

[Mik a lapszámozott jelentések a Power BI Premiumban?](paginated-reports-report-builder-power-bi.md)
