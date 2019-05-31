---
title: Tartalom terjesztése Azure AD B2B-s külső vendégfelhasználóknak
description: A Power BI integrálható az Azure Active Directory vállalatközi felhasználásra szánt verziójával (Azure AD B2B), ami lehetővé teszi, hogy a Power BI-tartalmakat cégen kívüli vendégfelhasználókkal is biztonságosan meg tudja osztani.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 2d1e9e32fcec67647bb75ac14ed872e6c51fef96
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65101809"
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>Power BI tartalmak terjesztése Azure AD B2B külső vendégfelhasználóknak

A Power BI integrálható az Azure Active Directory vállalatközi felhasználásra szánt verziójával (Azure AD B2B), ami lehetővé teszi, hogy a Power BI-tartalmakat a szervezeten kívüli vendégfelhasználókkal is biztonságosan meg tudja osztani, úgy, hogy közben teljes mértékben szabályozza a belső adatok felhasználását.  

Emellett engedélyezheti külső vendégfelhasználóknak, hogy szerkesszék és kezeljék a szervezeti tartalmakat.

## <a name="enable-access"></a>Hozzáférés engedélyezése

Ne feledje engedélyezni az [tartalom megosztása külső felhasználókkal](service-admin-portal.md#export-and-sharing-settings) funkció a Power BI felügyeleti portál vendégfelhasználók meghívása előtt.

Is használhatja a [külső vendégfelhasználóknak szerkeszthetik és kezelhetik a szervezeten belüli tartalom engedélyezése](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) funkció. Lehetővé teszi, hogy melyik vendégfelhasználó tekintse meg, és a tartalom létrehozása a munkaterületeken, beleértve a szervezet a Power BI-böngészés válassza.

## <a name="who-can-you-invite"></a>Kit lehet meghívni?

Meghívhat vendégfelhasználókat bármely e-mail címmel, közöttük személyes fiókokkal például hotmail.com, gmail.com és Outlook.com-os. Az Azure AD B2B meghívja ezeket a címeket *közösségi identitások*.

## <a name="invite-guest-users"></a>Vendégfelhasználók meghívása

Vendégfelhasználók csak szükség meghívók először felkéri őket a szervezet számára. Felhasználó meghívása kétféleképpen: tervezett szóló meghívásokról tájékoztató és ad-hoc meghívók.

### <a name="planned-invites"></a>Tervezett meghívások

Abban az esetben válassza a tervezett meghívási módot, ha már tudja, mely felhasználókat szeretné meghívni. Meghívót az Azure Portal vagy a PowerShell használatával küldhet. A meghíváshoz bérlői rendszergazdának kell lennie.

Meghívó az Azure Portalon való küldéséhez kövesse az alábbi lépéseket.

1. Az [Azure Portalon](https://portal.azure.com) válassza az **Azure Active Directory** lehetőséget.

1. A **kezelés**válassza **felhasználók** > **minden felhasználó** > **új vendégfelhasználó**.

    ![Képernyőkép az Azure Portalon, a Vendég felhasználó új lehetőség a kiemeltük.](media/service-admin-azure-ad-b2b/azure-ad-portal-new-guest-user.png)

1. Adja meg az **e-mail-címet** és egy **személyes üzenetet**.

    ![Képernyőkép az Azure AD Portal új vendégfelhasználó párbeszédpanelről.](media/service-admin-azure-ad-b2b/azure-ad-portal-invite-message.png)

1. Kattintson a **Meghívás** lehetőségre.

Ha egynél több vendéget szeretne meghívni, használja a PowerShellt. Ha további információra van szüksége, tekintse át az [Azure AD B2B együttműködési kódmintát és PowerShell-példákat](/azure/active-directory/b2b/code-samples/) tartalmazó cikket.

A vendégfelhasználónak az e-mailben kapott meghívóban rá kell majd kattintania az **Első lépések** (Get Started) lehetőségre. A rendszer ezután hozzá fogja adni a vendégfelhasználót a bérlőhöz.

![Képernyőfelvétel: a Vendég felhasználói e-mailes meghívót.](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>Az ad hoc meghívások

Egy külső felhasználó meghívása tetszőleges időpontban, adja hozzá őket az irányítópultjához vagy jelentéséhez a megosztási felületen, illetve az alkalmazásához a hozzáférési lapon. Az alábbi példán látható, hogy mi a teendő, amikor külső felhasználót hív meg egy alkalmazás használatára.

![A Power BI alkalmazás-hozzáférési listához hozzáadott képernyőképen külső felhasználó.](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

A vendégfelhasználó fog kapni egy e-mailt, amely azt jelzi, hogy az alkalmazás velük megosztott.

![Képernyőkép az e-mailben vendégfelhasználóval megosztott alkalmazásról](media/service-admin-azure-ad-b2b/guest-user-invite-email-2.png)

A vendégfelhasználónak a céges e-mail-címével kell bejelentkeznie. Fogadja el a meghívást, a bejelentkezést követően felszólítást kap. Bejelentkezés után az alkalmazás megnyílik a meghívott felhasználónak. Ahhoz, hogy később visszaléphessen az alkalmazásba, könyvjelzőzheti a hivatkozást vagy elmentheti az e-mailt.

## <a name="licensing"></a>Licencelés

A meghívott felhasználónak rendelkeznie kell a megfelelő licencre megosztott tartalmak megtekintéséhez. Győződjön meg arról, hogy a megfelelő licenccel rendelkező három módja van: a Power BI Premium használja, a Power BI Pro licenc hozzárendelése vagy a Vendég a Power BI Pro-licenccel.

Az [Annak engedélyezése, hogy külső vendégfelhasználók is szerkeszthessék és kezelhessék a szervezeti tartalmakat](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) funkció használatakor a munkaterületekhez tartalmat adó vagy másokkal tartalmat megosztó vendégfelhasználóknak Power BI Pro-licencre van szüksége.

### <a name="use-power-bi-premium"></a>Prémium szintű Power BI használata

Az alkalmazás-munkaterületét a [Power BI Premium-kapacitás](service-premium-what-is.md) lehetővé teszi, hogy a meghívott felhasználónak az alkalmazás használata a Power BI Pro-licenc nélkül. A Power BI Premium is lehetővé teszi alkalmazások, például a nagyobb gyakoribb frissítéseket, dedikált kapacitást és nagy modellméretet egyéb képességek előnyeit.

![Vendég felhasználói élmény a Power BI Premium diagramja.](media/service-admin-azure-ad-b2b/license-approach-1.png)

### <a name="assign-a-power-bi-pro-license-to-guest-user"></a>Power BI Pro-licenc hozzárendelése a vendégfelhasználóhoz

Power BI Pro-licenc hozzárendelése a vendégfelhasználóhoz a bérlőn belül való lehetővé teszi, hogy a Vendég felhasználói tartalom megtekintése a bérlőben.

![Rendelje hozzá a Pro-licenccel rendelkező Vendég felhasználói élmény diagramja.](media/service-admin-azure-ad-b2b/license-approach-2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>A vendégfelhasználók hozzák saját Power BI Pro-licencüket

A vendégfelhasználó saját bérlőjén már rendelkezik Power BI Pro-licenccel.

![Vendég felhasználói élményt, amikor azok a saját licenc használata diagramja.](media/service-admin-azure-ad-b2b/license-approach-3.png)

## <a name="guest-users-who-can-edit-and-manage-content"></a>Tartalom szerkesztésére és kezelésére jogosult vendégfelhasználók 

Használatakor a [külső vendégfelhasználóknak szerkeszthetik és kezelhetik a szervezeten belüli tartalom engedélyezése](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) funkció, a megadott vendég felhasználók is hozzáférhetnek a szervezet Power bi-bA. Megjelenik az bármilyen tartalmat, amely engedéllyel rendelkeznek. Megtekinthetik kezdőlap eléréséhez, keresse meg a munkaterületek, alkalmazások telepítése, hogy hol vannak a hozzáférési listán, és munkaterületek tartalmat közreműködőként. Létrehozhatnak olyan munkaterületeket, illetve ezek rendszergazdái lehetnek, amelyek az új munkaterületi felületet alkalmazzák. Bizonyos korlátozások érvényesek. A szempontok és korlátozások szakaszban korlátozások listája.
 
Annak érdekében, jelentkezzen be a Power BI ezeket a felhasználókat, adja meg azokat a bérlői URL-címet. A bérlői URL-cím megkereséséhez kövesse az alábbi lépéseket.

1. A Power BI szolgáltatásban a felső menüből válassza ki a Súgó ( **?** ), majd **A Power BI bemutatása** lehetőséget.

2. A **Bérlői URL-cím** melletti értékre van szüksége. A bérlői URL-címet, megoszthatja a vendégfelhasználók értéke.

    ![Képernyőfelvétel: a Power BI névjegye párbeszédpanel a Vendég felhasználó bérlői URL-cím kiemeltük.](media/service-admin-azure-ad-b2b/power-bi-about-dialog.png)

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások

* Alapértelmezés szerint a külső Azure AD B2B korlátozza a tartalomhoz csak a vendégek. Külső Azure AD B2B-vendégek megtekintheti az alkalmazásokat, irányítópultokat, jelentéseket, adatok exportálása és e-mailes feliratkozások irányítópultok és jelentések készítése. Nem férhetnek hozzá azonban munkaterületekhez, és nem tehetik közzé saját tartalmaikat. Azonban nem vonatkoznak ezek a korlátozások vendégfelhasználók számára keresztül hozzáférhet a [külső vendégfelhasználóknak szerkeszthetik és kezelhetik a szervezeten belüli tartalom engedélyezése](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) funkció.

* A vendégfelhasználók számára keresztül engedélyezhető a [külső vendégfelhasználóknak szerkeszthetik és kezelhetik a szervezeten belüli tartalom engedélyezése](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) funkció, bizonyos elemek nem érhetők el hozzájuk. Jelentések frissítéséhez vagy közzétételéhez nekik a Power BI szolgáltatás webes felületét kell használniuk, így a Power BI Desktop-fájlok feltöltéséhez az Adatok lekérése lehetőséget.  A következő funkciókat nem támogatottak:
    * Közvetlen közzététel a Power BI Desktopból a Power BI szolgáltatásba
    * Vendégfelhasználók nem csatlakozhat a Power BI desktop szolgáltatás adatkészleteket a Power BI szolgáltatásban
    * Office 365-csoportokhoz kötött klasszikus munkaterületek:
        * A vendégfelhasználók nem hozhatók létre, és ezek a munkaterületek rendszergazdái lehet
        * Vendég felhasználók is lehetnek tagjai
    * Ad-hoc meghívók küldését munkaterület hozzáférés listák esetében nem támogatott
    * Excelhez készült Power BI Publisher nem támogatott a vendégfelhasználók számára
    * Vendégfelhasználók nem tudja telepíteni a Power BI Gateway, és csatlakoztassa a szervezet
    * Vendég felhasználók nem telepíthetnek alkalmazásokat közzétenni a teljes szervezet számára
    * Vendégfelhasználók nem használja, létrehozása, frissítése vagy telepítése vállalati tartalomcsomagok
    * Vendég felhasználók nem használhatnak az elemzés az Excelben
    * Nem lehet a vendégfelhasználók @mentioned a megjegyzéseket
    * Vendég felhasználók nem használhatják az előfizetéseket
    * Azon vendégfelhasználóknak, akik ezt a funkciót veszik igénybe, munkahelyi vagy iskolai fiókkal kell rendelkezniük. Személyes fiókot használó vendégfelhasználókat tapasztalható további korlátozások miatt a korlátozások bejelentkezni.

* Ez a funkció jelenleg nem érhető el a Power BI SharePoint Online jelentéskijelzővel.

* Nincsenek külső vendég felhasználók mit tehetnek a teljes szervezetben korlátozni tudja Active Directory-beállítások. Amely a a Power BI-környezetbe is vonatkozik. Ezeket a beállításokat a következő dokumentáció ismerteti:
    * [Külső együttműködési beállítások kezelése](https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations#control-who-can-invite)
    * [Adott szervezetek B2B-felhasználók felé irányuló meghívásainak engedélyezése vagy letiltása](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)  

## <a name="next-steps"></a>Következő lépések

További részletes információ, beleértve a sorszintű biztonság működik tekintse meg a tanulmány megnyitása: [Power BI-tartalmak terjesztése Azure AD B2B külső vendégfelhasználóinak](https://aka.ms/powerbi-b2b-whitepaper).

Az Azure AD B2B kapcsolatos információkért lásd: [Mi az Azure AD B2B együttműködés?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b/).
