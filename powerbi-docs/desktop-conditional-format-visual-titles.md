---
title: Címek kifejezésen alapuló Power BI desktopban
description: A dinamikus címek létrehozása a Power BI Desktopban módosító programozott arckifejezések alapján programozott feltételes formázás használatával
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: reference
ms.date: 04/10/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b90ef66d2c118a70f1b18ed4fe302ce1db23e45c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "64769737"
---
# <a name="expression-based-titles-in-power-bi-desktop"></a>Címek kifejezésen alapuló Power BI desktopban

Létrehozhat dinamikus, testre szabott, hogy a Power BI-Vizualizációk címei. Data Analysis Expressions (DAX) mezőket, változóit vagy egyéb programozható elemek alapján hoz létre, a Vizualizáció címét is automatikusan szükség szerint módosítsa. Ezek a változások szűrőket, beállításokat is, vagy más felhasználói interakció érdekében és konfigurációk alapulnak.

![Képernyőfelvétel: a Power BI Desktop feltételes formázási lehetőség](media/desktop-conditional-formatting-visual-titles/expression-based-title-01.png)

Más néven dinamikus címek létrehozása *kifejezésen alapuló címek*, nagyon egyszerű. 

## <a name="create-a-field-for-your-title"></a>A cím mező létrehozása

Az első lépés egy kifejezésen alapuló cím létrehozása, ha egy mezőt a modellben a cím használatára. 

Számos adatforráshoz creative módja is van a Vizualizáció címének tükrözzék, mit kíván tegyük fel, vagy szeretné express. Vessünk egy pillantást néhány példa erre.

Létrehozhat egy kifejezés, amely a szűrőkörnyezet, amely a Vizualizáció megkapja a termék márkáját neveként függően változik. Az alábbi képen látható a DAX-képlet ilyen mező.

![Képernyőkép a DAX-képlet](media/desktop-conditional-formatting-visual-titles/expression-based-title-02.png)

Egy másik példa, amely a felhasználó nyelvi és kulturális környezet függően változik dinamikus címet használ. A DAX-mérték a nyelvspecifikus címek is létrehozhat a `USERCULTURE()` függvény. Ez a függvény a felhasználó számára, hogy operációs rendszer vagy a böngésző beállításai alapján a kulturális környezet kódot adja vissza. A következő DAX-switch utasítás segítségével válassza ki a megfelelő lefordított értéket. 

```
SWITCH (
  USERCULTURE(),
  "de-DE", “Umsatz nach Produkt”,
  "fr-FR", “Ventes par produit”,
  “Sales by product”
)
```

Vagy lehet lekérdezni a karakterlánc egy keresési táblázat, amely tartalmazza a megjelenő fordításokat. A modell helyez, hogy a táblázat. 

Ezek a példák segítségével dinamikus, kifejezésalapú címek, hogy a Vizualizációk létrehozása a Power BI Desktopban néhány. Mire képes a címek a korlátozottak, csak a képzelete, és a modell által.


## <a name="select-your-field-for-your-title"></a>Válassza ki a mezőt, a cím

Miután létrehozta a mező a modellben létrehozott DAX-kifejezése, alkalmazza a Vizualizáció címének kell.

Válassza ki a mezőt, és alkalmazza azt, hogy nyissa meg a **Vizualizációk** ablaktáblán. Az a **formátum** területen válassza **cím** a Vizualizáció a cím lehetőségeinek megjelenítéséhez. 

Amikor a jobb gombbal **címszöveget**, egy helyi menü megjelenik, amely lehetővé teszi, hogy válasszon ***fx * feltételes formázás**. A menüelem kiválasztásakor egy **címszöveget** párbeszédpanel jelenik meg. 

![Képernyőkép a cím szövegének párbeszédpanel](media/desktop-conditional-formatting-visual-titles/expression-based-title-02b.png)

Ezt az ablakot kiválaszthatja a mező, a cím használni létrehozott.

## <a name="limitations-and-considerations"></a>Korlátozások és szempontok

Néhány korlátozás címeit kifejezésen alapuló vizualizációkat az aktuális végrehajtásával:

* Kifejezés alapú formázás jelenleg nem támogatott Vizualizációk Python, R-Vizualizációk vagy a kulcs Véleményvezérek vizualizációt.
* A hoz létre, a cím mező kifejezésnek karakteres adattípusúnak kell lennie. Mértékek, szám vagy dátum/idő (vagy bármely más adattípussal) visszaadó jelenleg nem támogatottak.

## <a name="next-steps"></a>Következő lépések

Ez a cikk ismerteti a létrehozása, amely szerint a jelentések használata a felhasználók használják módosíthatók dinamikus mezők a Vizualizációk címei információkká DAX-kifejezésekre. Hasznosak lehetnek a következő cikkeket is.

* [Kereszt-jelentés részletezés használata a Power BI Desktopban](desktop-cross-report-drill-through.md)
* [Részletezés használata a Power BI Desktopban](desktop-drillthrough.md)