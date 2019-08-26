---
title: Adathalmazok használata több munkaterületen (előzetes verzió) – bevezetés
description: Útmutató adathalmaz megosztásához a vállalat több felhasználójával. Így mind jelentéseket készíthetnek az Ön adathalmaza alapján a saját munkaterületükön.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/15/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 258dd735c5ba97122d9e93f888e65cf2030f01eb
ms.sourcegitcommit: 4d5166944fcc6fe4666cab055ae75e7a0a77866d
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69530478"
---
# <a name="intro-to-datasets-across-workspaces-preview"></a>Adathalmazok használata több munkaterületen (előzetes verzió) – bevezetés

Az üzleti intelligencia együttműködésen alapuló tevékenység. Fontos az egységes adathalmazok létrehozása, amelyek „egyetlen információforrásaként” használhatók. Lényeges, hogy ez után ezeket a szabványosított adathalmazokat fedezze fel és hasznosítsa újra. Ha vállalata adatmodellező szakértői optimalizált adathalmazokat hoznak létre és osztanak meg, a jelentéskészítők ezekből az adathalmazokból kiindulva pontos jelentéseket készíthetnek. Így a vállalat egységes adatok alapján hozhat döntéseket, és megfelelő adatkultúrával fog rendelkezni.

![Megosztott adatkészlet kiválasztása](media/service-datasets-across-workspaces/power-bi-select-shared-dataset.png)

