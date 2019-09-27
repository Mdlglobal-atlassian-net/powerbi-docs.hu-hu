---
title: Indítási URL-cím létrehozása
description: Ez a cikk bemutatja, hogyan nyithat meg egy URL-címet egy új lapon Power BI-vizualizációkkal.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 281cbcd92deced8ec49bcd846e498922c7aae66d
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/23/2019
ms.locfileid: "71193932"
---
# <a name="create-a-launch-url"></a>Indítási URL-cím létrehozása

Indítási URL-cím létrehozásával új böngészőlapot (vagy -ablakot) nyithat meg a tényleges munka a Power BI-nak való delegálásával.

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

* Csak abszolút elérési utakat használjon, relatívokat ne. Példa egy abszolút elérési útra: `http://some.link.net/subfolder/page.html`. A `/page.html` relatív elérési út nem nyílik meg.

* Jelenleg csak a *HTTP* és *HTTPS* protokollok támogatottak. Ne használjon *FTP*, *MAILTO* és hasonló protokollokat.

## <a name="best-practices"></a>Ajánlott eljárások

* A legtöbb esetben célszerű csak egy felhasználó explicit műveletére reagálva megnyitni egy hivatkozást. Tegye könnyen érthetővé a felhasználó számára, hogy a hivatkozásra vagy gombra kattintva új lap nyílik meg. Egy `launchUrl()` hívás aktiválása felhasználói művelet nélkül vagy egy másik művelet mellékhatásaként zavaró és bosszantó lehet a felhasználónak.

* Ha a hivatkozás nem elengedhetetlen a vizualizáció megfelelő működéséhez, érdemes lehetővé tenni a jelentés szerzőjének, hogy letilthassa és elrejtse a hivatkozást. Ez különösen fontos különleges Power BI-forgatókönyvekben, például egy jelentés külső alkalmazásba való beágyazásakor vagy a weben való közzétételekor.

* Ne indítson `launchUrl()` hívást hurkon belül, a vizualizáció `update` függvényén belül, vagy egyéb gyakran ismétlődő kódban.

## <a name="a-step-by-step-example"></a>Részletes példa

### <a name="add-a-link-launching-element"></a>Hivatkozásindítási elem hozzáadása

A vizualizáció `constructor` függvényéhez a következő sorok lettek hozzáadva:

```typescript
    this.helpLinkElement = this.createHelpLinkElement();
    options.element.appendChild(this.helpLinkElement);
```

Bővült egy privát függvénnyel, amely a horgonyelemet hozza létre és csatolja:

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

Végül a *visual.less* fájl egyik bejegyzése definiálja a hivatkozási elem stílusát:

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

### <a name="add-a-toggling-mechanism"></a>Váltómechanizmus hozzáadása

Váltómechanizmus hozzáadásához egy statikus objektumot kell hozzáadnia, hogy a jelentés szerzője váltani tudjon a hivatkozáselem láthatósági beállításai között. (Az alapértelmezett beállítás a *rejtett* állapot.) További információért tekintse meg a [statikus objektumok oktatóanyagát](https://microsoft.github.io/PowerBI-visuals/docs/concepts/objects-and-properties).

A *capabilities.json* fájl objektumainak bejegyzése egy `showHelpLink` logikai statikus objektummal bővült, ahogyan az a következő kódban látható:

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

A *rejtett* osztály a *visual.less* fájlban van definiálva, és az elem megjelenítését vezérli.
