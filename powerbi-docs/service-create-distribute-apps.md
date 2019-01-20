---
title: Irányítópultokból és jelentésekből álló alkalmazások közzététele a Power BI-ban
description: Tudja meg, hogyan tehet közzé alkalmazásokat, azaz irányítópultokból és jelentésekből álló gyűjteményeket, amelyek célja az alapvető metrikák biztosítása a vállalat számára.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/24/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 451b5967dd648d982132282d2debbd4c4f86780f
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54294061"
---
# <a name="publish-apps-with-dashboards-and-reports-in-power-bi"></a>Irányítópultokból és jelentésekből álló alkalmazások közzététele a Power BI-ban

A Power BI szolgáltatásban közzétehet kapcsolódó irányítópultok-l és jelentésgyűjteményekből álló *alkalmazásokat*. Az alkalmazásokat a *alkalmazás-munkaterületeken* hozza létre, ahol együttműködhet a Power BI-tartalmakon a munkatársaival. Ezután közzéteheti a kész alkalmazásokat a szervezet számos tagja számára. További információ az [alkalmazás-munkaterületek létrehozásáról](service-create-workspaces.md).

![Power BI-alkalmazások](media/service-create-distribute-apps/power-bi-apps-left-nav.png)

Üzleti felhasználóinak gyakran lehet szükségük több Power BI-irányítópultra vagy -jelentésre az üzletvitelükhöz. A Power BI alkalmazásokkal irányítópult- és jelentésgyűjteményeket hozhat létre, majd közzéteheti az alkalmazásokat a teljes vállalat, vagy egy adott személy vagy csoport számára. A jelentés készítője vagy a rendszergazda számára az alkalmazásoknak köszönhetően egyszerűbbé válik a gyűjteményekre vonatkozó engedélyek kezelése.

Az üzleti felhasználók különböző módokon férhetnek hozzá az alkalmazásokhoz. Ha a Power BI-rendszergazda engedélyezi, egyenesen a munkatársai Power BI-fiókjába telepíthet alkalmazásokat. Ha nem, telepíthetik az alkalmazást a Microsoft AppSource-ból, vagy küldhet nekik egy közvetlen hivatkozást. Könnyen megtalálhatják újra a tartalmat, mert egy helyen érhető el minden. Nem módosíthatják az alkalmazás tartalmát, de használhatják a Power BI szolgáltatásban vagy valamelyik mobilalkalmazásban is – maguk is szűrhetik, kiemelhetik és rendezhetik az adatokat. A rendszer automatikusan frissíti az alkalmazásokat, és szabályozható, milyen gyakran frissüljenek az adatok. További információk az [üzleti felhasználóknak elérhető alkalmazásélményről](consumer/end-user-apps.md).

**Tudta?** A Power BI előzetes verziójú, új munkaterületi felhasználói felületet kínál. Az [Új munkaterületek létrehozása (előzetes verzió)](service-create-the-new-workspaces.md) című cikkben további információt talál a munkaterületek jövőbeni változásairól. 

## <a name="apps-and-organizational-content-packs"></a>Alkalmazások és vállalati tartalomcsomagok
Az alkalmazások a vállalati tartalomcsomagokból fejlődtek ki. Az új, előzetes verziójú munkaterületeken nem érhetők el a tartalomcsomagok. Ezen munkaterületek általános elérhetővé válása után nem használhat tartalomcsomagokat az újonnan létrehozott munkaterületeken. Ha még nem tette meg, kezdje meg a tartalomcsomagok az alkalmazásokba való migrálását.

## <a name="video-apps-and-app-workspaces"></a>Videó: Alkalmazások és alkalmazás-munkaterületek
<iframe width="640" height="360" src="https://www.youtube.com/embed/Ey5pyrr7Lk8?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="licenses-for-apps"></a>Licencek alkalmazásokhoz
Az alkalmazás-munkaterületek tagjainak Power BI Pro-licencre van szüksége. Az alkalmazás felhasználói esetében két lehetőség van.

* 1. lehetőség: Minden üzleti felhasználónak **Power BI Pro** licencre van szüksége az alkalmazás megtekintéséhez. 
* 2. lehetőség: A vállalat ingyenes felhasználói megtekinthetik az alkalmazás tartalmát, ha az alkalmazás egy Power BI Premium kapacitásban található. Részletek: [Mi a Power BI Premium?](service-premium.md).

## <a name="publish-your-app"></a>Az alkalmazás közzététele
Ha a munkaterület irányítópultjai és jelentései elkészültek, kiválaszthatja a közzétenni kívánt irányítópultokat és jelentéseket, majd alkalmazásként közzéteheti. Küldhet közvetlen hivatkozást a szélesebb közönségnek, vagy a **További alkalmazások AppSource-ból való letöltése és felderítése** területre lépve megkereshetik az alkalmazást az Alkalmazások lapon. 

