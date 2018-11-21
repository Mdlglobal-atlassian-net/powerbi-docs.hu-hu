---
title: Új munkaterületek létrehozása (előzetes verzió) – Power BI
description: Tudja meg, hogyan hozhat létre új munkaterületeket, olyan irányítópultokból és jelentésekből álló gyűjteményeket, amelyek célja az alapvető metrikák biztosítása a vállalat számára.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 11/14/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: cdc406ddd9c086114ca118130bb4973737de3ed1
ms.sourcegitcommit: 1e4fee6d1f4b7803ea285eb879c8d5a4f7ea8b85
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51717895"
---
# <a name="create-the-new-workspaces-preview-in-power-bi"></a>Új munkaterületek létrehozása a Power BI-ban (előzetes verzió)

A Power BI egy előzetes verziójú, új munkaterületi felhasználói felületet mutat be. A munkaterületeken együttműködhet munkatársaival, hogy irányítópult- és jelentésgyűjteményeket hozzanak létre, amelyeket *alkalmazásokba* csomagolhatnak, majd közzétehetik a teljes vállalat, vagy egy adott személy vagy csoport számára. 

![Power BI – új munkaterületek (előzetes verzió)](media/service-create-the-new-workspaces/power-bi-new-workspaces-preview.png)

Az előzetes verziójú munkaterületekkel a következőket végezheti el:

- Munkaterület-szerepköröket rendelhet felhasználói csoportokhoz: biztonsági csoportokhoz, terjesztési listákhoz, Office 365-csoportokhoz és egyéni felhasználókhoz.
- Office 365-csoport létrehozása nélkül hozhat létre egy Power BI-munkaterületet.
- Részletesebb munkaterület-szerepköröket használhat, amelyekkel rugalmasabb engedélykezelést érhet el a munkaterületeken.
 
