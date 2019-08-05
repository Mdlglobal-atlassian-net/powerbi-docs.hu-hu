---
title: Kontrasztos mód támogatása
description: Kontrasztos mód támogatásának hozzáadása Power BI-vizualizációkhoz
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: cb77ea012fdfdbd5be62c58c6f9b94a0355db1a9
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424930"
---
# <a name="high-contrast-mode-support"></a>Kontrasztos mód támogatása

A Windows *Kontrasztos* beállításával a szövegek és alkalmazások a jobban elkülönülő színek használatának köszönhetően jobban láthatók lesznek.
További tudnivalók a [kontrasztos mód Power BI általi támogatásáról](https://powerbi.microsoft.com/blog/power-bi-desktop-june-2018-feature-summary/#highContrast).

A kontrasztos mód vizualizációkhoz való felvételéhez a következők szükségesek:

1. Inicializáláskor: Annak észlelése, hogy a Power BI kontrasztos módban van-e, és ha igen, akkor az aktuális kontrasztos színek lekérése.
2. Minden frissítéskor: A vizualizáció renderelési módjának módosítása a jobb láthatóság érdekében.

A PowerBI-visuals-sampleBarChart vizualizációban implementálva van a kontrasztos megjelenítés támogatása.

További információt a [PowerBI-visuals-sampleBarChart vizualizáció adattárában](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/61011c82b66ca0d3321868f1d089c65101ca42e6) találhat

## <a name="on-init"></a>Inicializáláskor

Az `options.host` colorPalette tagja számos tulajdonsággal rendelkezik a kontrasztos módhoz. Ezen a tulajdonságok alapján határozható meg, hogy aktív-e a kontrasztos mód, és ha igen, milyen színek használhatók.

### <a name="detect-that-power-bi-is-in-high-contrast-mode"></a>A Power BI kontrasztos módjának észlelése

Ha a `host.colorPalette.isHighContrast` értéke `true`, akkor a kontrasztos mód aktív, és a vizualizációnak ennek megfelelően kell kirajzolódnia.

### <a name="get-high-contrast-colors"></a>A kontrasztos színek lekérése

Kontrasztos módban a vizualizációnak az alábbi színekre kell szorítkoznia:

* Az **előtér** színével rajzol minden vonalat, ikont, szöveget, valamint az alakzatok körvonalát vagy kitöltését.
* A **háttér** színét használja háttérként, valamint a körvonalas alakzatok kitöltőszíneként.
* A **kijelölt előtér** színét használja a kijelölt vagy aktív elemek jelölésére.
* A **hivatkozások** színét csak a hivatkozások szövegéhez használja.

> [!NOTE]
> Ha másodlagos színre van szükség, akkor az előtérszín bizonyos mértékű átlátszósággal (natív Power BI-vizualizációk esetén 40%) használható. Ez ritkán használandó, hogy a vizualizáció részletei jól láthatóak maradjanak.

Ezeket az értékeket tárolhatja az inicializálás során:

```typescript
private isHighContrast: boolean;

private foregroundColor: string;
private backgroundColor: string;
private foregroundSelectedColor: string;
private hyperlinkColor: string;
//...

constructor(options: VisualConstructorOptions) {
    this.host = options.host;
    let colorPalette: ISandboxExtendedColorPalette = host.colorPalette;
    //...
    this.isHighContrast = colorPalette.isHighContrast;
    if (this.isHighContrast) {
        this.foregroundColor = colorPalette.foreground.value;
        this.backgroundColor = colorPalette.background.value;
        this.foregroundSelectedColor = colorPalette.foregroundSelected.value;
        this.hyperlinkColor = colorPalette.hyperlink.value;
    }
```

Azt is megteheti, hogy inicializáláskor a `host` objektumot tárolja, és frissítéskor hozzáfér a vonatkozó `colorPalette` tulajdonságokhoz.

## <a name="on-update"></a>Frissítéskor

A kontrasztos mód támogatásának egyes implementációi vizualizációnként változnak és a grafikai kivitel részleteitől függnek. A kontrasztos mód általában az alapértelmezettől kissé eltérő tervezést igények, hogy a lényeges részletek kevesebb szín használata mellett is jól elkülönüljenek.

Az alábbiak a natív Power BI-vizualizációk által betartott irányelvek:

* Minden adatpont ugyanazt a színt használja (előtér).
* Minden szöveg, tengely, nyíl, vonal stb. az előtérszínt használja.
* A vastag alakzatok körvonalakkal vannak megrajzolva, vastag (legalább kettő képpontos) vonalakkal, és a háttérszínnel vannak kitöltve.
* Szükség esetén az adatpontok eltérő jelölőalakzatokkal, az adatvonalak pedig különböző szaggatással vannak megkülönböztetve.
* Egy adatelem kiemelésekor az összes többi elem átlátszósága 40%-ra módosul.
* Szeletelők esetén az aktív szűrőelemek a kijelölési előtérszínt használják.

A sampleBarChart esetében például minden sáv két képpontos előtérszínű körvonallal, a háttérszínnel kitöltve jelenik meg. Összehasonlíthatja az alapértelmezett színekkel és néhány kontrasztos témával megjelenő változatokat:

![A sampleBarChart szabványos színekben](./media/hc-samplebarchart-standard.png)
![A sampleBarChart a *Sötét #2* téma használatával](./media/hc-samplebarchart-dark2.png)
![A sampleBarChart a *Fehér* téma használatával](./media/hc-samplebarchart-white.png)

Az alábbi a `visualTransform` függvény egyik részlete, amely a kontrasztos mód támogatásához lett módosítva, és a renderelés részeként van meghívva `update` során:

### <a name="before"></a>Előtte

```typescript
for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
    let defaultColor: Fill = {
        solid: {
            color: colorPalette.getColor(category.values[i] + '').value
        }
    };

    barChartDataPoints.push({
        category: category.values[i] + '',
        value: dataValue.values[i],
        color: getCategoricalObjectValue<Fill>(category, i, 'colorSelector', 'fill', defaultColor).solid.color,
        selectionId: host.createSelectionIdBuilder()
            .withCategory(category, i)
            .createSelectionId()
    });
}
```

### <a name="after"></a>Utána

```typescript
for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
    const color: string = getColumnColorByIndex(category, i, colorPalette);

    const selectionId: ISelectionId = host.createSelectionIdBuilder()
        .withCategory(category, i)
        .createSelectionId();

    barChartDataPoints.push({
        color,
        strokeColor,
        strokeWidth,
        selectionId,
        value: dataValue.values[i],
        category: `${category.values[i]}`,
    });
}

//...

function getColumnColorByIndex(
    category: DataViewCategoryColumn,
    index: number,
    colorPalette: ISandboxExtendedColorPalette,
): string {
    if (colorPalette.isHighContrast) {
        return colorPalette.background.value;
    }

    const defaultColor: Fill = {
        solid: {
            color: colorPalette.getColor(`${category.values[index]}`).value,
        }
    };

    return getCategoricalObjectValue<Fill>(category, index, 'colorSelector', 'fill', defaultColor).solid.color;
}
```
