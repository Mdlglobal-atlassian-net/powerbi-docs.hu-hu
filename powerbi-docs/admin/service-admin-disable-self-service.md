---
title: Az önkiszolgáló regisztráció és a vásárlás engedélyezése vagy letiltása
description: Útmutató rendszergazdák számára ahhoz, hogyan tilthatják le a felhasználók számára a Power BI-ra való regisztrálást és a licencek megvásárlását.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/08/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 561d8b6cd0e17e885ced984315a04376400a2a58
ms.sourcegitcommit: b2cb0b02bdc451bf11a92a68f2c4d560a811f563
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81447510"
---
# <a name="enable-or-disable-self-service-sign-up-and-purchasing"></a>Az önkiszolgáló regisztráció és a vásárlás engedélyezése vagy letiltása

A legtöbb szervezetben az önkiszolgáló regisztráció alapértelmezés szerint engedélyezve van. A szervezet egyéni felhasználói regisztrálhatnak a Power BI-ra munkahelyi vagy iskolai fiókjukkal. A felhasználóknak arra is lehetősége van, hogy közvetlenül vásároljanak Power BI Pro-licencet, ha olyan funkciót próbálnak használni, amely Pro-licencet igényel. A rendszergazda eldöntheti, hogy engedélyezi vagy letiltja-e az önkiszolgáló regisztrációt. Azt is beállíthatja, hogy a cégen belüli felhasználók önkiszolgáló vásárlás használatával vásárolhatnak-e saját licencet.

> [!NOTE]
>Ha a Power BI-t egy Microsoft felhőszolgáltatótól (CSP-től) szerezte be, előfordulhat, hogy a beállítás le van tiltva, és a felhasználók nem regisztrálhatnak személyesen. Az is lehetséges, hogy a CSP az Ön szervezetének globális rendszergazdája, így ha módosítani szeretné ezt a beállítást, akkor fel kell vennie vele a kapcsolatot.
>
>

PowerShell-parancsokkal módosíthatja az önkiszolgáló regisztrációt és a vásárlást vezérlő beállításokat. Két beállítással szabályozható, hogy a szervezeten belüli felhasználók végezhetnek-e önkiszolgáló regisztrációt vagy önkiszolgáló vásárlást.

