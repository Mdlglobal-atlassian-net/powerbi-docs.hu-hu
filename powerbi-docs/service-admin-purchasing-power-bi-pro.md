---
title: Power BI Pro-licencek vásárlása és kiosztása
description: Megtudhatja, hogyan vásárolhat felhasználói Power BI Pro-licenceket, illetve hogyan oszthatja ki azokat, hogy felhasználók hozzáférhessenek a tartalomhoz, és együttműködhessenek a munkatársaikkal a Power BI szolgáltatásban.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: quickstart
ms.date: 12/18/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 01eb30857b0b76f96e7e18115d92fb1d68dbef0c
ms.sourcegitcommit: 02b05932a119527f255e1eacc745a257044e392f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75223822"
---
# <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Felhasználói Power BI Pro-licencek vásárlása és kiosztása

A Power BI Pro egyéni felhasználói licenc, amely lehetővé teszi, hogy a felhasználók más felhasználók által a Power BI szolgáltatásban közzétett jelentéseket és irányítópultokat olvassanak és kezeljenek, valamint tartalmat osszanak meg, és más Power BI Pro-felhasználókkal működjenek együtt. Tartalmat csak Power BI Pro-licenccel rendelkező felhasználók tehetnek közzé vagy oszthatnak meg más felhasználókkal, és csak ők használhatnak más felhasználók által létrehozott tartalmat, kivéve akkor, ha a tartalom Power BI Premium-kapacitásban van üzemeltetve. További információt a [Power BI díjszabása](https://powerbi.microsoft.com/pricing/) témakör _Power BI-funkciók összehasonlítása_ szakaszában talál.

## <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Felhasználói Power BI Pro-licencek vásárlása és kiosztása

Ez a cikk a felhasználói Power BI Pro licenceknek a Microsoft 365 Felügyeleti központban való megvásárlását ismerteti, valamint bemutatja azt a két módot, ahogyan a rendszergazdák kioszthatják ezeket a licenceket az egyes felhasználóknak: a Microsoft 365 Felügyeleti központban és az Azure Portalon (egy lehetőség választható).

### <a name="prerequisites"></a>Előfeltételek

Ahhoz, hogy licenceket vásároljon vagy osszon ki a Microsoft 365 Felügyeleti központban, **[globális rendszergazdai vagy számlázási adminisztrátor](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)** szerepkörrel kell rendelkeznie a Microsoft 365-ben.

A licencek Azure Portalon való kiosztásához a Power BI által az Azure Active Directory-keresésekhez használt Azure-előfizetés tulajdonosának kell lennie.

### <a name="purchase-licenses-in-microsoft-365"></a>Licencek vásárlása a Microsoft 365-ben

Kövesse az alábbi lépéseket a Power BI Pro licenceknek a Microsoft 365 Felügyeleti központban történő megvásárlásához:

1. Nyissa meg a [Microsoft 365 Felügyeleti központot](https://portal.office.com/adminportal/home#/homepage).

2. A navigációs panelen válassza a **Számlázás**, majd az **Előfizetések** lehetőséget.

3. Az **Előfizetések** lap jobb felső sarkában kattintson az **Előfizetések felvétele** gombra.

4. Keresse meg a kívánt előfizetési ajánlatot:

    - Válassza a **Nagyvállalati csomag** csoportban az **Office 365 Nagyvállalati E5 csomag** lehetőséget.

    - Válassza az **Egyéb csomagok** csoportban a **Power BI Pro** lehetőséget.

5. Mutasson a kívánt előfizetéshez tartozó három pontra ( **. . .** ), majd válassza a **Vásárlás** lehetőséget.

6. Válassza a **Fizetés havonta** vagy a **Fizetés egy teljes évre** lehetőséget a számlázási igényeinek megfelelően.

7. A **Hány felhasználóra van szüksége?** területen adja meg a licencek kívánt számát, válassza a **Fizetés most** lehetőséget, majd fejezze be a tranzakciót.

8. Ellenőrizze, hogy a beszerzett előfizetés megjelenik-e az **Előfizetések** lap listájában.

9. Ha az eredeti vásárlás után további licenceket szeretne hozzáadni, az **Előfizetések** oldalon válassza a **Power BI Pro** lehetőséget, majd válassza a **Licencmennyiség módosítása** elemet.

### <a name="assign-licenses-in-the-microsoft-365-admin-center"></a>Licencek kiosztása a Microsoft 365 Felügyeleti központban

A licencek Microsoft 365 felügyeleti központban való hozzárendelésével kapcsolatos információkért lásd: [Licencek kiosztása a felhasználók számára](/office365/admin/manage/assign-licenses-to-users).

A vendégfelhasználókkal kapcsolatban tekintse meg a [Licencek kiosztása felhasználók számára a Licencek oldalon](/office365/admin/manage/assign-licenses-to-users#assign-licenses-to-users-on-the-licenses-page) című témakört. Mielőtt Pro-licenceket rendelne a vendégfelhasználókhoz, forduljon a Microsoft-fiók képviselőjéhez, és ellenőrizze, hogy megfelel-e Ön a Microsofttal kötött szerződés feltételeinek.

### <a name="assign-licenses-in-the-azure-portal"></a>Licencek kiosztása az Azure Portalon

Az alábbi lépésekkel rendelheti hozzá a Power BI Pro-licenceket egyéni felhasználói fiókokhoz:

1. Nyissa meg az [Azure Portalt](https://portal.azure.com/).

2. Keresse meg és válassza ki az **Azure Active Directoryt**.

3. Az **Azure Active Directory** alatt válassza a **Licencek** lehetőséget.

4. A **Licencek** alatt válassza a **Minden termék**, majd a **Power BI Pro** lehetőséget a licenccel rendelkező felhasználók listájának megjelenítéséhez.

5. Power BI Pro-licenc felhasználó fiókhoz való hozzáadásához válassza **Hozzárendelés** lehetőséget.

## <a name="next-steps"></a>Következő lépések

Javasoljuk, hogy a licencek hozzárendelése után ismerkedjen meg közelebbről is a Power BI Pro használatával.

[Szervezeti Power BI-licencelés](service-admin-licensing-organization.md)

[Bejelentkezett Power BI-felhasználók keresése](service-admin-access-usage.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
