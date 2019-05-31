---
title: Sablonalkalmazások létrehozása a Power BI-ban (előzetes verzió)
description: Bármely Power BI-ügyfél számára terjeszthető sablonalkalmazás létrehozása a Power BI-ban.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 04/22/2019
ms.author: maggies
ms.openlocfilehash: 653050fbe5c860ef1902a4700c3a70a8af2f7092
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514926"
---
# <a name="create-a-template-app-in-power-bi-preview"></a>Sablonalkalmazás létrehozása a Power BI-ban (előzetes verzió)

A Power BI új *sablonalkalmazásai* lehetővé teszik a Power BI-partnerek részére, hogy kevés kódolással vagy anélkül hozzanak létre Power BI-alkalmazásokat, és helyezzék azokat üzembe a Power BI bármely ügyfele számára.  Ez a cikk lépésekre bontott utasításokat tartalmaz Power BI-sablonalkalmazás létrehozásához.

Ha a Power BI-jelentéseket és irányítópultokat hozhat létre, Ön is egy *sablon app builder* , és hozza létre, és az elemzési tartalommal csomagok egy *alkalmazás*. Előfordulhat, hogy más Power BI-bérlők bármely elérhető platformról, például az appsource-ban, vagy saját webes szolgáltatás használatával telepíti az alkalmazását. A jelentéskészítő, hozhat létre védett analytics-csomagot a terjesztési lehetősége van.

A Power BI bérlői rendszergazdái szabályozzák, hogy a vállalatuknál ki hozhat létre sablonalkalmazásokat, és ki telepítheti azokat. Ezek a felhasználók, akik jogosultak a sablonalapú alkalmazásként telepítheti, majd módosítsa, és osztja el a Power BI közvetítését a szervezet.

## <a name="prerequisites"></a>Előfeltételek

A sablonalkalmazások létrehozásának követelményei az alábbiak:  

