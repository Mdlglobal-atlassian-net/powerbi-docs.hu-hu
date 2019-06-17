---
title: fájlbefoglalás
description: fájlbefoglalás
services: powerbi
author: mgblythe
ms.service: powerbi
ms.topic: include
ms.date: 05/31/2019
ms.author: mblythe
ms.openlocfilehash: 94b6959b6bcbf250e54a353e8b725b6c9e5a2e30
ms.sourcegitcommit: c539726c9c180e899a8a34443e3fda2b9848beb2
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66448404"
---
## <a name="single-sign-on"></a>Egyszeri bejelentkezés

Miután közzétett egy Azure SQL DirectQuery-adathalmazt a szolgáltatásban, engedélyezheti az Azure Active Directory (Azure AD) OAuth2 használatával való egyszeri bejelentkezést (SSO) a végfelhasználók számára.

Az egyszeri bejelentkezés engedélyezéséhez nyissa meg az adathalmaz beállításait, majd az **Adatforrások** lapot, és jelölje be az Egyszeri bejelentkezés jelölőnégyzetet.

![Az Azure SQL DQ konfigurálása párbeszédpanel](media/direct-query-sso/sso-dialog.png)

Ha az egyszeri bejelentkezési beállítás engedélyezve van, és a felhasználók használják az adatforrásra épülő jelentéseket, a Power BI elküldi a hitelesített Azure AD-beli hitelesítő adataikat a lekérdezésekben az Azure SQL Database-adatbázisnak vagy -adattárháznak. Ez lehetővé teszi a Power BI számára, hogy figyelembe vegye az adatforrás szintjén konfigurált biztonsági beállításokat.

Az egyszeri bejelentkezési beállítás az adatforrást használó összes adathalmazra érvényes lesz. Az importálási forgatókönyvekhez használt hitelesítési módszerre nincs hatással.

> [!Note]
> Az Azure Multi-Factor Authentication (MFA) nem támogatott. Azokat a felhasználókat, akik egyszeri bejelentkezést kívánnak használni az Azure SQL DirectQueryvel, ki kell vonni az MFA hatálya alól.