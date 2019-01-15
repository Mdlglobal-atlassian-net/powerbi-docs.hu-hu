---
title: Sablonalapú Power BI tartalomcsomagok tesztelése
description: Sablonalapú tartalomcsomagok tesztelése
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/09/2017
ms.author: maggies
ms.openlocfilehash: 2ceb8440cd64b05966caaadc9346771dd28cba82
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54281229"
---
# <a name="testing-template-content-packs-for-power-bi"></a>Sablonalapú Power BI tartalomcsomagok tesztelése
A tartalomcsomagokat a közzétételre beküldés előtt többféleképpen is letesztelheti.  

> [!NOTE]
> Ha a tartalomcsomag saját fejlesztésű egyéni [adatösszekötőt](https://aka.ms/DataConnectors) használ, az adatfrissítés vagy a sablonalapú tartalomcsomag alább leírt frissítése nem lehetséges. Ebben az esetben [küldje be](#submission) a tartalomcsomagot, és a Power BI csapat Önnel együttműködve leteszteli azt.
> 
> 

## <a name="testing-scheduled-data-refresh"></a>Ütemezett adatfrissítések tesztelése
A sablonalapú tartalomcsomagok a PowerBI.com Frissítés szolgáltatásának lehetőségeit kihasználva példányosítják a tartalomcsomagot a csatlakozáskor az ügyfél adatainak felhasználásával. A tartalomcsomag nyilvános közzététele előtt letesztelheti a munkafolyamatot a létrehozott Desktop-fájllal.

A fájl frissítése után kattintson a három pontra (…) az adatkészlet mellett, és válassza a Frissítés ütemezése lehetőséget. Állítsa be a forrás hitelesítő adatait. Ellenőrizze, hogy az adatkészlet sikeresen frissül-e – az „Azonnali frissítés” és az „Ütemezett frissítés” működését egyaránt próbálja ki. Ha a frissítés hibát jelez, vizsgálja meg a hibaüzenetet, és ellenőrizze a lekérdezéseket és a célrendszert.

### <a name="additional-refresh-tips"></a>További frissítési tippek
* A frissítési kísérlet során a rendszernek csak egy adatforrást szabad észlelnie.  
* A tesztkapcsolatnak azt is jeleznie kell, hogy a felhasználó le tudja majd tölteni a tartalomcsomagot. Amennyiben nem így lenne, gondoskodjon róla, hogy a lekérdezések kezelik az ebből következő többi hibaeseteket.  
* A frissítésnek észszerű időn belül be kell fejeződnie, általában kb. 5 perc az ajánlott időkorlát.  

![beállítások](media/template-content-pack-testing/scheduledrefresh.png)

<a name="templates"></a>

## <a name="testing-templates"></a>Sablonok tesztelése
A sablonalapú tartalomcsomagok hasonlóak a meglévő megoldásokhoz, azzal a különbséggel, hogy nem tartalmaznak tényleges adatokat az adatkészletben. Ehelyett, amikor egy felhasználó alkalmaz vagy példányosít egy sablont, a rendszer kéri a kapcsolódási paramétereket vagy hitelesítő adatokat. A csatlakozás után a felhasználó a saját adatait látja majd az irányítópulton, a jelentésben és az adatkészletekben. 

Miután a felhasználó példányosította az általa elérhető tartalomcsomagot, az adatkészlet beállításai, többek közt az ütemezett frissítések és az adatkészlet bármely RLS-beállítása **nem** lesznek közzétéve a tartalomcsomaggal.  

> [!NOTE]
> A sablonalapú tartalomcsomagok legfeljebb 1 irányítópultot, 1 jelentést és 1 adatkészletet tartalmazhatnak. A korlátozások felsorolását a sablonok [készítésével](template-content-pack-authoring.md#restrictions) foglalkozó oldal írja le. 
> 
> 

Ha a bérlőn engedélyezni szeretné a sablonok létrehozását, kérje meg a Power BI-rendszergazdát, hogy engedélyezze az alábbi szolgáltatáskapcsolót. 

![szolgáltatáskapcsoló](media/template-content-pack-testing/featureswitch.png)

A kacsoló engedélyezését követően egy jelölőnégyzet jelenik meg a [„Tartalomcsomag létrehozása”](https://app.powerbi.com/groups/me/publish-content/) terület alján, amelynek bejelölésével közzéteheti a sablonalapú tartalomcsomagokat a szervezetben. 

![jelölőnégyzet](media/template-content-pack-testing/checkbox.png)

### <a name="naming"></a>Elnevezés
Javasoljuk, hogy a tartalomcsomagokban lévő irányítópultokat, jelentéseket és adatkészleteket következetesen nevezze el. Ezek a nevek szoftveresen kötöttek, és minden felhasználó ugyanazt látja majd, így a termék/forgatókönyv nevének használata segíthet a felhasználóknak könnyebben megtalálni ezeket.

### <a name="additional-template-tips"></a>További tippek a sablonokhoz
* A lekérdezésekben mindenképp olyan paramétereket adjon meg, amelyek jelentéssel bíró adatokat adnak vissza a végfelhasználók számára.
* Mérlegelje azt is, hogy a végfelhasználóknak milyen hosszan kell várakozniuk az ütemezett frissítések futtatása során.

![létrehozás](media/template-content-pack-testing/createtemplate.png)

<a name="submission"></a>

## <a name="submission"></a>Beküldés
A [Microsoft AppSource](https://appsource.microsoft.com/en-us/partners/list-an-app) beküldési eljárásával közzéteheti a sablonalapú tartalomcsomagot a szolgáltatás-tartalomcsomagok katalógusában a PowerBI.com helyen, valamint felveheti a tartalomcsomagot a [Microsoft AppSource](http://appsource.microsoft.com) listájára.

### <a name="before-submission"></a>Beküldés előtt
* Tekintse át a tartalomcsomag egyes összetevőinak létrehozására vonatkozó tippeket
* Tesztelje a csatlakozást különféle fiókokkal és adatfeltételekkel. (Ha saját egyéni [adatösszekötőt](https://aka.ms/DataConnectors) fejlesztett, hagyja ki ezt a lépést.)
* Tekintse át az összes vizualizációt, és nézze át, hogy nincsenek-e bennük elírások.
* Bizonyosodjon meg róla, hogy a tartalomcsomag jól reagál a kérdésekre – javasoljuk, hogy legalább 30 különféle kérdéssel tesztelje le a teljes adatmodellt. (Ha saját egyéni [adatösszekötőt](https://aka.ms/DataConnectors) fejlesztett, hagyja ki ezt a lépést.)

### <a name="submission"></a>Beküldés
Miután készen áll a beküldésre, lépjen az AppSource [alkalmazásbeküldési oldalára](https://appsource.microsoft.com/en-us/partners/list-an-app), és küldje be az adatokat. Az elérhető termékek listájában mindenképp válassza ki a Power BI terméket.

A Power BI csapat áttekinti az igénylést, és felveszi Önnel a kapcsolatot annak érdekében, hogy minden összetevő megfeleljen a beküldési előírásoknak. A teljesség ellenőrzése mellett mindenképpen ellenőrizze azt is, hogy a megadott irányítópult és jelentések megfelelnek-e az alkalmazásban leírt üzleti forgatókönyvnek.

### <a name="updates"></a>Frissítések
A tartalomcsomag frissítésének folyamata hasonló a kezdeti beküldés folyamatához. 

