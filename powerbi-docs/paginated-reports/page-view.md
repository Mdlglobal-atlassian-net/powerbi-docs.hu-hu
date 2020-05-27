---
title: Jelentés nézeteinek beállítása többoldalas jelentésekhez – Power BI
description: Ebben a cikkben a különféle jelentésnézetekről tanulhat, amelyek a Power BI szolgáltatásban elérhetőek a többoldalas jelentésekhez.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: ''
ms.topic: conceptual
ms.date: 05/14/2020
ms.openlocfilehash: 3816cfe4e1b61b9445e16d7c322c5ba19aa2bc3d
ms.sourcegitcommit: 21b06e49056c2f69a363d3a19337374baa84c83f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/15/2020
ms.locfileid: "83407932"
---
# <a name="set-report-views-for-paginated-reports-in-the-power-bi-service"></a>Jelentés nézeteinek beállítása többoldalas jelentésekhez a Power BI szolgáltatásban

Ha többoldalas jelentést jelenít meg a Power BI szolgáltatásban, az alapértelmezett nézet HTML-alapú és interaktív. Egy másik jelentésnézet, amely a rögzített oldalak, például a PDF formátuma, az új Oldal nézet beállítás.

**Alapértelmezett interaktív nézet**

![Alapértelmezett nézet](media/page-view/power-bi-paginated-default-view.png)

**Oldal nézet**

![Oldal nézet](media/page-view/power-bi-paginated-page-view.png)

Az oldal nézetben a megjelenített jelentés az alapértelmezett nézethez képest eltérően jelenik meg. A többoldalas jelentésekben szereplő tulajdonságok és fogalmak csak rögzített lapokra vonatkoznak. A nézet hasonló ahhoz, amikor a jelentést kinyomtatjuk vagy exportáljuk. Bizonyos elemeket, például a paraméterértékeket továbbra is módosíthatja, de nem rendelkezik más interaktív funkciókkal, például oszlopok rendezésével vagy váltásával.

Az oldal nézet támogatja a böngésző PDF-megjelenítője által támogatott összes funkciót, például a nagyítást, a kicsinyítést és a laphoz igazítást.

## <a name="switch-to-page-view"></a>Váltás oldal nézetre

Amikor megnyit egy többoldalas jelentést, az alapértelmezés szerint az interaktív nézetben jelenik meg. Ha a jelentésben paraméterek is vannak, válassza a paraméterek lehetőséget, majd tekintse meg a jelentést.

1. Az eszköztáron válassza a **Nézet** > **Oldal nézet** lehetőséget.

    ![Váltás oldal nézetre](media/page-view/power-bi-paginated-page-view-dropdown.png)

2. Az oldal nézet beállításainak megváltoztatásához válassza az **Oldalbeállítások** elemet az eszköztár **Nézet** menüjében. 

    ![Oldalbeállítások kiválasztása](media/page-view/power-bi-paginated-page-settings-dropdown.png)
    
    Az **Oldalbeállítások** párbeszédpanelen beállítható az **Oldalméret** és a **Tájolás** az oldal nézethez. Az oldalbeállítások alkalmazása után ugyanezek a beállítások lesznek érvényesek, amikor később kinyomtatja a lapot.
   
    ![Oldalbeállítások párbeszédpanel](media/page-view/power-bi-paginated-page-settings-dialog.png)

3. Ha vissza szeretne térni az interaktív nézetre, válassza az **Alapértelmezett** lehetőséget a **Nézet** legördülő listában.

## <a name="browser-support"></a>Böngészőtámogatás

Az oldal nézetet támogatja a Google Chrome és a Microsoft Edge. Ügyeljen rá, hogy a megtekintés PDF-ként engedélyezve legyen a böngészőben. Ezekben a böngészőkben az az alapértelmezett beállítás.

Az Internet Explorer és a Safari nem támogatja az oldal nézetet, ezért a beállítás le van tiltva. Nem támogatott továbbá mobileszközök böngészőiben és a natív Power BI mobilalkalmazásokban sem.  


## <a name="next-steps"></a>Következő lépések

- [Lapszámozott jelentés megtekintése a Power BI szolgáltatásban](../consumer/paginated-reports-view-power-bi-service.md)
- [Mik a lapszámozott jelentések a Power BI Premiumban?](paginated-reports-report-builder-power-bi.md)
