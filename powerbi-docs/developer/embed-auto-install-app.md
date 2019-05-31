---
title: Automatikus telepítés a Power BI-alkalmazások, ha a szervezete számára ágyaz be
description: 'Útmutató: alkalmazások telepítése a Power BI automatikusan, ha a szervezete számára ágyaz be.'
ms.subservice: powerbi-developer
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.topic: how-to
ms.service: powerbi
ms.custom: ''
ms.date: 04/16/2019
ms.openlocfilehash: bb9ba5531c2a23f15ccbf98261e246ab7080aecb
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61376222"
---
# <a name="auto-install-power-bi-apps-when-embedding-for-your-organization"></a>Ha a szervezete számára ágyaz be automatikus telepítés Power BI-alkalmazások

Az alkalmazás-tartalmak beágyazásához, rendelkeznie kell a felhasználót, hogy van-e beágyazási [elérhetik az alkalmazást](../service-create-distribute-apps.md). Ha az alkalmazás telepítve van a felhasználó számára, majd a beágyazás zökkenőmentesen működik. További információkért lásd: [jelentések vagy irányítópultok alkalmazásból beágyazási](embed-from-apps.md). Adjon meg a powerbi.com-on, amely az összes alkalmazás lehet [telepítése automatikusan](https://powerbi.microsoft.com/blog/automatically-install-apps/). Ez a művelet azonban bérlői szinten történik, és minden alkalmazásokra vonatkozik.

## <a name="auto-install-app-on-embedding"></a>Automatikus telepítés alkalmazás beágyazása

Ha a felhasználó férhet hozzá az alkalmazáshoz, de az alkalmazás nincs telepítve, majd beágyazás meghiúsul. Ezek a hibák elkerülése beágyazása az alkalmazásokból során, így lehetővé tehetik a beágyazása után az alkalmazás automatikus telepítése. Ez a művelet azt jelenti, ha a felhasználó megpróbál ágyazhat be az alkalmazás nincs telepítve, az automatikusan települ az Ön számára. Ezért csak a kívánt tartalom beolvasása beágyazott azonnal, a felhasználó egy zökkenőmentes élményt eredményez.

## <a name="embed-for-power-bi-users-user-owns-data"></a>Beágyazás a Power BI-felhasználók (a felhasználó az adatok tulajdonosa)

Ahhoz, hogy az alkalmazások automatikus telepítése a felhasználók számára, akkor engedélyeznie kell az alkalmazást a tartalom létrehozása során [az alkalmazás regisztrálása](register-app.md#register-with-the-power-bi-application-registration-tool), vagy adja hozzá, ha már regisztrálta az alkalmazást.

![Alkalmazás regisztrálása tartalmat hoz létre.](media/embed-auto-install-app/register-app-create-content.png)

Ezután meg kell adnia az Alkalmazásazonosító a beágyazási URL-címben. Ahhoz, hogy az alkalmazás azonosítója, az alkalmazás létrehozóját először meg kell telepíteni az alkalmazást, majd használja a támogatott operációs rendszerek egyikét [Power BI Rest API](https://docs.microsoft.com/rest/api/power-bi/) hívások - [jelentések lekérése](https://docs.microsoft.com/rest/api/power-bi/reports/getreports) vagy [Get Dashboards](https://docs.microsoft.com/rest/api/power-bi/dashboards/getdashboards). Ezután az alkalmazás létrehozóját kell vennie a beágyazási URL-címet a REST API-válaszból. Az Alkalmazásazonosító az URL-cím jelenik meg, ha a tartalom-alkalmazások.  Miután a beágyazási URL-címet, ágyazhat be rendszeresen használhatja.

## <a name="secure-embed"></a>Biztonságos beágyazása

Alkalmazások automatikus telepítése használatához az alkalmazás létrehozóját először meg kell telepíteni az alkalmazást, majd nyissa meg a PowerBI.com webhelyen alkalmazásra, keresse meg a jelentést, és a hivatkozás beszerzése a szokásos módon. Az alkalmazás által használható a hivatkozás hozzáféréssel rendelkező más felhasználók is be a jelentést.

## <a name="considerations-and-limitations"></a>Megfontolandó szempontok és korlátozások

* Csak beágyazhat jelentéseket és irányítópultokat ehhez a forgatókönyvhöz.

* Ez a funkció jelenleg nem támogatott az alkalmazás tulajdonában lévő adatok és a SharePoint beágyazása forgatókönyveket.