---
title: Alkalmazás közzététele a Power bi-ban
description: Ismerje meg, hogyan teheti közzé az új alkalmazásokat, és irányítópultokat és jelentéseket beépített navigációs gyűjteményei.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: f3f933a3e3af2ef1d7864b379e9b8b5520d505ff
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65941549"
---
# <a name="publish-an-app-in-power-bi"></a>Alkalmazás közzététele a Power bi-ban

A Power BI-tartalom létrehozása csomagolt hivatalos, majd osztja el egy széles közönség számára, mint egy *alkalmazás*. Az alkalmazásokat a *alkalmazás-munkaterületeken* hozza létre, ahol együttműködhet a Power BI-tartalmakon a munkatársaival. Ezután közzéteheti a kész alkalmazásokat a szervezet számos tagja számára. 

![Power BI-alkalmazások](media/service-create-distribute-apps/power-bi-new-apps.png)

Üzleti felhasználóinak gyakran lehet szükségük több Power BI-irányítópultra vagy -jelentésre az üzletvitelükhöz. A Power BI alkalmazásokkal irányítópult- és jelentésgyűjteményeket hozhat létre, majd közzéteheti az alkalmazásokat a teljes vállalat, vagy egy adott személy vagy csoport számára. A jelentés készítője vagy a rendszergazda számára az alkalmazásoknak köszönhetően egyszerűbbé válik a gyűjteményekre vonatkozó engedélyek kezelése.

Az üzleti felhasználók különböző módokon hozzá az alkalmazásokhoz:

- Keresse meg és telepítse az alkalmazást a Microsoft AppSource-ból
- Küldhet nekik egy közvetlen hivatkozást.
- Ha a Power BI rendszergazda engedélyezi, automatikusan telepítheti az alkalmazást a munkatársai Power BI-fiókjába.

Az alkalmazás létrehozhat saját beépített navigációs, így a felhasználók könnyen megtalálják a tartalmat az alkalmazásfejlesztést. Nem módosíthatják az alkalmazás tartalmát. Velük, vagy a Power BI szolgáltatásban vagy valamelyik mobilalkalmazásban is –, a – szűrés, kiemelés, és maguk az adatok rendezése. A rendszer automatikusan frissíti az alkalmazásokat, és szabályozható, milyen gyakran frissüljenek az adatok. További információk az [üzleti felhasználóknak elérhető alkalmazásélményről](consumer/end-user-apps.md).

## <a name="licenses-for-apps"></a>Licencek alkalmazásokhoz
Hozzon létre, vagy frissítheti az alkalmazásokat, Power BI Pro-licenccel kell. Alkalmazás *fogyasztók*, két lehetőség közül.

* 1. lehetőség: Minden üzleti felhasználónak **Power BI Pro** licencre van szüksége az alkalmazás megtekintéséhez. 
* 2. lehetőség: Ha az alkalmazás-munkaterület található, a Power BI prémium-kapacitás, a vállalat ingyenes felhasználói alkalmazás tartalmának megtekintéséhez. Részletek: [Mi a Power BI Premium?](service-premium.md).

## <a name="publish-your-app"></a>Az alkalmazás közzététele
Ha a munkaterület irányítópultjai és jelentései elkészültek, kiválaszthatja a közzétenni kívánt irányítópultokat és jelentéseket, majd alkalmazásként közzéteheti. 

1. A munkaterület listanézetében döntse el, mely irányítópultokat és jelentéseket szeretne **alkalmazásban szereplő**.

     ![A közzétenni kívánt irányítópult kiválasztása](media/service-create-distribute-apps/power-bi-apps-incude-dashboard.png)

     Ha nem kíván egy kapcsolódó irányítópultra egy jelentéssel, megjelenik egy figyelmeztetés a jelentés melletti. Így is közzéteheti az alkalmazást, de a kapcsolódó irányítópult nem fog tudni az adott jelentés csempéi.

     ![Figyelmeztetés kapcsolódó irányítópultról](media/service-create-distribute-apps/power-bi-apps-report-warning.png)

2. Válassza ki a **alkalmazás közzététele** gombra a folyamat létrehozásának és tegyünk közzé egy alkalmazást a munkaterületen a jobb felső sarokban.
   
     ![Alkalmazás közzététele](media/service-create-distribute-apps/power-bi-apps-publish-button.png)

3. A **telepítő**, töltse ki a nevet és leírást, hogy mások megtalálják az alkalmazást. A személyre szabásához témaszín állíthatja be. Egy hely támogatott hozzáadhat egy hivatkozást is.
   
     ![Az alkalmazás létrehozása](media/service-create-distribute-apps/power-bi-apps-build-your-apps.png)

