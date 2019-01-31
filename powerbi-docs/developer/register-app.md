---
title: Alkalmazás regisztrálása Power BI-tartalmak beágyazásához
description: Megismerheti, hogyan kell regisztrálni egy alkalmazást az Azure Active Directoryban Power BI-tartalmak beágyazásához.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 11/26/2018
ms.openlocfilehash: c05dddbddc2dd19fed1bfbec25bcd9e378df543f
ms.sourcegitcommit: a36f82224e68fdd3489944c9c3c03a93e4068cc5
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/31/2019
ms.locfileid: "55430153"
---
# <a name="register-an-azure-ad-app-to-embed-power-bi-content"></a>Azure AD-alkalmazás regisztrálása Power BI-tartalmak beágyazásához

Megismerheti, hogyan kell regisztrálni egy alkalmazást az Azure Active Directoryban (Azure AD) Power BI-tartalmak beágyazásához.

Az alkalmazás az Azure AD-vel regisztrálva hozzáférést biztosít az alkalmazásnak a Power BI REST API-khoz. Az alkalmazás regisztrálása után identitást hozhat létre a számára, és meghatározhatja a Power BI REST-erőforrásokhoz kötődő engedélyeket.

> [!IMPORTANT]
> A Power BI alkalmazás regisztrálása előtt szüksége van egy [Azure Active Directory-bérlőre és egy céges felhasználóra](create-an-azure-active-directory-tenant.md). Amennyiben nem a bérlő egyik felhasználójával regisztrál a Power BI-ba, nem tudja regisztrálni az alkalmazást.

