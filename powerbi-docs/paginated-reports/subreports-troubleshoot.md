---
title: Lapszámozott Power BI-jelentések segédjelentéseinek hibaelhárítása
description: Ebből a cikkből megtudhatja, hogy milyen adatforrásokat támogatnak a Power BI szolgáltatás többoldalas jelentései, és megismerheti az Azure SQL Database-adatforrások csatlakoztatásának módját.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 04/29/2020
ms.openlocfilehash: 6de85f6dda69e902a98d6ee63d1fc4b86fb4180b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82615634"
---
# <a name="troubleshoot-subreports-in-power-bi-paginated-reports"></a>Lapszámozott Power BI-jelentések segédjelentéseinek hibaelhárítása

Előfordulhat a segédjelentések lapszámozott jelentésekben történő használata során, hogy nem várt eredményt kap, vagy nem a kívánt módon működik. Ez a cikk a segédjelentések használata során felmerülő gyakori problémákra nyújt megoldást. A *segédjelentés* egy jelentéselem, amely egy másik lapszámozott jelentést jelenít meg egy főjelentés törzsében. További információ: [Lapszámozott Power BI-jelentések segédjelentései](subreports.md).

## <a name="subreport-couldnt-be-found"></a>A segédjelentés nem található

**Leírás:** A segédjelentés nem renderelhető. Ehelyett hibaüzenet jelenik meg.

### <a name="message"></a>Üzenet

„A Subreport1 nevű segédjelentés nem található a CustomerDetails területen. Győződjön meg arról, hogy a segédjelentés közzé lett téve, és a név helyes.”

### <a name="possible-reasons"></a>Lehetséges okok

- A megadott névvel nem létezik segédjelentés a főjelentéssel megegyező munkaterületen vagy alkalmazásban.
- A felhasználónak nincs hozzáférése a segédjelentéshez.
- A főjelentésben található segédjelentések száma elérte a felső korlátot (50).

### <a name="troubleshooting-steps"></a>Hibaelhárítási lépések

**Munkaterületen**

- Ellenőrizze, hogy létezik-e a hibaüzenetben szereplő nevű jelentés. A név megkülönbözteti a kis- és nagybetűket.

**Alkalmazásban**

- Ellenőrizze, hogy létezik-e az alkalmazásban a hibaüzenetben szereplő nevű jelentés. További segítségért forduljon az alkalmazás készítőjéhez.

**Megosztott jelentésnél**

1. Ellenőrizze, hogy meg van-e osztva Önnel a hibaüzenetben szereplő nevű jelentés.
2. Ha a jelentés létezik, ellenőrizze, hogy a tulajdonos neve ugyanaz-e a főjelentésben és a segédjelentésben. Ezután vegye fel a kapcsolatot a főjelentés tulajdonosával.

## <a name="subreport-renders-with-unexpected-content"></a>A segédjelentés váratlan tartalommal jelenik meg

### <a name="possible-reason"></a>Lehetséges ok

A Power BI engedélyezi, hogy a felhasználók több azonos nevű jelentéssel rendelkezzenek egy munkaterületen belül

### <a name="troubleshooting-steps-for-report-authors"></a>Hibaelhárítási lépések (jelentéskészítőknek)

1. Nyissa meg a főjelentést a Power BI Jelentéskészítőben, majd határozza meg a segédjelentés nevét.
2. Keressen azonos nevű jelentéseket a munkaterületen.
3. Keresse meg a várt jelentést, és nevezze át a többit.

**Nem készítőknek:** Forduljon a készítőhöz.

## <a name="data-retrieval-fails"></a>Adatlekérési hibák

**Leírás:** Az adatlekérés meghiúsul a segédjelentés renderelésekor. A segédjelentés nem renderelhető. Ehelyett hibaüzenet jelenik meg.

### <a name="message"></a>Üzenet

„Az adatlekérés sikertelen volt az alábbi helyen található, Subreport1 nevű segédjelentéshez: InvoiceDetails. További információkat a naplófájlban találhat.”

### <a name="troubleshooting-steps"></a>Hibaelhárítási lépések

Megegyeznek az adatelérési problémákkal rendelkező jelentések hibaelhárítási lépéseivel.

## <a name="rendering-fails-unspecified-parameters"></a>Renderelési hibák: Meghatározatlan paraméterek

**Leírás:** A segédjelentés renderelése meghiúsul nem meghatározott paraméterek miatt. A segédjelentés kötelező paramétereket tartalmaz, azonban nem mindegyiket a főjelentés állítja be.

### <a name="message"></a>Üzenet 
„Egy vagy több paraméter nem lett megadva a segédjelentéshez (Subreport1), amelynek helye: SubreportAWithDS.”

### <a name="troubleshooting-steps-for-the-report-author"></a>Hibaelhárítási lépések (a jelentéskészítőnek)

1. Nyissa meg a főjelentést a Power BI Jelentéskészítőben.
2. Nyissa meg a segédjelentést a Power BI Jelentéskészítőben.
3. Győződjön meg arról, hogy a főjelentés segédjelentésének jelentéselemében megadott paraméterek megegyeznek a segédjelentés paramétereivel.

**Nem készítőknek:** Forduljon a készítőhöz.

## <a name="rendering-fails-recursion-limit"></a>Renderelési hibák: Rekurziós korlát

**Leírás:** A segédjelentés renderelése meghiúsul a rekurziós korlát miatt. A segédjelentések nem ágyazhatók be 20 szintnél mélyebbre.

### <a name="message"></a>Üzenet

„A jelentésben vagy a segédjelentésben van egy rekurzív segédjelentés (Subreport1), amely túllépte az engedélyezett rekurziós korlátot.”

### <a name="troubleshooting-steps-for-report-authors"></a>Hibaelhárítási lépések (jelentéskészítőknek)

- Csökkentse a beágyazást.
- Tervezze újra a jelentés szerkezetét.

## <a name="other-errors"></a>Egyéb hibák

**Leírás:** Az előző kategóriákba nem besorolható hibák.

### <a name="message"></a>Üzenet

„Hiba: A segédjelentés nem jeleníthető meg.”

### <a name="possible-reasons"></a>Lehetséges okok

- Több hiba történt a segédjelentés renderelése során, például nem egyeztek a paraméterek, és adatlekérési hiba történt.
- Váratlan hibák.

### <a name="troubleshooting-steps-for-report-authors"></a>Hibaelhárítási lépések (jelentéskészítőknek)

1. Győződjön meg arról, hogy a segédjelentés közvetlenül renderelhető.
2. Ha a segédjelentés renderelhető, ellenőrizze a segédjelentés és a főjelentés paramétereit.
3. Győződjön meg arról, hogy a főjelentés nem rendelkezik 50-nél több egyéni segédjelentéssel, a segédjelentés pedig nincs 20 szintnél mélyebben beágyazva.
4. Ha nem tudja elhárítani a problémát, forduljon Power BI ügyfélszolgálatához.

**Nem készítőknek:** Forduljon a készítőhöz.

## <a name="next-steps"></a>Következő lépések

[Lapszámozott Power BI-jelentések segédjelentései](subreports.md)

[Lapszámozott jelentés megtekintése a Power BI szolgáltatásban](../consumer/paginated-reports-view-power-bi-service.md)

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)
