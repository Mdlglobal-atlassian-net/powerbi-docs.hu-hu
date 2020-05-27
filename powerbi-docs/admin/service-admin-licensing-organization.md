---
title: Szervezeti Power BI-licencelés
description: A Power BI-ban elérhető különböző licenctípusok áttekintése, valamint információ arról, hogy hogyan vásárolhatják meg és hogyan kezelhetik a rendszergazdák a licenceket a szervezetük számára.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 05/14/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: a0ce3eab2992c59c5b887db1f0838f88db7ad2da
ms.sourcegitcommit: a72567f26c1653c25f7730fab6210cd011343707
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/19/2020
ms.locfileid: "83563488"
---
# <a name="power-bi-licensing-in-your-organization"></a>Szervezeti Power BI-licencelés

Az, hogy a felhasználó mit tehet a Power BI szolgáltatásban attól függ, hogy milyen felhasználónkénti licenccel rendelkezik. A licencek által biztosított hozzáférési szint attól függ, hogy az elérni kívánt munkaterület prémium szintű Power BI-kapacitáshoz van-e rendelve. A Power BI szolgáltatás összes felhasználójának licenccel kell rendelkeznie.

A felhasználók kétféleképpen szerezhetnek licencet. Az önkiszolgáló bejelentkezési képességek és munkahelyi vagy iskolai fiókjuk használatával a felhasználók saját ingyenes vagy Pro-licencet szerezhetnek be. A másik lehetőség, hogy a rendszergazdák beszereznek egy Power BI-előfizetést, és licenceket rendelnek a felhasználókhoz.

A cikk a felhasználónkénti licencek és a szolgáltatások megvásárlásával foglalkozik a rendszergazda szemszögéből. Az [Egyéni Power BI-regisztráció](../fundamentals/service-self-service-signup-for-power-bi.md) című cikkben további információt talál arról, hogyan szerezhetik be a felhasználók a saját licencüket.

## <a name="who-can-purchase-and-assign-licenses"></a>Ki vásárolhat és rendelhet hozzá licenceket?

Ahhoz, hogy a szervezethez tartozó licenceket megvásárolhassa és másokhoz hozzárendelhesse, rendszergazdai szerepkörrel kell rendelkeznie. A rendszergazdai szerepköröket az Azure Active Directory felügyeleti központjában vagy a Microsoft 365 felügyeleti központjában lehet hozzárendelni. A következő táblázat azt mutatja be, hogy a vásárlással és a licenceléssel kapcsolatos feladatok elvégzéséhez milyen szerepkörre van szükség. A szerepkörök Azure Active Directoryben történő használatáról további információért lásd: [Rendszergazdai szerepkörök megtekintése és hozzárendelése az Azure Active Directoryben](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-manage-roles-portal). Ha többet szeretne megtudni a Microsoft 365 rendszergazdai szerepköreiről, tekintse meg a [Rendszergazdai szerepkörök bemutatása](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide) című cikket, ahol ajánlott eljárásokat is talál.

| Ki vásárolhat szolgáltatásokat és licenceket? | Ki kezelheti a felhasználói licenceket? |
| --------------- | --------------- |
| Számlázási adminisztrátor | Licencek rendszergazdája |
| Globális rendszergazda | Felhasználói rendszergazda |
|  | Globális rendszergazda |

Ezek a szerepkörök felügyelik a szervezetet. A Power BI szolgáltatás rendszergazdai szerepkörére vonatkozó további információkat [A Power BI rendszergazdai szerepkörét ismertető](service-admin-role.md) témakör tartalmaz.

## <a name="get-power-bi-for-your-organization"></a>Power BI beszerzése szervezeteknek

A globális rendszergazda vagy a számlázási rendszergazda regisztrálhat a Power BI szolgáltatásra, és licenceket vásárolhat a szervezet felhasználói számára. Ha még nem áll készen a vásárlásra, válassza a Power BI Pro próbaverzióját. Ezzel 25 licencet kap, melyeket egy hónapig használhat. A regisztráció lépésenkénti ismertetését itt tekintheti meg: [Power BI-előfizetés beszerzése a szervezet számára](service-admin-org-subscription.md).

## <a name="about-self-service-sign-up"></a>Az önkiszolgáló regisztráció

