---
title: Felhasználói Power BI-licencek megtekintése és kezelése
description: Útmutató a rendszergazdáknak a felhasználói Power BI-licencek szervezeten belüli megtekintéséhez és kezeléséhez.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/08/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: c3f0b536695f5ed126ddc82c9e1891d317ef953f
ms.sourcegitcommit: b2cb0b02bdc451bf11a92a68f2c4d560a811f563
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81447441"
---
# <a name="view-and-manage-power-bi-user-licenses"></a>Felhasználói Power BI-licencek megtekintése és kezelése

Ez a cikk azt ismerteti, hogyan használhatják a rendszergazdák a Microsoft 365 felügyeleti központot vagy az Azure Portalt felhasználói licencek megtekintésére és kezelésére.

> [!NOTE]
>
>A felhasználók rendelkezhetnek egyszerre egy hozzájuk rendelt (ingyenes) Power BI-licenccel és egy Power BI Pro-licenccel is. Ez akkor fordulhat elő, amikor egy felhasználó regisztrál egy ingyenes licencre, majd később hozzá rendelnek egy Power BI Pro-licencet is. Ebben az esetben a legmagasabb licencelési szint lesz érvényes.
>

## <a name="view-your-subscriptions"></a>Az előfizetések megtekintése

Az alábbi lépéseket követve ellenőrizheti, hogy a szervezet mely Power BI-előfizetésekkel rendelkezik.

1. Jelentkezzen be a [Microsoft 365 Felügyeleti központba](https://admin.microsoft.com).
2. A navigációs menüben válassza a **Számlázás** > **Termékek és Szolgáltatások** lehetőséget.

Ekkor megjelennek az aktív Power BI-előfizetések az összes többi előfizetéssel együtt. Előfordulhat, hogy váratlanul egy (ingyenes) Power BI-előfizetés is megjelenik itt.

  ![Ingyenes, felhasználó által aktivált Power BI-előfizetés](media/service-admin-manage-licenses/power-bi-free-user-activated.png)

Ez a típusú előfizetés akkor jön létre, ha a felhasználók az önkiszolgáló regisztrációt használták. További információt az [A Power BI a szervezetnél](https://docs.microsoft.com/microsoft-365/admin/misc/power-bi-in-your-organization?view=o365-worldwide) című cikkben talál.

## <a name="manage-user-licenses-in-microsoft-365"></a>Felhasználói licencek kezelése a Microsoft 365-ben

Ha a Microsoft 365 felügyeleti központot szeretné használni a felhasználói licencek kezeléséhez, tekintse meg az [Üzleti előfizetések és a számlázás dokumentációját](https://docs.microsoft.com/microsoft-365/commerce/?view=o365-worldwide).

## <a name="manage-user-licenses-in-azure-portal"></a>Felhasználói licencek kezelése az Azure Portalon

Az alábbi lépéseket követve megtekintheti és hozzárendelheti a Power BI-licenceket az Azure Portal használatával.

1. Jelentkezzen be az [Azure Portalra](https://portal.azure.com).

2. Keresse meg és válassza ki az **Azure Active Directoryt**.

3. Az Azure Active Directory erőforrásmenüjének **Kezelés** területén válassza a **Licencek** lehetőséget.

4. Válassza a **Minden termék** lehetőséget az erőforrásmenüben, majd válasszon ki egy Power BI-licenctípust a licenccel rendelkező felhasználók listájának megjelenítéséhez.

5. Licenc hozzárendeléséhez a parancssorból válassza a **+ Hozzárendelés** lehetőséget. A **Licenc hozzárendelése** lapon válasszon ki egy felhasználót, majd válassza a **Hozzárendelési beállításokat**, hogy bekapcsolhasson egy Power BI licencet a kiválasztott felhasználói fiókhoz.

6. A licencek eltávolításához jelölje be a felhasználó neve melletti jelölőnégyzetet, majd válassza a **Licenc eltávolítása** lehetőséget.

## <a name="next-steps"></a>Következő lépések

- [A Power BI Pro megvásárlása](../service-admin-purchasing-power-bi-pro.md)
- [Szervezeti licencelés](../service-admin-licensing-organization.md)
