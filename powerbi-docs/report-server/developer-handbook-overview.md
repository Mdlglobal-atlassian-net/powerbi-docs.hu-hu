---
title: A fejlesztői kézikönyv áttekintése, Power BI jelentéskészítő kiszolgáló
description: Üdvözöljük a Power BI-, mobil és lapokra tördelt jelentések tárolására és kezelésére szolgáló helyszíni hely, a Power BI jelentéskészítő kiszolgáló fejlesztői kézikönyvében.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/01/2017
ms.openlocfilehash: 773533fee8fc4fada0cc33d9a6d2188118135797
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "73859783"
---
# <a name="developer-handbook-overview-power-bi-report-server"></a>A fejlesztői kézikönyv áttekintése, Power BI jelentéskészítő kiszolgáló

Üdvözöljük a Power BI-, mobil és lapokra tördelt jelentések tárolására és kezelésére szolgáló helyszíni hely, a Power BI jelentéskészítő kiszolgáló fejlesztői kézikönyvében.

![Rendszergazdai kézikönyv](media/developer-handbook-overview/admin-handbook.png)

A kézikönyv bemutatja, hogy milyen lehetőségeket kínál a Power BI jelentéskészítő kiszolgáló a fejlesztők számára.

## <a name="embedding"></a>Beágyazás

A Power BI jelentéskészítő kiszolgálón bármely jelentést beágyazhat egy iFrame elembe, ha hozzáfűzi az `?rs:Embed=true` lekérdezési karakterláncot az URL-címe végéhez. Ez módszer a Power BI jelentésekkel és a többi jelentéstípussal is működik.

### <a name="report-viewer-control"></a>Jelentésmegjelenítő vezérlőelem

A több lapra tördelt jelentések esetében a jelentésmegjelenítő vezérlőelem alkalmazása hasznosnak bizonyulhat. Ezzel ugyanis a vezérlőt elhelyezheti egy .NET-es Windows- vagy webalkalmazásban. További információkért lásd a [Jelentésmegjelenítő vezérlőelem használatának első lépéseit](https://docs.microsoft.com/sql/reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-get-started) ismertető témakört.

## <a name="apis"></a>API-k

A Power BI jelentéskészítő kiszolgáló használatához számos API áll rendelkezésre. Ez a módszer a következőket foglalja magában.

* [REST API-k](rest-api.md)
* [URL-en keresztüli elérés](https://docs.microsoft.com/sql/reporting-services/url-access-ssrs)
* [WMI-szolgáltató](https://docs.microsoft.com/sql/reporting-services/wmi-provider-library-reference/reporting-services-wmi-provider-library-reference-ssrs)

Továbbá használhatja a nyílt forráskódú [PowerShell-segédprogramokat](https://github.com/Microsoft/ReportingServicesTools) is a jelentéskészítő kiszolgáló kezelésére.

> [!NOTE]
> A PowerShell-segédprogramok jelenleg nem támogatják a Power BI Desktop-fájlokat (.pbix).

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

Több kérdése van? [Kérdezze meg a Power BI-közösséget](https://community.powerbi.com/)