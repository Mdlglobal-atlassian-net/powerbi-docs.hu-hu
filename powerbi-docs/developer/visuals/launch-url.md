---
title: Indítási URL-cím
description: A Power BI vizualizációk új lapon nyithatnak meg URL-címeket
author: Guy-Moses
ms.author: guymos
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 1a7002c3b45f341c0cbc0db683bc4f8a113e21f9
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424861"
---
# <a name="launch-url"></a>Indítási URL-cím

Az Indítási URL-címmel új böngészőlap (vagy -ablak) nyitható meg a tényleges munka a Power BI-nak való delegálásával.

## <a name="sample"></a>Minta

```typescript
   this.host.launchUrl('https://powerbi.microsoft.com');
```

## <a name="usage"></a>Használat

A `host.launchUrl()` API-hívással sztringargumentumként adhatja meg a cél URL-címet:

```typescript
this.host.launchUrl('http://some.link.net');
```

## <a name="restrictions"></a>Korlátozások

* Csak abszolút útvonalakat használjon, relatívokat ne. A `http://some.link.net/subfolder/page.html` útvonal megfelel, a `/page.html` azonban nem nyitható meg.
* Jelenleg csak a `http` és `https` protokollok támogatottak. Ne használjon `ftp` és `mailto`, illetve hasonló protokollokat.

## <a name="best-practices"></a>Ajánlott eljárások

1. A legtöbb esetben célszerű csak egy felhasználó explicit műveletére reagálva megnyitni egy hivatkozást. Tegye könnyen érthetővé a felhasználó számára, hogy a hivatkozásra vagy gombra kattintva új lap nyílik meg. Egy `launchUrl()` hívás aktiválása felhasználói művelet nélkül vagy egy másik művelet mellékhatásaként zavaró és bosszantó lehet a felhasználónak.
2. Ha a hivatkozás nem elengedhetetlen a vizualizáció megfelelő működéséhez, érdemes lehetővé tenni a jelentés szerzőjének, hogy letilthassa és elrejtse a hivatkozást. Ez különösen fontos különleges Power BI-forgatókönyvekben, például egy jelentés külső alkalmazásba való beágyazásakor vagy a weben való közzétételekor.
3. Ne indítson `launchUrl()` hívást hurkon belül, a vizualizáció `update` függvényén belül, vagy egyéb gyakran ismétlődő kódban.

## <a name="step-by-step-example"></a>Részletes példa

### <a name="adding-a-link-launching-element"></a>Hivatkozásindítási elem hozzáadása

A vizualizáció `constructor` függvényéhez a következő sorok lettek hozzáadva:

```typescript
    this.helpLinkElement = this.createHelpLinkElement();
    options.element.appendChild(this.helpLinkElement);
```

Emellett bővült egy privát függvénnyel, amely a horgonyelemet hozza létre és csatolja:

```typescript
private createHelpLinkElement(): Element {
    let linkElement = document.createElement("a");
    linkElement.textContent = "?";
    linkElement.setAttribute("title", "Open documentation");
    linkElement.setAttribute("class", "helpLink");
    linkElement.addEventListener("click", () => {
        this.host.launchUrl("https://docs.microsoft.com/power-bi/developer/custom-visual-develop-tutorial");
    });
    return linkElement;
};
```

Végül a visual.less fájl egyik bejegyzése definiálja a hivatkozási elem stílusát:

```less
.helpLink {
    position: absolute;
    top: 0px;
    right: 12px;
    display: block;
    width: 20px;
    height: 20px;
    border: 2px solid #80B0E0;
    border-radius: 20px;
    color: #80B0E0;
    text-align: center;
    font-size: 16px;
    line-height: 20px;
    background-color: #FFFFFF;
    transition: all 900ms ease;

    &:hover {
        background-color: #DDEEFF;
        color: #5080B0;
        border-color: #5080B0;
        transition: all 250ms ease;
    }

    &.hidden {
        display: none;
    }
}
```

### <a name="adding-a-toggling-mechanism"></a>Váltómechanizmus hozzáadása

Ehhez egy statikus objektumot kell hozzáadni (lásd [a statikus objektumokról szóló oktatóanyagot](https://microsoft.github.io/PowerBI-visuals/docs/concepts/objects-and-properties)), hogy a jelentés szerzője váltani tudjon a hivatkozáselem láthatósági beállításai között (az alapértelmezett beállítás az elrejtett állapot).
Egy `showHelpLink` logikai statikus objektumot adtunk a `capabilities.json` objektumbejegyzéshez:

```typescript
"objects": {
    "generalView": {
            "displayName": "General View",
            "properties":
                "showHelpLink": {
                    "displayName": "Show Help Button",
                    "type": {
                        "bool": true
                    }
                }
            }
        }
    }
```

![Indítási URL-cím kapcsolója](./media/launchurl-toggle.png)

A vizualizáció `update` függvényéhez a következő sorok lettek hozzáadva:

```typescript
if (settings.generalView.showHelpLink) {
    this.helpLinkElement.classList.remove("hidden");
} else {
    this.helpLinkElement.classList.add("hidden");
}
```

A `hidden` osztály a visual.less fájlban van definiálva, és az elem megjelenítését vezérli.
