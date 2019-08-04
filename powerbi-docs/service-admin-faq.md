---
title: A Power BI felügyelete – gyakori kérdések (GYIK)
description: Ismerje meg a Power BI-előfizetéssel, bérlőkezeléssel és más adminisztratív feladatokkal kapcsolatos gyakori kérdésekre adott válaszokat.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: d6961007c3f7185b954188fa7bd7866d80a7f85a
ms.sourcegitcommit: f05ba39a0e46cb9cb43454772fbc5397089d58b4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/26/2019
ms.locfileid: "68523401"
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
* [Hogyan ellenőrizhető, hogy blokkoltam-e a bérlőt?](#how-do-i-check-if-i-have-the-block-on-in-the-tenant)
* [Hogyan gátolható meg, hogy a meglévő felhasználók elkezdjék használni a Power BI-t?](#how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi)
* [Hogyan engedélyezhető, hogy a meglévő felhasználók regisztráljanak a Power BI-ra?](#how-can-i-allow-my-existing-users-to-sign-up-for-power-bi)

### <a name="administration-of-power-bi-section"></a>A Power BI felügyelete szakasz

* [Hogyan változtatja meg a Power BI használata a felhasználók identitásának kezelését a cégen belül?](#how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today)
* [Hogyan lehet kezelni a Power BI-t?](#how-do-we-manage-power-bi)
* [Mi a Microsoft által a felhasználók számára létrehozott bérlők kezelésének folyamata?](#what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users)
* [Ha több tartományom van, felügyelhetem azt az Office 365-bérlőt, amelyhez a felhasználók hozzáadódnak?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to)
* [Hogyan távolítható el a Power BI a már regisztrált felhasználóktól?](#how-do-i-remove-power-bi-for-users-that-already-signed-up)
* [Honnan szerzek arról tudomást, ha új felhasználók csatlakoztak a bérlőhöz?](#how-do-i-know-when-new-users-have-joined-my-tenant)
* [Van még bármi egyéb, amire fel kell készülnöm?](#are-there-any-additional-things-i-should-prepare-for)
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

Rendszergazdaként a [Power BI webhelyén](https://powerbi.microsoft.com) vagy a Microsoft 365 Felügyeleti központ [Szolgáltatások vásárlása](https://admin.microsoft.com/AdminPortal/Home#/catalog) oldalán regisztrálhat a Power BI szolgáltatásra. Amikor egy rendszergazda regisztrál a Power BI-ra, felhasználói licenceket rendelhet azokhoz a felhasználókhoz, akiknek hozzáférésre van szükségük.

A cég egyes felhasználói külön-külön is regisztrálhatnak a [Power BI webhelyen](https://powerbi.microsoft.com) a Power BI-ra. Amikor a vállalat egy felhasználója regisztrál a Power BI-ra, a felhasználóhoz automatikusan Power BI-licenc lesz rendelve. További információ: [Egyéni Power BI-regisztráció](service-self-service-signup-for-power-bi.md) és [Szervezeti Power BI-licencelés](service-admin-licensing-organization.md).

### <a name="how-do-individual-users-in-my-organization-sign-up"></a>Hogyan regisztrálnak a cég egyéni felhasználói?

Három forgatókönyv vonatkozhat a cégen belüli felhasználókra:

* **1. forgatókönyv**: A cég már rendelkezik egy meglévő Office 365-környezettel, és a Power BI-ra regisztráló felhasználónak már van Office 365-fiókja.
    Ha ebben a forgatókönyvben egy felhasználó már rendelkezik a bérlőn (például contoso.com) munkahelyi vagy iskolai fiókkal, de még nincs Power BI-fiókja, a Microsoft egyszerűen aktiválja a csomagot a fiókhoz. A ezután felhasználó automatikusan értesítést kap a Power BI szolgáltatás használatának módjáról.

* **2. forgatókönyv**: A cég már rendelkezik egy meglévő Office 365-környezettel, de a Power BI-ra regisztráló felhasználónak nincs Office 365-fiókja.
    Ebben a forgatókönyvben a felhasználónak van egy, a vállalati tartományba eső e-mail-címe (például contoso.com), de még nincs Office 365-fiókja. Ebben az esetben a felhasználó regisztrálhat a Power BI-ra, és automatikusan kap egy fiókot, így hozzáférhet a Power BI szolgáltatáshoz. Ha például egy Nancy nevű alkalmazott a munkahelyi e-mail-címét (például nancy@contoso.com) használja a regisztráláshoz, a Microsoft automatikusan hozzáadja Nancyt felhasználóként a Contoso Office 365-környezetéhez, és aktiválja a Power BI-t ehhez a fiókhoz.

* **3. forgatókönyv**: A vállalatban nincs az e-mail-tartományhoz csatlakoztatott Office 365-környezet.
    A vállalatnak nem kell adminisztratív műveleteket elvégeznie a Power BI használatához. A szolgáltatás a felhasználókat egy új, kizárólag felhőalapú felhasználói címtárhoz adja. Igény szerint bérlői rendszergazdaként Ön is kezelheti őket.

> [!IMPORTANT]
> Ha a cég több e-mail-tartománnyal rendelkezik, és azt szeretné, hogy az összes e-mail-cím bővítmény ugyanabban a bérlőben legyen, adja az e-mail-címek összes tartományát egy Azure Active Directory-bérlőhöz, mielőtt bármelyik felhasználó regisztrálna. Nem áll rendelkezésre automatikus mechanizmus a felhasználók bérlők közötti mozgatásához, miután létrejöttek. A folyamatról további információt a cikk későbbi, [Ha több tartományom van, felügyelhetem azt az Office 365 bérlőt, amelyhez a felhasználók kerülnek?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to) című szakaszában és a [Tartomány hozzáadása az Office 365-höz](/office365/admin/setup/add-domain/) című cikkben talál.

### <a name="how-can-i-prevent-users-from-joining-my-existing-office-365-tenant"></a>Hogyan gátolható meg, hogy a felhasználók csatlakozzanak a meglévő Office 365-bérlőhöz?

Rendszergazdaként tehet olyan lépéseket, amelyek meggátolják, hogy a felhasználók csatlakozzanak a meglévő Office 365-bérlőhöz. Ha letiltja a hozzáférést, a regisztrációs kísérletek meghiúsulnak, és egy üzenet a cég rendszergazdájával való kapcsolatfelvételhez vezeti a felhasználókat. Nem kell megismételnie ezt a folyamatot, ha már letiltotta az automatikus licencterjesztést (például az Office 365 for Education for Students, Faculty és Staff esetén).

A következő PowerShell-paranccsal meggátolhatja, hogy az új felhasználók a felügyelt bérlőhöz csatlakozzanak. ([További információ a PowerShellről][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $false
```

> [!NOTE]
> A hozzáférés letiltása meggátolja, hogy a cég lévő új felhasználói regisztráljanak a Power BI-ra. Azon felhasználók licence, akik a vállalat új regisztrációinak letiltása előtt regisztráltak a Power BI-ra, továbbra is megmarad. Felhasználó eltávolításához tekintse meg a cikk [Hogyan távolítható el a Power BI a már regisztrált felhasználóktól?](#how-do-i-remove-power-bi-for-users-that-already-signed-up) című szakaszát.

### <a name="how-can-i-allow-users-to-join-my-existing-office-365-tenant"></a>Hogyan engedélyezhető, hogy a felhasználók csatlakozzanak a meglévő Office 365-bérlőhöz?

A következő PowerShell-paranccsal engedélyezheti, hogy az új felhasználók a felügyelt bérlőhöz csatlakozzanak. ([További információ a PowerShellről][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $true
```

### <a name="how-do-i-check-if-i-have-the-block-on-in-the-tenant"></a>Hogyan ellenőrizhető, hogy blokkoltam-e a bérlőt?

A beállítások ellenőrzéséhez használja a következő PowerShell-szkriptet. Az *AllowEmailVerifiedUsers* értékének hamisnak kell lennie. ([További információ a PowerShellről][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Get-MsolCompanyInformation | fl allow*
```

### <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>Hogyan gátolható meg, hogy a meglévő felhasználók elkezdjék használni a Power BI-t?

A jelen **AllowAdHocSubscriptions** paramétert vezérlő Azure AD-beállítás. A legtöbb bérlő esetén ez igaz értékre van állítva, vagyis engedélyezett. Ha a Power BI-t egy partneren keresztül szerezte be, elképzelhető, hogy false (hamis) érték van megadva, amely letiltja a regisztrációt.

Az alkalmi előfizetések letiltásához használja a következő PowerShell-szkriptet. ([További információ a PowerShellről][1].)

1. Jelentkezzen be az Azure Active Directoryba az Office 365 hitelesítő adataival. Az alábbi PowerShell-szkript első sora bekéri a hitelesítő adatokat. A második sor csatlakozik az Azure Active Directoryhoz.

    ```powershell
     $msolcred = get-credential
     connect-msolservice -credential $msolcred
    ```

   ![Képernyőkép Azure Active Directory PowerShelles bejelentkezéséről](media/service-admin-licensing-organization/azure-ad-sign-in.png)

1. Miután bejelentkezett, a következő parancs futtatásával ellenőrizheti a bérlő aktuális konfigurációját.

    ```powershell
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
    ```

1. A következő parancs futtatásával engedélyezheti (`$true`) vagy tilthatja le (`$false`) az **AllowAdHocSubscriptions** beállítást.

    ```powershell
     Set-MsolCompanySettings -AllowAdHocSubscriptions $false
    ```

> [!NOTE]
> Az **AllowAdHocSubscriptions** jelzővel irányítható a vállalat számos felhasználói képessége, beleértve a felhasználók azon képességét, hogy regisztráljanak az Azure Rights Management szolgáltatásra. A jelölő módosítása az összes képességre hatással van.

### <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>Hogyan engedélyezhető, hogy a meglévő felhasználók regisztráljanak a Power BI-ra?

Ha engedélyezni szeretné, hogy a meglévő felhasználók regisztráljanak a Power BI-ra, futtassa a korábbi kérdésben szereplő parancsot, de `$false` (hamis) helyett `$true` (igaz) értékkel az utolsó lépésben.

## <a name="administration-of-power-bi"></a>A Power BI felügyelete

### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>Hogyan változtatja meg a Power BI használata a felhasználók identitásának kezelését a cégen belül?

Három forgatókönyv vonatkozhat a cégen belüli felhasználókra:

* **1. forgatókönyv**: Ha a vállalata már rendelkezik egy meglévő Office 365-környezettel, és a vállalatában lévő összes felhasználó rendelkezik Office 365-fiókkal, az identitáskezelés nem változik.

* **2. forgatókönyv**: Ha a vállalata már rendelkezik egy meglévő Office 365-környezettel, de a vállalatában nem minden felhasználó rendelkezik Office 365-fiókkal, létrehozunk egy felhasználót a bérlőben, és licenceket rendelünk hozzá a felhasználó munkája, vagy iskolája, e-mail-címe alapján.

    Ez azt jelenti, hogy az Ön által bármely adott időpontban felügyelt felhasználók száma növekszik, ahogy a vállalatában lévő felhasználók regisztrálnak a szolgáltatásra.

* **3. forgatókönyv**: Ha a szervezet nem rendelkezik az e-mail tartományhoz csatlakoztatott Office 365-környezettel, akkor az identitások kezelése nem változik.

    A szolgáltatás a felhasználókat egy új, kizárólag felhőalapú felhasználói címtárhoz adja. Igény szerint bérlői rendszergazdaként Ön is kezelheti őket.

### <a name="how-do-we-manage-power-bi"></a>Hogyan lehet kezelni a Power BI-t?

A Power BI olyan rendszergazdai portált biztosít, amellyel megtekintheti a használattal kapcsolatos statisztikákat, hivatkozást biztosít a Microsoft 365 Felügyeleti központhoz a felhasználók és csoportok kezeléséhez, illetve lehetővé teszi a bérlők közötti beállítások kezelését.

A Power BI felügyeleti portáljának használatához fiókját **Globális rendszergazda** fiókként kell megjelölni az Office 365 vagy az Azure Active Directory szolgáltatáson belül, vagy a Power BI szolgáltatás rendszergazdai szerepkörét kell hozzárendelni az Ön felhasználói fiókjához. További információ: [A Power BI rendszergazdai szerepkörének ismertetése](service-admin-role.md) és [Power BI felügyeleti portál](service-admin-portal.md).

### <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>Mi a Microsoft által a felhasználók számára létrehozott bérlők kezelésének folyamata?

Amikor egy önkiszolgáló felhasználó olyan felhőszolgáltatásban regisztrál, amely az Azure-t használja, akkor az e-mail-tartománya alapján hozzá lesz adva egy nem felügyelt Azure AD-címtárhoz. A létrehozott bérlőt a *rendszergazdai átvétel* néven ismert folyamattal igényelheti és kezelheti. Az átvétel típusa attól függ, hogy van-e már létező felügyelt bérlő a tartományhoz társítva:

* Új felügyelt bérlő tartományhoz történő létrehozásához használjon *belső átvételt*.

* Használjon *külső átvételt* a tartománynak egy meglévő felügyelt bérlőbe történő áthelyezésére.

További információ: [Nem felügyelt címtár átvétele rendszergazdaként az Azure Active Directoryban](/azure/active-directory/users-groups-roles/domains-admin-takeover).

Külső átvétel végrehajtásakor az átvétel végrehajtása előtt létrehozott Power BI-tartalom a [Power BI archivált munkaterületére](service-admin-power-bi-archived-workspace.md) kerül. Minden tartalmat manuálisan kell áttelepítenie, amelyet az új bérlőben szeretne használni.

### <a name="if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to"></a>Ha több tartományom van, felügyelhetem azt az Office 365-bérlőt, amelyhez a felhasználók hozzáadódnak?

If you do nothing, the service creates a tenant for each user email domain and subdomain. Ha azt szeretné, hogy az e-mail-cím bővítményétől függetlenül mindegyik felhasználó ugyanabban a bérlőben legyen: Előre hozzon létre egy célbérlőt, vagy használjon egy meglévő bérlőt. Adja hozzá az összes meglévő tartományt és altartományt, amelyet szeretne a bérlőben egyesíteni. Ezután az összes olyan felhasználó, akinek az e-mail-címe ezekre a tartományokra és altartományokra végződik, automatikusan a célbérlőhöz lesz csatlakoztatva, amikor regisztrál.

> [!IMPORTANT]
> Nem áll rendelkezésre automatikus támogatott mechanizmus a felhasználók bérlők közötti mozgatásához, miután létrejöttek. A tartományok egyetlen Office 365-bérlőhöz való hozzáadásáról a [felhasználók és tartományok Office 365 szolgáltatáshoz adásával](/office365/admin/setup/add-domain/) kapcsolatos témakörben olvashat.

### <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>Hogyan távolítható el a Power BI a már regisztrált felhasználóktól?

Ha egy felhasználó regisztrált a Power BI-ra, de Ön már nem szeretné, hogy hozzáférjen a Power BI-hoz, eltávolíthatja a felhasználó Power BI-licencét.

1. A [Microsoft 365 Felügyeleti központ](https://admin.microsoft.com/AdminPortal/Home#/homepage) megnyitása.

1. A bal oldali navigációs sávban válassza a **Felhasználók** > **Aktív felhasználók** lehetőséget.

1. Keresse meg azt a felhasználót, akinek el szeretné távolítani a licencét, majd válassza ki a nevét.

    A felhasználók kötegelt licenckezelését is elvégezheti. Ehhez válasszon ki több felhasználót, és válassza a **Terméklicencek szerkesztése** lehetőséget.

1. A Felhasználó adatai lap **Terméklicencek** szakasza mellett válassza a **Szerkesztés** lehetőséget.

1. Kapcsolja **ki** a **Power BI (ingyenes)** vagy a **Power BI Pro** beállítást attól függően, hogy milyen licenc van alkalmazva a fiókra.

1. Kattintson a **Mentés** gombra.

### <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>Honnan szerzek arról tudomást, ha új felhasználók csatlakoztak a bérlőhöz?

A jelen program részeként a bérlőhöz csatlakozó felhasználókhoz egyedi licenc van rendelve, amely alapján szűrhet a felügyeleti irányítópult aktív felhasználó panelén. Az új nézet létrehozásához kövesse az alábbi lépéseket.

1. A [Microsoft 365 Felügyeleti központ](https://admin.microsoft.com/AdminPortal/Home#/homepage) megnyitása.

1. A bal oldali navigációs sávban válassza a **Felhasználók** > **Aktív felhasználók** lehetőséget.

1. A **Nézetek** menüben válassza az **Egyéni nézet hozzáadása** lehetőséget.

1. Nevezze el az új nézetet, és a **Hozzárendelt terméklicenc** területen válassza a **Power BI (ingyenes)** vagy a **Power BI Pro** lehetőséget.

    Egy nézethez csak egy licencet választhat ki. Ha **Power BI (ingyenes)** és **Power BI Pro** licencek is vannak a vállalatában, két nézetet is létrehozhat.

1. Adjon meg további kívánt feltételeket, majd válassza a **Hozzáadás** lehetőséget.

1. Az új nézet létrehozása után az elérhető a **Nézetek** menüben.

### <a name="are-there-any-additional-things-i-should-prepare-for"></a>Van még bármi egyéb, amire fel kell készülnöm?

Az új jelszavak létrehozásával kapcsolatos kérések növekedését tapasztalhatja. További információ erről a folyamatról: [Új jelszó kérése egy felhasználóhoz](/office365/admin/add-users/reset-passwords).

A Microsoft 365 Felügyeleti központban a szokásos eljárással távolíthat el felhasználókat a bérlőből. Ha azonban egy felhasználónak még mindig a vállalattól származó e-mail-címe van, újra tud csatlakozni, amíg le nem tiltja az összes felhasználó csatlakozását.

### <a name="where-is-my-power-bi-tenant-located"></a>Hol található a Power BI-bérlőm?

További információt a Power BI-bérlő adatrégiójáról a [Hol található a Power BI-bérlőm?](service-admin-where-is-my-tenant-located.md) című témakörben találhat.

### <a name="what-is-the-power-bi-sla"></a>Mi az a Power BI SLA?

A Power BI SLA-ról (szolgáltatásiszint-szerződésről) további információt a Microsoft licencelést bemutató webhelyének **Licencelés** szakaszában található [Licencelési feltételek és dokumentáció](http://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37) című témakörben talál.

### <a name="how-does-power-bi-handle-high-availability-and-failover"></a>Hogyan kezeli a Power BI a magas rendelkezésre állást és a feladatátvételt?

A magas rendelkezésre állásról és a feladatátvételről a [Gyakori kérdések a Power BI-beli magas rendelkezésre állással, feladatátvétellel és vészhelyreállítással kapcsolatban](service-admin-failover.md) című cikk nyújt tájékoztatást.

## <a name="security-in-power-bi"></a>Biztonság a Power BI-ban

### <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>Eleget tesz a Power BI az országos, regionális, illetve iparágra jellemző megfelelőségi követelményeknek?

A Power BI megfelelésével kapcsolatban további információért látogasson el a [Microsoft biztonsági és adatkezelési központba](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/default.aspx).

### <a name="how-does-security-work-in-power-bi"></a>Hogyan működik a biztonság a Power BI-ban?

A Microsoft Power BI az Office 365 alapjára épül, amely viszont Azure-szolgáltatásokon, például az Azure Active Directoryn alapul. A Power BI-architektúra áttekintését a [Power BI biztonságával](service-admin-power-bi-security.md) kapcsolatos témakörben találja.

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