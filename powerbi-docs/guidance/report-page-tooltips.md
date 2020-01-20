---
title: Vizualizációk kibővítése a jelentésoldalak elemleírásával
description: Útmutató a jelentésoldal elemleírásaihoz.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/24/2019
ms.author: v-pemyer
ms.openlocfilehash: 826af7b224b901b6dc9f3926260b1d920836a792
ms.sourcegitcommit: 0ae9328e7b35799d5d9613a6d79d2f86f53d9ab0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76040352"
---
# <a name="extend-visuals-with-report-page-tooltips"></a>Vizualizációk kibővítése a jelentésoldalak elemleírásával

Ez a cikk a Power BI-jelentéseket megtervező jelentéskészítők számára készült. Javaslatokat és ajánlásokat fogalmaz meg a [jelentésoldal elemleírásainak](../desktop-tooltips.md) létrehozásához.

## <a name="suggestions"></a>Javaslatok

A jelentésoldali elemleírások javíthatják a jelentésfelhasználói élményt. Az oldalak elemleírásaival a jelentésfelhasználók gyorsan és hatékonyan kaphatnak részletes elemzéseket egy vizualizációból. Ezek különböző jelentésobjektumokhoz társíthatók:

- **Vizualizációk:** Egyesével konfigurálhatja, hogy mely vizualizációk jelenítsék meg az oldal elemleírását. Így minden vizualizációhoz beállíthatja, hogy az ne jelenítsen meg elemleírást, a vizualizáció alapértelmezett elemleírását jelenítse meg (amelyet a vizualizáció Mezők panelén állíthat be), vagy egy adott elemleírást tartalmazzon.
- **Vizualizációs fejlécek:** Egyes vizualizációkat úgy konfigurálhat, hogy azok egy oldal elemleírását jelenítsék meg. A jelentés felhasználói a kurzor a vizualizáció fejlécikonjára való helyezésével jeleníthetik meg az oldal elemleírását. Győződjön meg róla, hogy tájékoztatta a felhasználókat erről az ikonról.

> [!NOTE]
> A jelentésvizualizáció csak akkor jelenítheti meg egy oldal elemleírását, ha az elemleírás oldalszűrői kompatibilisek a vizualizáció kialakításával. Egy _termék_ szerint csoportosított vizualizáció például egy olyan elemleírás-oldallal kompatibilis, amely _termék_ szerint szűr.
>
> Az oldalak elemleírásai nem támogatják az interaktivitást. Ha azt szeretné, hogy a jelentés felhasználói interakciókat végezhessenek, készítsen inkább [részletező lapot](../desktop-drillthrough.md).
>
> Az egyéni vizualizációk nem támogatják az oldalak elemleírásait.

Íme néhány javasolt tervezési forgatókönyv:

