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
ms.openlocfilehash: c8789d47ed1b67f9fd6808865514120457a29dfe
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051265"
---
# <a name="embed-with-report-web-part-in-sharepoint-online"></a>Beágyazás jelentéskijelzővel a SharePoint Online-ban

A Power BI új beágyazás jelentéskijelzővel a SharePoint Online-ban funkciójának használatával interaktív Power BI-jelentéseit könnyedén SharePoint Online-oldalakba illesztheti.

Ha az új **beágyazás a SharePoint online-hoz** beállítást, a beágyazott jelentések teljes biztonságban, így könnyedén hozhat létre biztonságos belső portálokat.

## <a name="requirements"></a>Követelmények

A **beágyazás a SharePoint online-hoz** jelentéseinek működéséhez szükség a következő:

* Power BI Pro-licenc vagy egy [Power BI Premium-kapacitás (EM vagy P Termékváltozat)](service-premium-what-is.md) Power BI-licenccel rendelkező.
* A Power BI-jelentéskijelző a SharePoint Online-hoz csak [Modern weblapokkal](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b) működik.

## <a name="embed-your-report"></a>A jelentés beágyazása
A jelentés beágyazása a SharePoint online-hoz, kell a jelentés URL-cím lekérése és használata a SharePoint Online új Power BI-kijelző.

### <a name="get-a-report-url"></a>A jelentés URL-cím beszerzése

1. Power BI-ban a jelentés megtekintéséhez.

2. Válassza ki a **fájl** legördülő menüben, majd válassza ki **beágyazás a SharePoint online-hoz**.

    ![Fájl menü](media/service-embed-report-spo/powerbi-file-menu.png)

3. Másolja a jelentés URL-CÍMÉT a párbeszédpanelről.

    ![Hivatkozás beágyazása](media/service-embed-report-spo/powerbi-embed-link-sharepoint.png)

### <a name="add-the-power-bi-report-to-a-sharepoint-online-page"></a>A Power BI-jelentés hozzáadása a SharePoint Online laphoz

1. Nyissa meg a cél lap a SharePoint online-ban, és válassza ki **szerkesztése**.

    ![SP-szerkesztések lap](media/service-embed-report-spo/powerbi-sharepoint-edit-page.png)

    Vagy a Sharepoint Online-ban válassza **+ új** hozhat létre egy új modern weblapot.

    ![Új SP-lap](media/service-embed-report-spo/powerbi-sharepoint-new-page.png)

2. Válassza ki a **+** legördülő listából, majd a **Power BI**.

    ![Új SP-kijelző](media/service-embed-report-spo/powerbi-sharepoint-new-web-part.png)

3. Válassza ki a **Jelentés hozzáadása** lehetőséget.

    ![Új SP-jelentés](media/service-embed-report-spo/powerbi-sharepoint-new-report.png)  

4. Illessze be a korábban másolt a jelentés URL-CÍMÉT a **Power BI-jelentés hivatkozása** ablaktáblán. A jelentés automatikusan betöltődik.

    ![Új SP-kijelző tulajdonságai](media/service-embed-report-spo/powerbi-sharepoint-new-web-part-properties.png)

5. Válassza a **Közzététel** lehetőséget ahhoz, hogy a változtatásokat a többi SharePoint Online-felhasználó is megtekinthesse.

    ![SP-jelentés betöltve](media/service-embed-report-spo/powerbi-sharepoint-report-loaded.png)

## <a name="grant-access-to-reports"></a>Hozzáférés biztosítása a jelentésekhez

Egy jelentés beágyazása a SharePoint online-hoz nem automatikusan engedélyt a felhasználóknak a jelentés megtekintéséhez,-be kell állítani az engedélyek megtekintése a Power bi-ban.

> [!IMPORTANT]
> Tekintse át kik láthatják a jelentést a Power BI szolgáltatásban, és adjon hozzáférést azoknak, akik még nem szerepelnek a listában.

Két módon adja meg a jelentés-hozzáférés a Power bi-ban. Az első módszer, ha a SharePoint online-hoz csoportwebhely létrehozásához Office 365-csoportot használ, hogy a felhasználó listából, amelynek a **alkalmazás-munkaterületet a Power BI szolgáltatásban** és a **SharePoint-lapba**. További információkért lásd: [Alkalmazás-munkaterület kezelése](service-manage-app-workspace-in-power-bi-and-office-365.md).

A másik lehetőség, hogy az alkalmazáson belül-jelentés beágyazása, és megoszthatja közvetlenül felhasználók:  

1. A szerző (kell lennie a Pro-felhasználó) létrehoz egy jelentést az alkalmazás-munkaterületen. Megosztja **Power BI free-felhasználókkal a**, az alkalmazás-munkaterületre kell állítani egy **prémium munkaterületeken**.

2. A szerző tesz közzé az alkalmazást, és telepíti azt. A szerző kell, hogy a jelentés URL-cím, amellyel a beágyazás a SharePoint online-hoz való hozzáférést az alkalmazás telepítéséhez.

3. Mostantól az összes végfelhasználónak is telepítenie kell az alkalmazást. Is használhatja a **alkalmazás automatikus telepítése** szolgáltatást, amely engedélyezheti a [Power BI felügyeleti portáljához](service-admin-portal.md), hogy az alkalmazás előre telepítve van a végfelhasználók számára.

   ![Alkalmazás automatikus telepítése](media/service-embed-report-spo/install-app-automatically.png)

4. A szerző megnyitja az alkalmazást és a jelentést.

