---
title: Adatforrások kapcsolati sztringjeinek módosítása a PowerShell-lel
description: Módosíthatja az adatforrások kapcsolati sztringjeit a PowerShell – Power BI jelentéskészítő kiszolgáló API-jaival.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/21/2020
ms.author: maggies
ms.openlocfilehash: 9ca5d47a938210c10903c916c54713b89923e287
ms.sourcegitcommit: 34cca70ba84f37b48407d5d8a45c3f51fb95eb3c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80751543"
---
# <a name="change-data-source-connection-strings-in-power-bi-reports-with-powershell---power-bi-report-server"></a>Módosíthatja az adatforrások kapcsolati sztringjeit a Power BI-jelentésekben a PowerShell – Power BI jelentéskészítő kiszolgáló API-jaival


A PowerShell API-jaival módosíthatja az adatforrások kapcsolati sztringjeit a Power BI-jelentésekben a Power BI jelentéskészítő kiszolgálón. 

> [!NOTE]
> Ez a funkció jelenleg csak a DirectQuery esetében működik. Az importálás és az adatfrissítés támogatása hamarosan elérhető lesz.

1. Telepítse a Power BI jelentéskészítő kiszolgáló PowerShell-parancsmagjait. A parancsmagokat és a telepítési útmutatót itt találja: [https://github.com/Microsoft/ReportingServicesTools](https://github.com/Microsoft/ReportingServicesTools). 

2. Olvassa be a Power BI-fájlhoz tartozó meglévő adatforrásadatokat a PowerShell-parancsmagokkal:

    ```powershell
    Get-RsRestItemDataSource -RsItem '/MyPbixReport'
    ```

    A Power BI-jelentésben szereplő első adatforrás adatainak megtekintése: 

    ```powershell
    $dataSources[0]
    ```

3. Szükség szerint frissítse a kapcsolati és a hitelesítő adatokat. Ha a kapcsolati sztring és az adatforrás frissítése hitelesítő adatokat alkalmaz, meg kell adnia a fiók jelszavát. 

    Egy adatforrás kapcsolati sztringjének frissítése:

    ```powershell
    $dataSources[0].ConnectionString = 'data source=myCatalogServer;initial catalog=ReportServer;persist security info=False' 
    ```

    Az adatforrás hitelesítőadat-típusának módosítása:

    ```powershell
    $dataSources[0].DataModelDataSource.AuthType = 'Integrated'
    ```

    Az adatforrás felhasználónevének vagy jelszavának módosítása:

    ```powershell
    $dataSources[0].DataModelDataSource.Username = 'domain\user'
    ```
    ```powershell
    $dataSources[0].DataModelDataSource.Secret = 'password'
    ```

4. Mentse vissza a frissített hitelesítő adatokat a kiszolgálóra.

    ```powershell
    Set-RsRestItemDataSource -RsItem '/MyPbixReport' -RsItemType 'PowerBIReport' -DataSources $dataSources
    ```

## <a name="next-steps"></a>Következő lépések

[Oldalakra osztott jelentések adatforrásai a Power BI jelentéskészítő kiszolgálón](connect-data-sources.md) 

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
