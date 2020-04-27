---
title: Vizualizáció másolása és beillesztése Power BI-jelentésbe
description: Vizualizáció másolása és beillesztése Power BI-jelentésbe
author: mihart
ms.reviewer: maggie tsang
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/13/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 03ce7f2a8ccd2c453521d28d172ffb25c1bb28bf
ms.sourcegitcommit: b2cb0b02bdc451bf11a92a68f2c4d560a811f563
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81440309"
---
# <a name="copy-and-paste-a-report-visualization"></a>Jelentésvizualizáció másolása és beillesztése

[!INCLUDE[consumer-appliesto-yyyn](../includes/consumer-appliesto-yyyn.md)]

Ez a cikk a vizualizációk másolásának és beillesztésének két különböző módját ismerteti. 
* egy jelentés vizualizációjának másolása, majd beillesztése egy másik jelentésoldalon (a jelentéshez szerkesztési engedély szükséges)

* vizualizáció képének másolása a Power BI-ból a vágólapra, majd beillesztése más alkalmazásokba

## <a name="copy-and-paste-within-the-same-report"></a>Másolás és beillesztés ugyanazon a jelentésen belül
A Power BI-jelentésekben lévő vizualizációk másolhatók a jelentésoldalon belül, vagy ugyanazon jelentés egy másik oldalára. 

A vizualizációk másolásához és beillesztéséhez a jelentésre vonatkozó szerkesztési jogosultságok szükségesek. A Power BI szolgáltatásban ehhez a [Szerkesztési nézetben](../consumer/end-user-reading-view.md) kell tudni megnyitni a jelentést. 

Az *irányítópultokon* lévő vizualizációk nem másolhatók és nem illeszthetők be Power BI-jelentésekben vagy más irányítópultokon.

1. Nyisson meg egy jelentést, amelyben legalább egy vizualizáció található.  

2. Jelölje ki a vizualizációt, és használja a **Ctrl+C** billentyűkombinációt a másoláshoz és a **Ctrl+V** billentyűkombinációt a beillesztéshez.      

   ![rövid videó a másolás és beillesztés menetéről](media/power-bi-visualization-copy-paste/copypasteviznew.gif)


## <a name="copy-a-visual-as-an-image-to-your-clipboard"></a>Vizualizáció másolása képként a vágólapra

Előfordult már, hogy egy Power BI-jelentésből vagy irányítópultból egy képet szeretett volna megosztani? Most már másolhatja a vizualizációt, és beillesztheti bármely olyan alkalmazásba, amely támogatja a beillesztést. 

Egy vizualizáció statikus képének másolásakor a vizualizáció és a metaadatok másolatát kapja meg. Ide tartoznak az alábbiak:
* hivatkozás a Power BI-jelentésre vagy irányítópultra
* a jelentés vagy az irányítópult címe
* értesítés, ha a rendszerkép bizalmas adatokat tartalmaz
* a legutóbbi frissítés időbélyege
* a vizualizációra alkalmazott szűrők

### <a name="copy-from-a-dashboard-tile"></a>Másolás irányítópult-csempéről

1. Lépjen arra az irányítópultra, amelyből másolni szeretne.

2. A vizualizáció jobb felső sarkában válassza a **További lehetőségek(...)** lehetőséget, majd válassza a **Vizualizáció másolása képként** elemet. 

    ![Megjelenik a vizualizáció másolása képként ikon](media/power-bi-visualization-copy-paste/power-bi-copy-dashboard.png)

3. Amikor megjelenik az **A vizualizáció készen áll a másolásra** párbeszédpanel, válassza a **Másolás a vágólapra** lehetőséget.

    ![a Másolás a vágólapra lehetőség párbeszédpanel](media/power-bi-visualization-copy-paste/power-bi-copied.png)

4. Ha a vizualizáció készen áll, illessze be egy másik alkalmazásba a **CTRL + V** billentyűkombinációval, vagy kattintson a jobb gombbal a Beillesztés elemre. Az alábbi képernyőképen a vizualizációt a Microsoft Wordbe illesztettük be. 

    ![az Outlookba beillesztett vizualizáció](media/power-bi-visualization-copy-paste/power-bi-paste-word.png)

### <a name="copy-from-a-report-visual"></a>Másolás jelentés vizualizációjából 

1. Lépjen arra a jelentésre, amelyből másolni szeretne.

2. A vizualizáció jobb felső sarkában válassza a **Vizualizáció másolása képként** elemet. 

    ![Megjelenik a vizualizáció másolása képként ikon](media/power-bi-visualization-copy-paste/power-bi-copy-icon.png)

3. Amikor megjelenik az **A vizualizáció készen áll a másolásra** párbeszédpanel, válassza a **Másolás a vágólapra** lehetőséget.

    ![a Másolás a vágólapra lehetőség párbeszédpanel](media/power-bi-visualization-copy-paste/power-bi-copied.png)


4. Ha a vizualizáció készen áll, illessze be egy másik alkalmazásba a **CTRL + V** billentyűkombinációval, vagy kattintson a jobb gombbal a Beillesztés elemre. Az alábbi képernyőképen a vizualizációt egy e-mailbe illesztettük be.

    ![az Outlookba beillesztett vizualizáció](media/power-bi-visualization-copy-paste/power-bi-copy-email.png)

