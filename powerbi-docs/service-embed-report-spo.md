---
title: Beágyazás jelentéskijelzővel a SharePoint Online-ban
description: A Power BI új beágyazás jelentéskijelzővel a SharePoint Online-ban funkciójának használatával interaktív Power BI-jelentéseit könnyedén SharePoint Online-oldalakba illesztheti.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 05/16/2019
ms.openlocfilehash: c5d35c1e7fef15c72314738c1d67f81656dc3101
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71073621"
---
# <a name="embed-with-report-web-part-in-sharepoint-online"></a>Beágyazás jelentéskijelzővel a SharePoint Online-ban

A Power BI új beágyazás jelentéskijelzővel a SharePoint Online-ban funkciójának használatával interaktív Power BI-jelentéseit könnyedén SharePoint Online-oldalakba illesztheti.

Az új **Beágyazás a SharePoint Online-ban** funkció használatával a beágyazott jelentések teljes biztonságban vannak, így könnyedén hozhat létre biztonságos belső portálokat.

## <a name="requirements"></a>Követelmények

A **Beágyazás a SharePointban** funkcióval készülő jelentések működésének feltételei az alábbiak:

* Power BI Pro-licenc vagy [Power BI Premium-kapacitás (EM vagy P termékváltozat)](service-premium-what-is.md) Power BI-licenccel.
* A Power BI-jelentéskijelző a SharePoint Online-hoz csak [Modern weblapokkal](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b) működik.

## <a name="embed-your-report"></a>A jelentés beágyazása
A jelentés SharePoint Online-ba való beágyazásához be kell szereznie a jelentés URL-címét, amelyet a SharePoint Online Power BI-kijelzőjében használhat.

### <a name="get-a-report-url"></a>A jelentés URL-címének beszerzése

1. Tekintse meg a jelentést a Power BI-ban.

2. Válassza a **Fájl** legördülő menüt, majd a **Beágyazás a SharePoint Online-ban** menüpontot.

    ![Fájl menü](media/service-embed-report-spo/powerbi-file-menu.png)

3. A párbeszédpanelről másolja ki a jelentés URL-címét.

    ![Hivatkozás beágyazása](media/service-embed-report-spo/powerbi-embed-link-sharepoint.png)

### <a name="add-the-power-bi-report-to-a-sharepoint-online-page"></a>A Power BI-jelentés hozzáadása a SharePoint Online laphoz

1. Nyissa meg a céllapot a SharePoint Online-ban, és válassza a **Szerkesztés** lehetőséget.

    ![SP-szerkesztések lap](media/service-embed-report-spo/powerbi-sharepoint-edit-page.png)

    Azt is megteheti, hogy a SharePoint Online-ban az **+ Új** lehetőséggel hoz létre új, modern weboldalt.

    ![Új SP-lap](media/service-embed-report-spo/powerbi-sharepoint-new-page.png)

2. Válassza a **+** jelű legördülő menüt, majd válassza ki a **Power BI** webes kijelzőt.

    ![Új SP-kijelző](media/service-embed-report-spo/powerbi-sharepoint-new-web-part.png)

3. Válassza ki a **Jelentés hozzáadása** lehetőséget.

    ![Új SP-jelentés](media/service-embed-report-spo/powerbi-sharepoint-new-report.png)  

4. Illessze be a jelentés korábban kimásolt URL-címét a **Power BI-jelentésre mutató hivatkozás** panelen. A jelentés automatikusan betöltődik.

    ![Új SP-kijelző tulajdonságai](media/service-embed-report-spo/powerbi-sharepoint-new-web-part-properties.png)

5. Válassza a **Közzététel** lehetőséget ahhoz, hogy a változtatásokat a többi SharePoint Online-felhasználó is megtekinthesse.

    ![SP-jelentés betöltve](media/service-embed-report-spo/powerbi-sharepoint-report-loaded.png)

## <a name="grant-access-to-reports"></a>Hozzáférés biztosítása a jelentésekhez

Egy jelentés beágyazása a SharePoint Online-ba még nem ad automatikusan engedélyt a felhasználóknak arra, hogy megtekinthessék a jelentést – a megtekintési jogosultságokat a Power BI-ban kell beállítania.

