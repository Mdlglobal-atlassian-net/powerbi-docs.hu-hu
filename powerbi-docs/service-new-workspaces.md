---
title: Munka szervezése az új munkaterületeken a Power BI-ban
description: Bemutatjuk az új munkaterületeket, olyan irányítópultokból és jelentésekből álló gyűjteményeket, amelyek célja az alapvető metrikák biztosítása a vállalat számára.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/07/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: c74e9c3119c9c9a8057672d68e6499d93b46e3f8
ms.sourcegitcommit: 9dd6dc8c06091ea02dee5e9ddc45a2922877b1f2
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/08/2020
ms.locfileid: "82991391"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Munka szervezése az új munkaterületeken a Power BI-ban

A *munkaterületeken* együttműködhet a munkatársaival irányítópultok, jelentések, adathalmazok és oldalakra osztott jelentések gyűjteményeinek készítésén. Az új munkaterületi felhasználói felület segítségével jobban kezelhető a tartalomhoz való hozzáférés. Ez a cikk bemutatja az új munkaterületeket, és hogy miben térnek el a klasszikus munkaterületektől.  Ahogyan a klasszikus munkaterületek, ezek is alkalmazások létrehozására és terjesztésére szolgálnak. Készen áll egy új munkaterület létrehozására? Olvassa el az [új munkaterületi felhasználói felület létrehozását](service-create-the-new-workspaces.md) ismertető cikket.

Az új, frissített munkaterületek a meglévő klasszikus munkaterületekkel egyidejűleg használhatóak. Az alapértelmezett munkaterület-típus az új felületű. Igény szerint továbbra is létrehozhat és használhat [klasszikus munkaterületeket](service-create-workspaces.md) Office 365-csoportok alapján. Készen áll a klasszikus munkaterülete migrálására? A részletekért lásd [a Power BI klasszikus munkaterületeinek új munkaterületekre frissítését](designer/service-upgrade-workspaces.md) bemutató cikket.

Az új munkaterületekkel a következőket végezheti el:

- Munkaterület-szerepköröket rendelhet felhasználói csoportokhoz: biztonsági csoportokhoz, terjesztési listákhoz, Office 365-csoportokhoz és egyéni felhasználókhoz.
- A Power BI-ban anélkül is létrehozhat munkaterületeket, hogy egy alapul szolgáló, társított Office 365-csoportot kellene létrehoznia. A munkaterület felügyelete kizárólag a Power BI-ban zajlik.
- Ha kívánja, továbbra is az Office 365-csoportokon keresztül kezelheti a tartalmakhoz való felhasználói hozzáférést. Ehhez egyszerűen adjon hozzá egy Office 365-csoportot a munkaterület hozzáférési listájához.
- Részletesebb munkaterület-szerepköröket használhat, amelyekkel rugalmasabb engedélykezelést érhet el a munkaterületeken.

A Power BI továbbra is felsorolja az összes olyan Office 365-csoportot, amelynek Ön tagja. Ezzel elkerülhető a meglévő munkafolyamatok módosítása.

## <a name="new-and-classic-workspace-differences"></a>Az új és a klasszikus munkaterületek közötti különbség

Az új munkaterületekkel újraterveztünk néhány funkciót. A főbb különbségek a következők.

* Ezeknek a munkaterületeknek a létrehozása nem hoz létre Office 365-csoportokat, ahogyan a klasszikus munkaterületek esetén történt. Egy Office 365-csoport viszont már felhasználható arra, hogy hozzáférést adjon a felhasználóknak a munkaterülethez, ha szerepkört rendel hozzá. 
* A klasszikus munkaterületeken csak egyéneket vehet fel a tagok és rendszergazdák listájára. Az új munkaterületeken több Active Directory-alapú biztonsági csoportot, terjesztési listát vagy Office 365-csoportot vehet fel ezekre a listákra, így könnyebben kezelheti a felhasználókat. 
- A klasszikus munkaterületeken létrehozhat vállalati tartalomcsomagot. Az új munkaterületen ezt nem teheti meg.
- A klasszikus munkaterületeken használhat szervezeti tartalomcsomagot. Az új munkaterületen ezt nem teheti meg.

### <a name="workspace-features-that-work-differently"></a>A munkaterületek másképp működő funkciói

A jelenlegi munkaterületek egyes funkciói másképp működnek, mint az új munkaterületeké. Ezeket a különbségeket szándékosan alakítottuk így, az ügyfelektől kapott visszajelzések alapján. Rugalmasabb megközelítést tesznek lehetővé a munkaterületekkel való együttműködéshez.

