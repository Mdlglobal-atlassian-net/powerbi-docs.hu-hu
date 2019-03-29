---
title: Azure Active Directory-bérlő létrehozása a Power BI szolgáltatással való használathoz
description: Ismerje meg, hogyan hozhat létre új Azure Active Directory-bérlőt (Azure AD-bérlőt) az egyéni alkalmazásokkal való használathoz a Power BI REST API-k segítségével.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 11/30/2017
ms.openlocfilehash: ec03ba86fdbf57a9898b127aae9b76990837b5ba
ms.sourcegitcommit: 9f31cd41bd92e398717da5a69a074273e8c6f8a6
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/26/2019
ms.locfileid: "58473844"
---
# <a name="create-an-azure-active-directory-tenant-to-use-with-power-bi"></a>Azure Active Directory-bérlő létrehozása a Power BI szolgáltatással való használathoz

Ismerje meg, hogyan hozhat létre új Azure Active Directory-bérlőt (Azure AD-bérlőt) az egyéni alkalmazásokkal való használathoz a Power BI REST API-k segítségével.

A bérlők a szervezetek képviselői az Azure Active Directoryban. Ez az Azure AD szolgáltatás egy dedikált példánya, amelyet a szervezetek megkapnak és a tulajdonukban áll, amikor regisztrálnak egy Microsoft-felhőszolgáltatásra, például az Azure, a Microsoft Intune vagy az Office 365 szolgáltatásra. Mindegyik Azure AD-bérlő önálló, és elkülönül a többi Azure AD-bérlőtől.

Ha már rendelkezik Azure AD-bérlővel, megadhat egy alkalmazást, és hozzárendelhet engedélyeket, így az alkalmazás használhatja a Power BI REST API-kat.

Lehet, hogy a szervezete már rendelkezik egy Azure AD-bérlővel, amelyet az alkalmazásához használhat. Használhatja azt a bérlőt, amelyre az alkalmazásnak szüksége van, vagy létrehozhat egy új bérlőt csak ehhez az alkalmazáshoz. Ez a cikk bemutatja egy új bérlő létrehozásának módját.

## <a name="create-an-azure-active-directory-tenant"></a>Azure Active Directory-bérlő létrehozása

