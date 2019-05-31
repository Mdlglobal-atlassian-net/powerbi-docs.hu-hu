---
title: Hozzon létre az új munkaterületek – Power bi-ban
description: Ismerje meg, hogyan hozhat létre az új munkaterületek, irányítópultok, jelentések és a szervezet alapvető metrikákat biztosít oldalakra osztott jelentések gyűjteményei.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/18/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d0c0781ea5d3864f1cf3627cd42d53cca632102d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61142066"
---
# <a name="create-the-new-workspaces-in-power-bi"></a>Az új munkaterületek létrehozása a Power bi-ban

A Power BI-ban bevezetjük új munkaterületi felhasználói élményt. Munkaterületek még hátravan a hely, ahol együttműködhet munkatársaival az irányítópultok, jelentések és tördelt jelentések gyűjteményeit hozhatja létre. Akkor is kötegeli az adott gyűjtemény egy *alkalmazás* és osztja el a teljes cég számára, vagy adott személyek vagy csoportok számára. 

Íme, mi a. Az új munkaterületek a következőket teheti:

- Munkaterület-szerepköröket rendelhet felhasználói csoportokhoz: biztonsági csoportokhoz, terjesztési listákhoz, Office 365-csoportokhoz és egyéni felhasználókhoz.
- Office 365-csoport létrehozása nélkül hozhat létre egy Power BI-munkaterületet.
- Részletesebb munkaterület-szerepköröket használhat, amelyekkel rugalmasabb engedélykezelést érhet el a munkaterületeken.

> [!NOTE]
> Sorszintű biztonság (RLS) a Power BI Pro felhasználói munkaterületen lévő tartalom tallózása kényszerítéséhez továbbra is az [klasszikus munkaterületek](service-create-workspaces.md). Válassza ki a **tagok csak a Power BI-tartalmak megtekintésére** lehetőséget. Azt is megteheti Power BI alkalmazások közzététele a felhasználók számára, vagy a tartalom terjesztése a megosztás használatával. A soron következő megjelenítő szerepkör lehetővé teszi az ebben a forgatókönyvben a jövőben az új munkaterületi felhasználói élményt munkaterületek.

A további háttér-információkért lásd: a [új munkaterületek](service-new-workspaces.md) cikk.

## <a name="create-one-of-the-new-app-workspaces"></a>Új típusú alkalmazás-munkaterület létrehozása

1. Kezdje az alkalmazás-munkaterület létrehozásával. Válassza a **Munkaterületek** > **Alkalmazás munkaterületének létrehozása** lehetőséget.
   
     ![Alkalmazás munkaterületének létrehozása](media/service-create-the-new-workspaces/power-bi-create-app-workspace.png)

2. Kivéve, ha úgy dönt, automatikusan hoz létre egy frissített munkaterület **visszatér a klasszikus**.
   
     ![Új munkaterületi felhasználói élmény](media/service-create-the-new-workspaces/power-bi-new-workspace.png)
     
     Ha **visszatér a klasszikus**, akkor hozzon létre egy munkaterületet, az Office 365-csoport alapján. Használja ezt a beállítást, ha van szüksége a **tagok csak a Power BI-tartalmak megtekintésére** szeretné kényszeríteni a sorszintű biztonság (RLS) a munkaterület tagjainak lehetőséget.

2. Nevezze el a munkaterületet. Ha a név nem érhető el, hozzon létre egy egyedi nevet a szerkesztése.
   
     Az alkalmazás a munkaterülethez, a munkaterület neve és ikon tartalmaz.
   
