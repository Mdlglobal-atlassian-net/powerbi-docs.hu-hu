---
title: 'DAX: A hibakezelő függvények megfelelő használata'
description: Útmutató a hibakezelő DAX-függvények használatához.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2019
ms.author: v-pemyer
ms.openlocfilehash: ae4e9081930b0f6934a557ba45afd99dd8dfc05d
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875644"
---
# <a name="dax-appropriate-use-of-error-functions"></a>DAX: A hibakezelő függvények megfelelő használata

Ez a cikk a DAX-kifejezéseket definiáló adatmodellezőknek szól.

## <a name="background"></a>Háttér

Olyan DAX-kifejezés írásakor, amely a kiértékeléskor hibát okozhat, érdemes lehet felhasználni két hasznos DAX-függvényt.

- Az [ISERROR](/dax/iserror-function-dax) függvény bemenete egyetlen kifejezés, és a TRUE értéket adja vissza, ha ez a kifejezés hibát eredményez.
- Az [IFERROR](/dax/iferror-function-dax) függvények két kifejezés a bemenete. Ha az első kifejezés hibát eredményez, akkor a második kifejezés értékét adja vissza. Tulajdonképpen ez az ISERROR függvény [IF](/dax/if-function-dax) függvénybe ágyazásának egy optimalizált implementációja.

Ezek a függvények hasznosak lehetnek, és hozzájárulhatnak a könnyen érthető kifejezések írásához, ugyanakkor azonban jelentősen ronthatják a számítások teljesítményét. Ennek az az oka, hogy ezek a függvények növelik a tárolási összetevő szükséges ellenőrzéseinek számát.

Fontos tudnivaló, hogy kiértékelési hibák többségét váratlan BLANK vagy nulla értékek, vagy érvénytelen adattípus-konverziók okozzák.

## <a name="recommendations"></a>Javaslatok

Érdemes kerülni az ISERROR és IFERROR függvény használatát. Helyettük alkalmazzon inkább megelőző stratégiát a modell kialakítása és a kifejezések írása során. Ilyenek lehetnek például a következők:

- **A modellbe betöltött adatok minőségének biztosítása:** Használjon Power Query-átalakításokat az érvénytelen vagy hiányzó értékek eltávolítására vagy helyettesítésére, és a helyes adattípusok beállítására. A Power Query-átalakítások sorok szűrésére is felhasználhatók, ha olyan hibák merülnek fel, mint az érvénytelen adatkonverzió.

    Az adatminőség a modelloszlop **Is Nullable** (nullázható) tulajdonságának Off (kikapcsolt) értékre állításával, így az adatfrissítés BLANK értékek esetén sikertelen lesz. Lényeges, hogy ilyen esetben a sikeres frissítés eredményeként betöltött adatok megmaradnak a táblákban.
- **Az IF függvény használata:** Az IF függvény logikai vizsgálatot végző kifejezés, amellyel megállapítható, hogy hibás eredmény jönne-e létre. Fontos tudni, hogy az ISERROR és az IFERROR függvényhez hasonlóan ez a függvény is a tárolási összetevő további ellenőrzéseit válthatja ki, de várhatóan azoknál jobb teljesítményt ér el, ha nem kell hibákat jelezni.
- **Hibatűrő függvények használata:** Egyes DAX-függvények ellenőrzik a hibakörülményeket, és kezelik azok következményeit. Az ilyen függvényekhez megadható egy másodlagos eredmény, amelyet ilyen esetben adnak vissza. Erre példa a [DIVIDE](/dax/divide-function-dax) függvény. Erről a függvényről további tudnivalókat talál a [DAX: A DIVIDE függvény és az osztási operátor (/) összehasonlítása](dax-divide-function-operator.md) című cikkben.

## <a name="example"></a>Példa

Az alábbi mértékkifejezés azt ellenőrzi, hogy keletkezne-e hiba. Ebben az esetben a BLANK értéket adja vissza (ez történik, ha az IF függvényhez nincs megadva érték hamis feltétel esetre).
```dax
= IF(ISERROR([Profit] / [Sales]))
```
A mértékkifejezés következő verzióját úgy módosítottuk, hogy az IS és az ISERROR függvény helyett az IFERROR függvényt használja.
```dax
= IFERROR([Profit] / [Sales], BLANK())
```
A mértékkifejezésnek ez a végleges változata azonban ugyanazt a végeredményt biztosítja, de hatékonyabban és elegánsabban.
```dax
= DIVIDE([Profit], [Sales])
```