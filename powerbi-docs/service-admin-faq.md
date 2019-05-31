---
title: A Power BI felügyelete – gyakori kérdések (GYIK)
description: Ismerje meg, a Power bi-ban regisztráció, bérlő felügyeleti és egyéb felügyeleti feladatok gyakori kérdésekre adott válaszokat.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 2e51017333a940bd9d7838e6a903c1a66ce2e342
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100782"
---
# <a name="administering-power-bi---frequently-asked-questions-faq"></a>A Power BI felügyelete – gyakori kérdések (GYIK)

A cikk a Power BI felügyeletével kapcsolatos gyakori kérdéseket ismerteti. A Power BI felügyeletének áttekintését a [Mi a Power BI-felügyelet?](service-admin-administering-power-bi-in-your-organization.md) című cikkben találja meg.

## <a name="whats-in-this-article"></a>A cikk tartalma

### <a name="sign-up-for-power-bi-section"></a>Regisztráció a Power BI-ra szakasz

* [A PowerShell használata](#using-powershell)
* [Hogyan regisztrálnak a felhasználók a Power BI-ra?](#how-do-users-sign-up-for-power-bi)
* [Hogyan regisztrálnak a cég egyéni felhasználói?](#how-do-individual-users-in-my-organization-sign-up)
* [Hogyan gátolható meg, hogy a felhasználók csatlakozzanak a meglévő Office 365-bérlőhöz?](#how-can-i-prevent-users-from-joining-my-existing-office-365-tenant)
* [Hogyan engedélyezhető, hogy a felhasználók csatlakozzanak a meglévő Office 365-bérlőhöz?](#how-can-i-allow-users-to-join-my-existing-office-365-tenant)
* [Hogyan ellenőrizhető, ha van a letiltása bérlőben?](#how-do-i-check-if-i-have-the-block-on-in-the-tenant)
* [Hogyan gátolható meg, hogy a meglévő felhasználók elkezdjék használni a Power BI-t?](#how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi)
* [Hogyan engedélyezhető, hogy a meglévő felhasználók regisztráljanak a Power BI-ra?](#how-can-i-allow-my-existing-users-to-sign-up-for-power-bi)

### <a name="administration-of-power-bi-section"></a>A Power BI felügyelete szakasz

* [Hogyan változtatja meg a Power BI használata a felhasználók identitásának kezelését a cégen belül?](#how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today)
* [Hogyan lehet kezelni a Power BI-t?](#how-do-we-manage-power-bi)
* [Mi a Microsoft által a felhasználók számára létrehozott bérlők kezelésének folyamata?](#what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users)
* [Ha több tartományom van, szabályozható, hogy a felhasználók hozzáadják az Office 365-bérlőhöz?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to)
* [Hogyan távolítható el a Power BI a már regisztrált felhasználóktól?](#how-do-i-remove-power-bi-for-users-that-already-signed-up)
* [Honnan szerzek arról tudomást, ha új felhasználók csatlakoztak a bérlőhöz?](#how-do-i-know-when-new-users-have-joined-my-tenant)
* [Vannak-e bármilyen további dolgot kell előkészítése?](#are-there-any-additional-things-i-should-prepare-for)
* [Hol található a Power BI-bérlőm?](#where-is-my-power-bi-tenant-located)
* [A Power BI SLA (szolgáltatásiszint-szerződés)](#what-is-the-power-bi-sla)
* [Hogyan kezeli a Power BI a magas rendelkezésre állást és a feladatátvételt?](#how-does-power-bi-handle-high-availability-and-failover)

### <a name="security-in-power-bi-section"></a>Biztonság a Power BI-ban szakasz

* [Eleget tesz a Power BI az országos, regionális, illetve iparágra jellemző megfelelőségi követelményeknek?](#does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements)
* [Hogyan működik a biztonság a Power BI-ban?](#how-does-security-work-in-power-bi)

## <a name="sign-up-for-power-bi"></a>Regisztráció a Power BI-ra

### <a name="using-powershell"></a>A PowerShell használata

A szakasz egyes folyamataihoz Windows PowerShell-szkriptek szükségesek. Ha még nem jártas a PowerShellben, tekintse meg a [PowerShell használatának első lépéseit ismertető útmutatót](http://go.microsoft.com/fwlink/p/?LinkID=286814). A szkriptek futtatásához telepítse az [Azure Active Directory PowerShell for Graph](/powershell/azure/active-directory/) legújabb, 64 bites verzióját.

### <a name="how-do-users-sign-up-for-power-bi"></a>Hogyan regisztrálnak a felhasználók a Power BI-ra?

Rendszergazdaként Ön regisztrálhat a Power BI-hoz a [Power BI webhelyén](https://powerbi.microsoft.com) vagy a [szolgáltatások vásárlása](https://admin.microsoft.com/AdminPortal/Home#/catalog) foglalkozó oldal a Microsoft 365 felügyeleti központban. Amikor egy rendszergazda regisztrál a Power bi-ban, a felhasználók számára, akik hozzáférhetnek a felhasználói licencek rendeljen.

A cég egyes felhasználói külön-külön is regisztrálhatnak a [Power BI webhelyen](https://powerbi.microsoft.com) a Power BI-ra. Ha a szervezet egy felhasználója regisztrál a Power bi-ban, a szolgáltatás automatikusan hozzárendeli egy Power BI-licenc a felhasználó. További információ: [való regisztráláskor a Power bi-bA](service-self-service-signup-for-power-bi.md) és [Power bi-ban a szervezet licencelési](service-admin-licensing-organization.md).

### <a name="how-do-individual-users-in-my-organization-sign-up"></a>Hogyan regisztrálnak a cég egyéni felhasználói?

Három forgatókönyv vonatkozhat a cégen belüli felhasználókra:

* **1. forgatókönyv**: A cég már rendelkezik egy meglévő Office 365-környezettel, és a Power BI-ra regisztráló felhasználónak már van Office 365-fiókja.
    Az ebben az esetben, ha a felhasználó már rendelkezik munkahelyi vagy iskolai fiókkal a bérlőben (például contoso.com) azonban még nem rendelkezik Power bi-ban a Microsoft egyszerűen aktiválja a csomagot a fiókhoz. A felhasználó pedig automatikus értesítést kap az adatok a Power BI szolgáltatás használatával.

* **2. forgatókönyv**: A cég már rendelkezik egy meglévő Office 365-környezettel, de a Power BI-ra regisztráló felhasználónak nincs Office 365-fiókja.
    Ebben a forgatókönyvben a felhasználó e-mail-címmel rendelkezik a szervezet tartományban (például contoso.com), de még nem rendelkezik Office 365-fiókkal. Ebben az esetben a felhasználó regisztrálhat a Power BI-ra, és automatikusan kap egy fiókot, Ez a művelet lehetővé teszi, hogy a felhasználó hozzáférését a Power BI szolgáltatásban. Például ha egy Nancy nevű alkalmazott használja a munkahelyi e-mail-címét (például nancy@contoso.com) szeretne regisztrálni, a Microsoft automatikus felveszi Emíliát felhasználóként a Contoso Office 365-környezettel és aktiválja a Power bi-ban az adott fiókhoz.

* **3. forgatókönyv**: A szervezete nem rendelkezik az Office 365-környezettel, az e-mail-tartományhoz csatlakozik.
    Nincsenek nem kell adminisztratív műveleteket kihasználásához a Power bi-ban a szervezet számára szükséges. A szolgáltatás hozzáadja a felhasználókat egy új, csak felhőalapú felhasználói könyvtárba. Azt is beállíthatja számára a bérlői rendszergazda szerepét és kezelni őket.

> [!IMPORTANT]
> Ha a cég több e-mail-tartománnyal rendelkezik, és azt szeretné, hogy az összes e-mail-cím bővítmény ugyanabban a bérlőben legyen, adja az e-mail-címek összes tartományát egy Azure Active Directory-bérlőhöz, mielőtt bármelyik felhasználó regisztrálna. Miután létrehozta a felhasználók, nincs nincs automatizált mechanizmus, amellyel a felhasználók bérlők közötti mozgatásához. Ezen folyamatról további információ: [Ha több tartományom van, felügyelhetem az Office 365-bérlőhöz, hogy a felhasználók hozzáadódnak?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to) a cikk későbbi részében és [tartomány hozzáadása az Office 365](/office365/admin/setup/add-domain/).

### <a name="how-can-i-prevent-users-from-joining-my-existing-office-365-tenant"></a>Hogyan gátolható meg, hogy a felhasználók csatlakozzanak a meglévő Office 365-bérlőhöz?

Rendszergazdaként tehet olyan lépéseket, amelyek meggátolják, hogy a felhasználók csatlakozzanak a meglévő Office 365-bérlőhöz. Ha letiltja a hozzáférést, a kísérletek sikertelenek lesznek, regisztráljon, és megjelenik egy üzenet, amely szólítja fel őket kapcsolatba a cég rendszergazdájával. Nem kell ismételje meg ezt a folyamatot, ha már letiltotta az automatikus licenckiosztást (például a diákoknak, oktatóknak és munkatársaknak for Education az Office 365).

A következő PowerShell-paranccsal meggátolhatja, hogy az új felhasználók a felügyelt bérlőhöz csatlakozzanak. ([További információ a PowerShellről][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $false
```

> [!NOTE]
> A hozzáférés letiltása meggátolja, hogy a cég lévő új felhasználói regisztráljanak a Power BI-ra. Azon felhasználók licence, akik a vállalat új regisztrációinak letiltása előtt regisztráltak a Power BI-ra, továbbra is megmarad. Felhasználó eltávolításához tekintse meg a cikk [Hogyan távolítható el a Power BI a már regisztrált felhasználóktól?](#how-do-i-remove-power-bi-for-users-that-already-signed-up) című szakaszát.

### <a name="how-can-i-allow-users-to-join-my-existing-office-365-tenant"></a>Hogyan engedélyezhető, hogy a felhasználók csatlakozzanak a meglévő Office 365-bérlőhöz?

A következő PowerShell-parancsfájl használatával lehetővé teszik az új felhasználók csatlakozzanak egy felügyelt bérlőhöz. ([További információ a PowerShellről][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $true
```

### <a name="how-do-i-check-if-i-have-the-block-on-in-the-tenant"></a>Hogyan ellenőrizhető, ha van a letiltása bérlőben?

A következő PowerShell-parancsfájl használatával ellenőrizze a beállításokat. Az *AllowEmailVerifiedUsers* értékének hamisnak kell lennie. ([További információ a PowerShellről][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Get-MsolCompanyInformation | fl allow*
```

### <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>Hogyan gátolható meg, hogy a meglévő felhasználók elkezdjék használni a Power BI-t?

A jelen **AllowAdHocSubscriptions** paramétert vezérlő Azure AD-beállítás. A legtöbb bérlő kell ezt a beállítást igaz értékre, ami azt jelenti, hogy engedélyezve van. Ha egy partneren keresztül szerezte be a Power bi-ban, ez FALSE, ami azt jelenti, hogy az le van tiltva lehet beállítani.

Az alkalmi előfizetések letiltásához használja a következő PowerShell-szkriptet. ([További információ a PowerShellről][1].)

1. Jelentkezzen be az Azure Active Directoryba az Office 365 hitelesítő adataival. Az alábbi PowerShell-szkript első sora bekéri a hitelesítő adatokat. A második sor csatlakozik az Azure Active Directoryhoz.

    ```powershell
     $msolcred = get-credential
     connect-msolservice -credential $msolcred
    ```

   ![Képernyőkép az Azure Active Directory jelentkezzen be a PowerShell-lel](media/service-admin-licensing-organization/azure-ad-sign-in.png)

1. Egyszeri bejelentkezés megtekintéséhez a bérlőben jelenleg beállítására a következő parancsot.

    ```powershell
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
    ```

1. Futtassa a következő parancsot az engedélyezéséhez (`$true`) vagy letiltása (`$false`) **AllowAdHocSubscriptions**.

    ```powershell
     Set-MsolCompanySettings -AllowAdHocSubscriptions $false
    ```

> [!NOTE]
> Használja a **AllowAdHocSubscriptions** jelző szabályozhatja a szervezete számára, beleértve a felhasználók számára, hogy regisztráljon az Azure Rights Management szolgáltatás számos felhasználói képessége. A jelölő módosítása az összes képességre hatással van.

### <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>Hogyan engedélyezhető, hogy a meglévő felhasználók regisztráljanak a Power BI-ra?

Lehetővé teszi a meglévő felhasználók Feliratkozás a Power bi-ban, futtassa a parancsot az előző kérdésnél felsorolt azonban át `$true` helyett `$false` az előző lépésben.

## <a name="administration-of-power-bi"></a>A Power BI felügyelete

### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>Hogyan változtatja meg a Power BI használata a felhasználók identitásának kezelését a cégen belül?

Három forgatókönyv vonatkozhat a cégen belüli felhasználókra:

* **1. forgatókönyv**: Ha a szervezet már rendelkezik meglévő Office 365-környezettel, és a a szervezet minden felhasználójának van Office 365-fiókja, nem történik változás az identitások kezelése.

* **2. forgatókönyv**: Ha a szervezet már rendelkezik meglévő Office 365-környezettel, de a szervezet nem minden felhasználó rendelkezik Office 365-fiókja, hogy hozzon létre egy felhasználót a bérlőben, és hozzárendelheti a licenceket a felhasználó munkahelyi vagy iskolai e-mail-cím alapján.

    Ennek eredményeképpen az adott időpontban kezelése felhasználók számát igényével együtt növekszik a szervezet felhasználói iratkozzon fel a szolgáltatásra.

* **3. forgatókönyv**: Ha a szervezet nem rendelkezik az Office 365-környezettel, az e-mail-tartományhoz csatlakozik, nem történik változás az identitások kezelése.

    A szolgáltatás hozzáadja a felhasználókat egy új, csak felhőalapú felhasználói könyvtárba. Emellett kiválaszthatja számára a bérlői rendszergazda szerepét és kezelni őket.

### <a name="how-do-we-manage-power-bi"></a>Hogyan lehet kezelni a Power BI-t?

A Power BI olyan rendszergazdai portált, amely lehetővé teszi, hogy megtekintse kihasználtságának statisztikai adatai, egy hivatkozást kínál a felhasználók és csoportok felügyeletére, a Microsoft 365 felügyeleti központban, és lehetővé teszi a bérlői szintű beállításainak kezeléséhez nyújt.

Szeretné használni a Power BI felügyeleti portálján, a fiókjába kell megjelölni egy **globális rendszergazdai** Office 365 vagy Azure Active Directoryban, vagy egy hozzá kell rendelnie a Power BI szolgáltatás rendszergazdai szerepkörét az felhasználói fiókhoz. További információ: [a Power BI rendszergazdai szerepkörét ismertető](service-admin-role.md) és [Power BI felügyeleti portál](service-admin-portal.md).

### <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>Mi a Microsoft által a felhasználók számára létrehozott bérlők kezelésének folyamata?

Amikor egy önkiszolgáló felhasználó regisztrál a szolgáltatásra egy felhőszolgáltatás, amely az Azure AD, a szolgáltatás hozzáadja őket egy nem felügyelt Azure AD-címtár e-mail-címe alapján. Igényelheti és kezelheti a bérlőt valaki létrehozott néven ismert folyamat segítségével egy *alá vonhatja rendszergazdai átvétellel*. Az átvétel mégis típusa attól függ, hogy van-e egy meglévő felügyelt tartományához társított tenant:

* Új felügyelt bérlő tartományhoz történő létrehozásához használjon *belső átvételt*.

* Használjon *külső átvételt* a tartománynak egy meglévő felügyelt bérlőbe történő áthelyezésére.

További információ: [rendszergazdaként az Azure Active Directoryban egy nem felügyelt könyvtár átvétele](/azure/active-directory/users-groups-roles/domains-admin-takeover).

Amikor ezt teszi, hogy egy külső átvételt, a szolgáltatás helyezi el a Power BI tartalom, amely az átvétel a korábban jött létre a [a Power BI archivált munkaterülete](service-admin-power-bi-archived-workspace.md). Minden tartalmat manuálisan kell áttelepítenie, amelyet az új bérlőben szeretne használni.

### <a name="if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to"></a>Ha több tartományom van, szabályozható, hogy a felhasználók hozzáadják az Office 365-bérlőhöz?

If you do nothing, the service creates a tenant for each user email domain and subdomain. Ha azt szeretné, hogy az e-mail-cím bővítményétől függetlenül mindegyik felhasználó ugyanabban a bérlőben legyen: Hozzon létre egy célbérlőt, vagy használjon egy meglévő bérlőt. Majd adja hozzá az összes meglévő tartományt és altartományt, amelyet szeretne a bérlőben. Minden felhasználó automatikusan az ezekre a tartományokra vagy altartományokra végződő e-mail-címekkel csatlakozik a, amikor regisztrál.

> [!IMPORTANT]
> Miután létrehozta a felhasználók, nincs nincs támogatott automatizált mechanizmus, amellyel a felhasználók bérlők közötti mozgatásához. A tartományok egyetlen Office 365-bérlőhöz való hozzáadásáról a [felhasználók és tartományok Office 365 szolgáltatáshoz adásával](/office365/admin/setup/add-domain/) kapcsolatos témakörben olvashat.

### <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>Hogyan távolítható el a Power BI a már regisztrált felhasználóktól?

Ha egy felhasználó regisztrált a Power BI-ra, de Ön már nem szeretné, hogy hozzáférjen a Power BI-hoz, eltávolíthatja a felhasználó Power BI-licencét.

1. A [Microsoft 365 Felügyeleti központ](https://admin.microsoft.com/AdminPortal/Home#/homepage) megnyitása.

1. A bal oldali navigációs sávban válassza a **Felhasználók** > **Aktív felhasználók** lehetőséget.

1. Keresse meg azt a felhasználót, akinek el szeretné távolítani a licencét, majd válassza ki a nevét.

    A felhasználók kötegelt licenckezelését is elvégezheti. Ehhez válasszon ki több felhasználót, és válassza a **Terméklicencek szerkesztése** lehetőséget.

1. A Felhasználó adatai lap **Terméklicencek** szakasza mellett válassza a **Szerkesztés** lehetőséget.

1. Attól függően, milyen licenc, alkalmazva a fiókra, és állítsa **Power BI (ingyenes)** vagy **Power BI Pro** való **ki**.

1. Kattintson a **Mentés** gombra.

### <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>Honnan szerzek arról tudomást, ha új felhasználók csatlakoztak a bérlőhöz?

Ez a program részeként a bérlőhöz csatlakozó felhasználókhoz egyedi licenc, amely be szűrhet a felügyeleti Irányítópult aktív felhasználó panelén lesznek hozzárendelve. Az új nézet létrehozásához kövesse az alábbi lépéseket.

1. A [Microsoft 365 Felügyeleti központ](https://admin.microsoft.com/AdminPortal/Home#/homepage) megnyitása.

1. A bal oldali navigációs sávban válassza a **Felhasználók** > **Aktív felhasználók** lehetőséget.

1. A **Nézetek** menüben válassza az **Egyéni nézet hozzáadása** lehetőséget.

1. Nevezze el az új nézetet, és a **Hozzárendelt terméklicenc** területen válassza a **Power BI (ingyenes)** vagy a **Power BI Pro** lehetőséget.

    Egy nézethez csak egy licencet választhat ki. Ha **Power BI (ingyenes)** és **Power BI Pro** licencek is vannak a vállalatában, két nézetet is létrehozhat.

1. Adjon meg további kívánt feltételeket, majd válassza a **Hozzáadás** lehetőséget.

1. Miután létrehozta az új nézetet, akkor érhető el a **nézetek** menü.

### <a name="are-there-any-additional-things-i-should-prepare-for"></a>Vannak-e bármilyen további dolgot kell előkészítése?

Az új jelszavak létrehozásával kapcsolatos kérések növekedését tapasztalhatja. További információ erről a folyamatról: [a jelszó alaphelyzetbe állítása](/office365/admin/add-users/reset-passwords).

A Microsoft 365 Felügyeleti központban a szokásos eljárással távolíthat el felhasználókat a bérlőből. Ha azonban egy felhasználónak még mindig a vállalattól származó e-mail-címe van, újra tud csatlakozni, amíg le nem tiltja az összes felhasználó csatlakozását.

### <a name="where-is-my-power-bi-tenant-located"></a>Hol található a Power BI-bérlőm?

Melyik adatterület kapcsolatos a Power BI-bérlője, az információ: [hol található a Power BI-bérlőm?](service-admin-where-is-my-tenant-located.md).

### <a name="what-is-the-power-bi-sla"></a>Mi az a Power BI SLA?

A Power BI SLA (szolgáltatásiszint-szerződés) kapcsolatos információ: a [licencelési feltételek és dokumentáció](http://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37) . a cikk a **licencelés** szakasz a Microsoft Licensing webhely.

### <a name="how-does-power-bi-handle-high-availability-and-failover"></a>Hogyan kezeli a Power BI a magas rendelkezésre állást és a feladatátvételt?

További információ a magas rendelkezésre állás és feladatátvétel: [Power bi-ban magas rendelkezésre állás, a feladatátvételt és a vész helyreállítási – gyakori kérdések](service-admin-failover.md).

## <a name="security-in-power-bi"></a>Biztonság a Power BI-ban

### <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>Eleget tesz a Power BI az országos, regionális, illetve iparágra jellemző megfelelőségi követelményeknek?

A Power BI megfelelésével kapcsolatban további információért látogasson el a [Microsoft biztonsági és adatkezelési központba](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/default.aspx).

### <a name="how-does-security-work-in-power-bi"></a>Hogyan működik a biztonság a Power BI-ban?

A Microsoft Power BI épülő alapját a Office 365-höz, ami viszont épül, mint az Azure Active Directory Azure-szolgáltatások. A Power BI-architektúra áttekintését a [Power BI biztonságával](service-admin-power-bi-security.md) kapcsolatos témakörben találja.

## <a name="next-steps"></a>Következő lépések

[Power BI felügyeleti portál](service-admin-portal.md)  
[A Power BI rendszergazdai szerep ismertetése](service-admin-role.md)  
[Önkiszolgáló regisztráció a Power BI-ra](service-self-service-signup-for-power-bi.md)  
[A Power BI Pro megvásárlása](service-admin-purchasing-power-bi-pro.md)  
[Mi a Power BI Premium?](service-premium-what-is.md)  
[A Power BI Premium megvásárlása](service-admin-premium-purchase.md)  
[Power BI Premium-tanulmány](https://aka.ms/pbipremiumwhitepaper)  
[Csoportok kezelése a Power BI és az Office 365 szolgáltatásban](service-manage-app-workspace-in-power-bi-and-office-365.md)  
[Office 365 felhasználói fiókok kezelése](/office365/servicedescriptions/office-365-platform-service-description/user-account-management/)  
[Office 365 csoportfelügyelet](/office365/admin/email/create-edit-or-delete-a-security-group/)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)

[1]: https://docs.microsoft.com/powershell/scripting/overview