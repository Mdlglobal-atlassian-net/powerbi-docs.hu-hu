---
title: Valós idejű adatokhoz automatikus adatmegőrzési szabályzatot használó Power BI API-k
description: További információ a Power BI szolgáltatás automatikus adatmegőrzési szabályzatáról
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: cdbf50ee5078eaade7794242b3ed522e043cab22
ms.sourcegitcommit: c395fe83d63641e0fbd7c98e51bbab224805bbcc
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74265849"
---
# <a name="automatic-retention-policy-for-real-time-data"></a>Automatikus adatmegőrzési szabályzat valós idejű adatokhoz

A Power BI szolgáltatás automatikus adatmegőrzési szabályzata egy olyan lekérdezésisztring-paraméter, amellyel az alapértelmezett adatmegőrzési szabályzat automatikusan törölheti a régi adatokat, míg az új adatokat folyamatosan hozzáadja az irányítópulthoz. Az első adatmegőrzési szabályzat neve *first in first out (FIFO)* . Ha ezt engedélyezte, az adatok egy táblában gyűlnek, amíg el nem érik a 200 000 sort. Amint meghaladják a 200 000 sort, a legrégebbi sor kikerül az adatkészletből. Ez 200 000 és 210 000 sor között tartja a legfrissebb adatok mennyiségét.  
  
<center>

![adatmegőrzési szabályzat](media/api-Automatic-retention-policy-for-real-time-data/retention-policy.png) 

</center>

Az adatmegőrzési szabályzatok az első adatkészletek létrehozásakor válnak elérhetővé. Csak adja hozzá az „alapértelmezett megőrzési szabályzat” lekérdezésparamétert a POST adatkészletek meghívásához, és állítsa a *basicFIFO* értékkel egyenlőre.  
  
    POST https://api.powerbi.com/v1.0/myorg/datasets?defaultRetentionPolicy={None | basicFIFO}