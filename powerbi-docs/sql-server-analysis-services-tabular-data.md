---
title: Az SQL Server Analysis Services élő adatai a Power BI-ban
description: Az SQL Server Analysis Services élő adatai a Power BI-ban. Ez egy vállalati átjáróhoz konfigurált adatforrásban történik.
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
author: Minewiskan
ms.author: owend
ms.reviewer: ''
ms.custom: ''
ms.date: 08/10/2017
LocalizationGroup: Data from databases
ms.openlocfilehash: 00b7c98236f37505fbb0ddec81a45b65bf3e3ee6
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73871188"
---
# <a name="sql-server-analysis-services-live-data-in-power-bi"></a>Az SQL Server Analysis Services élő adatai a Power BI-ban

A Power BI szolgáltatásban kétféleképpen csatlakozhat egy SQL Server Analysis Services-kiszolgálóhoz. Az **Adatok lekérése** lehetőséggel csatlakozhat egy SQL Server Analysis Services-kiszolgálóhoz, vagy egy [Power BI Desktop-fájlhoz](service-desktop-files.md), vagy egy olyan [Excel-munkafüzethez](service-excel-workbook-files.md), amely már csatlakozik egy Analysis Services-kiszolgálóhoz. Ajánlott eljárásként a Microsoft a Power BI Desktop használatát javasolja az ott elérhető gazdag eszközkészlet miatt, illetve mert könnyedén tárolhat helyben biztonsági másolatokat a Power BI Desktop-fájlról.

>[!IMPORTANT]
> * Egy élő Analysis Services-kiszolgálóhoz való csatlakozáshoz egy rendszergazdának egy helyszíni adatátjárót kell telepítenie és konfigurálnia. További információ: [Helyszíni adatátjáró](service-gateway-onprem.md).
> * Az átjáró használatakor az adatok a helyszínen maradnak.  Az adatok alapján létrehozott jelentéseket menti a Power BI szolgáltatás. 
> * [A Q&A természetes nyelvű lekérdezés](service-q-and-a-direct-query.md) jelenleg előzetes verzióban érhető el az Analysis Services élő kapcsolataihoz.

## <a name="to-connect-to-a-model-from-get-data"></a>Csatlakozás egy modellhez az Adatok lekérése funkcióval

1. A **Saját munkaterületen** válassza az**Adatok lekérése** lehetőséget. Amennyiben elérhető, egy csoportos munkaterületre is válthat.

   ![Kapcsolódás az Adatok lekérése gombhoz](media/sql-server-analysis-services-tabular-data/connecttoas_getdatabutton.png)

2. Válassza az **Adatbázisok és egyéb** lehetőséget.

   ![Kapcsolódás az adatok lekéréséhez, 1.](media/sql-server-analysis-services-tabular-data/connecttoas_getdata_1.png)

3. Válassza az **SQL Server Analysis Services** > **Csatlakozás** lehetőséget.

   ![Kapcsolódás az adatok lekéréséhez, 2.](media/sql-server-analysis-services-tabular-data/connecttoas_getdata_2.png)

4. Válasszon egy kiszolgálót. Ha nem lát egy kiszolgálót sem, akkor vagy egy átjáró vagy egy adatforrás nincs konfigurálva, vagy a fiókja nem szerepel az adatforrás **Felhasználók** lapján az átjáróban. Kérje a rendszergazda segítségét.

5. Válassza ki, melyik modellhez szeretne csatlakozni. Ez lehet egy táblázatos vagy többdimenziós típus.

Miután csatlakozott a modellhez, az megjelenik a saját Power BI-webhelyén a **Saját munkaterület/Adatkészletek** területen. Ha csoportos munkaterületre váltott, az adatkészlet a csoporton belül jelenik meg.

![Csatlakozás adatkészlethez](media/sql-server-analysis-services-tabular-data/connecttoas_dataset_5.png)

## <a name="dashboard-tiles"></a>Irányítópult-csempék

Ha vizualizációkat rögzít egy jelentésből az irányítópultra, a rögzített csempék 10 percenként automatikusan frissülnek. Ha frissülnek a helyszíni Analysis Services-adatok, a csempék 10 perc elteltével automatikusan frissülnek.

## <a name="common-issues"></a>Gyakori problémák

* A modellséma nem tölthető be hiba – Ez a hiba akkor jelentkezik, ha a SSAS-hez csatlakozó felhasználónak nincs hozzáférési jogosultsága az SSAS-adatbázishoz, -adatkockához vagy -modellhez.

## <a name="next-steps"></a>Következő lépések

* [Helyszíni adatátjáró](service-gateway-onprem.md)  
* [Az Analysis Services adatforrásainak kezelése](service-gateway-enterprise-manage-ssas.md)  
* [A Helyszíni adatátjáróval kapcsolatos hibák elhárítása](service-gateway-onprem-tshoot.md)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)