1. A munkaterület listanézetében határozhatja meg, mely irányítópultokat és jelentéseket szeretné felvenni az alkalmazásba.

     ![A közzétenni kívánt irányítópult kiválasztása](media/service-create-distribute-apps/power-bi-apps-incude-dashboard.png)

     Ha úgy dönt, hogy nem tesz közzé egy jelentést, megjelenik egy figyelmeztetés a jelentés és a kapcsolódó irányítópult mellett. Az alkalmazást így is közzéteheti, a kapcsolódó irányítópultról azonban hiányozni fognak az adott jelentés csempéi.

     ![Figyelmeztetés kapcsolódó irányítópultról](media/service-create-distribute-apps/power-bi-apps-report-warning.png)

2. Az adott munkaterületen található összes tartalom megosztási folyamatának indításához válassza a jobb felső részen található **Alkalmazás közzététele** gombot.
   
     ![Alkalmazás közzététele](media/service-create-distribute-apps/power-bi-apps-publish-button.png)

3. A **Részletek** területen töltse ki a leírást, hogy mások megtalálják az alkalmazást. Beállíthat egy háttérszínt a személyre szabásához.
   
     ![Alkalmazás részletei](media/service-create-distribute-apps/power-bi-apps-details.png)

4. A **Tartalom** lapon láthatja a tartalmat, amelyet az alkalmazás részeként közzé fog tenni – azaz mindent, amit azon a munkaterületen választ ki. Beállíthatja az alkalmazás kezdőlapját is, vagyis azt az irányítópultot vagy jelentést, amelyet az alkalmazást használók elsőként meglátnak. Választhatja az **Egyik sem** lehetőséget. Ekkor az alkalmazásban szereplő összes tartalom listája fog megjelenni számukra. 
   
     ![Alkalmazás tartalma](media/service-create-distribute-apps/power-bi-apps-content.png)

