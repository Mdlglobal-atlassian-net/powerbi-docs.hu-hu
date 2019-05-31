---
title: Csatlakozás a Microsoft Azure Consumption Insightshoz a Power BI használatával
description: A Power BI-hoz készült Microsoft Azure Consumption Insights
author: SarinaJoan
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 05/20/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 089f8c31a0b1eb11f6871268f2f848949be95d9b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222121"
---
# <a name="connect-to-microsoft-azure-consumption-insights-with-power-bi"></a>Csatlakozás a Microsoft Azure Consumption Insightshoz a Power BI használatával
A Power BI-tartalomcsomaggal a Power BI-ban vizsgálhatja és elemezheti a Microsoft Azure használati adatait. Az adatok naponta egyszer automatikusan frissülnek.

Csatlakozzon a Power BI-hoz készült [Microsoft Azure Consumption Insights tartalomcsomaghoz](https://app.powerbi.com/getdata/services/azureconsumption).

## <a name="how-to-connect"></a>Csatlakozás
1. A bal oldali navigációs ablaktábla alján kattintson az **Adatok lekérése** elemre.
   
    ![](media/service-connect-to-azure-consumption-insights/getdata.png)
2. A **Szolgáltatások** mezőben kattintson a **Lekérés** elemre.
   
   ![](media/service-connect-to-azure-consumption-insights/services.png)
3. Válassza ki **a Microsoft Azure Consumption Insights** \> **Letöltés most**. 
   
   ![](media/service-connect-to-azure-consumption-insights/mazureconsumption.png)
4. Adja meg, hogy hány hónapnyi adatot szeretne importálni, valamint az Azure Enterprise beléptetési számát. A [paraméterek fellelhetőségével](#FindingParams) kapcsolatos információt lásd alább.
   
    ![](media/service-connect-to-azure-consumption-insights/azureconsumptionparams.png)
5. A csatlakozáshoz adja meg a hozzáférési kulcsát. A regisztrációs kulcsot az Azure EA Portalon található. 
   
    ![](media/service-connect-to-azure-consumption-insights/msazureconsumptioncreds.png)
6. Az importálás automatikusan megkezdődik. Amikor végzett, egy új irányítópult, jelentés és modell jelennek meg a navigációs ablaktáblán. Válassza ki az irányítópultot az importált adatok megtekintéséhez.
   
   ![](media/service-connect-to-azure-consumption-insights/msazureconsumptiondashboard.png)

**Mi a következő lépés?**

* [Kérdéseket tehet fel a Q&A mezőben](consumer/end-user-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](consumer/end-user-tiles.md) a mögöttes jelentés megnyitásához.
* Míg az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy próbálja meg frissíteni ezt az adatkészletet a **frissítés most**

## <a name="whats-included"></a>Tartalom
A Microsoft Azure Consumption Insights tartalomcsomag a kapcsolódáskor a megadott hónap tartomány vonatkozó havi jelentésadatokat tartalmazza. A tartomány egy mozgó időablak,, így a dátumok az adatkészlet frissítésekor frissülnek.

## <a name="system-requirements"></a>Rendszerkövetelmények
A tartalomcsomag használatához hozzáférés a vállalati szolgáltatásokhoz az Azure Portalon. 

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Paraméterek helye
A Power BI-jelentés érhető el a közvetlen nagyvállalati szerződéssel rendelkező, partneri és közvetett ügyfelek számára, akiknek a számlázási információk is megtekinthetők. Olvassa el alább a csatlakozási folyamat vár értékeit helyével kapcsolatos részleteket.

**Hónapok száma**

* A mai importálni kívánt adatokat (1 és 36) hónapok száma.

**Beléptetési szám**

* Az Azure Enterprise beléptetési számát, amelyet címen találja a [Azure Enterprise Portalról](https://ea.azure.com/) kezdőképernyő alatt **regisztráció részletei**.
  
    ![](media/service-connect-to-azure-consumption-insights/params2.png)

**Hozzáférési kulcs**

* Találhatja meg a hozzáférési kulcsot az Azure Enterprise portálon a **használati adatok letöltése** > **API hozzáférési kulcsa**.
  
    ![](media/service-connect-to-azure-consumption-insights/creds2.png)

**További segítség**

* További segítséget a beállítása az Azure Enterprise Power BI-csomag, jelentkezzen be az Azure Enterprise Portalra, és megtekintheti az API súgófájlját alatt **súgó**. A további utasításokat is megtalálhatja **jelentések** -> **használati adatok letöltése** -> **API hozzáférési kulcsa**.

## <a name="next-steps"></a>Következő lépések
[Első lépések a Power BI-ban](service-get-started.md)

[Adatok lekérése a Power BI-ban](service-get-data.md)