- Egy [Power BI Pro-licenc](service-self-service-signup-for-power-bi.md)
- A [Power BI Desktop telepítése](desktop-get-the-desktop.md) (nem kötelező)
- Való ismerkedés során bizonyulhat a [alapvető fogalmait, Power bi-ban](service-basic-concepts.md)
- Sablonalkalmazás létrehozásához szükséges engedélyek. Részletekért tekintse meg a Power BI [felügyeleti portálján a sablonalkalmazás beállításait](service-admin-portal.md#template-apps-settings-preview).

## <a name="enable-app-developer-mode"></a>Alkalmazásfejlesztői mód engedélyezése

Ha más Power BI-bérlőkbe terjeszthető sablonalkalmazást szeretne létrehozni, akkor alkalmazásfejlesztői módba kell lépnie. Máskülönben csak a saját cégében hoz létre alkalmazást a Power BI-felhasználók számára.

1. Nyissa meg a Power BI szolgáltatást egy böngészőben.
2. Lépjen a **Beállítások** > **Általános** > **Fejlesztő** > **A sablonalkalmazás fejlesztői módjának engedélyezése** beállításra.

    ![Sablonalkalmazások engedélyezése](media/service-template-apps-create/power-bi-dev-template-app.png)

    Ha ez a lehetőség nem jelenik meg, a lépjen kapcsolatba a felügyeleti portálon a Power BI rendszergazdájával, hogy adjon az Ön számára [engedélyeket sablonalkalmazások fejlesztéséhez](service-admin-portal.md#template-apps-settings-preview).

3. Kattintson az **Alkalmaz** elemre.

## <a name="create-the-template-app-workspace"></a>A sablonalkalmazás munkaterületének létrehozása

Ha más Power BI-bérlőkbe terjeszthető sablonalkalmazást szeretne létrehozni, akkor azt az egyik új alkalmazás-munkaterületen kell létrehoznia.

1. A Power BI szolgáltatásban válassza a **Munkaterületek** > **Alkalmazás munkaterületének létrehozása** lehetőséget.

    ![Alkalmazás munkaterületének létrehozása](media/service-template-apps-create/power-bi-new-workspace.png)

2. Az **Alkalmazás munkaterületének létrehozása** **Továbbfejlesztett munkaterületek – előzetes verzió** alatt válassza a **Kipróbálás** lehetőséget.

    ![Új munkaterületek kipróbálása](media/service-template-apps-create/power-bi-try-now-new-workspace.png)

3. Adjon meg egy nevet, leírást (nem kötelező) és egy embléma képét (nem kötelező) az alkalmazás-munkaterülethez.

4. Válassza a **Sablonalkalmazás kifejlesztése** lehetőséget.

    ![Sablonalkalmazás kifejlesztése](media/service-template-apps-create/power-bi-template-app-develop.png)

5. Kattintson a **Mentés** gombra.
>[!NOTE]
>A sablon alkalmazások előléptetni a Power BI rendszergazdáit engedélyre van szükségük.

## <a name="create-the-content-in-your-template-app"></a>Tartalom létrehozása a sablonalkalmazásban

Csakúgy, mint a szokásos Power BI-munkaterületeknél, a következő lépés a tartalmak létrehozása a munkaterületen.  A sablonalkalmazásoknak ebben az előzetes verziójában a következő típusok közül csak egy támogatott: egy adathalmaz, egy jelentés és egy irányítópult.

- [Power BI-tartalom létrehozása](power-bi-creator-landing.md) az alkalmazás-munkaterületen.

Ha paramétereket használ a Power Queryben, győződjön meg róla, hogy jól meghatározott típussal (például szöveg) rendelkeznek-e. A bármely és a bináris típusok nem támogatottak.

A [Tippek sablonalkalmazások készítéséhez a Power BI-ban (előzetes verzió)](service-template-apps-tips.md) szakasz javaslatokat tartalmaz, amelyeket megfontolhat, amikor jelentéseket és irányítópultokat hoz létre a sablonalkalmazásához.

## <a name="create-the-test-template-app"></a>Tesztcélú sablonalkalmazás létrehozása

Most, hogy van tartalom a munkaterületen, készen áll, hogy becsomagolja azt egy sablonalkalmazásba. Az első lépés egy tesztcélú sablonalkalmazás létrehozása, amely csak a szervezeten belülről érhető el a bérlőjében.

1. A sablonalkalmazás munkaterületén válassza az **Alkalmazás létrehozása** lehetőséget.

    ![Alkalmazás létrehozása](media/service-template-apps-create/power-bi-create-app.png)

    Itt töltse ki további épület beállítások a sablon alkalmazás öt kategóriákban:

    **Védjegyezés**

    ![Védjegyezés](media/service-template-apps-create/power-bi-create-branding.png)
    - Alkalmazás neve
    - Leírás
    - Támogatási webhely (hivatkozás van alatt alkalmazásadatok után bemutatott verziójának terjesztése a szervezeti app alkalmazást sablon)
    - Alkalmazásembléma (45K fájl maximális mérete, 1:1 képarányú, .png, .jpg .jpeg formátumokat)
    - Alkalmazás téma színe

    **Tartalom**

    **App kezdőlapja:** Adja meg egy jelentést vagy irányítópultot az lehet az alkalmazás kezdőlapjára a kezdőlapja, amely a megfelelő benyomást ad használja:

    ![Tartalom](media/service-template-apps-create/power-bi-create-content.png)

    **Vezérlő**

    Állítsa be, amely az alkalmazás felhasználói számára az alkalmazás a tartalommal fog rendelkezni korlátozások. Ez a vezérlő segítségével szellemi tulajdon védelme az alkalmazásban.

    ![Vezérlő](media/service-template-apps-create/power-bi-create-control.png)

    >[!NOTE]
    >.Pbix formátumba exportálás mindig blokkolva van a felhasználók számára az alkalmazás telepítése.

    **Paraméterek**

    Ez a kategória segítségével kezelheti a paraméter viselkedés, adatforrásokhoz való kapcsolódáskor. Tudjon meg többet [létrehozása a lekérdezési paraméterek](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/).

    ![Paraméterek](media/service-template-apps-create/power-bi-create-parameters.png)
    - **Érték**: alapértelmezett paraméter értéke.
    - **Szükséges**: használja ezt a telepítőt adjon meg egy felhasználó-specifikus paraméter szükséges.
    - **Zárolási**: Zárolása megakadályozza, hogy a telepítő egy paraméter frissítése.
    - **Statikus**: Abban az esetben, ha az alkalmazás tartalmaz engedélyezése *csak* mintaadatokkal. Ha bejelöli **statikus**, a telepítővarázsló nem kér a felhasználóktól egy adatforráshoz csatlakozni.

    **Hozzáférés** a tesztelési fázisban döntse el, mely a szervezet más telepítheti és tesztelheti az alkalmazást. Ne aggódjon, mindig visszatérhet, és ezek a beállítások később módosíthatók (a beállítás nincs hatással a sablon elosztott alkalmazás hozzáférést).

2. Válassza az **Alkalmazás létrehozása** lehetőséget.

    Egy üzenet foga tájékoztatni a tesztalkalmazás elkészültéről, amely tartalmazni fog egy hivatkozást, amelyet lemásolhat és megoszthat az alkalmazástesztelőkkel.

    ![A tesztalkalmazás kész](media/service-template-apps-create/power-bi-template-app-test-ready.png)

    A soron következő kibocsátáskezelési folyamat első lépését is elvégezte.

## <a name="manage-the-template-app-release"></a>A sablonalkalmazás kiadásának kezelése

Mielőtt nyilvánosan kiadná ezt a sablonalkalmazást szeretne meggyőződni róla, hogy az készen áll a használatra. A Power BI létrehozta a kiadáskezelési panelt, ahol követheti és megfigyelheti a teljes alkalmazáskiadási folyamatot. A szakaszok közötti váltást is elindíthatja. A gyakori szakaszok az alábbiak:

- Tesztalkalmazás készítése: csak a szervezeti teszteléséhez.
- A vizsgálati csomag előléptetése üzem előtti szakaszba: a szervezeten kívüli teszteléséhez.
- Üzem előtti csomag előléptetése üzemi szakaszba: termékverzió.
- Az összes csomag törlése vagy újrakezdés az előző szakasztól.

Az URL-címe nem módosul, kiadási szakaszok közötti váltáskor. Előléptetés nem befolyásolja az URL-cím magát.

Vegyük a szakaszok keresztül:

1. A sablonalkalmazás munkaterületén válassza a **Kiadáskezelés** lehetőséget.

    ![A kiadáskezelés ikonja](media/service-template-apps-create/power-bi-release-management-icon.png)

2. Válassza az **Alkalmazás létrehozása** lehetőséget.

    Ha létrehozta a fenti **Tesztcélú sablonalkalmazás létrehozása** lépésben a tesztalkalmazást, akkor a **Tesztelés** mellett már látható egy sárga pont, és itt nem kell az **Alkalmazás létrehozása** lehetőséget választania. Ha kiválasztja, akkor visszatér a sablonalkalmazás létrehozási folyamatához.

3. Válassza a **Hivatkozás beolvasása** lehetőséget.

    ![Alkalmazás létrehozása, hivatkozás beolvasása](media/service-template-apps-create/power-bi-dev-template-create-app-get-link.png)

4. Ha tesztelni szeretné az alkalmazás telepítési folyamatát, másolja le az értesítési ablakban lévő hivatkozást, és illessze be egy új böngészőablakba.

    Innentől ugyanazt az eljárást fogja követni, mint amit az ügyfelei is követni fognak. Az ő verziójukat megtekintheti a [Sablonalkalmazások telepítése és terjesztése a szervezetnél](service-template-apps-install-distribute.md) szakaszban.

5. A párbeszédpanelen válassza a **Telepítés** lehetőséget.

    Ha a telepítés sikeres, megjelenik egy értesítés, hogy az új alkalmazás készen áll a használatra.

6. Válassza az **Ugrás az alkalmazásra** lehetőséget.
7. **Az új alkalmazás használatának első lépései** szakaszban ugyanúgy fogja látni az alkalmazását, ahogyan az az ügyfelei számára is meg fog jelenni.

    ![Az alkalmazás használatának első lépései](media/service-template-apps-create/power-bi-template-app-get-started.png)
8. Válassza **Az alkalmazás felfedezése** lehetőséget a tesztalkalmazás mintaadatokkal történő ellenőrzéséhez.
9. Ha valamilyen módosítást szeretne végezni, térjen vissza az alkalmazáshoz az eredeti munkaterületen. Frissítse a tesztalkalmazást, amíg elégedett nem lesz az eredménnyel.
10. Ha készen áll az éles üzem előtti további tesztelésre a bérlőn kívüli alkalmazás előléptetni, lépjen vissza a **Kiadáskezelés** ablaktáblán, és válassza ki **előléptetés alkalmazás**. 

    ![Alkalmazás előléptetése üzem előtti állapotba](media/service-template-apps-create/power-bi-template-app-promote.png)

    >[!NOTE]
    > Ha az alkalmazás hitelesítenie kelljen magát válik nyilvánosan elérhető, a szervezeten kívül.

11. A választás megerősítéséhez válassza az **Előléptetés** lehetőséget.
12. Másolja le ezt az új URL-címet, hogy megoszthassa a bérlőn kívül a teszteléshez. Ez a hivatkozás is, kezdje meg az alkalmazás az appsource-on terjesztése létrehozásával terjeszt egy olyan [Cloud Partner portálra az új ajánlat](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-publish-offer). Küldje el a Cloud Partner portálra mutató csak az üzem előtti. Csak azután az alkalmazás jóvá van hagyva, és az appsource-ban közzétett értesítést kap, majd előléptetheti ezt a csomagot az éles környezetben, a Power bi-ban.
13. Ha az alkalmazás készen áll az üzemi használatra vagy az AppSource-on keresztüli megosztásra, térjen vissza a **Kiadáskezelés** panelre, és válassza az **Alkalmazás előléptetése** lehetőséget az **Üzem előtti** elem mellett.
14. A választás megerősítéséhez válassza az **Előléptetés** lehetőséget.

    Az alkalmazás most már üzemi környezetben van, és készen áll a terjesztésre.

    ![Alkalmazás üzemi környezetben](media/service-template-apps-create/power-bi-template-app-production.png)

Az alkalmazás világszerte több ezer Power BI-felhasználó számára történő elérhetővé tételéhez javasoljuk, hogy töltse fel az AppSource-ba. Részletekért tekintse át [A Power BI-alkalmazásra vonatkozó ajánlat](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer) weblapot.

## <a name="update-your-app"></a>Alkalmazás frissítése

Most, hogy az alkalmazása üzemi környezetbe került, újrakezdheti a tesztelési fázist anélkül, hogy az üzemi környezetben lévő alkalmazás működését megzavarná.

1. A **Kiadáskezelés** panelen válassza az **Alkalmazás létrehozása** lehetőséget.
2. Menjen végig ismét az alkalmazás-létrehozási folyamaton.
3. Miután megadta a **Védjegyezés**, a **Tartalom**, a **Vezérlő** és a **Hozzáférés** beállításait, válassza ismét az **Alkalmazás létrehozása** lehetőséget.
4. Válassza a **Bezárás** lehetőséget, és térjen vissza **Kiadáskezelés** panelre.

   Láthatja, hogy most már két verzióval rendelkezik: Egy verzióval üzemi környezetben, valamint egy új tesztelési verzióval.

    ![A sablonalkalmazás két verziója](media/service-template-apps-create/power-bi-template-app-2-versions.png)

5. Ha készen áll az éles üzem előtti további tesztelésre a bérlőn kívüli alkalmazás előléptetni, lépjen vissza a Kiadáskezelés panelen, és válassza ki **előléptetés alkalmazás** melletti **tesztelés**.
6. A hivatkozás már élő, küldheti el újra a Cloud Partner portálra a következő lépéseket követve [ajánlat frissítése a Power BI alkalmazás](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-update-existing-offer).

>[!NOTE]
>Léptesse elő az alkalmazás éles szakaszba, csak akkor, ha az alkalmazást jóváhagyta Cloud Partner portálra, és közzétette azt.

## <a name="next-steps"></a>Következő lépések

Arról, hogyan használják a sablonalkalmazást az ügyfelek a [Sablonalkalmazások telepítése, testreszabása és terjesztése a szervezetnél](service-template-apps-install-distribute.md) szakaszban olvashat.

Az alkalmazás terjesztését részletesen [A Power BI-alkalmazásra vonatkozó ajánlat](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer) weblapon ismerheti meg.
