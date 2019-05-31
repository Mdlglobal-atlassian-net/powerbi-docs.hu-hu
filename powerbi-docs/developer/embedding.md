---
title: Beágyazott analitika a Power BI-jal
description: A Power BI az irányítópultokhoz és jelentésekhez használható analitikák alkalmazásokba való beágyazását lehetővé tevő API-kat kínál. Útmutató a Power BI-jal PaaS- vagy SaaS-környezetben végzett beágyazáshoz, beágyazott analitikai szoftver, beágyazott analitikai eszközök vagy beágyazott üzleti intelligencia eszközök használatával.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: overview
helpviewer_keywords:
- embedded analytics
- embedding
- Power BI embedding
- app owns data
- user owns data
- Power BI APIs
ms.custom: seodec18
ms.date: 05/15/2019
ms.openlocfilehash: a212691f2af877e3b86e021a4f48644f4fa6e8e3
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051065"
---
# <a name="embedded-analytics-with-power-bi"></a>Beágyazott analitika a Power BI-jal

A Power BI szolgáltatás (SaaS) és a Power BI Embedded szolgáltatás az Azure-ban (PaaS) API-kkal is rendelkezik az irányítópultok és jelentések beágyazásához. Tartalmak beágyazása során is elérheti a Power BI legújabb szolgáltatásai például irányítópultokhoz, átjárókhoz és alkalmazás-munkaterületek.