4. A **navigációs**, akkor válassza ki az alkalmazás részeként közzé kell tenni a tartalmat. Ezután hozzáadhat új alkalmazás navigációs szakaszok tartalmának rendszerezéséhez. Lásd: [a navigációt a az alkalmazás tervezési](#design-the-navigation-experience-for-your-app) részleteket ebben a cikkben.
   
     ![Alkalmazás-navigáció](media/service-create-distribute-apps/power-bi-apps-navigation.png)

5. A **hozzáférés**, döntse el, hogy ki férhet hozzá az alkalmazást. 
    - A [klasszikus munkaterületek](service-create-workspaces.md): a szervezet, az adott személyek vagy az Azure Active Directory (AAD) biztonsági csoportok minden tagja számára.
    - Az a [új élmény munkaterületek](service-create-the-new-workspaces.md): adott személyek, AAD biztonsági csoportokat és terjesztési listák és az Office 365-csoportok.

6. Ha rendelkezik engedélyekkel, telepítheti az alkalmazást automatikusan a címzettek számára. A Power BI-rendszergazdák a Power BI felügyeleti portálon engedélyezhetik ezt a beállítást. Tudjon meg többet [egy alkalmazás automatikus telepítése](#automatically-install-apps-for-end-users) ebben a cikkben.

     ![Alkalmazásengedélyek](media/service-create-distribute-apps/power-bi-apps-permissions.png)

7. Ha bejelöli **alkalmazás közzététele**, közzététele készen áll a megerősítő üzenet jelenik meg. Az a **alkalmazás megosztása** párbeszédpanelen is másolhatja az URL-cím, amely erre az alkalmazásra mutató közvetlen hivatkozást.
   
     ![Alkalmazás befejezése](media/service-create-distribute-apps/power-bi-apps-success.png)

Elküldheti, hogy közvetlen hivatkozás a személyek, akikkel megosztotta, vagy megtalálhassák az alkalmazást az alkalmazások lapon a **töltse le, és ismerje meg a további alkalmazások AppSource**. További információk az [üzleti felhasználóknak elérhető alkalmazásélményről](consumer/end-user-apps.md).

## <a name="change-your-published-app"></a>A közzétett alkalmazás módosítása
Előfordulhat, hogy módosítani vagy frissíteni szeretné az alkalmazást a közzététel után. Frissítés egyszerű, ha Ön rendszergazda vagy az új alkalmazás-munkaterületen tag. 

1. Nyissa meg azt az alkalmazás-munkaterületet, amely megfelel az alkalmazásnak. 
   
     ![Munkaterület megnyitása](media/service-create-distribute-apps/power-bi-apps-open-workspace.png)

2. Végezze el a kívánt módosításokat az irányítópultok vagy jelentések.
 
     Az alkalmazás-munkaterület a tervezési terület, tehát a módosításokat a rendszer nem küldi le élőben az alkalmazásba, amíg közzé nem teszi azokat. Ez lehetővé anélkül teszi lehetővé a módosításokat, hogy azok a közzétett alkalmazásokat érintenék.  
 
    > [!IMPORTANT]
    > Ha egy jelentés eltávolítása, és frissítse az alkalmazást, akkor is, ha a jelentés adhat vissza az alkalmazás a, az alkalmazások felhasználóinak elvetésével összes például a könyvjelzőket, a megjegyzéseket, stb.  
 
3. Lépjen vissza az alkalmazáslistából munkaterület Tartalomjegyzékéhez, és válassza a **app frissítése** jobb felső sarokban.
   
1. Frissítés **telepítő**, **navigációs**, és **engedélyek**, ha szükséges, majd válassza ki **app frissítése**.
   
Azok, akikkel megosztotta az alkalmazást, automatikusan az alkalmazás frissített verzióját látják. 

## <a name="design-the-navigation-experience-for-your-app"></a>A navigációt a az alkalmazás megtervezése
A **új navigációs builder** beállítás lehetővé teszi az alkalmazás egy egyéni navigációs hozhat létre. Az egyéni navigációs megkönnyíti a felhasználók kereséséhez és a tartalom használata az alkalmazásban. Meglévő alkalmazások rendelkeznek, ez a beállítás ki van kapcsolva és új alkalmazások alapértelmezés szerint a beállítás a.

Ha a beállítás ki van kapcsolva, kiválaszthatja a **alkalmazás kezdőlapja** lennie **adott tartalomra**, például egy irányítópultot vagy jelentést, vagy válassza ki a **nincs** alapszintű listájának megjelenítéséhez a felhasználó tartalmat.

Ha bekapcsolja a **új navigációs builder**, egy egyéni navigációs is tervezhet. Alapértelmezés szerint a jelentések, irányítópultok és Excel-munkafüzeteket tartalmazza az alkalmazás szerepelnek listáját. 

![Alkalmazás-navigáció](media/service-create-distribute-apps/power-bi-apps-navigation.png)

További testre szabhatja az alkalmazás navigációs szerint:
* A fel elemek átrendezése / lefelé mutató nyílra. 
* Cikkek átnevezése a **részleteiről**, **irányítópult részletek**, és **munkafüzet részletes adatainak**.
* Elrejti az egyes elemeket, a navigációs sávon.
* Használatával a **új** hozzáadására szolgáló **szakaszok** csoporthoz kapcsolódó tartalom.
* Használatával a **új** felvételének lehetősége egy **hivatkozás** , a bal oldali navigációs külső erőforrásokra. 

Amikor felvesz egy **hivatkozás**, a **részletes** is, a hivatkozás megnyitja. Alapértelmezés szerint hivatkozások megnyitásához a **az aktuális lap**, ugyanakkor kiválaszthatja **új lap**, vagy **terület tartalom**. 

### <a name="considerations-for-using-the-new-navigation-builder-option"></a>Az új navigáció a jelentéskészítő lehetőség használatának szempontjai
Általános dolog, vegye figyelembe, amikor az új navigáció builder használatával:
* Jelentésoldalak jelennek meg az alkalmazás navigációs területen egy bővíthető szakasz
* Kapcsolja ki az új navigáció jelentéskészítő és a közzététel vagy frissítse az alkalmazást, ha a testreszabott elvesznek. Például szakaszok, rendezés, hivatkozásokat és egyéni neveket, navigációs elemek is az összes elvesznek.

Ha a hivatkozások hozzáadása az alkalmazás navigációs és a tartalom terület lehetőséget választotta:
* Győződjön meg arról, a hivatkozás lehet beágyazni. Egyes szolgáltatások letiltása a külső helyek, mint a Power BI tartalmak beágyazásához.
* Például a jelentések és irányítópultok Power BI-tartalmak beágyazása más munkaterületekhez nem támogatott. 
* Beágyazás a Power BI jelentéskészítő kiszolgáló tartalmához a hozzá tartozó natív egy a helyi központi telepítéséből URL-cím-tartalmak beágyazásához. Szereplő lépések segítségével [létrehozása a Power BI jelentéskészítő kiszolgáló URL-címe](https://docs.microsoft.com/power-bi/report-server/quickstart-embed#creating-the-power-bi-report-server-report-url) az URL-Címének lekéréséhez. Vegye figyelembe, hogy rendszeres hitelesítési szabályok érvényesek lesznek, így a tartalmat megtekinti egy VPN-kapcsolat a helyszíni kiszolgáló szükséges. 
* Biztonsági figyelmeztetés jelzi, hogy a tartalom a Power bi-ban nem látható a beágyazott tartalmak tetején.



## <a name="automatically-install-apps-for-end-users"></a>Alkalmazások automatikus telepítése a végfelhasználók számára
Ha egy rendszergazda engedélyekkel biztosít, telepíthet alkalmazásokat, automatikusan *leküldése* azokat a végfelhasználók számára. A leküldéses funkció megkönnyíti a megfelelő embereknek vagy csoportoknak a megfelelő alkalmazások terjesztése. Az alkalmazás automatikusan megjelennek a végfelhasználók alkalmazásokat tartalmak listája. Keresse meg azt a Microsoft AppSource-ból, vagy egy telepítési hivatkozást követve ne kelljen. Tekintse meg, hogyan lehetővé a rendszergazdák [leküldött alkalmazások a végfelhasználók számára](service-admin-portal.md#push-apps-to-end-users) a Power BI felügyeleti portál cikkben.

### <a name="how-to-push-an-app-automatically-to-end-users"></a>Egy alkalmazás automatikus elküldése a végfelhasználók számára
Ha egy rendszergazda jogosultságot adott erre Önnek, **automatikusan telepítheti az alkalmazást**. Ha a jelölőnégyzetet, majd válassza **alkalmazás közzététele** (vagy **app frissítése**), az alkalmazás összes felhasználója át lett helyezve, vagy meghatározott csoportoknak a **engedélyek** az alkalmazás a szakaszában**Hozzáférés** fülre.

![Alkalmazásleküldés engedélyezése](media/service-create-distribute-apps//power-bi-apps-access.png)

### <a name="how-users-get-the-apps-that-you-push-to-them"></a>Felhasználói használatba az alkalmazásokat, akkor küldje le őket
Miután egy alkalmazás leküldéses továbbítása, az megjelenik az alkalmazáslistában, automatikusan. Ezzel a módszerrel válogathatja, hogy az alkalmazásokat, hogy egyes felhasználók vagy a feladat szerepkörök a szervezet szükséges, hogy azonnal a.

![Alkalmazásleküldés engedélyezése](media/service-create-distribute-apps/power-bi-apps-left-nav.png)

### <a name="considerations-for-automatically-installing-apps"></a>Alkalmazások automatikus telepítése – megfontolandó szempontok
Az alkalmazások leküldéses továbbítása során az alábbiakra érdemes ügyelni:

* Az alkalmazások automatikus telepítése a felhasználók számára időbe telik. A legtöbb alkalmazás telepítése azonnal a felhasználók, de alkalmazásleküldés időt is igénybe vehet.  Ez az alkalmazás elemeinek és a hozzáféréssel rendelkező személyek számától függ. Azt javasoljuk, hogy az alkalmazásleküldést munkaidőn kívül, jóval azelőtt végezze el, hogy a felhasználóknak szükségük lenne az alkalmazásokra. Egyeztessen több felhasználóval, mielőtt mindenkinek bejelentené az alkalmazás elérhetőségét.

* Frissítse a böngészőt. Előfordulhat, hogy a felhasználóknak frissíteniük kell vagy újból meg kell nyitniuk a böngészőjüket.

* Ha a felhasználók nem jelenik meg azonnal az alkalmazást az alkalmazáslistában, azok kell frissítse vagy zárja be és nyissa meg újra a böngészőt.

* Lehetőleg ne terhelje túl a felhasználókat. Ne küldjön egyszerre túl sok alkalmazást, hogy a felhasználók az előtelepített alkalmazásokat is hasznosnak érezhessék. Célszerű megszabni, hogy ki küldhet alkalmazásokat a végfelhasználóknak, és együttműködni ennek időzítésében. Az alkalmazások a végfelhasználóknak való leküldéséhez szervezet kapcsolatfelvételi pont létrehozásához.

* Vendég felhasználók, akik még nem fogadták el a meghívást azok automatikusan telepített alkalmazások nem kap.  

## <a name="unpublish-an-app"></a>Alkalmazás közzétételének visszavonása
Egy alkalmazás-munkaterület bármely tagja visszavonhatja az alkalmazás közzétételét.

>[!IMPORTANT]
>Ha visszavonja egy alkalmazás közzétételét, az alkalmazás felhasználóinak testreszabásai elvesznek. Személyes könyvjelzőket, megjegyzések, vagy az alkalmazás tartalmához társított előfizetéseket megszakad. Alkalmazás közzétételét csak akkor szüntesse meg, ha el szeretné távolítani az alkalmazást.
> 
> 

* Az alkalmazás-munkaterületen válassza a jobb felső sarokban a három pontot ( **...** ) > az **App közzétételének visszavonása** lehetőséget.
  
     ![App közzétételének visszavonása](media/service-create-distribute-apps/power-bi-app-unpublish.png)

Ez a művelet törli az alkalmazás telepítését mindenkitől, akivel megosztotta, és ezután nem fognak hozzáférni. Nem törli azonban az alkalmazás-munkaterületet vagy a tartalmát.

## <a name="view-your-published-app"></a>A közzétett alkalmazás megtekintése

Ha az alkalmazások felhasználóinak nyissa meg az alkalmazást, a navigációs hozta létre, a szokásos Power BI bal oldali navigációs panelen helyett látják. Az alkalmazás navigációs sorolja fel, a jelentések és irányítópultok a szakasz meghatározta. Felsorolja az egyes oldalak az egyes jelentések ahelyett, hogy csak a jelentés nevét.

![Navigációs-alkalmazás](media/service-create-distribute-apps/power-bi-new-apps-navigation.png)

## <a name="next-steps"></a>Következő lépések
* [Alkalmazás munkaterületének létrehozása](service-create-workspaces.md)
* [Alkalmazások telepítése és használata a Power BI-ban](consumer/end-user-apps.md)
* [Power BI alkalmazások külső szolgáltatásokhoz](service-connect-to-services.md)
* [Power BI Felügyeleti portál](https://docs.microsoft.com/power-bi/service-admin-portal)
* Kérdése van? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
