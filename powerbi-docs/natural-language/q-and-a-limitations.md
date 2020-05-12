---
title: A Power BI Q&A korlátozásai
description: A Power BI Q&A jelenlegi korlátozásai
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/21/2020
ms.author: maggies
ms.openlocfilehash: b71fd2986fb79adf88493416ac8234f2656aefa9
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/06/2020
ms.locfileid: "82866771"
---
# <a name="limitations-of-power-bi-qa"></a>A Power BI Q&A korlátozásai

A Power BI Q&A jelenlegi rendelkezik néhány korlátozással.

## <a name="data-sources"></a>Adatforrások

### <a name="supported-data-sources"></a>Támogatott adatforrások

A Power BI Q&A az adatforrások következő konfigurációit támogatja a Power BI szolgáltatásban:

- Importálás mód
- Élő kapcsolat az Azure Analysis Servicesszel
- Élő kapcsolat az SQL Server Analysis Servicesszel (átjárón keresztül)
- Power BI-adathalmazok.

Ezeknek a konfigurációknak mindegyikében a sorszintű biztonság is támogatott.

### <a name="data-sources-not-supported"></a>Nem támogatott adatforrások

A Power BI Q&A jelenleg nem támogatja a következő konfigurációkat:

- Objektumszintű biztonság bármilyen típusú adatforrással
- DirectQuery bármilyen forrásból. Kerülő megoldás a Live Connect használata az Azure Analysis Servicesszel, amely DirectQueryt használ.
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

- Country (Ország), amely az USA
- Country (Ország), amely nem az USA
- Termékek > 100
- 100-nál nagyobb termékek
- Termékek = 100
- Termékek 100
- Termékek < 100
- 100-nál kisebb termékek

> [!NOTE]
> A Q&A eszközkezelése csak az importálási módot támogatja. Még nem támogatja a helyszíni vagy Azure Analysis Servicesbeli adatforráshoz való kapcsolódást. A Power BI későbbi kiadásaiban ez a jelenlegi korlátozás el lesz távolítva.

### <a name="statements-not-supported"></a>Nem támogatott utasítások

- A mértékek használata a feltételekben jelenleg nem támogatott. Ehelyett alakítsa át a mértékeket a számított oszlopokra, hogy működjenek.
- Több feltétel használata nem támogatott. Megkerülő megoldásként hozzon létre egy DAX-alapú számított oszlopot, amely több feltételű logikai utasítást értékel ki, és inkább ezt a mezőt használja.
- Ha nem ad meg szűrési feltételt, amikor a Q&A az adatok egy részhalmazát kéri, akkor nem tudja menteni a definíciót, még akkor sem, ha a teljes utasítás nem tartalmaz vörös aláhúzást.

## <a name="next-steps"></a>Következő lépések

A természetes nyelvi motor fejlesztéséhez számos ajánlott eljárás áll rendelkezésre. További információ: [Q&A – Ajánlott eljárások](q-and-a-best-practices.md).