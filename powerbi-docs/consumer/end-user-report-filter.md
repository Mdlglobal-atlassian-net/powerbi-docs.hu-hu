---
title: A Power BI Szűrők paneljének áttekintése felhasználók számára
description: A jelentések Szűrők paneljének áttekintése a Power BI szolgáltatásban
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 09/25/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: c49e075bd7fbe2debb0b577a1ce2771491d5fac4
ms.sourcegitcommit: 52ac456bf2ac025b22ea634c28482f22e1cc19ac
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/10/2018
ms.locfileid: "48908279"
---
# <a name="take-a-tour-of-the-report-filters-pane"></a>Ismerkedés a jelentések Szűrők panelével
Ez a cikk a jelentések Szűrők paneljét mutatja be a Power BI szolgáltatásban.

Az adatok szűrésének számos módja áll rendelkezésre a Power BI-ban, ezért javasoljuk, hogy először olvassa el a [szűrőkkel és a kiemeléssel](../power-bi-reports-filters-and-highlighting.md) foglalkozó szakaszt.

![jelentés a böngészőben](media/end-user-report-filter/power-bi-browser.png)

## <a name="working-with-the-report-filters-pane"></a>A jelentések Szűrők panelének használata
Amikor a munkatársa megoszt Önnel egy jelentést, mindenképp keresse meg a **Szűrők** panelt. Előfordulhat, hogy össze van csukva a jelentés jobb szélén. Kattintson rá a kibontáshoz.   

![jelentés a böngészőben](media/end-user-report-filter/power-bi-expanded.png)

A Szűrők panel olyan szűrőket tartalmaz, amelyekkel a jelentés *tervezője* látta el a jelentést. A *felhasználók* kezelhetik a szűrőket és menthetik a módosításokat, azonban nem adhatnak hozzá új szűrőket a jelentéshez.

A Power BI szolgáltatásban a jelentések megtartják a Szűrők panelen végzett módosításokat, és a jelentés mobilos verziójára is alkalmazzák őket. A Szűrő panelnek a tervező alapértelmezett értékeire való visszaállításához válassza ki a felső menüsáv **Visszaállítás alapértelmezettre** lehetőségét.     

## <a name="open-the-filters-pane"></a>A Szűrők panel megnyitása
Amikor megnyit egy jelentést, a Szűrők panel megjelenik a jelentésvászon jobb oldalán. Ha a panel nem látható, a jobb felső sarokban található nyíllal nyitható meg.  

Ehhez a példához egy 6 szűrővel rendelkező vizualizációt választottunk. A jelentésoldalon szintén találhatóak szűrők – ezek a **Lapszintű szűrők** cím alatt vannak felsorolva. Egy [Részletezési szűrő](../power-bi-report-add-filter.md) is rendelkezésre áll, továbbá a teljes jelentésre is vonatkozik egy szűrő: a **FiscalYear** (Pénzügyi év) lehet 2013 vagy 2014.

![szűrők listája](media/end-user-report-filter/power-bi-filter-list.png)

Némelyik szűrő mellett a **Mind** szó szerepel, ami azt jelzi, hogy a szűrő az összes értékre kiterjed.  A fenti képernyőfelvételen például a **Chain (All)** (Lánc (Mind)) beállítás azt jelzi, hogy a jelentésoldal az összes áruházlánc adatait tartalmazza.  Másfelől, a **FiscalYear is 2013 or 2014** (A pénzügyi év 2013 vagy 2014) jelentésszintű szűrő azt jelzi, hogy a jelentés csak a 2013-as és 2014-es pénzügyi évek adatait tartalmazza.

Bárki, aki megtekinti a jelentést, kezelheti ezeket a szűrőket.

* Megtekintheti egy szűrő részleteit, ha a kurzort a mellette lévő nyílra viszi, majd kijelöli a nyilat.
  
   ![a kijelölt Lindseys megjelenítése](media/end-user-report-filter/power-bi-expan-filter.png)
* Módosíthatja a szűrő értékeit, például a **Lindseys** értékét **Fashions Direct** értékre válthatja.
  
     ![a kijelölt Fashion Direct megjelenítése](media/end-user-report-filter/power-bi-filter-chain.png)

* A felső menüsáv **Visszaállítás alapértelmezettre** lehetőségével visszaállíthatja az eredeti állapotra a szűrőket.    
    ![visszaállítás alapértelmezettre](media/end-user-report-filter/power-bi-reset-to-default.png)
    
