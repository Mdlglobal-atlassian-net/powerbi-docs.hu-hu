---
title: A Power BI Q&A korlátozásai
description: A Power BI Q&A jelenlegi korlátozásai
author: mohaali
manager: mohaali
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/18/2019
ms.author: mohaali
ms.openlocfilehash: fc4a605f1258bcd93e0b49b596cc3a1691ce2edb
ms.sourcegitcommit: 26123c6bb24c8174beb390f4e06fb938d31238ea
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72717540"
---
# <a name="limitations-of-power-bi-qa"></a>A Power BI Q&A korlátozásai

A Power BI Q&A jelenlegi rendelkezik néhány korlátozással.

## <a name="data-sources"></a>Adatforrások

### <a name="supported-data-sources"></a>Támogatott adatforrások

A Power BI Q&A az adatforrások következő konfigurációit támogatja a Power BI szolgáltatásban:

- Importálás mód
- Élő kapcsolat az Azure Analysis Servicesszel
- Élő kapcsolat az SQL Server Analysis Servicesszel (átjárón keresztül)
- Power BI-adathalmazok. A Power BI Desktop a Q&A hibáját jelenti egy Power BI-adathalmaz használatakor. Amikor azonban a jelentést közzéteszi a Power BI szolgáltatásban, a hiba eltűnik.

Ezeknek a konfigurációknak mindegyikében a sorszintű biztonság is támogatott.

### <a name="data-sources-not-supported"></a>Nem támogatott adatforrások

A Power BI Q&A jelenleg nem támogatja a következő konfigurációkat:

- Objektumszintű biztonság bármilyen típusú adatforrással
- DirectQuery bármilyen forrásból. Ennek a támogatásához kerülő megoldás a Live Connect használata az Azure Analysis Servicesszel, amely DirectQueryt használ.
- Összetett modellek
- Reporting Services 

## <a name="tooling-limitations"></a>Eszközhasználat korlátozásai

Az új eszközhasználati párbeszédpanel lehetővé teszi a felhasználók számára a természetes nyelv testreszabását és javítását a Q&A-ben. Ha többet szeretne megtudni az eszközhasználatról, olvassa el a [Bevezető a Q&A eszközhasználatába](q-and-a-tooling-intro.md) szakaszt.

## <a name="review-question-limitations"></a>A felülvizsgálati kérdések korlátozása

A felülvizsgálati kérdések az adatmodellel kapcsolatban feltett kérdéseket legfeljebb 28 napig tárolják. Az új felülvizsgálati kérdések funkció használatakor észreveheti, hogy a rendszer néhány kérdést nem rögzít. Ez szándékosan van így, mivel a természetes nyelvi motor adattörlési lépések sorát hajtja végre, így biztosítva, hogy a rendszer ne rögzítse vagy jelenítse meg a felhasználó minden billentyűleütését.

A bérlői rendszergazdák használhatják a bérlői rendszergazdai beállításokat a kérdéstárolási képesség kezelésére. Az engedélyek biztonsági csoportokon alapulnak. 

A felhasználók úgy is megakadályozhatják a kérdéseik rögzítését, hogy a **Beállítások** > **Általános** menüpontot választják, majd törlik a **Kifejezés rögzítésének engedélyezése a Q&A számára** kijelölését. 

## <a name="teach-qa-limitations"></a>A Q&A tanítása korlátai

A Q&A tanítása kétféle hiba javítását teszi lehetővé:

- Szó hozzárendelése egy mezőhöz.
- Szó hozzárendelése egy szűrési feltételhez.

Jelenleg nem támogatott a felismert kifejezések újradefiniálása vagy más típusú feltételek vagy kifejezések definiálása. Emellett a szűrési feltételek meghatározásakor csak a nyelv korlátozott részhalmazát használhatja, beleértve a következőket:

- „Country” (ország), amely az „USA”
- „Country” (ország), amely nem az „USA”
- „Weight” (súly) > 2000
- „Weight” (súly) = 2000
- „Weight” (súly) < 2000

> [!NOTE]
> A Q&A eszközkezelése csak az importálási módot támogatja. Még nem támogatja a helyszíni vagy Azure Analysis Servicesbeli adatforráshoz való kapcsolódást. A Power BI későbbi kiadásaiban ez a jelenlegi korlátozás el lesz távolítva.

### <a name="statements-not-supported"></a>Nem támogatott utasítások

- A mértékek használata a feltételekben jelenleg nem támogatott. Ehelyett alakítsa át a mértékeket a számított oszlopokra, hogy működjenek.
- Több feltétel használata nem támogatott. Megkerülő megoldásként hozzon létre egy DAX-alapú számított oszlopot, amely több feltételű logikai utasítást értékel ki, és inkább ezt a mezőt használja.
- Ha nem ad meg szűrési feltételt, amikor a Q&A az adatok egy részhalmazát kéri, akkor nem tudja menteni a definíciót, még akkor sem, ha a teljes utasítás nem tartalmaz vörös aláhúzást.
