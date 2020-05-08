---
title: Tartalom terjesztése Azure AD B2B-s külső vendégfelhasználóknak
description: A Power BI lehetővé teszi a tartalom külső vendégfelhasználókkal való megosztását az Azure Active Directory vállalatközi felhasználásra szánt verziójával (Azure AD B2B).
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: d17c6bbe5ddf6cd39626ac0038595543cd2fecfb
ms.sourcegitcommit: 220910f0b68cb1e265ccd5ac0cee4ee9c6080b26
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82841066"
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>Power BI tartalmak terjesztése Azure AD B2B külső vendégfelhasználóknak

A Power BI lehetővé teszi a tartalom külső vendégfelhasználókkal való megosztását az Azure Active Directory vállalatközi felhasználásra szánt verziójával (Azure AD B2B).
Az Azure AD B2B használatával a vállalat központilag engedélyezi és szabályozza a külső felhasználókkal való megosztást. A külső vendégek alapértelmezés szerint csak fogyasztói felülettel rendelkeznek. Emellett engedélyezheti külső vendégfelhasználóknak, hogy szerkesszék és kezeljék a szervezeti tartalmakat.

Ez a cikk a Power BI-beli Azure AD B2B-hez biztosít alapszintű bevezetést. További információért lásd: [Power BI-tartalom terjesztése külső vendégfelhasználóknak az Azure Active Directory B2B használatával](guidance/whitepaper-azure-b2b-power-bi.md).

## <a name="enable-access"></a>Hozzáférés engedélyezése

