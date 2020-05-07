---
title: Mobilfejlesztés
description: Mobilbarát Power BI-vizualizációk létrehozása
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/12/2019
ms.openlocfilehash: 38e6ac3be143381304f1fdfc8e1427b91f398a9a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82196629"
---
# <a name="how-to-create-mobile-friendly-power-bi-visuals"></a>Mobilbarát Power BI-vizualizációk létrehozása
A mobil felhasználás jelentős szerepet játszik a Power BI-ban. Egyik fő erénye éppen az, hogy bármikor, bárhol kapcsolódhat az adataihoz.

A Power BI-vizualizációkat létrehozó tervezőknek minden mobileszköz egyedi korlátozásait figyelembe kell venniük, hogy a lehető legtöbb felhasználó számára kínálhassák a lehető legjobb mobil-felületet.

A [Windows, iOS és Android rendszerhez készült Power BI-alkalmazás](/power-bi/consumer/mobile/mobile-apps-for-mobile-devices) használatával az üzleti felhasználók útközben is egyetlen érintéssel kaphatnak átfogó képet az adataikról.

## <a name="requirements"></a>Követelmények

A mobilbarát vizualizációk fejlesztésekor elengedhetetlen az alábbi szempontok figyelembe vétele:

- Megjelenítés

  A Power BI-vizualizációknak minden támogatott mobileszközön, emellett minden támogatott böngészőben és alkalmazásban is hiba nélkül kell megjelenniük a jelentésekben, irányítópultokon és **Fókusz** módban futtatva is. 

- Interaktív

  Az interaktív funkciókat ugyanúgy kell biztosítani, ahogyan az asztali eszközökön. Az asztali böngészőkben kezelhető összes eseménynek támogatottnak kell lenni, vagy hasonló eseménykezelőkkel kell rendelkeznie a mobileszközökön is.
  
  Az adatpontok közötti alapszintű navigálásnak és az adatpontok kijelölésének például ugyanúgy kell működnie, mint az asztali böngészőkben. Ha egy vizualizáció támogatja a **Ctrl** billentyűvel végzett többszörös kijelölést, a fejlesztőnek gondolnia kell rá, hogy hasonló eseménykezelőt biztosítson a mobileszközökhöz is.

  Az alábbi táblázat a mobileszközökön megfelelő események párosításait sorolja fel.

  | Egéresemény neve | Érintéses esemény neve |
  |:----------------:|:----------------:|
  | `click` | `click` |
  | `mousemove` | `touchmove` |
  | `mousedown` | `touchstart` |
  | `mouseup` | `touchend` |
  | `dblclick` | külső kódtár használata |
  | `contextmenu` | külső kódtár használata |
  | `mouseover` | `touchmove` |
  | `mouseout` | `touchmove` (vagy külső kódtár) |
  | `wheel` | `NaN` |

  > [!NOTE]
  > Nem minden mobil vagy érintőképernyős eszköz támogatja az egér- (vagy *mouse* előtagú) eseményeket. Ilyen esetekben az *egér* és az *érintés* eseményeket egyszerre kell kezelni.

## <a name="optional"></a>Nem kötelező
Az alábbi szempontok nem kötelezők, és a jobb felhasználói élmény kialakítását szolgálják.

- Megjelenítés

  A kisebb kijelzőméretek támogatásához próbáljon meg olyan formázási lehetőségeket felvenni, amelyek módosításával a felhasználó átállíthatja az egyes elemek méretét. Felvehet például formázási lehetőségeket a jelentésekben és irányítópultokon használható címkékhez. A felhasználó ezekkel kimondottan a saját mobileszközéhez igazíthat egy vizualizációt.
  
  Ugyanezek a beállítások az asztali böngészőkben is alkalmazhatók a vizualizációkra, és szükség esetén felülírhatók, hogy a vizualizáció alkalmazkodjon egy kisebb képernyőhöz.

  > [!NOTE]
  > A **Fókusz** módban megjelenő vizualizáció optimalizálásához a fekvő és az álló tájolásra is gondolni kell. Lásd: [Tartalom Fókusz módú megjelenítése](/power-bi/consumer/end-user-focus).

- Interaktív

  Vegye fontolóra az olyan mobilspecifikus eseménykezelők felvételét, mint a húzás és görgetés.

- Feladatátvétel

  A vizualizációnak beszédes hibaüzenetet kell kiírnia, ha nem jeleníthető meg a mobileszközön.

## <a name="supported-browsers-and-devices"></a>Támogatott böngészők és eszközök
A Power BI-vizualizációnak a Power BI Appst támogató összes eszközön meg kell jelennie. További információ: [A Power BI-hoz támogatott böngészők](/power-bi/power-bi-browsers) és [Power BI-mobilalkalmazások](/power-bi/consumer/mobile/mobile-apps-for-mobile-devices).

A legújabb Windows, iOS és Android rendszerű eszközmodelleken végzett teszteléskor a fejlesztőnek figyelembe kell vennie ezeket a minőségi szempontokat.

## <a name="next-steps"></a>Következő lépések
Ez első lépésekhez lásd: [Oktatóanyag: Power BI-vizualizáció fejlesztése](/power-bi/developer/visuals/custom-visual-develop-tutorial).
