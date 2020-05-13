---
title: Power BI-irányítópult és -jelentés megosztása munkatársakkal és másokkal
description: Tudnivalók Power BI-irányítópultoknak és -jelentéseknek a cégen belüli és kívüli munkatársakkal való megosztásáról és általában a megosztásról.
author: maggiesMSFT
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/26/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 119571e49b69ad6e3c6cfa0a7d3758912ebec0dc
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83348114"
---
# <a name="share-power-bi-dashboards-and-reports-with-coworkers-and-others"></a>Power BI-irányítópult és -jelentés megosztása munkatársakkal és másokkal
A *Megosztással* egyszerűen biztosíthatja néhány személy hozzáférését az irányítópultjaihoz és jelentéseihez. A Power BI-ban [többféle módon valósítható meg az irányítópultok és jelentések közös használata és terjesztése](service-how-to-collaborate-distribute-dashboards-reports.md).

![Megosztás ikon az irányítópultok listájában](media/service-share-dashboards/power-bi-share-new-look.png)

Akár a cégen belül, akár a cégen kívül oszt meg tartalmat, a megosztáshoz [Power BI Pro](../fundamentals/service-features-license-type.md)-licencre van szükség. Ha a tartalom nem [Prémium kapacitást](../admin/service-premium-what-is.md) használ, akkor a megosztás címzettjeinek is Power BI Pro-licenccel kell rendelkezniük. 

