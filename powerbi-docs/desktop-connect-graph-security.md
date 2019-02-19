---
title: Csatlakozás a Microsoft Graph Securityhez a Power BI Desktopban
description: Könnyű csatlakozás a Microsoft Graph Security API-hoz a Power BI Desktopban
author: preetikr
manager: kfile
ms.reviewer: ''
ms.custom: seojan19
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/29/2019
ms.author: preetikr
LocalizationGroup: Connect to data
ms.openlocfilehash: 2187a24820ef8ea3db9fdd1b7a881dc9cfb6393f
ms.sourcegitcommit: f07520591db6c3f27ab6490612cc56384abc6633
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56298891"
---
# <a name="connect-to-microsoft-graph-security-in-power-bi-desktop"></a>Csatlakozás a Microsoft Graph Securityhez a Power BI Desktopban

A Power BI Desktoppal és a Microsoft Graph Security Power BI-összekötőjével csatlakozhat a Microsoft Graph Security API-hoz. Ez lehetővé teszi, hogy irányítópultokat és jelentéseket hozzon létre, így biztonsági [riasztásokkal](https://docs.microsoft.com/graph/api/resources/alert?view=graph-rest-1.0) és [biztonsági pontszámokkal](https://docs.microsoft.com/graph/api/resources/securescores?view=graph-rest-beta) kapcsolatos elemzéseket végezhet. A [Microsoft Graph Security API](https://aka.ms/graphsecuritydocs) [több biztonsági megoldást](https://aka.ms/graphsecurityalerts) kapcsol össze a Microsofttól és az ökoszisztéma partnereitől, így megkönnyíti a riasztások egyeztetését, részletes környezeti információkat tesz elérhetővé, és leegyszerűsíti az automatizálást. A szervezetek így gyors elemzéseket végezhetnek, majd reagálhatnak ezekre a biztonsági termékeikben, mindeközben csökkentve a több integráció kiépítésével és karbantartásával járó költségeket és munkát.

## <a name="prerequisites-to-connect-with-the-microsoft-graph-security-connector"></a>A Microsoft Graph Security-összekötőhöz való csatlakozás előfeltételei

* A Microsoft Graph Security-összekötő használatához *explicit* Azure Active Directorybeli bérlői rendszergazdai hozzájárulás szükséges, amely a [Microsoft Graph Security hitelesítési követelményei](https://aka.ms/graphsecurityauth) közé is tartozik. A jóváhagyáshoz szükséges a Microsoft Graph Security Power BI-összekötő alkalmazás azonosítója és neve, amelyet az [Azure Portalon](https://portal.azure.com) is megtalálhat:

   | Tulajdonság | Érték |
   |----------|-------|
   | **Alkalmazás neve** | `MicrosoftGraphSecurityPowerBIConnector` |
   | **Alkalmazásazonosító** | `cab163b7-247d-4cb9-be32-39b6056d4189` |
   |||

   Az összekötő jóváhagyásához az Azure AD bérlői rendszergazdájának az alábbi lépések egyikét kell követnie:

   * [Adjon bérlői rendszergazdai jóváhagyást az Azure AD-alkalmazásokhoz](https://docs.microsoft.com/azure/active-directory/develop/v2-permissions-and-consent).

   * A logikai alkalmazás első futtatásakor az alkalmazás az [alkalmazás-jóváhagyási felületen](https://docs.microsoft.com/azure/active-directory/develop/application-consent-experience) kérhet jóváhagyást az Azure AD bérlői rendszergazdájától.
   
* A bejelentkezéshez és a Microsoft Graph Security Power BI-összekötőhöz való csatlakozáshoz használt felhasználói fióknak a Biztonsági olvasó korlátozott rendszergazdai szerepkör tagjának kell lennie az Azure AD-ben (Biztonsági olvasó vagy Biztonsági rendszergazda). Kövesse az [Azure AD-szerepkörök hozzárendelése a felhasználókhoz](https://docs.microsoft.com/graph/security-authorization#assign-azure-ad-roles-to-users) című szakasz lépéseit. 

## <a name="using-the-microsoft-graph-security-connector"></a>A Microsoft Graph Security-összekötő használata

A **Microsoft Graph Security**-összekötő használatához kövesse az alábbi lépéseket:

1. Válassza az **Adatok lekérése -> Továbbiak...** lehetőséget a Power BI Desktop **Kezdőlapján**.
2. A bal oldali kategóriák közül válassza az **Online szolgáltatások** lehetőséget.
3. Kattintson a **Microsoft Graph Security (Beta)** lehetőségre.

    ![Adatok beolvasása](media/desktop-connect-graph-security/GetData.PNG)
    
4. A megjelenő **Microsoft Graph Security** ablakban válassza ki a lekérdezni kívánt Microsoft Graph API-verziót. A következő lehetőségek közül választhat: v1.0 és béta.

    ![Verzió kiválasztása](media/desktop-connect-graph-security/selectVersion.PNG)
    
5. Amikor a rendszer kéri, jelentkezzen be az Azure Active Directory-fiókjába. A fióknak **Biztonsági olvasó** szerepkörrel kell rendelkeznie, ahogyan a fenti „Előfeltételek” szakaszban említettük.

    ![Bejelentkezés](media/desktop-connect-graph-security/SignIn.PNG)
    
6. Ha Ön a bérlői rendszergazda **és** még nem hagyta jóvá a Microsoft Graph Security Power BI-összekötőt (alkalmazást) az előfeltételeknek megfelelően, a következő párbeszédpanel fog megjelenni. Ügyeljen arra, hogy a „**Jóváhagyás a szervezet nevében**” lehetőséget válassza.

    ![Rendszergazdai jóváhagyás](media/desktop-connect-graph-security/AdminConsent.PNG)
    
7. A bejelentkezést követően ez az ablak jelenik meg, jelezve, hogy sikeres volt a hitelesítés. Kattintson a **Csatlakozás** gombra.

    ![Bejelentkezve](media/desktop-connect-graph-security/SignedIn.PNG)
    
8. A sikeres csatlakozás után egy **navigátor** ablak jelenik meg a lenti ábrához hasonlóan, amelyeken megtekintheti a korábbi lépésekben kiválasztott verzióhoz tartozó, a [Microsoft Graph Security API](https://aka.ms/graphsecuritydocs)-ban elérhető entitásokat (például a riasztásokat). Válasszon ki egy vagy több importálni és a **Power BI Desktopban** használni kívánt entitást. A 10. lépésben látható eredményhez kattintson a **Betöltés** lehetőségre.

   ![Navigációs tábla](media/desktop-connect-graph-security/NavTable.PNG)
    
9. Ha speciális lekérdezést szeretne intézni a Microsoft Graph Security API-ban, válassza az **Egyéni Microsoft Graph Security URL-cím megadása az eredmények szűréséhez** függvényt. Ezzel egy [OData.Feed](https://docs.microsoft.com/power-bi/desktop-connect-odata) típusú lekérdezést hozhat létre a Microsoft Graph Security API-ban, a hozzáféréshez szükséges engedélyekkel.

   > [!NOTE]
   > Az alábbi példában használt ServiceUri: `https://graph.microsoft.com/v1.0/security/alerts?$filter=Severity eq 'High'`. Ha az eredmények szűréséhez vagy a legutóbbi eredmények lekéréséhez szeretne lekérdezéseket készíteni, tekintse meg a [Graph által támogatott ODATA lekérdezésparamétereket](https://docs.microsoft.com/graph/query-parameters).

   ![OData-adatcsatorna](media/desktop-connect-graph-security/ODataFeed.PNG)
    
   A **Meghívás** lehetőséget választva az OData.Feed függvény meghívja az API-t, amely megnyitja a Lekérdezésszerkesztőt, amellyel szűrheti vagy finomíthatja a használni kívánt adatokat, majd a finomított adatkészletet betöltheti a Power BI Desktopba.

10. A következő képen a lekérdezett Microsoft Graph Security-entitás(ok) eredményablaka látható.

   ![Eredmény](media/desktop-connect-graph-security/Result.PNG)
    

Azonnal fel is használhatja az Microsoft Graph Security-összekötő importált adatait a Power BI Desktopban vizualizációk és jelentések készítéséhez, valamint kombinálhatja őket más csatlakoztatott és importált adatokkal, amelyek például egyéb Excel-munkafüzetekből, adatbázisokból vagy más adatforrásokból származnak.

## <a name="next-steps"></a>Következő lépések
* A [Microsoft Graph Security GitHub Power BI-mintaadattárában](https://aka.ms/graphsecuritypowerbiconnectorsamples) megtekintheti az ezt az összekötőt használó mintákat és sablonokat.

* A [Microsoft Graph Security Power BI-összekötő blogbejegyzésében](https://aka.ms/graphsecuritypowerbiconnectorblogpost) felhasználói forgatókönyveket és további információt találhat.

* A Power BI Desktop használatával számos adatforráshoz csatlakozhat. Az adatforrásokkal kapcsolatos információkért lásd az alábbi forrásanyagokat:

    * [Mi az a Power BI Desktop?](desktop-what-is-desktop.md)
    * [Adatforrások a Power BI Desktopban](desktop-data-sources.md)
    * [Adatok formázása és kombinálása a Power BI Desktoppal](desktop-shape-and-combine-data.md)
    * [Kapcsolódás az Excelhez a Power BI Desktopban](desktop-connect-excel.md)
    * [Adatok közvetlen bevitele a Power BI Desktopba](desktop-enter-data-directly-into-desktop.md)
