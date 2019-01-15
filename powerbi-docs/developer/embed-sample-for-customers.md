---
title: Beágyazott analitika Power BI-tartalom alkalmazásba való beágyazásához ügyfelei számára
description: Útmutató jelentés, irányítópult vagy csempe alkalmazásba való integrálásához vagy beágyazásához az ügyfelek számára, a beágyazott analitikákhoz készült Power BI API-k használatával. Útmutató a Power BI alkalmazásba való integrálásához beágyazott analitikai szoftver, beágyazott analitikai eszközök vagy beágyazott üzletiintelligencia-eszközök használatával.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.topic: tutorial
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: seodec18
ms.date: 12/10/2018
ms.openlocfilehash: c662fea5bb343d835cffec126ffe6eb071be2218
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54296639"
---
# <a name="tutorial-embed-a-power-bi-report-dashboard-or-tile-into-an-application-for-your-customers"></a>Oktatóanyag: Power BI-jelentés, -irányítópult vagy -csempe beágyazása egy alkalmazásba a saját ügyfelek részére

Az **Azure-beli Power BI Embedded** segítségével jelentéseket, irányítópultokat és csempéket ágyazhat be alkalmazásokba az alkalmazás tulajdonában lévő adatokkal. **Az alkalmazás tulajdonában lévő adatok** esetében egy alkalmazás a Power BI-t használja beágyazott elemzőplatformként. **ISV-fejlesztőként** létrehozhat olyan Power BI-tartalmakat, amelyek jelentéseket, irányítópultokat vagy csempéket jelenítenek meg egy teljes mértékben integrált és interaktív alkalmazásban anélkül, hogy a felhasználóknak Power BI-licenccel kellene rendelkeznie. Ez az oktatóanyag bemutatja, hogyan integrálhat jelentést ügyfelei által használt alkalmazásokba a Power BI .NET SDK és a Power BI JavaScript API segítségével, az **Azure-beli Power BI Embedded** használatával.

Az oktatóanyag a következőket ismerteti:
> [!div class="checklist"]
> * Alkalmazás regisztrálása az Azure-ban.
> * Ágyazzon be egy Power BI-jelentést egy alkalmazásba.

## <a name="prerequisites"></a>Előfeltételek

A kezdéshez szüksége van egy **Power BI Pro**-fiókra, amely a **fő fiókként** szolgál, és egy **Microsoft Azure**-előfizetésre.

