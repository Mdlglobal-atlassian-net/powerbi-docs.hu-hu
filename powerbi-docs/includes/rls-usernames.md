---
ms.openlocfilehash: 3e89344ef1298864b485f465b28c56397a7e1511
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61193813"
---
## <a name="using-the-username-or-userprincipalname-dax-function"></a>A username() és a usernameprincipal() DAX-függvény használata
A *username()* és a *usernameprincipal()* DAX-függvény felhasználható az adatkészletben. Használható a Power BI Desktopban megadott kifejezésekben is. A modell közzétételekor a Power BI szolgáltatásban lesznek felhasználva.

A Power BI Desktopban a *username()* a felhasználót adja eredményül *TARTOMÁNY\Felhasználó* formátumban, a *userprincipalname()* pedig <em>user@contoso.com</em> formátumban.

A Power BI szolgáltatásban a *username()* és a *userprincipalname()* eredménye egyaránt a felhasznál egyszerű felhasználóneve (UPN) lesz. Ez egy e-mail-címhez hasonlít.

