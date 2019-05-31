---
author: mgblythe
ms.service: powerbi
ms.topic: include
ms.date: 02/15/2019
ms.author: mblythe
ms.openlocfilehash: 44ef0aa9d436f3a8a02f9a6b831847d5c996558a
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61193835"
---
## <a name="limitations"></a>Korlátozások

Itt találja a sorszintű biztonság felhőmodellekben érvényes aktuális korlátozásait.

* Ha korábban szerepköröket és szabályokat adott meg a Power BI szolgáltatásban, újból létre kell hoznia őket a Power BI Desktopban.

* Csak a Power BI Desktoppal létrehozott adathalmazokon határozhat meg RLS-t. Ha az Excellel létrehozott adatkészletekhez szeretné engedélyeznie az RLS-t, először Power BI Desktop- (PBIX-) fájlokká kell konvertálnia a fájlokat. [További információ](../desktop-import-excel-workbooks.md)

* Csak az ETL- és a DirectQuery-kapcsolatok támogatottak. Az Analysis Services élő kapcsolatait a helyszíni modellen lehet kezelni.

* Cortana egyelőre nem támogatott az RLS-sel.

## <a name="known-issues"></a>Ismert problémák

Az egyik ismert hiba, hogy hibaüzenet jelenik meg, amikor korábban már közzétett jelentést próbál közzétenni a Power BI Desktopból. A forgatókönyv a következő.

1. Anna olyan adatkészlettel rendelkezik, amely közzé van téve a Power BI szolgáltatásban, és konfigurált RLS-sel rendelkezik.

1. Anna frissíti a jelentést a Power BI Desktopban, és újból közzéteszi.

1. Anna hibaüzenetet kap.

**Áthidaló megoldás:** Tegye közzé újra a Power BI Desktop-fájlt a Power BI szolgáltatásból a probléma megoldásáig. Ehhez válassza az **Adatok lekérése** > **Fájlok** lehetőséget.