- **Licencelés kikényszerítése**: A jelentések az új munkaterületi felhasználói felületen való közzététele kikényszeríti a meglévő licencelési szabályok betartását. Ahhoz, hogy a felhasználók a munkaterületeken együttműködhessenek, vagy tartalmat oszthassanak meg egymással a Power BI szolgáltatásban, Power BI Pro-licenccel kell rendelkezniük. A Pro-licenccel nem rendelkező felhasználók a „Csak Power BI Pro-licenccel rendelkező felhasználók tehetnek közzé tartalmakat ezen a munkaterületen.” hibaüzenetet kapják.
- **A tagok ismételt megosztásra vonatkozó jogosultsága**: A közreműködői szerepkör váltja fel ezt a beállítást.
- **Csak olvasható munkaterületek**: Ahelyett, hogy a felhasználóknak csak olvasási hozzáférést biztosít a munkaterülethez, rendelje hozzájuk a Megtekintő szerepkört. Ez hasonló, csak olvasói hozzáférést biztosít a munkaterületen lévő tartalmakhoz.
- **A Pro-licenccel nem rendelkező felhasználók** akkor is hozzáférnek a Power BI Premium-kapacitásban lévő munkaterülethez, ha csak Megtekintő szerepkörrel rendelkeznek.
- **Adatok exportálásának engedélyezése a felhasználók számára**: A Megtekintő szerepkörrel rendelkező felhasználók akkor exportálhatnak adatokat, ha összeállítási engedélyt biztosít nekik a munkaterületen lévő adathalmazokra vonatkozóan. További információ az [adathalmazok összeállítási engedélyéről](service-datasets-build-permissions.md).
- Nincs **Kilépés a munkaterületből** gomb.

### <a name="workspace-contact-list"></a>Munkaterületi címlista

Az új **Címlista** funkcióval meghatározhatja, hogy mely felhasználók kapjanak értesítést a munkaterületen felmerülő problémákról. Alapértelmezés szerint minden munkaterület-rendszergazdaként megadott felhasználó vagy csoport értesítést kap, de Ön testre szabhatja a listát. A címlistában felsorolt felhasználók vagy csoportok a felhasználói felületen is fel vannak tüntetve, megkönnyítve a felhasználók számára a munkaterülettel kapcsolatos segítségkérést. 

