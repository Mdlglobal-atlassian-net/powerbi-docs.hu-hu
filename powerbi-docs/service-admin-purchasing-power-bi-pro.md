---
title: Power BI Pro-licencek vásárlása és kiosztása
description: Megtudhatja, hogyan vásárolhat Power BI Pro-licenceket, illetve hogyan oszthatja ki azokat, hogy felhasználói a Power BI szolgáltatás minden tartalmához és funkciójához hozzáférhessenek.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: quickstart
ms.date: 10/21/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 76288ca77f184b27b5839377190a1708c69567af
ms.sourcegitcommit: a36f82224e68fdd3489944c9c3c03a93e4068cc5
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/31/2019
ms.locfileid: "55430694"
---
# <a name="purchase-and-assign-power-bi-pro-licenses"></a>Power BI Pro-licencek vásárlása és kiosztása

A Power BI Pro egyéni licenc, amely hozzáférést biztosít a Power BI szolgáltatásban minden tartalomhoz és funkcióhoz, többek között megosztható a tartalom, és lehetőség van más Pro-felhasználókkal való együttműködésre is. Csak a Pro szintű felhasználók tehetnek közzé és használhatnak tartalmat alkalmazás-munkaterületeken, oszthatnak meg irányítópultokat, és iratkozhatnak fel irányítópultokra és jelentésekre. További információ: [Power BI-szolgáltatások licenctípus szerint](service-features-license-type.md).

Ez a cikk elsőként azt ismerteti, hogyan vásárolhat Power BI Pro-licenceket az Office 365-ben. A cikk ezután két lehetőséget mutat be a licencek egyéni felhasználókhoz való hozzárendeléséhez: az Office 365-öt és az Azure-t (válassza ki az egyik lehetőséget).

## <a name="prerequisites"></a>Előfeltételek

Az Office 365-ben [**globális rendszergazdai** vagy **Számlázási rendszergazdai**](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d) szerepkörrel kell rendelkeznie.

A licencek az Azure-ban való hozzárendeléséhez a Power BI által az Active Directory-keresésekhez használt Azure-előfizetés tulajdonosának kell lennie.

## <a name="purchase-licenses-in-office-365"></a>Licencek vásárlása az Office 365-ben

Kövesse az alábbi lépéseket a Power BI Pro megvásárlásához:

1. Nyissa meg az [Office 365 Felügyeleti központot](https://portal.office.com/adminportal/home#/homepage).

2. A bal oldali navigációs ablaktáblán kattintson a **Számlázás** > **Előfizetések** lehetőségre.

    ![Navigációs panel](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-01.png)

3. Az **Előfizetések** lap jobb felső sarkában kattintson az **Előfizetések felvétele** gombra.

    ![Előfizetés](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-02.png)

4. Keresse meg a kívánt előfizetési ajánlatot:

    Válassza a **Nagyvállalati csomag** csoportban az **Office 365 Nagyvállalati E5 csomag** lehetőséget.

    ![Office E5 csomagra szóló előfizetés](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-03.png)

    Válassza az **Egyéb csomagok** csoportban a **Power BI Pro** lehetőséget.

    ![Power BI-előfizetés](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-04.png)

5. Mutasson a kívánt előfizetéshez tartozó három pontra (**. . .**), majd válassza a **Vásárlás** lehetőséget.

    ![Vásárlás](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-05.png)

6. Válassza a **Fizetés havonta** vagy a **Fizetés egy teljes évre** lehetőséget a számlázási igényeinek megfelelően.

7. A **Hány felhasználóra van szüksége?** területen adja meg a licencek kívánt számát, válassza a **Fizetés most** lehetőséget, majd fejezze be a tranzakciót.

8. Ellenőrizze, hogy a beszerzett előfizetés megjelenik-e az **Előfizetések** lap listájában.

   ![Beszerzett előfizetés](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-06.png)

9. Ha az eredeti vásárlás után további licenceket szeretne hozzáadni, az **Előfizetések** oldalon válassza a **Power BI Pro** lehetőséget, majd válassza a **Licencek hozzáadása/eltávolítása** elemet.

## <a name="assign-licenses-in-office-365"></a>Licencek kiosztása az Office 365-ben

Az alábbi lépésekkel rendelheti hozzá a Power BI Pro-licenceket egyéni felhasználói fiókokhoz:

1. Nyissa meg az [Office 365 Felügyeleti központot](https://portal.office.com/adminportal/home#/homepage).

2. A bal oldali navigációs panelen válassza a **Felhasználók**, majd az **Aktív felhasználók** lehetőséget.

    ![Aktív felhasználók](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-05.png)

3. Válasszon ki egy felhasználót, majd a **Terméklicencek** területen válassza a **Szerkesztés** lehetőséget.

    ![Terméklicencek szerkesztése](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-06.png)

4. A **Power BI Pro** területen állítsa a kapcsolót **Be** állásra, majd kattintson a **Mentés** gombra.

    ![Terméklicencek bekapcsolva](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-07.png)

5. Az **Állapot** oszlopban ellenőrizze, hogy a kijelölt fiókhoz sikeresen hozzá lett-e rendelve a Power BI Pro-licenc.

    ![Licenc állapotának ellenőrzése](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-08.png)

## <a name="assign-licenses-in-azure"></a>Licencek kiosztása az Azure-ban

Az alábbi lépésekkel rendelheti hozzá a Power BI Pro-licenceket egyéni felhasználói fiókokhoz:

1. Nyissa meg az [Azure Portalt](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/dashboard/private/39bc3cf7-31a4-43f6-954c-f2d69ca2f0).

2. A bal oldali navigációs sávon válassza az **Azure Active Directory** lehetőséget.

    ![Azure Active Directory](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-01.png)

3. Az **Azure Active Directory** alatt válassza a **Licencek** lehetőséget.

    ![Licencek](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-02.png)

4. A **Licencek** alatt válassza a **Minden termék**, majd a **Power BI Pro** lehetőséget a licenccel rendelkező felhasználók listájának megjelenítéséhez.

    ![Licencek – Minden termék](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-03.png)

5. Power BI Pro-licenc további felhasználói fiókhoz való rendeléséhez válassza a **Hozzárendelés** lehetőséget.

    ![Licenc hozzárendelése](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-04.png)

## <a name="next-steps"></a>Következő lépések

Javasoljuk, hogy a licencek hozzárendelése után ismerkedjen meg közelebbről is a Power BI Pro használatával.

[Szervezeti Power BI-licencelés](service-admin-licensing-organization.md)

[Bejelentkezett Power BI-felhasználók keresése](service-admin-access-usage.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
