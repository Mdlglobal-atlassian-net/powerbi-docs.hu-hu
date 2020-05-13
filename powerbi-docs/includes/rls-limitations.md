---
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 01/31/2020
ms.author: davidi
ms.openlocfilehash: 912b0213c328c623e7881f7f30fe7d67f6d889b3
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83274637"
---
## <a name="limitations"></a>Korlátozások

Itt találhatók a sorszintű biztonság felhőmodellekben érvényes aktuális korlátozásai:

* Ha korábban szerepköröket és szabályokat adott meg a Power BI szolgáltatásban, újból létre kell hoznia őket a Power BI Desktopban.

* Csak a Power BI Desktoppal létrehozott adathalmazokon határozhat meg RLS-t. Ha az Excellel létrehozott adatkészletekhez szeretné engedélyeznie az RLS-t, először Power BI Desktop- (PBIX-) fájlokká kell konvertálnia a fájlokat. [További tudnivalók](../connect-data/desktop-import-excel-workbooks.md).

* Csak az importálási és a DirectQuery-kapcsolatok támogatottak. Az Analysis Services élő kapcsolatait a helyszíni modellen lehet kezelni.

## <a name="known-issues"></a>Ismert problémák

Az egyik ismert hiba, hogy hibaüzenet jelenik meg, amikor korábban már közzétett jelentést próbál közzétenni a Power BI Desktopból. A helyzet a következőnek felel meg:

1. Anna olyan adatkészlettel rendelkezik, amely közzé van téve a Power BI szolgáltatásban, és konfigurált RLS-sel rendelkezik.

1. Anna frissíti a jelentést a Power BI Desktopban, és újból közzéteszi.

1. Anna hibaüzenetet kap.

**Áthidaló megoldás:** Tegye közzé újra a Power BI Desktop-fájlt a Power BI szolgáltatásból a probléma megoldásáig. Ehhez válassza az **Adatok lekérése** > **Fájlok** lehetőséget.