1. Az alábbiakban néhány beállíthatja, hogy a munkaterület nem kötelező elemek:

    Töltse fel a **munkaterület lemezkép**. Fájlok .png vagy .jpg formátumú lehet. Fájl mérete nem lehet kisebb, mint legfeljebb 45 KB.
    
    [Adjon hozzá egy **ügyfél lista**](#workspace-contact-list). Alapértelmezés szerint a munkaterületek rendszergazdái olyan ügyfeleket. 
    
    [Adjon meg egy **munkaterület OneDrive** ](#workspace-onedrive) csak a meglévő Office 365-csoportot, nem az URL-cím név beírásával. Ez a munkaterület mostantól használhatja az adott Office 365-csoport fájl tárolási helyéhez. 

    ![Adjon meg egy OneDrive-helyre](media/service-create-the-new-workspaces/power-bi-new-workspace-onedrive.png)

    A munkaterület hozzárendelése egy **dedikált kapacitás**, az a **prémium** lapon válassza **dedikált kapacitás**.
     
    ![Dedikált kapacitás](media/service-create-the-new-workspaces/power-bi-workspace-premium.png)

1. Kattintson a **Mentés** gombra.

    A Power BI létrehozza és megnyitja a munkaterületet. Megjelenik az olyan munkaterületek listájában, amelyeknek Ön a tagja. 

## <a name="workspace-contact-list"></a>Ismerősök listájának munkaterület

A munkaterület új ismerősök listájának megadása, hogy mely felhasználók kapják a munkaterületen előforduló problémákról értesítést teszi lehetővé. Alapértelmezés szerint minden olyan felhasználó vagy csoport a megadott munkaterületként rendszergazda értesítést kap, de testre szabhatja a listában. Felhasználók vagy csoportok, a kapcsolattartási listában felsorolt megjelenik a felhasználói felületen (UI) segítségével a munkaterülethez kapcsolódó felhasználók segítséget.

1. Hozzáférés az új **ügyfél lista** beállítása a két módszer egyikével:

    Az a **hozzon létre egy munkaterületet** panelen, amikor először hoz létre azt.

    A bal oldali navigációs ablaktáblán válassza ki a nyíl melletti **munkaterületek**, válassza ki a munkaterület neve melletti három pontra (...) > **munkaterület beállításainak**. A **beállítások** panel nyílik meg.

    ![Munkaterület beállításai](media/service-create-the-new-workspaces/power-bi-workspace-settings.png)

2. Alatt **speciális** > **ügyfél lista**, fogadja el az alapértelmezett **munkaterületek rendszergazdái**, vagy adja hozzá a saját listája **adott felhasználók vagy csoportok**. 
3. Kattintson a **Mentés** gombra.

## <a name="workspace-onedrive"></a>Munkaterület onedrive vállalati verzió

A munkaterület OneDrive funkcióval konfigurálja az Office 365-csoportot, amelynek SharePoint-dokumentumtárban fájltároló munkaterület felhasználók számára érhető el. Először hozzon létre a Power BI szolgáltatáson kívül a csoportot. 

A Power BI engedélyeit a felhasználók vagy csoportok, akiknek vannak konfigurálva az Office 365-csoport tagsággal rendelkező munkaterület-hozzáférés nem szinkronizálja. Az ajánlott eljárás az azonos Office 365-csoportot, amelynek ez a beállítás az Office 365 csoport konfigurálja a file storage van ad [hozzáférést a munkaterület](#give-access-to-your-workspace). Munkaterület-hozzáférés kezelését az Office 365-csoport tagságának kezeléséhez. 

1. Hozzáférés az új **munkaterület OneDrive** beállítása a két módszer egyikével:

    Az a **hozzon létre egy munkaterületet** panelen, amikor először hoz létre azt.

    A bal oldali navigációs ablaktáblán válassza ki a nyíl melletti **munkaterületek**, válassza ki a munkaterület neve melletti három pontra (...) > **munkaterület beállításainak**. A **beállítások** panel nyílik meg.

    ![Munkaterület beállításai](media/service-create-the-new-workspaces/power-bi-workspace-settings.png)

2. A **speciális** > **munkaterület OneDrive**, írja be a korábban létrehozott Office 365-csoport nevét. A Power BI automatikusan felveszi a onedrive vállalati verzió, a csoport számára.

    ![Adjon meg egy OneDrive-helyre](media/service-create-the-new-workspaces/power-bi-new-workspace-onedrive.png)

3. Kattintson a **Mentés** gombra.

### <a name="access-the-workspace-onedrive-location"></a>A munkaterület helye a onedrive vállalati verzió eléréséhez

Miután konfigurálta a OneDrive-helyre, érheti el azt a több különböző helyen, a munkaterület:

- Válassza ki **munkaterületek** > *munkaterületnév* > a három pontra ( **...** ) menü > **fájlok**. 

    ![Munkaterület-fájlok helyét](media/service-new-workspaces/power-bi-new-workspace-files.png)

- Kattintson a három pontra ( **...** ) menüben a munkaterület jobb felső sarkában > **fájlok**.

    ![Munkaterület-fájlok helyét](media/service-new-workspaces/power-bi-new-workspace-files-2.png)
    
- Az a **adatok lekérése** > **fájlok** tapasztalható. A **onedrive – vállalati verzió** bejegyzés a saját OneDrive vállalati verzióba. A második onedrive vállalati verzió hozzáadott lesz.

    ![Munkaterület-fájlok helye – az adatok beszerzése](media/service-new-workspaces/power-bi-new-workspace-get-data-onedrive.png)

## <a name="add-content-to-your-app-workspace"></a>Tartalom hozzáadása az alkalmazás-munkaterülethez

Miután létrehozott egy új munkaterületi felhasználói élményt munkaterületet, ideje adhat hozzá a tartalmat. Tartalom hozzáadása az új és klasszikus munkaterületen hasonlít. A Létrehozás gombra, vagy adatok lekérése használatával adja hozzá a tartalmat a munkaterülethez.

1. Az a **üdvözlő** képernyő az új munkaterülethez tartozó tartalmat adhat hozzá. 

    ![Az új munkaterület üdvözlőképernyője](media/service-create-the-new-workspaces/power-bi-workspace-welcome-screen.png)

1. Válassza például a **Minták** > **Ügyfél-jövedelmezőségi minta** lehetőséget.

> [!NOTE]
> Az új munkaterületek, a vállalati tartalomcsomagok vagy külső tartalomcsomagok nem lehet felhasználni. Alkalmazások érhetők el az összes külső tartalomra, csomagok korábban használt. Klasszikus munkaterületet használja, ha használatával tartalomcsomagok továbbra is kell. Tartalomcsomagok elavultak, így az alkalmazások használata ajánlott.

Ha egy alkalmazás-munkaterület tartalomlistájában tekint meg tartalmat, az alkalmazás-munkaterület neve tulajdonosként lesz feltüntetve.

### <a name="connecting-to-third-party-services-in-new-workspaces"></a>Az új munkaterületek külső szolgáltatásokhoz való csatlakozás

Az új munkaterületek felületén az *alkalmazásokra* helyezzük a hangsúlyt. A külső szolgáltatások alkalmazásaival a felhasználók könnyen lekérhetik a használt szolgáltatások, például a Microsoft Dynamics CRM, a Salesforce vagy a Google Analytics adatait.

Az új munkaterületi felhasználói felület nem hozható létre vagy vállalati tartalomcsomagok használata. Ehelyett a megadott alkalmazásokkal csatlakozhat külső szolgáltatásokhoz, vagy megkérheti a belső csapatokat, hogy szolgáltassanak alkalmazásokat a jelenleg használt tartalomcsomagokhoz. 

## <a name="give-access-to-your-workspace"></a>A munkaterülethez való hozzáférést

1. A munkaterület tartalmak listájában, mivel adminisztrátori jogosultsággal megjelenik egy új művelet **hozzáférés**.

    ![Munkaterületek tartalmak listája](media/service-create-the-new-workspaces/power-bi-workspace-content-list.png)

1. Válassza a **Hozzáférés** lehetőséget.

1. Adjon hozzá biztonsági csoportokat, terjesztési listákat, Office 365-csoportokat vagy egyéni felhasználókat a munkaterületekhez tagként, közreműködőként vagy rendszergazdaként. A különböző szerepkörök ismertetését [Az új munkaterületek szerepkörei](service-new-workspaces.md#roles-in-the-new-workspaces) című szakaszban találhatja.

    ![Munkaterületek – tagok, rendszergazdák és közreműködők hozzáadása](media/service-create-the-new-workspaces/power-bi-access-add-members.png)

9. Válassza a **Hozzáadás** > **Bezárás** lehetőséget.


## <a name="distribute-an-app"></a>Alkalmazások terjesztése

Ha egy nagy célközönség számára a szervezeten belül hivatalos tartalmat terjeszteni szeretné, a munkaterületről közzétehet alkalmazásokat.  Amikor készen áll a tartalom, válassza ki, mely irányítópultokat és jelentéseket közzé szeretné tenni, és tegye közzé azt egy *alkalmazás*. Minden munkaterületről létrehozhat egy alkalmazást.

További információ [tegyünk közzé egy alkalmazást, az új munkaterületek](service-create-distribute-apps.md)

## <a name="next-steps"></a>Következő lépések
* További információ [rendszerezéséhez az új munkaterületek funkció a Power bi-ban végzett munka](service-new-workspaces.md)
* [Klasszikus munkaterületek létrehozása](service-create-workspaces.md)
* [Az új munkaterületek az alkalmazás közzététele a Power bi-ban](service-create-distribute-apps.md)
* Kérdése van? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