Tovább tájékozódhat a [munkaterületi címlista beállításáról](service-create-the-new-workspaces.md#workspace-contact-list).

### <a name="workspace-onedrive"></a>Munkaterületi OneDrive

A munkaterületi OneDrive funkcióval olyan Office 365-csoportot konfigurálhat, amelynek SharePoint-dokumnetumtárbeli fájltárolója elérhető a munkaterület felhasználói számára. A csoportot a Power BI-on kívül hozza létre.

A Power BI nem szinkronizálja azon felhasználók és csoportok jogosultságait, akik számára Office 365-csoporttagsággal van konfigurálva a munkaterülethez való hozzáférés. Ajánlott a munkaterülethez való hozzáférést ugyanazzal az Office 365-csoporttal kezelni, amelynek fájltárolóját ebben a beállításban konfigurálja. 

Tovább tájékozódhat a [munkaterületi OneDrive beállításáról és eléréséről](service-create-the-new-workspaces.md#workspace-onedrive).  

## <a name="roles-in-the-new-workspaces"></a>Az új munkaterületek szerepkörei

Új munkaterülethez úgy adhat hozzáférést, hogy felhasználói csoportokat vagy személyeket vesz fel a munkaterületi szerepkörök (rendszergazdák, tagok, közreműködők vagy megtekintők) egyikébe. A meghatározott szerepkört a felhasználói csoport minden tagja megkapja. Ha egy felhasználó több felhasználói csoportnak is tagja, a szerepkörei nyújtotta legmagasabb szintű engedéllyel fog rendelkezni.

A szerepkörökkel kezelheti, hogy mely felhasználók milyen műveleteket végezhetnek a munkaterületeken, így elősegítheti a csapatok együttműködését. Az új munkaterületekkel szerepköröket rendelhet egyénekhez és felhasználói csoportokhoz: biztonsági csoportokhoz, Office 365-csoportokhoz és terjesztési listákhoz. 

Szerepkörök felhasználói csoportokhoz való hozzárendelésekor a csoport felhasználói hozzáférnek a tartalomhoz. Ha beágyaz felhasználói csoportokat, minden tag jogosultságot kap.

[!INCLUDE [power-bi-workspace-roles-table](includes/power-bi-workspace-roles-table.md)]

> [!NOTE]
> A munkaterület tartalmát tallózó felhasználókra vonatkozó sorszintű biztonságot a Megtekintő szerepkör használatával érvényesítheti. Ha anélkül szeretné kikényszeríteni az RLS-t, hogy hozzáférést adna a munkaterülethez, tegyen közzé egy Power BI alkalmazást az adott felhasználók számára, vagy használja a megosztást a tartalom terjesztéséhez.

## <a name="licensing"></a>Licencelés
A megosztott kapacitásban a munkaterülethez felvett személyek mindegyikének Power BI Pro-licenccel kell rendelkeznie. A munkaterületen a felhasználók együttműködhetnek az irányítópultokon és jelentéseken, amelyeket a szélesebb közönség vagy akár a teljes vállalat elé szeretne tárni. 

Ha másokkal is megszeretné osztani a tartalmat a szervezeten belül, rendeljen hozzájuk Power BI Pro-licencet, vagy helyezze a munkaterületet egy Power BI Prémium szintű kapacitásba.

Ha a munkaterület Power BI Premium-kapacitásban van, a Megtekintő szerepkörrel rendelkező felhasználók akkor is hozzáférnek a munkaterülethez, ha nem rendelkeznek Power BI Pro-licenccel. Ha azonban magasabb, például rendszergazda, tag vagy közreműködő szerepkört rendel ezekhez a felhasználókhoz, a rendszer Pro-próbaidőszak indítására szólítja fel őket, amikor megkísérelnek hozzáférni a munkaterülethez. Ahhoz, hogy a Pro-licenccel nem rendelkező felhasználók is használhassák a Megtekintő szerepkört, ellenőrizze, hogy nem rendelkeznek-e más munkaterületi szerepkörökkel, akár egyénileg, akár egy felhasználói csoporton keresztül.

> [!NOTE]
> Az jelentések közzététele az új munkaterületi felületen a jelenlegi licencelési szabályok szigorúbb érvényesítésével történik. A Power BI Desktopból vagy más ügyféleszközből Pro-licenc nélkül közzétételt megkísérlő felhasználók számára a „Csak Power BI Pro-licenccel rendelkező felhasználók tehetnek közzé tartalmakat ezen a munkaterületen.” hibaüzenet jelenik meg.

## <a name="administering-new-workspace-experience-workspaces"></a>Az új felületű munkaterületek felügyelete

Az új munkaterületi felhasználói felületek adminisztrációja a Power BI felügyeleti portálján történik. A Power BI rendszergazdái döntik el, hogy egy szervezet mely tagjai hozhatnak létre munkaterületeket és terjeszthetnek alkalmazásokat. A rendszergazdák megtekinthetik a szervezet összes munkaterületének állapotát. Ők végezhetik a munkaterületek kezelését és helyreállítását is. További információt a felügyeleti portál [új munkaterületek létrehozásáról](service-admin-portal.md#create-the-new-workspaces) szóló cikkében olvashat.

## <a name="guest-users"></a>Vendégfelhasználók

Az [Azure AD B2B vendégfelhasználói](service-admin-azure-ad-b2b.md) alapértelmezés szerint nem férhetnek hozzá munkaterületekhez. A Power BI-rendszergazdák [engedélyezhetik, hogy külső vendégfelhasználók is szerkeszthessék és kezelhessék a szervezet tartalmait](service-admin-azure-ad-b2b.md#guest-users-who-can-edit-and-manage-content). Az engedélyezett vendégfelhasználók azokhoz a munkaterületekhez férhetnek hozzá, amelyekhez van engedélyük.

## <a name="auditing"></a>Naplózás

A Power BI az alábbi tevékenységeket naplózza az új munkaterületi felületű munkaterületeken.

| Felhasználóbarát név | Művelet neve |
|---|---|
| Power BI-mappa létrehozása | CreateFolder (Mappa létrehozása) |
| Power BI-mappa törlése | DeleteFolder (Mappa törlése) |
| Power BI-mappa frissítése | UpdateFolder (Mappa frissítése) |
| Power BI-mappahozzáférés frissítése| UpdateFolderAccess (Mappahozzáférés frissítése) |

További tudnivalók a [Power BI-beli naplózásról](service-admin-auditing.md).

## <a name="limitations-and-considerations"></a>Korlátozások és szempontok

Figyelembe veendő korlátozások:

- Egy munkaterület legfeljebb 1000 adathalmazt, vagy adathalmazonként 1000 jelentést tartalmazhat. 
- Power BI Pro-licenccel rendelkező személy legfeljebb 1 000 munkaterületnek lehet tagja.
- Az Excelhez készült Power BI Publisher nem támogatott.

## <a name="frequently-asked-questions"></a>Gyakori kérdések

**Befolyásolja az új munkaterületi felhasználói felület a meglévő tartalmakra mutató hivatkozásokat?**

Nem. A klasszikus munkaterületeken már meglévő elemeket az új munkaterületi felület nem befolyásolja. Az új munkaterületi felület általános elérhetőségével megváltozott a létrehozható munkaterületek alapértelmezése, de a meglévő munkaterületek nem módosulnak. 

**Együtt jár az általános elérhetőség a meglévő munkaterületek új felületre való frissítésével?**

Nem. Az új munkaterületi felület általános elérhetőségével csak a munkaterületek alapértelmezése módosul az új felületű munkaterületre. Az Office 365-csoportokon alapul meglévő klasszikus munkaterületek változatlanok maradnak.

**Továbbra is automatikusan létre vannak hozva munkaterületek az Office 365-csoportokhoz?**

Igen. Mivel a két munkaterület-típust párhuzamosan támogatjuk, a munkaterületek listájában továbbra is megtalálható az összes Office 365-csoport felsorolása, amelyhez a felhasználónak hozzáférése van.

## <a name="next-steps"></a>Következő lépések

* [Új munkaterületek létrehozása a Power BI-ban](service-create-the-new-workspaces.md)
* [A klasszikus munkaterületek létrehozása](service-create-workspaces.md)
* [Alkalmazások telepítése és használata a Power BI-ban](service-create-distribute-apps.md)
* Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
