---
title: Adatmodell verzióinak kezelése – Power BI
description: Egy OData-szolgáltatás által elérhetővé tett adatmodell
author: rkarlin
ms.author: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 3835aabee88b33ba8b053550e4637cb387bace02
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875966"
---
# <a name="data-model-versioning"></a>Adatmodell verzióinak kezelése

Egy OData-szolgáltatás által elérhetővé tett adatmodell, például a Power BI-adatmodell, az OData-szolgáltatás és annak ügyfelei közötti szerződést definiálja. A szolgáltatások csak a meglévő ügyfelekkel való kompatibilitást megtartva terjeszthetik ki modelljeiket. A kompatibilitástörő változások (például a tulajdonságok eltávolítása vagy meglévő tulajdonságok módosítása) megkövetelik, hogy új szolgáltatásverzió legyen megadva egy másik szolgáltatási gyökér URL-címén az új modellhez.  
  
Az alábbi adatmodell bővítményei biztonságosak, és nem szükséges hozzájuk a szolgáltatások belépési pontjának verziószámozása.  
  
* Nullázható vagy alapértelmezett értékkel rendelkező tulajdonság hozzáadása: ha ez egy meglévő dinamikus tulajdonság nevével rendelkezik, ugyanolyan típusúnak (vagy alaptípusúnak) kell lennie, mint a meglévő dinamikus tulajdonság  
* Navigációs vagy gyűjteményértékű tulajdonság hozzáadása: ha ez egy meglévő navigációs tulajdonság nevével rendelkezik, ugyanolyan típusúnak (vagy alaptípusúnak) kell lennie, mint a meglévő navigációs tulajdonság  
* Új entitástípus hozzáadása a modellhez  
* Új összetett típus hozzáadása a modellhez  
* Új entitáskészlet hozzáadása  
* Új önálló adatbázis hozzáadása  
* Művelet, függvény, műveletimportálás vagy függvényimportálás hozzáadása
* Nullázható műveletparaméter hozzáadása  
* Típusdefiníció vagy enumerálás hozzáadása  
* Jegyzet hozzáadása egy olyan modellelemhez, amelynek nem kötelező az ügyfél által megérthetőnek lennie a szolgáltatással való megfelelő együttműködéshez  
  
Az ügyfeleknek ***AJÁNLOTT*** felkészülni arra, hogy a szolgáltatások növekményes módosításokat végeznek a modellen. Különös figyelmet érdemes szentelni azoknak a tulajdonságoknak és származtatott típusoknak, amelyeket a szolgáltatás még nem definiált.  
  
A szolgáltatásoknak ***NEM AJÁNLOTT*** módosítaniuk az adatmodellt a hitelesített felhasználótól függően. Ha az adatmodell egy felhasználótól vagy felhasználói csoporttól függ, a teljes modell a korlátozott hozzáféréssel rendelkező felhasználók számára látható modellel való összehasonlításakor KÖTELEZŐ minden módosításnak biztonságos módosításnak lennie a szakaszban meghatározottak szerint.  
  
További információ az OData adatmodellszabványairól: [OData 4.0-s verzió, 1. rész: Protokoll és hibajegyzék 02](https://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html).  
  
## <a name="see-also"></a>Lásd még:
[A Power BI REST API áttekintése](https://docs.microsoft.com/rest/api/power-bi/)  