> [!IMPORTANT]
> Tekintse át kik láthatják a jelentést a Power BI szolgáltatásban, és adjon hozzáférést azoknak, akik még nem szerepelnek a listában.

A Power BI-ban két módon adhat hozzáférést a jelentésekhez. Az első, hogy ha a SharePoint Online-csoportwebhely létrehozásához Office 365-csoportot használ, akkor a felhasználót hozzáadhatja tagként az **alkalmazás-munkaterülethez a Power BI szolgáltatásban** és a **SharePoint-oldalon**. További információkért lásd: [Alkalmazás-munkaterület kezelése](service-manage-app-workspace-in-power-bi-and-office-365.md).

A másik lehetőség, hogy egy alkalmazásban ágyaz be egy jelentést, és közvetlenül megosztja azt a felhasználókkal:  

1. A szerző, akinek Pro-felhasználónak kell lennie, jelentést hoz létre egy alkalmazás-munkaterületen. Ahhoz, hogy az alkalmazás-munkaterület megosztható legyen az *ingyenes Power BI-felhasználókkal*, az alkalmazás-munkaterületet *Premium-munkaterületként* kell beállítani.

2. A szerző közzéteszi, majd telepíti az alkalmazást. A szerzőnek telepítenie kell az alkalmazást, hogy az hozzáférjen a jelentés SharePoint Online-beli beágyazásához használt URL-címhez.

3. Mostantól az összes végfelhasználónak is telepítenie kell az alkalmazást. Használhatja a [Power BI felügyeleti portálján](service-admin-portal.md) engedélyezhető **Alkalmazás automatikus telepítése** funkciót is, hogy az alkalmazás előre telepítve legyen a végfelhasználók számára.

   ![Alkalmazás automatikus telepítése](media/service-embed-report-spo/install-app-automatically.png)

4. A szerző megnyitja az alkalmazást és a jelentést.

5. A szerző kimásolja a beágyazott jelentés URL-címét az alkalmazás által telepített jelentésből. Ne a jelentés alkalmazás-munkaterületről származó eredeti URL-címét használja.

6. Hozzon létre egy új csoportwebhelyet a SharePoint Online-ban.

7. Adja hozzá a jelentés korábban kimásolt URL-címét a Power BI webes kijelzőhöz.

8. Vegye fel az összes olyan felhasználót és/vagy csoportot, akik dolgozni fognak a létrehozott SharePoint Online oldalon és a Power BI alkalmazásban.

    > [!NOTE]
    > **Ahhoz, hogy a felhasználók és a csoportok a SharePoint Online-oldalon láthassák a jelentést, hozzá kell férniük a SharePoint Online-oldalhoz és a Power BI-ban lévő jelentéshez.**

Mostantól a végfelhasználó hozzáfér a SharePoint Online-on lévő csoportwebhelyhez, és láthatja rajta a jelentést.

## <a name="multi-factor-authentication"></a>Többtényezős hitelesítés

Ha a Power BI-környezetbe való bejelentkezéshez többtényezős hitelesítésre van szükség, akkor előfordulhat, hogy a rendszer arra kéri, hogy személyazonossága igazolásához jelentkezzen be egy biztonsági eszközzel. Ez olyankor fordul elő, amikor a SharePoint Online-ba nem többtényezős hitelesítés használatával jelentkezik be, a Power BI-környezetbe való belépéshez biztonsági eszköznek kell hitelesítenie a fiókot.

> [!NOTE]
> A Power BI egyelőre nem támogatja a többtényezős hitelesítést a Azure Active Directory 2.0-val – a felhasználók hibaüzenetet kapnak. Ha a felhasználó egy biztonsági eszköz használatával újból bejelentkezik a SharePoint Online-ba, akkor megtekintheti a jelentést.

## <a name="web-part-settings"></a>A jelentéskijelző beállításai

A Power BI webes kijelző alábbi beállításait adhatja meg a SharePoint Online-hoz.

![SP-kijelző tulajdonságai](media/service-embed-report-spo/powerbi-sharepoint-web-part-properties.png)