- [Különböző perspektívák](#different-perspective)
- [Részletek hozzáadása](#add-detail)
- [Súgó hozzáadása](#add-help)

### <a name="different-perspective"></a>Különböző perspektívák

Az oldal elemleírása megjelenítheti ugyanazokat az adatokat, mint a forrásvizualizáció. Ehhez ugyanazt a vizualizációt és kimutatási csoportokat, vagy más vizualizációtípusokat használ. Az oldal elemleírásai a forrásvizualizációra alkalmazott szűrőktől eltérő szűrőket is használhatnak.

A következő példa azt mutatja be, hogy mi történik, ha a jelentés felhasználója a kurzort az **EnabledUsers** érték fölé viszi. Az érték szűrőkontextusa 2018. novemberben a Yammer.

![A mátrixvizualizáció a sorokban év és hónap szerint csoportosított értékrácsot jelenít meg. A jelentés felhasználója egyetlen érték fölé helyezte a kurzort. Megjelent egy oldal elemleírása.](media/report-page-tooltips/suggestion-different-perspective.png)

Megjelent egy oldal elemleírása. Ez egy másik adatvizualizációt (egy vonal- és fürtözött oszlopdiagramot) jelenít meg, és kontrasztos időszűrőt alkalmaz. Látható, hogy az adatpont szűrőkontextusa 2018. november. A lap elemleírása azonban a _egy teljes évnyi hónapokra_ lebontva jeleníti meg a trendet.

### <a name="add-detail"></a>Részletek hozzáadása

Egy oldal elemleírása további részleteket jeleníthet meg, és kontextust is hozzáadhat.

A következő példa azt mutatja be, hogy mi történik, ha a jelentés felhasználója a kurzort az **Average of Violation Points** (Szabálysértési pontok átlaga) érték fölé viszi a 98022 irányítószám esetében.

![Egy táblázatos vizualizáció megjeleníti az értékrácsot, a táblázat pedig három oszlopot tartalmaz. Megjelent egy oldal elemleírása.](media/report-page-tooltips/suggestion-add-details.png)

Megjelent egy oldal elemleírása. Ez a 98022 irányítószám saját attribútumait és statisztikáit jeleníti meg.

### <a name="add-help"></a>Súgó hozzáadása

A vizualizációs fejlécek úgy konfigurálhatók, hogy oldalak elemleírásait jelenítsék meg vizualizációs fejlécekben. Súgódokumentációt adhat egy oldal elemleírásához részletesen formázott szövegmezőkkel. Emellett képeket és alakzatokat is felvehet.

Érdekes módon a gombok, képek, szövegmezők és alakzatok is megjeleníthetik oldalak elemleírásait a vizualizációs fejlécben.

A következő példa azt mutatja be, hogy mi történik, ha a jelentés felhasználója a kurzort a [vizualizációs fejléc ikon](../desktop-visual-elements-for-reports.md) fölé viszi.

![A jelentés felhasználója a kurzort a vizualizáció fejlécének ikonja (kérdőjel ikon) fölé helyezte. Megjelent egy részletesen formázott elemleírás.](media/report-page-tooltips/suggestion-add-help.png)

Megjelent egy oldal elemleírása. Ebben Rich Text formátumú szöveg látható négy szövegmezőben, illetve egy alakzat (vonal). Az oldal elemleírása a vizualizációban megjelenő egyes mozaikszavak leírásával nyújt segítséget.

## <a name="recommendations"></a>Javaslatok

A jelentés tervezésének idején a következő eljárásokat ajánljuk:

- **Oldalméret:** Konfigurálja túl kicsi méretűre az oldal elemleírását. Ehhez használhatja a beépített **Tooltip** (Elemleírás) beállítást (320 képpont széles, 240 képpont magas). Alternatívaként egyéni dimenziókat is beállíthat. Ügyeljen arra, hogy ne használjon túl nagy méretű oldalméretet – ez torzíthatja a forráslapon megjelenő vizualizációkat.
- **Oldal nézet:** A jelentéskészítőben állítsa az oldal nézetét **tényleges méretre** (az oldal nézet alapértelmezett értéke a **Laphoz igazítás**). Így tervezés közben megtekintheti az oldal elemleírásának valódi méretét.
- **Stílus:** Tervezze meg az oldal elemleírását úgy, hogy ugyanazt a témát és stílust használja, mint a jelentés. Így a felhasználók úgy érzik, mintha ugyanazt a jelentést tekintenék meg. Alternatívaként tervezhet egy ezt a témát kiegészítő stílust, amelyet célszerű minden oldal elemleírására alkalmaznia.
- **Elemleírás-szűrők:** Szűrőket rendelhet az oldal elemleírásához, így megtekintheti tervezés közben a valós eredmény előnézetét. A jelentés közzététele előtt ne felejtse el eltávolítani ezeket a szűrőket.
- **Oldal láthatósága:** Mindig rejtse el az elemleírás-oldalakat – a felhasználóknak nem szabad közvetlenül ezekre lépni.

## <a name="next-steps"></a>Következő lépések

Ezzel a cikkel kapcsolatosan a következő forrásanyagokban talál további információt:

- [Elemleírások létrehozása jelentésoldalak alapján a Power BI Desktopban](../desktop-tooltips.md)
- [Elemleírások testreszabása a Power BI Desktopban](../desktop-custom-tooltips.md)
- [Vizuális elemek használata Power BI-jelentések továbbfejlesztéséhez](../desktop-visual-elements-for-reports.md)
- Guy in a Cube videó: [Power BI-jelentésoldali elemleírás – Létrehozás a Power BI Desktopban](https://www.youtube.com/watch?v=URTA7JZsAtw)
- Kérdése van? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
