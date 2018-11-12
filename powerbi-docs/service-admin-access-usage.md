---
title: Bejelentkezett Power BI-felhasználók keresése
description: Ha Ön egy bérlői rendszergazda, és szeretné megtekinteni a Power BI-ba bejelentkezett felhasználók listáját, használhatja ehhez az Azure Active Directory hozzáférési és használati jelentéseit.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 10/31/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: dfd9aab419d0a097721c4f2b49e382c11be82541
ms.sourcegitcommit: 0611860a896e636ceeb6e30ce85243bfd8e7b61d
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/01/2018
ms.locfileid: "50909502"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>Bejelentkezett Power BI-felhasználók keresése

Ha Ön bérlői rendszergazda, és szeretné megtekinteni a Power BI-ba bejelentkezett felhasználók listáját, használja ehhez az [Azure Active Directory hozzáférési és használati jelentéseit](/azure/active-directory/reports-monitoring/concept-sign-ins).

<iframe width="640" height="360" src="https://www.youtube.com/embed/1AVgh9w9VM8?showinfo=0" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> A tevékenységjelentés fontos információkat közöl, de azt nem jelzi, hogy az egyes felhasználók milyen licenccel rendelkeznek. A licencek megtekintéséhez az Office 365 felügyeleti központját használhatja.

## <a name="requirements"></a>Követelmények

A saját bejelentkezéseit bármely felhasználó (nem rendszergazda is) megtekintheti, de az összes felhasználóra vonatkozó jelentés megtekintése csak a következő feltételekkel lehetséges.

* A bérlőnek Prémium szintű Microsoft Azure AD-licenccel kell rendelkeznie.

* A felhasználónak a következő szerepkörök egyikével kell rendelkeznie: globális rendszergazda, biztonsági rendszergazda, biztonsági olvasó.

## <a name="use-the-azure-portal-to-view-sign-ins"></a>Bejelentkezések megtekintése az Azure-portállal

A bejelentkezési tevékenység megtekintéséhez kövesse az alábbi lépéseket.

1. Az **Azure Portalon** válassza az **Azure Active Directory** lehetőséget.

1. A **Figyelés** területen kattintson a **Bejelentkezések** elemre.
   
    ![Azure AD-bejelentkezések](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. Szűrjön a kívánt alkalmazásra a **Microsoft Power BI** vagy a **Power BI Gateway** lehetőség választásával, majd kattintson az **Alkalmaz** elemre.

    A **Microsoft Power BI** lehetőség a szolgáltatáshoz kapcsolódó bejelentkezési tevékenységekre, a **Power BI Gateway** a Helyszíni adatátjáróhoz kapcsolódó bejelentkezési adatokra szűr.
   
    ![Bejelentkezések szűrése](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>Az adatok exportálása

A bejelentkezési adatokat kétféleképpen exportálhatja: CSV-fájl letöltésével vagy a PowerShell használatával. A bejelentkezési jelentés tetején válasszon az alábbi két lehetőség közül:

* **Letöltés**, ha CSV-fájlt szeretne letölteni a jelenleg szűrt adatokhoz.

* **Parancsfájl**, ha PowerShell-parancsfájlt szeretne letölteni a jelenleg szűrt adatokhoz. A parancsfájlban szükség szerint frissítheti a szűrőt.

![CSV-fájl vagy parancsfájl letöltése](media/service-admin-access-usage/download-sign-in-data-csv.png)

## <a name="data-retention"></a>Adatmegőrzés

A bejelentkezéshez kapcsolódó adatok legfeljebb 30 napig érhetők el. Bővebb információt az [Azure Active Directory-jelentések adatmegőrzési szabályzatában](/azure/active-directory/reports-monitoring/reference-reports-data-retention) találhat.

## <a name="next-steps"></a>Következő lépések

[Naplózás használata a cégnél](service-admin-auditing.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

