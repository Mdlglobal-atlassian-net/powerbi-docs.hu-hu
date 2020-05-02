---
title: fájlbefoglalás
description: fájlbefoglalás
services: powerbi
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 04/28/2020
ms.author: davidi
ms.openlocfilehash: d56988986cfd994bb21c9bc25d024903719472cf
ms.sourcegitcommit: c772c544ce2e1e2a147b9b62e5579ac3cb59d54c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/29/2020
ms.locfileid: "82255854"
---
## <a name="single-sign-on"></a>Egyszeri bejelentkezés

Miután közzétett egy Azure SQL DirectQuery-adathalmazt a szolgáltatásban, engedélyezheti az Azure Active Directory (Azure AD) OAuth2 használatával való egyszeri bejelentkezést (SSO) a végfelhasználók számára.

Az egyszeri bejelentkezés engedélyezéséhez nyissa meg az adathalmaz beállításait, majd az **Adatforrások** lapot, és jelölje be az Egyszeri bejelentkezés jelölőnégyzetet.

![Az Azure SQL DQ konfigurálása párbeszédpanel](media/direct-query-sso/sso-dialog.png)

Ha az egyszeri bejelentkezési beállítás engedélyezve van, és a felhasználók használják az adatforrásra épülő jelentéseket, a Power BI elküldi a hitelesített Azure AD-beli hitelesítő adataikat a lekérdezésekben az Azure SQL Database-adatbázisnak vagy -adattárháznak. Ez a beállítás lehetővé teszi a Power BI számára, hogy figyelembe vegye az adatforrás szintjén konfigurált biztonsági beállításokat.

Az egyszeri bejelentkezési beállítás az adatforrást használó összes adathalmazra érvényes lesz. Az importálási forgatókönyvekhez használt hitelesítési módszerre nincs hatással.

