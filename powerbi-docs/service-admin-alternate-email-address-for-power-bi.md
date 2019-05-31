---
title: Másodlagos e-mail cím használata
description: Másodlagos e-mail cím használata
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/23/2019
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 88432f55fc8cfeefa07b66ea68437bbb23f12531
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "64906658"
---
# <a name="use-an-alternate-email-address"></a>Másodlagos e-mail cím használata

Ha regisztrál a Power BI-ra, meg kell adnia egy e-mail-címet. A Power BI alapértelmezés szerint erre az e-mail-címre küld frissítéseket a szolgáltatásbeli tevékenységeiről. Ha például valaki megosztási felkérést küld Önnek, az erre az e-mail-címre fog megérkezni.

Bizonyos esetekben ezeket az üzeneteket érdemes lehet a regisztrációkor megadott e-mail-cím helyett inkább egy másodlagos e-mail-címre kézbesíttetni. Ez a cikk ismerteti, hogyan adhat meg egy másodlagos e-mail-címet az Office 365-ben és a PowerShell-ben. A cikk azt is bemutatja, hogyan oldja fel az Azure Active Directory (Azure AD) egy e-mail címet.

> [!NOTE]
> A másodlagos e-mail-cím megadása azt nem befolyásolja, hogy a Power BI melyik címre küldi a szolgáltatásfrissítéseket, hírleveleket és más promóciós értesítéseket. Ezek üzeneteket mindig küld az e-mail-cím a Power bi-ra való regisztráció során használt.

## <a name="use-office-365"></a>Az Office 365 használata

Kövesse az alábbi lépéseket másodlagos e-mail-cím megadásához az Office 365-ben.

1. Nyissa meg az [Office 365 Személyi adatok oldalát](https://portal.office.com/account/#personalinfo). Ha az alkalmazás kéri, jelentkezzen be az e-mail címet és a Power bi-hoz használt jelszó.

1. A bal oldali menüben válassza a **Személyi adatok** lehetőséget.

1. A **Kapcsolattartási adatok** szakaszban válassza a **Szerkesztés** elemet.

    Ha nem szerkeszthetők az adatait, ez azt jelenti, az Office 365 rendszergazda felügyeli az e-mail-címét. Forduljon a rendszergazdához, az e-mail cím frissítéséhez.

    ![Kapcsolattartási adatok](media/service-admin-alternate-email-address-for-power-bi/contact-details.png)

1. Az a **másodlagos e-mail cím** mezőbe írja be az Office 365-öt használja a Power BI a frissítéseket szeretné az e-mail-cím.

## <a name="use-powershell"></a>A PowerShell használata

A PowerShellben a [Set-AzureADUser](/powershell/module/azuread/set-azureaduser/) paranccsal adhat meg másodlagos e-mail-címet.

```powershell
Set-AzureADUser -ObjectId john@contoso.com -OtherMails "otheremail@somedomain.com"
```

## <a name="email-address-resolution-in-azure-ad"></a>E-mail-cím feloldása az Azure AD-ben

Rögzítheti az Azure AD beágyazási token Power BI-hoz, három különböző típusú e-mail-címek egyikét használhatja:

* -A felhasználó az Azure AD-fiókjához tartozó fő e-mail-cím

* az egyszerű felhasználónévhez (UPN) tartozó e-mail-cím

* Az *egyéb e-mail-cím* tömbattribútum

A Power BI a következő sorrendben választja ki a használandó e-mail-címet:

1. Ha az Azure AD-bérlő felhasználói objektumának „mail” attribútuma létezik, akkor a Power BI ezt az attribútumot használja e-mail-címként.

1. Ha az UPN-hez tartozó e-mail-cím *nem* **\*.onmicrosoft.com** tartománybeli cím (ez a „\@” jelet követő részből derül ki), akkor a Power BI ezt az attribútumot használja e-mail-címként.

1. Ha a *más e-mail-cím* tömbattribútum az Azure AD felhasználói objektum jelen, akkor a Power BI ebben a listában szereplő első e-mail használja a (mivel ez az attribútum az e-mail-címek listáját is lehet).

1. Ha a fenti feltételek sem található, a Power BI az UPN-cím használja.

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)