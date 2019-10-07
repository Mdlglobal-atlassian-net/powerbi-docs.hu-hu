---
ms.openlocfilehash: 6e48713315b23cf322b635f1650374251b639e4f
ms.sourcegitcommit: bbd9b38f30a4ca5cb8072496c9cacb635b03aa88
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71409366"
---
## <a name="define-roles-and-rules-in-power-bi-desktop"></a>Szerepkörök és szabályok definiálása a Power BI Desktopban
A Power BI Desktopban meghatározhat szerepköröket és szabályokat. Amikor közzéteszi a tartalmakat a Power BI-ban, a szerepkör-definíciók is közzé lesznek téve.

Biztonsági szerepkörök definiálásához kövesse az alábbi lépéseket.

1. Importálhatja az adatokat a Power BI Desktop-jelentésbe, vagy konfigurálhat egy DirectQuery-kapcsolatot.
   
   > [!NOTE]
   > A Power BI Desktopon belül nem definiálhat szerepköröket az Analysis Services élő kapcsolataihoz. Ezt az Analysis Services-modellben kell megtennie.
   > 
   > 
1. Válassza a **Modellezés** lapot.
2. Válassza a **Szerepkörök kezelése** lehetőséget.
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security.png)
4. Kattintson a **Létrehozás** gombra.
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security-create-role.png)
5. Adja meg a szerepkör nevét. 
6. Válassza ki a táblát, amelyen alkalmazni kívánja a DAX-szabályt.
7. Adja meg a DAX-kifejezéseket. A kifejezésnek igaz vagy hamis eredményt kell adnia. Például: [Entitásazonosító] = „Érték”.
   
   > [!NOTE]
   > A kifejezésben használhatja a *username()* függvényt. Ne feledje, hogy a Power BI Desktopban a *username()* a *TARTOMÁNY\felhasználónév* formátumot követi. A Power BI szolgáltatásban és a Power BI jelentéskészítő kiszolgálóban a felhasználó felhasználói nevének (UPN) formátumában van. Használhatja a *userprincipalname()* függvényt is, amely a felhasználót minden esetben az egyszerű felhasználónevével adja vissza: *felhasználónév\@contoso.com*.
   > 
   > 
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security-create-rule.png)
8. Miután összeállította a DAX-kifejezést, a Kifejezés mező fölötti pipára kattintva ellenőrizheti azt.
      
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security-validate-dax.png)
   
   > [!NOTE]
   > Ebben a kifejezésmezőben akkor is vesszőkkel kell elválasztania a DAX-függvény argumentumait, ha a területi beállítás (például francia vagy német) egyébként pontosvesszőt használ elválasztóként. 
   >
   >
   
9. Kattintson a **Mentés** gombra.

A Power BI Desktopban nem rendelhet felhasználókat a szerepkörökhöz. Ezt a Power BI szolgáltatásban teheti meg. A dinamikus biztonság engedélyezéséhez használja a Power BI Desktopban a *username()* vagy a *userprincipalname()* DAX-függvényt, és konfigurálja a megfelelő kapcsolatokat. 

