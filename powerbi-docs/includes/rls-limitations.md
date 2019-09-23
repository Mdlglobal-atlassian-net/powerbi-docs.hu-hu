---
author: mgblythe
ms.service: powerbi
ms.topic: include
ms.date: 09/13/2019
ms.author: mblythe
ms.openlocfilehash: b2be085c48b303304d46ea93c272e6a860143c51
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71074823"
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
