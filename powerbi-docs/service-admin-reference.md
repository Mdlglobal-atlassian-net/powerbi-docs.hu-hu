---
title: PowerShell-parancsmagok, REST API-k és a .NET SDK rendszergazdáknak
description: Ismerje meg a Power BI szkriptekkel és API-kkal való felügyeletének módjait.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: overview
ms.date: 06/25/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 216451874fcc66b14286ea4ed3aeb1845483bfb7
ms.sourcegitcommit: 05303d3e0454f5627eccaa25721b2e0bad2cc781
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52578359"
---
# <a name="powershell-cmdlets-rest-apis-and-net-sdk-for-power-bi-administration"></a>PowerShell-parancsmagok, REST API-k és a .NET SDK a Power BI felügyeletéhez
A Power BI segítségével a rendszergazdák gyakori feladatokat végeztethetnek el PowerShell-parancsmagokkal. A Power BI emellett REST API-kkal is rendelkezik, valamint felügyeleti megoldások fejlesztésére is használható a .NET SDK-val. Ez a témakör parancsmagokat, valamint a hozzájuk tartozó SDK-módszert és REST API-végpontot ismerteti. További információ:

- PowerShell – [Letöltés](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt/) és [dokumentáció](https://docs.microsoft.com/powershell/power-bi/overview?view=powerbi-ps)
- REST API – [dokumentáció](https://docs.microsoft.com/rest/api/power-bi/admin)
- .NET SDK – [Letöltés](https://www.nuget.org/packages/Microsoft.PowerBI.Api/)

> Az alábbi parancsmagokat a `-Scope Organization` hívhatja a bérlő kezeléséhez.

| **Parancsmag neve** | **Aliasnevek** | **SDK-módszer** | **REST API-végpont** | **Leírás** |
| --- | --- | --- | --- | --- |
| **Get-PowerBIDatasource** | N.A. | Datasets\_GetDataSourcesAsAdmin | /v1.0/myorg/admin/datasets/{datasetkey}/datasources | Lekéri egy adott adatkészlet adatforrásait. |
| **Get-PowerBIDataset** | N.A. | Datasets\_GetDatasetsAsAdmin | /v1.0/myorg/admin/datasets | Lekéri egy Power BI-bérlő összes adatkészletét. |
| **Get-PowerBIWorkspace** | **Get-PowerBIGroup** | Groups\_GetGroupsAsAdmin | /v1.0/myorg/admin/groups | Lekéri egy Power BI-bérlő összes munkaterületét. |
| **Add-PowerBIWorkspaceUser** | **Add-PowerBIGroupUser** |Groups\_AddUserAsAdmin | /v1.0/myorg/admin/groups/{groupId}/users | Tagként hozzáad egy felhasználót egy adott munkaterülethez. |
| **Remove-PowerBIWorkspaceUser** | **Remove-PowerBIGroupUser** | Groups\_DeleteUserAsAdmin | /v1.0/myorg/admin/groups/{groupId}/users/{user} | Eltávolít egy felhasználót egy adott munkaterület tagjai közül. |
| **Restore-PowerBIWorkspace** |**Restore-PowerBIGroup** | Groups\_RestoreDeletedGroupAsAdmin | /v1.0/myorg/admin/groups/{groupId}/restore | Visszaállít egy törölt munkaterületet. |
| **Set-PowerBIWorkspace** |**Set-PowerBIGroup** | Groups\_UpdateGroupAsAdmin | /v1.0/myorg/admin/groups/{groupId} | Frissíti egy adott munkaterület tulajdonságait. |
| **Get-PowerBIDataset -WorkspaceId** | N.A. | Groups\_GetDatasetsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/datasets | Lekéri egy adott munkaterület adatkészleteit. |
| **Get-PowerBIReport** | N.A. | Reports\_GetReportsAsAdmin | /v1.0/myorg/admin/reports | Lekéri egy Power BI-bérlő összes jelentését. |
| **Get-PowerBIDashboard** | N.A. | Dashboards\_GetDashboardsAsAdmin | /v1.0/myorg/admin/dashboards | Lekéri egy Power BI-bérlő összes irányítópultját. |
| **Get-PowerBIDashboard -WorkspaceId** | N.A. | Groups\_GetDashboardsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/dashboards | Lekéri egy adott munkaterület irányítópultjait. |
| **Get-PowerBITile** | **Get-PowerBIDashboardTile** | Dashboards\_GetTilesAsAdmin | /v1.0/myorg/admin/dashboards/{dashboard\_id}/tiles | Lekéri egy adott irányítópult csempéit. |
| **Get-PowerBIReport** | N.A. | Groups\_GetReportsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/reports | Lekéri egy adott munkaterület jelentéseit. |
| **Get-PowerBIImport** | N.A. | Import\_GetImportsAsAdmin | /v1.0/myorg/admin/imports | Lekéri egy Power BI-bérlő összes importálását. |
| **Connect-PowerBIServiceAccount** | **Login-PowerBI** &  **Login-PowerBIServiceAccount** | N.A. | N.A. | Bejelentkezés a Power BI-ba és egy munkamenet elindítása. |
| **Disconnect-PowerBIServiceAccount** | **Logout-PowerBI** & **Logout-PowerBIServiceAccount** | N.A. | N.A. | Kijelentkezés a Power BI-ból és az aktuális munkamenet bezárása. |
| **Invoke-PowerBIRestMethod**| N.A. | N.A. | N.A. | Tetszőleges REST API-hívások küldése a Power BI-ba. |
| **Get-PowerBIAccessToken**| N.A. | N.A. | N.A. | A Power BI hozzáférési jogkivonatának beszerzése egy munkamenetben. |
| **Resolve-PowerBIError**| N.A. | N.A. | N.A. | Részletes hibaadatok lekérése sikertelen parancsmaghívások esetén. |