* Ha még nem regisztrált a **Power BI Pro** szolgáltatásra, a kezdés előtt [hozzon létre egy ingyenes próbaverziós fiókot](https://powerbi.microsoft.com/en-us/pricing/).
* Ha még nincs Azure-előfizetése, kezdés előtt hozzon létre egy [ingyenes fiókot](https://azure.microsoft.com/free/?WT.mc_id=A261C142F).
* Állítson be egy saját [Azure Active Directory-bérlőt](create-an-azure-active-directory-tenant.md).
* Telepítse a [Visual Studio](https://www.visualstudio.com/) 2013-as vagy későbbi verzióját.

## <a name="set-up-your-embedded-analytics-development-environment"></a>A beágyazott elemzési fejlesztési környezet beállítása

Mielőtt jelentéseket, irányítópultokat vagy csempéket ágyazna az alkalmazásba, győződjön meg arról, hogy a környezete engedélyezi a beágyazást a Power BI-jal.

Az első lépések gyors elsajátítása érdekében követheti a [beágyazáshoz szükséges telepítési eszköz](https://aka.ms/embedsetup/AppOwnsData) lépéseit, és letölthet egy mintaalkalmazást, amely végigvezeti Önt a környezet létrehozásán és egy jelentés beágyazásán.

Ha mégis a környezet manuális létrehozása mellett dönt, folytathatja az alábbiak szerint.

### <a name="register-an-application-in-azure-active-directory-azure-ad"></a>Alkalmazás regisztrálása az Azure Active Directoryban (Azure AD)

Az alkalmazás Azure Active Directoryban történő regisztrálása lehetővé teszi az alkalmazás számára a Power BI REST API-k elérését. Az alkalmazás regisztrálásával identitást hozhat létre a számára, és meghatározhatja a Power BI REST-erőforrásokhoz kötődő engedélyeket.

1. Fogadja el a [Microsoft Power BI API használati feltételeit](https://powerbi.microsoft.com/api-terms).

2. Jelentkezzen be az [Azure Portalon](https://portal.azure.com).

    ![Az Azure Portal főoldala](media/embed-sample-for-customers/embed-sample-for-customers-002.png)

3. A bal oldali navigációs panelen válassza a **Minden szolgáltatás** lehetőséget, és kattintson az **Alkalmazásregisztrációk**, majd az **Új alkalmazás regisztrálása** elemre.

    ![Alkalmazásregisztráció keresése](media/embed-sample-for-customers/embed-sample-for-customers-003.png)</br>
    ![Új alkalmazás regisztrálása](media/embed-sample-for-customers/embed-sample-for-customers-004.png)

4. Kövesse az utasításokat az új alkalmazás létrehozásához. Az alkalmazáshoz tartozó adatok esetében a **Natív** alkalmazástípust kell használnia. Adja meg azt az **Átirányítási URI-t**, amelyet az **Azure AD** a jogkivonatválaszok visszaadására használ. Adjon meg egy alkalmazáshoz tartozó értéket (például: `http://localhost:13526/Redirect`).

    ![Alkalmazás létrehozása](media/embed-sample-for-customers/embed-sample-for-customers-005.png)

### <a name="apply-permissions-to-your-application-within-azure-active-directory"></a>Engedélyek alkalmazása a saját alkalmazásra az Azure AD-ben

Az alkalmazásregisztrációs oldalon megadottak mellett további engedélyeket adhat meg az alkalmazásnak. Jelentkezzen be a beágyazáshoz használt *fő* fiókkal. A fő fióknak globális rendszergazdai fióknak kell lennie.

### <a name="use-the-azure-active-directory-portal"></a>Az Azure Active Directory portál használata

1. Az Azure Portal [Alkalmazásregisztrációk](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ApplicationsListBlade) szakaszában keresse meg azt az alkalmazást, amelyet a beágyazáshoz kíván használni.

    ![Az alkalmazás kiválasztása](media/embed-sample-for-customers/embed-sample-for-customers-006.png)

2. Kattintson a **Beállítások** elemre, majd az **API-hozzáférés** területen válassza az **Szükséges engedélyek** lehetőséget.

    ![Szükséges engedélyek](media/embed-sample-for-customers/embed-sample-for-customers-008.png)

3. Válassza a **Windows Azure Active Directory** elemet, majd győződjön meg arról, hogy a **Hozzáférés a címtárhoz a bejelentkezett felhasználóként** beállítás be van jelölve. Kattintson a **Mentés** gombra.

    ![Windows Azure AD-engedélyek](media/embed-sample-for-customers/embed-sample-for-customers-011.png)

4. Válassza a **Hozzáadás** elemet.

    ![Engedélyek hozzáadása](media/embed-sample-for-customers/embed-sample-for-customers-012.png)

5. Kattintson az **API kiválasztása** lehetőségre.

    ![API-hozzáférés hozzáadása](media/embed-sample-for-customers/embed-sample-for-customers-013.png)

6. Kattintson a **Power BI szolgáltatás**, majd a **Kiválasztás** lehetőségre.

    ![PBI szolgáltatás kiválasztása](media/embed-sample-for-customers/embed-sample-for-customers-014.png)

7. Jelölje be az összes engedélyt a **Delegált engedélyek** szakaszban. Ha végzett, kattintson a **Mentés** gombra.

    ![Delegált engedélyek kiválasztása](media/embed-sample-for-customers/embed-sample-for-customers-015.png)

8. A **Szükséges engedélyek** listában kattintson az **Engedélyek megadása** elemre.

    Az **Engedélyek megadása** műveletre azért van szükség, hogy a *fő fióknál* ne kelljen Azure AD-hozzájárulást kérni. Ha globális rendszergazdai fiókkal végzi el a műveletet, az összes vállalati felhasználó részére meg kell adnia az engedélyeket ehhez az alkalmazáshoz. Ha a *fő fiókkal*, és nem a globális rendszergazdai fiókkal hajtja végre a műveletet, csak a *fő fiók* számára kell megadnia az engedélyeket ehhez az alkalmazáshoz.

    ![Engedélyek megadása a Szükséges engedélyek párbeszédpanelen](media/embed-sample-for-customers/embed-sample-for-customers-016.png)

## <a name="set-up-your-power-bi-environment"></a>A Power BI-környezet beállítása

### <a name="create-an-app-workspace"></a>Alkalmazás-munkaterület létrehozása

Ha jelentéseket, irányítópultokat vagy csempéket ágyaz be az ügyfelek számára, akkor ezeket a tartalmakat egy alkalmazás-munkaterületre kell helyezni. A *fő* fióknak az alkalmazás-munkaterület rendszergazdai fiókjának kell lennie.

1. Kezdjük a munkaterület létrehozásával. Kattintson a **munkaterületek** > **Alkalmazás-munkaterületek létrehozása** lehetőségre. Az Alkalmazás munkaterületének létrehozása elemnél helyezze el azokat a tartalmakat, amelyekhez az alkalmazásnak hozzá kell férnie.

    ![Munkaterület létrehozása](media/embed-sample-for-customers/embed-sample-for-customers-020.png)

2. Nevezze el a munkaterületet. Ha a megfelelő **munkaterület-azonosító** nem használható, szerkesztéssel hozzon létre egy egyedi azonosítót.

    ![Munkaterület elnevezése](media/embed-sample-for-customers/embed-sample-for-customers-021.png)

3. Néhány beállítást meg kell adnia. Ha **nyilvánosra** állítja a munkaterületet, a szervezet bármely tagja megtekintheti annak tartalmát. Ha a **Privát** beállítást választja, a munkaterület tartalmát csak annak tagjai láthatják.

    ![Privát/Nyilvános](media/embed-sample-for-customers/embed-sample-for-customers-022.png)

    A Nyilvános/Privát beállítás a csoport létrehozását követően nem módosítható.

4. Azt is beállíthatja, hogy a tagok **szerkeszthetik-e** a tartalmakat vagy **csak megtekintési** jogosultságuk van.

    ![Tagok felvétele](media/embed-sample-for-customers/embed-sample-for-customers-023.png)

5. Vegye fel az adott személyek e-mail-címét, akiknek hozzáférést kíván adni a munkaterülethez, majd kattintson a **Hozzáadás** gombra. Csoportaliasokat nem adhat hozzá, csak egyéneket.

6. Döntse le, hogy az egyes személyek egyszerű tagok vagy adminisztrátorok legyenek-e. Az adminisztrátorok szerkeszthetik magát a munkaterületet is, és tagokat is felvehetnek. A tagok a munkaterület tartalmát szerkeszthetik, amennyiben nem csak megtekintési jogosultsággal rendelkeznek. Az alkalmazást az adminisztrátorok és a tagok egyaránt közzétehetik.

    Most megtekintheti az új munkaterületet. A Power BI létrehozza és megnyitja a munkaterületet. Ekkor megjelenik az olyan munkaterületek listájában, amelyeknek Ön a tagja. Mivel adminisztrátori jogosultsággal rendelkezik, a három pontra (...) kattintva visszaléphet, és szerkesztheti a munkaterületet, például új tagokat adhat hozzá vagy módosíthatja a tagok jogosultságait.

    ![Új munkaterület](media/embed-sample-for-customers/embed-sample-for-customers-025.png)

### <a name="create-and-publish-your-reports"></a>Saját jelentések létrehozása és közzététele

A Power BI Desktop segítségével létrehozhatja jelentéseit és adatkészleteit, majd közzéteheti ezeket a jelentéseket egy alkalmazás-munkaterületen. A jelentéseket közzétevő végfelhasználónak Power BI Pro-licencre van szüksége az alkalmazás-munkaterületen történő közzétételhez.

1. Töltse le a [Blog Demo](https://github.com/Microsoft/powerbi-desktop-samples) mintát a GitHubról.

    ![jelentésminta](media/embed-sample-for-customers/embed-sample-for-customers-026-1.png)

2. PBIX-mintajelentés megnyitása a **Power BI Desktopban**

   ![PBI desktop jelentés](media/embed-sample-for-customers/embed-sample-for-customers-027.png)

3. Közzététel az **alkalmazás-munkaterületen**

   ![Desktop-jelentések közzététele](media/embed-sample-for-customers/embed-sample-for-customers-028.png)

    A jelentést mostantól online megtekintheti a Power BI szolgáltatásban.

   ![Jelentés nézet a PBI Desktopban](media/embed-sample-for-customers/embed-sample-for-customers-029.png)

## <a name="embed-your-content-using-the-sample-application"></a>Tartalom beágyazása a mintaalkalmazással

A mintaalkalmazás segítségével történő tartalombeágyazáshoz kövesse az alábbi lépéseket.

1. A kezdéshez töltse le az [App Owns Data mintát](https://github.com/Microsoft/PowerBI-Developer-Samples) a GitHubról.

    ![App Owns Data alkalmazásminta](media/embed-sample-for-customers/embed-sample-for-customers-026.png)

2. Nyissa meg a Web.config fájlt ugyanebben az alkalmazásban. Az alkalmazás sikeres futtatásához öt mezőt kell kitöltenie: az **applicationId** (ügyfél-azonosító), a **workspaceId** (munkaterület-azonosító), a **reportId** (jelentésazonosító), a **pbiUsername** (PBI-felhasználónév) és a **pbiPassword** (PBI-jelszó) mezőt.

    ![Web Config fájl](media/embed-sample-for-customers/embed-sample-for-customers-030.png)

    Az **applicationId** mezőbe írja be az **Azure**-beli **alkalmazásazonosítót**. Az alkalmazás az **applicationId**-vel azonosítja magát azon felhasználóknak, akiktől Ön engedélyeket kér. Az **applicationId** beszerzéséhez kövesse az alábbi lépéseket:

    Jelentkezzen be az [Azure Portalon](https://portal.azure.com).

    ![Az Azure Portal főoldala](media/embed-sample-for-customers/embed-sample-for-customers-002.png)

    A bal oldali navigációs panelen válassza a **Minden szolgáltatás**, majd az **Alkalmazásregisztrációk** elemet.

    ![Alkalmazásregisztráció keresése](media/embed-sample-for-customers/embed-sample-for-customers-003.png)

    Válassza ki azt az alkalmazást, amelynek az **applicationId**-jére szüksége van.

    ![Az alkalmazás kiválasztása](media/embed-sample-for-customers/embed-sample-for-customers-006.png)

    Megjelenik egy GUID-ként listázott **alkalmazásazonosító**. Használja ezt az **alkalmazásazonosítót** az alkalmazás **applicationId** mezőjében.

    ![applicationId](media/embed-sample-for-customers/embed-sample-for-customers-007.png)

    A **workspaceId** mezőbe írja be a Power BI-ban szereplő **alkalmazás-munkaterület GUID-azonosítóját**.

    ![workspaceId](media/embed-sample-for-customers/embed-sample-for-customers-031.png)

    A **jelentésazonosító** mezőbe írja be a Power BI-ban szereplő **jelentés GUID-azonosítóját**.

    ![jelentésazonosító](media/embed-sample-for-customers/embed-sample-for-customers-032.png)

    * A **pbiUsername** mezőbe írja be a főfelhasználói Power BI-fiókot.
    * A **pbiPassword** mezőbe írja be a főfelhasználói Power BI-fiók jelszavát.

3. Futtassa az alkalmazást!

    Először is kattintson a **Futtatás** elemre a **Visual Studióban**.

    ![Alkalmazás futtatása](media/embed-sample-for-customers/embed-sample-for-customers-033.png)

    Kattintson a **Jelentés beágyazása** lehetőségre. Válassza ki az alkalmazásban a jelentést, az irányítópultot vagy a csempét annak megfelelően, hogy melyiket szeretné kipróbálni.

    ![Tartalom kiválasztása](media/embed-sample-for-customers/embed-sample-for-customers-034.png)

    Most megtekintheti a jelentést a mintaalkalmazásban.

    ![Alkalmazás megtekintése](media/embed-sample-for-customers/embed-sample-for-customers-035.png)

## <a name="embed-your-content-within-your-application"></a>Tartalom beágyazása az alkalmazásba

Bár a tartalombeágyazás lépései elvégezhetők a [Power BI REST API-kkal](https://docs.microsoft.com/rest/api/power-bi/), a cikkben bemutatott mintakódok hajtanak a **.NET SDK-val** készültek.

Az ügyfelek számára történő beágyazáshoz a fő fióknak egy **hozzáférési jogkivonatra** van szüksége az **Azure AD-ből**. Mielőtt hívásokat intézhetne a [Power BI REST API-khoz](https://docs.microsoft.com/rest/api/power-bi/), be kell szereznie egy [Azure AD hozzáférési jogkivonatot](get-azuread-access-token.md#access-token-for-non-power-bi-users-app-owns-data) az **alkalmazás tulajdonában lévő adatokat** használó Power BI-alkalmazáshoz.

A Power BI-ügyfél **hozzáférési jogkivonattal** való létrehozásához célszerű létrehozni a Power BI-ügyfélobjektumot, amely lehetővé teszi a [Power BI REST API-k](https://docs.microsoft.com/rest/api/power-bi/) használatát. A Power BI-ügyfél létrehozásához az **AccessToken** hozzáférési jogkivonatot a ***Microsoft.Rest.TokenCredentials*** objektummal kell becsomagolni.

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.Rest;
using Microsoft.PowerBI.Api.V2;

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");

// Create a Power BI Client object. it's used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Your code to embed items.
}
```

### <a name="get-the-content-item-you-want-to-embed"></a>A beágyazni kívánt tartalomelem lekérése

A Power BI-ügyfélobjektummal lekérheti a beágyazni kívánt elem hivatkozását.

Itt láthat arra mintakódot, hogyan kérhető le az első jelentés egy adott munkaterületről.

*A tartalomelemek (beágyazni kívánt jelentések, irányítópultok vagy csempék) lekéréséről példát a [mintaalkalmazás](#embed-your-content-within-a-sample-application) Controllers\HomeController.cs fájljában találhat.*

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// You need to provide the workspaceId where the dashboard resides.
ODataResponseListReport reports = await client.Reports.GetReportsInGroupAsync(workspaceId);

// Get the first report in the group.
Report report = reports.Value.FirstOrDefault();
```

### <a name="create-the-embed-token"></a>A beágyazási token létrehozása

Generált egy beágyazási tokent, amely a JavaScript API-ból használható. A beágyazási token a beágyazott elemre vonatkozik. Ez azt jelenti, hogy amikor Power BI-tartalmat ágyaz be, mindig létre kell hoznia egy új beágyazási tokent. További információt (beleértve a használandó **hozzáférési szintet**) a [GenerateToken API-ban](https://msdn.microsoft.com/library/mt784614.aspx) talál.

Íme egy példa egy jelentéshez készült beágyazási token az alkalmazáshoz való hozzáadásáról.

*A jelentések, irányítópultok vagy csempék beágyazási tokenjeinek létrehozásáról példát a [mintaalkalmazás](#embed-your-content-within-a-sample-application) Controllers\HomeController.cs fájljában találhat.*

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Generate Embed Token.
var generateTokenRequestParameters = new GenerateTokenRequest(accessLevel: "view");
EmbedToken tokenResponse = client.Reports.GenerateTokenInGroup(workspaceId, report.Id, generateTokenRequestParameters);

// Generate Embed Configuration.
var embedConfig = new EmbedConfig()
{
    EmbedToken = tokenResponse,
    EmbedUrl = report.EmbedUrl,
    Id = report.Id
};
```

Létrejött egy osztály az **EmbedConfig** és a **TileEmbedConfig** elemekhez. Minta a **Models\EmbedConfig.cs** és a **Models\TileEmbedConfig.cs** fájlban érhető el.

### <a name="load-an-item-using-javascript"></a>Elem betöltése a JavaScript használatával

A JavaScript használatával egy jelentést tölthet be a div elembe a weblapon.

A JavaScript API teljes körű mintáját a [Playground eszköz](https://microsoft.github.io/PowerBI-JavaScript/demo) segítségével használhatja. Ez a demókörnyezeti eszköz lehetőséget ad a Power BI Embedded különböző mintáinak gyors kipróbálására. A JavaScript API-ról a [PowerBI-JavaScript wiki](https://github.com/Microsoft/powerbi-javascript/wiki) oldalon talál további információkat.

Íme egy minta, amely az **EmbedConfig** és a **TileEmbedConfig** modellt használja egy jelentés nézeteivel együtt.

*A nézetek jelentésekhez, irányítópultokhoz vagy csempékhez való hozzáadásáról példát a [mintaalkalmazás](#embed-your-content-within-a-sample-application) Views\Home\EmbedReport.cshtml, Views\Home\EmbedDashboard.cshtml és Views\Home\Embedtile.cshtml fájljaiban találhat.*

```javascript
<script src="~/scripts/powerbi.js"></script>
<div id="reportContainer"></div>
<script>
    // Read embed application token from Model
    var accessToken = "@Model.EmbedToken.Token";

    // Read embed URL from Model
    var embedUrl = "@Html.Raw(Model.EmbedUrl)";

    // Read report Id from Model
    var embedReportId = "@Model.Id";

    // Get models. models contains enums that can be used.
    var models = window['powerbi-client'].models;

    // Embed configuration used to describe the what and how to embed.
    // This object is used when calling powerbi.embed.
    // This also includes settings and options such as filters.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'report',
        tokenType: models.TokenType.Embed,
        accessToken: accessToken,
        embedUrl: embedUrl,
        id: embedReportId,
        permissions: models.Permissions.All,
        settings: {
            filterPaneEnabled: true,
            navContentPaneEnabled: true
        }
    };

    // Get a reference to the embedded report HTML element
    var reportContainer = $('#reportContainer')[0];

    // Embed the report and display it within the div container.
    var report = powerbi.embed(reportContainer, config);
</script>
```

## <a name="move-to-production"></a>Átállás éles üzemre

Most, hogy elkészült az alkalmazás fejlesztésével, ideje dedikált kapacitással ellátni az alkalmazás-munkaterületet. Az éles üzemre való átálláshoz ez kötelező lépés.

### <a name="create-a-dedicated-capacity"></a>Dedikált kapacitás létrehozása

Dedikált kapacitás létrehozásával dedikált erőforrást rendelhet egy ügyfélhez. Dedikált kapacitást a [Microsoft Azure Portalon](https://portal.azure.com) vásárolhat. A Power BI Embedded-kapacitások létrehozásával kapcsolatos részletekért tekintse meg a [Power BI Embedded-kapacitás az Azure Portalon való létrehozásával](azure-pbie-create-capacity.md) kapcsolatos cikket.

Az alábbi táblázatból megtudhatja, milyen kapacitású Power BI Embedded-kapacitás felel meg a leginkább az igényeinek.

| Kapacitáscsomópont | Magok száma összesen<br/>*(Háttérrendszer + előtérrendszer)* | Háttérrendszerbeli magok | Előtérrendszerbeli magok | DirectQuery-/élő kapcsolat korlátai|
| --- | --- | --- | --- | --- | --- |
| A1 |1 virtuális mag |0,5 mag, 3 GB RAM |0,5 mag |Másodpercenként 5 |
| A2 |2 virtuális mag |1 mag, 5 GB RAM |1 mag | Másodpercenként 10 |
| A3 |42 virtuális mag |2 mag, 10 GB RAM |2 mag | Másodpercenként 15 |
| A4 |8 virtuális mag |4 mag, 25 GB RAM |4 mag |Másodpercenként 30 |
| A5 |16 virtuális mag |8 mag, 50 GB RAM |8 mag |Másodpercenként 60 |
| A6 |32 virtuális mag |16 mag, 100 GB RAM |16 mag |Másodpercenként 120 |

**_A termékváltozatokkal nem férhet hozzá a Power BI-tartalmakhoz INGYENES Power BI-licenccel._**

A PRO licenccel a beágyazási tokenek elsődlegesen fejlesztési tesztelésre használhatók, a Power BI fő fiókja csak korlátozott mennyiségű tokent tud előállítani. Éles környezetben használt beágyazásokhoz dedikált kapacitás szükséges. Dedikált kapacitásokkal nincs korlátja a beágyazási tokenek előállításának. Az [Elérhető szolgáltatások](https://docs.microsoft.com/rest/api/power-bi/availablefeatures/getavailablefeatures) oldalon ellenőrizheti a használati értéket, amely százalékosan jelzi az aktuális beágyazott használatot. A használati mennyiséget fő fiókonként számoljuk.

További információ: [Tanulmány a beágyazott analitikai kapacitás tervezéséről](https://aka.ms/pbiewhitepaper).

### <a name="assign-an-app-workspace-to-a-dedicated-capacity"></a>Alkalmazás-munkaterület hozzárendelése dedikált kapacitáshoz

A dedikált kapacitás létrehozása után hozzárendelheti az alkalmazás-munkaterületet ehhez a kapacitáshoz. Dedikált kapacitást a következő lépésekkel rendelhet hozzá munkaterülethez.

1. A **Power BI szolgáltatásban** bontsa ki a munkaterületeket, és kattintson a három pont elemre azon munkaterület mellett, amelyiket tartalombeágyazáshoz használ. Válassza a **Munkaterületek szerkesztése** lehetőséget.

    ![Munkaterület szerkesztése](media/embed-sample-for-customers/embed-sample-for-customers-036.png)

2. Bontsa ki a **Speciális** elemet, engedélyezze a **Dedikált kapacitást**, majd kattintson a létrehozott dedikált kapacitásra. Kattintson a **Mentés** gombra.

    ![Dedikált kapacitás hozzárendelése](media/embed-sample-for-customers/embed-sample-for-customers-024.png)

3. A **Mentés** kiválasztása után meg kell jelennie egy **gyémántnak** az alkalmazás-munkaterület neve mellett.

    ![egy kapacitáshoz hozzárendelt alkalmazás-munkaterület](media/embed-sample-for-customers/embed-sample-for-customers-037.png)

## <a name="next-steps"></a>Következő lépések

Ebben az oktatóanyagban bemutattuk, hogyan lehet Power BI-tartalmat beágyazni az ügyfelek alkalmazásaiba. Megpróbálkozhat Power BI-tartalom beágyazásával a szervezete számára is.

> [!div class="nextstepaction"]
>[Beágyazás a cég számára](embed-sample-for-your-organization.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
