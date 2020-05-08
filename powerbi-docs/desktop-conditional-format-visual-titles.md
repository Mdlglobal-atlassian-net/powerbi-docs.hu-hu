---
title: Kifejezésalapú címek a Power BI Desktopban
description: Dinamikus, programozott kifejezések alapján változó címek létrehozása feltételes programozott formázás használatával a Power BI Desktopban
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: reference
ms.date: 04/10/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f3c1f047e3be7520005458294381877d1198ee21
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "73878633"
---
# <a name="expression-based-titles-in-power-bi-desktop"></a>Kifejezésalapú címek a Power BI Desktopban

Dinamikus, testreszabott címeket hozhat létre Power BI-vizualizációihoz. Mezőkön, változókon és más programozott elemeken alapuló adatelemzési (DAX-) kifejezések létrehozásával elérheti, hogy a vizualizáció címei automatikusan az igényeihez igazodjanak. Ezek a változások szűrőkön, kijelöléseken és más felhasználói beavatkozásokon és konfigurációkon alapulnak.

![Képernyőkép a Power BI Desktop feltételes formázási lehetőségéről](media/desktop-conditional-formatting-visual-titles/expression-based-title-01.png)

A dinamikus, más néven *kifejezésalapú címek* kézenfekvő módon hozhatók létre. 

## <a name="create-a-field-for-your-title"></a>Mező létrehozása a cím számára

A kifejezésalapú cím létrehozásának első lépése a címhez használandó mező létrehozása a modellben. 

Sokféle ötletes módon elérhető, hogy a vizualizáció címe azt tükrözze, amit tudatni akar általa, vagy amit ki szeretne fejezni vele. Tekintsünk át néhány példát.

Létrehozhat egy kifejezést, amely a vizualizáció által kapott, a termék márkanevére vonatkozó szűrőkörnyezet alapján változik. Az alábbi ábra egy ilyen mező DAX-képletét mutatja be.

![DAX-képlet képernyőképe](media/desktop-conditional-formatting-visual-titles/expression-based-title-02.png)

Egy másik példa a felhasználó nyelve vagy kultúrája alapján változó dinamikus cím használata. Egy DAX-mértékben a `USERCULTURE()` függvény használatával hozhat létre nyelvspecifikus címeket. Ez a függvény a felhasználó kultúrakódját adja vissza az operációs rendszer vagy a böngésző beállításai alapján. Az helyes lefordított érték a következő elágazási DAX-utasítással választható ki. 

```
SWITCH (
  USERCULTURE(),
  "de-DE", “Umsatz nach Produkt”,
  "fr-FR", “Ventes par produit”,
  “Sales by product”
)
```

A sztringet egy olyan keresőtáblázatból is beszerezheti, amely minden fordítást tartalmaz. Ezt a táblázatot el kell helyeznie a modellben. 

Ez csak néhány példa arra, ahogyan a dinamikus, kifejezésalapú címeket használhatja vizualizációkhoz a Power BI Desktopban. Hogy mit valósít meg ezekkel a címekkel, annak csak a képzelete és a modell szab határt.


## <a name="select-your-field-for-your-title"></a>A címhez tartozó mező kiválasztása

A modellben létrehozott mezőhöz tartozó DAX-kifejezés létrehozása után alkalmaznia kell azt a vizualizáció címére.

A mező kiválasztásához és alkalmazásához nyissa meg a **Vizualizációk** panelt. A **Formázás** területen válassza a **Cím** lehetőséget a vizualizáció címére vonatkozó beállítások megjelenítéséhez. 

Ha jobb gombbal a **Title text** (Cím szövege) elemre kattint, megjelenik egy helyi menü, amelyből kiválaszthatja az **<em>fx</em>Conditional formatting** (Feltételes formázás) elemet. Ha erre a menüelemre kattint, megjelenik egy **Cím szövege** párbeszédpanel. 

![A Cím szövege párbeszédpanel képernyőképe](media/desktop-conditional-formatting-visual-titles/expression-based-title-02b.png)

Ebben az ablakban kiválaszthatja a cím számára létrehozott mezőt.

## <a name="limitations-and-considerations"></a>Korlátozások és megfontolandó szempontok

A vizualizációk kifejezésalapú címeinek aktuális implementációjára vonatkozik néhány korlátozás:

* A kifejezésalapú formázás jelenleg nincs támogatva Python-vizualizációkban, R-vizualizációkban és a Főbb befolyásolók vizualizációban.
* A címhez létrehozott mezőnek szöveges adattípusúnak kell lennie. A számokat vagy dátumot és időt (vagy más adattípust) visszaadó mértékek jelenleg nincsenek támogatva.
* A kifejezésalapú címek nem vihetők át, amikor egy vizualizációt rögzít az irányítópulton.

## <a name="next-steps"></a>További lépések

Ez a cikk a vizualizációk címeit dinamikus, a jelentés felhasználónak tevékenysége alapján változó mezőkké alakító DAX-kifejezések létrehozását ismertette. A következő cikkeket is hasznosnak találhatja.

* [Táblázatok feltételes formázása](desktop-conditional-table-formatting.md)
* [Jelentésközi részletezés a Power BI Desktopban](desktop-cross-report-drill-through.md)
* [Részletezés használata a Power BI Desktopban](desktop-drillthrough.md)
