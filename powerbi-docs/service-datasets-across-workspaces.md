---
title: Adathalmazok használata több munkaterületen (előzetes verzió) – bevezetés
description: Útmutató adathalmaz megosztásához a vállalat több felhasználójával. Így mind jelentéseket készíthetnek az Ön adathalmaza alapján a saját munkaterületükön.
author: maggiesMSFT
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/01/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d30a8012161934ada4ff3cb2ce6852fe62f48892
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73877199"
---
# <a name="intro-to-datasets-across-workspaces-preview"></a>Adathalmazok használata több munkaterületen (előzetes verzió) – bevezetés

Az üzleti intelligencia együttműködésen alapuló tevékenység. Fontos az egységes adathalmazok létrehozása, amelyek „egyetlen információforrásaként” használhatók. Lényeges, hogy ez után ezeket a szabványosított adathalmazokat fedezze fel és hasznosítsa újra. Ha vállalata adatmodellező szakértői optimalizált adathalmazokat hoznak létre és osztanak meg, a jelentéskészítők ezekből az adathalmazokból kiindulva pontos jelentéseket készíthetnek. Így a vállalat egységes adatok alapján hozhat döntéseket, és megfelelő adatkultúrával fog rendelkezni.

![Megosztott adatkészlet kiválasztása](media/service-datasets-across-workspaces/power-bi-select-shared-dataset.png)

A Power BI-ban az adathalmazok létrehozói az [összeállítási engedély](service-datasets-build-permissions.md) használatával szabályozhatják, hogy ki férhet hozzá az adataikhoz. Az adathalmazok létrehozói ezen kívül *minősíthetik* vagy *meghirdethetik* az adathalmazokat, hogy mások felfedezhessék azokat. A jelentéskészítők ez alapján tudhatják, hogy melyek a jó minőségű és hivatalos adathalmazok, és ezeket használhatják mindahhoz, amit a Power BI-ban készítenek. A bérlői rendszergazdák egy új bérlői beállítással [szabályozhatják az adathalmazok több munkaterületen való felhasználását](service-datasets-admin-across-workspaces.md).

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

Összeállítási engedélytípussal egy adathalmaz létrehozójaként meghatározhatja, hogy a vállalatnál ki készíthet új tartalmat az adathalmazok alapján. Az Összeállítási engedéllyel rendelkezők az adathalmazból a Power BI-on kívül, például Excel-munkalapokon is készíthetnek új tartalmat az Elemzés az Excelben funkció, az XMLA és az exportálás használatával. További információ: [Összeállítási engedély](service-datasets-build-permissions.md).

## <a name="promotion-and-certification"></a>Meghirdetés és minősítés

Ha adathalmazokat hoz létre, és olyat készít, amelynek mások is hasznát vehetik, egyszerűbbé teheti annak felfedezését, ha [meghirdeti](service-datasets-promote.md). Azt is kérheti, hogy a vállalati szakértők [minősítsék adathalmazát](service-datasets-certify.md).

## <a name="licensing"></a>Licencelés

A megosztott adathalmazokkal kapcsolatos képességekre épülő funkciók és felületek azok meglévő felhasználási helyzete alapján vannak licencelve. Például:

- A megosztott adathalmazok felfedezése és az azokhoz való csatlakozás általában mindenki számára elérhető – az a szolgáltatás nincs a Prémium szintre korlátozva.
- A Pro-licenccel nem rendelkező felhasználók csak akkor használhatnak más munkaterületen lévő adathalmazokat jelentéskészítéshez, ha ezek az adathalmazok a felhasználó személyes Saját munkaterületén, vagy Prémium-szintű munkaterületen vannak. Ugyanez a licencelési korlátozás a Power BI Desktopban és a Power BI szolgáltatásban készülő jelentésekre is érvényes.
- Jelentések munkaterületek közötti másolásához Pro-licenc szükséges.
- Jelentéseknek egy alkalmazásból való másolásához a vállalati tartalomcsomagok követelményeinek megfelelően Pro-licenc szükséges.
- Adathalmazok meghirdetéséhez és minősítéséhez Pro-licenc szükséges.

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások

- Alkalmazás-közzétevőként gondoskodnia kell arról, hogy a célközönsége hozzáférjen a munkaterületen kívüli adathalmazokhoz. Ellenkező esetben a felhasználók problémákba ütköznek az alkalmazás használata során: az adathalmazokhoz való hozzáférés hiányában a jelentések nem nyílnak meg, az irányítópultok csempéi pedig zároltként jelennek meg. Ha a navigáció kezdőeleme egy jelentés, akkor az adathalmazhoz való hozzáférés nélkül a felhasználók az alkalmazást sem tudják megnyitni.
- Más munkaterületen lévő adathalmazra alapozott jelentés készítéséhez mindkét oldalon az új munkaterületi felhasználói felület szükséges: A jelentésnek új munkaterületi felületen kell lennie, és az adathalmaznak is új munkaterületi felületen kell lennie.
- Klasszikus munkaterületen az adathalmaz-felfedezési felületen csak az azon a munkaterületen lévő adathalmazok jelennek meg.
- A „Webes közzététel” megosztott adathalmazokon alapuló jelentések esetén szándékosan nem használható.
- Ha ketten olyan munkaterület tagjai, amely hozzáfér egy megosztott adathalmazhoz, akkor előfordulhat, hogy csak az egyikük látja a kapcsolódó adathalmazt a munkaterületen. A megosztott adathalmazt csak azok látják, akik legalább Olvasási hozzáféréssel rendelkeznek az adathalmazhoz. 

## <a name="next-steps"></a>Következő lépések

- [Adathalmazok meghirdetése](service-datasets-promote.md)
- [Adathalmazok minősítése](service-datasets-certify.md)
- [Adathalmazok több munkaterületen való használatának irányítása](service-datasets-admin-across-workspaces.md)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
