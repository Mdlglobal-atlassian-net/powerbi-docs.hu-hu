---
title: Power BI – első lépések harmadik féltől származó alkalmazásokkal
description: Power BI – első lépések harmadik féltől származó alkalmazásokkal
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.cunstom: ''
ms.date: 09/16/2019
LocalizationGroup: Get started
ms.openlocfilehash: ff44527ab0f6c57007db82c79d6b357973eded17
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/06/2020
ms.locfileid: "74699176"
---
# <a name="get-started-with-third-party-apps"></a>Első lépések harmadik féltől származó alkalmazásokkal

A Power BI segítségével olyan alkalmazásokat is használhat, amelyeket Microsofton kívüli cégek vagy személyek hoztak létre. Például használhat olyan, harmadik féltől származó alkalmazást, amely a Power BI csempéit egy egyénileg létrehozott webes alkalmazással integrálja. Harmadik féltől származó alkalmazás használata esetén a rendszer arra kéri, hogy adjon az alkalmazásnak bizonyos engedélyeket a Power BI-fiókhoz és annak erőforrásaihoz. Fontos, hogy csak olyan alkalmazásoknak adjon engedélyeket, amelyeket ismer, és amelyekben megbízik. Az alkalmazásnak adott engedély bármikor visszavonható. Lásd: [Harmadik féltől származó alkalmazások engedélyének visszavonása](#revoke).

Egy alkalmazás a következő hozzáférési típusokat kérheti.

## <a name="power-bi-app-permissions"></a>Power BI-alkalmazásengedélyek

* **Összes irányítópult megtekintése**
  
  * Ez az engedély lehetővé teszi az alkalmazásnak az Ön számára elérhető összes irányítópult megtekintését. Ide tartoznak a saját, a tartalomcsomagból származó, az Önnel megosztott, és az Ön csoportjában található irányítópultok. Az alkalmazás nem módosíthatja az irányítópultot. Az alkalmazás többek között arra használhatja ezt az engedélyt, hogy az irányítópult tartalmát beágyazza a saját felületébe.

* **Összes jelentés megtekintése**
  
  * Ez az engedély lehetővé teszi az alkalmazásnak az Ön számára elérhető összes jelentés megtekintését. Ide tartoznak a saját, a tartalomcsomagból származó, az Önnel megosztott, és az Ön csoportjában található jelentések. Az alkalmazás nem csupán a jelentést, hanem a benne foglalt adatokat is megtekintheti. Az alkalmazás magukat a jelentéseket nem módosíthatja. Az alkalmazás többek között arra használhatja az engedélyt, hogy a jelentés tartalmát beágyazza a saját felületébe.

* **Összes adatkészlet megtekintése**
  
  * Ez az engedély lehetővé teszi az alkalmazásnak az Ön számára elérhető összes adatkészlet listázását. Ide tartoznak a saját, a tartalomcsomagból származó, az Önnel megosztott, és az Ön csoportjában található adatkészletek. Az alkalmazás látja az adatkészleteket és azok szerkezetét, beleértve a táblázatok és az oszlopok nevét is. Ez az engedély jogosultságot ad az adatkészletben lévő adatok olvasásához. Az engedély nem ad jogosultságot az alkalmazásnak az adatkészlet kiegészítéséhez vagy módosításához.
* **Összes adatkészlet olvasása és írása**
  
  * Ez az engedély lehetővé teszi az alkalmazásnak az Ön számára elérhető összes adatkészlet listázását. Ide tartoznak a saját, a tartalomcsomagból származó, az Önnel megosztott, és az Ön csoportjában található adatkészletek. Az alkalmazás látja az adatkészleteket és azok szerkezetét, beleértve a táblázatok és az oszlopok nevét is. Ez az engedély jogosultságot ad az adatkészletben lévő adatok olvasásához és írásához. Az alkalmazás új adatkészleteket is létrehozhat, vagy módosíthatja a már meglévőket. Ezt általában a Power BI-nak történő közvetlen adatküldéshez használják az alkalmazások.

* **Felhasználói csoportok megtekintése**
  
  * Ez az engedély lehetővé teszi az alkalmazás számára az összes olyan csoport listázását, amelynek Ön a tagja. Ezt az engedélyt az alkalmazás egyes más, itt felsorolt engedélyekkel együtt, az adott csoporttartalom megtekintéséhez és frissítéséhez használhatja. Az alkalmazás nem módosíthatja magát a csoportot.

<a name="revoke"/>

## <a name="revoke-third-party-app-permissions"></a>Harmadik féltől származó alkalmazások engedélyének visszavonása

A harmadik féltől származó alkalmazás engedélyeit az Office 365 Saját alkalmazások oldalán vonhatja vissza.

Az **Office 365 Saját alkalmazások** oldalon az alábbi lépésekben vonhatja vissza a harmadik féltől származó alkalmazások engedélyeit:

1. Nyissa meg az [Office 365 Saját alkalmazások](https://portal.office.com/myapps) oldalt.

2. A **Saját alkalmazások** oldalon keresse meg a harmadik féltől származó alkalmazást.

3. Mutasson az alkalmazás csempéjére, és kattintson a **(...)** , majd az **Eltávolítás** elemre.

   ![Eltávolítás](media/service-power-bi-get-started-third-party-apps/remove.png)