* Törölheti a szűrőt, ha a neve melletti **x** gombra kattint.
  
  A szűrő törlése eltávolítja a szűrőt a listából, de az adatokat nem törli a jelentésből.  Például ha törli a **FiscalYear is 2013 or 2014** szűrőt, a pénzügyi évek adatai továbbra is elérhetők a jelentésben, azonban a jelentés nem lesz a 2013-as és 2014-es pénzügyi évre korlátozva, hanem az összes olyan üzleti évet mutatja majd, amelyre vonatkozóan vannak adatok.  Miután törölt egy szűrőt, többé már nem tudja módosítani, mert lekerül a listáról. Jobb megoldás, ha csak a szűrő értékét törli a radír ikonra ![radír ikon](media/end-user-report-filter/power-bi-eraser-icon.png) kattintva.
  
  ![kiemelt x](media/end-user-report-filter/power-bi-delete-filter.png)



## <a name="clear-a-filter"></a>Szűrők törlése
 A szűrőket az alapszintű és a speciális szűrési módban is a radír ikonnal  ![radír ikon](media/end-user-report-filter/pbi_erasericon.jpg) lehet törölni. 


## <a name="types-of-filters-text-field-filters"></a>Szűrők típusai: szövegmezők szűrői
### <a name="list-mode"></a>Lista mód
A jelölőnégyzetekkel jelölhetők be az értékek vagy vonható vissza a bejelölésük. A **Mind** jelölőnégyzettel az összes jelölőnégyzet egyszerre jelölhető be, illetve egyszerre vonható vissza a kijelölésük. A jelölőnégyzetek az adott mező összes lehetséges értékét felsorolják.  A szűrők módosításával a szűrőutasítás frissül, és tükrözi a változtatásokat. 

![lista mód szűrő](media/end-user-report-filter/pbi_restatement.png)

Mint látható, az utasítás most a következő: „is Amarilla or Carretera” („Amarilla vagy Carretera”).

### <a name="advanced-mode"></a>Speciális mód
Kattintson a **Speciális szűrés** gombra, ha speciális módra szeretne váltani. A legördülő vezérlőkkel és szövegmezőkkel választhatja ki a szerepeltetendő mezőket. Az **És** és a **Vagy** operátorok használatával összetett szűrőkifejezéseket hozhat létre. Miután beállította a kívánt értékeket, kattintson a **Szűrő alkalmazása** gombra.  

![speciális mód](media/end-user-report-filter/aboutfilters.png)

## <a name="types-of-filters-numeric-field-filters"></a>Szűrők típusai: numerikus mezők szűrői
### <a name="list-mode"></a>Lista mód
Ha az értékek száma véges, a mező nevének kijelölésekor egy lista jelenik meg.  A jelölőnégyzetek használatával kapcsolatban lásd a fenti **Szövegmezők szűrői** &gt; **Lista mód** szakaszt.   

### <a name="advanced-mode"></a>Speciális mód
Ha az értékek száma véges vagy egy tartományt jelölnek, a mező nevének kijelölésekor megnyílik a speciális szűrési mód. A legördülő listák és a szövegmezők használatával adhatja meg a megjeleníteni kívánt értékek tartományát. 

![speciális szűrő](media/end-user-report-filter/pbi_dropdown-and-text.png)

Az **És** és a **Vagy** operátorok használatával összetett szűrőkifejezéseket hozhat létre. Miután beállította a kívánt értékeket, kattintson a **Szűrő alkalmazása** gombra.

## <a name="types-of-filters-date-and-time"></a>Szűrők típusai: dátum és időpont
### <a name="list-mode"></a>Lista mód
Ha az értékek száma véges, a mező nevének kijelölésekor egy lista jelenik meg.  A jelölőnégyzetek használatával kapcsolatban lásd a fenti **Szövegmezők szűrői** &gt; **Lista mód** szakaszt.   

### <a name="advanced-mode"></a>Speciális mód
Ha egy mező dátum- vagy időértékeket tartalmaz, a Dátum/idő szűrőknél megadhat kezdő és befejező időpontokat.  

![dátum/idő szűrő](media/end-user-report-filter/pbi_date-time-filters.png)


## <a name="next-steps"></a>Következő lépések
[Ismerje meg, hogyan és miért történik keresztszűrés és keresztkiemelés a vizualizációknál a jelentésoldalakon.](end-user-interactions.md)