---
title: Power BI Pro-licencek vásárlása és kiosztása
description: Megtudhatja, hogyan vásárolhat felhasználói Power BI Pro-licenceket, illetve hogyan oszthatja ki azokat, hogy felhasználók hozzáférhessenek a tartalomhoz, és együttműködhessenek a munkatársaikkal a Power BI szolgáltatásban.
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: quickstart
ms.date: 10/29/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 72a158e2dca32d2199fcd48e2cc37bf4c90778ea
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73873547"
---
# <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Felhasználói Power BI Pro-licencek vásárlása és kiosztása

A Power BI Pro egyéni felhasználói licenc, amely lehetővé teszi, hogy a felhasználók más felhasználók által a Power BI szolgáltatásban közzétett jelentéseket és irányítópultokat olvassanak és kezeljenek, valamint tartalmat osszanak meg, és más Power BI Pro-felhasználókkal működjenek együtt. Tartalmat csak Power BI Pro-licenccel rendelkező felhasználók tehetnek közzé vagy oszthatnak meg más felhasználókkal, és csak ők használhatnak más felhasználók által létrehozott tartalmat, kivéve akkor, ha a tartalom Power BI Premium-kapacitásban van üzemeltetve. További információ: [Power BI-szolgáltatások licenctípus szerint](service-features-license-type.md).

## <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Felhasználói Power BI Pro-licencek vásárlása és kiosztása

Ez a cikk a felhasználói Power BI Pro licenceknek a Microsoft 365 Felügyeleti központban való megvásárlását ismerteti, valamint bemutatja azt a két módot, ahogyan a rendszergazdák kioszthatják ezeket a licenceket az egyes felhasználóknak: a Microsoft 365 Felügyeleti központban és az Azure Portalon (egy lehetőség választható).

### <a name="prerequisites"></a>Előfeltételek

Ahhoz, hogy licenceket vásároljon vagy osszon ki a Microsoft 365 Felügyeleti központban, **[globális rendszergazdai vagy számlázási adminisztrátor](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)** szerepkörrel kell rendelkeznie a Microsoft 365-ben.

A licencek Azure Portalon való kiosztásához a Power BI által az Azure Active Directory-keresésekhez használt Azure-előfizetés tulajdonosának kell lennie.

### <a name="purchase-licenses-in-microsoft-365"></a>Licencek vásárlása a Microsoft 365-ben

Kövesse az alábbi lépéseket a Power BI Pro licenceknek a Microsoft 365 Felügyeleti központban történő megvásárlásához:

1. Nyissa meg a [Microsoft 365 Felügyeleti központot](https://portal.office.com/adminportal/home#/homepage).

2. A navigációs panelen kattintson a **Számlázás** > **Előfizetések** lehetőségre.

    ![Navigációs ablaktábla](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-01.png)

3. Az **Előfizetések** lap jobb felső sarkában kattintson az **Előfizetések felvétele** gombra.

    ![Előfizetés](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-02.png)

4. Keresse meg a kívánt előfizetési ajánlatot:

    Válassza a **Nagyvállalati csomag** csoportban az **Office 365 Nagyvállalati E5 csomag** lehetőséget.

    ![Office E5 csomagra szóló előfizetés](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-03.png)

    Válassza az **Egyéb csomagok** csoportban a **Power BI Pro** lehetőséget.

    ![Power BI-előfizetés](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-04.png)

5. Mutasson a kívánt előfizetéshez tartozó három pontra ( **. . .** ), majd válassza a **Vásárlás** lehetőséget.

    ![Vásárlás](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-05.png)

6. Válassza a **Fizetés havonta** vagy a **Fizetés egy teljes évre** lehetőséget a számlázási igényeinek megfelelően.

7. A **Hány felhasználóra van szüksége?** területen adja meg a licencek kívánt számát, válassza a **Fizetés most** lehetőséget, majd fejezze be a tranzakciót.

8. Ellenőrizze, hogy a beszerzett előfizetés megjelenik-e az **Előfizetések** lap listájában.

   ![Beszerzett előfizetés](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-06.png)

9. Ha az eredeti vásárlás után további licenceket szeretne hozzáadni, az **Előfizetések** oldalon válassza a **Power BI Pro** lehetőséget, majd válassza a **Licencek hozzáadása/eltávolítása** elemet.

### <a name="assign-licenses-in-the-microsoft-365-admin-center"></a>Licencek kiosztása a Microsoft 365 Felügyeleti központban

Az alábbi lépésekkel rendelheti hozzá a Power BI Pro-licenceket egyéni felhasználói fiókokhoz:

1. Nyissa meg a [Microsoft 365 Felügyeleti központot](https://portal.office.com/adminportal/home#/homepage).

2. A navigációs panelen válassza a **Felhasználók**, majd az **Aktív felhasználók** lehetőséget.

    ![Aktív felhasználók](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-05.png)

3. Válasszon ki egy felhasználót, majd a **Terméklicencek** területen válassza a **Szerkesztés** lehetőséget.

    ![Terméklicencek szerkesztése](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-06.png)

4. A **Power BI Pro** területen állítsa a kapcsolót **Be** állásra, majd kattintson a **Mentés** gombra.

    ![Terméklicencek bekapcsolva](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-07.png)

5. Az **Állapot** oszlopban ellenőrizze, hogy a kijelölt fiókhoz sikeresen hozzá lett-e rendelve a Power BI Pro-licenc.

    ![Licenc állapotának ellenőrzése](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-08.png)

### <a name="assign-licenses-in-the-azure-portal"></a>Licencek kiosztása az Azure Portalon

Az alábbi lépésekkel rendelheti hozzá a Power BI Pro-licenceket egyéni felhasználói fiókokhoz:

1. Nyissa meg az [Azure Portalt](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/dashboard/private/39bc3cf7-31a4-43f6-954c-f2d69ca2f0).

2. A navigációs panelen válassza az **Azure Active Directory** lehetőséget.

    ![Azure Active Directory](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-01.png)

3. Az **Azure Active Directory** alatt válassza a **Licencek** lehetőséget.

    ![Licencek](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-02.png)

4. A **Licencek** alatt válassza a **Minden termék**, majd a **Power BI Pro** lehetőséget a licenccel rendelkező felhasználók listájának megjelenítéséhez.

    ![Licencek – Minden termék](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-03.png)

5. Power BI Pro-licenc felhasználó fiókhoz való hozzáadásához válassza **Hozzárendelés** lehetőséget.

    ![Licenc hozzárendelése](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-04.png)

## <a name="next-steps"></a>Következő lépések

Javasoljuk, hogy a licencek hozzárendelése után ismerkedjen meg közelebbről is a Power BI Pro használatával.

[Szervezeti Power BI-licencelés](service-admin-licensing-organization.md)

[Bejelentkezett Power BI-felhasználók keresése](service-admin-access-usage.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
