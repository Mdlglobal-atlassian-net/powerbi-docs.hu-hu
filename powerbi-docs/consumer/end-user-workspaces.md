---
title: A tartalom elrendezése a munkaterületeken
description: A munkaterületek és a munkaterületi szerepkörök ismertetése
author: mihart
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/22/2020
ms.author: mihart
LocalizationGroup: Consumers
ms.openlocfilehash: 801b5cf5400bbe1cc0487eef596ea3d1cdc5fb1e
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82120169"
---
# <a name="collaborate-in-workspaces"></a>Együttműködés a munkaterületeken

 A *munkaterületek* olyan helyek, ahol lehetséges a munkatársakkal való együttműködés egy adott tartalommal kapcsolatban. A munkaterületeket a Power BI *tervezői* hozzák létre az irányítópultok és jelentések gyűjteményeinek tárolására. Egy ilyen gyűjteményt a tervező később egy *alkalmazásba* csomagolhat, és terjesztheti azt a teljes szervezetben vagy meghatározott személyek és csoportok számára. 

 A Power BI-szolgáltatás minden felhasználója rendelkezik egy **Saját munkaterülettel** is.  A Saját munkaterület egy személyes tesztkörnyezet, amelyben önmagának hozhat létre tartalmat.

 Munkaterületeit a Power BI **Kezdőlapján**, vagy a bal oldali navigációs panel **Munkaterületek** vagy **Saját munkaterület** lehetőségét választva tekintheti meg.

 ![kétféle munkaterületet mutató navigációs panel](media/end-user-workspaces/power-bi-home.png)

## <a name="types-of-workspaces"></a>Munkaterület-típusok
Az összes tartalom, amellyel Ön rendelkezik vagy amelyet Ön hozott létre a **Saját munkaterületen** található. Tekintsen rá úgy mint a saját, személyes munkaterületére, ahol nyugodtan kísérletezhet tartalmaival. Sok Power BI-*fogyasztó* esetén azonban a **Saját munkaterület** üres marad, mert a feladata nem jár új tartalom létrehozásával. A *fogyasztók*, ahogy a neve is mutatja, „fogyasztják” a mások által létrehozott tartalmat, és ezeket az adatokat üzleti döntésekhez használják fel. Ha Ön létrehoz tartalmat, akkor inkább a [tervezők számára készült Power BI-cikkeket](../create-reports/index.yml) érdemes elolvasnia.

Az **alkalmazás-munkaterületek** a meghatározott alkalmazások tartalmait tartalmazzák. Amikor egy *tervező* létrehoz egy alkalmazást, akkor az alkalmazás használatához szükséges összes tartalmat egybecsomagolja. A tartalomban irányítópultok, jelentések és adathalmazok szerepelhetnek. Nem minden alkalmazás tartalmazza azonban mindhármat. Van olyan alkalmazás, amely csak egy irányítópultot tartalmaz, de olyan is, amelyben minden típusból három van, de akár olyan is, amely húsz jelentést tartalmaz. Mindez attól függ, hogy a *tervező* mit csomagolt be az alkalmazásba. A *fogyasztók* alkalmazás-munkaterületei általában nem tartalmazzák az adathalmazokat.

A Fig sales alkalmazás alábbi munkaterületén három jelentés és egy irányítópult látható. 

![kétféle munkaterületet mutató navigációs panel](media/end-user-workspaces/power-bi-app-workspace.png)

## <a name="roles-in-the-workspaces"></a>A munkaterületeken elérhető szerepkörök

A szerepkörök határozzák meg, milyen műveletek végezhetők el egy munkaterületen, ami elősegítheti a csapatok együttműködését.  Új munkaterülethez való hozzáférés engedélyezésekor a *tervezők* hozzáadják az egyes felhasználókat vagy csoportokat a munkaterület egyik szerepköréhez: **Megtekintő**, **Tag**, **Közreműködő** vagy **Rendszergazda**. 