| Tulajdonság | Leírás |
| --- | --- |
| Oldal neve |A webes kijelző alapértelmezett oldalát állítja be. Válasszon ki egy értéket a legördülő listából. Ha nem jelenik meg egyetlen oldal sem a listában, akkor vagy csak egyetlen oldalból áll a jelentés, vagy a bemásolt URL-cím már tartalmazza az egyik oldal nevét. Ahhoz, hogy a listából választhasson ki egy adott oldalt, el kell távolítani a jelentésre hivatkozó szakaszt az URL-címből. |
| Megjelenítés |A jelentés SharePoint Online-oldalon belüli igazítását állítja be. |
| Navigációs ablaktábla megjelenítése |Megjeleníti vagy elrejti az oldal navigációs ablaktábláját. |
| Szűrés ablaktábla megjelenítése |Megjeleníti vagy elrejti a szűrés ablaktábláját. |

## <a name="reports-that-do-not-load"></a>Nem betöltődő jelentések

Ha a jelentést nem sikerül betölteni a Power BI webes kijelzőbe, az alábbi üzenet jelenhet meg:

![Üzenet: Ez a tartalom nem elérhető](media/service-embed-report-spo/powerbi-sharepoint-report-not-found.png)

Ennek általában két oka lehet:

1. Nem rendelkezik hozzáféréssel a jelentéshez.
2. A jelentést időközben törölték.

A probléma elhárításához lépjen kapcsolatba a SharePoint Online-oldal tulajdonosával.

## <a name="licensing"></a>Licencelés

Egy jelentést SharePointban megtekintő felhasználónak vagy **Power BI Pro**-licencre van szüksége, vagy a tartalomnak kell **[Power BI Premium-kapacitáson (EM vagy P termékváltozat)](service-admin-premium-purchase.md)** lévő munkaterületen lennie.

## <a name="known-issues-and-limitations"></a>Ismert problémák és korlátozások

* Hiba: „Hiba történt, kérjük jelentkezzen ki, és újból be, majd nyissa meg ismét az oldalt. Korrelációs azonosító: nem meghatározott, http-válasz állapota: 400, kiszolgáló hibakódja: 10001, üzenet: Hiányzó frissítési jogkivonat”
  
  Ha ez a hibaüzenet jelenik meg, próbálkozzon az alábbi hibaelhárítási lépések egyikével.
  
  1. Jelentkezzen ki a SharePointból, majd jelentkezzen be ismét. Ügyeljen rá, hogy az összes böngészőablakot bezárja az újbóli bejelentkezés előtt.

  2. Ha a felhasználói fiókba való belépéshez többtényezős hitelesítés (MFA) szükséges, akkor az MFA-eszközzel jelentkezzen be a SharePoint Online-ba (telefonalkalmazás, intelligens kártya stb.).
  
  3. Az Azure B2B-vendégfelhasználói fiókok nem támogatottak. A felhasználók a kijelző betöltését mutató Power BI-logót látják, de a jelentés nem jelenik meg.

* A Power BI nem ugyanazokat a honosított nyelveket támogatja mint a SharePoint Online. Emiatt előfordulhat, hogy a beágyazott jelentés nem megfelelően honosított nyelven jelenik meg.

* Ha Internet Explorer 10-es böngészőt használ, előfordulhat, hogy problémákba ütközik. <!--You can look at the [browsers support for Power BI](consumer/end-user-browsers.md) and for [Office 365](https://products.office.com/office-system-requirements#Browsers-section). -->

* A Power BI jelentéskijelzője nem érhető el az [országos felhőkben](https://powerbi.microsoft.com/clouds/).

* A klasszikus SharePoint-kiszolgáló nincs támogatva ehhez a webes kijelzőhöz.

* Az [URL-szűrőket](service-url-filters.md) nem támogatja a SPO webes kijelző.

## <a name="next-steps"></a>Következő lépések

* [Modern weboldalak végfelhasználók általi létrehozásának engedélyezése vagy letiltása](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b)  
* [Alkalmazások létrehozása és terjesztése a Power BI-ban](service-create-distribute-apps.md)  
* [Irányítópult megosztása munkatársakkal és másokkal](service-share-dashboards.md)  
* [Mi a Power BI Premium?](service-premium-what-is.md)
* [Jelentés beágyazása egy biztonságos portálon vagy webhelyen](service-embed-secure.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)