Az egyes felhasználók is beszerezhetik saját Power BI-licencüket, ha a saját munkahelyi vagy iskolai fiókjukkal jelentkeznek be. Az ingyenes licenccel a felhasználók megismerkedhetnek a Power BI-jal, és azt személyes adatelemzésre és vizualizációkra használhatják a Saját munkaterület használatával, de nem tudnak tartalmat megosztani más felhasználókkal. A tartalom megosztásához Power BI Pro-licenc szükséges. A felhasználók a licencük típusát Pro-licencre frissíthetik, vagy közvetlenül is regisztrálhatnak a Próra, ha a szervezet a kereskedelmi felhőt használja. A közvetlen vásárlás vagy a Pro verzióra való frissítés nem érhető el az oktatási szervezeteknek és azoknak a szervezeteknek, amelyek az Azure Government, az Azure Germany vagy az Azure China 21Vianet régiókban használnak példányokat.

Ha nem szeretné, hogy az önkiszolgáló regisztráció elérhető legyen a szervezet felhasználói számára, kikapcsolhatja azt [Az önkiszolgáló regisztráció engedélyezése](service-admin-disable-self-service.md) című témakörben leírtak alapján.

Ha tudni szeretné, hogy a szervezeténél mely felhasználók rendelkeznek már licenccel, a [Felhasználói licencek megtekintése és kezelése](service-admin-manage-licenses.md) című cikkben talál erről további információt.

## <a name="license-types-and-capabilities"></a>A licencek típusai és képességei

