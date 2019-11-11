---
title: 'DAX: A DIVIDE függvény és a divide operátor (/)'
description: Útmutató a DAX DIVIDE függvény használatához.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: v-pemyer
ms.openlocfilehash: c96518bb8de7f323b51a7e1e3f34f9d9bf056c79
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875391"
---
# <a name="dax-divide-function-vs-divide-operator-"></a>DAX: A DIVIDE függvény és a divide operátor (/)

Ez a cikk a DAX-kifejezéseket definiáló adatmodellezőknek szól.

## <a name="background"></a>Háttér

Ha egy olyan DAX-kifejezést ír, amely egy számlálót oszt el egy nevezővel, használhatja a [DIVIDE](/dax/divide-function-dax) függvényt vagy a divide operátort (/ – perjel).

A DIVIDE függvény használatakor számlálót és nevezőt tartalmazó kifejezéseket kell megadnia. Igény szerint megadhat egy olyan értéket is, amely más eredményt képvisel.

```dax

DIVIDE(<numerator>, <denominator> [,<alternateresult>])

```

A DIVIDE függvény automatikusan kezeli a nullával való osztást tartalmazó eseteket. Ha nem ad meg alternatív eredményt, a nevező pedig nulla vagy ÜRES, a függvény eredménye ÜRES. Ha megad egy alternatív eredményt, ÜRES helyett az lesz az eredmény.

A DIVIDE függvény kézenfekvő, mivel segítségével a kifejezésnek nem kell tesztelnie a nevező értékét. Ez a függvény emellett jobban optimalizált a nevező értékének tesztelésére, mint az [IF](/dax/if-function-dax) függvény. A teljesítménytöbblet jelentős, mivel a nullával osztás költséges. A DIVIDE használata tömörebb és elegánsabb kifejezést eredményez.

## <a name="example"></a>Példa

A következő mértékkifejezés biztonságos osztást eredményez, azonban négy DAX-függvényt tartalmaz.

```dax

=IF(OR(ISBLANK([Sales]), [Sales] == 0), BLANK(), [Profit] / [Sales])

```

Ez a mértékkifejezés ugyanazt eredményezi, azonban hatékonyabban és elegánsabban.

```dax

=DIVIDE([Profit], [Sales])

```

## <a name="recommendations"></a>Javaslatok

A DIVIDE függvényt olyan esetekben célszerű használnia, amikor a nevető egy olyan kifejezés, amely _lehetséges_, hogy nulla vagy ÜRES eredménnyel zárul.

Ha a nevező egy állandó érték, használja a divide operátort. Ebben az esetben az osztás mindenképpen sikeres lesz, a kifejezés pedig jobb teljesítményt nyújt, mivel elkerüli a felesleges tesztelést.

Fontolja meg, hogy a DIVIDE függvénynek érdemes-e alternatív értéket visszaadnia. Mértékek esetében célszerűbb ÜRES eredményt visszaadnia. Ennek az az oka, hogy a jelentésvizualizációk alapértelmezés szerint eltávolítják a csoportosításokat ÜRES összegzések esetén. A vizualizáció így olyan csoportokra összpontosíthat, ahol léteznek adatok. Szükség esetén konfigurálhatja a vizualizációt úgy, hogy a szűrő minden csoportját (amely értékeket vagy ÜRES eredményt ad) megjelenítse. Ehhez engedélyeznie kell az „Adatot nem tartalmazó elemek megjelenítése” beállítást.