- Ha le szeretné tiltani az összes önkiszolgáló regisztrációt, akkor az Azure AD PowerShell-parancsok használatával módosítsa az Azure Active Directory **AllowAdHocSubscriptions** beállítását. A jelen cikkben ismertetett lépéseket követve [engedélyezheti vagy letilthatja az önkiszolgáló regisztrációt](#enable-or-disable-self-service-signup). Ez a lehetőség kikapcsolja az önkiszolgáló regisztrációt a Microsoft *minden* felhőalapú alkalmazására és szolgáltatására.

- Ha meg szeretné akadályozni, hogy a felhasználók saját Pro-licencet vásároljanak, módosítsa az **AllowSelfServicePurchase** beállítást az MSCommerce PowerShell-parancsokkal. Ezzel a beállítással kikapcsolhatja az önkiszolgáló vásárlást adott termékekre vonatkozóan. A jelen cikkben ismertetett lépéseket követve [engedélyezheti vagy letilthatja a Power BI Pro-licencek önkiszolgáló vásárlását](#enable-or-disable-self-service-purchase).

## <a name="enable-or-disable-self-service-signup"></a>Az önkiszolgáló regisztráció engedélyezése vagy letiltása

Ha az önkiszolgáló regisztráció engedélyezve van, akkor az **AllowAdHocSubscriptions** értéke *True* (igaz). Nézzük meg, mi történik, ha a beállítást *false* (hamis) értékre módosítja:

- Ha a beállítást true értékről false értékre módosítja, a cég új felhasználói nem fognak tudni egyénileg regisztrálni. Minden olyan felhasználó, aki a Power BI-ra a módosítás előtt regisztrált, megtartja a licenceit.

- Az (ingyenes) Power BI-licenccel rendelkező felhasználók a false (hamis) beállítás esetén is regisztrálhatnak egyéni Power BI Pro-próbaverzióra.

- A rendszergazdának kell hozzárendelnie az összes Power BI-licencet minden olyan felhasználóhoz, akinek szüksége van rá.

### <a name="before-you-begin"></a>Előkészületek

Ezek a lépések az Azure Active Directory PowerShell-parancsait használják az **AllowAdHocSubscriptions** beállítás értékének megváltoztatásához. A parancsok csak akkor lesznek elérhetők, ha telepítve van az Azure AD PowerShell-modulja. További információ a PowerShellről: [Ismerkedés a Windows PowerShell-lel](https://docs.microsoft.com/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-7).

Az Azure AD-modul telepítéséhez rendszergazdaként indítsa el a Windows PowerShellt. A helyi végrehajtási házirendnek lehetővé kell tennie a parancsfájlok futtatását. Ha problémákat tapasztal, tekintse meg a [PowerShell-végrehajtási házirendeket](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7#powershell-execution-policies), ahol megtudhatja, hogyan módosíthatja a helyi házirendet.

Az Azure AD-modul telepítéséhez futtassa az alábbi parancsot:

```powershell
Install-Module MSOnline
```

### <a name="change-the-self-service-signup-policy"></a>Az önkiszolgáló regisztrációs szabályzat módosítása

Az Azure AD-hez való csatlakozáshoz futtassa a következő parancsot a PowerShellben:

```powershell
Connect-MsolService
```

A bejelentkezési párbeszédpanelen adja meg a rendszergazdai hitelesítő adatait, és végezze el az esetlegesen szükséges többtényezős hitelesítést. Az ellenőrzés után visszakerül a PowerShell-ablakba.

Az aktuális beállítás megtekintéséhez futtassa az alábbi parancsot. A kimenet egy formázott listára kerül, az „fl” kapcsoló használatával.

```powershell
Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
```

Az aktuális beállítás módosításához futtassa a következő parancsot:

```powershell
Set-MsolCompanySettings -AllowAdHocSubscriptions $false
```

A parancs futtatása után az önkiszolgáló regisztráció le lesz tiltva az összes felhasználónál. Ha újra be szeretné kapcsolni, futtassa újra ezt a parancsot, és állítsa be $true értékre.

## <a name="enable-or-disable-self-service-purchase"></a>Az önkiszolgáló vásárlás engedélyezése vagy letiltása

Ha az önkiszolgáló vásárlás engedélyezve van, akkor az **AllowSelfServicePurchase** értéke *true*. Nézzük meg, mi történik, ha a beállítást *false* (hamis) értékre módosítja:

- Ha a beállítást true értékről false értékre módosítja, a cég felhasználói nem fognak tudni saját Power BI Pro-licencet vásárolni. Minden olyan felhasználó, aki a módosítás előtt vásárolt licencet, megtartja a licenceit.

- Az (ingyenes) Power BI-licenccel rendelkező felhasználók a false (hamis) beállítás esetén nem szerezhetnek be egyéni Power BI Pro-licencet. 

- A rendszergazdának kell Pro-licencet hozzárendelnie minden olyan felhasználóhoz, akinek szüksége van rá.

### <a name="before-you-begin"></a>Előkészületek

Ezek a lépések az MSCommerce PowerShell-parancsokat használják az **AllowSelfServicePurchase** beállítás értékének megváltoztatásához. A parancsok csak akkor lesznek elérhetők, ha telepítve van az MSCommerce PowerShell-modul. További információ a PowerShellről: [Ismerkedés a Windows PowerShell-lel](https://docs.microsoft.com/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-7).

Az MSCommerce modul telepítéséhez rendszergazdaként indítsa el a Windows PowerShellt. A helyi végrehajtási házirendnek lehetővé kell tennie a parancsfájlok futtatását. Ha problémákat tapasztal, tekintse meg a [PowerShell-végrehajtási házirendeket](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7#powershell-execution-policies), ahol megtudhatja, hogyan módosíthatja a helyi házirendet.

Futtassa az alábbi parancsot az MSCommerce-modulok telepítéséhez:

```powershell
Install-Module -name MSCommerce
```

### <a name="change-the-self-service-signup-policy"></a>Az önkiszolgáló regisztrációs szabályzat módosítása

A csatlakozáshoz futtassa a következő parancsot a PowerShellben:

```powershell
Connect-MSCommerce
```

A bejelentkezési párbeszédpanelen adja meg a rendszergazdai hitelesítő adatait, és végezze el az esetlegesen szükséges többtényezős hitelesítést. Az ellenőrzés után a PowerShell-ablak sikeres kapcsolatot jelenít meg.

Az aktuális beállítás megtekintéséhez futtassa az alábbi parancsot. A csonkolás elkerülése érdekében a kimenet egy formázott listára kerül, az „fl” kapcsoló használatával.

```powershell
Get-MSCommercePolicy -PolicyId AllowSelfServicePurchase | fl
```

Azt a beállítást, amely lehetővé teszi az önkiszolgáló vásárlást egy adott termékre vonatkozóan, az egyes termékekre vonatkozó **Termékkód** (ProductId) megadásával tilthatja le. A Power BI szolgáltatás aktuális beállításának módosításához futtassa a következő parancsot:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0L3PB -Enabled $False
```

A parancs futtatása után a Power BI önkiszolgáló megvásárlása le lesz tiltva az összes felhasználónál. Ha újra be szeretné kapcsolni, futtassa újra ezt a parancsot, és állítsa be $true értékre.

## <a name="next-steps"></a>Következő lépések

A Power BI önkiszolgáló vásárlásával és a Power Platform többi összetevőjével kapcsolatos további információkért tekintse meg a következő cikkeket:

- [Önkiszolgáló vásárlás – gyakori kérdések](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/self-service-purchase-faq?view=o365-worldwide#admin-capabilities)
- [Az AllowSelfServicePurchase használata az MSCommerce PowerShell-modulhoz](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell?view=o365-worldwide)
