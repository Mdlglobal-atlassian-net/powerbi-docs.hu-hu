---
title: Tartalom terjesztése Azure AD B2B-s külső vendégfelhasználóknak
description: A Power BI integrálható az Azure Active Directory vállalatközi felhasználásra szánt verziójával (Azure AD B2B), ami lehetővé teszi, hogy a Power BI-tartalmakat cégen kívüli vendégfelhasználókkal is biztonságosan meg tudja osztani.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/02/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 0eba54212ff9349ed75d9d9fb18878b39d5cd29a
ms.sourcegitcommit: 378265939126fd7c96cb9334dac587fc80291e97
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/07/2019
ms.locfileid: "57580197"
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>Power BI tartalmak terjesztése Azure AD B2B külső vendégfelhasználóknak

A Power BI integrálható az Azure Active Directory vállalatközi felhasználásra szánt verziójával (Azure AD B2B), ami lehetővé teszi, hogy a Power BI-tartalmakat a szervezeten kívüli vendégfelhasználókkal is biztonságosan meg tudja osztani, úgy, hogy közben teljes mértékben szabályozza a belső adatok felhasználását.  

Emellett engedélyezheti külső vendégfelhasználóknak, hogy szerkesszék és kezeljék a szervezeti tartalmakat.

## <a name="enable-access"></a>Hozzáférés engedélyezése

