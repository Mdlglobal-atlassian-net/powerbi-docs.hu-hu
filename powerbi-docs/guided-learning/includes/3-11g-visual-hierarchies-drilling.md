---
ms.openlocfilehash: 9aac366f04d53da56b62c10fdb85229d0d412834
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61397702"
---
Amikor egy *dátum* mezőt ad hozzá a *Tengely* mezőgyűjtőhöz, a Power BI automatikusan felvesz egy időhierarchiát *Év*, *Negyedév*, *Hónap* és *Nap* bontással. Ezáltal a Power BI lehetővé teszi a vizualizációk időalapú kezelését a jelentést olvasók számára azáltal, hogy a felhasználók kibonthatják a különböző időszinteket.

![](media/3-11g-visual-hierarchies-drilling/3-11g_1.png)

Ha a hierarchia létrejött, elkezdheti kibontani a szinteket az időhierarchiában. Ha például rákattint az egyik évre, azzal kibontja a hierarchia következő szintjét, amely jelen esetben a *Negyedév*, innentől ez fog megjelenni a vizualizációban.

![](media/3-11g-visual-hierarchies-drilling/3-11g_2.png)

Az automatikusan létrehozott hierarchiában azt is megadhatja, hogy a felhasználok melyik szintig hatolhassanak le a megosztott jelentésben. Ehhez a Vizualizációk panelen egyszerűen kattintson az X-re amellett a hierarchia mellett, amelyet el szeretne távolítani. A törölt szint eltűnik a jelentésből, és kibontáskor sem jelenik többé meg.

![](media/3-11g-visual-hierarchies-drilling/3-11g_3.png)

Ha mégis visszaállítaná a törölt hierarchiát, csak távolítsa el a *dátum* mezőt, és vegye fel ismét a **Mezők** panelről, így a hierarchia ismét automatikusan létrejön.

Előfordulhat, hogy időnként nem kívánja használni az adott hierarchiát a vizualizációban. Ennek vezérléséhez válassza ki a lefelé mutató nyilat a *Dátum* mező mellett (miután azt hozzáadta a vizualizációhoz), majd válassza a **Dátum** lehetőséget a **Dátumhierarchia** lehetőség helyett. Ezzel beállíthatja, hogy a Power BI a nyers dátumértékeket jelenítse meg a vizualizációban.

![](media/3-11g-visual-hierarchies-drilling/3-11g_4.png)

Egyetlen negyedév vagy év kiválasztása helyett kibonthatja egyszerre az összes látható adatelemet is. Ehhez a vizuális elem bal felső sarkában válassza az *Összes kibontása* ikont, amely egy lefelé mutató kettős nyilat formáz.

![](media/3-11g-visual-hierarchies-drilling/3-11g_5.png)

