---
title: Csatlakozás a Microsoft Azure Consumption Insightshoz a Power BI használatával
description: A Power BI-hoz készült Microsoft Azure Consumption Insights
author: SarinaJoan
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 09/25/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: e51f936e44e8c8ee3442aedfb2389675774c0a47
ms.sourcegitcommit: 5e277dae93832d10033defb2a9e85ecaa8ffb8ec
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/07/2019
ms.locfileid: "72020436"
---
# <a name="connect-to-microsoft-azure-consumption-insights-with-power-bi"></a>Csatlakozás a Microsoft Azure Consumption Insightshoz a Power BI használatával
A Power BI-tartalomcsomaggal a Power BI szolgáltatásban vizsgálhatja és elemezheti a Microsoft Azure használati adatait. Az adatokat naponta egyszer automatikusan frissíti a rendszer.

Csatlakozzon a Power BI szolgáltatáshoz készült [Microsoft Azure Consumption Insights tartalomcsomaghoz](https://app.powerbi.com/getdata/services/azureconsumption).

> [!NOTE]
> A beállítások jobb testreszabása érdekében próbálja ki az [Azure Consumption Insights-összekötőt](desktop-connect-azure-consumption-insights.md) a Power BI Desktopban.

## <a name="how-to-connect"></a>Csatlakozás
1. A Power BI szolgáltatás bal oldali navigációs panelének alján kattintson az **Adatok lekérése** elemre.
   
    ![Adatok beolvasása](media/service-connect-to-azure-consumption-insights/getdata.png)
2. A **Szolgáltatások** mezőben kattintson a **Lekérés** elemre.
   
   ![Szolgáltatások lekérése](media/service-connect-to-azure-consumption-insights/services.png)
3. Válassza a **Microsoft Azure Consumption Insights** \> **Azonnali lekérés** elemet. 
   
   ![Beszerzés most](media/service-connect-to-azure-consumption-insights/mazureconsumption.png)
4. Adja meg, hogy hány hónapnyi adatot szeretne importálni, valamint az Azure Enterprise beléptetési számát. A [paraméterek fellelhetőségével](#FindingParams) kapcsolatos információt lásd alább.
   
    ![Csatlakozás a Microsoft Azure Consumption Insights szolgáltatáshoz](media/service-connect-to-azure-consumption-insights/azureconsumptionparams.png)
5. A csatlakozáshoz adja meg a hozzáférési kulcsát. A regisztrációs kulcsot az Azure EA Portalon találja meg. 
   
    ![Microsoft Azure Consumption Insights: kulcs](media/service-connect-to-azure-consumption-insights/msazureconsumptioncreds.png)
6. Az importálás automatikusan megkezdődik. Ha befejeződött, a navigációs panelen megjelenik egy új irányítópult, jelentés és modell. Válassza ki az irányítópultot az importált adatok megtekintéséhez.
   
   ![Microsoft Azure Consumption Insights irányítópult](media/service-connect-to-azure-consumption-insights/msazureconsumptiondashboard.png)

**Mi a következő lépés?**

* [Kérdéseket tehet fel a Q&A mezőben](consumer/end-user-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](consumer/end-user-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal

## <a name="whats-included"></a>Tartalom
A Microsoft Azure Consumption Insights tartalomcsomag a csatlakozás során megadott hónaptartományra vonatkozó havi jelentésadatokat tartalmazza. A tartomány egy mozgó időablak, ezért a dátumok az adathalmaz frissítésekor lesznek frissítve.

## <a name="system-requirements"></a>Rendszerkövetelmények
A tartalomcsomag használatához hozzáférés szükséges a Vállalati szolgáltatásokhoz az Azure Portalon. 

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Paraméterek helye
A Power BI-jelentések készítése olyan közvetlen, partneri és közvetett vállalati szerződéssel rendelkező ügyfelek számára elérhető, akik meg tudják tekinteni a számlázási adatokat. Az alábbiakban megtalálhatja az ezeknek a csatlakozási folyamat során megadandó értékeknek a helyével kapcsolatos részleteket.

**Hónapok száma**

* Az importálni kívánt adatok dátuma a mai naptól számított hónapokban (1-36) megadva.

**Beléptetési szám**

* Ez az Ön Azure Enterprise beléptetési száma, amelyet az [Azure Enterprise Portal](https://ea.azure.com/) kezdőképernyőjén, a **Regisztráció részletei** területen talál.
  
    ![Regisztrációs szám](media/service-connect-to-azure-consumption-insights/params2.png)

**Hozzáférési kulcs**

* A hozzáférési kulcsot az Azure Enterprise portálon a **Használati adatok letöltése** > **API hozzáférési kulcsa** területen találhatja meg.
  
    ![Hozzáférési kulcs](media/service-connect-to-azure-consumption-insights/creds2.png)

**További segítség**

* További segítséget kaphat az Azure Enterprise Power BI-csomag beállításához, ha bejelentkezik az Azure Enterprise Portalra, és a **Súgó** területen megtekinti az API-súgófájlt. A **Jelentések** -> **Használati adatok letöltése** -> **API-hozzáférési kulcs** területen is találhat további útmutatást.
* A beállítások jobb testreszabása érdekében próbálja ki az [Azure Consumption Insights-összekötőt](desktop-connect-azure-consumption-insights.md) a Power BI Desktopban.

## <a name="next-steps"></a>Következő lépések

Az [Azure Consumption Insights-összekötő](desktop-connect-azure-consumption-insights.md) a Power BI Desktopban

[Adatok lekérése a Power BI-ban](service-get-data.md)

