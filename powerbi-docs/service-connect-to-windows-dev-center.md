---
title: Kapcsolódás a Windows fejlesztői központhoz a Power BI-jal
description: Windows fejlesztői központ a Power BI-hoz
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 81498dff9c70deaf8135faf244db96509b1cf18d
ms.sourcegitcommit: 750f0bfab02af24c8c72e6e9bbdd876e4a7399de
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/04/2019
ms.locfileid: "54008833"
---
# <a name="connect-to-windows-dev-center-with-power-bi"></a>Kapcsolódás a Windows fejlesztői központhoz a Power BI-jal
A Power BI-tartalomcsomag használatával a Power BI-ban vizsgálhatja és figyelheti a Windows fejlesztői központ alkalmazáselemzési adatait. Az adatok naponta egyszer automatikusan frissülnek.

Kapcsolódjon a [Windows fejlesztői központ Power BI-tartalomcsomagjához](https://app.powerbi.com/getdata/services/devcenter).

## <a name="how-to-connect"></a>A kapcsolódás menete
1. A bal oldali navigációs ablaktábla alján kattintson az **Adatok lekérése** elemre.
   
   ![](media/service-connect-to-windows-dev-center/getdata.png)
2. A **Szolgáltatások** mezőben válassza a **Beolvasás** elemet.
   
   ![](media/service-connect-to-windows-dev-center/services.png)
3. Válassza a **Windows fejlesztői központ** \> **Beolvasás** lehetőséget.
   
   ![](media/service-connect-to-windows-dev-center/windowsdev.png)
4. Adja meg egy, a tulajdonában lévő alkalmazás azonosítóját és kattintson a Következő gombra. A [paraméterek megkereséséről](#FindingParams) alább olvashat részletesebben.
   
   ![](media/service-connect-to-windows-dev-center/params.png)
5. A **Hitelesítési módszer** beállításnál válassza az **oAuth2** \> **Bejelentkezés** elemet. Amikor a rendszer kéri, adja meg a Windows fejlesztői központ-fiókjához tartozó Azure Active Directory-hitelesítő adatokat (további részletek a [Rendszerkövetelmények](#Requirements) között).
   
    ![](media/service-connect-to-windows-dev-center/creds.png)
   
    ![](media/service-connect-to-windows-dev-center/creds2.png)
6. A jóváhagyás után az importálás automatikusan megkezdődik. Amikor befejeződik, új irányítópult, jelentés és modell jelenik meg a navigációs panelen. Válassza ki az irányítópultot az importált adatok megtekintéséhez, majd nyissa meg az alapul szolgáló jelentéseket egy csempe választásával.
   
    ![](media/service-connect-to-windows-dev-center/dashboard.png)
   
    ![](media/service-connect-to-windows-dev-center/report.png)

**Hogyan tovább?**

* [Kérdéseket tehet fel a Q&A mezőben](consumer/end-user-q-and-a.md) az irányítópult tetején.
* [Módosíthatja az irányítópult csempéit](service-dashboard-edit-tile.md).
* [Kiválaszthatja valamelyik csempét](consumer/end-user-tiles.md) a mögöttes jelentés megnyitásához.
* Noha az adatkészlet napi frissítésre van ütemezve, módosíthatja a frissítési ütemezést, vagy igény szerint frissíthet az **Azonnali frissítés** gombbal.

## <a name="whats-included"></a>Tartalom
A fejlesztői központ Power BI-tartalomcsomag az alkalmazása elemzési adatait és IAP-beszerzéseit, minősítéseit, értékeléseit, és az alkalmazás állapotát tartalmazza. Az adatok csak az utolsó 3 hónapra terjednek ki. Az időintervallum változik, a dátumok az adatkészlet frissítésekor módosulnak.

<a name="Requirements"></a>

## <a name="system-requirements"></a>Rendszerkövetelmények
Ez a tartalomcsomag megkövetel legalább egy, a Windows Áruházban közzétett alkalmazást és egy Windows fejlesztői központ-fiókot (további részletek [itt](https://msdn.microsoft.com/windows/uwp/publish/manage-account-users)).

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Paraméterek keresése
Egy alkalmazás azonosítóját az Alkalmazáskezelés alatti Alkalmazásidentitás lap megnyitásával találhatja meg.

Az alkalmazás azonosítója a Windows 10 Áruházbeli URL-cím végén található (https://www.microsoft.com/store/apps/ **{alkalmazásazonosító}**)

## <a name="next-steps"></a>Következő lépések
[Első lépések a Power BI-ban](service-get-started.md)

[Adatok lekérése a Power BI-ban](service-get-data.md)

