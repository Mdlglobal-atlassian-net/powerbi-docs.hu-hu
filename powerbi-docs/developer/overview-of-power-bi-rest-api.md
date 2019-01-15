---
title: Mire használhatom a Power BI API-t?
description: Mire használhatom a Power BI API-t?
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 05/25/2018
ms.author: maghan
ms.openlocfilehash: 84e43f67c78949139ec856ef8ac770555fc6bd96
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54282701"
---
# <a name="what-can-developers-do-with-the-power-bi-api"></a>Mire használhatják a fejlesztők a Power BI API-t?

A Power BI interaktív irányítópultokat jelenít meg, amelyek valós időben hozhatók létre és frissíthetők számos különböző adatforrásból. Bármilyen, REST-hívásokat támogató programnyelv használatával létrehozhat olyan alkalmazásokat, amelyek valós időben integrálhatók a Power BI-irányítópultokkal. Az alkalmazásokba Power BI-csempéket és jelentéseket is integrálhat.

A fejlesztők létrehozhatnak saját adatmegjelenítéseket is, amelyek az interaktív jelentésekben és irányítópultokon használhatók.

Íme néhány, a Power BI API-k használatával elvégezhető feladat.

| **Feladat** | **Leírás** |
| --- | --- |
| Irányítópultok, jelentések és csempék beágyazása Power BI- és nem Power BI-felhasználók részére (alkalmazás tulajdonában lévő adatok) |[Power BI-irányítópultok, -jelentések és -csempék beágyazása](embedding-content.md) |
| Kulcsfontosságú adatok küldése Power BI-irányítópultokra a meglévő üzleti munkafolyamatok kiterjesztésével. |[Adatok küldése az irányítópultokra](walkthrough-push-data.md) |
| Hitelesítés a Power BI-ban. |[Hitelesítés a Power BI-ban](get-azuread-access-token.md) |
| Egyéni vizualizáció létrehozása. |[Egyéni Power BI-vizualizáció fejlesztése](custom-visual-develop-tutorial.md) |

> [!NOTE]
> A Power BI API-k továbbra is csoportokként hivatkoznak az alkalmazás-munkaterületekre. Bármely csoportokra való utalás alkalmazás-munkaterületek használatát jelöli.

## <a name="power-bi-developer-samples"></a>A Power BI fejlesztői mintái

A Power BI fejlesztői minták elemeket tartalmaznak az irányítópultokba, jelentésekbe és csempékbe való beágyazáshoz.

[Power BI fejlesztői minták](https://github.com/Microsoft/PowerBI-Developer-Samples)

* Az **Alkalmazás tulajdonában lévő adatok** kategóriában lévő minták a nem Power BI-felhasználók esetében történő beágyazásokhoz használhatók.
* A **Felhasználó tulajdonában lévő adatok** kategóriában lévő minták a Power BI-felhasználók esetében történő beágyazásokhoz használhatók.

## <a name="github-repositories"></a>GitHub-adattárak

* [.NET SDK](https://github.com/Microsoft/PowerBI-CSharp)
* [JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript)
* [Egyéni vizualizációk](https://github.com/Microsoft/PowerBI-visuals)

## <a name="developer-tools"></a>Fejlesztői eszközök

A következő eszközök a Power BI-elemek fejlesztése során lehetnek hasznosak.

Megismerkedhet a [Beágyazáshoz szükséges telepítési eszközzel](https://aka.ms/embedsetup), hogy gyorsan munkához láthasson, és letölthessen egy mintaalkalmazást, amely bemutatja a Power BI-tartalmak beágyazását.

Válassza ki az Ön számára megfelelő megoldást:

* Amennyiben az [ügyfelei számára végez beágyazást](embedding.md#embedding-for-your-customers), irányítópultokat és jelentéseket ágyazhat be olyan felhasználók számára, akik nem rendelkeznek Power BI-fiókkal. Futtassa a [Beágyazás az ügyfelek számára](https://aka.ms/embedsetup/AppOwnsData) megoldást.

* A [Beágyazás a cég számra](embedding.md#embedding-for-your-organization) használatával kiterjesztheti a Power BI szolgáltatást. Futtassa a [Beágyazás a cég számára](https://aka.ms/embedsetup/UserOwnsData) megoldást.

A JavaScript API teljes körű mintáját a [Playground eszköz](https://microsoft.github.io/PowerBI-JavaScript/demo) segítségével használhatja. Ez az eszköz lehetőséget ad a Power BI Embedded különböző mintáinak gyors kipróbálására. A JavaScript API-ról a [PowerBI-JavaScript wiki](https://github.com/Microsoft/powerbi-javascript/wiki) oldalon talál további információkat.

## <a name="push-data-into-power-bi"></a>Adatok leküldése a Power BI szolgáltatásba

A Power BI API lehetővé teszi az adatok leküldését az adatkészletekbe. A funkció segítéségével sorokat adhat hozzá az adatkészletekben lévő táblákhoz. Az irányítópultok csempéi vagy a jelentésekben lévő vizualizációk ezután tükrözik az új adatokat.

![Adatminta leküldése](media/what-can-you-do/powerbi-push-data.png)

## <a name="next-steps"></a>Következő lépések

[Adatok küldése adatkészletekbe](walkthrough-push-data.md)  
[Egyéni Power BI-vizualizáció fejlesztése](custom-visual-develop-tutorial.md)  
[A Power BI REST API-jainak leírása](https://docs.microsoft.com/rest/api/power-bi/)  

További kérdései vannak? [Kérdezze meg a Power BI közösségét](http://community.powerbi.com/)
