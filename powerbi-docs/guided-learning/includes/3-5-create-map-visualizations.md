---
ms.openlocfilehash: 033436e7078723508d6b9481807ace424c3f109f
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "61397765"
---
A Power BI két típusú térképi vizualizációval rendelkezik: egy buboréktérkép, amely egy földrajzi pont felé helyez egy buborékot, és egy alakzattérkép, amely a megjeleníteni kívánt terület körvonalát rajzolja meg.

![](media/3-5-create-map-visualizations/3-5_1.png)

> [!NOTE]
> Amikor országokkal vagy régiókkal dolgozik, használja a három betűből álló rövidítéseket, így meggyőződhet róla, hogy a térképes vizualizációk geokódolása megfelelően működik. *Ne* használjon kétbetűs rövidítéseket, mert ez esetben lehetséges, hogy egyes országok vagy régiók felismerése nem történik meg megfelelően.
> Ha csak a kétbetűs rövidítéseket ismeri, tekintse meg ezt a [külső blogbejegyzést](https://blog.ailon.org/how-to-display-2-letter-country-data-on-a-power-bi-map-85fc738497d6#.yudauacxp), amely az országok és régiók kétbetűs rövidítéseinek a hárombetűs rövidítéseknek való megfeleltetését ismerteti.
> 
> 

## <a name="create-bubble-maps"></a>Buboréktérképek létrehozása
Buboréktérkép létrehozásához válassza a **Vizualizációk** ablaktábla **Térkép** elemét. A térképi vizualizációk használatához a **Vizualizációk** beállításai között hozzá kell adnia egy értéket a *Hely* gyűjtőhöz.

![](media/3-5-create-map-visualizations/3-5_2.png)

A Power BI rugalmas a helyszínértékek elfogadását illetően, így az általánosabb részletektől kezdve (például egy városnév vagy egy repülőtér kódja) a legpontosabb szélességi és hosszúsági adatokig mindent elfogad. Ha a buborék méretét a térkép helyszíneinek méreteihez szeretné igazítani, adjon hozzá egy mezőt a **Méret** gyűjtőhöz.

![](media/3-5-create-map-visualizations/3-5_3.png)

## <a name="create-shape-maps"></a>Alakzatleképezések létrehozása
Alakzatleképezés létrehozásához válassza a Vizualizációk ablaktábla **Kartogram** elemét. A buboréktérképekhez hasonlóan a vizualizáció használatához hozzá kell adnia egy értéket a Hely gyűjtőhöz. A kitöltés színerősségének megfelelő módosításához adjon hozzá egy mezőt a Méret gyűjtőhöz.

![](media/3-5-create-map-visualizations/3-5_4.png)

A vizualizációs elem bal felső sarkában megjelenő figyelmeztető ikon azt jelzi, hogy a térképnek további helyszínadatokra van szüksége az értékek pontos ábrázolásához. Ez leggyakrabban akkor fordul elő, ha a Hely mező adatai nem egyértelműek, például olyan nevet adott meg, mint a *Washington*, amely egy állam és egy kerület is lehet. A problémát megoldhatja, ha az oszlopnak egy pontosabb nevet ad meg, például *Állam*. Másik lehetőségként kézzel visszaállíthatja az adatkategóriát a Modellezés lap **Adatkategória** elemének kiválasztásával. Ezen a területen hozzárendelhet egy kategóriát az adatokhoz, például az „Állam” vagy a „Város” értéket.

![](media/3-5-create-map-visualizations/3-5_5.png)

