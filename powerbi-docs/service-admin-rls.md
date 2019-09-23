---
title: Sorszintű biztonság (RLS) a Power BI-ban
description: Útmutató az importált adatkészletek és a DirectQuery sorszintű biztonságának konfigurálásához a Power BI szolgáltatásban.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.author: mblythe
ms.date: 09/09/2019
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: 04a8c8a08d885427e9de43b719674fce4ac2ebbd
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71074852"
---
# <a name="row-level-security-rls-with-power-bi"></a>Sorszintű biztonság (RLS) a Power BI-ban

A sorszintű biztonság (RLS) a Power BI-ban az adott felhasználók adatokhoz való hozzáférésének korlátozására használható. A szűrők a sorok szintjén korlátozzák az adatok elérését, és szerepkörökön belül határozhat meg szűrőket. Vegye figyelembe, hogy a Power BI szolgáltatásban a munkaterület tagjai hozzáférnek az adatkészletekhez a munkaterületen. Az RLS nem korlátozza ezt az adathozzáférést.

Konfigurálhat RLS-t a Power BI Desktoppal a Power BI-ba importált adatmodellekhez. Ezen kívül konfigurálhat RLS-t a DirectQueryt használó adatkészletekhez, például az SQL Serverhez is. Korábban csak a Power BI szolgáltatáson kívül, a helyszíni Analysis Services-modellekben lehetett RLS-t beállítani. Az Analysis Services élő kapcsolataihoz a helyszíni modellen konfigurálhatja a sorszintű biztonságot. Az élő kapcsolatok adatkészleteinél nem fog megjelenni a biztonsági beállítás.

[!INCLUDE [include-short-name](./includes/rls-desktop-define-roles.md)]

A sorszintű biztonsági szűrés alapbeállítás szerint egyirányú szűrőket alkalmaz, függetlenül attól, hogy a kapcsolatok egy- vagy kétirányúra vannak-e beállítva. A sorszintű biztonsági szűrés kétirányú keresztszűrését manuálisan lehet beállítani. Ehhez válassza ki a kapcsolatot, és jelölje be a **Biztonsági szűrés alkalmazása mindkét irányban** lehetőséget. Ezt a jelölőnégyzetet akkor javasolt bejelölnie, ha dinamikus sorszintű biztonságot is alkalmazott a kiszolgáló szintjén, ahol a sorszintű biztonság alapja a felhasználónév vagy a bejelentkezési azonosító.

További információt a [Kétirányú keresztszűrés a DirectQuery használatával a Power BI Desktopban](desktop-bidirectional-filtering.md) és [A táblázatos BI szemantikai modell biztonságossá tétele](http://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/Securing%20the%20Tabular%20BI%20Semantic%20Model.docx) című cikkekben talál.

![Biztonsági szűrő alkalmazása](media/service-admin-rls/rls-apply-security-filter.png)


[!INCLUDE [include-short-name](./includes/rls-desktop-view-as-roles.md)]

## <a name="manage-security-on-your-model"></a>Az adatmodell biztonságának kezelése

Az adatmodell biztonságának kezeléséhez a következő lépéseket hajthatja végre.

1. Az adatmodellnél kattintson a **három pontra (…)** .
2. Válassza a **Biztonság** elemet.
   
   ![Biztonsági szűrők alkalmazása mindkét irányba](media/service-admin-rls/rls-security.png)

Ekkor megnyílik az RLS-oldal, ahol hozzárendelheti a tagokat a Power BI Desktopban létrehozott szerepkörökhöz. A Biztonság lehetőség csak az adatkészlet tulajdonosai számára érhető el. Ha az adatkészlet egy Csoporthoz tartozik, akkor a Biztonság lehetőséget csak a csoport rendszergazdái látják. 

Csak a Power BI Desktopon belül hozhat létre és módosíthat szerepköröket.

## <a name="working-with-members"></a>Tagok kezelése

### <a name="add-members"></a>Tagok hozzáadása

A felvenni kívánt felhasználót, biztonsági csoportot vagy terjesztési listát az e-mail-cím vagy a név megadásával adhatja hozzá a szerepkörhöz. Power BI-ban létrehozott Csoportokat nem vehet fel. [Szervezeten kívüli](whitepaper-azure-b2b-power-bi.md#data-security-for-external-partners) tagokat is felvehet.

![Tag felvétele](media/service-admin-rls/rls-add-member.png)

A szerepkör neve vagy a Tagok melletti zárójelben a szerepkörhöz tartozó tagok számát is megtekintheti.

![Szerepkör tagjai](media/service-admin-rls/rls-member-count.png)

### <a name="remove-members"></a>Tagok eltávolítása

A tagokat a nevük mellett látható X elemre kattintva távolíthatja el. 

![Tag eltávolítása](media/service-admin-rls/rls-remove-member.png)

## <a name="validating-the-role-within-the-power-bi-service"></a>Szerepkör ellenőrzése a Power BI szolgáltatásban

Az adott szerepkör megfelelő működését a szerepkör tesztelésével ellenőrizheti. 

1. Kattintson a szerepkör mellett látható **három pontra (...)** .
2. Kattintson az **Adatok tesztelése szerepkörökként** elemre.

![Tesztelés szerepkörként](media/service-admin-rls/rls-test-role.png)

Ekkor megjelennek a szerepkör számára elérhető jelentések. Ebben a nézetben nem jelennek meg irányítópultok. A felső kék sávban látható az éppen tesztelt szerepkör.

![Megtekintés a következőként: <szerepkör>](media/service-admin-rls/rls-test-role2.png)

A **Megtekintés a következőként** elemre kattintva más szerepköröket és szerepkör-kombinációkat is tesztelhet.

![Más szerepkörök tesztelése](media/service-admin-rls/rls-test-role3.png)

Megtekinthet adatokat konkrét személyként, vagy választhatja az elérhető szerepkörök kombinációját a működésük ellenőrzéséhez. 

A **Vissza a sorszintű biztonsághoz** lehetőségre kattintva visszatérhet a normál nézethez.

[!INCLUDE [include-short-name](./includes/rls-usernames.md)]

## <a name="using-rls-with-app-workspaces-in-power-bi"></a>Az RLS használata Power BI-beli alkalmazás-munkaterületeken

Ha egy Power BI szolgáltatáson belüli alkalmazás-munkaterületen tesz közzé Power BI Desktop-jelentést, a szerepkörök a csak olvasási jogosultsággal rendelkező tagokra fognak vonatkozni. Jeleznie kell, hogy a tagok csak az alkalmazás-munkaterület beállításain belül láthatják a Power BI-tartalmakat.

> [!WARNING]
> Ha az alkalmazás-munkaterületet úgy konfigurálta, hogy a tagoknak szerkesztési engedélyük legyen, az RLS-szerepkörök nem fognak vonatkozni rájuk. A felhasználók az összes adatot megtekinthetik.

![Csoportbeállítások](media/service-admin-rls/rls-group-settings.png)

[!INCLUDE [include-short-name](./includes/rls-limitations.md)]

[!INCLUDE [include-short-name](./includes/rls-faq.md)]

## <a name="next-steps"></a>Következő lépések
[Sorszintű biztonság (RLS) a Power BI Desktoppal](desktop-rls.md)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