Amikor létrehoz egy új munkaterületet, nem hoz létre egy mögöttes, társított Office 365-csoportot is. A munkaterület felügyelete kizárólag a Power BI-ban zajlik. Továbbra is hozzáadhat egy Office 365-csoportot a munkaterülethez, ha a felhasználók tartalomhoz való hozzáférését Office 365-csoportokkal szeretné kezelni. Azonban emellett már biztonsági csoportokat és terjesztési listákat is használhat, valamint közvetlenül a Power BI-on belül hozzáadhat egyéni felhasználókat, így rugalmasan kezelheti a munkaterületek hozzáférését. Mivel a munkaterületek felügyelete most már a Power BI-ban történik, a Power BI rendszergazdái döntik el, hogy a cégen belül ki hozhat létre munkaterületet. További információt a [Power BI felügyeleti portálja cikkben, a Munkaterületek szakaszban](service-admin-portal.md#workspace-settings) talál. 

Felhasználói csoportokat vagy egyéneket tagként, közreműködőként vagy rendszergazdaként adhat hozzá az új munkaterületekhez. A meghatározott szerepkört a felhasználói csoport minden tagja megkapja. Ha egy felhasználó több csoport tagja, a szerepkör által nyújtott legmagasabb szintű engedélyekkel fog rendelkezni.  A különböző szerepkörök ismertetését a cikk későbbi, [Az új munkaterületek szerepkörei](#roles-in-the-new-workspaces) című szakaszában találhatja.

Az alkalmazás-munkaterületekhez adott tagoknak Power BI Pro-licencre van szüksége. A munkaterületen a felhasználók együttműködhetnek az irányítópultokon és jelentéseken, amelyeket a szélesebb közönség vagy akár a teljes vállalat elé szeretne tárni. Ha másokkal is megszeretné osztani a tartalmat a szervezeten belül, rendeljen hozzájuk Power BI Pro-licencet, vagy helyezze a munkaterületet egy Power BI Prémium szintű kapacitásba.

Az új munkaterületekkel újraterveztünk néhány funkciót. A cikk későbbi részében az [Alkalmazás-munkaterület másképpen működő funkciói](#app-workspace-features-that-work-differently) szakaszban megtekintheti a várhatóan maradandó változások ismertetését. Mivel ez egy előzetes verziójú funkció, érdemes tudnia a korlátozásokról. A jelenlegi korlátozásokat a cikk egy későbbi szakaszában, az [Ismert porlémák](#known-issues) részben ismertetjük. 

## <a name="roll-out-new-app-workspaces"></a>Az új alkalmazás-munkaterületek bevezetése

Az előzetes verzió ideje alatt a régi és új típusú alkalmazás-munkaterületek megférnek egymás mellett, és bármelyiket létrehozhatja. A régi munkaterületek az előzetes verzió vége, és az új munkaterületek általános elérhetővé válása után is elérhetők maradnak egy ideig. Létrehozni azonban már nem tudja őket, és elő kell készítenie őket az új infrastruktúrába való migráláshoz. Ne aggódjon, erre több hónapja lesz.

## <a name="create-one-of-the-new-app-workspaces"></a>Új típusú alkalmazás-munkaterület létrehozása

1. Kezdje az alkalmazás-munkaterület létrehozásával. Válassza a **Munkaterületek** > **Alkalmazás munkaterületének létrehozása** lehetőséget.
   
     ![Alkalmazás munkaterületének létrehozása](media/service-create-workspaces/power-bi-create-app-workspace.png)

2. A **Továbbfejlesztett munkaterületek** – előzetes verzió területen válassza a **Kipróbálás** lehetőséget.
   
     ![Továbbfejlesztett munkaterületek – előzetes verzió](media/service-create-workspaces/power-bi-preview-improved-workspaces.png)

2. Nevezze el a munkaterületet. Ha a név nem használható, szerkesztéssel hozzon létre egy egyedi azonosítót.
   
     Az alkalmazás neve meg fog egyezni a munkaterület nevével.
   
1. Ha kívánja, hozzáadhat egy képe. A fájlméret nem haladhatja meg a 45 kilobájtot.
 
    ![A munkaterület elnevezése és kép hozzáadása](media/service-create-workspaces/power-bi-name-workspace.png)

1. Kattintson a **Mentés** gombra.

    Az új munkaterület **üdvözlőképernyőjén** adatokat adhat hozzá. 

    ![Az új munkaterület üdvözlőképernyője](media/service-create-workspaces/power-bi-workspace-welcome-screen.png)

1. Válassza például a **Minták** > **Ügyfél-jövedelmezőségi minta** lehetőséget.

    Ekkor a munkaterület tartalomlistájában megjelenik az **Új előzetes verziós munkaterületek** elem. Mivel Ön rendszergazda, egy új művelet is megjelenik, a **Hozzáférés**.

    ![Előzetes verziós munkaterületek tartalomlistája](media/service-create-workspaces/power-bi-workspaces-preview-content-list.png)

1. Válassza a **Hozzáférés** lehetőséget.

1. Adjon hozzá biztonsági csoportokat, terjesztési listákat, Office 365-csoportokat vagy egyéni felhasználókat a munkaterületekhez tagként, közreműködőként vagy rendszergazdaként. A különböző szerepkörök ismertetését a cikk későbbi, [Az új munkaterületek szerepkörei](#roles-in-the-new-workspaces) című szakaszában találhatja.

    ![Munkaterületek – tagok, rendszergazdák és közreműködők hozzáadása](media/service-create-workspaces/power-bi-access-add-members.png)

9. Válassza a **Hozzáadás** > **Bezárás** lehetőséget.

1. A Power BI létrehozza és megnyitja a munkaterületet. Ekkor megjelenik az olyan munkaterületek listájában, amelyeknek Ön a tagja. Mivel adminisztrátori jogosultsággal rendelkezik, a három pontra (...) kattintva visszaléphet, és módosíthatja a munkaterület beállításait, például új tagokat adhat hozzá vagy módosíthatja a tagok jogosultságait.

     ![Munkaterület beállításainak és hozzáférésének módosítása](media/service-create-workspaces/power-bi-edit-workspace.png)

## <a name="add-content-to-your-app-workspace"></a>Tartalom hozzáadása az alkalmazás-munkaterülethez

Az új típusú alkalmazás-munkaterület létrehozása után ideje feltölteni azt tartalommal. A tartalom hozzáadása hasonlóan működik a régi és új típusú munkaterületeken is, egyetlen kivétellel. Amíg valamelyik alkalmazás-munkaterületen van, feltölthet tartalmat vagy csatlakozhat fájlokhoz, pont mintha a Saját munkaterületén lenne. Az új munkaterületeken azonban nem csatlakozhat szervezeti, valamint külső tartalomcsomagokhoz, például a Microsoft Dynamics CRM-hez, a Salesforce-hoz és a Google Analyticshez. A jelenlegi munkaterületen csatlakozhat tartalomcsomagokhoz.

Ha egy alkalmazás-munkaterület tartalomlistájában tekint meg tartalmat, az alkalmazás-munkaterület neve tulajdonosként lesz feltüntetve.

### <a name="connecting-to-third-party-services-in-new-workspaces-preview"></a>Csatlakozás a külső szolgáltatásokhoz az új munkaterületeken (előzetes verzió)

Az új munkaterületek felületén az alkalmazásokra helyezzük a hangsúlyt. A külső szolgáltatások alkalmazásaival a felhasználók könnyen lekérhetik a használt szolgáltatások, például a Microsoft Dynamics CRM, a Salesforce vagy a Google Analytics adatait.
A szervezeti alkalmazásokkal a felhasználók megkaphatják a szükséges belső adatokat. Tervezzük szervezeti alkalmazásfunkciók hozzáadását is, így a felhasználók testreszabhatják az alkalmazások tartalmait. Így nem lesz szükség tartalomcsomagokra. 

Az előzetes verziójú, új munkaterületekkel nem lehet létrehozni vagy telepíteni céges tartalomcsomagokat. Ehelyett a megadott alkalmazásokkal csatlakozhat külső szolgáltatásokhoz, vagy megkérheti a belső csapatokat, hogy szolgáltassanak alkalmazásokat a jelenleg használt tartalomcsomagokhoz. 

## <a name="roles-in-the-new-workspaces"></a>Az új munkaterületek szerepkörei

A szerepkörökkel kezelheti, hogy mely felhasználók milyen műveleteket végezhetnek a munkaterületeken, így elősegítheti a csapatok együttműködését. Az új munkaterületekkel szerepköröket rendelhet egyénekhez és felhasználói csoportokhoz: biztonsági csoportokhoz, Office 365-csoportokhoz és terjesztési listákhoz. 

Szerepkörök felhasználói csoportokhoz való hozzárendelésekor a csoport felhasználói hozzáférnek a tartalomhoz. Ha beágyaz felhasználói csoportokat, minden tag jogosultságot kap. Azok a felhasználók, akik több, különböző szerepkörrel rendelkező felhasználói csoport tagjai is, a legmagasabb szintű jogosultságot kapják. 

Az új munkaterületek három szerepkört kínálnak: rendszergazdák, tagok és közreműködők.

**A rendszergazdák a következő műveleteket végezhetik el:**

- Frissíthetik és törölhetik a munkaterületet. 
- Hozzáadhatnak és eltávolíthatnak felhasználókat, így más rendszergazdákat is.
- Minden, a tagok számára elérhető műveletet elvégezhetnek.

**A tagok a következő műveleteket végezhetik el:** 

- Tagokat vagy alacsonyabb jogosultsággal rendelkezőket adhatnak hozzá.
- Alkalmazást tehetnek közzé és frissíthetnek.
- Elemeket vagy alkalmazásokat oszthatnak meg.
- Engedélyezhetik másoknak az elemek újbóli megosztását.
- Minden, a közreműködők számára elérhető műveletet elvégezhetnek.


**A közreműködők a következő műveleteket végezhetik el:** 

- Létrehozhatnak, szerkeszthetnek és törölhetnek tartalmakat a munkaterületen. 
- Közzétehetnek jelentéseket a munkaterületen, és törölhetnek tartalmakat.
- Nem adhatnak hozzáférést másoknak, és nem oszthatnak meg új tartalmat, de megoszthatnak tartalmat olyan felhasználókkal, akikkel már meg van osztva a munkaterület, az elem vagy az alkalmazás. 
- Nem módosíthatják a csoport tagjait.
 
„Hozzáférés kérése” típusú munkafolyamatokkal azok a felhasználók is kérhetnek hozzáférést, akik ezzel nem rendelkeznek. A Hozzáférés kérése típusú munkafolyamatok jelenleg irányítópultok, jelentések és alkalmazások esetén érhetők el.

## <a name="distribute-an-app"></a>Alkalmazások terjesztése

Ha a tartalom elkészült, kiválaszthatja a közzétenni kívánt irányítópultokat és jelentéseket, amelyeket közzétehet *alkalmazásként*. Minden munkaterületről létrehozhat egy alkalmazást. A munkatársai különböző módokon férhetnek hozzá az alkalmazáshoz. Ha a Power BI rendszergazda engedélyezi, automatikusan telepítheti az alkalmazást a munkatársai Power BI-fiókjába. Ha nem, megkereshetik az alkalmazást a Microsoft AppSource-ban, és telepíthetik, vagy küldhet nekik egy közvetlen hivatkozást. A rendszer automatikusan frissíti az alkalmazásokat, és szabályozható, milyen gyakran frissüljenek az adatok. További információ: [Irányítópultokból és jelentésekből álló alkalmazások közzététele a Power BI-ban](service-create-distribute-apps.md).

## <a name="convert-old-app-workspaces-to-new-app-workspaces"></a>Régi alkalmazás-munkaterületek konvertálása új alkalmazás-munkaterületekké

Az előzetes verzió időtartama alatt nem konvertálhat automatikusan régi típusú alkalmazás-munkaterületeket új típusúakká. Létrehozhat azonban egy új alkalmazás-munkaterületet, és közzéteheti rajta a tartalmait. 

Az új típusú munkaterületek általános elérhetővé válásakor igény szerint automatikusan migrálhatja a régi munkaterületeket. Az általános elérhetővé válás után egy idővel kötelező lesz a migrálás.

## <a name="power-bi-apps-faq"></a>Power BI alkalmazások – gyakori kérdések

### <a name="how-are-the-new-app-workspaces-different-from-current-app-workspaces"></a>Miben különböznek az új alkalmazás-munkaterületek a jelenlegi munkaterületektől?
* Az alkalmazás-munkaterületek létrehozása nem fog megfelelő entitásokat létrehozni az Office 365-ben, mint ahogy eddig a jelenlegi munkaterületek esetében történt. (Szerepkör hozzárendelésével továbbra is hozzáadhat egy Office 365-csoportot a munkaterülethez). 
* A jelenlegi alkalmazás-munkaterületeken csak egyéneket vehet fel a tagok és rendszergazdák listájára. Az új alkalmazás-munkaterületeken több AD biztonsági csoportot, terjesztési listát vagy Office 365-csoportot vehet fel ezekre a listákra, így könnyebben kezelheti a felhasználókat. 
- A jelenlegi alkalmazás-munkaterületeken létrehozhat szervezeti tartalomcsomagot. Az új alkalmazás-munkaterületen ezt nem teheti meg.
- A jelenlegi alkalmazás-munkaterületeken használhat szervezeti tartalomcsomagot. Az új alkalmazás-munkaterületen ezt nem teheti meg.
- Az előzetes verzió időtartama alatt az új alkalmazás-munkaterületek egyes új funkciói még nem érhetők el. További információt a következő szakaszban ([Az új munkaterületek egyéb tervezett funkciói](service-create-the-new-workspaces.md#other-planned-new-app-workspace-preview-features)) találhat.

## <a name="planned-new-app-workspace-preview-features"></a>Az előzetes verziós, új alkalmazás-munkaterületek tervezett funkciói

Az új, előzetes verziós alkalmazás-munkaterületek egyes funkcióit még fejlesztjük, így az előzetes verzióban egyelőre nem érhetők el:

- Nincs **Kilépés a munkaterületből** gomb.
- A használati metrikák egyelőre nem támogatottak.
- A Premium működése: Prémium szintű kapacitásban hozzárendelhet és létrehozhat munkaterületeket, azonban azok kapacitások közti áthelyezéséhez a munkaterület beállításaira kell lépnie.
- A SharePoint-kijelzők beágyazása egyelőre nem támogatott.
- Nincs **OneDrive** gomb az Office 365-csoportokhoz az Adatok lekérése/Fájlok lekérése területen.

## <a name="app-workspace-features-that-work-differently"></a>Az alkalmazás-munkaterületek másképp működő funkciói

A jelenlegi alkalmazás-munkaterületek egyes funkciói másképp működnek, mint az új alkalmazás-munkaterületeké. Ezek a különbségek szándékosak, és az ügyfelek visszajelzésein alapulnak, segítségükkel pedig rugalmasabban működhet együtt másokkal a munkaterületeken:

- A tagok újbóli megosztási jogosultsága: ennek helyét a Közreműködő szerepkör vette át
- Csak olvasható munkaterületek: Ahelyett, hogy csak olvasási hozzáférést adna a felhasználóknak, hozzárendelheti őket a soron következő megtekintő szerepkörhöz, amely hasonló, csak olvasási hozzáférést biztosít a munkaterületen lévő tartalomhoz.

## <a name="known-issues"></a>Ismert problémák

A következő problémák ismertek, és már dolgozunk a megoldásukon:

- Az e-mailes feliratkozók címzettjeiként hozzáadott felhasználók vagy felhasználói csoportok nem kapják meg az e-maileket. Ez a probléma akkor merül fel, amikor az új munkaterületek egyike egy prémium szintű kapacitásban található, az előfizetést létrehozó felhasználó Saját munkaterülete azonban nem. Ha a Saját munkaterület egy Prémium szintű kapacitásban található, az ingyenes felhasználók és felhasználói csoportok is megkapják az e-maileket.
- Miután egy munkaterületet áthelyez egy Prémium szintű kapacitásból egy megosztott kapacitásba, az ingyenes felhasználók és felhasználói csoportok egyes esetekben továbbra is kapnak e-maileket, annak ellenére, hogy már nem szabadna. Ez a probléma akkor merül fel, az előfizetést létrehozó felhasználó Saját munkaterülete egy Prémium szintű kapacitásban található.

## <a name="next-steps"></a>Következő lépések
* [Jelenlegi munkaterületek létrehozása](service-create-workspaces.md)
* [Alkalmazások telepítése és használata a Power BI-ban](service-create-distribute-apps.md)
* Kérdése van? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
