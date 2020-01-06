---
title: A Power BI-vizualizáció létrehozásához használt adatok megjelenítése
description: Ez a dokumentum ismerteti, hogyan jelenítheti meg a Power BI-ban a vizualizációk létrehozásához használt adatokat, és hogyan exportálhatja ezeket az adatokat .csv fájlba.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/4/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 5417511b12c85cb467c3613671a1e101541c9609
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/06/2020
ms.locfileid: "73880614"
---
# <a name="show-the-data-that-was-used-to-create-the-visualization"></a>A vizualizáció létrehozásához használt adatok megjelenítése
## <a name="show-data"></a>Adatok megjelenítése
A Power BI-vizualizációk az adatkészletekből származó adatokból jönnek létre. Ha látni szeretné a háttérfolyamatokat, a Power BI-jal *megjelenítheti* a vizualizáció létrehozásához használt adatokat. Amikor az **Adatok megjelenítése** elemet választja, a Power BI megjeleníti a vizualizáció alatt (vagy mellett) lévő adatokat.

A vizualizáció létrehozásához használt adatokat exportálhatja is .xlsx vagy .csv fájlként, és megtekintheti azokat az Excelben. További információt az [Adatok exportálása Power BI-vizualizációkból](power-bi-visualization-export-data.md) című szakaszban talál.

> [!NOTE]
> Az *Adatok megjelenítése* és az *Adatok exportálása* a Power BI szolgáltatásban és a Power BI Desktopban is elérhető. A Power BI Desktop azonban egy további részletességi szintet nyújt; a [*Rekordok megjelenítése* megjeleníti az adatkészletből származó tényleges sorokat](../desktop-see-data-see-records.md).
> 
> 

## <a name="using-show-data"></a>Az *Adatok megjelenítése* funkció használata 
1. A Power BI Desktopban válasszon ki egy vizualizációt, hogy aktívvá tegye azt.

2. Válassza a **További műveletek** (...), majd az **Adatok megjelenítése** lehetőséget. 
    ![megjelenítési beállítás az Adatok megjelenítése funkcióhoz](media/service-reports-show-data/power-bi-more-action.png)


3. Alapértelmezés szerint az adatok a vizualizáció alatt jelennek meg.
   
   ![vizualizációk és adatok függőleges megjelenítése](media/service-reports-show-data/power-bi-show-data-below.png)

4. A tájolás módosításához válassza a függőleges elrendezést ![kis képernyőkép a függőleges elrendezésre való váltáshoz használt ikonról](media/service-reports-show-data/power-bi-vertical-icon-new.png) a vizualizáció jobb felső sarkában.
   
   ![vizualizációk és adatok vízszintes megjelenítése](media/service-reports-show-data/power-bi-show-data-side.png)
5. Ha az adatokat .csv fájlba szeretné exportálni, válassza a három pontot, majd az **Adatok exportálása** elemet.
   
    ![az Adatok exportálása lehetőség kiválasztása](media/service-reports-show-data/power-bi-export-data-new.png)
   
    Az adatok Excelbe való exportálásáról további információt az [Adatok exportálása Power BI-vizualizációkból](power-bi-visualization-export-data.md) című szakaszban talál.
6. Az adatok elrejtéséhez kapcsolja ki a **Tallózás** > **Adatok megjelenítése** beállítást.

## <a name="using-show-records"></a>A Rekordok megjelenítése funkció használata
A vizualizációk egy-egy adatrekordja is a középpontba állítható, és részletesen megvizsgálhatók az alapjául szolgáló mögöttes adatok. 

1. A **Rekordok megtekintése** funkció használatához válasszon ki egy vizualizációt, hogy aktívvá tegye azt. 

2. Az asztali szalagon válassza ki a **Vizuális eszközök** > **Adatok / Részletezés** > **Rekordok megjelenítése** lapot. 

    ![Képernyőkép a Rekordok megjelenítése lap kiválasztott állapotáról.](media/service-reports-show-data/power-bi-see-record.png)

3. Válasszon ki egy adatpontot vagy -sort a vizualizációban. Ebben a példában balról a negyedik oszlopot választottuk ki. A Power BI megjeleníti az ehhez az adatponthoz tartozó adatkészletrekordot.

    ![Képernyőkép az adatkészlet egyetlen rekordjáról.](media/service-reports-show-data/power-bi-row.png)

4. Válassza a **Vissza a jelentéshez** lehetőséget az asztali jelentésvászonhoz való visszatéréshez. 

## <a name="considerations-and-troubleshooting"></a>Megfontolandó szempontok és hibaelhárítás

- Ha a szalag **Rekordok megjelenítése** gombja le van tiltva és ki van szürkítve, az azt jelenti, hogy a kiválasztott vizualizáció nem támogatja a Rekordok megjelenítése funkciót.
- A Rekordok megjelenítése nézetben az adatok nem módosíthatók és nem menthetők vissza a jelentésbe.
- A Rekordok megjelenítése nem használható, ha a vizualizáció számított mértéket használ.
- A Rekordok megjelenítése nem használható, ha élő többdimenziós (multidimensional, MD) modellt használ.  

## <a name="next-steps"></a>Következő lépések
[Adatok exportálása Power BI-vizualizációkból](power-bi-visualization-export-data.md)    

További kérdései vannak? [Kérdezze meg a Power BI közösségét](https://community.powerbi.com/)

