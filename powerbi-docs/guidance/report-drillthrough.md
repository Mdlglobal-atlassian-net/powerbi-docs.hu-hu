---
title: Jelentésoldal részletezése
description: Útmutató a jelentésoldal részletezéséhez.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2019
ms.author: v-pemyer
ms.openlocfilehash: a19e8148a719186cbaefe3203d58a5a98687c067
ms.sourcegitcommit: 02b05932a119527f255e1eacc745a257044e392f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75223629"
---
# <a name="report-page-drillthrough"></a>Jelentésoldal részletezése

Ez a cikk a Power BI-jelentéseket megtervező jelentéskészítők számára íródott. Javaslatokat és ajánlásokat fogalmaz meg a [jelentésoldal részletezésének](../desktop-drillthrough.md) létrehozásához.

Javasoljuk, úgy tervezze meg a jelentést, hogy lehetővé tegye a jelentés felhasználói számára a következő folyamat elérését:

1. Jelentésoldal megtekintése.
2. Vizuális elem azonosítása a mélyebb elemzéshez.
3. Kattintson a jobb gombbal a vizualizációs elemre a részletezéshez.
4. Végezzen el kiegészítő elemzést.
5. Térjen vissza a forrás jelentésoldalára.

## <a name="suggestions"></a>Javaslatok

Javasoljuk, hogy vegyen figyelembe két részletezési típust:

- [További mélység](#additional-depth)
- [Szélesebb perspektíva](#broader-perspective)

### <a name="additional-depth"></a>További mélység

Ha a jelentésoldal összesített eredményeket jelenít meg, a részletezési oldal a jelentés felhasználóit a tranzakciós szintű részletekre irányíthatja. Ez a tervezési megközelítés lehetővé teszi a támogató tranzakciók megtekintését, de csak akkor, ha szükséges.

Az alábbi példa azt mutatja be, hogy mi történik, ha egy jelentés felhasználója egy havi értékesítési összegzésből hajt végre részletezést. A részletezési oldal egy adott hónapra vonatkozó megrendelések részletes listáját tartalmazza.

![Az Értékesítési összegzés nevű mátrixvizualizáció év és hónap szerint csoportosítja az értékesítéseket a sorokban és ország alapján az oszlopokban. A részletezési oldal is megjelenik.](media/report-drillthrough/suggestion-drillthrough-add-depth.png)

### <a name="broader-perspective"></a>Szélesebb perspektíva

A részletezési oldal a további mélységgel ellentétes hatást is elérhet. Ez a forgatókönyv kiválóan használható a teljes körű nézet részletezésére.

Az alábbi példa azt mutatja be, hogy mi történik, ha a jelentés felhasználója egy irányítószám alapján hajt végre részletezést. A részletezési lap általános információkat jelenít meg az irányítószámmal kapcsolatban.

![A táblázatos vizualizáció három oszlopot tartalmaz: Irányítószám, a szabálysértési pontok átlaga és a besorolási érték átlaga. A részletezési oldal is megjelenik.](media/report-drillthrough/suggestion-drillthrough-broader-perspective.png)

## <a name="recommendations"></a>Javaslatok

A jelentés tervezésének idején a következő eljárásokat ajánljuk:

- **Stílus:** Tervezze meg a részletezési oldalt úgy, hogy ugyanazt a témát és stílust használja, mint a jelentés. Így a felhasználók úgy érzik, mintha ugyanazt a jelentést tekintenék meg.
- **Részletezési szűrők:** Úgy állítsa be a részletezési szűrőket, hogy megtekinthesse az eredmény valóságos előnézetét a részletezési oldal megtervezésekor. A jelentés közzététele előtt ne felejtse el eltávolítani ezeket a szűrőket.
- **További képességek:** A részletezési oldal olyan, mint bármely más jelentésoldal. Még további interaktív képességekkel is bővítheti, többek között szeletelőkkel és szűrőkkel.
- **Üres értékek:** Kerülje el olyan vizualizációk felvételét, amelyek képesek ÜRES érték megjelenítésére, vagy hibákat eredményeznek a részletezési szűrők alkalmazásakor.
- **Oldal láthatósága:** Fontolja meg a részletezési oldalak elrejtését. Ha úgy dönt, hogy láthatóvá tesz egy részletezési oldalt, adjon hozzá egy gombot, amellyel a felhasználók törölhetik a korábban beállított részletezési szűrőket. Rendeljen hozzá egy [könyvjelzőt](../desktop-bookmarks.md) a gombhoz. A könyvjelzőt úgy kell konfigurálni, hogy eltávolítsa az összes szűrőt.
- **Vissza gomb:** Részletezési szűrő hozzáadásakor a rendszer automatikusan felvesz egy vissza [gombot](../desktop-buttons.md). Jó ötlet, ha ezt megtartja. Így a jelentés felhasználói egyszerűen visszatérhetnek a forrásoldalhoz.
- **Felderítés:** Segítheti a részletezési oldal megtalálását, ha megadja a vizuális fejléc ikonjának szövegét, vagy utasításokat ad hozzá a szövegmezőhöz. Átfedést is tervezhet, amint az [ebben a blogbejegyzésben](https://alluringbi.com/2019/10/23/overlays-for-true-self-serve-reporting/) szerepel.

> [!TIP]
> Lehetősége van részletezést konfigurálni a Power BI többoldalas jelentéseihez is. Ezt úgy teheti meg, hogy hivatkozásokat ad hozzá a Power BI-jelentésekhez. A hivatkozások meghatározhatják az [URL-paramétereket](https://powerbi.microsoft.com/blog/url-parameters-for-paginated-reports-are-now-available/).

## <a name="next-steps"></a>Következő lépések

Ezzel a cikkel kapcsolatosan a következő forrásanyagokban talál további információt:

- [Részletezés használata a Power BI Desktopban](../desktop-drillthrough.md)
- Guy in a Cube videó: [A részletezés használatának részletezése a Power BI Desktopban](https://www.youtube.com/watch?v=2x9lLHDbtDk)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
