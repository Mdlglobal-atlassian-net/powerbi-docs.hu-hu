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
ms.openlocfilehash: 97745d93de771d4888dd97717a5e8a8d2d6f5c7c
ms.sourcegitcommit: c395fe83d63641e0fbd7c98e51bbab224805bbcc
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74265647"
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
  
## <a name="see-also"></a>További információ

[Az Azure AD szolgáltatáskorlátozásai](https://docs.microsoft.com/azure/active-directory/active-directory-service-limits-restrictions)   
[A Power BI REST API áttekintése](https://docs.microsoft.com/rest/api/power-bi/)