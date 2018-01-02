---
title: "Alkalmazás regisztrálása az Azure AD-ben"
description: "Útmutató – Adatok küldése adatkészletekbe – Alkalmazás regisztrálása az Azure AD-ben"
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/10/2017
ms.author: asaxton
ms.openlocfilehash: e5c1629ea6b90ec52a3c567916a9f686eb4d1bee
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/15/2017
---
# <a name="step-1-register-an-app-with-azure-ad"></a>1. lépés: Alkalmazás regisztrálása az Azure AD-ben
Ez a cikk az [adatok adatkészletbe történő leküldését](walkthrough-push-data.md) ismertető részletes útmutató része.

Az első lépés az adatok a Power BI-adatkészletekbe való küldése esetén az alkalmazás regisztrálása az Azure AD-ben. Először ezt kell megtennie, hogy rendelkezzen egy **ügyfél-azonosítóval**, amely az Azure AD-ben azonosítja az alkalmazást. **Ügyfél-azonosító** nélkül az Azure AD nem tudja hitelesíteni az alkalmazást.

> **MEGJEGYZÉS:** Mielőtt regisztrálhatna egy alkalmazást a Power BI-ban, [regisztrálnia kell a Power BI-ra](create-an-azure-active-directory-tenant.md).
> 
> 

Az alkalmazások az Azure AD-ben való regisztrálásának lépései a következők.

## <a name="register-an-app-in-azure-ad"></a>Alkalmazás regisztrálása az Azure AD-ben
1. Keresse fel a dev.powerbi.com/apps oldalt.
2. Kattintson a **Bejelentkezés meglévő fiókkal** lehetőségre, és jelentkezzen be a Power BI-fiókjába.
3. Adja meg az **Alkalmazás nevét**, például: „Mintaalkalmazás adatküldéshez”.
4. Az **Alkalmazás típusa** mezőben válassza a **Natív alkalmazás** lehetőséget.
5. Adjon meg egy **Átirányítási URL-címet**, például: **https://login.live.com/oauth20_desktop.srf**. **Natív ügyfél-alkalmazás** esetén az átirányítási URI azonosító révén az **Azure AD** további információkat tud meg az adott alkalmazásról, amelyet hitelesítenie kell. Az ügyfél-alkalmazások standard URI azonosítója: https://login.live.com/oauth20_desktop.srf.
6. Az **Elérendő API-k kiválasztása** alatt válassza **Az összes adatkészlet olvasása és írása** lehetőséget. A Power BI összes alkalmazásengedélyéről további információt találhat a [Power BI-engedélyeket](power-bi-permissions.md) ismertető cikkben.
7. Kattintson az **Alkalmazás regisztrálása** gombra, és mentse az így létrehozott **ügyfél-azonosítót**. Az **ügyfél-azonosító** azonosítja az alkalmazást az Azure AD-ben.

Az **Alkalmazás regisztrálása a Power BI-ban** oldalnak így kell kinéznie:

![](media/walkthrough-push-data-register-app-with-azure-ad/powerbi-developer-sample-register-app.png)

A következő lépés bemutatja, hogyan [szerezhető be a hitelesítési hozzáférési token](walkthrough-push-data-get-token.md).

[Következő lépés >](walkthrough-push-data-get-token.md)

## <a name="next-steps"></a>Következő lépések
[Regisztráció a Power BI-ra](create-an-azure-active-directory-tenant.md)  
[Hitelesítési hozzáférési token beszerzése](walkthrough-push-data-get-token.md)  
[Útmutató: Adatok küldése adatkészletekbe](walkthrough-push-data.md)  
[Egy alkalmazás regisztrálása](register-app.md)  
[A Power BI REST API áttekintése](overview-of-power-bi-rest-api.md)  

További kérdései vannak? [Forduljon a Power BI közösségéhez](http://community.powerbi.com/)