Az irányítópultok és jelentések megosztása a Power BI szolgáltatás legtöbb helyén elvégezhető: A Kedvencek, a Legutóbbi, a Saját munkaterület, a Velem megosztva, ha a tulajdonos engedélyezte. Más munkaterületekről is megoszthat, ha a munkaterületen [rendszergazda, tag vagy közreműködő](service-new-workspaces.md#roles-in-the-new-workspaces) szerepkörrel rendelkezik. 

A megosztott irányítópultot vagy jelentést a címzettjei megtekinthetik és használhatják, de nem szerkeszthetik. Az irányítópultok és a jelentések adatait ugyanúgy látják, ahogyan Ön is, hacsak nem alkalmaz [sorszintű biztonságot (RLS-t)](../admin/service-admin-rls.md). A munkatársai, akikkel megosztotta a tartalmat, továbboszthatják azt másokkal, ha engedélyezi. A cégén kívüli címzettek is megtekinthetik és használhatják, de nem szerkeszthetik az irányítópultot vagy jelentést. 

Közvetlenül a Power BI Desktopból nem lehetséges *megosztást* végezni. A [jelentéseket a Power BI Desktopból](../create-reports/desktop-upload-desktop-files.md) a Power BI szolgáltatásba teheti közzé. Irányítópultot azonban [megoszthat a Power BI mobilalkalmazásból](../consumer/mobile/mobile-share-dashboard-from-the-mobile-apps.md).  

## <a name="video-share-a-dashboard"></a>Videó: Irányítópult megosztása
Nézze meg, hogyan osztja meg Amanda az irányítópultját cégen belüli és azon kívüli munkatársaival. Ezután a videó alatt látható részletes utasításokat követve próbálkozzon meg a feladat elvégzésével.

<iframe width="560" height="315" src="https://www.youtube.com/embed/0tUwn8DHo3s?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="share-a-dashboard-or-report"></a>Irányítópult vagy jelentés megosztása

1. Irányítópultok vagy jelentések listájában, vagy egy megnyitott irányítópulton vagy jelentésben válassza a **Megosztás** ![Megosztás ikon](media/service-share-dashboards/power-bi-share-icon.png) lehetőséget.

2. A felső mezőbe írja be a személyek, terjesztési csoportok vagy biztonsági csoportok teljes e-mail-címét. Dinamikus terjesztési listákkal nem oszthat meg irányítópultot. 
   
   A megosztás címzettjei lehetnek a cégen kívüli címmel rendelkező személyek is, de ilyenkor figyelmeztetés jelenik meg. A [szervezeten kívüli megosztásról](#share-a-dashboard-or-report-outside-your-organization) ebben a cikkben olvashat részletesebben.
   
   ![Figyelmeztetés külső megosztás esetén](media/service-share-dashboards/power-bi-share-dialog-warning.png) 
 
   >[!NOTE]
   >A beviteli mező legfeljebb 100 különböző felhasználót vagy csoportot engedélyez. A [Több mint 100 felhasználóval történő megosztásról](#share-with-more-than-100-separate-users) szóló részben ebben a cikkben tájékozódhat arról, hogyan lehet több személlyel is megosztani tartalmat.

3. Ha kívánja, hozzáfűzhet egy üzenetet. Ez nem kötelező.
4. Jelölje be az **Irányítópult vagy jelentés megosztásának engedélyezése a címzetteknek** lehetőséget, hogy a munkatársai megoszthassák másokkal a tartalmakat.
   
   A mások általi megosztás neve *újraosztás*. Akiknek engedélyezi, azok újraoszthatják az irányítópultot a Power BI szolgáltatásból vagy mobilalkalmazásokból, vagy továbbíthatják a meghívó e-mailt a cégen belüli más személyeknek. A meghívó egy hónap után lejár. A cégen kívüli személyek nem tudnak újraosztani. A tartalom tulajdonosaként kikapcsolhatja az újraosztás engedélyezését, és egyedi esetekre lebontva is engedélyezheti az újraosztást. Lásd a [Megosztás leállítása vagy módosítása](#stop-or-change-sharing) részt ebben a cikkben.

5. Ha kiválasztja az **Új tartalom az alapul szolgáló adathalmazokból történő létrehozásának engedélyezése a felhasználóknak** beállítást, a felhasználók létrehozhatnak saját jelentéseket más munkaterületeken az irányítópult adatkészlete alapján. További információ [jelentések létrehozásáról más munkaterületen lévő adathalmazok alapján](../connect-data/service-datasets-discover-across-workspaces.md).

1. Válassza a **Megosztás** lehetőséget.
   
   ![Megosztás gomb választása](media/service-share-dashboards/power-bi-share-dialog-share.png)  
   
   A Power BI a megosztott tartalomra mutató hivatkozást tartalmazó e-mailt küld az egyéni felhasználóknak, de a csoportoknak nem. Ilyenkor üzenet jelenik meg a **sikeres** végrehajtásról. 
   
   Amikor egy cégen belüli címzett a hivatkozásra kattint, a Power BI hozzáadja az irányítópultot vagy a jelentést a az ő **Velem megosztva** listázó oldalához. A címzett az Ön nevét kijelölve megtekintheti az összes Ön által vele megosztott tartalmat. 
   
   ![Velem megosztva listázó oldal](media/service-share-dashboards/power-bi-shared-with-me-new-look.png)
   
   Amikor egy cégen kívüli címzett a hivatkozásra kattint, akkor látni fogja az irányítópultot vagy a jelentést, de nem a szokásos Power BI-portálon. A [szervezeten kívüli megosztásról](#share-a-dashboard-or-report-outside-your-organization) ebben a cikkben olvashat részletesebben.

## <a name="see-who-has-access-to-a-dashboard-or-report"></a>Az irányítópulthoz vagy a jelentéshez hozzáférő felhasználók megtekintése
Előfordul, hogy tudnia kell, kikkel osztott meg tartalmat, és hogy ők kivel osztották újra.

1. Az irányítópultok vagy jelentések listájában vagy magán az irányítópulton vagy jelentésen válassza a **Megosztás** lehetőséget ![Megosztás ikon](media/service-share-dashboards/power-bi-share-icon.png). 
2. Az **Irányítópult megosztása** vagy **Jelentés megosztása** párbeszédpanelen válassza a **Hozzáférés** lehetőséget.
   
    ![Megosztás párbeszédablak, Hozzáférés lap](media/service-share-dashboards/power-bi-share-dialog-access.png)

    A cégen kívüli személyek **Vendég** hozzáféréssel jelennek meg.

    Ebben a nézetben [leállíthatja vagy módosíthatja a megosztási engedélyeket](#stop-or-change-sharing) ebben a cikkben. 

## <a name="share-a-dashboard-or-report-outside-your-organization"></a>Irányítópult vagy jelentés megosztása cégen kívüli személyekkel
A megosztás cégen kívüli címzettjei e-mailt kapnak a megosztott irányítópultra vagy jelentésre mutató hivatkozással. Ahhoz, hogy láthassák, hogy Ön mit osztott meg velük, be kell jelentkezniük a Power BI-ba. Ha nem rendelkeznek Power BI Pro-licenccel, akkor igényelhetnek egyet, miután a hivatkozásra kattintottak.

Bejelentkezés után a saját böngészőjükben tekinthetik meg a megosztott irányítópultot vagy jelentést, nem pedig a szokásos Power BI-portálon. Az irányítópult vagy jelentés jövőbeni eléréséhez menteniük kell a hivatkozást a kedvencek közé.

Ennek az irányítópultnak vagy jelentésnek a tartalmát egyáltalán nem módosíthatják. Használhatják a diagramokat és megváltoztathatják a szűrőket vagy a szeletelőket, de a változásokat nem menthetik. 

A megosztott irányítópultot vagy jelentést csak a közvetlen címzettek láthatják. Ha az e-mailt például a Vicki@contoso.com címre küldte, akkor az irányítópultot csak Vicki tekintheti meg. Az irányítópultot senki más nem láthatja, még ha Vicki el is küldi nekik a hivatkozást. Vickinek ugyanazt az e-mail-címet kell használnia a hozzáféréshez. Ha más e-mail-címmel jelentkezik be, akkor ő sem fog hozzáférni az irányítópulthoz.

A cégen kívüli személyek egyáltalán nem fogják látni az adatokat, ha szerepkör- vagy sorszintű biztonság van alkalmazva a helyszíni Analysis Services rendszerbeli táblázatos modellekben.

Külső e-mail-címmel rendelkező személyeket is magában foglaló csoporttal való megosztáshoz terjesztési csoport helyett használjon biztonsági csoportot. A terjesztési csoportok külső e-mail-címmel rendelkező tagjai csak akkor láthatják a megosztott tartalmat, ha B2B vendégfelhasználók az Azure Active Directoryban (Azure AD). További információ az [Azure AD B2B vendégfelhasználókról](../admin/service-admin-azure-ad-b2b.md).

Ha Power BI-mobilalkalmazásból küld hivatkozást cégen kívüli címzettnek, akkor a hivatkozásra kattintva az irányítópult böngészőben fog megnyílni, nem a Power BI-mobilalkalmazásban.

### <a name="allow-external-users-to-edit-content"></a>Tartalom szerkesztésének engedélyezése külső felhasználók számára

A Power BI-rendszergazda engedélyezheti, hogy külső vendégfelhasználók is szerkeszthessék és kezelhessék a szervezeti tartalmakat. Ebben az esetben a felhasználók nem csak a fogyasztói élményt használhatják. A szervezeten belül szerkeszthetik és kezelhetik is a tartalmakat. Lásd a [Power BI-tartalmak terjesztése Azure AD B2B külső vendégfelhasználóknak](../admin/service-admin-azure-ad-b2b.md) című témakört.

## <a name="stop-or-change-sharing"></a>Megosztás leállítása vagy módosítása
Az újraosztást csak az irányítópult vagy jelentés tulajdonosa kapcsolhatja be és ki.

### <a name="if-you-havent-sent-the-sharing-invitation-yet"></a>Ha még nem küldte el a megosztási meghívót
* Szüntesse meg az **Irányítópult vagy jelentés megosztásának engedélyezése a címzetteknek** jelölőnégyzet kijelölését a meghívó alján, mielőtt elküldené.

### <a name="if-youve-already-shared-the-dashboard-or-report"></a>Ha már megosztotta az irányítópultot vagy jelentést
1. Az irányítópultok vagy jelentések listájában vagy magán az irányítópulton vagy jelentésen válassza a **Megosztás** lehetőséget ![Megosztás ikon](media/service-share-dashboards/power-bi-share-icon.png). 
2. Az **Irányítópult megosztása** vagy **Jelentés megosztása** párbeszédpanelen válassza a **Hozzáférés** lehetőséget.
   
    ![Megosztás párbeszédablak, Hozzáférés lap](media/service-share-dashboards/power-bi-share-dialog-access.png)
3. Válassza az **Olvasás és újraosztás** lehetőség melletti három pontot ( **...** ), majd a következőt:
   
   ![Olvasás és újraosztás három pontja](media/service-share-dashboards/power-bi-change-access.png)
   
   * **Olvasás**, hogy a címzett ne oszthassa meg az irányítópultot másokkal.
   * **Hozzáférés letiltása**, hogy az adott személy ne is tekinthesse meg a megosztott tartalmat.

4. A **Hozzáférés letiltása** párbeszédablakban arra is lehetősége van, hogy a kapcsolódó tartalmakhoz (például jelentésekhez vagy adatkészletekhez) való hozzáférést is letiltsa. Ha ilyen figyelmeztető ikonnal ![Power BI figyelmeztető ikon](media/service-share-dashboards/power-bi-warning-icon.png) rendelkező elemet távolít el, ajánlatos a kapcsolódó tartalmat is eltávolítani. Ellenkező esetben nem jelenik meg megfelelően.

    ![A Power BI megosztásra figyelmeztető párbeszédpanele](media/service-share-dashboards/power-bi-sharing-warning-dialog.png)

## <a name="limitations-and-considerations"></a>Korlátozások és szempontok
Irányítópultok vagy jelentések megosztásakor vegye figyelembe a következőket:

* Ön és a munkatársai általában ugyanazokat az adatokat látják az irányítópulton vagy jelentésen. Ha tehát Ön több adathoz jogosult hozzáférni mint ők, akkor az irányítópultján vagy jelentésén ők is látni fogják az összes adatát. Ha azonban [sorszintű biztonság (RLS)](../admin/service-admin-rls.md) van érvényben egy irányítópult agy jelentés alapjául szolgáló adatkészletben, akkor a hozzáférhető adatok köre az egyes személyek hitelesítő adatai alapján lesz meghatározva.
* Mindenki, akivel Ön megosztotta az irányítópultot, megtekintheti és használhatja a vonatkozó jelentéseket az [Olvasó nézetben](../consumer/end-user-reading-view.md#reading-view). Általánosságban nem hozhatnak létre jelentéseket és nem menthetik a meglévő jelentések módosításait. Ha azonban kiválasztja az **Új tartalom az alapul szolgáló adathalmazokból történő létrehozásának engedélyezése a felhasználóknak** beállítást, a felhasználók létrehozhatnak saját jelentéseket más munkaterületeken az irányítópult vagy jelentés adatkészlete alapján.
* Az adatkészletet senki nem láthatja és nem töltheti le, de közvetlenül elérhetik azt az Elemzés az Excelben funkcióval. A rendszergazda úgy korlátozhatja az Elemzés az Excelben funkciót, hogy egy adott csoporton belül mindenkire kiterjeszti a korlátozást. A korlátozás azonban a csoport minden tagjára vonatkozik, és minden olyan munkaterületre kiterjed, amelyhez a csoport tartozik.
* Manuálisan mindenki [frissítheti az adatokat](../connect-data/refresh-data.md).
* Ha a levelezéshez az Office 365-öt használja, akkor a megosztás címzettjeként egy terjesztési csoportot is megadhat a csoporthoz tartozó e-mail-cím beírásával.
* Az Önnel egy e-mail-tartományban lévő munkatársai, valamint a más, de ugyanazon a bérlőn belül regisztrált tartományok tagjai másokkal is megoszthatják az irányítópultot. Legyen például a contoso.com és a contoso2.com tartomány egy bérlőn belül regisztrálva, és az Ön e-mail-címe konrads@contoso.com. Ekkor gustav@contoso2.com és ravali@contoso.com egyaránt megoszthatja az Ön irányítópultját, ha Ön engedélyezte számukra a megosztást.
* Ha munkatársai már hozzáférnek egy adott irányítópulthoz vagy jelentéshez, akkor nekik az irányítópultról vagy jelentésből kimásolt közvetlen hivatkozást is küldhet. Példa: `https://powerbi.com/dashboards/g12466b5-a452-4e55-8634-xxxxxxxxxxxx`.
* Hasonló módon [a mögöttes jelentésre mutató közvetlen hivatkozást is küldhet](service-share-reports.md) az adott irányítópulthoz hozzáféréssel rendelkező munkatársaknak. 

### <a name="share-with-more-than-100-separate-users"></a>Megosztás több mint 100 különböző felhasználóval

Egy megosztási műveletben legfeljebb 100 felhasználóval vagy csoporttal oszthat meg tartalmat. Egy elemhez azonban több mint 500 felhasználónak adhat hozzáférést. Íme néhány javaslat:

- Többször is megoszthatja a tartalmat a felhasználók egyenkénti megadásával.
- Olyan csoporttal osszon meg, amely az összes felhasználót tartalmazza. 
- Hozza létre a jelentést vagy az irányítópultot egy munkaterületen, majd hozzon létre egy alkalmazást a munkaterületről. Az alkalmazást sokkal több személlyel is megoszthatja. További információ az [alkalmazások Power BI-beli közzétételéről](service-create-distribute-apps.md).

## <a name="troubleshoot-sharing"></a>A megosztás hibaelhárítása

### <a name="my-dashboard-recipients-see-a-lock-icon-in-a-tile-or-a-permission-required-message"></a>Az irányítópult címzettjeinek lakat ikon vagy „Engedély szükséges” szöveg jelenik meg a címben

Előfordulhat, hogy a megosztás címzettjeinek lakat ikon vagy „Engedély szükséges” szöveg jelenik meg a címben, amikor meg akarják nézni a jelentést.

![Blokkolt Power BI-csempe](media/service-share-dashboards/power-bi-locked_tile_small.png)

Ha ez történik, engedélyt kell adnia nekik az alapul szolgáló adatkészlethez való hozzáféréshez.

1. A tartalomlistában nyissa meg az **Adatkészlet** lapot.

1. Az adatkészlet mellett válassza a három pontot ( **...** ), majd az **Engedélyek kezelése** lehetőséget.

    ![Engedélyek kezelése](media/service-share-dashboards/power-bi-sharing-manage-permissions.png)

1. Válassza a **Felhasználó hozzáadása** elemet.

    ![Felhasználó hozzáadása kiválasztása](media/service-share-dashboards/power-bi-share-dataset-add-user.png)

1. Írja be a személyek, terjesztési csoportok vagy biztonsági csoportok teljes e-mail-címét. Dinamikus terjesztési listákkal nem oszthat meg irányítópultot.

    ![E-mail címek hozzáadása](media/service-share-dashboards/power-bi-add-user-dataset.png)


1. Válassza a **Hozzáadás** elemet.

### <a name="i-cant-share-a-dashboard-or-report"></a>Nem tudok irányítópultot vagy jelentést megosztani

Az irányítópult vagy jelentés megosztásához rendelkeznie kell a mögöttes tartalmak (minden kapcsolódó jelentés és adatkészlet) újraosztásához szükséges jogosultságokkal. Ha olyan üzenetet kap, amely szerint nincs jogosultsága a megosztáshoz, forduljon a jelentés tulajdonosához, aki engedélyt adhat Önnek az adott jelentések és adatkészletek újraosztásához.

![A „Megosztás nem lehetséges” üzenet](media/service-share-dashboards/power-bi-sharing-unable-to-share.png)


## <a name="next-steps"></a>Következő lépések

* [Irányítópultok és jelentések közös használata és megosztása](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Szűrt Power BI-jelentés megosztása](service-share-reports.md)
* Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
