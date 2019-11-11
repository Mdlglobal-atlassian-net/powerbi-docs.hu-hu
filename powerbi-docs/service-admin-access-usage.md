---
title: Bejelentkezett Power BI-felhasználók keresése
description: Ha Ön bérlői rendszergazda, és szeretné megtekinteni a Power BI-ba bejelentkezett felhasználók listáját, használhatja ehhez az Azure Active Directory hozzáférési és használati jelentéseit.
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 63257953b89a6c96ce451783193656f9dfacf5bd
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73873754"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>Bejelentkezett Power BI-felhasználók keresése

Ha Ön bérlői rendszergazda, és szeretné megtekinteni a Power BI-ba bejelentkezett felhasználók listáját, használja ehhez az [Azure Active Directory hozzáférési és használati jelentéseit](/azure/active-directory/reports-monitoring/concept-sign-ins).

> [!NOTE]
> A **Bejelentkezések** jelentés fontos információkat közöl, de azt nem jelzi, hogy az egyes felhasználók milyen licenccel rendelkeznek. A licencek megtekintésére a Microsoft 365 Felügyeleti központját használhatja.

## <a name="requirements"></a>Követelmények

A saját bejelentkezéseit bármely felhasználó (nem rendszergazda is) megtekintheti, de az összes felhasználóra vonatkozó jelentés megtekintése csak a következő feltételekkel lehetséges.

* A bérlőnek prémium szintű Microsoft Azure Active Directory-licenccel kell rendelkeznie.

* A következő szerepkörök egyikével kell rendelkeznie: Globális rendszergazda, biztonsági rendszergazda, biztonsági olvasó.

## <a name="use-the-azure-portal-to-view-sign-ins"></a>Bejelentkezések megtekintése az Azure-portállal

A bejelentkezési tevékenység megtekintéséhez kövesse az alábbi lépéseket.

1. Az **Azure Portalon** válassza az **Azure Active Directory** lehetőséget.

1. A **Figyelés** területen kattintson a **Bejelentkezések** elemre.
   
    ![Az Azure felhasználói felületének képernyőképe az Azure Active Directory és a Bejelentkezések beállítások kiemelésével.](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. Szűrjön a kívánt alkalmazásra a **Microsoft Power BI** vagy a **Power BI Gateway** lehetőség választásával, majd kattintson az **Alkalmaz** elemre.

    A **Microsoft Power BI** lehetőség a szolgáltatáshoz kapcsolódó bejelentkezési tevékenységekre, a **Power BI Gateway** a helyszíni adatátjáróhoz kapcsolódó bejelentkezési adatokra szűr.
   
    ![A Bejelentkezések szűrő képernyőképe az Alkalmazások mező kiemelésével.](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>Az adatok exportálása

A [bejelentkezési jelentés letöltése](/azure/active-directory/reports-monitoring/quickstart-download-sign-in-report) két formátumban lehetséges: CSV-fájlként vagy JSON-fájlként.

![A letöltés gomb képernyőképe.](media/service-admin-access-usage/download-sign-in-data-csv.png)

A **Bejelentkezések** jelentés felső részén válassza a **Letöltés** lehetőséget, majd az alábbi két lehetőség egyikét:

* **CSV**, ha CSV-fájlként szeretné letölteni a jelenleg szűrt adatokat.

* **JSON**, ha JSON-fájlként szeretné letölteni a jelenleg szűrt adatokat.

## <a name="data-retention"></a>Adatmegőrzés

A bejelentkezéshez kapcsolódó adatok legfeljebb 30 napig érhetők el. Bővebb információt az [Azure Active Directory-jelentések adatmegőrzési szabályzatában](/azure/active-directory/reports-monitoring/reference-reports-data-retention) találhat.

## <a name="next-steps"></a>Következő lépések

[Naplózás használata a cégnél](service-admin-auditing.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)