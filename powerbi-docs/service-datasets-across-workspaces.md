---
title: Adathalmazok használata több munkaterületen (előzetes verzió) – Power BI
description: Útmutató adathalmaz megosztásához a vállalat több felhasználójával. Így mind jelentéseket készíthetnek az Ön adathalmaza alapján a saját munkaterületükön.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/31/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: a5e4b41b36dfbf6cca14a348268b96eaad21b00e
ms.sourcegitcommit: 7c426a5209d4fdd1360fc3d0442d57991be1984d
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/03/2019
ms.locfileid: "66461856"
---
# <a name="use-datasets-across-workspaces-preview"></a>Adathalmazok használata több munkaterületen (előzetes verzió)

Az üzleti intelligencia együttműködésen alapuló tevékenység. Fontos az egységes adathalmazok létrehozása, amelyek „egyetlen információforrásaként” használhatók. Sok múlik az ilyen egységes adathalmazok megismerésén és ismételt felhasználásán. Ha vállalata adatmodellező szakértői optimalizált adathalmazokat hoznak létre és osztanak meg, a jelentéskészítők ezekből az adathalmazokból kiindulva pontos jelentéseket készíthetnek. Így a vállalat egységes adatok alapján hozhat döntéseket, és megfelelő adatkultúrával fog rendelkezni.

