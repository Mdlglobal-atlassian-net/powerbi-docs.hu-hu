---
title: Fizessen elő a többoldalas jelentéseket a Power BI szolgáltatásban
description: Ebből a cikkből megtudhatja, többoldalas jelentéseket a Power BI szolgáltatásban való előfizetéssel kapcsolatos szem előtt tartani.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 05/24/2019
ms.openlocfilehash: ccec6658808d94728f2a4f14de67c36da0f51def
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222203"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Feliratkozás saját maga és mások többoldalas jelentéseket a Power BI szolgáltatásban 

Most már beállíthat e-mailes feliratkozások többoldalas jelentéseket a Power BI szolgáltatás saját maga és mások. A folyamat általában ugyanaz, mint [feliratkozás jelentésekre és irányítópultokra a Power BI szolgáltatásban](service-report-subscribe.md). Ez a cikk határozza meg a különbségek és szempontok. 

Előfizetések beállításában úgy dönt, milyen gyakran szeretne az e-mailt kapni: napi, heti vagy óránként. Ha úgy dönt, napi vagy heti, kiválaszthatja az idő az előfizetés futtatni szeretné. Az összes beállíthatja a jelentések naponta legfeljebb 24 eltérő előfizetésekben. 

## <a name="considerations-for-paginated-report-subscriptions"></a>Többoldalas jelentés-előfizetések szempontjai 

- Előfizetések irányítópultjának vagy a Power BI-jelentések, ellentétben az előfizetés tartalmazza a jelentés teljes kimenet melléklet.  A következő melléklet típusok támogatottak: PDF-fájlt, PowerPoint-bemutató (PPTX), az Excel-munkafüzet (XLSX), a Word-dokumentum (DOCX), CSV-fájl és XML.

- A jelentés az e-mail törzsének nincs előnézeti kép van.  Azt tervezi, hogy rendelkezik egy választható elem a jelentés első oldalán képe. 

- A jelentés maximális mellékletméretét érték 25 MB. 

- A lapokra tördelt jelentésekhez bármely jelenleg támogatott adatforrások, beleértve az Azure Analysis Services vagy a Power BI-adatkészletek csatlakozó többi felhasználó regisztrálhat egyet. A jelentés melléklet tükrözi az adatokat, az engedélyek alapján, ugyanúgy mint az SQL Server Reporting Services jelenleg szem előtt tartani. 

- A jelentés jelentésoldalakra a jelentés nevére.  

- E-mailes feliratkozások lesznek elküldve a jelentés alapértelmezett paraméterértékeket. 

- Nincs nem **után adatfrissítési** a többoldalas jelentések gyakoriságának beállítása. Mindig a legújabb értékeket le az alapul szolgáló adatforrás. 

## <a name="next-steps"></a>Következő lépések

[Saját maga és mások feliratkozás jelentésekre és irányítópultokra a Power BI szolgáltatásban](service-report-subscribe.md)

[Mik a lapszámozott jelentések a Power BI Premiumban? (előzetes verzió)](paginated-reports-report-builder-power-bi.md)
