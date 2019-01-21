---
title: A Power BI REST API korlátozásai
description: A Power BI Rest API a következő korlátozásokkal rendelkezik
author: markingmyname
manager: kfile
ms.author: maghan
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: df17563d384359fe33123ed87743754bb33bf04d
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54277974"
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