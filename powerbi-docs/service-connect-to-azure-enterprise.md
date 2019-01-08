---
title: Csatlakozás a Microsoft Azure Enterprise-hoz a Power BI használatával
description: Microsoft Azure Enterprise a Power BI-hoz
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 4cedeac37a47ffaa41ff9088c9ef36c37b4c784e
ms.sourcegitcommit: 750f0bfab02af24c8c72e6e9bbdd876e4a7399de
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/04/2019
ms.locfileid: "54008281"
---
# <a name="connect-to-microsoft-azure-enterprise-with-power-bi"></a>Csatlakozás a Microsoft Azure Enterprise-hoz a Power BI használatával
A Power BI-tartalomcsomag segítségével a Power BI-ban vizsgálhatja és figyelheti Microsoft Azure Enterprise-beli adatait. Az adatok naponta egyszer automatikusan frissülnek.

Csatlakozás a [Microsoft Azure Enterprise-tartalomcsomaghoz](https://app.powerbi.com/getdata/services/azure-enterprise) a Power BI használatával.

## <a name="how-to-connect"></a>A csatlakozás menete
1. A bal oldali navigációs ablaktábla alján kattintson az **Adatok lekérése** elemre.
   
    ![](media/service-connect-to-azure-enterprise/getdata.png)
2. A **Szolgáltatások** mezőben válasza a **Beolvasás** elemet.
   
   ![](media/service-connect-to-azure-enterprise/services.png)
3. Kattintson a **Microsoft Azure Enterprise** \> **Beolvasás** elemre.
   
   ![](media/service-connect-to-azure-enterprise/mazureenterprise.png)
4. Adja meg az Azure-környezet URL-címét, az Azure Enterprise regisztrációs számát, és azt, hogy hány havi adatot kíván importálni. Az Azure-környezet URL-címe `https://ea.azure.com` vagy `https://ea.windowsazure.cn`. A [paraméterek megkereséséről](#FindingParams) alább olvashat részletesebben.
   
    ![](media/service-connect-to-azure-enterprise/params.png)
5. A csatlakozáshoz adja meg a hozzáférési kulcsát. A beléptetési kulcs az Azure EA Portalon található.
   
    ![](media/service-connect-to-azure-enterprise/creds.png)
6. Az importálási folyamat automatikusan megkezdődik. Ha befejeződött, a navigációs panelen megjelenik egy új irányítópult, jelentés és modell. Válassza ki az irányítópultot az importált adatok megtekintéséhez.
   
   ![](media/service-connect-to-azure-enterprise/dashboard.png)

**Mi a következő lépés?**

* [Kérdéseket tehet fel a Q&A mezőben](consumer/end-user-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](consumer/end-user-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

## <a name="whats-included"></a>Tartalom
Az Azure Enterprise-tartalomcsomag havi adatjelentéseket nyújt a kapcsolódási folyamat során megadott hónapok időtartamára. A tartomány változó időintervalluma miatt az adatkészlet frissülésével a benne foglalt adatok is frissülnek.

## <a name="system-requirements"></a>Rendszerkövetelmények
A tartalomcsomag használatához hozzáférés szükséges a Vállalati szolgáltatásokhoz az Azure Portalon.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Paraméterek helye
A Power BI-jelentések készítése olyan közvetlen, partneri és közvetett vállalati szerződéssel rendelkező ügyfelek számára elérhető, akik meg tudják tekinteni a számlázási adatokat. A kapcsolódási folyamathoz szükséges értékek megkereséséről alább tájékozódhat.

**Az Azure-környezet URL-címe**

* Ez általában a https://ea.azure.com, de bejelentkezés után ellenőrizheti a megjelenő URL-címet.
  
    ![](media/service-connect-to-azure-enterprise/params3.png)

**Hónapok száma**

* Egy 1 és 36 közötti szám, amely az importálni kívánt hónapok száma (a mai naptól számítva).

**Beléptetési szám**

* Ez az Azure Enterprise beléptetési száma, amely az [Azure Enterprise Portal](https://ea.azure.com/) kezdőképernyőjén, a „Regisztráció részletei” felületen található.
  
    ![](media/service-connect-to-azure-enterprise/params2.png)

**Hozzáférési kulcs**

* A hozzáférési kulcs az Azure Enterprise portálon a „Használati adatok letöltése” > „API hozzáférési kulcsa” alatt található.
  
    ![](media/service-connect-to-azure-enterprise/creds2.png)

**További segítség**

* Az Azure Enterprise Power BI csomag telepítésével kapcsolatos további segítségért jelentkezzen be az Azure Enterprise Portalra, és tekintse meg az API súgófájlját a „Súgó” felületen, valamint a további utasításokat a Jelentések -> Használati adatok letöltése -> API hozzáférési kulcsa alatt.

## <a name="next-steps"></a>Következő lépések
[Első lépések a Power BI-ban](service-get-started.md)

[Adatok lekérése a Power BI-ban](service-get-data.md)

