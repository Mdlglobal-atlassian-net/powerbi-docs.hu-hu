---
title: A Power BI jelentéskészítő kiszolgáló és a Power BI szolgáltatás összehasonlítása
description: Ez a cikk a Power BI jelentéskészítő kiszolgáló és a Power BI szolgáltatás funkcióit hasonlítja össze.
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
ms.date: 02/13/2020
ms.openlocfilehash: c760450319f5ca32856520bce9c9f9b67a8616d6
ms.sourcegitcommit: d6a48e6f6e3449820b5ca03638b11c55f4e9319c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/18/2020
ms.locfileid: "77427760"
---
# <a name="comparing-power-bi-report-server-and-the-power-bi-service"></a>A Power BI jelentéskészítő kiszolgáló és a Power BI szolgáltatás összehasonlítása

A Power BI jelentéskészítő kiszolgálónak és a Power BI szolgáltatásnak sok hasonló és néhány jelentősen eltérő tulajdonsága van. Ez a táblázat ezeket mutatja be.

## <a name="features-of-power-bi-report-server-and-the-power-bi-service"></a>A Power BI jelentéskészítő kiszolgáló és a Power BI szolgáltatás funkciói

| Funkciók | Power BI jelentéskészítő kiszolgáló | Power BI szolgáltatás | Megjegyzések |
|---------|---------|---------|---------|
| Telepítés | Helyszíni vagy üzemeltetett felhőbeli | Felhő | A Power BI jelentéskészítő kiszolgáló akkor helyezhető üzembe Azure-beli virtuális gépeken (üzemeltetett felhőbeli) ha licencelése a Power BI Premiummal történt |
| Forrásadatok | Felhőbeli és/vagy helyszíni | Felhőbeli és/vagy helyszíni |  |
| Licenc | Power BI Premium vagy SQL Server EE frissítési garanciával (SA) | Power BI Pro és/vagy Power BI Premium | |  
| Életciklus | Modern életciklus-szabályzat | Teljes körűen felügyelt szolgáltatás |  |
| Kiadási ciklus | Évente háromszor (január, május, szeptember) | Havonta | A legújabb funkciók és javítások először a Power BI szolgáltatáshoz jelennek meg. Az alapfunkciók többsége a következő néhány kiadásban jelenik meg a Power BI jelentéskészítő kiszolgálóhoz; bizonyos funkciók csak a Power BI szolgáltatáshoz készülnek. |
| Power BI-jelentések létrehozása a Power BI Desktopban | Igen | Igen |  |
| Power BI-jelentések létrehozása a böngészőben | Nem | Igen |  |
| Megosztott Power BI-adatkészletek üzemeltetése és ezekhez való csatlakozás | Nem | Igen | [Adathalmazok használata több munkaterületen](../service-datasets-across-workspaces.md) |
| Átjáró szükséges | Nem | Helyszíni adatforrásokhoz igen |  |
| Valós idejű streamelés | Nem | Igen | [Valós idejű streamelés a Power BI-ban](../service-real-time-streaming.md) |
| Irányítópultok | Nem | Igen | [Irányítópultok a Power BI szolgáltatásban](../consumer/end-user-dashboards.md) |
| Jelentéscsoportok terjesztése alkalmazások használatával | Nem | Igen | [Irányítópultokat és jelentéseket tartalmazó alkalmazások létrehozása és közzététele](../service-create-distribute-apps.md) |
| Tartalomcsomagok | Nem | Igen | [Céges tartalomcsomagok: Bevezetés](../service-organizational-content-pack-introduction.md) |
| Csatlakozás olyan szolgáltatásokhoz, mint a Salesforce | Igen | Igen | [Csatlakozhat a használt szolgáltatásokhoz](../service-connect-to-services.md) a Power BI szolgáltatás tartalomcsomagjaival. A Power BI jelentéskészítő kiszolgálón a hitelesített összekötők használatával csatlakozhat szolgáltatásokhoz. További információt [A Power BI-jelentések adatforrásai a Power BI jelentéskészítő kiszolgálón](data-sources.md) című témakörben talál. |
| Q&A | Nem | Igen | [A Q&A a Power BI szolgáltatásban és a Power BI Desktopban](../power-bi-tutorial-q-and-a.md) 
| Gyors elemzések | Nem | Igen | [Adatelemzések automatikus generálása a Power BI-jal](../consumer/end-user-insights.md) |
| Elemzés az Excelben | Nem | Igen | [Elemzés az Excelben](../service-analyze-in-excel.md) 
| Oldalakra osztott jelentések | Igen | Igen | A prémium szintű kapacitásban előzetes verzióban [elérhetők a Power BI szolgáltatás lapszámozott jelentései](../paginated-reports-report-builder-power-bi.md) |
| Power BI – mobilalkalmazások | Igen | Igen | [Power BI-mobilalkalmazások áttekintése](../consumer/mobile/mobile-apps-for-mobile-devices.md) |
| ArcGIS-térképek | Nem | Igen | [Esri ArcGIS-térképek a Power BI szolgáltatásban és a Power BI Desktopban](../visuals/power-bi-visualization-arcgis.md) |
| E-mail-előfizetés Power BI-jelentésekre | Nem | Igen | [Feliratkozás és mások feliratkoztatása](../service-report-subscribe.md) egy jelentésre vagy irányítópultra a Power BI szolgáltatásban |
| E-mail-előfizetés többoldalas jelentésekre | Igen | Igen | [Feliratkozás és mások feliratkoztatása többoldalas jelentésre a Power BI szolgáltatásban](../consumer/paginated-reports-subscriptions.md)<br><br>[E-mail-kézbesítés a Reporting Servicesben](https://docs.microsoft.com/sql/reporting-services/working-with-subscriptions-web-portal)  |
| Adatriasztások | Nem | Igen | [Adatriasztások](../service-set-data-alerts.md) a Power BI szolgáltatásban
| Sorszintű biztonság (RLS) | Igen | Igen | Elérhető DirectQuery- (adatforrással) és Import-módban is <br><br>Sorszintű biztonság (RLS) a [Power BI szolgáltatásban](../service-admin-rls.md) <br><br>Sorszintű biztonság (RLS) a [Power BI jelentéskészítő kiszolgálóban](row-level-security-report-server.md) |
| Teljes képernyős mód | Nem | Igen | [Teljes képernyős mód](../consumer/end-user-focus.md) a Power BI szolgáltatásban |
| Fejlett Office 365-együttműködés | Nem | Igen | [Együttműködés egy munkaterületen](../service-collaborate-power-bi-workspace.md) az Office 365-tel |
| R vizualizációk | Nem | Igen | A Power BI Desktopban [R-vizualizációkat](../desktop-r-visuals.md) hozhat létre, és közzéteheti őket a Power BI szolgáltatásban. Az R-vizualizációt tartalmazó Power BI-jelentéseket nem lehet menteni a Power BI jelentéskészítő kiszolgálón.  |
| Előzetes verziójú funkciók | Nem | Igen | [Feliratkozás a Power BI szolgáltatás előzetes verziójú](../consumer/end-user-preview-features.md) funkcióira |
| Egyéni vizualizációk | Igen | Igen | [Egyéni vizualizációk a Power BI-ban](../developer/power-bi-custom-visuals.md) |
| Összetett modellek | Nem | Igen |
| Power BI Desktop | A Jelentéskészítő kiszolgálóhoz optimalizált verzió a Jelentéskészítő kiszolgálóval letölthető | A Power BI szolgáltatáshoz optimalizált verzió elérhető a Windows Áruházban | [Power BI Desktop a jelentéskészítő kiszolgálóhoz](https://powerbi.microsoft.com/report-server/) <br><br> [Power BI Desktop a Power BI szolgáltatáshoz](https://aka.ms/pbidesktopstore) |

## <a name="next-steps"></a>Következő lépések

[A Power BI jelentéskészítő kiszolgáló telepítése](install-report-server.md)
