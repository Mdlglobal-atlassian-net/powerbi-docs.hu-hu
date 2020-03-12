---
title: Lapszámozott jelentések a Power BI szolgáltatásban
description: A lapszámozott jelentéseket és azok a Power BI szolgáltatásban való megtekintését ismertető dokumentáció
author: mihart
ms.reviewer: chris finlan
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: mihart
LocalizationGroup: Common tasks
ms.openlocfilehash: 0ab2ececd4ede03a10094be53a2c08617463cc53
ms.sourcegitcommit: 480bba9c745cb9af2005637e693c5714b3c64a8a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/11/2020
ms.locfileid: "79113116"
---
# <a name="paginated-reports-in-the-power-bi-service"></a>Lapszámozott jelentések a Power BI szolgáltatásban

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

Már megismerkedhetett a [Power BI-jelentésekkel](end-user-reports.md), amelyekkel a leginkább valószínű, hogy találkozhat. Létezik azonban egy másik, úgynevezett *lapszámozott jelentés* is. A *jelentés tervezők* megoszthatják Önnel ezeket a lapszámozott jelentéseket egy Prémium kapacitás munkaterületén vagy egy ehhez a munkaterülethez tartozó alkalmazásban. 

## <a name="what-is-a-paginated-report"></a>A lapszámozott jelentések ismertetése

*Lapszámozott* jelentésnek hívjuk őket, mert egy nyomtatott oldalon jól megjeleníthetők. Egyik előnyük, hogy minden adatot egy táblázatban jelenítenek meg, akkor is, ha az több oldalon keresztül fut. A *jelentéstervezők* az oldalak elrendezését pontosan vezérelhetik egészen az utolsó pixelig.

A *jelentéstervezők* a lapszámozott jelentések tervezésekor valójában egy *jelentésdefiníciót* készítenek. Ez nem tartalmazza az adatokat. Az adatok lekérésének helyét, a lekérendő adatokat és azok megjelenítési módját szabja meg. A jelentés futtatásakor a jelentésfeldolgozó a jelentésdefiníció és a lekért adatok a jelentés elrendezésének egyesítésével létrehozza a jelentést. Időnként a jelentés az alapértelmezett értékeket jeleníti meg. Más alkalmakkor meg kell adnia jelentésparamétereket, mielőtt adatokat jeleníthetne meg. 

   ![A jelentés paraméterei](./media/end-user-paginated-report/power-bi-report-parameters.png)

A felhasználói interakció általában ennyiben ki is merül – a paraméterek megadásában. Ha Ön számlázási elemző, lapszámozott jelentésekkel létrehozhat vagy kinyomtathat számlákat. Ha Ön értékesítési vezető, lapszámozott jelentésekkel tekinthet meg rendeléseket áruház vagy értékesítő szerint. 

Ez az egyszerű lapszámozott jelentés az **Év** paraméter kiválasztása után az éves profitot jeleníti meg. 

![Egyszerű, egy paraméteres jelentés](./media/end-user-paginated-report/power-bi-report-simple.png)

A lapszámozott jelentésekhez képest a Power BI-jelentések sokkal interaktívabbak. A Power BI-jelentések ad-hoc jelentéseket tesznek lehetővé, és számos további vizualizációt támogatnak, így az egyéni vizualizációkat is.

## <a name="identify-a-paginated-report"></a>Lapszámozott jelentés azonosítása

A tartalomlistában és a kezdőlapon az ikon ![lapszámozott jelentés ikonja](media/end-user-paginated-report/power-bi-report-icon.png) alapján azonosíthatók a lapszámozott jelentések.  A lapszámozott jelentések közvetlenül vagy egy [Power BI-alkalmazás részeként](end-user-apps.md) is megoszthatók. Ha a *jelentéstervező* erre engedélyt adott Önnek, megoszthatja a lapszámozott jelentést, és feliratkozhat rá, illetve másokat is feliratkoztathat rá.

![jelentéslista különböző ikonokkal](./media/end-user-paginated-report/power-bi-report-list.png)

## <a name="interact-with-a-paginated-report"></a>Lapszámozott jelentés használata

A lapszámozott jelentések használata eltér a többi jelentésétől. Olyan műveleteket végezhet, mint a nyomtatás, a könyvjelzőzés, az exportálás vagy a megjegyzések hozzáfűzése, azonban összességében kevésbé interaktív a jelentés. A lapszámozott jelentésekhez gyakran felhasználói bemenetre van szükség a jelentésvászon kitöltéséhez.  A jelentés néha alapértelmezett adatokat jelenít meg, és Önnek kell paramétereket megadnia, hogy eltérő adatokat lásson.

