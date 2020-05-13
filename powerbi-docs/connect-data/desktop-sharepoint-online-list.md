---
title: Jelentés létrehozása SharePoint-listán
description: Ez az oktatóanyag bemutatja, hogyan alakíthatja át a SharePoint-lista adatait egy Power BI-jelentéssé.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 01/10/2020
ms.author: davidi
LocalizationGroup: Visualizations
ms.openlocfilehash: 4fd350ae5d4a916e6753f7cd66e1fca52137efd5
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83288660"
---
# <a name="create-a-report-on-a-sharepoint-list"></a>Jelentés létrehozása SharePoint-listán

A SharePoint Online-ban számos csapat és szervezet tárol adatokat, mivel egyszerűen beállítható, és a felhasználók könnyen frissíthetnek.  Egy diagrammal néha sokkal egyszerűbben értelmezhetőek az adatok, mintha magát a listát néznénk meg. Ez az oktatóanyag azt mutatja be, hogyan alakíthatja át a SharePoint-lista adatait egy Power BI-jelentéssé.

Tekintse meg ezt az öt perces oktatóvideót, vagy görgessen lefelé a lépésenkénti útmutatóhoz.

<iframe width="400" height="450" src="https://www.youtube.com/embed/OZO3x2NF8Ak" frameborder="0" allowfullscreen></iframe>

## <a name="part-1-connect-to-your-sharepoint-list"></a>1\. rész: Kapcsolódás a SharePoint-listához

1. Ha még nem rendelkezik a Power BI Desktoppal, itt [letöltheti](https://powerbi.microsoft.com/desktop/) és telepítheti.
2. Nyissa meg Power BI Desktopot, majd a menüszalag Kezdőlapján válassza az **Adatok lekérése** > **Tovább** lehetőséget.
3. Válassza az **Online szolgáltatások**, majd a **SharePoint Online-lista** lehetőséget.  

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-getdata.png" alt="get data" width="350"/>

4. Kattintson a **Csatlakozás** gombra.
4. Keresse meg annak a SharePoint Online webhelynek a címét (URL-jét), amely a listát tartalmazza.  A SharePoint Online oldalán a webhelycímet általában úgy találhatja meg, ha a navigációs panelen a **Kezdőlap** lehetőséget vagy az oldal tetején található webhelyikont választja, majd kimásolja a címet a webböngésző címsorából.

   Ezt a lépést megtekintheti ezen a videón:
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=48&end=90" frameborder="0" allowfullscreen></iframe>

5. A Power BI Desktopban illessze be a címet a megjelenő párbeszédpanel **Webhely URL-címe** mezőjébe.

6. Előfordulhat, hogy nem jelenik meg az alábbi ábrán láthatóan a SharePoint hozzáférési képernyője.  Ha nem látja, ugorjon a 10. lépésre.  Ha megjelenik, válassza a lap bal oldalán található **Microsoft-fiók** lehetőséget.

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-auth1.png" alt="choose Microsoft account" width="500"/>

7. Válassza a **Bejelentkezés** lehetőséget, és adja meg azt a felhasználónevet és jelszót, amellyel a Microsoft Office 365-be is bejelentkezik.

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-auth2.png" alt="sign in" width="500"/>

8. A bejelentkezést követően válassza a **Kapcsolódás** lehetőséget.

9. A Navigátor bal oldalán jelölje be a jelölőnégyzetet amellett a SharePoint-lista mellett, amelyhez csatlakozni szeretne.

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-select-list.png" alt="get data" width="450"/>

10. Válassza a **Betöltés** elemet.  A Power BI betölti a lista adatait egy új jelentésbe.

## <a name="part-2-create-a-report"></a>2\. rész: Jelentés létrehozása

1. A bal oldalon válassza az **Adatok** ikont, hogy ellenőrizze, hogy valóban be lettek-e töltve a SharePoint-lista adatai.

2. Ellenőrizze, hogy a lista számokat tartalmazó oszlopaiban szerepel-e a Sum (Összeg), más néven szigma ikon a jobb oldali **Mezők panelen**.  Ahol nem szerepel, válassza ki az oszlop fejlécét a táblázat nézetben, válassza a **Modellezés** lapot, majd módosítsa az **Adattípust** **Decimális szám** vagy **Egész szám** típusra az adatoknak megfelelően.  Ha a rendszer kéri, hogy erősítse meg a módosítást, válassza az **Igen**lehetőséget.  Ha a szám egy speciális formátum, például pénznem, akkor azt is kiválaszthatja a **Formátum** beállításánál.

   Ezt a lépést megtekintheti ezen a videón:
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=147&end=204" frameborder="0" allowfullscreen></iframe>

3. A bal oldalon válassza a **Jelentés** ikont.
4. Jelölje ki a megjeleníteni kívánt oszlopokat a jobb oldali **Mezők** panelen a mellettük található jelölőnégyzet bejelölésével.

   Ezt a lépést megtekintheti ezen a videón:
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=215&end=252" frameborder="0" allowfullscreen></iframe>

5. Ha szükséges, módosítsa a vizualizáció típusát.
6. Több vizualizációt is létrehozhat ugyanabban a jelentésben. Ehhez törölje a bejelölést a meglévő vizualizációnál, majd jelölje be a jelölőnégyzeteket a többi oszlophoz a **Mezők** panelen.
7. A jelentés mentéséhez válassza a **Mentés** gombot.
