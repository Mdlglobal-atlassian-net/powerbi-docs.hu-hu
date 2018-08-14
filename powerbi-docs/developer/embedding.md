---
title: Beágyazás a Power BI-jal
description: A Power BI az irányítópultok és jelentések alkalmazásokba való beágyazását lehetővé tevő API-kat kínál.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: overview
ms.date: 07/31/2018
ms.openlocfilehash: 2889345c5e4a5e93602c51baa27bf2c7e28e138f
ms.sourcegitcommit: 16098be04df05bc8e3d44a99b4d143b622759c59
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/07/2018
ms.locfileid: "39616028"
---
# <a name="embedding-with-power-bi"></a>Beágyazás a Power BI-jal

A Power BI szolgáltatás (SaaS) és a Power BI Embedded szolgáltatás az Azure-ban (PaaS) API-kkal is rendelkezik az irányítópultok és jelentések beágyazásához. Ez azt jelenti, hogy a tartalmak (például irányítópultok, átjárók és alkalmazás-munkaterületek) beágyazásához egy funkciókészlet és a Power BI legújabb szolgáltatásai használhatók.

Használhatja az [Előkészítési eszközt](https://aka.ms/embedsetup), amellyel egyszerűen elvégezheti az első lépéseket, és letölthet egy mintaalkalmazást.

Válassza ki az Ön számára megfelelő megoldást:

* Amennyiben [a cég számára végzi a beágyazást](embedding.md#embedding-for-your-organization), kibővítheti a Power BI szolgáltatást. Futtassa a [Beágyazás a cég számára](https://aka.ms/embedsetup/UserOwnsData) megoldást.
* Amennyiben az [ügyfelei számára végez beágyazást](embedding.md#embedding-for-your-customers), irányítópultokat és jelentéseket ágyazhat be olyan felhasználók számára, akik nem rendelkeznek Power BI-fiókkal. Futtassa a [Beágyazás az ügyfelek számára](https://aka.ms/embedsetup/AppOwnsData) megoldást.

![PBIE-minta](media/what-can-you-do/what-can-you-do-02.png)

## <a name="using-apis"></a>API-k használata

A Power BI-tartalmak beágyazása során két fő forgatókönyv képzelhető el.  Egyrészt a cégen belüli felhasználók számára történő beágyazás (a felhasználóknak rendelkezniük kell Power BI-licenccel), másrészt Power BI-licencet nem kívánó beágyazás más felhasználók és ügyfelek számára. A Power BI REST API mindkét forgatókönyvet támogatja.

Power BI-licenccel nem rendelkezők számára ugyanazt az API-t használva ágyazhat be irányítópultokat és jelentéseket egyéni alkalmazásokba függetlenül attól, hogy azt a cége vagy az ügyfele számára készíti. Az ügyfelek így megtekinthetik az alkalmazás által kezelt adatokat. A cégen belüli Power BI-felhasználók ezen kívül *saját adataikat* is megtekinthetik közvetlenül a Power BI-ban vagy a beágyazott alkalmazásban. A beágyazáshoz teljes körűen igénybe veheti a JavaScript és a REST API-k lehetőségeit.

Ha látni kívánja, hogyan működik a beágyazás tekintse meg a [JavaScript beágyazását szemléltető példát](https://microsoft.github.io/PowerBI-JavaScript/demo/).

## <a name="embedding-for-your-organization"></a>Beágyazás a cég számára

Amennyiben **a cég számára végzi a beágyazást**, kibővítheti a Power BI szolgáltatást. A szervezeti beágyazáshoz az alkalmazás felhasználóinak be kell jelentkezniük a Power BI szolgáltatásba, amikor meg szeretnék tekinteni a tartalmaikat. Amikor a cég egyik felhasználója bejelentkezik, csak azokhoz az irányítópultokhoz és jelentésekhez lesz hozzáférése, amelyeknek ők a tulajdonosai, vagy amelyeket a Power BI szolgáltatásban megosztottak vele.

*Példák a cégen belüli beágyazásra: belső alkalmazások, például [SharePoint Online](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/), [Microsoft Teams-integráció (ehhez rendszergazdai jogosultsággal kell rendelkeznie)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/), és [Microsoft Dynamics](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard).*

Amennyiben a cége számára végez beágyazást, tekintse át a következőket:

* [Jelentés integrálása egy alkalmazásba](embed-sample-for-your-organization.md)

Amikor Power BI-felhasználók számára végez beágyazást, az önkiszolgáló lehetőségek (pl. a szerkesztés, mentés stb.) a [JavaScript API-n](https://github.com/Microsoft/PowerBI-JavaScript) keresztül érhetők el.

A gyors indulás érdekében követheti az [Előkészítési eszköz vállalaton belüli beágyazáshoz](https://aka.ms/embedsetup/UserOwnsData) lépéseit, és letölthet egy mintaalkalmazást, amely végigvezeti Önt a jelentés integrálásán a cég számára.

## <a name="embedding-for-your-customers"></a>Beágyazás ügyfelek számára

Amennyiben az **ügyfelei számára végez beágyazást**, irányítópultokat és jelentéseket ágyazhat be olyan felhasználók számára, akik nem rendelkeznek Power BI-fiókkal. Az ügyfelek számára való beágyazást a **Power BI Embedded** végzi.

A [Power BI Embeddeddel](azure-pbie-what-is-power-bi-embedded.md) egy **Microsoft Azure**-szolgáltatás, amellyel független szoftverszállítók (ISV-k) és a fejlesztők lenyűgöző vizualizációkat, jelentéseket és irányítópultokat adhatnak gyorsan alkalmazásaikhoz egy kapacitásalapú, óránkénti díjjal számlázott modellel.

![A beágyazás folyamata ügyfelek számára végzett beágyazás során](media/embedding/powerbi-embed-flow.png)

A Power BI Embedded mind az ISV-k, mind a fejlesztők, mind a ügyfelek számára előnyös. Egy ISV például ingyenesen létrehozhat vizualizációkat a Power BI Desktoppal. Az ISV-k gyorsabban piacra vihetik az alkalmazásaikat a vizuális elemzési fejlesztések minimalizálásával, és kitűnhetnek versenytársaik közül az innovatív adatkörnyezeteikkel. Az ISV-k úgy is dönthetnek, hogy a beágyazott analitikákkal termelt értékért prémiumot számolnak fel.

A Power BI Embedded használatával az ügyfeleinek nem szükséges ismerniük a Power BI működését. Beágyazott alkalmazás létrehozásához csak egy Power BI Pro-fiók szükséges. Ez a Power BI Pro-fiók szolgál fő fiókként az alkalmazás számára (tehát tulajdonképpen egy proxyfiók). A Power BI Pro-fiók lehetővé teszi beágyazási tokenek létrehozását, amelyek hozzáférést biztosítanak a Power BI szolgáltatás olyan irányítópultjaihoz és jelentéseihez, amelyeket az alkalmazás kezel, vagy amelyek az alkalmazáshoz tartoznak.

A Power BI Embeddedet használó fejlesztők az alkalmazás alapvető működésének szentelhetik az idejüket, és nem kell vizualizációk és elemzések fejlesztésével foglalkozniuk. A fejlesztők gyorsan megfelelhetnek az ügyfelek jelentésekkel és irányítópultokkal kapcsolatos igényeinek, és könnyen, teljes mértékben dokumentált API-kkal és SDK-kal ágyazhatnak be tartalmakat. A könnyen navigálható, alkalmazáson belüli adatfeltárás engedélyezésével az ISV-k ügyfelei gyors és magabiztos és döntéseket hozhatnak bármilyen eszközről.

> [!IMPORTANT]
> Bár a beágyazás maga igényli a Power BI szolgáltatás meglétét, az ügyfeleknek nem kell rendelkezniük Power BI-előfizetéssel. Nem kell bejelentkezniük a Power BI szolgáltatásba a beágyazott tartalmak megtekintéséhez az alkalmazásban.

Amikor készen áll az éles környezetbe való áthelyezésre, az alkalmazás-munkaterülethez hozzá kell rendelni egy dedikált kapacitást. A Power BI Embedded a Microsoft Azure-on belül elérhetővé tesz az alkalmazásban felhasználható [dedikált kapacitást](azure-pbie-create-capacity.md).

A beágyazással kapcsolatos további információért lásd a [Power BI-irányítópultok, -jelentések és -csempék beágyazását](embed-sample-for-customers.md) ismertető cikket.

## <a name="next-steps"></a>Következő lépések

Most már elkezdhet Power BI-tartalmat beágyazni az alkalmazásba vagy az ügyfelek számára.

> [!div class="nextstepaction"]
> [Beágyazás a cég számára](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [Mi az a Power BI Embedded?](azure-pbie-what-is-power-bi-embedded.md)

> [!div class="nextstepaction"]
>[Beágyazás az ügyfelek számára](embed-sample-for-customers.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)