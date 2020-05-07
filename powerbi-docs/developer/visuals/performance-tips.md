---
title: Teljesítménnyel kapcsolatos tippek
description: Nagy teljesítményű Power BI-vizualizáció készítése
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 04/20/2020
ms.openlocfilehash: 7ebc02b2c459517957425e78438e12e89dc2e1bb
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82196560"
---
# <a name="how-to-build-a-high-performance-power-bi-visual"></a>Nagy teljesítményű Power BI-vizualizáció készítése
Ez a cikk olyan technikákat mutat be, amelyekkel a fejlesztők nagy teljesítményt érhetnek el a vizualizációk megjelenítése során. 

Senki sem szeretné, hogy egy vizualizáció betöltése sokáig tartson, így a megjelenítéskor az utolsó csepp teljesítményt is érdemes kisajtolni a kódból. 

> [!NOTE]
> A platform fejlesztése és megújítása során folyamatosan jelennek meg az API újabb verziói. A Power BI-vizualizációk platformjának és funkcióinak legjobb kihasználása érdekében ajánlott mindig megismerni a legújabb verziót.
>
> A legújabb, **2.1-es verzió** óta a Power BI-vizualizációk betöltési ideje átlagosan 20%-kal javult.

## <a name="power-bi-visual-performance-tips"></a>A Power BI-vizualizációk teljesítményével kapcsolatos tippek
A továbbiakban néhány javaslatot teszünk a vizualizációk optimális teljesítményének elérésére. 

### <a name="use-user-timing-api"></a>Használja a User Timing API-t
Az alkalmazás JavaScript-teljesítményét a **User Timing API** használatával mérve könnyebb eldönteni, hogy szkript mely részei szorulnak optimalizálásra.

További információ: [User Timing API](https://msdn.microsoft.com/library/hh772738(v=vs.85).aspx).

### <a name="review-animation-loops"></a>Vizsgálja felül az animációs ciklusokat
Újrarajzol az animációs ciklus módosítatlan elemeket? 

 - Probléma: A képkockák között nem módosuló elemek megrajzolása időveszteséggel jár.

 - Megoldás: Frissítse szelektíven a képkockákat. 
 
Statikus vizualizációk animálásakor erős a kísértés, hogy a rajzoló kódot egy frissítő függvénybe szúrjuk be és az animációs ciklus minden iterációjában ismételten meghívjuk az új adatokkal.

Ehelyett érdemes azt az eljárást követni, hogy ami statikus, azt egy konstruktor metódussal rajzoltatja meg, majd a frissítő függvénynek csak a vizualizáció módosuló elemeit kell megrajzolnia. 

   > [!TIP]
   > Alacsony hatékonyságú animációs ciklusok gyakran fordulnak elő tengelyeknél és jelmagyarázatoknál.

### <a name="cache-dom-nodes"></a>Gyorsítótárazza a DOM-csomópontokat 
Egy csomópont vagy csomópont-lista DOM-ból való lekérésekor figyelembe kell venni, hogy azok felhasználhatók-e újra a későbbi számításokban (olykor mindjárt a következő iterációban). Amíg nincs szükség további csomópontok felvételére vagy törlésére az érintett területen, addig a gyorsítótárazás javíthatja az alkalmazás általános hatékonyságát.

Annak érdekében, hogy a kód gyors legyen, és ne lassítsa le a böngészőt, a lehető legkevesebb DOM-elérésre kell törekedni. 

- Előtte: 

   ```javascript
   public update(options: VisualUpdateOptions) { 
       let axis = $(".axis"); 
   }
   ```

- Utána: 

   ```javascript
   public constructor(options: VisualConstructorOptions) { 
       this.$root = $(options.element); 
       this.xAxis = this.$root.find(".xAxis"); 
   } 
 
   public update(options: VisualUpdateOptions) { 
       let axis = this.axis; 
   }
   ```

### <a name="avoid-dom-manipulation"></a>Kerülje a DOM manipulálását 
A DOM-manipulációkat érdemes a legszükségesebbekre korlátozni.  Az olyan beszúrási műveletek, mint a `prepend()`, az `append()` és az `after()` időigényesek, és csak szükség esetén használandók.

Ilyenek például a következők:

  ```javascript
  for (let i=0; i<1000; i++) { 
      $('#list').append('<li>'+i+'</li>');
  }
  ```

A fenti példa felgyorsítható a `html()` használatával, és azzal, hogy a listát előre elkészíti: 

  ```javascript
  let list = ''; 
  for (let i=0; i<1000; i++) { 
      list += '<li>'+i+'</li>'; 
  } 

  $('#list').html(list); 
  ```

### <a name="reconsider-jquery"></a>Értékelje át a JQuery-t

Ha korlátozza a JS keretrendszerek használatát, és ha csak lehetséges, natív JS-t használ, növelheti a rendelkezésre álló sávszélességet, és csökkentheti a feldolgozási többletmunkát. Ezzel egyben a régebbi böngészőkkel fellépő kompatibilitási problémák egy részét is kiiktatja. 

Erről további információkat nyújt a [youmightnotneedjquery.com](http://youmightnotneedjquery.com/) oldal, ahol a `show`, a `hide`, az `addClass` és más JQuery-függvények helyett használható példákat is talál.  

### <a name="use-canvas-or-webgl"></a>Használjon vásznat vagy a WebGL-t 
Gyakran használt animációkhoz mérlegelje a **canvas** vagy a **WebGL** használatát SVG helyett. Az SVG-vel ellentétben ezeknél a teljesítményt nem a tartalom, hanem a méret határozza meg. 

A különbségek részletesebb ismertetése: [SVG vagy Canvas: Mi alapján válasszon?](https://msdn.microsoft.com/library/gg193983(v=vs.85).aspx) 

### <a name="use-requestanimationframe-instead-of-settimeout"></a>Használja a requestAnimationFrame műveletet a setTimeout helyett 
Ha a képernyőn megjelenő animációkat a [requestAnimationFrame](https://www.w3.org/TR/animation-timing/) használatával frissíti, akkor az animációs függvények az **előtt** lesznek meghívva, hogy a böngésző meghívna egy újrafestést.

Erről további információt talál a `requestAnimationFrame` használatával készült [példában](https://testdrive-archive.azurewebsites.net/Graphics/RequestAnimationFrame/Default.html).

## <a name="next-steps"></a>Következő lépések

További tudnivalók az optimalizálási technikákról: [Optimalizálási útmutató a Power BI-hoz](/power-bi/guidance/power-bi-optimization).
