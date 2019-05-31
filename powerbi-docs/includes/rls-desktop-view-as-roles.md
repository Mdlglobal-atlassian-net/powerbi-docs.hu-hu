---
ms.openlocfilehash: eb7cba03daee47f6772fc46be50419731b41765e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61193838"
---
## <a name="validate-the-roles-within-power-bi-desktop"></a>Szerepkörök érvényesítése a Power BI Desktopban
A szerepkör létrehozása után tesztelheti a szerepkör hatásait a Power BI Desktopban.

1. Válassza a **Megtekintés szerepkörökként** lehetőséget. 

    ![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles.png)

    A **Megtekintés szerepkörökként** alatt megjelennek a létrehozott szerepkörök.

    ![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles-dialog.png)

3. A szerepkör alkalmazásához válassza ki a létrehozott szerepkört > **OK**. A jelentés csak a szerepkör számára releváns adatot jeleníti meg. 

4. Az **Egyéb felhasználó** beállítással egy adott felhasználót is kiválaszthat. Az egyszerű felhasználónevet (UPN) érdemes megadni, mivel a Power BI szolgáltatás és a Power BI jelentéskészítő kiszolgáló azt használja.

    ![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-other-user.png)

1. Kattintson az **OK** gombra, és a jelentések csak a felhasználó számára elérhető adatokat fogják megjeleníteni. 

A Power BI Desktopban a **Más felhasználók** alatt csak akkor fognak megjelenni különböző eredmények, ha DAX-kifejezéseken alapuló dinamikus biztonsági megoldást alkalmaz. 

