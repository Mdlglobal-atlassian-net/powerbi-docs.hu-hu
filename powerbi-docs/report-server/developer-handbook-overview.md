---
title: A fejlesztői kézikönyv áttekintése, Power BI jelentéskészítő kiszolgáló
description: Üdvözöljük a Power BI-, mobil és lapokra tördelt jelentések tárolására és kezelésére szolgáló helyszíni hely, a Power BI jelentéskészítő kiszolgáló fejlesztői kézikönyvében.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/01/2017
ms.author: maghan
ms.openlocfilehash: df77d4b9642a6df511af8af054e3e983c0120f77
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54291625"
---
# <a name="developer-handbook-overview-power-bi-report-server"></a>A fejlesztői kézikönyv áttekintése, Power BI jelentéskészítő kiszolgáló
Üdvözöljük a Power BI-, mobil és lapokra tördelt jelentések tárolására és kezelésére szolgáló helyszíni hely, a Power BI jelentéskészítő kiszolgáló fejlesztői kézikönyvében.

![](media/developer-handbook-overview/admin-handbook.png)

A kézikönyv bemutatja, hogy milyen lehetőségeket kínál a Power BI jelentéskészítő kiszolgáló a fejlesztők számára.

## <a name="embedding"></a>Beágyazás
A Power BI jelentéskészítő kiszolgálón bármely jelentést beágyazhat egy iFrame elembe, ha hozzáfűzi az `?rs:Embed=true` lekérdezési karakterláncot az URL-címe végéhez. Ez a Power BI jelentésekkel és a többi jelentéstípussal is működik.

### <a name="report-viewer-control"></a>Jelentésmegjelenítő vezérlőelem
A több lapra tördelt jelentések esetében a jelentésmegjelenítő vezérlőelem alkalmazása hasznosnak bizonyulhat. Ezáltal ugyanis a vezérlőt elhelyezheti egy .NET-es Windows- vagy webalkalmazásban. További információkért lásd a [Jelentésmegjelenítő vezérlőelem használatának első lépéseit](https://docs.microsoft.com/sql/reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-get-started) ismertető témakört.

## <a name="apis"></a>API-k
A Power BI jelentéskészítő kiszolgáló használatához számos API áll rendelkezésre. Ezek a következők lehetnek.

* [REST API-k](rest-api.md)
* [URL-en keresztüli elérés](https://docs.microsoft.com/sql/reporting-services/url-access-ssrs)
* [WMI-szolgáltató](https://docs.microsoft.com/sql/reporting-services/wmi-provider-library-reference/reporting-services-wmi-provider-library-reference-ssrs)

Továbbá használhatja a nyílt forráskódú [PowerShell segédprogramokat](https://github.com/Microsoft/ReportingServicesTools) is a jelentéskészítő kiszolgáló kezelésére.

> [!NOTE]
> A PowerShell segédprogramok jelenleg nem támogatják a Power BI Desktop-fájlokat (.pbix).
> 
> 

## <a name="custom-extensions"></a>Egyéni bővítmények
A bővítménykódtár a Power BI jelentéskészítő kiszolgáló részét képező osztályok, felületek és értéktípusok halmaza. A kódtár a rendszerfunkciókhoz biztosít hozzáférést, és ez képezi azt az alapkészletet, amelynek segítségével a Microsoft .NET-keretrendszert használó alkalmazásokkal bővíthetőek a Power BI jelentéskészítő kiszolgáló összetevői.

A bővítmények többféle típusát hozhatja létre.

* Adatfeldolgozási bővítmények
* Kézbesítési bővítmények
* Renderelési bővítmények a lapokra tördelt jelentésekhez
* Biztonsági bővítmények

További tudnivalókért lásd: [Bővítménykódtár](https://docs.microsoft.com/sql/reporting-services/extensions/reporting-services-extension-library).

## <a name="next-steps"></a>További lépések
[A Jelentésmegjelenítő vezérlőelem használatának első lépései](https://docs.microsoft.com/sql/reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-get-started)  
[Alkalmazások készítése webszolgáltatás és a .NET-keretrendszer használatával](https://docs.microsoft.com/sql/reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework)  
[URL-en keresztüli elérés](https://docs.microsoft.com/sql/reporting-services/url-access-ssrs)  
[Bővítménykódtár](https://docs.microsoft.com/sql/reporting-services/extensions/reporting-services-extension-library)  
[WMI-szolgáltató](https://docs.microsoft.com/sql/reporting-services/wmi-provider-library-reference/reporting-services-wmi-provider-library-reference-ssrs)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

