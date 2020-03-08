---
title: Többoldalas jelentések adatforrásai a Power BI jelentéskészítő kiszolgálón
description: Ismerje meg azokat az adatforrásokat, amelyekhez csatlakozhatnak a Power BI jelentéskészítő kiszolgáló többoldalas jelentései (.rdl).
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/17/2018
ms.author: maggies
ms.openlocfilehash: 7cb5772e6ccdc1e4036d70f65a3a28210a4f6df1
ms.sourcegitcommit: d55d3089fcb3e78930326975957c9940becf2e76
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/04/2020
ms.locfileid: "78260715"
---
# <a name="paginated-report-data-sources--in-power-bi-report-server"></a>Többoldalas jelentések adatforrásai  a Power BI jelentéskészítő kiszolgálón
A Reporting Services a Power BI jelentéskészítő kiszolgálón található többoldalas jelentései ugyanazokat az adatforrásokat támogatják, mint amelyeket az SQL Server Reporting Services. Itt megtekintheti [a Reporting Services által támogatott adatforrásokat](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs).

## <a name="connect-to-oracle-data-sources-with-useinstalleduiculture"></a>Csatlakozás Oracle-adatforrásokhoz a UseInstalledUICulture tulajdonság használatával

Az Oracle-adatforrásokhoz való csatlakozáskor a Power BI Jelentéskészítő kiszolgáló a .NET keretrendszer Oracle-adatszolgáltatóját (ODP.NET) használja, amely nem veszi figyelembe a natív nyelvi beállításokat.

A jelentéskészítő kiszolgáló alapértelmezés szerint az első ügyfél felhasználói felületének kulturális környezetét használja az ODP.NET betöltéséhez.  Ennek következtében a jelentéskészítő kiszolgáló további Oracle-kapcsolatai a szolgáltatás újraindításáig ebben az kezdeti felhasználói kulturális környezetben lesznek.  Ez a megoldás a felhasználói kulturális környezetek eltérő formázási beállításai miatt problémákhoz vezethet a jelentések megjelenítésében.

Annak érdekében, hogy a Power BI Jelentéskészítő kiszolgálóval jobb élményt nyújtsunk, bevezettünk egy UseInstalledUICulture nevű beállítást. Ha a UseInstalledUICulture igaz értékre van beállítva, a jelentéskészítő kiszolgáló az első ügyfélé helyett mindig a kiszolgáló felhasználói felületi kulturális környezetében tölti be az ODP.NET-et.
Ez a beállítás a februári szolgáltatásverziótól kezdve érhető el a Power BI Jelentéskészítő kiszolgálóban

A funkció engedélyezéséhez módosítsa az ORACLE-bővítmény szakaszát az rsreportserver.config fájlban az alábbiak szerint.
```xml
<Extension Name="ORACLE" Type="Microsoft.ReportingServices.DataExtensions.OracleClientConnectionWrapper,Microsoft.ReportingServices.DataExtensions">
    <Configuration>
        <UseInstalledUICulture>true</UseInstalledUICulture>
    </Configuration>
</Extension>
```

## <a name="next-steps"></a>Következő lépések
Az adatforrás csatlakoztatása után [létrehozhat egy többoldalas jelentést](quickstart-create-paginated-report.md).  


További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