Vendégfelhasználók meghívása előtt győződjön meg arról, hogy engedélyezve van a [Tartalom megosztása külső felhasználókkal](service-admin-portal.md#export-and-sharing-settings) funkció a Power BI felügyeleti portálján.

Az [Annak engedélyezése, hogy külső vendégfelhasználók is szerkeszthessék és kezelhessék a szervezeti tartalmakat](service-admin-portal.md#export-and-sharing-settings) funkcióval továbbá kiválaszthatja, hogy melyik vendégfelhasználó láthat és hozhat létre tartalmakat a munkaterületeken, beleértve a szervezeti Power BI böngészését.

## <a name="who-can-you-invite"></a>Kit lehet meghívni?

Bármilyen e-mail-címet, akár olyan személyes fiókot használó vendégfelhasználókat is meghívhat, mint a gmail.com, az outlook.com és a hotmail.com. Az Azure AD B2B szolgáltatásban ezek az úgynevezett *közösségi identitások*.

## <a name="invite-guest-users"></a>Vendégfelhasználók meghívása

Meghívóra csak akkor van szükség, amikor először hív meg egy külső vendégfelhasználót a szervezetbe. Kétféleképpen hívhat meg felhasználót: tervezett meghívással vagy alkalmi meghívással.

### <a name="planned-invites"></a>Tervezett meghívások

Abban az esetben válassza a tervezett meghívási módot, ha már tudja, mely felhasználókat szeretné meghívni. Meghívót az Azure Portal vagy a PowerShell használatával küldhet. A meghíváshoz bérlői rendszergazdának kell lennie.

Meghívó az Azure Portalon való küldéséhez kövesse az alábbi lépéseket.

1. Az [Azure Portalon](https://portal.azure.com) válassza az **Azure Active Directory** lehetőséget.

1. A **Kezelés** szakaszban válassza a **Felhasználók** > **Minden felhasználó** > **Új vendégfelhasználó** elemet.

    ![Azure AD-portál – új vendégfelhasználó](media/service-admin-azure-ad-b2b/azuread-portal-new-guest-user.png)

1. Adja meg az **e-mail-címet** és egy **személyes üzenetet**.

    ![Azure AD Portal – Új vendégfelhasználó meghívó üzenete](media/service-admin-azure-ad-b2b/azuread-portal-invite-message.png)

1. Kattintson a **Meghívás** lehetőségre.

Ha egynél több vendéget szeretne meghívni, használja a PowerShellt. Ha további információra van szüksége, tekintse át az [Azure AD B2B együttműködési kódmintát és PowerShell-példákat](/azure/active-directory/b2b/code-samples/) tartalmazó cikket.

A vendégfelhasználónak az e-mailben kapott meghívóban rá kell majd kattintania az **Első lépések** (Get Started) lehetőségre. A rendszer ezután hozzá fogja adni a vendégfelhasználót a bérlőhöz.

![Vendégfelhasználó e-mailes meghívása](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>Ad-hoc meghívások

A meghívás végrehajtásához bármikor hozzáadhatja a külső felhasználót az irányítópultjához vagy jelentéséhez a megosztási felületen, illetve az alkalmazásához a hozzáférési lapon. Az alábbi példán látható, hogy mi a teendő, amikor külső felhasználót hív meg egy alkalmazás használatára.

![Alkalmazás-hozzáférési listához hozzáadott külső felhasználó](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

A vendégfelhasználó fog kapni egy e-mailt, amely tájékoztatja arról, hogy megosztották vele az alkalmazást.

![Vendégfelhasználóval megosztott alkalmazásról szóló e-mail](media/service-admin-azure-ad-b2b/guest-user-invite-email2.png)

A vendégfelhasználónak a céges e-mail-címével kell bejelentkeznie. Bejelentkezés után a rendszer kérni fogja a meghívó elfogadását. Bejelentkezés után a vendégfelhasználót a rendszer átirányítja az alkalmazás tartalmához. Ahhoz, hogy később visszaléphessen az alkalmazásba, könyvjelzőzheti a hivatkozást vagy elmentheti az e-mailt.

## <a name="licensing"></a>Licencelés

A vendégfelhasználónak megfelelő licenccel kell rendelkeznie ahhoz, hogy megtekinthesse a megosztott tartalmat. Ennek három módja van: a Power BI Premium használata, egy Power BI Pro-licenc hozzárendelése a felhasználóhoz, vagy a vendég saját Power BI Pro- licencének használata.

Az [Annak engedélyezése, hogy külső vendégfelhasználók is szerkeszthessék és kezelhessék a szervezeti tartalmakat](service-admin-portal.md#export-and-sharing-settings) funkció használatakor a munkaterületekhez tartalmat adó vagy másokkal tartalmat megosztó vendégfelhasználóknak Power BI Pro-licencre van szüksége.

### <a name="use-power-bi-premium"></a>Prémium szintű Power BI használata

Ha az alkalmazás munkaterületét [Power BI Premium-kapacitáshoz](service-premium.md) rendeli, a vendégfelhasználó Power BI Pro-licenc nélkül is használhatja az alkalmazást. A Power BI Premium az alkalmazások tekintetében további előnyöket, például gyakoribb frissítéseket, dedikált kapacitást és nagy modellméretet biztosít.

![Prémium szintű Power BI használata](media/service-admin-azure-ad-b2b/license-approach1.png)

### <a name="assign-a-power-bi-pro-license-to-guest-user"></a>Power BI Pro-licenc hozzárendelése a vendégfelhasználóhoz

Ha a vendégfelhasználóhoz Power BI Pro-licencet rendel a bérlőben, a vendégfelhasználó meg tudja tekinteni a bérlőben lévő tartalmat.

![Pro licenc hozzárendelése a bérlőről](media/service-admin-azure-ad-b2b/license-approach2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>A vendégfelhasználók hozzák saját Power BI Pro-licencüket

A vendégfelhasználó saját bérlőjén már rendelkezik Power BI Pro-licenccel.

![A vendégfelhasználók hozzák saját licencüket](media/service-admin-azure-ad-b2b/license-approach3.png)

## <a name="guest-users-who-can-edit-and-manage-content"></a>Tartalom szerkesztésére és kezelésére jogosult vendégfelhasználók 

Az [Annak engedélyezése, hogy külső vendégfelhasználók is szerkeszthessék és kezelhessék a szervezeti tartalmakat](service-admin-portal.md#export-and-sharing-settings) funkció használatakor a megadott vendégfelhasználók hozzáférést kapnak a szervezeti Power BI-hoz, és bármilyen tartalmat megtekinthetnek, amelyre jogosultak. Hozzáférhetnek a kezdőlaphoz, böngészhetnek a munkaterületek között, alkalmazásokat telepíthetnek a hozzáférési listáról, és tartalmakkal bővíthetik a munkaterületeket. Létrehozhatnak olyan munkaterületeket, illetve ezek rendszergazdái lehetnek, amelyek az új munkaterületi felületet alkalmazzák. Erre bizonyos korlátozások vonatkoznak, amelyeket a Megfontolandó szempontok és korlátozások szakaszban tekinthet meg.

Ha elő szeretné segíteni ezen felhasználók könnyebb bejelentkezését a Power BI szolgáltatásba, ossza meg velük a bérlői URL-címet. A bérlői URL-cím megkereséséhez kövesse az alábbi lépéseket.

1. A Power BI szolgáltatásban a felső menüből válassza ki a Súgó (**?**), majd **A Power BI bemutatása** lehetőséget.

2. A **Bérlői URL-cím** melletti értékre van szüksége. Ezt a bérlői URL-címet oszthatja meg a vendégfelhasználókkal.

![Vendégfelhasználó bérlői URL-címe](media/service-admin-azure-ad-b2b/power-bi-about-dialog.png)

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások

* Alapértelmezés szerint a külső B2B-vendégeknek csak olvasási jogosultságuk van a tartalomhoz. A külső B2B-vendégek megtekinthetnek alkalmazásokat, irányítópultokat, jelentéseket, illetve adatokat exportálhatnak, és irányítópultokhoz és jelentésekhez kapcsolódó e-mail-értesítéseket hozhatnak létre. Nem férhetnek hozzá azonban munkaterületekhez, és nem tehetik közzé saját tartalmaikat. Azonban ezek a korlátozások nem vonatkoznak azokra a vendégfelhasználókra, akiknek az [Annak engedélyezése, hogy külső vendégfelhasználók is szerkeszthessék és kezelhessék a szervezeti tartalmakat](service-admin-portal.md#export-and-sharing-settings) bérlői beállítással adott engedélyt.

* Az [Annak engedélyezése, hogy külső vendégfelhasználók is szerkeszthessék és kezelhessék a szervezeti tartalmakat](service-admin-portal.md#export-and-sharing-settings) bérlői beállítással engedélyezett vendégfelhasználók számára egyes elemek nem elérhetők. Jelentések frissítéséhez vagy közzétételéhez nekik a Power BI szolgáltatás webes felületét kell használniuk, így a Power BI Desktop-fájlok feltöltéséhez az Adatok lekérése lehetőséget.  A következő műveletek nem támogatottak:
    * Közvetlen közzététel a Power BI Desktopból a Power BI szolgáltatásba
    * A vendégfelhasználók nem csatlakozhatnak a Power BI szolgáltatás szolgáltatói adatkészleteihez a Power BI Desktoppal
    * Office 365-csoportokhoz kötött klasszikus munkaterületek: A vendégfelhasználók nem hozhatnak létre ilyen munkaterületeket, és nem lehetnek ezek rendszergazdái. Csak tagok lehetnek.
    * Az ad-hoc meghívások nem támogatottak a munkaterületek hozzáférési listáiban
    * A vendégfelhasználók számára nem támogatott a Power BI Publisher for Excel
    * A vendégfelhasználók nem telepíthetik a Power BI Gateway szolgáltatást, és nem csatlakoztathatják az Ön szervezetéhez
    * A vendégfelhasználók nem telepíthetnek alkalmazásokat, és nem tehetnek közzé tartalmakat a teljes szervezet számára
    * A vendégfelhasználók nem használhatnak, hozhatnak létre, frissíthetnek vagy telepíthetnek szervezeti tartalomcsomagokat
    * A vendégfelhasználók nem használhatják az Elemzés az Excelben funkciót
    * A vendégfelhasználók nem @mentioned megjegyzésekben
    * A vendégfelhasználók nem használhatnak előfizetéseket
    * Azon vendégfelhasználóknak, akik ezt a funkciót veszik igénybe, munkahelyi vagy iskolai fiókkal kell rendelkezniük. A személyes fiókkal rendelkező vendégfelhasználók további bejelentkezési korlátozásokat tapasztalhatnak.

* Ez a funkció a Power BI SharePoint Online-jelentés kijelzőjéhez jelenleg nem érhető el.

* Egyes Active Directory-beállítások, amelyek a külső vendégfelhasználók jogosultságait korlátozzák, a Power BI-környezetre is vonatkoznak. Ezeket a beállításokat a következő dokumentáció ismerteti:
    * [Külső együttműködési beállítások kezelése](https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations#control-who-can-invite)
    * [Adott szervezetek B2B-felhasználók felé irányuló meghívásainak engedélyezése vagy letiltása](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)  

## <a name="next-steps"></a>Következő lépések

Ha részletesebb információkra van szüksége például a sorszintű adatvédelem működésével kapcsolatban, olvassa el ezt a tanulmányt: [Power BI-tartalmak terjesztése Azure AD B2B külső vendégfelhasználóinak](https://aka.ms/powerbi-b2b-whitepaper).

Az Azure AD B2B szolgáltatással kapcsolatos további információt a [Mi az Azure AD B2B-csoportmunka?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b/) című cikkben találhat.