Power BI-*felhasználóként* Ön általában a **Megtekintő** szerepkörben létesít interakciót a különböző munkaterületeken. Egy *tervező* azonban a **Tag** vagy a **Közreműködő** szerepkörhöz is hozzárendelheti Önt. A Megtekintő szerepkör lehetővé teszi az olyan tartalom (irányítópultok, jelentések, alkalmazások) megtekintését és kezelését, amelyet mások hoztak létre és osztottak meg Önnel. Mivel a Megtekintő szerepkör nem fér hozzá a mögöttes adathalmazhoz, biztonságos módot kínál a tartalom kezelésére, és nem kell attól tartania, hogy „kárt tesz” a mögöttes adatokban.


A Megtekintő szerepkörrel rendelkező *fogyasztóként* végrehajtható tevékenységek részletes listáját a [Fogyasztóknak kínált Power BI-funkciók](end-user-features.md) című cikk tartalmazza.


### <a name="workspace-roles"></a>Munkaterületi szerepkörök
A négy szerepkör (rendszergazdák, tagok, közreműködők és megtekintők) képességei a következők: Ezekhez a képességekhez a megtekintés és a használat kivételével Power BI Pro-licenc szükséges.

|Képesség   | Rendszergazda  | Tag  | Közreműködő  | Megtekintő |
|---|---|---|---|---|
| Frissíthetik és törölhetik a munkaterületet.  | X  |   |   |   | 
| Hozzáadhatnak és eltávolíthatnak felhasználókat, így más rendszergazdákat is.  | X  |   |   |   |
| Tagokat vagy alacsonyabb jogosultsággal rendelkezőket adhatnak hozzá.  |  X | X  |   |   |
| Alkalmazást tehetnek közzé és frissíthetnek. |  X | X  |   |   |
| Elem vagy alkalmazás megosztása.<sup>1</sup> |  X | X  |   |   |
| Engedélyezhetik másoknak az elemek újbóli megosztását.<sup>1</sup> |  X | X  |   |   |
| Alkalmazások szerepeltetése munkatársak kezdőlapján |  X | X  |   |   |
| Irányítópultok és jelentések szerepeltetése munkatársak kezdőlapján |  X | X  | X |   |
| Létrehozhatnak, szerkeszthetnek és törölhetnek tartalmakat a munkaterületen.  |  X | X  | X  |   |
| Közzétehetnek jelentéseket a munkaterületen, és törölhetnek tartalmakat.  |  X | X  | X  |   |
| Jelentést hozhatnak létre másik munkaterületen egy ezen a munkaterületen lévő adathalmaz alapján.<sup>1</sup> |  X | X  | X  |   |
| Jelentés másolása. | X | X | X |  |
| Egy elem megtekintése és kezelése.<sup>2</sup> |  X | X  | X  | X  |
| A munkaterület adatfolyamaiban tárolt információk beolvasása | X | X | X | X |

1. A közreműködők és a tagok megoszthatnak elemeket egy munkaterületen, ha rendelkeznek újramegosztási engedélyekkel.

2. A Power BI szolgáltatás elemeit Power BI Pro licenc nélkül is megtekintheti és kezelheti, ha az elemek egy prémium szintű munkaterületen vannak.

## <a name="licensing-workspaces-and-capacity"></a>Licencelés, munkaterületek és kapacitás
A licencelés szerepet játszik annak meghatározásában, milyen műveleteket lehet végezni a munkaterületen. Sok funkcióhoz szükséges, hogy a felhasználó Power BI *Pro* licenccel rendelkezzen. A *fogyasztók* többsége *ingyenes* licenccel dolgozik. 

Ha Ön ingyenes licenccel rendelkezik, és a munkaterület *prémium szintű kapacitásban* van tárolva, akkor megtekintheti és kezelheti az ezen a munkaterületen lévő tartalmat. A prémium szintű kapacitásban tárolt munkaterületeket és alkalmazásokat egy gyémánt ikon jelöli.

![Kijelölt munkaterületek](media/end-user-workspaces/power-bi-diamond.png) További tudnivalók: [Milyen licencem van?](end-user-license.md).



## <a name="next-steps"></a>Következő lépések
* [Alkalmazások a Power BI-ban](end-user-apps.md)    

* Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

