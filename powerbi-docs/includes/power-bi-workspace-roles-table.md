---
title: Power BI-munkaterületi szerepkörök
description: Power BI-munkaterületi szerepkörök táblázata
services: powerbi
author: maggiesMSFT
ms.service: powerbi
ms.topic: include
ms.date: 04/23/2020
ms.author: maggies
ms.custom: include file
ms.openlocfilehash: 5ed3a65f1ef65640c76ada765931a85714aad3af
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82781350"
---
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
| Jelentés másolása.<sup>2</sup> | X | X | X |  |
| Adatfrissítések ütemezése helyszíni átjárón keresztül.<sup>3</sup> | X | X | X |  |
| Átjárókapcsolat beállításainak módosítása.<sup>3</sup> | X | X | X |  |
| Egy elem megtekintése és kezelése.<sup>4</sup> |  X | X  | X  | X  |
| A munkaterület adatfolyamaiban tárolt információk beolvasása | X | X | X | X |

1. A közreműködők és a megtekintők megoszthatnak elemeket egy munkaterületen, ha rendelkeznek újramegosztási engedélyekkel.
2. Ha jelentést szeretne másolni, és ha egy másik munkaterületen szeretne jelentést létrehozni az ezen a munkaterületen található adathalmaz alapján, akkor az adathalmazra vonatkozó Összeállítási engedéllyel kell rendelkeznie. Az ezen a munkaterületben lévő adathalmazok esetén a rendszergazda, tag és közreműködő szerepkörök rendelkeznek összeállítási engedéllyel a munkaterület-szerepkörük részeként.
3. Ne feledje, hogy az átjárón is engedélyekre van szüksége. Ezeket az engedélyeket máshol kell kezelni, a munkaterület szerepköreitől és engedélyeitől függetlenül. További információ: [Helyszíni átjáró kezelése](https://docs.microsoft.com/data-integration/gateway/service-gateway-manage).
4. Ha még nem is rendelkezik Power BI Pro licenccel, akkor is megtekintheti és kezelheti a Power BI szolgáltatás elemeit, ha az elemek egy prémium szintű munkaterületen vannak.

