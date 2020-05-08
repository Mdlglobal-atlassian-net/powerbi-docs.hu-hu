---
title: A Power BI REST API korlátozásai
description: A Power BI Rest API a következő korlátozásokkal rendelkezik
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 5f4067e77631f22951844c0d4d64b06e5e2e30cc
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "79079577"
---
# <a name="power-bi-rest-api-limitations"></a>A Power BI REST API korlátozásai  
  
**POST soroknál**
  
* Maximum 75 oszlop
* Maximum 75 tábla
* Maximum 10 000 oszlop POST-sorkérésenként  
* Óránként és adatkészletenként 1 000 000 hozzáadott sor  
* Maximum 5 függőben lévő POST-sorkérés adatkészletenként  
* 120 POST-sorkérés percenként és adatkészletenként
* Ha a tábla legalább 250 000 sort tartalmaz, 120 POST-sorkérés óránként és adatkészletenként
* Maximum 200 000 tárolt sor táblánként, FIFO-adatkészletben
* Legfeljebb 5 000 000 tárolt sor táblánként, adatmegőrzési szabályzat nélküli adathalmazban  
* 4000 karakter/érték sztringoszlopokhoz, POST-sorműveletekben
  
## <a name="see-also"></a>Lásd még

* [Azure AD szolgáltatási korlátozások](https://docs.microsoft.com/azure/active-directory/active-directory-service-limits-restrictions)   
* [A Power BI REST API áttekintése](https://docs.microsoft.com/rest/api/power-bi/)