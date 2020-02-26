---
ms.openlocfilehash: 8dc488a47ac2b5b4e7980b7404b2722b1120b6ab
ms.sourcegitcommit: cde65bb8b1bed1ee8cf512651afeb829ddc155de
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/19/2020
ms.locfileid: "77464404"
---
## <a name="validate-the-roles-within-power-bi-desktop"></a>Szerepkörök érvényesítése a Power BI Desktopban
A szerepkör létrehozása után tesztelheti a szerepkör hatásait a Power BI Desktopban.

1. A **Modellezés** lapon válassza a **Megtekintés szerepkörökként** elemet. 

    ![A Megtekintés szerepkörökként lehetőség kiválasztása](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles.png)

    Megnyílik a **Megtekintés szerepkörökként** ablak, ahol a létrehozott szerepkörök láthatók.

    ![A Megtekintés szerepkörökként ablak](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles-dialog.png)

3. A szerepkör alkalmazásához válassza ki a létrehozott szerepkört, majd válassza az **OK** lehetőséget. 

   A jelentés csak a szerepkör számára releváns adatot jeleníti meg.

4. Az **Egyéb felhasználó** beállítással egy adott felhasználót is kiválaszthat. 

    ![Az Egyéb felhasználó lehetőség kiválasztása](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-other-user.png)

   Az egyszerű felhasználónevet (UPN) érdemes megadni, mivel a Power BI szolgáltatás és a Power BI jelentéskészítő kiszolgáló azt használja.

   A Power BI Desktopban a **Más felhasználók** alatt csak akkor fognak megjelenni különböző eredmények, ha DAX-kifejezéseken alapuló dinamikus biztonsági megoldást alkalmaz. 

5. Válassza az **OK** lehetőséget. 

   A jelentés csak a felhasználó számára elérhető adatokat fogja megjeleníteni.



