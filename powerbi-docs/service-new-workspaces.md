---
title: Az új munkaterületek – a Power bi-ban végzett munka rendszerezése
description: Ismerje meg az új munkaterületek, amely gyűjteményei, irányítópultok és jelentések közvetíteni kívánt fontosabb metrikákat a szervezet számára.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/18/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 9f5dfaa5a23ae46fef131a52355531b5fbde3051
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100692"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Az új munkaterületek a Power bi-ban végzett munka rendszerezése

 *Munkaterületek* helyek együttműködhet munkatársaival az irányítópultok, jelentések és tördelt jelentések gyűjteményeit hozhatja létre a rendszer. Az új munkaterületi felhasználói felület segítségével hatékonyabban kezelheti a tartalomhoz való hozzáférését. Ez a cikk ismerteti az új munkaterületek és a klasszikus munkaterületek eltéréseikről.  Mivel a klasszikus munkaterületek, továbbra is használhatja őket alkalmazások létrehozása és közzététele. Megtudhatja, hogyan lehet a [hozzon létre egy új munkaterületi felhasználói élményt](service-create-the-new-workspaces.md).

Az új munkaterületi felhasználói felület elérte az általánosan elérhetővé tétel (GA), és most az alapértelmezett munkaterületre. Továbbra is hozhat létre és használhat [klasszikus munkaterületek](service-create-workspaces.md) Office 365-csoportok alapján. 

> [!NOTE]
> Sorszintű biztonság (RLS) a Power BI Pro felhasználói munkaterületen lévő tartalom tallózása kényszerítéséhez továbbra is az [klasszikus munkaterületek](service-create-workspaces.md). Válassza ki a **tagok csak a Power BI-tartalmak megtekintésére** lehetőséget. Azt is megteheti Power BI alkalmazások közzététele a felhasználók számára, vagy a tartalom terjesztése a megosztás használatával. A soron következő megjelenítő szerepkör lehetővé teszi az ebben a forgatókönyvben a jövőben az új munkaterületi felhasználói élményt munkaterületek.

Az új munkaterületek segítségével:

- Munkaterület-szerepköröket rendelhet felhasználói csoportokhoz: biztonsági csoportokhoz, terjesztési listákhoz, Office 365-csoportokhoz és egyéni felhasználókhoz.
- Office 365-csoport létrehozása nélkül hozhat létre egy Power BI-munkaterületet.
- Részletesebb munkaterület-szerepköröket használhat, amelyekkel rugalmasabb engedélykezelést érhet el a munkaterületeken.

Amikor létrehoz egy új munkaterületet, nem hoz létre egy mögöttes, társított Office 365-csoportot is. A munkaterület felügyelete kizárólag a Power BI-ban zajlik. Az új munkaterületi felhasználói felület – Office 365-csoportok tartalomhoz való hozzáférés kezelésének folytatásához a munkaterület-hozzáférési listán szereplő Office 365-csoportot most már hozzáadhat.

## <a name="administering-new-workspace-experience-workspaces"></a>Új munkaterület élmény munkaterületek felügyelete
Új munkaterületi felhasználói élményt munkaterületek felügyelete jelenleg a Power BI-ban a Power BI-rendszergazdák döntse el, az egy szervezeten belül kik hozhatnak létre munkaterületeket. Ezek is kezelheti és helyreállítani a munkaterületet. Ehhez a Power BI felügyeleti portálján vagy PowerShell-parancsmagok használata szükséges. Klasszikus munkaterületek az Office 365-csoportok alapján felügyeleti továbbra is fennáll, az Office 365 felügyeleti portálján és az Azure Active Directory.

A **munkaterület beállításainak** a felügyeleti portálon, a rendszergazdák a létrehozás munkaterületek (új munkaterületi felhasználói élményt), hogy mindenki vagy senki sem a szervezeten belüli beállítást segítségével hozhat létre új munkaterület élmény munkaterületek. Korlátozhatják is meghatározott biztonsági csoportok tagjaira a létrehozást.

