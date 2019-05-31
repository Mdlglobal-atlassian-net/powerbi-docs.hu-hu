---
title: Power BI-adatforrások előfeltételei
description: Power BI-adatforrások előfeltételei
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 5a95607c2328115df7b4485756f40340a8cb7b0f
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65454409"
---
# <a name="power-bi-data-source-prerequisites"></a>Power BI-adatforrások előfeltételei
A Power BI minden adatszolgáltató esetében egy adott szolgáltatóverziót támogat az objektumokon. A Power BI-hoz elérhető adatforrásokkal kapcsolatos további információkért lásd: [Adatforrások](desktop-data-sources.md). A következő táblázat ezeket a követelményeket ismerteti.

| Adatforrás | Szolgáltató | A szolgáltató legalacsonyabb verziója | Minimális adatforrás-verzió | Támogatott adatforrás-objektumok | Letöltési hivatkozás |
| --- | --- | --- | --- | --- | --- |
| SQL Server |ADO.net (a .NET-keretrendszer részeként) |.NET-keretrendszer 3.5 (kizárólag) |SQL Server 2005+ |Táblák/nézetek, skaláris függvények, táblafüggvények |A .NET-keretrendszer 3.5-ös vagy újabb verziójának részeként |
| Access |Microsoft Access adatbázismotor (ACE) |ACE 2010 SP1 |Nincs korlátozás |Táblák/nézetek |[Letöltési hivatkozás](http://go.microsoft.com/fwlink/?linkid=285987&clcid=0x409) |
| Excel (csak .xls fájlok) (lásd: 1. megjegyzés) |Microsoft Access adatbázismotor (ACE) |ACE 2010 SP1 |Nincs korlátozás |Táblák, táblázatok |[Letöltési hivatkozás](http://go.microsoft.com/fwlink/?linkid=285987&clcid=0x409) |
| Oracle (lásd: 2. megjegyzés) |ODP.NET |ODAC 11.2, 5. kiadás (11.2.0.3.20) |9.x+ |Táblák/nézetek |[Letöltési hivatkozás](http://go.microsoft.com/fwlink/?linkid=272376&clcid=0x409) |
| | System.Data.OracleClient (a .NET-keretrendszer részeként) |.NET-keretrendszer 3.5 |9.x+ |Táblák/nézetek |A .NET-keretrendszer 3.5-ös vagy újabb verziójának részeként |
| IBM DB2 |Az IBM ADO.Net-ügyfele (az IBM-adatkiszolgáló illesztőcsomag részeként) |10.1 |9.1+ |Táblák/nézetek |[Letöltési hivatkozás](http://go.microsoft.com/fwlink/?linkid=274911&clcid=0x409) |
| MySQL |Összekötő/hálózat |6.6.5 |5.1 |Táblák/nézetek, skaláris függvények |[Letöltési hivatkozás](http://go.microsoft.com/fwlink/?linkid=278885&clcid=0x409) |
| PostgreSQL |NPGSQL ADO.NET-szolgáltató |2.0.12 |7.4 |Táblák/nézetek |[Letöltési hivatkozás](http://go.microsoft.com/fwlink/?linkid=282716&clcid=0x409) |
| Teradata |.NET-adatszolgáltató a Teradata rendszerhez |14+ |12+ |Táblák/nézetek |[Letöltési hivatkozás](http://go.microsoft.com/fwlink/?linkid=278886&clcid=0x409) |
| SAP Sybase SQL Anywhere |iAnywhere.Data.SQLAnywhere a .NET 3.5-höz |16+ |16+ |Táblák/nézetek |[Letöltési hivatkozás](http://go.microsoft.com/fwlink/?linkid=324846) |

>[!NOTE]
>Az .xlsx kiterjesztésű Excel-fájlokhoz nem szükséges külön szolgáltatót telepíteni.

>[!NOTE]
>Az Oracle-szolgáltatókhoz Oracle-ügyfélszoftver (legalább 8.1.7-es verzió) is szükséges.
> 
> 

