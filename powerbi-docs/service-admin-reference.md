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
ms.openlocfilehash: f4455fef5a2ed0e7ee23ff8ca3a0b626cd695838
ms.sourcegitcommit: a1b7ca499f4ca7e90421511e9dfa61a33333de35
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/10/2018
ms.locfileid: "51507991"
---
# <a name="powershell-cmdlets-rest-apis-and-net-sdk-for-power-bi-administration"></a>PowerShell-parancsmagok, REST API-k és a .NET SDK a Power BI felügyeletéhez
A Power BI segítségével a rendszergazdák gyakori feladatokat végeztethetnek el PowerShell-parancsmagokkal. A Power BI emellett REST API-kkal is rendelkezik, valamint felügyeleti megoldások fejlesztésére is használható a .NET SDK-val. Ez a témakör parancsmagokat, valamint a hozzájuk tartozó SDK-módszert és REST API-végpontot ismerteti. További információ:

  - PowerShell – [Letöltés](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt/) és [dokumentáció](https://docs.microsoft.com/powershell/power-bi/overview?view=powerbi-ps)
  - REST API – [dokumentáció](https://docs.microsoft.com/rest/api/power-bi/admin)
  - .NET SDK – [Letöltés](https://www.nuget.org/packages/Microsoft.PowerBI.Api/) 


| **Parancsmag neve** | **SDK-módszer** | **REST API-végpont** | **Leírás** |
| --- | --- | --- | --- |
| **Get-PowerBIDatasource** | Datasets\_GetDataSourcesAsAdmin | /v1.0/myorg/admin/datasets/{datasetkey}/datasources | Lekéri egy adott adatkészlet adatforrásait. |
| **Get-PowerBIDataset** | Datasets\_GetDatasetsAsAdmin | /v1.0/myorg/admin/datasets | Lekéri egy Power BI-bérlő összes adatkészletét. |
| **Get-PowerBIWorkspace** | Groups\_GetGroupsAsAdmin | /v1.0/myorg/admin/groups | Lekéri egy Power BI-bérlő összes munkaterületét. |
| **Add-PowerBIWorkspaceUser** | Groups\_AddUserAsAdmin | /v1.0/myorg/admin/groups/{groupId}/users | Tagként hozzáad egy felhasználót egy adott munkaterülethez. |
| **Remove-PowerBIWorkspaceUser** | Groups\_DeleteUserAsAdmin | /v1.0/myorg/admin/groups/{groupId}/users/{user} | Eltávolít egy felhasználót egy adott munkaterület tagjai közül. |
| **Restore-PowerBIWorkspace** | Groups\_RestoreDeletedGroupAsAdmin | /v1.0/myorg/admin/groups/{groupId}/restore | Visszaállít egy törölt munkaterületet. |
| **Set-PowerBIWorkspace** | Groups\_UpdateGroupAsAdmin | /v1.0/myorg/admin/groups/{groupId} | Frissíti egy adott munkaterület tulajdonságait. |
| **Get-PowerBIDataset -WorkspaceId** | Groups\_GetDatasetsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/datasets | Lekéri egy adott munkaterület adatkészleteit. |
| **Export-PowerBIReport** | Reports\_ExportReportAsAdmin | N.A. | Egy helyi fájlba exportál egy adott jelentést. |
| **Get-PowerBIReport** | Reports\_GetReportsAsAdmin | /v1.0/myorg/admin/reports | Lekéri egy Power BI-bérlő összes jelentését. |
| **Get-PowerBIDashboard** | Dashboards\_GetDashboardsAsAdmin | /v1.0/myorg/admin/dashboards | Lekéri egy Power BI-bérlő összes irányítópultját. |
| **Get-PowerBIDashboard -WorkspaceId** | Groups\_GetDashboardsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/dashboards | Lekéri egy adott munkaterület irányítópultjait. |
| **Get-PowerBITile -DashboardId** | Dashboards\_GetTilesAsAdmin | /v1.0/myorg/admin/dashboards/{dashboard\_id}/tiles | Lekéri egy adott irányítópult csempéit. |
| **Get-PowerBIReport -WorkspaceId** | Groups\_GetReportsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/reports | Lekéri egy adott munkaterület jelentéseit. |
| **Get-PowerBIImport** | Import\_GetImportsAsAdmin | /v1.0/myorg/admin/imports | Lekéri egy Power BI-bérlő összes importálását. |
| **Connect-PowerBIServiceAccount** | N.A. | N.A. | Bejelentkezés a Power BI-ba és egy munkamenet elindítása. |
| **Disconnect-PowerBIServiceAccount** | N.A. | N.A. | Kijelentkezés a Power BI-ból és az aktuális munkamenet bezárása. |
| **Invoke-PowerBIRestMethod** | N.A. | N.A. | Tetszőleges REST API-hívások küldése a Power BI-ba. |
| **Get-PowerBIAccessToken** | N.A. | N.A. | A Power BI hozzáférési jogkivonatának beszerzése egy munkamenetben. |
| **Resolve-PowerBIError** | N.A. | N.A. | Részletes hibaadatok lekérése sikertelen parancsmaghívások esetén. |