5. Ha a jelentésre adatbizalmassági címke van alkalmazva, a másolás ikonra kattintva figyelmeztetés jelenik meg.  

    ![figyelmeztetés bizalmas adatokról](media/power-bi-visualization-copy-paste/power-bi-sensitive.png)

    A beillesztett vizualizáció alatti metaadatoknál megjelenik egy bizalmassági címke is. 

    ![vizualizáció bizalmas adatok címkével](media/power-bi-visualization-copy-paste/power-bi-confidential.png)

### <a name="manage-use-of-copying-a-visual-as-an-image"></a>Vizualizációk képként történő másolási lehetőségének kezelése
Ha Ön a tartalom tulajdonosa vagy a bérlő rendszergazdája, akkor meghatározhatja, hogy egy vizualizáció másolható legyen-e képként a jelentésekből vagy az irányítópultokról.

#### <a name="disable-copy-as-an-image-for-a-specific-visual"></a>A képként másolás letiltása meghatározott vizualizációhoz
Ha nem szeretné, hogy a felhasználók egy adott vizualizációt másolni tudjanak, eltávolíthatja a másolás ikont az adott vizualizációból.
1. A Formátum ablaktábla megnyitásához válassza a festőhenger ikont. 

1. Nyissa meg a **Vizualizáció formázása** kártyát.
1. Görgessen le a **Vizualizáció fejlécére**, bontsa ki a kártyát, és kapcsolja ki a **Másolás ikont**.

    ![festőhenger kiválasztva, másolás ikon kiválasztva](media/power-bi-visualization-copy-paste/power-bi-visual-header.png)

1. Ha nem találja a **Vizualizáció fejléce** beállítást, kapcsolja be a modern vizualizációs fejléc lehetőséget a **Jelentésbeállítások** alatt. 

    ![a modern vizualizáció-fejléc bekapcsolása](media/power-bi-visualization-copy-paste/power-bi-use-modern.png)

1. Mentse a módosításokat. Ha szükséges, végezze el újra a megosztást és a közzétételt.

#### <a name="disable-copy-as-an-image-for-a-group-of-users"></a>A képként másolás letiltása egy felhasználói csoporthoz

Ha Ön a tartalom tulajdonosa vagy a bérlő rendszergazdája, akkor meghatározhatja, hogy kik másolhatják a vizualizációkat. Ezzel a beállítással letiltható a *vizualizáció képként történő másolása* minden olyan tartalomhoz, amelyhez a felhasználó a Power BI-bérlőn keresztül fér hozzá.
  
1. Lépjen a felügyeleti portálra.

1. A **Bérlői beállítások** területen válassza az **Exportálási és megosztási beállítások** lehetőséget. 

    ![vizualizációk másolása és beillesztése engedélyezése](media/power-bi-visualization-copy-paste/power-bi-enable.png)

1. Tiltsa le a **Vizualizációk másolása és beillesztése** lehetőséget a kiválasztott felhasználói csoportokhoz. 

1. A módosítások mentése után a megadott csoportok nem tudják majd használni a **Vizualizáció másolása képként** lehetőséget a Power BI-ban. 
  

## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás

   ![másolás nem elérhető](media/power-bi-visualization-copy-paste/power-bi-copy-grey.png)


KÉRDÉS: Miért van letiltva a Másolás ikon a vizualizáción?    
VÁLASZ: Jelenleg a natív Power BI-vizualizációkat és a hitelesített vizualizációkat támogatjuk. Bizonyos vizualizációkat csak korlátozott mértékben támogatunk, többek között a következőket: 
- ESRI- és egyéb térképes vizualizációk 
- Python-vizualizációk 
- R vizualizációk 
- PowerApps 
- Nem tanúsított egyéni vizualizációk. Az egyéni vizualizációk támogatásáról további információt az [egyéni vizualizációk tanúsítása](../developer/visuals/power-bi-custom-visuals-certified.md) című témakörben talál. 


KÉRDÉS: Miért nem működik helyesen a vizualizációk beillesztése?    
VÁLASZ: A vizualizáció képként való másolásának korlátai vannak, többek között az alábbiak: 
- Egyéni vizualizációknál 
    - Vizualizációk témákkal és színekkel 
    - Csempe skálázása beillesztéskor 
    - Egyéni vizualizációk animációkkal 
- Másolási korlátozások 
    - Frissen rögzített irányítópult-csempe nem másolható 
    - A felhasználók nem irányíthatók át OData-szűrőkkel rendelkező tartalomhoz és ragadós állapotokhoz (például személyes könyvjelzőkhöz) 
- Azok az alkalmazások, melyeknél korlátozott a támogatás HTML-formázást tartalmazó tartalom vágólapról történő beillesztésére, előfordulhat, hogy nem jelenítenek meg mindent, ami a vizualizációból másolva lett 



## <a name="next-steps"></a>Következő lépések
További információk [a Power BI-jelentésekben lévő vizualizációkról](power-bi-report-visualizations.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

