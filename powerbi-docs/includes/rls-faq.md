---
ms.openlocfilehash: 0592cb7ef076f8094aca565d955cc238b2181068
ms.sourcegitcommit: f6ac9e25760561f49d4257a6335ca0f54ad2d22e
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69560939"
---
## <a name="faq"></a>Gyakori kérdések
**Kérdés:** Mi történik, ha korábban már hoztam létre szerepköröket és szabályokat egy adatkészlethez a Power BI szolgáltatásban? Akkor is működnek, ha nem teszek semmit?  
**Válasz:** Nem, a vizualizációk nem fognak megfelelően renderelődni. Újból létre kell hoznia a szerepköröket és szabályokat a Power BI Desktopban, majd közzé kell tennie őket a Power BI szolgáltatásban.

**Kérdés:** Létrehozhatom ezeket a szerepköröket Analysis Services-adatforrásokhoz?  
**Válasz:** Igen, ha az adatokat a Power BI Desktopba importálta. Ha élő kapcsolatot használ, nem konfigurálhatja az RLS-t a Power BI szolgáltatáson belül, mert a helyszínen van meghatározva az Analysis Services-modellben.

**Kérdés:** RLS-sel korlátozhatom a felhasználóim számára elérhető oszlopok vagy mértékek körét?  
**Válasz:** Nem, ha egy felhasználó hozzáfér egy adott adatsorhoz, a sor összes adatoszlopát láthatja.

**Kérdés:** Lehetővé teszi az RLS, hogy elrejtsem a részletes adatokat, de hozzáférést nyújtsak a vizualizációkban összegzett adatokhoz?  
**Válasz:** Nem. Egy-egy adatsort biztosíthat, de a felhasználók mindig látják a részleteket vagy az összegzett adatokat.