5. A **Hozzáférés** területen meghatározhatja, hogy ki férhet hozzá az alkalmazáshoz: a vállalat összes tagja, vagy adott személyek vagy Active Directory-csoportok. Ha rendelkezik a megfelelő engedélyekkel, dönthet úgy, hogy automatikusan telepíti az alkalmazást a címzetteknél. A Power BI-rendszergazdák a Power BI felügyeleti portálon engedélyezhetik ezt a beállítást. További információk: [Alkalmazások automatikus telepítése](#how-to-install-an-app-automatically-for-end-users).

    ![Alkalmazás-hozzáférés](media/service-create-distribute-apps/power-bi-apps-access.png)

6. Amikor a **Befejezés** lehetőséget választja, a rendszer egy üzenetben kéri, hogy erősítse meg, hogy tényleg készen áll-e a közzétételre. A sikerességet jelölő párbeszédpanelről kimásolhatja az alkalmazásra mutató közvetlen hivatkozást, és elküldheti azoknak, akikkel megosztja az alkalmazást.
   
     ![Alkalmazás befejezése](media/service-create-distribute-apps/power-bi-apps-success.png)

További információk az [üzleti felhasználóknak elérhető alkalmazásélményről](consumer/end-user-apps.md).

## <a name="change-your-published-app"></a>A közzétett alkalmazás módosítása
Előfordulhat, hogy módosítani vagy frissíteni szeretné az alkalmazást a közzététel után. A frissítés egyszerű, ha Ön rendszergazda vagy tag az alkalmazás-munkaterületen, vagy közreműködő egy új alkalmazás-munkaterületen. 

1. Nyissa meg azt az alkalmazás-munkaterületet, amely megfelel az alkalmazásnak. 
   
     ![Munkaterület megnyitása](media/service-create-distribute-apps/power-bi-apps-open-workspace.png)
2. Nyissa meg az irányítópultot vagy a jelentést. Láthatja, hogy elvégezheti a kívánt módosításokat.
   
     Az alkalmazás-munkaterület a tervezési terület, tehát a módosításokat a rendszer nem küldi le élőben az alkalmazásba, amíg közzé nem teszi azokat. Ez lehetővé anélkül teszi lehetővé a módosításokat, hogy azok a közzétett alkalmazásokat érintenék.  
 
3. Térjen vissza az alkalmazás-munkaterület tartalomjegyzékéhez, és válassza az **App frissítése** lehetőséget.
   
     ![App frissítése gomb](media/service-create-distribute-apps/power-bi-app-update-button.png)

4. Frissítse a **Részleteket**, a **Tartalmat** és a **Hozzáférést**, ha szükséges, majd válassza az **App frissítése** lehetőséget.
   
     ![App frissítése gomb](media/service-create-distribute-apps/power-bi-app-update-complete.png)

Azok, akikkel megosztotta az alkalmazást, automatikusan az alkalmazás frissített verzióját látják. 

## <a name="automatically-install-apps-for-end-users"></a>Alkalmazások automatikus telepítése a végfelhasználók számára
Az alkalmazásokkal eljuttathatja a végfelhasználók munkájához szükséges adatokat. Ha erre jogosultságot kap egy rendszergazdától, a végfelhasználók számára automatikusan telepíthet alkalmazásokat, így könnyebben eljuttathatja a megfelelő alkalmazásokat a megfelelő embereknek vagy csoportoknak. Az alkalmazás automatikusan megjelenik a végfelhasználók alkalmazástartalmainak listájában, így nem kell megkeresniük őket a Microsoft AppSource-ban vagy egy telepítési hivatkozást követve. Ennek köszönhetően könnyebben vezethet be szabványos Power BI-tartalmakat a felhasználók számára.

### <a name="how-to-install-an-app-automatically-for-end-users"></a>Alkalmazás automatikus telepítése a végfelhasználók számára
Ha egy rendszergazda jogosultságot adott erre Önnek, **automatikusan telepítheti az alkalmazást**. Ha bejelöli a négyzetet, és kiválasztja a **Befejezés** (vagy meglévő alkalmazások esetén az **Alkalmazás frissítése**) lehetőséget, az alkalmazás el lesz küldve a **Hozzáférés** lap **Engedélyek** szakaszában meghatározott csoportoknak.

![Alkalmazásleküldés engedélyezése](media/service-create-distribute-apps//power-bi-apps-access.png)

### <a name="how-users-get-the-apps-that-were-pushed-to-them"></a>A küldött alkalmazások felhasználói használatba vétele
Egy alkalmazás leküldéses továbbítása után az automatikusan megjelenik az alkalmazások listájában. Az alkalmazásokat úgy válogathatja, hogy csak az egy adott felhasználói csoport vagy szervezeti szerepkör számára szükségesek jelenjenek meg.

![Alkalmazásleküldés engedélyezése](media/service-create-distribute-apps/power-bi-apps-left-nav.png)

### <a name="considerations-for-automatically-installing-apps"></a>Alkalmazások automatikus telepítése – megfontolandó szempontok
Az alkalmazások leküldéses továbbítása során az alábbiakra érdemes ügyelni:

* Az alkalmazások automatikus telepítése a felhasználók számára időbe telik. A legtöbb alkalmazás azonnal települ, a leküldött alkalmazások azonban több időt vehetnek igénybe.  Ez az alkalmazás elemeinek és a hozzáféréssel rendelkező személyek számától függ. Azt javasoljuk, hogy az alkalmazásleküldést munkaidőn kívül, jóval azelőtt végezze el, hogy a felhasználóknak szükségük lenne az alkalmazásokra. Egyeztessen több felhasználóval, mielőtt mindenkinek bejelentené az alkalmazás elérhetőségét.

* Frissítse a böngészőjét. Előfordulhat, hogy a felhasználóknak frissíteniük kell vagy újból meg kell nyitniuk a böngészőjüket.

* Ha az alkalmazás nem jelenik meg azonnal az alkalmazáslistában, a felhasználók frissítsék vagy nyissák meg újra a böngészőt.

* Lehetőleg ne terhelje túl a felhasználókat. Ne küldjön egyszerre túl sok alkalmazást, hogy a felhasználók az előtelepített alkalmazásokat is hasznosnak érezhessék. Célszerű megszabni, hogy ki küldhet alkalmazásokat a végfelhasználóknak, és együttműködni ennek időzítésében. A szervezeti alkalmazások a végfelhasználóknak való leküldéséhez létrehozhat egy kapcsolatfelvételi pontot.

* Azoknál a vendégfelhasználóknál, akik nem fogadták el a meghívást, az alkalmazások nem lesznek automatikusan telepítve.  

## <a name="unpublish-an-app"></a>Alkalmazás közzétételének visszavonása
Egy alkalmazás-munkaterület bármely tagja visszavonhatja az alkalmazás közzétételét.

* Az alkalmazás-munkaterületen válassza a jobb felső sarokban a három pontot (**...**) > az **App közzétételének visszavonása** lehetőséget.
  
     ![App közzétételének visszavonása](media/service-create-distribute-apps/power-bi-app-unpublish.png)

Ez a művelet törli az alkalmazás telepítését mindenkitől, akivel megosztotta, és ezután nem fognak hozzáférni. Nem törli azonban az alkalmazás-munkaterületet vagy a tartalmát.

## <a name="next-steps"></a>Következő lépések
* [Alkalmazás munkaterületének létrehozása](service-create-workspaces.md)
* [Alkalmazások telepítése és használata a Power BI-ban](consumer/end-user-apps.md)
* [Power BI alkalmazások külső szolgáltatásokhoz](service-connect-to-services.md)
* [Power BI Felügyeleti portál](https://docs.microsoft.com/power-bi/service-admin-portal)
* Kérdése van? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
