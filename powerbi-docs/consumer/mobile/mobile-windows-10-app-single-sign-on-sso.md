---
title: Egyszeri bejelentkezés használata a windowsos Power BI mobilalkalmazásban
description: További információ az egyszeri bejelentkezés (SSO) használatáról a windowsos Power BI mobilalkalmazásban. Az egyszeri bejelentkezéssel mindössze egyetlen bejelentkezéssel és egyetlen felhasználói fiókkal elérheti az üzleti tevékenységeihez szükséges összes alkalmazást és erőforrást.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: painbar
ms.openlocfilehash: 767ea586ce35d60c99742ada6f90fe342bd59313
ms.sourcegitcommit: 480bba9c745cb9af2005637e693c5714b3c64a8a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/11/2020
ms.locfileid: "79114719"
---
# <a name="single-sign-on-in-the-power-bi-mobile-windows-app"></a>Egyszeri bejelentkezés használata a windowsos Power BI mobilalkalmazásban

További információ az egyszeri bejelentkezés (SSO) használatáról a windowsos Power BI mobilalkalmazásban. Az egyszeri bejelentkezéssel mindössze egyetlen bejelentkezéssel és egyetlen felhasználói fiókkal elérheti az üzleti tevékenységeihez szükséges összes alkalmazást és erőforrást. A bejelentkezést követően az összes alkalmazáshoz hozzáférhet anélkül, hogy ismét hitelesítenie kellene magát. 

Mivel a Power BI Windows-alkalmazás integrálva van az Azure Active Directoryba, az elsődleges szervezeti fiókját a tartományhoz csatlakozott eszközökbe való bejelentkezésen kívül a Power BI szolgáltatásba való bejelentkezésre is használhatja. Amennyiben a Power BI-t egy windowsos telefonon használja, győződjön meg arról, hogy a Power BI munkahelyi vagy iskolai fiókként van beállítva az eszközbeállításokban.  

Az SSO használata csak a Microsoft Azure Active Directory által felügyelt windowsos eszközökön használható. 

## <a name="sign-in-with-sso"></a>Bejelentkezés SSO-val

A bejelentkezési folyamat egyszerűsítése érdekében az alkalmazás első telepítésekor az alkalmazás automatikusan megpróbálja hitelesíteni a Power BI szolgáltatásban az SSO-val. Az alkalmazás csak abban az esetben kéri a Power BI-hitelesítőadatok megadását, ha ez a folyamat sikertelen volt.  

Amennyiben már a windowsos Power BI mobilalkalmazást használja, az alkalmazás új verziójára történő frissítéskor az SSO-t is használhatja. Jelentkezzen ki az alkalmazásból, zárja be, majd nyissa meg újra. Amikor ismét megnyílik az alkalmazás, automatikusan az aktuális windowsos hitelesítő adataival próbálja meg hitelesíteni a Power BI szolgáltatásban. 

Ha nem az aktív windowsos munkamenet hitelesítő adataival kíván bejelentkezni a Power BI-ba, a **Beállítások** lapon jelentkezzen ki, majd jelentkezzen be eltérő hitelesítő adatokkal. 
 
## <a name="next-steps"></a>Következő lépések

- [A Windows 10-hez készült Power BI mobilalkalmazás használatának első lépései](mobile-windows-10-phone-app-get-started.md)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

