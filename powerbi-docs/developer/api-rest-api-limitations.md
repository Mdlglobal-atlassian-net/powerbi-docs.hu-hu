---
title: A Power BI REST API korlátozásai
description: A Power BI Rest API a következő korlátozásokkal rendelkezik
author: rkarlin
ms.author: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 730123ba86e00e944a543feda77308c545a5b53e
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875926"
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
* Maximum 5 000 000 tárolt sor táblánként, adatmegőrzési szabályzat nélküli adatkészletben  
* 4000 karakter/érték sztringoszlopokhoz, POST-sorműveletekben
  
## <a name="see-also"></a>Lásd még:

[Az Azure AD szolgáltatáskorlátozásai](https://docs.microsoft.com/azure/active-directory/active-directory-service-limits-restrictions)   
[A Power BI REST API áttekintése](https://docs.microsoft.com/rest/api/power-bi/)