A Power BI egyszerűvé teszi az adathalmazok létrehozói számára az adathalmazok minősítését és megismertetését, hogy mások felfedezhessék azokat. A jelentéskészítők így minőségi, hivatalos adathalmazokra találhatnak, amelyeket bárhol felhasználhatnak a Power BI-ban. Az adathalmazok tulajdonosai az [összeállítási engedély](service-datasets-build-permissions.md#build-permissions-for-shared-datasets) használatával szabályozhatják, hogy ki férhet hozzá az adataikhoz. A bérlői rendszergazdák egy új bérlői beállítással [szabályozhatják az adathalmazok több munkaterületen való felhasználását](service-datasets-admin-across-workspaces.md).

## <a name="dataset-sharing-and-the-new-workspace-experience"></a>Adathalmazok megosztása és az új munkaterületi felhasználói felület

Az adathalmazokon alapuló jelentések különböző munkaterületeken végzett készítése és a jelentések munkaterületek közötti másolása szorosan összefügg az [új munkaterületi felhasználói felülettel](service-create-the-new-workspaces.md):

- Amikor új munkaterületi felületen nyit meg adathalmaz-katalógust a szolgáltatásban, ebben a katalógusban csak a saját munkaterületén és az új felületű munkaterületeken lévő adathalmazok jelennek meg. 
- Ha az adathalmaz-katalógust klasszikus munkaterületről nyitja meg, csak az azon a munkaterületen lévő adathalmazok jelennek meg, a más munkaterületeken lévők nem.
- Élő tartalmú jelentéseket tehet közzé a Desktopban, ha azok adathalmazai új felületű munkaterületeken vannak.
- Jelentések munkaterületek közötti másolásakor a célmunkaterületnek új felületű munkaterületnek kell lennie.

## <a name="build-permission-for-datasets"></a>Összeállítási engedély adathalmazokhoz

Az Összeállítás engedélytípussal vállalatán belül másoknak is engedélyezheti új tartalom, például jelentések, irányítópultok és Q&A-ból kitűzött csempék összeállítását egy meglévő adathalmaz alapján. Az adathalmazból a Power BI-on kívül, például Excel-munkalapokon is készíthetnek új tartalmat az Elemzés az Excelben funkció, az XMLA és az exportálás használatával. További információ: [Összeállítási engedély](service-datasets-build-permissions.md#build-permissions-for-shared-datasets).

## <a name="discover-datasets-preview"></a>Adathalmazok felfedezése (előzetes verzió)

Amikor meglévő adathalmazból készít jelentést, az első lépés az adathalmazhoz való csatlakozás a Power BI szolgáltatásban vagy a Power BI Desktopban. További információ [adathalmazok különböző munkaterületekről való felfedezéséről (előzetes verzió)](service-datasets-discover-across-workspaces.md)

## <a name="copy-a-report"></a>Jelentés másolása

Ha egy munkaterületen vagy alkalmazásban Önnek megfelelő jelentést talál, másolatot készíthet róla, amelyet igényeinek megfelelően módosíthat. Az adatmodell elkészítésével nem kell foglalkoznia. Azt már létrehozták az Ön számára. Egy meglévő jelentést ráadásul sokkal egyszerűbb módosítani, mint egy üresből kiindulni. További információ [jelentések másolásáról](service-datasets-copy-reports.md).

## <a name="promotion-and-certification"></a>Meghirdetés és minősítés

Ha adathalmazokat hoz létre, és olyat készít, amelynek mások is hasznát vehetik, egyszerűbbé teheti annak felfedezését, ha [meghirdeti](service-datasets-promote.md). Azt is kérheti, hogy a vállalati szakértők [minősítsék adathalmazát](service-datasets-certify.md).

## <a name="licensing"></a>Licencelés

A megosztott adathalmazokkal kapcsolatos képességekre épülő funkciók és felületek azok meglévő felhasználási helyzete alapján vannak licencelve.  Például:

- A megosztott adathalmazok felfedezése és az azokhoz való csatlakozás általában mindenki számára elérhető. Pro-licenccel nem rendelkező felhasználók azonban csak a saját munkaterületükön vagy prémium szintű munkaterületeken lévő adathalmazokhoz csatlakozhatnak.
- A személyes munkaterületeken kívüli adathalmazok meghirdetéséhez és minősítéséhez Pro-licenc szükséges, ugyanis csak Pro-licenc birtokában lehet tag egy alkalmazás-munkaterületen.
- A jelentések munkaterületek közötti másolásához Pro-licenc szükséges, szintén azért, mert csak Pro-licenc birtokában lehet tag egy alkalmazás-munkaterületen.
- Jelentéseknek egy alkalmazásból való másolásához a vállalati tartalomcsomagok követelményeinek megfelelően Pro-licenc szükséges.

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások

- Más munkaterületen lévő adathalmazra alapozott jelentés készítéséhez mindkét oldalon az új munkaterületi felhasználói felület szükséges: A jelentésnek új munkaterületi felületen kell lennie, és az adathalmaznak is új munkaterületi felületen kell lennie.
- Klasszikus munkaterületen az adathalmaz-felfedezési felületen csak az azon a munkaterületen lévő adathalmazok jelennek meg.
- Egy alkalmazás-munkaterületen készíthet más munkaterületen lévő adathalmazon alapuló jelentéseket. Nem készíthet azonban alkalmazást az ezeket az adathalmazokat tartalmazó munkaterülethez.
- Az ingyenes Desktop-felhasználók csak a saját munkaterületen lévő és a Premium-alapú munkaterületekről származó adathalmazokat látják.
- Ha megosztott adathalmazon alapuló jelentést szeretne hozzáadni egy alkalmazáshoz, akkor tagnak kell lennie az adathalmaz munkaterületén. Ez ismert probléma.
- A „Webes közzététel” megosztott adathalmazokon alapuló jelentések esetén nem használható. Ez szándékos.
- Ha ketten olyan munkaterület tagjai, amely hozzáfér egy megosztott adathalmazhoz, akkor előfordulhat, hogy csak az egyikük látja a kapcsolódó adathalmazt a munkaterületen. A megosztott adathalmazt csak azok látják, akik legalább Olvasási hozzáféréssel rendelkeznek az adathalmazhoz. 

## <a name="next-steps"></a>Következő lépések

- [Adathalmazok meghirdetése](service-datasets-promote.md)
- [Adathalmazok minősítése](service-datasets-certify.md)
- [Adathalmazok több munkaterületen való használatának irányítása](service-datasets-admin-across-workspaces.md)
- Kérdése van? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
