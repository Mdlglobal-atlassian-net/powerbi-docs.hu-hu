---
ms.openlocfilehash: cd0696b44e285119193059304c89cfa04c755771
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "71409367"
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

**Kérdés:** Az adatforrásomban már vannak definiált biztonsági szerepkörök (például SQL Server-szerepkörök vagy SAP BW-szerepkörök). Mi az összefüggés ezek és a sorszintű biztonság között?  
**Válasz:** A válasz attól függ, hogy importálja az adatokat, vagy DirectQueryt használ. Ha a Power BI-adathalmazba importálja az adatokat, akkor az adatforrásbeli biztonsági szerepkörök nem lesznek használva. Ilyen esetben sorszintű biztonság definiálásával kell érvényesítenie a Power BI-ban csatlakozó felhasználókra vonatkozó biztonsági szabályokat. Ha DirectQueryt használ, akkor az adatforrásbeli biztonsági szabályok lesznek érvényesek. Amikor egy felhasználó jelentést nyit meg, a Power BI lekérdezést küld a mögöttes adatforráshoz, amely a felhasználó hitelesítő adatai alapján érvényesíti az adatokra vonatkozó biztonsági szabályokat.
