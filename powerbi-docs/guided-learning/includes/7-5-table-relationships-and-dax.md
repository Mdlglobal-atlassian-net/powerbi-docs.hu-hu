---
ms.openlocfilehash: 679c3e8c3d94c93899e9dcfae1e57f4b678fb218
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "73799901"
---
A Power BI-ban kapcsolatokat alakíthat ki egyszerre több táblázat között is, beleértve a teljesen eltérő adatforrásból származókat. Az adatmodellek kapcsolatait a Power BI Desktop **Kapcsolatok** nézetében tekintheti meg.

![](media/7-5-table-relationships-and-dax/dax-relationships_1.png)

## <a name="dax-relational-functions"></a>A DAX relációs függvényei
A DAX **relációs függvényei** lehetővé teszik a létesített kapcsolatokkal rendelkező táblák kezelését.

A DAX-függvények segítségével eredményként visszaadhatja egy adott oszlop értékét, vagy akár egy kapcsolat összes sorát.

Például a **RELATED** (kapcsolódó) függvény a kapcsolódásokat követve visszaadja egy oszlop értékét, míg a **RELATEDTABLE** (kapcsolódó táblázat) követi a kapcsolódást, és egy kapcsolódó sorokra szűrt teljes táblázatot ad vissza eredményként.

![](media/7-5-table-relationships-and-dax/dax-relationships_2.png)

A **RELATED** (kapcsolódó) függvény *több-az-egyhez* típusú kapcsolatoknál használható, a **RELATEDTABLE** pedig *egy-a-többhöz* típusúaknál.

A relációs függvények használatával olyan kifejezéseket hozhat létre, amelyek több különböző táblázat értékeit tartalmazzák. A DAX a kapcsolati lánc hosszától függetlenül mindig visszaadja ezeknek a függvényeknek az eredményét.

> A videótartalomért köszönet illeti [Alberto Ferrarit az SQLBI-tól](https://www.sqlbi.com/learning-dax)
> 
> 

