---
title: Jelentésparaméter átadása URL-címben lapszámozott jelentéshez – Power BI jelentéskészítő
description: Ez a témakör azt ismerteti, hogyan adhatók át jelentésparaméterek a jelentéseknek úgy, hogy azokat egy lapszámozott jelentés URL-címében megadjuk.
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.custom: ''
ms.date: 05/01/2020
ms.openlocfilehash: e6e4187f89bb0ae6e6772f29b19782ee7fbfad25
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82692868"
---
# <a name="pass-a-report-parameter-in-a-url-for-a-paginated-report-in-power-bi"></a>Jelentésparaméter átadása URL-címben lapszámozott jelentéshez a Power BI-ban 

Jelentésparaméterek úgy adhat át jelentéseknek, hogy azokat egy többoldalas jelentés URL-címében megadja. Minden lekérdezési paraméter rendelkezhet hozzá kapcsolódó jelentésparaméterekkel. Ezért a lekérdezési paramétert úgy adhatja át a jelentésnek, ha átadja a megfelelő jelentésparamétert. A paraméter nevét `rp:` előtaggal kell ellátni, hogy a Power BI felismerje azt az URL-címben. 

A jelentésparaméterek megkülönböztetik a kis- és nagybetűket, és az alábbi speciális karaktereket is használhatják: 

- Az URL-cím paraméter részében szereplő szóköz plusz (+) jelre lesz cserélve.  Példa: 

    ```rp:Holiday=Christmas+Day```

- A sztringben szereplő pontosvesszőt a rendszer `%3A` karakterekre cseréli.

A böngészők feltehetően automatikusan elvégzik a megfelelő URL-kódolást. Önnek nem szükséges manuálisan kódolnia a karaktereket. 

Ha jelentésparamétert szeretne beállítani egy URL-címben, használja az alábbi szintaxist: 

```
rp:parameter=value
```

Ha például a „Salesperson” és a „State” kifejezést szeretné megadni, melyeket a Saját munkaterületen lévő jelentésben definiált, akkor az alábbi URL-címet kell használnia: 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:State=Utah 
```

Ha ugyanezt a két paramétert szeretné megadni, de azok egy jelentésben vannak definiálva, akkor az alábbi URL-címet kell használnia: 

```
https://app.powerbi.com/groups/me/apps/xxxxxxx-c4c4-4217-afd9-3920a0d1e2b0/rdlreports/b1d5e659-639e-41d0-b733-05d2bca9853c?rp:Salesperson=Tiggee&rp:State=Utah 
```

Ha NULL értéket szeretne átadni egy paraméterhez, használja a következő szintaxist: 

```
parameter:isnull=true
```

Példa:

```
rp:SalesOrderNumber:isnull=true
```

Logikai érték átadásához használja a 0 értéket false (hamis) értékhez, az 1-et pedig true (igaz) értékhez. Lebegőpontos érték átadásához adja meg a kiszolgáló területi beállításának decimális elválasztóját.

> [!NOTE]
> Ha a jelentés olyan jelentésparamétert tartalmaz, amely alapértelmezett értékkel rendelkezik, és a **Prompt** tulajdonság értéke **hamis** (azaz a **Prompt User** tulajdonság nincs kiválasztva a Jelentéskezelőben), akkor ahhoz a jelentésparaméterhez nem adhat át értéket URL-címen belül. Ez lehetővé teszi a rendszergazdák számára, hogy megakadályozzák a végfelhasználók számára bizonyos jelentési paraméterek értékének hozzáadását vagy módosítását.
> 
> A Power BI nem támogatja a 2,000 karakternél hosszabb lekérdezési sztringeket.  Ez az érték csak akkor haladható meg, ha URL-paraméterekkel tekinti meg a lapszámozott jelentést.  Ez különösen igaz, ha többértékű paramétereket használ.

## <a name="additional-examples"></a>További példák 

A következő URL-példa egy többértékű „Salesperson” (értékesítő) paramétert tartalmaz. A többértékű paraméterek formátuma az egyes értékekhez tartozó paraméter nevének megismétlése. 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:Salesperson=Mickey 
```

A következő URL-példa a SellStartDate-et egyetlen paraméterként adja át, amelynek értéke „7/1/2005” natív módú jelentéskészítő kiszolgálónak.

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:SellStartDate=7/1/2005
```

## <a name="next-steps"></a>További lépések

- [URL-paraméterek lapszámozott jelentésekben a Power BI-ban](report-builder-url-parameters.md)
- [Mik a lapszámozott jelentések a Power BI Premiumban?](paginated-reports-report-builder-power-bi.md)