A felhasználónkénti Power BI-licenceknek két típusa létezik: az ingyenes és a Pro. Az, hogy a felhasználónak melyik licencre van szüksége attól függ, hogy hol van tárolva a tartalom, és hogy hogyan fogják az adott tartalmat felhasználni. A tartalom tárolásának helyét a szervezet [előfizetésének típusa](#subscription-types) határozza meg.

A [Power BI Premium](service-admin-premium-purchase.md) előfizetés-típus lehetővé teszi, hogy a felhasználók ingyenes licenccel használják a prémium szintű kapacitáshoz rendelt munkaterületeken tárolt tartalmakat. A prémium szintű kapacitáson kívül az ingyenes licenccel rendelkező felhasználó a Power BI szolgáltatást csak arra használhatja, hogy adatokhoz csatlakozzon és jelentéseket és irányítópultokat hozzon létre a **Saját munkaterületen**. Nem oszthatnak meg tartalmakat másokkal, és nem tehetnek közzé tartalmat más munkaterületeken. A munkaterület-típusokról további információt a [Munkaterületek típusai](../consumer/end-user-workspaces.md#types-of-workspaces) című témakörben talál.

A standard Power BI-előfizetés megosztott kapacitást használ. Ha a tartalom megosztott kapacitásban van tárolva, a Power BI Pro-licenchez hozzárendelt felhasználók csak Power BI Pro-felhasználókkal tudnak együttműködni. Használhatják a mások által megosztott tartalmat, közzétehetnek tartalmat az alkalmazás-munkaterületeken, megoszthatnak irányítópultokat, és feliratkozhatnak irányítópultokra és jelentésekre.  Ha a munkaterületek prémium szintű kapacitásban vannak, a Pro-felhasználók olyan felhasználók számára is terjeszthetik a tartalmakat, akik nem rendelkeznek Power BI Pro-licenccel.

Az alábbi táblázat összefoglalja az egyes licencelési típusok alapszintű képességeit. Az egyes licenctípusok részletes funkcióit a [Funkciók licenctípusok szerint](../fundamentals/service-features-license-type.md) című témakörben találja.

| Licenctípus | Képességek, ha a munkaterület megosztott kapacitásban van | További képességek, ha a munkaterület prémium szintű kapacitásban van |
| --------- | ----------- | ----------- |
| Power BI (ingyenes) | Hozzáférés a Saját munkaterületen tárolt tartalomhoz | A velük megosztott tartalom felhasználása |
| Power BI Pro | A Pro-licenccel rendelkező felhasználók közzétehetnek tartalmat más munkaterületeken, megoszthatnak irányítópultokat, és feliratkozhatnak irányítópultokra és jelentésekre | Tartalom terjesztése ingyenes licenccel rendelkező felhasználók számára |

## <a name="subscription-types"></a>Előfizetés-típusok

A Microsoft minden felhasználóalapú kereskedelmi licencet használó előfizetése Azure Active Directory-identitáson alapul. A Power BI szolgáltatás használatához olyan identitással kell bejelentkeznie, amelyet az Azure Active Directory támogat kereskedelmi licencekhez. Bármely olyan Microsoft-előfizetéshez hozzáadhatja a Power BI-t, amely az Azure Active Directoryt használja identitásszolgáltatásként. Egyes előfizetések, például az Office 365 E5, már rendelkeznek Power BI Pro-licenccel, így nincs szükség arra, hogy külön regisztráljon a Power BI-ra.

Szervezetek számára kétféle Power BI-előfizetés érhető el: a standard és a prémium.

A standard önkiszolgáló Power BI Pro-előfizetéssel a rendszergazdák felhasználónkénti licenceket rendelhetnek hozzá. Power BI Pro-licencek esetében felhasználónkénti havi díjat számítunk fel. Ezek a licenctípusok lehetővé teszik az együttműködést, a közzétételt, a megosztást és az ad-hoc elemzést. A tartalmat a Microsoft által teljes mértékben felügyelt megosztott tárolókapacitásba menti a rendszer.

A Power BI Premium-előfizetés dedikált kapacitást foglal le a szervezet számára. A Prémium szint megfelelő a nagyvállalati üzleti elemzéshez, a big data-elemzéshez és a felhőbeli és helyszíni jelentéskészítéshez, és speciális felügyeleti és üzembe helyezési vezérlőket is elérhetővé tesz. A dedikált számítási és tárolási erőforrásokat a szervezet kapacitás-rendszergazdái kezelik. Ezért a dedikált környezetért havi díjat számítunk fel. A prémium szint többi előnyei mellett a prémium kapacitásban tárolt tartalmakat olyan felhasználók is elérhetik, akik nem rendelkeznek Power BI Pro-licenccel, és számukra is terjeszthető a tartalom. A prémium szint használatához legalább egy felhasználónak rendelkeznie kell egy hozzá rendelt Power BI Pro-licenccel, és a tartalom létrehozóinak és fejlesztőinek is Power BI Pro-licenccel kell rendelkezniük.

Az előfizetések két típusa nem zárja ki egymást. Rendelkezhet egyszerre Power BI Prémiummal és Power BI Próval is. Ebben az esetben a prémium szintű kapacitásban tárolt tartalmak megoszthatók az összes felhasználóval, és a megosztott kapacitás is elérhető. A kapacitáskorlátokról az [Adattárolás felügyelete Power BI-munkaterületeken](service-admin-manage-your-data-storage-in-power-bi.md) című témakörben tájékozódhat.

A termék funkcióinak és díjszabásának összehasonlításához tekintse meg a [Power BI díjszabását](https://powerbi.microsoft.com/pricing).

## <a name="guest-user-access"></a>Vendégfelhasználói hozzáférés

Előfordulhat, hogy tartalmat szeretne terjeszteni a szervezeten kívüli felhasználók számára is. Külső felhasználókkal úgy oszthat meg tartalmakat, ha vendégként meghívja őket a tartalom megtekintéséhez. A Vállalatközi Azure Active Directory (Azure AD B2B) lehetővé teszi a külső felhasználókkal való megosztást is. A külső felhasználókkal való megosztáshoz a következő feltételeket kell teljesíteni:

- Engedélyezni kell a tartalom külső felhasználókkal történő megosztását

- A vendégfelhasználónak megfelelő licenccel kell rendelkeznie ahhoz, hogy megtekinthesse a megosztott tartalmat

A vendégfelhasználói hozzáférésről további információt a [Power BI tartalmak terjesztése Azure AD B2B külső vendégfelhasználóknak](service-admin-azure-ad-b2b.md) című témakörben talál.

## <a name="purchase-power-bi-pro-licenses"></a>Power BI Pro-licencek vásárlása

Rendszergazdaként a Power BI Pro-licenceket a Microsoft 365-ön keresztül vagy egy Microsoft-partnertől vásárolhatja meg. A licenceket a megvásárlásuk után ki kell osztania az egyes felhasználóknak. További információkért lásd [a Power BI Pro-licencek vásárlását és kiosztását ismertető](service-admin-purchasing-power-bi-pro.md) témakört.

### <a name="power-bi-pro-license-expiration"></a>A Power BI Pro-licenc lejárata

A Power BI Pro-licenc lejárata után egy türelmi időszak kezdődik. A mennyiségi licenc részeként megvásárolt licencekre a türelmi időszak 90 nap. Közvetlenül vásárolt licencre a türelmi időszak 30 nap.

A Power BI Pro előfizetési életciklusa megegyezik a Microsoft 365-ével. További információ: [Mi történik az adatokkal és a hozzáféréssel, amikor a Microsoft 365 vállalati verzióra szóló előfizetés befejeződik?](/microsoft-365/commerce/subscriptions/what-if-my-subscription-expires).


## <a name="next-steps"></a>Következő lépések

- [Power BI Pro-licencek vásárlása és kiosztása](service-admin-purchasing-power-bi-pro.md)
- [A vállalati verziós előfizetéseinek és számlázásának dokumentációja](/microsoft-365/commerce/?view=o365-worldwide)
- [Bejelentkezett Power BI-felhasználók keresése](service-admin-access-usage.md)
- További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