Vendégfelhasználók meghívása előtt mindenképpen engedélyezze a [Tartalom megosztása külső felhasználókkal](service-admin-portal.md#export-and-sharing-settings) funkciót a Power BI felügyeleti portálján. Még ha ez a beállítás engedélyezve van is, a felhasználónak engedéllyel kell rendelkeznie az Azure Active Directoryban vendégfelhasználók meghívásához, amelyet a Vendégmeghívói szerepkörön keresztül van megadva. 

Az [Annak engedélyezése, hogy külső vendégfelhasználók is szerkeszthessék és kezelhessék a szervezeti tartalmakat](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) lehetőséggel megadhatja a vendégfelhasználóknak a lehetőséget, hogy tartalmakat tekintsenek meg és hozzanak létre a munkaterületeken, beleértve a vállalati Power BI böngészését.

> [!NOTE]
> A [Tartalom megosztása külső felhasználókkal](service-admin-portal.md#export-and-sharing-settings) beállítás szabályozza, engedélyez-e a Power BI külső felhasználókat a vállalatnál. Ha egy külső felhasználó elfogadja a meghívót, akkor a szervezet Microsoft Azure Active Directory B2B-vendégfelhasználójává válik. Megjelenik a személyválasztókban a Power BI különböző felületein. Ha a beállítás le van tiltva, a szervezetben a meglévő vendégfelhasználók továbbra is hozzáférhetnek az összes olyan elemhez, amelyet eddig is elérhettek, és továbbra is megjelennek a személyválasztó felületeken. Továbbá, ha a vendégeket a [tervezett meghívás](#planned-invites) megközelítési mód alkalmazásával veszik fel, szintén megjelennek a személyválasztókban. Ha meg szeretné akadályozni, hogy a vendégfelhasználók hozzáférjenek a Power BI-hoz, használja a Microsoft Azure Active Directory feltételes hozzáférési szabályzatát.

## <a name="who-can-you-invite"></a>Kit lehet meghívni?

Szinte bármilyen e-mail-címet, akár olyan személyes fiókot használó vendégfelhasználók is meghívhatók a vállalathoz, mint a gmail.com, az outlook.com és a hotmail.com. Az Azure AD B2B szóhasználatával ezek a *közösségi identitások*.

Nem hívhat meg olyan felhasználókat, akik kormányzati felhőhöz vannak társítva, például a [Power BI for US Government](service-govus-overview.md) felhasználóit.

## <a name="invite-guest-users"></a>Vendégfelhasználók meghívása

A vendégfelhasználóknak csak az első alkalommal van szükségük meghívóra, amikor meghívják őket a szervezetbe. Vendégek meghívásához tervezett vagy alkalmi meghívókat használhat.

Alkalmi meghíváshoz használja az alábbi képességeket:
* Jelentés és irányítópult megosztása
* Alkalmazás-hozzáférési lista

Az alkalmi meghívások nem támogatottak a munkaterület hozzáférési listájában. Ezeket a felhasználókat a [tervezett meghívási módszerrel](#planned-invites) adhatja a vállalathoz. Ha egy külső felhasználó már vendég a vállalatnál, vegye fel a munkaterület hozzáférési listájára.

### <a name="planned-invites"></a>Tervezett meghívások

Abban az esetben válassza a tervezett meghívási módot, ha már tudja, mely felhasználókat szeretné meghívni. A meghívók elküldésére az Azure Portal vagy a PowerShell nyújt lehetőséget. A meghíváshoz bérlői rendszergazdának kell lennie.

Meghívó az Azure Portalon való küldéséhez kövesse az alábbi lépéseket.

1. Az [Azure Portalon](https://portal.azure.com) válassza az **Azure Active Directory** lehetőséget.

1. A **Kezelés** szakaszban válassza a **Felhasználók** > **Minden felhasználó** > **Új vendégfelhasználó** elemet.

    ![Az Azure Portal képernyőképe az Új vendégfelhasználó beállítás kiemelésével.](media/service-admin-azure-ad-b2b/azure-ad-portal-new-guest-user.png)

1. Adja meg az **e-mail-címet** és egy **személyes üzenetet**.

    ![Az Azure AD portál képernyőképe az Új vendégfelhasználó párbeszédpanellel.](media/service-admin-azure-ad-b2b/azure-ad-portal-invite-message.png)

1. Kattintson a **Meghívás** lehetőségre.

Ha egynél több vendéget szeretne meghívni, használja a PowerShellt. Ha további információra van szüksége, tekintse át az [Azure AD B2B együttműködési kódmintát és PowerShell-példákat](/azure/active-directory/b2b/code-samples/) tartalmazó cikket.

A vendégfelhasználónak az e-mailben kapott meghívóban rá kell majd kattintania az **Első lépések** (Get Started) lehetőségre. A rendszer ezután hozzá fogja adni a vendégfelhasználót a bérlőhöz.

![Vendégfelhasználó e-mailes meghívásának képernyőképe.](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>Alkalmi meghívás

Külső felhasználó meghívásához bármikor hozzáadhatja őt az irányítópultjához vagy jelentéséhez a megosztási felületen, illetve az alkalmazásához a hozzáférési lapon. Az alábbi példán látható, hogy mi a teendő, amikor külső felhasználót hív meg egy alkalmazás használatára.

![Képernyőkép külső felhasználó alkalmazás-hozzáférési listára való felvételéről a Power BI-ban.](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

A vendégfelhasználó e-mailt fog kapni, amely tudatja vele, hogy Ön megosztotta vele az alkalmazást.

![Vendégfelhasználóval megosztott alkalmazásról szóló e-mail képernyőképe](media/service-admin-azure-ad-b2b/guest-user-invite-email-2.png)

A vendégfelhasználónak a céges e-mail-címével kell bejelentkeznie. Bejelentkezés után a rendszer kérni fogja a meghívó elfogadását. Bejelentkezés után az alkalmazás megnyílik a vendégfelhasználó számára. Ahhoz, hogy később visszaléphessen az alkalmazásba, érdemes könyvjelzőznie a hivatkozást vagy elmentenie az e-mailt.


## <a name="licensing"></a>Licencelés

A vendégfelhasználónak megfelelő licenccel kell rendelkeznie ahhoz, hogy megtekinthesse a megosztott tartalmat. Három módon biztosítható, hogy a felhasználó megfelelő licenccel rendelkezzen: a Power BI Premium használatával, egy Power BI Pro-licenc a felhasználóhoz való hozzárendelésével, vagy a vendég saját Power BI Pro-licencének használatával.

[Azoknak a vendégfelhasználóknak, akik tartalmat szerkeszthetnek és kezelhetnek a vállalatnál](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) Power BI Pro-licenccel kell rendelkezniük, hogy tartalmakkal járulhassanak hozzá a munkaterületekhez vagy tartalmakat oszthassanak meg másokkal.

### <a name="use-power-bi-premium"></a>Prémium szintű Power BI használata

Ha a munkaterületet [Power BI Premium-kapacitáshoz](service-premium-what-is.md) rendeli, a vendégfelhasználó Power BI Pro-licenc nélkül is használhatja az alkalmazást. A Power BI Premium az alkalmazások tekintetében további előnyöket, például gyakoribb frissítéseket, dedikált kapacitást és nagy modellméretet biztosít.

![Vendégfelhasználói felület ábrája a Power BI Premiummal.](media/service-admin-azure-ad-b2b/license-approach-1.png)

### <a name="assign-a-power-bi-pro-license-to-guest-user"></a>Power BI Pro-licenc hozzárendelése a vendégfelhasználóhoz

Ha egy vendégfelhasználóhoz Power BI Pro-licencet rendel a bérlőben, ez a vendégfelhasználó meg tudja tekinteni a bérlőben lévő tartalmat. További információ a licencek hozzárendeléséről: [Licencek hozzárendelése a felhasználókhoz a Licencek lapon](/office365/admin/manage/assign-licenses-to-users#assign-licenses-to-users-on-the-licenses-page). Mielőtt Pro-licenceket rendelne a vendégfelhasználókhoz, forduljon a Microsoft-fiókfelelőséhez, és ellenőrizze, hogy megfelel-e a Microsofttal kötött szerződés feltételeinek.

![Vendégfelhasználói felület ábrája a bérlőből hozzárendelt Pro-licenccel.](media/service-admin-azure-ad-b2b/license-approach-2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>A vendégfelhasználók hozzák saját Power BI Pro-licencüket

A vendégfelhasználó saját bérlőjén már rendelkezik Power BI Pro-licenccel.

![Vendégfelhasználói felület ábrája saját licenc használata esetén.](media/service-admin-azure-ad-b2b/license-approach-3.png)

## <a name="guest-users-who-can-edit-and-manage-content"></a>Tartalom szerkesztésére és kezelésére jogosult vendégfelhasználók

Az [Annak engedélyezése, hogy külső vendégfelhasználók is szerkeszthessék és kezelhessék a vállalati tartalmakat](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) funkció használatakor a megadott vendégfelhasználók további hozzáférést kapnak a vállalati Power BI-hoz. Az engedélyezett vendégek minden tartalmat megtekinthetnek, amelyhez engedélyük van, hozzáférhetnek a Kezdőlaphoz, böngészhetnek a munkaterületek között, alkalmazásokat telepíthetnek, megtekinthetik azok helyét a hozzáférési listán, és tartalmakkal bővíthetik a munkaterületeket. Létrehozhatnak olyan munkaterületeket, illetve ezek rendszergazdái lehetnek, amelyek az új munkaterületi felületet alkalmazzák. Bizonyos korlátozások érvényesek. Ezeket a Szempontok és korlátozások szakasz sorolja fel.
 
Ha elő szeretné segíteni az engedélyezett vendégek könnyebb bejelentkezését a Power BI szolgáltatásba, ossza meg velük a bérlői URL-címet. A bérlői URL-cím megkereséséhez kövesse az alábbi lépéseket.

1. A Power BI szolgáltatásban a felső menüből válassza ki a Súgó ( **?** ), majd **A Power BI bemutatása** lehetőséget.

2. A **Bérlői URL-cím** melletti értékre van szüksége. Ossza meg a bérlő URL-címét az engedélyezett vendégfelhasználókkal.

    ![Képernyőkép a Power BI Névjegy párbeszédpaneljéről a vendégfelhasználói bérlői URL-cím kiemelésével.](media/service-admin-azure-ad-b2b/power-bi-about-dialog.png)

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások

* A vendégeknek a külső Azure AD B2B alapértelmezés szerint csak olvasási jogosultságot ad a tartalomhoz. A külső Azure AD B2B-vendégek megtekinthetnek alkalmazásokat, irányítópultokat, jelentéseket, illetve adatokat exportálhatnak, és irányítópultokhoz és jelentésekhez kapcsolódó e-mail-értesítéseket hozhatnak létre. Nem férhetnek hozzá azonban munkaterületekhez, és nem tehetik közzé saját tartalmaikat. Ezeknek a korlátozásoknak a feloldásához használhatja az [Annak engedélyezése, hogy külső vendégfelhasználók is szerkeszthessék és kezelhessék a szervezeti tartalmakat](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) funkciót.

* Vendégfelhasználók meghívásához Power BI Pro-licencre van szükség. A Pro-próbaverzióval rendelkező felhasználók nem hívhatnak meg vendégfelhasználókat a Power BI-ban.

* Egyes felületek nem érhetők el [azon vendégfelhasználók számára, akik tartalmakat szerkeszthetnek és kezelhetnek a vállalatnál](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization). Jelentések frissítéséhez vagy közzétételéhez nekik a Power BI szolgáltatás webes felületét kell használniuk, így a Power BI Desktop-fájlok feltöltéséhez az Adatok lekérése lehetőséget.  Az alábbi használati módok nem támogatottak:
    * Közvetlen közzététel a Power BI Desktopból a Power BI szolgáltatásba
    * A vendégfelhasználók nem csatlakozhatnak a Power BI szolgáltatás szolgáltatói adathalmazaihoz a Power BI Desktoppal
    * Office 365-csoportokhoz kötött klasszikus munkaterületek:
        * A vendégfelhasználók nem hozhatnak létre ilyen munkaterületeket, és nem lehetnek ezek rendszergazdái
        * A vendégfelhasználók lehetnek tagok
    * Alkalmi meghívók küldése munkaterület-hozzáférési listák esetén nem támogatott
    * Az Excelhez készült Power BI Publisher vendégfelhasználók esetén nem támogatott
    * A vendégfelhasználók nem telepíthetik a Power BI Gateway szolgáltatást, és nem csatlakoztathatják a szervezethez
    * A vendégfelhasználók nem telepíthetnek alkalmazásokat, és nem tehetnek közzé tartalmakat a teljes szervezet számára
    * A vendégfelhasználók nem használhatnak, hozhatnak létre, frissíthetnek vagy telepíthetnek szervezeti tartalomcsomagokat
    * A vendégfelhasználók nem használhatják az Elemzés az Excelben funkciót
    * A vendégfelhasználók nem szerepelhetnek @mentioned minőségben a megjegyzésekben
    * A vendégfelhasználók nem használhatnak feliratkozásokat
    * Azon vendégfelhasználóknak, akik ezt a funkciót veszik igénybe, munkahelyi vagy iskolai fiókkal kell rendelkezniük. 
    
* A személyes fiókkal rendelkező vendégfelhasználók további korlátozásokat tapasztalhatnak a bejelentkezésre vonatkozó megkötések miatt.
    * Webböngészőben is használhatják a Power BI szolgáltatás felhasználási felületeit
    * Nem használhatják a Power BI-mobilalkalmazásokat.
    * Nem tudnak majd bejelentkezni a hitelesítő adatok megadásához azokban az esetekben, amelyekben munkahelyi vagy iskolai fiók szükséges.

* Ez a funkció a Power BI SharePoint Online-jelentés kijelzőjéhez jelenleg nem érhető el.

* Egyes Active Directory-beállítások az egész vállalaton belül korlátozhatják a külső vendégfelhasználók jogosultságait. Ezek a Power BI-környezetre is vonatkoznak. Ezeket a beállításokat a következő dokumentáció ismerteti:
    * [Külső együttműködési beállítások kezelése](/azure/active-directory/b2b/delegate-invitations#configure-b2b-external-collaboration-settings)
    * [Adott szervezetek B2B-felhasználók felé irányuló meghívásainak engedélyezése vagy letiltása](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)
    * [A Power BI szolgáltatás elérésének engedélyezése vagy letiltása a vendégfelhasználók számára](/azure/active-directory/conditional-access/overview)
    
* A vállalaton kívüli megosztás az országos felhőkben nem támogatott. Ehelyett hozzon létre olyan felhasználói fiókokat a szervezetben, amelyeket a külső felhasználók használhatnak a tartalom eléréséhez. 

* Ha közvetlenül oszt meg valamit egy vendégfelhasználóval, a Power BI a hivatkozást tartalmazó e-mailt küld neki. Az e-mail elküldésének elkerüléséhez vegye fel a vendégfelhasználót egy biztonsági csoportba, és a biztonsági csoporttal ossza meg a tartalmat.  

## <a name="next-steps"></a>Következő lépések

Ha részletesebb információkra van szüksége például a sorszintű adatvédelem működésével kapcsolatban, olvassa el ezt a tanulmányt: [Power BI-tartalmak terjesztése Azure AD B2B külső vendégfelhasználóinak](https://aka.ms/powerbi-b2b-whitepaper).

Az Azure AD B2B szolgáltatással kapcsolatos további információt a [Mi az Azure AD B2B-együttműködés?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b/) című cikkben találhat.
