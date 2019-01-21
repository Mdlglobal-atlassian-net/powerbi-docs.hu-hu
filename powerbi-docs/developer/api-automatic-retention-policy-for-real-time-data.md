---
title: Valós idejű adatokhoz automatikus adatmegőrzési szabályzatot használó Power BI API-k
description: További információ a Power BI szolgáltatás automatikus adatmegőrzési szabályzatáról
author: markingmyname
manager: kfile
ms.author: maghan
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 9b5923c7bd92b1fe53ebb7ab9416aca8cece3cfa
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54294380"
---
# <a name="automatic-retention-policy-for-real-time-data"></a>Automatikus adatmegőrzési szabályzat valós idejű adatokhoz

A Power BI szolgáltatás automatikus adatmegőrzési szabályzata egy olyan lekérdezésisztring-paraméter, amellyel az alapértelmezett adatmegőrzési szabályzat automatikusan törölheti a régi adatokat, míg az új adatokat folyamatosan hozzáadja az irányítópulthoz. Az első adatmegőrzési szabályzat neve *alapszintű first in first out (FIFO)*. Ha ezt engedélyezte, az adatok egy táblában gyűlnek, amíg el nem érik a 200 000 sort. Amint meghaladják a 200 000 sort, a legrégebbi sor kikerül az adatkészletből. Ez 200 000 és 210 000 sor között tartja a legfrissebb adatok mennyiségét.  
  
<center>

![adatmegőrzési szabályzat](media/api-Automatic-retention-policy-for-real-time-data/retention-policy.png) 

</center>

Az adatmegőrzési szabályzatok az első adatkészletek létrehozásakor válnak elérhetővé. Csak adja hozzá a „defaultRetentionPolicy” lekérdezésparamétert a POST adatkészletek meghívásához, és állítsa a *basicFIFO* értékkel egyenlőre.  
  
    POST https://api.powerbi.com/v1.0/myorg/datasets?defaultRetentionPolicy={None | basicFIFO}