> [!NOTE]
> A létrehozás munkaterületek (új munkaterületi felhasználói élményt) beállítás alapértelmezett értéke csak engedélyezése a felhasználóknak, akik létrehozhatnak az Office 365-csoportokat hozhat létre az új munkaterületek a Power bi-ban. Mindenképpen adja meg annak biztosítása érdekében a megfelelő felhasználók hozhatnak létre a új munkaterületi felhasználói élményt munkaterületeket a Power BI felügyeleti portáljához.

![Munkaterület-beállítások a felügyeleti portálon](media/service-new-workspaces/power-bi-workspace-admin-settings.png)

A [munkaterületek listája érhető el](service-admin-portal.md#workspaces) a Power BI felügyeleti portálon. 

![Munkaterületek listája](media/service-admin-portal/workspaces-list.png)

## <a name="new-workspaces-side-by-side-with-classic-workspaces"></a>Új munkaterületek egymás mellett a klasszikus munkaterületek

Új, frissített munkaterületek és klasszikus meglévő munkaterületek létezhet párhuzamosan, és akár hozhat létre. Az új munkaterületi felhasználói felület nem alapértelmezett munkaterületen típusú. Power bi-ban továbbra is megjeleníti az összes Office 365-csoportok a felhasználó tagja, ne módosítsa a meglévő munkafolyamatokba a Power BI-ban. Ismerje meg, hogyan hozhat létre egy új munkaterületet, olvassa el [hozzon létre új munkaterületek](service-create-the-new-workspaces.md). Ismerje meg, hogyan hozhat létre klasszikus munkaterületet, olvassa el [létrehozása a klasszikus munkaterületek](service-create-workspaces.md).

## <a name="roles-in-the-new-workspaces"></a>Az új munkaterületek szerepkörei

Hozzáférést biztosít egy új munkaterületet, adja hozzá felhasználói csoportoknak vagy személyeknek a munkaterület szerepkörök egyikét: Rendszergazdák, közreműködő vagy tagok. A meghatározott szerepkört a felhasználói csoport minden tagja megkapja. Ha egyéni több felhasználói csoportot, a legmagasabb szintű hozzá vannak rendelve a szerepkörök által biztosított engedélyt kapnak.

A szerepkörökkel kezelheti, hogy mely felhasználók milyen műveleteket végezhetnek a munkaterületeken, így elősegítheti a csapatok együttműködését. Az új munkaterületekkel szerepköröket rendelhet egyénekhez és felhasználói csoportokhoz: biztonsági csoportokhoz, Office 365-csoportokhoz és terjesztési listákhoz. 

Szerepkörök felhasználói csoportokhoz való hozzárendelésekor a csoport felhasználói hozzáférnek a tartalomhoz. Ha beágyaz felhasználói csoportokat, minden tag jogosultságot kap. Azok a felhasználók, akik több, különböző szerepkörrel rendelkező felhasználói csoport tagjai is, a legmagasabb szintű jogosultságot kapják. 

Az új munkaterületek három szerepkört kínálnak: rendszergazdák, tagok és közreműködők.

|Képesség   | Rendszergazda  | Tag  | Közreműködő  | 
|---|---|---|---|
| Frissíthetik és törölhetik a munkaterületet.  | X  |   |   |
| Hozzáadhatnak és eltávolíthatnak felhasználókat, így más rendszergazdákat is.  | X  |   |   |
| Tagokat vagy alacsonyabb jogosultsággal rendelkezőket adhatnak hozzá.  |  X | X  |   |
| Alkalmazást tehetnek közzé és frissíthetnek. |  X | X  |   |
| Elemeket vagy alkalmazásokat oszthatnak meg. |  X | X  |   |
| Engedélyezhetik másoknak az elemek újbóli megosztását. |  X | X  |   |
| Létrehozhatnak, szerkeszthetnek és törölhetnek tartalmakat a munkaterületen.  |  X | X  | X  |
| Közzétehetnek jelentéseket a munkaterületen, és törölhetnek tartalmakat. |  X | X  | X  |
 
 
## <a name="licensing"></a>Licencelés
A munkaterületekhez adott tagoknak Power BI Pro-licencre van szüksége. A munkaterületen a felhasználók együttműködhetnek az irányítópultokon és jelentéseken, amelyeket a szélesebb közönség vagy akár a teljes vállalat elé szeretne tárni. Ha másokkal is megszeretné osztani a tartalmat a szervezeten belül, rendeljen hozzájuk Power BI Pro-licencet, vagy helyezze a munkaterületet egy Power BI Prémium szintű kapacitásba.

> [!NOTE]
> Új munkaterületi felhasználói felületre a jelentéseket közzétevő szigorúbb kényszerítési meglévő tartozik szabályokkal licencelési. Felhasználók, akik a Power BI Desktop vagy a más ügyfelek közzététele a Pro-licenc nélküli eszközök tekintse meg a hiba "a Power BI Pro-licencek csak felhasználók tehetnek közzé a munkaterületre."

## <a name="how-are-the-new-workspaces-different-from-current-workspaces"></a>Miben különböznek az új munkaterületek a jelenlegi munkaterületektől?

Az új munkaterületekkel újraterveztünk néhány funkciót. Az alábbiakban a módosítások véglegesen várható. 

* Ezek a munkaterületek létrehozása Office 365-csoportokat, hajtsa végre a klasszikus munkaterületek nem hozza létre. Hozzáférést biztosít a felhasználóknak a munkaterülethez, ha hozzárendeli egy szerepkörhöz, azonban az Office 365-csoportot mostantól használhatja. 
* A klasszikus munkaterületeken is hozzáadhat egyéni felhasználók számára csak a tagok és rendszergazdák listájára. Az új munkaterületeken több AD biztonsági csoportot, terjesztési listát vagy Office 365-csoportot vehet fel ezekre a listákra, így könnyebben kezelheti a felhasználókat. 
- Egy klasszikus munkaterületről hozhat létre egy szervezeti tartalomcsomagot. Az új munkaterületen ezt nem teheti meg.
- Szervezeti tartalomcsomag klasszikus munkaterületről használhatja fel. Az új munkaterületen ezt nem teheti meg.

## <a name="workspace-contact-list"></a>Ismerősök listájának munkaterület
Az új **ügyfél lista** funkció lehetővé teszi, hogy adja meg, hogy mely felhasználók értesítés a munkaterületen előforduló problémákról. Alapértelmezés szerint minden olyan felhasználó vagy csoport a megadott munkaterületként rendszergazda értesítést kap, de testre szabhatja a listában. Felhasználók vagy csoportok, a kapcsolattartási listában felsorolt megjelenik a felhasználói felületen (UI) segítségével a munkaterülethez kapcsolódó felhasználók segítséget. 

Tudjon meg többet a [beállítása a munkaterület névjegylista](service-create-the-new-workspaces.md#workspace-contact-list).

## <a name="workspace-onedrive"></a>Munkaterület onedrive vállalati verzió
A munkaterület OneDrive funkcióval konfigurálja az Office 365-csoportot, amelynek SharePoint-dokumentumtárban fájltároló munkaterület felhasználók számára érhető el. A csoportot kell létrehozni a Power BI-on kívül. 

A Power BI engedélyeit a felhasználók vagy csoportok, akiknek vannak konfigurálva az Office 365-csoport tagsággal rendelkező munkaterület-hozzáférés nem szinkronizálja. Az ajánlott eljárás, hogy az azonos Office 365-csoport amelynek ezt a beállítást konfigurálja a file storage használatával munkaterület-hozzáférés kezelése. 

Megtudhatja, hogyan lehet a [állítsa be, és a munkaterület onedrive vállalati verzió eléréséhez](service-create-the-new-workspaces.md#workspace-onedrive).  
   
## <a name="auditing"></a>Naplózás
A következő tevékenységeket a Power BI által az új munkaterületi felhasználói élményt munkaterületekhez naplóz.

| Felhasználóbarát név |   Művelet neve |
|---|---|
| Power BI-mappa létrehozása | CreateFolder (Mappa létrehozása) |
| Power BI-mappa törlése | DeleteFolder (Mappa törlése) |
| Power BI-mappa frissítése | UpdateFolder (Mappa frissítése) |
| Power BI-mappahozzáférés frissítése| UpdateFolderAccess (Mappahozzáférés frissítése) |

Tudjon meg többet [Power BI-naplózás](service-admin-auditing.md#activities-audited-by-power-bi).

## <a name="limitations-and-considerations"></a>Korlátozások és szempontok

Figyelembe veendő korlátozások:

- Egy munkaterület legfeljebb 1000 adathalmazt, vagy adathalmazonként 1000 jelentést tartalmazhat. 
- A Power BI Pro-licenccel rendelkező személy egy legfeljebb 1000 munkaterületek tagja lehet.
- Excelhez készült Power BI publisher nem támogatott.

## <a name="workspace-features-that-work-differently"></a>A munkaterületek másképp működő funkciói

A jelenlegi munkaterületek egyes funkciói másképp működnek, mint az új munkaterületeké. Ezek a különbségek szándékosak legyenek, hogy ügyfelektől érkezett, és engedélyezze a munkaterületek együttműködést rugalmasabb módszer visszajelzései alapján:

- Licencelés kényszerítése: Új munkaterületi felhasználói felületre a jelentéseket közzétevő kényszeríti a meglévő licencelési szabályokat, amelyek Power BI Pro-licenc szükséges a felhasználók számára a munkaterületeken együttműködés vagy a tartalommegosztás másoknak a Power BI szolgáltatásban. Pro-licenccel nem rendelkező felhasználók tekintse meg a hiba "Powre BI Pro licenccel rendelkező csak felhasználók tehetnek közzé a munkaterületre."
- A tagok újbóli megosztási jogosultsága: ennek helyét a Közreműködő szerepkör vette át
- Csak olvasható munkaterületek: Ahelyett, hogy csak olvasási hozzáférést adna a felhasználóknak, hozzárendelheti őket a soron következő megtekintő szerepkörhöz, amely hasonló, csak olvasási hozzáférést biztosít a munkaterületen lévő tartalomhoz.
- Nincs **Kilépés a munkaterületből** gomb.

## <a name="frequently-asked-questions"></a>Gyakori kérdések

**Hatással az új munkaterület meglévő tartalmakra mutató hivatkozásokat élmény általánosan elérhető**

Nem. Meglévő elem a klasszikus munkaterületeken mutató hivatkozásokat az új munkaterületi felhasználói felület nem érinti. Az általánosan elérhető (GA) az új munkaterületi felhasználói felület módosítja az alapértelmezett munkaterületre, hozzon létre, de nem módosítja a meglévő munkaterületek. 

**A meglévő munkaterületek frissítve az új munkaterületi felhasználói felületre a végleges Verzióban**

Nem. Az új munkaterületi felhasználói élményt általánosan elérhető az új munkaterületi felhasználói felület csak módosítja az alapértelmezett munkaterület-típus. Office 365-csoportokra épülő meglévő klasszikus munkaterületek változatlan marad.

**Munkaterületek továbbra is automatikusan létrejönnek az Office 365-csoportokat**

Igen. Mivel támogatjuk a munkaterületek egymás mellett mindkét típusú, továbbra is listázhatja az összes Office 365-csoportok a felhasználónak hozzáférése van a munkaterületek listájában.

## <a name="next-steps"></a>Következő lépések
* [Az új munkaterületek létrehozása a Power bi-ban](service-create-the-new-workspaces.md)
* [A klasszikus munkaterületek létrehozása](service-create-workspaces.md)
* [Alkalmazások telepítése és használata a Power BI-ban](service-create-distribute-apps.md)
* Kérdése van? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
