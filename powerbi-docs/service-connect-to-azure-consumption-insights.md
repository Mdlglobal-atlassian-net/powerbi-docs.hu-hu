---
title: Csatlakozás a Microsoft Azure Consumption Insightshoz a Power BI használatával
description: A Power BI-hoz készült Microsoft Azure Consumption Insights
author: SarinaJoan
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 8a8b6d930dcb5ded8c8913ca9e706fe50d16048f
ms.sourcegitcommit: 750f0bfab02af24c8c72e6e9bbdd876e4a7399de
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/04/2019
ms.locfileid: "54008212"
---
# <a name="connect-to-microsoft-azure-consumption-insights-with-power-bi"></a>Csatlakozás a Microsoft Azure Consumption Insightshoz a Power BI használatával
A Power BI-tartalomcsomaggal a Power BI-ban vizsgálhatja és elemezheti a Microsoft Azure használati adatait. Az adatok naponta egyszer automatikusan frissülnek.

Csatlakozzon a Power BI-hoz készült [Microsoft Azure Consumption Insights tartalomcsomaghoz](https://app.powerbi.com/getdata/services/azureconsumption).

## <a name="how-to-connect"></a>Csatlakozás
1. A bal oldali navigációs ablaktábla alján kattintson az **Adatok lekérése** elemre.
   
    ![](media/service-connect-to-azure-consumption-insights/getdata.png)
2. A **Szolgáltatások** mezőben kattintson a **Lekérés** elemre.
   
   ![](media/service-connect-to-azure-consumption-insights/services.png)
3. Válassza a **Microsoft Azure Consumption Insights** \> **Lekérés** elemet. 
   
   ![](media/service-connect-to-azure-consumption-insights/mazureconsumption.png)
4. Adja meg, hogy hány hónapnyi adatot szeretne importálni, valamint az Azure Enterprise beléptetési számát. A [paraméterek fellelhetőségével](#FindingParams) kapcsolatos információt lásd alább.
   
    ![](media/service-connect-to-azure-consumption-insights/azureconsumptionparams.png)
5. A csatlakozáshoz adja meg a hozzáférési kulcsát. A beléptetési kulcs az Azure EA Portalon található. 
   
    ![](media/service-connect-to-azure-consumption-insights/msazureconsumptioncreds.png)
6. Az importálási folyamat automatikusan megkezdődik. Ha befejeződött, a navigációs panelen megjelenik egy új irányítópult, jelentés és modell. Válassza ki az irányítópultot az importált adatok megtekintéséhez.
   
   ![](media/service-connect-to-azure-consumption-insights/msazureconsumptiondashboard.png)

**Mi a következő lépés?**

* [Kérdéseket tehet fel a Q&A mezőben](consumer/end-user-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](consumer/end-user-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

## <a name="whats-included"></a>Tartalom
A Microsoft Azure Consumption Insights tartalomcsomag a csatlakozási folyamat során megadott hónaptartományra vonatkozó havi jelentésadatokat tartalmazza. A tartomány egy mozgó időablak, és a dátumok az adatkészlet frissítésekor frissülnek.

## <a name="system-requirements"></a>Rendszerkövetelmények
A tartalomcsomag használatához hozzáférés szükséges a Vállalati szolgáltatásokhoz az Azure Portalon. 

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Paraméterek helye
A Power BI-jelentések készítése olyan közvetlen, partneri és közvetett vállalati szerződéssel rendelkező ügyfelek számára elérhető, akik meg tudják tekinteni a számlázási adatokat. Ezeknek, a csatlakozási folyamat során megadni szükséges értékeknek a helyével kapcsolatos részleteket lásd alább.

**Hónapok száma**

* Egy 1 és 36 közötti szám, amely az importálni kívánt hónapok száma (a mai naptól számítva).

**Beléptetési szám**

* Ez az Azure Enterprise beléptetési száma, amely az [Azure Enterprise Portal](https://ea.azure.com/) kezdőképernyőjén, a „Regisztráció részletei” felületen található.
  
    ![](media/service-connect-to-azure-consumption-insights/params2.png)

**Hozzáférési kulcs**

* A hozzáférési kulcs az Azure Enterprise portálon a „Használati adatok letöltése” > „API hozzáférési kulcsa” alatt található.
  
    ![](media/service-connect-to-azure-consumption-insights/creds2.png)

**További segítség**

* Az Azure Enterprise Power BI csomag telepítésével kapcsolatos további segítségért jelentkezzen be az Azure Enterprise Portalra, és tekintse meg az API súgófájlját a „Súgó” felületen, valamint a további utasításokat a Jelentések -> Használati adatok letöltése -> API hozzáférési kulcsa alatt. 

## <a name="next-steps"></a>Következő lépések
[Első lépések a Power BI-ban](service-get-started.md)

[Adatok lekérése a Power BI-ban](service-get-data.md)