A Power BI egyéni alkalmazásokba integrálásához meg kell adnia egy alkalmazást az Azure AD-ban. Ehhez egy címtárra van szüksége az Azure AD-ban. Ez az Ön bérlője. Ha a cége még nem rendelkezik bérlővel, mert nem használ Power BI-t vagy Office 365-öt, [létre kell hoznia egyet](https://docs.microsoft.com/azure/active-directory/develop/active-directory-howto-tenant). Akkor is létre kell hoznia egyet, ha nem szeretné az alkalmazást keverni a szervezet bérlőjével. Így elkülönítve tarthatja a dolgokat.

Vagy csak létrehozhat egy bérlőt tesztelési célra is.

Új Azure AD-bérlő létrehozásához tegye a következőket.

1. Nyissa meg az [Azure Portalt](https://portal.azure.com), és jelentkezzen be egy Azure-előfizetéssel rendelkező fiókkal.

2. Válassza ki a **plusz ikont (+)** és keresse meg az *Azure Active Directoryt*.

    ![Plusz ikon (+)](media/create-an-azure-active-directory-tenant/new-directory.png)

3. Válassza ki az **Azure Active Directoryt** a keresési eredmények közül.

    ![AAD-keresés](media/create-an-azure-active-directory-tenant/new-directory2.png)

4. Kattintson a **Létrehozás** gombra.

5. Adja meg a **szervezet nevét** a **kezdeti tartománynevet**. Ezután kattintson a **Létrehozás** elemre. Ezzel létrejön a címtár.

    ![Szervezet és a tartomány](media/create-an-azure-active-directory-tenant/organization-and-domain.png)

   > [!NOTE]
   > A kezdeti tartománynév az onmicrosoft.com része lesz. Egyéb tartományneveket később adhat hozzá. Egy bérlő címtára több hozzárendelt tartománnyal is rendelkezhet.

6. A címtár létrehozása után válassza az információs dobozt az új címtár kezeléséhez.

A címtár létrehozása megtörtént. Ezután hozzáadunk egy felhasználót a bérlőhöz.

## <a name="create-some-users-in-your-azure-active-directory-tenant"></a>Néhány felhasználó létrehozása az Azure Active Directory-bérlőben

Most, hogy már rendelkezésre áll a címtár, hozzunk létre legalább két felhasználót. Az egyik a bérlő globális rendszergazdája, a másik pedig a beágyazás fő felhasználója. Gondoljon erre úgy, mint egy szolgáltatásfiókra.

1. Győződjön meg arról, hogy az Azure Portal Azure Active Directory lapján tartózkodik.

    ![](media/create-an-azure-active-directory-tenant/aad-flyout.png)

    Ha más helyen van, válassza az Azure Active Directory ikont a bal oldali szolgáltatások sávon.

    ![](media/create-an-azure-active-directory-tenant/aad-service.png)
2. A **Kezelés** menüpontban válassza a **Felhasználók és csoportok** lehetőséget.

    ![](media/create-an-azure-active-directory-tenant/users-and-groups.png)
3. Válassza a **Minden felhasználó**, majd az **+ Új felhasználó** lehetőséget.
4. Adjon meg egy nevet és egy felhasználónevet ennek a felhasználónak. Ez lesz a bérlő globális rendszergazdája. Érdemes módosítani a **Címtárszerepkört** *Globális rendszergazdára*. Megjelenítheti az ideiglenes jelszót is. Ha elkészült, kattintson a **Létrehozás** gombra.

    ![](media/create-an-azure-active-directory-tenant/global-admin.png)

5. Célszerű ugyanezt megtenni a bérlő normál felhasználója esetében is. Ez használható a fő beágyazó fiókhoz is. Ezúttal a **Címtárszerepkört** *Felhasználó* értéken hagyjuk. Ügyeljen arra, hogy feljegyezze a jelszót. Ezután kattintson a **Létrehozás** elemre.

    ![](media/create-an-azure-active-directory-tenant/pbiembed-user.png)
6. Regisztráljon a Power BI-ra az 5. lépésben létrehozott felhasználói fiókkal. Ezt úgy teheti meg, hogy ellátogat a [powerbi.com](https://powerbi.microsoft.com/get-started/) oldalra, és kiválasztja a **Próbálja ki ingyen** lehetőséget a *Power BI – Felhőbeli együttműködés és megosztás* résznél.

    ![](media/create-an-azure-active-directory-tenant/try-powerbi-free.png)

    Amikor regisztrál, a rendszer felkéri a Power BI Pro 60 napig tartó, ingyenes kipróbálására. Elfogadhatja ezt, és pro felhasználóvá válhat. Most elkezdheti egy beágyazott megoldás fejlesztését is, ha ezt szeretné tenni.

   > [!NOTE]
   > Győződjön meg arról, hogy azzal az e-mail-címmel regisztrál, amelyet a felhasználói fiókhoz adott meg.

## <a name="next-steps"></a>További lépések

Most, hogy már rendelkezik Azure AD-bérlővel, használhatja ezt a bérlőt a Power BI-ben található elemek teszteléséhez, és/vagy továbbléphet a Power BI irányítópultok és jelentések alkalmazásba való beágyázáshoz. Elemek beágyazásával kapcsolatos további információk: [Power BI irányítópultok, jelentések és csempék beágyazása](embedding-content.md).

[Mi az az Azure AD-címtár?](https://docs.microsoft.com/azure/active-directory/active-directory-whatis)  
[Azure AD-bérlő beszerzése](https://docs.microsoft.com/azure/active-directory/develop/active-directory-howto-tenant)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