### <a name="print-a-paginated-report"></a>Lapszámozott jelentés nyomtatása

A*lapszámozott* jelentések úgy vannak formázva, hogy jól elférjenek a kinyomtatható oldalakon. Amit a böngészőben lát, azt látja majd a nyomtatott lapon is. Emellett ha a jelentés egy hosszú táblázattal rendelkezik, a teljes táblázatot kinyomtathatja, akkor is, ha az több lapon átível. 

A lapszámozott jelentések számos oldalból állhatnak. Ez a jelentés például 563 oldalas. Mindegyik oldal pontosan egy számlát tartalmaz, valamint ismétlődő fejlécekből és élőlábakból áll. A jelentés kinyomtatásakor oldaltörések szerepelnek a számlák között.

   ![A Tailspin Toys lapszámozott jelentésének első oldala](./media/end-user-paginated-report/power-bi-paginated-500.png)


### <a name="navigate-the-paginated-report"></a>Navigálás a lapszámozott jelentésben

Ebben az értékesítési megrendelési jelentésben három paraméter szerepel: Üzlettípus, viszonteladó és rendelési szám. 

![három paraméterrel rendelkező jelentés](./media/end-user-paginated-report/power-bi-parameter.png)

A megjelenített adatok módosításához adjon meg új értékeket a három paraméterhez, majd válassza a **jelentés megtekintése** lehetőséget. Itt a **Specialty bike shop** és az **Alpine Ski House** paramétert, valamint az **SO46085** rendelési számot választottuk ki. A **Jelentés megtekintése** funkció frissíti a jelentésvászont az új értékesítésii megrendeléssel.

![paraméterek módosítása](./media/end-user-paginated-report/power-bi-order.png)

Megjelenik az új értékesítési megrendelés a kiválasztott paraméterekkel. 

![új értékesítési megrendelés](./media/end-user-paginated-report/power-bi-new-order.png)

Egyes lapszámozott jelentések számos oldalból állnak.  A jelentésben az oldalvezérlőkkel navigálhat. 

![oldalvezérlők](./media/end-user-paginated-report/power-bi-page.png)

### <a name="export-the-paginated-report"></a>A lapszámozott jelentés exportálása
Számos lehetőség áll rendelkezésre a lapszámozott jelentések exportálására, például PDF, Word, ML, PowerPoint, Excel és további formátumokban. Exportáláskor a rendszer a lehető legtöbb formázást megőrzi. Például az Excel-, Word-, PowerPoint-, MHTML- vagy PDF-fájlként exportált lapszámozott jelentések egészen pontosan megtartják a formázást. 

![új értékesítési megrendelés](./media/end-user-paginated-report/power-bi-exporting.png)

![négy különböző exportálási típus](./media/end-user-paginated-report/power-bi-four.png)

### <a name="subscribe-to-the-paginated-report"></a>Feliratkozás a lapszámozott jelentésre
Amikor feliratkozik egy lapszámozott jelentésre, a Power BI egy e-mailt küld Önnek, amelynek csatolmánya a jelentés. Feliratkozás beállításakor kiválaszthatja, hogy milyen gyakorisággal szeretné fogadni az e-maileket: naponta, hetente, havonta vagy óránként. A feliratkozás tartalmaz egy, a teljes jelentés eredményeit összesítő csatolmányt is (amely legfeljebb 25 MB méretű). Exportálja a teljes jelentést, vagy előre válassza ki a paramétereket. Számos különböző melléklettípusból választhat, így Excel, PDF, PowerPoint és hasonló formátumokból.  

![Feliratkozások formátumai](./media/end-user-paginated-report/power-bi-export-list.png)

## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás

- A lapszámozott jelentések üresen jelenhetnek meg, amíg Ön ki nem választja a paramétereket, majd a **Jelentés megtekintése** lehetőséget nem választja.

- Ha nem rendelkezik lapszámozott jelentésekkel, annak oka az lehet, hogy senki nem osztott meg Önnel ilyen típusú jelentést. De azt is jelentheti, hogy a rendszergazda nem engedélyezte Önnek a lapszámozott jelentéseket. 

 

## <a name="next-steps"></a>Következő lépések
- [A Power BI-jelentések](end-user-reports.md)
- További kérdései vannak? Kérdezze meg [a Power BI közösségét](https://community.powerbi.com/).