Az alkalmazást két módon regisztrálhatja. Az első lehetőség a [Power BI alkalmazásregisztráló eszköz](https://dev.powerbi.com/apps/), a másik pedig az Azure Portal használata. A Power BI alkalmazásregisztráló eszköz kínálja az egyszerűbb megoldást, mivel csak néhány mezőt kell kitöltenie. Amennyiben módosítani kívánja az alkalmazását, az Azure Portal használatát javasoljuk.

## <a name="register-with-the-power-bi-app-registration-tool"></a>Regisztráció a Power BI alkalmazásregisztráló eszközzel

Regisztrálja az alkalmazást az **Azure Active Directoryban**, hogy létrehozzon egy identitást az alkalmazása számára, és engedélyezze egyes Power BI REST-erőforrások használatát. Egy alkalmazás, például konzolalkalmazás vagy webhely regisztrációja során egy azonosítót kap, amelyet az alkalmazás a saját azonosítására használ azon felhasználóknál, akiktől engedélyeket kell kérnie.

Az alábbiak szerint regisztrálhatja alkalmazását a Power BI alkalmazásregisztráló eszközzel:

1. Keresse fel a [dev.powerbi.com/apps](https://dev.powerbi.com/apps) címet.
2. Válassza a **Bejelentkezés meglévő fiókkal** lehetőséget.
3. Adja meg az **Alkalmazás nevét**.
4. Az Alkalmazás típusának listájáról válassza ki a használt alkalmazás típusát.

   * Az ügyféleszközökön futó alkalmazások esetében a **Natív alkalmazás** lehetőséget kell választania. Válassza a **Natív alkalmazás** lehetőséget, ha bármilyen tartalmat ágyaz be az ügyfelei számára, függetlenül attól, hogy milyen alkalmazásról van szó, még webalkalmazások esetében is.
   * Webalkalmazások és webes API-k esetében válassza a **Kiszolgálóoldali webalkalmazás** lehetőséget.

5. Írjon be egy értéket az **Átirányítási URL-cím** és a **Kezdőlap URL-címe** mezőbe. A **Átirányítási URL-cím** bármilyen érvényes URL-címmel működik.

    A **Kezdőlap URL-címe** csak akkor adható meg, ha a **Kiszolgálóoldali webalkalmazás** alkalmazástípust választja.

    A *beágyazás ügyfelek számára* és az *irányítópulti webes alkalmazás integrálása* minták esetében az **átirányítási URL-cím** a következő: `http://localhost:13526/Redirect`. A jelentés- és csempeminták **átirányítási URL-címe**: `http://localhost:13526/`.
6. Válassza ki a hozzáféréssel rendelkező alkalmazáshoz az API-kat. További információt a Power BI hozzáférési engedélyeiről a [Power BI engedélyeit](power-bi-permissions.md) ismertető témakörben talál.

    ![Alkalmazásregisztrációs API-k](media/register-app/app-registration-apis.png)
7. Válassza az **Alkalmazás regisztrálása** lehetőséget.

    Ekkor kap egy **ügyfél-azonosítót**, és ha a **Kiszolgálóoldali webalkalmazás** lehetőséget választja, megkapja a **titkos ügyfélkulcsot**. Az **ügyfél-azonosítót** később is lekérdezheti az Azure Portalról. Amennyiben elveszíti **titkos ügyfélkulcsát**, egy újat kell létrehoznia az Azure Portalon.

8. Nyissa meg az Azure-t, és válassza az **Engedélyek megadása** lehetőséget.

   > [!Note]
   > A bérlő felhasználóinak az **_Engedélyek megadása_** lehetőség elérésére van szükségük a lépés elvégzéséhez.

* Nyissa meg az Azure-t.
* Keresse meg és válassza az **Alkalmazásregisztrációk** lehetőséget.
* Válassza ki az alkalmazást.
* Kattintson a **Beállítások** elemre.
* Kattintson a **Szükséges engedélyek** lehetőségre.
* Az alkalmazásregisztrációs webhelyen kiválasztott engedélyek ellenőrzéséhez válassza a **Power BI szolgáltatást**.
* Válassza az **Engedélyek megadása** lehetőséget.

Ezután a regisztrált alkalmazást saját egyéni alkalmazása részeként használhatja a Power BI szolgáltatásban.

> [!IMPORTANT]
> Amennyiben ügyfelei számára ágyaz be tartalmat, további engedélyeket kell beállítania az Azure Portalon. A további tudnivalókért lásd az [engedélyek a saját alkalmazásra történő alkalmazását](#apply-permissions-to-your-application) ismertető témakört.

## <a name="register-with-the-azure-portal"></a>Regisztráció az Azure Portalon

Az alkalmazást közvetlenül az Azure Portalon is regisztrálhatja. Az alkalmazás regisztrálása a következő módon történik.

1. Fogadja el a [Microsoft Power BI API használati feltételeit](https://powerbi.microsoft.com/api-terms).
2. Jelentkezzen be az [Azure Portalon](https://portal.azure.com).
3. Az oldal jobb felső részén kattintson a fiókra, és válassza ki az Azure AD-bérlőt.
4. A bal oldali navigációs ablaktáblán válassza a **További szolgáltatások** lehetőséget, a **Biztonság és identitás** menü **Alkalmazásregisztrációk** elemét, majd az **Új alkalmazás regisztrálása** elemet.

    ![Új alkalmazás regisztrálása](media/register-app/azuread-new-app-registration.png)
5. Kövesse az utasításokat az új alkalmazás létrehozásához.

   * Webalkalmazások esetén adja meg a Bejelentkezési URL-címet, vagyis az alkalmazás alap URL-címét, amelyen a felhasználók bejelentkezhetnek (például: `http://localhost:13526`).
   * Natív alkalmazások esetén adja meg az **Átirányítási URI-t**, amelyet az Azure AD a jogkivonatválaszok visszaadására használ. Ügyeljen rá, hogy az alkalmazáshoz tartozó értéket adjon meg, például: `http://myapplication/Redirect`.

További információt az alkalmazások Azure Active Directoryban történő regisztrálásáról az [alkalmazások Azure Active Directoryval való integrálását](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) ismertető témakörben talál.

## <a name="how-to-get-the-client-id"></a>Ügyfél-azonosító beszerzése

Az alkalmazás regisztrálásakor kap egy **ügyfél-azonosítót**.  Az **ügyfél-azonosító** engedélyeket kér a felhasználóknak az alkalmazáshoz, hogy azonosítsák magukat.

Az alábbiak szerint szerezheti be az ügyfél-azonosítót:

1. Jelentkezzen be az [Azure Portalon](https://portal.azure.com).
2. Az oldal jobb felső részén kattintson a fiókra, és válassza ki az Azure AD-bérlőt.
3. A bal oldali navigációs ablaktáblán válassza a **További szolgáltatások**, majd az **Alkalmazásregisztrációk** elemet.
4. Válassza ki azt az alkalmazást, amelynek ügyfél-azonosítóját be kívánja szerezni.
5. Az **alkalmazásazonosító** GUID-ként jelenik meg a listában. Ez az alkalmazás ügyfél-azonosítója.

    ![Az ügyfél-azonosító alkalmazásazonosítóként jelenik meg az alkalmazásregisztrációban.](media/register-app/powerbi-embedded-app-registration-client-id.png)

## <a name="apply-permissions-to-your-application-within-azure-ad"></a>Engedélyek alkalmazása a saját alkalmazásra az Azure AD-ben

> [!IMPORTANT]
> Ez a szakasz kizárólag azokra az alkalmazásokra vonatkozik, amelyekkel **saját cége számára végez tartalombeágyazást**.

Adjon további engedélyeket az alkalmazásnak azokon felül, amelyeket az alkalmazásregisztrációs oldalon megadott. Ezeket megadhatja az Azure AD portálon keresztül, vagy szoftveres úton.

Vagy a beágyazáshoz használt *fő* fiókkal, vagy egy globális rendszergazdai fiókkal kell bejelentkeznie.

### <a name="using-the-azure-ad-portal"></a>Az Azure AD Portal használata

1. Az Azure Portal [Alkalmazásregisztrációk](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ApplicationsListBlade) szakaszában keresse meg azt az alkalmazást, amelyet a beágyazáshoz kíván használni.

    ![Az Azure AD-ban regisztrált alkalmazások](media/register-app/powerbi-embedded-azuread-registered-apps.png)
2. Válassza az **API-hozzáférés**, majd a **Szükséges engedélyek** lehetőséget.

    ![Az Azure AD-alkalmazás számára szükséges engedélyek](media/register-app/powerbi-embedded-azuread-app-required-permissions.png)

3. A **Szükséges engedélyek** listán válassza ki a **Power BI szolgáltatás (Power BI)** elemet.

    ![Alkalmazásengedélyek (03)](media/register-app/powerbi-embedded-azuread-app-permissions03.png)

   > [!NOTE]
   > Amennyiben az alkalmazást közvetlenül az Azure AD portálon hozta létre, előfordulhat, hogy a **Power BI szolgáltatás (Power BI)** nem jelenik meg. Ebben az esetben kattintson a **+ Hozzáadás** gombra, és válassza az **1 Kiválasztás és API** lehetőséget. Válassza a **Power BI szolgáltatás** elemet az API-k listájából, és kattintson a **Kiválasztás** gombra.  Amennyiben a **Power BI szolgáltatás (Power BI)** nem érhető el a **+ Hozzáadás** listából sem, regisztráljon a Power BI szolgáltatásra legalább egy felhasználóval.

4. Jelölje be az összes engedélyt a **Delegált engedélyek** szakaszban. Egyenként jelölje be őket, hogy menteni tudja a kijelöléseket. Ha végzett, kattintson a **Mentés** gombra.

    ![Alkalmazásengedélyek (04)](media/register-app/powerbi-embedded-azuread-app-permissions04.png)
5. A **Szükséges engedélyek** listában kattintson az **Engedélyek megadása** elemre.

    Az **Engedélyek megadása** műveletre azért van szükség, hogy a *fő fióknál* ne kelljen Azure AD-hozzájárulást kérni. Amennyiben globális rendszergazdai fiókkal végzi el a műveletet, a cég összes felhasználója megkapja az engedélyeket ehhez az alkalmazáshoz. Amennyiben a *fő fiókkal*, és nem a globális rendszergazdai fiókkal hajtja végre a műveletet, csak a *fő fiók* számára adja meg az engedélyeket ehhez az alkalmazáshoz.

    ![Engedélyek megadása a Szükséges engedélyek párbeszédpanelen](media/register-app/powerbi-embedded-azuread-app-grant-permissions.png)

### <a name="applying-permissions-programmatically"></a>Engedélyek szoftveres alkalmazása

1. Be kell szereznie a bérlőn belül meglévő egyszerű szolgáltatásneveket (felhasználókat). További információt ennek menetéről a [Get servicePrincipal](https://developer.microsoft.com/graph/docs/api-reference/beta/api/serviceprincipal_get) használatát ismertető témakörben talál.

    Ha azonosító megadása nélkül hívja meg a *Get servicePrincipal* API-t, a bérlőben megtalálható összes egyszerű szolgáltatást lekéri.
2. Az egyszerű szolgáltatások ellenőrzéséhez használja **appId** tulajdonságként az alkalmazás ügyfélazonosítóját.

3. Hozzon létre egy új szolgáltatáscsomagot, amennyiben az alkalmazása nem rendelkezik azzal.

    ```json
    Post https://graph.microsoft.com/beta/servicePrincipals
    Authorization: Bearer ey..qw
    Content-Type: application/json
    {
    "accountEnabled" : true,
    "appId" : "{App_Client_ID}",
    "displayName" : "{App_DisplayName}"
    }
    ```

4. Alkalmazásengedély megadása a PowerBI API számára

   Ha egy meglévő bérlőt használ, és nem kíván a bérlő összes felhasználója részére engedélyeket kiadni, megadhatja az engedélyeket egy konkrét felhasználónak is. Ehhez a **contentType** esetén a **Principal** értéket kell megadnia.

   A **consentType** értéke megadhatja az **AllPrincipals** vagy a **Principal** értéket.

   * Az **AllPrincipals** csak a bérlői rendszergazda által használható, hogy a bérlő minden felhasználója nevébe engedélyeket adjon.
   * A **Principal** értéket választva egy konkrét felhasználó nevében lehet engedélyt adni. Ebben az esetben egy további tulajdonságot hozzá kell adni a kérelem törzsében: *principalId={User_ObjectId}*.

     Az *Engedélyek megadása* műveletre azért van szükség, hogy a fő fióknál ne kelljen Azure AD-hozzájárulást kérni, hiszen az nem interaktív bejelentkezés esetén lehetetlen volna.

     ```json
     Post https://graph.microsoft.com/beta/OAuth2PermissionGrants
     Authorization: Bearer ey..qw
     Content-Type: application/json
     {
     "clientId":"{Service_Plan_ID}",
     "consentType":"AllPrincipals",
     "resourceId":"c78a3685-1ce7-52cd-95f7-dc5aea8ec98e",
     "scope":"Dataset.ReadWrite.All Dashboard.Read.All Report.Read.All Group.Read Group.Read.All Content.Create Metadata.View_Any Dataset.Read.All Data.Alter_Any",
     "expiryTime":"2018-03-29T14:35:32.4943409+03:00",
     "startTime":"2017-03-29T14:35:32.4933413+03:00"
     }
     ```

    A *c78a3685-1ce7-52cd-95f7-dc5aea8ec98e* **resourceId** nem univerzális, hanem a bérlőtől függ. Ez az érték az AAD-bérlőben található „Power BI szolgáltatás” alkalmazás objectId azonosítója.

    A felhasználó ezt az értéket gyorsan beszerezheti az Azure Portalon:
    1. https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/AllApps
    2. A keresőmezőbe írja be a „Power BI szolgáltatás” kifejezést

5. Alkalmazásengedélyek megadása az Microsoft Azure Active Directorynak (AAD-nek)

   A **consentType** értéke megadhatja az **AllPrincipals** vagy a **Principal** értéket.

   * Az **AllPrincipals** csak a bérlői rendszergazda által használható, hogy a bérlő minden felhasználója nevébe engedélyeket adjon.
   * A **Principal** értéket választva egy konkrét felhasználó nevében lehet engedélyt adni. Ebben az esetben egy további tulajdonságot hozzá kell adni a kérelem törzsében: *principalId={User_ObjectId}*.

   Az *Engedélyek megadása* műveletre azért van szükség, hogy a fő fióknál ne kelljen Azure AD-hozzájárulást kérni, hiszen az nem interaktív bejelentkezés esetén lehetetlen volna.

   ```json
   Post https://graph.microsoft.com/beta/OAuth2PermissionGrants
   Authorization: Bearer ey..qw
   Content-Type: application/json
   { 
   "clientId":"{Service_Plan_ID}",
   "consentType":"AllPrincipals",
   "resourceId":"61e57743-d5cf-41ba-bd1a-2b381390a3f1",
   "scope":"User.Read Directory.AccessAsUser.All",
   "expiryTime":"2018-03-29T14:35:32.4943409+03:00",
   "startTime":"2017-03-29T14:35:32.4933413+03:00"
   }
   ```

## <a name="next-steps"></a>Következő lépések

Most, hogy regisztrálta alkalmazását az Azure AD-ben, hitelesítenie kell a felhasználókat az alkalmazásban. Erről részletesebben a [felhasználók hitelesítését és a Power BI-alkalmazáshoz való Azure AD-hozzáférési token beszerzését](get-azuread-access-token.md) ismertető témakörben olvashat.

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
