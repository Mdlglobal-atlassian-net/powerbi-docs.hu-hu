---
title: "Adatok optimalizálása a Power BI gyors elemzéseihez"
description: "Adatok optimalizálása a Power BI gyors elemzéseihez. Ha a Power BI nem talál összefüggéseket az adatok között, a következőket teheti"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: mihart
ms.openlocfilehash: 263d85a9db996bd7979c29b9c8919fc63f97b1d0
ms.sourcegitcommit: 54da95f184dd0f7bb59bb0bc8775a1d93129b195
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/08/2017
---
# <a name="optimize-your-data-for-power-bi-quick-insights"></a>Adatok optimalizálása a Power BI gyors elemzéseihez
Szeretne jobb eredményeket elérni a Gyors elemzésekkel?  Ha Ön az adatkészlet tulajdonosa, próbálja meg a következőket:

* Rejtsen el oszlopokat az adatkészletből, vagy szüntesse meg oszlopok elrejtését. A Power BI gyors elemzési szolgáltatása az elrejtett oszlopokban nem hajtja végre a keresést.  Ezért rejtse el az ismétlődő vagy szükségtelen oszlopokat, és szüntesse meg a releváns oszlopok elrejtését.
* Használjon többféle adattípust, például neveket, időpontokat, dátumokat és számokat.
* Kerülje (vagy rejtse el) az ismétlődő információt tartalmazó oszlopokat.  Ez értékes időt vehet el a jelentést hordozó mintázatok feltárásától.  Ilyen lehet például, ha az egyik oszlopban az államok neve szerepel, a másikban pedig az államnevek rövidítése.
* Kapott hibaüzenetet, mely arról tájékoztatja, hogy az adatok statisztikailag nem szignifikánsak?  Ez akkor fordulhat elő, ha a modell nagyon egyszerű, vagy nem tartalmaz túl sok adatot, vagy nem rendelkezik dátum- illetve számoszlopokkal. Elemzések generálásához az adatkészletnek rendelkeznie kell legalább egy dimenzióval és egy kategóriával.

### <a name="next-steps"></a>Következő lépések
[Power BI – gyors elemzések](service-insights.md)

További kérdései vannak? [Felteheti azokat a Power BI-közösségnek](http://community.powerbi.com/)