A [beágyazást előkészítő eszközzel](https://aka.ms/embedsetup) gyorsan megteheti az első lépéseket és letölthet egy mintaalkalmazást.

Válassza ki az Ön számára megfelelő megoldást:

* Amennyiben [a cég számára végzi a beágyazást](embedding.md#embedding-for-your-organization), kibővítheti a Power BI szolgáltatást. Ehhez megvalósítása a [a szervezet beágyazási](https://aka.ms/embedsetup/UserOwnsData) megoldás.
* [Az ügyfelek számára végez beágyazást](embedding.md#embedding-for-your-customers) lehetővé teszi, hogy a beágyazott irányítópultok és jelentések, a felhasználók számára, akik nem rendelkeznek Power BI-fiókkal. Ehhez megvalósítása a [beágyazási az ügyfelek számára](https://aka.ms/embedsetup/AppOwnsData) megoldás.

![PBIE-minta](media/what-can-you-do/what-can-you-do-02.png)

## <a name="use-apis"></a>API-k használata

A Power BI-tartalmak beágyazásához két fő forgatókönyv közül választhat:
- (A Power BI-licenccel rendelkező) a szervezet felhasználói számára ágyaz be. 
 
- A felhasználók és a Power BI-licenceket nem igénylő ügyfelek számára végez beágyazást. 

A [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/) mindkét forgatókönyvet támogatja.

Power BI-licenccel nem rendelkezők számára ugyanazt az API-t használva ágyazhat be irányítópultokat és jelentéseket egyéni alkalmazásokba függetlenül attól, hogy azt a cége vagy az ügyfele számára készíti. Az ügyfelek így megtekinthetik az alkalmazás felügyelt adatokat. Ezenkívül a Power BI-felhasználók a szervezet rendelkezik is megtekinthetik *adataikat* közvetlenül a Power bi-ban vagy a beágyazott alkalmazás a környezetben. A beágyazáshoz teljes körűen igénybe veheti a JavaScript és a REST API-k lehetőségeit.

Hogyan működik a beágyazás megismeréséhez tekintse meg a [JavaScript beágyazási minta](https://microsoft.github.io/PowerBI-JavaScript/demo/).

## <a name="embedding-for-your-organization"></a>Beágyazás a cég számára

Amennyiben **a cég számára végzi a beágyazást**, kibővítheti a Power BI szolgáltatást. A beágyazás megköveteli az alkalmazás felhasználók bejelentkezési tartalmak megtekintéséhez Power BI szolgáltatásba. A bejelentkező vállalati felhasználóknak csak azokhoz az irányítópultokhoz és jelentésekhez lesz hozzáférésük, amelyeknek ők a tulajdonosai, vagy amelyeket a Power BI szolgáltatásban megosztottak velük.

Szervezet beágyazási ilyenek például a belső alkalmazások például [SharePoint online-hoz](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/), [(rendszergazdai jogosultsággal kell rendelkeznie) Microsoft Teams-integráció](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/), és [Microsoft Dynamics](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard).

Ágyazhat be a szervezet számára, lásd: [oktatóanyag: A Power BI-tartalom beágyazása egy alkalmazásba, a szervezet](embed-sample-for-your-organization.md).

Amikor Power BI-felhasználók számára végez beágyazást, az önkiszolgáló lehetőségek (pl. a szerkesztés, mentés stb.) a [JavaScript API-n](https://github.com/Microsoft/PowerBI-JavaScript) keresztül érhetők el.

Lépkedjen végig a [beágyazása-telepítő eszköz](https://aka.ms/embedsetup/UserOwnsData) az első lépések és a egy mintaalkalmazást, amely végigvezeti a szervezet egy jelentés integrálása letöltése.

## <a name="embedding-for-your-customers"></a>Beágyazás ügyfelek számára

**Az ügyfelek számára végez beágyazást** ágyazhat be irányítópultokat és jelentéseket a Power BI-fiókkal nem rendelkező felhasználók számára teszi lehetővé. Más néven a beágyazás van *Power BI Embedded*.

[Power BI Embedded](azure-pbie-what-is-power-bi-embedded.md) van egy **Microsoft Azure** szolgáltatás, amely lehetővé teszi a független szoftvergyártók (ISV-k) és a fejlesztők gyorsan Vizualizációk, jelentések és irányítópultok beágyazása egy alkalmazásba. A beágyazás egy kapacitásalapú, óradíjas mért modellel történik.

![A beágyazás folyamata ügyfelek számára végzett beágyazás során](media/embedding/powerbi-embed-flow.png)

A Power BI Embedded mind az ISV-k, mind a fejlesztők, mind a ügyfelek számára előnyös. Egy ISV például ingyenesen létrehozhat vizualizációkat a Power BI Desktoppal. Csökkenthetik a vizuális elemzési fejlesztésekre fordított erőfeszítéseket, ISV-k elérése a gyorsabb piacra jutás és kitűnjenek a versenytársak adatkezelési élményt kínáló termékeikkel. ISV-k is dönthetnek, hogy egy prémium szintű hozhatnak létre az embedded analytics további értéket.

A Power BI Embedded használatával az ügyfeleinek nem szükséges ismerniük a Power BI működését. Két különböző módszerek segítségével beágyazott alkalmazás létrehozásához:
- A Power BI Pro-fiókja 
- Szolgáltatásnév 

A Power BI Pro-fiók funkcionál az alkalmazás fő fiók (lényegében úgy működik, egy proxykiszolgáló-fiók). Ez a fiók lehetővé teszi beágyazási tokenek, amelyek hozzáférést biztosítanak az alkalmazás Power BI-irányítópultok és jelentések.

A [Szolgáltatásnév](embed-service-principal.md) **csak az alkalmazásra vonatkozó** tokennel képes Power BI-tartalmat beágyazni az alkalmazásokba. Emellett lehetővé teszi, hogy hozzon létre beágyazási tokenek, amelyek hozzáférést biztosítanak az alkalmazás Power BI-irányítópultok és jelentések.

Power BI Embedded használatával a fejlesztők idejüket az alkalmazás fő funkciói helyett költségkeret Vizualizációk és elemzési való fókuszál. Ezeket rövid idő alatt igények figyelembevételével készült ügyfelek jelentésekre és irányítópultokra, és könnyedén beágyazhatják a teljes körű dokumentációval rendelkező API-k és SDK-k. A könnyen navigálható, alkalmazáson belüli adatfeltárás engedélyezésével az ISV-k ügyfelei gyors és magabiztos és döntéseket hozhatnak bármilyen eszközről.

> [!IMPORTANT]
> Bár a beágyazás van szüksége a Power BI szolgáltatásban, az ügyfelek nem kell az alkalmazás beágyazott tartalmak megtekintéséhez Power BI-fiókkal rendelkezik. 

Amikor készen áll az éles környezetbe való áthelyezésre, az alkalmazás-munkaterülethez hozzá kell rendelni egy dedikált kapacitást. A Power BI Embedded a Microsoft Azure-on belül elérhetővé tesz az alkalmazásban felhasználható [dedikált kapacitást](azure-pbie-create-capacity.md).

A részletek beágyazást, tekintse meg [Power BI-tartalmak beágyazása](embed-sample-for-customers.md).

## <a name="next-steps"></a>Következő lépések

Most már elkezdhet Power BI-tartalmat beágyazni az alkalmazásba vagy az ügyfelek számára.

> [!div class="nextstepaction"]
> [Beágyazás a cég számára](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [Mi az a Power BI Embedded?](azure-pbie-what-is-power-bi-embedded.md)

> [!div class="nextstepaction"]
>[Beágyazás az ügyfelek számára](embed-sample-for-customers.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