5. A szerző másolja a beágyazási jelentés URL-címet a jelentés az alkalmazás telepítve van. **Ne használja az eredeti jelentés URL-címe az alkalmazás-munkaterületről.**

6. Hozzon létre egy új csoportwebhelyet a SharePoint Online-ban.

7. A Power BI-kijelző hozzáadása a jelentés korábban másolt URL-címe.

8. Vegye fel az összes olyan felhasználót és/vagy csoportot, akik dolgozni fognak a létrehozott SharePoint Online oldalon és a Power BI alkalmazásban.

    > [!NOTE]
    > **Ahhoz, hogy a felhasználók és a csoportok a SharePoint Online-oldalon láthassák a jelentést, hozzá kell férniük a SharePoint Online-oldalhoz és a Power BI-ban lévő jelentéshez.**

Mostantól a végfelhasználó hozzáfér a SharePoint Online-on lévő csoportwebhelyhez, és láthatja rajta a jelentést.

## <a name="multi-factor-authentication"></a>Többtényezős hitelesítés

Ha a Power BI-környezetbe való bejelentkezéshez többtényezős hitelesítésre van szükség, akkor előfordulhat, hogy a rendszer arra kéri, hogy személyazonossága igazolásához jelentkezzen be egy biztonsági eszközzel. Ez akkor fordul elő, ha Ön nem jelentkeztek be a SharePoint online multi-factor authentication szolgáltatás használatával, de a Power BI-környezetbe egy biztonsági eszköz egy fiók érvényesítéséhez szükséges.

> [!NOTE]
> Az Azure Active Directory 2.0 nem támogatja a multi-factor authentication - felhasználók egy hibaüzenetet fog látni. Ha a felhasználó egy biztonsági eszköz használatával újból bejelentkezik a SharePoint Online-ba, akkor megtekintheti a jelentést.

## <a name="web-part-settings"></a>A jelentéskijelző beállításai

Az alábbiakban a beállíthatja a SharePoint online-hoz a Power BI-kijelző beállításait.

![SP-kijelző tulajdonságai](media/service-embed-report-spo/powerbi-sharepoint-web-part-properties.png)

| Tulajdonság | Leírás |
| --- | --- |
| Oldal neve |Megadja a kijelző alapértelmezett oldal. Válasszon ki egy értéket a legördülő listából. Ha nem jelenik meg egyetlen oldal sem a listában, akkor vagy csak egyetlen oldalból áll a jelentés, vagy a bemásolt URL-cím már tartalmazza az egyik oldal nevét. Ahhoz, hogy a listából választhasson ki egy adott oldalt, el kell távolítani a jelentésre hivatkozó szakaszt az URL-címből. |
| Megjelenítés |Itt állíthatja be, hogy a jelentés megfelel-e a SharePoint Online-oldal. |
| Navigációs ablaktábla megjelenítése |Megjeleníti vagy elrejti az oldal navigációs ablaktábláját. |
| Szűrés ablaktábla megjelenítése |Megjeleníti vagy elrejti a szűrés ablaktábláját. |

## <a name="reports-that-do-not-load"></a>Nem betöltődő jelentések

Ha a jelentés nem töltődik a Power BI-kijelző, a következő üzenetet láthatja:

![Ez a tartalom nem érhető el üzenet](media/service-embed-report-spo/powerbi-sharepoint-report-not-found.png)

Ennek általában két oka lehet:

1. Nem rendelkezik a jelentésekhez való hozzáférés.
2. A jelentést időközben törölték.

Lépjen kapcsolatba a SharePoint Online lap tulajdonosát, hogy a probléma megoldásához.

## <a name="licensing"></a>Licencelés

Egy jelentést SharePointban megtekintő felhasználónak vagy **Power BI Pro**-licencre van szüksége, vagy a tartalomnak kell **[Power BI Premium-kapacitáson (EM vagy P termékváltozat)](service-admin-premium-purchase.md)** lévő munkaterületen lennie.

## <a name="known-issues-and-limitations"></a>Ismert problémák és korlátozások

* Hiba: „Hiba történt, kérjük jelentkezzen ki, és újból be, majd nyissa meg ismét az oldalt. Korrelációs azonosító: nem meghatározott, http-válasz állapota: 400, kiszolgáló hibakódja: 10001, üzenet: Hiányzó frissítési jogkivonat”
  
  Ha ez a hibaüzenet jelenik meg, próbálkozzon az alábbi hibaelhárítási lépések egyikével.
  
  1. Jelentkezzen ki a SharePointból, majd jelentkezzen be ismét. Ügyeljen rá, hogy az összes böngészőablakot bezárja az újbóli bejelentkezés előtt.

  2. Ha a felhasználói fiókot igényel a többtényezős hitelesítés (MFA), majd jelentkezzen be a SharePoint használata az MFA-eszköz (telefonalkalmazás, intelligens kártya, stb.).
  
  3. Az Azure B2B-vendégfelhasználói fiókok nem támogatottak. A felhasználók a kijelző betöltését mutató Power BI-logót látják, de a jelentés nem jelenik meg.

* A Power BI nem ugyanazokat a honosított nyelveket támogatja mint a SharePoint Online. Emiatt előfordulhat, hogy a beágyazott jelentés nem megfelelően honosított nyelven jelenik meg.

* Ha Internet Explorer 10-es böngészőt használ, előfordulhat, hogy problémákba ütközik. Tekintse át mely [böngészők használatát támogatja a Power BI](consumer/end-user-browsers.md) és az [Office 365](https://products.office.com/office-system-requirements#Browsers-section).

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