A Power BI-ban az adathalmazok létrehozói az [összeállítási engedély](service-datasets-build-permissions.md#build-permissions-for-shared-datasets) használatával szabályozhatják, hogy ki férhet hozzá az adataikhoz. Az adathalmazok létrehozói ezen kívül *minősíthetik* vagy *meghirdethetik* az adathalmazokat, hogy mások felfedezhessék azokat. A jelentéskészítők ez alapján tudhatják, hogy melyek a jó minőségű és hivatalos adathalmazok, és ezeket használhatják mindahhoz, amit a Power BI-ban készítenek. A bérlői rendszergazdák egy új bérlői beállítással [szabályozhatják az adathalmazok több munkaterületen való felhasználását](service-datasets-admin-across-workspaces.md).

## <a name="dataset-sharing-and-the-new-workspace-experience"></a>Adathalmazok megosztása és az új munkaterületi felhasználói felület

Az adathalmazokon alapuló jelentések különböző munkaterületeken végzett készítése és a jelentések munkaterületek közötti másolása szorosan összefügg az [új munkaterületi felhasználói felülettel](service-create-the-new-workspaces.md):

- Amikor új munkaterületi felületen nyit meg adathalmaz-katalógust a szolgáltatásban, ebben a katalógusban csak a saját munkaterületén és más új felületű munkaterületeken lévő adathalmazok jelennek meg. 
- Ha az adathalmaz-katalógust klasszikus munkaterületről nyitja meg, csak az azon a munkaterületen lévő adathalmazok jelennek meg, a más munkaterületeken lévők nem.
- Élő tartalmú jelentéseket tehet közzé a Power BI Desktopban, ha azok adathalmazai új felületű munkaterületeken vannak.
- Jelentések munkaterületek közötti másolásakor a célmunkaterületnek új felületű munkaterületnek kell lennie.

## <a name="discover-datasets-preview"></a>Adathalmazok felfedezése (előzetes verzió)

Amikor meglévő adathalmazból készít jelentést, az első lépés az adathalmazhoz való csatlakozás a Power BI szolgáltatásban vagy a Power BI Desktopban. További információ [adathalmazok különböző munkaterületekről való felfedezéséről (előzetes verzió)](service-datasets-discover-across-workspaces.md)

## <a name="copy-a-report"></a>Jelentés másolása

Ha egy munkaterületen vagy alkalmazásban Önnek megfelelő jelentést talál, másolatot készíthet róla, amelyet igényeinek megfelelően módosíthat. Az adatmodell elkészítésével nem kell foglalkoznia. Azt már létrehozták az Ön számára. Egy meglévő jelentést ráadásul sokkal egyszerűbb módosítani, mint egy üresből kiindulni. További információ [jelentések másolásáról](service-datasets-copy-reports.md).

## <a name="build-permission-for-datasets"></a>Összeállítási engedély adathalmazokhoz

Az összeállítási engedélytípussal egy adathalmaz létrehozójaként meghatározhatja, hogy a vállalatnál ki készíthet új tartalmat az adathalmazok alapján. Az összeállítási engedéllyel rendelkezők az adathalmazból a Power BI-on kívül, például Excel-munkalapokon is készíthetnek új tartalmat az Elemzés az Excelben funkció, az XMLA és az exportálás használatával. További információ: [Összeállítási engedély](service-datasets-build-permissions.md#build-permissions-for-shared-datasets).

## <a name="promotion-and-certification"></a>Meghirdetés és minősítés

Ha adathalmazokat hoz létre, és olyat készít, amelynek mások is hasznát vehetik, egyszerűbbé teheti annak felfedezését, ha [meghirdeti](service-datasets-promote.md). Azt is kérheti, hogy a vállalati szakértők [minősítsék adathalmazát](service-datasets-certify.md).

## <a name="licensing"></a>Licencelés

A megosztott adathalmazokkal kapcsolatos képességekre épülő funkciók és felületek azok meglévő felhasználási helyzete alapján vannak licencelve. Például:

- A megosztott adathalmazok felfedezése és az azokhoz való csatlakozás általában mindenki számára elérhető. Pro-licenccel nem rendelkező felhasználók azonban csak a saját munkaterületükön lévő adathalmazokhoz csatlakozhatnak.
- A Power BI Desktopban a Pro-licenccel nem rendelkező felhasználók csak a saját munkaterületükön lévő adathalmazokat láthatják.
- Jelentések munkaterületek közötti másolásához Pro-licenc szükséges.
- Jelentéseknek egy alkalmazásból való másolásához a vállalati tartalomcsomagok követelményeinek megfelelően Pro-licenc szükséges.
- Adathalmazok meghirdetéséhez és minősítéséhez Pro-licenc szükséges.

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások

- Más munkaterületen lévő adathalmazra alapozott jelentés készítéséhez mindkét oldalon az új munkaterületi felhasználói felület szükséges: A jelentésnek új munkaterületi felületen kell lennie, és az adathalmaznak is új munkaterületi felületen kell lennie.
- Tegyük fel, hogy az A munkaterületen hoz létre egy jelentést egy B munkaterületen lévő adathalmaz alapján. Ha alkalmazást hoz létre az A munkaterülethez, a jelentést csak akkor foglalhatja bele az A munkaterületi alkalmazásba, ha Ön a B munkaterületnek is tagja.
- Klasszikus munkaterületen az adathalmaz-felfedezési felületen csak az azon a munkaterületen lévő adathalmazok jelennek meg.
- Ha megosztott adathalmazon alapuló jelentést szeretne hozzáadni egy alkalmazáshoz, akkor tagnak kell lennie az adathalmaz munkaterületén. Ez ismert probléma.
- A „Webes közzététel” megosztott adathalmazokon alapuló jelentések esetén nem használható. Ez szándékos.
- Ha ketten olyan munkaterület tagjai, amely hozzáfér egy megosztott adathalmazhoz, akkor előfordulhat, hogy csak az egyikük látja a kapcsolódó adathalmazt a munkaterületen. A megosztott adathalmazt csak azok látják, akik legalább Olvasási hozzáféréssel rendelkeznek az adathalmazhoz. 

## <a name="next-steps"></a>Következő lépések

- [Adathalmazok meghirdetése](service-datasets-promote.md)
- [Adathalmazok minősítése](service-datasets-certify.md)
- [Adathalmazok több munkaterületen való használatának irányítása](service-datasets-admin-across-workspaces.md)
- Kérdése van? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
